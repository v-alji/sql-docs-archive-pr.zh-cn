---
title: 检索和查询 XML 数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], retrieving
- XML instance retrieval
ms.assetid: 24a28760-1225-42b3-9c89-c9c0332d9c51
author: rothja
ms.author: jroth
ms.openlocfilehash: d387d1b96a57dcc7100368779f8ec6078fad5c7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688632"
---
# <a name="retrieve-and-query-xml-data"></a><span data-ttu-id="bcc0c-102">检索和查询 XML 数据</span><span class="sxs-lookup"><span data-stu-id="bcc0c-102">Retrieve and Query XML Data</span></span>
  <span data-ttu-id="bcc0c-103">本主题说明查询 XML 数据必须指定的查询选项。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-103">This topic describes the query options that you have to specify to query XML data.</span></span> <span data-ttu-id="bcc0c-104">它还说明了当 XML 实例存储在数据库中时未保留的部分。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-104">It also describes the parts of XML instances that are not preserved when they are stored in databases.</span></span>  
  
##  <a name="features-of-an-xml-instance-that-are-not-preserved"></a><a name="features"></a> <span data-ttu-id="bcc0c-105">未保留的 XML 实例的功能</span><span class="sxs-lookup"><span data-stu-id="bcc0c-105">Features of an XML Instance That Are Not Preserved</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bcc0c-106">可保留 XML 实例的内容，但不会保留 XML 数据模型中认为是不重要的 XML 实例的某些方面。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-106">preserves the content of the XML instance, but does not preserve aspects of the XML instance that are not considered to be significant in the XML data model.</span></span> <span data-ttu-id="bcc0c-107">这意味着检索到的 XML 实例可能与服务器中存储的实例不相同，但将包含同样的信息。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-107">This means that a retrieved XML instance might not be identical to the instance that was stored in the server, but will contain the same information.</span></span>  
  
### <a name="xml-declaration"></a><span data-ttu-id="bcc0c-108">XML 声明</span><span class="sxs-lookup"><span data-stu-id="bcc0c-108">XML Declaration</span></span>  
 <span data-ttu-id="bcc0c-109">当将某个实例存储在数据库中时，不会保留该实例中的 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-109">The XML declaration in an instance is not preserved when the instance is stored in the database.</span></span> <span data-ttu-id="bcc0c-110">例如：</span><span class="sxs-lookup"><span data-stu-id="bcc0c-110">For example:</span></span>  
  
```  
CREATE TABLE T1 (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T1 values (1, '<?xml version="1.0" encoding="windows-1252" ?><doc></doc>')  
GO  
SELECT Col2  
FROM T1  
```  
  
 <span data-ttu-id="bcc0c-111">结果为 `<doc/>`。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-111">The result is `<doc/>`.</span></span>  
  
 <span data-ttu-id="bcc0c-112">当在 `xml` 数据类型实例中存储 XML 数据时，不会保留 XML 声明（如 `<?xml version='1.0'?>`）。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-112">The XML declaration, such as `<?xml version='1.0'?>`, is not preserved when storing XML data in an `xml` data type instance.</span></span> <span data-ttu-id="bcc0c-113">这是设计的结果。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-113">This is by design.</span></span> <span data-ttu-id="bcc0c-114">将数据转换为类型后，XML 声明 ( # A1 及其特性 (版本/编码/独立) 会丢失 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-114">The XML declaration () and its attributes (version/encoding/stand-alone) are lost after data is converted to type `xml`.</span></span> <span data-ttu-id="bcc0c-115">XML 声明被视为对 XML 分析器的指令。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-115">The XML declaration is treated as a directive to the XML parser.</span></span> <span data-ttu-id="bcc0c-116">XML 数据在内部存储为 ucs-2。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-116">The XML data is stored internally as ucs-2.</span></span> <span data-ttu-id="bcc0c-117">XML 实例中所有其他 PI 均被保留。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-117">All other PIs in the XML instance are preserved.</span></span>  
  
  
### <a name="order-of-attributes"></a><span data-ttu-id="bcc0c-118">属性的顺序</span><span class="sxs-lookup"><span data-stu-id="bcc0c-118">Order of Attributes</span></span>  
 <span data-ttu-id="bcc0c-119">不保留 XML 实例中的属性顺序。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-119">The order of attributes in an XML instance is not preserved.</span></span> <span data-ttu-id="bcc0c-120">查询存储在 `xml` 类型列中的 XML 实例时，所得 XML 中的属性顺序可能与原 XML 实例中的顺序不同。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-120">When you query the XML instance stored in the `xml` type column, the order of attributes in the resulting XML may be different from the original XML instance.</span></span>  
  
  
### <a name="quotation-marks-around-attribute-values"></a><span data-ttu-id="bcc0c-121">属性值前后的引号</span><span class="sxs-lookup"><span data-stu-id="bcc0c-121">Quotation Marks Around Attribute Values</span></span>  
 <span data-ttu-id="bcc0c-122">不保留属性值前后的单引号和双引号。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-122">Single quotation marks and double quotations marks around attribute values are not preserved.</span></span> <span data-ttu-id="bcc0c-123">属性值作为名称和值对存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-123">The attribute values are stored in the database as a name and value pair.</span></span> <span data-ttu-id="bcc0c-124">不存储引号。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-124">The quotation marks are not stored.</span></span> <span data-ttu-id="bcc0c-125">对 XML 实例执行 XQuery 时，将用属性值前后的双引号对所得 XML 进行序列化。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-125">When an XQuery is executed against an XML instance, the resulting XML is serialized with double quotation marks around the attribute values.</span></span>  
  
```  
DECLARE @x xml  
-- Use double quotation marks.  
SET @x = '<root a="1" />'  
SELECT @x  
GO  
DECLARE @x xml  
-- Use single quotation marks.  
SET @x = '<root a=''1'' />'  
SELECT @x  
GO  
```  
  
 <span data-ttu-id="bcc0c-126">两个查询都返回 `<root a="1" />`。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-126">Both queries return = `<root a="1" />`.</span></span>  
  
  
### <a name="namespace-prefixes"></a><span data-ttu-id="bcc0c-127">命名空间前缀</span><span class="sxs-lookup"><span data-stu-id="bcc0c-127">Namespace Prefixes</span></span>  
 <span data-ttu-id="bcc0c-128">不保留命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-128">Namespace prefixes are not preserved.</span></span> <span data-ttu-id="bcc0c-129">对 `xml` 类型列指定 XQuery 时，序列化的 XML 结果可能会返回不同的命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-129">When you specify XQuery against an `xml` type column, the serialized XML result may return different namespace prefixes.</span></span>  
  
```  
DECLARE @x xml  
SET @x = '<ns1:root xmlns:ns1="abc" xmlns:ns2="abc">  
            <ns2:SomeElement/>  
          </ns1:root>'  
SELECT @x  
SELECT @x.query('/*')  
GO  
```  
  
 <span data-ttu-id="bcc0c-130">结果中的命名空间前缀可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-130">The namespace prefix in the result may be different.</span></span> <span data-ttu-id="bcc0c-131">例如：</span><span class="sxs-lookup"><span data-stu-id="bcc0c-131">For example:</span></span>  
  
```  
<p1:root xmlns:p1="abc"><p1:SomeElement/></p1:root>  
```  
  
  
##  <a name="setting-required-query-options"></a><a name="query"></a> <span data-ttu-id="bcc0c-132">设置所需的查询选项</span><span class="sxs-lookup"><span data-stu-id="bcc0c-132">Setting Required Query Options</span></span>  
 <span data-ttu-id="bcc0c-133">`xml`使用数据类型方法查询类型列或变量时 `xml` ，必须按所示设置以下选项。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-133">When querying `xml` type columns or variables using `xml` data type methods, the following options must be set as shown.</span></span>  
  
|<span data-ttu-id="bcc0c-134">SET 选项</span><span class="sxs-lookup"><span data-stu-id="bcc0c-134">SET Options</span></span>|<span data-ttu-id="bcc0c-135">所需值</span><span class="sxs-lookup"><span data-stu-id="bcc0c-135">Required Values</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="bcc0c-136">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="bcc0c-136">ANSI_NULLS</span></span>|<span data-ttu-id="bcc0c-137">ON</span><span class="sxs-lookup"><span data-stu-id="bcc0c-137">ON</span></span>|  
|<span data-ttu-id="bcc0c-138">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="bcc0c-138">ANSI_PADDING</span></span>|<span data-ttu-id="bcc0c-139">ON</span><span class="sxs-lookup"><span data-stu-id="bcc0c-139">ON</span></span>|  
|<span data-ttu-id="bcc0c-140">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="bcc0c-140">ANSI_WARNINGS</span></span>|<span data-ttu-id="bcc0c-141">ON</span><span class="sxs-lookup"><span data-stu-id="bcc0c-141">ON</span></span>|  
|<span data-ttu-id="bcc0c-142">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="bcc0c-142">ARITHABORT</span></span>|<span data-ttu-id="bcc0c-143">ON</span><span class="sxs-lookup"><span data-stu-id="bcc0c-143">ON</span></span>|  
|<span data-ttu-id="bcc0c-144">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="bcc0c-144">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="bcc0c-145">ON</span><span class="sxs-lookup"><span data-stu-id="bcc0c-145">ON</span></span>|  
|<span data-ttu-id="bcc0c-146">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="bcc0c-146">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="bcc0c-147">OFF</span><span class="sxs-lookup"><span data-stu-id="bcc0c-147">OFF</span></span>|  
|<span data-ttu-id="bcc0c-148">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="bcc0c-148">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="bcc0c-149">ON</span><span class="sxs-lookup"><span data-stu-id="bcc0c-149">ON</span></span>|  
  
 <span data-ttu-id="bcc0c-150">如果未按所示方式设置这些选项，则对数据类型方法的查询和修改 `xml` 将失败。</span><span class="sxs-lookup"><span data-stu-id="bcc0c-150">If the options are not set as shown, queries and modifications on `xml` data type methods will fail.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="bcc0c-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bcc0c-151">See Also</span></span>  
 [<span data-ttu-id="bcc0c-152">创建 XML 数据的实例</span><span class="sxs-lookup"><span data-stu-id="bcc0c-152">Create Instances of XML Data</span></span>](create-instances-of-xml-data.md)  
  
  
