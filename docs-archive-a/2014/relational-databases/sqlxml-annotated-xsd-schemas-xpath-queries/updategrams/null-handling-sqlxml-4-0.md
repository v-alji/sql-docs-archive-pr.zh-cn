---
title: SQLXML 4.0)  (的 NULL 处理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 430643e8a6c9bd3dd00b2763990645c6a162ee40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588444"
---
# <a name="null-handling-sqlxml-40"></a><span data-ttu-id="5fa00-102">NULL 处理 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="5fa00-102">NULL Handling (SQLXML 4.0)</span></span>
  <span data-ttu-id="5fa00-103">XML 语法将 NULL 视为不存在。</span><span class="sxs-lookup"><span data-stu-id="5fa00-103">XML syntax denotes NULL as an absence.</span></span> <span data-ttu-id="5fa00-104"> (例如，如果某个属性或元素的值为 NULL，则该属性或元素在 XML 文档中不存在。在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 中 ) ， `updg:nullvalue` 特性允许为元素或属性值指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="5fa00-104">(For example, if an attribute or element value is NULL, that attribute or element is absent from the XML document.) In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, the `updg:nullvalue` attribute enables specifying NULL for an element or attribute value.</span></span>  
  
 <span data-ttu-id="5fa00-105">例如，以下 updategram 确保**ContactID**为64的联系人的**标题**值为 NULL，然后将**Title**值更新为 "Mr"。</span><span class="sxs-lookup"><span data-stu-id="5fa00-105">For example, the following updategram ensures that the **Title** value for a contact with **ContactID** of 64 is NULL, and then updates the **Title** value to "Mr."</span></span> <span data-ttu-id="5fa00-106">此联系人。</span><span class="sxs-lookup"><span data-stu-id="5fa00-106">for this contact.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="5fa00-107">参数传递到 Updategram 时，NULL 可以作为参数值进行传递。</span><span class="sxs-lookup"><span data-stu-id="5fa00-107">When parameters are passed to an updategram, NULL can be passed as the parameter value.</span></span> <span data-ttu-id="5fa00-108">通过在 `nullvalue` 块中指定 `<updg:header>` 属性，可以完成该操作。</span><span class="sxs-lookup"><span data-stu-id="5fa00-108">This is done by specifying the `nullvalue` attribute in the `<updg:header>` block.</span></span> <span data-ttu-id="5fa00-109">有关示例，请参阅[将参数传递到 updategram &#40;SQLXML 4.0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa00-109">For an example, see [Passing Parameters to Updategrams &#40;SQLXML 4.0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa00-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5fa00-110">See Also</span></span>  
 [<span data-ttu-id="5fa00-111">&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="5fa00-111">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
