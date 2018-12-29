---
kep-number: 34
title: Recursive directory structure for configmaps and secrets
authors:
  - "@zhouhaibing089"
owning-sig: sig-apps
participating-sigs:
  - sig-apps
  - sig-api-machinery
reviewers:
  - TBD
approvers:
  - TBD
editor: TBD
creation-date: 2018-12-28
last-updated: 2018-12-28
status: provisional
see-also:
replaces:
superseded-by:
---

# Recursive Directory Structure for Configmaps and Secrets

## Table of Contents

A table of contents is helpful for quickly jumping to sections of a KEP and for highlighting any additional information provided beyond the standard KEP template.
[Tools for generating][] a table of contents from markdown are available.

* [Table of Contents](#table-of-contents)
* [Summary](#summary)
* [Motivation](#motivation)
    * [Goals](#goals)
* [Proposal](#proposal)
    * [User Stories [optional]](#user-stories-optional)
      * [Story 1](#story-1)
      * [Story 2](#story-2)
    * [Implementation Details/Notes/Constraints [optional]](#implementation-detailsnotesconstraints-optional)
    * [Risks and Mitigations](#risks-and-mitigations)
* [Graduation Criteria](#graduation-criteria)
* [Implementation History](#implementation-history)
* [Drawbacks [optional]](#drawbacks-optional)
* [Alternatives [optional]](#alternatives-optional)

[Tools for generating]: https://github.com/ekalinin/github-markdown-toc

## Summary

We propose adding support to build configmaps/secrets from recursive directories
and make them consumable from pods.

## Motivation

Pods generally mount configurations from configmaps or secrets, however it is not
easy to setup a pod which requires configurations from one directory and its
subdirectories recursively. For example, [62641][] mentioned a case where a java
application needs configurations like this but hard to setup today.

```
conf/
└── integrator
    └── conf
        ├── axis2
        │   └── axis2.xml
        ├── carbon.xml
        ├── datasources
        │   └── master-datasources.xml
        ├── registry.xml
        └── user-mgt.xml
```

[62641]: https://github.com/kubernetes/kubernetes/issues/62421

### Goals

1. Make it easy for user to create configmaps or secrets from directory and its
subdirectories recursively.
1. Pods can mount a single configmap or secret to setup files across subdirectories.

## Proposal

This is where we get down to the nitty gritty of what the proposal actually is.

### User Stories [optional]

Detail the things that people will be able to do if this KEP is implemented.
Include as much detail as possible so that people can understand the "how" of the system.
The goal here is to make this feel real for users without getting bogged down.

#### Story 1

#### Story 2

### Implementation Details/Notes/Constraints [optional]

What are the caveats to the implementation?
What are some important details that didn't come across above.
Go in to as much detail as necessary here.
This might be a good place to talk about core concepts and how they releate.

### Risks and Mitigations

What are the risks of this proposal and how do we mitigate.
Think broadly.
For example, consider both security and how this will impact the larger kubernetes ecosystem.

## Graduation Criteria

How will we know that this has succeeded?
Gathering user feedback is crucial for building high quality experiences and SIGs have the important responsibility of setting milestones for stability and completeness.
Hopefully the content previously contained in [umbrella issues][] will be tracked in the `Graduation Criteria` section.

[umbrella issues]: https://github.com/kubernetes/kubernetes/issues/42752

## Implementation History

Major milestones in the life cycle of a KEP should be tracked in `Implementation History`.
Major milestones might include

- the `Summary` and `Motivation` sections being merged signaling SIG acceptance
- the `Proposal` section being merged signaling agreement on a proposed design
- the date implementation started
- the first Kubernetes release where an initial version of the KEP was available
- the version of Kubernetes where the KEP graduated to general availability
- when the KEP was retired or superseded

## Drawbacks [optional]

Why should this KEP _not_ be implemented.

## Alternatives [optional]

Similar to the `Drawbacks` section the `Alternatives` section is used to highlight and record other possible approaches to delivering the value proposed by a KEP.

## Infrastructure Needed [optional]

Use this section if you need things from the project/SIG.
Examples include a new subproject, repos requested, github details.
Listing these here allows a SIG to get the process for these resources started right away.
