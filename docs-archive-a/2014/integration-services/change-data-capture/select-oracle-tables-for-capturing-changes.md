---
title: 为捕获更改选择 Oracle 表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selOraTabDia
ms.assetid: 2e295dc8-999d-4c4d-96cc-1519674b47a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e9064789dce83ff7d3917ed026c861743142e048
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691329"
---
# <a name="select-oracle-tables-for-capturing-changes"></a><span data-ttu-id="1482c-102">为捕获更改选择 Oracle 表</span><span class="sxs-lookup"><span data-stu-id="1482c-102">Select Oracle Tables for Capturing Changes</span></span>
  <span data-ttu-id="1482c-103">使用此对话框可选择在 CDC 实例中包含的表。</span><span class="sxs-lookup"><span data-stu-id="1482c-103">Use this dialog box to select the tables that are included in the CDC instance.</span></span> <span data-ttu-id="1482c-104">所选表将添加到新建实例向导的 **“选择表和列”** 页的列表中。</span><span class="sxs-lookup"><span data-stu-id="1482c-104">The tables selected are added to the list in the **Select Tables and Columns** page of the New Instance wizard.</span></span> <span data-ttu-id="1482c-105">可以在此对话框中执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="1482c-105">You can do the following in this dialog box.</span></span>  
  
 <span data-ttu-id="1482c-106">默认情况下，此对话框的表的列表中不包含任何表。</span><span class="sxs-lookup"><span data-stu-id="1482c-106">By default, no tables are included in the list of tables in this dialog box.</span></span> <span data-ttu-id="1482c-107">您可以选中复选框列顶部的复选框，以便选择所有表或搜索特定表。</span><span class="sxs-lookup"><span data-stu-id="1482c-107">You can select the check box at the top of the check box column to select all of the tables or search for specific tables.</span></span>  
  
 <span data-ttu-id="1482c-108">**搜索特定表**</span><span class="sxs-lookup"><span data-stu-id="1482c-108">**To search for specific tables**</span></span>  
 <span data-ttu-id="1482c-109">按如下所示输入搜索条件，然后单击“搜索”  ：</span><span class="sxs-lookup"><span data-stu-id="1482c-109">Enter search criteria as follows, and then click **Search**:</span></span>  
  
-   <span data-ttu-id="1482c-110">**架构**：从列表中选择数据库架构。</span><span class="sxs-lookup"><span data-stu-id="1482c-110">**Schema**: Select a database schema from the list.</span></span> <span data-ttu-id="1482c-111">只有具有该架构的表才会出现在列表中。</span><span class="sxs-lookup"><span data-stu-id="1482c-111">Only tables that have that schema will be included in the list.</span></span>  
  
-   <span data-ttu-id="1482c-112">**表名称模式**：输入任意字符串。</span><span class="sxs-lookup"><span data-stu-id="1482c-112">**Table Name Pattern**: Enter any string of characters.</span></span> <span data-ttu-id="1482c-113">将仅显示包含输入的字符串的表。</span><span class="sxs-lookup"><span data-stu-id="1482c-113">Only tables that include the character string entered are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1482c-114">您可以在其中一个或全部两个字段中输入条件。</span><span class="sxs-lookup"><span data-stu-id="1482c-114">You can enter criteria in one or both of these fields.</span></span>  
  
-   <span data-ttu-id="1482c-115">**显示前 1000 个匹配表**：默认情况下选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="1482c-115">**Display first 1000 matching tables**: By default this check box is selected.</span></span> <span data-ttu-id="1482c-116">它将显示限制为前 1000 个匹配表。</span><span class="sxs-lookup"><span data-stu-id="1482c-116">It limits the display to the first 1000 matching tables.</span></span> <span data-ttu-id="1482c-117">如果取消选中该复选框，将显示条件相匹配的所有表。</span><span class="sxs-lookup"><span data-stu-id="1482c-117">If you clear the check box, all tables that match the criteria are displayed.</span></span> <span data-ttu-id="1482c-118">如果有大量的表，则此方法可能需要较长的时间来显示列表。</span><span class="sxs-lookup"><span data-stu-id="1482c-118">If there are a large number of tables, it may take a long time to display the list.</span></span>  
  
 <span data-ttu-id="1482c-119">**选择要包括在 CDC 实例中的表**</span><span class="sxs-lookup"><span data-stu-id="1482c-119">**To select tables to include in the CDC instance**</span></span>  
 <span data-ttu-id="1482c-120">单击要包含的任何表旁边的复选框，然后单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="1482c-120">Click the check box next to any of the tables you want to include, and then click **Add**.</span></span> <span data-ttu-id="1482c-121">相应的表将添加到新建实例向导的 **“选择表和列”** 页的列表中。</span><span class="sxs-lookup"><span data-stu-id="1482c-121">The tables are added to the list in the New Instance Wizard **Select Tables and Columns** page.</span></span>  
  
 <span data-ttu-id="1482c-122">单击 **“关闭”** 将关闭该对话框并且不再添加任何表。</span><span class="sxs-lookup"><span data-stu-id="1482c-122">Click **Close** to close the dialog box without adding any additional tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1482c-123">如果您选择包含不支持的数据类型的表，将会看到一条错误消息，并且将不会包含该表。</span><span class="sxs-lookup"><span data-stu-id="1482c-123">If you select a table that includes a non-supported data type, you will see an error message and the table will not be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1482c-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1482c-124">See Also</span></span>  
 <span data-ttu-id="1482c-125">[如何创建 SQL Server 更改数据库实例](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="1482c-125">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="1482c-126">选择 Oracle 表和列</span><span class="sxs-lookup"><span data-stu-id="1482c-126">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
