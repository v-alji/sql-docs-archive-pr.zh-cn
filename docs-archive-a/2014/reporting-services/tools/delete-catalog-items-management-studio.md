---
title: 删除目录项 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.deleteitems.f1
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d2a1824f2611165c9ae891fcb702418244f3621e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581128"
---
# <a name="delete-catalog-items-management-studio"></a><span data-ttu-id="46f86-102">删除目录项 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="46f86-102">Delete Catalog Items (Management Studio)</span></span>
  <span data-ttu-id="46f86-103">使用此页可以删除共享计划和角色定义。</span><span class="sxs-lookup"><span data-stu-id="46f86-103">Use this page to delete shared schedules and role definitions.</span></span>  
  
 <span data-ttu-id="46f86-104">如果删除由多个报表和订阅使用的共享计划，报表服务器将为以前使用该共享计划的每个报表和订阅都创建一个计划。</span><span class="sxs-lookup"><span data-stu-id="46f86-104">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="46f86-105">每个新计划都将包含已在共享计划中指定的日期、时间和重复执行模式。</span><span class="sxs-lookup"><span data-stu-id="46f86-105">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="46f86-106">请注意， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 不提供对于各个计划的集中管理。</span><span class="sxs-lookup"><span data-stu-id="46f86-106">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="46f86-107">如果删除共享计划，您现在将需要维护每一项的计划信息。</span><span class="sxs-lookup"><span data-stu-id="46f86-107">If you delete a shared schedule, you will now need to maintain the schedule information for each individual item.</span></span> <span data-ttu-id="46f86-108">在删除共享计划之前，请使用 [“报表”页](schedule-properties-reports-page.md) 确定当前哪些报表正在使用该共享计划。</span><span class="sxs-lookup"><span data-stu-id="46f86-108">Before deleting a shared schedule, use the [Reports page](schedule-properties-reports-page.md) to determine which reports are currently using the shared schedule.</span></span>  
  
 <span data-ttu-id="46f86-109">对于角色定义，只能删除当前角色分配中未使用的角色定义。</span><span class="sxs-lookup"><span data-stu-id="46f86-109">For role definitions, you can only delete those that are not actively used in a role assignment.</span></span> <span data-ttu-id="46f86-110">如果您尝试删除当前正在使用的角色，则报表服务器将不删除该角色，您将看到有关该情况的错误消息。</span><span class="sxs-lookup"><span data-stu-id="46f86-110">If you try to delete a role that is currently in use, the report server will not delete the role and you will see an error message to that effect.</span></span> <span data-ttu-id="46f86-111">如果此页只包含一个当前未使用的角色定义，则您单击 **“确定”** 时，该角色定义将被删除。</span><span class="sxs-lookup"><span data-stu-id="46f86-111">If this page contains a single role definition that is not currently in use, it will be deleted when you click **OK**.</span></span> <span data-ttu-id="46f86-112">如果此页包含多个角色，您不能选择要保留或删除哪些角色。</span><span class="sxs-lookup"><span data-stu-id="46f86-112">If this page contains multiple roles, you cannot select which roles to keep or remove.</span></span> <span data-ttu-id="46f86-113">当您单击 **“确定”** 时，将删除所有未使用的角色定义。</span><span class="sxs-lookup"><span data-stu-id="46f86-113">All unused role definitions will be deleted when you click **OK**.</span></span>  
  
 <span data-ttu-id="46f86-114">不能撤消删除操作。</span><span class="sxs-lookup"><span data-stu-id="46f86-114">You cannot undo a delete operation.</span></span> <span data-ttu-id="46f86-115">若要恢复已删除的项，必须重新创建该项或还原报表服务器数据库的备份副本。</span><span class="sxs-lookup"><span data-stu-id="46f86-115">If you want to recover an item that you deleted, you must either recreate it or restore a backup copy of the report server database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="46f86-116">选项</span><span class="sxs-lookup"><span data-stu-id="46f86-116">Options</span></span>  
 <span data-ttu-id="46f86-117">**名称**</span><span class="sxs-lookup"><span data-stu-id="46f86-117">**Name**</span></span>  
 <span data-ttu-id="46f86-118">指定要删除的项的名称。</span><span class="sxs-lookup"><span data-stu-id="46f86-118">Specifies the name of the item you are deleting.</span></span>  
  
 <span data-ttu-id="46f86-119">类型 </span><span class="sxs-lookup"><span data-stu-id="46f86-119">**Type**</span></span>  
 <span data-ttu-id="46f86-120">显示要删除的项的类型。</span><span class="sxs-lookup"><span data-stu-id="46f86-120">Shows the type of item you are deleting.</span></span>  
  
 <span data-ttu-id="46f86-121">**所有者**</span><span class="sxs-lookup"><span data-stu-id="46f86-121">**Owner**</span></span>  
 <span data-ttu-id="46f86-122">显示所有者的名称。</span><span class="sxs-lookup"><span data-stu-id="46f86-122">Shows the name of the owner.</span></span> <span data-ttu-id="46f86-123">在大多数情况下，此名称为 System。</span><span class="sxs-lookup"><span data-stu-id="46f86-123">In most cases, this is System.</span></span>  
  
 <span data-ttu-id="46f86-124">**Status**</span><span class="sxs-lookup"><span data-stu-id="46f86-124">**Status**</span></span>  
 <span data-ttu-id="46f86-125">显示删除操作的进度信息。</span><span class="sxs-lookup"><span data-stu-id="46f86-125">Shows progress information for a delete operation.</span></span>  
  
 <span data-ttu-id="46f86-126">**错误**</span><span class="sxs-lookup"><span data-stu-id="46f86-126">**Error**</span></span>  
 <span data-ttu-id="46f86-127">如果在删除项的过程中出现错误，则显示错误代码。</span><span class="sxs-lookup"><span data-stu-id="46f86-127">Displays an error code if an error occurs while deleting an item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f86-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46f86-128">See Also</span></span>  
 <span data-ttu-id="46f86-129">[删除项 (Management Studio)](delete-an-item-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="46f86-129">[Delete an Item &#40;Management Studio&#41;](delete-an-item-management-studio.md) </span></span>  
 <span data-ttu-id="46f86-130">[Management Studio 中报表服务器的 F1 帮助](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="46f86-130">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="46f86-131">创建、修改和删除计划</span><span class="sxs-lookup"><span data-stu-id="46f86-131">Create, Modify, and Delete Schedules</span></span>](../subscriptions/create-modify-and-delete-schedules.md)  
  
  
