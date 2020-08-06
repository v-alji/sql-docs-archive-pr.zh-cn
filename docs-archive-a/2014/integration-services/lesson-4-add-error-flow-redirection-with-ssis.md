---
title: 第4课：添加错误流重定向 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5b1d1ff9abf59a6288d1b693fce5a6fb707a129b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693399"
---
# <a name="lesson-4-adding-error-flow-redirection"></a><span data-ttu-id="98c92-102">第 4 课：添加错误流重定向</span><span class="sxs-lookup"><span data-stu-id="98c92-102">Lesson 4: Adding Error Flow Redirection</span></span>
  <span data-ttu-id="98c92-103">为了处理在转换过程中可能发生的错误， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 使您能够根据每个组件和每个列来决定如何处理无法转换的数据。</span><span class="sxs-lookup"><span data-stu-id="98c92-103">To handle errors that may occur in the transformation process, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] gives you the ability to decide on a per component and per column basis how to handle data that cannot be transformed.</span></span> <span data-ttu-id="98c92-104">可以选择忽略某些列中的失败、重定向整个失败的行或者只是使组件失败。</span><span class="sxs-lookup"><span data-stu-id="98c92-104">You can choose to ignore a failure in certain columns, redirect the entire failed row, or just fail the component.</span></span> <span data-ttu-id="98c92-105">默认情况下， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的所有组件被配置为在发生错误时失败。</span><span class="sxs-lookup"><span data-stu-id="98c92-105">By default, all components in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] are configured to fail when errors occur.</span></span> <span data-ttu-id="98c92-106">而使组件失败又会导致包失败，并使所有后续处理停止。</span><span class="sxs-lookup"><span data-stu-id="98c92-106">Failing a component, in turn, causes the package to fail and all subsequent processing to stop.</span></span>  
  
 <span data-ttu-id="98c92-107">如果不让失败导致包停止执行，一个好方法是通过配置使在转换中发生潜在处理错误时这些错误能够得到处理。</span><span class="sxs-lookup"><span data-stu-id="98c92-107">Instead of letting failures stop package execution, it is good practice to configure and handle potential processing errors as they occur within the transformation.</span></span> <span data-ttu-id="98c92-108">虽然可能选择忽略失败以确保包成功运行，但通常更好的做法是将失败的行重定向到另一个处理路径，在这里可以使数据和错误持久化、接受检查并在随后的某个时间对其进行重新处理。</span><span class="sxs-lookup"><span data-stu-id="98c92-108">While you might choose to ignore failures to ensure your package runs successfully, it is often better to redirect the failed row to another processing path where the data and the error can be persisted, examined and reprocessed at a later time.</span></span>  
  
 <span data-ttu-id="98c92-109">在本课中，将创建在 [Lesson 3: Adding Logging](lesson-3-add-logging-with-ssis.md)中开发的包的副本。</span><span class="sxs-lookup"><span data-stu-id="98c92-109">In this lesson, you will create a copy of the package that you developed in [Lesson 3: Adding Logging](lesson-3-add-logging-with-ssis.md).</span></span> <span data-ttu-id="98c92-110">使用这个新包时，将创建一个示例数据文件的损坏版本。</span><span class="sxs-lookup"><span data-stu-id="98c92-110">Working with this new package, you will create a corrupted version of one of the sample data files.</span></span> <span data-ttu-id="98c92-111">损坏的文件将在运行包时强制发生处理错误。</span><span class="sxs-lookup"><span data-stu-id="98c92-111">The corrupted file will force a processing error to occur when you run the package.</span></span>  
  
 <span data-ttu-id="98c92-112">为了处理错误数据，您将添加并配置一个平面文件目标，它会将所有无法在 Lookup Currency Key 转换中找到查找值的行写入文件。</span><span class="sxs-lookup"><span data-stu-id="98c92-112">To handle the error data, you will add and configure a Flat File destination that will write any rows that fail to locate a lookup value in the Lookup Currency Key transformation to a file.</span></span>  
  
 <span data-ttu-id="98c92-113">将错误数据写入文件之前，需要包括一个使用脚本获取错误说明的脚本组件。</span><span class="sxs-lookup"><span data-stu-id="98c92-113">Before the error data is written to the file, you will include a Script component that uses script to get error descriptions.</span></span> <span data-ttu-id="98c92-114">然后，将重新配置 Lookup Currency Key 转换，以便将所有无法处理的数据重定向到脚本转换中。</span><span class="sxs-lookup"><span data-stu-id="98c92-114">You will then reconfigure the Lookup Currency Key transformation to redirect any data that could not be processed to the Script transformation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="98c92-115">本教程需要 **AdventureWorksDW2012** 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="98c92-115">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="98c92-116">有关如何安装和部署 **AdventureWorksDW2012**的详细信息，请参阅 [CodePlex 上的 Reporting Services 产品示例项目](https://go.microsoft.com/fwlink/p/?LinkId=526910)。</span><span class="sxs-lookup"><span data-stu-id="98c92-116">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples Project on CodePlex](https://go.microsoft.com/fwlink/p/?LinkId=526910).</span></span>  
  
## <a name="tasks-in-lesson"></a><span data-ttu-id="98c92-117">课程中的任务</span><span class="sxs-lookup"><span data-stu-id="98c92-117">Tasks in Lesson</span></span>  
 <span data-ttu-id="98c92-118">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="98c92-118">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="98c92-119">步骤 1：复制第 3 课包</span><span class="sxs-lookup"><span data-stu-id="98c92-119">Step 1: Copying the Lesson 3 Package</span></span>](lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [<span data-ttu-id="98c92-120">步骤 2：创建损坏的文件</span><span class="sxs-lookup"><span data-stu-id="98c92-120">Step 2: Creating a Corrupted File</span></span>](lesson-4-2-creating-a-corrupted-file.md)  
  
-   [<span data-ttu-id="98c92-121">步骤 3：添加错误流重定向</span><span class="sxs-lookup"><span data-stu-id="98c92-121">Step 3: Adding Error Flow Redirection</span></span>](lesson-4-3-adding-error-flow-redirection.md)  
  
-   [<span data-ttu-id="98c92-122">步骤 4：添加平面文件目标</span><span class="sxs-lookup"><span data-stu-id="98c92-122">Step 4: Adding a Flat File Destination</span></span>](lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [<span data-ttu-id="98c92-123">步骤 5：测试第 4 课教程包</span><span class="sxs-lookup"><span data-stu-id="98c92-123">Step 5: Testing the Lesson 4 Tutorial Package</span></span>](lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="98c92-124">开始课程</span><span class="sxs-lookup"><span data-stu-id="98c92-124">Start the Lesson</span></span>  
 [<span data-ttu-id="98c92-125">步骤 1：复制第 3 课包</span><span class="sxs-lookup"><span data-stu-id="98c92-125">Step 1: Copying the Lesson 3 Package</span></span>](lesson-4-1-copying-the-lesson-3-package.md)  
  
  
