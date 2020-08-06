---
title: "\"选择数据库\" 页 (新建可用性组向导-添加数据库向导) |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.selectdatabases.f1
- sql12.swb.newagwizard.selectdatabases.f1
ms.assetid: 929c5e15-d087-438d-b1f2-aa97c5f8bff8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c626b8f0953f18a6dd4661124a09b7f542caeb82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693104"
---
# <a name="select-databases-page-new-availability-group-wizard-add-database-wizard"></a><span data-ttu-id="f2156-102">"选择数据库" 页 (新建可用性组向导-添加数据库向导) </span><span class="sxs-lookup"><span data-stu-id="f2156-102">Select Databases Page (New Availability Group Wizard-Add Database Wizard)</span></span>
  <span data-ttu-id="f2156-103">本帮助主题介绍“指定数据库”页的选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2156-103">This help topic describes the options of the **Specify Databases** page.</span></span> <span data-ttu-id="f2156-104">本主题适用于 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 的 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 和 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f2156-104">This topic applies to the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
##  <a name="select-databases-options"></a><a name="PageOptions"></a><span data-ttu-id="f2156-105">选择数据库选项</span><span class="sxs-lookup"><span data-stu-id="f2156-105">Select Databases Options</span></span>  
 <span data-ttu-id="f2156-106">**“此 SQL Server 实例上的用户数据库”** 网格列出每个本地用户数据库。</span><span class="sxs-lookup"><span data-stu-id="f2156-106">The **User databases on this instance of SQL Server** grid lists every local user database.</span></span> <span data-ttu-id="f2156-107">这些列如下所示：</span><span class="sxs-lookup"><span data-stu-id="f2156-107">The columns are as follows:</span></span>  
  
 <span data-ttu-id="f2156-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="f2156-108">**Name**</span></span>  
 <span data-ttu-id="f2156-109">显示本地用户数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f2156-109">Displays the name of a local user database.</span></span>  
  
 <span data-ttu-id="f2156-110">**大小**</span><span class="sxs-lookup"><span data-stu-id="f2156-110">**Size**</span></span>  
 <span data-ttu-id="f2156-111">显示数据库大小（如果在该向导中提供）。</span><span class="sxs-lookup"><span data-stu-id="f2156-111">Displays the database size, if the size is available to the wizard.</span></span>  
  
 <span data-ttu-id="f2156-112">**Status**</span><span class="sxs-lookup"><span data-stu-id="f2156-112">**Status**</span></span>  
 <span data-ttu-id="f2156-113">显示超链接，其中的文本指示给定的数据库是否满足添加到可用性组的先决条件。</span><span class="sxs-lookup"><span data-stu-id="f2156-113">Displays a hyperlink whose text that indicates whether a given database meets the prerequisites for being added to an availability group.</span></span> <span data-ttu-id="f2156-114">如果状态为 **“满足先决条件”**，则可以将该数据库添加到可用性组。</span><span class="sxs-lookup"><span data-stu-id="f2156-114">If the status is "**Meets prerequisites**" you can add the database to the availability group.</span></span> <span data-ttu-id="f2156-115">如果数据库不满足所有先决条件， **“状态”** 超链接将提供关于该数据库为何不符合要求的简短解释。</span><span class="sxs-lookup"><span data-stu-id="f2156-115">If a database does not meet all of the prerequisites, the **Status** hyperlink provides a brief explanation of why the database is ineligible.</span></span> <span data-ttu-id="f2156-116">有关详细信息，请单击该超链接。</span><span class="sxs-lookup"><span data-stu-id="f2156-116">For more information, click the hyperlink.</span></span>  
  
 <span data-ttu-id="f2156-117">在对数据库采取操作以满足先决条件的过程中，您可以在 **“选择数据库”** 页上离开该向导。</span><span class="sxs-lookup"><span data-stu-id="f2156-117">You can leave the wizard on the **Select Database** page while you take action on a database to meet a prerequisite.</span></span> <span data-ttu-id="f2156-118">当您返回 **“选择数据库”** 页时，请单击 **“刷新”** 更新该网格。</span><span class="sxs-lookup"><span data-stu-id="f2156-118">When you return to the **Select Databases** page, click **Refresh** to update the grid.</span></span>  
  
 <span data-ttu-id="f2156-119">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="f2156-119">**Refresh**</span></span>  
 <span data-ttu-id="f2156-120">单击以刷新该网格。</span><span class="sxs-lookup"><span data-stu-id="f2156-120">Click to refresh the grid.</span></span> <span data-ttu-id="f2156-121">对数据库采取操作以满足先决条件后，这样做非常有用。</span><span class="sxs-lookup"><span data-stu-id="f2156-121">This is useful after you take action on a database to meet a prerequisite.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f2156-122">相关任务</span><span class="sxs-lookup"><span data-stu-id="f2156-122">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f2156-123">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f2156-123">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f2156-124">使用“将数据库添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f2156-124">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="f2156-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2156-125">See Also</span></span>  
 <span data-ttu-id="f2156-126">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f2156-126">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="f2156-127">AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;</span><span class="sxs-lookup"><span data-stu-id="f2156-127">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
