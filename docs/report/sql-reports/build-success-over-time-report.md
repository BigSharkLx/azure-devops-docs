---
title: Build Success Over Time report
titleSuffix: Azure DevOps Server 
ms.technology: devops-analytics
ms.topic: reference
description: Displays the status of the last build for each build category run for each day.  
ms.assetid: 1791d80f-91f6-4e4a-a544-a3289a8a39ac
ms.author: kaelli
author: KathrynEE
monikerRange: '< azure-devops'
ms.date: 10/14/2021
---

# Build Success Over Time report

[!INCLUDE [temp](../includes/tfs-report-platform-version.md)]

The Build Success Over Time report provides a pictorial version of the Build Summary report. The Build Success Over Time report displays the status of the last build for each build category run for each day. You can use this report to help track the quality of the code that the team is checking in. Also, for any day on which a build ran, you can view the Build Summary for that day.  
  
> [!IMPORTANT]  
> This report is only applicable for XAML builds, which are deprecated for TFS 2018 and later versions. If your build process isn't based on XAML builds, this report and the TFS Warehouse for builds won't yield any meaningful data.  

 For information about how to access, refresh, or manage reports, see [Reporting Services Reports](reporting-services-reports.md).  
  
> [!NOTE]
>  This report requires that the team project collection that contains your team project was provisioned with SQL Server Reporting Services. This report is not available if ![Report](media/icon_reportte.png "Icon_reportTE") **Reports** does not appear when you open Team Explorer and expand your team project node.  
  
**You can use this report to answer the following questions**:<br /><br /> -   What parts of the project have produced software that is ready to be tested?<br />-   What parts of the project are having trouble with regressions or bad checkins?<br />-   How well is the team testing the code? 
  
## Prerequisites  
  
 To view the report, you must be assigned or belong to a group that has been assigned the **Browser** role in Reporting Services. For more information, see [Add users to team projects](../admin/grant-permissions-to-reports.md).  

<a name="Data"></a>

## Data in the Report  
 The data that appears in the Build Success Over Time report is derived from the data warehouse. The report summarizes build and test results for a set of build definitions in one or more projects over time.  
  
 The chart shows a separate row for each combination of build definition, platform, and configuration. The report shows only those combinations that fall within the filters that you've specified for the report. At a glance, you can determine the success or failure of builds for the time period under review, as the following illustration shows.  
  
 ![Sample Build Success Over Time Report](media/procguid_successdata.png "ProcGuid_SuccessData")  
  
 The daily results of runs of build definitions appear in the colors that the following table describes:  
  
|Build status|Color|Indicates|  
|------------------|-|-----------|---------------|  
|Passed|:::image type="icon" source="media/procguid_buildsuccess_green.png" border="false"::: Green|-   Build succeeded.<br />-   All tests completed successfully.<br />-   Code coverage was good.|  
|Tests Passed, Low Coverage|:::image type="icon" source="media/procguid_buildsuccess_lightgreen.png" border="false"::: Light&nbsp;green|-   Build succeeded.<br />-   All tests completed successfully.<br />-   Code coverage was minimal.|  
|Build Succeeded, No Tests|:::image type="icon" source="media/procguid_buildsuccess_yellow.png" border="false"::: Yellow|-   Build succeeded.<br />-   No tests were run.|  
|Build Failed|:::image type="icon" source="media/procguid_buildsuccess_red.png" border="false"::: Red|-   Build ran but didn't pass.<br />-   At least one test failed that didn't previously fail. Either the test is new or the test passed in previous test runs.|  
|Tests Failed|:::image type="icon" source="media/procguid_buildsuccess_orange.png" border="false"::: Orange|-   Build failed because of a compile error or other error.|  
|No build|:::image type="icon" source="media/procguid_buildsuccess_white.png" border="false"::: White|-   Build wasn't run on this day.|  
  
 You can filter the report in the following ways:  
  
- Change the start and end dates for the report.  
  
- Filter the build definitions by specifying the platforms, configurations, and build definitions to include in the report.  
  
  For more information, see [Filtering the Report](#Changing) later in this article.  
  
### Required build management activities  
 For the Build Success Over Time report to be useful, team members must carry out the following activities to manage builds:  
  
-   **Configure a build system**. To use Team Foundation Build, you must set up a build system.  
  
     For more information, see [Build and Release agents](../../pipelines/agents/agents.md).
  
-   **Create build definitions**. You can create several build definitions, each of which can be run to produce code for a different platform. Also, you can run each build for a different configuration.  
  
     For more information, see [Get started with CI/CD](../../pipelines/create-first-pipeline.md).
  
-   **Run builds regularly**. You can run builds can be run at set intervals or after every check-in. You can schedule regular builds when you use the schedule trigger. For more information, see [Build triggers](../../pipelines/build/triggers.md).
  
    > [!NOTE]
    >  Although a team member can manually rate a build by using Build Explorer, this rating is not reflected in the Build Success Over Time report. The build rating appears in the Build Summary report. For more information, see [Rate the quality of a completed build](/previous-versions/ms181734(v=vs.140)) and [Build Summary](build-summary-report.md).  

<a name="Duration"></a>

## Set the duration of the report  
 To understand the progress that your team is making in your current iteration, the start and end dates for the report must match the dates of your current iteration cycle.  
  
### To change the duration of the iteration  
  
1.  Next to **Iteration Start (Date)** or **Iteration End (Date)**, select the calendar icon, and then select a date.  
  
2.  Select **View Report**.  

<a name="Interpreting"></a>

## Interpreting the report
 You should expect the Build Success Over Time report to vary based on where you are in your product development cycle. Early iterations often show some builds and tests failing. By reviewing the report together with the team early and often, you might be better able to focus efforts toward creating stable builds with high rates of tests passing.  
  
### Questions the report answers  
 You can review the Build Success Over Time report to find answers to these questions:  
  
- How high is the quality of the builds?  
  
- Is the quality improving, deteriorating, or staying constant?  
  
- What parts of the project are ready to test?  
  
- What parts of the project are having trouble with regressions or bad checkins?  
  
- How well is the code tested?  
  
  Team members should review the last column of the Build Success Over Time report to determine whether the most recent builds have passed. If long sections in the report aren't green, project managers and development leads should determine the root of persistent problems.  
  
### Healthy and unhealthy versions of report  
 A healthy Build Success Over Time report will show successive days of green, which indicates builds are passing. An unhealthy version of the report will show long blocks of orange or red. These blocks indicates builds aren't passing or that tests are failing. The following illustration shows some builds are in good shape and some need investigation:  
  
 ![Healthy and Unhealthy version of Build Success](media/procguid_buildsuccess_unhealthy.png "ProcGuid_BuildSuccess_Unhealthy")  

<a name="Changing"></a>

## Filter the report  
 You can filter the Build Success Over Time report in the following ways:  
  
- Change the start and end dates for the report.  
  
- Filter the builds that appear in the report by specifying the platform, configuration, and build definitions to include.  
  
  > [!NOTE]
  >  You can configure build definition to run no tests, some tests, or all tests. The report will vary greatly based on the configuration of the build definitions.  
  
  The following illustration shows the available filters:  
  
  ![Filters for Build Summary report](media/procguid_reports_buildsummary_filters.png "ProcGuid_Reports_BuildSummary_Filters")  
  
  Apply the filters in the sequence that the following procedure specifies. The options that are available with some filters depend on the filters that you applied previously.  
  
### To filter the builds that appear in the report
  
1.  In the **Platform** list, select the check box of each platform to include.  
  
2.  In the **Configuration** list, select the check box of each configuration to include.  
  
3.  In the **Build Definition** list, select the check box of each build definition to include.  
  
4.  Select **View Report**.  
  
## Related articles
 [Reporting Services Reports](reporting-services-reports.md)