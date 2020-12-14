---
id: document-management-policy
title: Document management policy
description: Policy describing how we organise and manage docs.
---

## Background
<Link artifactId="iso27001/7.5.1" kind="implements" />

Policies, procedures and records are documented and managed in a way that meets the requirements of both the information security management system (ISMS) and our preferred working practices.

## Objectives

- Define managed document
- Define management approach
- Define document hierarchy
- Describe lifecycle

## Scope

This policy covers all managed documents in scope of the ISMS.

## Definitions

- **Managed document** - a document that has a managed lifecycle. It is a type of **managed artifact** (see [artifact-management-policy]).
- **Policy** - the intention and direction of the organisation as formally expressed by management.
- **Procedure** - a detailed set of instructions for executing a process.
- **Record** - a record of the execution of a procedure.
- **External managed document** - a document produced by an external stakeholder (e.g. a cloud provider) that has a managed lifecycle.

## Policy

### Approach
<Link artifactId=="iso27001/7.5.2, iso27001/7.5.3" kind="implements" />

Modify is used to manage documents throughout their lifecycle using a [docs-as-code](https://www.writethedocs.org/guide/docs-as-code/) approach. 

Managed documents are written in GitHub Flavoured Markdown ([GFM](https://github.github.com/gfm/)) and [MDX](https://mdxjs.com/)  for portability, formatting consistency and suitability for version control (Git).

Markdown files are augmented with YAML front matter to improve computability:

```yaml
---
id: document-management-policy
title: Document management policy
description: Policy describing how we organise and manage docs.
---
```

Markdown/MDX files are stored in Git repositories, which provide the version control features needed for audit. Git hosting is provided by approved suppliers.

Modify is used for collaboration and review. Changes to managed documents require review in Modify by a named approver before being merged into the live branch.

Access controls are enabled. The Security, Privacy and Compliance Officers are given read and write access to the repository. All other staff are given read-only access.

New managed documents can be created from templates stored in the [template-index]. They include standard front matter and sections, which can be adapted as necessary.

### Hierarchy

The managed document hierarchy consists of 3 levels:

```
.
└── policy
    └── procedure
        └── record
```

This is a simplified view. There is also a policy hierarchy. The [information-security-policy] is the ISMS root policy and applies to all other policies (as well as procedures and records). A number of policies sit below this that describe controls that apply to a number of lower-level policies.

```
.
└── information security policy
    ├── artifact management policy
    ├── document management policy
    ├── software development lifecycle policy
    ├── risk management policy
    └── change management policy
        ├── access control policy
        └── other policies
```

Generally, policies have at least one related procedure, and procedures at least one related record. However, this need not be the case.

### Lifecycle
<Link artifactId=="iso27001/7.5.3, iso27001/A.5.1.2" kind="implements" />

Managed document lifecycles are the same as managed artifact lifecyles (see [artifact-management-policy]) and are controlled with the [change-control-sop].

Documents are published to a website with authentication controls for staff to view.

Publication details are automatically communicated to team members through integrations between version control and messaging tools. Additionally, the Security and Privacy Officers may communicate changes to affected employees directly.

All policies and procedures are reviewed at least annually, and on ad-hoc basis as they are used and reviewed as part of the team's regular working cadence.

Managed documents are retained in line with the handling rules for their information classification (see the [artifact-management-policy]).

### External documents
<Link artifactId=="iso27001/7.5.3 kind="implements" />

These can be added to the document management system by allocating internal identifiers and managing their lifecycles. As the content changes externally and an active decision will need to be made to integrate external changes and update the artifact.

This provides a way to fix the version of external documents and artifacts that do not have good semantic labelling and strong versioning.
