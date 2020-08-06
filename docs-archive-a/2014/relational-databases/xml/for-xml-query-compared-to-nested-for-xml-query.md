---
title: FOR XML 查询与嵌套 FOR XML 查询的比较 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], comparing query types
ms.assetid: 19225b4a-ee3f-47cf-8bcc-52699eeda32c
author: rothja
ms.author: jroth
ms.openlocfilehash: ca10060702d0c7e50f2be79310c55e177dca358d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694388"
---
# <a name="for-xml-query-compared-to-nested-for-xml-query"></a><span data-ttu-id="9e214-102">FOR XML 查询与嵌套 FOR XML 查询的比较</span><span class="sxs-lookup"><span data-stu-id="9e214-102">FOR XML Query Compared to Nested FOR XML Query</span></span>
  <span data-ttu-id="9e214-103">本主题将单个 FOR XML 查询与嵌套 FOR XML 查询进行了比较。</span><span class="sxs-lookup"><span data-stu-id="9e214-103">This topic compares a single-level FOR XML query to a nested FOR XML query.</span></span> <span data-ttu-id="9e214-104">使用嵌套 FOR XML 查询的好处之一就是可以为查询结果指定一个以属性为中心和以元素为中心的 XML 的组合。</span><span class="sxs-lookup"><span data-stu-id="9e214-104">One of the benefits of using nested FOR XML queries is that you can specify a combination of attribute-centric and element-centric XML for query results.</span></span> <span data-ttu-id="9e214-105">此示例演示了这种好处。</span><span class="sxs-lookup"><span data-stu-id="9e214-105">The example demonstrates this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e214-106">示例</span><span class="sxs-lookup"><span data-stu-id="9e214-106">Example</span></span>  
 <span data-ttu-id="9e214-107">以下 `SELECT` 查询检索 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中的产品类别和子类别信息。</span><span class="sxs-lookup"><span data-stu-id="9e214-107">The following `SELECT` query retrieves product category and subcategory information in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="9e214-108">该查询中没有嵌套 FOR XML。</span><span class="sxs-lookup"><span data-stu-id="9e214-108">There is no nested FOR XML in the query.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   ProductCategory.ProductCategoryID,   
         ProductCategory.Name as CategoryName,  
         ProductSubCategory.ProductSubCategoryID,   
         ProductSubCategory.Name  
FROM     Production.ProductCategory, Production.ProductSubCategory  
WHERE    ProductCategory.ProductCategoryID = ProductSubCategory.ProductCategoryID  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
GO  
```  
  
 <span data-ttu-id="9e214-109">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="9e214-109">This is the partial result:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory ProductSubCategoryID="1" Name="Mountain Bike"/>  
  <ProductSubCategory ProductSubCategoryID="2" Name="Road Bike"/>  
  <ProductSubCategory ProductSubCategoryID="3" Name="Touring Bike"/>  
</ProductCategory>  
...  
```  
  
 <span data-ttu-id="9e214-110">如果在查询中指定 `ELEMENTS` 指令，则会收到以元素为中心的结果，如以下结果片段中所示：</span><span class="sxs-lookup"><span data-stu-id="9e214-110">If you specify the `ELEMENTS` directive in the query, you receive an element-centric result, as shown in the following result fragment:</span></span>  
  
```  
<ProductCategory>  
  <ProductCategoryID>1</ProductCategoryID>  
  <CategoryName>Bike</CategoryName>  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <Name>Mountain Bike</Name>  
  </ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  </ProductSubCategory>  
</ProductCategory>  
```  
  
 <span data-ttu-id="9e214-111">然后，假设您希望生成一个 XML 层次结构，并且它是以属性为中心和以元素为中心的 XML 组合，则如以下片段中所示：</span><span class="sxs-lookup"><span data-stu-id="9e214-111">Next, assume that you want to generate an XML hierarchy that is a combination of attribute-centric and element-centric XML, as shown in the following fragment:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 <span data-ttu-id="9e214-112">在先前的片段中，产品类别信息（如类别 ID 和类别名称）为属性。</span><span class="sxs-lookup"><span data-stu-id="9e214-112">In the previous fragment, product category information such as category ID and category name are attributes.</span></span> <span data-ttu-id="9e214-113">但是，子类别信息是以元素为中心的。</span><span class="sxs-lookup"><span data-stu-id="9e214-113">However, the subcategory information is element-centric.</span></span> <span data-ttu-id="9e214-114">若要构造 <`ProductCategory`> 元素，则可以编写 `FOR XML` 查询，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9e214-114">To construct the <`ProductCategory`> element, you can write a `FOR XML` query as shown in the following:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName  
FROM Production.ProductCategory ProdCat  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="9e214-115">结果如下：</span><span class="sxs-lookup"><span data-stu-id="9e214-115">This is the result:</span></span>  
  
```  
< ProdCat ProductCategoryID="1" CategoryName="Bikes" />  
< ProdCat ProductCategoryID="2" CategoryName="Components" />  
< ProdCat ProductCategoryID="3" CategoryName="Clothing" />  
< ProdCat ProductCategoryID="4" CategoryName="Accessories" />  
```  
  
 <span data-ttu-id="9e214-116">若要在所需的 XML 中构造嵌套 <`ProductSubCategory`> 元素，则可以添加嵌套 `FOR XML` 查询，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9e214-116">To construct the nested <`ProductSubCategory`> elements in the XML you want, you then add a nested `FOR XML` query, as shown in the following:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName  
        FROM   Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="9e214-117">请注意上述查询的以下方面：</span><span class="sxs-lookup"><span data-stu-id="9e214-117">Note the following in the previous query:</span></span>  
  
-   <span data-ttu-id="9e214-118">内部 `FOR XML` 查询检索产品子类别信息。</span><span class="sxs-lookup"><span data-stu-id="9e214-118">The inner `FOR XML` query retrieves product subcategory information.</span></span> <span data-ttu-id="9e214-119">将 `ELEMENTS` 指令添加到内部 `FOR XML` ，以生成以元素为中心的 XML（它将添加到由外部查询生成的 XML）。</span><span class="sxs-lookup"><span data-stu-id="9e214-119">The `ELEMENTS` directive is added in the inner `FOR XML` to generate element-centric XML that is added to the XML generated by the outer query.</span></span> <span data-ttu-id="9e214-120">默认情况下，外部查询生成的是以属性为中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="9e214-120">By default, the outer query generates attribute-centric XML.</span></span>  
  
-   <span data-ttu-id="9e214-121">在内部查询中，指定 `TYPE` 指令以使结果为 **xml** 类型。</span><span class="sxs-lookup"><span data-stu-id="9e214-121">In the inner query, the `TYPE` directive is specified so the result is of **xml** type.</span></span> <span data-ttu-id="9e214-122">如果未指定 `TYPE`，则结果作为 `nvarchar(max)` 类型返回，XML 数据作为实体返回。</span><span class="sxs-lookup"><span data-stu-id="9e214-122">If `TYPE` is not specified, the result is returned as `nvarchar(max)` type and the XML data is returned as entities.</span></span>  
  
-   <span data-ttu-id="9e214-123">外部查询也指定 `TYPE` 指令。</span><span class="sxs-lookup"><span data-stu-id="9e214-123">The outer query also specifies the `TYPE` directive.</span></span> <span data-ttu-id="9e214-124">因此，此查询的结果将作为 **xml** 类型返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="9e214-124">Therefore, the result of this query is returned to the client as **xml** type.</span></span>  
  
 <span data-ttu-id="9e214-125">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="9e214-125">This is the partial result:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 <span data-ttu-id="9e214-126">以下查询只是先前查询的扩展。</span><span class="sxs-lookup"><span data-stu-id="9e214-126">The following query is just an extension of the previous query.</span></span> <span data-ttu-id="9e214-127">它显示 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中完整的产品层次结构。</span><span class="sxs-lookup"><span data-stu-id="9e214-127">It shows the full product hierarchy in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="9e214-128">其中包括：</span><span class="sxs-lookup"><span data-stu-id="9e214-128">This includes the following:</span></span>  
  
-   <span data-ttu-id="9e214-129">产品类别</span><span class="sxs-lookup"><span data-stu-id="9e214-129">Product categories</span></span>  
  
-   <span data-ttu-id="9e214-130">每种类别中的产品子类别</span><span class="sxs-lookup"><span data-stu-id="9e214-130">Product subcategories in each category</span></span>  
  
-   <span data-ttu-id="9e214-131">每种子类别的产品样式</span><span class="sxs-lookup"><span data-stu-id="9e214-131">Product models in each subcategory</span></span>  
  
-   <span data-ttu-id="9e214-132">每种样式的产品</span><span class="sxs-lookup"><span data-stu-id="9e214-132">Products in each model</span></span>  
  
 <span data-ttu-id="9e214-133">您可能会发现以下查询对了解 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库非常有用：</span><span class="sxs-lookup"><span data-stu-id="9e214-133">You might find the following query useful in understanding the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName,  
               (SELECT ProductModel.ProductModelID,   
                       ProductModel.Name as ModelName,  
                       (SELECT ProductID, Name as ProductName, Color  
                        FROM   Production.Product  
                        WHERE  Product.ProductModelID =   
                               ProductModel.ProductModelID  
                        FOR XML AUTO, TYPE)  
                FROM   (SELECT distinct ProductModel.ProductModelID,   
                               ProductModel.Name  
                        FROM   Production.ProductModel,   
                               Production.Product  
                        WHERE  ProductModel.ProductModelID =   
                               Product.ProductModelID  
                        AND    Product.ProductSubCategoryID =   
                               ProductSubCategory.ProductSubCategoryID)   
                                  ProductModel  
                FOR XML AUTO, type  
               )  
        FROM Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="9e214-134">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="9e214-134">This is the partial result:</span></span>  
  
```  
<Production.ProductCategory ProductCategoryID="1" CategoryName="Bikes">  
  <Production.ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bikes</SubCategoryName>  
    <ProductModel ProductModelID="19" ModelName="Mountain-100">  
      <Production.Product ProductID="771"   
                ProductName="Mountain-100 Silver, 38" Color="Silver" />  
      <Production.Product ProductID="772"   
                ProductName="Mountain-100 Silver, 42" Color="Silver" />  
      <Production.Product ProductID="773"   
                ProductName="Mountain-100 Silver, 44" Color="Silver" />  
        ...  
    </ProductModel>  
     ...  
```  
  
 <span data-ttu-id="9e214-135">如果从生成产品子类别的嵌套 `ELEMENTS` 查询中删除 `FOR XML` 指令，则整个结果均以属性为中心。</span><span class="sxs-lookup"><span data-stu-id="9e214-135">If you remove the `ELEMENTS` directive from the nested `FOR XML` query that generates product subcategories, the whole result is attribute-centric.</span></span> <span data-ttu-id="9e214-136">然后便可以编写没有嵌套的查询。</span><span class="sxs-lookup"><span data-stu-id="9e214-136">You can then write this query without nesting.</span></span> <span data-ttu-id="9e214-137">添加 `ELEMENTS` 会使 XML 部分以属性为中心、部分以元素为中心。</span><span class="sxs-lookup"><span data-stu-id="9e214-137">The addition of `ELEMENTS` results in an XML that is partly attribute-centric and partly element-centric.</span></span> <span data-ttu-id="9e214-138">此结果无法通过单一级别的 FOR XML 查询生成。</span><span class="sxs-lookup"><span data-stu-id="9e214-138">This result cannot be generated by a single-level, FOR XML query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e214-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e214-139">See Also</span></span>  
 [<span data-ttu-id="9e214-140">使用嵌套 FOR XML 查询</span><span class="sxs-lookup"><span data-stu-id="9e214-140">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
