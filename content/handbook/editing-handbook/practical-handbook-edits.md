---
title: "Practical Handbook Editing Tips"
description: "Video recordings and written tips for team members on additional tips to working handbook first."
aliases:
- /handbook/practical-handbook-edits/
---

This page contains instructions, tips, and historical recordings for non-technical team members on how to work handbook-first.

Content on this page is to provide additional tips as a supplement to the [editing handbook page]({{< ref "editing-handbook.md" >}}).
Please keep the basics of how to edit the handbook, including how to get help on the [editing handbook page]({{< ref "editing-handbook.md" >}}).

## Before you begin in command line

Some tips may require terminal shell access on macOS/Linux. Ensure that your environment is working and that you have cloned the [public handbook](https://gitlab.com/gitlab-com/content-sites/handbook) repository for example.

```shell
git clone https://gitlab.com/gitlab-com/content-sites/handbook.git
```

Sync it. Ensure that you stash away local changed not yet committed.

```shell
cd handbook
git stash
git checkout main
git pull
```

On macOS it is advised to use Homebrew and install the GNU tools. See [this blogpost](https://about.gitlab.com/blog/2020/04/17/dotfiles-document-and-automate-your-macbook-setup/) for a macOS setup.

```shell
brew install gnu-sed
```

## Find files

One of the shell tools provided with macOS/Linux GNU is `find`. Open a terminal an run the following command in the main directory of the `www-gitlab-com` repository to get a list of all `*.md` files. This matches `.md` as suffix.

```shell
find . -type f -name '*.md'
```

Instead of the `.` you can also use a directory in the current path.

```shell
find source/handbook -type f -name '*.md'
```

The type `f` specifies files, `d` matches for directories. When not specified, all files and directories are taken into account.

You can replace `-name` with `-regex` to do more sensitive matching, for example to match all `.md` and `.md.erb` files.

```shell
find . -type f -regex '.*\.md[.erb]*'
```

This can be useful to **check whether a blog post was merged to master**:

```shell
git checkout master
git pull
find . -type f -name '*blogpost-filename*'
```

## Find files and perform an action

This comes in handy when you want to print all matches with a prefix, or perform additional replace actions. The main principle is to follow the matching rules explained above, and add the `-exec` parameter.

The `exec` action should start a shell and execute a command in there. `sh -c '' \;` takes care of this for every file that matches. Imagine this as a loop of sequential steps to perform the action. The last missing bit is accessing the file in the current loop iteration. This is done via the `{}` marker inside the `echo` example printing the output.

Run the command in a terminal to see how it works:

```shell
find source/handbook/marketing -type f -name '*.md' -exec sh -c 'echo "Matched {}"' \;
```

## Replace strings in a file

The GNU `sed` shell command is useful to replace a defined string in a file. The `-i` flag specifies to do that inline in the same file. The `g` flag defines a global match, replacing all pattern matches.

```shell
sed -i 's/<searchtext>/<replacementtext>/g' file.md
```

On macOS, ensure that the `gnu-sed` package is installed, and run `gsed` (instead of `sed`).

```shell
gsed -i 's/<searchtext>/<replacementtext>/g' file.md
```

With using the `/` separator, it is necessary to escape all `/` characters in the string. You can avoid this by choosing another separator, for example `,`:

```shell
gsed -i 's,<searchtext>,<replacementtext>,g' file.md
```

## Find and Replace a String in all (Matching) Files

Please see the following suggestions for doing a bulk find and replace.

If you rename a file/URL in one of the handbook repositories, please [add a redirect using an alias]({{< ref "metadata.md#aliases" >}}).

If you rename a file/URL in the `www-gitlab-com` repository, please remember to add a redirect to [`redirects.yml`](https://gitlab.com/gitlab-com/www-gitlab-com/-/blob/master/data/redirects.yml) by [following this process](https://gitlab.com/gitlab-com/www-gitlab-com/blob/master/doc/redirects_on_about_gitlab_com.md).

### Using a terminal

Sometimes a project, URL target or Slack channel is being renamed. You can easily search and edit with the Web IDE on GitLab.com but for other files there is a quick and automated way required.

This method combines the find, exec and sed tips explained above. The `exec` action is now to use sed to perform an inline replacement of a pattern/string.

The following example is used in [this MR](https://gitlab.com/gitlab-com/www-gitlab-com/-/merge_requests/49617) for updating the Corporate Marketing project URL in all files.

```shell
git checkout master
git pull origin master

git checkout -b handbook/corp-mktg-project-url

find source/handbook -type f -exec sh -c 'gsed -i "s,https://gitlab.com/gitlab-com/marketing/corporate-marketing,https://gitlab.com/gitlab-com/marketing/corporate_marketing/corporate-marketing,g" "{}"' \;

git status
git diff

git commit -av -m "Handbook: Update corporate marketing project URL"

git push -u origin handbook/corp-mktg-project-url

<open URL in browser for MR>
```

To cut it down:

- Find and match all files in the `source/handbook` directory. The URL might be found in other files too.
- `exec` runs a `sed/gsed` action
- The replacement is `https://gitlab.com/gitlab-com/marketing/corporate-marketing` with `https://gitlab.com/gitlab-com/marketing/corporate_marketing/corporate-marketing`
- Verify the changes with `git status` and `git diff` before committing them
- Commit, push and create the MR from the URL

### Using Visual Studio Code

You can also do bulk find and replace operations using [Visual Studio Code](https://code.visualstudio.com/download) along with the [GitLab Workflow extension for VS Code](https://docs.gitlab.com/ee/user/project/repository/vscode.html). The following steps were used in this [MR](https://gitlab.com/gitlab-com/www-gitlab-com/-/merge_requests/106599) for updating `sub-value` to `operating principle`.

On macOS this can be a fairly seamless experience if you clone the project ([`www-gitlab-com`](https://gitlab.com/gitlab-com/www-gitlab-com) for the Handbook) [using SSH](/handbook/editing-handbook/#clone-via-ssh) and then use [1Password for SSH & Git](https://developer.1password.com/docs/ssh/).

Once you've configured and installed `Visual Studio Code` and logged into the `GitLab Workflow extension for VS Code` open the `www-gitlab-com` directory where you've synced the repo.

Create a new branch by:

1. Clicking on `master` in the bottom bar
1. Select `Create new branch`
1. Enter a branch name
1. Press the enter key

You can then use the `Search` functionality (`⌘⇧F`) to find all files matching your desired search. Searching in `Visual Studio Code` allows matching case, matching whole word, or using Regular Expressions. If you click on the ellipsis (`…`) you also have the option to include or exclude files by pattern matching on the path (uses commas to delimit multiple includes/excludes).

You can do a `Replace All` across all files with the matching search term directly in the `Search` functionality:

1. Click on the disclosure arrow next to the `Search` field or enter `⌘⇧H`
1. Enter the `Search` term
1. Enter the `Replace` term
1. Click on the `Replace All` button next to the `Replace` field or enter `⌥⌘Enter`

Once you've made your edits use the `Source Control` (`⌃⇧G`) functionality to:

1. Stage your changes by clicking on the `+` sign for each file, or the `+` sign for the entire commit
1. Provide a name to the commit in the Message field saving with a `⌘Enter`
1. Clicking on the publish or sync button

You can use the `GitLab Workflow` extension to manage the `Merge Request` (MR) once the branch has been pushed and MR created.

## Remove trailing whitespaces

CI/CD linting jobs can use checks for trailing whitespaces. When detected, the checks cause the pipeline to fail, and require editing the files again. This can increase time to create and review MRs. The following tips help with removing trailing spaces in detected files faster.

```shell
content/handbook/marketing/developer-relations-and-community/_index.md:78:70 MD009/no-trailing-spaces Trailing spaces [Expected: 0 or 2; Actual: 1]
```

An IDE or the command line are common ways to fix the problem.

1. [Visual Studio Code](/handbook/tools-and-tips/editors-and-ides/visual-studio-code/): Open the file to edit. On macOS, [use the shortcut `cmd k x`](https://code.visualstudio.com/docs/getstarted/keybindings#_rich-languages-editing) to clear trailing whitespaces and [`cmd s` to save the file](https://code.visualstudio.com/docs/getstarted/keybindings#_file-management).
1. [vim](/handbook/tools-and-tips/editors-and-ides/vim/): Change to the command mode (ESC), start a command with `:` and copy the following sequence to clear all trailing whitespaces: `%s/\s\+$//e`. Press enter, and save the file with `:wq`.

Visual Studio Code provides an editor setting to remove trailing whitespaces permanently. Navigate to `File > Preference > Settings > User > Text Editor > Files > Trim Trailing Whitespace` and check the box to trim whitespaces when files are saved automatically. Please use this setting carefully, because some files contain many whitespaces to fix and can render the Merge Request change diff hard to read. This increases MR review time. It is recommended to remove and fix trailing whitespaces in a separate MR.

### Bulk remove trailing whitespaces

You can replace trailing whitespaces in multiple files on the command line using [GNU sed](#before-you-begin-in-command-line) and [find](#using-a-terminal). The following example recurisvely searches the `content/handbook` directory for files matching the pattern `*.md` and executes a script on each file, which replaces trailing whitespaces inline (`sed -i ...`).

```shell
find content/handbook -type f -name '*.md' -exec sh -c "sed -i 's/[ \t]*$//' "$1" '{}'" \;
```

### Remove trailing whitespaces in a merge request

Sometimes the easiest way to fix one - or a few - trailing whitespace lint errors is directly in the merge request.

1. From the `Changes` tab in the merge request, find the file and line number mentioned in the lint error message
1. Click the speech bubble next to the line number to add a comment
1. In the comment dialog, click the `insert suggestion` button to copy the line into the comment dialog
1. Remove the trailing whitespace from the end of the line
1. Click `Add comment now` and apply the suggestion

{{< youtube Kfdf2VAk9sM >}}