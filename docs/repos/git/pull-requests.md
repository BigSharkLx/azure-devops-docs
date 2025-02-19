---
title: Create a pull request to review and merge code
titleSuffix: Azure Repos
description: Learn how to create pull requests or draft pull requests in Azure Repos using Git, and add details and reviewers. 
ms.assetid: 4C9DFD24-E894-454A-A080-DA511C90CA74
ms.technology: devops-code-git 
ms.topic: conceptual
ms.author: vijayma
author: vijayma
ms.date: 10/18/2021
monikerRange: '<= azure-devops'
---

# Create pull requests

[!INCLUDE [temp](../includes/version-tfs-2015-cloud.md)]
[!INCLUDE [temp](../includes/version-vs-2015-vs-2019.md)]

Create pull requests (PRs) to change, review, and merge code in a [Git project](../../organizations/projects/create-project.md). You can create PRs from branches in the same repository or from branches in your [fork](forks.md) of the repository.

Your team can review the PRs and give feedback on changes before they merge into the main branch. Reviewers can step through the proposed changes, leave comments, and vote to approve or reject the PRs.

For PR guidelines and management considerations, see [About pull requests](about-pull-requests.md).

## Prerequisites

::: moniker range="azure-devops"
- **Repos** must be enabled on your project. If the **Repos** hub and associated pages don't display, see [Turn an Azure DevOps service on or off](../../organizations/settings/set-services.md) to reenable Repos.
- To view or review PRs, you must be a member of an Azure DevOps project with **Basic** access or higher.
  - If you don't have a project, create one or [sign up for free](../../user-guide/sign-up-invite-teammates.md).
  - If you aren't a project member, [get added](../../organizations/accounts/add-organization-users.md).
- To contribute to a PR, you must be a member of the **Readers** security group or have the corresponding permissions.
- To create and complete a PR, you must be a member of the **Contributors** security group or have the corresponding permissions.

> [!NOTE]
> For public projects, users granted **Stakeholder** access have full access to Azure Repos.
::: moniker-end

::: moniker range=">= azure-devops-2019 < azure-devops"
- **Repos** must be enabled on your project. If the **Repos** hub and associated pages don't display, see [Turn an Azure DevOps service on or off](../../organizations/settings/set-services.md) to reenable Repos.
- To view or review PRs, you must be a member of the Azure DevOps project with **Basic** access or higher. If you aren't a project member, [get added](../../organizations/security/add-users-team-project.md).
- To create and complete a PR, you must be a member of the **Contributors** security group, or have the corresponding permissions, in the project you want to change.
- To contribute to a PR, you must be a member of the **Readers** security group or have the corresponding permissions.
::: moniker-end

::: moniker range="< azure-devops-2019"
- To create and complete a PR, you must be a member of the **Contributors** security group or have the corresponding permissions.
- To view or review PRs, you must be a member of an Azure DevOps project with **Basic** access or higher. If you aren't a project member, [get added](../../organizations/security/add-users-team-project.md).
- To contribute to a PR, you must be a member of the **Readers** security group or have the corresponding permissions.

::: moniker-end


Branch policies can automatically include optional or required reviewers in all or certain PRs. You can change optional included reviewers to be required or remove them, but you can't remove reviewers that are required by branch policy. To learn more about setting branch policies and reviewers, see [Improve code quality with branch policies, Automatically include code reviewers](branch-policies.md#include-code-reviewers).

To learn more about permissions and access, see [Default Git repository and branch permissions](../../organizations/security/default-git-permissions.md) and [About access levels](../../organizations/security/access-levels.md).


<a name="create-a-new-pull-request"></a>

## Create a pull request

You can create a new PR from the Azure DevOps project website, from Visual Studio, or from the Azure DevOps CLI.

# [Browser](#tab/browser)

From the Azure DevOps project website, you can create a new PR from:

- [A feature branch pushed to your repo](#from-a-pushed-branch).
- [The Development section in a linked Azure Boards work item](#from-a-linked-work-item).
- [The Pull requests page](#from-the-pull-requests-page).

### From a pushed branch

::: moniker range=">= azure-devops-2019"

After you push or update a feature branch, Azure Repos displays a prompt to create a PR.

- On the **Pull requests** page:

  ![Screenshot that shows the prompt to create a PR on the Pull Requests tab in Azure Repos.](media/pull-requests/create-pr-from-push-new-nav.png)

- On the **Files** page:

  ![Screenshot that shows the prompt to create a PR on the Files tab in Azure Repos.](media/pull-requests/create-pr-from-push-files-tab-new-nav.png)

Select **Create a pull request** to go to a page where you can [enter your PR details](pull-requests.md#finish) and create the PR.

::: moniker-end

::: moniker range="<= tfs-2018"

After you push or update a feature branch, Azure Repos prompts you to create a PR in the **Code** view on the web. This prompt is displayed on **Pull Requests** and **Files**.

![Screenshot that shows the prompt to create a PR on the Pull Requests tab in Azure Repos.](media/pull-requests/create-pr-from-push.png)

![Screenshot that shows the prompt to create a PR on the Files tab in Azure Repos.](media/pull-requests/create-pr-from-push-files-tab.png)

Select **Create a pull request** to go to a page where you can [enter your PR details](pull-requests.md#finish) and create the PR.

::: moniker-end

### From a linked work item

You can create a PR directly from an Azure Boards work item linked to the branch.

1. In Azure Boards, from **Backlogs** or **Queries** in the **Work** view, open a work item that's linked to the branch.
1. In the **Development** area of the work item, select **Create a pull request**.

   ![Screenshot of creating a PR from the Development area of a work item with a linked branch.](media/pull-requests/create-pr-from-work-item.png)

The link takes you to a page where you can [enter your PR details](pull-requests.md#finish) and create the PR.

### From the Pull requests page

You can create PRs for any branch from your project's **Pull requests** page on the web.

1. On the **Repos** > **Pull requests** page, select **New pull request** at upper right.

   ![Screenshot of the New pull request button.](media/pull-requests/new-pr-button.png)

1. Select the branch with the changes and the branch you want to merge the changes into, such as the main branch.

   ![Screenshot of source and target branches for a PR in Azure Repos.](media/pull-requests/pr-branch-targets.png)

1. [Enter your PR details](pull-requests.md#finish) and create the PR.


# [Visual Studio](#tab/visual-studio)

In Visual Studio 2015, 2017, and 2019, you can create PRs from Visual Studio Team Explorer:

1. [Connect to your project from Visual Studio](../../organizations/projects/connect-to-projects.md).

1. Select **View** > **Team Explorer** to open Team Explorer. You can also press **Ctrl**+**\\**, **Ctrl**+**M**.

1. From **Home**, select **Pull Requests** to view lists of PRs opened by you or assigned to you.

1. From the **Pull Requests** view, select **New Pull Request**.

   ![Screenshot of selecting New Pull Request.](media/pull-requests/new-pull-request.png)

1. Select the source and target branches, enter a title and optional description, and select **Create**. 

   ![Screenshot of creating a new PR in Visual Studio Team Explorer.](media/pull-requests/new-pr.png)

1. After the PR is created, select **Open in browser** to open the new PR in the Azure DevOps web portal.

You can also create PRs from the **Branches** view in Team Explorer by right-clicking the branch name and selecting **Create Pull Request**.

![Screenshot of initiating a PR from the Branches view.](media/pull-requests/new-pr-from-branch.png)


# [Azure Command Line](#tab/azure-command-line)

<a id="create-pr" />

::: moniker range=">= azure-devops-2020"

In Azure DevOps Server 2020 and Azure DevOps Services, you can manage PRs and other resources from the [Azure command-line interface (CLI)](/cli/azure/?view=azure-cli-latest&preserve-view=true) with the `azure-devops` extension. For more information about working with the Azure DevOps Services CLI, see [Get started with Azure DevOps CLI](../../cli/index.md).

Many `az devops` commands require `--org` and `--project` parameters. To avoid having to enter these parameters, you can set a default Azure DevOps organization and project with `az devops configure --defaults`.

For example, to set the Fabrikam Fiber project and FabrikamPrime organization as defaults, use:

```azurecli
az devops configure --defaults organization=https://fabrikamprime.visualstudio.com project="Fabrikam Fiber"
```

Once you set the defaults, `az devops` commands use the default organization and project. You can use the `org` and `project` parameters to specify other organizations and projects you have access to.

Azure Repos CLI commands for PRs use [az repos pr](/cli/azure/repos/pr).

To create a new PR in your project, use [az repos pr create](/cli/azure/repos/pr#az_repos_pr_create). The only parameters you need to add are `repository` and `source-branch`. If you don't specify `target-branch`, the PR targets the default branch of the target repository. To open the PR in your browser after creation, use `open`.

For example, the following command creates a PR from the `new` branch to the default `main` branch of the Fabrikam repository, and then opens the PR in the browser:

```azurecli
az repos pr create --repository Fabrikam --source-branch new --open
```

You can specify several other details about PRs at creation. To add details, reviewers, work items, and completion options to the PR at creation, see [Add details to PRs](#add-details-to-prs).

::: moniker-end

[!INCLUDE [temp](../../includes/note-cli-not-supported.md)]

***


<a name="draft-pull-requests"></a>

::: moniker range=">=azure-devops-2019"

## Create draft PRs

If your PR isn't ready for review, you can create a draft PR to indicate work in progress. When the PR is ready for review, you can publish it, and begin or resume the full review process.

Draft PRs have the following differences from published PRs:

- Build validation policies don't run automatically. You can queue build validations manually by selecting the more options menu in the PR.
- Voting is disabled while in draft mode.
- Required reviewers aren't automatically added. Notifications are sent only to reviewers that you explicitly add to the draft PR.
- Draft PRs display in the PR list with a **Draft** badge.

  ![Screenshot showing a draft PR in the PR list.](media/pull-requests/draft-pull-request-badge.png)

::: moniker-end

 
::: moniker range="azure-devops-2019"
> [!NOTE]
> Creating draft PRs requires Azure DevOps Server 2019.1 update or later version.
::: moniker-end

::: moniker range=">=azure-devops-2019"

# [Browser](#tab/browser)

To create a draft PR, select the arrow next to **Create** and select **Create as draft** when creating the PR. You don't have to use title prefixes such as WIP or DO NOT MERGE.

![Screenshot showing Create as draft P R.](media/pull-requests/create-draft-pr.png)

When you're ready to have the PR reviewed and completed, select **Publish** at upper right in the PR. Publishing a PR assigns required reviewers, evaluates policies, and kicks off voting.

![Screenshot showing Publish for a P R.](media/pull-requests/publish-pr.png)

To change an existing published PR to a draft, choose **Mark as draft**. Marking a PR as draft removes all existing votes.

![Screenshot showing Mark as draft.](media/pull-requests/mark-pr-as-draft.png)

# [Visual Studio](#tab/visual-studio)

To set a PR to draft, from the **Pull Requests** view in Team Explorer, right-click the PR and select **Open in browser**. On the PR's **Overview** page, select **Mark as draft**.

# [Azure Command Line](#tab/azure-command-line)

To create a PR as a draft, set the `draft` parameter to `true` when you create the PR. (Requires Azure DevOps Server 2020 or later version.)

For example:

```azurecli
az repos pr create --repository Fabrikam --source-branch new --draft true
```

To set an existing PR to draft, use `az repos pr update --id <PR Id> --draft true`

To remove draft status from a PR, set `draft` to `false`.

***

::: moniker-end


<a name="finish"></a>

## Add details to PRs

# [Browser](#tab/browser)

On the **New pull request** page, enter a **Title** and detailed **Description** of your changes, so others can see what problems the changes solve. As in an existing PR, you can see the **Files** and **Commits** in your PR on separate tabs. You can add reviewers, link work items, and add tags to the PR.

When you're ready to have your changes reviewed, select **Create** to create the PR.

:::moniker range="azure-devops"

:::image type="content" source="media/pull-requests/create-new-pull-request-2020.png" alt-text="Screenshot that shows creating a new P R.":::

:::moniker-end

:::moniker range="<= azure-devops-2020"

:::image type="content" source="media/pull-requests/add-detail-to-pr.png" alt-text="Adding details to a new P R.":::

:::moniker-end

Don't worry if you don't have all of the work items, reviewers, or details ready when you create your PR. You can add or update these items after you create the PR.

### Edit PR title and description

Keep the PR title and description up to date so reviewers can understand the changes in the PR.

You can update the title of an existing PR by selecting the current title and updating the text. Select the **Save** icon to save changes, or select the **Undo** icon to discard the changes.

Edit the PR description by selecting the **Edit** icon in the **Description** section.

:::image type="content" source="media/pull-requests/pull-request-edit-title-description-2020.png" alt-text="Screenshot that shows editing the P R title and selecting the description Edit button.":::
 

### Add tags to a PR

Use tags to show important details and help organize PRs. Tags can communicate extra information to reviewers, such as that the PR is still a work in progress, or is a hotfix for an upcoming release. 

![Screenshot showing P Rs with tags.](media/pull-requests/pull-request-labels.png)

To add a tag when creating a PR, type a tag name in the **Tags** section. After you create the PR, you can manage tags in the **Tags** section.

:::image type="content" source="media/pull-requests/pull-request-tags-section.png" alt-text="Screenshot that shows the P R Tags section highlighted.":::


::: moniker range=">= tfs-2018"

### Apply PR labels

You can communicate extra information about a PR to the reviewers by using labels. Maybe the PR is still a work in progress, or it's a hotfix for an upcoming release. Use labels to communicate important details and help organize PRs.
::: moniker-end
::: moniker range="tfs-2018"

> [!NOTE]
> Using PR labels requires TFS 2018.2 or later version.  
::: moniker-end

::: moniker range=">= tfs-2018"
![Screenshot showing P Rs with labels.](media/pull-requests/pull-request-labels.png)

To add a label when creating a PR, choose **Add label**. After you create a PR, you can manage its labels in the **Labels** section.

![Add P R label](media/pull-requests/add-pull-request-label.png)

::: moniker-end

<a name="add-and-remove-reviewers"></a>

### Add reviewers

::: moniker range=">= azure-devops-2019"

You can add reviewers in the **Reviewers** section of a new or existing PR. You can also make existing optional reviewers required, or change required reviewers to optional or remove them, unless they're required by policy.

If the user or group you want to review the PR isn't a member of your project, you'll need to [add them to the project](../../organizations/security/add-users-team-project.md) before you can add them as reviewers.

To add reviewers to your PR:

- **In a new PR**:

  1. On the **New pull request** page, under **Reviewers**, select **Search users and groups to add as reviewers**.
  1. As you enter a name or email address, a dropdown list shows a list of matching users and groups. Select names from the list to add as optional reviewers.
  1. To add required reviewers, select **Add required reviewers**, and then select **Search to add required reviewers** to search for and select the names.
  
  ![Screenshot of adding a reviewer to a new PR.](media/pull-requests/add-reviewer.png)

- **In an existing PR**:

  1. In the **Reviewers** section of the **Overview** page, select **Add**, and then select **Required reviewer** or **Optional reviewer**.

     :::image type="content" source="media/pull-requests/pull-request-add-reviewer-v2.png" alt-text="Pull request overview":::

  1. As you enter a name or email address, a list of matching users or groups appears. Select the names to add as reviewers.

     :::image type="content" source="media/pull-requests/pull-request-add-reviewer.png" alt-text="Add P R reviewer.":::

  To change a reviewer between required and optional, or remove a reviewer, select **More options** to the right of the reviewer name. To see the membership of a group or team designated as a reviewer, select the group's icon.

Branch policies can automatically include optional or required reviewers in all or certain PRs. You can change optional included reviewers to be required or remove them, but you can't remove reviewers that are required by branch policy.

In the **Reviewers** section of the PR **Overview** page, right-click **More options** next to an automatically included reviewer to see the branch policy that included them.

![Screenshot that shows View policy on a reviewer that's automatically included by branch policy.](media/pull-requests/view-policy.png)

::: moniker-end

<!---

To add reviewers to your PR:

1. Select **Overview** in the PR.

   :::image type="content" source="media/pull-requests/pull-request-overview-reviewers-new-nav.png" alt-text="Screenshot that shows the PR Overview tab":::    

1. Select the **Add** button in the **Reviewers** area.

1. Enter the name of the user or group to add to the reviewer list for the PR. If the user isn't a member of your project, you'll need to [add them](../../organizations/security/add-users-team-project.md).

1. As you enter a name or email address, a list of matching users or groups appears. Select the user or group from the list to add them as a reviewer.

   :::image type="content" source="media/pull-requests/add-pr-reviewer.png" alt-text="Add P R reviewer.":::

-->

::: moniker range="<= tfs-2018"

To add reviewers to your PR:

1. Select the **Overview** tab in the PR.

   ![PR overview](media/pull-requests/pull-request-overview-reviewers.png)

1. Select the add button in the **Reviewers** area. :::image type="icon" source="media/pull-requests/pull-request-add-button.png":::

1. Enter the name of the user or group to add to the reviewer list for the PR. If the user isn't a member of your project, you'll need to [add them](../../organizations/security/add-users-team-project.md).

1. As you enter a name or email address, a list of matching users or groups appears. Select the user or group from the list to add them as a reviewer.

   ![Add PR reviewer](media/pull-requests/add-pr-reviewer.png)

::: moniker-end

<a name="prlinkeditems"></a>
<a name="addworkitemstopr"></a>


### Link work items

::: moniker range=">= azure-devops-2020"

To link work items to your PR:

- **In a new PR**:

  1. On the **New pull request** page, under **Work items to link**, select **Search work items by ID or title**.
  1. Start to enter a work item ID or title, and select the work item to link from the dropdown list that appears.

- I**n an existing PR**:

  1. On the PR **Overview** tab, in the **Work items** area, select **+**.

     :::image type="content" source="media/pull-requests/pull-request-link-work-items-2020.png" alt-text="Screenshot that shows selecting the Overview tab and the work items section.":::

  1. Enter the ID of the work item or search for the work item title. Select the work item from the list that appears.

Remove a work item link by selecting the **x** icon next to the work item. Removing a link only removes the link between the work item and the PR. Links created in the branch or from commits remain in the work item.

::: moniker-end

:::moniker range="azure-devops-2019"

To link work items to your PR:

1. Select the **Overview** tab in the PR.

   :::image type="content" source="media/pull-requests/pull-request-overview-work-items-new-nav.png" alt-text="Screenshot that shows selecting the Overview tab and the link items button.":::

2. Select the add button in the **Work Items** area. ![Add icon in PRs](media/pull-requests/pr_add_icon.png)

3. Enter the ID of the work item or search for work items with titles that match your text. Select the work item from the list that appears.

Remove work item links by selecting the remove button that appears when you hover over the work item. ![remove button](media/pull-requests/pr_remove_icon.png)
Removing a link only removes the link between a work item to a PR. Links created in the branch or from commits stay in the work item.

:::moniker-end

::: moniker range="<= tfs-2018"

To link work items to your PR:

1. Select **Overview** in the PR.

   ![Select Overview in the PR.](media/pull-requests/pull-request-overview-work-items.png)

2. Select the add button in the **Work Items** area. :::image type="icon" source="media/pull-requests/pull-request-add-button.png":::

3. Enter the ID of the work item or search for work items with titles that match your text. Select the work item from the list that appears.

Remove work item links by selecting the remove button that appears when you hover over the work item. ![remove icon](media/pull-requests/pr_remove_icon.png)
Removing a link only removes the link between the work item and the PR. Links created in the branch or from commits stay in the work item.

::: moniker-end


# [Visual Studio](#tab/visual-studio)

When you create a PR in Visual Studio, enter a title and detailed description of your changes so others can see what problems the changes solve. Keep these fields up to date so reviewers can understand the changes in the PR.

To add reviewers, add tags, link work items, or change any details in an existing PR, open the PR in your browser. Right-click the PR from the **Pull Requests** view in Team Explorer, select **Open in browser**, and then make your updates on the PR's **Overview** page.


# [Azure Command Line](#tab/azure-command-line)

<a id="add-details-pr" /> 

::: moniker range=">= azure-devops-2020"

You can add details during PR creation with [az repos pr create](/cli/azure/repos/pr#az_repos_pr_create), or update details in existing PRs with [az repos pr update](/cli/azure/repos/pr#az_repos_pr_update).

### Add or edit title and description

When you create a PR with `az repos pr create`, add a `title` and a detailed `description` of your changes so others can see what problems the changes solve. The `description` parameter accepts Markdown entry, and each value in the argument is a new line of the PR description.

For example:

```azurecli
az repos pr create --repository Fabrikam --source-branch new --title "Update the readme" --description "This PR updates the readme." "These are *new* changes."
```

Keep these fields up to date so reviewers can understand the changes in the PR. To update details of a PR, use `az repos pr update` with the required PR `id` parameter.

For example, to update the title and description for PR #21, use:

```azurecli
az repos pr update --id 21 --description "These updates are *no longer new*." --title "Old updates"
```

### Add reviewers

You can add optional reviewers to a PR at creation with<br>`az repos pr create --reviewer "<Reviewer Name>" "<Another Reviewer>"`.

For example:

```azurecli
az repos pr create --repository Fabrikam --source-branch new --reviewer "[Fabrikam]\Fabrikam Team" "[Fabrikam Fiber]\Web"
```

To add required reviewers, or change reviewers between optional and required, open and update the PR in the browser.

To manage reviewers for an existing PR, use [az repos pr reviewer](/cli/azure/repos/pr/reviewer).

- To add reviewers to an existing PR, use<br>`az repos pr reviewer add --id <PR Id> --reviewer "<Reviewer Name>" "<Another Reviewer>"`.
- To list the reviewers for a PR, use `az repos pr reviewer list --id <PR Id>`.
- To remove reviewers from a PR, use `az repos pr reviewer remove --id <PR Id> --reviewer "<Reviewer Name>"`.

<a id="link-work-items-pr" /> 

### Link work items

You can link Azure Boards work items to PRs at PR creation with `az repos pr create --work-items <Id1> <Id2>`, where \<Id> is the work item's ID.

For example:

```azurecli
az repos pr create --repository Fabrikam --source-branch new --work-items 63 64
```

To manage work items for an existing PR, use [az repos pr work-item](/cli/azure/repos/pr/work-item).

- To link work items to an existing PR, use `az repos pr work-item add --id <PR Id> --work-items <Id1> <Id2>`.
- To list the work items linked to a PR, use `az repos pr work-item list --id <PR Id>`.
- To unlink a work item from a PR, use `az repos pr work-item remove --id <PR Id> --work-items <Id1>`.
  Removing a link only removes the link between the work item and the PR. Links created in the branch or from commits stay in the work item.

::: moniker-end


[!INCLUDE [temp](../../includes/note-cli-not-supported.md)]

***


::: moniker range=">=azure-devops-2019"

<a name="change-the-target-branch-of-a-pull-request"></a>

### Change the target branch of an active PR

For most teams, nearly all PRs target a default branch, such as `main` or `develop`. If you sometimes need to target a different branch, it's easy to forget to change the target branch when you create the PR. If that happens, you can change the target branch of an active PR:

1. Select **More actions** at upper-right on the PR **Overview** page, and then select **Change target branch** from the dropdown menu.
1. In the **Change target branch** pane, select **Choose a target branch**, select the new branch, and then select **Change**.

::: moniker-end


## Next steps

> [!div class="nextstepaction"]
> [Review pull requests](review-pull-requests.md)
 
## Related articles 

- [View pull requests](view-pull-requests.md)
- [Review pull requests](review-pull-requests.md)
- [Pull request update notifications](pull-request-notifications.md)
- [Complete pull requests](complete-pull-requests.md)
- [Change the default branch](change-default-branch.md)
- [Copy changes with cherry-pick](cherry-pick.md)
- [About pull requests and permissions](about-pull-requests.md)
