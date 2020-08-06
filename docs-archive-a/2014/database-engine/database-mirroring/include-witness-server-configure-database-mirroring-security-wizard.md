---
title: 包括见证服务器（配置数据库镜像安全向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 314d2205463436e2182b8d1a4cc0cc972213bd5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578392"
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a><span data-ttu-id="eec7e-102">包括见证服务器（配置数据库镜像安全向导）</span><span class="sxs-lookup"><span data-stu-id="eec7e-102">Include Witness Server (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="eec7e-103">使用此页可以指定是否要将见证服务器包括在数据库镜像的安全配置中。</span><span class="sxs-lookup"><span data-stu-id="eec7e-103">Use this page to specify whether you want to include a witness server in this security configuration for database mirroring.</span></span>  
  
 <span data-ttu-id="eec7e-104">**使用 SQL Server Management Studio 配置数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="eec7e-104">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="eec7e-105">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="eec7e-105">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="eec7e-106">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="eec7e-106">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="eec7e-107">选项</span><span class="sxs-lookup"><span data-stu-id="eec7e-107">Options</span></span>  
 <span data-ttu-id="eec7e-108">**是**</span><span class="sxs-lookup"><span data-stu-id="eec7e-108">**Yes**</span></span>  
 <span data-ttu-id="eec7e-109">单击此项可将见证服务器实例包括在安全配置中。</span><span class="sxs-lookup"><span data-stu-id="eec7e-109">Click to include a witness server instance in the security configuration.</span></span> <span data-ttu-id="eec7e-110">对于具有自动故障转移的高安全性模式，见证服务器是必需的，因为如果主体服务器实例失败，见证服务器将提供到镜像服务器实例的自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="eec7e-110">The witness is necessary for high-safety mode with automatic failover, which supports automatic failover to the mirror server instance if the principal server instance fails.</span></span>  
  
 <span data-ttu-id="eec7e-111">**否**</span><span class="sxs-lookup"><span data-stu-id="eec7e-111">**No**</span></span>  
 <span data-ttu-id="eec7e-112">单击此项可在不包括见证服务器的情况下配置安全性。</span><span class="sxs-lookup"><span data-stu-id="eec7e-112">Click to configure security without a witness.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec7e-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eec7e-113">See Also</span></span>  
 <span data-ttu-id="eec7e-114">[数据库属性（“镜像”页）](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="eec7e-114">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="eec7e-115">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eec7e-115">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="eec7e-116">数据库镜像见证服务器</span><span class="sxs-lookup"><span data-stu-id="eec7e-116">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
