---
title: 插件算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
author: minewiskan
ms.author: owend
ms.openlocfilehash: ebc5e007dcc6de7fb25d59547e21f1e892100570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690886"
---
# <a name="plugin-algorithms"></a><span data-ttu-id="24296-102">插件算法</span><span class="sxs-lookup"><span data-stu-id="24296-102">Plugin Algorithms</span></span>
  <span data-ttu-id="24296-103">除了提供的算法以外 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，还可以使用其他许多算法进行数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="24296-103">In addition to the algorithms that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides, there are many other algorithms that you can use for data mining.</span></span> <span data-ttu-id="24296-104">相应地， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 为由第三方创建的“插件”算法提供了某种机制。</span><span class="sxs-lookup"><span data-stu-id="24296-104">Accordingly, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides a mechanism for "plugging in" algorithms that are created by third parties.</span></span> <span data-ttu-id="24296-105">只要这些算法遵守特定的标准，就可以像使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 算法一样在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 中使用它们。</span><span class="sxs-lookup"><span data-stu-id="24296-105">As long as the algorithms follow certain standards, you can use them within [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] just as you use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms.</span></span> <span data-ttu-id="24296-106">插件算法具有提供的算法的所有功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="24296-106">Plugin algorithms have all the capabilities of algorithms that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides.</span></span>  
  
 <span data-ttu-id="24296-107">有关 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用于与插件算法进行通信的接口的完整说明，请参阅 [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) 网站上发布的创建自定义算法和自定义模型查看器的示例。</span><span class="sxs-lookup"><span data-stu-id="24296-107">For a full description of the interfaces that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses to communicate with plugin algorithms, see the samples for creating a custom algorithm and custom model viewer that are published on [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) Web site.</span></span>  
  
## <a name="algorithm-requirements"></a><span data-ttu-id="24296-108">算法要求</span><span class="sxs-lookup"><span data-stu-id="24296-108">Algorithm Requirements</span></span>  
 <span data-ttu-id="24296-109">若要将某个算法插入 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，必须实现下列 COM 接口：</span><span class="sxs-lookup"><span data-stu-id="24296-109">To plug an algorithm into [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must implement the following COM interfaces:</span></span>  
  
 `IDMAlgorithm`  
 <span data-ttu-id="24296-110">实现一个生成模型的算法，并且实现该结果模型的预测操作。</span><span class="sxs-lookup"><span data-stu-id="24296-110">Implements an algorithm that produces models, and implements the prediction operations of the resulting models.</span></span>  
  
 `IDMAlgorithmNavigation`  
 <span data-ttu-id="24296-111">启用浏览器来访问模型的内容。</span><span class="sxs-lookup"><span data-stu-id="24296-111">Enables browsers to access the content of the models.</span></span>  
  
 `IDMPersist`  
 <span data-ttu-id="24296-112">启用算法定型，将由 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]保存和加载的模型。</span><span class="sxs-lookup"><span data-stu-id="24296-112">Enables the models that the algorithm trains to be saved and loaded by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 `IDMAlgorithmMetadata`  
 <span data-ttu-id="24296-113">介绍算法的功能和输入参数。</span><span class="sxs-lookup"><span data-stu-id="24296-113">Describes the capabilities and input parameters of the algorithm.</span></span>  
  
 `IDMAlgorithmFactory`  
 <span data-ttu-id="24296-114">创建实现算法接口的对象的实例，并向 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供对算法元数据接口的访问。</span><span class="sxs-lookup"><span data-stu-id="24296-114">Creates instances of the objects that implement the algorithm interface, and provides [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] with access to the algorithm-metadata interface.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="24296-115">使用这些 COM 接口与插件算法进行通信。</span><span class="sxs-lookup"><span data-stu-id="24296-115">uses these COM interfaces to communicate with plugin algorithms.</span></span> <span data-ttu-id="24296-116">虽然使用的插件算法必须支持 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB for Data Mining 规范，但是这些算法不必支持该规范中的所有数据挖掘选项。</span><span class="sxs-lookup"><span data-stu-id="24296-116">Although plugin algorithms that you use must support the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB for Data Mining specification, they do not have to support all the data mining options in the specification.</span></span> <span data-ttu-id="24296-117">可以使用 [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) 架构行集来确定一个算法的功能。</span><span class="sxs-lookup"><span data-stu-id="24296-117">You can use the [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) schema rowset to determine the capabilities of an algorithm.</span></span> <span data-ttu-id="24296-118">此架构行集列出了每个插件算法提供程序的数据挖掘支持选项。</span><span class="sxs-lookup"><span data-stu-id="24296-118">This schema rowset lists the data mining support options for each plugin algorithm provider.</span></span>  
  
 <span data-ttu-id="24296-119">将新算法与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]一起使用之前必须对新算法进行注册。</span><span class="sxs-lookup"><span data-stu-id="24296-119">You must register new algorithms before you use them with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="24296-120">若要注册一个算法，请将以下信息包含在要将算法包含在其中的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的 .ini 文件中：</span><span class="sxs-lookup"><span data-stu-id="24296-120">To register an algorithm, include the following information in the .ini file of the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on which you want to include the algorithms:</span></span>  
  
-   <span data-ttu-id="24296-121">算法名称</span><span class="sxs-lookup"><span data-stu-id="24296-121">The algorithm name</span></span>  
  
-   <span data-ttu-id="24296-122">ProgID（可选并且只能为插件算法包括此信息）</span><span class="sxs-lookup"><span data-stu-id="24296-122">ProgID (this is optional and will only be included for plugin algorithms)</span></span>  
  
-   <span data-ttu-id="24296-123">指示算法是否启用的标志</span><span class="sxs-lookup"><span data-stu-id="24296-123">A flag that indicates whether the algorithm is enabled or not</span></span>  
  
 <span data-ttu-id="24296-124">下面的代码示例阐明了如何注册新算法：</span><span class="sxs-lookup"><span data-stu-id="24296-124">The following code sample illustrates how to register a new algorithm:</span></span>  
  
 `<ConfigurationSettings>`  
  
 `...`  
  
 `<DataMining>`  
  
 `...`  
  
 `<Algorithms>`  
  
 `...`  
  
 `<Sample_Plugin_Algorithm>`  
  
 `<Enabled>1</Enabled>`  
  
 `<ProgID>Microsoft.DataMining.SamplePlugInAlgorithm.Factory</ProgID>`  
  
 `</Sample_PlugIn_Algorithm>`  
  
 `...`  
  
 `</Algorithms>`  
  
 `...`  
  
 `</DataMining>`  
  
 `...`  
  
 `</ConfigurationSettings>`  
  
## <a name="see-also"></a><span data-ttu-id="24296-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24296-125">See Also</span></span>  
 <span data-ttu-id="24296-126">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="24296-126">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="24296-127">DMSCHEMA_MINING_SERVICES 行集</span><span class="sxs-lookup"><span data-stu-id="24296-127">DMSCHEMA_MINING_SERVICES Rowset</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)  
  
  
