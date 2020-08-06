---
title: SQLXML 4.0) 的其他批注 (|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: rothja
ms.author: jroth
ms.openlocfilehash: b654568c93df0a0c3e08cf6eaa615b7026a9c18a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586586"
---
# <a name="other-annotations-sqlxml-40"></a><span data-ttu-id="e14ce-102">其他批注 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e14ce-102">Other Annotations (SQLXML 4.0)</span></span>
  <span data-ttu-id="e14ce-103">除本节上文的主题中介绍的批注之外，XML 大容量加载还解释了以下其他批注：</span><span class="sxs-lookup"><span data-stu-id="e14ce-103">In addition to the annotations discussed in the previous topics in this section, XML Bulk Load interprets these other annotations, as follows:</span></span>  
  
 `sql:id-prefix`  
 <span data-ttu-id="e14ce-104">如果架构为 XML 数据指定了前缀，XML 大容量加载在将这些数据发送到 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之前会删除这些前缀。</span><span class="sxs-lookup"><span data-stu-id="e14ce-104">If the schema specifies prefixes to the XML data, XML Bulk Load removes the prefixes before sending the data to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `sql:use-cdata`  
 <span data-ttu-id="e14ce-105">XML 大容量加载读取存储在 CDATA 部分中的文本，然后将其发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e14ce-105">XML Bulk Load reads the text that is stored in the CDATA sections and sends it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `sql:url-encode`  
 <span data-ttu-id="e14ce-106">XML 大容量加载不支持此批注。</span><span class="sxs-lookup"><span data-stu-id="e14ce-106">XML Bulk Load does not support this annotation.</span></span> <span data-ttu-id="e14ce-107">例如，不能在 XML 数据输入中指定某一 URL 并期望大容量加载从该位置读取数据，以将其存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="e14ce-107">For example, you cannot specify a URL in the XML data input and expect XML Bulk Load to read data from that location to store it in the database.</span></span>  
  
 `sql:is-mapping-schema`  
 <span data-ttu-id="e14ce-108">XML 大容量加载不支持此批注，也不支持 `sql:id`。</span><span class="sxs-lookup"><span data-stu-id="e14ce-108">XML Bulk Load does not support this annotation, nor does it support `sql:id`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e14ce-109">XML 大容量加载不支持内联映射架构。</span><span class="sxs-lookup"><span data-stu-id="e14ce-109">XML Bulk Load does not support inline mapping schemas.</span></span>  
  
 `sql:key-fields`  
 <span data-ttu-id="e14ce-110">XML 大容量加载始终忽略此批注。</span><span class="sxs-lookup"><span data-stu-id="e14ce-110">XML Bulk Load always ignores this annotation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e14ce-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e14ce-111">See Also</span></span>  
 [<span data-ttu-id="e14ce-112">SQLXML 4.0 &#40;的批注解释&#41;</span><span class="sxs-lookup"><span data-stu-id="e14ce-112">Annotation Interpretation &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sqlxml-4-0.md)  
  
  
