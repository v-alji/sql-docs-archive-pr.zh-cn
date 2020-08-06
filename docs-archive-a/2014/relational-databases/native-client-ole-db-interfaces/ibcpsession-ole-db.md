---
title: IBCPSession (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d32da9c06a200d5924dbae18d6b7513f46c88ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692882"
---
# <a name="ibcpsession-ole-db"></a><span data-ttu-id="4cea1-102">IBCPSession (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="4cea1-102">IBCPSession (OLE DB)</span></span>
  <span data-ttu-id="4cea1-103">IBCPSession 接口公开了对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基于文件的大容量复制操作的支持\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4cea1-103">The **IBCPSession** interface exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file-based bulk copy operations.</span></span> <span data-ttu-id="4cea1-104">**IBCPSession**接口在与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会话相同的级别下，在 Native Client OLE DB 提供程序中公开。</span><span class="sxs-lookup"><span data-stu-id="4cea1-104">The **IBCPSession** interface is exposed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider under the same level as Sessions.</span></span> <span data-ttu-id="4cea1-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序中，数据源对象是会话对象的工厂，而大容量复制操作是在连接属性 SSPROP_ENABLEBULKCOPY 中指定的。</span><span class="sxs-lookup"><span data-stu-id="4cea1-105">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, data source objects are factories for Session objects, and bulk copy operations are specified in the connection property SSPROP_ENABLEBULKCOPY.</span></span> <span data-ttu-id="4cea1-106">此外，SSPROP_ENABLEFASTLOAD 属性应当设置为 True。</span><span class="sxs-lookup"><span data-stu-id="4cea1-106">In addition, the SSPROP_ENABLEFASTLOAD property should be set to true.</span></span>  
  
 <span data-ttu-id="4cea1-107">调用 IDBCreateSession::CreateSession 方法随后将创建 BulkCopySession 对象\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4cea1-107">Calling the **IDBCreateSession::CreateSession** method will then result in the creation of a **BulkCopySession** object.</span></span> <span data-ttu-id="4cea1-108">然后，可针对此 IBCPSession 对象的 IBCPSession 接口，采用极为相似的签名来调用通过 IBCPSession 对象公开的所有基于文件的大容量复制方法\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4cea1-108">All the file-based bulk copy methods exposed through the **IBCPSession** object are then callable with nearly similar signatures on this **IBCPSession** object's **IBCPSession** interface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cea1-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序通过[IRowsetFastLoad](irowsetfastload-ole-db.md)接口支持基于内存的大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="4cea1-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports memory-based bulk copy operations through the [IRowsetFastLoad](irowsetfastload-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="4cea1-110">有关使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序进行大容量复制操作的详细信息，请参阅[执行大容量复制操作](../native-client/features/performing-bulk-copy-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="4cea1-110">For more information about using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider for bulk copy operations, see [Performing Bulk Copy Operations](../native-client/features/performing-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="4cea1-111">有关演示如何使用 IBCPSession\*\*\*\* 接口的示例，请参阅 [IBCPSession::BCPDone (OLE DB)](ibcpsession-bcpdone-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="4cea1-111">For a sample showing how to use the **IBCPSession** interface, see [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cea1-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="4cea1-112">In This Section</span></span>  
  
|<span data-ttu-id="4cea1-113">方法</span><span class="sxs-lookup"><span data-stu-id="4cea1-113">Method</span></span>|<span data-ttu-id="4cea1-114">说明</span><span class="sxs-lookup"><span data-stu-id="4cea1-114">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4cea1-115">IBCPSession::BCPColFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4cea1-115">IBCPSession::BCPColFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcolfmt-ole-db.md)|<span data-ttu-id="4cea1-116">在程序变量与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列之间创建绑定。</span><span class="sxs-lookup"><span data-stu-id="4cea1-116">Creates a binding between program variables and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span>|  
|[<span data-ttu-id="4cea1-117">IBCPSession::BCPColumns &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4cea1-117">IBCPSession::BCPColumns &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcolumns-ole-db.md)|<span data-ttu-id="4cea1-118">设置绑定到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中列的字段数。</span><span class="sxs-lookup"><span data-stu-id="4cea1-118">Sets the number of fields that are to be bound to the columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|[<span data-ttu-id="4cea1-119">IBCPSession::BCPControl &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4cea1-119">IBCPSession::BCPControl &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcontrol-ole-db.md)|<span data-ttu-id="4cea1-120">设置大容量复制操作的选项。</span><span class="sxs-lookup"><span data-stu-id="4cea1-120">Sets the options for a bulk copy operation.</span></span>|  
|[<span data-ttu-id="4cea1-121">IBCPSession::BCPDone &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4cea1-121">IBCPSession::BCPDone &#40;OLE DB&#41;</span></span>](ibcpsession-bcpdone-ole-db.md)|<span data-ttu-id="4cea1-122">提交要发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的剩余行。</span><span class="sxs-lookup"><span data-stu-id="4cea1-122">Commits the remaining rows to be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4cea1-123">IBCPSession::BCPExec &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4cea1-123">IBCPSession::BCPExec &#40;OLE DB&#41;</span></span>](ibcpsession-bcpexec-ole-db.md)|<span data-ttu-id="4cea1-124">执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="4cea1-124">Performs the bulk copy operation.</span></span>|  
|[<span data-ttu-id="4cea1-125">IBCPSession::BCPInit &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4cea1-125">IBCPSession::BCPInit &#40;OLE DB&#41;</span></span>](ibcpsession-bcpinit-ole-db.md)|<span data-ttu-id="4cea1-126">初始化大容量复制结构，执行某些错误检查，验证数据和格式化文件名是否正确，然后打开文件。</span><span class="sxs-lookup"><span data-stu-id="4cea1-126">Initializes the bulk copy structure, performs some error checking, verifies that the data and format file names are correct, and then opens them.</span></span>|  
|[<span data-ttu-id="4cea1-127">IBCPSession::BCPReadFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4cea1-127">IBCPSession::BCPReadFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpreadfmt-ole-db.md)|<span data-ttu-id="4cea1-128">从格式化文件中读取每一列的格式信息。</span><span class="sxs-lookup"><span data-stu-id="4cea1-128">Reads format information for each column from the format file.</span></span>|  
|[<span data-ttu-id="4cea1-129">IBCPSession::BCPWriteFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4cea1-129">IBCPSession::BCPWriteFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpwritefmt-ole-db.md)|<span data-ttu-id="4cea1-130">将每一列的格式信息写入格式化文件。</span><span class="sxs-lookup"><span data-stu-id="4cea1-130">Writes format information for each column to the format file.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4cea1-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4cea1-131">See Also</span></span>  
 [<span data-ttu-id="4cea1-132">接口 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4cea1-132">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
