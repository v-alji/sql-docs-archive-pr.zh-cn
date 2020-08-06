---
title: 新建代理配置文件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.newperfprofile.f1
helpviewer_keywords:
- New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1d7848e44585fd35a5b5a33cf431e15de96c9375
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691676"
---
# <a name="new-agent-profile"></a><span data-ttu-id="c3248-102">新建代理配置文件</span><span class="sxs-lookup"><span data-stu-id="c3248-102">New Agent Profile</span></span>
  <span data-ttu-id="c3248-103">使用 **“新建代理配置文件”** 对话框可以创建新的配置文件。</span><span class="sxs-lookup"><span data-stu-id="c3248-103">Use the **New Agent Profile** dialog box to create a new profile.</span></span> <span data-ttu-id="c3248-104">新的配置文件始终基于现有配置文件，但可以进行修改以满足应用程序的要求。</span><span class="sxs-lookup"><span data-stu-id="c3248-104">New profiles are always based on existing profiles, but they can be modified to meet application requirements.</span></span> <span data-ttu-id="c3248-105">创建配置文件之后，可以在 **“代理配置文件”** 对话框中将其应用于现有的和将来的代理作业。</span><span class="sxs-lookup"><span data-stu-id="c3248-105">After a profile has been created, it can be applied to existing and future agent jobs in the **Agent Profiles** dialog box.</span></span> <span data-ttu-id="c3248-106">可在 \<**AgentProfileName> 属性\*\* 对话框中编辑代理参数值。</span><span class="sxs-lookup"><span data-stu-id="c3248-106">Agent parameter values can be edited in the \<**AgentProfileName> Properties\*\* dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c3248-107">选项</span><span class="sxs-lookup"><span data-stu-id="c3248-107">Options</span></span>  
 <span data-ttu-id="c3248-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="c3248-108">**Name**</span></span>  
 <span data-ttu-id="c3248-109">输入配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="c3248-109">Enter a name for the profile.</span></span>  
  
 <span data-ttu-id="c3248-110">**说明**</span><span class="sxs-lookup"><span data-stu-id="c3248-110">**Description**</span></span>  
 <span data-ttu-id="c3248-111">输入配置文件的说明。</span><span class="sxs-lookup"><span data-stu-id="c3248-111">Enter a description for the profile.</span></span>  
  
 <span data-ttu-id="c3248-112">**Parameter**</span><span class="sxs-lookup"><span data-stu-id="c3248-112">**Parameter**</span></span>  
 <span data-ttu-id="c3248-113">配置文件中包含的代理参数。</span><span class="sxs-lookup"><span data-stu-id="c3248-113">The agent parameters included in the profile.</span></span> <span data-ttu-id="c3248-114">新配置文件所基于的配置文件不必为每个参数指定值。</span><span class="sxs-lookup"><span data-stu-id="c3248-114">The profile on which the new profile is based does not necessarily specify a value for each parameter.</span></span> <span data-ttu-id="c3248-115">若要查看对给定代理有效的所有参数，请清除 **“仅显示此配置文件中使用的参数”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="c3248-115">To see all parameters that are valid for a given agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="c3248-116">有关每个参数的说明，请参阅：</span><span class="sxs-lookup"><span data-stu-id="c3248-116">For descriptions of each parameter, see:</span></span>  
  
-   [<span data-ttu-id="c3248-117">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="c3248-117">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
-   [<span data-ttu-id="c3248-118">复制日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="c3248-118">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="c3248-119">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="c3248-119">Replication Distribution Agent</span></span>](agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="c3248-120">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="c3248-120">Replication Merge Agent</span></span>](agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="c3248-121">复制队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="c3248-121">Replication Queue Reader Agent</span></span>](agents/replication-queue-reader-agent.md)  
  
 <span data-ttu-id="c3248-122">**默认值**</span><span class="sxs-lookup"><span data-stu-id="c3248-122">**Default Value**</span></span>  
 <span data-ttu-id="c3248-123">每个代理参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="c3248-123">The default value for each agent parameter.</span></span>  
  
 <span data-ttu-id="c3248-124">**值**</span><span class="sxs-lookup"><span data-stu-id="c3248-124">**Value**</span></span>  
 <span data-ttu-id="c3248-125">为新配置文件所基于的配置文件中的参数指定的值。</span><span class="sxs-lookup"><span data-stu-id="c3248-125">The value specified for the parameter in the profile on which the new profile is based.</span></span> <span data-ttu-id="c3248-126">对要更改的所有参数值，编辑此字段。</span><span class="sxs-lookup"><span data-stu-id="c3248-126">Edit this field for any parameter values you want to change.</span></span>  
  
 <span data-ttu-id="c3248-127">**“仅显示此配置文件中使用的参数”**</span><span class="sxs-lookup"><span data-stu-id="c3248-127">**Show only parameters used in this profile**</span></span>  
 <span data-ttu-id="c3248-128">清除此复选框将会显示给定代理的所有有效参数。</span><span class="sxs-lookup"><span data-stu-id="c3248-128">Clear to show all valid parameters for a given agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3248-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3248-129">See Also</span></span>  
 <span data-ttu-id="c3248-130">[使用复制代理配置文件](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="c3248-130">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="c3248-131">[复制代理概述](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="c3248-131">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="c3248-132">复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="c3248-132">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
