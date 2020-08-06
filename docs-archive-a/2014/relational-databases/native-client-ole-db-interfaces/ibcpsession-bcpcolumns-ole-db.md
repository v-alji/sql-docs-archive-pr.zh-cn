---
title: IBCPSession::BCPColumns (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColumns (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
author: rothja
ms.author: jroth
ms.openlocfilehash: c842b2a815074c0db7e6ab21e0a85eac68a986a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692886"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a><span data-ttu-id="bd1f5-102">IBCPSession::BCPColumns (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="bd1f5-102">IBCPSession::BCPColumns (OLE DB)</span></span>
  <span data-ttu-id="bd1f5-103">设置绑定到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中列的字段数。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-103">Sets the number of fields that are to be bound to the columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd1f5-104">语法</span><span class="sxs-lookup"><span data-stu-id="bd1f5-104">Syntax</span></span>  
  
```  
  
HRESULT BCPColumns(   
DBCOUNTITEMnColumns);  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd1f5-105">备注</span><span class="sxs-lookup"><span data-stu-id="bd1f5-105">Remarks</span></span>  
 <span data-ttu-id="bd1f5-106">在内部，它调用 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 以便为字段数据设置默认值。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-106">Internally it calls [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) to set the default values for field data.</span></span> <span data-ttu-id="bd1f5-107">这些默认值从当通过 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 指定表名称时提供程序内部检索的 SQL Server 列信息中获取。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-107">These default values are obtained from the SQL Server column information that the provider internally retrieves when the table name is specified through [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd1f5-108">只有在已用某一有效的文件名调用 BCPInit 后，才能调用此方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-108">This method can be called only after **BCPInit** has been called with a valid file name.</span></span>  
  
 <span data-ttu-id="bd1f5-109">只有在您要使用不同于默认设置的用户文件格式时，才应调用此方法。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-109">You should call this method only if you intend to use a user-file format that differs from the default.</span></span> <span data-ttu-id="bd1f5-110">有关默认用户文件格式的说明的详细信息，请参阅 BCPInit 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-110">For more information about a description of the default user-file format, see the **BCPInit** method.</span></span>  
  
 <span data-ttu-id="bd1f5-111">在调用 BCPColumns 方法后，必须为用户文件中的每一列都调用 BCPColFmt 方法，以便完全定义某一自定义文件格式\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-111">After calling the **BCPColumns** method, you must call the **BCPColFmt** method for each column in the user file to completely define a custom file format.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="bd1f5-112">参数</span><span class="sxs-lookup"><span data-stu-id="bd1f5-112">Arguments</span></span>  
 <span data-ttu-id="bd1f5-113">nColumns[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="bd1f5-113">*nColumns*[in]</span></span>  
 <span data-ttu-id="bd1f5-114">用户文件中字段的总数。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-114">The total number of fields in the user file.</span></span> <span data-ttu-id="bd1f5-115">即使准备将数据从用户文件大容量复制到某一 SQL Server 表，并且不想复制用户文件中的所有字段，仍必须将 nColumns 参数设置为用户字段的总数\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-115">Even if you are preparing to bulk copy data from the user file to a SQL Server table and do not intend to copy all fields in the user file, you must still set the *nColumns* argument to the total number of user-file fields.</span></span> <span data-ttu-id="bd1f5-116">然后，可通过 BCPColFmt 指定跳过的字段\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-116">The skipped fields can then be specified through **BCPColFmt**.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="bd1f5-117">返回代码值</span><span class="sxs-lookup"><span data-stu-id="bd1f5-117">Return Code Values</span></span>  
 <span data-ttu-id="bd1f5-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd1f5-118">S_OK</span></span>  
 <span data-ttu-id="bd1f5-119">方法成功。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-119">The method succeeded.</span></span>  
  
 <span data-ttu-id="bd1f5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd1f5-120">E_FAIL</span></span>  
 <span data-ttu-id="bd1f5-121">出现特定于提供程序的错误;有关详细信息，请使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)接口。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-121">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="bd1f5-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="bd1f5-122">E_UNEXPECTED</span></span>  
 <span data-ttu-id="bd1f5-123">意外调用了该方法。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-123">The call to the method was unexpected.</span></span> <span data-ttu-id="bd1f5-124">例如，在调用该方法之前，未调用 BCPInit 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-124">For example, the **BCPInit** method was not called before calling this method.</span></span> <span data-ttu-id="bd1f5-125">在为某一大容量复制操作多次调用此方法时，也会发生这一意外调用。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-125">Also occurs when this method is called more than once for a bulk copy operation.</span></span>  
  
 <span data-ttu-id="bd1f5-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bd1f5-126">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="bd1f5-127">内存不足错误。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-127">Out-of-memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1f5-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd1f5-128">See Also</span></span>  
 <span data-ttu-id="bd1f5-129">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="bd1f5-129">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="bd1f5-130">执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="bd1f5-130">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
