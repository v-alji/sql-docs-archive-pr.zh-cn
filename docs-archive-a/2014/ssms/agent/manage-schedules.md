---
title: 管理计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fa18d620d630484815966372d5de83bb52e8caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580542"
---
# <a name="manage-schedules"></a><span data-ttu-id="4e6c2-102">管理计划</span><span class="sxs-lookup"><span data-stu-id="4e6c2-102">Manage Schedules</span></span>
  <span data-ttu-id="4e6c2-103">允许您查看和更改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业计划的属性。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-103">Allows you to view and change properties for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job schedules.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4e6c2-104">选项</span><span class="sxs-lookup"><span data-stu-id="4e6c2-104">Options</span></span>  
 <span data-ttu-id="4e6c2-105">**可用计划**</span><span class="sxs-lookup"><span data-stu-id="4e6c2-105">**Available schedules**</span></span>  
 <span data-ttu-id="4e6c2-106">列出可用于此用户的计划。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-106">Lists the schedules available for this user.</span></span> <span data-ttu-id="4e6c2-107">请注意，作业和计划的所有者必须相同。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-107">Notice that a job and a schedule must have the same owner.</span></span> <span data-ttu-id="4e6c2-108">因此，此列表仅包括该作业所有者所拥有的计划。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-108">Therefore, this list only includes schedules owned by the owner of the job.</span></span>  
  
 <span data-ttu-id="4e6c2-109">**名称**</span><span class="sxs-lookup"><span data-stu-id="4e6c2-109">**Name**</span></span>  
 <span data-ttu-id="4e6c2-110">显示计划的名称。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-110">Displays the name of the schedule.</span></span>  
  
 <span data-ttu-id="4e6c2-111">**已启用**</span><span class="sxs-lookup"><span data-stu-id="4e6c2-111">**Enabled**</span></span>  
 <span data-ttu-id="4e6c2-112">选择此选项可以启用该计划。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-112">Select this option to enable the schedule.</span></span>  
  
 <span data-ttu-id="4e6c2-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="4e6c2-113">**Description**</span></span>  
 <span data-ttu-id="4e6c2-114">描述计划运行作业的条件。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-114">Describes the conditions under which the schedule runs the job.</span></span>  
  
 <span data-ttu-id="4e6c2-115">**计划中的作业**</span><span class="sxs-lookup"><span data-stu-id="4e6c2-115">**Jobs in schedule**</span></span>  
 <span data-ttu-id="4e6c2-116">列出附加到计划的作业编号。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-116">Lists the job numbers attached to the schedule.</span></span> <span data-ttu-id="4e6c2-117">单击编号可以查看相应作业的属性。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-117">Click a number to view the properties of the job.</span></span>  
  
 <span data-ttu-id="4e6c2-118">**新建**</span><span class="sxs-lookup"><span data-stu-id="4e6c2-118">**New**</span></span>  
 <span data-ttu-id="4e6c2-119">单击此按钮可创建新计划。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-119">Click this button to create a new schedule.</span></span>  
  
 <span data-ttu-id="4e6c2-120">**删除**</span><span class="sxs-lookup"><span data-stu-id="4e6c2-120">**Delete**</span></span>  
 <span data-ttu-id="4e6c2-121">单击此按钮可删除所选计划。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-121">Click this button to delete the selected schedule.</span></span>  
  
 <span data-ttu-id="4e6c2-122">**属性**</span><span class="sxs-lookup"><span data-stu-id="4e6c2-122">**Properties**</span></span>  
 <span data-ttu-id="4e6c2-123">单击此按钮可更改所选计划的属性。</span><span class="sxs-lookup"><span data-stu-id="4e6c2-123">Click this button to change the properties of the selected schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e6c2-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e6c2-124">See Also</span></span>  
 [<span data-ttu-id="4e6c2-125">创建计划并将计划附加到作业</span><span class="sxs-lookup"><span data-stu-id="4e6c2-125">Create and Attach Schedules to Jobs</span></span>](create-and-attach-schedules-to-jobs.md)  
  
  
