---
title: IRowsetFastLoad (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ecf72f0015d9ed197b3b7a33d4f9bb3246134b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590181"
---
# <a name="irowsetfastload-ole-db"></a><span data-ttu-id="236b1-102">IRowsetFastLoad (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="236b1-102">IRowsetFastLoad (OLE DB)</span></span>
  <span data-ttu-id="236b1-103">`IRowsetFastLoad`接口公开对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基于内存的大容量复制操作的支持。</span><span class="sxs-lookup"><span data-stu-id="236b1-103">The `IRowsetFastLoad` interface exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory-based bulk-copy operations.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="236b1-104">Native Client OLE DB 提供者使用接口将数据快速添加到现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="236b1-104">Native Client OLE DB provider consumers use the interface to rapidly add data to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="236b1-105">如果将会话的 SSPROP_ENABLEFASTLOAD 设置为 VARIANT_TRUE，则无法读取后续从该会话返回的行集中的数据。</span><span class="sxs-lookup"><span data-stu-id="236b1-105">If you set SSPROP_ENABLEFASTLOAD to VARIANT_TRUE for a session, you cannot read data from rowsets subsequently returned from that session.</span></span> <span data-ttu-id="236b1-106">将 SSPROP_ENABLEFASTLOAD 设置为 VARIANT_TRUE 时，在会话上创建的所有行集将属于 IRowsetFastLoad 类型。</span><span class="sxs-lookup"><span data-stu-id="236b1-106">When SSPROP_ENABLEFASTLOAD is set to VARIANT_TRUE, all rowsets created on the session will be of type IRowsetFastLoad.</span></span> <span data-ttu-id="236b1-107">IRowsetFastLoad 行集不支持行集提取功能，因此无法读取这些行集中的数据。</span><span class="sxs-lookup"><span data-stu-id="236b1-107">IRowsetFastLoad rowsets do not support rowset fetch functionality; therefore, data from these rowsets cannot be read.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="236b1-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="236b1-108">In This Section</span></span>  
  
|<span data-ttu-id="236b1-109">方法</span><span class="sxs-lookup"><span data-stu-id="236b1-109">Method</span></span>|<span data-ttu-id="236b1-110">说明</span><span class="sxs-lookup"><span data-stu-id="236b1-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="236b1-111">IRowsetFastLoad::Commit &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="236b1-111">IRowsetFastLoad::Commit &#40;OLE DB&#41;</span></span>](irowsetfastload-commit-ole-db.md)|<span data-ttu-id="236b1-112">标记一批插入的行的末尾并将这些行写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="236b1-112">Marks the end of a batch of inserted rows and writes the rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|[<span data-ttu-id="236b1-113">IRowsetFastLoad::InsertRow &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="236b1-113">IRowsetFastLoad::InsertRow &#40;OLE DB&#41;</span></span>](irowsetfastload-insertrow-ole-db.md)|<span data-ttu-id="236b1-114">将行添加到大容量复制行集中。</span><span class="sxs-lookup"><span data-stu-id="236b1-114">Adds a row to the bulk copy rowset.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="236b1-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="236b1-115">See Also</span></span>  
 <span data-ttu-id="236b1-116">[接口 &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="236b1-116">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 <span data-ttu-id="236b1-117">[使用 IRowsetFastLoad &#40;的批量复制数据 OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="236b1-117">[Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) </span></span>  
 [<span data-ttu-id="236b1-118">使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM 将 BLOB 数据发送到 SQL SERVER (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="236b1-118">Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
