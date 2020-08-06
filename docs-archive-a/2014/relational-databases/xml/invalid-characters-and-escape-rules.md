---
title: 无效字符和转义规则 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, invalid characters
- FOR XML clause, escape rules
ms.assetid: f2e9b997-f400-4963-b225-59d46c6b93e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 8624a31dea4e97e05da6d86c3c0c518b9c4d0aba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693668"
---
# <a name="invalid-characters-and-escape-rules"></a><span data-ttu-id="2e718-102">无效字符和转义规则</span><span class="sxs-lookup"><span data-stu-id="2e718-102">Invalid Characters and Escape Rules</span></span>
  <span data-ttu-id="2e718-103">本主题介绍 FOR XML 子句如何处理无效的 XML 字符，并列出了在 XML 名称中无效的字符的转义规则。</span><span class="sxs-lookup"><span data-stu-id="2e718-103">This topic describes how invalid XML characters are handled by the FOR XML clause, and lists the escape rules for characters that are invalid in XML names.</span></span>  
  
## <a name="for-xml-and-invalid-characters"></a><span data-ttu-id="2e718-104">For XML 与无效字符</span><span class="sxs-lookup"><span data-stu-id="2e718-104">For XML and Invalid Characters</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2e718-105">便会对这些字符进行实体化。</span><span class="sxs-lookup"><span data-stu-id="2e718-105">entitizes invalid XML characters when they are returned within FOR XML queries that do not use the TYPE directive.</span></span>  
  
 <span data-ttu-id="2e718-106">尽管 XML 1.0 一致性分析器不管这些字符是否被实体化都会生成分析错误，但是经过实体化的格式更符合 XML 1.1。</span><span class="sxs-lookup"><span data-stu-id="2e718-106">Although XML 1.0 conformant parsers raise parse errors regardless of whether these characters are entitized or not, the entitized form is better aligned with XML 1.1.</span></span> <span data-ttu-id="2e718-107">经过实体化的格式还可能更符合未来版本的 XML 标准。</span><span class="sxs-lookup"><span data-stu-id="2e718-107">The entitized form is also potentially better aligned with future versions of the XML standard.</span></span> <span data-ttu-id="2e718-108">此外，它使得调试变得更加简单，因为无效字符的码位将变为可见的。</span><span class="sxs-lookup"><span data-stu-id="2e718-108">Additionally, it makes debugging simpler, because the code point of the invalid character becomes visible.</span></span>  
  
 <span data-ttu-id="2e718-109">对于 XML 工具的用户，不需要任何解决方法，因为无论怎样，在数据流中出现无效字符的位置，XML 分析器都将失败。</span><span class="sxs-lookup"><span data-stu-id="2e718-109">For users of XML tools, no workaround is required, because the XML parser will fail either way at the point where the invalid characters occur in the data stream.</span></span> <span data-ttu-id="2e718-110">如果您使用非 XML 工具，则这种变化可能需要您更新编程逻辑以便将这些字符作为实体化后的值来搜索。</span><span class="sxs-lookup"><span data-stu-id="2e718-110">If you use non-XML tools, this change can require you to update your programming logic to search for these characters as entitized values.</span></span>  
  
 <span data-ttu-id="2e718-111">在 FOR XML 查询中以不同的方式来实体化下列空格字符，以使它们在整个往返中都存在：</span><span class="sxs-lookup"><span data-stu-id="2e718-111">The following white space characters are entitized differently in FOR XML queries to preserve their presence through round-tripping:</span></span>  
  
-   <span data-ttu-id="2e718-112">在元素内容和属性中： **hex(0D)** （回车符）</span><span class="sxs-lookup"><span data-stu-id="2e718-112">In element content and attributes: **hex(0D)** (carriage return)</span></span>  
  
-   <span data-ttu-id="2e718-113">在属性内容中： **hex(09)** （选项卡）、 **hex(0A)** （换行符）</span><span class="sxs-lookup"><span data-stu-id="2e718-113">In attribute content: **hex(09)** (tab), **hex(0A)** (line feed)</span></span>  
  
 <span data-ttu-id="2e718-114">输出中将保留这些字符，并且分析器将不再对它们进行规范。</span><span class="sxs-lookup"><span data-stu-id="2e718-114">These characters are preserved in output, and a parser will not normalize them.</span></span>  
  
## <a name="escape-rules"></a><span data-ttu-id="2e718-115">转义规则</span><span class="sxs-lookup"><span data-stu-id="2e718-115">Escape Rules</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2e718-116">名称转换成了 XML 名称。</span><span class="sxs-lookup"><span data-stu-id="2e718-116">names that contain characters that are invalid in XML names, such as spaces, are translated into XML names in a way in which the invalid characters are translated into escaped numeric entity encoding.</span></span>  
  
 <span data-ttu-id="2e718-117">只有两个非字母字符可以出现在 XML 名称中：冒号 (:) 和下划线 (_)。</span><span class="sxs-lookup"><span data-stu-id="2e718-117">There are only two non-alphabetic characters that can occur within an XML name: the colon (:) and the underscore (_).</span></span> <span data-ttu-id="2e718-118">由于冒号已经保留给命名空间，因此下划线被选作转义符。</span><span class="sxs-lookup"><span data-stu-id="2e718-118">Because the colon is already reserved for namespaces, the underscore is chosen as the escape character.</span></span> <span data-ttu-id="2e718-119">以下是用于编码的转义规则：</span><span class="sxs-lookup"><span data-stu-id="2e718-119">Following are the escape rules that are used for encoding:</span></span>  
  
-   <span data-ttu-id="2e718-120">根据 XML 1.0 规范，任何不是有效的 XML 名称字符的 UCS-2 字符都将被转义为 _xHHHH\_。</span><span class="sxs-lookup"><span data-stu-id="2e718-120">Any UCS-2 character that is not a valid XML name character, according to the XML 1.0 specification, is escaped as _xHHHH\_.</span></span> <span data-ttu-id="2e718-121">HHHH 代表该字符对应的四位十六进制 UCS-2 代码，最重要的位排在最前面。</span><span class="sxs-lookup"><span data-stu-id="2e718-121">The HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span> <span data-ttu-id="2e718-122">例如，表名 **Order Details** 被编码为 Order_x0020_Details。</span><span class="sxs-lookup"><span data-stu-id="2e718-122">For example, the table name **Order Details** is encoded as Order_x0020_Details.</span></span>  
  
-   <span data-ttu-id="2e718-123">不适合 UCS-2 领域的字符（介于 U+00010000 到 U+0010FFFF 之间的附加 UCS-4 字符）均被编码为 _xHHHHHHHH\_。</span><span class="sxs-lookup"><span data-stu-id="2e718-123">Characters that do not fit into the UCS-2 realm (the UCS-4 additions of the range U+00010000 to U+0010FFFF) are encoded as _xHHHHHHHH\_.</span></span> <span data-ttu-id="2e718-124">如果处在 SQL Server 2000 向后兼容模式下，则 HHHHHHHH 代表该字符对应的八位十六进制 UCS-4 编码。</span><span class="sxs-lookup"><span data-stu-id="2e718-124">The HHHHHHHH stands for the eight-digit hexadecimal UCS-4 encoding of the character, if under SQL Server 2000 backward compatibility mode.</span></span> <span data-ttu-id="2e718-125">否则，会将字符编码为 _xHHHHHH\_，以便符合 ISO 标准。</span><span class="sxs-lookup"><span data-stu-id="2e718-125">Otherwise, the characters are encoded as_xHHHHHH\_, in order to align with the ISO standard.</span></span>  
  
-   <span data-ttu-id="2e718-126">下划线字符不需要进行转义，除非其后为字符 x。</span><span class="sxs-lookup"><span data-stu-id="2e718-126">The underscore character does not have to be escaped unless it is followed by the character x.</span></span> <span data-ttu-id="2e718-127">例如，表名 **Order_Details** 不进行编码。</span><span class="sxs-lookup"><span data-stu-id="2e718-127">For example, the table name **Order_Details** is not encoded.</span></span>  
  
-   <span data-ttu-id="2e718-128">标识符中的冒号不进行转义，这样 FOR XML 查询就可以生成命名空间元素和属性名称。</span><span class="sxs-lookup"><span data-stu-id="2e718-128">The colon in identifiers is not escaped As a result, the namespace element and attribute names can be generated by the FOR XML query.</span></span> <span data-ttu-id="2e718-129">例如，下面的查询将生成其名称中包含冒号的命名空间属性：</span><span class="sxs-lookup"><span data-stu-id="2e718-129">For example, the following query generates a namespace attribute that has a colon in the name:</span></span>  
  
    ```  
    SELECT 'namespace-urn' as 'xmlns:namespace',   
     1 as 'namespace:a'   
    FOR XML RAW  
    ```  
  
     <span data-ttu-id="2e718-130">此查询产生以下结果：</span><span class="sxs-lookup"><span data-stu-id="2e718-130">The query produces this result:</span></span>  
  
    ```  
    <row xmlns:namespace="namespace-urn" namespace:a="1"/>  
    ```  
  
     <span data-ttu-id="2e718-131">请注意，建议使用 WITH XMLNAMESPACES 来添加 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="2e718-131">Note that WITH XMLNAMESPACES is the recommended way to add XML namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e718-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e718-132">See Also</span></span>  
 [<span data-ttu-id="2e718-133">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2e718-133">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
