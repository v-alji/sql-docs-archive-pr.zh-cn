---
title: 撤消签出 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ff6e6041b59caa75bf7f8530d915db48e0379338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577793"
---
# <a name="undo-checkouts"></a><span data-ttu-id="7e3de-102">撤消签出</span><span class="sxs-lookup"><span data-stu-id="7e3de-102">Undo Checkouts</span></span>
  <span data-ttu-id="7e3de-103">您可以使用 "**撤消签出**" 命令取消现有的签出。</span><span class="sxs-lookup"><span data-stu-id="7e3de-103">You can use the **Undo Checkout** command to cancel an existing checkout.</span></span> <span data-ttu-id="7e3de-104">如果您修改并保存了文件，但事后需要回滚所做的更改，此命令尤其有用。</span><span class="sxs-lookup"><span data-stu-id="7e3de-104">This is particularly useful when you have modified and saved a file, and then later need to roll back your changes.</span></span>  
  
 <span data-ttu-id="7e3de-105">根据你在 "**撤消签出高级选项**" 对话框中设置的选项，Studio 环境会将项的工作副本保留在本地磁盘上，或将其替换为最新的受源代码管理的版本。</span><span class="sxs-lookup"><span data-stu-id="7e3de-105">Depending on the options you set in the **Undo Checkout Advanced Options** dialog box, the Studio environment either leaves the working copy of the item on your local disk or replaces it with the latest source-controlled version.</span></span> <span data-ttu-id="7e3de-106">如果有人在源代码管理系统环境以外更改了项，那么检索到的版本就可能不是最新版本。</span><span class="sxs-lookup"><span data-stu-id="7e3de-106">If someone has modified the item outside the context of the source control system, the retrieved version may not be the latest one.</span></span>  
  
### <a name="to-undo-a-checkout"></a><span data-ttu-id="7e3de-107">撤消签出</span><span class="sxs-lookup"><span data-stu-id="7e3de-107">To undo a checkout</span></span>  
  
1.  <span data-ttu-id="7e3de-108">在“解决方案资源管理器”中，选择项目。</span><span class="sxs-lookup"><span data-stu-id="7e3de-108">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="7e3de-109">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**撤消签出**"。</span><span class="sxs-lookup"><span data-stu-id="7e3de-109">On the **File** menu, point to **Source Control**, and then click **Undo Checkout**.</span></span>  
  
3.  <span data-ttu-id="7e3de-110">在 "**撤消签出**" 对话框中，选择相应的选项，然后单击 "**撤消签出**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="7e3de-110">In the **Undo Checkout** dialog box, select the appropriate options, and then click the **Undo Checkout** button.</span></span>  
  
     <span data-ttu-id="7e3de-111">**“列”**</span><span class="sxs-lookup"><span data-stu-id="7e3de-111">**Columns**</span></span>  
     <span data-ttu-id="7e3de-112">标识要显示的列及其显示顺序。</span><span class="sxs-lookup"><span data-stu-id="7e3de-112">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="7e3de-113">**平面视图**</span><span class="sxs-lookup"><span data-stu-id="7e3de-113">**Flat View**</span></span>  
     <span data-ttu-id="7e3de-114">将项在其源代码管理连接下显示为平面列表。</span><span class="sxs-lookup"><span data-stu-id="7e3de-114">Display the items as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="7e3de-115">**名称**</span><span class="sxs-lookup"><span data-stu-id="7e3de-115">**Name**</span></span>  
     <span data-ttu-id="7e3de-116">显示要撤消签出的项的名称。</span><span class="sxs-lookup"><span data-stu-id="7e3de-116">Displays the names of the items for which to undo the checkout.</span></span> <span data-ttu-id="7e3de-117">所显示项旁边的复选框处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="7e3de-117">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="7e3de-118">如果不想撤消对某项的签出，请清除其复选框。</span><span class="sxs-lookup"><span data-stu-id="7e3de-118">If you do not want to undo the checkout of an item, clear its check box.</span></span>  
  
     <span data-ttu-id="7e3de-119">**选项**</span><span class="sxs-lookup"><span data-stu-id="7e3de-119">**Options**</span></span>  
     <span data-ttu-id="7e3de-120">单击按钮右侧的箭头时，显示源代码管理插件特定的撤消签出选项。</span><span class="sxs-lookup"><span data-stu-id="7e3de-120">Displays source control plug-in-specific undo checkout options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="7e3de-121">**Sort**</span><span class="sxs-lookup"><span data-stu-id="7e3de-121">**Sort**</span></span>  
     <span data-ttu-id="7e3de-122">对显示列进行排序。</span><span class="sxs-lookup"><span data-stu-id="7e3de-122">Sort the order of the display columns.</span></span>  
  
     <span data-ttu-id="7e3de-123">**树视图**</span><span class="sxs-lookup"><span data-stu-id="7e3de-123">**Tree View**</span></span>  
     <span data-ttu-id="7e3de-124">显示要撤消签出的项的文件夹和项层次结构。</span><span class="sxs-lookup"><span data-stu-id="7e3de-124">Display the folder and item hierarchy for items on which you are reversing the checkout.</span></span>  
  
     <span data-ttu-id="7e3de-125">**撤消签出**</span><span class="sxs-lookup"><span data-stu-id="7e3de-125">**Undo Checkout**</span></span>  
     <span data-ttu-id="7e3de-126">撤消签出，放弃对已签出文件所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="7e3de-126">Revert the checkout, discarding any changes to the checked-out file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3de-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e3de-127">See Also</span></span>  
 <span data-ttu-id="7e3de-128">[签出文件](../../2014/database-engine/check-out-files.md) </span><span class="sxs-lookup"><span data-stu-id="7e3de-128">[Check Out Files](../../2014/database-engine/check-out-files.md) </span></span>  
 [<span data-ttu-id="7e3de-129">管理签出</span><span class="sxs-lookup"><span data-stu-id="7e3de-129">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
