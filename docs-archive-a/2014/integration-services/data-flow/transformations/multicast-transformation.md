---
title: 多播转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b5c0a38c966c89f426a213f302b45c390b77cfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694551"
---
# <a name="multicast-transformation"></a><span data-ttu-id="8ac98-102">多播转换</span><span class="sxs-lookup"><span data-stu-id="8ac98-102">Multicast Transformation</span></span>
  <span data-ttu-id="8ac98-103">多播转换将其输入分发到一个或多个输出。</span><span class="sxs-lookup"><span data-stu-id="8ac98-103">The Multicast transformation distributes its input to one or more outputs.</span></span> <span data-ttu-id="8ac98-104">此转换与有条件拆分转换类似。</span><span class="sxs-lookup"><span data-stu-id="8ac98-104">This transformation is similar to the Conditional Split transformation.</span></span> <span data-ttu-id="8ac98-105">这两种转换都将一个输入定向到多个输出。</span><span class="sxs-lookup"><span data-stu-id="8ac98-105">Both transformations direct an input to multiple outputs.</span></span> <span data-ttu-id="8ac98-106">这两者之间的区别在于多播转换将每行定向到每个输出，而有条件拆分则将一行定向到单个输出。</span><span class="sxs-lookup"><span data-stu-id="8ac98-106">The difference between the two is that the Multicast transformation directs every row to every output, and the Conditional Split directs a row to a single output.</span></span> <span data-ttu-id="8ac98-107">有关详细信息，请参阅 [Conditional Split Transformation](conditional-split-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac98-107">For more information, see [Conditional Split Transformation](conditional-split-transformation.md).</span></span>  
  
 <span data-ttu-id="8ac98-108">您可以通过添加输出来配置多播转换。</span><span class="sxs-lookup"><span data-stu-id="8ac98-108">You configure the Multicast transformation by adding outputs.</span></span>  
  
 <span data-ttu-id="8ac98-109">使用多播转换，包可创建数据的逻辑副本。</span><span class="sxs-lookup"><span data-stu-id="8ac98-109">Using the Multicast transformation, a package can create logical copies of data.</span></span> <span data-ttu-id="8ac98-110">当包需要对相同的数据应用多个转换集时，此功能十分有用。</span><span class="sxs-lookup"><span data-stu-id="8ac98-110">This capability is useful when the package needs to apply multiple sets of transformations to the same data.</span></span> <span data-ttu-id="8ac98-111">例如，对数据的一个副本进行聚合并且仅将摘要信息加载到其目标，而对数据的另一个副本使用查找值和派生列进行扩展，然后再将其加载到目标。</span><span class="sxs-lookup"><span data-stu-id="8ac98-111">For example, one copy of the data is aggregated and only the summary information is loaded into its destination, while another copy of the data is extended with lookup values and derived columns before it is loaded into its destination.</span></span>  
  
 <span data-ttu-id="8ac98-112">此转换具有一个输入和多个输出。</span><span class="sxs-lookup"><span data-stu-id="8ac98-112">This transformation has one input and multiple outputs.</span></span> <span data-ttu-id="8ac98-113">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="8ac98-113">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-multicast-transformation"></a><span data-ttu-id="8ac98-114">多播转换的配置</span><span class="sxs-lookup"><span data-stu-id="8ac98-114">Configuration of the Multicast Transformation</span></span>  
 <span data-ttu-id="8ac98-115">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="8ac98-115">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="8ac98-116">有关可在 **“多播转换编辑器”** 对话框中设置的属性的详细信息，请参阅 [Multicast Transformation Editor](../../multicast-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac98-116">For information about the properties that you can set in the **Multicast Transformation Editor** dialog box, see [Multicast Transformation Editor](../../multicast-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="8ac98-117">有关可以编程方式设置的属性的信息，请参阅 [Common Properties](../../common-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac98-117">For information about the properties that you can set programmatically, see [Common Properties](../../common-properties.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8ac98-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8ac98-118">Related Tasks</span></span>  
 <span data-ttu-id="8ac98-119">有关如何设置数据流组件属性的信息，请参阅 [设置数据流组件属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac98-119">For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac98-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ac98-120">See Also</span></span>  
 <span data-ttu-id="8ac98-121">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="8ac98-121">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="8ac98-122">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="8ac98-122">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
