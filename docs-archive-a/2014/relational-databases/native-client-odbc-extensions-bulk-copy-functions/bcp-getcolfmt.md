---
title: bcp_getcolfmt |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_getcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: rothja
ms.author: jroth
ms.openlocfilehash: aabc811a5aa0babe5119c4ef0ed0e649586d73cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580254"
---
# <a name="bcp_getcolfmt"></a><span data-ttu-id="bdda1-102">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="bdda1-102">bcp_getcolfmt</span></span>
  <span data-ttu-id="bdda1-103">用于查找列格式属性值。</span><span class="sxs-lookup"><span data-stu-id="bdda1-103">Used to find the column format property value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdda1-104">语法</span><span class="sxs-lookup"><span data-stu-id="bdda1-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_getcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbvalue,  
INT*   
pcbLen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="bdda1-105">参数</span><span class="sxs-lookup"><span data-stu-id="bdda1-105">Arguments</span></span>  
 <span data-ttu-id="bdda1-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="bdda1-106">*hdbc*</span></span>  
 <span data-ttu-id="bdda1-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="bdda1-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="bdda1-108">*定义域*</span><span class="sxs-lookup"><span data-stu-id="bdda1-108">*field*</span></span>  
 <span data-ttu-id="bdda1-109">要检索其属性的列编号。</span><span class="sxs-lookup"><span data-stu-id="bdda1-109">Is the column number for which the property is retrieved.</span></span>  
  
 <span data-ttu-id="bdda1-110">*property*</span><span class="sxs-lookup"><span data-stu-id="bdda1-110">*property*</span></span>  
 <span data-ttu-id="bdda1-111">属性常量之一。</span><span class="sxs-lookup"><span data-stu-id="bdda1-111">Is one of the property constants.</span></span>  
  
 <span data-ttu-id="bdda1-112">*pValue*</span><span class="sxs-lookup"><span data-stu-id="bdda1-112">*pValue*</span></span>  
 <span data-ttu-id="bdda1-113">指向要从中检索属性值的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="bdda1-113">Is the pointer to the buffer from which to retrieve the property value.</span></span>  
  
 <span data-ttu-id="bdda1-114">*cbValue*</span><span class="sxs-lookup"><span data-stu-id="bdda1-114">*cbValue*</span></span>  
 <span data-ttu-id="bdda1-115">以字节表示的属性缓冲区的长度。</span><span class="sxs-lookup"><span data-stu-id="bdda1-115">Is the length of the property buffer in bytes.</span></span>  
  
 <span data-ttu-id="bdda1-116">*pcbLen*</span><span class="sxs-lookup"><span data-stu-id="bdda1-116">*pcbLen*</span></span>  
 <span data-ttu-id="bdda1-117">指向属性缓冲区中所返回数据的长度的指针。</span><span class="sxs-lookup"><span data-stu-id="bdda1-117">Pointer to length of the data that is being returned in the property buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="bdda1-118">返回</span><span class="sxs-lookup"><span data-stu-id="bdda1-118">Returns</span></span>  
 <span data-ttu-id="bdda1-119">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="bdda1-119">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdda1-120">备注</span><span class="sxs-lookup"><span data-stu-id="bdda1-120">Remarks</span></span>  
 <span data-ttu-id="bdda1-121">[Bcp_setcolfmt](bcp-setcolfmt.md)主题中列出了列格式属性值。</span><span class="sxs-lookup"><span data-stu-id="bdda1-121">Column format property values are listed in the [bcp_setcolfmt](bcp-setcolfmt.md) topic.</span></span> <span data-ttu-id="bdda1-122">列格式属性值是通过调用**bcp_setcolfmt**函数设置的，而**bcp_getcolfmt**函数用于查找列格式属性值。</span><span class="sxs-lookup"><span data-stu-id="bdda1-122">The column format property values are set by calling the **bcp_setcolfmt** function, and the **bcp_getcolfmt** function is used to find the column format property value.</span></span>  
  
 <span data-ttu-id="bdda1-123">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]与早期版本相比，连接到 (或更高版本) 服务器计算机时，可能会观察到行为更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bdda1-123">Behavior changes may be observed when connecting to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (or later) server computer, compared to earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span> <span data-ttu-id="bdda1-124">有关详细信息，请参阅[元数据发现](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="bdda1-124">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
## <a name="bcp_getcolfmt-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="bdda1-125">bcp_getcolfmt 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="bdda1-125">bcp_getcolfmt Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="bdda1-126">与 `BCP_FMT_TYPE` 日期/时间类型的属性一起使用的类型是在[&#40;OLE DB 和 ODBC&#41;的增强日期和时间类型的大容量复制更改](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)中指定的。</span><span class="sxs-lookup"><span data-stu-id="bdda1-126">The types used with the `BCP_FMT_TYPE` property for date/time types are as specified in [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="bdda1-127">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="bdda1-127">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdda1-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdda1-128">See Also</span></span>  
 [<span data-ttu-id="bdda1-129">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="bdda1-129">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
