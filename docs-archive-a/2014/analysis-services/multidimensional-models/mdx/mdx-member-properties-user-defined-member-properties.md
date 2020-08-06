---
title: " (MDX) 的用户定义成员属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75e5df5a0677ee205b5517f4c7ca89a390426971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689052"
---
# <a name="user-defined-member-properties-mdx"></a><span data-ttu-id="b5496-102">用户定义的成员属性 (MDX)</span><span class="sxs-lookup"><span data-stu-id="b5496-102">User-Defined Member Properties (MDX)</span></span>
  <span data-ttu-id="b5496-103">用户定义的成员属性可作为属性关系添加到维度的特定命名级别中。</span><span class="sxs-lookup"><span data-stu-id="b5496-103">User-defined member properties can be added to a specific named level in a dimension as attribute relationships.</span></span> <span data-ttu-id="b5496-104">用户定义的成员属性不能添加到层次结构的 `(All)` 级别，也不能添加到层次结构本身中。</span><span class="sxs-lookup"><span data-stu-id="b5496-104">User-defined member properties cannot be added to the `(All)` level of a hierarchy, or to the hierarchy itself.</span></span>  
  
## <a name="creating-user-defined-member-properties"></a><span data-ttu-id="b5496-105">创建用户定义的成员属性</span><span class="sxs-lookup"><span data-stu-id="b5496-105">Creating User-Defined Member Properties</span></span>  
 <span data-ttu-id="b5496-106">用户定义的成员属性可以通过用户界面或通过编程方式添加到基于服务器的维度或多维数据集中。</span><span class="sxs-lookup"><span data-stu-id="b5496-106">User-defined member properties can be added to server-based dimensions or cubes either through the user interface or programmatically:</span></span>  
  
-   <span data-ttu-id="b5496-107">若要通过用户界面添加用户定义的成员属性，请使用 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中的维度设计器。</span><span class="sxs-lookup"><span data-stu-id="b5496-107">To add user-defined member properties through the user interface, you use Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="b5496-108">有关详细信息，请参阅 [定义属性关系](../attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="b5496-108">For more information, see [Define Attribute Relationships](../attribute-relationships-define.md).</span></span>  
  
-   <span data-ttu-id="b5496-109">若要通过编程方式添加用户定义的成员属性，您的应用程序可以使用 Analysis Manager 对象 (AMO) 或者结合使用 XML for Analysis (XMLA) 和 Analysis Services 脚本语言 (ASSL)。</span><span class="sxs-lookup"><span data-stu-id="b5496-109">To add user-defined member properties programmatically, your application can use either Analysis Manager Objects (AMO) or a combination of XML for Analysis (XMLA) and Analysis Services Scripting Language (ASSL).</span></span> <span data-ttu-id="b5496-110">有关详细信息，请参阅 [属性关系](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="b5496-110">For more information, see [Attribute Relationships](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
## <a name="retrieving-user-defined-member-properties"></a><span data-ttu-id="b5496-111">检索用户定义的成员属性</span><span class="sxs-lookup"><span data-stu-id="b5496-111">Retrieving User-Defined Member Properties</span></span>  
 <span data-ttu-id="b5496-112">您可以使用 `PROPERTIES` 关键字或[properties](/sql/mdx/properties-mdx)函数检索用户定义的成员属性。</span><span class="sxs-lookup"><span data-stu-id="b5496-112">You can retrieve user-defined member properties using either the `PROPERTIES` keyword or the [Properties](/sql/mdx/properties-mdx) function.</span></span>  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a><span data-ttu-id="b5496-113">使用 PROPERTIES 关键字检索用户定义的成员属性</span><span class="sxs-lookup"><span data-stu-id="b5496-113">Using the PROPERTIES Keyword to Retrieve User-Defined Member Properties</span></span>  
 <span data-ttu-id="b5496-114">检索用户定义的成员属性的语法与用来检索内部级别成员属性的语法相似，如下列语法所示：</span><span class="sxs-lookup"><span data-stu-id="b5496-114">The syntax that retrieves user-defined member properties is similar to that used to retrieve intrinsic level member properties, as shown in the following syntax:</span></span>  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 <span data-ttu-id="b5496-115">`PROPERTIES` 关键字出现在轴规范的集表达式之后。</span><span class="sxs-lookup"><span data-stu-id="b5496-115">The `PROPERTIES` keyword appears after the set expression of the axis specification.</span></span> <span data-ttu-id="b5496-116">例如，以下 MDX 查询中的 `PROPERTIES` 关键字将检索用户定义成员属性 `List Price` 和 `Dealer Price`，并显示在标识一月份售出产品的集表达式之后。</span><span class="sxs-lookup"><span data-stu-id="b5496-116">For example, the following MDX query the `PROPERTIES` keyword retrieves the `List Price` and `Dealer Price` user-defined member properties and appears after the set expression that identifies the products sold in January:</span></span>  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a><span data-ttu-id="b5496-117">使用 Properties 函数检索用户定义的成员属性</span><span class="sxs-lookup"><span data-stu-id="b5496-117">Using the Properties Function to Retrieve User-Defined Member Properties</span></span>  
 <span data-ttu-id="b5496-118">也可以使用 `Properties` 函数访问自定义成员属性。</span><span class="sxs-lookup"><span data-stu-id="b5496-118">Alternatively, you can access custom member properties with the `Properties` function.</span></span> <span data-ttu-id="b5496-119">例如，以下 MDX 查询使用 `WITH` 关键字创建包含 `List Price` 成员属性的计算成员：</span><span class="sxs-lookup"><span data-stu-id="b5496-119">For example, the following MDX query uses the `WITH` keyword to create a calculated member consisting of the `List Price` member property:</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="b5496-120">有关生成计算成员的详细信息，请参阅[在 MDX 中生成计算成员 (MDX)](mdx-calculated-members-building-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="b5496-120">For more information about building calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5496-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5496-121">See Also</span></span>  
 <span data-ttu-id="b5496-122">[&#40;MDX&#41;使用成员属性](mdx-member-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b5496-122">[Using Member Properties &#40;MDX&#41;](mdx-member-properties.md) </span></span>  
 [<span data-ttu-id="b5496-123">属性 (MDX)</span><span class="sxs-lookup"><span data-stu-id="b5496-123">Properties &#40;MDX&#41;</span></span>](/sql/mdx/properties-mdx)  
  
  
