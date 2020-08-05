---
title: 第3课：添加日志记录 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58fcc29759f19ad215a76a1b9ed9bf313b4c869c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581373"
---
# <a name="lesson-3-adding-logging"></a><span data-ttu-id="8ad20-102">第 3 课：添加日志记录</span><span class="sxs-lookup"><span data-stu-id="8ad20-102">Lesson 3: Adding Logging</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="8ad20-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包含日志记录功能，可通过提供任务和容器事件跟踪监控包执行情况以及进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="8ad20-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] includes logging features that let you troubleshoot and monitor package execution by providing a trace of task and container events.</span></span> <span data-ttu-id="8ad20-104">日志记录功能非常灵活，可以在包级别或在包中的各个任务和容器上启用。</span><span class="sxs-lookup"><span data-stu-id="8ad20-104">The logging features are flexible, and can be enabled at the package level or on individual tasks and containers within the package.</span></span> <span data-ttu-id="8ad20-105">可以选择要记录的事件，也可以对单个包创建多个日志。</span><span class="sxs-lookup"><span data-stu-id="8ad20-105">You can select which events you want to log, and create multiple logs against a single package.</span></span>  
  
 <span data-ttu-id="8ad20-106">日志记录由日志提供程序提供。</span><span class="sxs-lookup"><span data-stu-id="8ad20-106">Logging is provided by a log provider.</span></span> <span data-ttu-id="8ad20-107">每个日志提供程序可以将日志记录信息写入不同的格式和目标类型。</span><span class="sxs-lookup"><span data-stu-id="8ad20-107">Each log provider can write logging information to different formats and destination types.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="8ad20-108">提供以下日志提供程序：</span><span class="sxs-lookup"><span data-stu-id="8ad20-108">provides the following log providers:</span></span>  
  
-   <span data-ttu-id="8ad20-109">文本文件</span><span class="sxs-lookup"><span data-stu-id="8ad20-109">Text file</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   <span data-ttu-id="8ad20-110">Windows 事件日志</span><span class="sxs-lookup"><span data-stu-id="8ad20-110">Windows Event log</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="8ad20-111">XML 文件</span><span class="sxs-lookup"><span data-stu-id="8ad20-111">XML file</span></span>  
  
 <span data-ttu-id="8ad20-112">在本课中，您将为 [Lesson 2: Adding Looping](lesson-2-adding-looping-with-ssis.md)中创建的包创建副本。</span><span class="sxs-lookup"><span data-stu-id="8ad20-112">In this lesson, you will create a copy of the package that you created in [Lesson 2: Adding Looping](lesson-2-adding-looping-with-ssis.md).</span></span> <span data-ttu-id="8ad20-113">使用这个新包，您将添加并配置日志记录，以在包执行过程中监控特定事件。</span><span class="sxs-lookup"><span data-stu-id="8ad20-113">Working with this new package, you will then add and configure logging to monitor specific events during package execution.</span></span> <span data-ttu-id="8ad20-114">如果您尚未完成前面的任何课程，也可以复制本教程附带的已完成的 Lesson 2 包。</span><span class="sxs-lookup"><span data-stu-id="8ad20-114">If you have not completed any of the previous lessons, you can also copy the completed Lesson 2 package that is included with the tutorial.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8ad20-115">本教程需要 **AdventureWorksDW2012** 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="8ad20-115">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="8ad20-116">有关如何安装和部署**AdventureWorksDW2012**的详细信息，请[Reporting Services GitHub 上的产品示例](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。</span><span class="sxs-lookup"><span data-stu-id="8ad20-116">For more information about how to install and deploy **AdventureWorksDW2012**, [Reporting Services Product Samples on GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="8ad20-117">课程任务</span><span class="sxs-lookup"><span data-stu-id="8ad20-117">Lesson Tasks</span></span>  
 <span data-ttu-id="8ad20-118">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="8ad20-118">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="8ad20-119">步骤 1：复制第 2 课包</span><span class="sxs-lookup"><span data-stu-id="8ad20-119">Step 1: Copying the Lesson 2 Package</span></span>](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [<span data-ttu-id="8ad20-120">步骤 2：添加并配置日志记录</span><span class="sxs-lookup"><span data-stu-id="8ad20-120">Step 2: Adding and Configuring Logging</span></span>](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [<span data-ttu-id="8ad20-121">步骤 3：测试第 3 课教程包</span><span class="sxs-lookup"><span data-stu-id="8ad20-121">Step 3: Testing the Lesson 3 Tutorial Package</span></span>](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="8ad20-122">开始课程</span><span class="sxs-lookup"><span data-stu-id="8ad20-122">Start the Lesson</span></span>  
 [<span data-ttu-id="8ad20-123">步骤 1：复制第 2 课包</span><span class="sxs-lookup"><span data-stu-id="8ad20-123">Step 1: Copying the Lesson 2 Package</span></span>](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
