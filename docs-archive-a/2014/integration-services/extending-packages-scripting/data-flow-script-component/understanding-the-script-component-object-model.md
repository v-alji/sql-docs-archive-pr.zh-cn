---
title: 了解脚本组件对象模型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a11556b00efc5749e8ddb895712d6c61f2459d8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581385"
---
# <a name="understanding-the-script-component-object-model"></a><span data-ttu-id="d9f98-102">了解脚本组件对象模型</span><span class="sxs-lookup"><span data-stu-id="d9f98-102">Understanding the Script Component Object Model</span></span>
  <span data-ttu-id="d9f98-103">如 [代码和调试脚本组件] 中所述 (。/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md，脚本组件项目包含三个项目项：</span><span class="sxs-lookup"><span data-stu-id="d9f98-103">As discussed in [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md, the Script component project contains three project items:</span></span>

1.  <span data-ttu-id="d9f98-104">`ScriptMain` 项，该项包含您要用来编写代码的 `ScriptMain` 类。</span><span class="sxs-lookup"><span data-stu-id="d9f98-104">The `ScriptMain` item, which contains the `ScriptMain` class in which you write your code.</span></span> <span data-ttu-id="d9f98-105">`ScriptMain` 类从 `UserComponent` 类继承。</span><span class="sxs-lookup"><span data-stu-id="d9f98-105">The `ScriptMain` class inherits from the `UserComponent` class.</span></span>

2.  <span data-ttu-id="d9f98-106">`ComponentWrapper` 项，包含 `UserComponent` 类，该类是 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>（包含用于处理数据和与包交互的方法和属性）的实例。</span><span class="sxs-lookup"><span data-stu-id="d9f98-106">The `ComponentWrapper` item, which contains the `UserComponent` class, an instance of <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> that contains the methods and properties that you will use to process data and to interact with the package.</span></span> <span data-ttu-id="d9f98-107">`ComponentWrapper` 项还包含 `Connections` 和 `Variables` 集合类。</span><span class="sxs-lookup"><span data-stu-id="d9f98-107">The `ComponentWrapper` item also contains `Connections` and `Variables` collection classes.</span></span>

3.  <span data-ttu-id="d9f98-108">`BufferWrapper` 项，该项包含的类从每个输入和输出的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 继承，该项还包含每一列的类型化属性。</span><span class="sxs-lookup"><span data-stu-id="d9f98-108">The `BufferWrapper` item, which contains classes that inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> for each input and output, and typed properties for each column.</span></span>

 <span data-ttu-id="d9f98-109">当您在 `ScriptMain` 项中编写代码时，将使用本主题中讨论的对象、方法和属性。</span><span class="sxs-lookup"><span data-stu-id="d9f98-109">As you write your code in the `ScriptMain` item, you will use the objects, methods, and properties discussed in this topic.</span></span> <span data-ttu-id="d9f98-110">每个组件不会用到此处列出的所有方法；但用到的方法都会按照此处所示的顺序。</span><span class="sxs-lookup"><span data-stu-id="d9f98-110">Each component will not use all the methods listed here; however, when used, they are used in the sequence shown.</span></span>

 <span data-ttu-id="d9f98-111"><xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 基类不包含本主题中讨论的方法的任何实现代码。</span><span class="sxs-lookup"><span data-stu-id="d9f98-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class does not contain any implementation code for the methods discussed in this topic.</span></span> <span data-ttu-id="d9f98-112">因此没有必要（但是无害）将对基类实现的调用添加到您自己的方法实现中。</span><span class="sxs-lookup"><span data-stu-id="d9f98-112">Therefore it is unnecessary, but harmless, to add a call to the base class implementation to your own implementation of the method.</span></span>

 <span data-ttu-id="d9f98-113">有关如何在特定类型的脚本组件中使用这些类的方法和属性的信息，请参阅[其他脚本组件示例](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)一节。</span><span class="sxs-lookup"><span data-stu-id="d9f98-113">For information about how to use the methods and properties of these classes in a particular type of Script component, see the section [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span> <span data-ttu-id="d9f98-114">该示例主题还包含完整的代码示例。</span><span class="sxs-lookup"><span data-stu-id="d9f98-114">The example topics also contain complete code samples.</span></span>

## <a name="acquireconnections-method"></a><span data-ttu-id="d9f98-115">AcquireConnections 方法</span><span class="sxs-lookup"><span data-stu-id="d9f98-115">AcquireConnections Method</span></span>
 <span data-ttu-id="d9f98-116">源和目标通常必须连接到外部数据源。</span><span class="sxs-lookup"><span data-stu-id="d9f98-116">Sources and destinations generally must connect to an external data source.</span></span> <span data-ttu-id="d9f98-117">请重写 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> 基类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法，以从相应的连接管理器获得连接或连接信息。</span><span class="sxs-lookup"><span data-stu-id="d9f98-117">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class to retrieve the connection or the connection information from the appropriate connection manager.</span></span>

 <span data-ttu-id="d9f98-118">下面的示例从 ADO.NET 连接管理器返回 `System.Data.SqlClient.SqlConnection`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-118">The following example returns a `System.Data.SqlClient.SqlConnection` from an ADO.NET connection manager.</span></span>

```vb
Dim connMgr As IDTSConnectionManager100
Dim sqlConn As SqlConnection

Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    connMgr = Me.Connections.MyADONETConnection
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

End Sub
```

 <span data-ttu-id="d9f98-119">下面的示例从平面文件连接管理器返回完整的路径和文件名，然后使用 `System.IO.StreamReader` 打开该文件。</span><span class="sxs-lookup"><span data-stu-id="d9f98-119">The following example returns a complete path and file name from a Flat File Connection Manager, and then opens the file by using a `System.IO.StreamReader`.</span></span>

```vb
Private textReader As StreamReader
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    Dim connMgr As IDTSConnectionManager100 = _
        Me.Connections.MyFlatFileSrcConnectionManager
    Dim exportedAddressFile As String = _
        CType(connMgr.AcquireConnection(Nothing), String)
    textReader = New StreamReader(exportedAddressFile)

End Sub
```

## <a name="preexecute-method"></a><span data-ttu-id="d9f98-120">PreExecute 方法</span><span class="sxs-lookup"><span data-stu-id="d9f98-120">PreExecute Method</span></span>
 <span data-ttu-id="d9f98-121">如果您有必须仅在开始处理数据行之前执行一次的处理，请重写 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> 基类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-121">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class whenever you have processing that you must perform one time only before you start processing rows of data.</span></span> <span data-ttu-id="d9f98-122">例如，在目标中，您可能希望配置参数化的命令，供目标将每个数据行插入到数据源中。</span><span class="sxs-lookup"><span data-stu-id="d9f98-122">For example, in a destination, you may want to configure the parameterized command that the destination will use to insert each row of data into the data source.</span></span>

```vb
    Dim sqlConn As SqlConnection
    Dim sqlCmd As SqlCommand
    Dim sqlParam As SqlParameter
...
    Public Overrides Sub PreExecute()

        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _
            "VALUES(@addressid, @city)", sqlConn)
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)
        sqlCmd.Parameters.Add(sqlParam)
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)
        sqlCmd.Parameters.Add(sqlParam)

    End Sub
```

```csharp
SqlConnection sqlConn; 
SqlCommand sqlCmd; 
SqlParameter sqlParam; 

public override void PreExecute() 
{ 

    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn); 
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int); 
    sqlCmd.Parameters.Add(sqlParam); 
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30); 
    sqlCmd.Parameters.Add(sqlParam); 

}
```

## <a name="processing-inputs-and-outputs"></a><span data-ttu-id="d9f98-123">处理输入和输出</span><span class="sxs-lookup"><span data-stu-id="d9f98-123">Processing Inputs and Outputs</span></span>

### <a name="processing-inputs"></a><span data-ttu-id="d9f98-124">处理输入</span><span class="sxs-lookup"><span data-stu-id="d9f98-124">Processing Inputs</span></span>
 <span data-ttu-id="d9f98-125">配置为转换或目标的脚本组件有一个输入。</span><span class="sxs-lookup"><span data-stu-id="d9f98-125">Script components that are configured as transformations or destinations have one input.</span></span>

#### <a name="what-the-bufferwrapper-project-item-provides"></a><span data-ttu-id="d9f98-126">BufferWrapper 项目项提供的内容</span><span class="sxs-lookup"><span data-stu-id="d9f98-126">What the BufferWrapper Project Item Provides</span></span>
 <span data-ttu-id="d9f98-127">对于已配置的每个输入，`BufferWrapper` 项目项包含从 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 派生并且与输入同名的类。</span><span class="sxs-lookup"><span data-stu-id="d9f98-127">For each input that you have configured, the `BufferWrapper` project item contains a class that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> and has the same name as the input.</span></span> <span data-ttu-id="d9f98-128">每个输入缓冲区类包含以下属性、函数和方法：</span><span class="sxs-lookup"><span data-stu-id="d9f98-128">Each input buffer class contains the following properties, functions, and methods:</span></span>

-   <span data-ttu-id="d9f98-129">每个所选输入列的已命名类型化取值函数属性。</span><span class="sxs-lookup"><span data-stu-id="d9f98-129">Named, typed accessor properties for each selected input column.</span></span> <span data-ttu-id="d9f98-130">这些属性是只读或读/写的，取决于在“脚本转换编辑器”的“输入列”页中为该列指定的“使用类型”    。</span><span class="sxs-lookup"><span data-stu-id="d9f98-130">These properties are read-only or read/write depending on the **Usage Type** specified for the column on the **Input Columns** page of the **Script Transformation Editor**.</span></span>

-   <span data-ttu-id="d9f98-131">每个所选输入列的 \<column>_IsNull 属性。</span><span class="sxs-lookup"><span data-stu-id="d9f98-131">A **\<column>_IsNull** property for each selected input column.</span></span> <span data-ttu-id="d9f98-132">此属性也是只读或读/写的，取决于为该列指定的“使用类型”  。</span><span class="sxs-lookup"><span data-stu-id="d9f98-132">This property is also read-only or read/write depending on the **Usage Type** specified for the column.</span></span>

-   <span data-ttu-id="d9f98-133">每个已配置输出的 DirectRowTo\<outputbuffer> 方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-133">A **DirectRowTo\<outputbuffer>** method for each configured output.</span></span> <span data-ttu-id="d9f98-134">在将行筛选到位于同一 `ExclusionGroup` 中的多个输出之一时，将使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-134">You will use these methods when filtering rows to one of several outputs in the same `ExclusionGroup`.</span></span>

-   <span data-ttu-id="d9f98-135">一个 `NextRow` 函数，用于获取下一个输入行，以及一个 `EndOfRowset` 函数，用于确定最后一个数据缓冲区是否已经处理。</span><span class="sxs-lookup"><span data-stu-id="d9f98-135">A `NextRow` function to get the next input row, and an `EndOfRowset` function to determine whether the last buffer of data has been processed.</span></span> <span data-ttu-id="d9f98-136">使用在 `UserComponent` 基类中实现的输入处理方法时，通常不需要这些函数。</span><span class="sxs-lookup"><span data-stu-id="d9f98-136">You typically do not need these functions when you use the input processing methods implemented in the `UserComponent` base class.</span></span> <span data-ttu-id="d9f98-137">下一节提供有关 `UserComponent` 基类的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d9f98-137">The next section provides more information about the `UserComponent` base class.</span></span>

#### <a name="what-the-componentwrapper-project-item-provides"></a><span data-ttu-id="d9f98-138">ComponentWrapper 项目项提供的内容</span><span class="sxs-lookup"><span data-stu-id="d9f98-138">What the ComponentWrapper Project Item Provides</span></span>
 <span data-ttu-id="d9f98-139">ComponentWrapper 项目项包含从 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 派生的名为 `UserComponent` 的类。</span><span class="sxs-lookup"><span data-stu-id="d9f98-139">The ComponentWrapper project item contains a class named `UserComponent` that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>.</span></span> <span data-ttu-id="d9f98-140">您要用来编写自定义代码的 `ScriptMain` 类又派生自 `UserComponent`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-140">The `ScriptMain` class in which you write your custom code derives in turn from `UserComponent`.</span></span> <span data-ttu-id="d9f98-141">`UserComponent` 类包含以下方法：</span><span class="sxs-lookup"><span data-stu-id="d9f98-141">The `UserComponent` class contains the following methods:</span></span>

-   <span data-ttu-id="d9f98-142">`ProcessInput` 方法的重写实现。</span><span class="sxs-lookup"><span data-stu-id="d9f98-142">An overridden implementation of the `ProcessInput` method.</span></span> <span data-ttu-id="d9f98-143">这是数据流引擎在运行时继调用 `PreExecute` 方法后调用的下一个方法，该方法可被调用多次。</span><span class="sxs-lookup"><span data-stu-id="d9f98-143">This is the method that the data flow engine calls next at run time after the `PreExecute` method, and it may be called multiple times.</span></span> <span data-ttu-id="d9f98-144">`ProcessInput`将处理移交给\*\* \<inputbuffer> _ProcessInput\*\*方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-144">`ProcessInput` hands off processing to the **\<inputbuffer>_ProcessInput** method.</span></span> <span data-ttu-id="d9f98-145">然后 `ProcessInput` 方法检查是否已到达输入缓冲区的末尾，如果已到达缓冲区末尾，则调用可重写的 `FinishOutputs` 方法和私有 `MarkOutputsAsFinished` 方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-145">Then the `ProcessInput` method checks for the end of the input buffer and, if the end of the buffer has been reached, calls the overridable `FinishOutputs` method and the private `MarkOutputsAsFinished` method.</span></span> <span data-ttu-id="d9f98-146">然后 `MarkOutputsAsFinished` 方法对最后一个输出缓冲区调用 `SetEndOfRowset`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-146">The `MarkOutputsAsFinished` method then calls `SetEndOfRowset` on the last output buffer.</span></span>

-   <span data-ttu-id="d9f98-147">\<inputbuffer>_ProcessInput 方法的可重写实现。</span><span class="sxs-lookup"><span data-stu-id="d9f98-147">An overridable implementation of the **\<inputbuffer>_ProcessInput** method.</span></span> <span data-ttu-id="d9f98-148">此默认实现只是遍历每个输入行并调用 \<inputbuffer>_ProcessInputRow。</span><span class="sxs-lookup"><span data-stu-id="d9f98-148">This default implementation simply loops through each input row and calls **\<inputbuffer>_ProcessInputRow**.</span></span>

-   <span data-ttu-id="d9f98-149">\<inputbuffer>_ProcessInputRow 方法的可重写实现。</span><span class="sxs-lookup"><span data-stu-id="d9f98-149">An overridable implementation of the **\<inputbuffer>_ProcessInputRow** method.</span></span> <span data-ttu-id="d9f98-150">默认实现为空。</span><span class="sxs-lookup"><span data-stu-id="d9f98-150">The default implementation is empty.</span></span> <span data-ttu-id="d9f98-151">通常会重写此方法以编写自定义数据处理代码。</span><span class="sxs-lookup"><span data-stu-id="d9f98-151">This is the method that you will normally override to write your custom data processing code.</span></span>

#### <a name="what-your-custom-code-should-do"></a><span data-ttu-id="d9f98-152">自定义代码应执行的操作</span><span class="sxs-lookup"><span data-stu-id="d9f98-152">What Your Custom Code Should Do</span></span>
 <span data-ttu-id="d9f98-153">可以使用以下方法在 `ScriptMain` 类中处理输入：</span><span class="sxs-lookup"><span data-stu-id="d9f98-153">You can use the following methods to process input in the `ScriptMain` class:</span></span>

-   <span data-ttu-id="d9f98-154">重写 \<inputbuffer>_ProcessInputRow 以便在每个输入行通过时处理其中的数据。</span><span class="sxs-lookup"><span data-stu-id="d9f98-154">Override **\<inputbuffer>_ProcessInputRow** to process the data in each input row as it passes through.</span></span>

-   <span data-ttu-id="d9f98-155">仅当你在遍历输入行时必须执行附加操作时，才重写 \<inputbuffer>_ProcessInput。</span><span class="sxs-lookup"><span data-stu-id="d9f98-155">Override **\<inputbuffer>_ProcessInput** only if you have to do something additional while looping through input rows.</span></span> <span data-ttu-id="d9f98-156">例如，在处理完所有行后，您必须对进行测试 `EndOfRowset` 以执行其他操作 (。 ) 调用\*\* \<inputbuffer> _ProcessInputRow\*\*执行行处理。</span><span class="sxs-lookup"><span data-stu-id="d9f98-156">(For example, you have to test for `EndOfRowset` to take some other action after all rows have been processed.) Call **\<inputbuffer>_ProcessInputRow** to perform the row processing.</span></span>

-   <span data-ttu-id="d9f98-157">如果必须在关闭输出之前对输出进行一些操作，请重写 `FinishOutputs`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-157">Override `FinishOutputs` if you have to do something to the outputs before they are closed.</span></span>

 <span data-ttu-id="d9f98-158">`ProcessInput` 方法确保以合适的次数调用这些方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-158">The `ProcessInput` method ensures that these methods are called at the appropriate times.</span></span>

### <a name="processing-outputs"></a><span data-ttu-id="d9f98-159">处理输出</span><span class="sxs-lookup"><span data-stu-id="d9f98-159">Processing Outputs</span></span>
 <span data-ttu-id="d9f98-160">配置为源或转换的脚本组件有一个或多个输出。</span><span class="sxs-lookup"><span data-stu-id="d9f98-160">Script components configured as sources or transformations have one or more outputs.</span></span>

#### <a name="what-the-bufferwrapper-project-item-provides"></a><span data-ttu-id="d9f98-161">BufferWrapper 项目项提供的内容</span><span class="sxs-lookup"><span data-stu-id="d9f98-161">What the BufferWrapper Project Item Provides</span></span>
 <span data-ttu-id="d9f98-162">对于已配置的每个输出，BufferWrapper 项目项包含从 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 派生并且与输出同名的类。</span><span class="sxs-lookup"><span data-stu-id="d9f98-162">For each output that you have configured, the BufferWrapper project item contains a class that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> and has the same name as the output.</span></span> <span data-ttu-id="d9f98-163">每个输入缓冲区类包含以下属性和方法：</span><span class="sxs-lookup"><span data-stu-id="d9f98-163">Each input buffer class contains the following properties and methods:</span></span>

-   <span data-ttu-id="d9f98-164">每个输出列的已命名类型化只写取值函数属性。</span><span class="sxs-lookup"><span data-stu-id="d9f98-164">Named, typed, write-only accessor properties for each output column.</span></span>

-   <span data-ttu-id="d9f98-165">每个所选输出列的只写\*\* \<column> _IsNull\*\*属性，可用于将列值设置为 `null` 。</span><span class="sxs-lookup"><span data-stu-id="d9f98-165">A write-only **\<column>_IsNull** property for each selected output column that you can use to set the column value to `null`.</span></span>

-   <span data-ttu-id="d9f98-166">一个 `AddRow` 方法，用于将空的新行添加到输出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="d9f98-166">An `AddRow` method to add an empty new row to the output buffer.</span></span>

-   <span data-ttu-id="d9f98-167">一个 `SetEndOfRowset` 方法，用于通知数据流引擎没有数据缓冲区了。</span><span class="sxs-lookup"><span data-stu-id="d9f98-167">A `SetEndOfRowset` method to let the data flow engine know that no more buffers of data are expected.</span></span> <span data-ttu-id="d9f98-168">还有一个 `EndOfRowset` 函数，用于确定当前缓冲区是否是最后一个数据缓冲区。</span><span class="sxs-lookup"><span data-stu-id="d9f98-168">There is also an `EndOfRowset` function to determine whether the current buffer is the last buffer of data.</span></span> <span data-ttu-id="d9f98-169">当使用基类中实现的输入处理方法时，通常不需要这些函数 `UserComponent` 。</span><span class="sxs-lookup"><span data-stu-id="d9f98-169">You generally do not need these functions when you use the input processing methods implemented in the `UserComponent` base class.</span></span>

#### <a name="what-the-componentwrapper-project-item-provides"></a><span data-ttu-id="d9f98-170">ComponentWrapper 项目项提供的内容</span><span class="sxs-lookup"><span data-stu-id="d9f98-170">What the ComponentWrapper Project Item Provides</span></span>
 <span data-ttu-id="d9f98-171">ComponentWrapper 项目项包含从 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 派生的名为 `UserComponent` 的类。</span><span class="sxs-lookup"><span data-stu-id="d9f98-171">The ComponentWrapper project item contains a class named `UserComponent` that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>.</span></span> <span data-ttu-id="d9f98-172">您要用来编写自定义代码的 `ScriptMain` 类又派生自 `UserComponent`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-172">The `ScriptMain` class in which you write your custom code derives in turn from `UserComponent`.</span></span> <span data-ttu-id="d9f98-173">`UserComponent` 类包含以下方法：</span><span class="sxs-lookup"><span data-stu-id="d9f98-173">The `UserComponent` class contains the following methods:</span></span>

-   <span data-ttu-id="d9f98-174">`PrimeOutput` 方法的重写实现。</span><span class="sxs-lookup"><span data-stu-id="d9f98-174">An overridden implementation of the `PrimeOutput` method.</span></span> <span data-ttu-id="d9f98-175">在运行时，数据流引擎在调用 `ProcessInput` 之前调用此方法，而且只调用一次。</span><span class="sxs-lookup"><span data-stu-id="d9f98-175">The data flow engine calls this method before `ProcessInput` at run time, and it is only called one time.</span></span> <span data-ttu-id="d9f98-176">`PrimeOutput` 将处理传送到 `CreateNewOutputRows` 方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-176">`PrimeOutput` hands off processing to the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="d9f98-177">然后，如果该组件是源（也就是说组件没有输入），则 `PrimeOutput` 调用可重写的 `FinishOutputs` 方法和私有 `MarkOutputsAsFinished` 方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-177">Then, if the component is a source (that is, the component has no inputs), `PrimeOutput` calls the overridable `FinishOutputs` method and the private `MarkOutputsAsFinished` method.</span></span> <span data-ttu-id="d9f98-178">`MarkOutputsAsFinished` 方法对最后一个输出缓冲区调用 `SetEndOfRowset`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-178">The `MarkOutputsAsFinished` method calls `SetEndOfRowset` on the last output buffer.</span></span>

-   <span data-ttu-id="d9f98-179">`CreateNewOutputRows` 方法的可重写实现。</span><span class="sxs-lookup"><span data-stu-id="d9f98-179">An overridable implementation of the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="d9f98-180">默认实现为空。</span><span class="sxs-lookup"><span data-stu-id="d9f98-180">The default implementation is empty.</span></span> <span data-ttu-id="d9f98-181">通常会重写此方法以编写自定义数据处理代码。</span><span class="sxs-lookup"><span data-stu-id="d9f98-181">This is the method that you will normally override to write your custom data processing code.</span></span>

#### <a name="what-your-custom-code-should-do"></a><span data-ttu-id="d9f98-182">自定义代码应执行的操作</span><span class="sxs-lookup"><span data-stu-id="d9f98-182">What Your Custom Code Should Do</span></span>
 <span data-ttu-id="d9f98-183">可以使用以下方法在 `ScriptMain` 类中处理输出：</span><span class="sxs-lookup"><span data-stu-id="d9f98-183">You can use the following methods to process outputs in the `ScriptMain` class:</span></span>

-   <span data-ttu-id="d9f98-184">仅当您可以在处理输入行之前添加和填充输出行时，重写 `CreateNewOutputRows`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-184">Override `CreateNewOutputRows` only when you can add and populate output rows before processing input rows.</span></span> <span data-ttu-id="d9f98-185">例如，可以在源中使用 `CreateNewOutputRows`，但在带有异步输出的转换中，应在输入数据处理期间或之后调用 `AddRow`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-185">For example, you can use `CreateNewOutputRows` in a source, but in a transformation with asynchronous outputs, you should call `AddRow` during or after the processing of input data.</span></span>

-   <span data-ttu-id="d9f98-186">如果必须在关闭输出之前对输出进行一些操作，请重写 `FinishOutputs`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-186">Override `FinishOutputs` if you have to do something to the outputs before they are closed.</span></span>

 <span data-ttu-id="d9f98-187">`PrimeOutput` 方法确保以合适的次数调用这些方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-187">The `PrimeOutput` method ensures that these methods are called at the appropriate times.</span></span>

## <a name="postexecute-method"></a><span data-ttu-id="d9f98-188">PostExecute 方法</span><span class="sxs-lookup"><span data-stu-id="d9f98-188">PostExecute Method</span></span>
 <span data-ttu-id="d9f98-189">如果您有必须仅在处理完数据行之后执行一次的处理，请重写 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> 基类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="d9f98-189">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class whenever you have processing that you must perform one time only after you have processed the rows of data.</span></span> <span data-ttu-id="d9f98-190">例如，在源中，您可能希望关闭曾用来将数据加载到数据流中的 `System.Data.SqlClient.SqlDataReader`。</span><span class="sxs-lookup"><span data-stu-id="d9f98-190">For example, in a source, you may want to close the `System.Data.SqlClient.SqlDataReader` that you have used to load data into the data flow.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="d9f98-191">`ReadWriteVariables` 集合仅在 `PostExecute` 方法中可用。</span><span class="sxs-lookup"><span data-stu-id="d9f98-191">The collection of `ReadWriteVariables` is available only in the `PostExecute` method.</span></span> <span data-ttu-id="d9f98-192">因此不能在处理每行数据时直接递增包变量的值，</span><span class="sxs-lookup"><span data-stu-id="d9f98-192">Therefore you cannot directly increment the value of a package variable as you process each row of data.</span></span> <span data-ttu-id="d9f98-193">相反，增加局部变量的值，并在 `PostExecute` 处理完所有数据后将包变量的值设置为方法中的局部变量的值。</span><span class="sxs-lookup"><span data-stu-id="d9f98-193">Instead, increment the value of a local variable, and set the value of the package variable to the value of the local variable in the `PostExecute` method after all data has been processed.</span></span>

## <a name="releaseconnections-method"></a><span data-ttu-id="d9f98-194">ReleaseConnections 方法</span><span class="sxs-lookup"><span data-stu-id="d9f98-194">ReleaseConnections Method</span></span>
 <span data-ttu-id="d9f98-195">源和目标通常必须连接到外部数据源。</span><span class="sxs-lookup"><span data-stu-id="d9f98-195">Sources and destinations typically must connect to an external data source.</span></span> <span data-ttu-id="d9f98-196">请重写 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> 基类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法，以关闭和释放先前在 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> 方法中打开的连接。</span><span class="sxs-lookup"><span data-stu-id="d9f98-196">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class to close and release the connection that you have opened previously in the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> method.</span></span>

```vb
    Dim connMgr As IDTSConnectionManager100
...
    Public Overrides Sub ReleaseConnections()

        connMgr.ReleaseConnection(sqlConn)

    End Sub
```

```csharp
IDTSConnectionManager100 connMgr;

public override void ReleaseConnections()
{

    connMgr.ReleaseConnection(sqlConn);

}
```

<span data-ttu-id="d9f98-197">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="d9f98-197">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d9f98-198">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="d9f98-198">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d9f98-199">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="d9f98-199">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d9f98-200">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="d9f98-200">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9f98-201">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9f98-201">See Also</span></span>
 <span data-ttu-id="d9f98-202">[在脚本组件编辑器中配置脚本组件](configuring-the-script-component-in-the-script-component-editor.md)[编写和调试脚本组件] (。/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md</span><span class="sxs-lookup"><span data-stu-id="d9f98-202">[Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md) [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md</span></span>


