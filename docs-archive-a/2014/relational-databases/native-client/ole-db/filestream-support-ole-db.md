---
title: FILESTREAM 支持 (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: rothja
ms.author: jroth
ms.openlocfilehash: cde3c2cd1b72773cfcf17eacedeb3276dd2f63da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588490"
---
# <a name="filestream-support-ole-db"></a><span data-ttu-id="804d6-102">FILESTREAM 支持 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="804d6-102">FILESTREAM Support (OLE DB)</span></span>
  <span data-ttu-id="804d6-103">从 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 开始，OLE DB 支持增强的 FILESTREAM 功能。</span><span class="sxs-lookup"><span data-stu-id="804d6-103">Beginning with [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, OLE DB supports the enhanced FILESTREAM feature.</span></span> <span data-ttu-id="804d6-104">有关此功能的详细信息，请参阅[FILESTREAM 支持](../features/filestream-support.md)。</span><span class="sxs-lookup"><span data-stu-id="804d6-104">For more information about this feature, see [FILESTREAM Support](../features/filestream-support.md).</span></span> <span data-ttu-id="804d6-105">有关示例，请参阅 [Filestream 和 OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="804d6-105">For samples, see [Filestream and OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).</span></span>  
  
 <span data-ttu-id="804d6-106">为了发送和接收大于 2 GB 的 `varbinary(max)` 值，应用程序在参数和结果绑定中使用 `DBTYPE_IUNKNOWN`。</span><span class="sxs-lookup"><span data-stu-id="804d6-106">To send and receive `varbinary(max)` values greater than 2 GB, an application uses `DBTYPE_IUNKNOWN` in parameter and result bindings.</span></span> <span data-ttu-id="804d6-107">对于参数，提供程序必须为 ISequentialStream 和返回 ISequentialStream 的结果调用 IUnknown::QueryInterface。</span><span class="sxs-lookup"><span data-stu-id="804d6-107">For parameters the provider must call IUnknown::QueryInterface for ISequentialStream and for results that return ISequentialStream.</span></span>  
  
 <span data-ttu-id="804d6-108">对于 OLE DB，对与 ISequentialStream 值相关的检查将放宽。</span><span class="sxs-lookup"><span data-stu-id="804d6-108">For OLE DB, checking related to ISequentialStream values will be relaxed.</span></span> <span data-ttu-id="804d6-109">当*wType* `DBTYPE_IUNKNOWN` 在结构中时 `DBBINDING` ，可以通过 `DBPART_LENGTH` 从*dwPart*中省略或将数据) 缓冲区中的偏移量*obLength*处的 (数据长度设置为 ~ 0 来禁用长度检查。</span><span class="sxs-lookup"><span data-stu-id="804d6-109">When *wType* is `DBTYPE_IUNKNOWN` in the `DBBINDING` struct, length checking can be disabled either by omitting `DBPART_LENGTH` from *dwPart* or by setting the length of the data (at offset *obLength* in the data buffer) to ~0.</span></span> <span data-ttu-id="804d6-110">在此情况下，提供程序将不检查值的长度，并且将请求和返回可通过流提供的所有数据。</span><span class="sxs-lookup"><span data-stu-id="804d6-110">In this case, the provider will not check the length of the value and will request and return all of the data available through the stream.</span></span> <span data-ttu-id="804d6-111">这一更改将适用于所有大型对象 (LOB) 类型和 XML，但只在连接到 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]（或更高版本）服务器时才适用。</span><span class="sxs-lookup"><span data-stu-id="804d6-111">This change will be applied to all large object (LOB) types and XML, but only when connected to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (or later) servers.</span></span> <span data-ttu-id="804d6-112">这将为开发人员提供更高的灵活性，同时为现有应用程序和下级服务器维护一致性和向下兼容性。</span><span class="sxs-lookup"><span data-stu-id="804d6-112">This will provide greater flexibility for developers, while maintaining consistency and backwards compatibility for existing applications and downlevel servers.</span></span>  
  
 <span data-ttu-id="804d6-113">这一更改会影响传输数据的所有接口，主要影响 IRowset::GetData、ICommand::Execute 和 IRowsetFastLoad::InsertRow。</span><span class="sxs-lookup"><span data-stu-id="804d6-113">This change affects all interfaces that transfer data, principally IRowset::GetData, ICommand::Execute, and IRowsetFastLoad::InsertRow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804d6-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="804d6-114">See Also</span></span>  
 [<span data-ttu-id="804d6-115">SQL Server Native Client 编程</span><span class="sxs-lookup"><span data-stu-id="804d6-115">SQL Server Native Client Programming</span></span>](../sql-server-native-client-programming.md)  
  
  
