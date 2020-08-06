---
title: 新建用户角色 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newrole.f1
ms.assetid: 9f76a235-0b58-479c-8e5b-50588091b71c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 78201c5ebedd0cdb7f8108b9e6effcaa7fbe87b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689741"
---
# <a name="new-user-role-management-studio"></a><span data-ttu-id="870ce-102">新建用户角色 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="870ce-102">New User Role (Management Studio)</span></span>
  <span data-ttu-id="870ce-103">使用此页可以创建项级角色定义。</span><span class="sxs-lookup"><span data-stu-id="870ce-103">Use this page to create an item-level role definition.</span></span> <span data-ttu-id="870ce-104">项级角色定义是一组任务的命名集合，这些任务用于枚举用户对于文件夹、报表、模型、资源和共享数据源可以执行的任务。</span><span class="sxs-lookup"><span data-stu-id="870ce-104">An item-level role definition is a named collection of tasks that enumerate the tasks a user can perform in relation to folders, reports, models, resources, and shared data sources.</span></span> <span data-ttu-id="870ce-105">例如，预定义“浏览者”角色就是属于项级角色定义。该角色可以标识报表最终用户在浏览文件夹和查看报表时可能需要执行的各种操作。</span><span class="sxs-lookup"><span data-stu-id="870ce-105">An example of an item-level role definition is the predefined Browser role that identifies the kinds of actions a report end user might require for navigating folders and viewing reports.</span></span>  
  
 <span data-ttu-id="870ce-106">角色定义的数量不应该很多。</span><span class="sxs-lookup"><span data-stu-id="870ce-106">Role definitions are intended to be few in number.</span></span> <span data-ttu-id="870ce-107">大多数单位都只要求几个角色定义。</span><span class="sxs-lookup"><span data-stu-id="870ce-107">Most organizations only require a few role definitions.</span></span> <span data-ttu-id="870ce-108">但是，如果预定义的角色定义不能满足需要，您可以对其进行修改或创建新的角色定义。</span><span class="sxs-lookup"><span data-stu-id="870ce-108">However, if the predefined role definitions are insufficient, you can vary them or create new ones.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="870ce-109">角色分配仅适用于在本机模式下运行的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="870ce-109">Role definitions are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="870ce-110">如果针对报表服务器配置了 SharePoint 集成，则此页不可用。</span><span class="sxs-lookup"><span data-stu-id="870ce-110">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="870ce-111">选项</span><span class="sxs-lookup"><span data-stu-id="870ce-111">Options</span></span>  
 <span data-ttu-id="870ce-112">**名称**</span><span class="sxs-lookup"><span data-stu-id="870ce-112">**Name**</span></span>  
 <span data-ttu-id="870ce-113">键入角色定义的名称。</span><span class="sxs-lookup"><span data-stu-id="870ce-113">Type the name of the role definition.</span></span> <span data-ttu-id="870ce-114">角色定义名称在报表服务器命名空间中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="870ce-114">A role definition name must be unique within the report server namespace.</span></span> <span data-ttu-id="870ce-115">名称必须至少包含一个字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="870ce-115">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="870ce-116">还可以包含空格和某些符号。</span><span class="sxs-lookup"><span data-stu-id="870ce-116">It can also include spaces and some symbols.</span></span> <span data-ttu-id="870ce-117">在指定名称时请不要使用以下字符：</span><span class="sxs-lookup"><span data-stu-id="870ce-117">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="870ce-118">; ?</span><span class="sxs-lookup"><span data-stu-id="870ce-118">; ?</span></span> <span data-ttu-id="870ce-119">： \@ & = +，$/\*\< ></span><span class="sxs-lookup"><span data-stu-id="870ce-119">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="870ce-120">" /</span><span class="sxs-lookup"><span data-stu-id="870ce-120">" /</span></span>  
  
 <span data-ttu-id="870ce-121">**说明**</span><span class="sxs-lookup"><span data-stu-id="870ce-121">**Description**</span></span>  
 <span data-ttu-id="870ce-122">键入介绍如何使用角色和枚举角色所支持任务的说明。</span><span class="sxs-lookup"><span data-stu-id="870ce-122">Type a description that explains how to use the role and enumerates what the role supports.</span></span>  
  
 <span data-ttu-id="870ce-123">**任务**</span><span class="sxs-lookup"><span data-stu-id="870ce-123">**Task**</span></span>  
 <span data-ttu-id="870ce-124">选择可通过此角色执行的任务。</span><span class="sxs-lookup"><span data-stu-id="870ce-124">Select the tasks that can be performed through this role.</span></span> <span data-ttu-id="870ce-125">不能创建新任务或修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]支持的现有任务。</span><span class="sxs-lookup"><span data-stu-id="870ce-125">You cannot create new tasks or modify the existing tasks that are supported by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="870ce-126">在项级角色定义中只能使用项级任务。</span><span class="sxs-lookup"><span data-stu-id="870ce-126">Only item-level tasks can be used in an item-level role definition.</span></span>  
  
 <span data-ttu-id="870ce-127">**任务说明**</span><span class="sxs-lookup"><span data-stu-id="870ce-127">**Task Description**</span></span>  
 <span data-ttu-id="870ce-128">显示任务说明，其中枚举了任务所支持的操作或权限。</span><span class="sxs-lookup"><span data-stu-id="870ce-128">Shows a description of the task that enumerates the operations or permissions that the task supports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870ce-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="870ce-129">See Also</span></span>  
 <span data-ttu-id="870ce-130">[Management Studio 中报表服务器的 F1 帮助](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="870ce-130">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="870ce-131">角色定义</span><span class="sxs-lookup"><span data-stu-id="870ce-131">Role Definitions</span></span>](../security/role-definitions.md)  
  
  
