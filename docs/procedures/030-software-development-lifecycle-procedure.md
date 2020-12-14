---
id: software-development-lifecycle-procedure
title: Software development lifecycle procedure
description:
---

## Background

To be read in conjunction with the [software-development-lifecycle-policy].

## Objectives

- Summarise software development lifecycle (SDLC)
- Define agendas for meetings
- Define sub-procedures

## Scope

Meetings and sub-procedures used in the SDLC.

## Definitions

- **Definition of ready (DOR)** - a ticket is ready for development when it:
  - conforms with the relevant template e.g. [user-story-template], [spike-template] or [bug-template]
  - contains enough information to be understood by everyone in the team
  - has been split into tickets that can be completed within a sprint (look at estimates vs. historic velocity to help you judge this)
  - has relationships with other tickets defined (e.g. `blocked`, `relates to`, `implements` etc)
  - has been risk assessed and treated
- **Definition of done (DOD)** - a ticket is considered done when:
  - acceptance criteria are satisfied
  - code is checked into source control
  - code has been peer reviewed by pull request from feature/topic branch
  - code builds and passes all tests in continuous integration (CI)
  - it has been deployed and available in a staging environment
  - security checks pass

## Procedure

### Meetings
#### Stand up

| | |
| :- | :- |
| **Who** | All devs, Product Owner (PO), Scrum Master (SM) |
| **When** | Every day (except sprint planning day) |
| **How long** | 5 mins |
| **Why** | Identify impediments and create actions to remove them |
| **What** |
| *Inputs* | Up-to-date board (physical or electronic) |
| *Agenda* | No minutes |
|| Go round team and list impediments |
|| Where impediments exist the team should identify and select ways of removing them |
|| All other conversations should occur outside of standup |
| *Outputs* | Actions to remove impediments |

#### Sprint planning

| | |
| :- | :- |
| **Who** | All devs, PO, SM |
| **When** | Every other Wednesday |
| **How long** | As long as it takes |
| **Why** | Define a potentially shippable increment of work |
| **What** |  |
| *Inputs* | Sprint backlog has been populated during backlog refinement |
| *Agenda* | Nominate someone to drive and make notes in Jira tickets or Modify |
|   | If deemed more efficient, split into front- and back-end groups and go through the steps before regrouping to discuss unknowns and iterating through appropriate steps again |
| | Go through tickets, checking they meet the Definition of Ready (DOR) |
| | If a ticket does not meet the DOR and is not crucial to the sprint, record a comment explaining what needs to be done to get it ready, assign the relevant team member and remove from the sprint, placing it either in a future sprint or the product backlog. If a ticket does not meet the DOR and is crucial to the sprint, work together to get the ticket ready. |
| | Where possible, define relationships between tickets using links e.g. of type `blocks` or `implements`.  |
|   | Reject any tickets that have been superseded, duplicated or are outdated, setting their status to `Rejected` and adding a comment explaining the decision |
| | Once all tickets in the sprint backlog have been reviewed, estimate them using planning poker and fibonacci scores and ensure they are prioritised. |  
| | Review estimated velocity for the sprint against historical averages in [Team velocity](https://docs.google.com/spreadsheets/d/1X2J4thZQtudHXHy3O8W5hgoe4FsGGQt_ywxekL66MxQ/edit#gid=1958016801) to sense check and adjust scope |
| | Plan for any pair programming. |
| | Check everyone knows which ticket they plan to pick up first.|
| | Start the sprint in Jira. |
| *Outputs* | A prioritised sprint backlog that meets the DOR |

- The planning poker process is described [here](https://www.mountaingoatsoftware.com/agile/planning-poker)

#### Mid-sprint review

| | |
| :- | :- |
|**Attendees** |All devs, PO, SM |
| **When** | Middle Wednesday of sprint |
| **How long** | Up to 1 hour |
| **Why** | To evaluate progress of the sprint, and add or remove stories where necessary |
| **What** | Nominate someone to drive and make notes in Jira tickets or Modify |
| | Go through any open impediments - if they can't be solved within 5 mins, plan for them to be unblocked outside of the meeting |
| | Using the burndown for context, ask the question: Given the resources available, will we complete the work we have planned? Dependent on the answer, add or remove stories. |
| | Once the new scope is agreed, team members must be transparent about further scope changes before sprint end. |

- As a rule of thumb, if a new ticket needs to be added, an "equivalent" ticket should be removed (equivalence will require judgement for unestimated tickets such as spikes), a comment added to the ticket and a message posted to the relevant slack channel.
- Sometimes there will be good reason to ignore this rule of thumb e.g. when the team's output is greater than expected. The team will need to use its judgement to determine when this is justified.

#### Backlog refinement

| | |
| :- | :- |
| **Attendees** | PO, SM, 2-3 devs |
| **When** | Middle Wednesday of sprint |
| **How long** | 1 hour |
| **Why** | To ensure the backlog is kept in order, improve the quality of tickets so they meet the DOR and add triage status labels |
| **What** | Nominate someone to drive and make notes in Jira tickets or Modify
| | Go through tickets in the sprint lined up next and/or backlog in priority and risk order. Use the DOR to determine if a story is ready or not |
| | Once a ticket has been reviewed, add the label `triaged` so it is clear to all team members it does not need to be reviewed again |
| | If a ticket is old, out of date, no longer necessary or relevant, change its status to `Rejected` |
| | Create action items where needed and assign a team member if relevant |

#### Sprint showcase

| | |
| :- | :- |
| **Attendees** | All devs, PO, SM |
| **When** | Last Tuesday of sprint, before the retrospective. |
| **How long** | Up to 1 hour |
| **Why** | Demo progress made during the sprint to the team |
| **What** | Nominate someone to make notes in Modify |
| | Take it in turns to demo work from the sprint and discuss with the team |

#### Sprint retrospective

| | |
| :- | :- |
| **Attendees** | All devs, PO, SM |
| **When** | Last Tuesday of sprint (PM) |
| **How long** | 30 mins |
| **Why** | Reflect on and evaluate how the sprint went, identify opportunities for improvement and review status of actions from last retro |
| **What** | Nominate someone to facilitate and make notes in Modify |
|   | Review actions from the last retrospective |
| | Everyone writes post-its for positives and negatives (e.g. challenges, annoyances, mistakes).
| | Everyone reads out their own positive post-its and places them on the whiteboard. This is repeated for negative post-its.
| | Focusing on negative post-its only, everyone assigns two votes to the issue(s) they consider most important (no discussion at this stage). People can vote for their own issue(s) and for the same issue twice. Once votes have been cast, post-its are ranked. |
| | Focusing on issues with 1 or more votes, the moderator reformulates issues into a 'How might we...' (HMW) statement designed to describe a goal for any solutions. |
| | Everyone has 5 mins to write down as many ways of solving the HMW challenge as they can - without discussion! After 5 mins everyone places their post-its on the board.|
| | Everyone reads proposed solutions (again, no discussion) and votes for their top 6 (the same voting rules apply). |
| | Ignore anything with less than 2 votes and rank solutions. |
| | Use an impact/effort grid (effort = horizontal axis, impact = vertical axis) to determine which solutions to action first. The moderator holds each solution in the centre of the grid and asks where it should be placed for effort and impact. |
| | Any post-its in the top left of the grid (low effort, high impact) are highlighted and turned into tasks that should be actioned within 1-2 weeks. |
|  | If there are no solutions in this region of the grid, either reconsider estimates or pick up the nearest 1 or 2 post-its and create tasks.|

### Quarterly retrospective

| | |
| :- | :- |
| **Attendees** | Everyone |
| **When** | Last Monday of each quarter |
| **How long** | 1 hour |
| **Why** | Review progress against quarterly objectives and key results (OKRs) |
| **What** |  |
| *Inputs* | Quarterly OKRs & data for measuring progress |
| *Agenda* | Nominate someone to take notes in Modify |
|   | Measure progress against quarterly OKRs |
| | Follow `Sprint retrospective` agenda |
| | Consider OKRs for upcoming quarters & suggest changes |
| | Create actions and assign |
| *Follow up* | Update OKRs register |
|   | Management to review suggested changes and tweak OKRs as needed |

- Quarterly and annual OKRs can be set using [this agenda](https://drive.google.com/open?id=1QsckOsKdzF9zR-zj1AVh5lpUsmoZYOKJ).

### Annual retrospective

| | |
| :- | :- |
| **Attendees** | Everyone |
| **When** | Third Friday in December |
| **How long** | 1 hour |
| **Why** | Review progress in the year against annual OKRs |
| **What** |  |
| *Inputs* | Annual OKRs & data for measuring progress |
| *Agenda* | Nominate someone to take notes in Modify |
| | Follow `Sprint retrospective` agenda |
| | Review action items and assign |
| | Create actions and assign |
| *Follow up* | Update OKRs register |

### Sub-procedures
<Link to="iso27001/A.14.2.2" kind="implements" />

#### Changes to source code
##### Existing projects

For projects with an established workflow:
- Place any changes in a branch off current `develop`
  - Use branch naming: `feature/<JIRA-ISSUE>`, `hotfix/<JIRA-ISSUE>`, `release/<NAME>`
- Push branch to remote for back up regularly
- To start the review process open a Pull Request, nominating reviewers
  - Ensure a Jira ticket is linked by mentioning it in either the PR title or branch name
  - Reviewers check for various best practices, adequate tests, passing CI builds
- Amend PR and branch with feedback from review, re-arranging commits if required
- Merge or Fast Forward PR into `develop` after agreement from reviewers
- Tidy up merged and unused branches

##### New projects

When starting new projects:
- Place changes directly on `develop`
- Configure version control, CI and deployment
  - Setup branch protection to prevent force pushes
  - Require Pull Requests with successful builds to merge
- Request review for the whole repo, CI, and deployment process
- Implement feedback from reviewers
- Switch to established workflow for further development

#### Releases

Releases are discussed, planned and approved during `Sprint planning` and implemented using the following procedure:

- A release branch is created from latest development branch for all repositories that contribute to the release
  - Name release branches as `release/<NAME>`
- Release branches are built and tested to check for problems
- Any major bug fixes are performed on a separate branch, and changes are merged back onto the release branch by PR
  - Name release feature branches as `release/<NAME>/<JIRA-ISSUE>`
- If following testing the branch is considered ready for release a release candidate is created
  - Tag created on branch `<NAME>-rc<VERSION>`
- Release candidates have accompanying release notes written in Modify and linked to appropriate tickets, commits and PRs
- All release candidate builds are performed in an isolated production environment
- All software built from a release candidate is deployed to a pre-production environment for release validation
- Any external validation is performed on the release candidate in the pre-production environment
- If a release candidate is considered unacceptable then further iterations are required
  - Perform further work on the release branch and create a new release candidate
- If a release is abandoned then the release branch may be merged back into `develop` by PR and stopped.
- If the release candidate is acceptable, it is tagged and merged into master by PR
  - Name release tag as `<NAME>`
- Release branches are merged back into develop by PR.

#### Production deployment

Deployments are discussed, planned and approved during `Sprint planning`.

When a release or release candidate is tagged in source control for an application, the production CI system automatically:
- Checks out, tests and builds the code in the production build environment
- Packages build artifacts into production docker container(s)
- Pushes container(s) to the production docker registry and tags with the release version and `latest`
- Deploys the container to a pre-production environment for release validation

Once approved, the system administrator manually triggers the production deploy job on a scheduled date, which:
  - Updates deployment configuration for each service to use new containers
  - Uses a rolling update deployment method
