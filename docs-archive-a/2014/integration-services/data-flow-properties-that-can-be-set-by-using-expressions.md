---
title: 可以使用表达式设置的数据流属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, property expressions
- Integration Services packages, property expressions
- packages [Integration Services], properties
- SSIS packages, property expressions
- property expressions [Integration Services]
ms.assetid: cd0e171a-08be-45d6-81dc-ed94f37698b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1763a531b1d91a60d2bb3775ae9fbe9942c6b7e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688083"
---
# <a name="data-flow-properties-that-can-be-set-by-using-expressions"></a><span data-ttu-id="5a1a3-102">可以使用表达式设置的数据流属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-102">Data Flow Properties that Can Be Set by Using Expressions</span></span>
  <span data-ttu-id="5a1a3-103">可以使用数据流任务容器上的可用属性表达式来指定数据流对象的某些属性的值。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-103">The values of certain properties of data flow objects can be specified by using property expressions available on the Data Flow task container.</span></span>  
  
 <span data-ttu-id="5a1a3-104">有关使用属性表达式的信息，请参阅 [在包中使用属性表达式](expressions/use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-104">For information about using property expressions, see [Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="5a1a3-105">可以使用属性表达式为包的每个已部署的实例自定义配置。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-105">You can use property expressions to customize configurations for each deployed instance of a package.</span></span> <span data-ttu-id="5a1a3-106">也可以使用属性表达式来为包指定运行时约束，方法是将 **/set** 选项与 **dtexec** 命令提示实用工具一起使用。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-106">You can also use property expressions to specify run-time constraints for a package by using the **/set** option with the **dtexec** command prompt utility.</span></span> <span data-ttu-id="5a1a3-107">例如，可以约束排序转换使用的 `MaximumThreads`，或约束模糊分组和模糊查找转换的 `MaxMemoryUsage`。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-107">For example, you can constrain the `MaximumThreads` used by the Sort transformation, or the `MaxMemoryUsage` of the Fuzzy Grouping and Fuzzy Lookup transformations.</span></span> <span data-ttu-id="5a1a3-108">如果无约束，则这些转换可能会在内存中高速缓存大量数据。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-108">If unconstrained, these transformations may cache large amounts of data in memory.</span></span>  
  
 <span data-ttu-id="5a1a3-109">若要为本主题中列出的数据流对象的其中一个属性指定属性表达式，请在设计器的 **“控制流”** 图面上选择该数据流任务，或选择设计器的 **“数据流”** 选项卡但不选择任何单个组件或路径，以此方式显示数据流任务的 **“属性”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-109">To specify a property expression for one of the properties of data flow objects listed in this topic, display the **Properties** window for the Data Flow task by selecting the Data Flow task on the **Control Flow** surface of the designer, or by selecting the **Data Flow** tab of the designer without selecting any individual component or path.</span></span> <span data-ttu-id="5a1a3-110">选择“表达式”\*\*\*\* 属性，然后单击省略号 (...) 以显示“属性表达式编辑器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-110">Select the **Expressions** property and click the ellipsis (...) to display the **Property Expressions Editor** dialog box.</span></span> <span data-ttu-id="5a1a3-111">下拉“属性”\*\*\*\* 列表以选择某个属性，然后在“表达式”\*\*\*\* 文本框中键入一个表达式，或者单击省略号 (...) 以显示“表达式生成器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-111">Drop down the **Property** list to select a property, then type an expression in the **Expression** text box, or click the ellipsis (...) to display the **Expression Builder** dialog box.</span></span>  
  
 <span data-ttu-id="5a1a3-112">**“属性”** 列表仅显示那些已位于设计器的 **“数据流”** 图面上的数据流对象的可用属性。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-112">The **Property** list displays available properties for only those data flow objects that you have already placed on the **Data Flow** surface of the designer.</span></span> <span data-ttu-id="5a1a3-113">因此，不能使用 **“属性”** 列表来查看那些支持属性表达式的数据流对象的所有可能的属性。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-113">Therefore, you cannot use the **Property** list to view all the possible properties of data flow objects that support property expressions.</span></span> <span data-ttu-id="5a1a3-114">例如，如果您将 ADO NET 源放置在设计器图面上，则**属性**列表将包含属性的项 `[ADO NET Source].[SqlCommand]` 。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-114">For example, if you have placed an ADO NET source on the designer surface, the **Property** list contains an entry for the `[ADO NET Source].[SqlCommand]` property.</span></span> <span data-ttu-id="5a1a3-115">该列表还显示了数据流任务自身的许多属性。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-115">The list also displays many properties of the Data Flow task itself.</span></span>  
  
## <a name="properties-of-data-flow-objects-that-support-property-expressions"></a><span data-ttu-id="5a1a3-116">支持属性表达式的数据流对象的属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-116">Properties of Data Flow Objects That Support Property Expressions</span></span>  
 <span data-ttu-id="5a1a3-117">下面的列表中的属性值可以使用属性表达式来指定。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-117">The values of the properties in the following list can be specified by using property expressions.</span></span>  
  
### <a name="data-flow-sources"></a><span data-ttu-id="5a1a3-118">数据流源</span><span class="sxs-lookup"><span data-stu-id="5a1a3-118">Data Flow Sources</span></span>  
  
|<span data-ttu-id="5a1a3-119">数据流对象</span><span class="sxs-lookup"><span data-stu-id="5a1a3-119">Data Flow object</span></span>|<span data-ttu-id="5a1a3-120">属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-120">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="5a1a3-121">ADO NET 源</span><span class="sxs-lookup"><span data-stu-id="5a1a3-121">ADO NET source</span></span>|<span data-ttu-id="5a1a3-122">TableOrViewName 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-122">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="5a1a3-123">SqlCommand 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-123">SqlCommand property</span></span>|  
|<span data-ttu-id="5a1a3-124">XML 源</span><span class="sxs-lookup"><span data-stu-id="5a1a3-124">XML source</span></span>|<span data-ttu-id="5a1a3-125">XMLData 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-125">XMLData property</span></span><br /><br /> <span data-ttu-id="5a1a3-126">XMLSchemaDefinition 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-126">XMLSchemaDefinition property</span></span>|  
  
### <a name="data-flow-transformations"></a><span data-ttu-id="5a1a3-127">数据流转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-127">Data Flow Transformations</span></span>  
 <span data-ttu-id="5a1a3-128">有关这些自定义属性的详细信息，请参阅 [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-128">For more information about these custom properties, see [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
|<span data-ttu-id="5a1a3-129">数据流对象</span><span class="sxs-lookup"><span data-stu-id="5a1a3-129">Data Flow object</span></span>|<span data-ttu-id="5a1a3-130">属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-130">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="5a1a3-131">有条件拆分转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-131">Conditional Split transformation</span></span>|<span data-ttu-id="5a1a3-132">FriendlyExpression 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-132">FriendlyExpression property</span></span>|  
|<span data-ttu-id="5a1a3-133">派生列转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-133">Derived Column transformation</span></span>|<span data-ttu-id="5a1a3-134">FriendlyExpression 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-134">FriendlyExpression property</span></span>|  
|<span data-ttu-id="5a1a3-135">模糊分组转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-135">Fuzzy Grouping transformation</span></span>|<span data-ttu-id="5a1a3-136">MaxMemoryUsage 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-136">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="5a1a3-137">模糊查找转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-137">Fuzzy Lookup transformation</span></span>|<span data-ttu-id="5a1a3-138">MaxMemoryUsage 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-138">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="5a1a3-139">查找转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-139">Lookup transformation</span></span>|<span data-ttu-id="5a1a3-140">SqlCommand 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-140">SqlCommand property</span></span><br /><br /> <span data-ttu-id="5a1a3-141">SqlCommandParam 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-141">SqlCommandParam property</span></span>|  
|<span data-ttu-id="5a1a3-142">OLE DB 命令转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-142">OLE DB Command transformation</span></span>|<span data-ttu-id="5a1a3-143">SqlCommand 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-143">SqlCommand property</span></span>|  
|<span data-ttu-id="5a1a3-144">百分比抽样转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-144">Percentage Sampling transformation</span></span>|<span data-ttu-id="5a1a3-145">SamplingValue 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-145">SamplingValue property</span></span>|  
|<span data-ttu-id="5a1a3-146">透视转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-146">Pivot transformation</span></span>|<span data-ttu-id="5a1a3-147">PivotKeyValue 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-147">PivotKeyValue property</span></span>|  
|<span data-ttu-id="5a1a3-148">行抽样转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-148">Row Sampling transformation</span></span>|<span data-ttu-id="5a1a3-149">SamplingValue 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-149">SamplingValue property</span></span>|  
|<span data-ttu-id="5a1a3-150">排序转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-150">Sort transformation</span></span>|<span data-ttu-id="5a1a3-151">MaximumThreads 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-151">MaximumThreads property</span></span>|  
|<span data-ttu-id="5a1a3-152">逆透视转换</span><span class="sxs-lookup"><span data-stu-id="5a1a3-152">Unpivot transformation</span></span>|<span data-ttu-id="5a1a3-153">PivotKeyValue 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-153">PivotKeyValue property</span></span>|  
  
### <a name="data-flow-destinations"></a><span data-ttu-id="5a1a3-154">数据流目标</span><span class="sxs-lookup"><span data-stu-id="5a1a3-154">Data Flow Destinations</span></span>  
  
|<span data-ttu-id="5a1a3-155">数据流对象</span><span class="sxs-lookup"><span data-stu-id="5a1a3-155">Data Flow object</span></span>|<span data-ttu-id="5a1a3-156">属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-156">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="5a1a3-157">ADO NET 目标</span><span class="sxs-lookup"><span data-stu-id="5a1a3-157">ADO NET Destination</span></span>|<span data-ttu-id="5a1a3-158">TableOrViewName 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-158">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="5a1a3-159">BatchSize 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-159">BatchSize property</span></span><br /><br /> <span data-ttu-id="5a1a3-160">CommandTimeout 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-160">CommandTimeout property</span></span>|  
|<span data-ttu-id="5a1a3-161">平面文件目标</span><span class="sxs-lookup"><span data-stu-id="5a1a3-161">Flat File destination</span></span>|<span data-ttu-id="5a1a3-162">Header 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-162">Header property</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="5a1a3-163">Compact 目标</span><span class="sxs-lookup"><span data-stu-id="5a1a3-163">Compact destination</span></span>|<span data-ttu-id="5a1a3-164">TableName 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-164">TableName property</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="5a1a3-165">目标</span><span class="sxs-lookup"><span data-stu-id="5a1a3-165">destination</span></span>|<span data-ttu-id="5a1a3-166">BulkInsertTableName 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-166">BulkInsertTableName property</span></span><br /><br /> <span data-ttu-id="5a1a3-167">BulkInsertFirstRow 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-167">BulkInsertFirstRow property</span></span><br /><br /> <span data-ttu-id="5a1a3-168">BulkInsertLastRow 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-168">BulkInsertLastRow property</span></span><br /><br /> <span data-ttu-id="5a1a3-169">BulkInsertOrder 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-169">BulkInsertOrder property</span></span><br /><br /> <span data-ttu-id="5a1a3-170">Timeout 属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-170">Timeout property</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="5a1a3-171">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="5a1a3-171">Related Tasks</span></span>  
  
-   [<span data-ttu-id="5a1a3-172">添加或更改属性表达式</span><span class="sxs-lookup"><span data-stu-id="5a1a3-172">Add or Change a Property Expression</span></span>](expressions/add-or-change-a-property-expression.md)  
  
## <a name="related-content"></a><span data-ttu-id="5a1a3-173">相关内容</span><span class="sxs-lookup"><span data-stu-id="5a1a3-173">Related Content</span></span>  
 <span data-ttu-id="5a1a3-174">pragmaticworks.com 上的技术文章 [SSIS 表达式小抄表](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)。</span><span class="sxs-lookup"><span data-stu-id="5a1a3-174">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a1a3-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a1a3-175">See Also</span></span>  
 <span data-ttu-id="5a1a3-176">[使用包中的属性表达式](expressions/use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="5a1a3-176">[Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="5a1a3-177">[通用属性](../../2014/integration-services/common-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5a1a3-177">[Common Properties](../../2014/integration-services/common-properties.md) </span></span>  
 <span data-ttu-id="5a1a3-178">[转换自定义属性](data-flow/transformations/transformation-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5a1a3-178">[Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md) </span></span>  
 [<span data-ttu-id="5a1a3-179">路径属性</span><span class="sxs-lookup"><span data-stu-id="5a1a3-179">Path Properties</span></span>](../../2014/integration-services/path-properties.md)  
  
  
