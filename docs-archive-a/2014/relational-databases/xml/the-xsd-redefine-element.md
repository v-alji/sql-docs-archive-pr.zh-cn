---
title: '&lt;xsd:redefine&gt; 元素 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: rothja
ms.author: jroth
ms.openlocfilehash: ce439e81cf87e97b4afe6e25a201e1ab0cb2a458
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691139"
---
# <a name="the-ltxsdredefinegt-element"></a><span data-ttu-id="7447c-102">&lt;xsd:redefine&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="7447c-102">The &lt;xsd:redefine&gt; Element</span></span>
  <span data-ttu-id="7447c-103">W3C XSD **redefine** 元素为重新定义架构组件提供了支持。</span><span class="sxs-lookup"><span data-stu-id="7447c-103">The W3C XSD **redefine** element provides support for redefining schema components.</span></span> <span data-ttu-id="7447c-104">但是，对此指令的支持可能会导致性能高昂，同时还要求重新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 验证与重新 `xml` 定义的架构关联的数据类型的所有实例。</span><span class="sxs-lookup"><span data-stu-id="7447c-104">However, support for this directive is potentially costly to performance and also requires that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] revalidate all instances of the `xml` data type associated with the redefined schema.</span></span> <span data-ttu-id="7447c-105">因此， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支持此元素。</span><span class="sxs-lookup"><span data-stu-id="7447c-105">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support this element.</span></span> <span data-ttu-id="7447c-106">服务器拒绝包含 \<xsd:redefine> 元素的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="7447c-106">XML schemas that include the **\<xsd:redefine>** element are rejected by the server.</span></span>  
  
 <span data-ttu-id="7447c-107">若要更新架构或其组件，您可以改为执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7447c-107">To update a schema or its components, you can do the following instead:</span></span>  
  
1.  <span data-ttu-id="7447c-108">用修改后的架构组件创建新的 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="7447c-108">Create a new XML Schema collection with the modified schema components.</span></span>  
  
2.  <span data-ttu-id="7447c-109">重新键入 `xml` (XML DT) 的所有数据类型，这些数据类型使用要重新定义的 Xml 架构集合来改用新的 Xml 架构集合。</span><span class="sxs-lookup"><span data-stu-id="7447c-109">Retype all `xml` data types (XML DT) that use the XML Schema collection to be redefined to use the new XML Schema collection instead.</span></span> <span data-ttu-id="7447c-110">为此，请使用 ALTER TABLE 命令的 ALTER COLUMN 选项来重新类型化列，或更改对变量或参数的 XML 架构集合约束。</span><span class="sxs-lookup"><span data-stu-id="7447c-110">To do this, use the ALTER COLUMN option of the ALTER TABLE command for retyping columns, or change the XML Schema collection constraints on variables or parameters.</span></span>  
  
3.  <span data-ttu-id="7447c-111">删除旧版本的 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="7447c-111">Drop the old version of the XML Schema collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7447c-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7447c-112">See Also</span></span>  
 [<span data-ttu-id="7447c-113">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="7447c-113">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
