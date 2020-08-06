---
title: IRowsetFastLoad::InsertRow (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::InsertRow (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e9ea952f27574270ee333919f778814ff3de462
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590182"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a><span data-ttu-id="aac91-102">IRowsetFastLoad::InsertRow (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="aac91-102">IRowsetFastLoad::InsertRow (OLE DB)</span></span>
  <span data-ttu-id="aac91-103">将行添加到大容量复制行集中。</span><span class="sxs-lookup"><span data-stu-id="aac91-103">Adds a row to the bulk copy rowset.</span></span> <span data-ttu-id="aac91-104">有关示例，请参阅[使用 IRowsetFastLoad 大容量复制数据 (OLE DB)](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) 和[使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM 将 BLOB 数据发送到 SQL Server (OLE DB)](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="aac91-104">For samples, see [Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) and [Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aac91-105">语法</span><span class="sxs-lookup"><span data-stu-id="aac91-105">Syntax</span></span>  
  
```  
  
HRESULT InsertRow(  
HACCESSOR  
hAccessor  
,  
void*  
pData  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="aac91-106">参数</span><span class="sxs-lookup"><span data-stu-id="aac91-106">Arguments</span></span>  
 <span data-ttu-id="aac91-107">\*\* hAccessor[in]</span><span class="sxs-lookup"><span data-stu-id="aac91-107">*hAccessor*[in]</span></span>  
 <span data-ttu-id="aac91-108">定义大容量复制的行数据的取值函数句柄。</span><span class="sxs-lookup"><span data-stu-id="aac91-108">The handle of the accessor defining the row data for bulk copy.</span></span> <span data-ttu-id="aac91-109">引用的取值函数为行取值函数，将绑定包含数据值的使用者拥有的内存。</span><span class="sxs-lookup"><span data-stu-id="aac91-109">The accessor referenced is a row accessor, binding consumer-owned memory containing data values.</span></span>  
  
 <span data-ttu-id="aac91-110">\*\* pData[in]</span><span class="sxs-lookup"><span data-stu-id="aac91-110">*pData*[in]</span></span>  
 <span data-ttu-id="aac91-111">指向包含数据值的使用者所拥有内存的指针。</span><span class="sxs-lookup"><span data-stu-id="aac91-111">A pointer to the consumer-owned memory containing data values.</span></span> <span data-ttu-id="aac91-112">有关详细信息，请参阅 [DBBINDING 结构](https://go.microsoft.com/fwlink/?LinkId=65955)。</span><span class="sxs-lookup"><span data-stu-id="aac91-112">For more information, see [DBBINDING Structures](https://go.microsoft.com/fwlink/?LinkId=65955).</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="aac91-113">返回代码值</span><span class="sxs-lookup"><span data-stu-id="aac91-113">Return Code Values</span></span>  
 <span data-ttu-id="aac91-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="aac91-114">S_OK</span></span>  
 <span data-ttu-id="aac91-115">方法成功。</span><span class="sxs-lookup"><span data-stu-id="aac91-115">The method succeeded.</span></span> <span data-ttu-id="aac91-116">所有列的任何绑定状态值都具有值 DBSTATUS_S_OK 或 DBSTATUS_S_NULL。</span><span class="sxs-lookup"><span data-stu-id="aac91-116">Any bound status values for all columns have value DBSTATUS_S_OK or DBSTATUS_S_NULL.</span></span>  
  
 <span data-ttu-id="aac91-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aac91-117">E_FAIL</span></span>  
 <span data-ttu-id="aac91-118">出现了错误。</span><span class="sxs-lookup"><span data-stu-id="aac91-118">An error occurred.</span></span> <span data-ttu-id="aac91-119">从行集的错误接口中发出错误信息。</span><span class="sxs-lookup"><span data-stu-id="aac91-119">Error information is available from the rowset's error interfaces.</span></span>  
  
 <span data-ttu-id="aac91-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="aac91-120">E_INVALIDARG</span></span>  
 <span data-ttu-id="aac91-121">pData 参数设置为 NULL 指针\*\*。</span><span class="sxs-lookup"><span data-stu-id="aac91-121">The *pData* argument was set to a NULL pointer.</span></span>  
  
 <span data-ttu-id="aac91-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aac91-122">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="aac91-123">SQLNCLI11 无法分配足够的内存来完成请求。</span><span class="sxs-lookup"><span data-stu-id="aac91-123">SQLNCLI11 was unable to allocate sufficient memory to complete the request.</span></span>  
  
 <span data-ttu-id="aac91-124">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="aac91-124">E_UNEXPECTED</span></span>  
 <span data-ttu-id="aac91-125">对以前被 [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) 方法作废的大容量复制行集调用了该方法。</span><span class="sxs-lookup"><span data-stu-id="aac91-125">The method was called on a bulk copy rowset previously invalidated by the [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="aac91-126">DB_E_BADACCESSORHANDLE</span><span class="sxs-lookup"><span data-stu-id="aac91-126">DB_E_BADACCESSORHANDLE</span></span>  
 <span data-ttu-id="aac91-127">使用者提供的 hAccessor 参数无效\*\*。</span><span class="sxs-lookup"><span data-stu-id="aac91-127">The *hAccessor* argument provided by the consumer was invalid.</span></span>  
  
 <span data-ttu-id="aac91-128">DB_E_BADACCESSORTYPE</span><span class="sxs-lookup"><span data-stu-id="aac91-128">DB_E_BADACCESSORTYPE</span></span>  
 <span data-ttu-id="aac91-129">指定的取值函数不是行取值函数，或者未指定使用者拥有的内存。</span><span class="sxs-lookup"><span data-stu-id="aac91-129">The specified accessor was not a row accessor or did not specify consumer-owned memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aac91-130">备注</span><span class="sxs-lookup"><span data-stu-id="aac91-130">Remarks</span></span>  
 <span data-ttu-id="aac91-131">将使用者数据转换为列的数据类型时出现错误将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导致从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序返回 E_FAIL。</span><span class="sxs-lookup"><span data-stu-id="aac91-131">An error converting consumer data to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for a column causes an E_FAIL return from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="aac91-132">可以通过任何 InsertRow 方法或只通过 Commit 方法将数据传输到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aac91-132">Data can be transmitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on any **InsertRow** method or only on **Commit** method.</span></span> <span data-ttu-id="aac91-133">在使用者应用程序收到存在数据类型转换错误的通知之前，它可以用错误数据多次调用 InsertRow 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aac91-133">The consumer application can call the **InsertRow** method many times with erroneous data before it receives notice that a data type conversion error exists.</span></span> <span data-ttu-id="aac91-134">因为 Commit 方法可确保使用者正确指定所有数据，所以使用者可在必要时使用 Commit 方法适当地验证数据\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aac91-134">Because the **Commit** method ensures that all data is correctly specified by the consumer, the consumer can use the **Commit** method appropriately to validate data as necessary.</span></span>  
  
 <span data-ttu-id="aac91-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序大容量复制行集是只写的。</span><span class="sxs-lookup"><span data-stu-id="aac91-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider bulk copy rowsets are write-only.</span></span> <span data-ttu-id="aac91-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序不公开允许使用者查询行集的方法。</span><span class="sxs-lookup"><span data-stu-id="aac91-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes no methods allowing consumer query of the rowset.</span></span> <span data-ttu-id="aac91-137">若要终止处理，使用者可以在不调用 Commit 方法的情况下释放其对 [IRowsetFastLoad](irowsetfastload-ole-db.md) 接口的引用\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aac91-137">To terminate processing, the consumer can release its reference on the [IRowsetFastLoad](irowsetfastload-ole-db.md) interface without calling the **Commit** method.</span></span> <span data-ttu-id="aac91-138">没有用于进行以下操作的设备：访问行集中使用者插入的行、更改其值或从行集中逐一删除该行。</span><span class="sxs-lookup"><span data-stu-id="aac91-138">There are no facilities for accessing a consumer-inserted row in the rowset and changing its values, or removing it individually from the rowset.</span></span>  
  
 <span data-ttu-id="aac91-139">大容量复制行在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务器上进行了格式化。</span><span class="sxs-lookup"><span data-stu-id="aac91-139">Bulk copied rows are formatted on the server for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="aac91-140">可能已针对连接或会话（例如 ANSI_PADDING）设置的任何选项均会影响行格式。</span><span class="sxs-lookup"><span data-stu-id="aac91-140">The row format is affected by any options that may have been set for the connection or session such as ANSI_PADDING.</span></span> <span data-ttu-id="aac91-141">默认情况下，此选项默认设置为通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序进行的任何连接。</span><span class="sxs-lookup"><span data-stu-id="aac91-141">This option is set on by default for any connection made through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac91-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aac91-142">See Also</span></span>  
 [<span data-ttu-id="aac91-143">IRowsetFastLoad &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="aac91-143">IRowsetFastLoad &#40;OLE DB&#41;</span></span>](irowsetfastload-ole-db.md)  
  
  
