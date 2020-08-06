---
title: 不确定性内容模型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- non-deterministic content models
- content models [XML in SQL Server]
ms.assetid: 9d4513e7-dd19-4491-b7c7-28bc7c2f8589
author: rothja
ms.author: jroth
ms.openlocfilehash: 6182ff4a5ee0c9c109f6880c7d3337fb6dd20749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687552"
---
# <a name="non-deterministic-content-models"></a><span data-ttu-id="e3c87-102">不确定性内容模型</span><span class="sxs-lookup"><span data-stu-id="e3c87-102">Non-Deterministic Content Models</span></span>
  <span data-ttu-id="e3c87-103">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) 之前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拒绝包含不确定性内容模型的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="e3c87-103">Before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejected XML schemas that had non-deterministic content models.</span></span>  
  
 <span data-ttu-id="e3c87-104">不过从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1 开始，如果匹配项约束为 0、1 或不受限制，则会接受不确定性内容模型。</span><span class="sxs-lookup"><span data-stu-id="e3c87-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1, however, non-deterministic content models are accepted if the occurrence constraints are 0,1, or unbounded.</span></span>  
  
## <a name="example-non-deterministic-content-model-rejected"></a><span data-ttu-id="e3c87-105">示例：已拒绝的不确定性内容模型</span><span class="sxs-lookup"><span data-stu-id="e3c87-105">Example: Non-deterministic content model rejected</span></span>  
 <span data-ttu-id="e3c87-106">下面的示例尝试创建具有不确定的内容模型的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="e3c87-106">The following example attempts to create an XML schema with a non-deterministic content model.</span></span> <span data-ttu-id="e3c87-107">此代码失败，因为不清楚 `<root>` 元素应有一个包含两个 `<a>` 元素的序列，还是 `<root>` 元素应有两个序列，其中每个序列有一个 `<a>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e3c87-107">The code fails because it is not clear whether the `<root>` element should have a sequence of two `<a>` elements or if the `<root>` element should have two sequences, each with an `<a>` element.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="1" maxOccurs="2">  
                <element name="a" type="string" minOccurs="1" maxOccurs="2"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
 <span data-ttu-id="e3c87-108">可以通过将匹配项约束移动到一个唯一的位置来修复此架构。</span><span class="sxs-lookup"><span data-stu-id="e3c87-108">The schema can be fixed by moving the occurrence constraint to a unique location.</span></span> <span data-ttu-id="e3c87-109">例如，可以将此约束移动到包含序列粒子：</span><span class="sxs-lookup"><span data-stu-id="e3c87-109">For example, the constraint can be moved to the containing sequence particle:</span></span>  
  
```  
<sequence minOccurs="1" maxOccurs="4">  
    <element name="a" type="string" minOccurs="1" maxOccurs="1"/>  
</sequence>  
```  
  
 <span data-ttu-id="e3c87-110">也可以将此约束移动到被包含元素：</span><span class="sxs-lookup"><span data-stu-id="e3c87-110">Or the constraint can be moved to the contained element:</span></span>  
  
```  
<sequence minOccurs="1" maxOccurs="1">  
     <element name="a" type="string" minOccurs="1" maxOccurs="4"/>  
</sequence>  
```  
  
## <a name="example-non-deterministic-content-model-accepted"></a><span data-ttu-id="e3c87-111">示例：已接受的不确定性内容模型</span><span class="sxs-lookup"><span data-stu-id="e3c87-111">Example: Non-deterministic content model accepted</span></span>  
 <span data-ttu-id="e3c87-112">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 版本中，会拒绝下面的架构。</span><span class="sxs-lookup"><span data-stu-id="e3c87-112">The following schema would be rejected in versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="0" maxOccurs="unbounded">  
                <element name="a" type="string" minOccurs="0" maxOccurs="1"/>  
                <element name="b" type="string" minOccurs="1" maxOccurs="unbounded"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3c87-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3c87-113">See Also</span></span>  
 [<span data-ttu-id="e3c87-114">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="e3c87-114">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
