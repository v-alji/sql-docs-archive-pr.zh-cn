---
title: 启动 dta 命令提示符实用工具并优化工作负荷 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: f34a5acf-1f3b-4484-a770-6470cb925ab0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4b2b1755a2ce8299556ab7d0ae14c89d3b2c8554
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682533"
---
# <a name="starting-the-dta-command-prompt-utility-and-tuning-a-workload"></a><span data-ttu-id="4419c-102">启动 dta 命令提示实用工具并优化工作负荷</span><span class="sxs-lookup"><span data-stu-id="4419c-102">Starting the dta Command Prompt Utility and Tuning a Workload</span></span>
  <span data-ttu-id="4419c-103">此任务指导你如何从命令提示符下启动 **dta** 实用工具，查看其帮助，以及使用它优化工作负荷。</span><span class="sxs-lookup"><span data-stu-id="4419c-103">This task guides you through starting the **dta** utility, viewing its Help, and then using it to tune a workload from the command prompt.</span></span> <span data-ttu-id="4419c-104">它使用为数据库引擎优化顾问图形用户界面 (GUI 创建的工作负荷，) 实践[优化工作负荷](lesson-1-1-tuning-a-workload.md)。</span><span class="sxs-lookup"><span data-stu-id="4419c-104">It uses the workload, MyScript.sql, which you created for the Database Engine Tuning Advisor graphical user interface (GUI) practice [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
 <span data-ttu-id="4419c-105">本教程使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="4419c-105">The tutorial uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="4419c-106">出于安全原因，默认情况下不安装该示例数据库。</span><span class="sxs-lookup"><span data-stu-id="4419c-106">For security reasons, the sample databases are not installed by default.</span></span> <span data-ttu-id="4419c-107">若要安装示例数据库，请参阅 [安装 SQL Server 示例和示例数据库](http://sqlserversamples.codeplex.com)。</span><span class="sxs-lookup"><span data-stu-id="4419c-107">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
 <span data-ttu-id="4419c-108">以下任务将指导你打开命令提示符，启动 **dta** 命令提示实用工具，查看其语法帮助，并优化在 [优化工作负荷](lesson-1-1-tuning-a-workload.md)中创建的一个简单工作负荷 MyScript.sql。</span><span class="sxs-lookup"><span data-stu-id="4419c-108">The following tasks guide you through opening a command prompt, starting the **dta** command prompt utility, viewing its syntax Help, and tuning a simple workload, MyScript.sql, which you created in [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
### <a name="to-start-the-dta-command-prompt-utility-and-view-help"></a><span data-ttu-id="4419c-109">启动 dta 命令提示实用工具并查看帮助</span><span class="sxs-lookup"><span data-stu-id="4419c-109">To start the dta command prompt utility and view Help</span></span>  
  
1.  <span data-ttu-id="4419c-110">在“开始”\*\*\*\* 菜单中，依次指向“所有程序”\*\*\*\*、“附件”\*\*\*\*，再单击“命令提示符”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4419c-110">On the **Start** menu, point to **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="4419c-111">在命令提示符下，键入以下命令，再按 Enter 键：</span><span class="sxs-lookup"><span data-stu-id="4419c-111">At the command prompt, type the following, and press ENTER:</span></span>  
  
    ```  
    dta -? | more  
    ```  
  
     <span data-ttu-id="4419c-112">该命令的 `| more` 部分是可选的。</span><span class="sxs-lookup"><span data-stu-id="4419c-112">The `| more` part of this command is optional.</span></span> <span data-ttu-id="4419c-113">但是，使用该选项可以逐页查看实用工具的语法帮助。</span><span class="sxs-lookup"><span data-stu-id="4419c-113">However, using it enables you to page through the syntax help for the utility.</span></span> <span data-ttu-id="4419c-114">按 Enter 键可以按行翻阅帮助文本，按空格键可按页翻阅。</span><span class="sxs-lookup"><span data-stu-id="4419c-114">Press ENTER to advance the help text by the line, or press the SPACEBAR to advance it by the page.</span></span>  
  
### <a name="to-tune-a-simple-workload-by-using-the-dta-command-prompt-utility"></a><span data-ttu-id="4419c-115">使用 dta 命令提示实用工具优化一个简单的工作负荷</span><span class="sxs-lookup"><span data-stu-id="4419c-115">To tune a simple workload by using the dta command prompt utility</span></span>  
  
1.  <span data-ttu-id="4419c-116">在命令提示符下，导航到存储 MyScript.sql 文件的目录。</span><span class="sxs-lookup"><span data-stu-id="4419c-116">At the command prompt, navigate to the directory where you have stored the MyScript.sql file.</span></span>  
  
2.  <span data-ttu-id="4419c-117">在命令提示符下，键入以下命令，然后按 Enter 键运行该命令并启动优化会话（请注意，实用工具分析命令时区分大小写）：</span><span class="sxs-lookup"><span data-stu-id="4419c-117">At the command prompt, type the following, and press ENTER to run the command and start the tuning session (note that the utility is case-sensitive when it parses commands):</span></span>  
  
    ```  
    dta -S YourServerName\YourSQLServerInstanceName -E -D AdventureWorks2012 -if MyScript.sql -s MySession2 -of MySession2OutputScript.sql -ox MySession2Output.xml -fa IDX_IV -fp NONE -fk NONE  
    ```  
  
     <span data-ttu-id="4419c-118">其中 `-S` 指定安装了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的服务器和 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="4419c-118">where `-S` specifies the name of your server and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance where the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database is installed.</span></span> <span data-ttu-id="4419c-119">`-E` 设置指定要使用可信连接来连接实例。使用 Windows 域帐户连接时可使用该设置。</span><span class="sxs-lookup"><span data-stu-id="4419c-119">The setting `-E` specifies that you want to use a trusted connection to the instance, which is appropriate if you are connecting with a Windows domain account.</span></span> <span data-ttu-id="4419c-120">`-D` 设置指定要优化的数据库， `-if` 指定工作负荷文件， `-s` 指定会话名称， `-of` 指定该工具要将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 建议脚本写入其中的文件， `-ox` 指定该工具要将 XML 格式的建议脚本写入其中的文件。</span><span class="sxs-lookup"><span data-stu-id="4419c-120">The setting `-D` specifies the database that you want to tune, `-if` specifies the workload file, `-s` specifies the session name, `-of` specifies the file to which you want the tool to write the [!INCLUDE[tsql](../../includes/tsql-md.md)] recommendations script, and `-ox` specifies the file to which you want the tool to write the recommendations in XML format.</span></span> <span data-ttu-id="4419c-121">最后三个开关指定如下优化选项： `-fa IDX_IV` 指定数据库引擎优化顾问应该只考虑添加索引（包括聚集和非聚集索引）和索引视图； `-fp NONE` 指定分析时不考虑分区策略； `-fk NONE` 指定数据库引擎优化顾问进行建议时不必保留数据库中的现有物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="4419c-121">The last three switches specify tuning options as follows: `-fa IDX_IV` specifies that Database Engine Tuning Advisor should only consider adding indexes (both clustered and nonclustered) and indexed views; `-fp NONE` specifies that no partition strategy should be considered during analysis; and `-fk NONE` specifies that no existing physical design structures in the database must be kept when Database Engine Tuning Advisor makes its recommendations.</span></span>  
  
3.  <span data-ttu-id="4419c-122">数据库引擎优化顾问完成了优化工作负荷后，将显示一个消息指示优化会话已成功完成。</span><span class="sxs-lookup"><span data-stu-id="4419c-122">After Database Engine Tuning Advisor finishes tuning the workload, it displays a message indicating that your tuning session completed successfully.</span></span> <span data-ttu-id="4419c-123">若要查看优化结果，可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 打开 MySession2OutputScript.sql 和 MySession2Output.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="4419c-123">You can view the tuning results, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to open the files MySession2OutputScript.sql and MySession2Output.xml.</span></span> <span data-ttu-id="4419c-124">此外，也可以在数据库引擎优化顾问 GUI 中打开 MySession2 优化会话并查看其建议和报告，执行的方式与 [查看优化建议](lesson-1-2-viewing-tuning-recommendations.md) 和 [查看优化报告](lesson-1-3-viewing-tuning-reports.md)中执行的方式相同。</span><span class="sxs-lookup"><span data-stu-id="4419c-124">Alternatively, you can also open the MySession2 tuning session in the Database Engine Tuning Advisor GUI and view its recommendations and reports in the same way that you did in [Viewing Tuning Recommendations](lesson-1-2-viewing-tuning-recommendations.md) and [Viewing Tuning Reports](lesson-1-3-viewing-tuning-reports.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="4419c-125">摘要</span><span class="sxs-lookup"><span data-stu-id="4419c-125">Summary</span></span>  
 <span data-ttu-id="4419c-126">你已使用 **dta** 实用工具在命令提示符下完成了对一个简单工作负荷的优化。</span><span class="sxs-lookup"><span data-stu-id="4419c-126">You have completed tuning a simple workload from the command prompt by using the **dta** utility.</span></span> <span data-ttu-id="4419c-127">该工具还提供了其他许多优化选项。</span><span class="sxs-lookup"><span data-stu-id="4419c-127">This tool provides many other tuning options.</span></span> <span data-ttu-id="4419c-128">有关详细信息，请参阅工具帮助 (**dta -?**) 和参考主题 [dta 实用工具](dta-utility.md) 。</span><span class="sxs-lookup"><span data-stu-id="4419c-128">Refer to the tool Help (**dta -?**) and the reference topic [dta Utility](dta-utility.md) for more information.</span></span>  
  
## <a name="after-you-finish-this-tutorial"></a><span data-ttu-id="4419c-129">学完本教程后</span><span class="sxs-lookup"><span data-stu-id="4419c-129">After You Finish This Tutorial</span></span>  
 <span data-ttu-id="4419c-130">学完本教程中的课程后，请参考以下主题来了解有关数据库引擎优化顾问的详细信息：</span><span class="sxs-lookup"><span data-stu-id="4419c-130">After you finish the lessons in this tutorial, refer to the following topics for more information about Database Engine Tuning Advisor:</span></span>  
  
-   <span data-ttu-id="4419c-131">[数据库引擎优化顾问](../../relational-databases/performance/database-engine-tuning-advisor.md) 提供有关如何使用此工具执行任务的说明。</span><span class="sxs-lookup"><span data-stu-id="4419c-131">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) for descriptions of how to perform tasks with this tool.</span></span>  
  
-   <span data-ttu-id="4419c-132">[dta 实用工具](dta-utility.md) 提供有关此命令提示实用工具的参考材料和可用于控制此实用工具的操作的可选 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="4419c-132">[dta Utility](dta-utility.md) for reference material on the command prompt utility and the optional XML file you can use to control the operation of the utility.</span></span>  
  
 <span data-ttu-id="4419c-133">若要返回教程的起始位置，请参阅 [教程：数据库引擎优化顾问](tutorial-database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="4419c-133">To return to the start of the tutorial, see [Tutorial: Database Engine Tuning Advisor](tutorial-database-engine-tuning-advisor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4419c-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4419c-134">See Also</span></span>  
 [<span data-ttu-id="4419c-135">数据库引擎教程</span><span class="sxs-lookup"><span data-stu-id="4419c-135">Database Engine Tutorials</span></span>](../../relational-databases/database-engine-tutorials.md)  
  
  
