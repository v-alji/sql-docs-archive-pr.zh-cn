---
title: 使用转换对数据进行转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], transformations
- transformations [Integration Services], about transformations
- transforming data [Integration Services]
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952d8ea4eeea2dd8010a17a2b3deba41447b6231
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590930"
---
# <a name="transform-data-with-transformations"></a><span data-ttu-id="c05cc-102">使用转换对数据进行转换</span><span class="sxs-lookup"><span data-stu-id="c05cc-102">Transform Data with Transformations</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="c05cc-103">包括三种类型的数据流组件：源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="c05cc-103">includes three types of data flow components: sources, transformations, and destinations.</span></span>  
  
 <span data-ttu-id="c05cc-104">下列关系图显示具有一个源、两个转换和一个目标的简单数据流。</span><span class="sxs-lookup"><span data-stu-id="c05cc-104">The following diagram shows a simple data flow that has a source, two transformations, and a destination.</span></span>  
  
 <span data-ttu-id="c05cc-105">![数据流](../../media/mw-dts-08.gif "数据流")</span><span class="sxs-lookup"><span data-stu-id="c05cc-105">![Data flow](../../media/mw-dts-08.gif "Data flow")</span></span>  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="c05cc-106">转换提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="c05cc-106">transformations provide the following functionality:</span></span>  
  
-   <span data-ttu-id="c05cc-107">拆分、复制与合并行集并执行查找操作。</span><span class="sxs-lookup"><span data-stu-id="c05cc-107">Splitting, copying, and merging rowsets and performing lookup operations.</span></span>  
  
-   <span data-ttu-id="c05cc-108">应用转换（如将小写更改为大写），从而更新列值和创建新列。</span><span class="sxs-lookup"><span data-stu-id="c05cc-108">Updating column values and creating new columns by applying transformations such as changing lowercase to uppercase.</span></span>  
  
-   <span data-ttu-id="c05cc-109">执行商业智能操作，如清除数据、挖掘文本或运行数据挖掘预测查询。</span><span class="sxs-lookup"><span data-stu-id="c05cc-109">Performing business intelligence operations such as cleaning data, mining text, or running data mining prediction queries.</span></span>  
  
-   <span data-ttu-id="c05cc-110">创建由聚合值或已排序值、示例数据或者透视数据和逆透视数据构成的新行集。</span><span class="sxs-lookup"><span data-stu-id="c05cc-110">Creating new rowsets that consist of aggregate or sorted values, sample data, or pivoted and unpivoted data.</span></span>  
  
-   <span data-ttu-id="c05cc-111">执行导出与导入数据、提供审核信息以及使用渐变维度等任务。</span><span class="sxs-lookup"><span data-stu-id="c05cc-111">Performing tasks such as exporting and importing data, providing audit information, and working with slowly changing dimensions.</span></span>  
  
 <span data-ttu-id="c05cc-112">有关详细信息，请参阅 [Integration Services Transformations](integration-services-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="c05cc-112">For more information, see [Integration Services Transformations](integration-services-transformations.md).</span></span>  
  
 <span data-ttu-id="c05cc-113">还可以编写自定义转换。</span><span class="sxs-lookup"><span data-stu-id="c05cc-113">You can also write custom transformations.</span></span> <span data-ttu-id="c05cc-114">有关详细信息，请参阅 [开发自定义数据流组件](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) 和 [开发特定类型的数据流组件](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)。</span><span class="sxs-lookup"><span data-stu-id="c05cc-114">For more information, see [Developing a Custom Data Flow Component](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) and [Developing Specific Types of Data Flow Components](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md).</span></span>  
  
 <span data-ttu-id="c05cc-115">将转换添加到数据流设计器之后但配置转换之前，请将数据流中另一转换或源的输出连接到此转换的输入，从而将此转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="c05cc-115">After you add the transformation to the data flow designer, but before you configure the transformation, you connect the transformation to the data flow by connecting the output of another transformation or source in the data flow to the input of this transformation.</span></span> <span data-ttu-id="c05cc-116">两个数据流组件之间的连接器称为路径。</span><span class="sxs-lookup"><span data-stu-id="c05cc-116">The connector between two data flow components is called a path.</span></span> <span data-ttu-id="c05cc-117">有关连接组件和使用路径的详细信息，请参阅 [使用路径连接组件](../../connect-components-with-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="c05cc-117">For more information about connecting components and working with paths, see [Connect Components with Paths](../../connect-components-with-paths.md).</span></span>  
  
### <a name="to-add-a-transformation-to-a-data-flow"></a><span data-ttu-id="c05cc-118">将转换添加到数据流</span><span class="sxs-lookup"><span data-stu-id="c05cc-118">To add a transformation to a data flow</span></span>  
  
-   [<span data-ttu-id="c05cc-119">在数据流中添加或删除组件</span><span class="sxs-lookup"><span data-stu-id="c05cc-119">Add or Delete a Component in a Data Flow</span></span>](../add-or-delete-a-component-in-a-data-flow.md)  
  
### <a name="to-connect-a-transformation-to-a-data-flow"></a><span data-ttu-id="c05cc-120">将转换连接到数据流</span><span class="sxs-lookup"><span data-stu-id="c05cc-120">To connect a transformation to a data flow</span></span>  
  
-   [<span data-ttu-id="c05cc-121">连接数据流中的组件</span><span class="sxs-lookup"><span data-stu-id="c05cc-121">Connect Components in a Data Flow</span></span>](../connect-components-in-a-data-flow.md)  
  
### <a name="to-set-the-properties-of-a-transformation"></a><span data-ttu-id="c05cc-122">设置转换的属性</span><span class="sxs-lookup"><span data-stu-id="c05cc-122">To set the properties of a transformation</span></span>  
  
-   [<span data-ttu-id="c05cc-123">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="c05cc-123">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="c05cc-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c05cc-124">See Also</span></span>  
 <span data-ttu-id="c05cc-125">[数据流任务](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="c05cc-125">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 <span data-ttu-id="c05cc-126">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="c05cc-126">[Data Flow](../data-flow.md) </span></span>  
 <span data-ttu-id="c05cc-127">[使用路径连接组件](../../connect-components-with-paths.md) </span><span class="sxs-lookup"><span data-stu-id="c05cc-127">[Connect Components with Paths](../../connect-components-with-paths.md) </span></span>  
 <span data-ttu-id="c05cc-128">[数据中的错误处理](../error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="c05cc-128">[Error Handling in Data](../error-handling-in-data.md) </span></span>  
 [<span data-ttu-id="c05cc-129">数据流</span><span class="sxs-lookup"><span data-stu-id="c05cc-129">Data Flow</span></span>](../data-flow.md)  
  
  
