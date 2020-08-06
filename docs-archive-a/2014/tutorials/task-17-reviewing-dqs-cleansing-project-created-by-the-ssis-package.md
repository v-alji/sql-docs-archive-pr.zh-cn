---
title: 任务17：查看由 SSIS 包创建的 DQS 清理项目 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0876a0b727e810f8834fcf5445958bf9884a87f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682454"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a><span data-ttu-id="83b3c-102">任务 17：查看由 SSIS 包创建的 DQS 清理项目</span><span class="sxs-lookup"><span data-stu-id="83b3c-102">Task 17: Reviewing DQS Cleansing Project Created by the SSIS package</span></span>
  <span data-ttu-id="83b3c-103">在该任务中，您将打开由 SSIS 包在 DQS 客户端中创建的 DQS 项目，检查清理过程的结果，并可选执行交互式清理和导出结果。</span><span class="sxs-lookup"><span data-stu-id="83b3c-103">In this task, you open the DQS project created by the SSIS package in DQS Client, review the results from the cleansing process, and optionally perform interactive cleansing and export the results.</span></span>  
  
1.  <span data-ttu-id="83b3c-104">启动**Data Quality Client**。</span><span class="sxs-lookup"><span data-stu-id="83b3c-104">Launch **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="83b3c-105">单击 "**管理**" 窗格中的 "**活动监视**"。</span><span class="sxs-lookup"><span data-stu-id="83b3c-105">Click **Activity Monitoring** in the **Administration** pane.</span></span>  
  
3.  <span data-ttu-id="83b3c-106">根据**活动开始时间**对列表排序，以查看最新记录。</span><span class="sxs-lookup"><span data-stu-id="83b3c-106">Sort the list based on **Activity Start Time** to see the latest record.</span></span>  
  
4.  <span data-ttu-id="83b3c-107">请注意，你会看到以下格式的项目名称： **cleanseandcurate.cleanse supplier data.guid**。</span><span class="sxs-lookup"><span data-stu-id="83b3c-107">Notice that you see a name of the project in the following format: **CleanseAndCurate.Cleanse Supplier Data.GUID**.</span></span>  
  
     <span data-ttu-id="83b3c-108">![SSIS 包创建的 DQS 清理项目](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "SSIS 包创建的 DQS 清理项目")</span><span class="sxs-lookup"><span data-stu-id="83b3c-108">![DQS Cleansing Project Created by SSIS Package](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "DQS Cleansing Project Created by SSIS Package")</span></span>  
  
5.  <span data-ttu-id="83b3c-109">请注意，"**处于活动状态**" 字段中的值为 "**活动**"。</span><span class="sxs-lookup"><span data-stu-id="83b3c-109">Notice that the value in the **Is Active** field is **Active**.</span></span>  
  
6.  <span data-ttu-id="83b3c-110">单击底部窗格中的 "**探查器**" 选项卡，查看 SSIS 包执行的清理活动的探查器统计信息。</span><span class="sxs-lookup"><span data-stu-id="83b3c-110">Click **Profiler** tab in the bottom pane to see profiler statistics for the Cleansing activity that the SSIS package performed.</span></span>  
  
7.  <span data-ttu-id="83b3c-111">单击 "**关闭**" 以关闭**管理**屏幕。</span><span class="sxs-lookup"><span data-stu-id="83b3c-111">Click **Close** to close the **Administration** screen.</span></span>  
  
8.  <span data-ttu-id="83b3c-112">在**DQS 客户端**的主页中，单击 "**数据质量项目**" 窗格中的 "**打开数据质量项目**"。</span><span class="sxs-lookup"><span data-stu-id="83b3c-112">In the main page of **DQS Client**, click **Open Data Quality Project** in the **Data Quality Projects** pane.</span></span>  
  
9. <span data-ttu-id="83b3c-113">在项目列表中，选择由 SSIS DQS 清理组件创建的项目。</span><span class="sxs-lookup"><span data-stu-id="83b3c-113">In the list of projects, select the project created by SSIS DQS Cleansing component.</span></span> <span data-ttu-id="83b3c-114">项目的名称应采用以下格式： \*\*cleanseandcurate.cleanse supplier data.guid。 (红色颜色) \*\*。</span><span class="sxs-lookup"><span data-stu-id="83b3c-114">The name of the project should be in format:  **CleanseAndCurate.Cleanse Supplier Data.GUID (in red color)**.</span></span> <span data-ttu-id="83b3c-115">您可能需要根据 "**创建日期**" 列对列表进行排序，并查找最新记录。</span><span class="sxs-lookup"><span data-stu-id="83b3c-115">You may need to sort the list based on **Date Created** column and look for the latest record.</span></span>  
  
10. <span data-ttu-id="83b3c-116">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="83b3c-116">Click **Next**.</span></span>  
  
11. <span data-ttu-id="83b3c-117">您在本教程前面部分的交互式清理中应熟悉 "**管理和查看结果**" 页。</span><span class="sxs-lookup"><span data-stu-id="83b3c-117">The **Manage and View Results** page should be familiar to you from the interactive cleansing you did earlier in this tutorial.</span></span>  
  
12. <span data-ttu-id="83b3c-118">查看清理结果。</span><span class="sxs-lookup"><span data-stu-id="83b3c-118">Review the cleansing results.</span></span> <span data-ttu-id="83b3c-119">在下一页中，您还可以执行交互式清理，并将结果导出到 Excel 文件或数据库中。</span><span class="sxs-lookup"><span data-stu-id="83b3c-119">You can also perform interactive cleansing and export results to an Excel file or to a database in the next page.</span></span>  
  
13. <span data-ttu-id="83b3c-120">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="83b3c-120">Click **Next**.</span></span> <span data-ttu-id="83b3c-121">在此 "**导出**" 页中，您可以将结果导出到 excel 文件、CSV 文件或 SQL 数据库。</span><span class="sxs-lookup"><span data-stu-id="83b3c-121">In this **Export** page, you can export results to an excel file, CSV file, or to a SQL database.</span></span>  
  
14. <span data-ttu-id="83b3c-122">单击 "**完成**" 完成活动。</span><span class="sxs-lookup"><span data-stu-id="83b3c-122">Click **Finish** to finish the activity.</span></span>  
  
15. <span data-ttu-id="83b3c-123">在**DQS 客户端**的主页中，单击 "**管理**" 窗格中的 "**活动监视**"。</span><span class="sxs-lookup"><span data-stu-id="83b3c-123">In the main page of **DQS Client**, click **Activity Monitoring** in the **Administration** pane.</span></span>  
  
16. <span data-ttu-id="83b3c-124">请注意，项目的**IsActive**字段值现在**结束**。</span><span class="sxs-lookup"><span data-stu-id="83b3c-124">Notice that the value of **IsActive** field for the project is **Ended** now.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="83b3c-125">下一步</span><span class="sxs-lookup"><span data-stu-id="83b3c-125">Next Step</span></span>  
 [<span data-ttu-id="83b3c-126">结论</span><span class="sxs-lookup"><span data-stu-id="83b3c-126">Conclusion</span></span>](../../2014/tutorials/conclusion.md)  
  
  
