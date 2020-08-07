---
title: SQL Server Native Client 11.0 中的 UTF-16 支持 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: rothja
ms.author: jroth
ms.openlocfilehash: af8581071400db888fb508b88f8e8ae93bc71f70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589011"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a><span data-ttu-id="15344-102">SQL Server Native Client 11.0 中的 UTF-16 支持</span><span class="sxs-lookup"><span data-stu-id="15344-102">UTF-16 Support in SQL Server Native Client 11.0</span></span>
  <span data-ttu-id="15344-103">从开始 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ，如果在绑定列结果或输出参数时提供固定长度的缓冲区，并且如果在 `wchar` 终止字符之前写入缓冲区的字符是代理项对的高代理项码位，并且下一个 `wchar` 字符是低代理项代码点，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 将不会向缓冲区添加高代理项码位。</span><span class="sxs-lookup"><span data-stu-id="15344-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], if you supply a fixed-length buffer when binding a column result or output parameter and if the `wchar` character written into the buffer before the terminating character is a high surrogate code point of a surrogate pair, and if the next `wchar` character is a low surrogate code point, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will not add the high surrogate code point to the buffer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15344-104">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15344-104">See Also</span></span>  
 [<span data-ttu-id="15344-105">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="15344-105">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
