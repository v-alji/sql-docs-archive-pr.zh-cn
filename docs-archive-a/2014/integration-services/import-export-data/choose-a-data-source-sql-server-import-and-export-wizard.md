---
title: 选择数据源（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 246c3b03bfefad83cbfc1d0110e1fd4cf0cedf7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588650"
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a><span data-ttu-id="c7a88-102">选择数据源（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="c7a88-102">Choose a Data Source (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="c7a88-103">使用 "**选择数据源**" 页可以指定要复制的数据的源。</span><span class="sxs-lookup"><span data-stu-id="c7a88-103">Use the **Choose a Data Source** page to specify the source of the data that you want to copy.</span></span>  
  
 <span data-ttu-id="c7a88-104">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a88-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="c7a88-105">若要了解启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a88-105">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="c7a88-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="c7a88-106">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="c7a88-107">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="c7a88-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="c7a88-108">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="c7a88-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="c7a88-109">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a88-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c7a88-110">选项</span><span class="sxs-lookup"><span data-stu-id="c7a88-110">Options</span></span>  
 <span data-ttu-id="c7a88-111">**数据源**</span><span class="sxs-lookup"><span data-stu-id="c7a88-111">**Data Source**</span></span>  
 <span data-ttu-id="c7a88-112">选择与源的数据存储格式相匹配的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="c7a88-112">Choose the data provider that matches the data storage format of the source.</span></span> <span data-ttu-id="c7a88-113">可用于数据源的访问接口可能不止一个。</span><span class="sxs-lookup"><span data-stu-id="c7a88-113">There may be more than one provider available for your data source.</span></span> <span data-ttu-id="c7a88-114">例如，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、用于 SQL Server 的 .NET Framework 数据提供程序或用于 SQL Server 的 Microsoft OLE DB 提供程序。</span><span class="sxs-lookup"><span data-stu-id="c7a88-114">For example, with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, the .NET Framework Data Provider for SQL Server, or the Microsoft OLE DB Provider for SQL Server.</span></span>  
  
 <span data-ttu-id="c7a88-115">根据计算机上安装的访问接口的不同， **“数据源”** 属性的选项数也会不同。</span><span class="sxs-lookup"><span data-stu-id="c7a88-115">The **Data Source** property has a variable number of options, which depend on the providers installed on the computer.</span></span> <span data-ttu-id="c7a88-116">下表列出了一些常用目标的选项。</span><span class="sxs-lookup"><span data-stu-id="c7a88-116">The following tables list the options for some frequently used destinations.</span></span> <span data-ttu-id="c7a88-117">有关其他访问接口的信息，请参阅访问接口特定的文档。</span><span class="sxs-lookup"><span data-stu-id="c7a88-117">For other providers, see the provider-specific documentation.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="c7a88-118">动态选项</span><span class="sxs-lookup"><span data-stu-id="c7a88-118">Dynamic Options</span></span>  
 <span data-ttu-id="c7a88-119">以下部分显示了可用于几种数据源的选项。</span><span class="sxs-lookup"><span data-stu-id="c7a88-119">The following sections show the options available for several data sources.</span></span> <span data-ttu-id="c7a88-120">此处并未列出“数据源”下拉列表中的所有可用数据源。</span><span class="sxs-lookup"><span data-stu-id="c7a88-120">Not all the data sources that are available in the Data Source drop-down are listed here.</span></span>  
  
### <a name="data-source--sql-server-native-client-and-microsoft-ole-db-provider-for-sql-server"></a><span data-ttu-id="c7a88-121">数据源 = SQL Server Native Client 和 Microsoft OLE DB Provider for SQL Server</span><span class="sxs-lookup"><span data-stu-id="c7a88-121">Data Source = SQL Server Native Client and Microsoft OLE DB Provider for SQL Server</span></span>  
 <span data-ttu-id="c7a88-122">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="c7a88-122">**Server name**</span></span>  
 <span data-ttu-id="c7a88-123">键入包含相应数据的服务器的名称，或者从列表中选择服务器。</span><span class="sxs-lookup"><span data-stu-id="c7a88-123">Type the name of the server that contains the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="c7a88-124">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="c7a88-124">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="c7a88-125">指定包是否应使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 身份验证登录数据库。</span><span class="sxs-lookup"><span data-stu-id="c7a88-125">Specify whether the package should use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication to log in to the database.</span></span> <span data-ttu-id="c7a88-126">为了实现更好的安全性，建议使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c7a88-126">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="c7a88-127">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="c7a88-127">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="c7a88-128">指定包是否应使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证登录数据库。</span><span class="sxs-lookup"><span data-stu-id="c7a88-128">Specify whether the package should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to log in to the database.</span></span> <span data-ttu-id="c7a88-129">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，则必须提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="c7a88-129">If you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="c7a88-130">**用户名**</span><span class="sxs-lookup"><span data-stu-id="c7a88-130">**User name**</span></span>  
 <span data-ttu-id="c7a88-131">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，指定数据库连接的用户名。</span><span class="sxs-lookup"><span data-stu-id="c7a88-131">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="c7a88-132">**密码**</span><span class="sxs-lookup"><span data-stu-id="c7a88-132">**Password**</span></span>  
 <span data-ttu-id="c7a88-133">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，提供数据库连接的密码。</span><span class="sxs-lookup"><span data-stu-id="c7a88-133">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="c7a88-134">**Database**</span><span class="sxs-lookup"><span data-stu-id="c7a88-134">**Database**</span></span>  
 <span data-ttu-id="c7a88-135">从指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的数据库列表中选择。</span><span class="sxs-lookup"><span data-stu-id="c7a88-135">Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c7a88-136">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="c7a88-136">**Refresh**</span></span>  
 <span data-ttu-id="c7a88-137">通过单击“刷新”\*\*\*\*，还原可用数据库的列表。</span><span class="sxs-lookup"><span data-stu-id="c7a88-137">Restore the list of available databases by clicking **Refresh**.</span></span>  
  
### <a name="data-source--net-framework-data-provider-for-sql-server"></a><span data-ttu-id="c7a88-138">数据源 = .NET Framework Data Provider for SQL Server</span><span class="sxs-lookup"><span data-stu-id="c7a88-138">Data Source = .NET Framework Data Provider for SQL Server</span></span>  
 <span data-ttu-id="c7a88-139">此页显示用于 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据访问接口的选项列表，按字母顺序排列。</span><span class="sxs-lookup"><span data-stu-id="c7a88-139">This page presents an alphabetical list of options for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c7a88-140">下表列出了最重要的选项。</span><span class="sxs-lookup"><span data-stu-id="c7a88-140">The most important options are listed in the following table.</span></span>  
  
 <span data-ttu-id="c7a88-141">**数据源**</span><span class="sxs-lookup"><span data-stu-id="c7a88-141">**Data Source**</span></span>  
 <span data-ttu-id="c7a88-142">键入包含相应数据的服务器的名称，或者从列表中选择服务器。</span><span class="sxs-lookup"><span data-stu-id="c7a88-142">Type the name of the server that contains the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="c7a88-143">**初始目录**</span><span class="sxs-lookup"><span data-stu-id="c7a88-143">**Initial Catalog**</span></span>  
 <span data-ttu-id="c7a88-144">键入源数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="c7a88-144">Type the name of the source database.</span></span>  
  
 <span data-ttu-id="c7a88-145">**Integrated Security**</span><span class="sxs-lookup"><span data-stu-id="c7a88-145">**Integrated Security**</span></span>  
 <span data-ttu-id="c7a88-146">若要使用 Windows 集成身份验证进行连接，请指定 `True`（建议）；若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接，请指定 `False`。</span><span class="sxs-lookup"><span data-stu-id="c7a88-146">Specify `True` to connect by using Windows integrated authentication, which is recommended, or `False` to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="c7a88-147">如果指定 `False`，则必须输入用户 ID 和密码。</span><span class="sxs-lookup"><span data-stu-id="c7a88-147">If you specify `False`, you must enter a user ID and password.</span></span> <span data-ttu-id="c7a88-148">默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="c7a88-148">The default value is `False`.</span></span>  
  
 <span data-ttu-id="c7a88-149">**用户 ID**</span><span class="sxs-lookup"><span data-stu-id="c7a88-149">**User ID**</span></span>  
 <span data-ttu-id="c7a88-150">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，指定数据库连接的用户名。</span><span class="sxs-lookup"><span data-stu-id="c7a88-150">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="c7a88-151">**密码**</span><span class="sxs-lookup"><span data-stu-id="c7a88-151">**Password**</span></span>  
 <span data-ttu-id="c7a88-152">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，提供数据库连接的密码。</span><span class="sxs-lookup"><span data-stu-id="c7a88-152">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="c7a88-153">选择此访问接口时所列出的其他选项并不是成功连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源数据库所必需。</span><span class="sxs-lookup"><span data-stu-id="c7a88-153">The additional options that are listed when you select this provider are not required to connect successfully to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source database.</span></span> <span data-ttu-id="c7a88-154">有关这些附加选项的说明，请参阅 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 软件开发包中有关用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口的文档。</span><span class="sxs-lookup"><span data-stu-id="c7a88-154">For a description of these additional options, see the documentation for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Software Development Kit.</span></span>  
  
### <a name="data-source--microsoft-excel"></a><span data-ttu-id="c7a88-155">数据源 = Microsoft Excel</span><span class="sxs-lookup"><span data-stu-id="c7a88-155">Data Source = Microsoft Excel</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7a88-156">仅当要连接到使用 Excel 2003 或更早版本的数据源时，才选择 " **Microsoft Excel** "。</span><span class="sxs-lookup"><span data-stu-id="c7a88-156">Select **Microsoft Excel** only if you want to connect to a data source that uses Excel 2003 or earlier.</span></span> <span data-ttu-id="c7a88-157">若要连接到使用 Excel 2007 的数据源，请选择**Microsoft Office 12.0 Access 数据库引擎 OLE DB 提供程序**，单击 "**属性**"，然后在 "**数据链接属性**" 对话框的 "**全部**" 选项卡上，输入 `Excel 12.0` 作为 "**扩展属性**" 的值。</span><span class="sxs-lookup"><span data-stu-id="c7a88-157">To connect to a data source that uses Excel 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, click **Properties**, and then on the **All** tab of the **Data Link Properties** dialog box, enter `Excel 12.0` as the value for **Extended Properties**.</span></span>  
  
 <span data-ttu-id="c7a88-158">**Excel 文件路径**</span><span class="sxs-lookup"><span data-stu-id="c7a88-158">**Excel file path**</span></span>  
 <span data-ttu-id="c7a88-159">指定要从其中导入数据的电子表格的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="c7a88-159">Specify the path and file name for the spreadsheet from which to import the data.</span></span> <span data-ttu-id="c7a88-160">例如， **C:\MyData.xls \\\Sales\Database\Northwind.xls**。</span><span class="sxs-lookup"><span data-stu-id="c7a88-160">For example, **C:\MyData.xls, \\\Sales\Database\Northwind.xls**.</span></span> <span data-ttu-id="c7a88-161">或单击 **“浏览”**。</span><span class="sxs-lookup"><span data-stu-id="c7a88-161">Or, click **Browse**.</span></span>  
  
 <span data-ttu-id="c7a88-162">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="c7a88-162">**Browse**</span></span>  
 <span data-ttu-id="c7a88-163">通过使用“打开”\*\*\*\* 对话框定位电子表格。</span><span class="sxs-lookup"><span data-stu-id="c7a88-163">Locate the spreadsheet by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="c7a88-164">**Excel 版本**</span><span class="sxs-lookup"><span data-stu-id="c7a88-164">**Excel version**</span></span>  
 <span data-ttu-id="c7a88-165">选择存储源数据的 Excel 的版本。</span><span class="sxs-lookup"><span data-stu-id="c7a88-165">Select the version of Excel that the source data is stored in.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7a88-166">从 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 源导入数据时，向导使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel 源组件。</span><span class="sxs-lookup"><span data-stu-id="c7a88-166">When you import data from a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] source, the wizard uses the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel Source component.</span></span> <span data-ttu-id="c7a88-167">有关使用注意事项和已知问题的信息，请参阅 [Excel Source](../data-flow/excel-source.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a88-167">For information about usage considerations and known issues, see [Excel Source](../data-flow/excel-source.md).</span></span>  
  
### <a name="data-source--microsoft-access"></a><span data-ttu-id="c7a88-168">数据源 = Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="c7a88-168">Data Source = Microsoft Access</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7a88-169">仅当要连接到使用 Access 2003 或更早版本的数据库时，才选择 " **Microsoft Access** "。</span><span class="sxs-lookup"><span data-stu-id="c7a88-169">Select **Microsoft Access** only if you want to connect to a database that uses Access 2003 or earlier.</span></span> <span data-ttu-id="c7a88-170">若要连接到使用 Access 2007 的数据库，请改为选择**Microsoft Office 12.0 访问数据库引擎 OLE DB 提供程序**。</span><span class="sxs-lookup"><span data-stu-id="c7a88-170">To connect to a database that uses Access 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider** instead.</span></span>  
  
 <span data-ttu-id="c7a88-171">**文件名**</span><span class="sxs-lookup"><span data-stu-id="c7a88-171">**File name**</span></span>  
 <span data-ttu-id="c7a88-172">指定要从其中导入数据的数据库文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="c7a88-172">Specify the path and file name for the database file from which to import the data.</span></span> <span data-ttu-id="c7a88-173">例如，**C:\MyData.mdb、\\\Sales\Database\Northwind.mdb**。</span><span class="sxs-lookup"><span data-stu-id="c7a88-173">For example, **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**.</span></span> <span data-ttu-id="c7a88-174">或单击 **“浏览”**。</span><span class="sxs-lookup"><span data-stu-id="c7a88-174">Or, click **Browse**.</span></span>  
  
 <span data-ttu-id="c7a88-175">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="c7a88-175">**Browse**</span></span>  
 <span data-ttu-id="c7a88-176">通过使用“打开”\*\*\*\* 对话框定位数据库文件。</span><span class="sxs-lookup"><span data-stu-id="c7a88-176">Locate the database file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="c7a88-177">**用户名**</span><span class="sxs-lookup"><span data-stu-id="c7a88-177">**User name**</span></span>  
 <span data-ttu-id="c7a88-178">当工作组信息文件与数据库关联时，为数据库连接指定一个有效的用户名。</span><span class="sxs-lookup"><span data-stu-id="c7a88-178">Specify a valid user name for the database connection when a workgroup information file is associated with the database.</span></span>  
  
 <span data-ttu-id="c7a88-179">**密码**</span><span class="sxs-lookup"><span data-stu-id="c7a88-179">**Password**</span></span>  
 <span data-ttu-id="c7a88-180">当工作组信息文件与数据库关联时，为数据库连接提供相应的用户密码。</span><span class="sxs-lookup"><span data-stu-id="c7a88-180">Provide the user's password for the database connection when a workgroup information file is associated with the database.</span></span> <span data-ttu-id="c7a88-181">但是，如果对于所有用户都使用一个密码保护数据库，则必须在 **“数据链接属性”** 对话框（可通过单击 **“高级”** 访问）中提供此值。</span><span class="sxs-lookup"><span data-stu-id="c7a88-181">However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed by clicking **Advanced**.</span></span>  
  
 <span data-ttu-id="c7a88-182">**高级**</span><span class="sxs-lookup"><span data-stu-id="c7a88-182">**Advanced**</span></span>  
 <span data-ttu-id="c7a88-183">您可能想要使用 "**数据链接属性**" 对话框指定高级选项，例如数据库密码或非默认工作组信息文件。</span><span class="sxs-lookup"><span data-stu-id="c7a88-183">You may want to specify advanced options, such as the database password or a non-default workgroup information file, by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="c7a88-184">有关 OLE DB 提供程序属性的详细信息，请在[MSDN library](https://go.microsoft.com/fwlink/?linkid=62553)的 "数据访问" 部分中进行搜索。</span><span class="sxs-lookup"><span data-stu-id="c7a88-184">For more information about OLE DB provider properties, search in the Data Access section of the [MSDN library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
### <a name="data-source--flat-file-source"></a><span data-ttu-id="c7a88-185">数据源 = 平面文件源</span><span class="sxs-lookup"><span data-stu-id="c7a88-185">Data Source = Flat File Source</span></span>  
 <span data-ttu-id="c7a88-186">有关平面文件数据源的选项的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="c7a88-186">See the following topics for information about the options for a flat file data source.</span></span>  
  
 [<span data-ttu-id="c7a88-187">平面文件连接管理器编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="c7a88-187">Flat File Connection Manager Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
 [<span data-ttu-id="c7a88-188">平面文件连接管理器编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="c7a88-188">Flat File Connection Manager Editor &#40;Columns Page&#41;</span></span>](../flat-file-connection-manager-editor-columns-page.md)  
  
 [<span data-ttu-id="c7a88-189">平面文件连接管理器编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="c7a88-189">Flat File Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../flat-file-connection-manager-editor-advanced-page.md)  
  
 [<span data-ttu-id="c7a88-190">平面文件连接管理器编辑器（“预览”页）</span><span class="sxs-lookup"><span data-stu-id="c7a88-190">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../flat-file-connection-manager-editor-preview-page.md)  
  
  
