---
title: “代理 XP”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 541c81ea8d9f782a9c1ea391824b90a6fee772d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588047"
---
# <a name="agent-xps-server-configuration-option"></a><span data-ttu-id="8ce75-102">“代理 XP”服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="8ce75-102">Agent XPs Server Configuration Option</span></span>
  <span data-ttu-id="8ce75-103">使用 **Agent XPs** 选项可以启用此服务器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="8ce75-103">Use the **Agent XPs** option to enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures on this server.</span></span> <span data-ttu-id="8ce75-104">如果禁用此选项，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象资源管理器将不显示 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="8ce75-104">When this option is not enabled, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer.</span></span>  
  
 <span data-ttu-id="8ce75-105">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 工具启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务时，会自动启用这些扩展的存储过程。</span><span class="sxs-lookup"><span data-stu-id="8ce75-105">When you use the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tool to start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, these extended stored procedures are enabled automatically.</span></span> <span data-ttu-id="8ce75-106">有关详细信息，请参阅 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="8ce75-106">For more information, see [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="8ce75-107">除非这些扩展存储过程在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务处于任何状态下都启用，否则对象资源管理器不会显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点的内容。</span><span class="sxs-lookup"><span data-stu-id="8ce75-107">Object Explorer does not display the contents of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent node unless these extended stored procedures are enabled regardless of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service state.</span></span>  
  
 <span data-ttu-id="8ce75-108">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="8ce75-108">The possible values are:</span></span>  
  
-   <span data-ttu-id="8ce75-109">**0**，表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理扩展存储过程不可用（默认值）。</span><span class="sxs-lookup"><span data-stu-id="8ce75-109">**0**, indicating that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures are not available (the default).</span></span>  
  
-   <span data-ttu-id="8ce75-110">**1**，表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理扩展存储过程可用。</span><span class="sxs-lookup"><span data-stu-id="8ce75-110">**1**, indicating that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures are available.</span></span>  
  
 <span data-ttu-id="8ce75-111">该设置立即生效，无需停止并重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="8ce75-111">The setting takes effect immediately without a server stop and restart.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8ce75-112">示例</span><span class="sxs-lookup"><span data-stu-id="8ce75-112">Examples</span></span>  
 <span data-ttu-id="8ce75-113">下面的示例启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="8ce75-113">The following example enables the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ce75-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ce75-114">See Also</span></span>  
 <span data-ttu-id="8ce75-115">[自动执行管理任务（SQL Server 代理）](../../ssms/agent/sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="8ce75-115">[Automated Administration Tasks &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md) </span></span>  
 [<span data-ttu-id="8ce75-116">启动、停止或暂停 SQL Server 代理服务</span><span class="sxs-lookup"><span data-stu-id="8ce75-116">Start, Stop, or Pause the SQL Server Agent Service</span></span>](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
