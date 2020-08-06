---
title: 数据中的错误处理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data conversion errors [Integration Services]
- errors [Integration Services], data flow components
- lookups [Integration Services]
- errors [Integration Services]
- errors [Integration Services], data flow outputs
- error outputs [Integration Services]
- data flow [Integration Services], errors
- expressions [Integration Services], errors
ms.assetid: c61667b4-25cb-4d45-a52f-a733e32863f4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 442ecc68fc352d50955af9302fbcedf77ba36338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694066"
---
# <a name="error-handling-in-data"></a><span data-ttu-id="d4d1c-102">数据中的错误处理</span><span class="sxs-lookup"><span data-stu-id="d4d1c-102">Error Handling in Data</span></span>
  <span data-ttu-id="d4d1c-103">数据流组件将转换应用到列数据、从源提取数据或将数据加载到目标中时，可能会发生错误。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-103">When a data flow component applies a transformation to column data, extracts data from sources, or loads data into destinations, errors can occur.</span></span> <span data-ttu-id="d4d1c-104">错误常因意外数据值而发生。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-104">Errors frequently occur because of unexpected data values.</span></span> <span data-ttu-id="d4d1c-105">例如，如果列包含字符串而不是数字，数据转换将失败；在数据库列中执行插入操作时，如果数据是日期而列的数据类型为数值，此操作将失败；如果因列值为零而导致数学运算无效，表达式将无法计算。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-105">For example, a data conversion fails because a column contains a string instead of a number, an insertion into a database column fails because the data is a date and the column has a numeric data type, or an expression fails to evaluate because a column value is zero, resulting in a mathematical operation that is not valid.</span></span>  
  
 <span data-ttu-id="d4d1c-106">错误通常属于下列类别之一：</span><span class="sxs-lookup"><span data-stu-id="d4d1c-106">Errors typically fall into one the following categories:</span></span>  
  
-   <span data-ttu-id="d4d1c-107">数据转换错误，其在转换导致重要数字丢失、非重要数字丢失和字符串截断时发生。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-107">Data conversion errors, which occur if a conversion results in loss of significant digits, the loss of insignificant digits, and the truncation of strings.</span></span> <span data-ttu-id="d4d1c-108">如果不支持请求的转换，也会发生数据转换错误。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-108">Data conversion errors also occur if the requested conversion is not supported.</span></span>  
  
-   <span data-ttu-id="d4d1c-109">表达式计算错误，其在运行时计算的表达式执行无效运算，或因数据值丢失或错误而出现语法错误时发生。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-109">Expression evaluation errors, which occur if expressions that are evaluated at run time perform invalid operations or become syntactically incorrect because of missing or incorrect data values.</span></span>  
  
-   <span data-ttu-id="d4d1c-110">查找错误，其在查找操作在查找表中找不到匹配时发生。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-110">Lookup errors, which occur if a lookup operation fails to locate a match in the lookup table.</span></span>  
  
 <span data-ttu-id="d4d1c-111">许多数据流组件支持错误输出，这使得您可以控制组件处理传入和传出数据中行级错误的方式。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-111">Many data flow components support error outputs, which let you control how the component handles row-level errors in both incoming and outgoing data.</span></span> <span data-ttu-id="d4d1c-112">通过设置输入或输出中各个列的选项，可以指定发生截断或错误时组件的行为。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-112">You specify how the component behaves when truncation or an error occurs by setting options on individual columns in the input or output.</span></span> <span data-ttu-id="d4d1c-113">例如，可以指定组件应在客户名称数据被截断时失败，但忽略另一包含不太重要数据的列上的错误。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-113">For example, you can specify that the component should fail if customer name data is truncated, but ignore errors on another column that contains less important data.</span></span>  
  
 <span data-ttu-id="d4d1c-114">错误输出可以连接到另一个转换的输入，或者加载到非错误输出以外的目标。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-114">The error output can be connected to the input of another transformation or loaded into a different destination than the non-error output.</span></span> <span data-ttu-id="d4d1c-115">例如，错误输出可以连接到为空白列提供字符串的派生列转换。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-115">For example, the error output can be a connected to a Derived Column transformation that provides a string for a column that is blank.</span></span>  
  
 <span data-ttu-id="d4d1c-116">下列关系图显示包含错误输出的简单数据流。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-116">The following diagram shows a simple data flow including an error output.</span></span>  
  
 <span data-ttu-id="d4d1c-117">![包含错误输出的数据流](../media/mw-dts-11.gif "包含错误输出的数据流")</span><span class="sxs-lookup"><span data-stu-id="d4d1c-117">![Data flow with error output](../media/mw-dts-11.gif "Data flow with error output")</span></span>  
  
 <span data-ttu-id="d4d1c-118">除数据列外，错误输出还包含 **ErrorCode** 列和 **ErrorColumn** 列。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-118">In addition to the data columns, the error output includes the **ErrorCode** and **ErrorColumn** columns.</span></span> <span data-ttu-id="d4d1c-119">**ErrorCode** 列标识错误，而 **ErrorColumn** 列则包含错误列的沿袭标识符。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-119">The **ErrorCode** column identifies the error and the **ErrorColumn** contains the lineage identifier of the error column.</span></span> <span data-ttu-id="d4d1c-120">若要查看这些列的元数据，请单击将错误输出连接到数据流中下一个组件的路径。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-120">To view the metadata of these columns, click the path that connects the error output to the next component in the data flow.</span></span> <span data-ttu-id="d4d1c-121">在某些环境下， **ErrorColumn** 列的值会设置为零。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-121">Under some circumstances, the value of the **ErrorColumn** column is set to zero.</span></span> <span data-ttu-id="d4d1c-122">当错误条件影响到整行而不是单列时，就会发生该情况。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-122">This occurs when the error condition affects the entire row instead of a single column.</span></span> <span data-ttu-id="d4d1c-123">例如，在查找转换中的查找失败时。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-123">An example is when a lookup fails in the Lookup transformation.</span></span>  
  
 <span data-ttu-id="d4d1c-124">有关详细信息，请参阅 [数据流](data-flow.md) 和 [Integration Services 路径](integration-services-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-124">For more information, see [Data Flow](data-flow.md) and [Integration Services Paths](integration-services-paths.md).</span></span>  
  
 <span data-ttu-id="d4d1c-125">有关 Integration Services 的错误、警告和其他消息的列表，请参阅 [Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-125">For a list of Integration Services errors, warnings, and other messages, see [Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md).</span></span>  
  
## <a name="error-and-truncation-options"></a><span data-ttu-id="d4d1c-126">错误和截断选项</span><span class="sxs-lookup"><span data-stu-id="d4d1c-126">Error and Truncation Options</span></span>  
 <span data-ttu-id="d4d1c-127">错误属于两个类别之一：错误或截断。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-127">Errors fall into one of two categories: errors or truncations.</span></span> <span data-ttu-id="d4d1c-128">错误指示确定的失败，并且生成 NULL 结果。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-128">An error indicates an unequivocal failure, and generates a NULL result.</span></span> <span data-ttu-id="d4d1c-129">此类错误可以包括数据转换错误或表达式计算错误。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-129">Such errors can include data conversion errors or expression evaluation errors.</span></span> <span data-ttu-id="d4d1c-130">例如，尝试将包含字母字符的字符串转换为数字将导致错误。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-130">For example, an attempt to convert a string that contains alphabetical characters to a number causes an error.</span></span> <span data-ttu-id="d4d1c-131">数据转换、表达式计算和对变量、属性和数据列的表达式结果分配可能会由于非法转换和不兼容的数据类型而失败。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-131">Data conversions, expression evaluations, and assignments of expression results to variables, properties, and data columns may fail because of illegal casts and incompatible data types.</span></span> <span data-ttu-id="d4d1c-132">有关详细信息，请参阅[转换 (SSIS 表达式)](../expressions/cast-ssis-expression.md)、[表达式中的 Integration Services 数据类型](../expressions/integration-services-data-types-in-expressions.md)和 [Integration Services 数据类型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-132">For more information see, [Cast &#40;SSIS Expression&#41;](../expressions/cast-ssis-expression.md), [Integration Services Data Types in Expressions](../expressions/integration-services-data-types-in-expressions.md), and [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="d4d1c-133">截断的严重程度小于错误。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-133">A truncation is less serious than an error.</span></span> <span data-ttu-id="d4d1c-134">截断生成的结果可能是有用的甚至是所希望的。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-134">A truncation generates results that might be usable or even desirable.</span></span> <span data-ttu-id="d4d1c-135">您可以将截断视为错误或可接受的情况。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-135">You can elect to treat truncations as errors or as acceptable conditions.</span></span> <span data-ttu-id="d4d1c-136">例如，如果将 15 个字符的字符串插入只有一个字符宽度的列，您可以截断该字符串。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-136">For example, if you are inserting a 15-character string into a column that is only one character wide, you can elect to truncate the string.</span></span>  
  
 <span data-ttu-id="d4d1c-137">可以配置源、转换和目标处理错误和截断的方式。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-137">You can configure how sources, transformations, and destinations handle errors and truncations.</span></span> <span data-ttu-id="d4d1c-138">下表对这些选项进行说明：</span><span class="sxs-lookup"><span data-stu-id="d4d1c-138">The following table describes the options.</span></span>  
  
|<span data-ttu-id="d4d1c-139">选项</span><span class="sxs-lookup"><span data-stu-id="d4d1c-139">Option</span></span>|<span data-ttu-id="d4d1c-140">说明</span><span class="sxs-lookup"><span data-stu-id="d4d1c-140">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d4d1c-141">组件失败</span><span class="sxs-lookup"><span data-stu-id="d4d1c-141">Fail Component</span></span>|<span data-ttu-id="d4d1c-142">发生错误或截断时数据流任务失败。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-142">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="d4d1c-143">失败是错误或截断的默认选项。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-143">Failure is the default option for an error and a truncation.</span></span>|  
|<span data-ttu-id="d4d1c-144">忽略失败</span><span class="sxs-lookup"><span data-stu-id="d4d1c-144">Ignore Failure</span></span>|<span data-ttu-id="d4d1c-145">忽略错误或截断，并且将数据行定向到转换或源的输出。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-145">The error or the truncation is ignored and the data row is directed to the output of the transformation or source.</span></span>|  
|<span data-ttu-id="d4d1c-146">重定向行</span><span class="sxs-lookup"><span data-stu-id="d4d1c-146">Redirect Row</span></span>|<span data-ttu-id="d4d1c-147">将错误或截断的数据行定向到源、转换或目标的错误输出。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-147">The error or the truncation data row is directed to the error output of the source, transformation, or destination.</span></span>|  
  
## <a name="adding-the-error-description"></a><span data-ttu-id="d4d1c-148">添加错误说明</span><span class="sxs-lookup"><span data-stu-id="d4d1c-148">Adding the Error Description</span></span>  
 <span data-ttu-id="d4d1c-149">默认情况下，错误输出提供了数值错误代码，并且通常包含发生错误的列的标识符。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-149">By default an error output provides the numeric error code and usually contains the identifier of the column in which the error occurred.</span></span> <span data-ttu-id="d4d1c-150">通过使用脚本的单独一行来调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 接口的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 方法，可以使用脚本组件来包括其他列中的错误说明。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-150">You can use the Script component to include the error description in an additional column by using a single line of script to call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span>  
  
 <span data-ttu-id="d4d1c-151">可以将脚本组件添加到数据流的错误段中希望捕获其错误的数据流组件下游的任何位置，但通常在错误行被写入目标之前立即将其放入。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-151">The Script component can be added to the error segment of the data flow anywhere downstream from the data flow components whose errors that you want to capture, but is typically placed immediately before the error rows are written to a destination.</span></span> <span data-ttu-id="d4d1c-152">这样，脚本只查找已写入的错误行的说明。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-152">This way, the script looks up only descriptions for error rows that are written.</span></span> <span data-ttu-id="d4d1c-153">例如，数据流的错误段可能纠正某些错误，并且不将这些行写入错误目标。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-153">For example, the error segment of the data flow may correct some errors and not write those rows to an error destination.</span></span> <span data-ttu-id="d4d1c-154">有关详细信息，请参阅[使用脚本组件增强错误输出](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-154">For more information, see [Enhancing an Error Output with the Script Component](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md).</span></span>  
  
### <a name="to-configure-an-error-output"></a><span data-ttu-id="d4d1c-155">配置错误输出</span><span class="sxs-lookup"><span data-stu-id="d4d1c-155">To configure an error output</span></span>  
  
-   [<span data-ttu-id="d4d1c-156">在数据流组件中配置错误输出</span><span class="sxs-lookup"><span data-stu-id="d4d1c-156">Configure an Error Output in a Data Flow Component</span></span>](../configure-an-error-output-in-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="d4d1c-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4d1c-157">See Also</span></span>  
 <span data-ttu-id="d4d1c-158">[数据流](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="d4d1c-158">[Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="d4d1c-159">[使用转换对数据进行转换](transformations/transform-data-with-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="d4d1c-159">[Transform Data with Transformations](transformations/transform-data-with-transformations.md) </span></span>  
 <span data-ttu-id="d4d1c-160">[使用路径连接组件](../connect-components-with-paths.md) </span><span class="sxs-lookup"><span data-stu-id="d4d1c-160">[Connect Components with Paths](../connect-components-with-paths.md) </span></span>  
 <span data-ttu-id="d4d1c-161">[数据流任务](../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="d4d1c-161">[Data Flow Task](../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="d4d1c-162">数据流</span><span class="sxs-lookup"><span data-stu-id="d4d1c-162">Data Flow</span></span>](data-flow.md)  
  
  
