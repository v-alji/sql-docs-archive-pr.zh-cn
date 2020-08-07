---
title: 运行 SQL Server 导入和导出向导 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 008c541b1f1a295057b0ee7cc384982627b9689a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588615"
---
# <a name="run-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="31818-102">运行 SQL Server 导入和导出向导</span><span class="sxs-lookup"><span data-stu-id="31818-102">Run the SQL Server Import and Export Wizard</span></span>
  <span data-ttu-id="31818-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导为在数据源之间复制数据和构造基本包提供了一种最为简单的方法。</span><span class="sxs-lookup"><span data-stu-id="31818-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard provides the simplest method of copying data between data sources and of constructing basic packages.</span></span> <span data-ttu-id="31818-104">有关该向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="31818-104">For more information about the wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="31818-105">有关演示如何使用 SQL Server 导入和导出向导创建将 SQL Server 数据库中的数据导出到 Microsoft Excel 电子表格的包的视频，请参阅将[SQL Server 数据导出到 Excel (SQL Server 视频) ](https://go.microsoft.com/fwlink/?LinkId=131024)。</span><span class="sxs-lookup"><span data-stu-id="31818-105">For a video that demonstrates how to use the SQL Server Import and Export Wizard to create a package that exports data from a SQL Server database to a Microsoft Excel spreadsheet, see [Exporting SQL Server Data to Excel (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131024).</span></span>  
  
### <a name="to-start-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="31818-106">启动 SQL Server 导入和导出向导</span><span class="sxs-lookup"><span data-stu-id="31818-106">To start the SQL Server Import and Export Wizard</span></span>  
  
-   <span data-ttu-id="31818-107">在 "**开始**" 菜单上，指向 "**所有程序**"，指向 "**Microsoft SQL Server** "，然后单击 "**导入和导出数据**"。</span><span class="sxs-lookup"><span data-stu-id="31818-107">On the **Start** menu, point to **All Programs**, point to**Microsoft SQL Server** , and then click **Import and Export Data**.</span></span>  
  
     <span data-ttu-id="31818-108">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="31818-108">-or-</span></span>  
  
     <span data-ttu-id="31818-109">在中 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，右键单击 " **SSIS 包**" 文件夹，然后单击 " **SSISImport" 和 "导出向导**"。</span><span class="sxs-lookup"><span data-stu-id="31818-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **SSIS Packages** folder, and then click **SSISImport and Export Wizard**.</span></span>  
  
     <span data-ttu-id="31818-110">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="31818-110">-or-</span></span>  
  
     <span data-ttu-id="31818-111">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 "**项目**" 菜单上，单击 " **SSISImport" 和 "导出向导**"。</span><span class="sxs-lookup"><span data-stu-id="31818-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Project** menu, click **SSISImport and Export Wizard**.</span></span>  
  
     <span data-ttu-id="31818-112">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="31818-112">-or-</span></span>  
  
     <span data-ttu-id="31818-113">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务器类型，展开 "数据库"，右键单击某个数据库，指向 "**任务**"，然后单击 "**导入数据**" 或 "**导出数据**"。</span><span class="sxs-lookup"><span data-stu-id="31818-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] server type, expand Databases, right-click a database, point to **Tasks**, and then click **Import Data** or **Export data**.</span></span>  
  
     <span data-ttu-id="31818-114">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="31818-114">-or-</span></span>  
  
     <span data-ttu-id="31818-115">在命令提示符窗口中运行 DTSWizard.exe（位于 C:\Program Files\Microsoft SQL Server\100\DTS\Binn）。</span><span class="sxs-lookup"><span data-stu-id="31818-115">In a command prompt window, run DTSWizard.exe, located in C:\Program Files\Microsoft SQL Server\100\DTS\Binn.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31818-116">在 64 位计算机上，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会安装 64 位版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导 (DTSWizard.exe)。</span><span class="sxs-lookup"><span data-stu-id="31818-116">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs the 64-bit version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard (DTSWizard.exe).</span></span> <span data-ttu-id="31818-117">但是，有些数据源（如 Access 或 Excel）只提供 32 位提供程序。</span><span class="sxs-lookup"><span data-stu-id="31818-117">However, some data sources, such as Access or Excel, only have a 32-bit provider available.</span></span> <span data-ttu-id="31818-118">若要使用这些数据源，您可能需要安装并运行 32 位版本的向导。</span><span class="sxs-lookup"><span data-stu-id="31818-118">To work with these data sources, you might have to install and run the 32-bit version of the wizard.</span></span> <span data-ttu-id="31818-119">若要安装 32 位版本的向导，必须在安装过程中选择“客户端工具”或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31818-119">To install the 32-bit version of the wizard, select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
### <a name="to-import-or-export-data-by-using-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="31818-120">使用 SQL Server 导入和导出向导导入或导出数据</span><span class="sxs-lookup"><span data-stu-id="31818-120">To import or export data by using the SQL Server Import and Export Wizard</span></span>  
  
1.  <span data-ttu-id="31818-121">启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导。</span><span class="sxs-lookup"><span data-stu-id="31818-121">Start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard.</span></span>  
  
2.  <span data-ttu-id="31818-122">在相应的向导页面上，选择数据源和数据目标。</span><span class="sxs-lookup"><span data-stu-id="31818-122">On the corresponding wizard pages, select a data source and a data destination.</span></span>  
  
     <span data-ttu-id="31818-123">可用数据源包括 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口、OLE DB 访问接口、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 提供程序、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 提供程序、Microsoft Office Excel、Microsoft Office Access 和平面文件源。</span><span class="sxs-lookup"><span data-stu-id="31818-123">The available data sources include [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers, OLE DB providers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client providers, [!INCLUDE[vstecado](../../includes/vstecado-md.md)] providers, Microsoft Office Excel, Microsoft Office Access, and the Flat File source.</span></span> <span data-ttu-id="31818-124">根据源的不同，需要设置身份验证模式、服务器名称、数据库名称和文件格式之类的选项。</span><span class="sxs-lookup"><span data-stu-id="31818-124">Depending on the source, you set options such as the authentication mode, server name, database name, and file format.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31818-125">[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Oracle 不支持 Oracle BLOB、CLOB、NCLOB、BFILE 和 UROWID 数据类型。</span><span class="sxs-lookup"><span data-stu-id="31818-125">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Oracle does not support the Oracle BLOB, CLOB, NCLOB, BFILE, and UROWID data types.</span></span> <span data-ttu-id="31818-126">因此，OLE DB 源无法从包含具有上述数据类型的列的表中提取数据。</span><span class="sxs-lookup"><span data-stu-id="31818-126">Therefore, the OLE DB source cannot extract data from tables that contain columns with these data types.</span></span>  
  
     <span data-ttu-id="31818-127">可用数据目标包括 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]数据访问接口、OLE DB 访问接口、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、Excel、Access 和平面文件目标。</span><span class="sxs-lookup"><span data-stu-id="31818-127">The available data destinations include [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers, OLE DB providers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, Excel, Access, and the Flat File destination.</span></span>  
  
3.  <span data-ttu-id="31818-128">为选定的目标类型设置选项。</span><span class="sxs-lookup"><span data-stu-id="31818-128">Set the options for the type of destination that you selected.</span></span>  
  
     <span data-ttu-id="31818-129">如果目标为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库，则可以指定下列内容：</span><span class="sxs-lookup"><span data-stu-id="31818-129">If the destination is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database you can specify the following:</span></span>  
  
    -   <span data-ttu-id="31818-130">指示是否创建新的数据库并设置数据库属性。</span><span class="sxs-lookup"><span data-stu-id="31818-130">Indicate whether to create a new database and set the database properties.</span></span> <span data-ttu-id="31818-131">下列属性无法配置，因此向导使用指定的默认值：</span><span class="sxs-lookup"><span data-stu-id="31818-131">The following properties cannot be configured and the wizard uses the specified default values:</span></span>  
  
        |<span data-ttu-id="31818-132">properties</span><span class="sxs-lookup"><span data-stu-id="31818-132">Property</span></span>|<span data-ttu-id="31818-133">值</span><span class="sxs-lookup"><span data-stu-id="31818-133">Value</span></span>|  
        |--------------|-----------|  
        |<span data-ttu-id="31818-134">排序规则</span><span class="sxs-lookup"><span data-stu-id="31818-134">Collation</span></span>|<span data-ttu-id="31818-135">Latin1_General_CS_AS_KS_WS</span><span class="sxs-lookup"><span data-stu-id="31818-135">Latin1_General_CS_AS_KS_WS</span></span>|  
        |<span data-ttu-id="31818-136">恢复模式</span><span class="sxs-lookup"><span data-stu-id="31818-136">Recovery model</span></span>|<span data-ttu-id="31818-137">完全</span><span class="sxs-lookup"><span data-stu-id="31818-137">Full</span></span>|  
        |<span data-ttu-id="31818-138">使用全文索引</span><span class="sxs-lookup"><span data-stu-id="31818-138">Use full-text indexing</span></span>|<span data-ttu-id="31818-139">True</span><span class="sxs-lookup"><span data-stu-id="31818-139">True</span></span>|  
  
    -   <span data-ttu-id="31818-140">选择是复制表或视图中的数据，还是复制查询结果。</span><span class="sxs-lookup"><span data-stu-id="31818-140">Select whether to copy data from tables or views, or to copy query results.</span></span>  
  
         <span data-ttu-id="31818-141">如果要查询源数据并复制结果，则可以构造 Transact-SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="31818-141">If you want to query the source data and copy the results, you can construct a Transact-SQL query.</span></span> <span data-ttu-id="31818-142">可以手动输入 Transact-SQL 查询，也可以使用保存到文件的查询。</span><span class="sxs-lookup"><span data-stu-id="31818-142">You can enter the Transact-SQL query manually or use a query saved to a file.</span></span> <span data-ttu-id="31818-143">向导包含用于查找文件的浏览功能，当您选定文件后，向导会自动打开文件，并将其内容粘贴到向导页中。</span><span class="sxs-lookup"><span data-stu-id="31818-143">The wizard includes a browse feature for locating the file, and the wizard automatically opens the file and pastes its content into the wizard page when you select the file.</span></span>  
  
         <span data-ttu-id="31818-144">如果源是 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 提供程序，则还可以使用该选项复制查询结果，并提供 DBCommand 字符串作为查询。</span><span class="sxs-lookup"><span data-stu-id="31818-144">If the source is an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider you can also use the option to copy query results, providing the DBCommand string as the query.</span></span>  
  
         <span data-ttu-id="31818-145">如果源数据是视图，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导自动将该视图转换为目标中的表。</span><span class="sxs-lookup"><span data-stu-id="31818-145">If the source data is a view, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard automatically converts the view to a table in the destination.</span></span>  
  
    -   <span data-ttu-id="31818-146">指示是否删除目标表然后重新创建，以及是否启用标识插入。</span><span class="sxs-lookup"><span data-stu-id="31818-146">Indicate whether the destination table is dropped and then re-created, and whether to enable identity inserts.</span></span>  
  
    -   <span data-ttu-id="31818-147">指示在现有目标表中是删除行，还是追加行。</span><span class="sxs-lookup"><span data-stu-id="31818-147">Indicate whether to delete rows or append rows in an existing destination table.</span></span> <span data-ttu-id="31818-148">如果该表不存在，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导会自动创建该表。</span><span class="sxs-lookup"><span data-stu-id="31818-148">If the table does not exist, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard automatically creates it.</span></span>  
  
     <span data-ttu-id="31818-149">如果目标是平面文件目标，则可以指定下列内容：</span><span class="sxs-lookup"><span data-stu-id="31818-149">If the destination is a Flat File destination you can specify the following:</span></span>  
  
    -   <span data-ttu-id="31818-150">指定目标文件中的行分隔符。</span><span class="sxs-lookup"><span data-stu-id="31818-150">Specify the row delimiter in the destination file.</span></span>  
  
    -   <span data-ttu-id="31818-151">指定目标文件中的列分隔符。</span><span class="sxs-lookup"><span data-stu-id="31818-151">Specify the column delimiter in the destination file.</span></span>  
  
4.  <span data-ttu-id="31818-152">（可选）选择一个表并更改源列和目标列之间的映射，或更改目标列的元数据：</span><span class="sxs-lookup"><span data-stu-id="31818-152">(Optional) Select one table and change the mappings between source and destination columns, or change the metadata of destination columns:</span></span>  
  
    -   <span data-ttu-id="31818-153">将源列映射到其他目标列。</span><span class="sxs-lookup"><span data-stu-id="31818-153">Map source columns to different destination columns.</span></span>  
  
    -   <span data-ttu-id="31818-154">更改目标列中的数据类型。</span><span class="sxs-lookup"><span data-stu-id="31818-154">Change the data type in the destination column.</span></span>  
  
    -   <span data-ttu-id="31818-155">设置字符数据类型的列的长度。</span><span class="sxs-lookup"><span data-stu-id="31818-155">Set the length of columns with character data types.</span></span>  
  
    -   <span data-ttu-id="31818-156">设置数值数据类型的列的精度和小数位数。</span><span class="sxs-lookup"><span data-stu-id="31818-156">Set the precision and scale of columns with numeric data types.</span></span>  
  
    -   <span data-ttu-id="31818-157">指定该列可否包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="31818-157">Specify whether the column can contain null values.</span></span>  
  
5.  <span data-ttu-id="31818-158">（可选）选择多个表并更新应用于这些表的元数据和选项：</span><span class="sxs-lookup"><span data-stu-id="31818-158">(Optional) Select multiple tables, and update the metadata and options to apply to those tables:</span></span>  
  
    -   <span data-ttu-id="31818-159">选择现有的目标架构或提供要为其分配表的新架构。</span><span class="sxs-lookup"><span data-stu-id="31818-159">Select an existing destination schema or provide a new schema to which to assign tables.</span></span>  
  
    -   <span data-ttu-id="31818-160">指定是否在目标表中启用标识插入。</span><span class="sxs-lookup"><span data-stu-id="31818-160">Specify whether to enable identity inserts in destination tables.</span></span>  
  
    -   <span data-ttu-id="31818-161">指定是否删除并重新创建目标表。</span><span class="sxs-lookup"><span data-stu-id="31818-161">Specify whether to drop and re-create destination tables.</span></span>  
  
    -   <span data-ttu-id="31818-162">指定是否截断现有的目标表。</span><span class="sxs-lookup"><span data-stu-id="31818-162">Specify whether to truncate existing destination tables.</span></span>  
  
6.  <span data-ttu-id="31818-163">保存并运行包。</span><span class="sxs-lookup"><span data-stu-id="31818-163">Save and run a package.</span></span>  
  
     <span data-ttu-id="31818-164">如果向导从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或命令提示符启动，则包可以立即运行。</span><span class="sxs-lookup"><span data-stu-id="31818-164">If the wizard is started from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the command prompt, the package can run immediately.</span></span> <span data-ttu-id="31818-165">您可以选择将包保存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**数据库或文件系统。</span><span class="sxs-lookup"><span data-stu-id="31818-165">You can optionally save the package to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** database or to the file system.</span></span> <span data-ttu-id="31818-166">有关**msdb**数据库的详细信息，请参阅[&#40;SSIS 服务&#41;包管理](../service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="31818-166">For more information about the **msdb** database, see [Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md).</span></span>  
  
     <span data-ttu-id="31818-167">保存包时，可以设置包保护级别，如果该保护级别使用密码，请提供密码。</span><span class="sxs-lookup"><span data-stu-id="31818-167">When you save the package you can set the package protection level, and if the protection level uses a password, provide the password.</span></span> <span data-ttu-id="31818-168">有关包保护级别的详细信息，请参阅[对包中敏感数据的访问控制](../security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="31818-168">For more information about package protection levels, see [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
     <span data-ttu-id="31818-169">如果向导从 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 项目启动，则无法从向导运行包。</span><span class="sxs-lookup"><span data-stu-id="31818-169">If the wizard is started from an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you cannot run the package from the wizard.</span></span> <span data-ttu-id="31818-170">相反，该包将添加到启动该向导的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目中。</span><span class="sxs-lookup"><span data-stu-id="31818-170">Instead, the package is added to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project from which you started the wizard.</span></span> <span data-ttu-id="31818-171">然后您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中运行包。</span><span class="sxs-lookup"><span data-stu-id="31818-171">You can then run the package in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31818-172">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中，未提供用来保存该向导所创建的包的选项。</span><span class="sxs-lookup"><span data-stu-id="31818-172">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31818-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31818-173">See Also</span></span>  
 <span data-ttu-id="31818-174">[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="31818-174">[SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md) </span></span>  
 [<span data-ttu-id="31818-175">在 SQL Server Data Tools 中创建包</span><span class="sxs-lookup"><span data-stu-id="31818-175">Create Packages in SQL Server Data Tools</span></span>](../create-packages-in-sql-server-data-tools.md)  
  
  
