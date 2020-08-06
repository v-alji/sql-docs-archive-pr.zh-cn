---
title: 返回的 XML 成形过程中的 AUTO 模式试探方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a64cda8989e1e45d4ad869f8883e1c9d65f4b7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577442"
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a><span data-ttu-id="42a1f-102">返回的 XML 成形过程中的 AUTO 模式试探方法</span><span class="sxs-lookup"><span data-stu-id="42a1f-102">AUTO Mode Heuristics in Shaping Returned XML</span></span>
  <span data-ttu-id="42a1f-103">AUTO 模式根据查询决定返回的 XML 的形式。</span><span class="sxs-lookup"><span data-stu-id="42a1f-103">AUTO mode determines the shape of returned XML based on the query.</span></span> <span data-ttu-id="42a1f-104">在决定嵌套元素的方式时，AUTO 模式试探方法会比较相邻行中的列值。</span><span class="sxs-lookup"><span data-stu-id="42a1f-104">In determining how elements are to be nested, AUTO mode heuristics compare column values in adjacent rows.</span></span> <span data-ttu-id="42a1f-105">**ntext**、 **text**、 **image**和 **xml**类型以外的所有类型的列都会进行比较。</span><span class="sxs-lookup"><span data-stu-id="42a1f-105">Columns of all types, except **ntext**, **text**, **image**, and **xml**, are compared.</span></span> <span data-ttu-id="42a1f-106">**(n)varchar(max)** 和 **varbinary(max)** 类型的列会进行比较。</span><span class="sxs-lookup"><span data-stu-id="42a1f-106">Columns of type **(n)varchar(max)** and **varbinary(max)** are compared.</span></span>  
  
 <span data-ttu-id="42a1f-107">下面的示例说明了确定生成的 XML 的形式的 AUTO 模式试探方法：</span><span class="sxs-lookup"><span data-stu-id="42a1f-107">The following example illustrates the AUTO mode heuristics that determine the shape of the resulting XML:</span></span>  
  
```  
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
FOR XML AUTO  
ORDER BY T1.Id  
```  
  
 <span data-ttu-id="42a1f-108">如果未指定表 T1 的键，若要确定新 <`T1`> 元素的开始位置，需要比较 T1 中除 **ntext** **text** **image** 和 **xml** 类型以外的所有列的值。</span><span class="sxs-lookup"><span data-stu-id="42a1f-108">To determine where a new <`T1`> element starts, all column values of T1, except **ntext**, **text**, **image** and **xml**, are compared if the key on the table T1 is not specified.</span></span> <span data-ttu-id="42a1f-109">接下来，假定 **Name** 列的数据类型为 **nvarchar(40)** ，SELECT 语句将返回如下行集：</span><span class="sxs-lookup"><span data-stu-id="42a1f-109">Next, assume that the **Name** column is **nvarchar(40)** and the SELECT statement returns this rowset:</span></span>  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 <span data-ttu-id="42a1f-110">AUTO 模式试探方法将比较表 T1 的所有值（Id 列和 Name 列）。</span><span class="sxs-lookup"><span data-stu-id="42a1f-110">The AUTO mode heuristics compare all the values of table T1, the Id and Name columns.</span></span> <span data-ttu-id="42a1f-111">因为前两行的 Id 列和 Name 列具有相同的值，所以向结果中添加了一个具有两个 \<T2> 子元素的 \<T1> 元素。</span><span class="sxs-lookup"><span data-stu-id="42a1f-111">Because the first two rows have the same values for the Id and Name columns, one \<T1> element having two \<T2> child elements is added in the result.</span></span>  
  
 <span data-ttu-id="42a1f-112">下面是返回的 XML：</span><span class="sxs-lookup"><span data-stu-id="42a1f-112">Following is the XML that is returned:</span></span>  
  
```  
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 <span data-ttu-id="42a1f-113">现在，假定 Name 列是 **text** 类型。</span><span class="sxs-lookup"><span data-stu-id="42a1f-113">Now assume that the Name column is of **text** type.</span></span> <span data-ttu-id="42a1f-114">AUTO 模式试探方法不比较此类型的值，</span><span class="sxs-lookup"><span data-stu-id="42a1f-114">The AUTO mode heuristics do not compare the values for this type.</span></span> <span data-ttu-id="42a1f-115">而是认为这些值不相同。</span><span class="sxs-lookup"><span data-stu-id="42a1f-115">Instead, it assumes that the values are not the same.</span></span> <span data-ttu-id="42a1f-116">这将产生如下所示的 XML 生成结果：</span><span class="sxs-lookup"><span data-stu-id="42a1f-116">This results in XML generation as shown in the following:</span></span>  
  
```  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42a1f-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42a1f-117">See Also</span></span>  
 [<span data-ttu-id="42a1f-118">将 AUTO 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="42a1f-118">Use AUTO Mode with FOR XML</span></span>](use-auto-mode-with-for-xml.md)  
  
  
