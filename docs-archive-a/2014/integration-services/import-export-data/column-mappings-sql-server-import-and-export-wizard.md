---
title: 列映射（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7994de1292677421447d441c1ac5aeb2b6fbc618
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588638"
---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a><span data-ttu-id="d4b77-102">列映射（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="d4b77-102">Column Mappings (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="d4b77-103">使用 "**列映射**" 对话框可以编辑转换参数。</span><span class="sxs-lookup"><span data-stu-id="d4b77-103">Use the **Column Mappings** dialog box to edit transformation parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d4b77-104">如果选中了“表复制”选项，则不必复制表中的所有列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-104">You do not have to copy all the columns in a table when you select the Table Copy option.</span></span> <span data-ttu-id="d4b77-105">**\<ignore>** 对于要跳过的列，请在此对话框的 "**目标**" 列中选择。</span><span class="sxs-lookup"><span data-stu-id="d4b77-105">Select **\<ignore>** in the **Destination** column of this dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="d4b77-106">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b77-106">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="d4b77-107">若要了解用于启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b77-107">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="d4b77-108">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="d4b77-108">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="d4b77-109">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="d4b77-109">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="d4b77-110">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="d4b77-110">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="d4b77-111">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b77-111">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d4b77-112">选项</span><span class="sxs-lookup"><span data-stu-id="d4b77-112">Options</span></span>  
 <span data-ttu-id="d4b77-113">**数据源**</span><span class="sxs-lookup"><span data-stu-id="d4b77-113">**Source**</span></span>  
 <span data-ttu-id="d4b77-114">标识所选的源表、视图或查询。</span><span class="sxs-lookup"><span data-stu-id="d4b77-114">Identifies the selected source table, view, or query.</span></span>  
  
 <span data-ttu-id="d4b77-115">**目标**</span><span class="sxs-lookup"><span data-stu-id="d4b77-115">**Destination**</span></span>  
 <span data-ttu-id="d4b77-116">标识所选的目标表、视图或查询。</span><span class="sxs-lookup"><span data-stu-id="d4b77-116">Identifies the selected destination table, view, or query.</span></span>  
  
 <span data-ttu-id="d4b77-117">**创建目标表/文件**</span><span class="sxs-lookup"><span data-stu-id="d4b77-117">**Create destination table/file**</span></span>  
 <span data-ttu-id="d4b77-118">指定如果目标表不存在是否创建目标表。</span><span class="sxs-lookup"><span data-stu-id="d4b77-118">Specify whether to create the destination table if it does not already exist.</span></span>  
  
 <span data-ttu-id="d4b77-119">**删除目标表/文件中的行**</span><span class="sxs-lookup"><span data-stu-id="d4b77-119">**Delete rows in destination table/file**</span></span>  
 <span data-ttu-id="d4b77-120">指定在加载新数据之前是否清除现有表的数据。</span><span class="sxs-lookup"><span data-stu-id="d4b77-120">Specify whether to clear the data from an existing table before loading new data.</span></span>  
  
 <span data-ttu-id="d4b77-121">**向目标表/文件中追加行**</span><span class="sxs-lookup"><span data-stu-id="d4b77-121">**Append rows to destination table/file**</span></span>  
 <span data-ttu-id="d4b77-122">指定是否将新数据追加到现有表的已存在数据中。</span><span class="sxs-lookup"><span data-stu-id="d4b77-122">Specify whether to append the new data to the data already present in an existing table.</span></span>  
  
 <span data-ttu-id="d4b77-123">**编辑 SQL**</span><span class="sxs-lookup"><span data-stu-id="d4b77-123">**Edit SQL**</span></span>  
 <span data-ttu-id="d4b77-124">使用 "**创建表 SQL 语句**" 对话框中的默认语句，或根据您的目的修改它。</span><span class="sxs-lookup"><span data-stu-id="d4b77-124">Use the default statement in the **Create Table SQL Statement** dialog box, or modify it for your purposes.</span></span> <span data-ttu-id="d4b77-125">如果要修改此语句，还必须对表映射进行相关更改。</span><span class="sxs-lookup"><span data-stu-id="d4b77-125">If you modify this statement, you must also make associated changes to table mapping.</span></span>  
  
 <span data-ttu-id="d4b77-126">**删除并重新创建目标表**</span><span class="sxs-lookup"><span data-stu-id="d4b77-126">**Drop and re-create destination table**</span></span>  
 <span data-ttu-id="d4b77-127">选择此选项可以覆盖目标表。</span><span class="sxs-lookup"><span data-stu-id="d4b77-127">Choose this option to overwrite the destination table.</span></span> <span data-ttu-id="d4b77-128">只有在使用该向导创建目标表时，该选项才可用。</span><span class="sxs-lookup"><span data-stu-id="d4b77-128">This option is only available when you use the wizard to create the destination table.</span></span> <span data-ttu-id="d4b77-129">如果保存的是向导创建的包，则只可以删除并重新创建目标表，然后再次运行该包。</span><span class="sxs-lookup"><span data-stu-id="d4b77-129">The destination table is only dropped and re-created if you save the package that the wizard creates, and then run the package again.</span></span>  
  
 <span data-ttu-id="d4b77-130">**启用标识插入**</span><span class="sxs-lookup"><span data-stu-id="d4b77-130">**Enable identity insert**</span></span>  
 <span data-ttu-id="d4b77-131">选择此选项可以将源数据中的现有标识值插入到目标表中的标识列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-131">Choose this option to allow existing identity values in the source data to be inserted into an identity column in the destination table.</span></span> <span data-ttu-id="d4b77-132">默认情况下，不允许对目标标识列执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d4b77-132">By default, the destination identity column does not allow this.</span></span>  
  
 <span data-ttu-id="d4b77-133">**映射**</span><span class="sxs-lookup"><span data-stu-id="d4b77-133">**Mappings**</span></span>  
 <span data-ttu-id="d4b77-134">显示数据源映射中的每个列如何映射到目标中列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-134">Displays how each column in the data source maps to a column in the destination.</span></span>  
  
 <span data-ttu-id="d4b77-135">此列表包含以下列：</span><span class="sxs-lookup"><span data-stu-id="d4b77-135">This list has the following columns:</span></span>  
  
 <span data-ttu-id="d4b77-136">**数据源**</span><span class="sxs-lookup"><span data-stu-id="d4b77-136">**Source**</span></span>  
 <span data-ttu-id="d4b77-137">查看可以为其设置转换参数的各个源列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-137">View each source column for which you can set transformation parameters.</span></span>  
  
 <span data-ttu-id="d4b77-138">**目标**</span><span class="sxs-lookup"><span data-stu-id="d4b77-138">**Destination**</span></span>  
 <span data-ttu-id="d4b77-139">指定在复制操作期间是否忽略列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-139">Specify whether you want to ignore a column during the copy operation.</span></span> <span data-ttu-id="d4b77-140">**\<ignore>** 对于要跳过的列，请在此列中进行选择，以便只复制列的子集。</span><span class="sxs-lookup"><span data-stu-id="d4b77-140">You can copy only a subset of columns by selecting **\<ignore>** in this column for columns that you want to skip.</span></span> <span data-ttu-id="d4b77-141">在映射列之前，必须忽略所有不会被映射的列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-141">Before you map columns, you must ignore all columns that will not be mapped.</span></span>  
  
 <span data-ttu-id="d4b77-142">类型</span><span class="sxs-lookup"><span data-stu-id="d4b77-142">**Type**</span></span>  
 <span data-ttu-id="d4b77-143">为列选择数据类型。</span><span class="sxs-lookup"><span data-stu-id="d4b77-143">Select a data type for the column.</span></span>  
  
 <span data-ttu-id="d4b77-144">**可以为 Null**</span><span class="sxs-lookup"><span data-stu-id="d4b77-144">**Nullable**</span></span>  
 <span data-ttu-id="d4b77-145">指定列是否允许 Null 值。</span><span class="sxs-lookup"><span data-stu-id="d4b77-145">Specify whether a column will allow a null value.</span></span>  
  
 <span data-ttu-id="d4b77-146">**大小**</span><span class="sxs-lookup"><span data-stu-id="d4b77-146">**Size**</span></span>  
 <span data-ttu-id="d4b77-147">指定列中的字符数。</span><span class="sxs-lookup"><span data-stu-id="d4b77-147">Specify the number of characters in the column.</span></span>  
  
 <span data-ttu-id="d4b77-148">**精度**</span><span class="sxs-lookup"><span data-stu-id="d4b77-148">**Precision**</span></span>  
 <span data-ttu-id="d4b77-149">指定所显示数据的精度（指数字的位数）。</span><span class="sxs-lookup"><span data-stu-id="d4b77-149">Specify the precision of displayed data, referring to the number of digits.</span></span>  
  
 <span data-ttu-id="d4b77-150">**缩放**</span><span class="sxs-lookup"><span data-stu-id="d4b77-150">**Scale**</span></span>  
 <span data-ttu-id="d4b77-151">指定所显示数据的小数位数（指小数点后的位数）。</span><span class="sxs-lookup"><span data-stu-id="d4b77-151">Specify the scale of displayed data, referring to the number of decimal places.</span></span>  
  
  
