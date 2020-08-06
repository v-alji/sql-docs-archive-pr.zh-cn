---
title: 为 AlwaysOn 可用性组 (SQL Server PowerShell 创建数据库镜像端点) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56058ff8aa72d2471381dd87fb25a3b68356ed36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694554"
---
# <a name="create-a-database-mirroring-endpoint-for-alwayson-availability-groups-sql-server-powershell"></a><span data-ttu-id="b8713-102">为 AlwaysOn 可用性组创建数据库镜像端点 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="b8713-102">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups (SQL Server PowerShell)</span></span>
  <span data-ttu-id="b8713-103">本主题介绍如何使用 PowerShell 创建供 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 使用的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="b8713-103">This topic describes how to create a database mirroring endpoint for use by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using PowerShell.</span></span>  
  
 <span data-ttu-id="b8713-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b8713-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b8713-105">**开始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="b8713-105">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="b8713-106">**若要创建数据库镜像端点，请使用：**  [PowerShell](#PowerShellProcedure)</span><span class="sxs-lookup"><span data-stu-id="b8713-106">**To create a database mirroring endpoint, using:**  [PowerShell](#PowerShellProcedure)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="b8713-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="b8713-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b8713-108">Security</span><span class="sxs-lookup"><span data-stu-id="b8713-108">Security</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b8713-109">不推荐使用 RC4 算法。</span><span class="sxs-lookup"><span data-stu-id="b8713-109">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="b8713-110">我们建议使用 AES。</span><span class="sxs-lookup"><span data-stu-id="b8713-110">We recommend that you use AES.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b8713-111">权限</span><span class="sxs-lookup"><span data-stu-id="b8713-111">Permissions</span></span>  
 <span data-ttu-id="b8713-112">要求具有 CREATE ENDPOINT 权限，或者具有 sysadmin 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="b8713-112">Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role.</span></span> <span data-ttu-id="b8713-113">有关详细信息，请参阅 [GRANT 终结点权限 (Transact-SQL)](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b8713-113">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="b8713-114">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8713-114">Using PowerShell</span></span>  
 <span data-ttu-id="b8713-115">**创建数据库镜像端点**</span><span class="sxs-lookup"><span data-stu-id="b8713-115">**To create a database mirroring endpoint**</span></span>  
  
1.  <span data-ttu-id="b8713-116">将目录 (`cd`) 更改到要为其创建数据库镜像端点的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b8713-116">Change directory (`cd`) to the server instance for which you want to create the database mirroring endpoint.</span></span>  
  
2.  <span data-ttu-id="b8713-117">使用 `New-SqlHadrEndpoint` cmdlet 创建端点，然后使用 `Set-SqlHadrEndpoint` 启动此端点。</span><span class="sxs-lookup"><span data-stu-id="b8713-117">Use the `New-SqlHadrEndpoint` cmdlet to create the endpoint and then use the `Set-SqlHadrEndpoint` to start the endpoint.</span></span>  
  
###  <a name="example-powershell"></a><a name="PShellExample"></a> <span data-ttu-id="b8713-118">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="b8713-118">Example (PowerShell)</span></span>  
 <span data-ttu-id="b8713-119">以下 PowerShell 命令在实例上创建一个数据库镜像端点，该端点在) SQL Server (*机* \\ *实例*。</span><span class="sxs-lookup"><span data-stu-id="b8713-119">The following PowerShell commands create a database mirroring endpoint on an instance of SQL Server (*Machine*\\*Instance*).</span></span> <span data-ttu-id="b8713-120">该端点使用端口 5022。</span><span class="sxs-lookup"><span data-stu-id="b8713-120">The endpoint uses port 5022.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b8713-121">此示例只适用于目前缺少数据库镜像端点的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b8713-121">This example works only on a server instance that currently lack a database mirroring endpoint.</span></span>  
  
```powershell
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b8713-122">相关任务</span><span class="sxs-lookup"><span data-stu-id="b8713-122">Related Tasks</span></span>  
 <span data-ttu-id="b8713-123">**配置数据库镜像端点**</span><span class="sxs-lookup"><span data-stu-id="b8713-123">**To Configure a Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="b8713-124">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8713-124">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="b8713-125">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8713-125">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="b8713-126">允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8713-126">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="b8713-127">允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8713-127">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="b8713-128">指定服务器网络地址（数据库镜像）</span><span class="sxs-lookup"><span data-stu-id="b8713-128">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="b8713-129">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b8713-129">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="b8713-130">**查看有关数据库镜像端点的信息**</span><span class="sxs-lookup"><span data-stu-id="b8713-130">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="b8713-131">sys.database_mirroring_endpoints (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8713-131">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="b8713-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8713-132">See Also</span></span>  
 <span data-ttu-id="b8713-133">[&#40;Transact-sql 创建可用性组&#41;](create-an-availability-group-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="b8713-133">[Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) </span></span>  
 [<span data-ttu-id="b8713-134">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="b8713-134">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
