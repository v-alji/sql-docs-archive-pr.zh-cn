---
title: 包含的数据库与 AlwaysOn 可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- contained database [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c8a0b41ee7224dad83fb41691a4898c15b7b38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577854"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a><span data-ttu-id="761b4-102">包含的数据库与 Always On 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="761b4-102">Contained Databases with Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="761b4-103">本主题包含将包含数据库用于 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的相关信息。</span><span class="sxs-lookup"><span data-stu-id="761b4-103">This topic contains information about the using a contained database with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="761b4-104">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="761b4-104">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="761b4-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="761b4-105">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="761b4-106">相关任务</span><span class="sxs-lookup"><span data-stu-id="761b4-106">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="761b4-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="761b4-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="761b4-108">在将包含数据库添加到某一可用性组之前，请确保在承载该可用性组的可用性副本的每个服务器实例上 `contained database authentication` 服务器选项都设置为 `1`。</span><span class="sxs-lookup"><span data-stu-id="761b4-108">Before adding a contained database to an availability group, ensure that the `contained database authentication` server option is set to `1` on every server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="761b4-109">有关详细信息，请参阅 [contained database authentication 服务器配置选项](../../configure-windows/contained-database-authentication-server-configuration-option.md) 和 [服务器配置选项 (SQL Server)](../../configure-windows/server-configuration-options-sql-server.md)的相关信息。</span><span class="sxs-lookup"><span data-stu-id="761b4-109">For more information, see [contained database authentication Server Configuration Option](../../configure-windows/contained-database-authentication-server-configuration-option.md) and [Server Configuration Options &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="761b4-110">相关任务</span><span class="sxs-lookup"><span data-stu-id="761b4-110">Related Tasks</span></span>  
  
-   [<span data-ttu-id="761b4-111">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="761b4-111">Server Configuration Options &#40;SQL Server&#41;</span></span>](../../configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="761b4-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="761b4-112">See Also</span></span>  
 <span data-ttu-id="761b4-113">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="761b4-113">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="761b4-114">包含的数据库</span><span class="sxs-lookup"><span data-stu-id="761b4-114">Contained Databases</span></span>](../../../relational-databases/databases/contained-databases.md)  
  
  
