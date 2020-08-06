---
title: xs:QName 类型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
author: rothja
ms.author: jroth
ms.openlocfilehash: 79aaf992243e665738f97c7ee1858528d6fb867c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691140"
---
# <a name="the-xsqname-type"></a><span data-ttu-id="f4fdb-102">xs:QName 类型</span><span class="sxs-lookup"><span data-stu-id="f4fdb-102">The xs:QName Type</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f4fdb-103">不支持通过使用 XML 架构限制元素从 **xs:QName** 派生的类型。</span><span class="sxs-lookup"><span data-stu-id="f4fdb-103">does not support types derived from **xs:QName** by the use of an XML Schema restriction element.</span></span> <span data-ttu-id="f4fdb-104">当前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也不支持将 **QName** 作为成员类型的联合类型。</span><span class="sxs-lookup"><span data-stu-id="f4fdb-104">Also, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] currently does not support union types with **QName** as a member type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4fdb-105">示例</span><span class="sxs-lookup"><span data-stu-id="f4fdb-105">Example</span></span>  
 <span data-ttu-id="f4fdb-106">下列 `CREATE XML SCHEMA COLLECTION` 语句无法加载 XML 架构，因为它们指定将 `xs:QName` 类型作为联合的成员类型：</span><span class="sxs-lookup"><span data-stu-id="f4fdb-106">The following `CREATE XML SCHEMA COLLECTION` statements cannot load the XML schema, because they specify the `xs:QName` type as a member type of the union:</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 <span data-ttu-id="f4fdb-107">两个语句都将失败并报告错误。</span><span class="sxs-lookup"><span data-stu-id="f4fdb-107">Both statements fail with an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4fdb-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4fdb-108">See Also</span></span>  
 [<span data-ttu-id="f4fdb-109">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="f4fdb-109">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
