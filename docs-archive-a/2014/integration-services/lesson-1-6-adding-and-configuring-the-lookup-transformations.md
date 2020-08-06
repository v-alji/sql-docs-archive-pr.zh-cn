---
title: 步骤 6：添加并配置查找转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c59f723-9707-4407-80ae-f05f483cf65f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 96b0a848508c19eb24cf1538244a39fcec57361a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586825"
---
# <a name="step-6-adding-and-configuring-the-lookup-transformations"></a><span data-ttu-id="277ed-102">步骤 6：添加并配置查找转换</span><span class="sxs-lookup"><span data-stu-id="277ed-102">Step 6: Adding and Configuring the Lookup Transformations</span></span>
  <span data-ttu-id="277ed-103">在配置用于从源文件中提取数据的平面文件源后，下一个任务是定义获取 **CurrencyKey** 和 **DateKey**值所需的查找转换。</span><span class="sxs-lookup"><span data-stu-id="277ed-103">After you have configured the Flat File source to extract data from the source file, the next task is to define the Lookup transformations needed to obtain the values for the **CurrencyKey** and **DateKey**.</span></span> <span data-ttu-id="277ed-104">查找转换通过将指定输入列中的数据联接到引用数据集中的列来执行查找。</span><span class="sxs-lookup"><span data-stu-id="277ed-104">A Lookup transformation performs a lookup by joining data in the specified input column to a column in a reference dataset.</span></span> <span data-ttu-id="277ed-105">引用数据集可以是现有的表或视图，也可以是新表或 SQL 语句的结果。</span><span class="sxs-lookup"><span data-stu-id="277ed-105">The reference dataset can be an existing table or view, a new table, or the result of an SQL statement.</span></span> <span data-ttu-id="277ed-106">在本教程中，查找转换使用 OLE DB 连接管理器连接到包含引用数据集的源数据的数据库。</span><span class="sxs-lookup"><span data-stu-id="277ed-106">In this tutorial, the Lookup transformation uses an OLE DB connection manager to connect to the database that contains the data that is the source of the reference dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="277ed-107">还可以配置查找转换，以连接到包含引用数据集的缓存。</span><span class="sxs-lookup"><span data-stu-id="277ed-107">You can also configure the Lookup transformation to connect to a cache that contains the reference dataset.</span></span> <span data-ttu-id="277ed-108">有关详细信息，请参阅 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="277ed-108">For more information, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="277ed-109">对于本教程，您将向包中添加以下两个查找转换组件并对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="277ed-109">For this tutorial, you will add and configure the following two Lookup transformation components to the package:</span></span>  
  
-   <span data-ttu-id="277ed-110">一个转换是根据平面文件中匹配的“CurrencyID”\*\*\*\* 列值对“DimCurrency”\*\*\*\* 维度表的“CurrencyKey”\*\*\*\* 列中的值执行查找。</span><span class="sxs-lookup"><span data-stu-id="277ed-110">One transformation to perform a lookup of values from the **CurrencyKey** column of the **DimCurrency** dimension table based on matching **CurrencyID** column values from the flat file.</span></span>  
  
-   <span data-ttu-id="277ed-111">一个转换是根据平面文件中匹配的“CurrencyDate”\*\*\*\* 列值对“DimDate”\*\*\*\* 维度表的“DateKey”\*\*\*\* 列中的值执行查找。</span><span class="sxs-lookup"><span data-stu-id="277ed-111">One transformation to perform a lookup of values from the **DateKey** column of the **DimDate** dimension table based on matching **CurrencyDate** column values from the flat file.</span></span>  
  
 <span data-ttu-id="277ed-112">无论在哪种情况下，查找转换都将使用前面创建的 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="277ed-112">In both cases, the Lookup transformation will utilize the OLE DB connection manager that you previously created.</span></span>  
  
### <a name="to-add-and-configure-the-lookup-currency-key-transformation"></a><span data-ttu-id="277ed-113">添加并配置 Lookup Currency Key 转换</span><span class="sxs-lookup"><span data-stu-id="277ed-113">To add and configure the Lookup Currency Key transformation</span></span>  
  
1.  <span data-ttu-id="277ed-114">在 " **SSIS 工具箱**" 中，展开 "**常规**"，然后将 "**查找**" 拖动到 "数据流" 选项卡的设计图**面上。** 将查找直接置于**提取示例货币数据**源下面。</span><span class="sxs-lookup"><span data-stu-id="277ed-114">In the **SSIS Toolbox**, expand **Common**, and then drag **Lookup** onto the design surface of the **Data Flow** tab. Place Lookup directly below the **Extract Sample Currency Data** source.</span></span>  
  
2.  <span data-ttu-id="277ed-115">单击“Extract Sample Currency Data”\*\*\*\* 平面文件源，然后将绿色箭头拖到新添加的“查找”\*\*\*\* 转换中，以连接这两个组件。</span><span class="sxs-lookup"><span data-stu-id="277ed-115">Click the **Extract Sample Currency Data** flat file source and drag the green arrow onto the newly added **Lookup** transformation to connect the two components.</span></span>  
  
3.  <span data-ttu-id="277ed-116">在“数据流”\*\*\*\* 设计图面上，单击“查找”\*\*\*\* 转换中的“查找”\*\*\*\*，然后将该名称更改为 **Lookup Currency Key**。</span><span class="sxs-lookup"><span data-stu-id="277ed-116">On the **Data Flow** design surface, click **Lookup** in the **Lookup** transformation, and change the name to **Lookup Currency Key**.</span></span>  
  
4.  <span data-ttu-id="277ed-117">双击 **Lookup CurrencyKey** 转换，以显示查找转换编辑器。</span><span class="sxs-lookup"><span data-stu-id="277ed-117">Double-click the **Lookup CurrencyKey** transformation to display the Lookup Transformation Editor.</span></span>  
  
5.  <span data-ttu-id="277ed-118">在“常规”  页上，进行以下选择：</span><span class="sxs-lookup"><span data-stu-id="277ed-118">On the **General** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="277ed-119">选择“完全缓存”  。</span><span class="sxs-lookup"><span data-stu-id="277ed-119">Select **Full cache**.</span></span>  
  
    2.  <span data-ttu-id="277ed-120">在 **“连接类型”** 区域，选择 **“OLE DB 连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="277ed-120">In the **Connection type** area, select **OLE DB connection manager**.</span></span>  
  
6.  <span data-ttu-id="277ed-121">在“连接”  页上，进行以下选择：</span><span class="sxs-lookup"><span data-stu-id="277ed-121">On the **Connection** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="277ed-122">在“OLE DB 连接管理器”  对话框中，确保显示 **localhost.AdventureWorksDW2012**。</span><span class="sxs-lookup"><span data-stu-id="277ed-122">In the **OLE DB connection manager** dialog box, ensure that **localhost.AdventureWorksDW2012** is displayed.</span></span>  
  
    2.  <span data-ttu-id="277ed-123">选择“使用 SQL 查询的结果”\*\*\*\*，然后键入或复制以下 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="277ed-123">Select **Use results of an SQL query**, and then type or copy the following SQL statement:</span></span>  
  
        ```  
        select * from (select * from [dbo].[DimCurrency]) as refTable  
        where [refTable].[CurrencyAlternateKey] = 'ARS'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'AUD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'BRL'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CAD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CNY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'DEM'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'EUR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'FRF'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'GBP'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'JPY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'MXN'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'SAR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'USD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'VEB'  
        ```  
  
7.  <span data-ttu-id="277ed-124">在“列”\*\*\*\* 页上，进行以下选择：</span><span class="sxs-lookup"><span data-stu-id="277ed-124">On the **Columns** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="277ed-125">在“可用输入列”\*\*\*\* 面板中，将“CurrencyID”\*\*\*\* 拖到“可用查找列”\*\*\*\* 面板的“CurrencyAlternateKey”\*\*\*\* 上。</span><span class="sxs-lookup"><span data-stu-id="277ed-125">In the **Available Input Columns** panel, drag **CurrencyID** to the **Available Lookup Columns** panel and drop it on **CurrencyAlternateKey**.</span></span>  
  
    2.  <span data-ttu-id="277ed-126">在“可用查找列”\*\*\*\* 列表中，选中“CurrencyKey”\*\*\*\* 左侧的复选框。</span><span class="sxs-lookup"><span data-stu-id="277ed-126">In the **Available Lookup Columns** list, select the check box to the left of **CurrencyKey**.</span></span>  
  
8.  <span data-ttu-id="277ed-127">单击“确定”\*\*\*\* 返回“数据流”\*\*\*\* 设计图面。</span><span class="sxs-lookup"><span data-stu-id="277ed-127">Click **OK** to return to the **Data Flow** design surface.</span></span>  
  
9. <span data-ttu-id="277ed-128">右键单击“Lookup Currency Key”转换，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="277ed-128">Right-click the Lookup Currency Key transformation, click **Properties**.</span></span>  
  
10. <span data-ttu-id="277ed-129">在属性窗口中，验证 `LocaleID` 属性是否设置为**英语 (美国) \*\* ，并将**DefaultCodePage**属性设置为**1252\*\*。</span><span class="sxs-lookup"><span data-stu-id="277ed-129">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the **DefaultCodePage** property is set to **1252**.</span></span>  
  
### <a name="to-add-and-configure-the--lookup-datekey-transformation"></a><span data-ttu-id="277ed-130">添加并配置 Lookup DateKey 转换</span><span class="sxs-lookup"><span data-stu-id="277ed-130">To add and configure the  Lookup DateKey transformation</span></span>  
  
1.  <span data-ttu-id="277ed-131">在“SSIS 工具箱”\*\*\*\* 中，将“查找”\*\*\*\* 拖到“数据流”\*\*\*\* 设计图面上。</span><span class="sxs-lookup"><span data-stu-id="277ed-131">In the **SSIS Toolbox**, drag **Lookup** onto the **Data Flow** design surface.</span></span> <span data-ttu-id="277ed-132">将“查找”直接放置在 **Lookup Currency Key** 转换的下面。</span><span class="sxs-lookup"><span data-stu-id="277ed-132">Place Lookup directly below the **Lookup Currency Key** transformation.</span></span>  
  
2.  <span data-ttu-id="277ed-133">单击 **Lookup Currency Key** 转换，并将绿色箭头拖动到新添加的“查找”\*\*\*\* 转换中，以连接这两个组件。</span><span class="sxs-lookup"><span data-stu-id="277ed-133">Click the **Lookup Currency Key** transformation and drag the green arrow onto the newly added **Lookup** transformation to connect the two components.</span></span>  
  
3.  <span data-ttu-id="277ed-134">在“选择输入输出”\*\*\*\* 对话框中，单击“输出”\*\*\*\* 列表框中的“查找匹配输出”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="277ed-134">In the **Input Output Selection** dialog box, click **Lookup Match Output** in the **Output** list box, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="277ed-135">在“数据流”\*\*\*\* 设计图面上，在新添加的“查找”\*\*\*\* 转换中单击“查找”\*\*\*\*，然后将名称更改为 **Lookup Date Key**。</span><span class="sxs-lookup"><span data-stu-id="277ed-135">On the **Data Flow** design surface, click **Lookup** in the newly added **Lookup** transformation, and change the name to **Lookup Date Key**.</span></span>  
  
5.  <span data-ttu-id="277ed-136">双击 **Lookup Date Key** 转换。</span><span class="sxs-lookup"><span data-stu-id="277ed-136">Double-click the **Lookup Date Key** transformation.</span></span>  
  
6.  <span data-ttu-id="277ed-137">在“常规”\*\*\*\* 页上，选择“部分缓存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="277ed-137">On the **General** page, select **Partial cache**.</span></span>  
  
7.  <span data-ttu-id="277ed-138">在“连接”\*\*\*\* 页上，进行以下选择：</span><span class="sxs-lookup"><span data-stu-id="277ed-138">On the **Connection** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="277ed-139">在“OLEDB 连接管理器”\*\*\*\* 对话框中，确保已显示 **localhost.AdventureWorksDW2012**。</span><span class="sxs-lookup"><span data-stu-id="277ed-139">In the **OLEDB connection manager** dialog box, ensure that **localhost.AdventureWorksDW2012** is displayed.</span></span>  
  
    2.  <span data-ttu-id="277ed-140">在“使用表或视图”\*\*\*\* 框中，键入或选择 **[dbo].[DimDate]**。</span><span class="sxs-lookup"><span data-stu-id="277ed-140">In the **Use a table or view** box, type or select **[dbo].[DimDate]**.</span></span>  
  
8.  <span data-ttu-id="277ed-141">在“列”\*\*\*\* 页上，进行以下选择：</span><span class="sxs-lookup"><span data-stu-id="277ed-141">On the **Columns** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="277ed-142">在“可用输入列”\*\*\*\* 面板中，将“CurrencyDate”\*\*\*\* 拖到“可用查找列”\*\*\*\* 面板的“FullDateAlternateKey”\*\*\*\* 上。</span><span class="sxs-lookup"><span data-stu-id="277ed-142">In the **Available Input Columns** panel, drag **CurrencyDate** to the **Available Lookup Columns** panel and drop it on **FullDateAlternateKey**.</span></span>  
  
    2.  <span data-ttu-id="277ed-143">在“可用查找列”\*\*\*\* 列表中，选中“DateKey”\*\*\*\* 左侧的复选框。</span><span class="sxs-lookup"><span data-stu-id="277ed-143">In the **Available Lookup Columns** list, select the check box to the left of **DateKey**.</span></span>  
  
9. <span data-ttu-id="277ed-144">在“高级”\*\*\*\* 页上，查看缓存选项。</span><span class="sxs-lookup"><span data-stu-id="277ed-144">On the **Advanced** page, review the caching options.</span></span>  
  
10. <span data-ttu-id="277ed-145">单击“确定”\*\*\*\* 返回“数据流”\*\*\*\* 设计图面。</span><span class="sxs-lookup"><span data-stu-id="277ed-145">Click **OK** to return to the **Data Flow** design surface.</span></span>  
  
11. <span data-ttu-id="277ed-146">双击“Lookup Date Key”转换，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="277ed-146">Right-click the Lookup Date Key transformation and click **Properties.**</span></span>  
  
12. <span data-ttu-id="277ed-147">在属性窗口中，验证 `LocaleID` 属性是否设置为**英语 (美国) \*\* ，并将**DefaultCodePage**属性设置为**1252\*\*。</span><span class="sxs-lookup"><span data-stu-id="277ed-147">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the **DefaultCodePage** property is set to **1252**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="277ed-148">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="277ed-148">Next Task in Lesson</span></span>  
 [<span data-ttu-id="277ed-149">步骤 7：添加并配置 OLE DB 目标</span><span class="sxs-lookup"><span data-stu-id="277ed-149">Step 7: Adding and Configuring the OLE DB Destination</span></span>](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
## <a name="see-also"></a><span data-ttu-id="277ed-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="277ed-150">See Also</span></span>  
 [<span data-ttu-id="277ed-151">查找转换</span><span class="sxs-lookup"><span data-stu-id="277ed-151">Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
