---
title: 将目标服务器登记到主服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 256f1a78d298d89a36412ee5689695f3ab3fde8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577211"
---
# <a name="enlist-a-target-server-to-a-master-server"></a><span data-ttu-id="f83f1-102">将目标服务器登记到主服务器</span><span class="sxs-lookup"><span data-stu-id="f83f1-102">Enlist a Target Server to a Master Server</span></span>
  <span data-ttu-id="f83f1-103">本主题介绍了如何将目标服务器添加到多服务器管理配置中。</span><span class="sxs-lookup"><span data-stu-id="f83f1-103">This topic describes how to add target servers to a multiserver administration configuration.</span></span> <span data-ttu-id="f83f1-104">从主服务器运行此过程。</span><span class="sxs-lookup"><span data-stu-id="f83f1-104">Run this procedure from the master server.</span></span> <span data-ttu-id="f83f1-105">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]，或使用 SQL Server 管理对象 (SMO)。</span><span class="sxs-lookup"><span data-stu-id="f83f1-105">in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="f83f1-106">有关用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务的 Windows 帐户如何影响多服务器环境的信息，请参阅 [创建多服务器环境](create-a-multiserver-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="f83f1-106">For information about how the Windows account used for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service affects a multiserver environment, see [Create a Multiserver Environment](create-a-multiserver-environment.md).</span></span>  
  
 <span data-ttu-id="f83f1-107">默认情况下，将为主服务器和目标服务器之间的连接启用完全安全套接字层 (SSL) 加密和证书验证。</span><span class="sxs-lookup"><span data-stu-id="f83f1-107">Full Secure Sockets Layer (SSL) encryption and certificate validation is enabled for connections between master servers and target servers by default.</span></span> <span data-ttu-id="f83f1-108">有关详细信息，请参阅 [在目标服务器上设置加密选项](set-encryption-options-on-target-servers.md)</span><span class="sxs-lookup"><span data-stu-id="f83f1-108">For more information, see [Set Encryption Options on Target Servers](set-encryption-options-on-target-servers.md).</span></span>  
  
 <span data-ttu-id="f83f1-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f83f1-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f83f1-110">**若要登记目标服务器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="f83f1-110">**To enlist a target server, using:**</span></span>  
  
     [<span data-ttu-id="f83f1-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f83f1-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f83f1-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f83f1-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="f83f1-113">SMO</span><span class="sxs-lookup"><span data-stu-id="f83f1-113">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f83f1-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f83f1-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enlist-a-target-server"></a><span data-ttu-id="f83f1-115">登记目标服务器</span><span class="sxs-lookup"><span data-stu-id="f83f1-115">To enlist a target server</span></span>  
  
1.  <span data-ttu-id="f83f1-116">在对象资源管理器中，展开配置为主服务器的服务器。 </span><span class="sxs-lookup"><span data-stu-id="f83f1-116">In **Object Explorer**, expand a server that is configured as a master server.</span></span>  
  
2.  <span data-ttu-id="f83f1-117">右键单击“SQL Server 代理”  ，指向“多服务器管理”  ，然后单击“添加目标服务器”  。</span><span class="sxs-lookup"><span data-stu-id="f83f1-117">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Add Target Servers**.</span></span>  
  
3.  <span data-ttu-id="f83f1-118">完成目标服务器向导，它将指导您完成该进程。</span><span class="sxs-lookup"><span data-stu-id="f83f1-118">Complete the Target Server Wizard, which guides you through the process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f83f1-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f83f1-119">Using Transact-SQL</span></span>  
  
#### <a name="to-enlist-a-target-server"></a><span data-ttu-id="f83f1-120">登记目标服务器</span><span class="sxs-lookup"><span data-stu-id="f83f1-120">To enlist a target server</span></span>  
  
1.  <span data-ttu-id="f83f1-121">使用 `sp_msx_enlist` 存储过程。</span><span class="sxs-lookup"><span data-stu-id="f83f1-121">Use the `sp_msx_enlist` stored procedure.</span></span>  <span data-ttu-id="f83f1-122">有关详细信息，请参阅[sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="f83f1-122">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="f83f1-123">使用 SQL Server 管理对象 (SMO) </span><span class="sxs-lookup"><span data-stu-id="f83f1-123">Using SQL Server Management Objects (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f83f1-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f83f1-124">See Also</span></span>  
 [<span data-ttu-id="f83f1-125">企业范围的自动化管理</span><span class="sxs-lookup"><span data-stu-id="f83f1-125">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
