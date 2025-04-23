# sanjivani_demo
Set 1: Git and JQL Queries (Linux Environment)
Q1. Git Scenario – Project Initialization (Linux)
Initialize Git in the project folder:

Navigate to your project directory:

bash
Copy
Edit
cd /path/to/your/InvoiceApp
git init
This will initialize a Git repository in the InvoiceApp folder.

Create a remote GitHub repository and connect it:

Go to GitHub and create a new repository called InvoiceApp.

Copy the URL provided for the repository (e.g., https://github.com/yourusername/InvoiceApp.git).

Then, connect your local Git repository to GitHub:

bash
Copy
Edit
git remote add origin https://github.com/yourusername/InvoiceApp.git
Add all files, commit with the message "Initial commit", and push the project:

Add all files to the staging area:

bash
Copy
Edit
git add .
Commit the changes with the message "Initial commit":

bash
Copy
Edit
git commit -m "Initial commit"
Push the changes to the GitHub repository:

bash
Copy
Edit
git push -u origin master
Q2. JQL Advanced Search – Created, Due, and Resolution Filters
Find all issues created in the last 10 days that are still unresolved:

jql
Copy
Edit
created >= -10d AND resolution = EMPTY
Show all issues that are due in the next 3 days:

jql
Copy
Edit
due <= 3d
Find all bugs that were resolved in the last 5 days:

jql
Copy
Edit
type = Bug AND resolutiondate >= -5d
Difference between resolution = EMPTY and status != Done:

resolution = EMPTY: This filters issues that have not yet been resolved, meaning no resolution has been set.

status != Done: This filters issues that are not in the "Done" status. They could have a resolution set, but their status is still not completed.

Set 2: GitHub and JQL Queries
Q1. GitHub Scenario – Team Collaboration (Linux)
Create a new GitHub repository:

Go to GitHub and create a new repository called InvoiceApp.

Do not initialize it with a README (you’ll add it locally).

Add a README.md:

Create a README.md file in your project directory:

bash
Copy
Edit
touch README.md
Add some basic information to the file:

bash
Copy
Edit
echo "# InvoiceApp" > README.md
Invite your team for collaboration:

Go to the "Settings" of your GitHub repository.

In the "Collaborators" section, invite team members by entering their GitHub usernames.

Set up branch protection on the main branch to require pull requests:

Go to "Settings" -> "Branches".

Under "Branch protection rules", click "Add rule" and select the main branch.

Enable the "Require pull request reviews before merging" option.

Q2. JQL Search – Transitions, Assignee, Due Dates
Find issues where status changed from "To Do" to "In Progress" in the last 7 days:

jql
Copy
Edit
status CHANGED FROM "To Do" TO "In Progress" DURING (-7d, now())
List all issues assigned to you that are overdue:

jql
Copy
Edit
assignee = currentUser() AND due < now() AND resolution = EMPTY
Show all tasks that transitioned to “Done” in the last 2 days:

jql
Copy
Edit
status CHANGED TO "Done" DURING (-2d, now())
Explanation of the CHANGED keyword in tracking workflow changes:

The CHANGED keyword in JQL allows you to track changes in issue fields like status, assignee, priority, etc. It's useful to filter issues based on specific transitions or modifications over a time period.

Set 3: Git and JQL Queries
Q1. Git Scenario – Branching & PR (Linux)
Create a new branch called search-feature:

bash
Copy
Edit
git checkout -b search-feature
Make changes and push the branch:

After making changes in your files, add and commit them:

bash
Copy
Edit
git add .
git commit -m "Added search feature"
Push the new branch to GitHub:

bash
Copy
Edit
git push -u origin search-feature
Open a pull request and assign a reviewer:

Go to GitHub, navigate to your repository, and open a pull request (PR) for the search-feature branch.

Assign a reviewer to the PR.

Merge the changes after review:

After the reviewer approves the PR, merge it using the GitHub interface, or use the command:

bash
Copy
Edit
git checkout main
git pull origin main
git merge search-feature
git push origin main
Q2. JQL – Created/Updated/Transitioned Filter Queries
Issues created between March 1 and March 10, 2025:

jql
Copy
Edit
created >= "2025-03-01" AND created <= "2025-03-10"
Issues updated within the last 3 days:

jql
Copy
Edit
updated >= -3d
Issues that transitioned from "In Progress" to "Testing" after April 1, 2025:

jql
Copy
Edit
status CHANGED FROM "In Progress" TO "Testing" AFTER "2025-04-01"
Difference between updated >= -3d and created >= -3d:

updated >= -3d: Filters issues that have been updated in the last 3 days, meaning any change in the issue (status change, comment, etc.).

created >= -3d: Filters issues that were created in the last 3 days.
Set 4: Git and JQL Queries (Linux Environment)
Q1. Git Scenario – Resolve Merge Conflict (Linux)
How to view the conflict: When you attempt to merge two branches (for example, feature into main) and there’s a conflict, Git will indicate the conflict during the merge process. To view the conflicted files, use:

bash
Copy
Edit
git status
This will list files with merge conflicts, marked as "both modified."

How to resolve it locally:

Open the conflicted file in your text editor (e.g., nano, vim, VSCode).

Git will mark the conflict areas in the file using <<<<<<<, =======, and >>>>>>>.

Choose which changes to keep (yours or the teammate’s) or manually merge them.

After resolving the conflict, save the file.

How to commit and complete the merge:

After resolving all conflicts, add the resolved files to the staging area:

bash
Copy
Edit
git add <file-name>
Commit the merge resolution:

bash
Copy
Edit
git commit -m "Resolved merge conflict"
Finally, complete the merge by pushing the changes to the remote repository:

bash
Copy
Edit
git push origin main
Q2. JQL – Component, Labels, Sprint Filters
Find all issues in the Frontend component that are unresolved:

jql
Copy
Edit
component = "Frontend" AND resolution = EMPTY
List issues labeled as urgent or production-fix:

jql
Copy
Edit
labels in ("urgent", "production-fix")
Show all issues in the current sprint and assigned to your team:

jql
Copy
Edit
Sprint in openSprints() AND assignee in (membersOf("your-team"))
When is it better to use labels vs components in organizing issues?

Labels are better for categorizing issues by specific characteristics that might span multiple components (e.g., "urgent", "performance"). Labels are flexible and can be used to add context to issues.

Components are better for grouping issues related to a specific part of the product or application, such as "Frontend", "Backend", "Database", etc. Components help organize issues by their functional or technical areas.

Set 5: GitHub and JQL Queries
Q1. GitHub Scenario – Team Collaboration (Linux)
Create a new GitHub repository:

Go to GitHub and create a new repository, such as InvoiceApp.

Do not initialize it with a README, as you will add it locally.

Add a README.md:

Create a new README.md file in your project directory:

bash
Copy
Edit
touch README.md
Add content to the README file:

bash
Copy
Edit
echo "# InvoiceApp" > README.md
Invite your team for collaboration:

On the GitHub repository page, go to "Settings" > "Collaborators".

Invite your team members by entering their GitHub usernames.

Set up branch protection on the main branch to require pull requests:

Go to "Settings" > "Branches".

Add a new branch protection rule for the main branch.

Enable the "Require pull request reviews before merging" option.

Q2. JQL – Release Readiness Queries
Find all issues targeted for fixVersion = "v2.0":

jql
Copy
Edit
fixVersion = "v2.0"
List bugs in v2.0 that are still unresolved:

jql
Copy
Edit
fixVersion = "v2.0" AND type = Bug AND resolution = EMPTY
Find tasks in v2.0 that were resolved in the last 7 days:

jql
Copy
Edit
fixVersion = "v2.0" AND type = Task AND resolutiondate >= -7d
Why is fixVersion useful for managing product releases?

fixVersion helps track which version of the software an issue is related to. It allows teams to organize issues based on the release version and plan tasks, bug fixes, and new features for a specific version of the product. This is essential for release planning and managing the scope of each release.

Set 6: Git and JQL Queries
Q1. Git Scenario – Tag and Release (Linux)
Tag the release as v1.0:

To tag the release:

bash
Copy
Edit
git tag -a v1.0 -m "Release version 1.0"
Push the tag to GitHub:

To push the tag to the remote repository:

bash
Copy
Edit
git push origin v1.0
Create a release on GitHub from the tag:

Go to your GitHub repository.

Under "Releases", click "Draft a new release".

Choose the tag (v1.0), add release notes, and publish the release.

Q2. JQL – Overdue & SLA Queries
Show all issues that are overdue by more than 2 days:

jql
Copy
Edit
due < -2d AND resolution = EMPTY
List all issues that must be resolved within 48 hours (use SLA label or custom field if available):

jql
Copy
Edit
"SLA" <= 48h AND resolution = EMPTY
Find issues with a due date within this week:

jql
Copy
Edit
due <= endOfWeek() AND resolution = EMPTY
How JQL helps with SLA enforcement in service-based teams:

JQL can be used to monitor SLA compliance by filtering issues that are overdue or need to be resolved within specific timeframes. By creating queries for SLA-related custom fields (e.g., "SLA" field), teams can ensure that issues are addressed on time and meet service level expectations.

Set 7: Jira and JQL Queries
Q1. Jira Scenario – Scrum Project Setup
Create the project:

Go to Jira and click "Create Project".

Select the "Scrum" template and follow the steps to create the project.

Set up a board and sprints:

After the project is created, set up a Scrum board in Jira to visualize work.

Add backlog items (issues) to the board and create sprints from the backlog.

Add backlog items:

In the "Backlog" view, click "Create Issue" to add items to the backlog.

Start and manage a sprint:

From the "Active Sprints" view, start a sprint and assign issues from the backlog.

Manage the sprint by tracking progress and adjusting the scope as necessary.

Q2. JQL – Team Assignment and Status Filters
Find all unresolved tasks assigned to Team-A:

jql
Copy
Edit
assignee in (membersOf("Team-A")) AND resolution = EMPTY
Find issues currently in "Blocked" status for more than 2 days:

jql
Copy
Edit
status = Blocked AND updated <= -2d
List all bugs assigned to your name and in "In Review":

jql
Copy
Edit
assignee = currentUser() AND type = Bug AND status = "In Review"
Why is it valuable to include team-level JQL filters on sprint dashboards?

Team-level JQL filters on sprint dashboards provide visibility into the progress of team-specific work. This allows teams to track their assigned tasks and prioritize issues effectively during the sprint, ensuring that all work items are properly managed and completed on time.

Set 8: GitHub and JQL Queries
Q1. GitHub Scenario – Fork and Contribute (Linux)
Fork the repo:

Go to the repository you want to contribute to on GitHub.

Click the "Fork" button to create a copy of the repository under your GitHub account.

Clone your fork:

bash
Copy
Edit
git clone https://github.com/yourusername/repository.git
Create a branch, make changes, and push:

bash
Copy
Edit
git checkout -b new-feature
# Make changes to the code
git add .
git commit -m "Add new feature"
git push origin new-feature
Open a pull request to the original repository:

Go to the original repository on GitHub and open a pull request to merge your changes.

Q2. JQL – Time-Sensitive Filters & Workload Tracking
Find issues where created >= startOfWeek():

jql
Copy
Edit
created >= startOfWeek()
Find all issues resolved in the previous quarter:

jql
Copy
Edit
resolutiondate >= startOfQuarter(-1) AND resolutiondate <= endOfQuarter(-1)
Show unresolved issues due within the next 7 days and assigned to your team:

jql
Copy
Edit
due <= 7d AND assignee in (membersOf("your-team")) AND resolution = EMPTY
Explain the use of startOfWeek(), startOfQuarter(-1), and <= 7d in time-sensitive reporting:

startOfWeek(): Filters issues created since the start of the current week.

startOfQuarter(-1): Filters issues resolved in the previous quarter.

<= 7d: Filters issues with a due date within the next 7 days.

Set 1:

Q1. Git Scenario – Recover Deleted Local Changes
You deleted a local file accidentally before committing. Here's how you can recover it:

If the file is staged:
Use the following command to recover the file:

bash
Copy
Edit
git checkout -- <file-path>
This command restores the file to the last committed version.

If it's only modified (but not staged):
You can restore the file to its last committed state using:

bash
Copy
Edit
git checkout <file-path>
If it was deleted after the last commit:
Use this command to recover the deleted file:

bash
Copy
Edit
git checkout HEAD <file-path>
This command brings back the file from the last commit.

Q2. JQL – Tracking Creation & Reopened Issues

a. Find issues created in the last 14 days assigned to yourself:

jql
Copy
Edit
created >= -14d AND assignee = currentUser()
b. List all issues with status Reopened after being marked Done:

jql
Copy
Edit
status = Reopened AND status CHANGED FROM Done TO Reopened
c. Find bugs created by QA team members that are unresolved:

jql
Copy
Edit
issuetype = Bug AND reporter in membersOf("QA") AND resolution = Unresolved
Explanation:
The status CHANGED JQL function helps in filtering reopened issues because it tracks when the status changes, allowing you to pinpoint when the issue has been marked as "Reopened" after a "Done" status.

Set 2:

Q1. GitHub Scenario – Manage Repo Access

Add a collaborator with write access:

Go to your repository on GitHub.

Navigate to Settings > Collaborators & teams.

Click Add people and enter their GitHub username or email.

Select Write access and invite them.

Prevent force pushes to main:

Go to your repository on GitHub.

Navigate to Settings > Branches.

Under Branch protection rules, select the main branch.

Enable Restrict who can push to matching branches and check Do not allow force pushes.

Set up required PR reviews:

Go to Settings > Branches.

Under Branch protection rules, click Add rule.

Choose the main branch and enable Require pull request reviews before merging.

Q2. JQL – Priority, Due Dates, and Overdue Items

a. Find all critical-priority issues assigned to your team:

jql
Copy
Edit
priority = Critical AND assignee in membersOf("YourTeam")
b. Show tasks due within 3 days that are unresolved:

jql
Copy
Edit
due <= 3d AND resolution = Unresolved
c. List overdue issues created in the past 20 days:

jql
Copy
Edit
created >= -20d AND due < now() AND resolution = Unresolved
Explanation:
Using dynamic dates like <= 3d allows flexibility in filtering issues based on real-time date differences. Fixed dates could miss issues if dates are not manually adjusted.

Set 3:

Q1. Jira Scenario – Add Custom Workflow Status

Add the status to workflow:

Go to Jira Settings > Issues > Workflows.

Select the workflow you want to modify.

Add a new status named "Code Review" and place it between “In Progress” and “Done.”

Update transitions:

Click Add Transition from "In Progress" to "Code Review" and from "Code Review" to "Done."

Define the transition conditions and validators as needed.

Reflect changes on the board:
Ensure the board is updated with the new status by checking the board settings and configuring the workflow status mapping.

Q2. JQL – Workflow Transition Metrics

a. Find tasks that moved to "Code Review" in the past 5 days:

jql
Copy
Edit
status = "Code Review" AND status CHANGED TO "Code Review" AFTER -5d
b. Show all issues where status changed from "In Progress" to "Blocked":

jql
Copy
Edit
status CHANGED FROM "In Progress" TO "Blocked"
c. List stories that have never transitioned to "Testing":

jql
Copy
Edit
issuetype = Story AND status NOT IN ("Testing")
Explanation:
The NOT status WAS function is useful to filter out issues that have never transitioned through a specific status, such as "Testing."

Set 4:

Q1. Git Scenario – Clean Up Commits Before Push

How to squash commits:
Use git rebase to squash commits:

bash
Copy
Edit
git rebase -i HEAD~n
Replace n with the number of commits to squash. Then, change pick to squash for all commits except the first one.

Rewrite the commit message:
During the rebase, you can modify the commit message by changing the pick command to reword for the commit you want to edit.

Push with force (safely):
After squashing and modifying the commit message, push the changes using:

bash
Copy
Edit
git push origin main --force-with-lease
Q2. JQL – Epic, Sprint & FixVersion Filters

a. Find all issues linked to epic "Checkout Redesign":

jql
Copy
Edit
"Epic Link" = "Checkout Redesign"
b. Show tasks from the current sprint that are unresolved:

jql
Copy
Edit
sprint in openSprints() AND resolution = Unresolved
c. List stories targeted for release version v1.1:

jql
Copy
Edit
issuetype = Story AND fixVersion = "v1.1"
Explanation:
The fixVersion field is essential for tracking releases and versions in Jira. It ensures that issues are associated with specific release versions for better release planning.
Set 5:

Q1. GitHub Scenario – Using GitHub Issues for Planning

Enable issues on the repo:

Go to your GitHub repository.

Click on Settings.

Under the Features section, ensure that Issues is checked to enable issue tracking.

Create labels like bug, enhancement, urgent:

In the Issues tab of your repository, click on Labels.

Click New Label and create labels like bug, enhancement, urgent. Assign colors for better visual identification.

Assign and close issues:

To assign an issue, go to the issue, and on the right sidebar, under Assignees, select a team member.

To close an issue, navigate to the issue and click Close issue at the bottom of the page.

Q2. JQL – Label, Component, and Reporter Filters

a. Find issues labeled security and unresolved:

jql
Copy
Edit
labels = security AND resolution = Unresolved
b. Show issues in the component API and created in the last 7 days:

jql
Copy
Edit
component = API AND created >= -7d
c. List all issues reported by devops@example.com:

jql
Copy
Edit
reporter = devops@example.com
Explanation:
Components are useful for breaking down a project into smaller, manageable parts (like "API"), while labels are more flexible and often used for categorization or tagging (like "security" or "urgent"). Components are useful for structured filtering of project sections, whereas labels provide more dynamic, flexible categorization.

Set 6:

Q1. Git Scenario – Clone and Contribute to a Repo

Clone the repo:

bash
Copy
Edit
git clone <repo-url>
Create a branch feature-contact-form:

bash
Copy
Edit
git checkout -b feature-contact-form
Commit and push changes:

bash
Copy
Edit
git add .
git commit -m "Add contact form feature"
git push origin feature-contact-form
Submit a pull request:

Go to your repository on GitHub.

Navigate to the Pull requests tab and click New Pull Request.

Select your branch (feature-contact-form) and compare it with the main branch.

Click Create Pull Request and add a description.

Q2. JQL – Bug Analysis Over Time

a. Show bugs unresolved for more than 10 days:

jql
Copy
Edit
issuetype = Bug AND resolution = Unresolved AND created <= -10d
b. Find bugs resolved within 3 days of creation:

jql
Copy
Edit
issuetype = Bug AND resolution = Resolved AND resolved - created <= 3d
c. Show bugs that have been reopened at least once:

jql
Copy
Edit
issuetype = Bug AND status CHANGED FROM Resolved TO Reopened
Explanation:
The created, resolved, and status changed fields help track the time it takes for a bug to get resolved, measure the efficiency of the bug resolution process, and identify bugs that were reopened, which can indicate recurring issues or incomplete fixes.

Set 7:

Q1. Jira Scenario – Dashboard Customization

Create a filter for unresolved bugs:

Go to Filters > Create a filter.

Use the following JQL query:

jql
Copy
Edit
issuetype = Bug AND resolution = Unresolved
Save the filter.

Add a pie chart showing bugs by priority:

Go to Dashboards and create a new dashboard or edit an existing one.

Add a Pie Chart gadget.

Configure the gadget to display the filter for unresolved bugs and group by Priority.

Display bugs by assignee in a table view:

Add a Filter Results gadget.

Configure it to display your unresolved bug filter.

In the columns section, choose to display the Assignee column.

Q2. JQL – Assignee, Due Date, Priority Filters

a. Find all unresolved tasks assigned to yourself:

jql
Copy
Edit
assignee = currentUser() AND resolution = Unresolved
b. Show high-priority issues due this week:

jql
Copy
Edit
priority = High AND due >= startOfWeek() AND due <= endOfWeek()
c. List all issues where assignee is EMPTY:

jql
Copy
Edit
assignee is EMPTY
Explanation:
"Unassigned tasks" are crucial to track because they indicate potential bottlenecks in the workflow. These tasks might need to be assigned to someone, and tracking them helps ensure that work is evenly distributed across the team.

Set 8:

Q1. Git Scenario – Work with Remote Branches

Track the remote branch:

bash
Copy
Edit
git fetch
git checkout -b report-gen origin/report-gen
Pull changes made by your teammate:

bash
Copy
Edit
git pull origin main
Delete the remote branch after merge:

bash
Copy
Edit
git push origin --delete report-gen
Q2. JQL – User, Status, and Date Combinations

a. Find tasks assigned to john.doe that are in progress:

jql
Copy
Edit
assignee = john.doe AND status = "In Progress"
b. Show issues created by you this month:

jql
Copy
Edit
reporter = currentUser() AND created >= startOfMonth()
c. Find all issues that transitioned to “Done” after April 1, 2025:

jql
Copy
Edit
status = Done AND status CHANGED TO Done AFTER "2025-04-01"
Explanation:
The startOfMonth() function helps track tasks for the current month by dynamically adjusting the query based on the current date. This is useful for reporting on monthly work progress without manually updating date ranges.
