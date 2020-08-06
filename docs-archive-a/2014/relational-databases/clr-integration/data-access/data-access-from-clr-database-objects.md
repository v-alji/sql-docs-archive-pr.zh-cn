---
title: 从 CLR 数据库对象进行数据访问 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
author: rothja
ms.author: jroth
ms.openlocfilehash: d229d490a9f3a7bc6f613259ee0535218de47975
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590212"
---
# <a name="data-access-from-clr-database-objects"></a><span data-ttu-id="9991d-102">从 CLR 数据库对象进行数据访问</span><span class="sxs-lookup"><span data-stu-id="9991d-102">Data Access from CLR Database Objects</span></span>
  <span data-ttu-id="9991d-103">公共语言运行时 (CLR) 例程可以轻松地访问存储在其中运行的实例中的数据 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] ，以及存储在远程实例中的数据。</span><span class="sxs-lookup"><span data-stu-id="9991d-103">A common language runtime (CLR) routine may easily access data stored in the instance of [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] in which it runs, as well as data stored in remote instances.</span></span> <span data-ttu-id="9991d-104">该例程可以访问的特定数据由代码正在其中运行的用户上下文确定。</span><span class="sxs-lookup"><span data-stu-id="9991d-104">Which particular data the routine can access is determined by the user context in which the code is running.</span></span> <span data-ttu-id="9991d-105">通过使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 来自托管客户端和中间层应用程序的数据的 .NET Framework 数据提供程序，从 CLR 数据库对象中访问数据。</span><span class="sxs-lookup"><span data-stu-id="9991d-105">Access data from within a CLR database object by using the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data from managed client and middle-tier applications.</span></span> <span data-ttu-id="9991d-106">因此，您可以在客户端和中间层应用程序中充分利用您所掌握的有关 ADO.NET 和 `SqlClient` 的知识。</span><span class="sxs-lookup"><span data-stu-id="9991d-106">Because of this, you can leverage your knowledge of ADO.NET and `SqlClient` in client and middle-tier applications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9991d-107">默认情况下，不允许用户定义类型方法和用户定义函数执行数据访问。</span><span class="sxs-lookup"><span data-stu-id="9991d-107">User-defined type methods and user-defined functions are not allowed to perform data access by default.</span></span> <span data-ttu-id="9991d-108">您必须将 `DataAccess` 或 `SqlMethodAttribute` 的 `SqlFunctionAttribute` 属性设置为 `DataAccessKind.Read`，才能从用户定义类型 (UDT) 方法或用户定义函数进行只读数据访问。</span><span class="sxs-lookup"><span data-stu-id="9991d-108">You must set the `DataAccess` property of `SqlMethodAttribute` or `SqlFunctionAttribute` to `DataAccessKind.Read` to enable read-only data access from user-defined type (UDT) methods or user-defined functions.</span></span> <span data-ttu-id="9991d-109">不允许从 UDT 或用户定义函数执行数据修改操作，否则，将在执行时引发异常。</span><span class="sxs-lookup"><span data-stu-id="9991d-109">Data modification operations are not allowed from UDTs or user-defined functions, and throws exceptions at execution time if attempted.</span></span>  
  
 <span data-ttu-id="9991d-110">本节只讨论当从 CLR 数据库对象中访问数据时特定的功能差异和行为差异。</span><span class="sxs-lookup"><span data-stu-id="9991d-110">This section discusses only the specific functional and behavioral differences when accessing data from within a CLR database object.</span></span> <span data-ttu-id="9991d-111">有关 ADO.NET 的特性和功能的详细信息，请参阅 .NET Framework SDK 随附的 ADO.NET 文档。</span><span class="sxs-lookup"><span data-stu-id="9991d-111">For more information about the features and functionality of ADO.NET, see the ADO.NET documentation included in the .NET Framework SDK.</span></span>  
  
 <span data-ttu-id="9991d-112">下表列出了本节的主题。</span><span class="sxs-lookup"><span data-stu-id="9991d-112">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="9991d-113">上下文连接</span><span class="sxs-lookup"><span data-stu-id="9991d-113">Context Connection</span></span>](context-connection.md)  
 <span data-ttu-id="9991d-114">介绍与 SQL Server 之间的上下文连接。</span><span class="sxs-lookup"><span data-stu-id="9991d-114">Describes the context connection to SQL Server.</span></span>  
  
 [<span data-ttu-id="9991d-115">模拟和连接凭据</span><span class="sxs-lookup"><span data-stu-id="9991d-115">Impersonation and Credentials for Connections</span></span>](impersonation-and-credentials-for-connections.md)  
 <span data-ttu-id="9991d-116">介绍模拟连接和连接凭据。</span><span class="sxs-lookup"><span data-stu-id="9991d-116">Describes impersonating connections and connection credentials.</span></span>  
  
 [<span data-ttu-id="9991d-117">SQL Server 进程内专用的 ADO.NET 扩展</span><span class="sxs-lookup"><span data-stu-id="9991d-117">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 <span data-ttu-id="9991d-118">讨论进程内特定的 `SqlPipe`、`SqlContext`、`SqlTriggerContext` 和 `SqlDataRecord` 对象。</span><span class="sxs-lookup"><span data-stu-id="9991d-118">Discusses the in-process specific `SqlPipe`, `SqlContext`, `SqlTriggerContext`, and `SqlDataRecord` objects.</span></span>  
  
 [<span data-ttu-id="9991d-119">CLR 集成和事务</span><span class="sxs-lookup"><span data-stu-id="9991d-119">CLR Integration and Transactions</span></span>](../../native-client-ole-db-transactions/transactions.md)  
 <span data-ttu-id="9991d-120">介绍 System.Transactions 命名空间中提供的新事务框架如何与 ADO.NET 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 集成相集成。</span><span class="sxs-lookup"><span data-stu-id="9991d-120">Describes how the new transaction framework provided in the System.Transactions namespace integrates with ADO.NET and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR integration.</span></span>  
  
 [<span data-ttu-id="9991d-121">从 CLR 数据库对象进行 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="9991d-121">XML Serialization from CLR Database Objects</span></span>](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 <span data-ttu-id="9991d-122">说明如何对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 CLR 数据库对象启用 XML 序列化方案。</span><span class="sxs-lookup"><span data-stu-id="9991d-122">Explains how to enable XML serialization scenarios of CLR database objects inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
  
