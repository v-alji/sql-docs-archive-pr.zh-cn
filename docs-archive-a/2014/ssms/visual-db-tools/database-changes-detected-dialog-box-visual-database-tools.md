---
title: “检测到数据库更改”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.schema.databasechangesdetected
- vdtsql.chm:65543
- vdtsql.chm:65554
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91d58e812b93f207d592d245d094b0fbeddcce72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689200"
---
# <a name="database-changes-detected-dialog-box-visual-database-tools"></a><span data-ttu-id="54fd6-102">“检测到数据库更改”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="54fd6-102">Database Changes Detected Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="54fd6-103">如果尝试保存数据库关系图或选定的表，但某些将受保存操作影响的数据库对象对于数据库已经过期，则会显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="54fd6-103">This dialog appears if you attempt to save a database diagram or selected tables but some of the database objects that will be affected by the save action are out of date with the database.</span></span> <span data-ttu-id="54fd6-104">如果接受对话框中显示的更改，则将更新数据库以匹配关系图并改写其他用户所做的更改。</span><span class="sxs-lookup"><span data-stu-id="54fd6-104">Accepting the changes shown in this dialog box updates the database to match your diagram and overwrites other users' changes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54fd6-105">虽然您无法撤消对表或数据库关系图所做的更改，但在保存表或关系图之前，这些更改并不会保存到数据库中。</span><span class="sxs-lookup"><span data-stu-id="54fd6-105">Although you cannot undo changes made to a table or database diagram, the changes are not saved to the database until you save the table or diagram.</span></span> <span data-ttu-id="54fd6-106">通过选择“否”  并关闭所有打开的关系图而不进行保存，即可放弃所有未保存的更改。</span><span class="sxs-lookup"><span data-stu-id="54fd6-106">You can discard any unsaved changes by choosing **No** and closing all open diagrams without saving them.</span></span>  
  
## <a name="options"></a><span data-ttu-id="54fd6-107">选项</span><span class="sxs-lookup"><span data-stu-id="54fd6-107">Options</span></span>  
 <span data-ttu-id="54fd6-108">**检测到差异时警告**</span><span class="sxs-lookup"><span data-stu-id="54fd6-108">**Warn about difference detection**</span></span>  
 <span data-ttu-id="54fd6-109">指定在您下次尝试保存数据库关系图或所选表时是否显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="54fd6-109">Specify whether this dialog box appears the next time you attempt to save a database diagram or selected tables.</span></span> <span data-ttu-id="54fd6-110">选中此项表示在您每次保存对于数据库已过期的关系图或表时，该对话框都仍会显示。</span><span class="sxs-lookup"><span data-stu-id="54fd6-110">Checked means that the dialog box continues to appear each time you save a diagram or table that is out of date with the database.</span></span> <span data-ttu-id="54fd6-111">未选中此项表示该对话框不再显示。</span><span class="sxs-lookup"><span data-stu-id="54fd6-111">Unchecked means that the dialog box does not appear.</span></span> <span data-ttu-id="54fd6-112">默认情况下，此框处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="54fd6-112">By default, this box is checked.</span></span> <span data-ttu-id="54fd6-113">如果取消选中此选项，可以在“选项”  对话框中重新选中它。</span><span class="sxs-lookup"><span data-stu-id="54fd6-113">If you uncheck this option, you can recheck it in the **Options** dialog box.</span></span>  
  
 <span data-ttu-id="54fd6-114">**是**</span><span class="sxs-lookup"><span data-stu-id="54fd6-114">**Yes**</span></span>  
 <span data-ttu-id="54fd6-115">用列表中显示的所有更改更新数据库。</span><span class="sxs-lookup"><span data-stu-id="54fd6-115">Update the database with all the changes shown in the list.</span></span>  
  
 <span data-ttu-id="54fd6-116">**是**</span><span class="sxs-lookup"><span data-stu-id="54fd6-116">**No**</span></span>  
 <span data-ttu-id="54fd6-117">取消保存操作。</span><span class="sxs-lookup"><span data-stu-id="54fd6-117">Cancel the save action.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54fd6-118">若要刷新关系图以匹配数据库，请将其关闭而不保存更改，在服务器资源管理器中右键单击该关系图，再单击“刷新”，然后重新打开该关系图。</span><span class="sxs-lookup"><span data-stu-id="54fd6-118">To refresh your diagram to match the database, close it without saving changes, right-click the diagram in Server Explorer and click Refresh, and then reopen the diagram.</span></span>  
  
 <span data-ttu-id="54fd6-119">**保存文本文件**</span><span class="sxs-lookup"><span data-stu-id="54fd6-119">**Save Text File**</span></span>  
 <span data-ttu-id="54fd6-120">显示“另存为”  对话框，用于为包含数据库更改列表的文本文件指定位置。</span><span class="sxs-lookup"><span data-stu-id="54fd6-120">Display the **Save As** dialog box, letting you specify a location for a text file containing a list of the database changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54fd6-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54fd6-121">See Also</span></span>  
 <span data-ttu-id="54fd6-122">[将数据库关系图与已修改的数据库进行协调 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="54fd6-122">[Reconcile a Database Diagram with a Modified Database &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="54fd6-123">多用户环境 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="54fd6-123">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](multiuser-environments-visual-database-tools.md)  
  
  
