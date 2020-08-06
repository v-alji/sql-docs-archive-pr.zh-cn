---
title: 在90或更高版本的兼容模式下，大常量被类型化为大值类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- binary constants
- CHARINDEX function
- constants
- character string constants
- PATINDEX function
ms.assetid: 6e309fa0-5fb9-45a1-9739-f13fae525bfe
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 58acde8aaebdcac629463edcfb565eed13355ad4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578013"
---
# <a name="large-constants-are-typed-as-large-value-types-in-90-or-later-compatibility-modes"></a><span data-ttu-id="0cc2d-102">在 90 或更高的兼容模式下，大的常量作为大值类型键入</span><span class="sxs-lookup"><span data-stu-id="0cc2d-102">Large constants are typed as large-value types in 90 or later compatibility modes</span></span>
  <span data-ttu-id="0cc2d-103">升级顾问检测到有大的常量存在。</span><span class="sxs-lookup"><span data-stu-id="0cc2d-103">Upgrade Advisor detected the presence of large constants.</span></span> <span data-ttu-id="0cc2d-104">大小大于 8,000 个字节的字符串常量和二进制常量在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中被视为大型对象数据类型。</span><span class="sxs-lookup"><span data-stu-id="0cc2d-104">Character string constants and binary constants that are more than 8,000 bytes in size are treated as large object data types in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="0cc2d-105">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本中，大型字符、Unicode 和二进制常量作为大值类型键入。</span><span class="sxs-lookup"><span data-stu-id="0cc2d-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, large character, Unicode, and binary constants, are typed as large-value types.</span></span>  
  
## <a name="component"></a><span data-ttu-id="0cc2d-106">组件</span><span class="sxs-lookup"><span data-stu-id="0cc2d-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="0cc2d-107">说明</span><span class="sxs-lookup"><span data-stu-id="0cc2d-107">Description</span></span>  
 <span data-ttu-id="0cc2d-108">当字符串函数（如 CHARINDEX 和 PATINDEX）与超过 8,000 个字节的字符串常量或二进制常量一起使用时，[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 将返回错误号 8116，而 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本将返回错误号 8152。</span><span class="sxs-lookup"><span data-stu-id="0cc2d-108">When string functions, such as CHARINDEX and PATINDEX, are used with string or binary constants that exceed 8,000 bytes, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] returns error number 8116, and [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions return error number 8152.</span></span>  
  
 <span data-ttu-id="0cc2d-109">在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，当字符串函数与 `text`、`ntext` 和 `image` 数据类型一起使用时，将返回错误 8116。</span><span class="sxs-lookup"><span data-stu-id="0cc2d-109">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], the string functions return error 8116 when they are used with the `text`, `ntext`, and `image` data types.</span></span>  
  
 <span data-ttu-id="0cc2d-110">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本中，大的常量被分别视为 `varchar(max)`、`nvarchar(max)` 和 `varbinary(max)` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0cc2d-110">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, the large constants are treated as `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data types, respectively.</span></span> <span data-ttu-id="0cc2d-111">这些数据类型均与字符串函数兼容。</span><span class="sxs-lookup"><span data-stu-id="0cc2d-111">These data types are compatible with string functions.</span></span>  
  
 <span data-ttu-id="0cc2d-112">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本中，字符串函数（如 CHARINDEX 和 PATINDEX）假定包含要查找的字符序列的字符串少于 8,000 个字节。</span><span class="sxs-lookup"><span data-stu-id="0cc2d-112">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, string functions, such as CHARINDEX and PATINDEX, assume the string that contains the sequence of characters to be found is less than 8,000 bytes.</span></span> <span data-ttu-id="0cc2d-113">因此，对于 CHARINDEX 和 PATINDEX，将引发错误 8152。</span><span class="sxs-lookup"><span data-stu-id="0cc2d-113">This is why error 8152 is raised for CHARINDEX and PATINDEX.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc2d-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cc2d-114">See Also</span></span>  
 <span data-ttu-id="0cc2d-115">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0cc2d-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0cc2d-116">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="0cc2d-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
