---
title: 用户定义数据类型 (UDT) 的 FOR XML 支持 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: rothja
ms.author: jroth
ms.openlocfilehash: b668ad2da13fdfc880ab26cb2b2759ff3693f7d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694381"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a><span data-ttu-id="6c155-102">用户定义数据类型 (UDT) 的 FOR XML 支持</span><span class="sxs-lookup"><span data-stu-id="6c155-102">FOR XML Support for the User-Defined Data Types (UDT)</span></span>
  <span data-ttu-id="6c155-103">FOR XML 不支持公共语言运行时 (CLR) 用户定义数据类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="6c155-103">FOR XML does not support common language runtime (CLR) user-defined data types (UDTs).</span></span>  
  
 <span data-ttu-id="6c155-104">若要将 FOR XML 与 CLR 用户定义数据类型结合使用，请确保该数据类型具有 XML 序列化，并在 FOR XML select 子句中使用到 XML 的显式转换。</span><span class="sxs-lookup"><span data-stu-id="6c155-104">To use FOR XML with CLR user-defined data types, make sure that the data type has an XML serialization, and use an explicit cast to XML in the FOR XML select clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c155-105">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c155-105">See Also</span></span>  
 [<span data-ttu-id="6c155-106">各种 SQL Server 数据类型的 FOR XML 支持</span><span class="sxs-lookup"><span data-stu-id="6c155-106">FOR XML Support for Various SQL Server Data Types</span></span>](for-xml-support-for-various-sql-server-data-types.md)  
  
  
