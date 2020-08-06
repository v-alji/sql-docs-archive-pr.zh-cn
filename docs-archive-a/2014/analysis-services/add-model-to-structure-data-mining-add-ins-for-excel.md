---
title: 向 (用于 Excel 的数据挖掘外接程序添加模型) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, creating
ms.assetid: 8efd5bf4-4e6a-4ee8-971a-6efaed5f3b76
author: minewiskan
ms.author: owend
ms.openlocfilehash: b42cecafc2e3d676465e372e00fe472132f06a3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579436"
---
# <a name="add-model-to-structure-data-mining-add-ins-for-excel"></a><span data-ttu-id="f82cd-102">将模型添加到结构（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="f82cd-102">Add Model to Structure (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="f82cd-103">![“将模型添加到结构”按钮](media/dmc-addmodel.gif "“将模型添加到结构”按钮")</span><span class="sxs-lookup"><span data-stu-id="f82cd-103">![Add Model to Structure button](media/dmc-addmodel.gif "Add Model to Structure button")</span></span>  
  
 <span data-ttu-id="f82cd-104">单击 "**将模型添加到结构**" 时，将启动一个向导，该向导将帮助您创建新的挖掘模型以用于现有挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="f82cd-104">When you click **Add Model to Structure**, a wizard starts that helps you create a new mining model to use with an existing mining structure.</span></span> <span data-ttu-id="f82cd-105">此选项十分有用，因为通过它可以比较基于相同数据的模型或创建自定义模型。</span><span class="sxs-lookup"><span data-stu-id="f82cd-105">This option is useful because it lets you compare models that are based on the same data, or create customized models.</span></span>  
  
 <span data-ttu-id="f82cd-106">如果 Analysis Services 的实例尚未包含所需的数据，请使用 "[创建挖掘结构" &#40;SQL Server 数据挖掘外接程序 "&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)向导来设置挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="f82cd-106">If the instance of Analysis Services does not already contain the data you need, use the [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) wizard to set up a mining structure.</span></span> <span data-ttu-id="f82cd-107">或者，可以启动一个建模向导，然后向该向导创建的结构添加新模型。</span><span class="sxs-lookup"><span data-stu-id="f82cd-107">Or, you can launch one of the modeling wizards, and then add a new model to the structure created by the wizard.</span></span>  
  
 <span data-ttu-id="f82cd-108">若要使用向导不支持的算法创建高级模型，请使用 "**数据挖掘高级查询编辑器**" 创建一个挖掘结构，然后添加一个模型。</span><span class="sxs-lookup"><span data-stu-id="f82cd-108">To create advanced models using algorithms not supported by the wizards, create a mining structure and then add a model using the **Data Mining Advanced Query Editor**.</span></span>  
  
## <a name="add-a-new-model-to-an-existing-structure"></a><span data-ttu-id="f82cd-109">向现有结构添加新模型</span><span class="sxs-lookup"><span data-stu-id="f82cd-109">Add a new model to an existing structure</span></span>  
  
1.  <span data-ttu-id="f82cd-110">在 "**数据挖掘**" 功能区上，单击 "**高级**" 下的箭头，然后选择 "**将模型添加到结构**"。</span><span class="sxs-lookup"><span data-stu-id="f82cd-110">On the **Data Mining** ribbon, click the arrow under **Advanced**, and then select **Add Model to Structure**.</span></span>  
  
2.  <span data-ttu-id="f82cd-111">在 "**选择结构**" 对话框中，选择包含要使用的数据的结构，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="f82cd-111">In the **Select Structure** dialog box, choose the structure that contains the data you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="f82cd-112">**提示**：如果你不确定哪个挖掘结构包含所需的数据，请使用**文档模型**向导查看有关数据的列和基本统计信息。</span><span class="sxs-lookup"><span data-stu-id="f82cd-112">**Tip**: If you are not sure which mining structure contains the data you need, use the **Document Model** wizard to view the columns and basic statistics about the data.</span></span>  
  
     <span data-ttu-id="f82cd-113">如果找不到挖掘结构，请检查当前使用的连接。</span><span class="sxs-lookup"><span data-stu-id="f82cd-113">If you can't find a mining structure, check the connection that you are currently using.</span></span> <span data-ttu-id="f82cd-114">可能需要打开另一个服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="f82cd-114">You might need to open a connection to a different server.</span></span>  
  
3.  <span data-ttu-id="f82cd-115">在 "**选择挖掘算法**" 对话框中，选择要在新挖掘模型中使用的挖掘算法。</span><span class="sxs-lookup"><span data-stu-id="f82cd-115">In the **Select Mining Algorithm** dialog box, choose a mining algorithm to use in the new mining model.</span></span>  
  
     <span data-ttu-id="f82cd-116">请注意，此对话框提供的选项比在向导中看到的选项多。</span><span class="sxs-lookup"><span data-stu-id="f82cd-116">Notice that the dialog box provides a lot more options than you'll see in the wizards.</span></span> <span data-ttu-id="f82cd-117">只要数据兼容，便可以使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器上支持的任何算法创建模型。</span><span class="sxs-lookup"><span data-stu-id="f82cd-117">You can create a model using any algorithm supported on your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, provided your data is compatible.</span></span>  
  
4.  <span data-ttu-id="f82cd-118">建议您还可以单击 "**参数**" 按钮打开 "**算法参数**" 对话框并自定义算法的参数。</span><span class="sxs-lookup"><span data-stu-id="f82cd-118">We recommend that you also click the **Parameters** button to open the **Algorithm Parameters** dialog box and customize parameters on the algorithm.</span></span> <span data-ttu-id="f82cd-119">此选项是创建自定义挖掘模型的最简便方法。</span><span class="sxs-lookup"><span data-stu-id="f82cd-119">This option is the easiest way to create custom mining models.</span></span>  
  
5.  <span data-ttu-id="f82cd-120">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f82cd-120">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="f82cd-121">在 "**选择列**" 对话框中，查看列的列表，如有必要，请将列的用法更改为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="f82cd-121">In the **Select Columns** dialog box, review the list of columns, and if necessary, change the usage of the columns to one of these values:</span></span>  
  
    -   <span data-ttu-id="f82cd-122">输入。</span><span class="sxs-lookup"><span data-stu-id="f82cd-122">**Input**.</span></span> <span data-ttu-id="f82cd-123">指示列包含可能影响结果并且应用作模型输入的变量。</span><span class="sxs-lookup"><span data-stu-id="f82cd-123">Indicates that the column contains variables that may affect the outcome and should be used as inputs to the model.</span></span>  
  
    -   <span data-ttu-id="f82cd-124">**输入和预测**。</span><span class="sxs-lookup"><span data-stu-id="f82cd-124">**Input and Predict**.</span></span> <span data-ttu-id="f82cd-125">指示数据应用作输入，并且您还要预测这些值。</span><span class="sxs-lookup"><span data-stu-id="f82cd-125">Indicates that the data should be used as an input, and that you also want to predict these values.</span></span>  
  
    -   <span data-ttu-id="f82cd-126">**仅预测**。</span><span class="sxs-lookup"><span data-stu-id="f82cd-126">**Predict only**.</span></span> <span data-ttu-id="f82cd-127">指示数据不应用作模型的输入。</span><span class="sxs-lookup"><span data-stu-id="f82cd-127">Indicates that the data should not be used as an input for the model.</span></span>  
  
    -   <span data-ttu-id="f82cd-128">**Key**。</span><span class="sxs-lookup"><span data-stu-id="f82cd-128">**Key**.</span></span> <span data-ttu-id="f82cd-129">每个模型至少需要一个密钥。</span><span class="sxs-lookup"><span data-stu-id="f82cd-129">Each model requires at least one key.</span></span> <span data-ttu-id="f82cd-130">根据模型类型，您还可以选择其他特殊键，如**SequenceKey**或**TimeKey**。</span><span class="sxs-lookup"><span data-stu-id="f82cd-130">Depending on the model type, you might also have the option to additional special keys, such as the **SequenceKey** or **TimeKey**.</span></span>  
  
    -   <span data-ttu-id="f82cd-131">**请勿使用**。</span><span class="sxs-lookup"><span data-stu-id="f82cd-131">**Do not use**.</span></span> <span data-ttu-id="f82cd-132">指示数据不应在模型中使用（即使在结构中存在）。</span><span class="sxs-lookup"><span data-stu-id="f82cd-132">Indicates that the data should not be used in the model, even if present in the structure.</span></span>  
  
7.  <span data-ttu-id="f82cd-133">单击 "浏览\*\* ( ..." ) **按钮，打开 "**设置列模型标志\*\*" 对话框。</span><span class="sxs-lookup"><span data-stu-id="f82cd-133">Click the browse **(...)** button to open the **Set Column Model Flags** dialog box.</span></span>  
  
     <span data-ttu-id="f82cd-134">花点时间验证每个数据列的用法是否适合于模型。</span><span class="sxs-lookup"><span data-stu-id="f82cd-134">Take a minute to verify that the usage of each data column is appropriate for the model.</span></span> <span data-ttu-id="f82cd-135">这是防止在尝试处理模型时发生错误的重要步骤。</span><span class="sxs-lookup"><span data-stu-id="f82cd-135">This is an important step for preventing errors when you try to process the model.</span></span>  
  
     <span data-ttu-id="f82cd-136">例如，如果您重复使用为决策树模型创建的结构并对其应用 Naïve Bayes 算法，则具有数据类型 `Numeric` 和内容类型 `Continuous` 的列需要装箱或更改为离散变量。</span><span class="sxs-lookup"><span data-stu-id="f82cd-136">For example, if you re-use a structure that was created for a decision trees model and apply the Naïve Bayes algorithm to it, columns that have the data type `Numeric` and the content type `Continuous` will need to be binned or changed to discrete variables.</span></span>  
  
     <span data-ttu-id="f82cd-137">如果结构中的列不适用于新算法，则可以通过选择 "不**使用**" 来跳过这些列。</span><span class="sxs-lookup"><span data-stu-id="f82cd-137">If columns in the structure are not applicable to the new algorithm, you can bypass them by selecting **Do not use**.</span></span>  
  
8.  <span data-ttu-id="f82cd-138">在 "**设置列模型标志**" 对话框中，查看或设置建模标志（如果有）。</span><span class="sxs-lookup"><span data-stu-id="f82cd-138">In the **Set Column Model Flags** dialog box, review or set the modeling flags, if any.</span></span>  
  
     <span data-ttu-id="f82cd-139">通过建模标志可以控制处理 null 的方式（但不仅限于此）。</span><span class="sxs-lookup"><span data-stu-id="f82cd-139">Modeling flags let you control the way that nulls are handled, among other things.</span></span> <span data-ttu-id="f82cd-140">有关详细信息，请参阅[建模标志（数据挖掘）](data-mining/modeling-flags-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="f82cd-140">For more information, see [Modeling Flags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).</span></span>  
  
     <span data-ttu-id="f82cd-141">完成后，单击 **"确定"** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="f82cd-141">Click **OK** when done to close the dialog box.</span></span>  
  
9. <span data-ttu-id="f82cd-142">在 "**完成**" 对话框中，键入新挖掘模型的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="f82cd-142">In the **Finish** dialog box, type a name and description for the new mining model.</span></span>  
  
     <span data-ttu-id="f82cd-143">根据生成的模型类型，您还有以下选项：</span><span class="sxs-lookup"><span data-stu-id="f82cd-143">Depending on the type of model you built, you might also have these options:</span></span>  
  
    -   <span data-ttu-id="f82cd-144">生成之后浏览已完成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f82cd-144">Browse the completed mining model after it is built.</span></span>  
  
    -   <span data-ttu-id="f82cd-145">从模型对数据源使用钻取。</span><span class="sxs-lookup"><span data-stu-id="f82cd-145">Use drillthrough from the model to the source data.</span></span>  
  
         <span data-ttu-id="f82cd-146">有关详细信息，请参阅[挖掘模型钻取](data-mining/drillthrough-on-mining-models.md)。</span><span class="sxs-lookup"><span data-stu-id="f82cd-146">For more information, see [Drillthrough on Mining Models](data-mining/drillthrough-on-mining-models.md).</span></span>  
  
10. <span data-ttu-id="f82cd-147">单击“完成”以保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="f82cd-147">Click **Finish** to save your changes.</span></span> <span data-ttu-id="f82cd-148">执行此操作时，新模型会部署到服务器并进行处理。</span><span class="sxs-lookup"><span data-stu-id="f82cd-148">As you do so the new model is deployed to the server and processed.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="f82cd-149">相关选项</span><span class="sxs-lookup"><span data-stu-id="f82cd-149">Related Options</span></span>  
  
|<span data-ttu-id="f82cd-150">选项</span><span class="sxs-lookup"><span data-stu-id="f82cd-150">Option</span></span>|<span data-ttu-id="f82cd-151">注释</span><span class="sxs-lookup"><span data-stu-id="f82cd-151">Comments</span></span>|  
|------------|--------------|  
|<span data-ttu-id="f82cd-152">"**选择结构或模型**" 对话框</span><span class="sxs-lookup"><span data-stu-id="f82cd-152">**Select Structure or Model** dialog box</span></span>|<span data-ttu-id="f82cd-153">选择一种现有挖掘结构作为生成新模型的基础。</span><span class="sxs-lookup"><span data-stu-id="f82cd-153">Choose en existing mining structure to use as the basis for building a new model.</span></span>  <span data-ttu-id="f82cd-154">选取的结构必须位于当前连接上。</span><span class="sxs-lookup"><span data-stu-id="f82cd-154">The structure you pick must be located on the current connection.</span></span> <span data-ttu-id="f82cd-155">如果不是，则使用 "[连接到源数据" &#40;Excel&#41;工具的数据挖掘客户端来](connect-to-source-data-data-mining-client-for-excel.md)更改连接。</span><span class="sxs-lookup"><span data-stu-id="f82cd-155">If not, change connections using the [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) tool.</span></span>|  
|<span data-ttu-id="f82cd-156">"**选择挖掘算法**" 对话框</span><span class="sxs-lookup"><span data-stu-id="f82cd-156">**Select Mining Algorithm** dialog Box</span></span>|<span data-ttu-id="f82cd-157">数据挖掘算法列表的内容取决于所连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="f82cd-157">The list of data mining algorithms depends on which server you are connected to.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="f82cd-158">在 Standard 和 Enterprise 版本中提供不同的算法。</span><span class="sxs-lookup"><span data-stu-id="f82cd-158">provides different algorithms in the Standard and Enterprise editions.</span></span> <span data-ttu-id="f82cd-159">管理员还可能添加了自定义算法。</span><span class="sxs-lookup"><span data-stu-id="f82cd-159">Your administrator also might have added custom algorithms.</span></span><br /><br /> <span data-ttu-id="f82cd-160">如果看不到任何算法，请验证是否已连接到的实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f82cd-160">If you can't see any algorithms, verify that you are connected to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>|  
|<span data-ttu-id="f82cd-161">**算法参数**对话框</span><span class="sxs-lookup"><span data-stu-id="f82cd-161">**Algorithm Parameters** Dialog Box</span></span>|<span data-ttu-id="f82cd-162">在这些设置中，可以使用特定于分析方法的参数自定义每个算法。</span><span class="sxs-lookup"><span data-stu-id="f82cd-162">In these settings, you can customize each algorithm using parameters specific to the analytical method.</span></span> <span data-ttu-id="f82cd-163">还可以设置种子以确保模型的结果可以在多个定型过程间重新生成。</span><span class="sxs-lookup"><span data-stu-id="f82cd-163">You can also set a seed to ensure that the results of the model can be reproduced across multiple training passes.</span></span><br /><br /> <span data-ttu-id="f82cd-164">有关详细信息，请参阅[&#40;SQL Server 数据挖掘外接程序&#41;的算法参数](algorithm-parameters-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="f82cd-164">For more information, see [Algorithm Parameters &#40;SQL Server Data Mining Add-ins&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md).</span></span>|  
|<span data-ttu-id="f82cd-165">**设置列模型标志**对话框</span><span class="sxs-lookup"><span data-stu-id="f82cd-165">**Set Column Model Flags** Dialog Box</span></span>|<span data-ttu-id="f82cd-166">建模标志可通过指定缺失数据的处理方式来改进模型。</span><span class="sxs-lookup"><span data-stu-id="f82cd-166">Modeling flags can improve your model by specifying how missing data is to be handled.</span></span> <span data-ttu-id="f82cd-167">有关详细信息，请参阅[建模标志（数据挖掘）](data-mining/modeling-flags-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="f82cd-167">For more information, see [Modeling Flags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).</span></span>|  
  
###  <a name="setting-column-usage"></a><a name="Bkmk_mdlcolumn"></a><span data-ttu-id="f82cd-168">设置列用法</span><span class="sxs-lookup"><span data-stu-id="f82cd-168">Setting Column Usage</span></span>  
 <span data-ttu-id="f82cd-169">向现有挖掘结构添加新的模型时，必须指定该模型将如何使用挖掘结构中的每个数据列。</span><span class="sxs-lookup"><span data-stu-id="f82cd-169">When you add a new model to an existing mining structure, you must specify how the model will use each of the columns of data in the mining structure.</span></span> <span data-ttu-id="f82cd-170">您可能会发现，此向导中的选项比挖掘结构上的选项更详细。</span><span class="sxs-lookup"><span data-stu-id="f82cd-170">You'll probably observe that the options in this wizard are far more detailed than the options on the mining structure.</span></span> <span data-ttu-id="f82cd-171">为什么？</span><span class="sxs-lookup"><span data-stu-id="f82cd-171">Why?</span></span>  
  
 <span data-ttu-id="f82cd-172">原因在于，使用向导一起创建模型和结构时，许多控制算法对数据的使用方式的选项会自动设置。</span><span class="sxs-lookup"><span data-stu-id="f82cd-172">The reason is that when you create a model and a structure together using a wizard, many of the options that control how data is used by the algorithm are set automatically.</span></span> <span data-ttu-id="f82cd-173">但是，向现有模型添加新模型时，需要手动查看这些选项，并指定数据是否应用于分析、数据类型是否正确等。</span><span class="sxs-lookup"><span data-stu-id="f82cd-173">However, when you add a new model to an existing, you need to see these options manually, and specify whether data should be used for analysis, whether the data type is correct, and so forth.</span></span>  
  
 <span data-ttu-id="f82cd-174">向现有数据应用新算法时您可能会收到错误消息，但是这些消息通常提供有关为允许处理模型而需要进行的更正的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f82cd-174">You might get error messages when applying new algorithms to existing data, but these messages generally provide detailed information about the corrections you need to make to allow the model to be processed.</span></span> <span data-ttu-id="f82cd-175">典型问题如下：</span><span class="sxs-lookup"><span data-stu-id="f82cd-175">Typical problems include the following:</span></span>  
  
-   <span data-ttu-id="f82cd-176">模型需要的数据类型与结构包含的数据类型不同。</span><span class="sxs-lookup"><span data-stu-id="f82cd-176">The model expects a different data type than the structure contains.</span></span>  
  
     <span data-ttu-id="f82cd-177">某些算法只能用于数字；某些算法只能用于文本。</span><span class="sxs-lookup"><span data-stu-id="f82cd-177">Some algorithms can only work with numbers; some can only work with text.</span></span> <span data-ttu-id="f82cd-178">如果数据对于新模型是错误类型，则可能需要修改结构以使模型可以进行处理。</span><span class="sxs-lookup"><span data-stu-id="f82cd-178">If your data is the wrong type for the new model, you might need to modify the structure to enable the model to process.</span></span>  
  
-   <span data-ttu-id="f82cd-179">挖掘结构不包含任何可预测属性。</span><span class="sxs-lookup"><span data-stu-id="f82cd-179">The mining structure contains no predictable attribute.</span></span>  
  
     <span data-ttu-id="f82cd-180">聚类分析模型在生成时可以不使用可预测值，但是其他模型通常需指定单个列用于预测。</span><span class="sxs-lookup"><span data-stu-id="f82cd-180">Clustering models can be built with no predictable value, but other models generally require that you specify a single column for prediction.</span></span>  
  
-   <span data-ttu-id="f82cd-181">数据的构成与您选择的算法不兼容。</span><span class="sxs-lookup"><span data-stu-id="f82cd-181">The composition of the data is incompatible with the algorithm you've chosen.</span></span>  
  
     <span data-ttu-id="f82cd-182">某些类型的分析需要根据唯一规则仔细构造的数据。</span><span class="sxs-lookup"><span data-stu-id="f82cd-182">Some types of analysis require data that is carefully structured according to unique rules.</span></span> <span data-ttu-id="f82cd-183">示例包括预测模型和关联模型。</span><span class="sxs-lookup"><span data-stu-id="f82cd-183">Examples are forecasting models and association models.</span></span> <span data-ttu-id="f82cd-184">可以方便地添加具有相同类型的新模型（可能包含自定义项），但是数据可能不适用于其他算法。</span><span class="sxs-lookup"><span data-stu-id="f82cd-184">You can easily add new models of the same type, perhaps with customizations, but the data might not work with other algorithms.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="f82cd-185">要求</span><span class="sxs-lookup"><span data-stu-id="f82cd-185">Requirements</span></span>  
 <span data-ttu-id="f82cd-186">若要创建数据挖掘模型，必须具有到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的连接。</span><span class="sxs-lookup"><span data-stu-id="f82cd-186">To create data mining models, you must have a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="f82cd-187">有关如何创建或更改连接的详细信息，请参阅[连接到源数据 &#40;Excel 数据挖掘客户端&#41;](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="f82cd-187">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="f82cd-188">如果看不到所需的数据挖掘结构，则可能是因为该结构已被保存到其他实例或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中。</span><span class="sxs-lookup"><span data-stu-id="f82cd-188">If you cannot see the data mining structure that you want, it could be that the structure was saved to a different instance or different [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="f82cd-189">有关如何更改为其他数据挖掘连接的信息，请参阅[连接到数据挖掘服务器](connect-to-a-data-mining-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f82cd-189">For information about how to change to a different data mining connection, see [Connect to a Data Mining Server](connect-to-a-data-mining-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82cd-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f82cd-190">See Also</span></span>  
 [<span data-ttu-id="f82cd-191">创建数据挖掘模型</span><span class="sxs-lookup"><span data-stu-id="f82cd-191">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)   
