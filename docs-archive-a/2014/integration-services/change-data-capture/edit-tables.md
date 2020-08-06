---
title: 编辑表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8e8058a0c3e8b81814283f055e4c4ac2b08dd2fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577781"
---
# <a name="edit-tables"></a><span data-ttu-id="5be85-102">编辑表</span><span class="sxs-lookup"><span data-stu-id="5be85-102">Edit Tables</span></span>
  <span data-ttu-id="5be85-103">使用 **“表”** 选项卡可对您从 Oracle 源数据库中选择的表和列进行更改。</span><span class="sxs-lookup"><span data-stu-id="5be85-103">Use the **Tables** tab to make changes to the tables and columns that you selected from the Oracle source database.</span></span> <span data-ttu-id="5be85-104">该选项卡具有以下元素：</span><span class="sxs-lookup"><span data-stu-id="5be85-104">This tab has the following elements:</span></span>  
  
 <span data-ttu-id="5be85-105">**表列表**</span><span class="sxs-lookup"><span data-stu-id="5be85-105">**Table list**</span></span>  
 <span data-ttu-id="5be85-106">此表列表具有三列：</span><span class="sxs-lookup"><span data-stu-id="5be85-106">The table list has three columns:</span></span>  
  
-   <span data-ttu-id="5be85-107">**Oracle 表名称**：表的名称，包括表架构。</span><span class="sxs-lookup"><span data-stu-id="5be85-107">**Oracle Table Name**: The name of the table, including the table schema.</span></span>  
  
-   <span data-ttu-id="5be85-108">**捕获实例**：用于命名特定于实例的变更数据捕获对象的捕获实例的名称。</span><span class="sxs-lookup"><span data-stu-id="5be85-108">**Capture Instance**: The name of the capture instance used to name instance-specific change data capture objects.</span></span> <span data-ttu-id="5be85-109">捕获实例不能为 NULL。</span><span class="sxs-lookup"><span data-stu-id="5be85-109">The capture instance cannot be NULL.</span></span> <span data-ttu-id="5be85-110">如果未指定，则该名称将从源架构名称加上源表名称中派生而来，格式为 `<schema-name>_<table-name>.` 。捕获实例名称不能超过 100 个字符，并且在数据库中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="5be85-110">If not specified, the name is derived from the source schema name plus the source table name in the format `<schema-name>_<table-name>.` The capture instance name cannot exceed 100 characters and must be unique within the database.</span></span> <span data-ttu-id="5be85-111">可单击此列的任意单元格对 **capture_instance**进行手动编辑。</span><span class="sxs-lookup"><span data-stu-id="5be85-111">You can click in any cell in this column to manually edit the **capture_instance**.</span></span>  
  
-   <span data-ttu-id="5be85-112">**安全角色**：用于获取对更改数据的访问权限的数据库角色的名称。</span><span class="sxs-lookup"><span data-stu-id="5be85-112">**Security Role**: The name of the database role used to gain access to change data.</span></span> <span data-ttu-id="5be85-113">可单击此列的任意单元格对 **security_role**进行手动编辑。</span><span class="sxs-lookup"><span data-stu-id="5be85-113">You can click in any cell in this column to manually edit the **security_role**.</span></span>  
  
 <span data-ttu-id="5be85-114">**添加表**</span><span class="sxs-lookup"><span data-stu-id="5be85-114">**Add Tables**</span></span>  
 <span data-ttu-id="5be85-115">单击“添加表”  可打开“表选择”对话框，从中可以[将表添加到 CDC 实例](add-tables-to-a-cdc-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="5be85-115">Click **Add Tables** to open the Table Selection dialog box where you can [Add Tables to a CDC Instance](add-tables-to-a-cdc-instance.md).</span></span> <span data-ttu-id="5be85-116">首次访问 Oracle 数据库时，您必须 [Connect to Oracle](connect-to-oracle.md)。</span><span class="sxs-lookup"><span data-stu-id="5be85-116">The first time this session that you access the Oracle database, you must [Connect to Oracle](connect-to-oracle.md).</span></span>  
  
 <span data-ttu-id="5be85-117">**编辑**</span><span class="sxs-lookup"><span data-stu-id="5be85-117">**Edit**</span></span>  
 <span data-ttu-id="5be85-118">从该列表中选择一个表，然后选择“编辑”  以便打开该表的“属性”  对话框，从中可以[编辑表格属性](edit-the-table-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5be85-118">Select a table from the list and select **Edit** to open the **Properties** dialog box for that table where you can [Edit the Table Properties](edit-the-table-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5be85-119">您不能编辑已具有镜像表的表的类型映射。</span><span class="sxs-lookup"><span data-stu-id="5be85-119">You cannot edit type mapping for tables that already have mirror tables.</span></span> <span data-ttu-id="5be85-120">只能对新表执行此操作。</span><span class="sxs-lookup"><span data-stu-id="5be85-120">You can do this for new tables only.</span></span>  
  
 <span data-ttu-id="5be85-121">**删除**</span><span class="sxs-lookup"><span data-stu-id="5be85-121">**Remove**</span></span>  
 <span data-ttu-id="5be85-122">从该列表中选择一个表，然后单击“删除”  可从 CDC 实例中删除该表。</span><span class="sxs-lookup"><span data-stu-id="5be85-122">Select a table from the list and click **Remove** to remove the table from the CDC instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be85-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5be85-123">See Also</span></span>  
 <span data-ttu-id="5be85-124">[如何编辑 CDC 实例属性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5be85-124">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="5be85-125">选择 Oracle 表和列</span><span class="sxs-lookup"><span data-stu-id="5be85-125">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
