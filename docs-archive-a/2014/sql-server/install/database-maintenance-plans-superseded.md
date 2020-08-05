---
title: 数据库维护计划被取代 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3aea75cc4ecc94ccbaeb1f35cecd0b18ff3a65ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577236"
---
# <a name="database-maintenance-plans-superseded"></a><span data-ttu-id="144fa-102">数据库维护计划被取代</span><span class="sxs-lookup"><span data-stu-id="144fa-102">Database maintenance plans superseded</span></span>
    
## <a name="component"></a><span data-ttu-id="144fa-103">组件</span><span class="sxs-lookup"><span data-stu-id="144fa-103">Component</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="144fa-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理</span><span class="sxs-lookup"><span data-stu-id="144fa-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="144fa-105">说明</span><span class="sxs-lookup"><span data-stu-id="144fa-105">Description</span></span>  
 <span data-ttu-id="144fa-106">现有数据库维护计划已经过升级并可继续使用。</span><span class="sxs-lookup"><span data-stu-id="144fa-106">Existing database maintenance plans are upgraded and continue to work.</span></span> <span data-ttu-id="144fa-107">但是，您无法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 创建新的数据库维护计划。</span><span class="sxs-lookup"><span data-stu-id="144fa-107">However, you will not be able to create new database maintenance plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="144fa-108">若要在对象资源管理器中查看维护计划，请展开“管理”，然后展开“早期”。</span><span class="sxs-lookup"><span data-stu-id="144fa-108">To view the maintenance plans in Object Explorer, expand Management, and then expand Legacy.</span></span> <span data-ttu-id="144fa-109">可以从任何数据库维护计划的上下文菜单中选择 "**迁移**"，将现有数据库维护计划迁移到新的格式。</span><span class="sxs-lookup"><span data-stu-id="144fa-109">You can migrate existing database maintenance plans to the new format by selecting **Migrate** from the context menu for any database maintenance plan.</span></span> <span data-ttu-id="144fa-110">由于新维护计划功能不能直接替代数据库维护计划，因此迁移后某些功能可能会丢失。</span><span class="sxs-lookup"><span data-stu-id="144fa-110">Because the new maintenance plan feature is not a direct replacement of database maintenance plans, some functionality might be lost after migration.</span></span> <span data-ttu-id="144fa-111">迁移数据库维护计划不会删除旧计划，因此可以在删除旧计划之前，先将其作为维护计划对其功能进行测试。</span><span class="sxs-lookup"><span data-stu-id="144fa-111">Migrating a database maintenance plan does not delete the old plan, so you can test its functionality as a maintenance plan before removing the old plan.</span></span>  
  
 <span data-ttu-id="144fa-112">数据库维护计划中不再支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="144fa-112">The following features are no longer supported within database maintenance plans:</span></span>  
  
-   <span data-ttu-id="144fa-113">日志传送</span><span class="sxs-lookup"><span data-stu-id="144fa-113">Log shipping</span></span>  
  
-   <span data-ttu-id="144fa-114">"**数据库完整性检查**" 任务的 "**尝试修复任何次要问题**" 选项</span><span class="sxs-lookup"><span data-stu-id="144fa-114">The **Attempt to repair any minor problems** option of the **Database Integrity Check** task</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="144fa-115">纠正措施</span><span class="sxs-lookup"><span data-stu-id="144fa-115">Corrective Action</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="144fa-116">阻止日志传送包括在数据库维护计划中。</span><span class="sxs-lookup"><span data-stu-id="144fa-116">prevents log shipping from being included in a database maintenance plan.</span></span> <span data-ttu-id="144fa-117">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“日志传送”。</span><span class="sxs-lookup"><span data-stu-id="144fa-117">For more information, see "Log Shipping" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
