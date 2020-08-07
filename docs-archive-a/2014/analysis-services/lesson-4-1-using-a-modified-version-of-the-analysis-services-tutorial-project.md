---
title: 使用 Analysis Services 教程项目的修改版本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 685aa217-de1b-4df2-bf22-095228c40775
author: minewiskan
ms.author: owend
ms.openlocfilehash: b833a05a567f37443cf89f7356a0855e0827ea73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588123"
---
# <a name="using-a-modified-version-of-the-analysis-services-tutorial-project"></a><span data-ttu-id="06ad4-102">使用 Analysis Services Tutorial 项目的修改版本</span><span class="sxs-lookup"><span data-stu-id="06ad4-102">Using a Modified Version of the Analysis Services Tutorial Project</span></span>
  <span data-ttu-id="06ad4-103">本教程中的其余几节课基于您已在前三课中完成的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目的增强版本。</span><span class="sxs-lookup"><span data-stu-id="06ad4-103">The remaining lessons in this tutorial are based on an enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons.</span></span> <span data-ttu-id="06ad4-104">已向 \*\*Adventure Works DW 2012[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据源视图中添加了额外的表和命名计算；已向该项目添加了额外的维度，并且已将这些新维度添加到 \*\* Tutorial 多维数据集内。</span><span class="sxs-lookup"><span data-stu-id="06ad4-104">Additional tables and named calculations have been added to the **Adventure Works DW 2012** data source view, additional dimensions have been added to the project, and these new dimensions have been added to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="06ad4-105">此外，还添加了另一个度量值组，该组包含另一个事实数据表中的度量值。</span><span class="sxs-lookup"><span data-stu-id="06ad4-105">In addition, a second measure group has been added, which contains measures from a second fact table.</span></span> <span data-ttu-id="06ad4-106">这一增强项目使您无需重复学习前面已了解的技能，即可继续学习如何在商业智能应用程序中添加功能。</span><span class="sxs-lookup"><span data-stu-id="06ad4-106">This enhanced project will enable you to continue learning how to add functionality to your business intelligence application without having to repeat the skills you have already learned.</span></span>  
  
 <span data-ttu-id="06ad4-107">在继续本教程之前，必须下载、解压缩、加载和处理 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目的增强版本。</span><span class="sxs-lookup"><span data-stu-id="06ad4-107">Before you can continue with the tutorial, you must download, extract, load and process the enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span>  <span data-ttu-id="06ad4-108">请使用本课程中的说明以确保您已执行了所有步骤。</span><span class="sxs-lookup"><span data-stu-id="06ad4-108">Use the instructions in this lesson to ensure you have performed all the steps.</span></span>  
  
## <a name="downloading-and-extracting-the-project-file"></a><span data-ttu-id="06ad4-109">下载并解压缩项目文件</span><span class="sxs-lookup"><span data-stu-id="06ad4-109">Downloading and Extracting the Project File</span></span>  
  
1.  <span data-ttu-id="06ad4-110">[单击此处](https://go.microsoft.com/fwlink/?LinkID=221866) 可以转到下载页，此页提供本教程随附的示例项目。</span><span class="sxs-lookup"><span data-stu-id="06ad4-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to go to the download page that provides the sample projects that go with this tutorial.</span></span> <span data-ttu-id="06ad4-111">教程项目包括在 **Analysis Services 教程 SQL Server 2012** 下载中。</span><span class="sxs-lookup"><span data-stu-id="06ad4-111">The tutorial projects are included in the **Analysis Services Tutorial SQL Server 2012** download.</span></span>  
  
2.  <span data-ttu-id="06ad4-112">单击“Analysis Services 教程 SQL Server 2012”可下载包含此教程项目的包。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="06ad4-112">Click **Analysis Services Tutorial SQL Server 2012** to download the package that contains the projects for this tutorial.</span></span>  
  
     <span data-ttu-id="06ad4-113">默认情况下，.zip 文件将保存到 Downloads 文件夹。</span><span class="sxs-lookup"><span data-stu-id="06ad4-113">By default, a .zip file is saved to the Downloads folder.</span></span> <span data-ttu-id="06ad4-114">您必须将该 .zip 文件移到具有更短路径的位置（例如，创建一个 C:\Tutorials 文件夹以便存储这些文件）。</span><span class="sxs-lookup"><span data-stu-id="06ad4-114">You must move the .zip file to a location that has a shorter path (for example, create a C:\Tutorials folder to store the files).</span></span>  <span data-ttu-id="06ad4-115">然后，您可以解压缩在该 .zip 文件中包含的文件。</span><span class="sxs-lookup"><span data-stu-id="06ad4-115">You can then extract the files contained in the .zip file.</span></span> <span data-ttu-id="06ad4-116">如果您尝试从具有较长路径的 Downloads 文件夹解压缩这些文件，将只会获得课程 1。</span><span class="sxs-lookup"><span data-stu-id="06ad4-116">If you attempt to unzip the files from the Downloads folder, which has a longer path, you will only get Lesson 1.</span></span>  
  
3.  <span data-ttu-id="06ad4-117">在根驱动器处或附近创建一个子文件夹，例如 C:\Tutorial。</span><span class="sxs-lookup"><span data-stu-id="06ad4-117">Create a subfolder at or near the root drive, for example, C:\Tutorial.</span></span>  
  
4.  <span data-ttu-id="06ad4-118">将 **Analysis Services Tutorial SQL Server 2012.zip** 文件移到子文件夹。</span><span class="sxs-lookup"><span data-stu-id="06ad4-118">Move the **Analysis Services Tutorial SQL Server 2012.zip** file to the subfolder.</span></span>  
  
5.  <span data-ttu-id="06ad4-119">右键单击该文件，然后选择“全部提取”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="06ad4-119">Right-click the file and select **Extract All**.</span></span>  
  
6.  <span data-ttu-id="06ad4-120">浏览到 **Lesson 4 Start** 文件夹，以便找到 **Analysis Services Tutorial.sln** 文件。</span><span class="sxs-lookup"><span data-stu-id="06ad4-120">Browse to the **Lesson 4 Start** folder to find the **Analysis Services Tutorial.sln** file.</span></span>  
  
## <a name="loading-and-processing-the-enhanced-project"></a><span data-ttu-id="06ad4-121">加载和处理增强的项目</span><span class="sxs-lookup"><span data-stu-id="06ad4-121">Loading and Processing the Enhanced Project</span></span>  
  
1.  <span data-ttu-id="06ad4-122">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的 "**文件**" 菜单上，单击 "**关闭解决方案**" 关闭不使用的文件。</span><span class="sxs-lookup"><span data-stu-id="06ad4-122">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **File** menu, click **Close Solution** to close files you won't be using.</span></span>  
  
2.  <span data-ttu-id="06ad4-123">在“文件”\*\*\*\* 菜单中，指向“打开”\*\*\*\*，然后单击“项目”/“解决方案”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="06ad4-123">On the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="06ad4-124">浏览到将教程项目文件解压缩到的位置。</span><span class="sxs-lookup"><span data-stu-id="06ad4-124">Browse to the location where you extracted the tutorial project files.</span></span>  
  
     <span data-ttu-id="06ad4-125">找到名为 **Lesson 4 Start**的文件夹，双击 Analysis Services Tutorial.sln。</span><span class="sxs-lookup"><span data-stu-id="06ad4-125">Find the folder named **Lesson 4 Start**, and then double-click Analysis Services Tutorial.sln.</span></span>  
  
4.  <span data-ttu-id="06ad4-126">将 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目的增强版本部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的本地实例或其他实例，并确认处理已成功完成。</span><span class="sxs-lookup"><span data-stu-id="06ad4-126">Deploy the enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project to the local instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], or to another instance, and verify that processing completes successfully.</span></span>  
  
## <a name="understanding-the-enhancements-to-the-project"></a><span data-ttu-id="06ad4-127">了解该项目的增强功能</span><span class="sxs-lookup"><span data-stu-id="06ad4-127">Understanding the Enhancements to the Project</span></span>  
 <span data-ttu-id="06ad4-128">该项目的增强版本与前三节课程中所完成 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目的版本不同。</span><span class="sxs-lookup"><span data-stu-id="06ad4-128">The enhanced version of the project is different from the version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons.</span></span> <span data-ttu-id="06ad4-129">下面几节说明了具体的差异。</span><span class="sxs-lookup"><span data-stu-id="06ad4-129">The differences are described in the following sections.</span></span> <span data-ttu-id="06ad4-130">在继续学习本教程的其余课程之前，请查看此信息。</span><span class="sxs-lookup"><span data-stu-id="06ad4-130">Review this information before continuing with the remaining lessons in the tutorial.</span></span>  
  
### <a name="data-source-view"></a><span data-ttu-id="06ad4-131">“数据源视图”</span><span class="sxs-lookup"><span data-stu-id="06ad4-131">Data Source View</span></span>  
 <span data-ttu-id="06ad4-132">该增强的项目的数据源视图中新增了来自 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 数据库的一个事实数据表和四个维度表。</span><span class="sxs-lookup"><span data-stu-id="06ad4-132">The data source view in the enhanced project contains one additional fact table and four additional dimension tables from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="06ad4-133">可以看到该数据源视图包含十个表， \<All Tables> 关系图变得很拥挤，</span><span class="sxs-lookup"><span data-stu-id="06ad4-133">Notice that with ten tables in the data source view, the \<All Tables> diagram is becoming crowded.</span></span> <span data-ttu-id="06ad4-134">因此很难轻松理解各表之间的关系并找到特定表。</span><span class="sxs-lookup"><span data-stu-id="06ad4-134">This makes it difficult to easily understand the relationships between the tables and to locate specific tables.</span></span> <span data-ttu-id="06ad4-135">为了解决这一问题，将这些表组织为两个逻辑关系图：“Internet 销售”关系图和“分销商销售”关系图。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="06ad4-135">To solve this problem, the tables are organized into two logical diagrams, the **Internet Sales** diagram and the **Reseller Sales** diagram.</span></span> <span data-ttu-id="06ad4-136">这两个关系图均围绕一个事实数据表进行组织。</span><span class="sxs-lookup"><span data-stu-id="06ad4-136">These diagrams are each organized around a single fact table.</span></span> <span data-ttu-id="06ad4-137">通过创建逻辑关系图，您可以在数据源视图中查看和使用表的特定子集，而无需始终在一个关系图中查看所有表及其关系。</span><span class="sxs-lookup"><span data-stu-id="06ad4-137">Creating logical diagrams lets you view and work with a specific subset of the tables in a data source view instead of always viewing all the tables and their relationships in a single diagram.</span></span>  
  
#### <a name="internet-sales-diagram"></a><span data-ttu-id="06ad4-138">“Internet 销售”关系图</span><span class="sxs-lookup"><span data-stu-id="06ad4-138">Internet Sales Diagram</span></span>  
 <span data-ttu-id="06ad4-139">“Internet 销售”关系图包含与直接通过 Internet 向客户销售 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 产品相关的表。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="06ad4-139">The **Internet Sales** diagram contains the tables that are related to the sale of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] products directly to customers through the Internet.</span></span> <span data-ttu-id="06ad4-140">该关系图包含四个维度表和一个事实表，在第 1 课中已经将这些表添加到 **Adventure Works DW 2012** 数据源视图。</span><span class="sxs-lookup"><span data-stu-id="06ad4-140">The tables in the diagram are the four dimension tables and one fact table that you added to the **Adventure Works DW 2012** data source view in Lesson 1.</span></span> <span data-ttu-id="06ad4-141">这些表包括：</span><span class="sxs-lookup"><span data-stu-id="06ad4-141">These tables are as follows:</span></span>  
  
-   <span data-ttu-id="06ad4-142">**地域**</span><span class="sxs-lookup"><span data-stu-id="06ad4-142">**Geography**</span></span>  
  
-   <span data-ttu-id="06ad4-143">**Customer**</span><span class="sxs-lookup"><span data-stu-id="06ad4-143">**Customer**</span></span>  
  
-   <span data-ttu-id="06ad4-144">**Date**</span><span class="sxs-lookup"><span data-stu-id="06ad4-144">**Date**</span></span>  
  
-   <span data-ttu-id="06ad4-145">**Product**</span><span class="sxs-lookup"><span data-stu-id="06ad4-145">**Product**</span></span>  
  
-   <span data-ttu-id="06ad4-146">**InternetSales**</span><span class="sxs-lookup"><span data-stu-id="06ad4-146">**InternetSales**</span></span>  
  
#### <a name="reseller-sales-diagram"></a><span data-ttu-id="06ad4-147">“分销商销售”关系图</span><span class="sxs-lookup"><span data-stu-id="06ad4-147">Reseller Sales Diagram</span></span>  
 <span data-ttu-id="06ad4-148">“分销商销售”关系图包含与分销商销售 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 产品相关的表。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="06ad4-148">The **Reseller Sales** diagram contains the tables that are related to the sale of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] products by resellers.</span></span> <span data-ttu-id="06ad4-149">该关系图包含来自 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 数据库的下列七个维度表和一个事实数据表：</span><span class="sxs-lookup"><span data-stu-id="06ad4-149">This diagram contains the following seven dimension tables and one fact table from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database:</span></span>  
  
-   <span data-ttu-id="06ad4-150">**Reseller**</span><span class="sxs-lookup"><span data-stu-id="06ad4-150">**Reseller**</span></span>  
  
-   <span data-ttu-id="06ad4-151">**Promotion**</span><span class="sxs-lookup"><span data-stu-id="06ad4-151">**Promotion**</span></span>  
  
-   <span data-ttu-id="06ad4-152">**SalesTerritory**</span><span class="sxs-lookup"><span data-stu-id="06ad4-152">**SalesTerritory**</span></span>  
  
-   <span data-ttu-id="06ad4-153">**地域**</span><span class="sxs-lookup"><span data-stu-id="06ad4-153">**Geography**</span></span>  
  
-   <span data-ttu-id="06ad4-154">**Date**</span><span class="sxs-lookup"><span data-stu-id="06ad4-154">**Date**</span></span>  
  
-   <span data-ttu-id="06ad4-155">**Product**</span><span class="sxs-lookup"><span data-stu-id="06ad4-155">**Product**</span></span>  
  
-   <span data-ttu-id="06ad4-156">**员工**</span><span class="sxs-lookup"><span data-stu-id="06ad4-156">**Employee**</span></span>  
  
-   <span data-ttu-id="06ad4-157">**ResellerSales**</span><span class="sxs-lookup"><span data-stu-id="06ad4-157">**ResellerSales**</span></span>  
  
 <span data-ttu-id="06ad4-158">请注意，“Internet 销售”关系图和“分销商销售”关系图中都使用了 **DimGeography**、**DimDate** 和 **DimProduct** 表。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="06ad4-158">Notice that the **DimGeography**, **DimDate**, and **DimProduct** tables are used in both the **Internet Sales** diagram and the **Reseller Sales** diagram.</span></span> <span data-ttu-id="06ad4-159">维度表可链接到多个事实数据表。</span><span class="sxs-lookup"><span data-stu-id="06ad4-159">Dimension tables can be linked to multiple fact tables.</span></span>  
  
### <a name="database-and-cube-dimensions"></a><span data-ttu-id="06ad4-160">数据库和多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="06ad4-160">Database and Cube Dimensions</span></span>  
 <span data-ttu-id="06ad4-161">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目包含五个新数据库维度，而 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集包含与此相同的五个维度作为多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="06ad4-161">The [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project contains five new database dimensions, and the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube contains these same five dimensions as cube dimensions.</span></span> <span data-ttu-id="06ad4-162">这些维度已定义为具有通过使用命名计算、组合成员键和显示文件夹修改过的用户层次结构和属性。</span><span class="sxs-lookup"><span data-stu-id="06ad4-162">These dimensions have been defined to have user hierarchies and attributes that were modified by using named calculations, composition member keys, and display folders.</span></span> <span data-ttu-id="06ad4-163">下面的列表对这些新维度进行了说明。</span><span class="sxs-lookup"><span data-stu-id="06ad4-163">The new dimensions are described in the following list.</span></span>  
  
 <span data-ttu-id="06ad4-164">“分销商”维度</span><span class="sxs-lookup"><span data-stu-id="06ad4-164">Reseller Dimension</span></span>  
 <span data-ttu-id="06ad4-165">“分销商”维度基于 **Adventure Works DW 2012** 数据源视图中的 **Reseller** 表。</span><span class="sxs-lookup"><span data-stu-id="06ad4-165">The Reseller dimension is based on the **Reseller** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="06ad4-166">“促销”维度</span><span class="sxs-lookup"><span data-stu-id="06ad4-166">Promotion Dimension</span></span>  
 <span data-ttu-id="06ad4-167">“促销”维度基于 **Adventure Works DW 2012** 数据源视图中的 **Promotion** 表。</span><span class="sxs-lookup"><span data-stu-id="06ad4-167">The Promotion dimension is based on the **Promotion** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="06ad4-168">“销售区域”维度</span><span class="sxs-lookup"><span data-stu-id="06ad4-168">Sales Territory Dimension</span></span>  
 <span data-ttu-id="06ad4-169">“销售区域”维度基于 **Adventure Works DW 2012** 数据源视图中的 **SalesTerritory** 表。</span><span class="sxs-lookup"><span data-stu-id="06ad4-169">The Sales Territory dimension is based on the **SalesTerritory** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="06ad4-170">“雇员”维度</span><span class="sxs-lookup"><span data-stu-id="06ad4-170">Employee Dimension</span></span>  
 <span data-ttu-id="06ad4-171">“雇员”维度基于 **Adventure Works DW 2012** 数据源视图中的 **Employee** 表。</span><span class="sxs-lookup"><span data-stu-id="06ad4-171">The Employee dimension is based on the **Employee** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="06ad4-172">“地域”维度</span><span class="sxs-lookup"><span data-stu-id="06ad4-172">Geography Dimension</span></span>  
 <span data-ttu-id="06ad4-173">“地域”维度基于 **Adventure Works DW 2012** 数据源视图中的 **Geography** 表。</span><span class="sxs-lookup"><span data-stu-id="06ad4-173">The Geography dimension is based on the **Geography** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
#### <a name="analysis-services-cube"></a><span data-ttu-id="06ad4-174">Analysis Services 多维数据集</span><span class="sxs-lookup"><span data-stu-id="06ad4-174">Analysis Services Cube</span></span>  
 <span data-ttu-id="06ad4-175">现在， **Analysis Services Tutorial** 多维数据集包含两个度量值组：原始度量值组和另一个度量值组；前者基于 **InternetSales** 表，后者基于 **Adventure Works DW 2012** 数据源视图中的 **ResellerSales** 表。</span><span class="sxs-lookup"><span data-stu-id="06ad4-175">The **Analysis Services Tutorial** cube now contains two measure groups, the original measure group based on the **InternetSales** table and a second measure group based on the **ResellerSales** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="06ad4-176">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="06ad4-176">Next Task in Lesson</span></span>  
 [<span data-ttu-id="06ad4-177">定义父子层次结构中的父特性属性</span><span class="sxs-lookup"><span data-stu-id="06ad4-177">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>](lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md) 
  
## <a name="see-also"></a><span data-ttu-id="06ad4-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06ad4-178">See Also</span></span>  
 [<span data-ttu-id="06ad4-179">部署 Analysis Services 项目</span><span class="sxs-lookup"><span data-stu-id="06ad4-179">Deploying an Analysis Services Project</span></span>](lesson-2-5-deploying-an-analysis-services-project.md)  
  
  
