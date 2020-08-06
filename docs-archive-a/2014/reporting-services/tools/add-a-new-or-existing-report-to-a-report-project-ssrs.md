---
title: 向报表项目中添加新报表或现有报表 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], creating
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b66bf8ef0181b549900d984d20b1279f9b5005c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692252"
---
# <a name="add-a-new-or-existing-report-to-a-report-project-ssrs"></a><span data-ttu-id="10e04-102">向报表项目中添加新报表或现有报表 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="10e04-102">Add a New or Existing Report to a Report Project (SSRS)</span></span>
  <span data-ttu-id="10e04-103">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，您可以通过使用报表向导或通过将新的空白报表添加到项目中来添加新报表。</span><span class="sxs-lookup"><span data-stu-id="10e04-103">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can add a new report by using the Report Wizard or by adding a new blank report to your project.</span></span> <span data-ttu-id="10e04-104">也可以添加现有报表。</span><span class="sxs-lookup"><span data-stu-id="10e04-104">You can also add an existing report.</span></span> <span data-ttu-id="10e04-105">添加报表后，您可以看到项目 **“报表”** 文件夹下会列出该报表名称。</span><span class="sxs-lookup"><span data-stu-id="10e04-105">After you add a report, you can see the report name listed under the **Reports** folder in your project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10e04-106">若要使用现有数据源预览报表，您必须有权从报表创作客户端访问此数据源。</span><span class="sxs-lookup"><span data-stu-id="10e04-106">To preview a report with existing data sources, you must have permissions to the data source from your report authoring client.</span></span> <span data-ttu-id="10e04-107">有关详细信息，请参阅[&#40;SSRS&#41;创建嵌入数据源或共享数据源](../create-an-embedded-or-shared-data-source-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="10e04-107">For more information, see [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span></span>  
  
 <span data-ttu-id="10e04-108">添加报表后，您可以定义数据源和数据集，并且可以设计报表布局。</span><span class="sxs-lookup"><span data-stu-id="10e04-108">After you add a report, you can define data sources, datasets, and design a report layout.</span></span> <span data-ttu-id="10e04-109">要开始使用，请参阅[创建基本表报表（SSRS 教程）](../create-a-basic-table-report-ssrs-tutorial.md)或[表（报表生成器和 SSRS）](../report-design/tables-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="10e04-109">To get started, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md) or [Tables &#40;Report Builder  and SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-add-a-new-report-using-the-report-wizard"></a><span data-ttu-id="10e04-110">使用报表向导添加新报表</span><span class="sxs-lookup"><span data-stu-id="10e04-110">To add a new report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="10e04-111">在解决方案资源管理器中，右键单击“报表”文件夹，然后单击“添加新报表”  。</span><span class="sxs-lookup"><span data-stu-id="10e04-111">In Solution Explorer, right-click the Reports folder, and then click **Add New Report**.</span></span> <span data-ttu-id="10e04-112">将打开 **“报表向导”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="10e04-112">The **Report Wizard** dialog box opens.</span></span>  
  
     <span data-ttu-id="10e04-113">该向导将指导您逐步完成以下操作：创建数据源，创建带查询的数据集，定义组，指定布局，选择样式（包括颜色和字体）以及创建报表。</span><span class="sxs-lookup"><span data-stu-id="10e04-113">The wizard steps you through creating a data source, creating a dataset with a query, defining groups, specifying a layout, choosing a style that includes color and font, and creating the report.</span></span> <span data-ttu-id="10e04-114">步骤包括：</span><span class="sxs-lookup"><span data-stu-id="10e04-114">The steps include:</span></span>  
  
    -   <span data-ttu-id="10e04-115">**选择数据源。**</span><span class="sxs-lookup"><span data-stu-id="10e04-115">**Select a Data Source.**</span></span> <span data-ttu-id="10e04-116">创建报表的第一步是定义数据源。</span><span class="sxs-lookup"><span data-stu-id="10e04-116">The first step in creating a report is to define a data source.</span></span> <span data-ttu-id="10e04-117">报表向导提供了报表项目中的所有共享数据源的列表，此外还提供了选项，用于创建新数据源。</span><span class="sxs-lookup"><span data-stu-id="10e04-117">Report Wizard provides a list of all shared data sources in the report project, in addition to an option to create a new data source.</span></span>  
  
    -   <span data-ttu-id="10e04-118">**设计查询。**</span><span class="sxs-lookup"><span data-stu-id="10e04-118">**Design a Query.**</span></span> <span data-ttu-id="10e04-119">第二步是设计查询。</span><span class="sxs-lookup"><span data-stu-id="10e04-119">The next step is to design a query.</span></span> <span data-ttu-id="10e04-120">您可以键入查询字符串，然后使用查询设计器生成它，也可以从另一个报表导入一个查询。</span><span class="sxs-lookup"><span data-stu-id="10e04-120">You can type the query string, build it using Query Designer, or import a query from another report.</span></span> <span data-ttu-id="10e04-121">有关查询设计器的信息，请参阅 [Reporting Services Query Designers](../reporting-services-query-designers.md)。</span><span class="sxs-lookup"><span data-stu-id="10e04-121">For information about Query Designers, see [Reporting Services Query Designers](../reporting-services-query-designers.md).</span></span>  
  
    -   <span data-ttu-id="10e04-122">**选择报表类型。**</span><span class="sxs-lookup"><span data-stu-id="10e04-122">**Choose a Report Type.**</span></span> <span data-ttu-id="10e04-123">第三步是选择所需的报表类型。</span><span class="sxs-lookup"><span data-stu-id="10e04-123">The next step is to select the type of report you want.</span></span> <span data-ttu-id="10e04-124">您可以选择表格报表或矩阵报表。</span><span class="sxs-lookup"><span data-stu-id="10e04-124">You can choose a tabular or matrix report.</span></span> <span data-ttu-id="10e04-125">表格报表的列数是固定的。</span><span class="sxs-lookup"><span data-stu-id="10e04-125">A tabular report has a fixed number of columns.</span></span> <span data-ttu-id="10e04-126">而矩阵报表（即交叉表报表）的列数根据查询结果而变化。</span><span class="sxs-lookup"><span data-stu-id="10e04-126">A matrix, or crosstab, report has a variable number of columns based on the results of the query.</span></span> <span data-ttu-id="10e04-127">地图报表在地图背景下显示分析。</span><span class="sxs-lookup"><span data-stu-id="10e04-127">A map report displays analytical against a geographic background.</span></span>  
  
    -   <span data-ttu-id="10e04-128">**选择样式。**</span><span class="sxs-lookup"><span data-stu-id="10e04-128">**Choose a Style.**</span></span> <span data-ttu-id="10e04-129">接下来是使用样式模板将样式应用于报表。</span><span class="sxs-lookup"><span data-stu-id="10e04-129">The next step is to apply a style to the report using a style template.</span></span> <span data-ttu-id="10e04-130">选择一个模板以将样式（如字体、颜色和边框样式）应用于报表。</span><span class="sxs-lookup"><span data-stu-id="10e04-130">Select a template to apply styles such as font, color, and border style to the report.</span></span> <span data-ttu-id="10e04-131">报表设计器提供了六个样式模板：石板、森林、公司、粗体、海洋和一般。</span><span class="sxs-lookup"><span data-stu-id="10e04-131">Report Designer provides six style templates: Slate, Forest, Corporate, Bold, Ocean, and Generic.</span></span> <span data-ttu-id="10e04-132">您还可以添加其他样式模板。</span><span class="sxs-lookup"><span data-stu-id="10e04-132">You can also add additional style templates.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="10e04-133">你可以通过编辑 \Program Files\Microsoft Visual Studio 10.0 \ Common7\IDE\PrivateAssemblies\Business 智能 Wizards\Reports\Styles<lang 文件夹中的 StyleTemplates.xml 文件来更改现有模板或添加新模板 \\ \> ，其中 \<lang> 是你使用的语言 (例如，如果你使用的是英语版本的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，则该文件夹名称为 "EN" ) 。</span><span class="sxs-lookup"><span data-stu-id="10e04-133">You can alter existing templates or add new ones by editing the StyleTemplates.xml file in the \Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\<lang\> folder, where \<lang> is the language you are using (for example, if you are using the English language version of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], the folder name is "EN").</span></span> <span data-ttu-id="10e04-134">该文件夹位于安装报表设计器的计算机上。</span><span class="sxs-lookup"><span data-stu-id="10e04-134">This folder is located on the computer on which Report Designer is installed.</span></span> <span data-ttu-id="10e04-135">StyleTemplates.xml 文件有两个副本。</span><span class="sxs-lookup"><span data-stu-id="10e04-135">There are two copies of the StyleTemplates.xml file.</span></span> <span data-ttu-id="10e04-136">若要修改通过报表向导所应用的样式，请编辑针对您所用语言创建的上述文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="10e04-136">To modify the styles that are applied through the Report Wizard, edit the file that is in the folder created for the language you are using.</span></span>  
  
    -   <span data-ttu-id="10e04-137">**为报表命名。**</span><span class="sxs-lookup"><span data-stu-id="10e04-137">**Name the Report.**</span></span>  <span data-ttu-id="10e04-138">最后一步是为报表命名并验证报表中将要包含的各个字段。</span><span class="sxs-lookup"><span data-stu-id="10e04-138">The final step is to name the report and verify the fields that will be included in the report.</span></span> <span data-ttu-id="10e04-139">完成所有步骤之后，报表设计器将创建报表，并将其添加到报表服务器项目。</span><span class="sxs-lookup"><span data-stu-id="10e04-139">When all steps are completed, Report Designer creates the report and adds it to the report server project.</span></span>  
  
### <a name="to-add-a-new-blank-report"></a><span data-ttu-id="10e04-140">添加新的空白报表</span><span class="sxs-lookup"><span data-stu-id="10e04-140">To add a new blank report</span></span>  
  
1.  <span data-ttu-id="10e04-141">在 **“项目”** 菜单上单击 **“添加新项”**。</span><span class="sxs-lookup"><span data-stu-id="10e04-141">From the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="10e04-142">在 **“模板”** 上单击 **“报表”**。</span><span class="sxs-lookup"><span data-stu-id="10e04-142">In **Templates**, click **Report**.</span></span>  
  
3.  <span data-ttu-id="10e04-143">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="10e04-143">Click **Add**.</span></span>  
  
     <span data-ttu-id="10e04-144">一个新的空白报表随即添加到项目中并显示在设计图面上。</span><span class="sxs-lookup"><span data-stu-id="10e04-144">A new blank report is added to the project and displayed on the design surface.</span></span>  
  
### <a name="to-add-an-existing-report"></a><span data-ttu-id="10e04-145">添加现有报表</span><span class="sxs-lookup"><span data-stu-id="10e04-145">To add an existing report</span></span>  
  
1.  <span data-ttu-id="10e04-146">从 "**项目**" 菜单中，单击 "**添加**"，然后单击 "**现有项**"。</span><span class="sxs-lookup"><span data-stu-id="10e04-146">From the **Project** menu, click **Add**, and then **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="10e04-147">浏览到 .rdl 文件所在的位置并选择它，然后单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="10e04-147">Navigate to the location of the .rdl file, select it, and then click **Add**.</span></span>  
  
     <span data-ttu-id="10e04-148">该报表随即添加到项目的 **“报表”** 文件夹下。</span><span class="sxs-lookup"><span data-stu-id="10e04-148">The report is added to the project under the **Reports** folder.</span></span> <span data-ttu-id="10e04-149">关闭并重新打开项目后，报表将按字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="10e04-149">When you close and re-open the project, reports are sorted alphabetically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e04-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10e04-150">See Also</span></span>  
 [<span data-ttu-id="10e04-151">Reporting Services 教程 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="10e04-151">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
