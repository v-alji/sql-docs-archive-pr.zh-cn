---
title: 创建目标邮件挖掘模型结构 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6a27f818b29120e40248044091c78205dad945bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690937"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a><span data-ttu-id="e52ee-102">创建目标邮件挖掘模型结构（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="e52ee-102">Creating a Targeted Mailing Mining Model Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="e52ee-103">要创建目标邮件方案，第一步是使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的数据挖掘向导创建新的挖掘结构和决策树挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e52ee-103">The first step in creating a targeted mailing scenario is to use the Data Mining Wizard in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a new mining structure and decision tree mining model.</span></span>  
  
 <span data-ttu-id="e52ee-104">在此任务中，您将设置一个新的挖掘结构，并基于决策树算法添加一个初始挖掘模型 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e52ee-104">In this task you will set up a new mining structure, and add an initial mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="e52ee-105">若要创建此结构，需要首先选择表和视图，然后标识将用于定型的列和将用于测试的列。</span><span class="sxs-lookup"><span data-stu-id="e52ee-105">To create the structure, you will first select tables and views and then identify which columns will be used for training and which for testing.</span></span>  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a><span data-ttu-id="e52ee-106">创建用于目标邮件方案的挖掘结构</span><span class="sxs-lookup"><span data-stu-id="e52ee-106">To create a mining structure for the targeted mailing scenario</span></span>  
  
1.  <span data-ttu-id="e52ee-107">在解决方案资源管理器中，右键单击 "**挖掘结构**"，然后选择 "**新建挖掘结构**" 以启动数据挖掘向导。</span><span class="sxs-lookup"><span data-stu-id="e52ee-107">In Solution Explorer, right-click **Mining Structures** and select **New Mining Structure** to start the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="e52ee-108">在 **“欢迎使用数据挖掘向导”** 页上，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e52ee-108">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="e52ee-109">在 "**选择定义方法**" 页上，验证是否选择了 "**从现有关系数据库或数据仓库**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="e52ee-109">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="e52ee-110">在 "**创建数据挖掘结构**" 页上，在 "**要使用何种数据挖掘技术？**" 下，选择 " **Microsoft 决策树**"。</span><span class="sxs-lookup"><span data-stu-id="e52ee-110">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Decision Trees**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e52ee-111">如果收到警告，告知无法找到数据挖掘算法，则项目属性可能配置不正确。</span><span class="sxs-lookup"><span data-stu-id="e52ee-111">If you get a warning that no data mining algorithms can be found, the project properties might not be configured correctly.</span></span> <span data-ttu-id="e52ee-112">当项目尝试从 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器检索数据挖掘算法列表却找不到服务器时，就会出现此警告。</span><span class="sxs-lookup"><span data-stu-id="e52ee-112">This warning occurs when the project attempts to retrieve a list of data mining algorithms from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server and cannot find the server.</span></span> <span data-ttu-id="e52ee-113">默认情况下， [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 将使用**localhost**作为服务器。</span><span class="sxs-lookup"><span data-stu-id="e52ee-113">By default, [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] will use **localhost** as the server.</span></span> <span data-ttu-id="e52ee-114">如果要使用其他实例或命名实例，则必须更改项目属性。</span><span class="sxs-lookup"><span data-stu-id="e52ee-114">If you are using a different instance, or a named instance, you must change the project properties.</span></span> <span data-ttu-id="e52ee-115">有关详细信息，请参阅[创建 Analysis Services 项目 &#40;基本数据挖掘教程&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="e52ee-115">For more information, see [Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).</span></span>  
  
5.  <span data-ttu-id="e52ee-116">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e52ee-116">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="e52ee-117">在 "**选择数据源视图**" 页上的 "**可用数据源视图**" 窗格中，选择 "**目标邮件**"。</span><span class="sxs-lookup"><span data-stu-id="e52ee-117">On the **Select Data Source View** page, in the **Available data source views** pane, select **Targeted Mailing**.</span></span> <span data-ttu-id="e52ee-118">您可以单击 "**浏览**" 以在数据源视图中查看表，然后单击 "**关闭**" 以返回到向导。</span><span class="sxs-lookup"><span data-stu-id="e52ee-118">You can click **Browse** to view the tables in the data source view and then click **Close** to return to the wizard.</span></span>  
  
7.  <span data-ttu-id="e52ee-119">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e52ee-119">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="e52ee-120">在 "**指定表类型**" 页上，选中 "vTargetMail" 的 "**事例**" 列中的复选框以将其用作事例表，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="e52ee-120">On the **Specify Table Types** page, select the check box in the **Case** column for vTargetMail to use it as the case table, and then click **Next**.</span></span> <span data-ttu-id="e52ee-121">稍后您将使用 ProspectiveBuyer 表进行测试，不过现在可以忽略它。</span><span class="sxs-lookup"><span data-stu-id="e52ee-121">You will use the ProspectiveBuyer table later for testing; ignore it for now.</span></span>  
  
9. <span data-ttu-id="e52ee-122">在 "**指定定型数据**" 页上，您将为模型标识至少一个可预测列、一个键列和一个输入列。</span><span class="sxs-lookup"><span data-stu-id="e52ee-122">On the **Specify the Training Data** page, you will identify at least one predictable column, one key column, and one input column for your model.</span></span> <span data-ttu-id="e52ee-123">选中 " **BikeBuyer** " 行的 "**可预测**" 列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="e52ee-123">Select the check box in the **Predictable** column in the **BikeBuyer** row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e52ee-124">请注意窗口底部的警告。</span><span class="sxs-lookup"><span data-stu-id="e52ee-124">Notice the warning at the bottom of the window.</span></span> <span data-ttu-id="e52ee-125">在至少选择一个**输入**和一个**可预测**列之前，将无法导航到下一页。</span><span class="sxs-lookup"><span data-stu-id="e52ee-125">You will not be able to navigate to the next page until you select at least one **Input** and one **Predictable** column.</span></span>  
  
10. <span data-ttu-id="e52ee-126">单击 "**建议**" 以打开 "提供**相关列建议**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="e52ee-126">Click **Suggest** to open the **Suggest Related Columns** dialog box.</span></span>  
  
     <span data-ttu-id="e52ee-127">只要至少选择了一个可预测属性，就会启用 "**建议**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="e52ee-127">The **Suggest** button is enabled whenever at least one predictable attribute has been selected.</span></span> <span data-ttu-id="e52ee-128">"**建议相关列**" 对话框列出最与可预测列密切相关的列，并通过与可预测属性的关联对属性进行排序。</span><span class="sxs-lookup"><span data-stu-id="e52ee-128">The **Suggest Related Columns** dialog box lists the columns that are most closely related to the predictable column, and orders the attributes by their correlation with the predictable attribute.</span></span> <span data-ttu-id="e52ee-129">显著相关的列（置信度高于 95%）将被自动选中以添加到模型中。</span><span class="sxs-lookup"><span data-stu-id="e52ee-129">Columns with a significant correlation (confidence greater than 95%) are automatically selected to be included in the model.</span></span>  
  
     <span data-ttu-id="e52ee-130">查看建议，然后单击 "**取消**" toignore 建议。</span><span class="sxs-lookup"><span data-stu-id="e52ee-130">Review the suggestions, and then click **Cancel** toignore the suggestions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e52ee-131">如果单击 **"确定"**，则所有列出的建议都将在向导中标记为输入列。</span><span class="sxs-lookup"><span data-stu-id="e52ee-131">If you click **OK**, all listed suggestions will be marked as input columns in the wizard.</span></span> <span data-ttu-id="e52ee-132">如果仅同意其中的某些建议，则必须手动更改值。</span><span class="sxs-lookup"><span data-stu-id="e52ee-132">If you agree with only some of the suggestions, you must change the values manually.</span></span>  
  
11. <span data-ttu-id="e52ee-133">验证**CustomerKey**行中是否已选中 "**键**" 列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="e52ee-133">Verify that the check box in the **Key** column is selected in the **CustomerKey** row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e52ee-134">如果数据源视图中的源表表示一个键，则数据挖掘向导将自动选择该列作为模型的键。</span><span class="sxs-lookup"><span data-stu-id="e52ee-134">If the source table from the data source view indicates a key, the Data Mining Wizard automatically chooses that column as a key for the model.</span></span>  
  
12. <span data-ttu-id="e52ee-135">选中以下行中的 "**输入**" 列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="e52ee-135">Select the check boxes in the **Input** column in the following rows.</span></span> <span data-ttu-id="e52ee-136">可通过下面的方法来同时选中多个列：突出显示一系列单元格，然后在按住 Ctrl 的同时选中一个复选框。</span><span class="sxs-lookup"><span data-stu-id="e52ee-136">You can check multiple columns by highlighting a range of cells and pressing CTRL while selecting a check box.</span></span>  
  
    -   <span data-ttu-id="e52ee-137">**年限**</span><span class="sxs-lookup"><span data-stu-id="e52ee-137">**Age**</span></span>  
  
    -   <span data-ttu-id="e52ee-138">**CommuteDistance**</span><span class="sxs-lookup"><span data-stu-id="e52ee-138">**CommuteDistance**</span></span>  
  
    -   <span data-ttu-id="e52ee-139">**EnglishEducation**</span><span class="sxs-lookup"><span data-stu-id="e52ee-139">**EnglishEducation**</span></span>  
  
    -   <span data-ttu-id="e52ee-140">**EnglishOccupation**</span><span class="sxs-lookup"><span data-stu-id="e52ee-140">**EnglishOccupation**</span></span>  
  
    -   <span data-ttu-id="e52ee-141">**性别**</span><span class="sxs-lookup"><span data-stu-id="e52ee-141">**Gender**</span></span>  
  
    -   <span data-ttu-id="e52ee-142">**GeographyKey**</span><span class="sxs-lookup"><span data-stu-id="e52ee-142">**GeographyKey**</span></span>  
  
    -   <span data-ttu-id="e52ee-143">**HouseOwnerFlag**</span><span class="sxs-lookup"><span data-stu-id="e52ee-143">**HouseOwnerFlag**</span></span>  
  
    -   <span data-ttu-id="e52ee-144">**MaritalStatus**</span><span class="sxs-lookup"><span data-stu-id="e52ee-144">**MaritalStatus**</span></span>  
  
    -   <span data-ttu-id="e52ee-145">**NumberCarsOwned**</span><span class="sxs-lookup"><span data-stu-id="e52ee-145">**NumberCarsOwned**</span></span>  
  
    -   <span data-ttu-id="e52ee-146">**NumberChildrenAtHome**</span><span class="sxs-lookup"><span data-stu-id="e52ee-146">**NumberChildrenAtHome**</span></span>  
  
    -   <span data-ttu-id="e52ee-147">**区域**</span><span class="sxs-lookup"><span data-stu-id="e52ee-147">**Region**</span></span>  
  
    -   <span data-ttu-id="e52ee-148">**TotalChildren**</span><span class="sxs-lookup"><span data-stu-id="e52ee-148">**TotalChildren**</span></span>  
  
    -   <span data-ttu-id="e52ee-149">**YearlyIncome**</span><span class="sxs-lookup"><span data-stu-id="e52ee-149">**YearlyIncome**</span></span>  
  
13. <span data-ttu-id="e52ee-150">在该页的最左侧的列中，选中以下行中的复选框。</span><span class="sxs-lookup"><span data-stu-id="e52ee-150">On the far left column of the page, select the check boxes in the following rows.</span></span>  
  
    -   <span data-ttu-id="e52ee-151">**AddressLine1**</span><span class="sxs-lookup"><span data-stu-id="e52ee-151">**AddressLine1**</span></span>  
  
    -   <span data-ttu-id="e52ee-152">**AddressLine2**</span><span class="sxs-lookup"><span data-stu-id="e52ee-152">**AddressLine2**</span></span>  
  
    -   <span data-ttu-id="e52ee-153">**DateFirstPurchase**</span><span class="sxs-lookup"><span data-stu-id="e52ee-153">**DateFirstPurchase**</span></span>  
  
    -   <span data-ttu-id="e52ee-154">**EmailAddress**</span><span class="sxs-lookup"><span data-stu-id="e52ee-154">**EmailAddress**</span></span>  
  
    -   <span data-ttu-id="e52ee-155">**名字**</span><span class="sxs-lookup"><span data-stu-id="e52ee-155">**FirstName**</span></span>  
  
    -   <span data-ttu-id="e52ee-156">**姓氏**</span><span class="sxs-lookup"><span data-stu-id="e52ee-156">**LastName**</span></span>  
  
     <span data-ttu-id="e52ee-157">确保这些行仅选择了左侧列中的复选标记。</span><span class="sxs-lookup"><span data-stu-id="e52ee-157">Ensure that these rows have checks only in the left column.</span></span> <span data-ttu-id="e52ee-158">这些列将添加到结构中，但不会包含在模型中。</span><span class="sxs-lookup"><span data-stu-id="e52ee-158">These columns will be added to your structure but will not be included in the model.</span></span> <span data-ttu-id="e52ee-159">但是，模型生成后，它们将可用于钻取和测试。</span><span class="sxs-lookup"><span data-stu-id="e52ee-159">However, after the model is built, they will be available for drillthrough and testing.</span></span> <span data-ttu-id="e52ee-160">有关钻取的详细信息，请参阅[钻取查询 &#40;数据挖掘&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="e52ee-160">For more information about drillthrough, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span></span>  
  
14. <span data-ttu-id="e52ee-161">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e52ee-161">Click **Next**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e52ee-162">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="e52ee-162">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e52ee-163">指定数据类型和内容类型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="e52ee-163">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="e52ee-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e52ee-164">See Also</span></span>  
 <span data-ttu-id="e52ee-165">[在数据挖掘向导 &#40;指定表类型&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="e52ee-165">[Specify Table Types &#40;Data Mining Wizard&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="e52ee-166">[数据挖掘设计器](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e52ee-166">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="e52ee-167">Microsoft 决策树算法</span><span class="sxs-lookup"><span data-stu-id="e52ee-167">Microsoft Decision Trees Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
