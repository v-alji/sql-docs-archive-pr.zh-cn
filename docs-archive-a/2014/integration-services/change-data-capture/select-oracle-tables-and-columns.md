---
title: 选择 Oracle 表和列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selTabCol
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d51e597f1210643b1543ed981045ade7b2fc2b62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580322"
---
# <a name="select-oracle-tables-and-columns"></a><span data-ttu-id="17028-102">选择 Oracle 表和列</span><span class="sxs-lookup"><span data-stu-id="17028-102">Select Oracle Tables and Columns</span></span>
  <span data-ttu-id="17028-103">使用“选择 Oracle 表和列”页可以从捕获了更改的 Oracle 源数据库选择表。</span><span class="sxs-lookup"><span data-stu-id="17028-103">Use the Select Oracle Tables and Columns page to select the tables from the Oracle source database where changes are captured.</span></span> <span data-ttu-id="17028-104">该页具有以下元素：</span><span class="sxs-lookup"><span data-stu-id="17028-104">This page has the following elements:</span></span>  
  
## <a name="options"></a><span data-ttu-id="17028-105">选项</span><span class="sxs-lookup"><span data-stu-id="17028-105">Options</span></span>  
 <span data-ttu-id="17028-106">**表列表**</span><span class="sxs-lookup"><span data-stu-id="17028-106">**Table list**</span></span>  
 <span data-ttu-id="17028-107">此表列表具有三列：</span><span class="sxs-lookup"><span data-stu-id="17028-107">The table list has three columns:</span></span>  
  
-   <span data-ttu-id="17028-108">**Oracle 表名称**：表的名称，包括表架构。</span><span class="sxs-lookup"><span data-stu-id="17028-108">**Oracle Table Name**: The name of the table, including the table schema.</span></span>  
  
-   <span data-ttu-id="17028-109">**捕获实例**：用于命名特定于实例的变更数据捕获对象的捕获实例的名称。</span><span class="sxs-lookup"><span data-stu-id="17028-109">**Capture Instance**: The name of the capture instance used to name instance-specific change data capture objects.</span></span> <span data-ttu-id="17028-110">捕获实例不能为 NULL。</span><span class="sxs-lookup"><span data-stu-id="17028-110">The capture instance cannot be NULL.</span></span>  
  
     <span data-ttu-id="17028-111">如果未指定，则该名称将从源架构名称加上源表名称中派生而来，格式为 `<schema-name>_<table-name>`。</span><span class="sxs-lookup"><span data-stu-id="17028-111">If not specified, the name is derived from the source schema name plus the source table name in the format `<schema-name>_<table-name>`.</span></span> <span data-ttu-id="17028-112">捕获实例名称不能超过 100 个字符，并且在数据库中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="17028-112">The capture instance name cannot exceed 100 characters and must be unique within the database.</span></span>  
  
     <span data-ttu-id="17028-113">可单击此列的任意单元格对 **capture_instance**进行手动编辑。</span><span class="sxs-lookup"><span data-stu-id="17028-113">You can click in any cell in this column to manually edit the **capture_instance**.</span></span>  
  
-   <span data-ttu-id="17028-114">**安全角色**：用于控制对更改数据的访问的数据库访问控制角色的名称。</span><span class="sxs-lookup"><span data-stu-id="17028-114">**Security Role**: The name of the database gating role used to control access to change data.</span></span>  
  
     <span data-ttu-id="17028-115">可单击此列的任意单元格对 **security_role**进行手动编辑。</span><span class="sxs-lookup"><span data-stu-id="17028-115">You can click in any cell in this column to manually edit the **security_role**.</span></span>  
  
 <span data-ttu-id="17028-116">**添加表**</span><span class="sxs-lookup"><span data-stu-id="17028-116">**Add Tables**</span></span>  
 <span data-ttu-id="17028-117">单击“添加表”  可打开“表选择”对话框，从中你可以[为捕获更改选择 Oracle 表](select-oracle-tables-for-capturing-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="17028-117">Click **Add Tables** to open the Table Selection dialog box where you can [Select Oracle Tables for Capturing Changes](select-oracle-tables-for-capturing-changes.md).</span></span>  
  
 <span data-ttu-id="17028-118">**编辑**</span><span class="sxs-lookup"><span data-stu-id="17028-118">**Edit**</span></span>  
 <span data-ttu-id="17028-119">从该列表中选择一个表，然后选择“编辑”  以便打开该表的“属性”  对话框，从中你可以[对为捕获更改选择的表进行更改](make-changes-to-the-tables-selected-for-capturing-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="17028-119">Select a table from the list and select **Edit** to open the **Properties** dialog box for that table where you can [Make Changes to the Tables Selected for Capturing Changes](make-changes-to-the-tables-selected-for-capturing-changes.md).</span></span>  
  
 <span data-ttu-id="17028-120">**删除**</span><span class="sxs-lookup"><span data-stu-id="17028-120">**Remove**</span></span>  
 <span data-ttu-id="17028-121">从该列表中选择一个表，然后单击“删除”  可从 CDC 实例中删除该表。</span><span class="sxs-lookup"><span data-stu-id="17028-121">Select a table from the list and click **Remove** to remove the table from the CDC instance.</span></span>  
  
 <span data-ttu-id="17028-122">在使用正确的对话框[为捕获更改选择 Oracle 表](select-oracle-tables-for-capturing-changes.md)或[对为捕获更改选择的表进行更改](make-changes-to-the-tables-selected-for-capturing-changes.md)后，单击“下一步”  以[生成和运行补充日志记录脚本](generate-and-run-the-supplemental-logging-script.md)。</span><span class="sxs-lookup"><span data-stu-id="17028-122">After you [Select Oracle Tables for Capturing Changes](select-oracle-tables-for-capturing-changes.md) and/or [Make Changes to the Tables Selected for Capturing Changes](make-changes-to-the-tables-selected-for-capturing-changes.md) using the correct dialog boxes, click **Next** to [Generate and Run the Supplemental Logging Script](generate-and-run-the-supplemental-logging-script.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17028-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17028-123">See Also</span></span>  
 <span data-ttu-id="17028-124">[如何创建 SQL Server 更改数据库实例](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="17028-124">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 <span data-ttu-id="17028-125">[编辑表](edit-tables.md) </span><span class="sxs-lookup"><span data-stu-id="17028-125">[Edit Tables](edit-tables.md) </span></span>  
 <span data-ttu-id="17028-126">[将表添加到 CDC 实例](add-tables-to-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="17028-126">[Add Tables to a CDC Instance](add-tables-to-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="17028-127">编辑表属性</span><span class="sxs-lookup"><span data-stu-id="17028-127">Edit the Table Properties</span></span>](edit-the-table-properties.md)  
  
  
