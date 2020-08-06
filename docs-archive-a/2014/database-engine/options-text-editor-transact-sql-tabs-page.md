---
title: 选项 (文本编辑器-Transact-sql-选项卡页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Tabs
dev_langs:
- TSQL
ms.assetid: a4499784-67f7-46ef-9f7c-2d0fdd117a52
author: rothja
ms.author: jroth
ms.openlocfilehash: 6caa659d13f8089fdd9f990a55e503657ef72a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588689"
---
# <a name="options-text-editor---transact-sql---tabs-page"></a><span data-ttu-id="258cd-102">选项 (文本编辑器-Transact-sql-选项卡页) </span><span class="sxs-lookup"><span data-stu-id="258cd-102">Options (Text Editor - Transact-SQL - Tabs Page)</span></span>
  <span data-ttu-id="258cd-103">使用此对话框可以更改用于对 [!INCLUDE[ssDE](../includes/ssde-md.md)] 脚本进行编程的[!INCLUDE[tsql](../includes/tsql-md.md)]查询编辑器的跳格行为。</span><span class="sxs-lookup"><span data-stu-id="258cd-103">Use this dialog to change the tabbing behavior of the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor, which is used to program [!INCLUDE[tsql](../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="258cd-104">若要显示这些设置，请在“工具”\*\*\*\* 菜单上单击“选项”\*\*\*\*，依次展开“文本编辑器”\*\*\*\* 文件夹和“Transact-SQL”\*\*\*\* 子文件夹，然后单击“制表符”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="258cd-104">To display these settings, click **Options** on the **Tools** menu, expand the **Text Editor** folder, expand the **Transact-SQL** subfolder and then click **Tabs**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="258cd-105">在多个位置设置选项</span><span class="sxs-lookup"><span data-stu-id="258cd-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="258cd-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] 查询编辑器的选项也可在“所有语言选项卡”\*\*\*\* 对话框中设置。</span><span class="sxs-lookup"><span data-stu-id="258cd-106">Options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor can also be set in the **All Languages Tabs** dialog.</span></span> <span data-ttu-id="258cd-107">如果使用 **“所有语言”** 对话框来设置其他 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 编辑器（例如 DMX 或 MDX 编辑器）的其他选项，则必须使用此对话框重置 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查询编辑器选项。</span><span class="sxs-lookup"><span data-stu-id="258cd-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor options using this dialog.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="258cd-108">缩进</span><span class="sxs-lookup"><span data-stu-id="258cd-108">Indenting</span></span>  
 <span data-ttu-id="258cd-109">**无**</span><span class="sxs-lookup"><span data-stu-id="258cd-109">**None**</span></span>  
 <span data-ttu-id="258cd-110">选择此选项后，则按 Enter 键时所创建的新行不会缩进。</span><span class="sxs-lookup"><span data-stu-id="258cd-110">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="258cd-111">光标置于新行的第一列。</span><span class="sxs-lookup"><span data-stu-id="258cd-111">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="258cd-112">**阻止**</span><span class="sxs-lookup"><span data-stu-id="258cd-112">**Block**</span></span>  
 <span data-ttu-id="258cd-113">如果选择此选项，则按 Enter 时创建的新行的自动缩进距离与上一行的缩进距离相同。</span><span class="sxs-lookup"><span data-stu-id="258cd-113">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line.</span></span>  
  
 <span data-ttu-id="258cd-114">**智能**</span><span class="sxs-lookup"><span data-stu-id="258cd-114">**Smart**</span></span>  
 <span data-ttu-id="258cd-115">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="258cd-115">This option is unavailable.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="258cd-116">选项卡</span><span class="sxs-lookup"><span data-stu-id="258cd-116">Tabs</span></span>  
 <span data-ttu-id="258cd-117">**制表符大小**</span><span class="sxs-lookup"><span data-stu-id="258cd-117">**Tab size**</span></span>  
 <span data-ttu-id="258cd-118">设置制表位之间的距离（以空格为单位）。</span><span class="sxs-lookup"><span data-stu-id="258cd-118">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="258cd-119">默认为四个空格。</span><span class="sxs-lookup"><span data-stu-id="258cd-119">The default is four spaces.</span></span>  
  
 <span data-ttu-id="258cd-120">**缩进大小**</span><span class="sxs-lookup"><span data-stu-id="258cd-120">**Indent size**</span></span>  
 <span data-ttu-id="258cd-121">设置自动缩进的大小（以空格为单位）。</span><span class="sxs-lookup"><span data-stu-id="258cd-121">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="258cd-122">默认为四个空格。</span><span class="sxs-lookup"><span data-stu-id="258cd-122">The default is four spaces.</span></span> <span data-ttu-id="258cd-123">可能会插入制表符、空格字符，或同时插入这二者，以填充为指定大小。</span><span class="sxs-lookup"><span data-stu-id="258cd-123">Tab characters, space characters, or both are inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="258cd-124">**插入空格**</span><span class="sxs-lookup"><span data-stu-id="258cd-124">**Insert spaces**</span></span>  
 <span data-ttu-id="258cd-125">选择此选项后，缩进操作仅插入空格字符，而不会插入制表符。</span><span class="sxs-lookup"><span data-stu-id="258cd-125">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="258cd-126">例如，如果 "**缩进大小**" 设置为5，则每次按 tab 键或单击主窗口工具栏上的 "**增加缩进**" 按钮时，都会插入五个空格字符 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="258cd-126">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar in the main [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] window.</span></span>  
  
 <span data-ttu-id="258cd-127">**保留制表符**</span><span class="sxs-lookup"><span data-stu-id="258cd-127">**Keep tabs**</span></span>  
 <span data-ttu-id="258cd-128">选择此选项后，缩进操作会插入尽可能多的制表符。</span><span class="sxs-lookup"><span data-stu-id="258cd-128">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="258cd-129">每个制表符都会填充 **“制表符大小”** 中指定的空格数。</span><span class="sxs-lookup"><span data-stu-id="258cd-129">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="258cd-130">如果 **“缩进大小”** 不是 **“制表符大小”** 的偶数倍，则会添加空格字符补齐。</span><span class="sxs-lookup"><span data-stu-id="258cd-130">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
