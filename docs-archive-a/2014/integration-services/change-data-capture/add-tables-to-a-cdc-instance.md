---
title: 将表添加到 CDC 实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- addTabs
ms.assetid: ad260e19-c021-4035-9311-c02fc96ceaea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: edcd84db9e3c464334d407987cb3567f78edd44e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683032"
---
# <a name="add-tables-to-a-cdc-instance"></a><span data-ttu-id="75089-102">将表添加到 CDC 实例</span><span class="sxs-lookup"><span data-stu-id="75089-102">Add Tables to a CDC Instance</span></span>
  <span data-ttu-id="75089-103">使用“表选择”对话框可以将 Oracle 源中的附加表添加到 CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="75089-103">Use the Table Selection dialog box to add additional tables from the Oracle source to the CDC instance.</span></span> <span data-ttu-id="75089-104">选定的表将添加到属性编辑器的 **“表”** 选项卡的列表中。</span><span class="sxs-lookup"><span data-stu-id="75089-104">The tables selected are added to the list in the **Tables** tab of the Properties editor.</span></span>  
  
 <span data-ttu-id="75089-105">默认情况下，此对话框的表的列表中不包含任何表。</span><span class="sxs-lookup"><span data-stu-id="75089-105">By default, no tables are included in the list of tables in this dialog box.</span></span> <span data-ttu-id="75089-106">可以选中“(全选)”  复选框或搜索特定表。</span><span class="sxs-lookup"><span data-stu-id="75089-106">You can select the **(Select All)** check box or search for specific tables.</span></span>  
  
 <span data-ttu-id="75089-107">**搜索特定表**</span><span class="sxs-lookup"><span data-stu-id="75089-107">**To search for specific tables**</span></span>  
 <span data-ttu-id="75089-108">按如下所示输入搜索条件，然后单击“搜索”  ：</span><span class="sxs-lookup"><span data-stu-id="75089-108">Enter search criteria as follows, and then click **Search**:</span></span>  
  
-   <span data-ttu-id="75089-109">**架构**：从列表中选择数据库架构。</span><span class="sxs-lookup"><span data-stu-id="75089-109">**Schema**: Select a database schema from the list.</span></span> <span data-ttu-id="75089-110">只有具有该架构的表才会出现在列表中。</span><span class="sxs-lookup"><span data-stu-id="75089-110">Only tables that have that schema will be included in the list.</span></span>  
  
-   <span data-ttu-id="75089-111">**表名称模式**：输入任意字符串。</span><span class="sxs-lookup"><span data-stu-id="75089-111">**Table Name Pattern**: Enter any string of characters.</span></span> <span data-ttu-id="75089-112">将仅显示包含输入的字符串的表。</span><span class="sxs-lookup"><span data-stu-id="75089-112">Only tables that include the character string entered are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75089-113">您可以在其中一个或全部两个字段中输入条件。</span><span class="sxs-lookup"><span data-stu-id="75089-113">You can enter criteria in one or both of these fields.</span></span>  
  
-   <span data-ttu-id="75089-114">**显示前 1000 个匹配表**：默认情况下选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="75089-114">**Display first 1000 matching tables**: By default this check box is selected.</span></span> <span data-ttu-id="75089-115">它将显示限制为前 1000 个匹配表。</span><span class="sxs-lookup"><span data-stu-id="75089-115">It limits the display to the first 1000 matching tables.</span></span> <span data-ttu-id="75089-116">如果取消选中该复选框，将显示条件相匹配的所有表。</span><span class="sxs-lookup"><span data-stu-id="75089-116">If you clear the check box, all tables that match the criteria are displayed.</span></span> <span data-ttu-id="75089-117">如果有大量的表，则此方法可能需要较长的时间来显示列表。</span><span class="sxs-lookup"><span data-stu-id="75089-117">If there are a large number of tables, it may take a long time to display the list.</span></span>  
  
 <span data-ttu-id="75089-118">**选择要包括在 CDC 实例中的表**</span><span class="sxs-lookup"><span data-stu-id="75089-118">**To select tables to include in the CDC instance**</span></span>  
 <span data-ttu-id="75089-119">单击要包含的任何表旁边的复选框，然后单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="75089-119">Click the check box next to any of the tables you want to include, and then click **Add**.</span></span> <span data-ttu-id="75089-120">相应的表将添加到新建实例向导的 **“选择表和列”** 页的列表中。</span><span class="sxs-lookup"><span data-stu-id="75089-120">The tables are added to the list in the New Instance Wizard **Select Tables and Columns** page.</span></span>  
  
 <span data-ttu-id="75089-121">单击 **“关闭”** 将关闭该对话框并且不添加任何表。</span><span class="sxs-lookup"><span data-stu-id="75089-121">Click **Close** to close the dialog box without adding any tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75089-122">如果您选择包含不支持的数据类型的表，将会看到一条错误消息，并且将不会包含该表。</span><span class="sxs-lookup"><span data-stu-id="75089-122">If you select a table that includes a non-supported data type, you will see an error message and the table will not be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75089-123">您可以在查看器中查看表的列表。</span><span class="sxs-lookup"><span data-stu-id="75089-123">You can view the list of tables in the viewer.</span></span> <span data-ttu-id="75089-124">在使用查看器时，信息是只读的。</span><span class="sxs-lookup"><span data-stu-id="75089-124">When using the viewer the information is read only.</span></span> <span data-ttu-id="75089-125">查看器还在表中包括捕获列的列表。</span><span class="sxs-lookup"><span data-stu-id="75089-125">The viewer also includes a list of the captured columns in the table.</span></span> <span data-ttu-id="75089-126">有关如何访问查看器的信息，请参阅 [How to Manage a CDC Instance](manage-a-cdc-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="75089-126">For information on how to access the viewer, see [How to Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75089-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75089-127">See Also</span></span>  
 <span data-ttu-id="75089-128">[如何编辑 CDC 实例属性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="75089-128">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 <span data-ttu-id="75089-129">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="75089-129">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="75089-130">为捕获更改选择 Oracle 表</span><span class="sxs-lookup"><span data-stu-id="75089-130">Select Oracle Tables for Capturing Changes</span></span>](select-oracle-tables-for-capturing-changes.md)  
  
  
