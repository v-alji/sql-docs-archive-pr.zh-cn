---
title: 使用脚本任务查询 Active Directory | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 624aa56289b9cab9174882b586a37e5d0de7ca9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578359"
---
# <a name="querying-the-active-directory-with-the-script-task"></a><span data-ttu-id="0651f-102">使用脚本任务查询 Active Directory</span><span class="sxs-lookup"><span data-stu-id="0651f-102">Querying the Active Directory with the Script Task</span></span>
  <span data-ttu-id="0651f-103">企业数据处理应用程序（如 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包）通常需要根据 Active Directory 中存储的雇员的级别、职务或其他特征来以不同方式处理数据。</span><span class="sxs-lookup"><span data-stu-id="0651f-103">Enterprise data processing applications, such as [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, often need to process data differently based on the rank, job title, or other characteristics of employees stored in Active Directory.</span></span> <span data-ttu-id="0651f-104">Active Directory 是一个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 目录服务，它不仅提供集中存储有关用户的元数据，还可以提供集中存储有关其他组织资产（如计算机和打印机）的元数据。</span><span class="sxs-lookup"><span data-stu-id="0651f-104">Active Directory is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows directory service that provides a centralized store of metadata, not only about users, but also about other organizational assets such as computers and printers.</span></span> <span data-ttu-id="0651f-105">Microsoft .NET Framework 中的 `System.DirectoryServices` 命名空间提供使用 Active Directory 的类，以帮助您根据 Active Directory 中存储的信息来定向数据处理工作流。</span><span class="sxs-lookup"><span data-stu-id="0651f-105">The `System.DirectoryServices` namespace in the Microsoft .NET Framework provides classes for working with Active Directory, to help you direct data processing workflow based on the information that it stores.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0651f-106">如果希望创建可更方便地重用于多个包的任务，请考虑以此脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="0651f-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="0651f-107">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="0651f-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="0651f-108">说明</span><span class="sxs-lookup"><span data-stu-id="0651f-108">Description</span></span>  
 <span data-ttu-id="0651f-109">下面的示例基于 `email` 变量的值（包含雇员的电子邮件地址），从 Active Directory 检索雇员的姓名、职务和电话号码。</span><span class="sxs-lookup"><span data-stu-id="0651f-109">The following example retrieves an employee's name, title, and phone number from Active Directory based on the value of the `email` variable, which contains the e-mail address of the employee.</span></span> <span data-ttu-id="0651f-110">包中的优先约束可使用检索到的信息，例如基于雇员的职务来确定发送具有低优先级的电子邮件消息，还是具有高优先级的页。</span><span class="sxs-lookup"><span data-stu-id="0651f-110">Precedence constraints in the package can use the retrieved information to determine, for example, whether to send a low-priority e-mail message or a high-priority page, based on the job title of the employee.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="0651f-111">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="0651f-111">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="0651f-112">创建三个字符串变量：`email`、`name` 和 `title`。</span><span class="sxs-lookup"><span data-stu-id="0651f-112">Create the three string variables `email`, `name`, and `title`.</span></span> <span data-ttu-id="0651f-113">输入一个有效的企业电子邮件地址作为 `email` 变量的值。</span><span class="sxs-lookup"><span data-stu-id="0651f-113">Enter a valid corporate email address as the value of the `email` variable.</span></span>  
  
2.  <span data-ttu-id="0651f-114">在 "**脚本任务编辑器**" 的 "**脚本**" 页中，将 `email` 变量添加到属性中 `ReadOnlyVariables` 。</span><span class="sxs-lookup"><span data-stu-id="0651f-114">On the **Script** page of the **Script Task Editor**, add the `email` variable to the `ReadOnlyVariables` property.</span></span>  
  
3.  <span data-ttu-id="0651f-115">将 `name` 和 `title` 变量添加到 `ReadWriteVariables` 属性中。</span><span class="sxs-lookup"><span data-stu-id="0651f-115">Add the `name` and `title` variables to the `ReadWriteVariables` property.</span></span>  
  
4.  <span data-ttu-id="0651f-116">在脚本项目中，添加对 `System.DirectoryServices` 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="0651f-116">In the script project, add a reference to the `System.DirectoryServices` namespace.</span></span>  
  
5.  <span data-ttu-id="0651f-117">。</span><span class="sxs-lookup"><span data-stu-id="0651f-117">.</span></span> <span data-ttu-id="0651f-118">在您的代码中，使用 `Imports` 语句导入 `DirectoryServices` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="0651f-118">In your code, use an `Imports` statement to import the `DirectoryServices` namespace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0651f-119">若要成功运行此脚本，您的企业必须在其网络中使用 Active Directory，并在其中存储此示例使用的雇员信息。</span><span class="sxs-lookup"><span data-stu-id="0651f-119">To run this script successfully, your company must be using Active Directory on its network and storing the employee information that this example uses.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0651f-120">代码</span><span class="sxs-lookup"><span data-stu-id="0651f-120">Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="0651f-121">外部资源</span><span class="sxs-lookup"><span data-stu-id="0651f-121">External Resources</span></span>  
  
-   <span data-ttu-id="0651f-122">social.technet.microsoft.com 上的技术文章，[在 SSIS 中处理 Active Directory 信息](https://go.microsoft.com/fwlink/?LinkId=199588)。</span><span class="sxs-lookup"><span data-stu-id="0651f-122">Technical article, [Processing Active Directory Information in SSIS](https://go.microsoft.com/fwlink/?LinkId=199588), on social.technet.microsoft.com</span></span>  
  
<span data-ttu-id="0651f-123">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="0651f-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="0651f-124">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="0651f-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="0651f-125">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="0651f-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="0651f-126">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="0651f-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
