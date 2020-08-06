---
title: 使用变量和参数 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd01cf78ea5e3284aa51cad7dc848176a5dc9298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691942"
---
# <a name="using-variables-and-parameters-mdx"></a><span data-ttu-id="56dc4-102">使用变量和参数 (MDX)</span><span class="sxs-lookup"><span data-stu-id="56dc4-102">Using Variables and Parameters (MDX)</span></span>
  <span data-ttu-id="56dc4-103">在中 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，可以 (MDX) 语句参数化多维表达式。</span><span class="sxs-lookup"><span data-stu-id="56dc4-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], you can parameterize a Multidimensional Expressions (MDX) statement.</span></span> <span data-ttu-id="56dc4-104">参数化语句允许您创建可在运行时自定义的一般语句。</span><span class="sxs-lookup"><span data-stu-id="56dc4-104">A parameterized statement lets you create generic statements that can be customized at runtime.</span></span>  
  
 <span data-ttu-id="56dc4-105">在创建参数化语句时，通过在参数名称前面添加 at 符号 (@) 来标识参数名称。</span><span class="sxs-lookup"><span data-stu-id="56dc4-105">In creating a parameterized statement, you identify the parameter name by prefixing the name with the at sign (@).</span></span> <span data-ttu-id="56dc4-106">例如， @Year 是一个有效的参数名称</span><span class="sxs-lookup"><span data-stu-id="56dc4-106">For example, @Year would be a valid parameter name</span></span>  
  
 <span data-ttu-id="56dc4-107">MDX 仅支持文字值或标量值的参数。</span><span class="sxs-lookup"><span data-stu-id="56dc4-107">MDX supports only parameters for literal or scalar values.</span></span> <span data-ttu-id="56dc4-108">若要创建引用成员、集或元组的参数，必须使用函数，如 [StrToMember](/sql/mdx/strtomember-mdx) 或 [StrToSet](/sql/mdx/strtoset-mdx)。</span><span class="sxs-lookup"><span data-stu-id="56dc4-108">To create a parameter that references a member, set, or tuple, you would have to use a function such as [StrToMember](/sql/mdx/strtomember-mdx) or [StrToSet](/sql/mdx/strtoset-mdx).</span></span>  
  
 <span data-ttu-id="56dc4-109">在下面的 XML for Analysis (XMLA) 示例中， @CountryName 参数将包含检索其客户数据的国家/地区：</span><span class="sxs-lookup"><span data-stu-id="56dc4-109">In the following XML for Analysis (XMLA) example, the @CountryName parameter will contain the country for which customer data is retrieved:</span></span>  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 <span data-ttu-id="56dc4-110">若要将此功能与 OLE DB 结合使用，请使用 `ICommandWithParameters` 接口。</span><span class="sxs-lookup"><span data-stu-id="56dc4-110">To use this functionality with OLE DB, you would use the `ICommandWithParameters` interface.</span></span> <span data-ttu-id="56dc4-111">若要将此功能与 ADOMD.Net 结合使用，请使用 **AdomdCommand.Parameters** 集合。</span><span class="sxs-lookup"><span data-stu-id="56dc4-111">To use this functionality with ADOMD.Net, you would use the **AdomdCommand.Parameters** collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56dc4-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56dc4-112">See Also</span></span>  
 [<span data-ttu-id="56dc4-113">MDX 脚本编写基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="56dc4-113">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)  
  
  
