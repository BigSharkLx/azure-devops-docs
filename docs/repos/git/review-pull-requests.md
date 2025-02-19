---
title: Review and comment on pull requests
titleSuffix: Azure Repos
description: Learn how to review pull requests using Git in Azure Repos. Make comments, add suggestions, and vote on changes.
ms.assetid: 4C9DFD24-E894-454A-A080-DA511C90CA74
ms.technology: devops-code-git 
ms.topic: conceptual
ms.author: vijayma
author: vijayma
ms.date: 10/18/2021
monikerRange: '<= azure-devops'
---

# Review pull requests

[!INCLUDE [temp](../includes/version-tfs-2015-cloud.md)]
[!INCLUDE [temp](../includes/version-vs-2015-vs-2019.md)]

Teams can set [branch policies](branch-policies.md) to require pull requests (PRs) on protected branches to meet certain criteria. These criteria can include a minimum number of reviewers, and specific required and optional reviewers.

## Prerequisites

::: moniker range="azure-devops"
- **Repos** must be enabled on your project. If the **Repos** hub and associated pages don't display, see [Turn an Azure DevOps service on or off](../../organizations/settings/set-services.md) to reenable Repos.
 
- To review PRs, you must be a member of the Azure DevOps project the PR is in, with **Basic** access or higher. If you aren't a project member, [get added](../../organizations/accounts/add-organization-users.md).

> [!NOTE]
> For public projects, users granted **Stakeholder** access have full access to Azure Repos.
::: moniker-end

::: moniker range=">= azure-devops-2019 < azure-devops"
- **Repos** must be enabled on your project. If the **Repos** hub and associated pages don't display, see [Turn an Azure DevOps service on or off](../../organizations/settings/set-services.md) to reenable Repos.

- To review PRs, you must be a member of the Azure DevOps project with **Basic** access or higher. If you aren't a project member, [get added](../../organizations/security/add-users-team-project.md).
::: moniker-end

::: moniker range="< azure-devops-2019"
- To view or review PRs, you must be a member of the Azure DevOps project with **Basic** access or higher. If you aren't a project member, [get added](../../organizations/security/add-users-team-project.md).

::: moniker-end

To learn more about permissions and access, see [Default Git repository and branch permissions](../../organizations/security/default-git-permissions.md) and [About access levels](../../organizations/security/access-levels.md).

## Browse changes

- To give reviewers quick picture of PR status, the PR **Overview** tab summarizes branch policies that are passing or failing. In some cases, the summary shows a snippet of the failure message from the check's log. The overview lists only failed policies, but you can see all the passed and failed policy checks by selecting **View \<n> checks**.

  :::image type="content" source="media/review-pull-requests/pull-request-overview-2020.png" alt-text="Screenshot that shows the PR overview tab.":::

  On the PR **Overview** tab, you can review the PR title, description, and comments to understand proposed changes and see issues other reviewers raised.

::: moniker range="azure-devops"
- Select the PR **Files** tab to review the actual changes made in the source branch, **Inline** or **Side-by-side** with the target branch.
  
  You can see how a file will look published by selecting the **View** button on a file, and then selecting **Preview**.
  
  :::image type="content" source="media/review-pull-requests/pull-request-browse-changes-2020.png" alt-text="Screenshot that shows a side-by-side diff view of file changes in a P R.":::
  
  >[!NOTE]
  >When viewing the difference for a *single selected file*, there's a file size limit of 5 MB. To view and diff files larger than 5 MB, you can download the file and view it using a local diff tool. When viewing the difference for a *collection of files*, the size limit for each file is 0.5 MB, for performance reasons.
::: moniker-end

::: moniker range="<= azure-devops-2020"
- Select the PR **Files** tab to view the actual changes made to the source branch next to the target branch of the pull request.
  
  ![PR files](media/review-pull-requests/pull-request-files.png)
  
  >[!NOTE]
  >When viewing the difference for a *single selected file*, there's a file size limit of 5 MB. To view and diff files larger than 5 MB, you can download the file and view it using a local diff tool. When viewing the difference for a *collection of files*, the size limit for each file is 0.5 MB, for performance reasons.
::: moniker-end

::: moniker range="azure-devops"
- You can review previous versions of the code from the **All Changes** drop-down list.
  
  Every update to the branch adds a new version to the list and on the **Updates** tab of the PR. As you select different updates, the diff view updates to show the differences between the files in each version of the PR.

  You can catch up with PR updates after being away from the PR by stepping through changes made since your last review. You can view multiple updates at once by pressing **Shift** while selecting the updates you want to see. 
  
  :::image type="content" source="media/review-pull-requests/pull-request-all-changes-dropdown.png" alt-text="Screenshot that shows the All changes drop-down.":::

::: moniker-end

::: moniker range="<= azure-devops-2020"

- Review previous versions of the code from the **All updates** drop-down list.
  
  ![PR updates](media/review-pull-requests/pull-request-file-updates.png)

  Every update to the branch adds a new version to the list and on the **Updates** tab of the PR. As you select different updates, the diff view updates to show the differences between the files in each version of the PR.

  Catch up with PR updates after being away from the PR by stepping through changes made since your last review.

::: moniker-end

::: moniker range="azure-devops"
- Browse a list of changes from the author on the **Updates** tab.
  
  ![Browse a list of changes from the author.](media/review-pull-requests/new-pull-request-updates.png)

- View and select changes made in commits to the branch on the **Commits** tab.
  
  ![PR commits](media/review-pull-requests/new-pull-request-commits.png)
::: moniker-end

::: moniker range="<= azure-devops-2020"
- Browse a list of changes from the author on the **Updates** tab.
  
  ![Browse a list of changes from the author.](media/review-pull-requests/pull-request-updates.png)

- View and select changes made in commits to the branch on the **Commits** tab.
  
  ![PR commits](media/review-pull-requests/pull-request-commits.png)
::: moniker-end

## Make comments

Add comments to a PR to make suggestions, reply to previous comments, and point out problems with the proposed changes.

::: moniker range="azure-devops"
- Comment inline in the **Files** tab of a PR by hovering over the line you want to comment on and selecting the comment button :::image type="icon" source="./media/review-pull-requests/new-comment-icon.png":::.

  ![Screenshot of comments in Azure Repos P Rs.](./media/review-pull-requests/pr-comments-summary.png)
::: moniker-end

::: moniker range="<= azure-devops-2020"
- Comment inline in the **Files** tab of a PR by hovering over the line you want to comment on and selecting the comment button ![Comment button in a PR](./media/review-pull-requests/pr-comment-icon.png).

  ![Screenshot of comments in Azure Repos P Rs.](./media/review-pull-requests/pr-comments-summary.png)
::: moniker-end

- To suggest changes directly, select the lightbulb icon in the comment interface, make your suggested changes in the code, and then select **Comment**.

  ![Screenshot showing how to make a suggested change.](./media/review-pull-requests/add-suggestion.png)

- Give feedback not tied to a specific code line by commenting on the **Overview** tab.

- Address the author or other reviewers directly in your comments by using `@username`, and reference work items by using `#workitemID`. You can also reference other PRs by using `!pullrequestID`.

## Vote on changes

# [Browser](#tab/browser)
Use the button at upper right in the PR to vote on the PR changes. The default option is **Approve**, but you can select other options from the dropdown list:

- **Approve**: Approve the proposed changes in the PR.
- **Approve with suggestions**: Approve the PR, but provide optional suggestions for improvement.
- **Wait for author**: Don't approve the changes, and ask the author to review your comments. The author should let you know to review the code again after they address your concerns.
- **Reject**: The changes aren't acceptable. Leave a comment in the PR to explain why.
- **Reset feedback**: Remove your vote.

![Screenshot that shows P R voting options.](./media/review-pull-requests/pr-voting-options.png)


# [Visual Studio](#tab/visual-studio)

In Visual Studio 2015, 2017, and 2019, you can access PRs from Visual Studio Team Explorer:

1. [Connect to your project from Visual Studio](../../organizations/projects/connect-to-projects.md).

1. Select **View** > **Team Explorer** to open Team Explorer. You can also press **Ctrl**+**\\**, **Ctrl**+**M**.

1. From **Home**, select **Pull Requests** to view lists of PRs opened by you or assigned to you.

1. To open a PR in the web portal, right-click the PR and select **Open in browser**.

To vote on a PR, open the PR in the browser, and on the **Overview** page, use the button at upper right to vote on the changes.


# [Azure Command Line](#tab/azure-command-line)

::: moniker range=">= azure-devops-2020"

In Azure DevOps Server 2020 and Azure DevOps Services, you can manage PRs and other resources from the [Azure command-line interface (CLI)](/cli/azure/?view=azure-cli-latest&preserve-view=true) with the `azure-devops` extension. For more information about working with the Azure DevOps Services CLI, see [Get started with Azure DevOps CLI](../../cli/index.md).

Many `az devops` commands require `--org` and `--project` parameters. To avoid having to enter these parameters, you can set a default Azure DevOps organization and project with `az devops configure --defaults`.

For example, to set the Fabrikam Fiber project and FabrikamPrime organization as defaults, use:

```azurecli
az devops configure --defaults organization=https://fabrikamprime.visualstudio.com project="Fabrikam Fiber"
```

Once you set the defaults, `az devops` commands use the default organization and project. You can use the `org` and `project` parameters to specify other organizations and projects you have access to.

Azure Repos CLI commands for PRs use [az repos pr](/cli/azure/repos/pr).

To vote whether to approve a PR, use [az repos pr set-vote](/cli/azure/repos/pr#az_repos_pr_set_vote). The vote options are `approve`, `approve-with-suggestions`, `reject`, `reset`, or `wait-for-author`.

For example, to vote to approve PR #21, use:

```azurecli
az repos pr set-vote --id 21 --vote approve
```

::: moniker-end

::: moniker range="<= azure-devops-2019"

The Azure CLI isn't supported in this version. For more information, see [Get started with Azure DevOps CLI](../../cli/index.md).

::: moniker-end


[!INCLUDE [temp](../../includes/note-cli-not-supported.md)]

***


## Next steps

- [Pull request update notifications](pull-request-notifications.md)
- [Respond to comments and complete a pull request](complete-pull-requests.md)
- [About pull requests and permissions](about-pull-requests.md)
