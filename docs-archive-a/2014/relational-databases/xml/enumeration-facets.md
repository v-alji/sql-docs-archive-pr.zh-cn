---
title: 枚举方面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e06598890d9b652879327e0351db5113cc17e6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577424"
---
# <a name="enumeration-facets"></a><span data-ttu-id="9a173-102">枚举方面</span><span class="sxs-lookup"><span data-stu-id="9a173-102">Enumeration Facets</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9a173-103">拒绝包含以下类型的 XML 架构：具有模式方面或违反这些方面的枚举的类型。</span><span class="sxs-lookup"><span data-stu-id="9a173-103">rejects XML schemas with types that have pattern facets or enumerations that violate those facets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a173-104">示例</span><span class="sxs-lookup"><span data-stu-id="9a173-104">Example</span></span>  
 <span data-ttu-id="9a173-105">下面的架构将会被拒绝，因为主要枚举值包含大小写混合的值。</span><span class="sxs-lookup"><span data-stu-id="9a173-105">The following schema would be rejected, because the featured enumeration value includes a mixed-case value.</span></span> <span data-ttu-id="9a173-106">此值违反了将值限制为只包含小写字母的模式值，从这一点来说，它也会被拒绝。</span><span class="sxs-lookup"><span data-stu-id="9a173-106">It would also be rejected because this value violates the pattern value that limits values to only lowercase letters.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a173-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a173-107">See Also</span></span>  
 [<span data-ttu-id="9a173-108">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="9a173-108">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
