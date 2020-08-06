---
title: 升级主服务器之前升级所有目标服务器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 031fedc4af4b058704cef1da8df846397b235305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578012"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a><span data-ttu-id="0619b-102">升级主服务器前先升级所有目标服务器</span><span class="sxs-lookup"><span data-stu-id="0619b-102">Upgrade all target servers before upgrading the master server</span></span>
  <span data-ttu-id="0619b-103">在升级主服务器前，升级正在运行配置为目标服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有计算机。</span><span class="sxs-lookup"><span data-stu-id="0619b-103">Before you upgrade the master server, upgrade all computers that are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are configured as target servers.</span></span>  
  
## <a name="component"></a><span data-ttu-id="0619b-104">组件</span><span class="sxs-lookup"><span data-stu-id="0619b-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0619b-105">代理</span><span class="sxs-lookup"><span data-stu-id="0619b-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="0619b-106">说明</span><span class="sxs-lookup"><span data-stu-id="0619b-106">Description</span></span>  
 <span data-ttu-id="0619b-107">若要在多服务器环境下进行自动管理，您必须至少有一台主服务器和至少一台目标服务器。</span><span class="sxs-lookup"><span data-stu-id="0619b-107">To automate administration in multiserver environments, you must have at least one master server and at least one target server.</span></span> <span data-ttu-id="0619b-108">主服务器将作业分发到目标服务器并从它那里接收事件。</span><span class="sxs-lookup"><span data-stu-id="0619b-108">A master server distributes jobs to, and receives events from, target servers.</span></span> <span data-ttu-id="0619b-109">主服务器还存储在目标服务器上运行的作业的作业定义的中央副本。</span><span class="sxs-lookup"><span data-stu-id="0619b-109">A master server also stores the central copy of job definitions for jobs that are run on target servers.</span></span>  
  
 <span data-ttu-id="0619b-110">如果当前服务器已配置为主服务器，则在升级此主服务器前，请先升级所有目标服务器。</span><span class="sxs-lookup"><span data-stu-id="0619b-110">If the current server is configured as a master server, upgrade all of your target servers first before you upgrade the master server.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="0619b-111">纠正措施</span><span class="sxs-lookup"><span data-stu-id="0619b-111">Corrective Action</span></span>  
 <span data-ttu-id="0619b-112">如果无法在升级主服务器前升级所有目标服务器，则必须先脱离所有目标服务器，再在升级后重新登记这些服务器。</span><span class="sxs-lookup"><span data-stu-id="0619b-112">If you cannot upgrade all target servers before you upgrade the master server, you must defect all target servers and reenlist them after you upgrade.</span></span>  
  
 <span data-ttu-id="0619b-113">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“企业内的自动化管理”、“如何使目标服务器脱离主服务器”以及“如何在主服务器上登记目标服务器”主题。</span><span class="sxs-lookup"><span data-stu-id="0619b-113">For more information, see the topics "Automating Administration across an Enterprise," "How to: Defect a Target Server from a Master Server," and "How to: Enlist a Target Server to a Master" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0619b-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0619b-114">See Also</span></span>  
 <span data-ttu-id="0619b-115">[SQL Server 代理升级问题](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0619b-115">[SQL Server Agent Upgrade Issues](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0619b-116">SQL Server 代理升级问题</span><span class="sxs-lookup"><span data-stu-id="0619b-116">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
