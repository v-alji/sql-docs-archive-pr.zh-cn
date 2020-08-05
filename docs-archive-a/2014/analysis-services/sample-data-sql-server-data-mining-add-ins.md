---
title: " (SQL Server 数据挖掘外接程序的示例数据) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- holdout
- testing cases
- training cases
- partitioning data [data mining]
- mining models, testing
ms.assetid: 35907ae6-887f-4cb3-a750-cff3d7683d90
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17da9a42f4d76f5c271d5b225cf897a8ac2e97ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579121"
---
# <a name="sample-data-sql-server-data-mining-add-ins"></a><span data-ttu-id="56d98-102">示例数据（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="56d98-102">Sample Data (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="56d98-103">![“数据挖掘”功能区中的为数据分区向导](media/dmc-partition.gif "“数据挖掘”功能区中的为数据分区向导")</span><span class="sxs-lookup"><span data-stu-id="56d98-103">![Partition Data wizard in Data Mining ribbon](media/dmc-partition.gif "Partition Data wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="56d98-104">利用**示例数据**向导，可以轻松地将源数据分为两组，一组用于构建 (定型) 模型，另一组用于测试模型。</span><span class="sxs-lookup"><span data-stu-id="56d98-104">The **Sample Data** wizard makes it easy to divide your source data into two sets, one for building (training) the model and one for testing the model.</span></span> <span data-ttu-id="56d98-105">此向导还提供了一个选项，可用于重新抽样数据来生成能更好地表示您的目标的新数据集。</span><span class="sxs-lookup"><span data-stu-id="56d98-105">This wizard also provides an option for resampling the data to build a new data set that better represents your target.</span></span>  
  
 <span data-ttu-id="56d98-106">为模型的定型和测试创建正确类型的数据是数据挖掘的一个重要部分，但如果没有适当的工具，将非常单调乏味。</span><span class="sxs-lookup"><span data-stu-id="56d98-106">Creating the right kind of data for training and testing your models is an important part of data mining, but one that can be tedious without the right tools.</span></span> <span data-ttu-id="56d98-107">该向导执行分层抽样以确保定型和测试集均衡。</span><span class="sxs-lookup"><span data-stu-id="56d98-107">The wizard performs stratified sampling to make sure that training and testing sets are well balanced.</span></span>  
  
## <a name="random-sampling-and-oversampling"></a><span data-ttu-id="56d98-108">随机抽样和过度抽样</span><span class="sxs-lookup"><span data-stu-id="56d98-108">Random Sampling and Oversampling</span></span>  
 <span data-ttu-id="56d98-109">.</span><span class="sxs-lookup"><span data-stu-id="56d98-109">.</span></span> <span data-ttu-id="56d98-110">随机抽样是确保用于测试模型的数据能准确表示用于创建模型的数据的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="56d98-110">Random sampling is the best way to ensure that the data you use for testing a model fairly represents the data that you use for creating the model.</span></span> <span data-ttu-id="56d98-111">可对存储在 Excel 或外部数据源中的数据进行随机抽样</span><span class="sxs-lookup"><span data-stu-id="56d98-111">You can randomly sample data that is stored in Excel or in an external data source</span></span>  
  
 <span data-ttu-id="56d98-112">如果使用随机抽样选项，则 "**示例数据**" 向导会自动创建定型和测试数据集，并将其输出到单独的 Excel 工作表中以供日后参考。</span><span class="sxs-lookup"><span data-stu-id="56d98-112">If you use the random sampling option, the **Sample Data** wizard automatically creates training and test data sets and outputs them into separate Excel worksheets for later reference.</span></span>  
  
 <span data-ttu-id="56d98-113">如果你的数据存储在 Excel 工作簿中，而不是外部数据源中，则还可以选择使用*过度抽样*。</span><span class="sxs-lookup"><span data-stu-id="56d98-113">If your data is stored in an Excel workbook, and not an external data source, you also have the option to use *oversampling*.</span></span> <span data-ttu-id="56d98-114">通过此选项，指定可能在数据中罕见的目标值，而该向导将收集均衡的一组，其中不仅包括目标值。</span><span class="sxs-lookup"><span data-stu-id="56d98-114">With this option, you specify a target value that might be scarce in your data, and the wizard will collect a balanced set that includes more of the target value.</span></span> <span data-ttu-id="56d98-115">可让向导达到一个目标百分比或创建某个数量的行。</span><span class="sxs-lookup"><span data-stu-id="56d98-115">You can direct the wizard to achieve a targeted percentage, or to create a certain number of rows.</span></span>  
  
 <span data-ttu-id="56d98-116">如果使用过度抽样选项，则 "**示例数据**" 向导会创建一个新的工作表，其中包含新平衡的示例数据。</span><span class="sxs-lookup"><span data-stu-id="56d98-116">If you use the oversampling option, the **Sample Data** wizard creates a new worksheet that contains the newly balanced sample data.</span></span>  
  
## <a name="using-the-sample-data-wizard"></a><span data-ttu-id="56d98-117">使用示例数据向导</span><span class="sxs-lookup"><span data-stu-id="56d98-117">Using the Sample Data Wizard</span></span>  
  
#### <a name="to-separate-data-into-training-and-testing-sets"></a><span data-ttu-id="56d98-118">将数据分为定型集和测试集</span><span class="sxs-lookup"><span data-stu-id="56d98-118">To separate data into training and testing sets</span></span>  
  
1.  <span data-ttu-id="56d98-119">在 "**数据挖掘**" 功能区中，单击 "**示例数据**"。</span><span class="sxs-lookup"><span data-stu-id="56d98-119">In the **Data Mining** ribbon, click **Sample Data**.</span></span>  
  
2.  <span data-ttu-id="56d98-120">在 "**选择源数据**" 页上，指定要分区的**数据**是位于 Excel 范围还是表中，或在外部数据源中。</span><span class="sxs-lookup"><span data-stu-id="56d98-120">On the **Select Source Data** page, specify whether the **data** that you want to partition is in an Excel range or table, or in an external data source.</span></span>  
  
3.  <span data-ttu-id="56d98-121">在 "**选择抽样类型**" 页上，指定是否要通过随机采样创建定型和测试数据集，或通过过度抽样创建新的数据集。</span><span class="sxs-lookup"><span data-stu-id="56d98-121">On the **Select Sampling Type** page, specify whether you want to create training and test data sets by random sampling, or create a new data set by oversampling.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="56d98-122">如果使用的是外部数据源，则只能使用随机抽样选项。</span><span class="sxs-lookup"><span data-stu-id="56d98-122">If you are using an external data source, only the random sampling option is available.</span></span> <span data-ttu-id="56d98-123">如果您要使用外部数据进行过度抽样，则可以通过使用 Excel 数据连接，将外部数据导入 Excel 工作簿中，然后使用“示例数据”向导。</span><span class="sxs-lookup"><span data-stu-id="56d98-123">If you want to use oversampling with external data, you can import the data to an Excel workbook by using an Excel data connection, and then use the Sample Data wizard.</span></span>  
  
4.  <span data-ttu-id="56d98-124">设置特定于您所选的抽样方法的选项。</span><span class="sxs-lookup"><span data-stu-id="56d98-124">Set options specific to the sampling method that you selected.</span></span>  
  
    -   <span data-ttu-id="56d98-125">对于随机抽样，请指定测试是使用原始数据的百分比，还是使用测试数据集中的总行数。</span><span class="sxs-lookup"><span data-stu-id="56d98-125">For random sampling, specify either a percentage of the original data to use for testing, or the total number of rows to use in the test data set.</span></span>  
  
    -   <span data-ttu-id="56d98-126">对于过度抽样，请选择要强调的列和值。</span><span class="sxs-lookup"><span data-stu-id="56d98-126">For oversampling, select the column and value that you want to emphasize.</span></span> <span data-ttu-id="56d98-127">然后，指定新数据集中的总行数，以及应包括目标值的新数据集中的行百分比。</span><span class="sxs-lookup"><span data-stu-id="56d98-127">Then, specify the total number of rows in the new data set, and the percentage of rows in the new data set that should include the target value.</span></span>  
  
         <span data-ttu-id="56d98-128">过度抽样的目标值必须是一个离散值，不能对连续数值数据进行过度抽样。</span><span class="sxs-lookup"><span data-stu-id="56d98-128">The target value for oversampling must be a discrete value; you cannot oversample continuous numeric data.</span></span>  
  
5.  <span data-ttu-id="56d98-129">在 "**完成" 页**上，接受新数据集的默认名称，或键入新名称。</span><span class="sxs-lookup"><span data-stu-id="56d98-129">On the **Finish page**, accept the default names for the new data sets, or type a new name.</span></span>  
  
     <span data-ttu-id="56d98-130">该向导会为每个数据集创建新工作表。</span><span class="sxs-lookup"><span data-stu-id="56d98-130">The wizard creates new worksheets for each set of data.</span></span>  
  
 <span data-ttu-id="56d98-131">Excel 数据挖掘客户端中的多数向导还提供一个选项，用于将数据随机划入定型集和测试集。</span><span class="sxs-lookup"><span data-stu-id="56d98-131">Most of the wizards in the Data Mining Client for Excel also provide an option to randomly separate your data into training and testing sets.</span></span> <span data-ttu-id="56d98-132">但是，如果使用这些向导，则数据保留在同一工作表（或其他数据源）中，并在内部存储有关特定行是测试事例还是定型事例的信息。</span><span class="sxs-lookup"><span data-stu-id="56d98-132">However, if you use the wizards, your data stays in the same worksheet (or other data source), and the information about whether a particular row is a test case or training case is stored internally.</span></span> <span data-ttu-id="56d98-133">与此相反，当您使用 "**示例数据**" 向导时，测试数据和定型数据将输出到不同的工作表中，以便于引用。</span><span class="sxs-lookup"><span data-stu-id="56d98-133">In contrast, when you use the **Sample Data** wizard, the testing and training data are output to separate worksheets for easy reference.</span></span>  
  
## <a name="related-options"></a><span data-ttu-id="56d98-134">相关选项</span><span class="sxs-lookup"><span data-stu-id="56d98-134">Related Options</span></span>  
 <span data-ttu-id="56d98-135">在向导中前进时，将有以下选项：</span><span class="sxs-lookup"><span data-stu-id="56d98-135">As you progress through the wizard, you will have these options:</span></span>  
  
|<span data-ttu-id="56d98-136">选项</span><span class="sxs-lookup"><span data-stu-id="56d98-136">Options</span></span>|<span data-ttu-id="56d98-137">注释</span><span class="sxs-lookup"><span data-stu-id="56d98-137">Comments</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="56d98-138">“选择源数据”对话框（Excel 数据挖掘客户端）</span><span class="sxs-lookup"><span data-stu-id="56d98-138">Select Source Data Dialog Box (Data Mining Client for Excel)</span></span>|<span data-ttu-id="56d98-139">选择包含数据的 Excel 范围或表。</span><span class="sxs-lookup"><span data-stu-id="56d98-139">Select an Excel range or table that contains the data.</span></span> <span data-ttu-id="56d98-140">如果要使用外部数据，则可使用关系数据，但这些数据必须包括在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据源中。</span><span class="sxs-lookup"><span data-stu-id="56d98-140">If you want to use external data, the data can be relational, but it must be included in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="56d98-141">T</span><span class="sxs-lookup"><span data-stu-id="56d98-141">T</span></span>|  
|<span data-ttu-id="56d98-142">“选择抽样类型”页（Excel 数据挖掘客户端）</span><span class="sxs-lookup"><span data-stu-id="56d98-142">Select Sampling Type Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="56d98-143">如果您使用外部数据源，则会限制您只能使用随机抽样选项。</span><span class="sxs-lookup"><span data-stu-id="56d98-143">If you use an external data source, you are limited to using the random sampling option.</span></span> <span data-ttu-id="56d98-144">此外，还必须通过使用 "**行计数**" 选项来指定要在最终数据集中创建的行数。</span><span class="sxs-lookup"><span data-stu-id="56d98-144">Also, you must specify the number of rows to create in the final data set, by using the **Row count** option.</span></span> <span data-ttu-id="56d98-145">不能指定源数据的百分比。</span><span class="sxs-lookup"><span data-stu-id="56d98-145">You cannot specify a percentage of the source data.</span></span>|  
|<span data-ttu-id="56d98-146">“随机抽样类型”页（Excel 数据挖掘客户端）</span><span class="sxs-lookup"><span data-stu-id="56d98-146">Random Sampling Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="56d98-147">可从源复制行的某个百分比或特定行数。</span><span class="sxs-lookup"><span data-stu-id="56d98-147">You can copy a percentage of rows from the source, or a specific number of rows.</span></span>|  
|<span data-ttu-id="56d98-148">“过度抽样”页（Excel 数据挖掘客户端）</span><span class="sxs-lookup"><span data-stu-id="56d98-148">Oversampling Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="56d98-149">**目标状态**</span><span class="sxs-lookup"><span data-stu-id="56d98-149">**Target state**</span></span><br /><br /> <span data-ttu-id="56d98-150">从列表中选择在原始数据集中不常见的值。</span><span class="sxs-lookup"><span data-stu-id="56d98-150">Select a value from the list that is underrepresented in the original data set.</span></span> <span data-ttu-id="56d98-151">过度抽样将增加包含此状态的数据行的比例。</span><span class="sxs-lookup"><span data-stu-id="56d98-151">Oversampling will increase the proportion of data rows that include this state.</span></span><br /><br /> <span data-ttu-id="56d98-152">**样本大小**</span><span class="sxs-lookup"><span data-stu-id="56d98-152">**Sample size**</span></span><br /><br /> <span data-ttu-id="56d98-153">选择要提取的总行数。</span><span class="sxs-lookup"><span data-stu-id="56d98-153">Select the total number of rows to extract.</span></span> <span data-ttu-id="56d98-154">此值表示最终数据集的大小。</span><span class="sxs-lookup"><span data-stu-id="56d98-154">This value represents the size of the final data set.</span></span>|  
  
## <a name="other-sampling-options"></a><span data-ttu-id="56d98-155">其他抽样选项</span><span class="sxs-lookup"><span data-stu-id="56d98-155">Other Sampling Options</span></span>  
 <span data-ttu-id="56d98-156">如果此向导中的抽样选项不能满足您的需求，您可使用 SQL Server Integration Services (SSIS) 中的抽样转换功能从多个数据源中抽取行。</span><span class="sxs-lookup"><span data-stu-id="56d98-156">If the sampling options in this wizard do not meet your needs, you can use the sampling transformation in SQL Server Integration Services (SSIS) to sample rows from multiple data sources.</span></span>  
  
 <span data-ttu-id="56d98-157">有关详细信息，请参阅[行采样转换](../integration-services/data-flow/transformations/row-sampling-transformation.md)和[百分比抽样转换](../integration-services/data-flow/transformations/percentage-sampling-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="56d98-157">For more information, see [Row Sampling Transformation](../integration-services/data-flow/transformations/row-sampling-transformation.md) and [Percentage Sampling Transformation](../integration-services/data-flow/transformations/percentage-sampling-transformation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d98-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56d98-158">See Also</span></span>  
 [<span data-ttu-id="56d98-159">数据挖掘准备清单</span><span class="sxs-lookup"><span data-stu-id="56d98-159">Checklist of Preparation for Data Mining</span></span>](checklist-of-preparation-for-data-mining.md)  
  
  
