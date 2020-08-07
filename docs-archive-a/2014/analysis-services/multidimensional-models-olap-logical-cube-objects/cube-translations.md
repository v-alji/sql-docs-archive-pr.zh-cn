---
title: 多维数据集翻译 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- cubes [Analysis Services], translations
- OLAP objects [Analysis Services], translations
- translations [Analysis Services], cubes
ms.assetid: 4e4fd6a4-d324-4508-b75a-2a57de9ab8ff
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8cd4347baae8504ef5dd0f13a3adcca634c49ea2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587638"
---
# <a name="cube-translations"></a><span data-ttu-id="18ea0-102">多维数据集翻译</span><span class="sxs-lookup"><span data-stu-id="18ea0-102">Cube Translations</span></span>
  <span data-ttu-id="18ea0-103">翻译是将显示的标签和标题从一种语言更改为另一种语言的简单机制。</span><span class="sxs-lookup"><span data-stu-id="18ea0-103">A translation is a simple mechanism to change the displayed labels and captions from one language to another.</span></span> <span data-ttu-id="18ea0-104">每个翻译都被定义为一对值：带已翻译文本的字符串和带语言 ID 的数字。</span><span class="sxs-lookup"><span data-stu-id="18ea0-104">Each translation is defined as a pair of values: a string with the translated text, and a number with the language ID.</span></span> <span data-ttu-id="18ea0-105">翻译可用于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="18ea0-105">Translations are available for all objects in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="18ea0-106">还可以翻译维度的属性值。</span><span class="sxs-lookup"><span data-stu-id="18ea0-106">Dimensions can also have the attribute values translated.</span></span> <span data-ttu-id="18ea0-107">客户端应用程序不但要负责查找用户定义的语言设置，还要将所有标题和标签都切换为以该语言显示。</span><span class="sxs-lookup"><span data-stu-id="18ea0-107">The client application is responsible for finding the language setting that the user has defined, and switch to display all captions and labels to that language.</span></span> <span data-ttu-id="18ea0-108">根据您的需要，一个对象可有多种翻译。</span><span class="sxs-lookup"><span data-stu-id="18ea0-108">An object can have as many translations as you want.</span></span>  
  
 <span data-ttu-id="18ea0-109">一个简单的 <xref:Microsoft.AnalysisServices.Translation> 对象由语言 ID 号和翻译后的标题组成。</span><span class="sxs-lookup"><span data-stu-id="18ea0-109">A simple <xref:Microsoft.AnalysisServices.Translation> object is composed of: language ID number, and translated caption.</span></span> <span data-ttu-id="18ea0-110">语言 ID 号是带语言 ID 的 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="18ea0-110">The language ID number is an `Integer` with the language ID.</span></span> <span data-ttu-id="18ea0-111">翻译后的标题是已翻译的文本。</span><span class="sxs-lookup"><span data-stu-id="18ea0-111">The translated caption is the translated text.</span></span>  
  
 <span data-ttu-id="18ea0-112">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，多维数据集转换是多维数据集对象（如标题或显示文件夹）的名称的特定于语言的表示形式。</span><span class="sxs-lookup"><span data-stu-id="18ea0-112">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a cube translation is a language-specific representation of the name of a cube object, such as a caption or a display folder.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="18ea0-113">还支持维度和成员名称的翻译。</span><span class="sxs-lookup"><span data-stu-id="18ea0-113">also supports translations of dimension and member names.</span></span>  
  
 <span data-ttu-id="18ea0-114">翻译为可支持多种语言的客户端应用程序提供了服务器支持。</span><span class="sxs-lookup"><span data-stu-id="18ea0-114">Translations provide server support for client applications that can support multiple languages.</span></span> <span data-ttu-id="18ea0-115">通常，来自不同国家/地区的用户会查看多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="18ea0-115">Frequently, users from different countries view cube data.</span></span> <span data-ttu-id="18ea0-116">将多维数据集的各种元素翻译为其他语言很有用，因为这样这些用户才能查看并了解多维数据集的元数据。</span><span class="sxs-lookup"><span data-stu-id="18ea0-116">It is useful to be able to translate various elements of a cube into a different language so that these users can view and understand the cube's metadata.</span></span> <span data-ttu-id="18ea0-117">例如，法国的业务用户可以通过采用了法语区域设置的工作站来访问多维数据集，查看以法语显示的对象属性值。</span><span class="sxs-lookup"><span data-stu-id="18ea0-117">For example, a business user in France can access a cube from a workstation with a French locale setting, and view the object property values in French.</span></span> <span data-ttu-id="18ea0-118">同样，德国的业务用户可以通过采用了德语区域设置的工作站来访问相同的多维数据集，查看以德语显示的对象属性值。</span><span class="sxs-lookup"><span data-stu-id="18ea0-118">Similarly, a business user in Germany can access the same cube from a workstation with a German locale setting and view the object property values in German.</span></span>  
  
 <span data-ttu-id="18ea0-119">客户端计算机的排序规则和语言信息以区域设置标识符 (LCID) 的形式进行存储。</span><span class="sxs-lookup"><span data-stu-id="18ea0-119">The collation and language information for the client computer is stored in the form of a locale identifier (LCID).</span></span> <span data-ttu-id="18ea0-120">客户端通过连接将 LCID 传递给 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="18ea0-120">Upon connection, the client passes the LCID to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="18ea0-121">然后，该实例使用 LCID 来确定在向每个业务用户提供 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象的元数据时所用的翻译集。</span><span class="sxs-lookup"><span data-stu-id="18ea0-121">The instance uses the LCID to determine which set of translations to use when providing metadata for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects to each business user.</span></span> <span data-ttu-id="18ea0-122">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象未包含指定的翻译，则使用默认语言将内容返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="18ea0-122">If an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object does not contain the specified translation, the default language is used to return the content back to the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ea0-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18ea0-123">See Also</span></span>  
 <span data-ttu-id="18ea0-124">[维度翻译](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span><span class="sxs-lookup"><span data-stu-id="18ea0-124">[Dimension Translations](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span></span>  
 <span data-ttu-id="18ea0-125">[翻译 &#40;Analysis Services&#41;](../translations-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="18ea0-125">[Translations &#40;Analysis Services&#41;](../translations-analysis-services.md) </span></span>  
 [<span data-ttu-id="18ea0-126">全球化提示和最佳实践 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="18ea0-126">Globalization Tips and Best Practices &#40;Analysis Services&#41;</span></span>](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
