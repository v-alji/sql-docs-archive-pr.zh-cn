---
title: 管理代码格式
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- indenting code [SQL Server]
- displaying URLs
- code formatting [SQL Server Management Studio]
- collapsing text
- formats [SQL Server], code formatting in SQL Server Management Studio
- hiding text
- formats [SQL Server]
- text [SQL Server], code formats
- automatic indentation
- converting text to lower case
- Query Editor [SQL Server Management Studio], managing code formats
- URL displayed in code [SQL Server Management Studio]
- converting text to upper case
- text [SQL Server]
- unindenting code
ms.assetid: ddbac4d2-6bdc-4467-a352-e869ec880eed
author: rothja
ms.author: jroth
ms.openlocfilehash: 873848c8aee575b47f7a3d8c31d8392cba5ed12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591222"
---
# <a name="manage-code-formatting"></a><span data-ttu-id="4e4a3-102">管理代码格式</span><span class="sxs-lookup"><span data-stu-id="4e4a3-102">Manage Code Formatting</span></span>
  <span data-ttu-id="4e4a3-103">使用编辑器可以用缩进、隐藏文本、URL 等来设置代码的格式。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-103">With the Editor you can format your code with indenting, hidden text, URLs, and so forth.</span></span> <span data-ttu-id="4e4a3-104">还可以使用智能缩进在键入时自动格式化代码。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-104">You can also auto-format your code as you type by using Smart Indenting.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="4e4a3-105">缩进</span><span class="sxs-lookup"><span data-stu-id="4e4a3-105">Indenting</span></span>  
 <span data-ttu-id="4e4a3-106">可以选择三种不同样式的文本缩进。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-106">You can choose three different styles of text indenting.</span></span> <span data-ttu-id="4e4a3-107">此外，还可以指定由多少个空格组成一个缩进或制表符，以及在缩进时编辑器是使用制表符，还是使用空格。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-107">You can also specify how many spaces compose a single indentation or tab, and whether the Editor uses tabs or space characters when indenting.</span></span>  
  
#### <a name="to-choose-an-indenting-style"></a><span data-ttu-id="4e4a3-108">选择缩进样式</span><span class="sxs-lookup"><span data-stu-id="4e4a3-108">To choose an indenting style</span></span>  
  
1.  <span data-ttu-id="4e4a3-109">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-109">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="4e4a3-110">单击 **“文本编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-110">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="4e4a3-111">单击文件夹，并选择 **“所有语言”** ，可以为所有语言设置缩进。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-111">Click the folder, and select **All Languages** to set indenting for all languages.</span></span>  
  
4.  <span data-ttu-id="4e4a3-112">单击 **“选项卡”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-112">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="4e4a3-113">单击下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="4e4a3-113">Click one of the following options:</span></span>  
  
    -   <span data-ttu-id="4e4a3-114">**无**。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-114">**None**.</span></span> <span data-ttu-id="4e4a3-115">光标转到下一行的开始位置。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-115">The cursor goes to the beginning of the next line.</span></span>  
  
    -   <span data-ttu-id="4e4a3-116">**块**。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-116">**Block**.</span></span> <span data-ttu-id="4e4a3-117">光标在下一行时与在上一行时的位置对齐。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-117">The cursor aligns the next line with the previous line.</span></span>  
  
    -   <span data-ttu-id="4e4a3-118">“智能”  （默认）。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-118">**Smart** (Default).</span></span> <span data-ttu-id="4e4a3-119">由语言服务确定要使用的适当缩进样式。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-119">The language service determines the appropriate indenting style to use.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4e4a3-120">某些语言不提供所有这三种缩进选项。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-120">Some languages do not offer all three indenting options.</span></span>  
  
#### <a name="to-change-indent-tab-settings"></a><span data-ttu-id="4e4a3-121">更改缩进制表符设置</span><span class="sxs-lookup"><span data-stu-id="4e4a3-121">To change indent tab settings</span></span>  
  
1.  <span data-ttu-id="4e4a3-122">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-122">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="4e4a3-123">单击 **“文本编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-123">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="4e4a3-124">选择 **“所有语言”** 的文件夹，可以为所有语言设置缩进。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-124">Select the folder for **All Languages** to set indenting for all languages.</span></span>  
  
4.  <span data-ttu-id="4e4a3-125">单击 **“选项卡”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-125">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="4e4a3-126">若要指定制表符和缩进操作的制表符字符数，请单击 **“保留制表符”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-126">To specify tab characters for tab and indent operations, click **Keep tabs**.</span></span> <span data-ttu-id="4e4a3-127">若要指定空格数，请选择 **“插入空格”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-127">To specify space characters, select **Insert spaces**.</span></span>  
  
     <span data-ttu-id="4e4a3-128">如果选择 **“插入空格”** ，请在 **“制表符大小”** 或 **“缩进大小”** 下分别输入每个制表符或缩进所代表的空格数。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-128">If you select **Insert Spaces**, enter the number of space characters each tab or indent represents under **Tab Size** or **Indent Size**, respectively.</span></span>  
  
#### <a name="to-indent-code"></a><span data-ttu-id="4e4a3-129">缩进代码</span><span class="sxs-lookup"><span data-stu-id="4e4a3-129">To indent code</span></span>  
  
1.  <span data-ttu-id="4e4a3-130">选择要缩进的文本。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-130">Select the text you want to indent.</span></span>  
  
2.  <span data-ttu-id="4e4a3-131">按 Tab 键，或在标准工具栏上单击 **“缩进”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-131">Press TAB, or click the **Indent** button on the Standard toolbar.</span></span>  
  
#### <a name="to-unindent-code"></a><span data-ttu-id="4e4a3-132">取消代码的缩进</span><span class="sxs-lookup"><span data-stu-id="4e4a3-132">To unindent code</span></span>  
  
1.  <span data-ttu-id="4e4a3-133">选择要取消缩进的文本。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-133">Select the text you want to unindent.</span></span>  
  
2.  <span data-ttu-id="4e4a3-134">按 Shift+Tab，或在标准工具栏上单击  “取消缩进”按钮。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-134">Press SHIFT+TAB, or click the **Unindent** button on the Standard toolbar.</span></span>  
  
#### <a name="to-automatically-indent-all-of-your-code"></a><span data-ttu-id="4e4a3-135">自动缩进所有代码</span><span class="sxs-lookup"><span data-stu-id="4e4a3-135">To automatically indent all of your code</span></span>  
  
1.  <span data-ttu-id="4e4a3-136">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-136">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="4e4a3-137">单击 **“文本编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-137">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="4e4a3-138">单击 **“所有语言”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-138">Click **All Languages**.</span></span>  
  
4.  <span data-ttu-id="4e4a3-139">单击 **“选项卡”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-139">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="4e4a3-140">单击 **“智能”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-140">Click **Smart**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e4a3-141"> “智能”选项对某些语言不可用。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-141">The **Smart** option is not available for some languages.</span></span>  
  
#### <a name="to-convert-white-space-to-tabs"></a><span data-ttu-id="4e4a3-142">将空白空格转换成制表符</span><span class="sxs-lookup"><span data-stu-id="4e4a3-142">To convert white space to tabs</span></span>  
  
1.  <span data-ttu-id="4e4a3-143">选择要将其空白空格转换成制表符的文本。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-143">Select the text whose white space you want to convert to tabs.</span></span>  
  
2.  <span data-ttu-id="4e4a3-144">在 **“编辑”** 菜单上，指向 **“高级”** ，并单击 **“制表符替换空格”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-144">On the **Edit** menu, point to **Advanced**, and click **Tabify Selection**.</span></span>  
  
#### <a name="to-convert-tabs-to-spaces"></a><span data-ttu-id="4e4a3-145">将制表符转换成空格</span><span class="sxs-lookup"><span data-stu-id="4e4a3-145">To convert tabs to spaces</span></span>  
  
1.  <span data-ttu-id="4e4a3-146">选择想要将其制表符转换成空格的文本。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-146">Select the text whose tabs you want to convert to spaces.</span></span>  
  
2.  <span data-ttu-id="4e4a3-147">在 **“编辑”** 菜单上，指向 **“高级”** ，并单击 **“空格替换制表符”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-147">On the **Edit** menu, point to **Advanced**, and click **Untabify Selection**.</span></span>  
  
 <span data-ttu-id="4e4a3-148">这些命令的行为取决于在 **“选项”** 对话框中的制表符设置。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-148">The behavior of these commands depends on the tab settings in the **Options** dialog box.</span></span> <span data-ttu-id="4e4a3-149">例如，如果制表符设置是 4，则 **“制表符替换空格”** 为每 4 个连续空格创建一个制表符，而 **“空格替换制表符”** 则为每个制表符创建 4 个空格。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-149">For example, if the tab setting is 4, **Tabify Selection** creates a tab for every 4 contiguous spaces, and **Untabify Selection** creates 4 spaces for every tab.</span></span>  
  
## <a name="converting-text-to-upper-and-lower-case"></a><span data-ttu-id="4e4a3-150">转换文本的大小写</span><span class="sxs-lookup"><span data-stu-id="4e4a3-150">Converting Text to Upper and Lower Case</span></span>  
 <span data-ttu-id="4e4a3-151">可以使用命令将文本转换为全部大写或小写。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-151">You can use commands to convert text to all uppercase or lower case.</span></span>  
  
#### <a name="to-switch-text-to-upper-or-lower-case"></a><span data-ttu-id="4e4a3-152">将文本切换为大写或小写</span><span class="sxs-lookup"><span data-stu-id="4e4a3-152">To switch text to upper or lower case</span></span>  
  
1.  <span data-ttu-id="4e4a3-153">选择要转换的文本。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-153">Select the text you want to convert.</span></span>  
  
2.  <span data-ttu-id="4e4a3-154">若要将文本转换为大写，请按 Ctrl+Shift+U，或单击“编辑”菜单的“高级”子菜单上的“转换为大写”。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-154">To convert text to uppercase, press CTRL+SHIFT+U, or click **Make Uppercase** on the **Advanced** submenu of the **Edit** menu.</span></span>  
  
3.  <span data-ttu-id="4e4a3-155">若要将文本转换为小写，请按 Ctrl+Shift+L，或单击“编辑”菜单的“高级”子菜单上的“转换为小写”。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-155">To convert text to lowercase, press CTRL+SHIFT+L, or click **Make Lowercase** on the **Advanced** submenu of the **Edit** menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e4a3-156">有关键盘快捷键的完整列表，请参阅 [SQL Server Management Studio 键盘快捷键](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-156">For a complete list of keyboard shortcut keys, see [SQL Server Management Studio Keyboard Shortcuts](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).</span></span>  
  
## <a name="displaying-and-linking-to-urls"></a><span data-ttu-id="4e4a3-157">显示和链接到 URL</span><span class="sxs-lookup"><span data-stu-id="4e4a3-157">Displaying and Linking to URLs</span></span>  
 <span data-ttu-id="4e4a3-158">可以在代码中创建并显示可单击的 URL。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-158">You can create and display clickable URLs in your code.</span></span> <span data-ttu-id="4e4a3-159">默认情况下，URL：</span><span class="sxs-lookup"><span data-stu-id="4e4a3-159">By default, the URLs:</span></span>  
  
-   <span data-ttu-id="4e4a3-160">带下划线。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-160">Are underlined.</span></span>  
  
-   <span data-ttu-id="4e4a3-161">鼠标指针移到它们上面时，指针更改为手形。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-161">Change the mouse pointer to a hand when you move over them.</span></span>  
  
-   <span data-ttu-id="4e4a3-162">如果 URL 有效，单击时将打开 URL。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-162">Open the URL when clicked, if the URL is valid.</span></span>  
  
#### <a name="to-display-a-clickable-url"></a><span data-ttu-id="4e4a3-163">显示可单击的 URL</span><span class="sxs-lookup"><span data-stu-id="4e4a3-163">To display a clickable URL</span></span>  
  
1.  <span data-ttu-id="4e4a3-164">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-164">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="4e4a3-165">单击 **“文本编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-165">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="4e4a3-166">若要只更改一种语言的选项，请单击该语言文件夹，再单击 **“常规”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-166">To change the option for only one language, click that language folder and then click **General**.</span></span> <span data-ttu-id="4e4a3-167">若要更改所有语言的选项，请单击 **“所有语言”** ，再单击 **“常规”** 。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-167">To change the option for all languages, click **All Languages** and then click **General**.</span></span>  
  
4.  <span data-ttu-id="4e4a3-168">选择  “启用单击 URL 定位”。</span><span class="sxs-lookup"><span data-stu-id="4e4a3-168">Select **Enable single-click URL navigation**.</span></span>  
  
  
