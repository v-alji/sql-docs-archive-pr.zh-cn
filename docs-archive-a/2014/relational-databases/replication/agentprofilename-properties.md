---
title: '&lt;AgentProfileName&gt; 属性 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofileprops.f1
helpviewer_keywords:
- Agent Profile Properties dialog box
ms.assetid: 01a992d2-e4ff-417c-93f0-dc43ab2d1624
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 561f55353b7e40d168266cf5ba531519c8225053
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591299"
---
# <a name="ltagentprofilenamegt-properties"></a><span data-ttu-id="bbec7-102">&lt;AgentProfileName&gt; 属性</span><span class="sxs-lookup"><span data-stu-id="bbec7-102">&lt;AgentProfileName&gt; Properties</span></span>
  <span data-ttu-id="bbec7-103">可以使用 **“代理配置文件属性”** 对话框查看为配置文件中的每个代理参数指定的值，以及修改用户定义的配置文件的值。</span><span class="sxs-lookup"><span data-stu-id="bbec7-103">Use the **Agent Profiles Properties** dialog box to view the values specified for each agent parameter in a profile and to modify the values for user-defined profiles.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bbec7-104">选项</span><span class="sxs-lookup"><span data-stu-id="bbec7-104">Options</span></span>  
 <span data-ttu-id="bbec7-105">**名称**</span><span class="sxs-lookup"><span data-stu-id="bbec7-105">**Name**</span></span>  
 <span data-ttu-id="bbec7-106">配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="bbec7-106">The name of the profile.</span></span>  
  
 <span data-ttu-id="bbec7-107">**说明**</span><span class="sxs-lookup"><span data-stu-id="bbec7-107">**Description**</span></span>  
 <span data-ttu-id="bbec7-108">关于配置文件的说明。</span><span class="sxs-lookup"><span data-stu-id="bbec7-108">A description of the profile.</span></span>  
  
 <span data-ttu-id="bbec7-109">**Parameter**</span><span class="sxs-lookup"><span data-stu-id="bbec7-109">**Parameter**</span></span>  
 <span data-ttu-id="bbec7-110">配置文件中包含的代理参数。</span><span class="sxs-lookup"><span data-stu-id="bbec7-110">The agent parameters included in the profile.</span></span> <span data-ttu-id="bbec7-111">配置文件无需指定每个参数值。</span><span class="sxs-lookup"><span data-stu-id="bbec7-111">Profiles do not necessarily specify a value for each parameter.</span></span> <span data-ttu-id="bbec7-112">若要查看对给定代理有效的所有参数，请清除 **“仅显示此配置文件中使用的参数”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="bbec7-112">To see all parameters that are valid for a given agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="bbec7-113">有关每个参数的说明，请参阅：</span><span class="sxs-lookup"><span data-stu-id="bbec7-113">For descriptions of each parameter, see:</span></span>  
  
-   [<span data-ttu-id="bbec7-114">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="bbec7-114">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
-   [<span data-ttu-id="bbec7-115">复制日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="bbec7-115">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="bbec7-116">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="bbec7-116">Replication Distribution Agent</span></span>](agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="bbec7-117">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="bbec7-117">Replication Merge Agent</span></span>](agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="bbec7-118">复制队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="bbec7-118">Replication Queue Reader Agent</span></span>](agents/replication-queue-reader-agent.md)  
  
 <span data-ttu-id="bbec7-119">**默认值**</span><span class="sxs-lookup"><span data-stu-id="bbec7-119">**Default Value**</span></span>  
 <span data-ttu-id="bbec7-120">每个代理参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="bbec7-120">The default value for each agent parameter.</span></span>  
  
 <span data-ttu-id="bbec7-121">**值**</span><span class="sxs-lookup"><span data-stu-id="bbec7-121">**Value**</span></span>  
 <span data-ttu-id="bbec7-122">配置文件中指定的参数值。</span><span class="sxs-lookup"><span data-stu-id="bbec7-122">The value specified for the parameter in the profile.</span></span> <span data-ttu-id="bbec7-123">对于用户定义的配置文件，此字段是可编辑的。</span><span class="sxs-lookup"><span data-stu-id="bbec7-123">This field is editable for user-defined profiles.</span></span>  
  
 <span data-ttu-id="bbec7-124">**“仅显示此配置文件中使用的参数”**</span><span class="sxs-lookup"><span data-stu-id="bbec7-124">**Show only parameters used in this profile**</span></span>  
 <span data-ttu-id="bbec7-125">清除此复选框将会显示给定代理的所有有效参数。</span><span class="sxs-lookup"><span data-stu-id="bbec7-125">Clear to show all valid parameters for a given agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbec7-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbec7-126">See Also</span></span>  
 <span data-ttu-id="bbec7-127">[使用复制代理配置文件](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="bbec7-127">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="bbec7-128">[复制代理概述](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="bbec7-128">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="bbec7-129">复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="bbec7-129">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
