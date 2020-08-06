---
title: 错误接口中的信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: rothja
ms.author: jroth
ms.openlocfilehash: e9859ccbd804ba15685d84b98cbe74d4b096d98c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589542"
---
# <a name="information-in-error-interfaces"></a><span data-ttu-id="21cc6-102">错误接口中的信息</span><span class="sxs-lookup"><span data-stu-id="21cc6-102">Information in Error Interfaces</span></span>
  <span data-ttu-id="21cc6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序在 OLE DB 定义的错误接口**IErrorInfo**、 **IErrorRecords**和**ISQLErrorInfo**中报告一些错误和状态信息。</span><span class="sxs-lookup"><span data-stu-id="21cc6-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reports some error and status information in the OLE DB-defined error interfaces **IErrorInfo**, **IErrorRecords**, and **ISQLErrorInfo**.</span></span>  
  
 <span data-ttu-id="21cc6-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持**IErrorInfo**成员函数，如下所示。</span><span class="sxs-lookup"><span data-stu-id="21cc6-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **IErrorInfo** member functions as follows.</span></span>  
  
|<span data-ttu-id="21cc6-105">成员函数</span><span class="sxs-lookup"><span data-stu-id="21cc6-105">Member function</span></span>|<span data-ttu-id="21cc6-106">说明</span><span class="sxs-lookup"><span data-stu-id="21cc6-106">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="21cc6-107">**GetDescription**</span><span class="sxs-lookup"><span data-stu-id="21cc6-107">**GetDescription**</span></span>|<span data-ttu-id="21cc6-108">错误消息说明性字符串。</span><span class="sxs-lookup"><span data-stu-id="21cc6-108">Descriptive error message string.</span></span>|  
|<span data-ttu-id="21cc6-109">**GetGUID**</span><span class="sxs-lookup"><span data-stu-id="21cc6-109">**GetGUID**</span></span>|<span data-ttu-id="21cc6-110">定义错误的接口的 GUID。</span><span class="sxs-lookup"><span data-stu-id="21cc6-110">GUID of the interface that defined the error.</span></span>|  
|<span data-ttu-id="21cc6-111">**GetHelpContext**</span><span class="sxs-lookup"><span data-stu-id="21cc6-111">**GetHelpContext**</span></span>|<span data-ttu-id="21cc6-112">不支持。</span><span class="sxs-lookup"><span data-stu-id="21cc6-112">Not supported.</span></span> <span data-ttu-id="21cc6-113">始终返回零。</span><span class="sxs-lookup"><span data-stu-id="21cc6-113">Always returns zero.</span></span>|  
|<span data-ttu-id="21cc6-114">**GetHelpFile**</span><span class="sxs-lookup"><span data-stu-id="21cc6-114">**GetHelpFile**</span></span>|<span data-ttu-id="21cc6-115">不支持。</span><span class="sxs-lookup"><span data-stu-id="21cc6-115">Not supported.</span></span> <span data-ttu-id="21cc6-116">始终返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="21cc6-116">Always returns NULL.</span></span>|  
|<span data-ttu-id="21cc6-117">**GetSource**</span><span class="sxs-lookup"><span data-stu-id="21cc6-117">**GetSource**</span></span>|<span data-ttu-id="21cc6-118">“Microsoft SQL Server Native Client”字符串。</span><span class="sxs-lookup"><span data-stu-id="21cc6-118">String "Microsoft SQL Server Native Client".</span></span>|  
  
 <span data-ttu-id="21cc6-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持使用者可用的**IErrorRecords**成员函数，如下所示。</span><span class="sxs-lookup"><span data-stu-id="21cc6-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer-available **IErrorRecords** member functions as follows.</span></span>  
  
|<span data-ttu-id="21cc6-120">成员函数</span><span class="sxs-lookup"><span data-stu-id="21cc6-120">Member function</span></span>|<span data-ttu-id="21cc6-121">说明</span><span class="sxs-lookup"><span data-stu-id="21cc6-121">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="21cc6-122">**GetBasicErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="21cc6-122">**GetBasicErrorInfo**</span></span>|<span data-ttu-id="21cc6-123">使用有关错误的基本信息填充 ERRORINFO 结构。</span><span class="sxs-lookup"><span data-stu-id="21cc6-123">Fills an ERRORINFO structure with basic information about an error.</span></span> <span data-ttu-id="21cc6-124">ERRORINFO 结构包含标识错误的 HRESULT 返回值的成员、访问接口和该错误适用的接口。</span><span class="sxs-lookup"><span data-stu-id="21cc6-124">An ERRORINFO structure contains members that identify the HRESULT return value for the error, and the provider and interface to which the error applies.</span></span>|  
|<span data-ttu-id="21cc6-125">**GetCustomErrorObject**</span><span class="sxs-lookup"><span data-stu-id="21cc6-125">**GetCustomErrorObject**</span></span>|<span data-ttu-id="21cc6-126">返回对 ISQLErrorInfo 和 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 接口的引用  。</span><span class="sxs-lookup"><span data-stu-id="21cc6-126">Returns a reference on interfaces **ISQLErrorInfo,** and [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).</span></span>|  
|<span data-ttu-id="21cc6-127">**GetErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="21cc6-127">**GetErrorInfo**</span></span>|<span data-ttu-id="21cc6-128">返回对 IErrorInfo 接口的引用  。</span><span class="sxs-lookup"><span data-stu-id="21cc6-128">Returns a reference on an **IErrorInfo** interface.</span></span>|  
|<span data-ttu-id="21cc6-129">**GetErrorParameters**</span><span class="sxs-lookup"><span data-stu-id="21cc6-129">**GetErrorParameters**</span></span>|<span data-ttu-id="21cc6-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序不通过**GetErrorParameters**将参数返回给使用者。</span><span class="sxs-lookup"><span data-stu-id="21cc6-130">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not return parameters to the consumer through **GetErrorParameters**.</span></span>|  
|<span data-ttu-id="21cc6-131">**GetRecordCount**</span><span class="sxs-lookup"><span data-stu-id="21cc6-131">**GetRecordCount**</span></span>|<span data-ttu-id="21cc6-132">可用错误记录的计数。</span><span class="sxs-lookup"><span data-stu-id="21cc6-132">Count of error records available.</span></span>|  
  
 <span data-ttu-id="21cc6-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持**ISQLErrorInfo：： GetSQLInfo**参数，如下所示。</span><span class="sxs-lookup"><span data-stu-id="21cc6-133">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **ISQLErrorInfo::GetSQLInfo** parameters as follows.</span></span>  
  
|<span data-ttu-id="21cc6-134">参数</span><span class="sxs-lookup"><span data-stu-id="21cc6-134">Parameter</span></span>|<span data-ttu-id="21cc6-135">说明</span><span class="sxs-lookup"><span data-stu-id="21cc6-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21cc6-136">pbstrSQLState </span><span class="sxs-lookup"><span data-stu-id="21cc6-136">*pbstrSQLState*</span></span>|<span data-ttu-id="21cc6-137">返回错误的 SQLSTATE 值。</span><span class="sxs-lookup"><span data-stu-id="21cc6-137">Returns a SQLSTATE value for the error.</span></span> <span data-ttu-id="21cc6-138">SQLSTATE 值在 SQL-92、ODBC 和 ISO SQL 以及 API 规范中定义。</span><span class="sxs-lookup"><span data-stu-id="21cc6-138">SQLSTATE values are defined in the SQL-92, ODBC and ISO SQL, and API specifications.</span></span> <span data-ttu-id="21cc6-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 都不 OLE DB 提供程序定义的特定于实现的 SQLSTATE 值。</span><span class="sxs-lookup"><span data-stu-id="21cc6-139">Neither [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defined implementation-specific SQLSTATE values.</span></span>|  
|<span data-ttu-id="21cc6-140">plNativeError </span><span class="sxs-lookup"><span data-stu-id="21cc6-140">*plNativeError*</span></span>|<span data-ttu-id="21cc6-141">返回 master.dbo.sysmessages 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误编号（如果存在）  。</span><span class="sxs-lookup"><span data-stu-id="21cc6-141">Returns the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error number from **master.dbo.sysmessages** when available.</span></span> <span data-ttu-id="21cc6-142">在成功初始化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机客户端 OLE DB 提供程序数据源后，会提供本机错误。</span><span class="sxs-lookup"><span data-stu-id="21cc6-142">Native errors are available after a successful attempt to initialize a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source.</span></span> <span data-ttu-id="21cc6-143">尝试之前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序始终返回零。</span><span class="sxs-lookup"><span data-stu-id="21cc6-143">Prior to the attempt, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider always returns zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21cc6-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21cc6-144">See Also</span></span>  
 [<span data-ttu-id="21cc6-145">错误</span><span class="sxs-lookup"><span data-stu-id="21cc6-145">Errors</span></span>](errors.md)  
  
  
