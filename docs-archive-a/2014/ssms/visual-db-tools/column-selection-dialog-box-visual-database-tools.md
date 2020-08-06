---
title: “列选择”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.columnselection
- vdtsql.chm:65548
ms.assetid: 479bae2c-fee0-4215-b424-1ab779a7e5ca
author: stevestein
ms.author: sstein
ms.openlocfilehash: da3effa33704b796dc2597512be7780594706423
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682616"
---
# <a name="column-selection-dialog-box-visual-database-tools"></a><span data-ttu-id="9b4f0-102">“列选择”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b4f0-102">Column Selection Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="9b4f0-103">使用此对话框可以在数据库关系图中更改表的“自定义”视图。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-103">Lets you change the Custom view for tables in the database diagram.</span></span> <span data-ttu-id="9b4f0-104">“自定义”视图仅显示由用户标识的列属性。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-104">Custom view shows only the column properties identified by the user.</span></span>  
  
 <span data-ttu-id="9b4f0-105">右键单击一个表并从快捷菜单中选择“修改自定义视图”  后，将显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-105">This dialog box appears when you right-click a table and then choose **Modify Custom View** from the shortcut menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9b4f0-106">选项</span><span class="sxs-lookup"><span data-stu-id="9b4f0-106">Options</span></span>  
 <span data-ttu-id="9b4f0-107">**可用列**</span><span class="sxs-lookup"><span data-stu-id="9b4f0-107">**Available columns**</span></span>  
 <span data-ttu-id="9b4f0-108">列出所选数据库表中的全部现有列。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-108">Lists all columns existing in the selected database table.</span></span> <span data-ttu-id="9b4f0-109">在此列出的列取决于数据库表的属性和数据库的类型。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-109">The columns listed here depend on the properties of the database table and the type of database.</span></span> <span data-ttu-id="9b4f0-110">突出显示所需的列，再使用箭头按钮，可以将这些列移入“选定的列”  框。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-110">Highlight the desired column and use the arrow buttons to move the columns to the **Selected columns** box.</span></span>  
  
 <span data-ttu-id="9b4f0-111">**选定的列**</span><span class="sxs-lookup"><span data-stu-id="9b4f0-111">**Selected columns**</span></span>  
 <span data-ttu-id="9b4f0-112">显示当前为“自定义”视图定义的列属性。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-112">Displays the column properties currently defined for the Custom view.</span></span> <span data-ttu-id="9b4f0-113">使用箭头按钮可以将列属性添加到“选定的列”列表中或从该列表中移除列属性。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-113">Use the arrow buttons to add and remove column properties to the Selected Columns list.</span></span>  
  
 <span data-ttu-id="9b4f0-114">**箭头控件**</span><span class="sxs-lookup"><span data-stu-id="9b4f0-114">**Arrow controls**</span></span>  
 <span data-ttu-id="9b4f0-115">使用向上和向下箭头按钮可以在“选定的列”  列表中上下移动突出显示的列。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-115">Use the up and down arrow buttons to move highlighted columns up or down in the **Selected columns** list.</span></span>  
  
 <span data-ttu-id="9b4f0-116">使用 > 箭头和 >> 箭头可以向自定义视图中添加一个或所有属性。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-116">Use the > and >> arrows to add one or all of the properties to the custom view.</span></span>  
  
 <span data-ttu-id="9b4f0-117">使用 < 箭头和 << 箭头可以从自定义视图中删除一个或所有属性。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-117">Use the < and << arrows to remove one or all of the properties from the custom view.</span></span>  
  
 <span data-ttu-id="9b4f0-118">**按默认值另存**</span><span class="sxs-lookup"><span data-stu-id="9b4f0-118">**Save as default**</span></span>  
 <span data-ttu-id="9b4f0-119">用此对话框中所选的列替换默认的“自定义”视图。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-119">Replaces the default Custom view with the columns selected in this dialog box.</span></span> <span data-ttu-id="9b4f0-120">如果未选择此项，则该对话框中所选的列只应用于数据库关系图中选定的表。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-120">If not selected, the column selection specified in the dialog box will be applied only to the selected table in the database diagram.</span></span>  
  
 <span data-ttu-id="9b4f0-121">**确定**</span><span class="sxs-lookup"><span data-stu-id="9b4f0-121">**OK**</span></span>  
 <span data-ttu-id="9b4f0-122">保存“自定义”视图。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-122">Saves the Custom view.</span></span>  
  
 <span data-ttu-id="9b4f0-123">**取消**</span><span class="sxs-lookup"><span data-stu-id="9b4f0-123">**Cancel**</span></span>  
 <span data-ttu-id="9b4f0-124">取消对“自定义”视图的修改。</span><span class="sxs-lookup"><span data-stu-id="9b4f0-124">Cancels the modification of Custom view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b4f0-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b4f0-125">See Also</span></span>  
 <span data-ttu-id="9b4f0-126">[使用数据库关系图 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9b4f0-126">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="9b4f0-127">自定义关系图中显示的信息量 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b4f0-127">Customize the Amount of Information Displayed in Diagrams &#40;Visual Database Tools&#41;</span></span>](customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md)  
  
  
