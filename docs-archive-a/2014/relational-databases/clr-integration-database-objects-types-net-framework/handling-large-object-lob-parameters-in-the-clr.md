---
title: 在 CLR 中处理大型对象 (LOB) 参数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
ms.openlocfilehash: ee791c73a6610761c2086723f9e41c2351b37dd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693976"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a><span data-ttu-id="17723-102">在 CLR 中处理大型对象 (LOB) 参数</span><span class="sxs-lookup"><span data-stu-id="17723-102">Handling Large Object (LOB) Parameters in the CLR</span></span>
  <span data-ttu-id="17723-103">分别使用 `SqlBytes` 和 `SqlChars` 来传递大型对象 (LOB) 二进制类型 (`varbinary(max)`) 和 LOB 字符类型 (`nvarchar(max)`) 参数。</span><span class="sxs-lookup"><span data-stu-id="17723-103">Use `SqlBytes` and `SqlChars` to pass large object (LOB) binary type (`varbinary(max)`) and LOB character type (`nvarchar(max)`) parameters, respectively.</span></span> <span data-ttu-id="17723-104">这些类型允许以流方式将 LOB 值从数据库传送到公共语言运行时 (CLR) 例程，而不是将整个值复制到托管空间中。</span><span class="sxs-lookup"><span data-stu-id="17723-104">These types allow streaming the LOB values from the database to the common language runtime (CLR) routine, instead of copying the entire value into managed space.</span></span> <span data-ttu-id="17723-105">`SqlBinary` 和 `SqlString` 只能用于小型二进制和字符串值。</span><span class="sxs-lookup"><span data-stu-id="17723-105">`SqlBinary` and `SqlString` should be used only for small binary and character string values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17723-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17723-106">See Also</span></span>  
 [<span data-ttu-id="17723-107">.NET Framework 中的 SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="17723-107">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
