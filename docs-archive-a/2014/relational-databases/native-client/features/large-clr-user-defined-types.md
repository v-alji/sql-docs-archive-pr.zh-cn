---
title: 大型 CLR 用户定义类型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: rothja
ms.author: jroth
ms.openlocfilehash: 27f0c13caea8c4aca63d78238509c6d05f1bf7bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688871"
---
# <a name="large-clr-user-defined-types"></a><span data-ttu-id="ff6d5-102">大型 CLR 用户定义类型</span><span class="sxs-lookup"><span data-stu-id="ff6d5-102">Large CLR User-Defined Types</span></span>
  <span data-ttu-id="ff6d5-103">在 SQL Server 2005 中，公共语言运行时 (CLR) 中的用户定义类型 (UDT) 已限制为最大 8,000 字节。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-103">In SQL Server 2005, user-defined types (UDTs) in the common language runtime (CLR) were restricted to 8,000 bytes in size.</span></span> <span data-ttu-id="ff6d5-104">这一限制在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和更高版本中已取消。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-104">This restriction has been lifted in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and later versions.</span></span> <span data-ttu-id="ff6d5-105">CLR UDT 现在以针对大型对象 (LOB) 类型的类似方式处置。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-105">CLR UDTs are now treated in a similar way to large object (LOB) types.</span></span> <span data-ttu-id="ff6d5-106">也就是说，小于或等于 8,000 字节的 UDT 在行为上与 SQL Server 2005 中相同，但支持更大的 UDT 并且将其大小报告为“无限制”。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-106">That is, UDTs less than or equal to 8,000 bytes behave the same way as in SQL Server 2005, but larger UDTs are supported and report their size as "unlimited".</span></span>  
  
 <span data-ttu-id="ff6d5-107">有关详细信息，请参阅 &#40;OLE DB&#41;和[大型 Clr 用户定义类型 &#40;ODBC&#41;](../odbc/large-clr-user-defined-types-odbc.md)中的[大型 Clr 用户定义类型](../ole-db/large-clr-user-defined-types-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-107">For more information, see [Large CLR User-Defined Types &#40;OLE DB&#41;](../ole-db/large-clr-user-defined-types-ole-db.md) and [Large CLR User-Defined Types &#40;ODBC&#41;](../odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="use-cases"></a><span data-ttu-id="ff6d5-108">用例</span><span class="sxs-lookup"><span data-stu-id="ff6d5-108">Use Cases</span></span>  
 <span data-ttu-id="ff6d5-109">对于 ODBC，对大型 UDT 的支持包括能够分块将 UDT 值作为执行时数据参数发送。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-109">For ODBC, support for large UDTs includes the ability to send UDT values in pieces as data-at-execution parameters.</span></span> <span data-ttu-id="ff6d5-110">这可以通过使用 SQLPutData 来完成。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-110">This is done by using SQLPutData.</span></span>  
  
 <span data-ttu-id="ff6d5-111">对于 OLE DB，对大型 UDT 的支持包括能够通过使用 ISequentialStream 绑定在服务器之间传送 UDT 值。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-111">For OLE DB, support for large UDTs includes the ability to stream UDT values to and from the server by using ISequentialStream binding.</span></span>  
  
 <span data-ttu-id="ff6d5-112">小于或等于 8,000 字节的 UDT 在行为上与 SQL Server 2005 中相同。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-112">UDTs less than or equal to 8,000 bytes will behave as they did in SQL Server 2005.</span></span> <span data-ttu-id="ff6d5-113">对于 OLE DB，仍可以通过使用 ISequentialStream 绑定来流式传输小型 UDT。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-113">For OLE DB, you can still stream small UDTs by using ISequentialStream binding.</span></span>  
  
 <span data-ttu-id="ff6d5-114">有时候，本机代码将必须理解 CLR UDT 的内容，但将不必实例化托管对象。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-114">Sometimes native code will have to understand the contents of CLR UDTs, but will not have to instantiate managed objects.</span></span> <span data-ttu-id="ff6d5-115">在此情况下，您可以使用自定义序列化将服务器上的 UDT 值转换为客户端的已知格式。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-115">If this is the case, you can use custom serialization to convert UDT values on the server into a well known format for clients.</span></span>  
  
 <span data-ttu-id="ff6d5-116">对于具有现有数据访问代码的应用程序，您可以通过在本机 API 中检索 UDT 并通过在混合模式应用程序中使用 C++ CLI interop 实例化它们，在客户端上利用 CLR UDT 行为。</span><span class="sxs-lookup"><span data-stu-id="ff6d5-116">For applications that have existing data access code, you can exploit CLR UDT behavior on the client by retrieving UDTs through native APIs and instantiating them by using C++ CLI interop in mixed mode applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6d5-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff6d5-117">See Also</span></span>  
 [<span data-ttu-id="ff6d5-118">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="ff6d5-118">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
