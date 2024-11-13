# Kuksa Quickstart

The quickest possible way to get Kuksa up and running

*Note: The examples in this document do not use TLS or access control.*
*They use the latest released version and use default settings as far as possible.*
*More details on how you can configure the components is available in the [GitHub Repositories](https://github.com/eclipse-kuksa)!*


## Starting broker
First we want to run latest released version of Kuksa Databroker

```
docker run -it --rm --net=host ghcr.io/eclipse-kuksa/kuksa-databroker:latest --insecure
```

## Reading and Writing VSS data via CLI
You can interact with the VSS datapoints using the cli clients. The first option is databroker-cli.

This is, how you start it:

```
docker run -it --rm --net=host ghcr.io/eclipse-kuksa/kuksa-databroker-cli:latest
```

Here is how you can use it:

```
kuksa.val.v1 > get Vehicle.Speed
[get]  OK  
Vehicle.Speed: NotAvailable
kuksa.val.v1 > publish Vehicle.Speed 200
[publish]  OK  
kuksa.val.v1 > get Vehicle.Speed
[get]  OK  
Vehicle.Speed: 200.00 km/h
kuksa.val.v1 > quit
Bye bye!

```

An alternative is the kuksa-client CLI (based on our Python client library).

Here is how you start it:

```
docker run -it --rm --net=host ghcr.io/eclipse-kuksa/kuksa-python-sdk/kuksa-client:latest
```

Here is how you can use it:

```
Test Client> getValue Vehicle.Speed
{
    "path": "Vehicle.Speed"
}

Test Client> setValue Vehicle.Speed 200
OK

Test Client> getValue Vehicle.Speed    
{
    "path": "Vehicle.Speed",
    "value": {
        "value": 200.0,
        "timestamp": "2024-11-13T14:29:37.156154+00:00"
    }
}

Test Client> quit
2024-11-13 14:29:50,087 INFO kuksa_client.cli_backend.grpc: gRPC channel disconnected.

```

It is also possible to install the kuksa-client using [PyPI](https://pypi.org/project/kuksa-client/)

## Reading and Writing VSS data with code

To realize your ideas with Kuksa you need to write programs that interact with its API. The easiest way to achieve this is using our Python library.

### Generating data

Create a file `speed_provider.py` with the following content

```python
from kuksa_client.grpc import VSSClient
from kuksa_client.grpc import Datapoint

import time

with VSSClient('127.0.0.1', 55555) as client:
    for speed in range(0,100):
        client.set_current_values({
        'Vehicle.Speed': Datapoint(speed),
        })
        print(f"Feeding Vehicle.Speed to {speed}")
        time.sleep(1)
print("Finished.")
```

Do a `pip install kuksa-client` and start with

```
python ./speed_provider.py
```

### Subscribing data:

Create a file `speed_subscriber.py` with the following content

```python
from kuksa_client.grpc import VSSClient

with VSSClient('127.0.0.1', 55555) as client:

    for updates in client.subscribe_current_values([
        'Vehicle.Speed',
    ]):
        speed = updates['Vehicle.Speed'].value
        print(f"Received updated speed: {speed}")
```

Do a `pip install kuksa-client` and start with

```
python ./speed_subscriber.py
```

If you now run `speed_provider.py` and `speed_subscriber.py` in parallel you should get updated speed values in the subscriber.

```
Received updated speed: 0.0
Received updated speed: 1.0
Received updated speed: 2.0
Received updated speed: 3.0
Received updated speed: 4.0
Received updated speed: 5.0
...
```

## FAQ & Notes
Frequently anticipated questions and tips.

### This is not working on OS X

Unfortunately OS X has a bug that does not allow you to use the Databroker default port 55555. To change when starting the server:

```
docker run -it --rm --net=host ghcr.io/eclipse-kuksa/kuksa-databroker:latest --port 55556 --insecure
```

Using the databroker-cli

```
docker run -it --rm --net=host -e KUKSA_DATA_BROKER_PORT=55556 ghcr.io/eclipse-kuksa/kuksa-databroker-cli:latest
```

Using kuksa-client CLI

```
docker run -it --rm --net=host ghcr.io/eclipse-kuksa/kuksa-python-sdk/kuksa-client:latest grpc://127.0.0.1:55556
```

### Docker desktop: Host networking not supported

The examples above all used docker's `--net=host` option. That is quite convenient for development, as basically your containers "share" your hosts networking and there is no need for any port publishing.

However when using Docker Desktop on Mac OS or Windows, [host networking is not supported](https://docs.docker.com/network/host/).

One alternative is using a Docker distribution, that does support it even on Mac OS or Windows. [Rancher Desktop](https://rancherdesktop.io) is an alternative that does.

With Docker Desktop you can still forward ports, so this should work:

```
docker run -it --rm --publish 55556:55556 ghcr.io/eclipse-kuksa/kuksa-databroker:latest  --port 55556 --insecure
```

From your host computer you can now reach databroker at `127.0.0.1:55556`. To connect from another container, you need to use your computers IP address (**not** 127.0.0.1), i.e. to use the client

```
docker run -it --rm  -e KUKSA_DATA_BROKER_PORT=55556 -e KUKSA_DATA_BROKER_ADDR=<YOUR_IP> ghcr.io/eclipse-kuksa/kuksa-databroker-cli:latest
```

Recent versions of the databroker-cli also support command line arguments, so you can also write

```
docker run -it --rm  ghcr.io/eclipse-kuksa/kuksa-databroker-cli:latest  --server http://<YOUR_IP>:55556
```

### publish/set: Why is my data not updated?
Some VSS points are "sensors", e.g. Vehicle.Speed. You can read/get Vehicle speed, but we are not expecting to be able to influence it via VSS.
Historically components, that gather the actual vehicle speed from some sensors/busses in a vehicle and providing a VSS representation to Kuksa have been called `feeders`. Hence, to update the current speed in the Rust-cli, you use

```
publish Vehicle.Speed 200
```

while in the Python-cli you use

```
set Vehicle.Speed 200
```

The other thing, that VSS provides you are "actuators" `Vehicle.Body.Trunk.Rear.IsOpen`. The most important thing to remember about actuators: Every actuators is also a sensor, so everything written on top applies as well!
The second-most important thing is: For VSS actuatorss, it is expected that you might be able to influence the state of the real Vehicle by writing to them. So while being used as a sensor, you will get the current position of the Window in the example, you might also want to set the _desired_ position.

You express this in the databroker-cli as

```
actuate Vehicle.Body.Trunk.Rear.IsOpen true
```

In kuksa-client cli you do

```
Test Client> setTargetValue Vehicle.Body.Trunk.Rear.IsOpen True
```

In the code examples above you would do

```python
client.set_target_values({
        'Vehicle.Body.Trunk.Rear.IsOpen': Datapoint(True),
    })
```

### All I see is Python, shouldn't this be high-performance?
Our Python library makes it easy to interact with Databroker. While this is often sufficient for many applications, you are not limited by it: Databroker's native interface is based on gRPC, a high-performance GRPC framework. gRPC enables you to generate bindings for _any_ language. Check the [gRPC website](https://grpc.io) and take a look at the [Databroker interface definitions](https://github.com/eclipse-kuksa/kuksa-databroker/tree/main/proto).
