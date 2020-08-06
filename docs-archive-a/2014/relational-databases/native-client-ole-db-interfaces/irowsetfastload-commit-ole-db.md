---
title: IRowsetFastLoad::Commit (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
author: rothja
ms.author: jroth
ms.openlocfilehash: cfdf355919f65fd2cedacd09249e2aae59321390
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590186"
---
# <a name="irowsetfastloadcommit-ole-db"></a><span data-ttu-id="c677d-102">IRowsetFastLoad::Commit (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="c677d-102">IRowsetFastLoad::Commit (OLE DB)</span></span>
  <span data-ttu-id="c677d-103">标记一批插入的行的末尾并将这些行写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="c677d-103">Marks the end of a batch of inserted rows and writes the rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="c677d-104">有关示例，请参阅[使用 IRowsetFastLoad 大容量复制数据 (OLE DB)](irowsetfastload-ole-db.md) 和[使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM 将 BLOB 数据发送到 SQL Server (OLE DB)](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="c677d-104">For samples, see [Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md) and [Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c677d-105">语法</span><span class="sxs-lookup"><span data-stu-id="c677d-105">Syntax</span></span>  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c677d-106">参数</span><span class="sxs-lookup"><span data-stu-id="c677d-106">Arguments</span></span>  
 <span data-ttu-id="c677d-107">\*\* fDone[in]</span><span class="sxs-lookup"><span data-stu-id="c677d-107">*fDone*[in]</span></span>  
 <span data-ttu-id="c677d-108">如果是 FALSE，则行集保持有效性，并且可由使用者用于插入其他行。</span><span class="sxs-lookup"><span data-stu-id="c677d-108">If FALSE, the rowset maintains validity and can be used by the consumer for additional row insertion.</span></span> <span data-ttu-id="c677d-109">如果是 TRUE，则行集失去有效性，并且使用者无法执行进一步的插入。</span><span class="sxs-lookup"><span data-stu-id="c677d-109">If TRUE, the rowset loses validity and no further insertion can be done by the consumer.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="c677d-110">返回代码值</span><span class="sxs-lookup"><span data-stu-id="c677d-110">Return Code Values</span></span>  
 <span data-ttu-id="c677d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c677d-111">S_OK</span></span>  
 <span data-ttu-id="c677d-112">方法成功，并且所有插入的数据已写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="c677d-112">The method succeeded and all inserted data has been written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="c677d-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c677d-113">E_FAIL</span></span>  
 <span data-ttu-id="c677d-114">发生了特定于访问接口的错误。</span><span class="sxs-lookup"><span data-stu-id="c677d-114">A provider-specific error occurred.</span></span> <span data-ttu-id="c677d-115">从访问接口检索特定错误文本的错误信息。</span><span class="sxs-lookup"><span data-stu-id="c677d-115">Retrieve error information for the specific error text from the provider.</span></span>  
  
 <span data-ttu-id="c677d-116">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="c677d-116">E_UNEXPECTED</span></span>  
 <span data-ttu-id="c677d-117">对以前被 **IRowsetFastLoad::Commit** 方法作废的大容量复制行集调用了该方法。</span><span class="sxs-lookup"><span data-stu-id="c677d-117">The method was called on a bulk copy rowset previously invalidated by the **IRowsetFastLoad::Commit** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c677d-118">备注</span><span class="sxs-lookup"><span data-stu-id="c677d-118">Remarks</span></span>  
 <span data-ttu-id="c677d-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序大容量复制行集作为延迟更新模式行集的行为。</span><span class="sxs-lookup"><span data-stu-id="c677d-119">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider bulk copy rowset behaves as a delayed-update mode rowset.</span></span> <span data-ttu-id="c677d-120">当用户通过行集插入行数据时，对插入行的处理方式与在支持 IRowsetUpdate 的行集上挂起插入相同\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c677d-120">As the user inserts row data through the rowset, inserted rows are treated in the same fashion as pending inserts on a rowset supporting **IRowsetUpdate**.</span></span>  
  
 <span data-ttu-id="c677d-121">使用者必须对大容量复制行集调用 Commit 方法，才能以与使用 IRowsetUpdate::Update 方法将挂起行提交到 SQL Server 实例相同的方式将插入行写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c677d-121">The consumer must call the **Commit** method on the bulk copy rowset to write inserted rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table in the same way as the **IRowsetUpdate::Update** method is used to submit pending rows to an instance of SQL Server.</span></span>  
  
 <span data-ttu-id="c677d-122">如果使用者释放其对大容量复制行集的引用，而不调用 Commit 方法，则以前未写入的所有插入行将丢失\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c677d-122">If the consumer releases its reference on the bulk copy rowset without calling the **Commit** method, all inserted rows not previously written are lost.</span></span>  
  
 <span data-ttu-id="c677d-123">通过在将 fDone 参数设置为 FALSE 的情况下调用 Commit 方法，使用者可以成批插入行\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c677d-123">The consumer can batch inserted rows by calling the **Commit** method with the *fDone* argument set to FALSE.</span></span> <span data-ttu-id="c677d-124">当 fDone 设置为 TRUE 时，行集变为无效\*\*。</span><span class="sxs-lookup"><span data-stu-id="c677d-124">When *fDone*is set to TRUE, the rowset becomes invalid.</span></span> <span data-ttu-id="c677d-125">无效的大容量复制行集仅支持 ISupportErrorInfo 接口和 IRowsetFastLoad::Release 方法\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c677d-125">An invalid bulk copy rowset supports only the **ISupportErrorInfo** interface and **IRowsetFastLoad::Release** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c677d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c677d-126">See Also</span></span>  
 [<span data-ttu-id="c677d-127">IRowsetFastLoad &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="c677d-127">IRowsetFastLoad &#40;OLE DB&#41;</span></span>](irowsetfastload-ole-db.md)  
  
  
