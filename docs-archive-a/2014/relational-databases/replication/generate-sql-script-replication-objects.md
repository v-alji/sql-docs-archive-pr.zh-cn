---
title: 生成 SQL 脚本（复制对象）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.generatesqlscript.f1
helpviewer_keywords:
- Generate SQL Script dialog box
ms.assetid: b7ccc34e-1c22-44b8-8eb5-f6423af3164e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 31a4b318eb3a4c0e5d9f79f43efdcf97c42957f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578081"
---
# <a name="generate-sql-script-replication-objects"></a><span data-ttu-id="4dcd5-102">生成 SQL 脚本（复制对象）</span><span class="sxs-lookup"><span data-stu-id="4dcd5-102">Generate SQL Script (Replication Objects)</span></span>
  <span data-ttu-id="4dcd5-103">复制脚本包含实现已编写脚本的复制组件（如发布或订阅）所需的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-103">A replication script contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures necessary to implement the replication components scripted, such as a publication or subscription.</span></span> <span data-ttu-id="4dcd5-104">制订灾难恢复计划时，应要求对拓扑中的所有复制组件编写脚本，另外，脚本还可以用来自动处理重复性的任务。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-104">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="4dcd5-105">复制提供了两个对话框用以编写复制对象的脚本：</span><span class="sxs-lookup"><span data-stu-id="4dcd5-105">Replication offers two dialog boxes for scripting replication objects:</span></span>  
  
-   <span data-ttu-id="4dcd5-106">“生成 SQL 脚本”对话框，可以在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的“复制”文件夹和所有子文件夹的上下文菜单中找到 。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-106">**Generate SQL Script**, which is available from the context menu of the **Replication** folder and all subfolders in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4dcd5-107">使用此对话框，可以在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上编写所有复制对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-107">This dialog box allows you to script all replication objects on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="4dcd5-108">生成 SQL 脚本 \<ObjectName>，可以在发布和订阅的上下文菜单中找到它。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-108">**Generate SQL Script \<ObjectName>**, which is available from the context menu for publications and subscriptions.</span></span> <span data-ttu-id="4dcd5-109">使用此对话框，可以编写单个对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-109">This dialog box allows you to script individual objects.</span></span>  
  
 <span data-ttu-id="4dcd5-110">这些对话框在单个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上编写对象脚本；并不连接到其他实例编写相关对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-110">These dialog boxes script objects on a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; they do not connect to other instances to script related objects.</span></span>  
  
## <a name="generate-sql-script-options"></a><span data-ttu-id="4dcd5-111">生成 SQL 脚本选项</span><span class="sxs-lookup"><span data-stu-id="4dcd5-111">Generate SQL Script Options</span></span>  
 <span data-ttu-id="4dcd5-112">**分发服务器属性**</span><span class="sxs-lookup"><span data-stu-id="4dcd5-112">**Distributor properties**</span></span>  
 <span data-ttu-id="4dcd5-113">选择此选项可编写存储过程脚本以执行以下操作：启用或禁用分发服务器；添加或删除与分发服务器相关联的发布服务器；创建或删除分发数据库。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-113">Select to script stored procedures to: enable or disable the Distributor; add or drop Publishers associated with the Distributor; and create or drop the distribution database.</span></span>  
  
 <span data-ttu-id="4dcd5-114">**下列数据源中的发布**</span><span class="sxs-lookup"><span data-stu-id="4dcd5-114">**Publications in the following data sources**</span></span>  
 <span data-ttu-id="4dcd5-115">选择此选项可编写存储过程脚本以执行以下操作：启用或禁用发布；以及创建或删除发布、项目、推送订阅和复制作业。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-115">Select to script stored procedures to: enable or disable publishing; and create or drop publications, articles, push subscriptions, and replication jobs.</span></span>  
  
 <span data-ttu-id="4dcd5-116">**下列数据源中的订阅**</span><span class="sxs-lookup"><span data-stu-id="4dcd5-116">**Subscriptions in the following data sources**</span></span>  
 <span data-ttu-id="4dcd5-117">选择此项将编写存储过程脚本，以创建或删除请求订阅和复制作业。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-117">Select to script stored procedures to create or drop pull subscriptions and replication jobs.</span></span>  
  
 <span data-ttu-id="4dcd5-118">**“用于创建或启用组件”** 和 **“用于删除或禁用组件”**</span><span class="sxs-lookup"><span data-stu-id="4dcd5-118">**To create or enable the components** and **To drop or disable the components**</span></span>  
 <span data-ttu-id="4dcd5-119">指定脚本是否应包含用于创建或删除复制对象的命令。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-119">Specify whether the script should include commands for creating or dropping a replication object.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="4dcd5-120">建议使用此对话框创建一组用于启用和禁用组件的脚本。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-120">recommends that you use the dialog box to create a set of scripts for enabling and disabling components.</span></span>  
  
 <span data-ttu-id="4dcd5-121">**复制作业**</span><span class="sxs-lookup"><span data-stu-id="4dcd5-121">**Replication jobs**</span></span>  
 <span data-ttu-id="4dcd5-122">选择此项将编写复制作业脚本（除编写存储过程调用脚本之外）。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-122">Select to script replication jobs in addition to stored procedure calls.</span></span> <span data-ttu-id="4dcd5-123">只有在分发服务器中编写脚本时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-123">This option is available only when scripting from a Distributor.</span></span>  
  
 <span data-ttu-id="4dcd5-124">在执行复制存储过程时将创建必需的作业，因此不需要选择此选项。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-124">Replication stored procedures create the necessary jobs when they are executed, so it is not required to select this option.</span></span> <span data-ttu-id="4dcd5-125">不过，在必须重新创建单个作业时，创建作业记录还是有用的。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-125">However, it can be useful to have a record of the jobs created in case an individual job must be recreated.</span></span>  
  
## <a name="generate-sql-script-objectname-options"></a><span data-ttu-id="4dcd5-126">生成 SQL 脚本 \<ObjectName> 选项</span><span class="sxs-lookup"><span data-stu-id="4dcd5-126">Generate SQL Script \<ObjectName> Options</span></span>  
 <span data-ttu-id="4dcd5-127">**“用于创建或启用组件”** 和 **“用于删除或禁用组件”**</span><span class="sxs-lookup"><span data-stu-id="4dcd5-127">**To create or enable the components** and **To drop or disable the components**</span></span>  
 <span data-ttu-id="4dcd5-128">指定脚本是否应包含用于创建或删除复制对象的命令。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-128">Specify whether the script should include commands for creating or dropping a replication object.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="4dcd5-129">建议使用此对话框来创建一组用于启用和禁用组件的脚本。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-129">recommends that you use the dialog box, creating a set of scripts for enabling and disabling components.</span></span>  
  
 <span data-ttu-id="4dcd5-130">**复制作业**</span><span class="sxs-lookup"><span data-stu-id="4dcd5-130">**Replication jobs**</span></span>  
 <span data-ttu-id="4dcd5-131">只有在 **“生成 SQL 脚本”** 对话框中，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="4dcd5-131">This option is available only from the **Generate SQL Script** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dcd5-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4dcd5-132">See Also</span></span>  
 [<span data-ttu-id="4dcd5-133">编写复制脚本</span><span class="sxs-lookup"><span data-stu-id="4dcd5-133">Scripting Replication</span></span>](scripting-replication.md)  
  
  
