---
title: 混合类型和简单内容 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
author: rothja
ms.author: jroth
ms.openlocfilehash: eb46769ee4c4d635af36a3c50fda34e8e1801b34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687559"
---
# <a name="mixed-type-and-simple-content"></a><span data-ttu-id="07b35-102">混合类型和简单内容</span><span class="sxs-lookup"><span data-stu-id="07b35-102">Mixed Type and Simple Content</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="07b35-103">不支持将混合类型限制为简单内容。</span><span class="sxs-lookup"><span data-stu-id="07b35-103">does not support restricting a mixed type to a simple content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07b35-104">示例</span><span class="sxs-lookup"><span data-stu-id="07b35-104">Example</span></span>  
 <span data-ttu-id="07b35-105">在下面的 XML 架构集合中， `myComplexTypeA` 是可以清空的复杂类型。</span><span class="sxs-lookup"><span data-stu-id="07b35-105">In the following XML schema collection, `myComplexTypeA` is a complex type that can be emptied.</span></span> <span data-ttu-id="07b35-106">即它的两个元素都将 `minOccurs` 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="07b35-106">That is, both its elements have `minOccurs` set to 0.</span></span> <span data-ttu-id="07b35-107">与在 `myComplexTypeB` 声明中一样，不支持将此限制为简单内容的尝试。</span><span class="sxs-lookup"><span data-stu-id="07b35-107">The attempt to restrict this to a simple content, as in the `myComplexTypeB` declaration, is not supported.</span></span> <span data-ttu-id="07b35-108">因此，下面的 XML 架构集合创建语句将失败：</span><span class="sxs-lookup"><span data-stu-id="07b35-108">Therefore, the following XML schema collection creation fails:</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns"  
xmlns:ns1="http://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="07b35-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07b35-109">See Also</span></span>  
 [<span data-ttu-id="07b35-110">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="07b35-110">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
