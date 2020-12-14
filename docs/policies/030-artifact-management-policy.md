---
id: artifact-management-policy
title: Artifact management policy
description: 
---

## Background

Artifacts store information of value like customer data. How we classify and handle these artifacts forms the foundation of the information security management system (ISMS).

## Objectives

- Define managed artifacts
- Define classification and handling rules
- Define the lifecycle of managed artifacts

## Scope

All managed artifacts in scope of the ISMS.

## Definitions

- **Artifact** - a digital or physical object that stores information and has a value. Also commonly called an `asset`.
- **Managed artifact** - a digital or physical object that has a managed lifecycle.
- **Proxy artifact** - a digital register entry for a managed artifact.
- **Managed artifact register** - a digital list of proxy artifacts.

## Policy

### Managed artifacts

An artifact is considered a managed artifact if it has a lifecycle managed by the policies and procedures of the ISMS.

A managed artifact will usually have a proxy artifact created in the [managed-artifact-register], whether it is a digital or physical artifact.

An artifact that is not managed is outside the scope of the ISMS.

### Managed artifact types

#### Data files

The following data files may be managed artifacts:

- Text files:
  - Plain text, Markdown, Restructured Text files, etc
  - JSON
  - YAML
- Binary files:
  - Google Docs and Sheets
  - Microsoft Office (Word, Excel, PowerPoint) files
  - PDF files
  - File-based databases, e.g. Microsoft Access databases, H2 databases
  - Encrypted files
  - Application files (compiled source code)
- Image files:
  - Bitmap images (png, jpeg, etc)
  - Sketch files
  - Illustrator files
- Source files:
  - Code files (in various languages)
  - Process description and code files (BPMN, PlantUML, XML, etc)
- Cloud files:
  - AWS S3 files with versioning enabled

#### Proxy artifacts

Entries in a register used as proxies for an underlying managed artifact.

Proxy artifacts and underlying managed artifacts have separate lifecycles. Whilst the proxy artifact must reflect the underlying managed artifact, it need not be in the same lifecycle state. 

#### Physical artifacts

The following physical artifacts may be managed artifacts:

- Computer hardware
- Mobile devices
- Alarm systems
- Keys
- Physical access fobs

### Managed artifact register
<Link artifactId="iso27001/A.8.1.1" kind="implements" />

The [managed-artifact-register] lists register entries for all managed artifacts within scope of the ISMS. 

Each entry has the following fields:

- `id`
- `title`
- `description`
- `type`
- `lifecycle state`
- `info classification`
- `personal data`
- `value`
- `owner`

The register must be stored in a repository that has:

- *Access control* - access is limited only to those users that require access, ideally by role.
- *Version control* - artifacts are versioned, subject to change control and can be reverted easily.

The register and its entries are reviewed at least annually.

### Lifecycle

Digital artifacts and proxy artifacts have a lifecycle with the following states:

- **New** - A new or existing artifact is identified as requiring lifecycle management and is added to the [managed-artifact-register]. Prior to approval, the artifact should be marked as _new_, indicating that an entry has been made for the artifact. 
- **Draft** - When changes are made to an _active_ managed artifact, a new _draft_ revision should be created.
- **Active** - A _draft_ artifact that has been reviewed and approved is marked as _active_. 
- **Deprecated** - An _active_ artifact can be marked as _deprecated_ once it is no longer needed or actively maintained. It is retained in the [managed-artifact-register] for audit purposes.
- **Deleted** - An artifact in any state can be marked as _deleted_ following review and approval. The reason for deletion must be recorded in the [managed-artifact-register], even if the content of the artifact is removed. Legitimate reasons include _entered-in-error_, _no-longer-needed_.

Physical artifacts have a lifecycle that is managed in line with the Hardware management policy.

### Classification
<Link artifactId="iso27001/A.8.2.1, iso27001/A.8.2.2" kind="implements" />

Managed artifacts store information. Handling rules for an artifact are based on the classification of this information.

The [information-classification-procedure] outlines the process used to determine the classification of an artifact. Managed artifacts must be classified into one of four classes: Public, Internal, Confidential or Restricted (see [artifact-management-policy/#appendix-a]).

Physical artifacts have physical labels with classifications applied:

- Hardware is labelled with barcoded artifact tags
- Paper is labelled with Public or Internal (it is not permitted to store Confidential or Restricted information in paper unless an exception has been approved by the Security Officer).

Where a managed artifact stores information classified in more than one way, it should be handled on the basis of the information with the highest classification.

### Owners
<Link artifactId="iso27001/A.8.1.2 kind="implements" />

Managed artifacts are assigned owners. Managed artifact owners must:

- Be senior or responsible individuals
- Classify information stored in artifacts
- Control access permissions to artifacts
- Be involved in change control on artifacts
- Keep their understanding of the artifact and its use current

Additionally, managed artifact owners should also:

- Collaborate closely with the Privacy and Security Officers

## Appendix A
<Link artifactId="iso27001/A.8.2.3" kind="implements" />

<table border="1" class="docutils" id="id9">
  <caption>
    <span class="caption-text">Information Classification schema</span
    ><a class="headerlink" href="#id9" title="Permalink to this table"></a>
  </caption>
  <colgroup>
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
  </colgroup>
  <thead valign="bottom">
    <tr class="row-odd">
      <th class="head">&nbsp;</th>
      <th class="head">Public</th>
      <th class="head">Internal</th>
      <th class="head">Confidential</th>
      <th class="head">Restricted</th>
    </tr>
  </thead>
  <tbody valign="top">
    <tr class="row-even">
      <td><strong>Description</strong></td>
      <td>Non-sensitive information available for external release</td>
      <td>
        Information that is sensitive only outside the company, generally
        available to employees and approved non-employees
      </td>
      <td>
        Information that is sensitive within the company, and is intended for
        business use only by specific groups of employees
      </td>
      <td>
        Information that is extremely sensitive, of highest value to the company
        and intended for use by named individual(s) only
      </td>
    </tr>
    <tr class="row-odd">
      <td><strong>Examples</strong></td>
      <td>Advertising literature once issued</td>
      <td>ISMS policies and procedures</td>
      <td>Customer information, personnel information</td>
    </tr>
    <tr class="row-even">
      <td>
        <strong>Confidentiality requirements</strong>
      </td>
      <td>Accessible to all employees</td>
      <td>
        Access normally restricted to employees and approved non-employees for
        business purposes only
      </td>
      <td>
        Access must be granted only on a business need to know. Access by
        external parties must be subject to a non-disclosure agreement as well
        as a business need to know
      </td>
      <td>
        Access must be limited to named authorised individuals, access lists
        maintained, access by external parties must be subject to a
        non-disclosure agreement as well as a business need to know
      </td>
    </tr>
    <tr class="row-odd">
      <td><strong>Impact of unauthorised disclosure</strong></td>
      <td>Very low</td>
      <td>Low</td>
      <td>Medium</td>
      <td>High</td>
    </tr>
    <tr class="row-even">
      <td><strong>Integrity requirements</strong></td>
      <td>&lt;90% Error Free</td>
      <td>90-95% Error Free</td>
      <td>96-99% Error Free</td>
      <td>100% Error Free</td>
    </tr>
    <tr class="row-odd">
      <td><strong>Impact of unauthorised modification</strong></td>
      <td>Very low</td>
      <td>Low</td>
      <td>Medium</td>
      <td>High</td>
    </tr>
    <tr class="row-even">
      <td>
        <strong>Availability requirement</strong>
      </td>
      <td>No interruption of access beyond 7 days</td>
      <td>No interruption of access beyond 1 day</td>
      <td>No interruption of access beyond 0.5 day</td>
      <td>No interruption of access</td>
    </tr>
    <tr class="row-odd">
      <td><strong>Impact of service disruption</strong></td>
      <td>Very low</td>
      <td>Low</td>
      <td>Medium</td>
      <td>High</td>
    </tr>
    <tr class="row-even">
      <td>
        <strong>Access controls</strong>
      </td>
      <td>None</td>
      <td>Basic</td>
      <td>Strict</td>
      <td>Strict</td>
    </tr>
    <tr class="row-odd">
      <td>
        <strong>Storage controls</strong>
      </td>
      <td>None</td>
      <td>Encryption may be required</td>
      <td>Encryption required</td>
      <td>Encryption required</td>
    </tr>
    <tr class="row-even">
      <td>
        <strong>Transmission controls</strong>
      </td>
      <td>None</td>
      <td>Encryption may be required</td>
      <td>Encryption required</td>
      <td>Encryption required</td>
    </tr>
    <tr class="row-odd">
      <td>
        <strong>Labelling</strong>
      </td>
      <td>Label required (digital or physical)</td>
      <td>Label required (digital or physical)</td>
      <td>Label required (digital)</td>
      <td>Label required (digital)</td>
    </tr>
    <tr class="row-even">
      <td>
        <strong>Disposal</strong>
      </td>
      <td>Removal of directory entry for file</td>
      <td>Removal of directory entry for file</td>
      <td>Secure disposal required</td>
      <td>Secure disposal required</td>
    </tr>
    <tr class="row-even">
      <td>
        <strong>Retention</strong>
      </td>
      <td>Indefinitely</td>
      <td>Indefinitely</td>
      <td>Indefinitely</td>
      <td>Customer data: 30 days from contract termination, Employee personal data: 7 years from contract termination</td>
    </tr>
  </tbody>
</table>
