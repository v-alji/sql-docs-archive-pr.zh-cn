---
title: 通过个性化扩展 OLAP |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93669980e989b1cb11673f45c111de3609bbe920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693535"
---
# <a name="extending-olap-through-personalizations"></a><span data-ttu-id="40a6c-102">通过个性化设置扩展 OLAP</span><span class="sxs-lookup"><span data-stu-id="40a6c-102">Extending OLAP through personalizations</span></span>
  <span data-ttu-id="40a6c-103">Microsoft  [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] 提供了诸多可用于多维表达式 (MDX) 和数据挖掘扩展插件 (DMX) 语言的内部函数。</span><span class="sxs-lookup"><span data-stu-id="40a6c-103">Microsoft  [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] supplies many intrinsic functions for use with the Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) languages.</span></span> <span data-ttu-id="40a6c-104">这些函数经过专门设计，可用于完成从标准统计计算到遍历层次结构中的成员的所有任务。</span><span class="sxs-lookup"><span data-stu-id="40a6c-104">These functions are designed to accomplish everything from standard statistical calculations to traversing members in a hierarchy.</span></span> <span data-ttu-id="40a6c-105">但是，任何复杂且可靠的产品都需要不断地扩展其功能，本产品也不例外。</span><span class="sxs-lookup"><span data-stu-id="40a6c-105">However, as with any other complex and robust product, there is always the need to extend the functionality of such a product further.</span></span>  
  
 <span data-ttu-id="40a6c-106">因此，Analysis Services 为您提供了向服务实例添加程序集和个性化扩展插件的功能，其目的是在标准功能不能胜任时满足您的业务需要。</span><span class="sxs-lookup"><span data-stu-id="40a6c-106">Therefore, Analysis Services provides you with the ability to add assemblies and personalized extensions to an instance of the service, in order to complete your business needs whenever the standard functionality is not enough.</span></span>  
  
## <a name="assemblies"></a><span data-ttu-id="40a6c-107">程序集</span><span class="sxs-lookup"><span data-stu-id="40a6c-107">Assemblies</span></span>  
 <span data-ttu-id="40a6c-108">使用程序集可以扩展 MDX 和 DMX 的业务功能。</span><span class="sxs-lookup"><span data-stu-id="40a6c-108">Assemblies enable you to extend the business functionality of MDX and DMX.</span></span> <span data-ttu-id="40a6c-109">您在诸如动态链接库 (DLL) 这样的库中构建所需的功能，然后将库作为程序集添加到 Analysis Services 的实例或 Analysis Services 数据库。</span><span class="sxs-lookup"><span data-stu-id="40a6c-109">You build the functionality that you want into a library, such as a dynamic link library (DLL), then add the library as an assembly to an instance of Analysis Services or to an Analysis Services database.</span></span> <span data-ttu-id="40a6c-110">然后，库中的公共方法对 MDX 和 DMX 表达式、过程、计算、操作和客户端应用程序显示为用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="40a6c-110">The public methods in the library are then exposed as user-defined functions to MDX and DMX expressions, procedures, calculations, actions, and client applications.</span></span>  
  
## <a name="personalized-extensions"></a><span data-ttu-id="40a6c-111">个性化扩展</span><span class="sxs-lookup"><span data-stu-id="40a6c-111">Personalized Extensions</span></span>  
 <span data-ttu-id="40a6c-112">SQL Server Analysis Services 个性化扩展插件是实现插件体系结构想法的基础。</span><span class="sxs-lookup"><span data-stu-id="40a6c-112">SQL Server Analysis Services personalization extensions are the foundation of the idea of implementing a plug-in architecture.</span></span> <span data-ttu-id="40a6c-113">Analysis Services 的个性化设置扩展是对现有托管程序集体系结构的简单、精致的修改，并在整个 Analysis Services [AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120))对象模型、多维表达式 (MDX) 语法和架构行集）中公开。</span><span class="sxs-lookup"><span data-stu-id="40a6c-113">Analysis Services personalization extensions are a simple and elegant modification to the existing managed assembly architecture and are exposed throughout the Analysis Services [Microsoft.AnalysisServices.AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120)) object model, Multidimensional Expressions (MDX) syntax, and schema rowsets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a6c-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40a6c-114">See Also</span></span>  
 <span data-ttu-id="40a6c-115">[多维模型程序集管理](../multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="40a6c-115">[Multidimensional Model Assemblies Management](../multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="40a6c-116">Analysis Services 个性化设置扩展</span><span class="sxs-lookup"><span data-stu-id="40a6c-116">Analysis Services Personalization Extensions</span></span>](analysis-services-personalization-extensions.md)  
  
  
