---
title: “错误列表”窗口
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- error list window
- SQL Server Management Studio [SQL Server], error list window
ms.assetid: fae6327d-e268-44ae-a474-4a8f8f843129
author: rothja
ms.author: jroth
ms.openlocfilehash: 00455c339344b7b38a48500c49d139aa52df6116
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590704"
---
# <a name="error-list-window-management-studio"></a><span data-ttu-id="954f7-102">“错误列表”窗口 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="954f7-102">Error List Window (Management Studio)</span></span>
  <span data-ttu-id="954f7-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]“错误列表”  用于显示由 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中的 IntelliSense 代码生成的语法和语义错误。</span><span class="sxs-lookup"><span data-stu-id="954f7-103">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Error List** displays the syntax and semantic errors that are generated from the IntelliSense code in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="features-of-the-error-list"></a><span data-ttu-id="954f7-104">“错误列表”的功能</span><span class="sxs-lookup"><span data-stu-id="954f7-104">Features of the Error List</span></span>  
 <span data-ttu-id="954f7-105">**“错误列表”** 提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="954f7-105">The **Error List** provides the following functionality:</span></span>  
  
-   <span data-ttu-id="954f7-106">编辑脚本时， **“错误列表”** 可显示由 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中的 IntelliSense 生成的错误和警告。</span><span class="sxs-lookup"><span data-stu-id="954f7-106">As you edit scripts, the **Error List** displays the errors and warnings produced by IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
-   <span data-ttu-id="954f7-107">可以通过双击任意错误消息项来着重查看生成此错误的脚本文件的选项卡，并移至出错的位置。</span><span class="sxs-lookup"><span data-stu-id="954f7-107">You can double-click any error message entry to focus on the tab for the script file that generated the error, and move to the error location.</span></span>  
  
-   <span data-ttu-id="954f7-108">可以筛选要显示哪些项以及为每一项显示哪些列的信息。</span><span class="sxs-lookup"><span data-stu-id="954f7-108">You can filter which entries you want to display, and which columns of information you want appear for each entry.</span></span>  
  
-   <span data-ttu-id="954f7-109">修复某错误后，相应错误项将从 **“错误列表”** 中删除。</span><span class="sxs-lookup"><span data-stu-id="954f7-109">After you fix an error, the error entry is removed from the **Error List**.</span></span>  
  
-   <span data-ttu-id="954f7-110">关闭某个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件的选项卡后，与该文件相关的错误将从 **“错误列表”** 中删除。</span><span class="sxs-lookup"><span data-stu-id="954f7-110">When you close the tab for a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file, the errors for that file are removed from the **Error List**.</span></span>  
  
## <a name="working-with-the-error-list"></a><span data-ttu-id="954f7-111">使用“错误列表”</span><span class="sxs-lookup"><span data-stu-id="954f7-111">Working with the Error List</span></span>  
 <span data-ttu-id="954f7-112">若要显示 **“错误列表”** ，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="954f7-112">To display the **Error List**, do one of the following:</span></span>  
  
-   <span data-ttu-id="954f7-113">在 **“视图”** 菜单上单击 **“错误列表”** 。</span><span class="sxs-lookup"><span data-stu-id="954f7-113">On the **View** menu, click **Error List**.</span></span>  
  
-   <span data-ttu-id="954f7-114">使用键盘快捷键 CTRL+\\和 CTRL+E。</span><span class="sxs-lookup"><span data-stu-id="954f7-114">Enter the keyboard shortcut CTRL+\\, CTRL+E.</span></span>  
  
 <span data-ttu-id="954f7-115">打开 **“错误列表”** 后，可以通过执行以下操作自定义视图：</span><span class="sxs-lookup"><span data-stu-id="954f7-115">After you open the **Error List**, you can customize your view by performing the following actions:</span></span>  
  
-   <span data-ttu-id="954f7-116">若要对列表进行排序，请单击任一列标题。</span><span class="sxs-lookup"><span data-stu-id="954f7-116">To sort the list, click any column header.</span></span> <span data-ttu-id="954f7-117">若要按其他列对列表进行进一步排序，请按住 Shift 键然后单击其他列标题。</span><span class="sxs-lookup"><span data-stu-id="954f7-117">To sort again by an additional column, press and hold the SHIFT key, and then click another column header.</span></span>  
  
-   <span data-ttu-id="954f7-118">若要选择显示的列和隐藏的列，请从快捷菜单中选择 **“显示列”** 。</span><span class="sxs-lookup"><span data-stu-id="954f7-118">To select which columns are displayed and which are hidden, select **Show Columns** from the shortcut menu.</span></span>  
  
-   <span data-ttu-id="954f7-119">若要更改列显示的顺序，请将任一列标题向左或向右拖动。</span><span class="sxs-lookup"><span data-stu-id="954f7-119">To change the order in which columns are displayed, drag any column header to the left or right.</span></span>  
  
 <span data-ttu-id="954f7-120">**“错误列表”** 中不包含指向有关特定错误的附加信息的链接。</span><span class="sxs-lookup"><span data-stu-id="954f7-120">The **Error List** does not link to additional information about specific errors.</span></span>  
  
## <a name="transact-sql-errors-in-management-studio"></a><span data-ttu-id="954f7-121">Management Studio 中的 Transact-SQL 错误</span><span class="sxs-lookup"><span data-stu-id="954f7-121">Transact-SQL Errors in Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="954f7-122">在以下位置显示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本的错误：</span><span class="sxs-lookup"><span data-stu-id="954f7-122">displays errors for [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts in the following locations:</span></span>  
  
-   <span data-ttu-id="954f7-123">**“错误列表”** 包含 IntelliSense 在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 编辑器中找到的所有语法和语义错误。</span><span class="sxs-lookup"><span data-stu-id="954f7-123">The **Error List** contains all syntax and semantic errors found by IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Editor.</span></span> <span data-ttu-id="954f7-124">当您编辑 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本时，此错误列表将动态更新。</span><span class="sxs-lookup"><span data-stu-id="954f7-124">This list of errors is dynamically updated as you edit [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="954f7-125">此列表包括编辑器在每个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本中找到的所有错误。</span><span class="sxs-lookup"><span data-stu-id="954f7-125">The list includes all errors that the editor has found in each [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="954f7-126">在脚本中遇到错误后，编辑器并不会停止分析文件。</span><span class="sxs-lookup"><span data-stu-id="954f7-126">The editor does not stop parsing a file after encountering errors in a script.</span></span> <span data-ttu-id="954f7-127">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]中， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 编辑器中的 IntelliSense 不支持所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法元素。</span><span class="sxs-lookup"><span data-stu-id="954f7-127">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Editor does not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax elements.</span></span> <span data-ttu-id="954f7-128">**“错误列表”** 仅包含 IntelliSense 支持的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法所产生的错误。</span><span class="sxs-lookup"><span data-stu-id="954f7-128">The **Error List** contains only errors from the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that is supported by IntelliSense.</span></span>  
  
-   <span data-ttu-id="954f7-129">**查询编辑器底部的** “消息” [!INCLUDE[ssDE](../../includes/ssde-md.md)] 选项卡显示执行 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 脚本时 [!INCLUDE[tsql](../../includes/tsql-md.md)] 返回的所有错误和警告。</span><span class="sxs-lookup"><span data-stu-id="954f7-129">The **Messages** tab at the bottom of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window displays all errors and messages that are returned by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] when a [!INCLUDE[tsql](../../includes/tsql-md.md)] script is executed.</span></span> <span data-ttu-id="954f7-130">只有再次执行该脚本此列表才会发生变化。</span><span class="sxs-lookup"><span data-stu-id="954f7-130">This list does not change until you execute the script again.</span></span> <span data-ttu-id="954f7-131">当 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 找到一个或两个编译错误后，它将停止分析批处理；因此， **“消息”** 选项卡中可能不会列出脚本中的所有错误。</span><span class="sxs-lookup"><span data-stu-id="954f7-131">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] stops parsing a batch after it finds one or two compile errors; therefore, the **Messages** tab might not list all errors in a script.</span></span>  
  
 <span data-ttu-id="954f7-132">有时候错误会同时在上述两个位置列出。</span><span class="sxs-lookup"><span data-stu-id="954f7-132">Sometimes errors are listed in both locations.</span></span> <span data-ttu-id="954f7-133">例如，某脚本文件可能存在已在 **“错误列表”** 中列出的语法错误。</span><span class="sxs-lookup"><span data-stu-id="954f7-133">For example, a script file might have a syntax error that is listed in the **Error List**.</span></span> <span data-ttu-id="954f7-134">如果在纠正此错误之前执行了该脚本，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 分析器会检测到相同的错误情形并在 **“消息”** 选项卡中返回此错误消息。</span><span class="sxs-lookup"><span data-stu-id="954f7-134">If you execute the script before you correct the error, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] parser can detect the same condition and return another copy of the error message in the **Messages** tab.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="954f7-135">“错误列表”  仅显示来源于 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器的错误，而不显示来源于 MDX、DMX 或 XML/A 编辑器的错误。</span><span class="sxs-lookup"><span data-stu-id="954f7-135">The **Error List** only displays errors from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor; it does not display errors from the MDX, DMX, or XML/A Editors.</span></span> <span data-ttu-id="954f7-136">所有 MDX、DMX 和 XML/A 错误均显示在这些编辑器的“消息”  选项卡中。</span><span class="sxs-lookup"><span data-stu-id="954f7-136">All MDX, DMX, and XML/A errors are displayed in the **Messages** tab in those editors.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="954f7-137">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="954f7-137">UI element list</span></span>  
 <span data-ttu-id="954f7-138">**“错误列表”** 后，将在以下列中显示相关信息：</span><span class="sxs-lookup"><span data-stu-id="954f7-138">When the **Error List** is open, the information is displayed in the following columns:</span></span>  
  
 <span data-ttu-id="954f7-139">**默认顺序**</span><span class="sxs-lookup"><span data-stu-id="954f7-139">**Default Order**</span></span>  
 <span data-ttu-id="954f7-140">显示一个整数，该整数指示相应项的生成次序。</span><span class="sxs-lookup"><span data-stu-id="954f7-140">Displays an integer that indicates the order in which an entry was generated.</span></span>  
  
 <span data-ttu-id="954f7-141">**说明**</span><span class="sxs-lookup"><span data-stu-id="954f7-141">**Description**</span></span>  
 <span data-ttu-id="954f7-142">显示相应错误项的文本。</span><span class="sxs-lookup"><span data-stu-id="954f7-142">Displays the text of the error entry.</span></span> <span data-ttu-id="954f7-143">较长的说明会自动换行。</span><span class="sxs-lookup"><span data-stu-id="954f7-143">Lengthy descriptions wrap onto additional lines.</span></span>  
  
 <span data-ttu-id="954f7-144">**File**</span><span class="sxs-lookup"><span data-stu-id="954f7-144">**File**</span></span>  
 <span data-ttu-id="954f7-145">显示生成相应错误的脚本文件的名称。</span><span class="sxs-lookup"><span data-stu-id="954f7-145">Displays the name of the script file that generated the error.</span></span>  
  
 <span data-ttu-id="954f7-146">**线条**</span><span class="sxs-lookup"><span data-stu-id="954f7-146">**Line**</span></span>  
 <span data-ttu-id="954f7-147">显示一个整数，该整数指示包含相应错误的代码行。</span><span class="sxs-lookup"><span data-stu-id="954f7-147">Displays an integer that indicates which line of the code includes the error.</span></span>  
  
 <span data-ttu-id="954f7-148">**列**</span><span class="sxs-lookup"><span data-stu-id="954f7-148">**Column**</span></span>  
 <span data-ttu-id="954f7-149">显示一个整数，该整数指示错误在相应代码行中的位置。</span><span class="sxs-lookup"><span data-stu-id="954f7-149">Displays an integer that indicates the position of the error in the line of code.</span></span>  
  
 <span data-ttu-id="954f7-150">**项目**</span><span class="sxs-lookup"><span data-stu-id="954f7-150">**Project**</span></span>  
 <span data-ttu-id="954f7-151">显示包含相应脚本文件的项目的名称。</span><span class="sxs-lookup"><span data-stu-id="954f7-151">Displays the name of the project that includes the script file.</span></span>  
