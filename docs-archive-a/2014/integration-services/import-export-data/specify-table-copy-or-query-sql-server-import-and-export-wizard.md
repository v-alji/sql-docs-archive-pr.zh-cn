---
title: 指定表复制或查询（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.specifytablecopyorquery.f1
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a3d1eafb57475ed6a0f9fb20894fcc9718d1f0c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588614"
---
# <a name="specify-table-copy-or-query-sql-server-import-and-export-wizard"></a><span data-ttu-id="0744d-102">指定表复制或查询（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="0744d-102">Specify Table Copy or Query (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="0744d-103">使用 "**指定表复制或查询**" 页可以指定复制数据的方式。</span><span class="sxs-lookup"><span data-stu-id="0744d-103">Use the **Specify Table Copy or Query** page to specify how to copy data.</span></span> <span data-ttu-id="0744d-104">您可以使用图形界面选择所希望复制的现有数据库对象，或使用 Transact-SQL 创建更复杂的查询。</span><span class="sxs-lookup"><span data-stu-id="0744d-104">You can use a graphical interface to select the existing database objects you want to copy, or you can use Transact-SQL to create a more complex query.</span></span>  
  
 <span data-ttu-id="0744d-105">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="0744d-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="0744d-106">若要了解用于启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="0744d-106">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="0744d-107">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="0744d-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="0744d-108">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="0744d-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="0744d-109">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="0744d-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="0744d-110">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="0744d-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0744d-111">选项</span><span class="sxs-lookup"><span data-stu-id="0744d-111">Options</span></span>  
 <span data-ttu-id="0744d-112">**复制一个或多个表或视图的数据**</span><span class="sxs-lookup"><span data-stu-id="0744d-112">**Copy data from one or more tables or views**</span></span>  
 <span data-ttu-id="0744d-113">使用 "**选择源表和视图**" 对话框将选定源表和视图中的字段复制到指定的目标。</span><span class="sxs-lookup"><span data-stu-id="0744d-113">Copy fields from selected source tables and views to the specified destination or destinations by using the **Select Source Tables and Views** dialog box.</span></span> <span data-ttu-id="0744d-114">如果希望在不对记录进行筛选或排序的情况下复制源中的所有数据，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0744d-114">Use this option if you want to copy all data in the source without filtering or ordering records.</span></span>  
  
 <span data-ttu-id="0744d-115">使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口连接到数据源时， **“复制一个或多个表或视图的数据”** 选项可能不可用。</span><span class="sxs-lookup"><span data-stu-id="0744d-115">When you use a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider to connect to your data source, the **Copy data from one or more tables or views** option might not be available.</span></span> <span data-ttu-id="0744d-116">此选项仅对在 ProviderDescriptors.xml 文件中有 ProviderDescription 部分的信息的那些访问接口可用。</span><span class="sxs-lookup"><span data-stu-id="0744d-116">This option is available only for those providers that have a ProviderDescription section in the ProviderDescriptors.xml file.</span></span> <span data-ttu-id="0744d-117">每个 ProviderDescription 部分都包含从相应访问接口检索元数据所需的信息。</span><span class="sxs-lookup"><span data-stu-id="0744d-117">Each ProviderDescription section contains the information that is required to retrieve metadata from the corresponding provider.</span></span> <span data-ttu-id="0744d-118">默认情况下，ProviderDescriptors.xml 文件仅包含以下访问接口的 ProviderDescription 部分：</span><span class="sxs-lookup"><span data-stu-id="0744d-118">By default, the ProviderDescriptors.xml file contains a ProviderDescription section for only the following providers:</span></span>  
  
-   <span data-ttu-id="0744d-119">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="0744d-119">System.Data.SqlClient</span></span>  
  
-   <span data-ttu-id="0744d-120">System.Data.OracleClient</span><span class="sxs-lookup"><span data-stu-id="0744d-120">System.Data.OracleClient</span></span>  
  
-   <span data-ttu-id="0744d-121">System.Data.OleDb</span><span class="sxs-lookup"><span data-stu-id="0744d-121">System.Data.OleDb</span></span>  
  
-   <span data-ttu-id="0744d-122">System.Data.Odbc</span><span class="sxs-lookup"><span data-stu-id="0744d-122">System.Data.Odbc</span></span>  
  
 <span data-ttu-id="0744d-123">若要使**一个或多个表或视图中的数据复制**选项可用于其他提供程序，第三方可以将其自己的 ProviderDescriptor 部分添加到 ProviderDescriptors.xml 文件中。</span><span class="sxs-lookup"><span data-stu-id="0744d-123">To make the **Copy data from one or more tables or views** option available for additional providers, third parties can add their own ProviderDescriptor sections to the ProviderDescriptors.xml file.</span></span> <span data-ttu-id="0744d-124">默认情况下，此文件位于 \<*drive*> ： \Program FILES\MICROSOFT SQL server\100\dts\providerdescriptors 中。</span><span class="sxs-lookup"><span data-stu-id="0744d-124">By default, this file is in \<*drive*>:\Program Files\Microsoft SQL Server\100\DTS\ProviderDescriptors.</span></span> <span data-ttu-id="0744d-125">若要查看 ProviderDescriptor 部分的要求，请参阅 ProviderDescriptors.xsd 架构文件，默认情况下，该文件位于 ProviderDescriptors.xml 文件所在的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0744d-125">To review the requirements for the ProviderDescriptor section, see the ProviderDescriptors.xsd schema file that is, by default, in the same folder as the ProviderDescriptors.xml file.</span></span>  
  
 <span data-ttu-id="0744d-126">**编写查询以指定要传输的数据**</span><span class="sxs-lookup"><span data-stu-id="0744d-126">**Write a query to specify the data to transfer**</span></span>  
 <span data-ttu-id="0744d-127">使用 "**提供源查询**" 对话框生成用于检索行的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="0744d-127">Build SQL statements to retrieve rows by using the **Provide a Source Query** dialog box.</span></span> <span data-ttu-id="0744d-128">如果希望在复制操作中修改或限制源数据，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0744d-128">Use this option if you want to modify or restrict the source data during the copy operation.</span></span> <span data-ttu-id="0744d-129">只有符合选择条件的行才可用于复制。</span><span class="sxs-lookup"><span data-stu-id="0744d-129">Only the rows matching the selection criteria are available for copying.</span></span>  
  
  
