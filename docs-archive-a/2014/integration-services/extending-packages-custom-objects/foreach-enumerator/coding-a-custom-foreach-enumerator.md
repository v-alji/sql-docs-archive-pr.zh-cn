---
title: 编写自定义 Foreach 枚举器代码 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services], coding
ms.assetid: 279cf6de-d06f-40e7-b8ca-569310449f36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2b7e6c16124f4682dbdc98f602417bf8f68ce099
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579648"
---
# <a name="coding-a-custom-foreach-enumerator"></a><span data-ttu-id="513a5-102">编写自定义 Foreach 枚举器代码</span><span class="sxs-lookup"><span data-stu-id="513a5-102">Coding a Custom Foreach Enumerator</span></span>
  <span data-ttu-id="513a5-103">创建继承自 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 基类的类并将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 属性应用于该类后，必须重写基类的属性和方法的实现以提供自定义功能。</span><span class="sxs-lookup"><span data-stu-id="513a5-103">After you have created a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>  
  
 <span data-ttu-id="513a5-104">若要查看自定义枚举器的工作示例，请参阅[为自定义 ForEach 枚举器开发用户界面](developing-a-user-interface-for-a-custom-foreach-enumerator.md)。</span><span class="sxs-lookup"><span data-stu-id="513a5-104">For a working sample of a custom enumerator, see [Developing a User Interface for a Custom ForEach Enumerator](developing-a-user-interface-for-a-custom-foreach-enumerator.md).</span></span>  
  
## <a name="initializing-the-enumerator"></a><span data-ttu-id="513a5-105">初始化枚举器</span><span class="sxs-lookup"><span data-stu-id="513a5-105">Initializing the Enumerator</span></span>  
 <span data-ttu-id="513a5-106">可以重写 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.InitializeForEachEnumerator%2A> 方法以缓存对包中定义的连接管理器的引用，和缓存对事件接口（用于引发错误、警告和信息性消息）的引用。</span><span class="sxs-lookup"><span data-stu-id="513a5-106">You can override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.InitializeForEachEnumerator%2A> method to cache references to the connection managers defined in the package, and to cache references to the events interface that you can use to raise errors, warnings, and informational messages.</span></span>  
  
## <a name="validating-the-enumerator"></a><span data-ttu-id="513a5-107">验证枚举器</span><span class="sxs-lookup"><span data-stu-id="513a5-107">Validating the Enumerator</span></span>  
 <span data-ttu-id="513a5-108">重写 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> 方法以验证枚举器是否正确配置。</span><span class="sxs-lookup"><span data-stu-id="513a5-108">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> method to verify that the enumerator is correctly configured.</span></span> <span data-ttu-id="513a5-109">如果该方法返回 `Failure`，则枚举器和包含枚举器的包将不执行。</span><span class="sxs-lookup"><span data-stu-id="513a5-109">If the method returns `Failure`, the enumerator and the package that contains the enumerator will not be executed.</span></span> <span data-ttu-id="513a5-110">此方法的实现是特定于每个枚举器的，但如果枚举器依赖于 <xref:Microsoft.SqlServer.Dts.Runtime.Variable> 或 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 对象，则应该添加代码以验证这些对象存在于提供给方法的集合中。</span><span class="sxs-lookup"><span data-stu-id="513a5-110">The implementation of this method is specific to each enumerator, but if the enumerator relies on <xref:Microsoft.SqlServer.Dts.Runtime.Variable> or <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects, you should add code to verify that these objects exist in the collections that are provided to the method.</span></span>  
  
 <span data-ttu-id="513a5-111">下面的代码示例演示 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> 的实现，该接口用于检查在枚举器的属性中指定的变量。</span><span class="sxs-lookup"><span data-stu-id="513a5-111">The following code example demonstrates an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> that checks for a variable specified in a property of the enumerator.</span></span>  
  
```csharp  
private string variableNameValue;  
  
public string VariableName  
{  
    get{ return this.variableNameValue; }  
    set{ this.variableNameValue = value; }  
}  
  
public override DTSExecResult Validate(Connections connections, VariableDispenser variableDispenser, IDTSInfoEvents infoEvents, IDTSLogging log)  
{  
    if (!variableDispenser.Contains(this.variableNameValue))  
    {  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + this.variableNameValue + " does not exist in the collection.", "", 0);  
            return DTSExecResult.Failure;  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Private variableNameValue As String  
  
Public Property VariableName() As String  
    Get   
         Return Me.variableNameValue  
    End Get  
    Set (ByVal Value As String)   
         Me.variableNameValue = value  
    End Set  
End Property  
  
Public Overrides Function Validate(ByVal connections As Connections, ByVal variableDispenser As VariableDispenser, ByVal infoEvents As IDTSInfoEvents, ByVal log As IDTSLogging) As DTSExecResult  
    If Not variableDispenser.Contains(Me.variableNameValue) Then  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + Me.variableNameValue + " does not exist in the collection.", "", 0)  
            Return DTSExecResult.Failure  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
## <a name="returning-the-collection"></a><span data-ttu-id="513a5-112">返回集合</span><span class="sxs-lookup"><span data-stu-id="513a5-112">Returning the Collection</span></span>  
 <span data-ttu-id="513a5-113">在执行期间，<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 容器调用自定义枚举器的 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="513a5-113">During execution, the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container calls the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method of the custom enumerator.</span></span> <span data-ttu-id="513a5-114">在此方法中，枚举器创建并填充它的项集合，然后返回该集合。</span><span class="sxs-lookup"><span data-stu-id="513a5-114">In this method, the enumerator creates and populates its collection of items, and then returns the collection.</span></span> <span data-ttu-id="513a5-115">然后 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 遍历集合中的所有项，并为集合中的每个项执行控制流。</span><span class="sxs-lookup"><span data-stu-id="513a5-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> then iterates the items in the collection, and executes its control flow for each item in the collection.</span></span>  
  
 <span data-ttu-id="513a5-116">下面的示例演示返回随机整数数组的 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 的实现。</span><span class="sxs-lookup"><span data-stu-id="513a5-116">The following example shows an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> that returns an array of random integers.</span></span>  
  
```csharp  
public override object GetEnumerator()  
{  
    ArrayList numbers = new ArrayList();  
  
    Random randomNumber = new Random(DateTime.Now);  
  
    for( int x=0; x < 100; x++ )  
        numbers.Add( randomNumber.Next());  
  
    return numbers;  
}  
```  
  
```vb  
Public Overrides Function GetEnumerator() As Object  
    Dim numbers As ArrayList =  New ArrayList()   
  
    Dim randomNumber As Random =  New Random(DateTime.Now)   
  
        Dim x As Integer  
        For  x = 0 To  100- 1  Step  x + 1  
        numbers.Add(randomNumber.Next())  
        Next  
  
    Return numbers  
End Function  
```  
  
<span data-ttu-id="513a5-117">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="513a5-117">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="513a5-118">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="513a5-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="513a5-119">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="513a5-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="513a5-120">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="513a5-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="513a5-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="513a5-121">See Also</span></span>  
 <span data-ttu-id="513a5-122">[创建自定义 Foreach 枚举器](creating-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="513a5-122">[Creating a Custom Foreach Enumerator](creating-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="513a5-123">为自定义 ForEach 枚举器开发用户界面</span><span class="sxs-lookup"><span data-stu-id="513a5-123">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
