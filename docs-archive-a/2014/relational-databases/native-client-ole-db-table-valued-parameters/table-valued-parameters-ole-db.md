---
title: 表值参数 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: rothja
ms.author: jroth
ms.openlocfilehash: 41d125bcb254125d7f7562ca1873e8af03dab929
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692363"
---
# <a name="table-valued-parameters-ole-db"></a><span data-ttu-id="2c46d-102">表值参数 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="2c46d-102">Table-Valued Parameters (OLE DB)</span></span>
  <span data-ttu-id="2c46d-103">本节介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口中的表值参数支持。</span><span class="sxs-lookup"><span data-stu-id="2c46d-103">This section describes support for table-valued parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider.</span></span> <span data-ttu-id="2c46d-104">有关其他概述信息，请参阅[表值参数 &#40;SQL Server Native Client&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="2c46d-104">For additional overview information, see [Table-Valued Parameters &#40;SQL Server Native Client&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md).</span></span> <span data-ttu-id="2c46d-105">有关示例，请参阅[使用表值参数 (OLE DB)](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="2c46d-105">For a sample, see [Use Table-Valued Parameters &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c46d-106">备注</span><span class="sxs-lookup"><span data-stu-id="2c46d-106">Remarks</span></span>  
 <span data-ttu-id="2c46d-107">当前，您可以将多行数据作为带有参数集的过程的参数（如 `ICommand::Execute` 中的 DBPARAMS 参数）发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="2c46d-107">Currently, you can send multirow data to the server as parameters to a procedure with parameter sets (the DBPARAMS parameter in `ICommand::Execute`).</span></span> <span data-ttu-id="2c46d-108">使用参数集时，该参数集中的每个元素都必须通过单独的远程过程调用 (RPC) 请求发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="2c46d-108">With parameter sets, every element of the set has to be sent in a separate remote procedure call (RPC) request to the server.</span></span> <span data-ttu-id="2c46d-109">表值参数提供类似的功能，但可以与服务器更好地集成。</span><span class="sxs-lookup"><span data-stu-id="2c46d-109">Table-valued parameters provide similar functionality, but there is better integration with the server.</span></span> <span data-ttu-id="2c46d-110">这可以减少 RPC 请求数，并在服务器上启用基于集的操作。</span><span class="sxs-lookup"><span data-stu-id="2c46d-110">This reduces the number of RPC requests and enables set-based operations on the server.</span></span>  
  
 <span data-ttu-id="2c46d-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口将表值参数作为 OLE DB `Rowset` 对象提供支持。</span><span class="sxs-lookup"><span data-stu-id="2c46d-111">Table-value parameters are supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider as OLE DB `Rowset` objects.</span></span> <span data-ttu-id="2c46d-112">使用者（即使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口的客户端应用程序）可以将任意 `Rowset` 对象作为表值参数的占位符提供。</span><span class="sxs-lookup"><span data-stu-id="2c46d-112">Any `Rowset` object could be provided by the consumer (that is, the client application using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider) as a placeholder for table-valued parameter parameters.</span></span> <span data-ttu-id="2c46d-113">表值参数的处理方式与其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 参数类型相似。</span><span class="sxs-lookup"><span data-stu-id="2c46d-113">Table-valued parameters are treated like other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] parameter types.</span></span> <span data-ttu-id="2c46d-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口提供创建、发现、规范、绑定和架构接口。</span><span class="sxs-lookup"><span data-stu-id="2c46d-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider provides creation, discovery, specification, binding and schema interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c46d-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="2c46d-115">In This Section</span></span>  
  
-   [<span data-ttu-id="2c46d-116">创建表值参数行集</span><span class="sxs-lookup"><span data-stu-id="2c46d-116">Table-Valued Parameter Rowset Creation</span></span>](table-valued-parameter-rowset-creation.md)  
  
-   [<span data-ttu-id="2c46d-117">表值参数类型发现</span><span class="sxs-lookup"><span data-stu-id="2c46d-117">Table-Valued Parameter Type Discovery</span></span>](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md)  
  
-   [<span data-ttu-id="2c46d-118">执行包含表值参数的命令</span><span class="sxs-lookup"><span data-stu-id="2c46d-118">Executing Commands Containing Table-Valued Parameters</span></span>](executing-commands-containing-table-valued-parameters.md)  
  
-   [<span data-ttu-id="2c46d-119">向表值参数中插入数据</span><span class="sxs-lookup"><span data-stu-id="2c46d-119">Inserting Data into Table-Valued Parameters</span></span>](inserting-data-into-table-valued-parameters.md)  
  
-   [<span data-ttu-id="2c46d-120">为 OLE DB 表值参数更改的架构行集</span><span class="sxs-lookup"><span data-stu-id="2c46d-120">Schema Rowsets Changed for OLE DB Table-Valued Parameters</span></span>](schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [<span data-ttu-id="2c46d-121">OLE DB 表值参数类型支持</span><span class="sxs-lookup"><span data-stu-id="2c46d-121">OLE DB Table-Valued Parameter Type Support</span></span>](ole-db-table-valued-parameter-type-support.md)  
  
-   [<span data-ttu-id="2c46d-122">OLE DB 表值参数类型支持（方法）</span><span class="sxs-lookup"><span data-stu-id="2c46d-122">OLE DB Table-Valued Parameter Type Support &#40;Methods&#41;</span></span>](ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [<span data-ttu-id="2c46d-123">OLE DB 表值参数类型支持（属性）</span><span class="sxs-lookup"><span data-stu-id="2c46d-123">OLE DB Table-Valued Parameter Type Support &#40;Properties&#41;</span></span>](ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c46d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c46d-124">See Also</span></span>  
 <span data-ttu-id="2c46d-125">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="2c46d-125">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 [<span data-ttu-id="2c46d-126">使用表值参数 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="2c46d-126">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
