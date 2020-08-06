---
title: 自定义（“命令”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.vs.customizecom.f1
ms.assetid: c8965f2c-51d9-437d-a6f3-8ac2075ede6b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 684fb9a6266fafae00b9881eb64a3642e6c98c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690298"
---
# <a name="customize-commands-page"></a><span data-ttu-id="b2e8a-102">自定义（“命令”页）</span><span class="sxs-lookup"><span data-stu-id="b2e8a-102">Customize (Commands Page)</span></span>
  <span data-ttu-id="b2e8a-103">使用此对话框，您可以在工具栏和菜单上添加和删除命令，以及更改用于工具栏按钮或菜单命令的图像。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-103">This dialog box enables you to add and remove commands on toolbars and menus as well as change the images used for toolbar buttons or menu commands.</span></span> <span data-ttu-id="b2e8a-104">可以通过在“工具”  菜单上单击“自定义  ”，再单击“命令”  ，来访问“命令”  页。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-104">You can access the **Commands** page by clicking **Customize** on the **Tools** menu and then clicking **Commands**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b2e8a-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="b2e8a-105">UI element list</span></span>  
 <span data-ttu-id="b2e8a-106">**类别**</span><span class="sxs-lookup"><span data-stu-id="b2e8a-106">**Categories**</span></span>  
 <span data-ttu-id="b2e8a-107">指定在“命令”  列表框中显示的命令集。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-107">Specifies the set of commands that are displayed in the **Commands** list box.</span></span> <span data-ttu-id="b2e8a-108">命令的类别基于环境当前支持的工具和设计器所提供的菜单标题。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-108">The categories of commands are based on menu titles provided by the tools and designers that the environment is currently supporting.</span></span> <span data-ttu-id="b2e8a-109">此标题列表是动态的，所以根据工具和设计器的不同，以及对它们所做的任何自定义设置，类别和菜单标题的顺序会有所变化。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-109">This list of titles is dynamic so that the order of categories and the menu titles change, depending on the tools and the designer, as well as any customizations made to them.</span></span> <span data-ttu-id="b2e8a-110">因此，来自不同设计器的两个菜单可能具有相同的名称，所以相同的标题可以会出现两次，却提供不同的命令集。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-110">Therefore, it is possible for two menus from different designers to have the same name, so the same title can appear twice but offer different command sets.</span></span>  
  
 <span data-ttu-id="b2e8a-111">**命令**</span><span class="sxs-lookup"><span data-stu-id="b2e8a-111">**Commands**</span></span>  
 <span data-ttu-id="b2e8a-112">根据所选的类别显示命令和命令图像。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-112">Displays the commands and command images based on the category you selected.</span></span> <span data-ttu-id="b2e8a-113">您可以将命令拖动到要自定义的工具栏上。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-113">You can drag a command onto the toolbar you want to customize.</span></span>  
  
 <span data-ttu-id="b2e8a-114">**修改选中的内容**</span><span class="sxs-lookup"><span data-stu-id="b2e8a-114">**Modify Selection**</span></span>  
 <span data-ttu-id="b2e8a-115">显示可用于自定义工具栏上按钮显示的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-115">Displays a list of commands you can use to customize the display of the button on the toolbar.</span></span> <span data-ttu-id="b2e8a-116">例如，您可以更改图像或快捷键，以及指定是否显示文本以替代命令的图像。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-116">For example, you can change the image or accelerator keys, as well as specify whether to display text instead of an image for the command.</span></span> <span data-ttu-id="b2e8a-117">在要自定义的工具栏上选择一个命令按钮后，即可使用此按钮。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-117">This button is available after you select a command button on a toolbar you want to customize.</span></span>  
  
 <span data-ttu-id="b2e8a-118">**重排命令**</span><span class="sxs-lookup"><span data-stu-id="b2e8a-118">**Rearrange Commands**</span></span>  
 <span data-ttu-id="b2e8a-119">显示“重排命令”  对话框，在其中可以对菜单和工具栏上的命令进行重命名、重新排序、添加和删除操作，并可以更改按钮和命令图像。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-119">Displays the **Rearrange Commands** dialog box, which allows you to rename, reorder, add, and remove commands on menus and toolbars as well as change button and command images.</span></span>  
  
 <span data-ttu-id="b2e8a-120">**键盘**</span><span class="sxs-lookup"><span data-stu-id="b2e8a-120">**Keyboard**</span></span>  
 <span data-ttu-id="b2e8a-121">显示“选项”  对话框的“键盘”  页，以便可以为命令指定快捷键组合。</span><span class="sxs-lookup"><span data-stu-id="b2e8a-121">Displays the **Keyboard** page of the **Options** dialog box so you can specify shortcut key combinations for commands.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e8a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2e8a-122">See Also</span></span>  
 [<span data-ttu-id="b2e8a-123">自定义菜单和快捷键</span><span class="sxs-lookup"><span data-stu-id="b2e8a-123">Customize Menus and Shortcut Keys</span></span>](../customize-menus-and-shortcut-keys.md)  
