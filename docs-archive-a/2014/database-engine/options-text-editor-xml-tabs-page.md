---
title: 选项 (文本编辑器： XML： Tabs Page) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
ms.assetid: 13bf5f8c-aba3-4c05-b8bb-eb475797c9bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 3047d6c05ffb88d07a4bf2e5b1d4143412046c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682370"
---
# <a name="options-text-editorxmltabs-page"></a><span data-ttu-id="ef82b-102">选项（“文本编辑器”:“XML”:“选项卡”页）</span><span class="sxs-lookup"><span data-stu-id="ef82b-102">Options (Text Editor:XML:Tabs Page)</span></span>
  <span data-ttu-id="ef82b-103">此对话框支持您更改 XML 编辑器（用于编辑 XML 文档）的跳格行为。</span><span class="sxs-lookup"><span data-stu-id="ef82b-103">This dialog box lets you change the tabbing behavior of the XML Editor, which is used to edit XML documents.</span></span> <span data-ttu-id="ef82b-104">若要显示这些设置，请在 **“工具”** 菜单上单击 **“选项”** ，展开 **“文本编辑器”** 文件夹，展开 **XML** 子文件夹，再单击 **“制表符”**。</span><span class="sxs-lookup"><span data-stu-id="ef82b-104">To display these settings, click **Options** on the **Tools** menu, expand the **Text Editor** folder, expand the **XML** subfolder and then click **Tabs**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="ef82b-105">在多个位置设置选项</span><span class="sxs-lookup"><span data-stu-id="ef82b-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="ef82b-106">XML 编辑器的选项也可在“所有语言”和“常规”对话框中设置。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ef82b-106">Options for the XML Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="ef82b-107">如果使用 "**所有语言**" 对话框来设置其他 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 编辑器（例如 DMX 或 MDX 编辑器）的其他选项，则必须使用此对话框重置 XML 编辑器选项。</span><span class="sxs-lookup"><span data-stu-id="ef82b-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the XML Editor options using this dialog.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="ef82b-108">缩进</span><span class="sxs-lookup"><span data-stu-id="ef82b-108">Indenting</span></span>  
 <span data-ttu-id="ef82b-109">**无**</span><span class="sxs-lookup"><span data-stu-id="ef82b-109">**None**</span></span>  
 <span data-ttu-id="ef82b-110">选择此选项后，则按 Enter 键时所创建的新行不会缩进。</span><span class="sxs-lookup"><span data-stu-id="ef82b-110">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="ef82b-111">光标置于新行的第一列。</span><span class="sxs-lookup"><span data-stu-id="ef82b-111">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="ef82b-112">**阻止**</span><span class="sxs-lookup"><span data-stu-id="ef82b-112">**Block**</span></span>  
 <span data-ttu-id="ef82b-113">如果选择此选项，则按 Enter 时创建的新行的自动缩进距离与上一行的缩进距离相同。</span><span class="sxs-lookup"><span data-stu-id="ef82b-113">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line.</span></span>  
  
 <span data-ttu-id="ef82b-114">**智能**</span><span class="sxs-lookup"><span data-stu-id="ef82b-114">**Smart**</span></span>  
 <span data-ttu-id="ef82b-115">选择此选项后，则按 Enter 键时所创建的新行会根据上下文调整位置。</span><span class="sxs-lookup"><span data-stu-id="ef82b-115">When this option is selected, the new line created when you press ENTER is positioned according to the context.</span></span> <span data-ttu-id="ef82b-116">例如，在左大括号 ({) 后，包含的行将自动多缩进一个制表位。</span><span class="sxs-lookup"><span data-stu-id="ef82b-116">For example, after an opening brace ({), the included lines are automatically indented an extra tab stop.</span></span> <span data-ttu-id="ef82b-117">对应的右大括号 (}) 将根据其左大括号重新对齐。</span><span class="sxs-lookup"><span data-stu-id="ef82b-117">The matching closing brace (}) is realigned with its opening brace.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="ef82b-118">选项卡</span><span class="sxs-lookup"><span data-stu-id="ef82b-118">Tabs</span></span>  
 <span data-ttu-id="ef82b-119">**制表符大小**</span><span class="sxs-lookup"><span data-stu-id="ef82b-119">**Tab size**</span></span>  
 <span data-ttu-id="ef82b-120">设置制表位之间的距离（以空格为单位）。</span><span class="sxs-lookup"><span data-stu-id="ef82b-120">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="ef82b-121">默认为四个空格。</span><span class="sxs-lookup"><span data-stu-id="ef82b-121">The default is four spaces.</span></span>  
  
 <span data-ttu-id="ef82b-122">**缩进大小**</span><span class="sxs-lookup"><span data-stu-id="ef82b-122">**Indent size**</span></span>  
 <span data-ttu-id="ef82b-123">设置自动缩进的大小（以空格为单位）。</span><span class="sxs-lookup"><span data-stu-id="ef82b-123">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="ef82b-124">默认为四个空格。</span><span class="sxs-lookup"><span data-stu-id="ef82b-124">The default is four spaces.</span></span> <span data-ttu-id="ef82b-125">可能会插入制表符、空格字符，或同时插入这二者，以填充为指定大小。</span><span class="sxs-lookup"><span data-stu-id="ef82b-125">Tab characters, space characters, or both are inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="ef82b-126">**插入空格**</span><span class="sxs-lookup"><span data-stu-id="ef82b-126">**Insert spaces**</span></span>  
 <span data-ttu-id="ef82b-127">选择此选项后，缩进操作仅插入空格字符，而不会插入制表符。</span><span class="sxs-lookup"><span data-stu-id="ef82b-127">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="ef82b-128">例如，如果 "**缩进大小**" 设置为5，则每次按 tab 键或单击主窗口工具栏上的 "**增加缩进**" 按钮时，都会插入五个空格字符 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ef82b-128">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar in the main [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] window.</span></span>  
  
 <span data-ttu-id="ef82b-129">**保留制表符**</span><span class="sxs-lookup"><span data-stu-id="ef82b-129">**Keep tabs**</span></span>  
 <span data-ttu-id="ef82b-130">选择此选项后，缩进操作会插入尽可能多的制表符。</span><span class="sxs-lookup"><span data-stu-id="ef82b-130">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="ef82b-131">每个制表符都会填充 **“制表符大小”** 中指定的空格数。</span><span class="sxs-lookup"><span data-stu-id="ef82b-131">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="ef82b-132">如果 **“缩进大小”** 不是 **“制表符大小”** 的偶数倍，则会添加空格字符补齐。</span><span class="sxs-lookup"><span data-stu-id="ef82b-132">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
