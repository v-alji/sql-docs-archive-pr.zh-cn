---
title: 第2课：添加循环 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 65efb84b4e50b470470e396bbe5681ce4b5dfac3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579631"
---
# <a name="lesson-2-adding-looping"></a><span data-ttu-id="29e7d-102">第 2 课：添加循环</span><span class="sxs-lookup"><span data-stu-id="29e7d-102">Lesson 2: Adding Looping</span></span>
  <span data-ttu-id="29e7d-103">在[第1课：创建项目和基本包](lesson-1-create-a-project-and-basic-package-with-ssis.md)中，创建了从单个平面文件源提取数据的包，使用查找转换转换数据，最后将数据加载到**AdventureWorksDW2012**示例数据库的**FactCurrency**事实数据表中。</span><span class="sxs-lookup"><span data-stu-id="29e7d-103">In [Lesson 1: Creating the Project and Basic Package](lesson-1-create-a-project-and-basic-package-with-ssis.md), you created a package that extracted data from a single flat file source, transformed the data using Lookup transformations, and finally loaded the data into the **FactCurrency** fact table of the **AdventureWorksDW2012** sample database.</span></span>  
  
 <span data-ttu-id="29e7d-104">但是，提取、转换和加载 (ETL) 过程很少使用单个平面文件。</span><span class="sxs-lookup"><span data-stu-id="29e7d-104">However, it is rare for an extract, transform, and load (ETL) process to use a single flat file.</span></span> <span data-ttu-id="29e7d-105">典型的 ETL 过程从多个平面文件源提取数据。</span><span class="sxs-lookup"><span data-stu-id="29e7d-105">A typical ETL process would extract data from multiple flat file sources.</span></span> <span data-ttu-id="29e7d-106">从多个源提取数据需要采用迭代控制流。</span><span class="sxs-lookup"><span data-stu-id="29e7d-106">Extracting data from multiple sources requires an iterative control flow.</span></span> <span data-ttu-id="29e7d-107">的最重要功能之一是能够 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 轻松地向包中添加迭代或循环。</span><span class="sxs-lookup"><span data-stu-id="29e7d-107">One of the most anticipated features of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is the ability to easily add iteration or looping to packages.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="29e7d-108">为循环遍历包提供了两种容器类型：Foreach 循环容器和 For 循环容器。</span><span class="sxs-lookup"><span data-stu-id="29e7d-108">provides two types of containers for looping through packages: the Foreach Loop container and the For Loop container.</span></span> <span data-ttu-id="29e7d-109">Foreach 循环容器使用枚举器执行循环，而 For 循环容器则通常使用变量表达式。</span><span class="sxs-lookup"><span data-stu-id="29e7d-109">The Foreach Loop container uses an enumerator to perform the looping, whereas the For Loop container typically uses a variable expression.</span></span> <span data-ttu-id="29e7d-110">本课使用 Foreach 循环容器。</span><span class="sxs-lookup"><span data-stu-id="29e7d-110">This lesson uses the Foreach Loop container.</span></span>  
  
 <span data-ttu-id="29e7d-111">Foreach 循环容器使包能够对指定枚举器的每个成员重复执行控制流。</span><span class="sxs-lookup"><span data-stu-id="29e7d-111">The Foreach Loop container enables a package to repeat the control flow for each member of a specified enumerator.</span></span> <span data-ttu-id="29e7d-112">使用 Foreach 循环容器，可以枚举：</span><span class="sxs-lookup"><span data-stu-id="29e7d-112">With the Foreach Loop container, you can enumerate:</span></span>  
  
-   <span data-ttu-id="29e7d-113">ADO 记录集行</span><span class="sxs-lookup"><span data-stu-id="29e7d-113">ADO recordset rows</span></span>  
  
-   <span data-ttu-id="29e7d-114">ADO .Net 架构信息</span><span class="sxs-lookup"><span data-stu-id="29e7d-114">ADO .Net schema information</span></span>  
  
-   <span data-ttu-id="29e7d-115">文件和目录结构</span><span class="sxs-lookup"><span data-stu-id="29e7d-115">File and directory structures</span></span>  
  
-   <span data-ttu-id="29e7d-116">系统、包和用户变量</span><span class="sxs-lookup"><span data-stu-id="29e7d-116">System, package and user variables</span></span>  
  
-   <span data-ttu-id="29e7d-117">在变量中包含的可枚举对象</span><span class="sxs-lookup"><span data-stu-id="29e7d-117">Enumerable objects contained in a variable</span></span>  
  
-   <span data-ttu-id="29e7d-118">集合中的项</span><span class="sxs-lookup"><span data-stu-id="29e7d-118">Items in a collection</span></span>  
  
-   <span data-ttu-id="29e7d-119">XML Path 语言 (XPath) 表达式中的节点</span><span class="sxs-lookup"><span data-stu-id="29e7d-119">Nodes in an XML Path Language (XPath) expression</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="29e7d-120">管理对象 (SMO)</span><span class="sxs-lookup"><span data-stu-id="29e7d-120">Management Objects (SMO)</span></span>  
  
 <span data-ttu-id="29e7d-121">在本课中，您将修改在第 1 课中创建的简单 ETL 包，以便利用 Foreach 循环容器。</span><span class="sxs-lookup"><span data-stu-id="29e7d-121">In this lesson, you will modify the simple ETL package created in Lesson 1 to take advantage of the Foreach Loop container.</span></span> <span data-ttu-id="29e7d-122">还将设置用户定义的包变量，以便使该教程包能够迭代遍历文件夹中的所有平面文件。</span><span class="sxs-lookup"><span data-stu-id="29e7d-122">You will also set user-defined package variables to enable the tutorial package to iterate through all the flat files in the folder.</span></span> <span data-ttu-id="29e7d-123">如果您尚未完成上一课，则也可以复制本教程中附带的已完成的 Lesson 1 包。</span><span class="sxs-lookup"><span data-stu-id="29e7d-123">If you have not completed the previous lesson, you can also copy the completed Lesson 1 package that is included with the tutorial.</span></span>  
  
 <span data-ttu-id="29e7d-124">在本课中，将不修改数据流，而只修改控制流。</span><span class="sxs-lookup"><span data-stu-id="29e7d-124">In this lesson, you will not modify the data flow, only the control flow.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="29e7d-125">本教程需要 **AdventureWorksDW2012** 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="29e7d-125">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="29e7d-126">有关如何安装和部署 **AdventureWorksDW2012**的详细信息，请参阅 [CodePlex 上的 Reporting Services 产品示例](https://go.microsoft.com/fwlink/p/?LinkID=526910)。</span><span class="sxs-lookup"><span data-stu-id="29e7d-126">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples on CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="29e7d-127">课程任务</span><span class="sxs-lookup"><span data-stu-id="29e7d-127">Lesson Tasks</span></span>  
 <span data-ttu-id="29e7d-128">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="29e7d-128">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="29e7d-129">步骤 1：复制 Lesson 1 包</span><span class="sxs-lookup"><span data-stu-id="29e7d-129">Step 1: Copying the Lesson 1 Package</span></span>](lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [<span data-ttu-id="29e7d-130">步骤 2：添加和配置 Foreach 循环容器</span><span class="sxs-lookup"><span data-stu-id="29e7d-130">Step 2: Adding and Configuring the Foreach Loop Container</span></span>](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [<span data-ttu-id="29e7d-131">步骤 3：修改平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="29e7d-131">Step 3: Modifying the Flat File Connection Manager</span></span>](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [<span data-ttu-id="29e7d-132">步骤 4：测试第 2 课教程包</span><span class="sxs-lookup"><span data-stu-id="29e7d-132">Step 4: Testing the Lesson 2 Tutorial Package</span></span>](lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="29e7d-133">开始课程</span><span class="sxs-lookup"><span data-stu-id="29e7d-133">Start the Lesson</span></span>  
 [<span data-ttu-id="29e7d-134">步骤 1：复制 Lesson 1 包</span><span class="sxs-lookup"><span data-stu-id="29e7d-134">Step 1: Copying the Lesson 1 Package</span></span>](lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a><span data-ttu-id="29e7d-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29e7d-135">See Also</span></span>  
 [<span data-ttu-id="29e7d-136">For 循环容器</span><span class="sxs-lookup"><span data-stu-id="29e7d-136">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
