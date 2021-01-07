# GIT COMMANDS

<p>
Git is an open source distributed version control system that allows developers to collaborate on a codebase by tracking the changes made between the local version of an individual developer's code and the remotely hosted "main" code. Using git, developers can update this "main" code, as well as "pull" changes that other collaborators have "pushed" to the "main" code. This guide lists the most common commands you will be using in a git workflow. They are organized by function.
</p>


***Optional parameters are in square brackets ( `[]` )**


## Making a Repository

<table>

<th>Command</th>
<th>Purpose</th>

<tr>
<td>git init [project name]</td>
<td>Initialize current directory as git repository. No remote repository by default. Providing a name creates a new local folder and initializes that instead.</td>
</tr>
<tr>
<td>git clone url</td>
<td>Creates a new local folder and downloads a copy of an existing remote git repository into it.</td>
</tr>
</table>

<br/>


## Staging and Committing Changes

<table>

<th>Command</th>
<th>Purpose</th>

<tr>
<td>git status</td>
<td>Lists all new or yet-to-be-committed files in the current repository.</td>
</tr>
<tr>
<td>git add [file]</td>
<td>Add indicated file, readying it to be committed to your git history. If [file] is omitted, all files that are new or have changes will be readied (AKA "staged").</td>
</tr>
<tr>
<td>git reset [file]</td>
<td>Undoes the staging on the specified file established by git add. Omitting will undo all staging.</td>
</tr>
<tr>
<td>git diff</td>
<td>Shows what has been changed, but yet to be staged via git add. </td>
</tr>
<tr>
<td>git diff --staged</td>
<td>Shows the staged (but not yet committed) changes</td>
</tr>
<tr>
<td>git commit -m "[changes of description]"</td>
<td>commits the changes that were staged with git add. Be sure to include the double-quotes around your message.  </td>
</tr>
<tr>
<td>git log</td>
<td>Displays all commits in the current branch's history</td>
</tr>
</table>

## Syncing and Updating Local and Remote Repositories

<table>

<th>Command</th>
<th>Purpose</th>

<tr>
<td>git remote add [alias] [url]</td>
<td>Names and links to a remote repository. The value of [alias] is of your choosing, and will be used to refer to that particular repository.</td>
</tr>
<tr>
<td>git fetch [alias]</td>
<td>Brings all changes from the previously added [alias] to your local repository. These changes are not finalized (or "merged").</td>
</tr>
<tr>
<td>git push [alias] [branch]</td>
<td>Sends local commits to the remote repository. If [alias] is not provided, defaults to tracked remote master branch.</td>
</tr>
<tr>
<td>git pull</td>
<td>Retrieves AND merges and commits from the remote branch being tracked (often the "main" or "master" branch)</td>
</tr>
</table>

<br/>

## Making and Using Branches 

<table>

<th>Command</th>
<th>Purpose</th>

<tr>
<td>git branch</td>
<td>Lists all git branches in your current repository. An asterix (*) will appear next to your current branch.</td>
</tr>
<tr>
<td>git branch [new-branch-name]</td>
<td>Creates a new branch, identical to the current (at the current commit)</td>
</tr>
<tr>
<td>git checkout branch-name</td>
<td>Switches to the branch name that was created with git branch.</td>
</tr>
<tr>
<td>git merge [branch]</td>
<td>Merges the targeted branch (including branch history) with the current branch</td>
</tr>
</table>

## Rewriting Commit History

<table>

<th>Command</th>
<th>Purpose</th>

<tr>
<td>git rebase [branch]</td>
<td>Takes commits from current branch and appends them to the specified [branch].</td>
</tr>

</table>

## Configuring Local Repository Information
This is for initial setup. It is unlikely you will have to utilize `git config` very often. 
<table>

<th>Command</th>
<th>Purpose</th>

<tr>
<td>git config --global user.name "[firstName lastName]"</td>
<td>Defines a name that will be included in all commits made locally.</td>
</tr>
<tr>
<td>git config --global user.name "[your-email]"</td>
<td>Defines an email that will be included in all commits made locally.</td>
</tr>
</table>

## Troubleshooting

<table>

<th>Command</th>
<th>Purpose</th>

<tr>
<td>git help</td>
<td>Displays a list of other possible actions and their descriptions.</td>
</tr>
</table>