---
title: 使用升级顾问 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], when to use
- SQL Server Upgrade Advisor, when to use
- when to use Upgrade Advisor
ms.assetid: 5f26a7b9-1ac2-442c-8316-87b078db3baf
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 75a16e57734493cdd7ac00e7bad3124eb7a99d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586073"
---
# <a name="working-with-upgrade-advisor"></a><span data-ttu-id="9ce2c-102">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="9ce2c-102">Working with Upgrade Advisor</span></span>
  <span data-ttu-id="9ce2c-103">为了帮助确保成功升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，升级顾问提供了一个中央控制台，用于确定升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之前要在您的安装中解决的问题。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-103">To help ensure that your upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is successful, Upgrade Advisor provides a central console to identify issues to address in your installations before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="9ce2c-104">可以使用升级顾问来执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="9ce2c-104">You can use Upgrade Advisor to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="9ce2c-105">分析本地服务器或远程服务器上的以前版本的组件。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-105">Analyze previous version's components on local or remote servers.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9ce2c-106">不能分析 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的远程实例。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-106">You cannot analyze remote instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="9ce2c-107">查看分析结果。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-107">View the results of the analysis.</span></span>  
  
 <span data-ttu-id="9ce2c-108">升级顾问包含一个分析器和一个查看器。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-108">Upgrade Advisor includes an analyzer and a viewer.</span></span> <span data-ttu-id="9ce2c-109">升级顾问分析向导会分析您选择的组件。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-109">The Upgrade Advisor Analysis Wizard analyzes the components you select.</span></span> <span data-ttu-id="9ce2c-110">然后，分析器生成有关升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之前必须解决的问题的自定义报表。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-110">The analyzer then generates custom reports about issues that you must handle before you can upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9ce2c-111">可以使用升级顾问报表查看器查看自定义报表。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-111">You use the Upgrade Advisor Report Viewer to view the custom reports.</span></span> <span data-ttu-id="9ce2c-112">有关升级顾问分析检测到的情况的详细信息，请参阅[解决升级问题](../../../2014/sql-server/install/resolving-upgrade-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-112">For more information about what Upgrade Advisor analysis detects, see [Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md).</span></span>  
  
 <span data-ttu-id="9ce2c-113">本节中的主题提供了升级顾问功能概述以及有关如何使用升级顾问和升级顾问报表的信息。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-113">The topics in this section provide an overview of Upgrade Advisor functionality and information about how to use Upgrade Advisor and Upgrade Advisor reports.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ce2c-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="9ce2c-114">In This Section</span></span>  
  
|<span data-ttu-id="9ce2c-115">主题</span><span class="sxs-lookup"><span data-stu-id="9ce2c-115">Topic</span></span>|<span data-ttu-id="9ce2c-116">说明</span><span class="sxs-lookup"><span data-stu-id="9ce2c-116">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9ce2c-117">升级顾问概述</span><span class="sxs-lookup"><span data-stu-id="9ce2c-117">Overview of Upgrade Advisor</span></span>](../../../2014/sql-server/install/overview-of-upgrade-advisor.md)|<span data-ttu-id="9ce2c-118">概要介绍升级过程、升级顾问分析向导以及升级顾问报表查看器。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-118">Provides an overview of the upgrade process, the Upgrade Advisor Analysis Wizard, and the Upgrade Advisor Report Viewer.</span></span>|  
|[<span data-ttu-id="9ce2c-119">升级顾问操作指南主题</span><span class="sxs-lookup"><span data-stu-id="9ce2c-119">Upgrade Advisor How-to Topics</span></span>](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)|<span data-ttu-id="9ce2c-120">提供执行升级顾问常用步骤的说明。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-120">Provides instructions to perform common Upgrade Advisor procedures.</span></span>|  
|[<span data-ttu-id="9ce2c-121">升级顾问用户界面参考</span><span class="sxs-lookup"><span data-stu-id="9ce2c-121">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)|<span data-ttu-id="9ce2c-122">包含按 F1 键或单击升级顾问分析向导页上的 "**帮助**" 时显示的主题。</span><span class="sxs-lookup"><span data-stu-id="9ce2c-122">Contains topics that appear if you press the F1 key or click **Help** on the Upgrade Advisor Analysis Wizard pages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ce2c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ce2c-123">See Also</span></span>  
 <span data-ttu-id="9ce2c-124">[安装升级顾问](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="9ce2c-124">[Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="9ce2c-125">解决升级问题</span><span class="sxs-lookup"><span data-stu-id="9ce2c-125">Resolving Upgrade Issues</span></span>](../../../2014/sql-server/install/resolving-upgrade-issues.md)  
  
  
