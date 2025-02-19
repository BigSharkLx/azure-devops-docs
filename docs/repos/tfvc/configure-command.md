---
title: Configure Command
titleSuffix: Azure Repos
description: Configure Command
ms.assetid: c61c2a48-20d4-4452-b6e1-6c1aa3b521ee
ms.technology: devops-code-tfvc
ms.topic: reference
ms.date: 08/10/2016
monikerRange: '>= tfs-2015'
---


# Configure Command

**Azure Repos | Azure DevOps Server 2020 | Azure DevOps Server 2019 | TFS 2018 | TFS 2017 | TFS 2015 | VS 2017 | VS 2015 | VS 2013**

Enables an administrator to view and change the following configuration settings for a project in the **Source Control Settings** dialog box:

-   Check-out settings

-   Check-in policies

-   Check-in notes

**Required Permissions**

To use the **configure** command, you must have the **Edit server-level information** permission set to **Allow**. For more information, see [Permissions and groups reference](../../organizations/security/permissions.md).

```
tf configure [PathOfTeamProject] [/collection:TeamProjectCollectionUrl][/login:username,[password]]
```

## Parameters

### Argument

|**Argument**|**Description**|
|---|---|
|*PathOfTeamProject*|Path of the project whose configuration settings an administrator can view, change, or both.|
|*TeamProjectCollectionUrl*|The URL of the project collection that contains the project that you specified (for example, http://myserver:8080/tfs/DefaultCollection).|
|*username*|Provides a value to the **/login** option. You can specify a username value as either *DOMAIN\UserName* or *UserName.*|


### Option

|**Option**|**Description**|
|---|---|
|**/collection**|Specifies the project collection.|
|**/login**|Specifies the user name and password to authenticate the user with Team Foundation Server.|

## Remarks

You can manage the following project settings using the **configure** command:

-   **Check-out settings** can be used to determine whether multiple users can edit files at the same time. Also, they can be used to configure the get latest on check-out behavior.

-   **Check-in policies** provide controls that are invoked at check-in time, to make sure that defined criteria are met before a user checks in pending changes.

-   **Check-in notes** define custom fields into which users provide information during the check-in process. Check-in notes can be either required or optional.

The settings are configured in the **Source Control Settings** dialog box which appears after you run the **configure** command. When you complete your changes, click **OK** to save them to the server.

For more information about these settings, see [Walkthrough: Customizing Checkin Policies and Notes](/previous-versions/ms181281(v=vs.100)).

For links to other Team Foundation commands that provide additional information about the items in your Team Foundation version control server and all the workspaces that map to it, see [Informational Commands](/previous-versions/visualstudio/visual-studio-2010/ms181450(v=vs.100)).

For more information on how to find the **tf** command-line utility, see [Tf Command-Line Utility Commands](/previous-versions/visualstudio/visual-studio-2010/z51z7zy0(v=vs.100)).

## Examples

The following example displays the **Source** **Control** **Settings** dialog box in which you can examine and modify the project settings of the workspace for the c:\\projects folder.

```
c:\projects>tf configure
```

The following example displays the myproj project settings in the project collection at `http://myserver:8080/tfs/DefaultCollection`.

```
c:\projects>tf configure $/myproj / http://myserver:8080/tfs/DefaultCollection 
```

## See Also

#### Tasks

[Configure Check-Out Settings](configure-check-out-settings.md)

#### Concepts

[Managing File Types](/azure/devops/server/admin/manage-file-types)

#### Other Resources

[Tf Command-Line Utility Commands](/previous-versions/visualstudio/visual-studio-2010/z51z7zy0(v=vs.100))