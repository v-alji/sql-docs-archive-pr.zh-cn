---
title: 数据事件探查任务和查看器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], about data profiling
- data profiling
- profiling data
ms.assetid: 756840e3-aa09-45cd-9951-1a17af4b5925
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ae15d1cc75f8db04c36a830e44d07800c5aecf75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580824"
---
# <a name="data-profiling-task-and-viewer"></a><span data-ttu-id="01124-102">数据事件探查任务和查看器</span><span class="sxs-lookup"><span data-stu-id="01124-102">Data Profiling Task and Viewer</span></span>
  <span data-ttu-id="01124-103">数据事件探查任务在提取、转换和加载数据的过程中提供数据事件探查功能。</span><span class="sxs-lookup"><span data-stu-id="01124-103">The Data Profiling task provides data profiling functionality inside the process of extracting, transforming, and loading data.</span></span> <span data-ttu-id="01124-104">使用数据事件探查任务，有以下好处：</span><span class="sxs-lookup"><span data-stu-id="01124-104">By using the Data Profiling task, you can achieve the following benefits:</span></span>  
  
-   <span data-ttu-id="01124-105">更有效地分析源数据</span><span class="sxs-lookup"><span data-stu-id="01124-105">Analyze the source data more effectively</span></span>  
  
-   <span data-ttu-id="01124-106">更好地了解源数据</span><span class="sxs-lookup"><span data-stu-id="01124-106">Understand the source data better</span></span>  
  
-   <span data-ttu-id="01124-107">将数据引入数据仓库之前防止数据质量问题。</span><span class="sxs-lookup"><span data-stu-id="01124-107">Prevent data quality problems before they are introduced into the data warehouse.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="01124-108">数据事件探查任务仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中存储的数据。</span><span class="sxs-lookup"><span data-stu-id="01124-108">The Data Profiling task works only with data that is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="01124-109">它不适用于第三方或基于文件的数据源。</span><span class="sxs-lookup"><span data-stu-id="01124-109">It does not work with third-party or file-based data sources.</span></span>  
  
## <a name="data-profiling-overview"></a><span data-ttu-id="01124-110">数据事件探查概述</span><span class="sxs-lookup"><span data-stu-id="01124-110">Data Profiling Overview</span></span>  
 <span data-ttu-id="01124-111">数据质量对所有业务都至关重要。</span><span class="sxs-lookup"><span data-stu-id="01124-111">Data quality is important to every business.</span></span> <span data-ttu-id="01124-112">由于企业将分析和业务智能系统建立在他们的事务系统之上，因此关键绩效指标和数据挖掘预测的可靠性完全取决于所依据的数据的有效性。</span><span class="sxs-lookup"><span data-stu-id="01124-112">As enterprises build analytical and business intelligence systems on top of their transactional systems, the reliability of key performance indicators and of data mining predictions depends completely on the validity of the data on which they are based.</span></span> <span data-ttu-id="01124-113">不过，尽管数据的有效性对于业务决策越来越重要，但如何确保该数据有效也越来越具有挑战性。</span><span class="sxs-lookup"><span data-stu-id="01124-113">But although the importance of valid data for business decision-making is increasing, the challenge of making sure of this data's validity is also increasing.</span></span> <span data-ttu-id="01124-114">因为，数据在源源不断地从各种系统和源以及大量用户处流入企业。</span><span class="sxs-lookup"><span data-stu-id="01124-114">Data is streaming into the enterprise constantly from diverse systems and sources, and a large numbers of users.</span></span>  
  
 <span data-ttu-id="01124-115">数据质量的度量难以定义，原因是度量特定于域或应用程序。</span><span class="sxs-lookup"><span data-stu-id="01124-115">Metrics for data quality can be difficult to define because they are specific to the domain or the application.</span></span> <span data-ttu-id="01124-116">一个常用的定义数据质量的方法就是数据事件探查。</span><span class="sxs-lookup"><span data-stu-id="01124-116">One common approach to defining data quality is data profiling.</span></span>  
  
 <span data-ttu-id="01124-117">数据配置文件是聚合统计信息的集合，其中可能包含下面的信息：</span><span class="sxs-lookup"><span data-stu-id="01124-117">A data profile is a collection of aggregate statistics about data that might include the following:</span></span>  
  
-   <span data-ttu-id="01124-118">Customer 表中的行数。</span><span class="sxs-lookup"><span data-stu-id="01124-118">The number of rows in the Customer table.</span></span>  
  
-   <span data-ttu-id="01124-119">State 列中非重复的值的数目。</span><span class="sxs-lookup"><span data-stu-id="01124-119">The number of distinct values in the State column.</span></span>  
  
-   <span data-ttu-id="01124-120">Zip 列中 null 值或缺失值的数目。</span><span class="sxs-lookup"><span data-stu-id="01124-120">The number of null or missing values in the Zip column.</span></span>  
  
-   <span data-ttu-id="01124-121">City 列中值的分布。</span><span class="sxs-lookup"><span data-stu-id="01124-121">The distribution of values in the City column.</span></span>  
  
-   <span data-ttu-id="01124-122">State 列对 Zip 列的函数依赖强度，即对于指定的邮政编码值，省/市/自治区应始终是一样的。</span><span class="sxs-lookup"><span data-stu-id="01124-122">The strength of the functional dependency of the State column on the Zip column-that is, the state should always be the same for a given zip value.</span></span>  
  
 <span data-ttu-id="01124-123">数据配置文件提供的统计信息为您提供了所需信息，可以有效地最大限度降低使用源数据过程中可能出现的质量问题。</span><span class="sxs-lookup"><span data-stu-id="01124-123">The statistics that a data profile provides gives you the information that you need in order to effectively minimize the quality issues that might occur from using the source data.</span></span>  
  
## <a name="integration-services-and-data-profiling"></a><span data-ttu-id="01124-124">Integration Services 和数据事件探查</span><span class="sxs-lookup"><span data-stu-id="01124-124">Integration Services and Data Profiling</span></span>  
 <span data-ttu-id="01124-125">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中，数据事件探查过程包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="01124-125">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the data profiling process consist of the following steps:</span></span>  
  
 <span data-ttu-id="01124-126">**步骤 1：设置数据事件探查任务**</span><span class="sxs-lookup"><span data-stu-id="01124-126">**Step 1: Setting up the Data Profiling Task**</span></span>  
 <span data-ttu-id="01124-127">数据事件探查任务是用于配置要计算的配置文件的任务。</span><span class="sxs-lookup"><span data-stu-id="01124-127">The Data Profiling task is a task that you use to configure the profiles that you want to compute.</span></span> <span data-ttu-id="01124-128">运行包含数据事件探查任务的包以计算配置文件。</span><span class="sxs-lookup"><span data-stu-id="01124-128">You then run the package that contains the Data Profiling task to compute the profiles.</span></span> <span data-ttu-id="01124-129">该任务将配置文件输出以 XML 格式保存到文件或包变量。</span><span class="sxs-lookup"><span data-stu-id="01124-129">The task saves the profile output in XML format to a file or a package variable.</span></span>  
  
 <span data-ttu-id="01124-130">**详细信息：** [设置数据事件探查任务](data-profiling-task.md)</span><span class="sxs-lookup"><span data-stu-id="01124-130">**For more information:** [Setup of the Data Profiling Task](data-profiling-task.md)</span></span>  
  
 <span data-ttu-id="01124-131">**步骤 2：查看数据事件探查任务计算的配置文件**</span><span class="sxs-lookup"><span data-stu-id="01124-131">**Step 2: Reviewing the Profiles that the Data Profiling Task Computes**</span></span>  
 <span data-ttu-id="01124-132">若要查看数据事件探查任务计算的数据配置文件，请将输出发送到文件，然后使用数据配置文件查看器。</span><span class="sxs-lookup"><span data-stu-id="01124-132">To view the data profiles that the Data Profiling task computes, you send the output to a file, and then you use the Data Profile Viewer.</span></span> <span data-ttu-id="01124-133">此查看器是一种独立的实用工具，可以通过可选的明细功能以摘要的格式和以详细信息的格式显示配置文件输出。</span><span class="sxs-lookup"><span data-stu-id="01124-133">This viewer is a stand-alone utility that displays the profile output in both summary and detail format with optional drilldown capability.</span></span>  
  
 <span data-ttu-id="01124-134">**详细信息：** [数据配置文件查看器](data-profile-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="01124-134">**For more information:** [Data Profile Viewer](data-profile-viewer.md)</span></span>  
  
### <a name="addition-of-conditional-logic-to-the-data-profiling-workflow"></a><span data-ttu-id="01124-135">向数据事件探查工作流添加条件逻辑</span><span class="sxs-lookup"><span data-stu-id="01124-135">Addition of Conditional Logic to the Data Profiling Workflow</span></span>  
 <span data-ttu-id="01124-136">数据事件探查任务不包含内置功能，即无法根据配置文件输出使用条件逻辑来将此任务连接到下游任务。</span><span class="sxs-lookup"><span data-stu-id="01124-136">The Data Profiling task does not have built-in features that allow you to use conditional logic to connect this task to downstream tasks based on the profile output.</span></span> <span data-ttu-id="01124-137">但是，您只要在脚本任务中进行少量的编程工作即可轻松地添加此逻辑。</span><span class="sxs-lookup"><span data-stu-id="01124-137">However, you can easily add this logic, with a small amount of programming, in a Script task.</span></span> <span data-ttu-id="01124-138">例如，脚本任务可以对数据事件探查任务的输出文件执行 Xpath 查询。</span><span class="sxs-lookup"><span data-stu-id="01124-138">For example, the Script task could perform an XPath query against the output file of the Data Profiling task.</span></span> <span data-ttu-id="01124-139">该查询可以确定在特定列中 null 值的百分比是否超过特定的阈值。</span><span class="sxs-lookup"><span data-stu-id="01124-139">The query could determine whether the percentage of null values in a particular column exceeds a certain threshold.</span></span> <span data-ttu-id="01124-140">如果该百分比超过阈值，则应中断包并解决源数据中的问题，然后再继续执行。</span><span class="sxs-lookup"><span data-stu-id="01124-140">If the percentage exceeds the threshold, you could interrupt the package and resolve the problem in the source data before continuing.</span></span> <span data-ttu-id="01124-141">有关详细信息，请参阅 [合并包工作流中的数据分析任务](incorporate-a-data-profiling-task-in-package-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="01124-141">For more information, see [Incorporate a Data Profiling Task in Package Workflow](incorporate-a-data-profiling-task-in-package-workflow.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="01124-142">相关内容</span><span class="sxs-lookup"><span data-stu-id="01124-142">Related Content</span></span>  
 [<span data-ttu-id="01124-143">数据探查器架构</span><span class="sxs-lookup"><span data-stu-id="01124-143">Data Profiler Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=251524)  
  
  
