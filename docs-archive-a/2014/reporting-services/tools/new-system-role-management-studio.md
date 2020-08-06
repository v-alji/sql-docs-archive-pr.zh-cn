---
title: 新建系统角色 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a744fc78bdd5ae6ef3a37f96ff5ae8cd10f71a80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689742"
---
# <a name="new-system-role-management-studio"></a><span data-ttu-id="424be-102">新建系统角色 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="424be-102">New System Role (Management Studio)</span></span>
  <span data-ttu-id="424be-103">使用此页可以创建系统级角色定义。</span><span class="sxs-lookup"><span data-stu-id="424be-103">Use this page to create a system-level role definition.</span></span> <span data-ttu-id="424be-104">系统角色定义指定了作为整体应用于报表服务器的一组系统级任务。</span><span class="sxs-lookup"><span data-stu-id="424be-104">A system role definition specifies a set of system-level tasks that apply to a report server as whole.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="424be-105">角色分配仅适用于在本机模式下运行的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="424be-105">Role definitions are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="424be-106">如果针对报表服务器配置了 SharePoint 集成，则此页不可用。</span><span class="sxs-lookup"><span data-stu-id="424be-106">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="424be-107">选项</span><span class="sxs-lookup"><span data-stu-id="424be-107">Options</span></span>  
 <span data-ttu-id="424be-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="424be-108">**Name**</span></span>  
 <span data-ttu-id="424be-109">键入角色定义的名称。</span><span class="sxs-lookup"><span data-stu-id="424be-109">Type the name of the role definition.</span></span> <span data-ttu-id="424be-110">角色定义名称在报表服务器命名空间中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="424be-110">A role definition name must be unique within the report server namespace.</span></span> <span data-ttu-id="424be-111">名称必须至少包含一个字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="424be-111">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="424be-112">还可以包含空格和某些符号。</span><span class="sxs-lookup"><span data-stu-id="424be-112">It can also include spaces and some symbols.</span></span> <span data-ttu-id="424be-113">在指定名称时请不要使用以下字符：</span><span class="sxs-lookup"><span data-stu-id="424be-113">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="424be-114">; ?</span><span class="sxs-lookup"><span data-stu-id="424be-114">; ?</span></span> <span data-ttu-id="424be-115">： \@ & = +，$/\*\< ></span><span class="sxs-lookup"><span data-stu-id="424be-115">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="424be-116">" /</span><span class="sxs-lookup"><span data-stu-id="424be-116">" /</span></span>  
  
 <span data-ttu-id="424be-117">**说明**</span><span class="sxs-lookup"><span data-stu-id="424be-117">**Description**</span></span>  
 <span data-ttu-id="424be-118">提供介绍如何使用角色和枚举角色所支持任务的说明。</span><span class="sxs-lookup"><span data-stu-id="424be-118">Provide a description that explains how to use the role and enumerates what the role supports.</span></span>  
  
 <span data-ttu-id="424be-119">**任务**</span><span class="sxs-lookup"><span data-stu-id="424be-119">**Task**</span></span>  
 <span data-ttu-id="424be-120">选择可通过此角色执行的系统级任务。</span><span class="sxs-lookup"><span data-stu-id="424be-120">Select the system-level tasks that can be performed through this role.</span></span> <span data-ttu-id="424be-121">不能创建新任务或修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]支持的现有任务。</span><span class="sxs-lookup"><span data-stu-id="424be-121">You cannot create new tasks or modify the existing tasks that are supported by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="424be-122">不能为系统角色定义选择项级任务。</span><span class="sxs-lookup"><span data-stu-id="424be-122">You cannot choose item-level tasks for a system role definition.</span></span>  
  
 <span data-ttu-id="424be-123">**任务说明**</span><span class="sxs-lookup"><span data-stu-id="424be-123">**Task Description**</span></span>  
 <span data-ttu-id="424be-124">显示任务说明，其中枚举了任务所支持的操作或权限。</span><span class="sxs-lookup"><span data-stu-id="424be-124">Shows a description of the task that enumerates the operations or permissions that the task supports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="424be-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="424be-125">See Also</span></span>  
 <span data-ttu-id="424be-126">[Management Studio 中报表服务器的 F1 帮助](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="424be-126">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="424be-127">角色定义</span><span class="sxs-lookup"><span data-stu-id="424be-127">Role Definitions</span></span>](../security/role-definitions.md)  
  
  
