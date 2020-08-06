---
title: SQL Server Compact Edition 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5d4feb001cc7c0fd0bd8b6e60d5ab22b33ad2eb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693431"
---
# <a name="sql-server-compact-edition-connection-manager"></a><span data-ttu-id="37380-102">SQL Server Compact Edition 连接管理器</span><span class="sxs-lookup"><span data-stu-id="37380-102">SQL Server Compact Edition Connection Manager</span></span>
  <span data-ttu-id="37380-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接管理器使包能够连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据库。</span><span class="sxs-lookup"><span data-stu-id="37380-103">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager enables a package to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span> <span data-ttu-id="37380-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包括的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 目标使用该连接管理器将数据加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="37380-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager to load data into a table in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="37380-105">在 64 位计算机上，必须以 32 位模式运行连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据源的包。</span><span class="sxs-lookup"><span data-stu-id="37380-105">On a 64-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources in 32-bit mode.</span></span> <span data-ttu-id="37380-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用于连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 数据源的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Provider 只在 32 位版本中提供。</span><span class="sxs-lookup"><span data-stu-id="37380-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources is available only in a 32-bit version.</span></span>  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a><span data-ttu-id="37380-107">SQL Server Compact Edition 连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="37380-107">Configuration the SQL Server Compact Edition Connection Manager</span></span>  
 <span data-ttu-id="37380-108">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接管理器添加到包时， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时解析为 Compact 连接的连接管理器 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，设置该连接管理器的属性，并将该连接管理器添加到 `Connections` 包上的集合。</span><span class="sxs-lookup"><span data-stu-id="37380-108">When you add a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="37380-109">该连接管理器的 `ConnectionManagerType` 属性设置为 `SQLMOBILE`。</span><span class="sxs-lookup"><span data-stu-id="37380-109">The `ConnectionManagerType` property of the connection manager is set to `SQLMOBILE`.</span></span>  
  
 <span data-ttu-id="37380-110">可以通过以下方式配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="37380-110">You can configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="37380-111">提供指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据库位置的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="37380-111">Provide a connection string that specifies the location of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
-   <span data-ttu-id="37380-112">为受密码保护的数据库提供密码。</span><span class="sxs-lookup"><span data-stu-id="37380-112">Provide a password for a password-protected database.</span></span>  
  
-   <span data-ttu-id="37380-113">指定存储数据库的服务器。</span><span class="sxs-lookup"><span data-stu-id="37380-113">Specify the server on which the database is stored.</span></span>  
  
-   <span data-ttu-id="37380-114">指示是否在运行时保留从连接管理器中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="37380-114">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="37380-115">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="37380-115">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="37380-116">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="37380-116">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="37380-117">SQL Server Compact Edition 连接管理器编辑器（“连接”页）</span><span class="sxs-lookup"><span data-stu-id="37380-117">SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;</span></span>](../sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [<span data-ttu-id="37380-118">SQL Server Compact Edition 连接管理器编辑器（“全部”页）</span><span class="sxs-lookup"><span data-stu-id="37380-118">SQL Server Compact Edition Connection Manager Editor &#40;All Page&#41;</span></span>](../sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 <span data-ttu-id="37380-119">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="37380-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
