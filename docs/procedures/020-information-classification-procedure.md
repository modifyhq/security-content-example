---
id: information-classification-procedure
title: Information classification procedure
description: 
---

## Background

To be read in conjunction with the [artifact-management-policy].

## Objectives

- Define procedure for classifying new or existing information

## Scope

All managed artifacts in scope of the ISMS.

## Procedure
<Link artifactId="iso27001/A.8.2.1" kind="implements" />

Information shall be classified into one of four classes:
- Public
- Internal
- Confidential
- Restricted.

Definitions for each class can be found in the [artifact-management-policy]

This is done by asking the following questions and recording the answers.

| Question | Classification if answer is "Yes" |
| :- | :- |
| **Customer data** | |
| Is the information stored on behalf of a customer? | Restricted |
| **Personal data** | |
| Does the personal data contain special categories of personal data as defined by [Article 9 GDPR](https://gdpr-info.eu/art-9-gdpr/)? | Restricted |
| Does the data contain only non-special categories of personal data? | Confidential |
| **Credentials, keys, secrets** | |
| Is the information credentials, keys or secrets used in a production system? | Restricted |
| Is the information credentials, keys or secrets used in a staging system that contains production data? | Restricted |
| Is the information credentials, keys or secrets used in a development or staging system that contains test data? | Confidential |
| **Public data** | |
| Can the information be made public without damaging the company in any way? | Public |
| **Internal data** | |
| Can the information be made available to all employees and approved non-employees without damaging the company in any way? | Internal |
| If none of the questions above has been answered "Yes", then this further question should be answered - Can this data be safely marked as Internal with limited damage to the company? | Internal |
