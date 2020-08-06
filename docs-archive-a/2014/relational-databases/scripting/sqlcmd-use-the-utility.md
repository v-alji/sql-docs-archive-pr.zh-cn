---
title: 使用 sqlcmd 实用工具
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL statements, executing
- command prompt utilities [SQL Server], sqlcmd
- statements [SQL Server], executing
- sqlcmd utility, about sqlcmd utility
ms.assetid: 3ec89119-7314-43ef-9e91-12e72bb63d62
author: rothja
ms.author: jroth
ms.openlocfilehash: 922f9915272fb2d7fc63487ec135ce44ee91e88b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588960"
---
# <a name="use-the-sqlcmd-utility"></a><span data-ttu-id="5d60f-102">使用 sqlcmd 实用工具</span><span class="sxs-lookup"><span data-stu-id="5d60f-102">Use the sqlcmd Utility</span></span>
  <span data-ttu-id="5d60f-103">`sqlcmd` 实用工具是一个命令行实用工具，用于 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和脚本的即席、交互执行以及自动执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本撰写任务。</span><span class="sxs-lookup"><span data-stu-id="5d60f-103">The `sqlcmd` utility is a command-line utility for ad hoc, interactive execution of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and scripts and for automating [!INCLUDE[tsql](../../includes/tsql-md.md)] scripting tasks.</span></span> <span data-ttu-id="5d60f-104">若要以交互方式使用 `sqlcmd`，或要生成可使用 `sqlcmd` 运行的脚本文件，用户需要了解 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d60f-104">To use `sqlcmd` interactively, or to build script files to be run using `sqlcmd`, users must understand [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5d60f-105">`sqlcmd`实用程序通常按以下方式使用：</span><span class="sxs-lookup"><span data-stu-id="5d60f-105">The `sqlcmd` utility is typically used in the following ways:</span></span>  
  
-   <span data-ttu-id="5d60f-106">用户以交互方式输入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，输入方式与在命令提示符下输入的方式类似。</span><span class="sxs-lookup"><span data-stu-id="5d60f-106">Users interactively enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a manner similar to working at the command prompt.</span></span> <span data-ttu-id="5d60f-107">结果将显示在命令提示符处。</span><span class="sxs-lookup"><span data-stu-id="5d60f-107">The results are displayed at the command prompt.</span></span> <span data-ttu-id="5d60f-108">若要打开命令提示符窗口，依次单击 **“开始”**、 **“所有程序”**，指向 **“附件”**，然后单击 **“命令提示符”**。</span><span class="sxs-lookup"><span data-stu-id="5d60f-108">To open a Command Prompt window, click **Start**, click **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span> <span data-ttu-id="5d60f-109">在命令提示符处，键入 `sqlcmd`，后面跟随所需的选项列表。</span><span class="sxs-lookup"><span data-stu-id="5d60f-109">At the command prompt, type `sqlcmd` followed by a list of options that you want.</span></span> <span data-ttu-id="5d60f-110">有关支持的选项的完整列表 `sqlcmd` ，请参阅[sqlcmd 实用工具](../../tools/sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="5d60f-110">For a complete list of the options that are supported by `sqlcmd`, see [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span>  
  
-   <span data-ttu-id="5d60f-111">用户通过下列方式提交 `sqlcmd` 作业：指定要执行的单个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，或将实用工具指向要执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句所在的文本文件。</span><span class="sxs-lookup"><span data-stu-id="5d60f-111">Users submit a `sqlcmd` job either by specifying a single [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to execute, or by pointing the utility to a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to execute.</span></span> <span data-ttu-id="5d60f-112">输出通常定向到一个文本文件，但也可以显示在命令提示符处。</span><span class="sxs-lookup"><span data-stu-id="5d60f-112">The output is usually directed to a text file, but it can also be displayed at the command prompt.</span></span>  
  
-   <span data-ttu-id="5d60f-113">[查询编辑器中的](edit-sqlcmd-scripts-with-query-editor.md) SQLCMD 模式 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5d60f-113">[SQLCMD mode](edit-sqlcmd-scripts-with-query-editor.md) in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span>  
  
-   <span data-ttu-id="5d60f-114">SQL Server 管理对象 (SMO)</span><span class="sxs-lookup"><span data-stu-id="5d60f-114">SQL Server Management Objects (SMO)</span></span>  
  
-   <span data-ttu-id="5d60f-115">SQL Server 代理 CmdExec 作业。</span><span class="sxs-lookup"><span data-stu-id="5d60f-115">SQL Server Agent CmdExec jobs.</span></span>  
  
## <a name="typically-used-sqlcmd-options"></a><span data-ttu-id="5d60f-116">常用 sqlcmd 选项</span><span class="sxs-lookup"><span data-stu-id="5d60f-116">Typically Used sqlcmd Options</span></span>  
 <span data-ttu-id="5d60f-117">最常用的选项如下：</span><span class="sxs-lookup"><span data-stu-id="5d60f-117">The following options are used most frequently:</span></span>  
  
-   <span data-ttu-id="5d60f-118">服务器\*\*选项 () \*\* ，用于标识 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接到的实例 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="5d60f-118">The server option (**-S**) that identifies the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to which `sqlcmd` connects.</span></span>  
  
-   <span data-ttu-id="5d60f-119">身份验证选项 (**-E**、 **-U**和 **-P**) ，用于指定用于 `sqlcmd` 连接到实例的凭据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5d60f-119">Authentication options (**-E**, **-U**, and **-P**) that specify the credentials that `sqlcmd` uses to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d60f-120">**-E** 选项为默认选项，毋须指定。</span><span class="sxs-lookup"><span data-stu-id="5d60f-120">The **-E** option is the default and does not have to be specified.</span></span>  
  
-   <span data-ttu-id="5d60f-121">输入选项 (**-q**、 **-q**和 **-i**) ，用于标识输入的位置 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="5d60f-121">Input options (**-Q**, **-q**, and **-i**) that identify the location of the input to `sqlcmd`.</span></span>  
  
-   <span data-ttu-id="5d60f-122">Output 选项 (**-o**) ，用于指定 `sqlcmd` 要放置其输出的文件。</span><span class="sxs-lookup"><span data-stu-id="5d60f-122">The output option (**-o**) that specifies the file in which `sqlcmd` is to put its output.</span></span>  
  
## <a name="connecting-to-the-sqlcmd-utility"></a><span data-ttu-id="5d60f-123">连接到 sqlcmd 实用工具</span><span class="sxs-lookup"><span data-stu-id="5d60f-123">Connecting to the sqlcmd Utility</span></span>  
 <span data-ttu-id="5d60f-124">以下是 `sqlcmd` 实用工具的常见用法：</span><span class="sxs-lookup"><span data-stu-id="5d60f-124">The following are common uses of the `sqlcmd` utility:</span></span>  
  
-   <span data-ttu-id="5d60f-125">使用 Windows 身份验证连接到默认实例，以交互方式运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="5d60f-125">Connecting to a default instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d60f-126">在前面的示例中，未指定 **-E** ，因为它是默认值，并且 `sqlcmd` 通过使用 Windows 身份验证连接到默认实例。</span><span class="sxs-lookup"><span data-stu-id="5d60f-126">In the previous example, **-E** is not specified because it is the default and `sqlcmd` connects to the default instance by using Windows Authentication.</span></span>  
  
-   <span data-ttu-id="5d60f-127">使用 Windows 身份验证连接到命名实例，以交互方式运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="5d60f-127">Connecting to a named instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName>  
    ```  
  
     <span data-ttu-id="5d60f-128">或</span><span class="sxs-lookup"><span data-stu-id="5d60f-128">or</span></span>  
  
    ```  
    sqlcmd -S .\<InstanceName>  
    ```  
  
-   <span data-ttu-id="5d60f-129">使用 Windows 身份验证连接到命名实例，并指定输入和输出文件：</span><span class="sxs-lookup"><span data-stu-id="5d60f-129">Connecting to a named instance by using Windows Authentication and specifying input and output files:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName> -i <MyScript.sql> -o <MyOutput.rpt>  
    ```  
  
-   <span data-ttu-id="5d60f-130">使用 Windows 身份验证连接到本地计算机上的默认实例，执行查询，并在查询运行完毕后使 `sqlcmd` 保持运行状态：</span><span class="sxs-lookup"><span data-stu-id="5d60f-130">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, and having `sqlcmd` remain running after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -q "SELECT * FROM AdventureWorks2012.Person.Person"  
    ```  
  
-   <span data-ttu-id="5d60f-131">使用 Windows 身份验证连接到本地计算机上的默认实例，执行查询，将输出定向到某个文件，并在查询运行完毕后使 `sqlcmd` 退出：</span><span class="sxs-lookup"><span data-stu-id="5d60f-131">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, directing the output to a file, and having `sqlcmd` exit after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -Q "SELECT * FROM AdventureWorks2012.Person.Person" -o MyOutput.txt  
    ```  
  
-   <span data-ttu-id="5d60f-132">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到命名实例，以交互方式运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，并由 `sqlcmd` 提示输入密码：</span><span class="sxs-lookup"><span data-stu-id="5d60f-132">Connecting to a named instance using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, with `sqlcmd` prompting for a password:</span></span>  
  
    ```  
    sqlcmd -U MyLogin -S <ComputerName>\<InstanceName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d60f-133">若要查看 `sqlcmd` 实用工具所支持选项的列表，请运行：`sqlcmd -?`。</span><span class="sxs-lookup"><span data-stu-id="5d60f-133">To see a list of the options that are supported by the `sqlcmd` utility run: `sqlcmd -?`.</span></span>  
  
## <a name="running-transact-sql-statements-interactively-by-using-sqlcmd"></a><span data-ttu-id="5d60f-134">使用 sqlcmd 以交互方式运行 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="5d60f-134">Running Transact-SQL Statements Interactively by Using sqlcmd</span></span>  
 <span data-ttu-id="5d60f-135">您可以使用 `sqlcmd` 实用工具以交互方式在命令提示符窗口中执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="5d60f-135">You can use the `sqlcmd` utility interactively to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a Command Prompt window.</span></span> <span data-ttu-id="5d60f-136">若要使用以交互方式执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句 `sqlcmd` ，请在不使用 **-q**、 **-q**、 **-Z**或 **-i**选项指定任何输入文件或查询的情况下运行实用工具。</span><span class="sxs-lookup"><span data-stu-id="5d60f-136">To interactively execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using `sqlcmd`, run the utility without using the **-Q**, **-q**, **-Z**, or **-i** options to specify any input files or queries.</span></span> <span data-ttu-id="5d60f-137">例如：</span><span class="sxs-lookup"><span data-stu-id="5d60f-137">For example:</span></span>  
  
 `sqlcmd -S <ComputerName>\<InstanceName>`  
  
 <span data-ttu-id="5d60f-138">在未指定输入文件或查询的情况下执行命令时，`sqlcmd` 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的指定实例，然后显示一个新行，其中包含 `1>` 并且后面跟着一个闪烁的下划线（称为 `sqlcmd` 提示符）。</span><span class="sxs-lookup"><span data-stu-id="5d60f-138">When the command is executed without input files or queries, `sqlcmd` connects to the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then displays a new line with a `1>` followed by a blinking underscore that is named the `sqlcmd` prompt.</span></span> <span data-ttu-id="5d60f-139">`1` 表示这是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的第一行，而 `sqlcmd` 提示符则是您键入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的起点。</span><span class="sxs-lookup"><span data-stu-id="5d60f-139">The `1` signifies that this is the first line of a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, and the `sqlcmd` prompt is the point at which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will start when you type it in.</span></span>  
  
 <span data-ttu-id="5d60f-140">在 `sqlcmd` 提示符中，可以键入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和 `sqlcmd` 命令，如 `GO` 和 `EXIT`。</span><span class="sxs-lookup"><span data-stu-id="5d60f-140">At the `sqlcmd` prompt, you can type both [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands, such as `GO` and `EXIT`.</span></span> <span data-ttu-id="5d60f-141">每个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句放在称为“语句缓存”的缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="5d60f-141">Each [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is put in a buffer called the statement cache.</span></span> <span data-ttu-id="5d60f-142">键入 `GO` 命令并按 Enter 键后，这些语句将发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d60f-142">These statements are sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] after you type the `GO` command and press ENTER.</span></span> <span data-ttu-id="5d60f-143">若要退出 `sqlcmd` ， `EXIT` 请 `QUIT` 在新行的开头键入或。</span><span class="sxs-lookup"><span data-stu-id="5d60f-143">To exit `sqlcmd`, type `EXIT` or `QUIT` at the start of a new line.</span></span>  
  
 <span data-ttu-id="5d60f-144">若要清除语句缓存，请键入 `:RESET`。</span><span class="sxs-lookup"><span data-stu-id="5d60f-144">To clear the statement cache, type `:RESET`.</span></span> <span data-ttu-id="5d60f-145">键入 `^C` `sqlcmd` 将导致退出。</span><span class="sxs-lookup"><span data-stu-id="5d60f-145">Typing `^C` causes `sqlcmd` to exit.</span></span> <span data-ttu-id="5d60f-146">在发出 `^C` 命令后，还可以用 `GO` 停止语句缓存的执行。</span><span class="sxs-lookup"><span data-stu-id="5d60f-146">`^C` can also be used to stop the execution of the statement cache after a `GO` command has been issued.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="5d60f-147">可以通过输入 **： ED**命令和提示符来编辑在交互式会话中输入的语句 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="5d60f-147">statements that are entered in an interactive session can edited by entering the **:ED** command and the `sqlcmd` prompt.</span></span> <span data-ttu-id="5d60f-148">编辑器将打开，编辑 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句并关闭编辑器后，修改后的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将显示于命令窗口中。</span><span class="sxs-lookup"><span data-stu-id="5d60f-148">The editor will open and, after editing the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement and closing the editor, the revised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will appear in the command window.</span></span> <span data-ttu-id="5d60f-149">输入 `GO` 以运行 therevised [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="5d60f-149">Enter `GO` to run therevised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
## <a name="quoted-strings"></a><span data-ttu-id="5d60f-150">带引号的字符串</span><span class="sxs-lookup"><span data-stu-id="5d60f-150">Quoted Strings</span></span>  
 <span data-ttu-id="5d60f-151">用引号引起来的字符无需任何额外的预处理即可使用。例外，输入两个连续的引号可以将引号插入字符串中。</span><span class="sxs-lookup"><span data-stu-id="5d60f-151">Characters that are enclosed in quotation marks are used without any additional preprocessing, except that quotations marks can be inserted into a string by entering two consecutive quotation marks.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5d60f-152">将这种字符序列视作一个引号。</span><span class="sxs-lookup"><span data-stu-id="5d60f-152">treats this character sequence as one quotation mark.</span></span> <span data-ttu-id="5d60f-153">（但在服务器上会进行转换。）当脚本变量出现在字符串中时，不会展开它们。</span><span class="sxs-lookup"><span data-stu-id="5d60f-153">(However, the translation occurs in the server.) Scripting variables will not be expanded when they appear within a string.</span></span>  
  
 <span data-ttu-id="5d60f-154">例如：</span><span class="sxs-lookup"><span data-stu-id="5d60f-154">For example:</span></span>  
  
 `sqlcmd`  
  
 `PRINT "Length: 5"" 7'";`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Length: 5" 7'`  
  
## <a name="strings-that-span-multiple-lines"></a><span data-ttu-id="5d60f-155">跨多行的字符串</span><span class="sxs-lookup"><span data-stu-id="5d60f-155">Strings That Span Multiple Lines</span></span>  
 <span data-ttu-id="5d60f-156">`sqlcmd` 支持包含跨多行的字符串的脚本。</span><span class="sxs-lookup"><span data-stu-id="5d60f-156">`sqlcmd` supports scripts that have strings that span multiple lines.</span></span> <span data-ttu-id="5d60f-157">例如，下面的 `SELECT` 语句跨多行，但键入 `GO`并按 Enter 键后，将执行单个字符串。</span><span class="sxs-lookup"><span data-stu-id="5d60f-157">For example, the following `SELECT` statement spans multiple lines but is a single string executed when you press the ENTER key after typing `GO`.</span></span>  
  
 `SELECT First line`  
  
 `FROM Second line`  
  
 `WHERE Third line;`  
  
 `GO`  
  
## <a name="interactive-sqlcmd-example"></a><span data-ttu-id="5d60f-158">交互式 sqlcmd 示例</span><span class="sxs-lookup"><span data-stu-id="5d60f-158">Interactive sqlcmd Example</span></span>  
 <span data-ttu-id="5d60f-159">本示例说明了以交互方式运行 `sqlcmd` 的过程。</span><span class="sxs-lookup"><span data-stu-id="5d60f-159">This is an example of what you see when you run `sqlcmd` interactively.</span></span>  
  
 <span data-ttu-id="5d60f-160">打开命令提示符窗口时，出现如下一行内容：</span><span class="sxs-lookup"><span data-stu-id="5d60f-160">When you open a Command Prompt window, there is one line similar to:</span></span>  
  
 `C:\> _`  
  
 <span data-ttu-id="5d60f-161">这表示文件夹 `C:\` 为当前文件夹，如果您指定文件名，则 Windows 将在此文件夹中查找这个文件。</span><span class="sxs-lookup"><span data-stu-id="5d60f-161">This means the folder `C:\` is the current folder, and if you specify a file name, Windows will look for the file in that folder.</span></span>  
  
 <span data-ttu-id="5d60f-162">键入 `sqlcmd` 连接到本地计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 默认实例，命令提示符窗口的内容为：</span><span class="sxs-lookup"><span data-stu-id="5d60f-162">Type `sqlcmd` to connect to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer, and the contents of the Command Prompt window will be:</span></span>  
  
 `C:\>sqlcmd`  
  
 `1> _`  
  
 <span data-ttu-id="5d60f-163">这表示您已连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，并且 `sqlcmd` 现在已可以接受 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和 `sqlcmd` 命令。</span><span class="sxs-lookup"><span data-stu-id="5d60f-163">This means you have connected to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and `sqlcmd` is now ready to accept [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands.</span></span> <span data-ttu-id="5d60f-164">`1>` 后闪烁的下划线是 `sqlcmd` 提示符，它标明了所键入语句和命令的显示位置。</span><span class="sxs-lookup"><span data-stu-id="5d60f-164">The flashing underscore after the `1>` is the `sqlcmd` prompt that marks the location at which the statements and commands you type will be displayed.</span></span> <span data-ttu-id="5d60f-165">现在，键入 `USE AdventureWorks2012` 并按 enter，然后键入 `GO` 并按 enter。</span><span class="sxs-lookup"><span data-stu-id="5d60f-165">Now, type `USE AdventureWorks2012` and press ENTER, and then type `GO` and press ENTER.</span></span> <span data-ttu-id="5d60f-166">命令提示符窗口的内容如下：</span><span class="sxs-lookup"><span data-stu-id="5d60f-166">The contents of the Command Prompt window will be:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `1> _`  
  
 <span data-ttu-id="5d60f-167">输入 `USE AdventureWorks2012` 后按 Enter 键，即向 `sqlcmd` 发出换行信号。</span><span class="sxs-lookup"><span data-stu-id="5d60f-167">Pressing ENTER after entering `USE AdventureWorks2012` signaled `sqlcmd` to start a new line.</span></span> <span data-ttu-id="5d60f-168">键入 `GO,` 后按 Enter 键，即向 `sqlcmd` 发出信号将 `USE AdventureWorks2012` 语句发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="5d60f-168">Pressing ENTER, after you type `GO,` signaled `sqlcmd` to send the `USE AdventureWorks2012` statement to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5d60f-169">`sqlcmd` 随后返回一条消息，指示 `USE` 语句已成功完成并显示新的 `1>` 提示符作为输入新语句或命令的信号。</span><span class="sxs-lookup"><span data-stu-id="5d60f-169">`sqlcmd` then returned a message to indicate that the `USE` statement completed successfully and displayed a new `1>` prompt as a signal to enter a new statement or command.</span></span>  
  
 <span data-ttu-id="5d60f-170">下面的示例说明了键入 `SELECT` 语句和 `GO` 执行 `SELECT`以及键入 `EXIT` 退出 `sqlcmd`时命令提示符窗口包含的内容：</span><span class="sxs-lookup"><span data-stu-id="5d60f-170">The following example shows what the Command Prompt window contains if you type a `SELECT` statement, a `GO` to execute the `SELECT`, and an `EXIT` to exit `sqlcmd`:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `BusinessEntityID   FirstName                 LastName`  
  
 `----------- -------------------------------- -----------`  
  
 `1           Syed                             Abbas`  
  
 `2           Catherine                        Abel`  
  
 `3           Kim                              Abercrombie`  
  
 `(3 rows affected)`  
  
 `1> EXIT`  
  
 `C:\>`  
  
 <span data-ttu-id="5d60f-171">行 `3> GO` 后的几行内容为 `SELECT` 语句的输出。</span><span class="sxs-lookup"><span data-stu-id="5d60f-171">The lines after line `3> GO` are the output of a `SELECT` statement.</span></span> <span data-ttu-id="5d60f-172">生成输出后， `sqlcmd` 重置 `sqlcmd` 提示符并显示 `1>`。</span><span class="sxs-lookup"><span data-stu-id="5d60f-172">After you generate output, `sqlcmd` resets the `sqlcmd` prompt and displays `1>`.</span></span> <span data-ttu-id="5d60f-173">在 `EXIT` 行输入 `1>`后，命令提示符窗口显示第一次打开时显示的行。</span><span class="sxs-lookup"><span data-stu-id="5d60f-173">After entering `EXIT` at line `1>`, the Command Prompt window displays the same line it did when you first opened it.</span></span> <span data-ttu-id="5d60f-174">它指示 `sqlcmd` 已退出会话。</span><span class="sxs-lookup"><span data-stu-id="5d60f-174">This indicates that `sqlcmd` has exited its session.</span></span> <span data-ttu-id="5d60f-175">现在可以再键入一个 `EXIT` 命令关闭命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="5d60f-175">You can now close the Command Prompt window by typing another `EXIT` command.</span></span>  
  
## <a name="running-transact-sql-script-files-by-using-sqlcmd"></a><span data-ttu-id="5d60f-176">使用 sqlcmd 运行 Transact-SQL 脚本文件</span><span class="sxs-lookup"><span data-stu-id="5d60f-176">Running Transact-SQL Script Files by Using sqlcmd</span></span>  
 <span data-ttu-id="5d60f-177">可以使用 `sqlcmd` 执行数据库脚本文件。</span><span class="sxs-lookup"><span data-stu-id="5d60f-177">You can use `sqlcmd` to execute database script files.</span></span> <span data-ttu-id="5d60f-178">脚本文件是包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句、 `sqlcmd` 命令和脚本变量混合的文本文件。</span><span class="sxs-lookup"><span data-stu-id="5d60f-178">Script files are text files that contain a mix of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, `sqlcmd` commands, and scripting variables.</span></span> <span data-ttu-id="5d60f-179">有关如何使用脚本变量的详细信息，请参阅 [将 sqlcmd 与脚本变量结合使用](sqlcmd-use-with-scripting-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="5d60f-179">For more information about how to script variables, see [Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md).</span></span> <span data-ttu-id="5d60f-180">`sqlcmd` 与脚本文件中语句、命令和脚本变量的配合方式类似于它与交互输入的语句和命令的配合方式。</span><span class="sxs-lookup"><span data-stu-id="5d60f-180">`sqlcmd` works with the statements, commands, and scripting variables in a script file in a manner similar to how it works with statements and commands that are entered interactively.</span></span> <span data-ttu-id="5d60f-181">主要区别在于 `sqlcmd` 从输入文件连续读取内容，而不是等待用户输入语句、命令和脚本变量。</span><span class="sxs-lookup"><span data-stu-id="5d60f-181">The main difference is that `sqlcmd` reads through the input file without pause instead of waiting for a user to enter the statements, commands, and scripting variables.</span></span>  
  
 <span data-ttu-id="5d60f-182">可以通过几种不同的方式创建数据库脚本文件：</span><span class="sxs-lookup"><span data-stu-id="5d60f-182">There are different ways to create database script files:</span></span>  
  
-   <span data-ttu-id="5d60f-183">可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中以交互方式生成和调试一组 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]语句，然后将“查询”窗口中的内容另存为脚本文件。</span><span class="sxs-lookup"><span data-stu-id="5d60f-183">You can interactively build and debug a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then save the contents of the Query window as a script file.</span></span>  
  
-   <span data-ttu-id="5d60f-184">可以使用记事本等文本编辑器创建包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的文本文件。</span><span class="sxs-lookup"><span data-stu-id="5d60f-184">You can create a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using a text editor, such as Notepad.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5d60f-185">示例</span><span class="sxs-lookup"><span data-stu-id="5d60f-185">Examples</span></span>  
  
### <a name="a-running-a-script-by-using-sqlcmd"></a><span data-ttu-id="5d60f-186">A.</span><span class="sxs-lookup"><span data-stu-id="5d60f-186">A.</span></span> <span data-ttu-id="5d60f-187">使用 sqlcmd 运行脚本</span><span class="sxs-lookup"><span data-stu-id="5d60f-187">Running a script by using sqlcmd</span></span>  
 <span data-ttu-id="5d60f-188">启动记事本并键入以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="5d60f-188">Start Notepad, and type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 <span data-ttu-id="5d60f-189">创建一个名为 `MyFolder` 的文件夹，然后将脚本另存为文件夹 `MyScript.sql` 中的文件 `C:\MyFolder`。</span><span class="sxs-lookup"><span data-stu-id="5d60f-189">Create a folder named `MyFolder` and then save the script as the file `MyScript.sql` in the folder `C:\MyFolder`.</span></span> <span data-ttu-id="5d60f-190">在命令提示符处输入以下命令运行脚本，并将输出放入 `MyOutput.txt` 的 `MyFolder`中：</span><span class="sxs-lookup"><span data-stu-id="5d60f-190">Enter the following at the command prompt to run the script and put the output in `MyOutput.txt` in `MyFolder`:</span></span>  
  
 `sqlcmd -i C:\MyFolder\MyScript.sql -o C:\MyFolder\MyOutput.txt`  
  
 <span data-ttu-id="5d60f-191">在记事本中查看 `MyOutput.txt` 的内容时，将看到以下内容：</span><span class="sxs-lookup"><span data-stu-id="5d60f-191">When you view the contents of `MyOutput.txt` in Notepad, you will see the following:</span></span>  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `BusinessEntityID FirstName   LastName`  
  
 `---------------- ----------- -----------`  
  
 `1                Syed        Abbas`  
  
 `2                Catherine   Abel`  
  
 `3                Kim         Abercrombie`  
  
 `(3 rows affected)`  
  
### <a name="b-using-sqlcmd-with-a-dedicated-administrative-connection"></a><span data-ttu-id="5d60f-192">B.</span><span class="sxs-lookup"><span data-stu-id="5d60f-192">B.</span></span> <span data-ttu-id="5d60f-193">通过专用管理连接使用 sqlcmd</span><span class="sxs-lookup"><span data-stu-id="5d60f-193">Using sqlcmd with a dedicated administrative connection</span></span>  
 <span data-ttu-id="5d60f-194">在下面的示例中， `sqlcmd` 通过专用管理员连接 (DAC) 连接到一台具有阻塞问题的服务器。</span><span class="sxs-lookup"><span data-stu-id="5d60f-194">In the following example, `sqlcmd` is used to connect to a server that has a blocking problem by using the dedicated administrator connection (DAC).</span></span>  
  
 `C:\>sqlcmd -S ServerName -A`  
  
 `1> SELECT blocked FROM sys.dm_exec_requests WHERE blocked <> 0;`  
  
 `2> GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `spid   blocked`  
  
 `------ -------`  
  
 `62       64`  
  
 `(1 rows affected)`  
  
 <span data-ttu-id="5d60f-195">使用 `sqlcmd` 结束阻塞进程。</span><span class="sxs-lookup"><span data-stu-id="5d60f-195">Use `sqlcmd` to end the blocking process.</span></span>  
  
 `1> KILL 64;`  
  
 `2> GO`  
  
### <a name="c-using-sqlcmd-to-execute-a-stored-procedure"></a><span data-ttu-id="5d60f-196">C.</span><span class="sxs-lookup"><span data-stu-id="5d60f-196">C.</span></span> <span data-ttu-id="5d60f-197">使用 sqlcmd 执行存储过程</span><span class="sxs-lookup"><span data-stu-id="5d60f-197">Using sqlcmd to execute a stored procedure</span></span>  
 <span data-ttu-id="5d60f-198">下面的示例说明如何使用 `sqlcmd`执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="5d60f-198">The following example shows how to execute a stored procedure by using `sqlcmd`.</span></span> <span data-ttu-id="5d60f-199">创建以下存储过程。</span><span class="sxs-lookup"><span data-stu-id="5d60f-199">Create the following stored procedure.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `IF OBJECT_ID ( ' dbo.ContactEmailAddress, 'P' ) IS NOT NULL`  
  
 `DROP PROCEDURE dbo.ContactEmailAddress;`  
  
 `GO`  
  
 `CREATE PROCEDURE dbo.ContactEmailAddress`  
  
 `(`  
  
 `@FirstName nvarchar(50)`  
  
 `,@LastName nvarchar(50)`  
  
 `)`  
  
 `AS`  
  
 `SET NOCOUNT ON`  
  
 `SELECT EmailAddress`  
  
 `FROM Person.Person`  
  
 `WHERE FirstName = @FirstName`  
  
 `AND LastName = @LastName;`  
  
 `SET NOCOUNT OFF`  
  
 <span data-ttu-id="5d60f-200">在 `sqlcmd` 提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="5d60f-200">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\sqlcmd`  
  
 `1> :Setvar FirstName Gustavo`  
  
 `1> :Setvar LastName Achong`  
  
 `1> EXEC dbo.ContactEmailAddress $(Gustavo),$(Achong)`  
  
 `2> GO`  
  
 `EmailAddress`  
  
 `-----------------------------`  
  
 `gustavo0@adventure-works.com`  
  
### <a name="d-using-sqlcmd-for-database-maintenance"></a><span data-ttu-id="5d60f-201">D.</span><span class="sxs-lookup"><span data-stu-id="5d60f-201">D.</span></span> <span data-ttu-id="5d60f-202">使用 sqlcmd 进行数据库维护</span><span class="sxs-lookup"><span data-stu-id="5d60f-202">Using sqlcmd for database maintenance</span></span>  
 <span data-ttu-id="5d60f-203">下面的示例说明了如何将 `sqlcmd` 用于数据库维护任务。</span><span class="sxs-lookup"><span data-stu-id="5d60f-203">The following example shows how to use `sqlcmd` for a database maintenance task.</span></span> <span data-ttu-id="5d60f-204">使用以下代码创建 `C:\BackupTemplate.sql` 。</span><span class="sxs-lookup"><span data-stu-id="5d60f-204">Create `C:\BackupTemplate.sql` with the following code.</span></span>  
  
 `USE master;`  
  
 `BACKUP DATABASE [$(db)] TO DISK='$(bakfile)';`  
  
 <span data-ttu-id="5d60f-205">在 `sqlcmd` 提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="5d60f-205">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\ >sqlcmd`  
  
 `1> :connect <server>`  
  
 `Sqlcmd: Successfully connected to server <server>.`  
  
 `1> :setvar db msdb`  
  
 `1> :setvar bakfile c:\msdb.bak`  
  
 `1> :r c:\BackupTemplate.sql`  
  
 `2> GO`  
  
 `Changed database context to 'master'.`  
  
 `Processed 688 pages for database 'msdb', file 'MSDBData' on file 2.`  
  
 `Processed 5 pages for database 'msdb', file 'MSDBLog' on file 2.`  
  
 `BACKUP DATABASE successfully processed 693 pages in 0.725 seconds (7.830 MB/sec)`  
  
### <a name="e-using-sqlcmd-to-execute-code-on-multiple-instances"></a><span data-ttu-id="5d60f-206">E.</span><span class="sxs-lookup"><span data-stu-id="5d60f-206">E.</span></span> <span data-ttu-id="5d60f-207">使用 sqlcmd 对多个实例执行代码</span><span class="sxs-lookup"><span data-stu-id="5d60f-207">Using sqlcmd to execute code on multiple instances</span></span>  
 <span data-ttu-id="5d60f-208">某文件中的以下代码表示一个连接到两个实例的脚本。</span><span class="sxs-lookup"><span data-stu-id="5d60f-208">The following code in a file shows a script that connects to two instances.</span></span> <span data-ttu-id="5d60f-209">请注意连接到第二个实例之前的 `GO` 。</span><span class="sxs-lookup"><span data-stu-id="5d60f-209">Notice the `GO` before the connection to the second instance.</span></span>  
  
 `:CONNECT <server>\,<instance1>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
 `:CONNECT <server>\,<instance2>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
### <a name="e-returning-xml-output"></a><span data-ttu-id="5d60f-210">E.</span><span class="sxs-lookup"><span data-stu-id="5d60f-210">E.</span></span> <span data-ttu-id="5d60f-211">返回 XML 输出</span><span class="sxs-lookup"><span data-stu-id="5d60f-211">Returning XML output</span></span>  
 <span data-ttu-id="5d60f-212">下面的示例说明了如何以连续流返回未格式化的 XML 输出。</span><span class="sxs-lookup"><span data-stu-id="5d60f-212">The following example shows how XML output is returned unformatted, in a continuous stream.</span></span>  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> :XML ON`  
  
 `1> SELECT TOP 3 FirstName + ' ' + LastName + ', '`  
  
 `2> FROM Person.Person`  
  
 `3> GO`  
  
 `Syed Abbas, Catherine Abel, Kim Abercrombie,`  
  
### <a name="f-using-sqlcmd-in-a-windows-script-file"></a><span data-ttu-id="5d60f-213">F.</span><span class="sxs-lookup"><span data-stu-id="5d60f-213">F.</span></span> <span data-ttu-id="5d60f-214">在 Windows 脚本文件中使用 sqlcmd</span><span class="sxs-lookup"><span data-stu-id="5d60f-214">Using sqlcmd in a Windows script file</span></span>  
 <span data-ttu-id="5d60f-215">`sqlcmd`命令（如） `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` 可以与 VBScript 一起在 .bat 文件中执行。</span><span class="sxs-lookup"><span data-stu-id="5d60f-215">A `sqlcmd`command such as `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` can be executed in a .bat file together with VBScript.</span></span> <span data-ttu-id="5d60f-216">此时，不要使用交互选项。</span><span class="sxs-lookup"><span data-stu-id="5d60f-216">In this case, do not use interactive options.</span></span> <span data-ttu-id="5d60f-217">执行 .bat 文件的计算机上必须安装 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="5d60f-217">`sqlcmd` must be installed on the computer that is executing the .bat file.</span></span>  
  
 <span data-ttu-id="5d60f-218">首先，创建以下四个文件：</span><span class="sxs-lookup"><span data-stu-id="5d60f-218">First, create the following four files:</span></span>  
  
-   <span data-ttu-id="5d60f-219">C:\badscript.sql</span><span class="sxs-lookup"><span data-stu-id="5d60f-219">C:\badscript.sql</span></span>  
  
    ```  
    SELECT batch_1_this_is_an_error  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="5d60f-220">C:\goodscript.sql</span><span class="sxs-lookup"><span data-stu-id="5d60f-220">C:\goodscript.sql</span></span>  
  
    ```  
    SELECT 'batch #1'  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="5d60f-221">C:\returnvalue.sql</span><span class="sxs-lookup"><span data-stu-id="5d60f-221">C:\returnvalue.sql</span></span>  
  
    ```  
    :exit(select 100)  
    @echo off  
    C:\windowsscript.bat  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
-   <span data-ttu-id="5d60f-222">C:\windowsscript.bat</span><span class="sxs-lookup"><span data-stu-id="5d60f-222">C:\windowsscript.bat</span></span>  
  
    ```  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
 <span data-ttu-id="5d60f-223">然后，在命令提示符处运行 `C:\windowsscript.bat`：</span><span class="sxs-lookup"><span data-stu-id="5d60f-223">Then, at the command prompt, run `C:\windowsscript.bat`:</span></span>  
  
 `C:\>windowsscript.bat`  
  
 `Running badscript.sql`  
  
 `== An error occurred`  
  
 `Running goodscript.sql`  
  
 `Running returnvalue.sql`  
  
 `SQLCMD returned 100 to the command shell`  
  
### <a name="g-using-sqlcmd-to-set-encryption-on-azure-sql-database"></a><span data-ttu-id="5d60f-224">G.</span><span class="sxs-lookup"><span data-stu-id="5d60f-224">G.</span></span> <span data-ttu-id="5d60f-225">使用 sqlcmd 在 Azure SQL 数据库上设置加密</span><span class="sxs-lookup"><span data-stu-id="5d60f-225">Using sqlcmd to set encryption on Azure SQL Database</span></span>  
 <span data-ttu-id="5d60f-226">`sqlcmd`可以在与上的数据的连接上执行， [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 以指定加密和证书信任。</span><span class="sxs-lookup"><span data-stu-id="5d60f-226">A `sqlcmd`can be executed on a connection to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] data on to specify encryption and certificate trust.</span></span> <span data-ttu-id="5d60f-227">提供两个 "sqlcmd" 选项：</span><span class="sxs-lookup"><span data-stu-id="5d60f-227">Two \`sqlcmd\`\`\`options are available:</span></span>  
  
-   <span data-ttu-id="5d60f-228">-N 开关，客户端使用它来请求加密连接。</span><span class="sxs-lookup"><span data-stu-id="5d60f-228">The -N switch is used by the client to request an encrypted connection.</span></span> <span data-ttu-id="5d60f-229">此选项等同于 ADO.net 选项 `ENCRYPT = true`。</span><span class="sxs-lookup"><span data-stu-id="5d60f-229">This option is equivalent to the ADO.net option `ENCRYPT = true`.</span></span>  
  
-   <span data-ttu-id="5d60f-230">-C 开关，客户端用来将其配置为隐式信任服务器证书且不对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="5d60f-230">The -C switch is used by the client to configure it to implicitly the trust server certificate and not validate it.</span></span> <span data-ttu-id="5d60f-231">此选项等同于 ADO.net 选项 `TRUSTSERVERCERTIFICATE = true`。</span><span class="sxs-lookup"><span data-stu-id="5d60f-231">This option is equivalent to the ADO.net option `TRUSTSERVERCERTIFICATE = true`.</span></span>  
  
 <span data-ttu-id="5d60f-232">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 服务并不支持 SQL Server 实例上所有可用的 `SET` 选项。</span><span class="sxs-lookup"><span data-stu-id="5d60f-232">The [!INCLUDE[ssSDS](../../includes/sssds-md.md)] service does not support all the `SET` options available on a SQL Server instance.</span></span> <span data-ttu-id="5d60f-233">当将相应的 `SET` 选项设置为 `ON` 或 `OFF`时，下面的选项将引发错误：</span><span class="sxs-lookup"><span data-stu-id="5d60f-233">The following options throw an error when the corresponding `SET` option is set to `ON` or `OFF`:</span></span>  
  
-   <span data-ttu-id="5d60f-234">SET ANSI_DEFAULTS</span><span class="sxs-lookup"><span data-stu-id="5d60f-234">SET ANSI_DEFAULTS</span></span>  
  
-   <span data-ttu-id="5d60f-235">SET ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="5d60f-235">SET ANSI_NULLS</span></span>  
  
-   <span data-ttu-id="5d60f-236">SET REMOTE_PROC_TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="5d60f-236">SET REMOTE_PROC_TRANSACTIONS</span></span>  
  
-   <span data-ttu-id="5d60f-237">SET ANSI_NULL_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5d60f-237">SET ANSI_NULL_DEFAULT</span></span>  
  
 <span data-ttu-id="5d60f-238">下面的 SET 选项虽然不会引发异常，但无法使用。</span><span class="sxs-lookup"><span data-stu-id="5d60f-238">The following SET options do not throw exceptions but cannot be used.</span></span> <span data-ttu-id="5d60f-239">不推荐使用这些选项：</span><span class="sxs-lookup"><span data-stu-id="5d60f-239">They are deprecated:</span></span>  
  
-   <span data-ttu-id="5d60f-240">SET CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="5d60f-240">SET CONCAT_NULL_YIELDS_NULL</span></span>  
  
-   <span data-ttu-id="5d60f-241">SET ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="5d60f-241">SET ANSI_PADDING</span></span>  
  
-   <span data-ttu-id="5d60f-242">SET QUERY_GOVERNOR_COST_LIMIT</span><span class="sxs-lookup"><span data-stu-id="5d60f-242">SET QUERY_GOVERNOR_COST_LIMIT</span></span>  
  
#### <a name="syntax"></a><span data-ttu-id="5d60f-243">语法</span><span class="sxs-lookup"><span data-stu-id="5d60f-243">Syntax</span></span>  
 <span data-ttu-id="5d60f-244">以下示例介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 访问接口设置包括的情况： `ForceProtocolEncryption = False`、 `Trust Server Certificate = No`</span><span class="sxs-lookup"><span data-stu-id="5d60f-244">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = False`, `Trust Server Certificate = No`</span></span>  
  
 <span data-ttu-id="5d60f-245">使用 Windows 凭据进行连接并对通信加密：</span><span class="sxs-lookup"><span data-stu-id="5d60f-245">Connect using Windows credentials and encrypt communication:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="5d60f-246">使用 Windows 凭据进行连接并信任服务器证书：</span><span class="sxs-lookup"><span data-stu-id="5d60f-246">Connect using Windows credentials and trust server certificate:</span></span>  
  
```  
SQLCMD -E -C  
  
```  
  
 <span data-ttu-id="5d60f-247">使用 Windows 凭据进行连接、对通信加密并信任服务器证书：</span><span class="sxs-lookup"><span data-stu-id="5d60f-247">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="5d60f-248">以下示例介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 访问接口设置包括的情况： `ForceProtocolEncryption = True`、 `TrustServerCertificate = Yes`。</span><span class="sxs-lookup"><span data-stu-id="5d60f-248">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = True`, `TrustServerCertificate = Yes`.</span></span>  
  
 <span data-ttu-id="5d60f-249">使用 Windows 凭据进行连接、对通信加密并信任服务器证书：</span><span class="sxs-lookup"><span data-stu-id="5d60f-249">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E  
  
```  
  
 <span data-ttu-id="5d60f-250">使用 Windows 凭据进行连接、对通信加密并信任服务器证书：</span><span class="sxs-lookup"><span data-stu-id="5d60f-250">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="5d60f-251">使用 Windows 凭据进行连接、对通信加密并信任服务器证书：</span><span class="sxs-lookup"><span data-stu-id="5d60f-251">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -T  
  
```  
  
 <span data-ttu-id="5d60f-252">使用 Windows 凭据进行连接、对通信加密并信任服务器证书：</span><span class="sxs-lookup"><span data-stu-id="5d60f-252">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="5d60f-253">如果访问接口指定了 `ForceProtocolEncryption = True` ，则启用加密，即使连接字符串中具有 `Encrypt=No` 。</span><span class="sxs-lookup"><span data-stu-id="5d60f-253">If the provider specifies `ForceProtocolEncryption = True` then encryption is enabled even if `Encrypt=No` in the connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d60f-254">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d60f-254">See Also</span></span>  
 <span data-ttu-id="5d60f-255">[sqlcmd 实用工具](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="5d60f-255">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="5d60f-256">[将 sqlcmd 与脚本变量结合使用](sqlcmd-use-with-scripting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="5d60f-256">[Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md) </span></span>  
 <span data-ttu-id="5d60f-257">[使用查询编辑器编辑 SQLCMD 脚本](edit-sqlcmd-scripts-with-query-editor.md) </span><span class="sxs-lookup"><span data-stu-id="5d60f-257">[Edit SQLCMD Scripts with Query Editor](edit-sqlcmd-scripts-with-query-editor.md) </span></span>  
 <span data-ttu-id="5d60f-258">[管理作业步骤](../../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="5d60f-258">[Manage Job Steps](../../ssms/agent/manage-job-steps.md) </span></span>  
 [<span data-ttu-id="5d60f-259">创建 CmdExec 作业步骤</span><span class="sxs-lookup"><span data-stu-id="5d60f-259">Create a CmdExec Job Step</span></span>](../../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
