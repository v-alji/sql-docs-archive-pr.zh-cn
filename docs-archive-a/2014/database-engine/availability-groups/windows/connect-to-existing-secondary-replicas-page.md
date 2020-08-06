---
title: "\"连接到现有的辅助副本\" 页 (添加副本向导和添加数据库向导) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.connecttoreplicas.f1
- sql12.swb.adddatabasewizard.connecttoreplicas.f1
ms.assetid: 850f1bc8-d7d0-425c-bd7b-03f0e9d3348e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 80af8dfebd6e23a923ddf67438edabf9ab0e2f65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688231"
---
# <a name="connect-to-existing-secondary-replicas-page-add-replica-wizard-and-add-databases-wizard"></a><span data-ttu-id="f722f-102">“连接到现有的次要副本”页（添加副本向导和添加数据库向导）</span><span class="sxs-lookup"><span data-stu-id="f722f-102">Connect to Existing Secondary Replicas Page (Add Replica Wizard and Add Databases Wizard)</span></span>
  <span data-ttu-id="f722f-103">帮助主题介绍“连接到现有的次要副本”页的选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f722f-103">This help topic describes the options of the **Connect to Existing Secondary Replicas** page.</span></span> <span data-ttu-id="f722f-104">本主题由 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] 的“ [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] ”和“ [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]”使用。</span><span class="sxs-lookup"><span data-stu-id="f722f-104">This topic is used by the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="f722f-105">**网格列：**</span><span class="sxs-lookup"><span data-stu-id="f722f-105">**Grid columns:**</span></span>  
 <span data-ttu-id="f722f-106">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="f722f-106">**Server Instance**</span></span>  
 <span data-ttu-id="f722f-107">显示将承载可用性副本的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="f722f-107">Displays the name of the server instance that will host the availability replica.</span></span>  
  
 <span data-ttu-id="f722f-108">**连接为**</span><span class="sxs-lookup"><span data-stu-id="f722f-108">**Connected As**</span></span>  
 <span data-ttu-id="f722f-109">显示在建立了连接后连接到服务器实例的帐户。</span><span class="sxs-lookup"><span data-stu-id="f722f-109">Displays the account that is connected to the server instance, once the connection has been established.</span></span> <span data-ttu-id="f722f-110">如果此页对于某一给定的服务器实例显示 **“未连接”**，则您将需要单击 **“连接”** 或 **“全部连接”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="f722f-110">If this column displays "**Not Connected**" for a given server instance, you will need to click either the **Connect** or **Connect All** button.</span></span>  
  
 <span data-ttu-id="f722f-111">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="f722f-111">**Connect**</span></span>  
 <span data-ttu-id="f722f-112">如果此服务器实例正基于与您将需要连接到的其他服务器实例不同的帐户运行，则单击此选项。</span><span class="sxs-lookup"><span data-stu-id="f722f-112">Click if this server instance is running under a different account than other server instances to which you need to connect.</span></span>  
  
 <span data-ttu-id="f722f-113">**“全部连接”**</span><span class="sxs-lookup"><span data-stu-id="f722f-113">**Connect All**</span></span>  
 <span data-ttu-id="f722f-114">仅当您需要连接到的每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例都作为相同用户帐户中的服务运行时，才单击此选项。</span><span class="sxs-lookup"><span data-stu-id="f722f-114">Click only if every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which you need to connect is running as a service in the same user account.</span></span>  
  
 <span data-ttu-id="f722f-115">**取消**</span><span class="sxs-lookup"><span data-stu-id="f722f-115">**Cancel**</span></span>  
 <span data-ttu-id="f722f-116">单击此选项可取消向导操作。</span><span class="sxs-lookup"><span data-stu-id="f722f-116">Click to cancel the wizard.</span></span> <span data-ttu-id="f722f-117">在 **“连接到现有的辅助副本”** 页上，取消此向导将导致其退出而不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="f722f-117">On the **Connect to Existing Secondary Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f722f-118">相关任务</span><span class="sxs-lookup"><span data-stu-id="f722f-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f722f-119">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f722f-119">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f722f-120">使用“将数据库添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f722f-120">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="f722f-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f722f-121">See Also</span></span>  
 [<span data-ttu-id="f722f-122">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="f722f-122">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
