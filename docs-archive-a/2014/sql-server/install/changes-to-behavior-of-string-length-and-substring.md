---
title: 对字符串长度和子字符串的行为的更改 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1188823a877b4c5dc9cef13431492dfe3b303e23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586214"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a><span data-ttu-id="86326-102">string-length 和 substring 行为的变化</span><span class="sxs-lookup"><span data-stu-id="86326-102">Changes to behavior of string-length and substring</span></span>
  <span data-ttu-id="86326-103">当与包含代理项字符的 XML 数据库一起使用时，[字符串长度函数 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-string-length)和[Substring 函数 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-substring)函数可能返回不同的结果。</span><span class="sxs-lookup"><span data-stu-id="86326-103">The [string-length Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-string-length) and [substring Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-substring) functions may return different results when used with XML databases that contain surrogate characters.</span></span>  
  
## <a name="description"></a><span data-ttu-id="86326-104">说明</span><span class="sxs-lookup"><span data-stu-id="86326-104">Description</span></span>  
 <span data-ttu-id="86326-105">如果数据库设置为与兼容，则在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 处理 Unicode 补充字符的情况下，[字符串长度函数 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-string-length)和[substring 函数 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-substring)函数更改。</span><span class="sxs-lookup"><span data-stu-id="86326-105">When a database is set to be compatible with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the behavior of the [string-length Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-string-length) and [substring Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-substring) functions changes when dealing with Unicode supplementary characters.</span></span> <span data-ttu-id="86326-106">每个 Unicode 增补字符（通过大于 U+FFFF 的码位来定义）将被这些函数计为一个字符，而不是早期版本中的两个字符。</span><span class="sxs-lookup"><span data-stu-id="86326-106">Each Unicode supplementary character, which is defined by having a code point larger than U+FFFF, is counted as one character by these functions rather than two, as it was in previous versions.</span></span>  
  
 <span data-ttu-id="86326-107">有关代理项字符的详细信息，请参阅[代理项和补充字符](https://go.microsoft.com/fwlink/?LinkId=178317)。</span><span class="sxs-lookup"><span data-stu-id="86326-107">For more information about surrogate characters, see [Surrogates and Supplementary Characters](https://go.microsoft.com/fwlink/?LinkId=178317).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86326-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86326-108">See Also</span></span>  
 <span data-ttu-id="86326-109">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="86326-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="86326-110">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="86326-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
