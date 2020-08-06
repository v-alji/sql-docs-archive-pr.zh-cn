---
title: 步骤 2：添加和配置平面文件连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9a77dd32-d8c2-4961-ad37-2a971f9d6043
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ba3adee2422af8b2df027f55ec84366b90ddd7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586844"
---
# <a name="step-2-adding-and-configuring-a-flat-file-connection-manager"></a><span data-ttu-id="70eb9-102">步骤 2：添加和配置平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="70eb9-102">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>
  <span data-ttu-id="70eb9-103">在本任务中，将在刚创建的包中添加一个平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="70eb9-103">In this task, you add a Flat File connection manager to the package that you just created.</span></span> <span data-ttu-id="70eb9-104">通过平面文件连接管理器，包可从平面文件中提取数据。</span><span class="sxs-lookup"><span data-stu-id="70eb9-104">A Flat File connection manager enables a package to extract data from a flat file.</span></span> <span data-ttu-id="70eb9-105">使用平面文件连接管理器，可以指定包从平面文件中提取数据时要应用的文件的名称与位置、区域设置与代码页以及文件格式，其中包括列分隔符。</span><span class="sxs-lookup"><span data-stu-id="70eb9-105">Using the Flat File connection manager, you can specify the file name and location, the locale and code page, and the file format, including column delimiters, to apply when the package extracts data from the flat file.</span></span> <span data-ttu-id="70eb9-106">另外，还可以为各个列手动指定数据类型；也可以使用“提供列类型建议”对话框，自动将提取出来的数据列映射到 **数据类型。** [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70eb9-106">In addition, you can manually specify the data type for the individual columns, or use the **Suggest Column Types** dialog box to automatically map the columns of extracted data to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] data types.</span></span>  
  
 <span data-ttu-id="70eb9-107">必须为要使用的每种文件格式创建一个新的平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="70eb9-107">You must create a new Flat File connection manager for each file format that you work with.</span></span> <span data-ttu-id="70eb9-108">因为本教程从多个数据格式完全相同的平面文件提取数据，所以只需为您的包添加和配置一个平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="70eb9-108">Because this tutorial extracts data from multiple flat files that have exactly the same data format, you will need to add and configure only one Flat File connection manager for your package.</span></span>  
  
 <span data-ttu-id="70eb9-109">在本教程中，将在平面文件连接管理器中配置以下属性：</span><span class="sxs-lookup"><span data-stu-id="70eb9-109">For this tutorial, you will configure the following properties in your Flat File connection manager:</span></span>  
  
-   <span data-ttu-id="70eb9-110">**列名：** 因为平面文件没有列名，因此平面文件连接管理器将创建默认的列名。</span><span class="sxs-lookup"><span data-stu-id="70eb9-110">**Column names:** Because the flat file does not have column names, the Flat File connection manager creates default column names.</span></span> <span data-ttu-id="70eb9-111">这些默认名称不能用于标识每个列代表的内容。</span><span class="sxs-lookup"><span data-stu-id="70eb9-111">These default names are not useful for identifying what each column represents.</span></span> <span data-ttu-id="70eb9-112">若要使这些默认名称更有用，需要将默认名称改为要加载平面文件数据的事实数据表匹配的名称。</span><span class="sxs-lookup"><span data-stu-id="70eb9-112">To make these default names more useful, you need to change the default names to names that match the fact table into which the flat file data is to be loaded.</span></span>  
  
-   <span data-ttu-id="70eb9-113">**数据映射：** 为平面文件连接管理器指定的数据类型映射，将由所有引用该连接管理器的平面文件数据源组件使用。</span><span class="sxs-lookup"><span data-stu-id="70eb9-113">**Data mappings:** The data type mappings that you specify for the Flat File connection manager will be used by all flat file data source components that reference the connection manager.</span></span> <span data-ttu-id="70eb9-114">可以使用平面文件连接管理器，或者使用“提供列类型建议”对话框来手动映射数据类型。 </span><span class="sxs-lookup"><span data-stu-id="70eb9-114">You can either manually map the data types by using the Flat File connection manager, or you can use the **Suggest Column Types** dialog box.</span></span> <span data-ttu-id="70eb9-115">在本教程中，将查看“提供列类型建议”对话框中建议的映射，然后在“平面文件连接管理器编辑器”对话框中手动设置必要的映射。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-115">In this tutorial, you will view the mappings suggested in the **Suggest Column Types** dialog box and then manually make the necessary mappings in the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="70eb9-116">平面文件连接管理器提供了有关数据文件的区域设置信息。</span><span class="sxs-lookup"><span data-stu-id="70eb9-116">The Flat File connection manager provides locale information about the data file.</span></span> <span data-ttu-id="70eb9-117">如果你的计算机未配置为使用区域选项 "英语 (美国) ，则必须在"**平面文件连接管理器编辑器**"对话框中设置其他属性。</span><span class="sxs-lookup"><span data-stu-id="70eb9-117">If your computer is not configured to use the regional option English (United States), you must set additional properties in the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
### <a name="to-add-a-flat-file-connection-manager-to-the-ssis-package"></a><span data-ttu-id="70eb9-118">向 SSIS 包添加平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="70eb9-118">To add a Flat File connection manager to the SSIS package</span></span>  
  
1.  <span data-ttu-id="70eb9-119">右键单击“连接管理器”区域中的任意位置，再单击“新建平面文件连接”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-119">Right-click anywhere in the **Connection Managers** area, and then click **New Flat File Connection**.</span></span>  
  
2.  <span data-ttu-id="70eb9-120">在“平面文件连接管理器编辑器”对话框的“连接管理器名称”字段中，键入“Sample Flat File Source Data”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-120">In the **Flat File Connection Manager Editor** dialog box, for **Connection manager name**, type **Sample Flat File Source Data**.</span></span>  
  
3.  <span data-ttu-id="70eb9-121">单击“浏览” 。</span><span class="sxs-lookup"><span data-stu-id="70eb9-121">Click **Browse**.</span></span>  
  
4.  <span data-ttu-id="70eb9-122">在“打开”对话框中，找到计算机上的 SampleCurrencyData.txt 文件。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-122">In the **Open** dialog box, locate the SampleCurrencyData.txt file on your machine.</span></span>  
  
     <span data-ttu-id="70eb9-123">示例数据与 [!INCLUDE[ssIS](../includes/ssis-md.md)] 课程包一起提供。</span><span class="sxs-lookup"><span data-stu-id="70eb9-123">The sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="70eb9-124">要下载示例数据和课程包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="70eb9-124">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="70eb9-125">导航到 [Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="70eb9-125">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="70eb9-126">单击 "**下载**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="70eb9-126">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="70eb9-127">单击 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="70eb9-127">Click the  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="70eb9-128">清除第一个数据行复选框中的“列名”。</span><span class="sxs-lookup"><span data-stu-id="70eb9-128">Clear the Column names in the first data row checkbox.</span></span>  
  
### <a name="to-set-locale-sensitive-properties"></a><span data-ttu-id="70eb9-129">设置受区域设置影响的属性</span><span class="sxs-lookup"><span data-stu-id="70eb9-129">To set locale sensitive properties</span></span>  
  
1.  <span data-ttu-id="70eb9-130">在“平面文件连接管理器编辑器”对话框中，单击“常规”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-130">In the **Flat File Connection Manager Editor** dialog box, click **General**.</span></span>  
  
2.  <span data-ttu-id="70eb9-131">将**区域**设置设置为英语 (美国) ，并将**代码页**设置为1252。</span><span class="sxs-lookup"><span data-stu-id="70eb9-131">Set **Locale** to English (United States) and **Code page** to 1252.</span></span>  
  
### <a name="to-rename-columns-in-the-flat-file-connection-manager"></a><span data-ttu-id="70eb9-132">重命名平面文件连接管理器中的列</span><span class="sxs-lookup"><span data-stu-id="70eb9-132">To rename columns in the Flat File connection manager</span></span>  
  
1.  <span data-ttu-id="70eb9-133">在“平面文件连接管理器编辑器”对话框中，单击“高级”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-133">In the **Flat File Connection Manager Editor** dialog box, click **Advanced**.</span></span>  
  
2.  <span data-ttu-id="70eb9-134">在属性窗格中，进行如下更改：</span><span class="sxs-lookup"><span data-stu-id="70eb9-134">In the property pane, make the following changes:</span></span>  
  
    -   <span data-ttu-id="70eb9-135">将**列 0**名称属性更改为 `AverageRate` 。</span><span class="sxs-lookup"><span data-stu-id="70eb9-135">Change the **Column 0** name property to `AverageRate`.</span></span>  
  
    -   <span data-ttu-id="70eb9-136">将 "**列 1**名称" 属性更改为 `CurrencyID` 。</span><span class="sxs-lookup"><span data-stu-id="70eb9-136">Change the **Column 1** name property to `CurrencyID`.</span></span>  
  
    -   <span data-ttu-id="70eb9-137">将**第2列**的 name 属性更改为 `CurrencyDate` 。</span><span class="sxs-lookup"><span data-stu-id="70eb9-137">Change the **Column 2** name property to `CurrencyDate`.</span></span>  
  
    -   <span data-ttu-id="70eb9-138">将**Column 3**名称属性更改为 `EndOfDayRate` 。</span><span class="sxs-lookup"><span data-stu-id="70eb9-138">Change the **Column 3** name property to `EndOfDayRate`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70eb9-139">默认情况下，所有四个列最初都设置为字符串数据类型 [DT_STR]，其 `OutputColumnWidth` 为 50。</span><span class="sxs-lookup"><span data-stu-id="70eb9-139">By default, all four of the columns are initially set to a string data type [DT_STR] with an `OutputColumnWidth` of 50.</span></span>  
  
### <a name="to-remap-column-data-types"></a><span data-ttu-id="70eb9-140">重新映射列数据类型</span><span class="sxs-lookup"><span data-stu-id="70eb9-140">To remap column data types</span></span>  
  
1.  <span data-ttu-id="70eb9-141">在“平面文件连接管理器编辑器”对话框中，单击“建议类型”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-141">In the **Flat File Connection Manager Editor** dialog box, click **Suggest Types**.</span></span>  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="70eb9-142">根据前 200 行数据自动建议最合适的数据类型。</span><span class="sxs-lookup"><span data-stu-id="70eb9-142">automatically suggests the most appropriate data types based on the first 200 rows of data.</span></span> <span data-ttu-id="70eb9-143">您还可以将这些建议选项改为增加或减少取样数据，以便指定整数数据或布尔数据的默认数据类型，或添加作为填充量添加到字符串列中的空格。</span><span class="sxs-lookup"><span data-stu-id="70eb9-143">You can also change these suggestion options to sample more or less data, to specify the default data type for integer or Boolean data, or to add spaces as padding to string columns.</span></span>  
  
     <span data-ttu-id="70eb9-144">现在，不对“提供列类型建议”对话框中的选项进行任何更改，单击“确定”使 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供列数据类型的建议。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-144">For now, make no changes to the options in the **Suggest Column Types** dialog box, and click **OK** to have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggest data types for columns.</span></span> <span data-ttu-id="70eb9-145">这样，将转到“平面文件连接管理器编辑器”对话框的“高级”窗格，在此可以查看 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 建议使用的列数据类型。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-145">This returns you to the **Advanced** pane of the **Flat File Connection Manager Editor** dialog box, where you can view the column data types suggested by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="70eb9-146">（如果单击“取消”，则不对列元数据提供任何建议，并使用默认字符串 (DT_STR) 数据类型。） \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70eb9-146">(If you click **Cancel**, no suggestions are made to column metadata and the default string (DT_STR) data type is used.)</span></span>  
  
     <span data-ttu-id="70eb9-147">在本教程中， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 为 SampleCurrencyData.txt 文件中的数据建议了下表第二列中显示的数据类型。</span><span class="sxs-lookup"><span data-stu-id="70eb9-147">In this tutorial, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggests the data types shown in the second column of the following table for the data from the SampleCurrencyData.txt file.</span></span> <span data-ttu-id="70eb9-148">但是，目标中的列要求的数据类型（将在以后的步骤中定义）显示在下表的最后一列。</span><span class="sxs-lookup"><span data-stu-id="70eb9-148">However, the data types that are required for the columns in the destination, which will be defined in a later step, are shown in the last column of the following table.</span></span>  
  
    |<span data-ttu-id="70eb9-149">平面文件列</span><span class="sxs-lookup"><span data-stu-id="70eb9-149">Flat File Column</span></span>|<span data-ttu-id="70eb9-150">建议的类型</span><span class="sxs-lookup"><span data-stu-id="70eb9-150">Suggested Type</span></span>|<span data-ttu-id="70eb9-151">目标列</span><span class="sxs-lookup"><span data-stu-id="70eb9-151">Destination Column</span></span>|<span data-ttu-id="70eb9-152">目标类型</span><span class="sxs-lookup"><span data-stu-id="70eb9-152">Destination Type</span></span>|  
    |----------------------|--------------------|------------------------|----------------------|  
    |<span data-ttu-id="70eb9-153">AverageRate</span><span class="sxs-lookup"><span data-stu-id="70eb9-153">AverageRate</span></span>|<span data-ttu-id="70eb9-154">float [DT_R4]</span><span class="sxs-lookup"><span data-stu-id="70eb9-154">float [DT_R4]</span></span>|<span data-ttu-id="70eb9-155">FactCurrency.AverageRate</span><span class="sxs-lookup"><span data-stu-id="70eb9-155">FactCurrency.AverageRate</span></span>|<span data-ttu-id="70eb9-156">FLOAT</span><span class="sxs-lookup"><span data-stu-id="70eb9-156">float</span></span>|  
    |<span data-ttu-id="70eb9-157">CurrencyID</span><span class="sxs-lookup"><span data-stu-id="70eb9-157">CurrencyID</span></span>|<span data-ttu-id="70eb9-158">string [DT_STR]</span><span class="sxs-lookup"><span data-stu-id="70eb9-158">string [DT_STR]</span></span>|<span data-ttu-id="70eb9-159">DimCurrency.CurrencyAlternateKey</span><span class="sxs-lookup"><span data-stu-id="70eb9-159">DimCurrency.CurrencyAlternateKey</span></span>|<span data-ttu-id="70eb9-160">nchar(3)</span><span class="sxs-lookup"><span data-stu-id="70eb9-160">nchar(3)</span></span>|  
    |<span data-ttu-id="70eb9-161">CurrencyDate</span><span class="sxs-lookup"><span data-stu-id="70eb9-161">CurrencyDate</span></span>|<span data-ttu-id="70eb9-162">date [DT_DATE]</span><span class="sxs-lookup"><span data-stu-id="70eb9-162">date [DT_DATE]</span></span>|<span data-ttu-id="70eb9-163">DimDate.FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="70eb9-163">DimDate.FullDateAlternateKey</span></span>|<span data-ttu-id="70eb9-164">date</span><span class="sxs-lookup"><span data-stu-id="70eb9-164">date</span></span>|  
    |<span data-ttu-id="70eb9-165">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="70eb9-165">EndOfDayRate</span></span>|<span data-ttu-id="70eb9-166">float [DT_R4]</span><span class="sxs-lookup"><span data-stu-id="70eb9-166">float [DT_R4]</span></span>|<span data-ttu-id="70eb9-167">FactCurrency.EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="70eb9-167">FactCurrency.EndOfDayRate</span></span>|<span data-ttu-id="70eb9-168">FLOAT</span><span class="sxs-lookup"><span data-stu-id="70eb9-168">float</span></span>|  
  
     <span data-ttu-id="70eb9-169">建议用于列的数据类型 `CurrencyID` 与目标表中字段的数据类型不兼容。</span><span class="sxs-lookup"><span data-stu-id="70eb9-169">The data type suggested for the `CurrencyID` column is incompatible with the data type of the field in the destination table.</span></span> <span data-ttu-id="70eb9-170">由于的数据类型 `DimCurrency.CurrencyAlternateKey` 为 nchar (3) ，因此 `CurrencyID` 必须从 string [DT_STR] 改为 string [DT_WSTR]。</span><span class="sxs-lookup"><span data-stu-id="70eb9-170">Because the data type of `DimCurrency.CurrencyAlternateKey` is nchar (3), `CurrencyID` must be changed from string [DT_STR] to string [DT_WSTR].</span></span> <span data-ttu-id="70eb9-171">此外，该字段 `DimDate.FullDateAlternateKey` 定义为 date 数据类型; 因此， `CurrencyDate` 需要从日期 [DT_Date] 改为数据库日期 [DT_DBDATE]。</span><span class="sxs-lookup"><span data-stu-id="70eb9-171">Additionally, the field `DimDate.FullDateAlternateKey` is defined as a date data type; therefore, `CurrencyDate` needs to be changed from date [DT_Date] to database date [DT_DBDATE].</span></span>  
  
2.  <span data-ttu-id="70eb9-172">在列表中，选择 "CurrencyID" 列，然后在 "属性" 窗格中，将列的数据类型 `CurrencyID` 从 string [DT_STR] 改为 Unicode string [DT_WSTR]。</span><span class="sxs-lookup"><span data-stu-id="70eb9-172">In the list, select the CurrencyID column and in the property pane, change the Data Type of column `CurrencyID` from string [DT_STR] to Unicode string [DT_WSTR].</span></span>  
  
3.  <span data-ttu-id="70eb9-173">在 "属性" 窗格中，将列的数据类型 `CurrencyDate` 从日期 [DT_DATE] 改为数据库日期 [DT_DBDATE]。</span><span class="sxs-lookup"><span data-stu-id="70eb9-173">In the property pane, change the data type of column `CurrencyDate` from date [DT_DATE] to database date [DT_DBDATE].</span></span>  
  
4.  <span data-ttu-id="70eb9-174">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="70eb9-174">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="70eb9-175">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="70eb9-175">Next Task in Lesson</span></span>  
 [<span data-ttu-id="70eb9-176">步骤 3：添加并配置 OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="70eb9-176">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
## <a name="see-also"></a><span data-ttu-id="70eb9-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70eb9-177">See Also</span></span>  
 <span data-ttu-id="70eb9-178">[平面文件连接管理器](connection-manager/file-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="70eb9-178">[Flat File Connection Manager](connection-manager/file-connection-manager.md) </span></span>  
 [<span data-ttu-id="70eb9-179">Integration Services 数据类型</span><span class="sxs-lookup"><span data-stu-id="70eb9-179">Integration Services Data Types</span></span>](data-flow/integration-services-data-types.md)  
  
  
