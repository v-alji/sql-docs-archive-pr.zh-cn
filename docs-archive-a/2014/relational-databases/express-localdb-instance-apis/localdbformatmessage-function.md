---
title: LocalDBFormatMessage 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBFormatMessage
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 31b3152a-94cf-4f75-a31b-296d7dd16dbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ece28f19e3488fae248bf26c3a54a018ba6efd0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694469"
---
# <a name="localdbformatmessage-function"></a><span data-ttu-id="5650c-102">LocalDBFormatMessage 函数</span><span class="sxs-lookup"><span data-stu-id="5650c-102">LocalDBFormatMessage Function</span></span>
  <span data-ttu-id="5650c-103">返回指定的 SQL Server Express LocalDB 错误的本地化文本说明。</span><span class="sxs-lookup"><span data-stu-id="5650c-103">Returns the localized textual description for the specified SQL Server Express LocalDB error.</span></span>  
  
 <span data-ttu-id="5650c-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="5650c-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5650c-105">语法</span><span class="sxs-lookup"><span data-stu-id="5650c-105">Syntax</span></span>  
  
```  
HRESULT LocalDBFormatMessage(  
           HRESULT hrLocalDB,  
           DWORD dwFlags,   
           DWORD dwLanguageId,   
           LPWSTR wszMessage,   
           LPDWORD lpcchMessage   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5650c-106">参数</span><span class="sxs-lookup"><span data-stu-id="5650c-106">Parameters</span></span>  
 <span data-ttu-id="5650c-107">*hrLocalDB*</span><span class="sxs-lookup"><span data-stu-id="5650c-107">*hrLocalDB*</span></span>  
 <span data-ttu-id="5650c-108">[输入] LocalDB 错误代码。</span><span class="sxs-lookup"><span data-stu-id="5650c-108">[Input] The LocalDB error code.</span></span>  
  
 <span data-ttu-id="5650c-109">dwFlags\*\*</span><span class="sxs-lookup"><span data-stu-id="5650c-109">*dwFlags*</span></span>  
 <span data-ttu-id="5650c-110">[输入] 用于指定此函数的行为的标志。</span><span class="sxs-lookup"><span data-stu-id="5650c-110">[Input] The flags specifying the behavior of this function.</span></span>  
  
 <span data-ttu-id="5650c-111">可用标志：</span><span class="sxs-lookup"><span data-stu-id="5650c-111">Available flags:</span></span>  
  
 <span data-ttu-id="5650c-112">LOCALDB_TRUNCATE_ERR_MESSAGE</span><span class="sxs-lookup"><span data-stu-id="5650c-112">LOCALDB_TRUNCATE_ERR_MESSAGE</span></span>  
 <span data-ttu-id="5650c-113">如果输入缓冲区太小，则将截断错误消息以适合缓冲区。</span><span class="sxs-lookup"><span data-stu-id="5650c-113">If the input buffer is too short, the error message will be truncated to fit the buffer.</span></span>  
  
 <span data-ttu-id="5650c-114">*dwLanguageId*</span><span class="sxs-lookup"><span data-stu-id="5650c-114">*dwLanguageId*</span></span>  
 <span data-ttu-id="5650c-115">[输入] 所需的语言 (LANGID) 或 0，在这种情况下，将使用 Win32 FormatMessage 语言顺序。</span><span class="sxs-lookup"><span data-stu-id="5650c-115">[Input] The language desired (LANGID) or 0, in which case the Win32 FormatMessage language order is used.</span></span>  
  
 <span data-ttu-id="5650c-116">*wszMessage*</span><span class="sxs-lookup"><span data-stu-id="5650c-116">*wszMessage*</span></span>  
 <span data-ttu-id="5650c-117">[输出] 要存储 LocalDB 错误消息的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="5650c-117">[Output] The buffer to store the LocalDB error message.</span></span>  
  
 <span data-ttu-id="5650c-118">*lpcchMessage*</span><span class="sxs-lookup"><span data-stu-id="5650c-118">*lpcchMessage*</span></span>  
 <span data-ttu-id="5650c-119">[输入/输出]输入时包含*wszMessage*缓冲区的大小（以字符为限）。</span><span class="sxs-lookup"><span data-stu-id="5650c-119">[Input/Output] On input contains the size of the *wszMessage* buffer in characters.</span></span> <span data-ttu-id="5650c-120">输出时，如果给定的缓冲区太小，则包含所需的缓冲区大小（以字符数表示，包括任何尾随空格）。</span><span class="sxs-lookup"><span data-stu-id="5650c-120">On output, if the given buffer size is too small, contains the buffer size required in characters, including any trailing nulls.</span></span> <span data-ttu-id="5650c-121">如果函数成功，则包含消息中的字符数（任何尾随空格除外）。</span><span class="sxs-lookup"><span data-stu-id="5650c-121">If the function succeeds, contains the number of characters in the message, excluding any trailing nulls.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="5650c-122">返回</span><span class="sxs-lookup"><span data-stu-id="5650c-122">Returns</span></span>  
 <span data-ttu-id="5650c-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="5650c-123">S_OK</span></span>  
 <span data-ttu-id="5650c-124">函数成功。</span><span class="sxs-lookup"><span data-stu-id="5650c-124">The function succeeded.</span></span>  
  
 [<span data-ttu-id="5650c-125">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="5650c-125">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="5650c-126">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="5650c-126">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="5650c-127">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="5650c-127">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="5650c-128">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="5650c-128">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="5650c-129">LOCALDB_ERROR_UNKNOWN_ERROR_CODE</span><span class="sxs-lookup"><span data-stu-id="5650c-129">LOCALDB_ERROR_UNKNOWN_ERROR_CODE</span></span>](../express-localdb-error-messages/localdb-error-unknown-error-code.md)  
 <span data-ttu-id="5650c-130">请求的消息不存在。</span><span class="sxs-lookup"><span data-stu-id="5650c-130">The requested message does not exist.</span></span>  
  
 [<span data-ttu-id="5650c-131">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span><span class="sxs-lookup"><span data-stu-id="5650c-131">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span></span>](../express-localdb-error-messages/localdb-error-unknown-language-id.md)  
 <span data-ttu-id="5650c-132">该消息在请求的语言中不可用。</span><span class="sxs-lookup"><span data-stu-id="5650c-132">The message is not available in the requested language.</span></span>  
  
 [<span data-ttu-id="5650c-133">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5650c-133">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="5650c-134">输入缓冲区*wszMessage*太短，不请求截断。</span><span class="sxs-lookup"><span data-stu-id="5650c-134">The input buffer *wszMessage* is too short, and truncation is not requested.</span></span>  
  
 [<span data-ttu-id="5650c-135">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="5650c-135">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="5650c-136">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="5650c-136">An unexpected error occurred.</span></span> <span data-ttu-id="5650c-137">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="5650c-137">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5650c-138">备注</span><span class="sxs-lookup"><span data-stu-id="5650c-138">Remarks</span></span>  
 <span data-ttu-id="5650c-139">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="5650c-139">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5650c-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5650c-140">See Also</span></span>  
 [<span data-ttu-id="5650c-141">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="5650c-141">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
