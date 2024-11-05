---
title: "Contributing"
date: 2019-01-29T09:46:31+02:00
draft: false
---

# How to contribute to Eclipse Kuksa
Great that you are interested in contributing to Eclipse Kuksa. 
We really looking forward to receive your contribution!

In the project we agreed upon the following approach to add contributions to the project.

1. Meet the Definition of Done (DoD)
2. A review took place for the code
3. The new feature was at least once tested manually, deployed to a running test instance
4. Clearly outline third party dependencies

## Definition of Done

First, we have DoD for solved issues. Please check if you met all the items in the following list:

* File headers in file OK (see section [License Headers](#licensing-and-file-header) for details)

* Coding style
  * Clean code is encouraged (see ‘Clean Code’ by Robert C. Martin or the 
    [Clean Code Cheatsheet](https://www.bbv.ch/images/bbv/pdf/downloads/V2_Clean_Code_V3.pdf).
    Reviewers might refer to specific clean code practices to help improve contributed code.

* Avoid (serious) compiler warnings

* Add tests for new / added functionality

* All tests pass
  * Unit testing as it is already present
  * If you have more - contribute them!

* Documentation
  * Provide the necessary technical documentation of your feature in the respective 
    Github repository that you contribute to. Documentation is in markdown and it either 
    included in the top-level README.md file of the Github repository, or linked from 
    there. 

* Commit style
  * Please write brief and useful commit messages: Separate the subject from body with a blank line because the subject line
    is shown in the git history and should summarize the commit body. Use the body to explain what and why vs. how.
    https://chris.beams.io/posts/git-commit/#seven-rules has more tips and details.
  * Before you push your commits to a repository, you can squash your commits into one or more logical units of work, e.g. if
    you want to add a new feature solely in a single commit.
    * The [Pro Git book](https://git-scm.com/book/en/v2/) has a great section on [Rewriting 
    History](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) and a section 
    on [Squashing](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History#_squashing).
  * Rebase during pull (i.e. `git pull --rebase`) instead of merging so all commits can
    be signed off. You can also
    [configure git to rebase by default](https://stackoverflow.com/questions/13846300/how-to-make-git-pull-use-rebase-by-default-for-all-my-repositories)
    - you IDE will also have according configuration options. 
  * If you are not a committer to the project your commits need to be signed off with a valid Eclipse user account. Check the Eclipse handbook for details ([Eclipse Project Handbook](https://www.eclipse.org/projects/handbook/#resources-commit)).

If you checked your code according to the DoD and you feel it can be merged to master, please create a PR to master. 
Each PR that is merged to master has to pass all tests and needs a code review of some other person of the project that looks onto your contribution from another angle, 
i.e. didn't work with you on the new feature. Probably a good idea is to have someone from another organization doing the review.
Eclipse Kuksa Committers regularly scan the repositories for new Pull Requests.
 
## Review
If you conduct a code review, please look at the following issues:

  * Is code style ok, not really formatting, but issues like style attributes in HTML tags or exception handling useful
  * Are DoD items reached
  * Are there any design / architecture issues
  * Does the new feature fit the overall project goal, is it suitable for the community

## Manual Test
If applicable the new feature should at least be deployed and tested by someone before actually merged to master.
This could be done by the same person that is doing the review but could be performed by another person.

After review and tests are finished it should be documented who actually did the review and the test.
Use the GitHub review mechanism and give comment stating what you have done.

## Licensing and file header

All files contributed require headers - this will ensure the license and copyright clearing at the end.
Also, all contributions must have the same license as the original source.

Most Eclipse KUKSA repositories use the [Apache-2.0 ](https://www.apache.org/licenses/LICENSE-2.0) license.
A header like the one below shall be used.

```
/********************************************************************************
* Copyright (c) {year} Contributors to the Eclipse Foundation
*
* See the NOTICE file(s) distributed with this work for additional
* information regarding copyright ownership.
*
* This program and the accompanying materials are made available under the
* terms of the Apache License 2.0 which is available at
* http://www.apache.org/licenses/LICENSE-2.0
*
* SPDX-License-Identifier: Apache-2.0
********************************************************************************/
```
(please adapt comment characters usage)

## Eclipse Contributor Agreement

Before your contribution can be accepted by the project team contributors must
electronically sign the Eclipse Contributor Agreement (ECA).

* http://www.eclipse.org/legal/ECA.php

Commits that are provided by non-committers must have a Signed-off-by field in
the footer indicating that the author is aware of the terms by which the
contribution has been provided to the project. The non-committer must
additionally have an Eclipse Foundation account and must have a signed Eclipse
Contributor Agreement (ECA) on file.

For more information, please see the Eclipse Committer Handbook:
https://www.eclipse.org/projects/handbook/#resources-commit
