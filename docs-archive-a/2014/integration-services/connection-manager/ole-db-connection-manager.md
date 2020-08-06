---
title: OLE DB 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5431de956a1039c2978688982792f190b0abc544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587964"
---
# <a name="ole-db-connection-manager"></a><span data-ttu-id="07acc-102">OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="07acc-102">OLE DB Connection Manager</span></span>
  <span data-ttu-id="07acc-103">OLE DB 连接管理器使包能够用 OLE DB 访问接口连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="07acc-103">An OLE DB connection manager enables a package to connect to a data source by using an OLE DB provider.</span></span> <span data-ttu-id="07acc-104">例如，连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 OLE DB 连接管理器可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07acc-104">For example, an OLE DB connection manager that connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07acc-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB 提供程序不支持用于多子网故障转移群集的新连接字符串关键字 (MultiSubnetFailover=True)。</span><span class="sxs-lookup"><span data-stu-id="07acc-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB provider does not support the new connection string key words (MultiSubnetFailover=True) for Multi-Subnet Failover Clustering.</span></span> <span data-ttu-id="07acc-106">有关详细信息，请参阅 www.mattmasson.com 上的[SQL Server 发行说明](https://go.microsoft.com/fwlink/?LinkId=247824)和博客文章[AlwaysOn 多子网故障转移和 SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)。</span><span class="sxs-lookup"><span data-stu-id="07acc-106">For more information, see the [SQL Server Release  Notes](https://go.microsoft.com/fwlink/?LinkId=247824) and the blog post, [AlwaysOn Multi-Subnet Failover and SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/), on www.mattmasson.com.</span></span>  
  
 <span data-ttu-id="07acc-107">若干 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 任务和数据流组件使用 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="07acc-107">Several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks and data flow components use an OLE DB connection manager.</span></span> <span data-ttu-id="07acc-108">例如，OLE DB 源和 OLE DB 目标使用这种连接管理器来提取和加载数据，而执行 SQL 任务可以使用这种连接管理器来连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库以运行查询。</span><span class="sxs-lookup"><span data-stu-id="07acc-108">For example, the OLE DB source and OLE DB destination use this connection manager to extract and load data, and the Execute SQL task can use this connection manager to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to run queries.</span></span>  
  
 <span data-ttu-id="07acc-109">OLE DB 连接管理器还用于在以使用 C++ 等语言的非托管代码编写的自定义任务中访问 OLE DB 数据源。</span><span class="sxs-lookup"><span data-stu-id="07acc-109">The OLE DB connection manager is also used to access OLE DB data sources in custom tasks written in unmanaged code that uses a language such as C++.</span></span>  
  
 <span data-ttu-id="07acc-110">将 OLE DB 连接管理器添加到包时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时决定 OLE DB 连接的连接管理器，设置该连接管理器的属性，并将该连接管理器添加到包上的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="07acc-110">When you add an OLE DB connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an OLE DB connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="07acc-111">该连接管理器的 `ConnectionManagerType` 属性设置为 `OLEDB`。</span><span class="sxs-lookup"><span data-stu-id="07acc-111">The `ConnectionManagerType` property of the connection manager is set to `OLEDB`.</span></span>  
  
 <span data-ttu-id="07acc-112">可以按下列方式配置 OLE DB 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="07acc-112">The OLE DB connection manager can be configured in the following ways:</span></span>  
  
-   <span data-ttu-id="07acc-113">提供配置为满足选定访问接口要求的特定连接字符串。</span><span class="sxs-lookup"><span data-stu-id="07acc-113">Provide a specific connection string configured to meet the requirements of the selected provider.</span></span>  
  
-   <span data-ttu-id="07acc-114">包括要连接到的数据源的名称（取决于访问接口）。</span><span class="sxs-lookup"><span data-stu-id="07acc-114">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="07acc-115">为选定的访问接口提供相应的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="07acc-115">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="07acc-116">指示是否在运行时保留从连接管理器中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="07acc-116">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
## <a name="logging"></a><span data-ttu-id="07acc-117">Logging</span><span class="sxs-lookup"><span data-stu-id="07acc-117">Logging</span></span>  
 <span data-ttu-id="07acc-118">可以记录 OLE DB 连接管理器对外部数据访问接口所做的调用。</span><span class="sxs-lookup"><span data-stu-id="07acc-118">You can log the calls that the OLE DB connection manager makes to external data providers.</span></span> <span data-ttu-id="07acc-119">使用此日志记录功能，可以对 OLE DB 连接管理器与外部数据源的连接进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="07acc-119">You can use this logging capability to troubleshoot the connections that the OLE DB connection manager makes to external data sources.</span></span> <span data-ttu-id="07acc-120">若要记录 OLE DB 连接管理器对外部数据访问接口所做的调用，请在包级别启用包日志记录并选择 **“诊断”** 事件。</span><span class="sxs-lookup"><span data-stu-id="07acc-120">To log the calls that the OLE DB connection manager makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="07acc-121">有关详细信息，请参阅 [包执行的疑难解答工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="07acc-121">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuration-of-the-oledb-connection-manager"></a><span data-ttu-id="07acc-122">OLEDB 连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="07acc-122">Configuration of the OLEDB Connection Manager</span></span>  
 <span data-ttu-id="07acc-123">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="07acc-123">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="07acc-124">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅 [配置 OLE DB 连接管理器](../configure-ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="07acc-124">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Configure OLE DB Connection Manager](../configure-ole-db-connection-manager.md).</span></span> <span data-ttu-id="07acc-125">有关以编程方式配置连接管理器的信息，请参阅开发人员指南中针对 **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** 类的文档。</span><span class="sxs-lookup"><span data-stu-id="07acc-125">For information about configuring a connection manager programmatically, see the documentation for **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** class in the Developer Guide.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="07acc-126">相关内容</span><span class="sxs-lookup"><span data-stu-id="07acc-126">Related Content</span></span>  
  
-   <span data-ttu-id="07acc-127">Social.technet.microsoft.com 上的 Wiki 文章[SSIS 与 Oracle 连接器](https://go.microsoft.com/fwlink/?LinkId=220670)。</span><span class="sxs-lookup"><span data-stu-id="07acc-127">Wiki article, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670) on social.technet.microsoft.com.</span></span>  
  
-   <span data-ttu-id="07acc-128">carlprothman.net 上的技术文章 [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744)（OLE DB 访问接口的连接字符串）。</span><span class="sxs-lookup"><span data-stu-id="07acc-128">Technical article, [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744), on carlprothman.net.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07acc-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07acc-129">See Also</span></span>  
 <span data-ttu-id="07acc-130">[OLE DB 源](../data-flow/ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="07acc-130">[OLE DB Source](../data-flow/ole-db-source.md) </span></span>  
 <span data-ttu-id="07acc-131">[OLE DB 目标](../data-flow/ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="07acc-131">[OLE DB Destination](../data-flow/ole-db-destination.md) </span></span>  
 <span data-ttu-id="07acc-132">[执行 SQL 任务](../control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="07acc-132">[Execute SQL Task](../control-flow/execute-sql-task.md) </span></span>  
 [<span data-ttu-id="07acc-133">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="07acc-133">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
