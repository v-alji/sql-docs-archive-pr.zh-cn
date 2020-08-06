---
title: “属性”窗口 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing properties
- sorting properties [SQL Server]
- Properties window [SQL Server Management Studio]
- modifying properties
ms.assetid: 6a9a1389-df8d-4cfc-928b-eccbf884a22d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 33a48ef65a29823abb2e9757575ed006c309969b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682635"
---
# <a name="properties-window-management-studio"></a><span data-ttu-id="e614a-102">属性窗口 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e614a-102">Properties Window (Management Studio)</span></span>
  <span data-ttu-id="e614a-103">使用此窗口可查看选定元素的属性。</span><span class="sxs-lookup"><span data-stu-id="e614a-103">Use this window to view properties of selected elements.</span></span> <span data-ttu-id="e614a-104">还可以使用“属性”窗口查看文件、项目和解决方案的属性。</span><span class="sxs-lookup"><span data-stu-id="e614a-104">You can also use the Properties window to view file, project, and solution properties.</span></span> <span data-ttu-id="e614a-105">在“视图”  菜单上单击“属性窗口”  ，即可显示“属性”窗口。</span><span class="sxs-lookup"><span data-stu-id="e614a-105">The Properties window is available by clicking **Properties Window** on the **View** menu.</span></span>  
  
 <span data-ttu-id="e614a-106">根据属性需求的不同，“属性”窗口将显示不同类型的编辑字段。</span><span class="sxs-lookup"><span data-stu-id="e614a-106">The Properties window displays different types of editing fields, depending on the needs of a particular property.</span></span> <span data-ttu-id="e614a-107">显示为灰色的属性为只读属性。</span><span class="sxs-lookup"><span data-stu-id="e614a-107">Properties shown in gray are read-only.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e614a-108">选项</span><span class="sxs-lookup"><span data-stu-id="e614a-108">Options</span></span>  
  
|<span data-ttu-id="e614a-109">元素</span><span class="sxs-lookup"><span data-stu-id="e614a-109">Element</span></span>|<span data-ttu-id="e614a-110">说明</span><span class="sxs-lookup"><span data-stu-id="e614a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e614a-111">**对象名称**</span><span class="sxs-lookup"><span data-stu-id="e614a-111">**Object name**</span></span>|<span data-ttu-id="e614a-112">列出当前选择的对象。</span><span class="sxs-lookup"><span data-stu-id="e614a-112">Lists the currently selected object or objects.</span></span> <span data-ttu-id="e614a-113">只有处于活动状态的编辑器或设计器中的对象是可见的。</span><span class="sxs-lookup"><span data-stu-id="e614a-113">Only objects from the active editor or designer are visible.</span></span>|  
|<span data-ttu-id="e614a-114">**按分类顺序**</span><span class="sxs-lookup"><span data-stu-id="e614a-114">**Categorized**</span></span>|<span data-ttu-id="e614a-115">按类别列出所选对象的所有属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="e614a-115">Lists all properties and property values for the selected object, by category.</span></span> <span data-ttu-id="e614a-116">可以将类别折叠起来以减少可见属性的数量。</span><span class="sxs-lookup"><span data-stu-id="e614a-116">You can collapse a category to reduce the number of visible properties.</span></span> <span data-ttu-id="e614a-117">折叠或展开类别时，在类别名称的左侧将显示一个加号 (+) 或减号 (-)。</span><span class="sxs-lookup"><span data-stu-id="e614a-117">When you expand or collapse a category, you see a plus (+) or minus (-) to the left of the category name.</span></span> <span data-ttu-id="e614a-118">类别按字母顺序列出。</span><span class="sxs-lookup"><span data-stu-id="e614a-118">Categories are listed alphabetically.</span></span>|  
|<span data-ttu-id="e614a-119">**字母顺序**</span><span class="sxs-lookup"><span data-stu-id="e614a-119">**Alphabetic**</span></span>|<span data-ttu-id="e614a-120">所选对象的所有设计时属性和事件按字母顺序排列。</span><span class="sxs-lookup"><span data-stu-id="e614a-120">Alphabetically sorts all design-time properties and events for selected objects.</span></span>|  
|<span data-ttu-id="e614a-121">**属性**</span><span class="sxs-lookup"><span data-stu-id="e614a-121">**Properties**</span></span>|<span data-ttu-id="e614a-122">显示对象的属性。</span><span class="sxs-lookup"><span data-stu-id="e614a-122">Displays the properties for an object.</span></span>|  
|<span data-ttu-id="e614a-123">**说明窗格**</span><span class="sxs-lookup"><span data-stu-id="e614a-123">**Description pane**</span></span>|<span data-ttu-id="e614a-124">说明窗格出现在“属性”窗口的底部，可以显示属性的类型和简短说明。</span><span class="sxs-lookup"><span data-stu-id="e614a-124">The description pane appears at the bottom of the Properties window and shows the property type and a short description of the property.</span></span> <span data-ttu-id="e614a-125">可以使用快捷菜单上的“说明”  命令打开或关闭属性的说明。</span><span class="sxs-lookup"><span data-stu-id="e614a-125">You can turn the description of the property off and on using the **Description** command on the shortcut menu.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e614a-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e614a-126">See Also</span></span>  
 [<span data-ttu-id="e614a-127">常规用户界面元素</span><span class="sxs-lookup"><span data-stu-id="e614a-127">General User Interface Elements</span></span>](general-user-interface-elements.md)  
  
  
