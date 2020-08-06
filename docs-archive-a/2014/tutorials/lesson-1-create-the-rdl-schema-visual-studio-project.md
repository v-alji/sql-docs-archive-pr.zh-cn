---
title: 第1课：创建 RDL 架构 Visual Studio 项目 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f420509c-51aa-4170-8c25-64c2954f4bb9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a8411e3f0458ccda8c291d5c86a4467bb051a263
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682473"
---
# <a name="lesson-1-create-the-rdl-schema-visual-studio-project"></a><span data-ttu-id="b7b9b-102">第 1 课：创建 RDL 架构 Visual Studio 项目</span><span class="sxs-lookup"><span data-stu-id="b7b9b-102">Lesson 1: Create the RDL Schema Visual Studio Project</span></span>
  <span data-ttu-id="b7b9b-103">针对本教程，您将创建一个简单控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-103">For this tutorial, you will create a simple console application.</span></span> <span data-ttu-id="b7b9b-104">本教程假定你在中进行开发 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-104">This tutorial assumes you are developing in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7b9b-105">访问在具有高级服务的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] 上运行的报表服务器 Web 服务时，必须将“_SQLExpress”追加到“ReportServer”路径。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-105">When accessing the Report Server Web service running on [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services, you must append "_SQLExpress" to the "ReportServer" path.</span></span> <span data-ttu-id="b7b9b-106">例如：</span><span class="sxs-lookup"><span data-stu-id="b7b9b-106">For example:</span></span>  
>   
>  `http://myserver/reportserver_sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-create-the-web-service-proxy"></a><span data-ttu-id="b7b9b-107">创建 Web 服务代理</span><span class="sxs-lookup"><span data-stu-id="b7b9b-107">To create the web service proxy</span></span>  
  
1.  <span data-ttu-id="b7b9b-108">从 "**开始**" 菜单中选择 "**所有程序**"，然后 Microsoft Visual Studio "，然后**Visual Studio Tools**，然后选择" **Visual Studio 2010 命令提示符**"。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-108">From the **Start** menu, select **All Programs**, then Microsoft Visual Studio, then **Visual Studio Tools**, and then **Visual Studio 2010 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="b7b9b-109">在命令提示符窗口中，如果您使用 C#，则运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b7b9b-109">In the command prompt window, run the following command if you are using C#:</span></span>  
  
    ```  
    wsdl /language:CS /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="b7b9b-110">如果您使用 Visual Basic，则运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b7b9b-110">If you are using Visual Basic, then run the following command:</span></span>  
  
    ```  
    wsdl /language:VB /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="b7b9b-111">此命令将生成一个 .cs 或 .vb 文件。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-111">This command generates a .cs or .vb file.</span></span> <span data-ttu-id="b7b9b-112">您将把该文件添加到您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-112">You will add this file to your application.</span></span>  
  
### <a name="to-create-a-console-application"></a><span data-ttu-id="b7b9b-113">创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="b7b9b-113">To create a console application</span></span>  
  
1.  <span data-ttu-id="b7b9b-114">在“文件”\*\*\*\* 菜单上指向“新建”\*\*\*\*，然后单击“项目”\*\*\*\* 打开“新建项目”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-114">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="b7b9b-115">在左窗格中的 "**已安装的模板**" 下，单击 " **Visual Basic** " 或 " **Visual c #** " 节点，然后从展开的列表中选择一类项目类型。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-115">In the left pane, under **Installed Templates**, click either **Visual Basic** or the **Visual C#** node, and select a category of project types from the expanded list.</span></span>  
  
3.  <span data-ttu-id="b7b9b-116">选择 "**控制台应用程序**" 项目类型。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-116">Choose the **Console Application** project type.</span></span>  
  
4.  <span data-ttu-id="b7b9b-117">在 "**名称**" 框中，输入项目的名称。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-117">In the **Name** box, enter a name for your project.</span></span> <span data-ttu-id="b7b9b-118">键入名称 `SampleRDLSchema` 。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-118">Type the name `SampleRDLSchema`.</span></span>  
  
5.  <span data-ttu-id="b7b9b-119">在 "**位置**" 框中，键入要保存项目的路径，或单击 "**浏览**" 导航到该文件夹。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-119">In the **Location** box, type the path where you want to save your project, or click **Browse** to navigate to the folder.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="b7b9b-120">项目的折叠视图以解决方案资源管理器显示。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-120">A collapsed view of your project appears in Solution Explorer.</span></span>  
  
7.  <span data-ttu-id="b7b9b-121">在“项目”\*\*\*\* 菜单上，单击“添加现有项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-121">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
8.  <span data-ttu-id="b7b9b-122">导航到生成的 .cs 或 .vb 文件的位置，选择该文件，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-122">Navigate to the location for the .cs or .vb file you generated, then select the file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="b7b9b-123">您还需要添加对 <xref:System.Web.Services> 命名空间的引用，Web 引用才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-123">You will also need to add a reference to the <xref:System.Web.Services> namespace for your Web reference to work.</span></span>  
  
9. <span data-ttu-id="b7b9b-124">在 "项目" 菜单上，单击 "**添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-124">On the Project menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="b7b9b-125">在 "**添加引用**" 对话框的 " **.net** " 选项卡中，选择 " **System.web**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-125">In the **Add Reference** dialog box, in the **.NET** tab, select **System.Web.Services**, then click **OK**.</span></span>  
  
     <span data-ttu-id="b7b9b-126">有关如何连接到报表服务器 Web 服务的详细信息，请参阅[使用 Web 服务构建应用程序和 .NET Framework](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-126">For more information about how to connect to the Report Server Web service, see [Building Applications Using the Web Service and the .NET Framework](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
10. <span data-ttu-id="b7b9b-127">在解决方案资源管理器中，展开该项目节点。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-127">In Solution Explorer, expand the project node.</span></span> <span data-ttu-id="b7b9b-128">您将看到默认名称为 Program.cs（对于 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]，为 Module1.vb）的代码文件已添加到您的项目中。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-128">You will see a code file with the default name of Program.cs (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) has been added to your project.</span></span>  
  
11. <span data-ttu-id="b7b9b-129">打开 Program.cs（对于 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]，为 Module1.vb）文件，并使用以下内容替换该代码：</span><span class="sxs-lookup"><span data-stu-id="b7b9b-129">Open the Program.cs (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) file and replace the code with the following:</span></span>  
  
     <span data-ttu-id="b7b9b-130">以下代码提供了将用于实现加载、更新和保存功能的方法存根 (Stub)。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-130">The following code provides the method stubs we will use to implement the Load, Update and Save functionality.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using ReportService2010;  
  
    namespace SampleRDLSchema  
    {  
        class ReportUpdater  
        {  
            ReportingService2010 _reportService;  
  
            static void Main(string[] args)  
            {  
                ReportUpdater reportUpdater = new ReportUpdater();  
                reportUpdater.UpdateReport();  
            }  
  
            private void UpdateReport()  
            {  
                try  
                {  
                    // Set up the Report Service connection  
                    _reportService = new ReportingService2010();  
                    _reportService.Credentials =  
                        System.Net.CredentialCache.DefaultCredentials;  
                    _reportService.Url =  
                       "http://<Server Name>/reportserver/" +  
                                       "reportservice2010.asmx";  
  
                    // Call the methods to update a report definition  
                    LoadReportDefinition();  
                    UpdateReportDefinition();  
                    PublishReportDefinition();  
                }  
                catch (Exception ex)  
                {  
                    System.Console.WriteLine(ex.Message);  
                }  
            }  
  
            private void LoadReportDefinition()  
            {  
                //Lesson 3: Load a report definition from the report   
                //          catalog  
            }  
  
            private void UpdateReportDefinition()  
            {  
                //Lesson 4: Update the report definition using the    
                //          classes generated from the RDL Schema  
            }  
  
            private void PublishReportDefinition()  
            {  
                //Lesson 5: Publish the updated report definition back   
                //          to the report catalog  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports ReportService2010  
  
    Namespace SampleRDLSchema  
  
        Module ReportUpdater  
  
            Private m_reportService As ReportingService2010  
  
            Public Sub Main(ByVal args As String())  
  
                Try  
                    'Set up the Report Service connection  
                    m_reportService = New ReportingService2010  
                    m_reportService.Credentials = _  
                        System.Net.CredentialCache.DefaultCredentials  
                    m_reportService.Url = _  
                        "http:// <Server Name>/reportserver/" & _  
                               "reportservice2010.asmx"  
  
                    'Call the methods to update a report definition  
                    LoadReportDefinition()  
                    UpdateReportDefinition()  
                    PublishReportDefinition()  
                Catch ex As Exception  
                    System.Console.WriteLine(ex.Message)  
                End Try  
  
            End Sub  
  
            Private Sub LoadReportDefinition()  
                'Lesson 3: Load a report definition from the report   
                '          catalog  
            End Sub  
  
            Private Sub UpdateReportDefinition()  
                'Lesson 4: Update the report definition using the   
                '          classes generated from the RDL Schema  
            End Sub  
  
            Private Sub PublishReportDefinition()  
                'Lesson 5: Publish the updated report definition back   
                '          to the report catalog  
            End Sub  
  
        End Module  
  
    End Namespace   
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="b7b9b-131">下一课</span><span class="sxs-lookup"><span data-stu-id="b7b9b-131">Next Lesson</span></span>  
 <span data-ttu-id="b7b9b-132">在下一课中，您将使用 XML 架构定义工具 (Xsd.exe) 从 RDL 架构中生成类，并将其包含在项目中。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-132">In the next lesson, you will use the XML Schema Definition Tool (Xsd.exe) to generate classes from the RDL schema and include them in your project.</span></span> <span data-ttu-id="b7b9b-133">请参阅[第2课：使用 Xsd 工具从 RDL 架构生成类](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="b7b9b-133">See [Lesson 2: Generate Classes from the RDL Schema using the xsd Tool](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b9b-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7b9b-134">See Also</span></span>  
 <span data-ttu-id="b7b9b-135">[使用从 RDL 架构生成的类更新报表 &#40;SSRS 教程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="b7b9b-135">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="b7b9b-136">报表定义语言 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b7b9b-136">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
