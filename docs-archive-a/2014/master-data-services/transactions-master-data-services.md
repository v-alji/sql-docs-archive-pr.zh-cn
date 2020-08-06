---
title: 事务 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], about transactions
- transactions [Master Data Services]
ms.assetid: 4cd2fa6f-9c76-4b7a-ae18-d4e5fd2f03f5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c693b550e0c1adb8f5910d99c7125c85f41abb8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692981"
---
# <a name="transactions-master-data-services"></a><span data-ttu-id="c401f-102">事务 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c401f-102">Transactions (Master Data Services)</span></span>
  <span data-ttu-id="c401f-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，每次对成员执行操作时，都记录一个事务。</span><span class="sxs-lookup"><span data-stu-id="c401f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a transaction is recorded each time action is taken on a member.</span></span> <span data-ttu-id="c401f-104">事务可供所有用户查看并由管理员撤销。</span><span class="sxs-lookup"><span data-stu-id="c401f-104">Transactions can be viewed by all users and reversed by administrators.</span></span> <span data-ttu-id="c401f-105">事务显示执行操作的日期、时间和用户以及其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="c401f-105">Transactions show the date, time, and user who took the action, along with other details.</span></span> <span data-ttu-id="c401f-106">用户可以为事务添加批注，以指示事务发生的时间。</span><span class="sxs-lookup"><span data-stu-id="c401f-106">Users can add an annotation to a transaction, to indicate why a transaction took place.</span></span>  
  
## <a name="when-transaction-are-recorded"></a><span data-ttu-id="c401f-107">何时记录事务</span><span class="sxs-lookup"><span data-stu-id="c401f-107">When Transaction Are Recorded</span></span>  
 <span data-ttu-id="c401f-108">当成员处于以下状态时将对事务进行记录：</span><span class="sxs-lookup"><span data-stu-id="c401f-108">Transactions are recorded when members:</span></span>  
  
-   <span data-ttu-id="c401f-109">已创建、已删除或重新激活。</span><span class="sxs-lookup"><span data-stu-id="c401f-109">Are created, deleted, or reactivated.</span></span>  
  
-   <span data-ttu-id="c401f-110">已更改属性值。</span><span class="sxs-lookup"><span data-stu-id="c401f-110">Have attribute values changed.</span></span>  
  
-   <span data-ttu-id="c401f-111">在层次结构中移动了位置。</span><span class="sxs-lookup"><span data-stu-id="c401f-111">Are moved in a hierarchy.</span></span>  
  
 <span data-ttu-id="c401f-112">当业务规则更改属性值时，不记录事务。</span><span class="sxs-lookup"><span data-stu-id="c401f-112">Transactions are not recorded when business rules change attribute values.</span></span>  
  
## <a name="view-and-manage-transactions"></a><span data-ttu-id="c401f-113">查看和管理事务</span><span class="sxs-lookup"><span data-stu-id="c401f-113">View and Manage Transactions</span></span>  
 <span data-ttu-id="c401f-114">在“资源管理器”\*\*\*\* 功能区域中，可以查看自行创建的事务并为其添加批注（注释）。</span><span class="sxs-lookup"><span data-stu-id="c401f-114">In the **Explorer** functional area, you can view and annotate (add comments to) the transactions that you made yourself.</span></span>  
  
 <span data-ttu-id="c401f-115">在 **“版本管理”** 功能区域中，管理员可以查看其有权访问的模型的所有用户的所有事务，并撤消这些事务中的任意事务。</span><span class="sxs-lookup"><span data-stu-id="c401f-115">In the **Version Management** functional area, administrators can view all transactions for all users for the models they have access to, and reverse any of these transactions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c401f-116">管理员可以查看所有用户的所有事务，除非他们在“版本权限”\*\*\*\* 功能区域应用了只读权限级别。</span><span class="sxs-lookup"><span data-stu-id="c401f-116">Administrators can view all transactions for all users as long as they don't have the read-only permission level applied in the **Version Management** functional area .</span></span> <span data-ttu-id="c401f-117">例如，如果为管理员设置了只读权限和更新权限级别，管理员将无法查看其他用户事务，因为只读权限将优先于更新权限。</span><span class="sxs-lookup"><span data-stu-id="c401f-117">For example, if the read-only permission and update permission level is set for the administrator, the administrator will not be able to see other user transactions because the read-only permission will take precedence over the update permission.</span></span>

## <a name="system-settings"></a><span data-ttu-id="c401f-118">系统设置</span><span class="sxs-lookup"><span data-stu-id="c401f-118">System Settings</span></span>  
 <span data-ttu-id="c401f-119">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中有一个设置影响在暂存记录时是否记录事务。</span><span class="sxs-lookup"><span data-stu-id="c401f-119">There is a setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affects whether or not transactions are recorded when records are staged.</span></span> <span data-ttu-id="c401f-120">该设置只影响 SQL Server 2008 R2。</span><span class="sxs-lookup"><span data-stu-id="c401f-120">This setting affects SQL Server 2008 R2 only.</span></span> <span data-ttu-id="c401f-121">可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中或直接在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库的“系统设置”表中调整此设置。</span><span class="sxs-lookup"><span data-stu-id="c401f-121">You can adjust this setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="c401f-122">有关详细信息，请参阅[系统设置 (Master Data Services)](system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c401f-122">For more information, see [System Settings &#40;Master Data Services&#41;](system-settings-master-data-services.md).</span></span>  
  
 <span data-ttu-id="c401f-123">在将数据导入此版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中时，您可以指定是否在启动存储过程时记录事务。</span><span class="sxs-lookup"><span data-stu-id="c401f-123">When importing data in this version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can specify whether or not to log transactions when initiating the stored procedure.</span></span> <span data-ttu-id="c401f-124">有关详细信息，请参阅[临时存储过程 (Master Data Services)](../../2014/master-data-services/staging-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c401f-124">For more information, see [Staging Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).</span></span>  
  
## <a name="concurrency"></a><span data-ttu-id="c401f-125">并发</span><span class="sxs-lookup"><span data-stu-id="c401f-125">Concurrency</span></span>  
 <span data-ttu-id="c401f-126">如果某个实体值在多个资源管理器会话中同时显示，则可能对同一个值进行并发编辑。</span><span class="sxs-lookup"><span data-stu-id="c401f-126">If a particular entity value is shown simultaneously in more than one Explorer session, concurrent edits to the same value are possible.</span></span> <span data-ttu-id="c401f-127">MDS 不会自动检测并发编辑。</span><span class="sxs-lookup"><span data-stu-id="c401f-127">Concurrent edits will not be detected automatically by MDS.</span></span> <span data-ttu-id="c401f-128">当多个用户从多个会话（例如从多个计算机、多个浏览器选项卡或窗口，或多个用户帐户）使用 Web 浏览器中的 MDS 资源管理器时，就会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="c401f-128">This can occur when multiple users use the MDS Explorer in the Web browser from multiple sessions, for example from multiple computers, multiple browser tabs or windows, or multiple user accounts.</span></span>  
  
 <span data-ttu-id="c401f-129">多个用户可以更新相同的实体值而不会出错（即便启用了事务记录也不影响）。</span><span class="sxs-lookup"><span data-stu-id="c401f-129">More than one user can update the same entity values without error despite transactions being enabled.</span></span> <span data-ttu-id="c401f-130">一段时间内针对该值的最后一次编辑通常优先级最高。</span><span class="sxs-lookup"><span data-stu-id="c401f-130">Typically the last edit to the value in a sequence of time will take precedence.</span></span> <span data-ttu-id="c401f-131">可以在事务历史记录中手工检测到重复编辑冲突，并可由管理员手动解决。</span><span class="sxs-lookup"><span data-stu-id="c401f-131">The duplicate edit conflict can be manually observed in the transaction history and can be reversed manually by the administrator.</span></span> <span data-ttu-id="c401f-132">事务历史记录将为每个会话的相关属性的 **“旧值”** 和 **“新值”** 显示各个事务，但不会在同一个旧值存在多个 **“新值”** 时自动解决冲突。</span><span class="sxs-lookup"><span data-stu-id="c401f-132">The transaction history will show the individual transactions for the **Prior value** and **New value** for the attribute in question from each session, but will not automatically resolve the conflict when multiple **New Values** exist for the same old value.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c401f-133">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c401f-133">Related Tasks</span></span>  
  
|<span data-ttu-id="c401f-134">任务说明</span><span class="sxs-lookup"><span data-stu-id="c401f-134">Task Description</span></span>|<span data-ttu-id="c401f-135">主题</span><span class="sxs-lookup"><span data-stu-id="c401f-135">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="c401f-136">通过撤消事务来撤消操作（仅限管理员）。</span><span class="sxs-lookup"><span data-stu-id="c401f-136">Undo an action by reversing a transaction (administrators only).</span></span>|[<span data-ttu-id="c401f-137">撤消事务 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c401f-137">Reverse a Transaction &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reverse-a-transaction-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="c401f-138">相关内容</span><span class="sxs-lookup"><span data-stu-id="c401f-138">Related Content</span></span>  
  
-   [<span data-ttu-id="c401f-139">管理员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c401f-139">Administrators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/administrators-master-data-services.md)  
  
-   [<span data-ttu-id="c401f-140">批注 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c401f-140">Annotations &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/annotations-master-data-services.md)  
  
  
