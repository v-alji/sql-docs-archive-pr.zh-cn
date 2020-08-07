---
title: 代理配置文件（单个代理）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofileagentname.f1
helpviewer_keywords:
- Agent Profile dialog box
ms.assetid: 22713555-c496-4ce1-8ec7-4ae75cfadca8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7def9a6fef4e7e66076ee18552705c6071dab134
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580155"
---
# <a name="agent-profiles-single-agent"></a><span data-ttu-id="2c8e9-102">代理配置文件（单个代理）</span><span class="sxs-lookup"><span data-stu-id="2c8e9-102">Agent Profiles (single agent)</span></span>
  <span data-ttu-id="2c8e9-103">可以使用 **“代理配置文件”** 对话框管理代理的配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-103">Use the **Agent Profiles** dialog box to manage profiles for an agent.</span></span> <span data-ttu-id="2c8e9-104">代理配置文件为每个代理提供了一种便于管理运行时参数的方法。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-104">Agent profiles provide a convenient way to manage the runtime parameters for each agent.</span></span> <span data-ttu-id="2c8e9-105">每个代理均有一个默认配置文件，某些代理还有附加的预定义配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-105">Each agent has a default profile, and some agents have additional predefined profiles.</span></span> <span data-ttu-id="2c8e9-106">例如，合并代理有一个为低带宽连接设计的“慢速链接”配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-106">For example, the Merge Agent has a "slow link" profile designed for low bandwidth connections.</span></span> <span data-ttu-id="2c8e9-107">预定义配置文件对于大多数应用程序已经足够，不过，您仍然可以创建用户定义的配置文件，以便自定义代理行为。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-107">Predefined profiles are sufficient for most applications, but you can also create user-defined profiles, allowing you to customize agent behavior.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2c8e9-108">选项</span><span class="sxs-lookup"><span data-stu-id="2c8e9-108">Options</span></span>  
 <span data-ttu-id="2c8e9-109">**作为新项的默认值**</span><span class="sxs-lookup"><span data-stu-id="2c8e9-109">**Default for New**</span></span>  
 <span data-ttu-id="2c8e9-110">选择在为给定类型的代理创建作业时将使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-110">Select the profile that will be used when jobs are created for an agent of a given type.</span></span> <span data-ttu-id="2c8e9-111">例如，如果创建指向合并发布的多个订阅，则每个订阅的合并代理作业都将使用选定的配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-111">For example, if you create a number of subscriptions to a merge publication, the Merge Agent job for each subscription will use the profile selected.</span></span> <span data-ttu-id="2c8e9-112">如果希望更改现有作业的配置文件，请选择一个配置文件，再单击 **“更改现有代理”** 。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-112">If you want to change the profile for existing jobs, select a profile, and then click **Change Existing Agents**.</span></span>  
  
 <span data-ttu-id="2c8e9-113">**名称**</span><span class="sxs-lookup"><span data-stu-id="2c8e9-113">**Name**</span></span>  
 <span data-ttu-id="2c8e9-114">配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-114">The name of the profile.</span></span>  
  
 <span data-ttu-id="2c8e9-115">类型 </span><span class="sxs-lookup"><span data-stu-id="2c8e9-115">**Type**</span></span>  
 <span data-ttu-id="2c8e9-116">配置文件类型： **“用户”** （用户定义）或 **“系统”** （预定义）。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-116">The type of profile: **User** (user-defined) or **System** (predefined).</span></span>  
  
 <span data-ttu-id="2c8e9-117">**属性(...)**</span><span class="sxs-lookup"><span data-stu-id="2c8e9-117">**Properties (...)**</span></span>  
 <span data-ttu-id="2c8e9-118">单击此项可查看用于代理配置文件中每个参数的值。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-118">Click to view the values used for each parameter in the agent profile.</span></span>  
  
 <span data-ttu-id="2c8e9-119">**新建**</span><span class="sxs-lookup"><span data-stu-id="2c8e9-119">**New**</span></span>  
 <span data-ttu-id="2c8e9-120">单击此项可创建一个新的配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-120">Click to create a new profile.</span></span>  
  
 <span data-ttu-id="2c8e9-121">**删除**</span><span class="sxs-lookup"><span data-stu-id="2c8e9-121">**Delete**</span></span>  
 <span data-ttu-id="2c8e9-122">选择一个用户定义的配置文件，再单击 **“删除”** 可以删除该配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-122">Select a user-defined profile, and then click **Delete** to delete that profile.</span></span> <span data-ttu-id="2c8e9-123">不能删除预定义的配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-123">Predefined profiles cannot be deleted.</span></span>  
  
 <span data-ttu-id="2c8e9-124">**“更改现有代理”**</span><span class="sxs-lookup"><span data-stu-id="2c8e9-124">**Change Existing Agents**</span></span>  
 <span data-ttu-id="2c8e9-125">选择一个配置文件，再单击 **“更改现有代理”** 以指定给定类型的代理的所有现有作业都应使用选定的配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-125">Select a profile, and then click **Change Existing Agents** to specify that all existing jobs for an agent of a given type should use the selected profile.</span></span> <span data-ttu-id="2c8e9-126">例如，如果创建了指向合并发布的多个订阅，并且希望更改配置文件以指定其中每个订阅的合并代理作业都应使用 **“慢速链接代理配置文件”** ，请选择该配置文件，再单击 **“更改现有代理”** 。</span><span class="sxs-lookup"><span data-stu-id="2c8e9-126">For example, if you have created a number of subscriptions to a merge publication, and you want to change the profile to specify that the Merge Agent job for each of these subscriptions should use the **Slow link agent profile**, select that profile, and then click **Change Existing Agents**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c8e9-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c8e9-127">See Also</span></span>  
 <span data-ttu-id="2c8e9-128">[使用复制代理配置文件](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="2c8e9-128">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="2c8e9-129">[复制代理概述](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="2c8e9-129">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="2c8e9-130">复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="2c8e9-130">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
