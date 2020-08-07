---
title: 选择目标（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4bf9b717ef9de20d84d32c18eb3caa4c54cad87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588644"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a><span data-ttu-id="dbe16-102">选择目标（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="dbe16-102">Choose a Destination (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="dbe16-103">使用 "**选择目标**" 页可以指定要复制的数据的目标。</span><span class="sxs-lookup"><span data-stu-id="dbe16-103">Use the **Choose a Destination** page to specify the destination of the data that you want to copy.</span></span>  
  
 <span data-ttu-id="dbe16-104">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe16-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="dbe16-105">若要了解用于启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe16-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="dbe16-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="dbe16-106">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="dbe16-107">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="dbe16-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="dbe16-108">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="dbe16-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="dbe16-109">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe16-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="dbe16-110">静态选项</span><span class="sxs-lookup"><span data-stu-id="dbe16-110">Static Options</span></span>  
 <span data-ttu-id="dbe16-111">**目标**</span><span class="sxs-lookup"><span data-stu-id="dbe16-111">**Destination**</span></span>  
 <span data-ttu-id="dbe16-112">选择与目标的数据存储格式相匹配的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="dbe16-112">Choose the data provider that matches the data storage format of the destination.</span></span> <span data-ttu-id="dbe16-113">可用于数据源的访问接口可能不止一个。</span><span class="sxs-lookup"><span data-stu-id="dbe16-113">There may be more than one provider available for your data source.</span></span> <span data-ttu-id="dbe16-114">例如，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、用于 SQL Server 的 .NET Framework 数据提供程序或用于 SQL Server 的 Microsoft OLE DB 提供程序。</span><span class="sxs-lookup"><span data-stu-id="dbe16-114">For example, with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, the .NET Framework Data Provider for SQL Server, or the Microsoft OLE DB Provider for SQL Server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbe16-115">若要将数据保存到 ODBC 目标，请选择用于 ODBC 的 .NET Framework 数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="dbe16-115">To save data to an ODBC destination, select the .NET Framework Data Provider for ODBC.</span></span>  
  
 <span data-ttu-id="dbe16-116">"**数据源**" 属性的选项数量可变，这取决于计算机上安装的提供程序。</span><span class="sxs-lookup"><span data-stu-id="dbe16-116">The **Data Source** property has a variable number of options, which change depending on the providers installed on the computer.</span></span> <span data-ttu-id="dbe16-117">下表列出了一些常用目标的选项。</span><span class="sxs-lookup"><span data-stu-id="dbe16-117">The following tables list the options for some commonly used destinations.</span></span> <span data-ttu-id="dbe16-118">有关其他访问接口的信息，请参阅访问接口特定的文档。</span><span class="sxs-lookup"><span data-stu-id="dbe16-118">For other providers, see the provider-specific documentation.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="dbe16-119">动态选项</span><span class="sxs-lookup"><span data-stu-id="dbe16-119">Dynamic Options</span></span>  
 <span data-ttu-id="dbe16-120">以下部分显示了可用于几种数据源的选项。</span><span class="sxs-lookup"><span data-stu-id="dbe16-120">The following sections show the options available for several data sources.</span></span> <span data-ttu-id="dbe16-121">此处并未列出“目标”下拉列表中的所有可用目标。</span><span class="sxs-lookup"><span data-stu-id="dbe16-121">Not all the destinations that are available in the Destination drop-down are listed here.</span></span>  
  
### <a name="destination--sql-server-native-client-or-microsoft-ole-db-provider-for-sql-server"></a><span data-ttu-id="dbe16-122">目标 = SQL Server Native Client 或 Microsoft OLE DB Provider for SQL Server</span><span class="sxs-lookup"><span data-stu-id="dbe16-122">Destination = SQL Server Native Client or Microsoft OLE DB Provider for SQL Server</span></span>  
 <span data-ttu-id="dbe16-123">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="dbe16-123">**Server name**</span></span>  
 <span data-ttu-id="dbe16-124">键入接收数据的服务器的名称，或者从列表中选择服务器。</span><span class="sxs-lookup"><span data-stu-id="dbe16-124">Type the name of the server to receive the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="dbe16-125">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="dbe16-125">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="dbe16-126">指定包是否应使用 Microsoft Windows 身份验证登录数据库。</span><span class="sxs-lookup"><span data-stu-id="dbe16-126">Specify whether the package should use Microsoft Windows Authentication to log in to the database.</span></span> <span data-ttu-id="dbe16-127">为了实现更好的安全性，建议使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="dbe16-127">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="dbe16-128">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="dbe16-128">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="dbe16-129">指定包是否应使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证登录数据库。</span><span class="sxs-lookup"><span data-stu-id="dbe16-129">Specify whether the package should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to log in to the database.</span></span> <span data-ttu-id="dbe16-130">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，则必须提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="dbe16-130">If you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="dbe16-131">**用户名**</span><span class="sxs-lookup"><span data-stu-id="dbe16-131">**User name**</span></span>  
 <span data-ttu-id="dbe16-132">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，指定数据库连接的用户名。</span><span class="sxs-lookup"><span data-stu-id="dbe16-132">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="dbe16-133">**密码**</span><span class="sxs-lookup"><span data-stu-id="dbe16-133">**Password**</span></span>  
 <span data-ttu-id="dbe16-134">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，提供数据库连接的密码。</span><span class="sxs-lookup"><span data-stu-id="dbe16-134">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="dbe16-135">**Database**</span><span class="sxs-lookup"><span data-stu-id="dbe16-135">**Database**</span></span>  
 <span data-ttu-id="dbe16-136">从的指定实例上的数据库列表中进行选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，或单击 "**新建**" 创建新的数据库。</span><span class="sxs-lookup"><span data-stu-id="dbe16-136">Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or create a new database by clicking **New**.</span></span>  
  
 <span data-ttu-id="dbe16-137">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="dbe16-137">**Refresh**</span></span>  
 <span data-ttu-id="dbe16-138">通过单击“刷新”\*\*\*\*，还原可用数据库的列表。</span><span class="sxs-lookup"><span data-stu-id="dbe16-138">Restore the list of available databases by clicking **Refresh**.</span></span>  
  
 <span data-ttu-id="dbe16-139">**新建**</span><span class="sxs-lookup"><span data-stu-id="dbe16-139">**New**</span></span>  
 <span data-ttu-id="dbe16-140">使用 "**创建数据库**" 对话框创建新的目标数据库。</span><span class="sxs-lookup"><span data-stu-id="dbe16-140">Create a new destination database by using the **Create Database** dialog box.</span></span>  
  
### <a name="destination--flat-file-destination"></a><span data-ttu-id="dbe16-141">目标 = 平面文件目标</span><span class="sxs-lookup"><span data-stu-id="dbe16-141">Destination = Flat File Destination</span></span>  
 <span data-ttu-id="dbe16-142">**文件名**</span><span class="sxs-lookup"><span data-stu-id="dbe16-142">**File name**</span></span>  
 <span data-ttu-id="dbe16-143">指定要存储数据的文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="dbe16-143">Specify the path and file name for the file in which to store the data.</span></span> <span data-ttu-id="dbe16-144">或者，单击 **“浏览”** 定位文件。</span><span class="sxs-lookup"><span data-stu-id="dbe16-144">Or, click **Browse** to locate a file.</span></span>  
  
 <span data-ttu-id="dbe16-145">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="dbe16-145">**Browse**</span></span>  
 <span data-ttu-id="dbe16-146">使用“打开”\*\*\*\* 对话框定位文件。</span><span class="sxs-lookup"><span data-stu-id="dbe16-146">Locate a file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="dbe16-147">**区域设置**</span><span class="sxs-lookup"><span data-stu-id="dbe16-147">**Locale**</span></span>  
 <span data-ttu-id="dbe16-148">指定定义字符排序顺序以及日期和时间格式的区域设置 ID (LCID)。</span><span class="sxs-lookup"><span data-stu-id="dbe16-148">Specify the locale ID (LCID) that defines character sort orders and date and time formatting.</span></span>  
  
 <span data-ttu-id="dbe16-149">**Unicode**</span><span class="sxs-lookup"><span data-stu-id="dbe16-149">**Unicode**</span></span>  
 <span data-ttu-id="dbe16-150">指示是否使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="dbe16-150">Indicate whether to use Unicode.</span></span> <span data-ttu-id="dbe16-151">如果使用 Unicode，则不必指定代码页。</span><span class="sxs-lookup"><span data-stu-id="dbe16-151">If you use Unicode, you do not have to specify a code page.</span></span>  
  
 <span data-ttu-id="dbe16-152">**代码页**</span><span class="sxs-lookup"><span data-stu-id="dbe16-152">**Code page**</span></span>  
 <span data-ttu-id="dbe16-153">指定所需使用的语言的代码页。</span><span class="sxs-lookup"><span data-stu-id="dbe16-153">Specify the code page for the language you want to use.</span></span>  
  
 <span data-ttu-id="dbe16-154">**格式**</span><span class="sxs-lookup"><span data-stu-id="dbe16-154">**Format**</span></span>  
 <span data-ttu-id="dbe16-155">指示是否使用带分隔符、固定宽度或右边未对齐的格式。</span><span class="sxs-lookup"><span data-stu-id="dbe16-155">Indicate whether to use delimited, fixed width, or ragged right formatting.</span></span>  
  
|<span data-ttu-id="dbe16-156">值</span><span class="sxs-lookup"><span data-stu-id="dbe16-156">Value</span></span>|<span data-ttu-id="dbe16-157">说明</span><span class="sxs-lookup"><span data-stu-id="dbe16-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbe16-158">带分隔符</span><span class="sxs-lookup"><span data-stu-id="dbe16-158">Delimited</span></span>|<span data-ttu-id="dbe16-159">各列之间由在 **“列”** 页上指定的分隔符隔开。</span><span class="sxs-lookup"><span data-stu-id="dbe16-159">Columns are separated by a delimiter, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="dbe16-160">固定宽度</span><span class="sxs-lookup"><span data-stu-id="dbe16-160">Fixed width</span></span>|<span data-ttu-id="dbe16-161">列的宽度固定。</span><span class="sxs-lookup"><span data-stu-id="dbe16-161">Columns have a fixed width.</span></span>|  
|<span data-ttu-id="dbe16-162">右边未对齐</span><span class="sxs-lookup"><span data-stu-id="dbe16-162">Ragged right</span></span>|<span data-ttu-id="dbe16-163">在右边未对齐的文件中，除最后一列之外的每一列的宽度都固定，而最后一列由行分隔符进行分隔。</span><span class="sxs-lookup"><span data-stu-id="dbe16-163">Ragged right files are files in which every column has a fixed width, except for the last column, which is delimited by the row delimiter.</span></span>|  
  
 <span data-ttu-id="dbe16-164">**文本限定符**</span><span class="sxs-lookup"><span data-stu-id="dbe16-164">**Text qualifier**</span></span>  
 <span data-ttu-id="dbe16-165">键入要使用的文本限定符。</span><span class="sxs-lookup"><span data-stu-id="dbe16-165">Type the text qualifier to use.</span></span> <span data-ttu-id="dbe16-166">例如，您可以指定每个文本列均包含在引号中。</span><span class="sxs-lookup"><span data-stu-id="dbe16-166">For example, you can specify that each text column be surrounded with quotation marks.</span></span>  
  
 <span data-ttu-id="dbe16-167">**第一个数据行中的列名称**</span><span class="sxs-lookup"><span data-stu-id="dbe16-167">**Column names in first data row**</span></span>  
 <span data-ttu-id="dbe16-168">指示是否希望在第一个数据行中显示列名称。</span><span class="sxs-lookup"><span data-stu-id="dbe16-168">Indicate whether you want to display column names in the first data row.</span></span>  
  
### <a name="destination--microsoft-excel"></a><span data-ttu-id="dbe16-169">目标 = Microsoft Excel</span><span class="sxs-lookup"><span data-stu-id="dbe16-169">Destination = Microsoft Excel</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbe16-170">仅当要连接到使用 Excel 2003 或更早版本的数据源时，才选择 " **Microsoft Excel** "。</span><span class="sxs-lookup"><span data-stu-id="dbe16-170">Select **Microsoft Excel** only if you want to connect to a data source that uses Excel 2003 or earlier.</span></span> <span data-ttu-id="dbe16-171">若要连接到使用 Excel 2007 的数据源，请选择**Microsoft Office 12.0 Access 数据库引擎 OLE DB 提供程序**，单击 "**属性**"，然后在 "**数据链接属性**" 对话框的 "**全部**" 选项卡上，对于 "**扩展属性**"，输入 `Excel 12.0` 。</span><span class="sxs-lookup"><span data-stu-id="dbe16-171">To connect to a data source that uses Excel 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, click **Properties**, and then on the **All** tab of the **Data Link Properties** dialog box, for **Extended Properties**, enter `Excel 12.0`.</span></span>  
  
 <span data-ttu-id="dbe16-172">**Excel 文件路径**</span><span class="sxs-lookup"><span data-stu-id="dbe16-172">**Excel file path**</span></span>  
 <span data-ttu-id="dbe16-173">指定要在其中存储数据的工作簿的路径和文件名 (例如，C:\MyData.xls， \\\Sales\Database\Northwind.xls) 。</span><span class="sxs-lookup"><span data-stu-id="dbe16-173">Specify the path and file name for the workbook in which to store the data (for example, C:\MyData.xls, \\\Sales\Database\Northwind.xls).</span></span> <span data-ttu-id="dbe16-174">或者，单击 **“浏览”** 定位工作簿。</span><span class="sxs-lookup"><span data-stu-id="dbe16-174">Or, click **Browse** to locate a workbook.</span></span>  
  
 <span data-ttu-id="dbe16-175">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="dbe16-175">**Browse**</span></span>  
 <span data-ttu-id="dbe16-176">使用 "**打开**" 对话框定位到 Excel 工作簿。</span><span class="sxs-lookup"><span data-stu-id="dbe16-176">Locate an Excel workbook by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="dbe16-177">**Excel 版本**</span><span class="sxs-lookup"><span data-stu-id="dbe16-177">**Excel version**</span></span>  
 <span data-ttu-id="dbe16-178">选择目标工作簿使用的 Excel 版本。</span><span class="sxs-lookup"><span data-stu-id="dbe16-178">Select the version of Excel that is used by the destination workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbe16-179">将数据导出到 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 目标时，向导将使用“ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel 目标”组件。</span><span class="sxs-lookup"><span data-stu-id="dbe16-179">When you export data to a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] destination, the wizard uses the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel Destination component.</span></span> <span data-ttu-id="dbe16-180">有关某些使用注意事项和已知问题的信息，请参阅[Excel Destination](../data-flow/excel-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe16-180">For information on some usage considerations and known issues, see [Excel Destination](../data-flow/excel-destination.md).</span></span>  
  
### <a name="destination--microsoft-access"></a><span data-ttu-id="dbe16-181">目标 = Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="dbe16-181">Destination = Microsoft Access</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbe16-182">仅当要连接到使用 Access 2003 或更早版本的数据库时，才选择 " **Microsoft Access** "。</span><span class="sxs-lookup"><span data-stu-id="dbe16-182">Select **Microsoft Access** only if you want to connect to a database that uses Access 2003 or earlier.</span></span> <span data-ttu-id="dbe16-183">若要连接到使用 Access 2007 的数据库，请选择 " **Microsoft Office 12.0 访问数据库引擎 OLE DB 提供程序**"。</span><span class="sxs-lookup"><span data-stu-id="dbe16-183">To connect to a database that uses Access 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**.</span></span>  
  
 <span data-ttu-id="dbe16-184">**文件名**</span><span class="sxs-lookup"><span data-stu-id="dbe16-184">**File name**</span></span>  
 <span data-ttu-id="dbe16-185">指定要在其中存储 (数据的数据库文件的路径和文件名，例如 C:\MyData.mdb、 \\ \Sales\Database\Northwind.mdb) 。</span><span class="sxs-lookup"><span data-stu-id="dbe16-185">Specify the path and file name for the database file in which to store the data (for example, C:\MyData.mdb, \\\Sales\Database\Northwind.mdb).</span></span> <span data-ttu-id="dbe16-186">或者，单击 **“浏览”** 定位数据库文件。</span><span class="sxs-lookup"><span data-stu-id="dbe16-186">Or, click **Browse** to locate a database file.</span></span>  
  
 <span data-ttu-id="dbe16-187">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="dbe16-187">**Browse**</span></span>  
 <span data-ttu-id="dbe16-188">使用 "**打开**" 对话框浏览到数据库文件。</span><span class="sxs-lookup"><span data-stu-id="dbe16-188">Browse to the database file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="dbe16-189">**用户名**</span><span class="sxs-lookup"><span data-stu-id="dbe16-189">**User name**</span></span>  
 <span data-ttu-id="dbe16-190">当工作组信息文件与数据库关联时，为数据库连接指定一个有效的用户名。</span><span class="sxs-lookup"><span data-stu-id="dbe16-190">Specify a valid user name for the database connection when a workgroup information file is associated with the database.</span></span>  
  
 <span data-ttu-id="dbe16-191">**密码**</span><span class="sxs-lookup"><span data-stu-id="dbe16-191">**Password**</span></span>  
 <span data-ttu-id="dbe16-192">当工作组信息文件与数据库关联时，为数据库连接提供相应的用户密码。</span><span class="sxs-lookup"><span data-stu-id="dbe16-192">Provide the user's password for the database connection when a workgroup information file is associated with the database.</span></span> <span data-ttu-id="dbe16-193">但是，如果对于所有用户都使用一个密码保护数据库，则必须在 **“数据链接属性”** 对话框（可通过 **“高级”** 按钮访问）中提供此值。</span><span class="sxs-lookup"><span data-stu-id="dbe16-193">However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed from the **Advanced** button.</span></span>  
  
 <span data-ttu-id="dbe16-194">**高级**</span><span class="sxs-lookup"><span data-stu-id="dbe16-194">**Advanced**</span></span>  
 <span data-ttu-id="dbe16-195">通过使用“数据链接属性”\*\*\*\* 对话框指定高级选项，例如数据库密码或非默认工作组信息文件。</span><span class="sxs-lookup"><span data-stu-id="dbe16-195">Specify advanced options, such as the database password or a non-default workgroup information file, by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="dbe16-196">有关 OLE DB 访问接口属性的详细信息，请在 [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553)的“Data Access”（数据访问）部分中进行搜索。</span><span class="sxs-lookup"><span data-stu-id="dbe16-196">For more information about OLE DB provider properties, search in the Data Access section of the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
  
