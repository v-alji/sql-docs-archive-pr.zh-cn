---
title: 启动数据库镜像监视器 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- Database Mirroring Monitor [SQL Server], starting
- database mirroring [SQL Server], monitoring
ms.assetid: 53165335-97ca-4f88-8e78-22f1839dee98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67c7b393b28d4d400535281c18c637146a5d8da7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576974"
---
# <a name="start-database-mirroring-monitor-sql-server-management-studio"></a><span data-ttu-id="7b8b0-102">启动数据库镜像监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7b8b0-102">Start Database Mirroring Monitor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="7b8b0-103">数据库镜像监视器是通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]监视器的一部分。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-103">The Database Mirroring Monitor is part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Monitor, which is launched from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b8b0-104">并非 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的每个版本都提供数据库镜像监视。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-104">Database Mirroring Monitor is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7b8b0-105">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
### <a name="to-launch-the-database-mirroring-monitor"></a><span data-ttu-id="7b8b0-106">启动数据库镜像监视器</span><span class="sxs-lookup"><span data-stu-id="7b8b0-106">To launch the Database Mirroring Monitor</span></span>  
  
1.  <span data-ttu-id="7b8b0-107">连接到主体服务器实例之后，在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-107">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="7b8b0-108">展开 **“数据库”**，再选择要监视的数据库。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-108">Expand **Databases**, and select the database to be monitored.</span></span>  
  
3.  <span data-ttu-id="7b8b0-109">右键单击数据库，选择“任务” \*\*\*\*，再单击“启动数据库镜像监视器” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-109">Right-click the database, select **Tasks**, and then click **Launch Database Mirroring Monitor**.</span></span>  
  
4.  <span data-ttu-id="7b8b0-110">在 **“数据库镜像监视器”** 对话框中，单击 **“注册镜像数据库”** 以注册一个或多个镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-110">In the **Database Mirroring Monitor** dialog box, click **Register Mirrored Database** to register one or more mirrored database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b8b0-111">在一个伙伴上注册数据库时，会自动在另一个伙伴上注册此数据库。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-111">When you register a database at one partner, the database is automatically registered at the other partner.</span></span> <span data-ttu-id="7b8b0-112">如果监视器已具有另一个伙伴实例的连接凭据，则可以使用这些凭据进行连接。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-112">If the monitor already has connection credentials for the other partner instance, those are used to connect.</span></span> <span data-ttu-id="7b8b0-113">否则，监视器尝试使用 Windows 身份验证进行连接。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-113">Otherwise the monitor attempts to connect using Windows Authentication.</span></span> <span data-ttu-id="7b8b0-114">如果要更改用于连接到任一服务器实例的凭据，则单击 **“当单击‘确定’后，显示‘管理服务器连接’对话框”**。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-114">If you want to change the credentials used to connect to either server instance, click **Show the Manage Server Connections dialog box when I click OK**.</span></span>  
  
 <span data-ttu-id="7b8b0-115">有关数据库镜像监视器的详细信息，请参阅 [数据库镜像监视器概述](database-mirroring-monitor-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7b8b0-115">For more information about Database Mirroring Monitor, see [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b8b0-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b8b0-116">See Also</span></span>  
 <span data-ttu-id="7b8b0-117">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7b8b0-117">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="7b8b0-118">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7b8b0-118">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
  
