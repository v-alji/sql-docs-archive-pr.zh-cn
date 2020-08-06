---
title: 选项 (设计器-"表和数据库设计器" 页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Designers.Table_Designer
ms.assetid: b43f4b97-17b9-4004-a824-f77b9e145741
author: stevestein
ms.author: sstein
ms.openlocfilehash: d8a1218b4ea1ae9c6f9cf734bb33a2a4bebcb167
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588801"
---
# <a name="options-designers-table-and-database-designers-page"></a><span data-ttu-id="3f3b0-102">选项 (设计器-"表和数据库设计器" 页) </span><span class="sxs-lookup"><span data-stu-id="3f3b0-102">Options (Designers-Table and Database Designers Page)</span></span>
  <span data-ttu-id="3f3b0-103">使用此页可确定设计器的默认行为。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-103">Use this page to determine the default behavior of the designer.</span></span> <span data-ttu-id="3f3b0-104">若要访问这些设置，请在“工具”  菜单上，单击“选项  ”，展开“设计器”  文件夹，再单击“表设计器”  。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-104">To access the settings, on the **Tools** menu, click **Options**, expand the **Designers** folder, and click **Table Designer**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="3f3b0-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="3f3b0-105">UI element list</span></span>  
 <span data-ttu-id="3f3b0-106">**为表设计器更新重写连接字符串的超时值**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-106">**Override connection string time-out value for table designer updates**</span></span>  
 <span data-ttu-id="3f3b0-107">允许为表设计器的操作设置新的超时值。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-107">Permits a new time-out value to be set for the actions of the table designer.</span></span> <span data-ttu-id="3f3b0-108">这在表设计器影响大型表，需要更多的时间完成表修改时非常有用。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-108">This can be useful when the table designer affects a large table and requires extra time to complete the table modification.</span></span>  
  
 <span data-ttu-id="3f3b0-109">**事务超时时间**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-109">**Transaction time-out after**</span></span>  
 <span data-ttu-id="3f3b0-110">为表设计器设置超时值。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-110">Sets a time-out value for the table designer.</span></span>  
  
 <span data-ttu-id="3f3b0-111">**自动生成更改脚本**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-111">**Auto generate change scripts**</span></span>  
 <span data-ttu-id="3f3b0-112">自动创建脚本，以实现表设计器中定义的更改。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-112">Automatically creates a script to implement the changes defined in the table designer.</span></span>  
  
 <span data-ttu-id="3f3b0-113">**出现空主键时警告**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-113">**Warn on null primary keys**</span></span>  
 <span data-ttu-id="3f3b0-114">如果为主键选择的字段包含 Null 值，则提供警告对话框。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-114">Provides a warning dialog box when a field that is selected for a primary key can contain null values.</span></span>  
  
 <span data-ttu-id="3f3b0-115">**检测到差异时警告**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-115">**Warn about difference detection**</span></span>  
 <span data-ttu-id="3f3b0-116">如果选中此框，在保存更改时将出现一个消息框，其中列出您所做的更改与其他用户所做的更改之间存在的所有冲突。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-116">If you check this box, when you save the changes, a message box will list any conflicts between your changes and changes that were made by another user.</span></span>  
  
 <span data-ttu-id="3f3b0-117">**表受到影响时警告**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-117">**Warn about tables affected**</span></span>  
 <span data-ttu-id="3f3b0-118">提供警告对话框，列出受操作影响的表，并提示确认。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-118">Provides a warning dialog box that lists the tables to be affected by the action and prompts for confirmation.</span></span>  
  
 <span data-ttu-id="3f3b0-119">**阻止保存要求重新创建表的更改**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-119">**Prevent saving changes that require table re-creation**</span></span>  
 <span data-ttu-id="3f3b0-120">禁止用户进行要求重新创建表的更改。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-120">Prevents a user from making changes that require re-creating the table.</span></span> <span data-ttu-id="3f3b0-121">以下操作可能要求重新创建表：</span><span class="sxs-lookup"><span data-stu-id="3f3b0-121">The following actions might require a table to be re-created:</span></span>  
  
-   <span data-ttu-id="3f3b0-122">在表中间添加一个新列</span><span class="sxs-lookup"><span data-stu-id="3f3b0-122">Adding a new column to the middle of the table</span></span>  
  
-   <span data-ttu-id="3f3b0-123">删除列</span><span class="sxs-lookup"><span data-stu-id="3f3b0-123">Dropping a column</span></span>  
  
-   <span data-ttu-id="3f3b0-124">更改列为 Null 性</span><span class="sxs-lookup"><span data-stu-id="3f3b0-124">Changing column nullability</span></span>  
  
-   <span data-ttu-id="3f3b0-125">更改列的顺序</span><span class="sxs-lookup"><span data-stu-id="3f3b0-125">Changing the order of the columns</span></span>  
  
-   <span data-ttu-id="3f3b0-126">更改列的数据类型</span><span class="sxs-lookup"><span data-stu-id="3f3b0-126">Changing the data type of a column</span></span>  
  
 <span data-ttu-id="3f3b0-127">**默认表视图**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-127">**Default table view**</span></span>  
 <span data-ttu-id="3f3b0-128">选择要在设计器中查看表的方式：</span><span class="sxs-lookup"><span data-stu-id="3f3b0-128">Select the way you want to see tables in the designers:</span></span>  
  
-   <span data-ttu-id="3f3b0-129">**Standard**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-129">**Standard**</span></span>  
  
     <span data-ttu-id="3f3b0-130">显示表头、所有列名、数据类型和“允许空值”设置。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-130">Shows the table header, all column names, data types, and the Allow Nulls setting.</span></span>  
  
-   <span data-ttu-id="3f3b0-131">**列名**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-131">**Column Names**</span></span>  
  
     <span data-ttu-id="3f3b0-132">显示列名称。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-132">Shows the column names.</span></span>  
  
-   <span data-ttu-id="3f3b0-133">**Key**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-133">**Key**</span></span>  
  
     <span data-ttu-id="3f3b0-134">显示表头和主键列。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-134">Shows the table header and the primary key columns.</span></span>  
  
-   <span data-ttu-id="3f3b0-135">**仅名称**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-135">**Name Only**</span></span>  
  
     <span data-ttu-id="3f3b0-136">仅显示表头及其名称。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-136">Shows only the table header with it's name.</span></span>  
  
-   <span data-ttu-id="3f3b0-137">**自定义**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-137">**Custom**</span></span>  
  
     <span data-ttu-id="3f3b0-138">允许选择要查看的列。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-138">Allows you to choose which columns to view.</span></span>  
  
 <span data-ttu-id="3f3b0-139">**在新建关系图时启动“添加表”对话框**</span><span class="sxs-lookup"><span data-stu-id="3f3b0-139">**Launch add table dialog on new diagram**</span></span>  
 <span data-ttu-id="3f3b0-140">在打开设计器时自动打开“添加表”  对话框。</span><span class="sxs-lookup"><span data-stu-id="3f3b0-140">Automatically opens the **Add Table** dialog box when the designers open.</span></span>  
  
  
