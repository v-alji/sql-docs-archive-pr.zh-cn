---
title: 表值参数 (SQL Server Native Client) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, table-valued parameters
- table-valued parameters (SQL Server Native Client)
ms.assetid: 5ee6bdcd-0309-4a20-b5c2-0e6b6839f34f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6af4979b9a77c94f52be5197b01179007a971283
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578853"
---
# <a name="table-valued-parameters-sql-server-native-client"></a><span data-ttu-id="33907-102">表值参数 (SQL Server Native Client)</span><span class="sxs-lookup"><span data-stu-id="33907-102">Table-Valued Parameters (SQL Server Native Client)</span></span>
  <span data-ttu-id="33907-103">表值参数在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 中引入，它们为将多个数据行传递到服务器提供了有效方式。</span><span class="sxs-lookup"><span data-stu-id="33907-103">Table-valued parameters were introduced in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], and provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="33907-104">表值参数提供类似于参数数组的功能，但它们提供了更好的灵活性和与 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 的更紧密集成，并且可以极大地提高性能。</span><span class="sxs-lookup"><span data-stu-id="33907-104">Table-valued parameters provide functionality similar to parameter arrays, but they offer more flexibility and closer integration with [!INCLUDE[tsql](../../../includes/tsql-md.md)], and can frequently improve performance.</span></span> <span data-ttu-id="33907-105">表值参数还可以参与基于集合的操作，而参数数组不能参与。</span><span class="sxs-lookup"><span data-stu-id="33907-105">Table-valued parameters can also participate in set-based operations, whereas parameter arrays cannot.</span></span>  
  
 <span data-ttu-id="33907-106">有关表值参数和 ODBC 的信息，请参阅[odbc&#41;&#40;表值参数](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="33907-106">For information about table-valued parameters and ODBC, see [Table-Valued Parameters &#40;ODBC&#41;](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
 <span data-ttu-id="33907-107">有关表值参数和 OLE DB 的信息，请参阅[表值参数 (OLE DB)](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="33907-107">For information about table-valued parameters and OLE DB, see [Table-Valued Parameters &#40;OLE DB&#41;](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33907-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33907-108">See Also</span></span>  
 [<span data-ttu-id="33907-109">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="33907-109">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
