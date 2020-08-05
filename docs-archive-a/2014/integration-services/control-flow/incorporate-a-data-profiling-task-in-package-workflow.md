---
title: 合并包工作流中的数据事件探查任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], using output in workflow
ms.assetid: 39a51586-6977-4c45-b80b-0157a54ad510
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd3544586ac99f66b961f7961e4f4af4d9e4a4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580823"
---
# <a name="incorporate-a-data-profiling-task-in-package-workflow"></a><span data-ttu-id="920e8-102">合并包工作流中的数据事件探查任务</span><span class="sxs-lookup"><span data-stu-id="920e8-102">Incorporate a Data Profiling Task in Package Workflow</span></span>
  <span data-ttu-id="920e8-103">数据事件探查和清除在其早期阶段不适合作为自动过程。</span><span class="sxs-lookup"><span data-stu-id="920e8-103">Data profiling and cleanup are not candidates for an automated process in their early stages.</span></span> <span data-ttu-id="920e8-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，通常需要对数据事件探查任务的输出进行直观的分析和人为判断，以确定报告的冲突是有意义还是过多。</span><span class="sxs-lookup"><span data-stu-id="920e8-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the output of the Data Profiling task usually requires visual analysis and human judgment to determine whether reported violations are meaningful or excessive.</span></span> <span data-ttu-id="920e8-105">即使在确认了数据质量问题之后，仍然需要通过周详的计划来确定执行清除的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="920e8-105">Even after recognizing data quality problems, there still has to be a carefully thought-out plan that addresses the best approach for cleanup.</span></span>  
  
 <span data-ttu-id="920e8-106">不过，在确定了有关数据质量的条件之后，您可能希望对数据源自动执行定期的分析和清除。</span><span class="sxs-lookup"><span data-stu-id="920e8-106">However, after criteria for data quality have been established, you might want to automate a periodic analysis and cleanup of the data source.</span></span> <span data-ttu-id="920e8-107">请考虑下面的方案：</span><span class="sxs-lookup"><span data-stu-id="920e8-107">Consider these scenarios:</span></span>  
  
-   <span data-ttu-id="920e8-108">**在增量加载之前检查数据质量**。</span><span class="sxs-lookup"><span data-stu-id="920e8-108">**Checking data quality before an incremental load**.</span></span> <span data-ttu-id="920e8-109">使用数据事件探查任务计算用于 Customers 表 CustomerName 列的新数据的列 Null 比率配置文件。</span><span class="sxs-lookup"><span data-stu-id="920e8-109">Use the Data Profiling task to compute the Column Null Ratio Profile of new data intended for the CustomerName column in a Customers table.</span></span> <span data-ttu-id="920e8-110">如果 Null 值的百分比大于 20%，则向操作员发送包含该配置文件输出的电子邮件并结束该包。</span><span class="sxs-lookup"><span data-stu-id="920e8-110">If the percentage of null values is greater than 20%, send an e-mail message that contains the profile output to the operator and end the package.</span></span> <span data-ttu-id="920e8-111">否则，请继续执行增量加载。</span><span class="sxs-lookup"><span data-stu-id="920e8-111">Otherwise, continue the incremental load.</span></span>  
  
-   <span data-ttu-id="920e8-112">**满足指定条件时自动执行清除**。</span><span class="sxs-lookup"><span data-stu-id="920e8-112">**Automating cleanup when the specified conditions are met**.</span></span> <span data-ttu-id="920e8-113">使用数据事件探查任务根据省/市/自治区的查找表计算 State 列的值包含配置文件，根据邮政编码的查找表计算 ZIP Code/Postal Code 列的值包含配置文件。</span><span class="sxs-lookup"><span data-stu-id="920e8-113">Use the Data Profiling task to compute the Value Inclusion Profile of the State column against a lookup table of states, and of the ZIP Code/Postal Code column against a lookup table of zip codes.</span></span> <span data-ttu-id="920e8-114">如果 State 值的包含强度小于 80%，但 ZIP Code/Postal Code 值的包含强度大于 99%，则表明两个问题：</span><span class="sxs-lookup"><span data-stu-id="920e8-114">If the inclusion strength of the state values is less than 80%, but the inclusion strength of the ZIP Code/Postal Code values is greater than 99%, this indicates two things.</span></span> <span data-ttu-id="920e8-115">首先，State 数据无效。</span><span class="sxs-lookup"><span data-stu-id="920e8-115">First, the state data is bad.</span></span> <span data-ttu-id="920e8-116">其次，ZIP Code/Postal Code 数据有效。</span><span class="sxs-lookup"><span data-stu-id="920e8-116">Second, the ZIP Code/Postal Code data is good.</span></span> <span data-ttu-id="920e8-117">启动数据流任务，该任务通过从当前的 Zip Code/Postal Code 值中查找正确的 State 值来清除 State 数据。</span><span class="sxs-lookup"><span data-stu-id="920e8-117">Launch a Data Flow task that cleans up the state data by performing a lookup of the correct state value from the current Zip Code/Postal Code value.</span></span>  
  
 <span data-ttu-id="920e8-118">具有可以将数据流任务合并到其中的工作流后，还需要了解添加此任务所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="920e8-118">After you have a workflow into which you can incorporate the Data Flow task, you have to understand the steps that are required to add this task.</span></span> <span data-ttu-id="920e8-119">下一部分介绍合并数据流任务的一般过程。</span><span class="sxs-lookup"><span data-stu-id="920e8-119">The next section describes the general process of incorporating the Data Flow task.</span></span> <span data-ttu-id="920e8-120">最后两部分介绍如何将数据流任务直接连接到数据源或连接到从该数据流转换的数据。</span><span class="sxs-lookup"><span data-stu-id="920e8-120">The final two sections describe how to connect the Data Flow task either directly to a data source or to transformed data from the Data Flow.</span></span>  
  
## <a name="defining-a-general-workflow-for-the-data-flow-task"></a><span data-ttu-id="920e8-121">为数据流任务定义常规工作流</span><span class="sxs-lookup"><span data-stu-id="920e8-121">Defining a General Workflow for the Data Flow Task</span></span>  
 <span data-ttu-id="920e8-122">下面的过程概述了在包的工作流中使用数据事件探查任务的输出的常规方法。</span><span class="sxs-lookup"><span data-stu-id="920e8-122">The following procedure outlines the general approach for using the output of the Data Profiling task in the workflow of a package.</span></span>  
  
#### <a name="to-use-the-output-of-the-data-profiling-task-programmatically-in-a-package"></a><span data-ttu-id="920e8-123">在包中以编程的方式使用数据事件探查任务的输出</span><span class="sxs-lookup"><span data-stu-id="920e8-123">To use the output of the Data Profiling task programmatically in a package</span></span>  
  
1.  <span data-ttu-id="920e8-124">在包中添加和配置数据事件探查任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-124">Add and configure the Data Profiling task in a package.</span></span>  
  
2.  <span data-ttu-id="920e8-125">配置包变量以便保存要从配置文件结果中检索的值。</span><span class="sxs-lookup"><span data-stu-id="920e8-125">Configure package variables to hold the values that you want to retrieve from the profile results.</span></span>  
  
3.  <span data-ttu-id="920e8-126">添加和配置脚本任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-126">Add and configure a Script task.</span></span> <span data-ttu-id="920e8-127">将脚本任务连接到数据事件探查任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-127">Connect the Script task to the Data Profiling task.</span></span> <span data-ttu-id="920e8-128">在脚本任务中，写入用于从数据事件探查任务的输出文件读取所需值并填充包变量的代码。</span><span class="sxs-lookup"><span data-stu-id="920e8-128">In the Script task, write code that reads the desired values from the output file of the Data Profiling task and populates the package variables.</span></span>  
  
4.  <span data-ttu-id="920e8-129">在将脚本任务连接到工作流下游分支的优先约束中，写入使用变量值定位工作流的表达式。</span><span class="sxs-lookup"><span data-stu-id="920e8-129">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
 <span data-ttu-id="920e8-130">在将数据事件探查任务合并到包的工作流中时，请注意该任务的以下两个功能：</span><span class="sxs-lookup"><span data-stu-id="920e8-130">When incorporating the Data Profiling task into the workflow of a package, keep these two features of the task in mind:</span></span>  
  
-   <span data-ttu-id="920e8-131">**任务输出**。</span><span class="sxs-lookup"><span data-stu-id="920e8-131">**Task output**.</span></span> <span data-ttu-id="920e8-132">数据事件探查任务根据 DataProfile.xsd 架构以 XML 格式将输出写入文件或包变量。</span><span class="sxs-lookup"><span data-stu-id="920e8-132">The Data Profiling task writes its output to a file or a package variable in XML format according to the DataProfile.xsd schema.</span></span> <span data-ttu-id="920e8-133">因此，如果希望在包的条件工作流中使用配置文件结果，则需要查询该 XML 输出。</span><span class="sxs-lookup"><span data-stu-id="920e8-133">Therefore, you have to query the XML output if you want to use the profile results in the conditional workflow of a package.</span></span> <span data-ttu-id="920e8-134">您可以方便地使用 Xpath 查询语言查询此 XML 输出。</span><span class="sxs-lookup"><span data-stu-id="920e8-134">You can easily use the Xpath query language to query this XML output.</span></span> <span data-ttu-id="920e8-135">若要学习此 XML 输出的结构，可以打开一个示例输出文件或打开该架构本身。</span><span class="sxs-lookup"><span data-stu-id="920e8-135">To study the structure of this XML output, you can open a sample output file or the schema itself.</span></span> <span data-ttu-id="920e8-136">若要打开输出文件或架构，可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、另一个 XML 编辑器或文本编辑器（如记事本）。</span><span class="sxs-lookup"><span data-stu-id="920e8-136">To open the output file or schema, you can use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], another XML editor, or a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="920e8-137">数据配置文件查看器中显示的某些配置文件结果是不能在输出中直接找到的计算值。</span><span class="sxs-lookup"><span data-stu-id="920e8-137">Some of the profile results that are displayed in the Data Profile Viewer are calculated values that are not directly found in the output.</span></span> <span data-ttu-id="920e8-138">例如，列 Null 比率配置文件的输出包括总行数和包含 Null 值的行数。</span><span class="sxs-lookup"><span data-stu-id="920e8-138">For example, the output of the Column Null Ratio Profile contains the total number of rows and the number of rows that contain null values.</span></span> <span data-ttu-id="920e8-139">您需要查询这两个值，然后计算包含 Null 值的行的百分比，以得到列 Null 比率。</span><span class="sxs-lookup"><span data-stu-id="920e8-139">You have to query these two values, and then calculate the percentage of rows that contain null values, to obtain the column null ratio.</span></span>  
  
-   <span data-ttu-id="920e8-140">**任务输入**。</span><span class="sxs-lookup"><span data-stu-id="920e8-140">**Task input**.</span></span> <span data-ttu-id="920e8-141">数据事件探查任务从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中读取输入。</span><span class="sxs-lookup"><span data-stu-id="920e8-141">The Data Profiling task reads its input from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="920e8-142">因此，如果要对数据流中已加载并转换的数据进行事件探查，则需要将内存中的数据保存到临时表中。</span><span class="sxs-lookup"><span data-stu-id="920e8-142">Therefore, you have to save data that is in memory to staging tables if you want to profile data that has already been loaded and transformed in the data flow.</span></span>  
  
 <span data-ttu-id="920e8-143">以下各部分将应用此常规工作流，以对直接来自外部数据源的数据或从数据流任务转换而来的数据进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="920e8-143">The following sections apply this general workflow to profiling data that comes directly from an external data source or that comes transformed from the Data Flow task.</span></span> <span data-ttu-id="920e8-144">这些部分还说明如何处理数据流任务的输入和输出要求。</span><span class="sxs-lookup"><span data-stu-id="920e8-144">These sections also show how to handle the input and output requirements of the Data Flow task.</span></span>  
  
## <a name="connecting-the-data-profiling-task-directly-to-an-external-data-source"></a><span data-ttu-id="920e8-145">将数据事件探查任务直接连接到外部数据源</span><span class="sxs-lookup"><span data-stu-id="920e8-145">Connecting the Data Profiling Task Directly to an External Data Source</span></span>  
 <span data-ttu-id="920e8-146">数据事件探查任务可以对直接来自数据源的数据进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="920e8-146">The Data Profiling task can profile data that comes directly from a data source.</span></span>  <span data-ttu-id="920e8-147">为了举例说明此功能，下面的示例使用数据事件探查任务对 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中的 Person.Address 表的列计算列 Null 比率配置文件。</span><span class="sxs-lookup"><span data-stu-id="920e8-147">To illustrate this capability, the following example uses the Data Profiling task to compute a Column Null Ratio Profile on the columns of the Person.Address table in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="920e8-148">然后，此示例使用脚本任务从输出文件检索结果，并填充可用来定位工作流的包变量。</span><span class="sxs-lookup"><span data-stu-id="920e8-148">Then, this example uses a Script task to retrieve the results from the output file and populate package variables that can be used to direct workflow.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="920e8-149">因为 AddressLine2 列包含 Null 值的比例高，所以选择该列用于此简单示例。</span><span class="sxs-lookup"><span data-stu-id="920e8-149">The AddressLine2 column was selected for this simple example because this column contains a high percentage of null values.</span></span>  
  
 <span data-ttu-id="920e8-150">此示例步骤如下：</span><span class="sxs-lookup"><span data-stu-id="920e8-150">This example consists of the following steps:</span></span>  
  
-   <span data-ttu-id="920e8-151">对连接到外部数据源的连接管理器以及连接到将包含配置文件结果的输出文件的连接管理器进行配置。</span><span class="sxs-lookup"><span data-stu-id="920e8-151">Configuring the connection managers that connect to the external data source and to the output file that will contain the profile results.</span></span>  
  
-   <span data-ttu-id="920e8-152">对将保存数据事件探查任务所需值的包变量进行配置。</span><span class="sxs-lookup"><span data-stu-id="920e8-152">Configuring the package variables that will hold the values needed by the Data Profiling task.</span></span>  
  
-   <span data-ttu-id="920e8-153">配置数据事件探查任务以计算列 Null 比率配置文件。</span><span class="sxs-lookup"><span data-stu-id="920e8-153">Configuring the Data Profiling task to compute the Column Null Ratio Profile.</span></span>  
  
-   <span data-ttu-id="920e8-154">配置脚本任务来处理数据事件探查任务的 XML 输出。</span><span class="sxs-lookup"><span data-stu-id="920e8-154">Configuring the Script task to work the XML output from the Data Profiling task.</span></span>  
  
-   <span data-ttu-id="920e8-155">配置优先约束，这些约束将根据数据事件探查任务的结果控制运行工作流中的哪些下游分支。</span><span class="sxs-lookup"><span data-stu-id="920e8-155">Configuring the precedence constraints that will control which downstream branches in the workflow are run based on the results of the Data Profiling task.</span></span>  
  
### <a name="configure-the-connection-managers"></a><span data-ttu-id="920e8-156">配置连接管理器</span><span class="sxs-lookup"><span data-stu-id="920e8-156">Configure the Connection Managers</span></span>  
 <span data-ttu-id="920e8-157">在本例中，有两种连接管理器：</span><span class="sxs-lookup"><span data-stu-id="920e8-157">For this example, there are two connection managers:</span></span>  
  
-   <span data-ttu-id="920e8-158">连接到 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 数据库的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="920e8-158">An [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span>  
  
-   <span data-ttu-id="920e8-159">文件连接管理器，该管理器将创建用于保存数据事件探查任务的结果的输出文件。</span><span class="sxs-lookup"><span data-stu-id="920e8-159">A File connection manager that creates the output file that will hold the results of the Data Profiling task.</span></span>  
  
##### <a name="to-configure-the-connection-managers"></a><span data-ttu-id="920e8-160">配置连接管理器</span><span class="sxs-lookup"><span data-stu-id="920e8-160">To configure the connection managers</span></span>  
  
1.  <span data-ttu-id="920e8-161">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中创建一个新 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="920e8-161">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
2.  <span data-ttu-id="920e8-162">向该包添加一个 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="920e8-162">Add an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to the package.</span></span> <span data-ttu-id="920e8-163">对此连接管理器进行配置，以使用 NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 并连接到 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库的可用实例。</span><span class="sxs-lookup"><span data-stu-id="920e8-163">Configure this connection manager to use the NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) and to connect to an available instance of the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span>  
  
     <span data-ttu-id="920e8-164">默认情况下，该连接管理器的名称为：\<server name>.AdventureWorks1。</span><span class="sxs-lookup"><span data-stu-id="920e8-164">By default, the connection manager has the following name: \<server name>.AdventureWorks1.</span></span>  
  
3.  <span data-ttu-id="920e8-165">向该包添加一个文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="920e8-165">Add a File connection manager to the package.</span></span> <span data-ttu-id="920e8-166">对此连接管理器进行配置，以便为数据事件探查任务创建输出文件。</span><span class="sxs-lookup"><span data-stu-id="920e8-166">Configure this connection manager to create the output file for the Data Profiling task.</span></span>  
  
     <span data-ttu-id="920e8-167">此示例使用文件名 DataProfile1.xml。</span><span class="sxs-lookup"><span data-stu-id="920e8-167">This example uses the file name, DataProfile1.xml.</span></span> <span data-ttu-id="920e8-168">默认情况下，该连接管理器与该文件具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="920e8-168">By default, the connection manager has the same name as the file.</span></span>  
  
### <a name="configure-the-package-variables"></a><span data-ttu-id="920e8-169">配置包变量</span><span class="sxs-lookup"><span data-stu-id="920e8-169">Configure the Package Variables</span></span>  
 <span data-ttu-id="920e8-170">此示例使用两个包变量：</span><span class="sxs-lookup"><span data-stu-id="920e8-170">This example uses two package variables:</span></span>  
  
-   <span data-ttu-id="920e8-171">ProfileConnectionName 变量将文件连接管理器的名称传递给脚本任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-171">The ProfileConnectionName variable passes the name of the File connection manager to the Script task.</span></span>  
  
-   <span data-ttu-id="920e8-172">AddressLine2NullRatio 变量将计算得出的此列的 Null 比率从脚本任务传递给包。</span><span class="sxs-lookup"><span data-stu-id="920e8-172">The AddressLine2NullRatio variable passes the calculated null ratio for this column out of the Script task to the package.</span></span>  
  
##### <a name="to-configure-the-package-variables-that-will-hold-profile-results"></a><span data-ttu-id="920e8-173">对将保存配置文件结果的包变量进行配置</span><span class="sxs-lookup"><span data-stu-id="920e8-173">To configure the package variables that will hold profile results</span></span>  
  
-   <span data-ttu-id="920e8-174">在 **“变量”** 窗口中，添加并配置以下两个包变量：</span><span class="sxs-lookup"><span data-stu-id="920e8-174">In the **Variables** window, add and configure the following two package variables:</span></span>  
  
    -   <span data-ttu-id="920e8-175">`ProfileConnectionName`为其中一个变量输入名称，并将此变量的类型设置为**String**。</span><span class="sxs-lookup"><span data-stu-id="920e8-175">Enter the name, `ProfileConnectionName`, for one of the variables and set the type of this variable to **String**.</span></span>  
  
    -   <span data-ttu-id="920e8-176">为另一个变量输入名称， `AddressLine2NullRatio` 并将此变量的类型设置为**Double**。</span><span class="sxs-lookup"><span data-stu-id="920e8-176">Enter the name, `AddressLine2NullRatio`, for the other variable and set the type of this variable to **Double**.</span></span>  
  
### <a name="configure-the-data-profiling-task"></a><span data-ttu-id="920e8-177">配置数据事件探查任务</span><span class="sxs-lookup"><span data-stu-id="920e8-177">Configure the Data Profiling Task</span></span>  
 <span data-ttu-id="920e8-178">在以下情况下，必须对数据事件探查任务进行配置：</span><span class="sxs-lookup"><span data-stu-id="920e8-178">The Data Profiling task has to be configured in the following way:</span></span>  
  
-   <span data-ttu-id="920e8-179">使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器提供的数据作为输入。</span><span class="sxs-lookup"><span data-stu-id="920e8-179">To use the data that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager supplies as input.</span></span>  
  
-   <span data-ttu-id="920e8-180">对输入数据计算列 Null 比率配置文件。</span><span class="sxs-lookup"><span data-stu-id="920e8-180">To perform a Column Null Ratio profile on the input data.</span></span>  
  
-   <span data-ttu-id="920e8-181">将配置文件结果保存到与文件连接管理器关联的文件中。</span><span class="sxs-lookup"><span data-stu-id="920e8-181">To save the profile results to the file that is associated with the File connection manager.</span></span>  
  
##### <a name="to-configure-the-data-profiling-task"></a><span data-ttu-id="920e8-182">配置数据事件探查任务</span><span class="sxs-lookup"><span data-stu-id="920e8-182">To configure the Data Profiling task</span></span>  
  
1.  <span data-ttu-id="920e8-183">向控制流添加一个数据事件探查任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-183">To the Control Flow, add a Data Profiling task.</span></span>  
  
2.  <span data-ttu-id="920e8-184">打开 **“数据事件探查任务编辑器”** 以配置该任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-184">Open the **Data Profiling Task Editor** to configure the task.</span></span>  
  
3.  <span data-ttu-id="920e8-185">在该编辑器的 **“常规”** 页上，选择前面配置的文件连接管理器的名称作为 **“目标”** 。</span><span class="sxs-lookup"><span data-stu-id="920e8-185">On the **General** page of the editor, for **Destination**, select the name of the File connection manager that you have previously configured.</span></span>  
  
4.  <span data-ttu-id="920e8-186">在该编辑器的 **“配置文件请求”** 页上，创建新的列 Null 比率配置文件。</span><span class="sxs-lookup"><span data-stu-id="920e8-186">On the **Profile Requests** page of the editor, create a new Column Null Ratio Profile.</span></span>  
  
5.  <span data-ttu-id="920e8-187">在 **“请求属性”** 窗格中，选择前面配置的 **连接管理器作为**ConnectionManager [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="920e8-187">In the **Request properties** pane, for **ConnectionManager**, select the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that you have previously configured.</span></span> <span data-ttu-id="920e8-188">然后选择 Person.Address 作为 **TableOrView**。</span><span class="sxs-lookup"><span data-stu-id="920e8-188">Then, for **TableOrView**, select Person.Address.</span></span>  
  
6.  <span data-ttu-id="920e8-189">关闭数据事件探查任务编辑器。</span><span class="sxs-lookup"><span data-stu-id="920e8-189">Close the Data Profiling Task Editor.</span></span>  
  
### <a name="configure-the-script-task"></a><span data-ttu-id="920e8-190">配置脚本任务</span><span class="sxs-lookup"><span data-stu-id="920e8-190">Configure the Script Task</span></span>  
 <span data-ttu-id="920e8-191">必须对脚本任务进行配置，以便从输出文件检索结果并填充前面配置的包变量。</span><span class="sxs-lookup"><span data-stu-id="920e8-191">The Script task has to be configured to retrieve the results from the output file and populate the package variables that were previously configured.</span></span>  
  
##### <a name="to-configure-the-script-task"></a><span data-ttu-id="920e8-192">配置脚本任务</span><span class="sxs-lookup"><span data-stu-id="920e8-192">To configure the Script task</span></span>  
  
1.  <span data-ttu-id="920e8-193">向控制流添加一个脚本任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-193">To the Control Flow, add a Script task.</span></span>  
  
2.  <span data-ttu-id="920e8-194">将脚本任务连接到数据事件探查任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-194">Connect the Script task to the Data Profiling task.</span></span>  
  
3.  <span data-ttu-id="920e8-195">打开 **“脚本任务编辑器”** 以配置该任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-195">Open the **Script Task Editor** to configure the task.</span></span>  
  
4.  <span data-ttu-id="920e8-196">在 **“脚本”** 页上，选择首选编程语言。</span><span class="sxs-lookup"><span data-stu-id="920e8-196">On the **Script** page, select your preferred programming language.</span></span> <span data-ttu-id="920e8-197">然后，使两个包变量对该脚本可用：</span><span class="sxs-lookup"><span data-stu-id="920e8-197">Then, make the two package variables available to the script:</span></span>  
  
    1.  <span data-ttu-id="920e8-198">对于 `ReadOnlyVariables` ，请选择 `ProfileConnectionName` 。</span><span class="sxs-lookup"><span data-stu-id="920e8-198">For `ReadOnlyVariables`, select `ProfileConnectionName`.</span></span>  
  
    2.  <span data-ttu-id="920e8-199">对于**ReadWriteVariables**，请选择 `AddressLine2NullRatio` 。</span><span class="sxs-lookup"><span data-stu-id="920e8-199">For **ReadWriteVariables**, select `AddressLine2NullRatio`.</span></span>  
  
5.  <span data-ttu-id="920e8-200">选择 **“编辑脚本”** 以打开脚本开发环境。</span><span class="sxs-lookup"><span data-stu-id="920e8-200">Select **Edit Script** to open the script development environment.</span></span>  
  
6.  <span data-ttu-id="920e8-201">添加对 System.Xml 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="920e8-201">Add a reference to the System.Xml namespace.</span></span>  
  
7.  <span data-ttu-id="920e8-202">输入与您的编程语言对应的示例代码：</span><span class="sxs-lookup"><span data-stu-id="920e8-202">Enter the sample code that corresponds to your programming language:</span></span>  
  
    ```vb  
    Imports System  
    Imports Microsoft.SqlServer.Dts.Runtime  
    Imports System.Xml  
  
    Public Class ScriptMain  
  
      Private FILENAME As String = "C:\ TEMP\DataProfile1.xml"  
      Private PROFILE_NAMESPACE_URI As String = "https://schemas.microsoft.com/DataDebugger/"  
      Private NULLCOUNT_XPATH As String = _  
        "/default:DataProfile/default:DataProfileOutput/default:Profiles" & _  
        "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:NullCount/text()"  
      Private TABLE_XPATH As String = _  
        "/default:DataProfile/default:DataProfileOutput/default:Profiles" & _  
        "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:Table"  
  
      Public Sub Main()  
  
        Dim profileConnectionName As String  
        Dim profilePath As String  
        Dim profileOutput As New XmlDocument  
        Dim profileNSM As XmlNamespaceManager  
        Dim nullCountNode As XmlNode  
        Dim nullCount As Integer  
        Dim tableNode As XmlNode  
        Dim rowCount As Integer  
        Dim nullRatio As Double  
  
        ' Open output file.  
        profileConnectionName = Dts.Variables("ProfileConnectionName").Value.ToString()  
        profilePath = Dts.Connections(profileConnectionName).ConnectionString  
        profileOutput.Load(profilePath)  
        profileNSM = New XmlNamespaceManager(profileOutput.NameTable)  
        profileNSM.AddNamespace("default", PROFILE_NAMESPACE_URI)  
  
        ' Get null count for column.  
        nullCountNode = profileOutput.SelectSingleNode(NULLCOUNT_XPATH, profileNSM)  
        nullCount = CType(nullCountNode.Value, Integer)  
  
        ' Get row count for table.  
        tableNode = profileOutput.SelectSingleNode(TABLE_XPATH, profileNSM)  
        rowCount = CType(tableNode.Attributes("RowCount").Value, Integer)  
  
        ' Compute and return null ratio.  
        nullRatio = nullCount / rowCount  
        Dts.Variables("AddressLine2NullRatio").Value = nullRatio  
  
        Dts.TaskResult = Dts.Results.Success  
  
      End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SqlServer.Dts.Runtime;  
    using System.Xml;  
  
    public class ScriptMain  
    {  
  
      private string FILENAME = "C:\\ TEMP\\DataProfile1.xml";  
      private string PROFILE_NAMESPACE_URI = "https://schemas.microsoft.com/DataDebugger/";  
      private string NULLCOUNT_XPATH = "/default:DataProfile/default:DataProfileOutput/default:Profiles" + "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:NullCount/text()";  
      private string TABLE_XPATH = "/default:DataProfile/default:DataProfileOutput/default:Profiles" + "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:Table";  
  
      public void Main()  
      {  
  
        string profileConnectionName;  
        string profilePath;  
        XmlDocument profileOutput = new XmlDocument();  
        XmlNamespaceManager profileNSM;  
        XmlNode nullCountNode;  
        int nullCount;  
        XmlNode tableNode;  
        int rowCount;  
        double nullRatio;  
  
        // Open output file.  
        profileConnectionName = Dts.Variables["ProfileConnectionName"].Value.ToString();  
        profilePath = Dts.Connections[profileConnectionName].ConnectionString;  
        profileOutput.Load(profilePath);  
        profileNSM = new XmlNamespaceManager(profileOutput.NameTable);  
        profileNSM.AddNamespace("default", PROFILE_NAMESPACE_URI);  
  
        // Get null count for column.  
        nullCountNode = profileOutput.SelectSingleNode(NULLCOUNT_XPATH, profileNSM);  
        nullCount = (int)nullCountNode.Value;  
  
        // Get row count for table.  
        tableNode = profileOutput.SelectSingleNode(TABLE_XPATH, profileNSM);  
        rowCount = (int)tableNode.Attributes["RowCount"].Value;  
  
        // Compute and return null ratio.  
        nullRatio = nullCount / rowCount;  
        Dts.Variables["AddressLine2NullRatio"].Value = nullRatio;  
  
        Dts.TaskResult = Dts.Results.Success;  
  
      }  
  
    }  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="920e8-203">此过程中显示的示例代码说明如何从文件加载数据事件探查任务的输出。</span><span class="sxs-lookup"><span data-stu-id="920e8-203">The sample code shown in this procedure demonstrates how to load the output of the Data Profiling task from a file.</span></span> <span data-ttu-id="920e8-204">若要从包变量加载数据事件探查任务的输出，请参阅此过程后面的替代示例代码。</span><span class="sxs-lookup"><span data-stu-id="920e8-204">To load the output of the Data Profiling task from a package variable instead, see the alternative sample code that follows this procedure.</span></span>  
  
8.  <span data-ttu-id="920e8-205">关闭脚本开发环境，然后关闭脚本任务编辑器。</span><span class="sxs-lookup"><span data-stu-id="920e8-205">Close the script development environment, and then close the Script Task Editor.</span></span>  
  
#### <a name="alternative-code-reading-the-profile-output-from-a-variable"></a><span data-ttu-id="920e8-206">替代代码 - 从变量读取配置文件输出</span><span class="sxs-lookup"><span data-stu-id="920e8-206">Alternative Code-Reading the Profile Output from a Variable</span></span>  
 <span data-ttu-id="920e8-207">前面的过程显示如何从文件加载数据事件探查任务的输出。</span><span class="sxs-lookup"><span data-stu-id="920e8-207">The previous procedure shows how to load the output of the Data Profiling task from a file.</span></span> <span data-ttu-id="920e8-208">不过，还有一种方法是从包变量加载此输出。</span><span class="sxs-lookup"><span data-stu-id="920e8-208">However, an alternative method would be to load this output from a package variable.</span></span> <span data-ttu-id="920e8-209">若要从变量加载输出，必须对示例代码进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="920e8-209">To load the output from a variable, you have to make the following changes to the sample code:</span></span>  
  
-   <span data-ttu-id="920e8-210">调用 `LoadXml` 类的 `XmlDocument` 方法而不是 `Load` 方法。</span><span class="sxs-lookup"><span data-stu-id="920e8-210">Call the `LoadXml` method of the `XmlDocument` class instead of the `Load` method.</span></span>  
  
-   <span data-ttu-id="920e8-211">在脚本任务编辑器中，将包含配置文件输出的包变量的名称添加到该任务的 `ReadOnlyVariables` 列表中。</span><span class="sxs-lookup"><span data-stu-id="920e8-211">In the Script Task Editor, add the name of the package variable that contains the profile output to the task's `ReadOnlyVariables` list.</span></span>  
  
-   <span data-ttu-id="920e8-212">将该变量的字符串值传递给 `LoadXML` 方法，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="920e8-212">Pass the string value of the variable to the `LoadXML` method, as shown in the following code example.</span></span> <span data-ttu-id="920e8-213">（本示例使用“ProfileOutput”作为包含配置文件输出的包变量的名称。）</span><span class="sxs-lookup"><span data-stu-id="920e8-213">(This example uses "ProfileOutput" as the name of the package variable that contains the profile output.)</span></span>  
  
    ```vb  
    Dim outputString As String  
    outputString = Dts.Variables("ProfileOutput").Value.ToString()  
    ...  
    profileOutput.LoadXml(outputString)  
    ```  
  
    ```csharp  
    string outputString;  
    outputString = Dts.Variables["ProfileOutput"].Value.ToString();  
    ...  
    profileOutput.LoadXml(outputString);  
    ```  
  
### <a name="configure-the-precedence-constraints"></a><span data-ttu-id="920e8-214">配置优先约束</span><span class="sxs-lookup"><span data-stu-id="920e8-214">Configure the Precedence Constraints</span></span>  
 <span data-ttu-id="920e8-215">必须对优先约束进行配置，以便根据数据事件探查任务的结果控制运行工作流中的哪些下游分支。</span><span class="sxs-lookup"><span data-stu-id="920e8-215">The precedence constraints have to be configured to control which downstream branches in the workflow are run based on the results of the Data Profiling task.</span></span>  
  
##### <a name="to-configure-the-precedence-constraints"></a><span data-ttu-id="920e8-216">配置优先约束</span><span class="sxs-lookup"><span data-stu-id="920e8-216">To configure the precedence constraints</span></span>  
  
-   <span data-ttu-id="920e8-217">在将脚本任务连接到工作流下游分支的优先约束中，写入使用变量值定位工作流的表达式。</span><span class="sxs-lookup"><span data-stu-id="920e8-217">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
     <span data-ttu-id="920e8-218">例如，可以将优先约束的 **“求值运算”** 设置为 **“表达式和约束”** 。</span><span class="sxs-lookup"><span data-stu-id="920e8-218">For example, you might set the **Evaluation operation** of the precedence constraint to **Expression and Constraint**.</span></span> <span data-ttu-id="920e8-219">然后，可以使用 `@AddressLine2NullRatio < .90` 作为该表达式的值。</span><span class="sxs-lookup"><span data-stu-id="920e8-219">Then, you might use `@AddressLine2NullRatio < .90` as the value of the expression.</span></span> <span data-ttu-id="920e8-220">当前面的任务成功并且所选列的 Null 值的百分比小于 90% 时，这将使工作流遵循所选的路径。</span><span class="sxs-lookup"><span data-stu-id="920e8-220">This causes the workflow to follow the selected path when the previous tasks succeed, and when the percentage of null values in the selected column is less than 90%.</span></span>  
  
## <a name="connecting-the-data-profiling-task-to-transformed-data-from-the-data-flow"></a><span data-ttu-id="920e8-221">将数据事件探查任务连接到从数据流转换的数据</span><span class="sxs-lookup"><span data-stu-id="920e8-221">Connecting the Data Profiling Task to Transformed Data from the Data Flow</span></span>  
 <span data-ttu-id="920e8-222">您可以不对直接来自数据源的数据进行事件探查，而是对数据流中已加载并转换的数据进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="920e8-222">Instead of profiling data directly from a data source, you can profile data that has already been loaded and transformed in the data flow.</span></span> <span data-ttu-id="920e8-223">不过，数据事件探查任务仅针对持久化数据而不针对内存中的数据进行操作。</span><span class="sxs-lookup"><span data-stu-id="920e8-223">However, the Data Profiling task works only against persisted data, not against in-memory data.</span></span> <span data-ttu-id="920e8-224">因此，必须首先使用目标组件将已转换的数据保存到临时表中。</span><span class="sxs-lookup"><span data-stu-id="920e8-224">Therefore, you must first use a destination component to save the transformed data to a staging table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="920e8-225">在配置数据事件探查任务时，必须选择现有表和列。</span><span class="sxs-lookup"><span data-stu-id="920e8-225">When you configure the Data Profiling task, you have to select existing tables and columns.</span></span> <span data-ttu-id="920e8-226">因此必须在设计时创建临时表，才能配置该任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-226">Therefore, you must create the staging table at design time before you can configure the task.</span></span> <span data-ttu-id="920e8-227">也就是说，此方案不允许使用在运行时创建的临时表。</span><span class="sxs-lookup"><span data-stu-id="920e8-227">In other words, this scenario does not allow you to use a temporary table that is created at run time.</span></span>  
  
 <span data-ttu-id="920e8-228">将数据保存到临时表中后，即可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="920e8-228">After saving the data to a staging table, you can do the following actions:</span></span>  
  
-   <span data-ttu-id="920e8-229">使用数据事件探查任务对数据进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="920e8-229">Use the Data Profiling task to profile the data.</span></span>  
  
-   <span data-ttu-id="920e8-230">按照本主题前面所述使用脚本任务读取结果。</span><span class="sxs-lookup"><span data-stu-id="920e8-230">Use a Script task to read the results as described earlier in this topic.</span></span>  
  
-   <span data-ttu-id="920e8-231">使用这些结果定位包的后续工作流。</span><span class="sxs-lookup"><span data-stu-id="920e8-231">Use those results to direct the subsequent workflow of the package.</span></span>  
  
 <span data-ttu-id="920e8-232">下面的过程介绍使用数据事件探查任务对已由数据流转换的数据进行事件探查的常规方法。</span><span class="sxs-lookup"><span data-stu-id="920e8-232">The following procedure provides the general approach for using the Data Profiling task to profile data that has been transformed by the data flow.</span></span> <span data-ttu-id="920e8-233">其中的很多步骤与前面介绍的对直接来自外部数据源的数据进行事件探查的步骤类似。</span><span class="sxs-lookup"><span data-stu-id="920e8-233">Many of these steps are similar to the ones described earlier for profiling data that comes directly from an external data source.</span></span> <span data-ttu-id="920e8-234">您可能需要查看前面的这些步骤，以便了解如何配置各种组件的更多信息。</span><span class="sxs-lookup"><span data-stu-id="920e8-234">You might want to review those earlier steps for more information about how to configure the various components.</span></span>  
  
#### <a name="to-use-the-data-profiling-task-in-the-data-flow"></a><span data-ttu-id="920e8-235">在数据流中使用数据事件探查任务</span><span class="sxs-lookup"><span data-stu-id="920e8-235">To use the Data Profiling task in the data flow</span></span>  
  
1.  <span data-ttu-id="920e8-236">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中创建一个包。</span><span class="sxs-lookup"><span data-stu-id="920e8-236">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create a package.</span></span>  
  
2.  <span data-ttu-id="920e8-237">在数据流中，添加、配置并连接相应的源和转换。</span><span class="sxs-lookup"><span data-stu-id="920e8-237">In the Data Flow, add, configure, and connect the appropriate sources and transformations.</span></span>  
  
3.  <span data-ttu-id="920e8-238">在数据流中，添加、配置并连接将已转换的数据保存到临时表的目标组件。</span><span class="sxs-lookup"><span data-stu-id="920e8-238">In the Data Flow, add, configure, and connect a destination component that saves the transformed data to a staging table.</span></span>  
  
4.  <span data-ttu-id="920e8-239">在控制流中，添加并配置数据事件探查任务，该任务将根据临时表中的已转换数据计算所需的配置文件。</span><span class="sxs-lookup"><span data-stu-id="920e8-239">In the Control Flow, add and configure a Data Profiling task that computes the desired profiles against the transformed data in the staging table.</span></span> <span data-ttu-id="920e8-240">将数据事件探查任务连接到数据流任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-240">Connect the Data Profiling task to the Data Flow task.</span></span>  
  
5.  <span data-ttu-id="920e8-241">配置包变量以便保存要从配置文件结果中检索的值。</span><span class="sxs-lookup"><span data-stu-id="920e8-241">Configure package variables to hold the values that you want to retrieve from the profile results.</span></span>  
  
6.  <span data-ttu-id="920e8-242">添加和配置脚本任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-242">Add and configure a Script task.</span></span> <span data-ttu-id="920e8-243">将脚本任务连接到数据事件探查任务。</span><span class="sxs-lookup"><span data-stu-id="920e8-243">Connect the Script task to the Data Profiling task.</span></span> <span data-ttu-id="920e8-244">在脚本任务中，写入用于从数据事件探查任务的输出文件读取所需值并填充包变量的代码。</span><span class="sxs-lookup"><span data-stu-id="920e8-244">In the Script task, write code that reads the desired values from the output of the Data Profiling task and populates the package variables.</span></span>  
  
7.  <span data-ttu-id="920e8-245">在将脚本任务连接到工作流下游分支的优先约束中，写入使用变量值定位工作流的表达式。</span><span class="sxs-lookup"><span data-stu-id="920e8-245">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="920e8-246">另请参阅</span><span class="sxs-lookup"><span data-stu-id="920e8-246">See Also</span></span>  
 <span data-ttu-id="920e8-247">[设置数据事件探查任务](data-profiling-task.md) </span><span class="sxs-lookup"><span data-stu-id="920e8-247">[Setup of the Data Profiling Task](data-profiling-task.md) </span></span>  
 [<span data-ttu-id="920e8-248">数据配置文件查看器</span><span class="sxs-lookup"><span data-stu-id="920e8-248">Data Profile Viewer</span></span>](data-profile-viewer.md)  
  
  
