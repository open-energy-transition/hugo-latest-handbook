---

title: AI Framework Group
description: "The AI Framework gruop is focused on how to support other product groups at GitLab with the AI Abstraction Layer, and GitLab Duo Chat functionality."
---







## Vision

The AI Framework group is focused on how to support other product groups at GitLab with the AI Abstraction Layer, and GitLab Duo Chat functionality.

### 👌 Team OKRs

If you're interested in the team's Objectives and Key Results (OKRs), you can find them on [GitLab](https://gitlab.com/gitlab-com/gitlab-OKRs/-/issues/?sort=title_asc&state=opened&label_name%5B%5D=group%3A%3Aai%20framework&first_page_size=20).

### 🚀 Team Members

**Engineering Manager & Engineers**

<%= direct_team(manager_slug: 'davidoregan') %>

**Product, Design & Quality**

<%= stable_counterparts(role_regexp: /AI Framework/, direct_manager_role: 'Engineering Manager, AI Framework') %>

**Team members who are supporting this team on a short-term basis are located [here](https://comp-calculator.gitlab.net/org_chart) where "Work priorities" include "AI Framework."**

### ☕ Team Responsibilities

**Team responsibilities include**

* Facilitating the integration of AI capabilities throughout GitLab by leveraging the AI Abstraction Layer and AI Gateway.
* Guaranteeing the presence of comprehensive global observability, monitoring, documentation, and enhancements in latency.
* Providing essential support for our AI chat system framework.
* Incorporating support for new AI providers when required.
* Assisting with the production support and ensuring the readiness of the AI Gateway.

### ☎️ How to reach us

Depending on the context here are the most appropriate ways to reach out to the IDE Group:

- Slack Channel: [`#g_ai_framework`][slack]
- Slack Groups: `@ai-framework` (entire team) and `@ai-framework-engs` (just engineers)

## 📦 Team Processes

### 📆 Regular team meetings

**❗️Important**: For every meeting, the [AI Framework team's meeting document][gdoc] should be used, and filled with the meeting notes, as well as references to any other sync meeting agendas/notes/recordings which have recently occurred. This will make it easier for people to find any meeting notes.

#### Office Hours

- When: [Biweekly](https://docs.google.com/document/d/1Zy2behLK2dYq8QV3x0vFNs5QtY_Z6L9ObU8tzeJWWZw/edit#heading=h.onbz64sai6dd) (for specific time, refer to the GitLab Team Meetings calendar)
- What: This meeting is an opportunity for team members to ask questions about AI features, especially the abstraction layer and GitLab Duo chat, seek support for ongoing experiments, or learn how to write good prompts. If there are no topics to discuss, the meeting may not be held. Recordings from previous sessions can be found in this GitLab Unfiltered YouTube [playlist](https://www.youtube.com/playlist?list=PL05JrBw4t0Kpt0DsmS5WSZbeiMgrBeZXv).

#### Main team meeting

- **When:** Every Tuesday at 14:00 UTC (EMEA/AMEA friendly)
- **What:** This meeting operates on an open agenda. If there are no topics to discuss, the meeting will be cancelled. This meeting provides an opportunity for team members to engage in informal discussions and share updates.

#### Short sync meeting

- **When:** Every Thusday at 9:30 UTC (APAC/EMEA friendly)
- **What:** This meeting also operates on an open agenda. If there are no topics to discuss, the meeting will be cancelled. This meeting serves as a platform for team members to catch up, share quick updates, and engage in brief discussions.

### Shared calendars

- AI Framework PTO (Calendar ID: `c_eca9440729dba2cbd88b3117fa70839836fb5811cb072132b94c52f912a31bf5@group.calendar.google.com`)
- AI-Powered Stage Calendar (Calendar ID: `c_n5pdr2i2i5bjhs8aopahcjtn84@group.calendar.google.com`)

AI Framework team members should [sync your PTO events](https://handbook.gitlab.com/handbook/people-group/engineering/team-pto-calendar/) with AI Framework PTO calendar.

### 🖖 Weekly EM Updates

Each week the team EM provides a Weekly Status update issue which aims to capture the most important items for the team to be aware of. These can be found [here](https://gitlab.com/gitlab-org/ai-powered/ai-framework/team-hq/-/issues/?sort=title_asc&state=opened&label_name%5B%5D=Weekly%20Announcements&first_page_size=20).

### 📄 Milestone Planning

Every month, we create a Milestone Planning issue that serves as the single source of truth (SSoT) for the current milestone.

This issue provides us with a centralized location to discuss our upcoming milestone work, plan for feature, bug, and maintenance tasks, and provides us with the necessary flexibility to iterate mid-milestone if required.

You can find all milestone planning issues in the [AI Framework team’s project](https://gitlab.com/gitlab-org/ai-powered/ai-framework/team-hq/-/issues/?sort=title_asc&state=opened&label_name%5B%5D=Planning%20Issue&first_page_size=20).

The layout for these Milestone issues are automated and can be found [here](https://gitlab.com/gitlab-org/ai-powered/ai-framework/team-hq/-/blob/main/.gitlab/issue_templates/planning_issue.md).

Additionaly, you can filter by:

- To find the issues you're currently working on, change the filter to `Assignee=<your-handle-name>`.
- To find a new issue that you will work on, change the filter to `Assignee=None` (And assign yourself to the issue to prevent other people from working on it).

### 📚 AI Framework Board Outline

Our workflow process for our [board](https://gitlab.com/gitlab-org/gitlab/-/boards/5518200?label_name[]=group%3A%3Aai%20framework) is outlined below.

1. **Open** 📝: This list contains all identified issues. An engineering manager will be assigned if either the Milestone or the label "workflow::ready for development" is missing.
2. **workflow::ready for development** 🎯: Issues that have been prioritized and assigned to a specific milestone are moved to this list and the "ready for development" label is applied.
3. **workflow::in dev** 👩‍💻: When a developer starts working on an issue, they should move it to this list and apply the "in dev" label.
4. **workflow::in review** 👀: Once the development work on an issue is complete, it should be moved to this list and the "in review" label should be applied.
5. **workflow::verification** ✅: After the code and UX review is complete, the issue should be moved to this list and the "verification" label should be applied.
6. **workflow::complete** 🎉: Once the issue has been verified and everything is working, it should be moved to this list, the "complete" label should be applied, and the issue should be closed.

### 🔄 Processes

#### Weekly 🗓️

1. **Issue Review** 🕵️‍♂️: (DRI: Engineering Manager and Product Manager) Review all the issues in the Open list. Prioritize them based on their importance, urgency, and input from development EM, Quality, and UX. Move the top priority issues to the "workflow::ready for development" list.
2. **Progress Check** 🔄: (DRI: Assigned Developer) Check the "workflow::in dev" list to see the status of the ongoing tasks. If a task has been in progress for too long, find out why and try to resolve any blockers.
3. **Review Completed Tasks** 👥: (DRI: Assigned Developer and Reviewer) Review the tasks in the "workflow::in review" list. Test them to ensure they've been completed correctly. If they pass the review, move them to the "workflow::verification" list.

#### Monthly 📅

1. **Board Cleanup** 🧹: (DRI: Engineering Manager, Product Manager) On the last day of each milestone (e.g., for milestone 16.7, this would be December 15, 2023), clean up the board. Close all the issues in the "workflow::complete" list. Archive any issues in the "Open" list that are no longer relevant.
2. **Milestone Planning** 🗓️: (DRI: Product Manager) 19 days before the next milestone begins (e.g., for milestone 16.8, this would be November 27, 2023), plan for the next milestone. Identify the tasks that need to be completed in the next month and move them to the "workflow::ready for development" list. This
3. **Performance Review** 📈: (DRI: Engineering Manager, Product Manager) On the third Friday of the month (e.g., for milestone 16.7, this would be December 15, 2023, the day after the release date), review the team's performance. See how many issues were completed in the past month and how many are still in progress. Use this information to improve your planning and workflow.

#### Milestone Running Dates 2023 - 2024 📅

| Milestone | Start Date | End Date |
|-----------|------------|----------|
| 16.7 | Nov 11, 2023 | Dec 15, 2023 |
| 16.8 | Dec 16, 2023 | Jan 19, 2024 |
| 16.9 | Jan 20, 2024 | Feb 16, 2024 |
| 16.10 | Feb 17, 2024 | Mar 15, 2024 |
| 16.11 | Mar 16, 2024 | Apr 19, 2024 |
| 16.12 | Apr 20, 2024 | May 17, 2024 |
| 17.0 | May 18, 2024 | Jun 21, 2024 |
| 17.1 | Jun 22, 2024 | Jul 19, 2024 |
| 17.2 | Jul 20, 2024 | Aug 16, 2024 |
| 17.3 | Aug 17, 2024 | Sep 20, 2024 |
| 17.4 | Sep 21, 2024 | Oct 18, 2024 |
| 17.5 | Oct 19, 2024 | Nov 15, 2024 |

### 📝 Issue Guidelines

These guidelines apply to all issues we use for planning and scheduling work within our group. Our Engineers can define specific implementation issues when needed, but the overall goal for our issues are as follows:

- Provide a meaningful **title** that describes a deliverable result.
    - ✅ `Add the new GitLab Duo chat package as a Vue2 extension`
    - ✅ `Chat: move away from using OpenAI embeddings`
    - ❌ `Make Chat better`
- Provide a meaningful description that clearly explains the goal of the issue, and provide some technical details if necessary.
- Should there be critical implementation steps or other useful ways to create small tasks as part of the issue, please use a checklist as part of the issue descriptions.
- The issue should have a weight, milestone and workflow label assigned.

It's okay to create specific engineering-driven implementation issues for more complex features. These would be called **Child Issues** and they should always link back to their parent. If one issue would spawn many child issues, consider creating an Epic.

## 👏 Communication

The AI Framework Team communicates based on the following guidelines:

1. Always prefer async communication over sync meetings.
1. Don't shy away from arranging a [sync call](#-ad-hoc-sync-calls) when async is proving inefficient, however always record it to share with team members.
1. By default communicate in the open.
1. All work-related communication in Slack happens in the [#g_ai_framework][slack] channel.

### ⏲ Time Off

Team members should add any [planned time off][paid-time-off] in the "Time Off by Deel" slack app, so that the Engineering Manager can use the proper number of days off during capacity planning.

### 🤙 Ad-hoc sync calls

We operate using async communication by default. There are times when a sync discussion can be beneficial and we encourage team members to schedule sync calls with the required team members as needed.

## 🔗 Other Useful Links

### 📝 Dashboards (internal only)

- [All Usage](https://app.periscopedata.com/app/gitlab/1137231/Ai-Features)
- [Requests per provider](https://thanos-query.ops.gitlab.net/graph?g0.expr=sum%20by%20(client)(rate(gitlab_sli_llm_client_request_total%7Benv%3D%22gprd%22%7D%5B1m%5D))&g0.tab=0&g0.stacked=0&g0.range_input=1w&g0.max_source_resolution=0s&g0.deduplicate=1&g0.partial_response=0&g0.store_matches=%5B%5D&g0.step_input=60)
- [Error budgets](https://dashboards.gitlab.net/d/product-ai-powered_error_budget/product-error-budgets-ai-powered?orgId=1)
- [AI Gateway SLIs](https://dashboards.gitlab.net/d/ai-gateway-main/ai-gateway-overview?orgId=1)
- [GCP quota limits](https://dashboards.gitlab.net/d/ai-gateway-main/ai-gateway-overview?orgId=1&viewPanel=1515902021)
- [LLM Sidekiq completions](https://dashboards.gitlab.net/d/sidekiq-main/sidekiq-overview?orgId=1)
- [Duo Chat Question Categorization](https://app.periscopedata.com/app/gitlab/1173299/Duo-Chat-Question-Categorization)
- [Security Issues](https://gitlab.com/groups/gitlab-org/-/issues/?sort=due_date&state=opened&label_name%5B%5D=security&label_name%5B%5D=group%3A%3Aai%20framework&first_page_size=20)
- [Reliability Issues](https://gitlab.com/gitlab-org/gitlab/-/boards/4227439?not[label_name][]=type%3A%3Afeature&label_name[]=section%3A%3Adev&label_name[]=group%3A%3Aai%20framework)
- [Sentry via CompletionWorker](https://new-sentry.gitlab.net/organizations/gitlab/issues/?query=is%3Aunresolved++CompletionWorker&referrer=issue-list&statsPeriod=14d)
- [Sentry via Feature Category](https://new-sentry.gitlab.net/organizations/gitlab/issues/?query=is%3Aunresolved+feature_category%3Aai_abstraction_layer&referrer=issue-list&statsPeriod=24h)
- [Monthly Retros](https://gitlab.com/gl-retrospectives/data-science/ai-powered/ai-framework-retros)
- [Chat QA Evaluation](https://gitlab.com/gitlab-org/ai-powered/ai-framework/qa-evaluation)

### 📹 GitLab Unfiltered Playlist

The AI Framework Group collates all video recordings related to the group and its team members in [a playlist][youtube] in the [GitLab Unfiltered](https://www.youtube.com/channel/UCMtZ0sc1HHNtGGWZFDRTh5A) YouTube channel.

<%= partial "handbook/engineering/metrics/partials/_cross_functional_dashboard.erb", locals: { filter_value: "AI Framework" } %>

<!-- LINKS START -->

[slack]: TBA
[youtube]: https://www.youtube.com/playlist?list=PL05JrBw4t0Kpt0DsmS5WSZbeiMgrBeZXv
[paid-time-off]: /handbook/paid-time-off/#paid-time-off
[gdoc]: https://docs.google.com/document/d/1rSJNmRZJ0q8hd9S6W_AXlCMvtNTC6cfWr6VU0e2fJCQ/edit#heading=h.3xbjtjtrp0e9

<!-- LINKS END -->