---
title: datetime 数据类型转换 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
author: rothja
ms.author: jroth
ms.openlocfilehash: 142e4388cb87055ddbc6faa7d5b1a92a627738c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589031"
---
# <a name="datetime-data-type-conversions-odbc"></a><span data-ttu-id="1dfa6-102">datetime 数据类型转换 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="1dfa6-102">datetime Data Type Conversions (ODBC)</span></span>
  <span data-ttu-id="1dfa6-103">以下转换或者已由 ODBC 定义，或者是 ODBC 的一致扩展。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-103">The following conversions are either already defined by ODBC or are a consistent extension of ODBC.</span></span> <span data-ttu-id="1dfa6-104">每个访问接口提供的转换由该访问接口所服务的社区决定，因此，各个访问接口之间通常不一致。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-104">The conversions supplied by each provider are determined by the community served by the provider, and there are often inconsistencies between providers as a result.</span></span> <span data-ttu-id="1dfa6-105">方括号中的值是可选的。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-105">Values in square brackets are optional.</span></span>  
  
-   <span data-ttu-id="1dfa6-106">日期时间字符串的格式为 'yyyy-mm-dd[ hh:mm:ss[.9999999][ 加/减 hh:mm]]'</span><span class="sxs-lookup"><span data-stu-id="1dfa6-106">The format of datetime strings is 'yyyy-mm-dd[ hh:mm:ss[.9999999][ plus/minus hh:mm]]'</span></span>  
  
-   <span data-ttu-id="1dfa6-107">时间字符串的格式为 'hh:mm:ss[.9999999]'</span><span class="sxs-lookup"><span data-stu-id="1dfa6-107">The format of time strings is 'hh:mm:ss[.9999999]'</span></span>  
  
-   <span data-ttu-id="1dfa6-108">日期字符串的格式为 'yyyy-mm-dd'</span><span class="sxs-lookup"><span data-stu-id="1dfa6-108">The format of date strings is 'yyyy-mm-dd'</span></span>  
  
 <span data-ttu-id="1dfa6-109">从字符串转换允许更灵活处理空格和字段宽度。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-109">Conversions from strings allow flexibility in white space and field width.</span></span> <span data-ttu-id="1dfa6-110">有关详细信息，请参阅[针对 ODBC 日期和时间改进的数据类型支持](data-type-support-for-odbc-date-and-time-improvements.md)中的 "数据格式：字符串和文字" 部分。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-110">For more information, see the "Data Formats: Strings and Literals" section of [Data Type Support for ODBC Date and Time Improvements](data-type-support-for-odbc-date-and-time-improvements.md).</span></span>  
  
 <span data-ttu-id="1dfa6-111">下面是一般的转换规则：</span><span class="sxs-lookup"><span data-stu-id="1dfa6-111">The following are general conversion rules:</span></span>  
  
-   <span data-ttu-id="1dfa6-112">如果未提供时间但接收方可存储时间，则将时间设置为零。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-112">If no time is present but the receiver can store time, the time is set to zero.</span></span>  
  
-   <span data-ttu-id="1dfa6-113">如果不存在日期但接收方可以存储日期，则使用当前日期。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-113">If no date is present but the receiver can store date, the current date is used.</span></span>  
  
-   <span data-ttu-id="1dfa6-114">如果客户端正在使用的数据类型中不存在时区，但服务器可以存储时区，则在客户端时区中存储日期。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-114">If no timezone is present in the data type that the client is using but the server can store timezone, the date is stored in the client timezone.</span></span> <span data-ttu-id="1dfa6-115">请注意，此行为与服务器行为不同。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-115">Note that this differs from the server behavior.</span></span>  
  
-   <span data-ttu-id="1dfa6-116">如果服务器类型中不存在时区，但客户端类型具有时区，则先将时间转换为 UTC，再将其存储到服务器。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-116">If no timezone is present in the server type but the client type has a timezone, time is converted to UTC before being stored on the server.</span></span>  
  
-   <span data-ttu-id="1dfa6-117">如果存在时间但接收方无法存储时间，则忽略时间部分。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-117">If time is present but the receiver cannot store time, the time component is ignored.</span></span>  
  
-   <span data-ttu-id="1dfa6-118">如果存在日期但接收方无法存储日期，则忽略日期部分。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-118">If a date is present but the receiver cannot store the date, the date component is ignored.</span></span>  
  
-   <span data-ttu-id="1dfa6-119">如果在从 C 转换到 SQL 时截断了秒或秒的小数部分，则生成带有 SQLSTATE 22008 的诊断记录和消息“日期时间字段溢出”。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-119">If truncation of seconds or fractional seconds occurs when converting from C to SQL, a diagnostic record is generated with SQLSTATE 22008 and the message "Datetime field overflow".</span></span>  
  
-   <span data-ttu-id="1dfa6-120">如果在从 SQL 转换到 C 时截断了秒或秒的小数部分，则生成带有 SQLSTATE 01S07 的诊断记录和消息“截断小数部分”。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-120">If truncation of seconds or fractional seconds occurs when converting from SQL to C, a diagnostic record is generated with SQLSTATE 01S07 and the message "Fractional truncation".</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1dfa6-121">本节内容</span><span class="sxs-lookup"><span data-stu-id="1dfa6-121">In This Section</span></span>  
 [<span data-ttu-id="1dfa6-122">由 C 转换为 SQL</span><span class="sxs-lookup"><span data-stu-id="1dfa6-122">Conversions from C to SQL</span></span>](datetime-data-type-conversions-from-c-to-sql.md)  
 <span data-ttu-id="1dfa6-123">列出了在从 C 类型转换到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期/时间类型时要考虑的问题。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-123">Lists issues to consider when you convert from C types to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data/time types.</span></span>  
  
 [<span data-ttu-id="1dfa6-124">由 SQL 转换为 C</span><span class="sxs-lookup"><span data-stu-id="1dfa6-124">Conversions from SQL to C</span></span>](datetime-data-type-conversions-from-sql-to-c.md)  
 <span data-ttu-id="1dfa6-125">列出了在从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期/时间类型转换到 C 类型时要考虑的问题。</span><span class="sxs-lookup"><span data-stu-id="1dfa6-125">Lists issues to consider when you convert from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data/time types to C types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dfa6-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1dfa6-126">See Also</span></span>  
 [<span data-ttu-id="1dfa6-127">ODBC&#41;&#40;的日期和时间改进</span><span class="sxs-lookup"><span data-stu-id="1dfa6-127">Date and Time Improvements &#40;ODBC&#41;</span></span>](date-and-time-improvements-odbc.md)  
  
  
