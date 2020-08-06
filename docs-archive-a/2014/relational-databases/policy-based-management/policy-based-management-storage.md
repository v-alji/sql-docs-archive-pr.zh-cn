---
title: 基于策略的管理存储 | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, storage
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0e775d038c5bb4f7a467f2691e374296f1389d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689330"
---
# <a name="policy-based-management-storage"></a><span data-ttu-id="c4b61-102">基于策略的管理存储</span><span class="sxs-lookup"><span data-stu-id="c4b61-102">Policy-Based Management Storage</span></span>
  <span data-ttu-id="c4b61-103">策略存储在 msdb 数据库中。</span><span class="sxs-lookup"><span data-stu-id="c4b61-103">Policies are stored in the msdb database.</span></span> <span data-ttu-id="c4b61-104">在更改策略或条件后，应对 msdb 进行备份。</span><span class="sxs-lookup"><span data-stu-id="c4b61-104">After a policy or condition is changed, msdb should be backed up.</span></span> <span data-ttu-id="c4b61-105">有关详细信息，请参阅[备份和还原系统数据库 (SQL Server)](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c4b61-105">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
## <a name="storing-policies"></a><span data-ttu-id="c4b61-106">存储策略</span><span class="sxs-lookup"><span data-stu-id="c4b61-106">Storing Policies</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="c4b61-107">包括可用于监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的策略。</span><span class="sxs-lookup"><span data-stu-id="c4b61-107">includes policies that can be used to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c4b61-108">默认情况下，中未安装这些策略 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ; 不过，可以从 C:\Program 文件的默认安装位置 (x86) \MICROSOFT SQL server\120\tools\policies\databaseengine\1033 导入这些策略。</span><span class="sxs-lookup"><span data-stu-id="c4b61-108">By default, these policies are not installed on the [!INCLUDE[ssDE](../../includes/ssde-md.md)]; however, they can be imported from the default installation location of C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.</span></span>  
  
 <span data-ttu-id="c4b61-109">可以使用“文件/新建”  菜单直接创建策略，然后将这些策略保存到文件中。</span><span class="sxs-lookup"><span data-stu-id="c4b61-109">You can directly create policies by using the **File/New** menu, and then saving them to a file.</span></span> <span data-ttu-id="c4b61-110">这样，在未连接到[!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的情况下也可以创建策略。</span><span class="sxs-lookup"><span data-stu-id="c4b61-110">This enables you to create policies when you are not connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="c4b61-111">在当前 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例中评估的策略的策略历史记录保存在 msdb 系统表中。</span><span class="sxs-lookup"><span data-stu-id="c4b61-111">Policy history for policies evaluated in the current instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is maintained in msdb system tables.</span></span> <span data-ttu-id="c4b61-112">不会保留应用于 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的其他实例、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的策略的策略历史记录。</span><span class="sxs-lookup"><span data-stu-id="c4b61-112">Policy history for policies applied to other instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] or applied to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not retained.</span></span>  
  
  
