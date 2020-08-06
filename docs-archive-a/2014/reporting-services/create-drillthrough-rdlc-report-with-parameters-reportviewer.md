---
title: 使用 ReportViewer (SSRS 的参数创建钻取 (.RDLC) 报表) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02864ea8bdd80d6f46b7aad552fa30241322370c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692290"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a><span data-ttu-id="902a2-102">使用 ReportViewer 创建带有参数的钻取 (RDLC) 报表（SSRS 教程）</span><span class="sxs-lookup"><span data-stu-id="902a2-102">Create a Drillthrough (RDLC) Report with Parameters using ReportViewer (SSRS Tutorial)</span></span>
  <span data-ttu-id="902a2-103">[钻取](https://technet.microsoft.com/library/ff519554.aspx) 报表是指用户通过单击其他报表中的链接打开的报表。</span><span class="sxs-lookup"><span data-stu-id="902a2-103">A [drillthrough](https://technet.microsoft.com/library/ff519554.aspx) report is a report that a user opens by clicking a link within another report.</span></span> <span data-ttu-id="902a2-104">钻取报表通常包含某原始汇总报表中所包含的某项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="902a2-104">Drillthrough reports commonly contain details about an item that is contained in an original summary report.</span></span> <span data-ttu-id="902a2-105">本教程将详细介绍以下在 [本地模式报表](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)中使用参数和查询创建钻取报表的课程。</span><span class="sxs-lookup"><span data-stu-id="902a2-105">This tutorial will walk you through the following lessons of creating a drillthrough report with parameters and a query, in [local mode reporting](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="902a2-106">要求</span><span class="sxs-lookup"><span data-stu-id="902a2-106">Requirements</span></span>  
 <span data-ttu-id="902a2-107">若要使用本演练，必须具有访问**AdventureWorks2008**示例数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="902a2-107">To use this walkthrough, you must have access to the **AdventureWorks2008** sample database.</span></span> <span data-ttu-id="902a2-108">本演练中使用的查询也可用于**AdventureWorks2012**数据库。</span><span class="sxs-lookup"><span data-stu-id="902a2-108">The query used in this walkthrough will also work with **AdventureWorks2012** database.</span></span> <span data-ttu-id="902a2-109">有关如何获取**AdventureWorks2008**示例数据库的详细信息，请参阅演练：安装适用于 Microsoft Visual Studio 2010[的 AdventureWorks 数据库](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="902a2-109">For more information about how to get the **AdventureWorks2008** sample database, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) for Microsoft Visual Studio 2010.</span></span>  
  
 <span data-ttu-id="902a2-110">此演练假定你熟悉 Transaction-SQL 查询和 ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) 和 [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) 对象。</span><span class="sxs-lookup"><span data-stu-id="902a2-110">This walkthrough assumes that you are familiar with Transaction-SQL queries and ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) and [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) objects.</span></span>  
  
 <span data-ttu-id="902a2-111">使用 Visual Studio 2010 或 Visual Studio 2012 和 ASP.NET 网站模板创建具有 ReportViewer 控件的 ASP.NET 网页。</span><span class="sxs-lookup"><span data-stu-id="902a2-111">Use Visual Studio 2010, or Visual Studio 2012, and the ASP.NET website template to create an ASP.NET webpage with a ReportViewer control.</span></span> <span data-ttu-id="902a2-112">该控件被配置为查看您创建的报表。</span><span class="sxs-lookup"><span data-stu-id="902a2-112">The control is configured to view a report that you create.</span></span> <span data-ttu-id="902a2-113">对于本演练，您在 Microsoft Visual C# 中创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="902a2-113">For this walkthrough, you create the application in Microsoft Visual C#.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="902a2-114">任务</span><span class="sxs-lookup"><span data-stu-id="902a2-114">Tasks</span></span>  
 <span data-ttu-id="902a2-115">[第1课：创建新网站](../reporting-services/lesson-1-create-a-new-web-site.md) </span><span class="sxs-lookup"><span data-stu-id="902a2-115">[Lesson 1: Create a New Web Site](../reporting-services/lesson-1-create-a-new-web-site.md) </span></span>  
 <span data-ttu-id="902a2-116">[第2课：定义用于父报表的数据连接和数据表](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="902a2-116">[Lesson 2: Define a Data Connection and Data Table for Parent Report](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span></span>  
 <span data-ttu-id="902a2-117">[第3课：使用报表向导设计父报表](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="902a2-117">[Lesson 3: Design the Parent Report using the Report Wizard](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="902a2-118">[第4课：定义用于子报表的数据连接和数据表](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span><span class="sxs-lookup"><span data-stu-id="902a2-118">[Lesson 4: Define a Data Connection and Data Table for Child Report](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span></span>  
 <span data-ttu-id="902a2-119">[第5课：使用报表向导设计子报表](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="902a2-119">[Lesson 5: Design the Child Report using the Report Wizard](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="902a2-120">[第6课：将 ReportViewer 控件添加到应用程序](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="902a2-120">[Lesson 6: Add a ReportViewer Control to the Application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span></span>  
 <span data-ttu-id="902a2-121">[第7课：在父报表上添加钻取操作](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="902a2-121">[Lesson 7: Add Drillthrough Action on Parent Report](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span></span>  
 <span data-ttu-id="902a2-122">[第8课：创建数据筛选器](../reporting-services/lesson-8-create-a-data-filter.md) </span><span class="sxs-lookup"><span data-stu-id="902a2-122">[Lesson 8: Create a Data Filter](../reporting-services/lesson-8-create-a-data-filter.md) </span></span>  
 [<span data-ttu-id="902a2-123">第 9 课：生成并运行应用程序</span><span class="sxs-lookup"><span data-stu-id="902a2-123">Lesson 9: Build and Run the Application</span></span>](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="902a2-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="902a2-124">See Also</span></span>  
 <span data-ttu-id="902a2-125">[Reporting Services 的教程 &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="902a2-125">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md) </span></span>  
 [<span data-ttu-id="902a2-126">使用报表设计器设计报表 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="902a2-126">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
