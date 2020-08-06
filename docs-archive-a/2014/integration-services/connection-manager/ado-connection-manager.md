---
title: ADO 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ADO
- connection managers [Integration Services], ADO
- ADO connection manager [Integration Services]
ms.assetid: 490418bc-5ef1-41b8-a9c8-de38aa96e0f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb4b667733f81eebbaf2b6a2ab9b205c09fe2c66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589845"
---
# <a name="ado-connection-manager"></a><span data-ttu-id="16a2b-102">ADO 连接管理器</span><span class="sxs-lookup"><span data-stu-id="16a2b-102">ADO Connection Manager</span></span>
  <span data-ttu-id="16a2b-103">ADO 连接管理器使包可以连接到 ActiveX 数据对象 (ADO) 对象（如记录集）。</span><span class="sxs-lookup"><span data-stu-id="16a2b-103">An ADO connection manager enables a package to connect to ActiveX Data Objects (ADO) objects, such as a recordset.</span></span> <span data-ttu-id="16a2b-104">此连接管理器通常用于以 Microsoft Visual Basic 6.0 等语言的早期版本编写的自定义任务，或用于从属于使用 ADO 连接到数据源的现有应用程序的自定义任务。</span><span class="sxs-lookup"><span data-stu-id="16a2b-104">This connection manager is typically used in custom tasks written in an earlier version of a language, such as Microsoft Visual Basic 6.0, or in custom tasks that are part of an existing application that uses ADO to connect to a data source.</span></span>  
  
 <span data-ttu-id="16a2b-105">将 ADO 连接管理器添加到包时， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时解析为 ADO 连接的连接管理器，设置该连接管理器的属性，并将该连接管理器添加到 `Connections` 包上的集合。</span><span class="sxs-lookup"><span data-stu-id="16a2b-105">When you add an ADO connection manager to a package, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an ADO connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="16a2b-106">该连接管理器的 `ConnectionManagerType` 属性设置为 `ADO`。</span><span class="sxs-lookup"><span data-stu-id="16a2b-106">The `ConnectionManagerType` property of the connection manager is set to `ADO`.</span></span>  
  
## <a name="troubleshooting-the-ado-connection-manager"></a><span data-ttu-id="16a2b-107">ADO 连接管理器故障排除</span><span class="sxs-lookup"><span data-stu-id="16a2b-107">Troubleshooting the ADO Connection Manager</span></span>  
 <span data-ttu-id="16a2b-108">ADO 连接管理器在读取数据时，某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期数据类型将生成下表中显示的结果。</span><span class="sxs-lookup"><span data-stu-id="16a2b-108">When being read by an ADO connection manager, certain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types will generate the results shown in the following table.</span></span>  
  
|<span data-ttu-id="16a2b-109">SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="16a2b-109">SQL Server Data type</span></span>|<span data-ttu-id="16a2b-110">结果</span><span class="sxs-lookup"><span data-stu-id="16a2b-110">Result</span></span>|  
|--------------------------|------------|  
|<span data-ttu-id="16a2b-111">`time`, `datetimeoffset`</span><span class="sxs-lookup"><span data-stu-id="16a2b-111">`time`, `datetimeoffset`</span></span>|<span data-ttu-id="16a2b-112">除非包使用参数化 SQL 命令，否则，包将失败。</span><span class="sxs-lookup"><span data-stu-id="16a2b-112">The package fails unless the package uses parameterized SQL commands.</span></span> <span data-ttu-id="16a2b-113">若要使用参数化 SQL 命令，请在包中使用执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="16a2b-113">To use parameterized SQL commands, use the Execute SQL Task in your package.</span></span> <span data-ttu-id="16a2b-114">有关详细信息，请参阅 [执行 SQL 任务](../control-flow/execute-sql-task.md) 和 [执行 SQL 任务中的参数和返回代码](../parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="16a2b-114">For more information, see [Execute SQL Task](../control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>|  
|`datetime2`|<span data-ttu-id="16a2b-115">ADO 连接管理器截断毫秒值。</span><span class="sxs-lookup"><span data-stu-id="16a2b-115">The ADO connection manager truncates the millisecond value.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="16a2b-116">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型和它们如何映射到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型的详细信息，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) 和 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="16a2b-116">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) and [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="configuring-the-ado-connection-manager"></a><span data-ttu-id="16a2b-117">配置 ADO 连接管理器</span><span class="sxs-lookup"><span data-stu-id="16a2b-117">Configuring the ADO Connection Manager</span></span>  
 <span data-ttu-id="16a2b-118">可以使用下列方式配置 ADO 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="16a2b-118">You can configure an ADO connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="16a2b-119">提供配置为满足选定访问接口要求的特定连接字符串。</span><span class="sxs-lookup"><span data-stu-id="16a2b-119">Provide a specific connection string configured to meet the requirements of the selected provider.</span></span>  
  
-   <span data-ttu-id="16a2b-120">包括要连接到的数据源的名称（取决于访问接口）。</span><span class="sxs-lookup"><span data-stu-id="16a2b-120">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="16a2b-121">为选定的访问接口提供相应的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="16a2b-121">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="16a2b-122">指示是否在运行时保留从连接管理器中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="16a2b-122">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="16a2b-123">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="16a2b-123">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="16a2b-124">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="16a2b-124">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="16a2b-125">配置 OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="16a2b-125">Configure OLE DB Connection Manager</span></span>](ole-db-connection-manager.md)  
  
 <span data-ttu-id="16a2b-126">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="16a2b-126">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a2b-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16a2b-127">See Also</span></span>  
 [<span data-ttu-id="16a2b-128">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="16a2b-128">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
