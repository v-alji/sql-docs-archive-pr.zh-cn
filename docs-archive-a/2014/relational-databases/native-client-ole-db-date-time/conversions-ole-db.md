---
title: 绑定和转换 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
ms.assetid: c187df58-a8c8-4c74-a76f-663abbc5f0c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 95c73bdad80b5f948a45235ad208ab307fcceff3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590204"
---
# <a name="bindings-and-conversions-ole-db"></a><span data-ttu-id="ba2f1-102">绑定和转换 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="ba2f1-102">Bindings and Conversions (OLE DB)</span></span>
  <span data-ttu-id="ba2f1-103">本节介绍如何在 `datetime` 值和 `datetimeoffset` 值之间进行转换。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-103">This section discusses how to convert between `datetime` and `datetimeoffset` values.</span></span> <span data-ttu-id="ba2f1-104">本节中描述的这些转换或者已由 OLE DB 提供，或者是 OLE DB 的一致扩展。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-104">The conversions described in this section are either already provided by OLE DB or are a consistent extension of OLE DB.</span></span>  
  
 <span data-ttu-id="ba2f1-105">OLE DB 中时间和日期的文字和字符串的格式通常遵循 ISO，并且不依赖于客户端区域性。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-105">The format of literals and strings for dates and times in OLE DB generally follows ISO, and is not dependent on the client locale.</span></span> <span data-ttu-id="ba2f1-106">但 DBTYPE_DATE 是个例外，它遵循的标准是 OLE 自动化。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-106">One exception is DBTYPE_DATE, where the standard is OLE Automation.</span></span> <span data-ttu-id="ba2f1-107">但是，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 只在数据从客户端传输或传输到客户端时在两个类型之间转换，所以，应用程序无法强制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 在 DBTYPE_DATE 和字符串格式之间转换。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-107">However, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client only converts between types when data is transmitted to or from the client, there is no way for an application to force [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client to convert between DBTYPE_DATE and string formats.</span></span> <span data-ttu-id="ba2f1-108">否则，字符串使用以下格式（括号中的文本指示某一可选元素）：</span><span class="sxs-lookup"><span data-stu-id="ba2f1-108">Otherwise, strings use the following formats (text in brackets indicates an optional element):</span></span>  
  
-   <span data-ttu-id="ba2f1-109">`datetime` 和 `datetimeoffset` 字符串的格式是：</span><span class="sxs-lookup"><span data-stu-id="ba2f1-109">The format of `datetime` and `datetimeoffset` strings is:</span></span>  
  
     <span data-ttu-id="ba2f1-110">*yyyy* -*mm* -*dd*[ *hh*：*mm*：*ss*[。*9999999*] [？？</span><span class="sxs-lookup"><span data-stu-id="ba2f1-110">*yyyy*-*mm*-*dd*[ *hh*:*mm*:*ss*[.*9999999*][ ??</span></span> <span data-ttu-id="ba2f1-111">*hh*：*mm*]]</span><span class="sxs-lookup"><span data-stu-id="ba2f1-111">*hh*:*mm*]]</span></span>  
  
-   <span data-ttu-id="ba2f1-112">`time` 字符串的格式是：</span><span class="sxs-lookup"><span data-stu-id="ba2f1-112">The format of `time` strings is:</span></span>  
  
     <span data-ttu-id="ba2f1-113">hh:mm:ss[.9999999]    </span><span class="sxs-lookup"><span data-stu-id="ba2f1-113">*hh*:*mm*:*ss*[.*9999999*]</span></span>  
  
-   <span data-ttu-id="ba2f1-114">`date` 字符串的格式是：</span><span class="sxs-lookup"><span data-stu-id="ba2f1-114">The format of `date` strings is:</span></span>  
  
     <span data-ttu-id="ba2f1-115">yyyy-mm-dd   </span><span class="sxs-lookup"><span data-stu-id="ba2f1-115">*yyyy*-*mm*-*dd*</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba2f1-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 SQLOLEDB 的早期版本实现了 OLE 转换，以防标准转换失败。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-116">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and SQLOLEDB implemented OLE conversions, in case standard conversions failed.</span></span> <span data-ttu-id="ba2f1-117">因此，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 和更高版本执行的某些转换不同于 OLE DB 规范。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-117">As a result, some conversions performed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 and later differ from the OLE DB specification.</span></span>  
  
 <span data-ttu-id="ba2f1-118">从字符串转换允许更灵活处理空格和字段宽度。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-118">Conversions from strings allow flexibility in white space and field width.</span></span> <span data-ttu-id="ba2f1-119">有关详细信息，请参阅[数据类型支持 OLE DB 日期和时间改进](data-type-support-for-ole-db-date-and-time-improvements.md)中的 "数据格式：字符串和文字" 部分。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-119">For more information, see the "Data Formats: Strings and Literals" section in [Data Type Support for OLE DB Date and Time Improvements](data-type-support-for-ole-db-date-and-time-improvements.md).</span></span>  
  
 <span data-ttu-id="ba2f1-120">下面是一般的转换规则：</span><span class="sxs-lookup"><span data-stu-id="ba2f1-120">The following are general conversion rules:</span></span>  
  
-   <span data-ttu-id="ba2f1-121">在某一字符串转换为日期/时间类型时，该字符串首先作为某一 ISO 文字进行分析。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-121">When a string is converted to a date/time type, the string is first parsed as an ISO literal.</span></span> <span data-ttu-id="ba2f1-122">如果此分析失败，则该字符串将作为某一 OLE 日期文字进行分析，该日期文字具有时间部分。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-122">If this fails, the string is parsed as an OLE date literal, which has time components.</span></span>  
  
-   <span data-ttu-id="ba2f1-123">如果未提供时间但接收方可存储时间，则将时间设置为零。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-123">If no time is present but the receiver can store time, the time is set to zero.</span></span> <span data-ttu-id="ba2f1-124">如果未提供日期但接收方可存储日期，则在使用 ISO 转换时将该日期设置为当前日期，在使用 OLE 转换时将该日期设置为 1899-12-30。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-124">If no date is present but the receiver can store a date, the date is set to the current date when ISO conversions are used and to 1899-12-30 when OLE conversions are used.</span></span>  
  
-   <span data-ttu-id="ba2f1-125">如果在客户端正使用的数据类型中未提供时区，但服务器可以存储时区，则假定客户端上的数据处于客户端时区中。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-125">If no timezone is present in the data type that the client is using, but the server can store timezone, the data on the client is assumed to be in the client timezone.</span></span>  
  
-   <span data-ttu-id="ba2f1-126">如果在服务器上未提供时区，但客户端具有时区信息，则假定采用 UTC 时区。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-126">If no timezone is present at the server but the client has timezone information, the UTC timezone is assumed.</span></span> <span data-ttu-id="ba2f1-127">此行为与服务器行为不同。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-127">This differs from server behavior.</span></span>  
  
-   <span data-ttu-id="ba2f1-128">如果提供了时间但接收方无法存储时间，则忽略时间部分。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-128">If the time is present but the receiver cannot store time, the time component is ignored.</span></span>  
  
-   <span data-ttu-id="ba2f1-129">如果提供了日期但接收方无法存储日期，则忽略日期部分。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-129">If the date is present but the receiver cannot store the date, the date component is ignored.</span></span>  
  
-   <span data-ttu-id="ba2f1-130">如果在从客户端转换为服务器时截断了秒或秒的小数部分，则返回 DB_E_ERRORSOCCURRED 并且设置状态 DBSTATUS_E_DATAOVERFLOW。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-130">If truncation of seconds or fractional seconds occurs when converting from client to server, DB_E_ERRORSOCCURRED is returned and the status DBSTATUS_E_DATAOVERFLOW is set.</span></span>  
  
-   <span data-ttu-id="ba2f1-131">如果在从服务器转换为客户端时截断了秒或秒的小数部分，则设置 DBSTATUS_S_TRUNCATED。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-131">If truncation of seconds or fractional seconds occurs when converting from server to client, DBSTATUS_S_TRUNCATED is set</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba2f1-132">本节内容</span><span class="sxs-lookup"><span data-stu-id="ba2f1-132">In This Section</span></span>  
 [<span data-ttu-id="ba2f1-133">在客户端和服务器之间执行的转换</span><span class="sxs-lookup"><span data-stu-id="ba2f1-133">Conversions Performed from Client to Server</span></span>](conversions-performed-from-client-to-server.md)  
 <span data-ttu-id="ba2f1-134">说明在使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 编写的客户端应用程序与 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]（或更高版本）之间执行的日期/时间转换。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-134">Describes date/time conversions performed between a client application written with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later).</span></span>  
  
 [<span data-ttu-id="ba2f1-135">在服务器和客户端之间执行的转换</span><span class="sxs-lookup"><span data-stu-id="ba2f1-135">Conversions Performed from Server to Client</span></span>](conversions-performed-from-server-to-client.md)  
 <span data-ttu-id="ba2f1-136">说明在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]（或更高版本）与使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 编写的客户端应用程序之间执行的日期/时间转换。</span><span class="sxs-lookup"><span data-stu-id="ba2f1-136">Describes date/time conversions performed between [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) and a client application written with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba2f1-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba2f1-137">See Also</span></span>  
 [<span data-ttu-id="ba2f1-138">日期和时间改进 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="ba2f1-138">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
