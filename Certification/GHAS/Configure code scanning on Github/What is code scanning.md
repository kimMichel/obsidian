Code scanning uses CodeQL to analyze the code in a Github repository to find security vulnerabilities and coding errors. Code scanning is available for all public repositories, and for private repositories owned by organizations where GHAS is enabled. If code scanning finds a potential vulnerability or error in your code, Github displays an alert in the repository's Security tab. After you fix the code that triggered the alert, Github closes the alert.

You can use code scanning to find, triage, and prioritize fixes for existing problems in your code. Code scanning also prevents developers from introducing new problems. You can schedule scans for certain days and times, or trigger scans when a specific event occurs in the repository, such as a push.

In this unit, you'll learn about CodeQL, the three options for setting up code scanning, and how to add the CodeQL workflow to your repository.

# About code scanning with CodeQL

CodeQL is the code analysis engine Github developed to automate security checks. You can analyze your code using CodeQL and display the results as code scanning alerts. There are three main ways to set up CodeQL analysis for code scanning:

- Use default setup to quickly configure CodeQL analysis for code scanning on your repository. The default setup handles choosing the languages to analyze, query suite to run, and events that trigger scans with the option to manually configure the languages and query suites. This setup option runs code scanning as a Github Action.
- Use advanced setup to add the CodeQL workflow directly to your repository. Adding the CodeQL workflow directly into your repository generates a customizable workflow file, which uses the github/codeql-action to run the CodeQL CLI as a Github Action.
- Run the CodeQL CLI directly in an external CI system and upload the results to Github.

CodeQL treats code like data, allowing you to find potential vulnerabilities in your code with greater confidence than traditional static analyzers. You generate a CodeQL database to represent your codebase, then run CodeQL queries on that database to identify problems in the codebase. The query results are shown as code scanning alerts in Github when you use CodeQL with code scanning.

CodeQL supports both compiled and interpreted languages, and it can find vulnerabilities and errors in code written in the following supported languages:

- C or C++
- C#
- Go
- Java/Kotlin
- JavaScript/Typescript
- Python
- Ruby
- Swift

The next section explains how to add the CodeQL workflow to your repository. You'll learn how to set up CodeQL using external tools in the Enable code scanning with third party tools unit.

# Enable CodeQL in your repository with the Default Setup

If you have write permissions to a repository, you can set up or configure code scanning for that repository.

Follow these steps to set up code scanning using the CodeQL Github Actions workflow:

1. On Github.com, navigate to the repository's main page.
2. Under your repository name, select Security.
3. Select Set up code scanning. If this option isn't available, ask an organization owner or repository administrator to enable GHAS.
4. In the Set up drop-down, select Default.
5. Review the default options. If needed, select the Edit button in the bottom left corner of the new window to customize how CodeQL runs.
	The ``on:pull_request`` and ``on:push`` triggers are the default for code scanning are each useful for different purposes. You'll learn more about these triggers in the Configure Code Scanning unit.
6. Select Enable CodeQL once you're ready to turn on code scanning.
	In the default CodeQL analysis workflow, code scanning is configured to analyze your code each time you either push a change to any protected branches or raise a pull request against the default branch. Once the push is made, code scanning runs automatically.

In the previous section, we enabled code scanning using the default setup, which runs code scans as a Github Action without needing to maintain a workflow file. The other option is Advanced setup, which generates the default workflow file you can edit for advanced configuration and more steps. We'll cover using the advanced setup for configuring code scanning in a later unit.

Running code scanning with Github Actions affects your monthly billing minutes. If you want to use Github Actions beyond the storage or minutes included in your account, you'll be billed for more usage.

# About Billing for Actions

Code scanning uses Github Actions, and each run of code-scanning workflow consumes minutes for Github Actions. Github Actions usage is free for both public repositories and self-hosted runners. For private repositories, each Github account receives a certain number of free minutes and storage, depending on the product used with the account. Spending limits control any usage beyond the included amounts. If you're a monthly billed customer, your account has a default spending limit of zero US dollars (USD), which prevents extra usage of minutes or storage for private repositories beyond the amounts included with your account. If you pay your account by invoice, your account will have an unlimited default spending limit. Minutes reset every month, while storage usage doesn't.

