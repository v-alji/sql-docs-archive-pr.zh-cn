---
title: 管理使用编码的文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio]
- encoding [SQL Server Management Studio]
- files [SQL Server Management Studio], encoding
ms.assetid: 919544c9-59f0-4cc6-bb2a-f1ad671eb74b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9b0aaa123001fed3f6ad42ea9d642e4007e2640f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591693"
---
# <a name="manage-files-with-encoding"></a><span data-ttu-id="abf25-102">管理使用编码的文件</span><span class="sxs-lookup"><span data-stu-id="abf25-102">Manage Files with Encoding</span></span>
  <span data-ttu-id="abf25-103">为便于以特定语言显示代码以及在特定平台中显示代码，可以将特定的字符编码与文件关联。</span><span class="sxs-lookup"><span data-stu-id="abf25-103">To facilitate the display of your code in a particular language and on a particular platform, you can associate a particular character encoding with a file.</span></span>  
  
## <a name="opening-files"></a><span data-ttu-id="abf25-104">打开文件</span><span class="sxs-lookup"><span data-stu-id="abf25-104">Opening Files</span></span>  
 <span data-ttu-id="abf25-105">可以选择用于编辑文件的编辑器。</span><span class="sxs-lookup"><span data-stu-id="abf25-105">You can choose the editor you want to use to edit the file.</span></span>  
  
#### <a name="to-open-a-file-with-a-specific-editor"></a><span data-ttu-id="abf25-106">用特定的编辑器打开文件</span><span class="sxs-lookup"><span data-stu-id="abf25-106">To open a file with a specific editor</span></span>  
  
1.  <span data-ttu-id="abf25-107">在“文件”  菜单中，指向“打开”  ，再单击“文件”  。</span><span class="sxs-lookup"><span data-stu-id="abf25-107">On the **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="abf25-108">在“打开文件”  对话框中，选择文件名。</span><span class="sxs-lookup"><span data-stu-id="abf25-108">In the **Open File** dialog box, select the file name.</span></span>  
  
3.  <span data-ttu-id="abf25-109">单击“打开”  按钮旁边的箭头，再从显示的菜单中单击“打开方式”  。</span><span class="sxs-lookup"><span data-stu-id="abf25-109">Click the arrow next to the **Open** button, and then click**Open With** from the menu that appears.</span></span>  
  
4.  <span data-ttu-id="abf25-110">在“选择要打开的程序”  列表中，选择一种编辑器，再单击“打开”  。</span><span class="sxs-lookup"><span data-stu-id="abf25-110">In the **Select a program to open** list, select an editor, and then click **Open**.</span></span> <span data-ttu-id="abf25-111">若要用特定的编码打开文件，请选择提供编码支持的编辑器（如使用编码的 SQL 查询编辑器或使用编码的 XML 编辑器）。</span><span class="sxs-lookup"><span data-stu-id="abf25-111">To open the file with a particular encoding, select an editor with encoding support, such as SQL Query Editor with Encoding or XML Editor with Encoding.</span></span>  
  
## <a name="saving-files"></a><span data-ttu-id="abf25-112">保存文件</span><span class="sxs-lookup"><span data-stu-id="abf25-112">Saving Files</span></span>  
 <span data-ttu-id="abf25-113">也可以用 Unicode 编码或其他代码页保存代码，以支持各种语言，如西欧或东欧语言。</span><span class="sxs-lookup"><span data-stu-id="abf25-113">You can also save your code with a Unicode encoding or a different code page to support various languages, such as Western European or Eastern European.</span></span> <span data-ttu-id="abf25-114">可以将特定的字符编码与文件关联，以便于以该语言显示代码；也可以将特定的字符编码与行尾类型关联，以支持特定的操作系统。</span><span class="sxs-lookup"><span data-stu-id="abf25-114">You can associate a particular character encoding with a file to facilitate the display of your code in that language, as well as a line-ending type to support a particular operating system.</span></span> <span data-ttu-id="abf25-115">此外，某些字符如果被用在文件名中，则只有使用 Unicode 编码才能保存这些字符。</span><span class="sxs-lookup"><span data-stu-id="abf25-115">Also, some characters, when used in file names, cannot be saved unless they are saved with Unicode encoding.</span></span>  
  
#### <a name="to-save-a-file-with-a-different-encoding-or-line-ending-type"></a><span data-ttu-id="abf25-116">用其他编码或行尾类型保存文件</span><span class="sxs-lookup"><span data-stu-id="abf25-116">To save a file with a different encoding or line ending type</span></span>  
  
1.  <span data-ttu-id="abf25-117">在“文件”菜单上，单击“将 \<filename> 另存为”。</span><span class="sxs-lookup"><span data-stu-id="abf25-117">On the **File** menu, click **Save \<filename> As**.</span></span>  
  
2.  <span data-ttu-id="abf25-118">在“文件另存为”  对话框中，展开“保存”  按钮，再单击“编码保存”  。</span><span class="sxs-lookup"><span data-stu-id="abf25-118">In the **Save File As** dialog, expand the **Save** button, and then click **Save with Encoding**.</span></span>  
  
3.  <span data-ttu-id="abf25-119">从“高级保存选项”  对话框的“编码”  列表中，选择所需的编码。</span><span class="sxs-lookup"><span data-stu-id="abf25-119">In the **Advanced Save Options** dialog box, select the encoding you want from the **Encoding** list.</span></span>  
  
4.  <span data-ttu-id="abf25-120">从“行尾”  列表中，选择所需的行尾类型。</span><span class="sxs-lookup"><span data-stu-id="abf25-120">From the **Line Endings**list, select the type of line ending you want.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="abf25-121">如果用 Unicode 编码保存文件，则该文件应作为二进制文件签入 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe，因为 Visual SourceSafe 不支持对保存为 Unicode 的文件间的差异进行合并、比较和显示。</span><span class="sxs-lookup"><span data-stu-id="abf25-121">If you save your file your file with Unicode encoding, the file should be checked into [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe as a binary file because Visual SourceSafe does not support merging, comparing, and showing differences between files that are saved as Unicode.</span></span>  
  
 <span data-ttu-id="abf25-122">如果您使用 Visual SourceSafe 并以 ANSI、UTF8 或 Unicode 存储文件，请注意以下各种编码的限制：</span><span class="sxs-lookup"><span data-stu-id="abf25-122">If you are using Visual SourceSafe to store files with ANSI, UTF8, or Unicode, be aware of the following limitations for each:</span></span>  
  
-   <span data-ttu-id="abf25-123">ANSI 文件仅允许使用当前代码页中支持的字符，这将限制国际化的使用。</span><span class="sxs-lookup"><span data-stu-id="abf25-123">ANSI files allow only characters that are supported in the current code page, which limits international use.</span></span>  
  
-   <span data-ttu-id="abf25-124">Unicode 文件是作为二进制文件处理的，因此不能以共享方式签出、进行差异检查或合并功能。</span><span class="sxs-lookup"><span data-stu-id="abf25-124">Unicode files cannot use shared checkout, difference checking, or merging functionality because they are handled as binary files.</span></span> <span data-ttu-id="abf25-125">可以在国际化文件中使用此格式。</span><span class="sxs-lookup"><span data-stu-id="abf25-125">You can use this format in international files.</span></span>  
  
-   <span data-ttu-id="abf25-126">UTF8 文件不能在 Visual SourceSafe 中安全使用，因为在签入、签出、差异检查和合并过程中，会产生导致 UTF8 文件编辑器出现问题的更改。</span><span class="sxs-lookup"><span data-stu-id="abf25-126">UTF8 files do not work safely with Visual SourceSafe because changes that cause problems for UTF8 file editors are made during check in, check out, difference checking, and merging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf25-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abf25-127">See Also</span></span>  
 <span data-ttu-id="abf25-128">[用于管理解决方案和项目的文件](files-that-manage-solutions-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="abf25-128">[Files That Manage Solutions and Projects](files-that-manage-solutions-and-projects.md) </span></span>  
 [<span data-ttu-id="abf25-129">将文件扩展名与代码编辑器关联</span><span class="sxs-lookup"><span data-stu-id="abf25-129">Associate File Extensions to a Code Editor</span></span>](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
  
  
