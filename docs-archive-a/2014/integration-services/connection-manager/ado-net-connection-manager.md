---
title: ADO.NET 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bdc25eeeae93fe0bd85deb55bfc86c55ab91ee5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586929"
---
# <a name="adonet-connection-manager"></a><span data-ttu-id="7485f-102">ADO.NET 连接管理器</span><span class="sxs-lookup"><span data-stu-id="7485f-102">ADO.NET Connection Manager</span></span>
  <span data-ttu-id="7485f-103">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器使包能够使用 .NET 访问接口访问数据源。</span><span class="sxs-lookup"><span data-stu-id="7485f-103">An [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager enables a package to access data sources by using a .NET provider.</span></span> <span data-ttu-id="7485f-104">此连接管理器通常用于访问等数据源 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，也用于访问通过使用 c # 等语言以托管代码编写的自定义任务中的 OLE DB 和 XML 公开的数据源。</span><span class="sxs-lookup"><span data-stu-id="7485f-104">This connection manager is typically used to access data sources such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and also data sources exposed through OLE DB and XML in custom tasks that are written in managed code by using a language such C#.</span></span>  
  
 <span data-ttu-id="7485f-105">将 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器添加到包时，将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 创建一个连接管理器，该管理器 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 在运行时作为连接进行解析，设置连接管理器属性，并将该连接管理器添加到 `Connections` 包上的集合。</span><span class="sxs-lookup"><span data-stu-id="7485f-105">When you add an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="7485f-106">该连接管理器的 `ConnectionManagerType` 属性设置为 `ADO.NET`。</span><span class="sxs-lookup"><span data-stu-id="7485f-106">The `ConnectionManagerType` property of the connection manager is set to `ADO.NET`.</span></span> <span data-ttu-id="7485f-107">`ConnectionManagerType` 的值受到限定，以包含连接管理器所使用的 .NET 访问接口的名称。</span><span class="sxs-lookup"><span data-stu-id="7485f-107">The value of `ConnectionManagerType` is qualified to include the name of the .NET provider that the connection manager uses.</span></span>  
  
## <a name="adonet-connection-manager-troubleshooting"></a><span data-ttu-id="7485f-108">ADO.NET 连接管理器故障排除</span><span class="sxs-lookup"><span data-stu-id="7485f-108">ADO.NET Connection Manager Troubleshooting</span></span>  
 <span data-ttu-id="7485f-109">可以记录 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器对外部数据访问接口所做的调用。</span><span class="sxs-lookup"><span data-stu-id="7485f-109">You can log the calls that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data providers.</span></span> <span data-ttu-id="7485f-110">使用此日志记录功能，可以对 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器与外部数据源的连接进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="7485f-110">You can use this logging capability to troubleshoot the connections that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data sources.</span></span> <span data-ttu-id="7485f-111">若要记录 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器对外部数据访问接口所做的调用，请在包级别启用包日志记录并选择 **“诊断”** 事件。</span><span class="sxs-lookup"><span data-stu-id="7485f-111">To log the calls that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="7485f-112">有关详细信息，请参阅 [包执行的疑难解答工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="7485f-112">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="7485f-113">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器在读取数据时，某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期数据类型的数据将生成下表中显示的结果。</span><span class="sxs-lookup"><span data-stu-id="7485f-113">When being read by an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager, data of certain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types will generate the results shown in the following table.</span></span>  
  
|<span data-ttu-id="7485f-114">SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="7485f-114">SQL Server data type</span></span>|<span data-ttu-id="7485f-115">结果</span><span class="sxs-lookup"><span data-stu-id="7485f-115">Result</span></span>|  
|--------------------------|------------|  
|<span data-ttu-id="7485f-116">`time`, `datetimeoffset`</span><span class="sxs-lookup"><span data-stu-id="7485f-116">`time`, `datetimeoffset`</span></span>|<span data-ttu-id="7485f-117">除非包使用参数化 SQL 命令，否则，包将失败。</span><span class="sxs-lookup"><span data-stu-id="7485f-117">The package fails unless the package uses parameterized SQL commands.</span></span> <span data-ttu-id="7485f-118">若要使用参数化 SQL 命令，请在包中使用执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="7485f-118">To use parameterized SQL commands, use the Execute SQL Task in your package.</span></span> <span data-ttu-id="7485f-119">有关详细信息，请参阅 [执行 SQL 任务](../control-flow/execute-sql-task.md) 和 [执行 SQL 任务中的参数和返回代码](../parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="7485f-119">For more information, see [Execute SQL Task](../control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>|  
|`datetime2`|<span data-ttu-id="7485f-120">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器截断毫秒值。</span><span class="sxs-lookup"><span data-stu-id="7485f-120">The [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager truncates the millisecond value.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="7485f-121">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型和它们如何映射到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型的详细信息，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) 和 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7485f-121">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) and [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="adonet-connection-manager-configuration"></a><span data-ttu-id="7485f-122">配置 ADO.NET 连接管理器</span><span class="sxs-lookup"><span data-stu-id="7485f-122">ADO.NET Connection Manager Configuration</span></span>  
 <span data-ttu-id="7485f-123">可以通过下列方式配置 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="7485f-123">You can configure an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager in the following ways:</span></span>  
  
 <span data-ttu-id="7485f-124">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="7485f-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
-   <span data-ttu-id="7485f-125">提供配置为满足选定 .NET 访问接口的要求的特定连接字符串。</span><span class="sxs-lookup"><span data-stu-id="7485f-125">Provide a specific connection string configured to meet the requirements of the selected .NET provider.</span></span>  
  
-   <span data-ttu-id="7485f-126">包括要连接到的数据源的名称（取决于访问接口）。</span><span class="sxs-lookup"><span data-stu-id="7485f-126">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="7485f-127">为选定的访问接口提供相应的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="7485f-127">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="7485f-128">指示是否在运行时保留从连接管理器中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="7485f-128">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="7485f-129">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器的许多配置选项取决于该连接管理器所使用的 .NET 访问接口。</span><span class="sxs-lookup"><span data-stu-id="7485f-129">Many of configuration options of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager depend on the .NET provider that the connection manager uses.</span></span>  
  
 <span data-ttu-id="7485f-130">有关可以在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="7485f-130">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="7485f-131">配置 ADO.NET 连接管理器</span><span class="sxs-lookup"><span data-stu-id="7485f-131">Configure ADO.NET Connection Manager</span></span>](../configure-ado-net-connection-manager.md)  
  
 <span data-ttu-id="7485f-132">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="7485f-132">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7485f-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7485f-133">See Also</span></span>  
 [<span data-ttu-id="7485f-134">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="7485f-134">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
