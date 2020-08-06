---
title: 选项 (文本编辑器-Transact-sql-常规页面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.General
dev_langs:
- TSQL
ms.assetid: 7021ecb7-8fb5-4d8c-b984-3d34fcde8be2
author: rothja
ms.author: jroth
ms.openlocfilehash: f008d0d84a15cfbf0bfa988232015e6619f4f5c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588695"
---
# <a name="options-text-editor---transact-sql--general-page"></a><span data-ttu-id="945e8-102">选项 (文本编辑器-Transact-sql-常规页面) </span><span class="sxs-lookup"><span data-stu-id="945e8-102">Options (Text Editor - Transact-SQL- General Page)</span></span>
  <span data-ttu-id="945e8-103">使用 **“常规”** 选项对话框可以更改用于编辑 [!INCLUDE[ssDE](../includes/ssde-md.md)] 脚本的 [!INCLUDE[tsql](../includes/tsql-md.md)] 查询编辑器的常规编辑行为。</span><span class="sxs-lookup"><span data-stu-id="945e8-103">Use the **General** options dialog box to change the general editing behavior of the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor, which is used to edit [!INCLUDE[tsql](../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="945e8-104">若要显示这些设置，请在“工具”\*\*\*\* 菜单上单击“选项”\*\*\*\*，展开 **Transact-SQL** 子文件夹，再单击“常规”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="945e8-104">To display these settings, click **Options** on the **Tools** menu, expand the **Transact-SQL** subfolder, and then click **General**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="945e8-105">在多个位置设置选项</span><span class="sxs-lookup"><span data-stu-id="945e8-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="945e8-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] 查询编辑器的选项也可在 **“所有语言”** 和“常规”对话框中设置。</span><span class="sxs-lookup"><span data-stu-id="945e8-106">Options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="945e8-107">如果使用 **“所有语言”** 对话框来设置其他 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 编辑器（例如 DMX 或 MDX 编辑器）的其他选项，则必须使用此对话框重置 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查询编辑器选项。</span><span class="sxs-lookup"><span data-stu-id="945e8-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor options using this dialog.</span></span>  
  
## <a name="statement-completion"></a><span data-ttu-id="945e8-108">语句结束</span><span class="sxs-lookup"><span data-stu-id="945e8-108">Statement Completion</span></span>  
 <span data-ttu-id="945e8-109">**自动列出成员**</span><span class="sxs-lookup"><span data-stu-id="945e8-109">**Auto list members**</span></span>  
 <span data-ttu-id="945e8-110">选中此复选框后，在编辑器中键入时会显示可用数据库和架构对象、列、表值函数或函数的列表。</span><span class="sxs-lookup"><span data-stu-id="945e8-110">When this check box is selected, lists of available database and schema objects, columns, table-valued functions, or functions are displayed as you type in the editor.</span></span> <span data-ttu-id="945e8-111">从弹出列表中任选一项，即可将其插入到代码中。</span><span class="sxs-lookup"><span data-stu-id="945e8-111">Choose any item from the pop-up list to insert it into your code.</span></span>  
  
 <span data-ttu-id="945e8-112">**隐藏高级成员**</span><span class="sxs-lookup"><span data-stu-id="945e8-112">**Hide advanced members**</span></span>  
 <span data-ttu-id="945e8-113">此复选框不可用。</span><span class="sxs-lookup"><span data-stu-id="945e8-113">This check box is unavailable.</span></span>  
  
 <span data-ttu-id="945e8-114">**参数信息**</span><span class="sxs-lookup"><span data-stu-id="945e8-114">**Parameter information**</span></span>  
 <span data-ttu-id="945e8-115">在该复选框处于选中状态时，将显示紧挨在插入点（光标）左侧的存储过程或函数的参数信息。</span><span class="sxs-lookup"><span data-stu-id="945e8-115">When this check box is selected, parameter information is displayed for a stored procedure or function that is immediately to the left of the insertion point (cursor).</span></span> <span data-ttu-id="945e8-116">这些信息包括可用参数及其名称和数据类型的列表。</span><span class="sxs-lookup"><span data-stu-id="945e8-116">The information includes a list of the available parameters with their names and data types.</span></span>  
  
## <a name="settings"></a><span data-ttu-id="945e8-117">设置</span><span class="sxs-lookup"><span data-stu-id="945e8-117">Settings</span></span>  
 <span data-ttu-id="945e8-118">**启用虚拟空间**</span><span class="sxs-lookup"><span data-stu-id="945e8-118">**Enable virtual space**</span></span>  
 <span data-ttu-id="945e8-119">选中此复选框后，您可以单击代码行结束处后面的任意位置，然后键入。</span><span class="sxs-lookup"><span data-stu-id="945e8-119">When this check box is selected, you can click anywhere beyond the end of a line of code and type.</span></span> <span data-ttu-id="945e8-120">如果选中此复选框，可将注释始终定位在代码旁的同一位置。</span><span class="sxs-lookup"><span data-stu-id="945e8-120">Select this check box to position comments at a consistent point next to your code.</span></span> <span data-ttu-id="945e8-121">选中此复选框将禁用 **“自动换行”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="945e8-121">Selecting this check box disables the **Word wrap** check box.</span></span>  
  
 <span data-ttu-id="945e8-122">**自动换行**</span><span class="sxs-lookup"><span data-stu-id="945e8-122">**Word wrap**</span></span>  
 <span data-ttu-id="945e8-123">如果选中此复选框，则水平延伸到编辑器可见区域以外的行的其他部分都将自动显示在下一行。</span><span class="sxs-lookup"><span data-stu-id="945e8-123">When this check box is selected, any portion of a line that extends horizontally beyond the viewable editor area is automatically displayed on the next line.</span></span> <span data-ttu-id="945e8-124">选中此复选框将启用 **“显示可视的自动换行标志符号”** 复选框，并禁用 **“启用虚空格”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="945e8-124">Selecting this check box enables the **Show visual glyphs for word wrap** check box and disables the **Enable virtual space** check box.</span></span>  
  
 <span data-ttu-id="945e8-125">**显示可视的自动换行标志符号**</span><span class="sxs-lookup"><span data-stu-id="945e8-125">**Show visual glyphs for word wrap**</span></span>  
 <span data-ttu-id="945e8-126">如果选中此复选框，则在长行换行的位置显示返回箭头指示符。</span><span class="sxs-lookup"><span data-stu-id="945e8-126">When this check box is selected, a return arrow indicator is displayed where a long line wraps to the next line.</span></span>  
  
 <span data-ttu-id="945e8-127">**没有选定内容时对空行应用剪切或复制命令**</span><span class="sxs-lookup"><span data-stu-id="945e8-127">**Apply Cut/Copy commands to blank lines when there is no selection**</span></span>  
 <span data-ttu-id="945e8-128">此复选框用于设置将插入点放在空白行上，不选择任何内容，再单击 **“复制”** 或 **“剪切”** 时的编辑器行为。</span><span class="sxs-lookup"><span data-stu-id="945e8-128">This check box sets the behavior of the editor when you place the insertion point on a blank line, select nothing, and then click **Copy** or **Cut**.</span></span>  
  
 <span data-ttu-id="945e8-129">如果选中此复选框，将复制或剪切空白行。</span><span class="sxs-lookup"><span data-stu-id="945e8-129">When this check box is selected, the blank line is copied or cut.</span></span> <span data-ttu-id="945e8-130">如果随后单击 **“粘贴”**，将插入一个新空白行。</span><span class="sxs-lookup"><span data-stu-id="945e8-130">If you then click **Paste**, a new, blank line is inserted.</span></span>  
  
 <span data-ttu-id="945e8-131">如果此复选框处于未选中状态，则不复制或剪切任何内容。</span><span class="sxs-lookup"><span data-stu-id="945e8-131">When this check box is cleared, nothing is copied or cut.</span></span> <span data-ttu-id="945e8-132">如果随后单击 **“粘贴”**，将粘贴最近一次复制的内容。</span><span class="sxs-lookup"><span data-stu-id="945e8-132">If you then click **Paste**, the content most recently copied is pasted.</span></span> <span data-ttu-id="945e8-133">如果以前尚未复制任何内容，则不会粘贴任何内容。</span><span class="sxs-lookup"><span data-stu-id="945e8-133">If nothing has been copied previously, nothing is pasted.</span></span>  
  
 <span data-ttu-id="945e8-134">如果不是空白行，则此设置对 **“复制”** 或 **“剪切”** 无效。</span><span class="sxs-lookup"><span data-stu-id="945e8-134">This setting has no effect on **Copy** or **Cut** when a line is not blank.</span></span> <span data-ttu-id="945e8-135">如果没有选定任何内容，将复制或剪切整个行。</span><span class="sxs-lookup"><span data-stu-id="945e8-135">If nothing is selected, the entire line is copied or cut.</span></span> <span data-ttu-id="945e8-136">如果随后单击 **“粘贴”**，将粘贴整个行的文本及其行终止符。</span><span class="sxs-lookup"><span data-stu-id="945e8-136">If you then click **Paste**, the text of the entire line and its end line character are pasted.</span></span>  
  
## <a name="display"></a><span data-ttu-id="945e8-137">显示</span><span class="sxs-lookup"><span data-stu-id="945e8-137">Display</span></span>  
 <span data-ttu-id="945e8-138">**行号**</span><span class="sxs-lookup"><span data-stu-id="945e8-138">**Line numbers**</span></span>  
 <span data-ttu-id="945e8-139">如果选中此复选框，则将在每个代码行的旁边显示行号。</span><span class="sxs-lookup"><span data-stu-id="945e8-139">When this check box is selected, a line number appears next to each line of code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="945e8-140">这些行号不会添加到代码中，也不会打印出来。</span><span class="sxs-lookup"><span data-stu-id="945e8-140">These line numbers are not added to your code, and they do not print.</span></span> <span data-ttu-id="945e8-141">它们仅供参考。</span><span class="sxs-lookup"><span data-stu-id="945e8-141">They are for reference only.</span></span>  
  
 <span data-ttu-id="945e8-142">**启用单击 URL 定位**</span><span class="sxs-lookup"><span data-stu-id="945e8-142">**Enable single-click URL navigation**</span></span>  
 <span data-ttu-id="945e8-143">选中此复选框后，当光标在编辑器中的 URL 上方经过时，光标会变为手形指针。</span><span class="sxs-lookup"><span data-stu-id="945e8-143">When this check box is selected, the cursor changes to a pointing hand as it passes over a URL in the editor.</span></span> <span data-ttu-id="945e8-144">您可以单击 URL 以在 Web 浏览器中显示所指示的页。</span><span class="sxs-lookup"><span data-stu-id="945e8-144">You can click the URL to display the indicated page in your Web browser.</span></span>  
  
 <span data-ttu-id="945e8-145">**导航栏**</span><span class="sxs-lookup"><span data-stu-id="945e8-145">**Navigation bar**</span></span>  
 <span data-ttu-id="945e8-146">此复选框不可用。</span><span class="sxs-lookup"><span data-stu-id="945e8-146">This check box is unavailable.</span></span>  
  
  
