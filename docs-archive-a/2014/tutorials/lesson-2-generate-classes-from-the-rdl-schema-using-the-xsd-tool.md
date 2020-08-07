---
title: 第2课：使用 xsd 工具从 RDL 架构生成类 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2c5db118ad8f94afc72cea44b9a2489f2b4fd7f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690925"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a><span data-ttu-id="362a4-102">第 2 课：使用 XSD 工具从 RDL 架构生成类</span><span class="sxs-lookup"><span data-stu-id="362a4-102">Lesson 2: Generate Classes from the RDL Schema using the xsd Tool</span></span>
  <span data-ttu-id="362a4-103">创建 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 项目后，下一步是检索报表定义架构的本地副本和运行 XML 架构定义工具 (Xsd.exe)。</span><span class="sxs-lookup"><span data-stu-id="362a4-103">After you have created your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project, the next step is to retrieve a local copy of the report definition schema and run the XML Schema Definition Tool (Xsd.exe).</span></span>  
  
### <a name="to-generate-the-rdl-classes"></a><span data-ttu-id="362a4-104">生成 RDL 类</span><span class="sxs-lookup"><span data-stu-id="362a4-104">To generate the RDL classes</span></span>  
  
1.  <span data-ttu-id="362a4-105">打开 [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (或等效 Web 浏览器的实例) 并导航到以下 URL：</span><span class="sxs-lookup"><span data-stu-id="362a4-105">Open an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (or equivalent Web browser) and navigate to the following URL:</span></span>  
  
    ```  
    https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  <span data-ttu-id="362a4-106">在浏览器中打开 RDL 架构后，浏览到 "**文件**" 菜单，然后选择 "**另存为**"。</span><span class="sxs-lookup"><span data-stu-id="362a4-106">Once the RDL schema has been opened in the browser, browse to the **File** menu, and select **Save As**.</span></span>  
  
3.  <span data-ttu-id="362a4-107">浏览到您创建 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 项目的位置，使用文件名 ReportDefinition.xsd 保存该架构。</span><span class="sxs-lookup"><span data-stu-id="362a4-107">Browse to the location where you created your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project and save the schema with the file name ReportDefinition.xsd.</span></span>  
  
4.  <span data-ttu-id="362a4-108">保存文件后，打开 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 命令提示符的实例。</span><span class="sxs-lookup"><span data-stu-id="362a4-108">After the file has been saved, open an instance of the [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] command prompt.</span></span> <span data-ttu-id="362a4-109">若要打开命令提示符的实例，请单击 "开始" 菜单，依次指向 "**所有程序**"、 **Microsoft Visual Studio 2010**"，然后依次指向" **Visual Studio Tools** "和" \*\*Visual Studio 命令提示符 (2010) \*\*"。</span><span class="sxs-lookup"><span data-stu-id="362a4-109">To open an instance of the command prompt, click the Start menu, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools** and click **Visual Studio Command Prompt (2010)**.</span></span>  
  
5.  <span data-ttu-id="362a4-110">将当前路径更改为 ReportDefinition.xsd 文件的保存位置：</span><span class="sxs-lookup"><span data-stu-id="362a4-110">Change the current path to the location where you saved the ReportDefinition.xsd file:</span></span>  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  <span data-ttu-id="362a4-111">用以下命令生成包含 RDL 架构的类的 ReportDefinition.cs 文件：</span><span class="sxs-lookup"><span data-stu-id="362a4-111">Generate the ReportDefinition.cs file that contains the classes for the RDL schema with the following command:</span></span>  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     <span data-ttu-id="362a4-112">若要生成 ReportDefinition.vb 文件，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="362a4-112">To generate a ReportDefinition.vb file use this command:</span></span>  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  <span data-ttu-id="362a4-113">向您的项目添加 ReportDefinition.xsd。</span><span class="sxs-lookup"><span data-stu-id="362a4-113">Add ReportDefinition.xsd your project.</span></span> <span data-ttu-id="362a4-114">从 "**项目**" 菜单中，单击 "**添加现有项**"。</span><span class="sxs-lookup"><span data-stu-id="362a4-114">From the **Project** menu, click **Add Existing Item**.</span></span> <span data-ttu-id="362a4-115">浏览到 Reportdefinition.xsd 文件的位置，选择 Reportdefinition.xsd，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="362a4-115">Browse to the location of the ReportDefinition.xsd file, select ReportDefinition.xsd, and click **Add**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="362a4-116">将 Reportdefinition.xsd 文件添加到项目后，你会注意到**解决方案资源管理器**ReportDefinition.cs ( .vb) 文件不在该项目中。</span><span class="sxs-lookup"><span data-stu-id="362a4-116">After you have added the ReportDefinition.xsd file to the project you will notice in **Solution Explorer** that the ReportDefinition.cs (.vb) file is not there.</span></span> <span data-ttu-id="362a4-117">若要显示该文件，请单击 ReportDefinition.xsd 文件旁边的展开/折叠按钮。</span><span class="sxs-lookup"><span data-stu-id="362a4-117">To display the file, click the expand/collapse button next to the ReportDefinition.xsd file.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="362a4-118">下一课</span><span class="sxs-lookup"><span data-stu-id="362a4-118">Next Lesson</span></span>  
 <span data-ttu-id="362a4-119">在下一课中，您将使用从 RDL 架构生成的类编写用于从报表服务器加载报表定义的代码。</span><span class="sxs-lookup"><span data-stu-id="362a4-119">In the next lesson, you will write code to load a report definition from a report server using the classes you generated from the RDL schema.</span></span> <span data-ttu-id="362a4-120">请参阅[第3课：从报表服务器加载报表定义](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="362a4-120">See [Lesson 3: Load a Report Definition from the Report Server](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="362a4-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="362a4-121">See Also</span></span>  
 <span data-ttu-id="362a4-122">[使用从 RDL 架构生成的类更新报表 &#40;SSRS 教程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="362a4-122">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="362a4-123">报表定义语言 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="362a4-123">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
