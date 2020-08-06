---
title: 第1课：创建项目和基本包 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a9ddc36ef242cc4e4b146e90dfa9de470e68d83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586820"
---
# <a name="lesson-1-creating-the-project-and-basic-package"></a><span data-ttu-id="61adc-102">第 1 课：创建项目和基本包</span><span class="sxs-lookup"><span data-stu-id="61adc-102">Lesson 1: Creating the Project and Basic Package</span></span>
  <span data-ttu-id="61adc-103">在本课中，将创建一个简单 ETL 包，该包可以从单个平面文件源中提取数据，使用两个查找转换组件转换该数据，然后将该数据写入 **AdventureWorksDW2012** 的 **FactCurrency**事实数据表中。</span><span class="sxs-lookup"><span data-stu-id="61adc-103">In this lesson, you will create a simple ETL package that extracts data from a single flat file source, transforms the data using two lookup transformation components, and writes that data to the **FactCurrency** fact table in **AdventureWorksDW2012**.</span></span> <span data-ttu-id="61adc-104">在本课中，您还将学习如何创建新包、添加和配置数据源和目标连接以及使用新的控制流和数据流组件。</span><span class="sxs-lookup"><span data-stu-id="61adc-104">As part of this lesson, you will learn how to create new packages, add and configure data source and destination connections, and work with new control flow and data flow components.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="61adc-105">本教程需要 **AdventureWorksDW2012** 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="61adc-105">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="61adc-106">有关安装和部署**AdventureWorksDW2012**的详细信息，请参阅[Microsoft SQL Server 产品示例： Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples)。</span><span class="sxs-lookup"><span data-stu-id="61adc-106">For more information on installing and deploying **AdventureWorksDW2012**, see [Microsoft SQL Server Product Samples: Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples).</span></span>  
  
## <a name="understanding-the-package-requirements"></a><span data-ttu-id="61adc-107">了解包要求</span><span class="sxs-lookup"><span data-stu-id="61adc-107">Understanding the Package Requirements</span></span>  
 <span data-ttu-id="61adc-108">本教程需要 Microsoft SQL Server Data Tools。</span><span class="sxs-lookup"><span data-stu-id="61adc-108">This tutorial requires Microsoft SQL Server Data Tools.</span></span>  
  
 <span data-ttu-id="61adc-109">有关安装 SQL Server Data Tools 的详细信息，请参阅 [SQL Server Data Tools 下载](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017)。</span><span class="sxs-lookup"><span data-stu-id="61adc-109">For more information on installing the SQL Server Data Tools see [SQL Server Data Tools Download](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017).</span></span>  
  
 <span data-ttu-id="61adc-110">在创建包之前，需要充分了解在源数据和目标数据中使用的格式。</span><span class="sxs-lookup"><span data-stu-id="61adc-110">Before creating a package, you need a good understanding of the formatting used in both the source data and the destination.</span></span> <span data-ttu-id="61adc-111">了解了这些数据格式后，便可定义将源数据映射到目标数据所需的转换。</span><span class="sxs-lookup"><span data-stu-id="61adc-111">Once you understand both of these data formats, you will be ready to define the transformations necessary to map the source data to the destination.</span></span>  
  
### <a name="looking-at-the-source"></a><span data-ttu-id="61adc-112">查看源</span><span class="sxs-lookup"><span data-stu-id="61adc-112">Looking at the Source</span></span>  
 <span data-ttu-id="61adc-113">在本教程中，源数据是平面文件 SampleCurrencyData.txt 中包含的一组历史货币数据。</span><span class="sxs-lookup"><span data-stu-id="61adc-113">For this tutorial, the source data is a set of historical currency data contained in the flat file, SampleCurrencyData.txt.</span></span> <span data-ttu-id="61adc-114">源数据具有以下四列：货币的平均汇率、货币键、日期键和收盘汇率。</span><span class="sxs-lookup"><span data-stu-id="61adc-114">The source data has the following four columns: the average rate of the currency, a currency key, a date key, and the end-of-day rate.</span></span>  
  
 <span data-ttu-id="61adc-115">下面是 SampleCurrencyData.txt 文件中所包含的源数据示例：</span><span class="sxs-lookup"><span data-stu-id="61adc-115">Here is an example of the source data contained in the SampleCurrencyData.txt file:</span></span>  
  
 `1.00070049USD9/3/05 0:001.001201442`  
  
 `1.00020004USD9/4/05 0:001`  
  
 `1.00020004USD9/5/05 0:001.001201442`  
  
 `1.00020004USD9/6/05 0:001`  
  
 `1.00020004USD9/7/05 0:001.00070049`  
  
 `1.00070049USD9/8/05 0:000.99980004`  
  
 `1.00070049USD9/9/05 0:001.001502253`  
  
 `1.00070049USD9/10/05 0:000.99990001`  
  
 `1.00020004USD9/11/05 0:001.001101211`  
  
 `1.00020004USD9/12/05 0:000.99970009`  
  
 <span data-ttu-id="61adc-116">在使用平面文件源数据时，需要了解平面文件连接管理器如何解释平面文件数据，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="61adc-116">When working with flat file source data, it is important to understand how the Flat File connection manager interprets the flat file data.</span></span> <span data-ttu-id="61adc-117">如果平面文件源是 Unicode 编码的，则平面文件连接管理将所有列定义为 [DT_WSTR]，默认列宽为 50。</span><span class="sxs-lookup"><span data-stu-id="61adc-117">If the flat file source is Unicode, the Flat File connection manager defines all columns as [DT_WSTR] with a default column width of 50.</span></span> <span data-ttu-id="61adc-118">如果平面文件源是 ANSI 编码的，则将列定义为 [DT_STR]，默认列宽为 50。</span><span class="sxs-lookup"><span data-stu-id="61adc-118">If the flat file source is ANSI-encoded, the columns are defined as [DT_STR] with a column width of 50.</span></span> <span data-ttu-id="61adc-119">您可能必须更改这些默认设置，才能使字符串列类型与所使用的数据更相符。</span><span class="sxs-lookup"><span data-stu-id="61adc-119">You will probably have to change these defaults to make the string column types more appropriate for your data.</span></span> <span data-ttu-id="61adc-120">为此，您需要查看将写入数据的目标的数据类型，然后在平面文件连接管理器中选择正确的类型。</span><span class="sxs-lookup"><span data-stu-id="61adc-120">To do this, you will need to look at the data type of the destination where the data will be written to and then choose the correct type within the Flat File connection manager.</span></span>  
  
### <a name="looking-at-the-destination"></a><span data-ttu-id="61adc-121">查看目标</span><span class="sxs-lookup"><span data-stu-id="61adc-121">Looking at the Destination</span></span>  
 <span data-ttu-id="61adc-122">源数据的最终目标是 **AdventureWorksDW** 中的 **FactCurrency**事实数据表。</span><span class="sxs-lookup"><span data-stu-id="61adc-122">The ultimate destination for the source data is the **FactCurrency** fact table in **AdventureWorksDW**.</span></span> <span data-ttu-id="61adc-123">**FactCurrency** 事实数据表有四列，并且与两个维度表有关系，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="61adc-123">The **FactCurrency** fact table has four columns, and has relationships to two dimension tables, as shown in the following table.</span></span>  
  
|<span data-ttu-id="61adc-124">列名</span><span class="sxs-lookup"><span data-stu-id="61adc-124">Column Name</span></span>|<span data-ttu-id="61adc-125">数据类型</span><span class="sxs-lookup"><span data-stu-id="61adc-125">Data Type</span></span>|<span data-ttu-id="61adc-126">查找表</span><span class="sxs-lookup"><span data-stu-id="61adc-126">Lookup Table</span></span>|<span data-ttu-id="61adc-127">查找列</span><span class="sxs-lookup"><span data-stu-id="61adc-127">Lookup Column</span></span>|  
|-----------------|---------------|------------------|-------------------|  
|<span data-ttu-id="61adc-128">AverageRate</span><span class="sxs-lookup"><span data-stu-id="61adc-128">AverageRate</span></span>|<span data-ttu-id="61adc-129">FLOAT</span><span class="sxs-lookup"><span data-stu-id="61adc-129">float</span></span>|<span data-ttu-id="61adc-130">无</span><span class="sxs-lookup"><span data-stu-id="61adc-130">None</span></span>|<span data-ttu-id="61adc-131">无</span><span class="sxs-lookup"><span data-stu-id="61adc-131">None</span></span>|  
|<span data-ttu-id="61adc-132">CurrencyKey</span><span class="sxs-lookup"><span data-stu-id="61adc-132">CurrencyKey</span></span>|<span data-ttu-id="61adc-133">int (FK)</span><span class="sxs-lookup"><span data-stu-id="61adc-133">int (FK)</span></span>|<span data-ttu-id="61adc-134">DimCurrency</span><span class="sxs-lookup"><span data-stu-id="61adc-134">DimCurrency</span></span>|<span data-ttu-id="61adc-135">CurrencyKey (PK)</span><span class="sxs-lookup"><span data-stu-id="61adc-135">CurrencyKey (PK)</span></span>|  
|<span data-ttu-id="61adc-136">DateKey</span><span class="sxs-lookup"><span data-stu-id="61adc-136">DateKey</span></span>|<span data-ttu-id="61adc-137">int (FK)</span><span class="sxs-lookup"><span data-stu-id="61adc-137">Int (FK)</span></span>|<span data-ttu-id="61adc-138">DimDate</span><span class="sxs-lookup"><span data-stu-id="61adc-138">DimDate</span></span>|<span data-ttu-id="61adc-139">DateKey (PK)</span><span class="sxs-lookup"><span data-stu-id="61adc-139">DateKey (PK)</span></span>|  
|<span data-ttu-id="61adc-140">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="61adc-140">EndOfDayRate</span></span>|<span data-ttu-id="61adc-141">FLOAT</span><span class="sxs-lookup"><span data-stu-id="61adc-141">float</span></span>|<span data-ttu-id="61adc-142">无</span><span class="sxs-lookup"><span data-stu-id="61adc-142">None</span></span>|<span data-ttu-id="61adc-143">无</span><span class="sxs-lookup"><span data-stu-id="61adc-143">None</span></span>|  
  
### <a name="mapping-source-data-to-be-compatible-with-the-destination"></a><span data-ttu-id="61adc-144">将源数据映射为与目标兼容</span><span class="sxs-lookup"><span data-stu-id="61adc-144">Mapping Source Data to be Compatible with the Destination</span></span>  
 <span data-ttu-id="61adc-145">对源数据和目标数据的分析指出需要查找 **CurrencyKey** 和 **DateKey** 值。</span><span class="sxs-lookup"><span data-stu-id="61adc-145">Analysis of the source and destination data formats indicates that lookups will be necessary for the **CurrencyKey** and **DateKey** values.</span></span> <span data-ttu-id="61adc-146">将执行这些查找的转换通过使用 **DimCurrency** 和 **DimDate** 维度表中的备用键来获取 **CurrencyKey** 和 **DateKey** 值。</span><span class="sxs-lookup"><span data-stu-id="61adc-146">The transformations that will perform these lookups will obtain the **CurrencyKey** and **DateKey** values by using the alternate keys from **DimCurrency** and **DimDate** dimension tables.</span></span>  
  
|<span data-ttu-id="61adc-147">平面文件列</span><span class="sxs-lookup"><span data-stu-id="61adc-147">Flat File Column</span></span>|<span data-ttu-id="61adc-148">表名称</span><span class="sxs-lookup"><span data-stu-id="61adc-148">Table Name</span></span>|<span data-ttu-id="61adc-149">列名</span><span class="sxs-lookup"><span data-stu-id="61adc-149">Column Name</span></span>|<span data-ttu-id="61adc-150">数据类型</span><span class="sxs-lookup"><span data-stu-id="61adc-150">Data Type</span></span>|  
|----------------------|----------------|-----------------|---------------|  
|<span data-ttu-id="61adc-151">0</span><span class="sxs-lookup"><span data-stu-id="61adc-151">0</span></span>|<span data-ttu-id="61adc-152">AdventureWorksDW2012</span><span class="sxs-lookup"><span data-stu-id="61adc-152">FactCurrency</span></span>|<span data-ttu-id="61adc-153">AverageRate</span><span class="sxs-lookup"><span data-stu-id="61adc-153">AverageRate</span></span>|<span data-ttu-id="61adc-154">FLOAT</span><span class="sxs-lookup"><span data-stu-id="61adc-154">float</span></span>|  
|<span data-ttu-id="61adc-155">1</span><span class="sxs-lookup"><span data-stu-id="61adc-155">1</span></span>|<span data-ttu-id="61adc-156">DimCurrency</span><span class="sxs-lookup"><span data-stu-id="61adc-156">DimCurrency</span></span>|<span data-ttu-id="61adc-157">CurrencyAlternateKey</span><span class="sxs-lookup"><span data-stu-id="61adc-157">CurrencyAlternateKey</span></span>|<span data-ttu-id="61adc-158">nchar(3)</span><span class="sxs-lookup"><span data-stu-id="61adc-158">nchar (3)</span></span>|  
|<span data-ttu-id="61adc-159">2</span><span class="sxs-lookup"><span data-stu-id="61adc-159">2</span></span>|<span data-ttu-id="61adc-160">DimDate</span><span class="sxs-lookup"><span data-stu-id="61adc-160">DimDate</span></span>|<span data-ttu-id="61adc-161">FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="61adc-161">FullDateAlternateKey</span></span>|<span data-ttu-id="61adc-162">date</span><span class="sxs-lookup"><span data-stu-id="61adc-162">date</span></span>|  
|<span data-ttu-id="61adc-163">3</span><span class="sxs-lookup"><span data-stu-id="61adc-163">3</span></span>|<span data-ttu-id="61adc-164">AdventureWorksDW2012</span><span class="sxs-lookup"><span data-stu-id="61adc-164">FactCurrency</span></span>|<span data-ttu-id="61adc-165">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="61adc-165">EndOfDayRate</span></span>|<span data-ttu-id="61adc-166">FLOAT</span><span class="sxs-lookup"><span data-stu-id="61adc-166">float</span></span>|  
  
## <a name="lesson-tasks"></a><span data-ttu-id="61adc-167">课程任务</span><span class="sxs-lookup"><span data-stu-id="61adc-167">Lesson Tasks</span></span>  
 <span data-ttu-id="61adc-168">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="61adc-168">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="61adc-169">步骤 1：创建新的 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="61adc-169">Step 1: Creating a New Integration Services Project</span></span>](lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [<span data-ttu-id="61adc-170">步骤 2：添加和配置平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="61adc-170">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [<span data-ttu-id="61adc-171">步骤 3：添加并配置 OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="61adc-171">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [<span data-ttu-id="61adc-172">步骤 4：将数据流任务添加到包</span><span class="sxs-lookup"><span data-stu-id="61adc-172">Step 4: Adding a Data Flow Task to the Package</span></span>](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [<span data-ttu-id="61adc-173">步骤 5：添加并配置平面文件源</span><span class="sxs-lookup"><span data-stu-id="61adc-173">Step 5: Adding and Configuring the Flat File Source</span></span>](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [<span data-ttu-id="61adc-174">步骤 6：添加并配置查找转换</span><span class="sxs-lookup"><span data-stu-id="61adc-174">Step 6: Adding and Configuring the Lookup Transformations</span></span>](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [<span data-ttu-id="61adc-175">步骤 7：添加并配置 OLE DB 目标</span><span class="sxs-lookup"><span data-stu-id="61adc-175">Step 7: Adding and Configuring the OLE DB Destination</span></span>](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [<span data-ttu-id="61adc-176">步骤 8：使 Lesson 1 包更易理解</span><span class="sxs-lookup"><span data-stu-id="61adc-176">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [<span data-ttu-id="61adc-177">步骤 9：测试 Lesson 1 教程包</span><span class="sxs-lookup"><span data-stu-id="61adc-177">Step 9: Testing the Lesson 1 Tutorial Package</span></span>](lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="61adc-178">开始课程</span><span class="sxs-lookup"><span data-stu-id="61adc-178">Start the Lesson</span></span>  
 [<span data-ttu-id="61adc-179">步骤 1：创建新的 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="61adc-179">Step 1: Creating a New Integration Services Project</span></span>](lesson-1-1-creating-a-new-integration-services-project.md)  
  
  
