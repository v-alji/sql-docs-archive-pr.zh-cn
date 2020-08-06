---
title: 将表从一个数据库关系图复制到另一个 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7e90c8f324e80f7c59674def06a77e93a5bf0cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682595"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a><span data-ttu-id="17971-102">将表从一个数据库关系图复制到另一个数据库关系图 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="17971-102">Copy Tables from One Database Diagrams to Another (Visual Database Tools)</span></span>
  <span data-ttu-id="17971-103">可以将表从一个数据库关系图复制到同一数据库的另一个数据库关系图。</span><span class="sxs-lookup"><span data-stu-id="17971-103">You can copy a table from one database diagram to another in the same database.</span></span>  
  
 <span data-ttu-id="17971-104">如果将一个表从一个数据库关系图复制到另一个关系图，则会在第二个关系图中添加对该表的引用。</span><span class="sxs-lookup"><span data-stu-id="17971-104">Copying a table from one database diagram to another diagram adds a reference to the table in the second diagram.</span></span> <span data-ttu-id="17971-105">该表并未在您的数据库中重复。</span><span class="sxs-lookup"><span data-stu-id="17971-105">The table is not duplicated in your database.</span></span> <span data-ttu-id="17971-106">例如，如果将 `authors` 表从一个数据库关系图复制到另一个关系图，则每个关系图都引用数据库中的同一 `authors` 表。</span><span class="sxs-lookup"><span data-stu-id="17971-106">For example, if you copy the `authors` table from one database diagram to another, each diagram references the same `authors` table in the database.</span></span>  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a><span data-ttu-id="17971-107">从另一个数据库关系图复制表</span><span class="sxs-lookup"><span data-stu-id="17971-107">To copy a table from another database diagram</span></span>  
  
1.  <span data-ttu-id="17971-108">确保已连接到要复制其中的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="17971-108">Make sure you are connected to the database whose table you want to copy.</span></span>  
  
2.  <span data-ttu-id="17971-109">打开源数据库关系图和目标数据库关系图，并在源关系图中选择要复制到目标关系图的表。</span><span class="sxs-lookup"><span data-stu-id="17971-109">Open the source and target database diagrams and within the source diagram, select the table that you want to copy to the target diagram.</span></span>  
  
3.  <span data-ttu-id="17971-110">单击工具栏上的“复制”  按钮。</span><span class="sxs-lookup"><span data-stu-id="17971-110">Click the **Copy** button on the toolbar.</span></span> <span data-ttu-id="17971-111">此操作会将所选表的定义放置到剪贴板上。</span><span class="sxs-lookup"><span data-stu-id="17971-111">This action places the selected table definition on the Clipboard.</span></span>  
  
4.  <span data-ttu-id="17971-112">切换到目标关系图。</span><span class="sxs-lookup"><span data-stu-id="17971-112">Switch to the target diagram.</span></span> <span data-ttu-id="17971-113">此关系图必须与源关系图位于同一数据库中。</span><span class="sxs-lookup"><span data-stu-id="17971-113">This diagram must be in the same database as the source diagram.</span></span>  
  
5.  <span data-ttu-id="17971-114">单击工具栏上的“粘贴”  按钮。</span><span class="sxs-lookup"><span data-stu-id="17971-114">Click the **Paste** button on the toolbar.</span></span> <span data-ttu-id="17971-115">剪贴板内容将出现在新的位置，而且在单击其他位置之前保持突出显示状态。</span><span class="sxs-lookup"><span data-stu-id="17971-115">The Clipboard contents appear at the new location and remain highlighted until you click elsewhere.</span></span> <span data-ttu-id="17971-116">如果选定的表与目标关系图中的其他表之间存在关系，则将自动绘制关系线。</span><span class="sxs-lookup"><span data-stu-id="17971-116">If relationships exist between the selected tables and other tables in the target diagram, relationship lines are automatically drawn.</span></span>  
  
 <span data-ttu-id="17971-117">当在任一关系图中编辑该表时，所做更改将同时反映在这两个关系图中。</span><span class="sxs-lookup"><span data-stu-id="17971-117">When you edit the table in either diagram, your changes are reflected in both diagrams.</span></span> <span data-ttu-id="17971-118">同样，在任一关系图中保存表之后，在任一关系图中都不再将该表视为“已修改”。</span><span class="sxs-lookup"><span data-stu-id="17971-118">Similarly, once you save the table in either diagram, the table is no longer considered "modified" in either diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17971-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17971-119">See Also</span></span>  
 <span data-ttu-id="17971-120">[使用数据库关系图 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="17971-120">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="17971-121">向关系图中添加表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="17971-121">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](add-tables-to-diagrams-visual-database-tools.md)  
  
  
