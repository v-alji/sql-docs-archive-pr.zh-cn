---
title: 数据库引擎脚本
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], PowerShell
- scripts [SQL Server]
- scripting [SQL Server Database Engine]
- scripting [SQL Server Database Engine], PowerShell
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
author: rothja
ms.author: jroth
ms.openlocfilehash: 79dca27e2aa5f2c0bc473534e0a8b204345b3993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576618"
---
# <a name="database-engine-scripting"></a><span data-ttu-id="5f1ee-102">数据库引擎脚本</span><span class="sxs-lookup"><span data-stu-id="5f1ee-102">Database Engine Scripting</span></span>
  <span data-ttu-id="5f1ee-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 支持 [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell 脚本环境，以管理 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例和这些实例中的对象。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-103">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] supports the [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell scripting environment to manage instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the objects in the instances.</span></span> <span data-ttu-id="5f1ee-104">还可以在与脚本环境非常类似的环境中生成并运行包含 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 Xquery 的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-104">You can also build and run [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries that contain [!INCLUDE[tsql](../../includes/tsql-md.md)] and XQuery in environments very similar to scripting environments.</span></span>  
  
## <a name="sql-server-powershell"></a><span data-ttu-id="5f1ee-105">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f1ee-105">SQL Server PowerShell</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5f1ee-106">包含两个可用来实现以下内容的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 管理单元：</span><span class="sxs-lookup"><span data-stu-id="5f1ee-106">includes two [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins that implement:</span></span>  
  
-   <span data-ttu-id="5f1ee-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 提供程序，它将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理对象模型层次结构公开为类似于文件系统路径的 PowerShell 路径。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-107">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider that exposes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management object model hierarchies as PowerShell paths that are similar to file system paths.</span></span> <span data-ttu-id="5f1ee-108">可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理对象模型类来管理路径的每个节点处表示的对象。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-108">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management object model classes to manage the objects represented at each node of the path.</span></span>  
  
-   <span data-ttu-id="5f1ee-109">一组执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 命令的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-109">A set of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cmdlets that implement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commands.</span></span> <span data-ttu-id="5f1ee-110">其中一个 cmdlet 是 **Invoke-Sqlcmd**。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-110">One of the cmdlets is **Invoke-Sqlcmd**.</span></span> <span data-ttu-id="5f1ee-111">这用于运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 要与实用工具一起运行的查询脚本 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-111">This is used to run [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query scripts to be run with the `sqlcmd` utility.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5f1ee-112">提供了用于运行 PowerShell 的以下功能：</span><span class="sxs-lookup"><span data-stu-id="5f1ee-112">provides these features for running PowerShell:</span></span>  
  
-   <span data-ttu-id="5f1ee-113">可导入到 PowerShell 会话中的 **sqlps** PowerShell 模块，该模块之后将加载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理单元。可以交互方式运行即席 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-113">The **sqlps** PowerShell module that can be imported to a PowerShell session, the module then loads the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] snap-ins. You can interactively run ad hoc PowerShell commands.</span></span> <span data-ttu-id="5f1ee-114">可以使用诸如 .\MyFolder\MyScript.ps1 这样的命令来运行脚本文件。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-114">You can run script files using a command such as .\MyFolder\MyScript.ps1.</span></span>  
  
-   <span data-ttu-id="5f1ee-115">PowerShell 脚本文件可用作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理 PowerShell 作业步骤的输入，这些步骤按预订的时间间隔或者作为对系统事件的响应来运行脚本。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-115">PowerShell script files can be used as input to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent PowerShell job steps that run the scripts either at scheduled intervals or in response to system events.</span></span>  
  
-   <span data-ttu-id="5f1ee-116">用于启动 PowerShell 和导入 **模块的** sqlps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-116">The **sqlps** utility that starts PowerShell and imports the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] module.</span></span> <span data-ttu-id="5f1ee-117">然后，您可以执行该模块支持的所有操作。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-117">You can then perform all actions supported by the module.</span></span> <span data-ttu-id="5f1ee-118">可以在命令提示符中启动 **sqlps** 实用工具，也可以通过在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio 对象资源管理器树中右键单击节点并选择“启动 PowerShell”  来启动 sqlps 实用工具。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-118">You can start the **sqlps** utility either in a command prompt or by right-clicking on the nodes in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio Object Explorer tree and selecting **Start PowerShell**.</span></span>  
  
## <a name="database-engine-queries"></a><span data-ttu-id="5f1ee-119">数据库引擎查询</span><span class="sxs-lookup"><span data-stu-id="5f1ee-119">Database Engine Queries</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="5f1ee-120">查询脚本包含三种类型的元素：</span><span class="sxs-lookup"><span data-stu-id="5f1ee-120">query scripts contain three types of elements:</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="5f1ee-121">语言语句。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-121">language statements.</span></span>  
  
-   <span data-ttu-id="5f1ee-122">Xquery 语言语句。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-122">XQuery language statements</span></span>  
  
-   <span data-ttu-id="5f1ee-123">实用工具中的命令和变量 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-123">Commands and variables from the `sqlcmd` utility.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5f1ee-124">提供了三种用于生成和运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询的环境：</span><span class="sxs-lookup"><span data-stu-id="5f1ee-124">provides three environments for building and running [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries:</span></span>  
  
-   <span data-ttu-id="5f1ee-125">可以在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中以交互方式运行和调试 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]查询。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-125">You can interactively run and debug [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5f1ee-126">可以在一个会话中编写并调试多个语句，然后将所有这些语句保存在一个脚本文件中。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-126">You can code and debug several statements in one session, then save all of the statements in a single script file.</span></span>  
  
-   <span data-ttu-id="5f1ee-127">通过 `sqlcmd` 命令提示实用工具，您可以以交互方式运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询，还可以运行现有的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询脚本文件。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-127">The `sqlcmd` command prompt utility lets you interactively run [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries, and also run existing [!INCLUDE[ssDE](../../includes/ssde-md.md)] query script files.</span></span>  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="5f1ee-128">查询脚本文件通常是使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中以交互方式进行编码的。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-128">query script files are typically coded interactively in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="5f1ee-129">之后，可在下面的某个环境中打开此文件：</span><span class="sxs-lookup"><span data-stu-id="5f1ee-129">The file can later be opened in one of these environments:</span></span>  
  
-   <span data-ttu-id="5f1ee-130">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的“文件”  /“打开”  菜单，在新的[!INCLUDE[ssDE](../../includes/ssde-md.md)]查询编辑器窗口中打开此文件。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-130">Use the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **File**/**Open** menu to open the file in a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span>  
  
-   <span data-ttu-id="5f1ee-131">使用 **-i**_input_file_参数通过实用工具运行文件 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-131">Use the **-i**_input_file_ parameter to run the file with the `sqlcmd` utility.</span></span>  
  
-   <span data-ttu-id="5f1ee-132">通过 **PowerShell 脚本中的** Invoke-Sqlcmd **cmdlet 使用** -QueryFromFile [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 参数运行此文件。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-132">Use the **-QueryFromFile** parameter to run the file with the **Invoke-Sqlcmd** cmdlet in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell scripts.</span></span>  
  
-   <span data-ttu-id="5f1ee-133">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作业步骤按计划的时间间隔或作为对系统事件的响应来运行脚本。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-133">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps to run the scripts either at scheduled intervals or in response to system events.</span></span>  
  
 <span data-ttu-id="5f1ee-134">此外，还可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生成脚本向导来生成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-134">In addition, you can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Generate Script Wizard to generate [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="5f1ee-135">可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对象资源管理器中右键单击对象，然后选择“生成脚本”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-135">You can right-click objects in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, then select the **Generate Script** menu item.</span></span> <span data-ttu-id="5f1ee-136">**“生成脚本”** 会启动向导，指导您完成创建脚本的过程。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-136">**Generate Script** launches the wizard, which guides you through the process of creating a script.</span></span>  
  
## <a name="database-engine-scripting-tasks"></a><span data-ttu-id="5f1ee-137">数据库引擎脚本任务</span><span class="sxs-lookup"><span data-stu-id="5f1ee-137">Database Engine Scripting Tasks</span></span>  
  
|<span data-ttu-id="5f1ee-138">任务说明</span><span class="sxs-lookup"><span data-stu-id="5f1ee-138">Task Description</span></span>|<span data-ttu-id="5f1ee-139">主题</span><span class="sxs-lookup"><span data-stu-id="5f1ee-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="5f1ee-140">介绍如何使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的代码和文本编辑器来以交互方式开发、调试和运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本</span><span class="sxs-lookup"><span data-stu-id="5f1ee-140">Describes how to use the code and text editors in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to interactively develop, debug, and run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts</span></span>|[<span data-ttu-id="5f1ee-141">查询和文本编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5f1ee-141">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)|  
|<span data-ttu-id="5f1ee-142">介绍如何使用 `sqlcmd` 实用工具从命令提示符运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本，包括以交互方式开发脚本的能力。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-142">Describes how to use the `sqlcmd` utility to run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts from the command prompt, including the ability to interactively develop scripts.</span></span>|[<span data-ttu-id="5f1ee-143">sqlcmd 操作指南主题</span><span class="sxs-lookup"><span data-stu-id="5f1ee-143">sqlcmd How-to Topics</span></span>](../../database-engine/sqlcmd-how-to-topics.md)|  
|<span data-ttu-id="5f1ee-144">介绍如何将 SQL Server 组件集成到 Windows PowerShell 2.0 环境中，然后生成 PowerShell 脚本以便管理 SQL Server 实例和对象。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-144">Describes how to integrate the SQL Server components into a Windows PowerShell 2.0 environment and then build PowerShell scripts for managing SQL Server instances and objects.</span></span>|[<span data-ttu-id="5f1ee-145">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f1ee-145">SQL Server PowerShell</span></span>](../../powershell/sql-server-powershell.md)|  
|<span data-ttu-id="5f1ee-146">介绍如何使用 **“生成和发布脚本”** 向导创建从数据库重新创建一个或多个对象的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="5f1ee-146">Describes how to use the **Generate and Publish Scripts** wizard to create [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that recreate one or more of the objects from a database.</span></span>|[<span data-ttu-id="5f1ee-147">生成脚本 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5f1ee-147">Generate Scripts &#40;SQL Server Management Studio&#41;</span></span>](generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a><span data-ttu-id="5f1ee-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f1ee-148">See Also</span></span>  
 <span data-ttu-id="5f1ee-149">[sqlcmd 实用工具](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="5f1ee-149">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="5f1ee-150">教程：编写 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="5f1ee-150">Tutorial: Writing Transact-SQL Statements</span></span>](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
