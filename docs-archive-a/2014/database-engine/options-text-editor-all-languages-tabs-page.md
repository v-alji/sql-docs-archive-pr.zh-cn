---
title: 选项 (文本编辑器-所有语言-选项卡页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bd715d6b-f873-41d4-aa10-57b7098b61cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 13f791e34b2099e8c0492c25886ee6b37ef1a1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589870"
---
# <a name="options-text-editor---all-languages--tabs-page"></a><span data-ttu-id="376ad-102">选项（“文本编辑器”-“所有语言”-“选项卡”页）</span><span class="sxs-lookup"><span data-stu-id="376ad-102">Options (Text Editor - All Languages -Tabs Page)</span></span>
  <span data-ttu-id="376ad-103">使用此对话框可以设置 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的所有五个编辑器的跳格行为。</span><span class="sxs-lookup"><span data-stu-id="376ad-103">Use this dialog box to set the tabbing behavior in all five of the editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="376ad-104">若要显示这些选项，请在 **“工具”** 菜单上单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="376ad-104">To display these options, click **Options** on the **Tools** menu.</span></span> <span data-ttu-id="376ad-105">选择“文本编辑器”\*\*\*\* 文件夹，展开“所有语言”\*\*\*\* 文件夹，再单击“制表符”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="376ad-105">Select the **Text Editor** folder, expand the **All Languages** folder and then click **Tabs**.</span></span>  
  
## <a name="tabbing-options-by-editor"></a><span data-ttu-id="376ad-106">编辑器的跳格选项</span><span class="sxs-lookup"><span data-stu-id="376ad-106">Tabbing Options by Editor</span></span>  
 <span data-ttu-id="376ad-107">您必须使用 **“所有语言”** 对话框来设置 DMX、MDX 和 SQL Server Compact 编辑器的选项。</span><span class="sxs-lookup"><span data-stu-id="376ad-107">You must use the **All Languages** dialogs to set options for the DMX, MDX, and SQL Server Compact editors.</span></span> <span data-ttu-id="376ad-108">此处设置的选项也适用于纯文本、Transact-SQL 和 XML 编辑器，但您可以通过展开这些语言的子文件夹并选择相应的选项页面来为这些编辑器单独设置选项。</span><span class="sxs-lookup"><span data-stu-id="376ad-108">Options set here are also applied to the Plain Text, Transact-SQL, and XML editors, but you can set options separately for those editors by expanding the subfolders for those languages and selecting their option pages.</span></span> <span data-ttu-id="376ad-109">某些语言只能支持部分跳格选项。</span><span class="sxs-lookup"><span data-stu-id="376ad-109">Some languages do not support all of the tabbing options.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="376ad-110">如果你使用此对话框设置了选项，但希望在纯文本、Transact-SQL 或 XML 编辑器中使用不同设置，则必须在“所有语言”\*\*\*\* 对话框中应用选项之后为这些编辑器设置选项。</span><span class="sxs-lookup"><span data-stu-id="376ad-110">If you set an option using this dialog, but want a different setting for the Plain Text, Transact-SQL, or XML editors, you must set the options for those editors after applying your selections in the **All Languages** dialog.</span></span>  
  
 <span data-ttu-id="376ad-111">如果为特定编辑器选择了不同设置，则将显示“各种文本格式的缩进(或制表符)设置相互冲突”消息。</span><span class="sxs-lookup"><span data-stu-id="376ad-111">The message "The indentation (or tab) settings for individual text formats conflict with each other" is displayed when different settings have been selected for particular editors.</span></span> <span data-ttu-id="376ad-112">例如，如果为“纯文本”\*\*\*\* 选择了“块缩进”\*\*\*\* 选项，而为“XML”\*\*\*\* 选择了“无”\*\*\*\*，那么将会显示此提示信息。</span><span class="sxs-lookup"><span data-stu-id="376ad-112">For example, this reminder is displayed if the **Block indenting** option is selected for **Plain Text**, but **None** is selected for **XML**.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="376ad-113">缩进</span><span class="sxs-lookup"><span data-stu-id="376ad-113">Indenting</span></span>  
 <span data-ttu-id="376ad-114">**无**</span><span class="sxs-lookup"><span data-stu-id="376ad-114">**None**</span></span>  
 <span data-ttu-id="376ad-115">选择此选项后，则按 Enter 键时所创建的新行不会缩进。</span><span class="sxs-lookup"><span data-stu-id="376ad-115">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="376ad-116">光标置于新行的第一列。</span><span class="sxs-lookup"><span data-stu-id="376ad-116">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="376ad-117">**阻止**</span><span class="sxs-lookup"><span data-stu-id="376ad-117">**Block**</span></span>  
 <span data-ttu-id="376ad-118">如果选择此选项，则按 Enter 时所创建新行的自动缩进距离与上一行的缩进距离相同。</span><span class="sxs-lookup"><span data-stu-id="376ad-118">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line was indented.</span></span>  
  
 <span data-ttu-id="376ad-119">**智能**</span><span class="sxs-lookup"><span data-stu-id="376ad-119">**Smart**</span></span>  
 <span data-ttu-id="376ad-120">选择此选项后，则按 Enter 键时所创建的新行会根据上下文调整位置。</span><span class="sxs-lookup"><span data-stu-id="376ad-120">When this option is selected, the new line created when you press ENTER is positioned according to the context.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="376ad-121">选项卡</span><span class="sxs-lookup"><span data-stu-id="376ad-121">Tabs</span></span>  
 <span data-ttu-id="376ad-122">**制表符大小**</span><span class="sxs-lookup"><span data-stu-id="376ad-122">**Tab size**</span></span>  
 <span data-ttu-id="376ad-123">设置制表位之间的距离（以空格为单位）。</span><span class="sxs-lookup"><span data-stu-id="376ad-123">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="376ad-124">默认为四个空格。</span><span class="sxs-lookup"><span data-stu-id="376ad-124">The default is four spaces.</span></span>  
  
 <span data-ttu-id="376ad-125">**缩进大小**</span><span class="sxs-lookup"><span data-stu-id="376ad-125">**Indent size**</span></span>  
 <span data-ttu-id="376ad-126">设置自动缩进的大小（以空格为单位）。</span><span class="sxs-lookup"><span data-stu-id="376ad-126">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="376ad-127">默认为四个空格。</span><span class="sxs-lookup"><span data-stu-id="376ad-127">The default is four spaces.</span></span> <span data-ttu-id="376ad-128">可能会插入制表符、空格字符，或同时插入这二者，以填充为指定大小。</span><span class="sxs-lookup"><span data-stu-id="376ad-128">Tab characters, space characters, or both will be inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="376ad-129">**插入空格**</span><span class="sxs-lookup"><span data-stu-id="376ad-129">**Insert spaces**</span></span>  
 <span data-ttu-id="376ad-130">选择此选项后，缩进操作仅插入空格字符，而不会插入制表符。</span><span class="sxs-lookup"><span data-stu-id="376ad-130">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="376ad-131">如果“缩进大小”\*\*\*\* 设置为 5，则在按 Tab 键或单击 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 主窗口工具栏上的“增加缩进”\*\*\*\* 按钮时会插入五个空格。</span><span class="sxs-lookup"><span data-stu-id="376ad-131">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] main window.</span></span>  
  
 <span data-ttu-id="376ad-132">**保留制表符**</span><span class="sxs-lookup"><span data-stu-id="376ad-132">**Keep tabs**</span></span>  
 <span data-ttu-id="376ad-133">选择此选项后，缩进操作会插入尽可能多的制表符。</span><span class="sxs-lookup"><span data-stu-id="376ad-133">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="376ad-134">每个制表符都会填充 **“制表符大小”** 中指定的空格数。</span><span class="sxs-lookup"><span data-stu-id="376ad-134">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="376ad-135">如果 **“缩进大小”** 不是 **“制表符大小”** 的偶数倍，则会添加空格字符补齐。</span><span class="sxs-lookup"><span data-stu-id="376ad-135">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
