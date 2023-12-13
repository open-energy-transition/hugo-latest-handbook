---

title: "Create:Editor Extensions Group"
description: The Create:Editor Extensions Group is responsible for all product categories that fall under the Editor Extensions group of the Create stage.
---







The Create:Editor Extensions Group is responsible for all aspects of the product categories that fall under the [Editor Extensions group][group] of the [Create stage][stage] of the [DevOps lifecycle][lifecycle].

[group]: /handbook/product/categories/#editor-extensions-group
[stage]: /handbook/product/categories/#create-stage
[lifecycle]: /handbook/product/categories/#devops-stages

## Group overview

### Group members

The following people are permanent members of the Create:Editor Extensions Group:

<%= product_group_table(group: 'Create:Editor Extensions') %>

<%# TODO: make this list dynamic based on the `borrow` field in yaml files %>
The following people are temporary members ([borrow process](/handbook/product/product-processes/#borrow)) of the Create:Editor Extensions Group, each one working on a specific area:

- Language Server
  - [Olena HK.](https://about.gitlab.com/company/team/#ohoral)
- VS Code extension
  - [Sri Rang](https://about.gitlab.com/company/team/#sri19)

### Stable counterparts

<%# TODO: replace this list with a call to stable_counterparts(...) once titles have been updated %>

The following people are [stable counterparts](/handbook/leadership/#stable-counterparts) of the Create:Editor Extensions Group:

- [Kai Armstrong](https://about.gitlab.com/company/team/#phikai), Senior Product Manager (acting)
- [Amy Qualls](https://about.gitlab.com/company/team/#aqualls), Senior Technical Writer
- [Jay McCure](https://about.gitlab.com/company/team/#jay_mccure), Senior Software Engineer in Test, Create

### Product categories

The Editor Extensions group is responsible for the following [product categories](/handbook/product/categories/#editor-extensions-group):

- [Editor Extensions](/direction/create/editor_extensions/)

## Communication

We have a sync meeting as a team once per week.
Recordings are uploaded to the [Editor Extensions Category](https://www.youtube.com/playlist?list=PL05JrBw4t0KoC0pFfuNOAQjKxe4_ypFKc) playlist on GitLab Unfiltered.
When the discussion is finished, we stop the recording and stay on the call for the remaining time to have a group [coffee chat](https://handbook.gitlab.com/handbook/company/culture/all-remote/informal-communication/#coffee-chats).

Additionally to our main team's slack channels, each extension/project we work on has its own slack channel:

- Team:
  - [#g_editor-extensions](https://gitlab.slack.com/archives/C058YCHP17C) - [Sync Agenda](https://docs.google.com/document/d/1UJg-Prf5qGjiGImvaYl5HNjMcJddoeE4u33Ri6SxQ6g)
  - [#g_editor-extensions_social](https://gitlab.slack.com/archives/C062W19B8NR)
  - [#g_editor-extensions-standup](https://gitlab.slack.com/archives/C058YCWPKMG)
- Projects
  - Language Server: [#f_language_server](https://gitlab.slack.com/archives/C05B1PFHRPU)
  - VS Code extension: [#f_vscode_extension](https://gitlab.slack.com/archives/C013QJ9NEPL)
  - Visual Studio extension: [#f_visual_studio_extension](https://gitlab.slack.com/archives/C0581SE363C)
  - JetBrains extension: [#f_jetbrains_plugin](https://gitlab.slack.com/archives/C02UY9XKABH)
  - Neovim extension: [#f_neovim_plugin](https://gitlab.slack.com/archives/C05BF7L6PEX)

## Group processes

Our group processes are documented in this section.
If a process is in use but not described here, please follow the guidance in [Evolving the process](#evolving-the-process) to document it.

Our group is relatively new, and currently light on processes.
There are several differences between how we operate and the shared processes documented in the [product development flow](/handbook/product-development-flow/) and [engineering workflow](/handbook/engineering/workflow/).

### Evolving the process

We take an [iterative](/handbook/values/#iteration) approach to our processes.
Instead of defining it all at once, we add process when we see a gap or identify a problem.
For [efficiency](/handbook/values/#freedom-and-responsibility-over-rigidity), we also don't shy away from removing a process that has outlived its usefulness.

To evolve the process, please [start with an MR](/handbook/communication/#start-with-a-merge-request) to this page which contains your specific proposal, and ask for feedback.
If an issue is better suited for the discussion, it should be created in the [`meta` project](https://gitlab.com/gitlab-org/editor-extensions/meta/-/issues).

### Epics & Issues

We exclusively use [issue/epic descriptions as the single source of truth](/handbook/product-development-flow/#issue-descriptions-as-the-single-source-of-truth-ssot) for our planned work.

- Epics: [GitLab Epic Search](https://gitlab.com/groups/gitlab-org/-/epics?state=opened&page=1&sort=start_date_desc&label_name[]=group::editor+extensions)
- Issues: [GitLab Issue Search](https://gitlab.com/groups/gitlab-org/-/issues/?sort=due_date&state=opened&label_name%5B%5D=group%3A%3Aeditor%20extensions&first_page_size=20)

Epics and issues are created in the project that matches their scope in the narrowest possible way. We use the following projects:
- Work specific to a single extension or to the Language Server:
  - [Language Server](https://gitlab.com/gitlab-org/editor-extensions/gitlab-language-server-for-code-suggestions)
  - [Visual Studio Extension](https://gitlab.com/gitlab-org/editor-extensions/gitlab-visual-studio-extension)
  - [VS Code Extension](https://gitlab.com/gitlab-org/gitlab-vscode-extension)
  - [JetBrains Extension](https://gitlab.com/gitlab-org/editor-extensions/gitlab-jetbrains-plugin)
  - [Neovim Extension](https://gitlab.com/gitlab-org/editor-extensions/gitlab.vim)
- Other projects:
  - [Editor Extensions Meta](https://gitlab.com/gitlab-org/editor-extensions/meta) - Extensions work that isn't specific to a single extension, and general team-related issues
  - [Code Suggestions](https://gitlab.com/gitlab-org/modelops/applied-ml/code-suggestions) - Code Suggestions work that isn't specific to Extensions
  - [GitLab](https://gitlab.com/gitlab-org/gitlab) - Monolith work

### Prioritizing

We use [Milestone Planning Issues](https://gitlab.com/gitlab-org/editor-extensions/meta/-/issues/?sort=created_date&state=all&label_name%5B%5D=Planning%20Issue) 
to define our goals for the current/upcoming milestone.
The PM and EM are responsible for aligning on the goals.
The planning issues are [created automatically](https://gitlab.com/gitlab-org/editor-extensions/meta/-/tree/main#issue-creation-process) every month.

We use the [Editor Extensions Priority Board](https://gitlab.com/groups/gitlab-org/-/boards/7088820?label_name[]=group%3A%3Aeditor%20extensions)
to track the relative [priority of issues](/handbook/product/product-processes/#boards). Issues at the top of a column have the highest priority.

Separately, the technical writer for this group also triages open issues for potential documentation and UI text changes,
and follows the Technical Writing [triage process](/handbook/product/ux/technical-writing/workflow/#documentation-feedback-and-improvements). After review, each issue receives the `~tw::triaged` label.

### Temporary silos

Our team owns several projects, written in different languages (Typescript, Kotlin, C#, Lua) and targeting different platforms.

We are currently intentionally working in silos, by assigning engineers to the project/technology that they can contribute to most efficiently.
This increases speed of development as we aim to reach GA for Code Suggestions, at the cost of knowledge sharing and team resiliency.

This intentional siloing is a temporary measure.
While we do need to cultivate deep expertise in each project,
the mid-term vision for the team is to provide opportunities for [everyone to contribute](https://handbook.gitlab.com/handbook/company/mission/) across each project.
This will increase collaboration, team resiliency, and provide opportunities for growth.

## Knowledge sharing

This section contains links to make it easier to find the same information for each extension.
This is a first iteration, this content should probably live somewhere else eventually.

#### Languages supported by Code Suggestions
Each extension defines an array of supported languages.
- VS Code: [AI_ASSISTED_CODE_SUGGESTIONS_LANGUAGES](https://gitlab.com/gitlab-org/gitlab-vscode-extension/-/blob/f28a17478a41f554e1c620648237705007128d57/src/common/code_suggestions/constants.ts#L9-37)
- Visual Studio: [LanguageManager](https://gitlab.com/gitlab-org/editor-extensions/gitlab-visual-studio-extension/-/blob/a973ef56bac290ed0c2c5c69d20c5606a7198125/GitLab.Extension/CodeSuggestions/LanguageManager.cs#L17-42)
- JetBrains: [SUPPORTED_EXTENSIONS](https://gitlab.com/gitlab-org/editor-extensions/gitlab-jetbrains-plugin/-/blob/ec5b239e6dea3714139031a4d6a9a547142afffc/src/main/kotlin/com/gitlab/plugin/util/GitLabUtil.kt#L20-43)
- Neovim: [auto_filetypes](https://gitlab.com/gitlab-org/editor-extensions/gitlab.vim/-/blob/5b781dffbd047df7050064ad3255154ecef2524c/lua/gitlab/config/defaults.lua#L7-28)

#### Language Server versions in use
- Visual Studio: the server binary is versioned directly: [GitLab.Extension/Resources/gitlab-lsp-win-x64.exe](https://gitlab.com/gitlab-org/editor-extensions/gitlab-visual-studio-extension/-/blob/a973ef56bac290ed0c2c5c69d20c5606a7198125/GitLab.Extension/Resources/gitlab-lsp-win-x64.exe)
- VS Code: the server is pulled as a package: [package.json](https://gitlab.com/gitlab-org/gitlab-vscode-extension/-/blob/main/package.json)
- JetBrains: N/A - see [issue](https://gitlab.com/gitlab-org/editor-extensions/gitlab-jetbrains-plugin/-/issues/30)
- Neovim: the server is pulled as a package: [lsp/package.json](https://gitlab.com/gitlab-org/editor-extensions/gitlab.vim/-/blob/main/lsp/package.json)

## Hiring

Check out our [jobs page](/jobs/) for current openings.

## Engineering metrics

<%= partial "handbook/engineering/metrics/partials/_cross_functional_dashboard.erb", locals: { filter_value: "editor extensions" } %>