---
title: 选择源表和视图（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e18f9f34db7965033d4e1e62964060a26404a45e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588617"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a><span data-ttu-id="ded99-102">选择源表和源视图（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="ded99-102">Select Source Tables and Views (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="ded99-103">使用 "**选择源表和视图**" 页可以指定要从数据源复制到目标的表和视图。</span><span class="sxs-lookup"><span data-stu-id="ded99-103">Use the **Select Source Tables and Views** page to specify the tables and views to be copied from the data source to the destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ded99-104">如果选中了“表复制”选项，则不必复制表中的所有列。</span><span class="sxs-lookup"><span data-stu-id="ded99-104">You do not have to copy all the columns in a table when you select the Table Copy option.</span></span> <span data-ttu-id="ded99-105">选择目标表后，请单击 "编辑映射" 以显示 "**列映射**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="ded99-105">After selecting a destination table, click Edit Mappings to display the **Column Mappings** dialog box.</span></span> <span data-ttu-id="ded99-106">**\<ignore>** 对于要跳过的列，请在 "**列映射**" 对话框的 "**目标**" 列中选择。</span><span class="sxs-lookup"><span data-stu-id="ded99-106">Select **\<ignore>** in the **Destination** column of the **Column Mappings** dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="ded99-107">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="ded99-107">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="ded99-108">若要了解启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="ded99-108">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="ded99-109">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="ded99-109">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="ded99-110">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="ded99-110">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="ded99-111">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="ded99-111">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="ded99-112">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="ded99-112">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ded99-113">选项</span><span class="sxs-lookup"><span data-stu-id="ded99-113">Options</span></span>  
  
### <a name="tables-and-views-list"></a><span data-ttu-id="ded99-114">表和视图列表</span><span class="sxs-lookup"><span data-stu-id="ded99-114">Tables and views List</span></span>  
 <span data-ttu-id="ded99-115">**数据源**</span><span class="sxs-lookup"><span data-stu-id="ded99-115">**Source**</span></span>  
 <span data-ttu-id="ded99-116">使用这些复选框，可以从可用表和视图的列表中进行选择，以复制到目标。</span><span class="sxs-lookup"><span data-stu-id="ded99-116">Using the check boxes, select from the list of available tables and views to copy to the destination.</span></span> <span data-ttu-id="ded99-117">如果选择了源表或源视图并且不执行其他操作，将从源不加更改地复制架构和数据。</span><span class="sxs-lookup"><span data-stu-id="ded99-117">If you select a source table or view and perform no other action, the schema and data from the source are copied without changes.</span></span>  
  
 <span data-ttu-id="ded99-118">**目标**</span><span class="sxs-lookup"><span data-stu-id="ded99-118">**Destination**</span></span>  
 <span data-ttu-id="ded99-119">从列表中为每个源表选择一个目标表。</span><span class="sxs-lookup"><span data-stu-id="ded99-119">Select a destination table from the list for each source table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ded99-120">如果此时在向导中暂停操作，并使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或其他工具在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中创建目标表，新表不会立即出现在可用目标表的列表中。</span><span class="sxs-lookup"><span data-stu-id="ded99-120">If you pause at this point in the wizard to create a destination table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or another tool, the new table is not immediately visible in the list of available destination tables.</span></span> <span data-ttu-id="ded99-121">若要刷新目标表的列表，请将两页返回到 "**选择目标**" 页，重新选择目标数据库，然后再次前进到 "**选择源表和视图**"。</span><span class="sxs-lookup"><span data-stu-id="ded99-121">To refresh the list of destination tables, step back two pages to the **Choose a Destination** page, re-select the destination database, then step forward again to the **Select Source Tables and Views**.</span></span>  
  
### <a name="other-options"></a><span data-ttu-id="ded99-122">其他选项</span><span class="sxs-lookup"><span data-stu-id="ded99-122">Other Options</span></span>  
 <span data-ttu-id="ded99-123">**编辑映射**</span><span class="sxs-lookup"><span data-stu-id="ded99-123">**Edit mappings**</span></span>  
 <span data-ttu-id="ded99-124">使用 "**列映射**" 对话框可以指定要接收源数据的目标列。</span><span class="sxs-lookup"><span data-stu-id="ded99-124">Use the **Column Mappings** dialog box to specify destination columns to receive the source data.</span></span> <span data-ttu-id="ded99-125">您可以通过 \<ignore> 在 "**列映射**" 对话框的 "**目标**" 列中选择要跳过的列来只复制列的子集。</span><span class="sxs-lookup"><span data-stu-id="ded99-125">You can copy only a subset of columns by selecting \<ignore> in the **Destination** column of the **Column Mappings** dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="ded99-126">**预览**</span><span class="sxs-lookup"><span data-stu-id="ded99-126">**Preview**</span></span>  
 <span data-ttu-id="ded99-127">在执行导入或导出之前，在 "**预览数据**" 对话框中预览源数据以对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="ded99-127">Preview source data in the **Preview Data** dialog box to verify it before performing the import or export.</span></span> <span data-ttu-id="ded99-128">"**预览数据**" 对话框最多可显示200行数据。</span><span class="sxs-lookup"><span data-stu-id="ded99-128">The **Preview Data** dialog box displays up to 200 rows of data.</span></span>  
  
 <span data-ttu-id="ded99-129">预览数据后，可能需要更改为数据源和目标选定的选项。</span><span class="sxs-lookup"><span data-stu-id="ded99-129">After previewing the data, you might want to change the options that you have selected for the data source and destination.</span></span> <span data-ttu-id="ded99-130">若要进行这些更改，请在 **“选择源表和源视图”** 页，单击 **“后退”** 返回到可以更改选项的上一页。</span><span class="sxs-lookup"><span data-stu-id="ded99-130">To make these changes, on the **Select Source Tables and Views** page, click **Back** to return to previous pages where you can change your selections.</span></span>  
  
  
