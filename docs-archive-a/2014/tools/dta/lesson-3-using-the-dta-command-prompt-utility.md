---
title: 第3课：使用 dta 命令提示实用工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 30f27f4d-8852-4b12-ba62-57f63e496f1d
author: stevestein
ms.author: sstein
ms.openlocfilehash: abbde02cd73e01937e6d0669c10f2db28da8a76e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682530"
---
# <a name="lesson-3-using-the-dta-command-prompt-utility"></a><span data-ttu-id="d4504-102">第 3 课：使用 dta 命令提示实用工具</span><span class="sxs-lookup"><span data-stu-id="d4504-102">Lesson 3: Using the dta Command Prompt Utility</span></span>
  <span data-ttu-id="d4504-103">**dta** 命令提示实用工具除了包含数据库引擎优化顾问提供的功能之外，还包含其他功能。</span><span class="sxs-lookup"><span data-stu-id="d4504-103">The **dta** command-prompt utility offers functionality in addition to that provided by the Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="d4504-104">通过数据库引擎优化顾问 XML 架构，您可以使用自己喜爱的 XML 工具创建实用工具的输入文件。</span><span class="sxs-lookup"><span data-stu-id="d4504-104">You can use your favorite XML tools to create input files for the utility by using the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="d4504-105">该架构随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一起安装，可在 C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd 中找到。</span><span class="sxs-lookup"><span data-stu-id="d4504-105">This schema is installed when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and can be found at: C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd.</span></span>  
  
 <span data-ttu-id="d4504-106">数据库引擎优化顾问 XML 架构也可通过 [此 Microsoft 网站](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)在线获得。</span><span class="sxs-lookup"><span data-stu-id="d4504-106">The Database Engine Tuning Advisor XML schema is also available online at [this Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).</span></span>  
  
 <span data-ttu-id="d4504-107">数据库引擎优化顾问 XML 架构在设置优化选项时可提供更大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="d4504-107">The Database Engine Tuning Advisor XML schema provides more flexibility to set tuning options.</span></span> <span data-ttu-id="d4504-108">例如，可通过它执行“假设分析”。</span><span class="sxs-lookup"><span data-stu-id="d4504-108">For example, it enables you to perform "what-if" analysis.</span></span> <span data-ttu-id="d4504-109">“假设分析”包括：为要优化的数据库指定一组现有的假设物理设计结构，然后使用数据库引擎优化顾问对该数据库进行分析，以判定此假设物理设计是否能改善查询处理性能。</span><span class="sxs-lookup"><span data-stu-id="d4504-109">"What-if" analysis involves specifying a set of existing and hypothetical physical design structures for the database you want to tune, and then analyzing it with the Database Engine Tuning Advisor to find out whether this hypothetical physical design will improve query processing performance.</span></span> <span data-ttu-id="d4504-110">此类分析具有的优点是，在评估新配置时不会引起实际实施它的开销。</span><span class="sxs-lookup"><span data-stu-id="d4504-110">This type of analysis provides the advantage of evaluating the new configuration without incurring the overhead of actually implementing it.</span></span> <span data-ttu-id="d4504-111">如果假设物理设计不能提供预期的性能改善，则可以方便地进行更改和重新分析，直到获得能够满足需要的配置为止。</span><span class="sxs-lookup"><span data-stu-id="d4504-111">If your hypothetical physical design does not provide the performance improvements you want, it is easy to change it and analyze it again until you reach the configuration that produces the results you need.</span></span>  
  
 <span data-ttu-id="d4504-112">此外，通过结合使用数据库引擎优化顾问 XML 架构和 **dta** 命令提示实用工具，可以将数据库引擎优化顾问功能加入到脚本中，并可将其与其他数据库设计工具一起使用。</span><span class="sxs-lookup"><span data-stu-id="d4504-112">In addition, using the Database Engine Tuning Advisor XML schema and the **dta** command-prompt utility, you can incorporate Database Engine Tuning Advisor functionality into scripts and use it with other database design tools.</span></span>  
  
 <span data-ttu-id="d4504-113">使用数据库引擎优化顾问的 XML 输入功能不在本课程的讨论范围之内。</span><span class="sxs-lookup"><span data-stu-id="d4504-113">Using the XML input functionality of Database Engine Tuning Advisor is beyond the scope of this lesson.</span></span>  
  
 <span data-ttu-id="d4504-114">本课程介绍了 **dta** 命令提示实用工具的基本语法，如何访问帮助，以及如何优化简单的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="d4504-114">This lesson provides an introduction to the basic **dta** command-prompt utility syntax, how to access help, and practice for tuning simple workloads.</span></span>  
  
 <span data-ttu-id="d4504-115">本节包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="d4504-115">It contains the following topic:</span></span>  
  
-   <span data-ttu-id="d4504-116">启动**dta**命令提示实用工具并优化工作负荷</span><span class="sxs-lookup"><span data-stu-id="d4504-116">Starting the **dta** Command Prompt Utility and Tuning a Workload</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d4504-117">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="d4504-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d4504-118">启动 dta 命令提示实用工具并优化工作负荷</span><span class="sxs-lookup"><span data-stu-id="d4504-118">Starting the dta Command Prompt Utility and Tuning a Workload</span></span>](lesson-1-1-tuning-a-workload.md)  
  
  
