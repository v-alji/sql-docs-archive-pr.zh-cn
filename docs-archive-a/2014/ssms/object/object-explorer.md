---
title: 对象资源管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.objectexplorer.commandsoptions
- SQL12.SWB.SQLSERVEROBJECTEXPLORER.DHELP
- sql12.swb.objectexplorer.scriptingoptions
- sql12.swb.oe.f1
helpviewer_keywords:
- multi-select [SQL Server Management Studio]
- Registered Servers [SQL Server], Object Explorer
- Query Editor [SQL Server Management Studio], Object Explorer
- connections [SQL Server], SQL Server Management Studio
- servers [SQL Server], Registered Servers
- Object Explorer
- SQL Server Management Studio [SQL Server], connections
- viewing objects
- filtering objects [SQL Server]
- Object Explorer, about Object Explorer
ms.assetid: 469ea8e2-79b9-44c8-bb6f-f0e1c5dbf0f2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3acefcd03af1b39d467625800d8837553ff5253b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587139"
---
# <a name="object-explorer"></a><span data-ttu-id="98fc5-102">“对象资源管理器”</span><span class="sxs-lookup"><span data-stu-id="98fc5-102">Object Explorer</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="98fc5-103">提供用于在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]实例中管理对象的功能。</span><span class="sxs-lookup"><span data-stu-id="98fc5-103">provides features for managing objects in instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="benefits-of-object-explorer"></a><span data-ttu-id="98fc5-104">对象资源管理器的优点</span><span class="sxs-lookup"><span data-stu-id="98fc5-104">Benefits of Object Explorer</span></span>  
 <span data-ttu-id="98fc5-105">对象资源管理器提供一个层次结构用户界面，用于查看和管理每个 SQL Server 实例中的对象。</span><span class="sxs-lookup"><span data-stu-id="98fc5-105">Object Explorer provides a hierarchical user interface to view and manage the objects in each instance of SQL Server.</span></span> <span data-ttu-id="98fc5-106">“对象资源管理器详细信息”窗格显示一个实例对象的表格视图以及用于搜索特定对象的功能。</span><span class="sxs-lookup"><span data-stu-id="98fc5-106">The Object Explorer Details pane presents a tabular view of instance objects, and the capability to search for specific objects.</span></span> <span data-ttu-id="98fc5-107">对象资源管理器的功能根据服务器的类型稍有不同，但一般都包括用于数据库的开发功能和用于所有服务器类型的管理功能。</span><span class="sxs-lookup"><span data-stu-id="98fc5-107">The capabilities of Object Explorer vary slightly depending on the type of server, but generally include the development features for databases, and management features for all server types.</span></span>  
  
## <a name="object-explorer-tasks"></a><span data-ttu-id="98fc5-108">对象资源管理器任务</span><span class="sxs-lookup"><span data-stu-id="98fc5-108">Object Explorer Tasks</span></span>  
  
|<span data-ttu-id="98fc5-109">说明</span><span class="sxs-lookup"><span data-stu-id="98fc5-109">Description</span></span>|<span data-ttu-id="98fc5-110">主题</span><span class="sxs-lookup"><span data-stu-id="98fc5-110">Topic</span></span>|  
|-----------------|-----------|  
|<span data-ttu-id="98fc5-111">介绍如何打开对象资源管理器和配置定义资源管理器的行为的选项。</span><span class="sxs-lookup"><span data-stu-id="98fc5-111">Describes how to open the Object Explorer and configure the options that define the behavior of the explorer.</span></span>|[<span data-ttu-id="98fc5-112">打开和配置对象资源管理器</span><span class="sxs-lookup"><span data-stu-id="98fc5-112">Open and Configure Object Explorer</span></span>](open-and-configure-object-explorer.md)|  
|<span data-ttu-id="98fc5-113">介绍如何将对象资源管理器连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="98fc5-113">Describes how to connect Object Explorer to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>|[<span data-ttu-id="98fc5-114">从对象资源管理器连接到实例</span><span class="sxs-lookup"><span data-stu-id="98fc5-114">Connect to an Instance From Object Explorer</span></span>](connect-to-an-instance-from-object-explorer.md)|  
|<span data-ttu-id="98fc5-115">介绍如何管理在对象资源管理器层次结构中表示为节点的对象。</span><span class="sxs-lookup"><span data-stu-id="98fc5-115">Describes how to manage objects represented as nodes in the Object Explorer hierarchy.</span></span>|[<span data-ttu-id="98fc5-116">使用对象资源管理器管理对象</span><span class="sxs-lookup"><span data-stu-id="98fc5-116">Manage Objects by Using Object Explorer</span></span>](manage-objects-by-using-object-explorer.md)|  
|<span data-ttu-id="98fc5-117">介绍“对象资源管理器详细信息”窗格、服务器中所有对象的表格视图及管理这些对象的用户界面。</span><span class="sxs-lookup"><span data-stu-id="98fc5-117">Describes the Object Explorer Details Pane, a tabular view of all of the objects in the server with a user interface to manage them.</span></span>|[<span data-ttu-id="98fc5-118">对象资源管理器详细信息窗格</span><span class="sxs-lookup"><span data-stu-id="98fc5-118">Object Explorer Details Pane</span></span>](object-explorer-details-pane.md)|  
|<span data-ttu-id="98fc5-119">介绍在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中运行自定义报表的方法。</span><span class="sxs-lookup"><span data-stu-id="98fc5-119">Describes ways to run custom reports in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|[<span data-ttu-id="98fc5-120">Management Studio 中的自定义报告</span><span class="sxs-lookup"><span data-stu-id="98fc5-120">Custom Reports in Management Studio</span></span>](custom-reports-in-management-studio.md)|  
  
  
