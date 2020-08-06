---
title: 维度翻译 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], translations
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- LCIDs
- translations [Analysis Services], dimensions
ms.assetid: 38fc1e05-2ac9-4816-b52b-dfd19c3a43a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f31773ad871ef7e3fc8f99d57e7a9099335b899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692602"
---
# <a name="dimension-translations"></a><span data-ttu-id="856c1-102">维度翻译</span><span class="sxs-lookup"><span data-stu-id="856c1-102">Dimension Translations</span></span>
  <span data-ttu-id="856c1-103">翻译是将显示的标签和标题从一种语言更改为另一种语言的简单机制。</span><span class="sxs-lookup"><span data-stu-id="856c1-103">A translation is a simple mechanism to change the displayed labels and captions from one language to another.</span></span> <span data-ttu-id="856c1-104">每个翻译都被定义为一对值：带已翻译文本的字符串和带语言 ID 的数字。</span><span class="sxs-lookup"><span data-stu-id="856c1-104">Each translation is defined as a pair of values: a string with the translated text, and a number with the language ID.</span></span> <span data-ttu-id="856c1-105">翻译可用于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="856c1-105">Translations are available for all objects in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="856c1-106">还可以翻译维度的属性值。</span><span class="sxs-lookup"><span data-stu-id="856c1-106">Dimensions can also have the attribute values translated.</span></span> <span data-ttu-id="856c1-107">客户端应用程序不但要负责查找用户定义的语言设置，还要将所有标题和标签都切换为以该语言显示。</span><span class="sxs-lookup"><span data-stu-id="856c1-107">The client application is responsible for finding the language setting that the user has defined, and switch to display all captions and labels to that language.</span></span> <span data-ttu-id="856c1-108">根据您的需要，一个对象可有多种翻译。</span><span class="sxs-lookup"><span data-stu-id="856c1-108">An object can have as many translations as you want.</span></span>  
  
 <span data-ttu-id="856c1-109">一个简单的 <xref:Microsoft.AnalysisServices.Translation> 对象由语言 ID 号和翻译后的标题组成。</span><span class="sxs-lookup"><span data-stu-id="856c1-109">A simple <xref:Microsoft.AnalysisServices.Translation> object is composed of: language ID number, and translated caption.</span></span> <span data-ttu-id="856c1-110">语言 ID 号是带语言 ID 的 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="856c1-110">The language ID number is an `Integer` with the language ID.</span></span> <span data-ttu-id="856c1-111">翻译后的标题是已翻译的文本。</span><span class="sxs-lookup"><span data-stu-id="856c1-111">The translated caption is the translated text.</span></span>  
  
 <span data-ttu-id="856c1-112">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，维度翻译是指维度名称、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象或其某个成员（如标题、成员或层次结构级别）的名称的特定于语言的表示形式。</span><span class="sxs-lookup"><span data-stu-id="856c1-112">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a dimension translation is a language-specific representation of the name of a dimension, the name of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object or one of its members, such as a caption, member, or hierarchy level.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="856c1-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]还支持多维数据集对象的翻译。</span><span class="sxs-lookup"><span data-stu-id="856c1-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] also supports translations of cube objects.</span></span>  
  
 <span data-ttu-id="856c1-114">翻译为可支持多种语言的客户端应用程序提供了服务器支持。</span><span class="sxs-lookup"><span data-stu-id="856c1-114">Translations provide server support for client applications that can support multiple languages.</span></span> <span data-ttu-id="856c1-115">通常，来自不同国家/地区的用户都会查看多维数据集及其维度。</span><span class="sxs-lookup"><span data-stu-id="856c1-115">Frequently, users from different countries view a cube and its dimensions.</span></span> <span data-ttu-id="856c1-116">将多维数据集及其维度的各种元素翻译为其他语言很有用，因为这样这些用户才能查看并了解多维数据集。</span><span class="sxs-lookup"><span data-stu-id="856c1-116">It is useful to be able to translate various elements of a cube and its dimensions into a different language so that these users can view and understand the cube.</span></span> <span data-ttu-id="856c1-117">例如，法国的业务用户可以从具有法语区域设置的工作站访问多维数据集，并以法语查看对象属性值。</span><span class="sxs-lookup"><span data-stu-id="856c1-117">For example, a business user in France can access a cube from a workstation with a French locale setting, and see the object property values in French.</span></span> <span data-ttu-id="856c1-118">但是，德国的业务用户如果通过采用了德语区域设置的工作站来访问相同的多维数据集，则会看到以德语显示的同一对象属性值。</span><span class="sxs-lookup"><span data-stu-id="856c1-118">However, a business user in Germany who accesses the same cube from a workstation with a German locale setting sees the same object property values in German.</span></span>  
  
 <span data-ttu-id="856c1-119">客户端计算机的排序规则和语言信息以区域设置标识符 (LCID) 的形式进行存储。</span><span class="sxs-lookup"><span data-stu-id="856c1-119">The collation and language information for the client computer is stored in the form of a locale identifier (LCID).</span></span> <span data-ttu-id="856c1-120">客户端通过连接将 LCID 传递给 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="856c1-120">Upon connection, the client passes the LCID to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="856c1-121">实例使用 LCID 来确定在为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象提供元数据时所用的翻译集。</span><span class="sxs-lookup"><span data-stu-id="856c1-121">The instance uses the LCID to determine which set of translations to use when providing metadata for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="856c1-122">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象未包含指定的翻译，则使用默认语言将内容返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="856c1-122">If an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object does not contain the specified translation, the default language is used to return the content back to the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856c1-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="856c1-123">See Also</span></span>  
 <span data-ttu-id="856c1-124">[多维数据集翻译](../multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span><span class="sxs-lookup"><span data-stu-id="856c1-124">[Cube Translations](../multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span></span>  
 <span data-ttu-id="856c1-125">[翻译 &#40;Analysis Services&#41;](../translations-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="856c1-125">[Translations &#40;Analysis Services&#41;](../translations-analysis-services.md) </span></span>  
 [<span data-ttu-id="856c1-126">全球化提示和最佳实践 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="856c1-126">Globalization Tips and Best Practices &#40;Analysis Services&#41;</span></span>](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
