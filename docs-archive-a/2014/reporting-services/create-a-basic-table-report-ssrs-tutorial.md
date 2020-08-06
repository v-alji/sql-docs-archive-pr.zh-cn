---
title: 创建基本表报表（SSRS 教程）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02e0f42869a3bfa88e0c6646fd447968c8ba3a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576539"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a><span data-ttu-id="10b9b-102">创建基本表报表（SSRS 教程）</span><span class="sxs-lookup"><span data-stu-id="10b9b-102">Create a Basic Table Report (SSRS Tutorial)</span></span>
  <span data-ttu-id="10b9b-103">本教程旨在帮助用户使用“报表设计器”创建基于 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库的基本表报表。</span><span class="sxs-lookup"><span data-stu-id="10b9b-103">This tutorial is designed to help you create a basic table report based on the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database using Report Designer.</span></span> <span data-ttu-id="10b9b-104">您还可以使用报表生成器或报表向导创建报表。</span><span class="sxs-lookup"><span data-stu-id="10b9b-104">You can also use Report Builder or the Report Wizard to create reports.</span></span> <span data-ttu-id="10b9b-105">在本教程中，您将执行以下操作：创建报表项目、设置连接信息、定义查询、添加表数据区域、对某些字段进行分组和汇总以及预览报表。</span><span class="sxs-lookup"><span data-stu-id="10b9b-105">In this tutorial, you will create a report project, set up connection information, define a query, add a Table data region, group and total some fields, and preview the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10b9b-106">若要完成此教程，您必须在本机模式下运行 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="10b9b-106">To complete this tutorial, you must be running [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in native mode.</span></span> <span data-ttu-id="10b9b-107">如果在 SharePoint 集成模式下运行 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]，则使用报表服务器 URL 的步骤无效。</span><span class="sxs-lookup"><span data-stu-id="10b9b-107">If you are running [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint integrated mode, the steps that use report server URLs do not work.</span></span> <span data-ttu-id="10b9b-108">有关模式的详细信息 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ，请参阅[Reporting Services 报表服务器](reporting-services-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="10b9b-108">For more information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] modes, see [Reporting Services Report Server](reporting-services-report-server.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10b9b-109">要求</span><span class="sxs-lookup"><span data-stu-id="10b9b-109">Requirements</span></span>  
 <span data-ttu-id="10b9b-110">若要使用本教程，您的系统必须安装以下组件：</span><span class="sxs-lookup"><span data-stu-id="10b9b-110">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="10b9b-111">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]数据库引擎。</span><span class="sxs-lookup"><span data-stu-id="10b9b-111">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database engine.</span></span>  
  
-   <span data-ttu-id="10b9b-112">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="10b9b-112">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  <span data-ttu-id="10b9b-113">有关详细信息，请参阅[SQL Server 2012 的艾德作品 (艾德公司 SQL Server 2012) ](https://go.microsoft.com/fwlink/?LinkId=245471) (https://go.microsoft.com/fwlink/?LinkId=245471). 。</span><span class="sxs-lookup"><span data-stu-id="10b9b-113">For more information, see [Adventure Works for SQL Server 2012 (Adventure Works for SQL Server 2012)](https://go.microsoft.com/fwlink/?LinkId=245471) (https://go.microsoft.com/fwlink/?LinkId=245471)..</span></span> <span data-ttu-id="10b9b-114">有关对的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 示例数据库和示例代码的支持的详细信息 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] ，请参阅 CodePlex 网站上的[数据库和示例概述](https://go.microsoft.com/fwlink/?LinkId=110391)。</span><span class="sxs-lookup"><span data-stu-id="10b9b-114">For more information about support for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sample databases and sample code for [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], see [Databases and Samples Overview](https://go.microsoft.com/fwlink/?LinkId=110391) on the CodePlex Web site.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]<span data-ttu-id="10b9b-115">.</span><span class="sxs-lookup"><span data-stu-id="10b9b-115">.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="10b9b-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10b9b-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 <span data-ttu-id="10b9b-117">还必须具有从 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库检索数据的只读权限。</span><span class="sxs-lookup"><span data-stu-id="10b9b-117">You must also have read-only permissions to retrieve data from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="10b9b-118">任务</span><span class="sxs-lookup"><span data-stu-id="10b9b-118">Tasks</span></span>  
 [<span data-ttu-id="10b9b-119">第 1 课：创建报表服务器项目 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="10b9b-119">Lesson 1: Creating a Report Server Project &#40;Reporting Services&#41;</span></span>](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [<span data-ttu-id="10b9b-120">第 2 课：指定连接信息 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="10b9b-120">Lesson 2: Specifying Connection Information &#40;Reporting Services&#41;</span></span>](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [<span data-ttu-id="10b9b-121">第 3 课：为表报表定义数据集 (Reporting Services)。</span><span class="sxs-lookup"><span data-stu-id="10b9b-121">Lesson 3: Defining a Dataset for the Table Report &#40;Reporting Services&#41;</span></span>](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [<span data-ttu-id="10b9b-122">第 4 课：向报表添加表 (Reporting Services)。</span><span class="sxs-lookup"><span data-stu-id="10b9b-122">Lesson 4: Adding a Table to the Report &#40;Reporting Services&#41;</span></span>](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [<span data-ttu-id="10b9b-123">第 5 课：设置报表格式 (Reporting Services)。</span><span class="sxs-lookup"><span data-stu-id="10b9b-123">Lesson 5: Formatting a Report &#40;Reporting Services&#41;</span></span>](lesson-5-formatting-a-report-reporting-services.md)  
  
 [<span data-ttu-id="10b9b-124">第 6 课：添加分组和总计 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="10b9b-124">Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;</span></span>](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  <span data-ttu-id="10b9b-125">查看教程时，建议您将 "**下一步**" 和 "**上**一步" 按钮添加到文档查看器工具栏。</span><span class="sxs-lookup"><span data-stu-id="10b9b-125">When reviewing tutorials, we recommend that you add **Next** and **Previous** buttons to the document viewer toolbar.</span></span> <span data-ttu-id="10b9b-126">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="10b9b-126">For more information, see.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b9b-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10b9b-127">See Also</span></span>  
 [<span data-ttu-id="10b9b-128">Reporting Services 教程 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="10b9b-128">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](reporting-services-tutorials-ssrs.md)  
  
  
