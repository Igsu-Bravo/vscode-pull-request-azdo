# Review and manage your Azure Devops pull requests directly in VS Code

![Build and Test](https://github.com/ankitbko/vscode-pull-request-azdo/workflows/Build%20and%20Test/badge.svg?branch=master&event=push)

This extension is inspired and based on [Github Pull Request Extension for VS Code](https://github.com/Microsoft/vscode-pull-request-github). The extension only works with *git* based repository. *TFVC* is not supported. Currently the extension supports following feature -

- Authenticating and connecting VS Code to Azure Devops.
- Listing and browsing PRs from within VS Code.
- Reviewing PRs from within VS Code with in-editor commenting.
- Validating PRs from within VS Code with easy checkouts.


You can read more about the basic features in my [blog](https://ankitbko.github.io/blog/2021/01/azdo-pr-vscode-extension/).


> **Note From Author**: I created this extension during last 2 weeks of December 2020 as a fun side project. Having never created a VS Code Extension before this was quite a journey. I am currently planning to get this to somewhat stable state before adding more features to it. Please try this extension and report any bugs by raising issue. Since this is a fork of Github PR Extension I will try to backport important updates from upstream to this extension. If you feel there has been an important bug fix or feature update in upstream that you would like in this extension, please raise an Issue here with link to the PR or Issue in upstream.

> **Disclaimer**: Although I work at Microsoft and this is a fork of Github PR Extension, this extension is not an official release or supported by Microsoft. This is a side project that I will try to maintain in my free time. Any help is always appreciated.

![PR Diff](documentation/images/pr_modified.jpg)
![PR Dashboard](documentation/images/pr_dashboard.jpg)

## Getting Started
It's easy to get started with Azure Devops Pull Requests for Visual Studio Code. Simply follow these steps to get started.

1. Make sure you have VSCode version 1.52.0 or higher.
1. Reload VS Code after the installation (click the reload button next to the extension).
1. Open your desired Azure Devops repository.
1. You will need to configure the `azdoPullRequests.projectName` and `azdoPullRequests.orgUrl` setting. You can configure it in workspace settings and commit it so others in your team wouldn't need to do this configuration again. (Look at the next section to understand the format of these settings).
1. You will need to configure [PAT token in Azure Devops](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=preview-page) to login. Click on *show all scopes* and select the following scopes for the token - `Code: Read & Write`, `Pull Request Threads: Read & Write`, `Work Items: Read & Write`, `Member Entitlement Management: Read`. Read more about these scope in next section.
1. A new tab would have appeared on the activity bar on the left. Open it and click on `Sign in` button. Enter the PAT token and press enter.
1. You should be good to go!

### Scopes required by PAT Token
- **Minimum**: These scopes are required for extension to access Pull Requests and Threads. Without these scopes the extension will not even start.
	- `Code: Read & Write`: Required to access repository metadata and pull requests.
	- `Pull Request Threads: Read & Write`: Access Pull Request comment threads.
- **Additional**: These scopes are required to experience the extension in its completeness. Without these some functionality of extension may not work or the extension may cause errors.
	- `Work Items: Read & Write`: Allow to read and associate work items to a PR.
	- `Member Entitlement Management: Read`: Used to search for users when adding reviewers to PR.

## Configuring the extension
#### azdoPullRequests.orgUrl
- *type*: string
- *required*: true
- *Description*: The organization URL of Azure Devops. You can get it from the URL of the AZDO. This is typically the first segment of URL after host name in AZDO. `https://dev.azure.com/<org_name>` or `https://<org_name>.visualstudio.com`. You will need to enter the complete URL.
- *Example*: `https://dev.azure.com/anksinha` or `https://anksinha.visualstudio.com`

#### azdoPullRequests.projectName
- *type*: string
- *required*: true
- *Description*: The project in the Azure Devops. This is typically the next segment of URL after organization name in AZDO. `https://dev.azure.com/<org_name>/<project_name>` or `https://<org_name>.visualstudio.com/<project_name>`. **Do not enter the complete URL, you only need to enter the *project_name* part**. 
- *Example*: `prExtension`

#### azdoPullRequests.logLevel
- *type*: enum
- *required*: false
- *default*: Info
- *Description*: The level of log to display in AzDO Pull Request Channel in Output window.

#### azdoPullRequests.diffBase
- *type*: enum
- *required*: false
- *default*: mergebase
- *Description*: The commit to use to get diff against the PR branch's HEAD. Read more about different options in [wiki](https://github.com/ankitbko/vscode-pull-request-azdo/wiki/Diff-Options:-HEAD-vs-Merge-Base)

## Known Major Issues
1. Mentions in comments are not resolved to user and no hover support
1. Can't mention users in comments
1. **Some incompatibility with Github PR Extension**. If you have both extensions installed and seeing issues with either try disabling the other extension and reloading the window.
1. In some cases, user avatar image does not show up in Dashboard.

## Questions? Authentication?

See our [wiki](https://github.com/ankitbko/vscode-pull-request-azdo/wiki) for our FAQ.

## Contributing

TODO
