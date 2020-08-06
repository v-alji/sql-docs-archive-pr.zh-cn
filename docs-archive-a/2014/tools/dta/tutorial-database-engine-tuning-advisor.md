---
title: 教程：数据库引擎优化顾问 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], tutorials
- tutorials [Database Engine Tuning Advisor]
ms.assetid: 3b54cbbe-d8c6-424d-92f1-aa58179f4da8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 68e026cb28b875b834f20c906232285ede8e217b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577984"
---
# <a name="tutorial-database-engine-tuning-advisor"></a><span data-ttu-id="c2889-102">教程：Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="c2889-102">Tutorial: Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="c2889-103">欢迎使用数据库引擎优化顾问教程。</span><span class="sxs-lookup"><span data-stu-id="c2889-103">Welcome to the Database Engine Tuning Advisor tutorial.</span></span> <span data-ttu-id="c2889-104">数据库引擎优化顾问检查指定数据库中处理查询的方式，然后建议如何通过修改数据库结构（例如索引、索引视图和分区）来改善查询处理性能。</span><span class="sxs-lookup"><span data-stu-id="c2889-104">Database Engine Tuning Advisor examines how queries are processed in the databases you specify, and then recommends how you can improve query processing performance by modifying database structures such as indexes, indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="c2889-105">数据库引擎优化顾问提供两个用户界面：图形用户界面 (GUI) 和 **dta** 命令提示实用工具。</span><span class="sxs-lookup"><span data-stu-id="c2889-105">Database Engine Tuning Advisor provides two user interfaces: a graphical user interface (GUI) and the **dta** command prompt utility.</span></span> <span data-ttu-id="c2889-106">使用 GUI 可以方便快捷地查看优化会话结果，而使用 **dta** 实用工具则可以轻松地将数据库引擎优化顾问功能并入脚本中，从而实现自动优化。</span><span class="sxs-lookup"><span data-stu-id="c2889-106">The GUI makes it easy to quickly view the results of tuning sessions, and the **dta** utility makes it easy to incorporate Database Engine Tuning Advisor functionality into scripts for automated tuning.</span></span> <span data-ttu-id="c2889-107">此外，数据库引擎优化顾问可以接受 XML 输入，该输入可对优化过程进行更多控制。</span><span class="sxs-lookup"><span data-stu-id="c2889-107">In addition, Database Engine Tuning Advisor can take XML input, which offers more control over the tuning process.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="c2889-108">学习内容</span><span class="sxs-lookup"><span data-stu-id="c2889-108">What You Will Learn</span></span>  
 <span data-ttu-id="c2889-109">本教程将讲述如何定位数据库引擎优化顾问 GUI，以及如何通过 GUI 和 **dta** 实用工具执行一些基本任务。</span><span class="sxs-lookup"><span data-stu-id="c2889-109">This tutorial will teach you how to navigate the Database Engine Tuning Advisor GUI, and how to perform some basic tasks with both the GUI and the **dta** utility.</span></span> <span data-ttu-id="c2889-110">本教程包含以下几课：</span><span class="sxs-lookup"><span data-stu-id="c2889-110">It contains the following lessons:</span></span>  
  
 [<span data-ttu-id="c2889-111">第 1 课：数据库引擎优化顾问基本导览</span><span class="sxs-lookup"><span data-stu-id="c2889-111">Lesson 1: Basic Navigation in Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
 <span data-ttu-id="c2889-112">在本课程中，您将熟悉新的数据库引擎优化顾问 GUI，并学习如何设置显示选项和布局。</span><span class="sxs-lookup"><span data-stu-id="c2889-112">In this lesson, you will familiarize yourself with the new Database Engine Tuning Advisor GUI and learn how to set display options and layout.</span></span>  
  
 [<span data-ttu-id="c2889-113">第 2 课：使用数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="c2889-113">Lesson 2: Using Database Engine Tuning Advisor</span></span>](lesson-2-using-database-engine-tuning-advisor.md)  
 <span data-ttu-id="c2889-114">在本课中，您将学习如何通过数据库引擎优化顾问 GUI 执行基本的优化任务。</span><span class="sxs-lookup"><span data-stu-id="c2889-114">In this lesson, you will learn how to perform basic tuning tasks with the Database Engine Tuning Advisor GUI.</span></span>  
  
 [<span data-ttu-id="c2889-115">第 3 课：使用 dta 命令提示实用工具</span><span class="sxs-lookup"><span data-stu-id="c2889-115">Lesson 3: Using the dta Command Prompt Utility</span></span>](lesson-3-using-the-dta-command-prompt-utility.md)  
 <span data-ttu-id="c2889-116">在本课程中，将学习如何启动 **dta** 命令提示实用工具以及如何运行一些简单的优化命令。</span><span class="sxs-lookup"><span data-stu-id="c2889-116">In this lesson, you learn how to start the **dta** command prompt utility and how to run some simple tuning commands.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2889-117">要求</span><span class="sxs-lookup"><span data-stu-id="c2889-117">Requirements</span></span>  
 <span data-ttu-id="c2889-118">本教程面向符合以下条件的数据库管理员：不熟悉数据库引擎优化顾问 GUI 或 **dta** 命令提示实用工具，但对于数据库概念和结构（如索引和索引视图）经验丰富。</span><span class="sxs-lookup"><span data-stu-id="c2889-118">This tutorial is intended for database administrators who are not familiar with the Database Engine Tuning Advisor GUI or the **dta** command prompt utility, but who are experienced with database concepts and structures, such as indexes and indexed views.</span></span>  
  
 <span data-ttu-id="c2889-119">必须使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 示例数据库安装 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] （或更高版本）。</span><span class="sxs-lookup"><span data-stu-id="c2889-119">You must install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (or a later version) with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="c2889-120">为了增强安全性，默认情况下不会安装示例数据库。</span><span class="sxs-lookup"><span data-stu-id="c2889-120">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="c2889-121">若要安装示例数据库，请参阅 [安装 SQL Server 示例和示例数据库](http://sqlserversamples.codeplex.com)。</span><span class="sxs-lookup"><span data-stu-id="c2889-121">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
## <a name="after-you-finish-this-tutorial"></a><span data-ttu-id="c2889-122">学完本教程后</span><span class="sxs-lookup"><span data-stu-id="c2889-122">After You Finish This Tutorial</span></span>  
 <span data-ttu-id="c2889-123">学完本教程中的课程后，请参考以下主题来了解有关数据库引擎优化顾问的详细信息：</span><span class="sxs-lookup"><span data-stu-id="c2889-123">After you finish the lessons in this tutorial, refer to the following topics for more information about Database Engine Tuning Advisor:</span></span>  
  
-   <span data-ttu-id="c2889-124">[数据库引擎优化顾问](../../relational-databases/performance/database-engine-tuning-advisor.md) 提供有关如何使用此工具执行任务的说明。</span><span class="sxs-lookup"><span data-stu-id="c2889-124">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) for descriptions of how to perform tasks with this tool.</span></span>  
  
-   <span data-ttu-id="c2889-125">[dta 实用工具](dta-utility.md) 提供有关此命令提示实用工具的参考材料和可用于控制此实用工具的操作的可选 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="c2889-125">[dta Utility](dta-utility.md) for reference material on the command prompt utility and the optional XML file you can use to control the operation of the utility.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="c2889-126">下一课</span><span class="sxs-lookup"><span data-stu-id="c2889-126">Next Lesson</span></span>  
 [<span data-ttu-id="c2889-127">第 1 课：数据库引擎优化顾问基本导览</span><span class="sxs-lookup"><span data-stu-id="c2889-127">Lesson 1: Basic Navigation in Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
