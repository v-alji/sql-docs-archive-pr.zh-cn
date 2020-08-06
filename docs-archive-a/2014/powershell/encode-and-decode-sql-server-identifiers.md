---
title: 对 SQL Server 标识符进行编码和解码 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 88e7ebbc81d9c3cb91b1bf678075c5b5d0884890
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687951"
---
# <a name="encode-and-decode-sql-server-identifiers"></a><span data-ttu-id="377ed-102">对 SQL Server 标识符进行编码和解码</span><span class="sxs-lookup"><span data-stu-id="377ed-102">Encode and Decode SQL Server Identifiers</span></span>
  <span data-ttu-id="377ed-103">SQL Server 分隔标识符有时候包含 Windows PowerShell 路径名称中不支持的字符。</span><span class="sxs-lookup"><span data-stu-id="377ed-103">SQL Server delimited identifiers sometimes contain characters not supported in Windows PowerShell paths.</span></span> <span data-ttu-id="377ed-104">可以通过对其十六进制值进行编码来指定这些字符。</span><span class="sxs-lookup"><span data-stu-id="377ed-104">These characters can be specified by encoding their hexadecimal values.</span></span>  
  
1.  <span data-ttu-id="377ed-105">**开始之前：**  [限制和局限](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="377ed-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="377ed-106">**处理特殊字符：**  [对标识符进行编码](#EncodeIdent)、 [对标识符进行解码](#DecodeIdent)</span><span class="sxs-lookup"><span data-stu-id="377ed-106">**To process special characters:**  [Encoding an Identifier](#EncodeIdent), [Decoding an Identifier](#DecodeIdent)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="377ed-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="377ed-107">Before You Begin</span></span>  
 <span data-ttu-id="377ed-108">对于 Windows PowerShell 路径名称中不支持的字符，可以表示或编码为 "%" 字符，后跟代表该字符的位模式的十六进制值，如 "xx" 中所示 **%** 。</span><span class="sxs-lookup"><span data-stu-id="377ed-108">Characters that are not supported in Windows PowerShell path names can be represented, or encoded, as the "%" character followed by the hexadecimal value for the bit pattern that represents the character, as in "**%** xx".</span></span> <span data-ttu-id="377ed-109">对于 Windows PowerShell 路径中不支持的字符，始终可以使用编码来处理字符。</span><span class="sxs-lookup"><span data-stu-id="377ed-109">Encoding can always be used to handle characters that are not supported in Windows PowerShell paths.</span></span>  
  
 <span data-ttu-id="377ed-110">**Encode-SqlName** cmdlet 将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 标识符作为输入。</span><span class="sxs-lookup"><span data-stu-id="377ed-110">The **Encode-SqlName** cmdlet takes as input a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifier.</span></span> <span data-ttu-id="377ed-111">它输出一个字符串，其中包含所有不受 Windows PowerShell 语言支持且已经用“%xx”编码的字符。</span><span class="sxs-lookup"><span data-stu-id="377ed-111">It outputs a string with all the characters that are not supported by the Windows PowerShell language encoded with "%xx".</span></span> <span data-ttu-id="377ed-112">**Decode-SqlName** cmdlet 将经过编码的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 标识符作为输入并返回初始标识符。</span><span class="sxs-lookup"><span data-stu-id="377ed-112">The **Decode-SqlName** cmdlet takes as input an encoded [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifier and returns the original identifier.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="377ed-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="377ed-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="377ed-114">`Encode-Sqlname` 和 `Decode-Sqlname` cmdlet 仅对 SQL Server 分隔标识符中允许、但在 PowerShell 路径中不支持的字符进行编码和解码。</span><span class="sxs-lookup"><span data-stu-id="377ed-114">The `Encode-Sqlname` and `Decode-Sqlname` cmdlets only encode or decode the characters that are allowed in SQL Server delimited identifiers, but are not supported in PowerShell paths.</span></span> <span data-ttu-id="377ed-115">下面是可通过 **Encode-SqlName** 编码并可通过 **Decode-SqlName**解码的字符：</span><span class="sxs-lookup"><span data-stu-id="377ed-115">These are the characters encoded by **Encode-SqlName** and decoded by **Decode-SqlName**:</span></span>  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="377ed-116">**字符**</span><span class="sxs-lookup"><span data-stu-id="377ed-116">**Character**</span></span>|\ |/|<span data-ttu-id="377ed-117">:</span><span class="sxs-lookup"><span data-stu-id="377ed-117">:</span></span>|%|\<|>|*|<span data-ttu-id="377ed-118">?</span><span class="sxs-lookup"><span data-stu-id="377ed-118">?</span></span>|<span data-ttu-id="377ed-119">[</span><span class="sxs-lookup"><span data-stu-id="377ed-119">[</span></span>|<span data-ttu-id="377ed-120">]</span><span class="sxs-lookup"><span data-stu-id="377ed-120">]</span></span>|<span data-ttu-id="377ed-121">&#124;</span><span class="sxs-lookup"><span data-stu-id="377ed-121">&#124;</span></span>|  
|<span data-ttu-id="377ed-122">**十六进制编码**</span><span class="sxs-lookup"><span data-stu-id="377ed-122">**Hexadecimal Encoding**</span></span>|<span data-ttu-id="377ed-123">%5C</span><span class="sxs-lookup"><span data-stu-id="377ed-123">%5C</span></span>|<span data-ttu-id="377ed-124">%2F</span><span class="sxs-lookup"><span data-stu-id="377ed-124">%2F</span></span>|<span data-ttu-id="377ed-125">%3A</span><span class="sxs-lookup"><span data-stu-id="377ed-125">%3A</span></span>|<span data-ttu-id="377ed-126">%25</span><span class="sxs-lookup"><span data-stu-id="377ed-126">%25</span></span>|<span data-ttu-id="377ed-127">%3C</span><span class="sxs-lookup"><span data-stu-id="377ed-127">%3C</span></span>|<span data-ttu-id="377ed-128">%3E</span><span class="sxs-lookup"><span data-stu-id="377ed-128">%3E</span></span>|<span data-ttu-id="377ed-129">%2A</span><span class="sxs-lookup"><span data-stu-id="377ed-129">%2A</span></span>|<span data-ttu-id="377ed-130">%3F</span><span class="sxs-lookup"><span data-stu-id="377ed-130">%3F</span></span>|<span data-ttu-id="377ed-131">%5B</span><span class="sxs-lookup"><span data-stu-id="377ed-131">%5B</span></span>|<span data-ttu-id="377ed-132">%5D</span><span class="sxs-lookup"><span data-stu-id="377ed-132">%5D</span></span>|<span data-ttu-id="377ed-133">%7C</span><span class="sxs-lookup"><span data-stu-id="377ed-133">%7C</span></span>|  
  
##  <a name="encoding-an-identifier"></a><a name="EncodeIdent"></a> <span data-ttu-id="377ed-134">对标识符进行编码</span><span class="sxs-lookup"><span data-stu-id="377ed-134">Encoding an Identifier</span></span>  
 <span data-ttu-id="377ed-135">**对 PowerShell 路径中的 SQL Server 标识符进行编码**</span><span class="sxs-lookup"><span data-stu-id="377ed-135">**To encode a SQL Server identifier in a PowerShell path**</span></span>  
  
-   <span data-ttu-id="377ed-136">使用以下两种方法之一对 SQL Server 标识符进行编码：</span><span class="sxs-lookup"><span data-stu-id="377ed-136">Use one of two methods to encode a SQL Server identifier:</span></span>  
  
    -   <span data-ttu-id="377ed-137">使用语法 %XX（其中，XX 是十六进制代码）为不支持的字符指定十六进制代码。</span><span class="sxs-lookup"><span data-stu-id="377ed-137">Specify the hexadecimal code for the unsupported character using the syntax %XX, where XX is the hexadecimal code.</span></span>  
  
    -   <span data-ttu-id="377ed-138">将标识符以带引号的字符串的形式传递到 `Encode-Sqlname` cmdlet</span><span class="sxs-lookup"><span data-stu-id="377ed-138">Pass the identifier as a quoted string to the `Encode-Sqlname` cmdlet</span></span>  
  
### <a name="examples-encoding"></a><span data-ttu-id="377ed-139">示例（编码）</span><span class="sxs-lookup"><span data-stu-id="377ed-139">Examples (Encoding)</span></span>  
 <span data-ttu-id="377ed-140">此示例指定“:”字符 (%3A) 的编码版本：</span><span class="sxs-lookup"><span data-stu-id="377ed-140">This example specifies the encoded version of the ":" character (%3A):</span></span>  
  
```  
Set-Location Table%3ATest  
```  
  
 <span data-ttu-id="377ed-141">或者，可以使用 **Encode-SqlName** 生成受 Windows PowerShell 支持的名称：</span><span class="sxs-lookup"><span data-stu-id="377ed-141">Alternatively, you can use **Encode-SqlName** to build a name supported by Windows PowerShell:</span></span>  
  
```powershell
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="decoding-an-identifier"></a><a name="DecodeIdent"></a><span data-ttu-id="377ed-142">对标识符进行解码</span><span class="sxs-lookup"><span data-stu-id="377ed-142">Decoding an Identifier</span></span>  
 <span data-ttu-id="377ed-143">**对 PowerShell 路径中的 SQL Server 标识符进行解码**</span><span class="sxs-lookup"><span data-stu-id="377ed-143">**To decode a SQL Server identifier from a PowerShell path**</span></span>  
  
 <span data-ttu-id="377ed-144">使用 `Decode-Sqlname` cmdlet 可用编码表示的字符替代十六进制编码。</span><span class="sxs-lookup"><span data-stu-id="377ed-144">Use the `Decode-Sqlname` cmdlet to replace the hexadecimal encodings with the characters represented by the encoding.</span></span>  
  
### <a name="examples-decoding"></a><span data-ttu-id="377ed-145">示例（解码）</span><span class="sxs-lookup"><span data-stu-id="377ed-145">Examples (Decoding)</span></span>  
 <span data-ttu-id="377ed-146">下面的示例返回“Table:Test”：</span><span class="sxs-lookup"><span data-stu-id="377ed-146">This example returns "Table:Test":</span></span>  
  
```powershell
Decode-SqlName "Table%3ATest"  
```  
  
## <a name="see-also"></a><span data-ttu-id="377ed-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="377ed-147">See Also</span></span>  
 <span data-ttu-id="377ed-148">[SQL Server PowerShell 中的标识符](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="377ed-148">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="377ed-149">[SQL Server PowerShell 提供程序](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="377ed-149">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="377ed-150">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="377ed-150">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
