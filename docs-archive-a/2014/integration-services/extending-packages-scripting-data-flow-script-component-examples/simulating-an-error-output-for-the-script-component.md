---
title: 模拟脚本组件的错误输出 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], error output
- error outputs [Integration Services], Script component
ms.assetid: f8b6ecff-ac99-4231-a0e7-7ce4ad76bad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bed458ce378eb26cd863811b4974b5f39429e1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688036"
---
# <a name="simulating-an-error-output-for-the-script-component"></a><span data-ttu-id="bfc25-102">模拟脚本组件的错误输出</span><span class="sxs-lookup"><span data-stu-id="bfc25-102">Simulating an Error Output for the Script Component</span></span>
  <span data-ttu-id="bfc25-103">虽然您无法在脚本组件中直接将输出配置为错误输出，以便自动处理错误行，但必要时可通过创建附加输出并在脚本中使用条件逻辑将行定向到此输出，以再现内置错误输出的功能。</span><span class="sxs-lookup"><span data-stu-id="bfc25-103">Although you cannot directly configure an output as an error output in the Script component for automatic handling of error rows, you can reproduce the functionality of a built-in error output by creating an additional output and using conditional logic in your script to direct rows to this output when appropriate.</span></span> <span data-ttu-id="bfc25-104">您可能希望通过添加两个用于接收错误号以及出现错误的列的 ID 的附加输出列，以模拟内置错误输出的行为。</span><span class="sxs-lookup"><span data-stu-id="bfc25-104">You may want to imitate the behavior of a built-in error output by adding two additional output columns to receive the error number and the ID of the column in which an error occurred.</span></span>  
  
 <span data-ttu-id="bfc25-105">若要添加与特定预定义 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 错误代码对应的错误说明，可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 接口的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 方法，该接口可通过脚本组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 属性提供。</span><span class="sxs-lookup"><span data-stu-id="bfc25-105">If you want to add the error description that corresponds to a specific predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error code, you can use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the Script component's <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfc25-106">示例</span><span class="sxs-lookup"><span data-stu-id="bfc25-106">Example</span></span>  
 <span data-ttu-id="bfc25-107">下面的示例使用一个配置为具有两个同步输出的转换的脚本组件。</span><span class="sxs-lookup"><span data-stu-id="bfc25-107">The example shown here uses a Script component configured as a transformation that has two synchronous outputs.</span></span> <span data-ttu-id="bfc25-108">该脚本组件的目的是从 AdventureWorks 示例数据库中的地址数据中筛选错误行。</span><span class="sxs-lookup"><span data-stu-id="bfc25-108">The purpose of the Script component is to filter error rows from address data in the AdventureWorks sample database.</span></span> <span data-ttu-id="bfc25-109">此虚构示例假设我们正在为一项针对北美客户的促销活动做准备，需要筛选出不在北美的地址。</span><span class="sxs-lookup"><span data-stu-id="bfc25-109">This fictitious example assumes that we are preparing a promotion for North American customers and need to filter out addresses that are not located in North America.</span></span>  
  
#### <a name="to-configure-the-example"></a><span data-ttu-id="bfc25-110">配置示例</span><span class="sxs-lookup"><span data-stu-id="bfc25-110">To configure the example</span></span>  
  
1.  <span data-ttu-id="bfc25-111">创建新脚本组件之前，先创建一个连接管理器，并配置一个从 AdventureWorks 示例数据库选择地址数据的数据流源。</span><span class="sxs-lookup"><span data-stu-id="bfc25-111">Before creating the new Script component, create a connection manager and configure a data flow source that selects address data from the AdventureWorks sample database.</span></span> <span data-ttu-id="bfc25-112">对于此示例，由于仅查看 CountryRegionName 列，所以只需使用 Person.vStateCountryProvinceRegion 视图，或通过联接 Person.Address、Person.StateProvince 和 Person.CountryRegion 表来选择数据。</span><span class="sxs-lookup"><span data-stu-id="bfc25-112">For this example, which only looks at the CountryRegionName column, you can simply use the Person.vStateCountryProvinceRegion view, or you can select data by joining the Person.Address, Person.StateProvince, and Person.CountryRegion tables.</span></span>  
  
2.  <span data-ttu-id="bfc25-113">向数据流设计器图面添加新的脚本组件并将其配置为转换。</span><span class="sxs-lookup"><span data-stu-id="bfc25-113">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span> <span data-ttu-id="bfc25-114">打开“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="bfc25-114">Open the **Script Transformation Editor**.</span></span>  
  
3.  <span data-ttu-id="bfc25-115">在“脚本”  页中，将 **ScriptLanguage** 属性设置为要用于编写脚本代码的脚本语言。</span><span class="sxs-lookup"><span data-stu-id="bfc25-115">On the **Script** page, set the **ScriptLanguage** property to the script language that you want to use to code the script.</span></span>  
  
4.  <span data-ttu-id="bfc25-116">单击“编辑脚本”打开   Tools for Applications (VSTA)[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bfc25-116">Click **Edit Script** to open [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
5.  <span data-ttu-id="bfc25-117">在 `Input0_ProcessInputRow` 方法中，键入或粘贴如下所示的示例代码。</span><span class="sxs-lookup"><span data-stu-id="bfc25-117">In the `Input0_ProcessInputRow` method, type or paste the sample code shown below.</span></span>  
  
6.  <span data-ttu-id="bfc25-118">关闭 VSTA。</span><span class="sxs-lookup"><span data-stu-id="bfc25-118">Close VSTA.</span></span>  
  
7.  <span data-ttu-id="bfc25-119">在“输入列”  页中，选择要在脚本转换中处理的列。</span><span class="sxs-lookup"><span data-stu-id="bfc25-119">On the **Input Columns** page, select the columns that you want to process in the Script transformation.</span></span> <span data-ttu-id="bfc25-120">此示例仅使用 CountryRegionName 列。</span><span class="sxs-lookup"><span data-stu-id="bfc25-120">This example uses only the CountryRegionName column.</span></span> <span data-ttu-id="bfc25-121">您未选择的可用列将不进行任何更改，原封不动地在数据流中传递。</span><span class="sxs-lookup"><span data-stu-id="bfc25-121">Available input columns that you leave unselected will simply be passed through unchanged in the data flow.</span></span>  
  
8.  <span data-ttu-id="bfc25-122">在 "**输入和输出**" 页上，添加一个新的第二个输出，并将其 `SynchronousInputID` 值设置为输入的 ID，这也是 `SynchronousInputID` 默认输出的属性的值。</span><span class="sxs-lookup"><span data-stu-id="bfc25-122">On the **Inputs and Outputs** page, add a new, second output, and set its `SynchronousInputID` value to the ID of the input, which is also the value of the `SynchronousInputID` property of the default output.</span></span> <span data-ttu-id="bfc25-123">将两个输出的 `ExclusionGroup` 属性都设置为同一非零值（例如 1），以指示每一行都将仅定向到两个输出中的一个。</span><span class="sxs-lookup"><span data-stu-id="bfc25-123">Set the `ExclusionGroup` property of both outputs to the same non-zero value (for example, 1) to indicate that each row will be directed to only one of the two outputs.</span></span> <span data-ttu-id="bfc25-124">以不同名称为新的错误输出命名，如“MyErrorOutput”。</span><span class="sxs-lookup"><span data-stu-id="bfc25-124">Give the new error output a distinctive name, such as "MyErrorOutput."</span></span>  
  
9. <span data-ttu-id="bfc25-125">向新错误输出中添加其他输出列，以捕获所需的错误信息，其中包括错误代码、出现错误的列的 ID，可能还有错误说明。</span><span class="sxs-lookup"><span data-stu-id="bfc25-125">Add additional output columns to the new error output to capture the desired error information, which may include the error code, the ID of the column in which the error occurred, and possibly the error description.</span></span> <span data-ttu-id="bfc25-126">此示例将创建新列：ErrorColumn 和 ErrorMessage。</span><span class="sxs-lookup"><span data-stu-id="bfc25-126">This example creates the new columns, ErrorColumn and ErrorMessage.</span></span> <span data-ttu-id="bfc25-127">若要在自己的实现中捕获预定义的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 错误，请确保为错误号添加了 ErrorCode 列。</span><span class="sxs-lookup"><span data-stu-id="bfc25-127">If you are catching predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] errors in your own implementation, make sure to add an ErrorCode column for the error number.</span></span>  
  
10. <span data-ttu-id="bfc25-128">记下脚本组件将查找其错误情况的一个或多个输入列的 ID 值。</span><span class="sxs-lookup"><span data-stu-id="bfc25-128">Note the ID value of the input column or columns that the Script component will check for error conditions.</span></span> <span data-ttu-id="bfc25-129">本示例使用此列标识符填充 ErrorColumn 值。</span><span class="sxs-lookup"><span data-stu-id="bfc25-129">This example uses this column identifier to populate the ErrorColumn value.</span></span>  
  
11. <span data-ttu-id="bfc25-130">关闭“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="bfc25-130">Close the **Script Transformation Editor.**</span></span>  
  
12. <span data-ttu-id="bfc25-131">将脚本组件的输出附加到合适的目标。</span><span class="sxs-lookup"><span data-stu-id="bfc25-131">Attach the outputs of the Script component to suitable destinations.</span></span> <span data-ttu-id="bfc25-132">对于即席测试，平面文件目标是最容易配置的。</span><span class="sxs-lookup"><span data-stu-id="bfc25-132">Flat file destinations are the easiest to configure for ad hoc testing.</span></span>  
  
13. <span data-ttu-id="bfc25-133">运行包。</span><span class="sxs-lookup"><span data-stu-id="bfc25-133">Run the package.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  If Row.CountryRegionName <> "Canada" _  
      And Row.CountryRegionName <> "United States" Then  
  
    Row.ErrorColumn = 68 ' ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America."  
    Row.DirectRowToMyErrorOutput()  
  
  Else  
  
    Row.DirectRowToOutput0()  
  
  End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
{  
  
  if (Row.CountryRegionName!="Canada"&&Row.CountryRegionName!="United States")  
  
  {  
    Row.ErrorColumn = 68; // ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America.";  
    Row.DirectRowToMyErrorOutput();  
  
  }  
  else  
  {  
  
    Row.DirectRowToOutput0();  
  
  }  
  
}  
```  
  
<span data-ttu-id="bfc25-134">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="bfc25-134">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bfc25-135">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="bfc25-135">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bfc25-136">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="bfc25-136">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bfc25-137">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="bfc25-137">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc25-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bfc25-138">See Also</span></span>  
 <span data-ttu-id="bfc25-139">[数据中的错误处理](../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="bfc25-139">[Error Handling in Data](../data-flow/error-handling-in-data.md) </span></span>  
 <span data-ttu-id="bfc25-140">[在数据流组件中使用错误输出](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="bfc25-140">[Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="bfc25-141">使用脚本组件创建同步转换</span><span class="sxs-lookup"><span data-stu-id="bfc25-141">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
