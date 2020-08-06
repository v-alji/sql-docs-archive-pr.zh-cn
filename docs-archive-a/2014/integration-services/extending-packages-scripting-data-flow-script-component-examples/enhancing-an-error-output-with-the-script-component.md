---
title: 使用脚本组件增强错误输出 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18637aa1e147ce989645ae859681929f4d0c438a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590924"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a><span data-ttu-id="66126-102">使用脚本组件增强错误输出</span><span class="sxs-lookup"><span data-stu-id="66126-102">Enhancing an Error Output with the Script Component</span></span>
  <span data-ttu-id="66126-103">默认情况下，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 错误输出中的另外两列 ErrorCode 和 ErrorColumn 只包含表示错误号的数值代码以及出现错误的列的 ID。</span><span class="sxs-lookup"><span data-stu-id="66126-103">By default, the two extra columns in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error output, ErrorCode and ErrorColumn, contain only numeric codes that represent an error number, and the ID of the column in which the error occurred.</span></span> <span data-ttu-id="66126-104">如果没有相应的错误说明，这些数值没有多大用处。</span><span class="sxs-lookup"><span data-stu-id="66126-104">These numeric values may be of limited use without the corresponding error description.</span></span>  
  
 <span data-ttu-id="66126-105">本主题介绍如何使用脚本组件向数据流中的现有错误输出数据中添加错误说明列。</span><span class="sxs-lookup"><span data-stu-id="66126-105">This topic describes how to add an error description column to existing error output data in the data flow by using the Script component.</span></span> <span data-ttu-id="66126-106">示例使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 接口的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 方法添加与特定预定义 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 错误代码对应的错误说明，该接口通过脚本组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 属性提供。</span><span class="sxs-lookup"><span data-stu-id="66126-106">The example adds the error description that corresponds to a specific predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error code by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the Script component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66126-107">如果希望创建可更方便地重用于多个数据流任务和多个包的组件，请考虑以此脚本组件示例中的代码为基础，创建自定义数据流组件。</span><span class="sxs-lookup"><span data-stu-id="66126-107">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="66126-108">有关详细信息，请参阅 [开发自定义数据流组件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="66126-108">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66126-109">示例</span><span class="sxs-lookup"><span data-stu-id="66126-109">Example</span></span>  
 <span data-ttu-id="66126-110">下面显示的示例使用一个配置为转换的脚本组件向数据流中的现有错误输出数据中添加错误说明列。</span><span class="sxs-lookup"><span data-stu-id="66126-110">The example shown here uses a Script component configured as a transformation to add an error description column to existing error output data in the data flow.</span></span>  
  
 <span data-ttu-id="66126-111">有关如何配置脚本组件以用作数据流中的转换的详细信息，请参阅[使用脚本组件创建同步转换](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)和[使用脚本组件创建异步转换](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="66126-111">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="66126-112">配置此脚本组件示例</span><span class="sxs-lookup"><span data-stu-id="66126-112">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="66126-113">创建新脚本组件之前，先配置数据流中的上游组件，以便在错误或截断出现时将行重定向到上游组件的错误输出。</span><span class="sxs-lookup"><span data-stu-id="66126-113">Before creating the new Script component, configure an upstream component in the data flow to redirect rows to its error output when an error or truncation occurs.</span></span> <span data-ttu-id="66126-114">出于测试目的，可能希望以确保将发生错误的方式来配置组件，例如，在两个将发生查找失败的表之间配置一个查找转换。</span><span class="sxs-lookup"><span data-stu-id="66126-114">For testing purposes, you may want to configure a component in a manner that ensures that errors will occur-for example, by configuring a Lookup transformation between two tables where the lookup will fail.</span></span>  
  
2.  <span data-ttu-id="66126-115">向数据流设计器图面添加新的脚本组件并将其配置为转换。</span><span class="sxs-lookup"><span data-stu-id="66126-115">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>  
  
3.  <span data-ttu-id="66126-116">将错误输出从上游组件连接到新脚本组件。</span><span class="sxs-lookup"><span data-stu-id="66126-116">Connect the error output from the upstream component to the new Script component.</span></span>  
  
4.  <span data-ttu-id="66126-117">打开“脚本转换编辑器”\*\*\*\*，在“脚本”\*\*\*\* 页中，为 **ScriptLanguage** 属性选择脚本语言。</span><span class="sxs-lookup"><span data-stu-id="66126-117">Open the **Script Transformation Editor**, and on the **Script** page, for the **ScriptLanguage** property, select the script language.</span></span>  
  
5.  <span data-ttu-id="66126-118">单击“编辑脚本”打开 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE，并添加下面的示例代码\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66126-118">Click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE and add the sample code shown below.</span></span>  
  
6.  <span data-ttu-id="66126-119">关闭 VSTA。</span><span class="sxs-lookup"><span data-stu-id="66126-119">Close VSTA.</span></span>  
  
7.  <span data-ttu-id="66126-120">在 "脚本转换编辑器" 的 "**输入列**" 页中，选择 ErrorCode 列。</span><span class="sxs-lookup"><span data-stu-id="66126-120">In the Script Transformation Editor, on the **Input Columns** page, select the ErrorCode column.</span></span>  
  
8.  <span data-ttu-id="66126-121">在 "**输入和输出**" 页中，添加 `String` 名为**ErrorDescription**的类型的新输出列。</span><span class="sxs-lookup"><span data-stu-id="66126-121">On the **Inputs and Outputs** page, add a new output column of type `String` named **ErrorDescription**.</span></span> <span data-ttu-id="66126-122">将新列的默认长度提高到 255 以支持长消息。</span><span class="sxs-lookup"><span data-stu-id="66126-122">Increase the default length of the new column to 255 to support long messages.</span></span>  
  
9. <span data-ttu-id="66126-123">关闭“脚本转换编辑器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66126-123">Close the **Script Transformation Editor.**</span></span>  
  
10. <span data-ttu-id="66126-124">将脚本组件的输出附加到合适的目标。</span><span class="sxs-lookup"><span data-stu-id="66126-124">Attach the output of the Script component to a suitable destination.</span></span> <span data-ttu-id="66126-125">对于即席测试，平面文件目标是最容易配置的。</span><span class="sxs-lookup"><span data-stu-id="66126-125">A Flat File destination is the easiest to configure for ad hoc testing.</span></span>  
  
11. <span data-ttu-id="66126-126">运行包。</span><span class="sxs-lookup"><span data-stu-id="66126-126">Run the package.</span></span>  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  Row.ErrorDescription = _  
    Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
  Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
    }  
}  
  
```  
  
<span data-ttu-id="66126-127">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="66126-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="66126-128">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="66126-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="66126-129">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="66126-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="66126-130">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="66126-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66126-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66126-131">See Also</span></span>  
 <span data-ttu-id="66126-132">[数据中的错误处理](../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="66126-132">[Error Handling in Data](../data-flow/error-handling-in-data.md) </span></span>  
 <span data-ttu-id="66126-133">[在数据流组件中使用错误输出](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="66126-133">[Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="66126-134">使用脚本组件创建同步转换</span><span class="sxs-lookup"><span data-stu-id="66126-134">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
