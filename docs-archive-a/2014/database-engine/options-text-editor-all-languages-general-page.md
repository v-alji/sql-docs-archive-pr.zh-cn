---
title: 选项 (文本编辑器-所有语言-常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bf18907c-94e2-4c09-9b2b-0925ac04c627
author: rothja
ms.author: jroth
ms.openlocfilehash: 9510ff7c8d28a084ac250c937ec01458b612ac60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589871"
---
# <a name="options-text-editor---all-languages---general-page"></a><span data-ttu-id="b47b5-102">选项（“文本编辑器”-“所有语言”-“常规”页）</span><span class="sxs-lookup"><span data-stu-id="b47b5-102">Options (Text Editor - All Languages - General Page)</span></span>
  <span data-ttu-id="b47b5-103">使用此对话框可以设置 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的所有五个编辑器的常规编辑选项。</span><span class="sxs-lookup"><span data-stu-id="b47b5-103">Use this dialog box to set general editing options in all five of the editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="b47b5-104">若要显示这些选项，请在 **“工具”** 菜单上单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="b47b5-104">To display these options, click **Options** on the **Tools** menu.</span></span> <span data-ttu-id="b47b5-105">选择 **“文本编辑器”** 文件夹，展开 **“所有语言”** 文件夹，再单击 **“常规”**。</span><span class="sxs-lookup"><span data-stu-id="b47b5-105">Select the **Text Editor** folder, expand the **All Languages** folder and then click **General**.</span></span>  
  
## <a name="option-settings-by-editor"></a><span data-ttu-id="b47b5-106">通过编辑器进行的选项设置</span><span class="sxs-lookup"><span data-stu-id="b47b5-106">Option Settings by Editor</span></span>  
 <span data-ttu-id="b47b5-107">您必须使用 **“所有语言”** 对话框来设置 DMX、MDX 和 SQL Server Compact 编辑器的选项。</span><span class="sxs-lookup"><span data-stu-id="b47b5-107">You must use the **All Languages** dialogs to set options for the DMX, MDX, and SQL Server Compact editors.</span></span> <span data-ttu-id="b47b5-108">此处设置的选项也适用于纯文本、Transact-SQL 和 XML 编辑器，但您可以通过展开这些语言的子文件夹并选择相应的选项页面来为这些编辑器单独设置选项。</span><span class="sxs-lookup"><span data-stu-id="b47b5-108">Options set here are also applied to the Plain Text, Transact-SQL, and XML editors, but you can set options separately for those editors by expanding the subfolders for those languages and selecting their option pages.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b47b5-109">如果你使用此对话框设置了选项，但希望在纯文本、Transact-SQL 或 XML 编辑器中使用不同设置，则必须在“所有语言”\*\*\*\* 对话框中应用选项之后为这些编辑器设置选项。</span><span class="sxs-lookup"><span data-stu-id="b47b5-109">If you set an option using this dialog, but want a different setting for the Plain Text, Transact-SQL, or XML editors, you must set the options for those editors after applying your selections in the **All Languages** dialog.</span></span>  
  
 <span data-ttu-id="b47b5-110">某些编辑器只能支持本页面上列出的部分选项。</span><span class="sxs-lookup"><span data-stu-id="b47b5-110">Some editors may not support all of the options listed on this page.</span></span> <span data-ttu-id="b47b5-111">如果已经在 **“选项”** 对话框的 **“常规”** 页上为某些编程语言选择了某个选项，而没有为其他语言选择该选项，则会显示带阴影的选中标记。</span><span class="sxs-lookup"><span data-stu-id="b47b5-111">A shaded check mark is displayed when an option has been selected on the **General** page of the **Options** dialog box for some programming languages, but not for others.</span></span>  
  
## <a name="statement-completion"></a><span data-ttu-id="b47b5-112">语句结束</span><span class="sxs-lookup"><span data-stu-id="b47b5-112">Statement Completion</span></span>  
 <span data-ttu-id="b47b5-113">**自动列出成员**</span><span class="sxs-lookup"><span data-stu-id="b47b5-113">**Auto list members**</span></span>  
 <span data-ttu-id="b47b5-114">当您在编辑器中键入内容时，将显示可用的成员、属性或值的弹出列表。</span><span class="sxs-lookup"><span data-stu-id="b47b5-114">Display pop-up lists of available members, properties, or values as you type in the editor.</span></span> <span data-ttu-id="b47b5-115">从弹出列表中任选一项，即可将其插入到代码中。</span><span class="sxs-lookup"><span data-stu-id="b47b5-115">Choose any item from the pop-up list to insert the item into your code.</span></span> <span data-ttu-id="b47b5-116">选中此复选框将启用 **“隐藏高级成员”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b47b5-116">Selecting this check box enables the **Hide advanced members** option.</span></span>  
  
 <span data-ttu-id="b47b5-117">**隐藏高级成员**</span><span class="sxs-lookup"><span data-stu-id="b47b5-117">**Hide advanced members**</span></span>  
 <span data-ttu-id="b47b5-118">通过仅显示那些最常用的项来缩短弹出语句结束列表。</span><span class="sxs-lookup"><span data-stu-id="b47b5-118">Shorten pop-up statement completion lists by displaying only those items most commonly used.</span></span> <span data-ttu-id="b47b5-119">其他项将从该列表中筛选出去。</span><span class="sxs-lookup"><span data-stu-id="b47b5-119">Other items are filtered from the list.</span></span> <span data-ttu-id="b47b5-120">如果没有成员标记为高级成员，此选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="b47b5-120">This option will not be available if no members are marked as advanced members.</span></span>  
  
 <span data-ttu-id="b47b5-121">**参数信息**</span><span class="sxs-lookup"><span data-stu-id="b47b5-121">**Parameter information**</span></span>  
 <span data-ttu-id="b47b5-122">在编辑器中，当前声明或过程的完整语法会显示在插入点的左侧，并显示其所有可用参数。</span><span class="sxs-lookup"><span data-stu-id="b47b5-122">Display the complete syntax for the current declaration or procedure to the left of the insertion point in the editor with all of its available parameters.</span></span> <span data-ttu-id="b47b5-123">下一个可分配参数以粗体显示。</span><span class="sxs-lookup"><span data-stu-id="b47b5-123">The next parameter you can assign is displayed in bold.</span></span>  
  
## <a name="settings"></a><span data-ttu-id="b47b5-124">设置</span><span class="sxs-lookup"><span data-stu-id="b47b5-124">Settings</span></span>  
 <span data-ttu-id="b47b5-125">**启用虚拟空间**</span><span class="sxs-lookup"><span data-stu-id="b47b5-125">**Enable virtual space**</span></span>  
 <span data-ttu-id="b47b5-126">注释在代码旁的位置将保持不变。</span><span class="sxs-lookup"><span data-stu-id="b47b5-126">Position comments at a consistent point next to your code.</span></span> <span data-ttu-id="b47b5-127">选中此复选框之后，可以将光标放置在行中的最后一个字符之外。</span><span class="sxs-lookup"><span data-stu-id="b47b5-127">When this check box is selected, you can position the cursor beyond the last character in the row.</span></span> <span data-ttu-id="b47b5-128">键入内容时，将自动添加制表符和空格以结束到插入点的行。</span><span class="sxs-lookup"><span data-stu-id="b47b5-128">When you type, tabs or spaces are automatically added to complete the row to the insertion point.</span></span>  
  
 <span data-ttu-id="b47b5-129">**自动换行**</span><span class="sxs-lookup"><span data-stu-id="b47b5-129">**Word wrap**</span></span>  
 <span data-ttu-id="b47b5-130">在下一行中显示将行水平延伸到编辑器可见区域之外的所有部分。</span><span class="sxs-lookup"><span data-stu-id="b47b5-130">Display on the next line any portion of a line that extends horizontally beyond the viewable editor area.</span></span> <span data-ttu-id="b47b5-131">选中此复选框将启用 **“显示可视的自动换行标志符号”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b47b5-131">Selecting this check box enables the **Show visual glyphs for word wrap** option.</span></span>  
  
 <span data-ttu-id="b47b5-132">**显示可视的自动换行标志符号**</span><span class="sxs-lookup"><span data-stu-id="b47b5-132">**Show visual glyphs for word wrap**</span></span>  
 <span data-ttu-id="b47b5-133">在长行换行的位置显示返回箭头指示符。</span><span class="sxs-lookup"><span data-stu-id="b47b5-133">Display a return-arrow indicator where a long line wraps onto a second line.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b47b5-134">这些提示箭头不会添加到代码中，也不会打印出来。</span><span class="sxs-lookup"><span data-stu-id="b47b5-134">These reminder arrows are not added to your code, and they do not print.</span></span> <span data-ttu-id="b47b5-135">它们仅供参考。</span><span class="sxs-lookup"><span data-stu-id="b47b5-135">They are for reference only.</span></span> <span data-ttu-id="b47b5-136">有些类型的编辑器中未提供此功能。</span><span class="sxs-lookup"><span data-stu-id="b47b5-136">This feature is not available in all types of editors.</span></span>  
  
 <span data-ttu-id="b47b5-137">**没有选定内容时对空行应用剪切或复制命令**</span><span class="sxs-lookup"><span data-stu-id="b47b5-137">**Apply Cut/Copy commands to blank lines when there is no selection**</span></span>  
 <span data-ttu-id="b47b5-138">设置将插入点放在空行中，不选择任何内容，再单击 **“复制”** 或 **“剪切”** 时的编辑器行为。</span><span class="sxs-lookup"><span data-stu-id="b47b5-138">Set the behavior of the editor when you place the insertion point on a blank line, select nothing, and then click **Copy** or **Cut**.</span></span>  
  
 <span data-ttu-id="b47b5-139">如果选中此复选框，将复制或剪切空白行。</span><span class="sxs-lookup"><span data-stu-id="b47b5-139">When this check box is selected, the blank line is copied or cut.</span></span> <span data-ttu-id="b47b5-140">如果随后单击 **“粘贴”**，将插入一个新空白行。</span><span class="sxs-lookup"><span data-stu-id="b47b5-140">If you then click **Paste**, a new, blank line is inserted.</span></span>  
  
 <span data-ttu-id="b47b5-141">如果此复选框处于未选中状态，则不复制或剪切任何内容。</span><span class="sxs-lookup"><span data-stu-id="b47b5-141">When this check box is cleared, nothing is copied or cut.</span></span> <span data-ttu-id="b47b5-142">如果随后单击 **“粘贴”**，将粘贴最近一次复制的内容。</span><span class="sxs-lookup"><span data-stu-id="b47b5-142">If you then click **Paste**, the content most recently copied is pasted.</span></span> <span data-ttu-id="b47b5-143">如果尚未复制任何内容，则不会粘贴任何内容。</span><span class="sxs-lookup"><span data-stu-id="b47b5-143">If nothing has been copied, nothing is pasted.</span></span>  
  
 <span data-ttu-id="b47b5-144">如果所在行不是空白行，则此设置对 **“复制”** 或 **“剪切”** 无效。</span><span class="sxs-lookup"><span data-stu-id="b47b5-144">This setting has no effect on the **Copy** or **Cut** commands when a line is not blank.</span></span> <span data-ttu-id="b47b5-145">如果没有选定任何内容，将复制或剪切整个行。</span><span class="sxs-lookup"><span data-stu-id="b47b5-145">If nothing is selected, the entire line is copied or cut.</span></span> <span data-ttu-id="b47b5-146">如果随后单击 **“粘贴”**，将粘贴整个行的文本及其行终止符。</span><span class="sxs-lookup"><span data-stu-id="b47b5-146">If you then click **Paste**, the text of the entire line and its end line character are pasted.</span></span>  
  
## <a name="display"></a><span data-ttu-id="b47b5-147">显示</span><span class="sxs-lookup"><span data-stu-id="b47b5-147">Display</span></span>  
 <span data-ttu-id="b47b5-148">**行号**</span><span class="sxs-lookup"><span data-stu-id="b47b5-148">**Line numbers**</span></span>  
 <span data-ttu-id="b47b5-149">在每行代码的旁边显示行号。</span><span class="sxs-lookup"><span data-stu-id="b47b5-149">Display a line number next to each line of code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b47b5-150">这些行号不会添加到代码中，也不会打印出来。</span><span class="sxs-lookup"><span data-stu-id="b47b5-150">These line numbers are not added to your code, and they do not print.</span></span> <span data-ttu-id="b47b5-151">它们仅供参考。</span><span class="sxs-lookup"><span data-stu-id="b47b5-151">They are for reference only.</span></span>  
  
 <span data-ttu-id="b47b5-152">**启用单击 URL 定位**</span><span class="sxs-lookup"><span data-stu-id="b47b5-152">**Enable single-click URL navigation**</span></span>  
 <span data-ttu-id="b47b5-153">当光标移至编辑器的 URL 上方时将变为手形指针符号。</span><span class="sxs-lookup"><span data-stu-id="b47b5-153">Change the cursor to a symbol of a pointing hand when it passes over a URL in the editor.</span></span> <span data-ttu-id="b47b5-154">您可以单击 URL 以在 Web 浏览器中显示所指示的页。</span><span class="sxs-lookup"><span data-stu-id="b47b5-154">You can click the URL to display the indicated page in your Web browser.</span></span>  
  
 <span data-ttu-id="b47b5-155">**导航栏**</span><span class="sxs-lookup"><span data-stu-id="b47b5-155">**Navigation bar**</span></span>  
 <span data-ttu-id="b47b5-156">在代码编辑器的顶端显示导航栏。</span><span class="sxs-lookup"><span data-stu-id="b47b5-156">Display a navigation bar at the top of the Code Editor.</span></span> <span data-ttu-id="b47b5-157">使用其“对象”\*\*\*\* 和“过程”\*\*\*\* 下拉列表可以选择代码中的特定对象，再从所列的过程中进行选择，然后插入所选过程的实例。</span><span class="sxs-lookup"><span data-stu-id="b47b5-157">Use its **Objects**and **Procedures** drop-down lists to choose a particular object in your code, select from its procedures, and insert an instance of the selected procedure.</span></span> <span data-ttu-id="b47b5-158">并不是所有代码类型都可使用导航栏。</span><span class="sxs-lookup"><span data-stu-id="b47b5-158">The navigation baris not available for all code types.</span></span>  
  
  
