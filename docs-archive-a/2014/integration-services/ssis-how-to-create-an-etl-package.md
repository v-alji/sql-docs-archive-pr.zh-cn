---
title: SSIS 教程：创建简单的 ETL 包 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 780b008052a2ff64aa75b2036aa7202128f95ae2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690733"
---
# <a name="ssis-tutorial-creating-a-simple-etl-package"></a><span data-ttu-id="75b17-102">SSIS 教程：创建简单的 ETL 包</span><span class="sxs-lookup"><span data-stu-id="75b17-102">SSIS Tutorial: Creating a Simple ETL Package</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="75b17-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) 是一种用于构建高性能数据集成解决方案的平台，其中包括数据仓库的 ETL) 包的提取、转换和加载 (。</span><span class="sxs-lookup"><span data-stu-id="75b17-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) is a platform for building high performance data integration solutions, including extraction, transformation, and load (ETL) packages for data warehousing.</span></span> <span data-ttu-id="75b17-104">SSIS 包括生成并调试包的图形工具和向导；执行如 FTP 操作、执行 SQL 语句和发送电子邮件等工作流功能的任务；用于提取和加载数据的数据源和目标；用于清理、聚合、合并和复制数据的转换；管理服务，即用于管理包执行和存储的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务；以及用于对 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 对象模型编程的应用程序编程接口 (API)。</span><span class="sxs-lookup"><span data-stu-id="75b17-104">SSIS includes graphical tools and wizards for building and debugging packages; tasks for performing workflow functions such as FTP operations, executing SQL statements, and sending e-mail messages; data sources and destinations for extracting and loading data; transformations for cleaning, aggregating, merging, and copying data; a management service, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service for administering package execution and storage; and application programming interfaces (APIs) for programming the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model.</span></span>  
  
 <span data-ttu-id="75b17-105">在本教程中，您将学习如何使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器创建一个简单的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="75b17-105">In this tutorial, you will learn how to use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create a simple [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="75b17-106">所创建的包将从平面文件提取数据，重新设置数据的格式，然后将已重新设置格式的数据插入到事实数据表中。</span><span class="sxs-lookup"><span data-stu-id="75b17-106">The package that you create takes data from a flat file, reformats the data, and then inserts the reformatted data into a fact table.</span></span> <span data-ttu-id="75b17-107">在下列课程中，将扩展包以阐释循环、包配置、日志记录和错误流。</span><span class="sxs-lookup"><span data-stu-id="75b17-107">In following lessons, the package is expanded to demonstrate looping, package configurations, logging and error flow.</span></span>  
  
 <span data-ttu-id="75b17-108">在安装教程所用的示例数据的同时，也会安装将在教程的每一课中创建的完整的包版本。</span><span class="sxs-lookup"><span data-stu-id="75b17-108">When you install the sample data that the tutorial uses, you also install the completed versions of the packages that you will create in each lesson of the tutorial.</span></span> <span data-ttu-id="75b17-109">使用完整的包，您可以按需要跳过前面几课而从后面的课程开始学习教程。</span><span class="sxs-lookup"><span data-stu-id="75b17-109">By using the completed packages, you can skip ahead and begin the tutorial at a later lesson if you like.</span></span> <span data-ttu-id="75b17-110">如果您是第一次使用包或新的开发环境，我们建议从第 1 课开始学习。</span><span class="sxs-lookup"><span data-stu-id="75b17-110">If this is your first time working with packages or the new development environment, we recommend that you begin with Lesson1.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="75b17-111">学习内容</span><span class="sxs-lookup"><span data-stu-id="75b17-111">What You Will Learn</span></span>  
 <span data-ttu-id="75b17-112">熟悉中提供的新工具、控件和功能的最佳方式 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 是使用它们。</span><span class="sxs-lookup"><span data-stu-id="75b17-112">The best way to become acquainted with the new tools, controls and features available in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is to use them.</span></span> <span data-ttu-id="75b17-113">本教程将引导您使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器创建一个简单的 ETL 包，其中包含循环、配置、错误流逻辑和日志记录。</span><span class="sxs-lookup"><span data-stu-id="75b17-113">This tutorial walks you through [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create a simple ETL package that includes looping, configurations, error flow logic and logging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75b17-114">要求</span><span class="sxs-lookup"><span data-stu-id="75b17-114">Requirements</span></span>  
 <span data-ttu-id="75b17-115">本教程适用于熟悉基本数据库操作，但对中可用的新功能有限制的用户 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="75b17-115">This tutorial is intended for users familiar with fundamental database operations, but who have limited exposure to the new features available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="75b17-116">若要使用本教程，系统中必须安装下列组件：</span><span class="sxs-lookup"><span data-stu-id="75b17-116">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="75b17-117">数据库的 **数据库的** 。</span><span class="sxs-lookup"><span data-stu-id="75b17-117">with the **AdventureWorksDW2012** database.</span></span> <span data-ttu-id="75b17-118">为了增强安全性，默认情况下不会安装示例数据库。</span><span class="sxs-lookup"><span data-stu-id="75b17-118">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="75b17-119">要下载 **AdventureWorksDW2012** 数据库，请参阅 [Adventure Works for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=275026)。</span><span class="sxs-lookup"><span data-stu-id="75b17-119">To download the **AdventureWorksDW2012** database, see [Adventure Works for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=275026).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="75b17-120">附加数据库 (\*.mdf file) 时，默认情况下 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 将搜索 .ldf 文件。</span><span class="sxs-lookup"><span data-stu-id="75b17-120">When you attach the database (\*.mdf file), [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] will by default search for an .ldf file.</span></span> <span data-ttu-id="75b17-121">在 **“附加数据库”** 对话框中单击“确定”前，您必须手动删除 .ldf 文件。</span><span class="sxs-lookup"><span data-stu-id="75b17-121">You must manually remove the .ldf file before clicking OK in the **Attach Databases** dialog box.</span></span>  
    >   
    >  <span data-ttu-id="75b17-122">有关附加数据库的详细信息，请参阅 [Attach a Database](../relational-databases/databases/attach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="75b17-122">For more information about attaching databases, see [Attach a Database](../relational-databases/databases/attach-a-database.md).</span></span>  
  
-   <span data-ttu-id="75b17-123">示例数据。</span><span class="sxs-lookup"><span data-stu-id="75b17-123">Sample data.</span></span> <span data-ttu-id="75b17-124">示例数据与 [!INCLUDE[ssIS](../includes/ssis-md.md)] 课程包一起提供。</span><span class="sxs-lookup"><span data-stu-id="75b17-124">The sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="75b17-125">要下载示例数据和课程包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="75b17-125">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="75b17-126">导航到 [Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="75b17-126">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="75b17-127">单击 "**下载**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="75b17-127">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="75b17-128">单击 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="75b17-128">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="75b17-129">本教程中的课程</span><span class="sxs-lookup"><span data-stu-id="75b17-129">Lessons in This Tutorial</span></span>  
 [<span data-ttu-id="75b17-130">第 1 课：创建项目和基本包</span><span class="sxs-lookup"><span data-stu-id="75b17-130">Lesson 1: Creating the Project and Basic Package</span></span>](lesson-1-create-a-project-and-basic-package-with-ssis.md)  
 <span data-ttu-id="75b17-131">在本课中，将创建一个简单的 ETL 包，从单个平面文件中提取数据，再使用查找转换转换数据，最后将所得结果加载到目标事实数据表中。</span><span class="sxs-lookup"><span data-stu-id="75b17-131">In this lesson, you will create a simple ETL package that extracts data from a single flat file, transforms the data using lookup transformations and finally loads the result into a fact table destination.</span></span>  
  
 [<span data-ttu-id="75b17-132">第 2 课：添加循环</span><span class="sxs-lookup"><span data-stu-id="75b17-132">Lesson 2: Adding Looping</span></span>](lesson-2-adding-looping-with-ssis.md)  
 <span data-ttu-id="75b17-133">在本课中，将扩展第 1 课中创建的包，利用新增的循环功能，将多个平面文件提取到单个数据流进程中。</span><span class="sxs-lookup"><span data-stu-id="75b17-133">In this lesson, you will expand the package you created in Lesson 1 to take advantage of new looping features to extract multiple flat files into a single data flow process.</span></span>  
  
 [<span data-ttu-id="75b17-134">第 3 课：添加日志记录</span><span class="sxs-lookup"><span data-stu-id="75b17-134">Lesson 3: Adding Logging</span></span>](lesson-3-add-logging-with-ssis.md)  
 <span data-ttu-id="75b17-135">在本课中，将扩展第 2 课中创建的包，利用新增的日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="75b17-135">In this lesson, you will expand the package you created in Lesson 2 to take advantage of new logging features.</span></span>  
  
 [<span data-ttu-id="75b17-136">第 4 课：添加错误流重定向</span><span class="sxs-lookup"><span data-stu-id="75b17-136">Lesson 4: Adding Error Flow Redirection</span></span>](lesson-4-add-error-flow-redirection-with-ssis.md)  
 <span data-ttu-id="75b17-137">在本课中，将扩展第 3 课中创建的包，以便利用新增的错误输出配置。</span><span class="sxs-lookup"><span data-stu-id="75b17-137">In this lesson, you will expand the package you created in lesson 3 to take advantage of new error output configurations.</span></span>  
  
 [<span data-ttu-id="75b17-138">第 5 课：添加包部署模型的包配置</span><span class="sxs-lookup"><span data-stu-id="75b17-138">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
 <span data-ttu-id="75b17-139">在本课中，将扩展第 4 课中创建的包，利用新增的包配置选项。</span><span class="sxs-lookup"><span data-stu-id="75b17-139">In this lesson, you will expand the package you created in Lesson 4 to take advantage of new package configuration options.</span></span>  
  
 [<span data-ttu-id="75b17-140">第 6 课：对项目部署模型使用参数</span><span class="sxs-lookup"><span data-stu-id="75b17-140">Lesson 6: Using Parameters with the Project Deployment Model</span></span>](lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
 <span data-ttu-id="75b17-141">在本课中，将扩展第 5 课中创建的包，以将新参数用于项目部署模型。</span><span class="sxs-lookup"><span data-stu-id="75b17-141">In this lesson, you will expand the package you created in Lesson 5 to take advantage of using new parameters with the project deployment model.</span></span>  
  
  
