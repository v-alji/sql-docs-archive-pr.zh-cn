---
title: 代理配置文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofiles.f1
helpviewer_keywords:
- Agent Profiles dialog box
ms.assetid: 0422e99c-e688-419b-bb4c-c7bebeef1d8d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7584670088da1ac7a9c81f1f8f0cbdce8b040c7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580154"
---
# <a name="agent-profiles"></a><span data-ttu-id="07737-102">代理配置文件</span><span class="sxs-lookup"><span data-stu-id="07737-102">Agent Profiles</span></span>
  <span data-ttu-id="07737-103">可以使用 **“代理配置文件”** 对话框管理代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="07737-103">Use the **Agent Profiles** dialog box to manage agent profiles.</span></span> <span data-ttu-id="07737-104">代理配置文件为每个代理提供了一种便于管理运行时参数的方法。</span><span class="sxs-lookup"><span data-stu-id="07737-104">Agent profiles provide a convenient way to manage the runtime parameters for each agent.</span></span> <span data-ttu-id="07737-105">每个代理均有一个默认配置文件，某些代理还有附加的预定义配置文件。</span><span class="sxs-lookup"><span data-stu-id="07737-105">Each agent has a default profile, and some agents have additional predefined profiles.</span></span> <span data-ttu-id="07737-106">例如，合并代理有一个为低带宽连接设计的“慢速链接”配置文件。</span><span class="sxs-lookup"><span data-stu-id="07737-106">For example, the Merge Agent has a "slow link" profile designed for low bandwidth connections.</span></span> <span data-ttu-id="07737-107">预定义配置文件对于大多数应用程序已经足够，不过，您仍然可以创建用户定义的配置文件，以便自定义代理行为。</span><span class="sxs-lookup"><span data-stu-id="07737-107">Predefined profiles are sufficient for most applications, but you can also create user-defined profiles, allowing you to customize agent behavior.</span></span>  
  
## <a name="options"></a><span data-ttu-id="07737-108">选项</span><span class="sxs-lookup"><span data-stu-id="07737-108">Options</span></span>  
 <span data-ttu-id="07737-109">**选择页**</span><span class="sxs-lookup"><span data-stu-id="07737-109">**Select a page**</span></span>  
 <span data-ttu-id="07737-110">在左窗格中选择一个代理，此代理的配置文件将显示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="07737-110">Select an agent in the left pane, and the profiles for the agent are displayed in the right pane.</span></span>  
  
 <span data-ttu-id="07737-111">**作为新项的默认值**</span><span class="sxs-lookup"><span data-stu-id="07737-111">**Default for New**</span></span>  
 <span data-ttu-id="07737-112">选择在为给定类型的代理创建作业时将使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="07737-112">Select the profile that will be used when jobs are created for an agent of a given type.</span></span> <span data-ttu-id="07737-113">例如，如果创建指向合并发布的多个订阅，则每个订阅的合并代理作业都将使用选定的配置文件。</span><span class="sxs-lookup"><span data-stu-id="07737-113">For example, if you create a number of subscriptions to a merge publication, the Merge Agent job for each subscription will use the profile selected.</span></span> <span data-ttu-id="07737-114">如果希望更改现有作业的配置文件，请选择一个配置文件，再单击 **“更改现有代理”** 。</span><span class="sxs-lookup"><span data-stu-id="07737-114">If you want to change the profile for existing jobs, select a profile, and then click **Change Existing Agents**.</span></span>  
  
 <span data-ttu-id="07737-115">**名称**</span><span class="sxs-lookup"><span data-stu-id="07737-115">**Name**</span></span>  
 <span data-ttu-id="07737-116">配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="07737-116">The name of the profile.</span></span>  
  
 <span data-ttu-id="07737-117">类型 </span><span class="sxs-lookup"><span data-stu-id="07737-117">**Type**</span></span>  
 <span data-ttu-id="07737-118">配置文件类型： **“用户”** （用户定义）或 **“系统”** （预定义）。</span><span class="sxs-lookup"><span data-stu-id="07737-118">The type of profile: **User** (user-defined) or **System** (predefined).</span></span>  
  
 <span data-ttu-id="07737-119">**属性(...)**</span><span class="sxs-lookup"><span data-stu-id="07737-119">**Properties (...)**</span></span>  
 <span data-ttu-id="07737-120">单击此项可查看用于代理配置文件中每个参数的值。</span><span class="sxs-lookup"><span data-stu-id="07737-120">Click to view the values used for each parameter in the agent profile.</span></span>  
  
 <span data-ttu-id="07737-121">**新建**</span><span class="sxs-lookup"><span data-stu-id="07737-121">**New**</span></span>  
 <span data-ttu-id="07737-122">单击此项可创建一个新的配置文件。</span><span class="sxs-lookup"><span data-stu-id="07737-122">Click to create a new profile.</span></span>  
  
 <span data-ttu-id="07737-123">**删除**</span><span class="sxs-lookup"><span data-stu-id="07737-123">**Delete**</span></span>  
 <span data-ttu-id="07737-124">选择一个用户定义的配置文件，再单击 **“删除”** 可以删除该配置文件。</span><span class="sxs-lookup"><span data-stu-id="07737-124">Select a user-defined profile, and then click **Delete** to delete that profile.</span></span> <span data-ttu-id="07737-125">不能删除预定义的配置文件。</span><span class="sxs-lookup"><span data-stu-id="07737-125">Predefined profiles cannot be deleted.</span></span>  
  
 <span data-ttu-id="07737-126">**“更改现有代理”**</span><span class="sxs-lookup"><span data-stu-id="07737-126">**Change Existing Agents**</span></span>  
 <span data-ttu-id="07737-127">选择一个配置文件，再单击 **“更改现有代理”** 以指定给定类型的代理的所有现有作业都应使用选定的配置文件。</span><span class="sxs-lookup"><span data-stu-id="07737-127">Select a profile, and then click **Change Existing Agents** to specify that all existing jobs for an agent of a given type should use the selected profile.</span></span> <span data-ttu-id="07737-128">例如，如果创建了指向合并发布的多个订阅，并且希望更改配置文件以指定其中每个订阅的合并代理作业都应使用 **“慢速链接代理配置文件”** ，请选择该配置文件，再单击 **“更改现有代理”** 。</span><span class="sxs-lookup"><span data-stu-id="07737-128">For example, if you have created a number of subscriptions to a merge publication, and you want to change the profile to specify that the Merge Agent job for each of these subscriptions should use the **Slow link agent profile**, select that profile, and then click **Change Existing Agents**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07737-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07737-129">See Also</span></span>  
 <span data-ttu-id="07737-130">[使用复制代理配置文件](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="07737-130">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="07737-131">[复制代理概述](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="07737-131">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="07737-132">复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="07737-132">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
