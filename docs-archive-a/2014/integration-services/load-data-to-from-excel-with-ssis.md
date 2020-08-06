---
title: 使用 SSIS 从 Excel 导入数据或将数据导出到 Excel | Microsoft Docs
description: 了解如何使用 SQL Server Integration Services (SSIS) 导入或导出 Excel 数据，以及先决条件、已知问题和限制。
ms.date: 04/10/2018
ms.prod: sql-server-2014
ms.prod_service: integration-services
ms.reviewer: ''
ms.custom: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58b0165925e73d0eb72b118113bc354338741a0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586806"
---
# <a name="import-data-from-excel-or-export-data-to-excel-with-sql-server-integration-services-ssis"></a><span data-ttu-id="89abd-103">使用 SQL Server Integration Services (SSIS) 从 Excel 导入数据或将数据导出到 Excel</span><span class="sxs-lookup"><span data-stu-id="89abd-103">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>

<span data-ttu-id="89abd-104">本文介绍如何使用 SQL Server Integration Services (SSIS) 将数据导入 Excel 或从 Excel 导出数据。</span><span class="sxs-lookup"><span data-stu-id="89abd-104">This article describes how to import data from Excel or export data to Excel with SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="89abd-105">本文还会介绍先决条件、限制和已知问题。</span><span class="sxs-lookup"><span data-stu-id="89abd-105">The article also describes prerequisites, limitations, and known issues.</span></span>

<span data-ttu-id="89abd-106">可通过创建 SSIS 包和使用 Excel 连接管理器、Excel 源或 Excel 目标提供程序，从 Excel 导出文件或将文件导入 Excel。</span><span class="sxs-lookup"><span data-stu-id="89abd-106">You can import data from Excel or export data to Excel by creating an SSIS package and using the Excel Connection Manager and the Excel Source or the Excel Destination.</span></span> <span data-ttu-id="89abd-107">还可使用内置于 SSIS 的 SQL Server 导入和导出向导。</span><span class="sxs-lookup"><span data-stu-id="89abd-107">You can also use the SQL Server Import and Export Wizard, which is built on SSIS.</span></span>

<span data-ttu-id="89abd-108">本文包含在 SSIS 中成功使用 Excel 或者了解和排除常见问题所必需的三组信息：</span><span class="sxs-lookup"><span data-stu-id="89abd-108">This article contains the three sets of information you need to use Excel successfully from SSIS or to understand and troubleshoot common problems:</span></span>
1.  <span data-ttu-id="89abd-109">[所需的文件](#files-you-need)。</span><span class="sxs-lookup"><span data-stu-id="89abd-109">[The files you need](#files-you-need).</span></span>
2.  <span data-ttu-id="89abd-110">从 Excel 中加载数据或将数据加载到 Excel 时需要提供的信息。</span><span class="sxs-lookup"><span data-stu-id="89abd-110">The information you have to provide when you load data from or to Excel.</span></span>
    -   <span data-ttu-id="89abd-111">[指定 Excel](#specify-excel) 作为数据源。</span><span class="sxs-lookup"><span data-stu-id="89abd-111">[Specify Excel](#specify-excel) as your data source.</span></span>
    -   <span data-ttu-id="89abd-112">提供 [Excel 文件和路径](#excel-file)。</span><span class="sxs-lookup"><span data-stu-id="89abd-112">Provide the [Excel file name and path](#excel-file).</span></span>
    -   <span data-ttu-id="89abd-113">选择 [Excel 版本](#excel-version)。</span><span class="sxs-lookup"><span data-stu-id="89abd-113">Select the [Excel version](#excel-version).</span></span>
    -   <span data-ttu-id="89abd-114">指定[第一行是否包含列名称](#first-row)。</span><span class="sxs-lookup"><span data-stu-id="89abd-114">Specify whether the [first row contains column names](#first-row).</span></span>
    -   <span data-ttu-id="89abd-115">提供[包含数据的工作表或范围](#sheets-ranges)。</span><span class="sxs-lookup"><span data-stu-id="89abd-115">Provide the [worksheet or range that contains the data](#sheets-ranges).</span></span>
3.  <span data-ttu-id="89abd-116">已知问题和限制。</span><span class="sxs-lookup"><span data-stu-id="89abd-116">Known issues and limitations.</span></span>
    -   <span data-ttu-id="89abd-117">[数据类型](#issues-types)的问题。</span><span class="sxs-lookup"><span data-stu-id="89abd-117">Issues with [data types](#issues-types).</span></span>
    -   <span data-ttu-id="89abd-118">[导入](#issues-importing)的问题。</span><span class="sxs-lookup"><span data-stu-id="89abd-118">Issues with [importing](#issues-importing).</span></span>
    -   <span data-ttu-id="89abd-119">[导出](#issues-exporting)的问题。</span><span class="sxs-lookup"><span data-stu-id="89abd-119">Issues with [exporting](#issues-exporting).</span></span>

## <a name="get-the-files-you-need-to-connect-to-excel"></a><a name="files-you-need"></a><span data-ttu-id="89abd-120">获取连接到 Excel 所需的文件</span><span class="sxs-lookup"><span data-stu-id="89abd-120">Get the files you need to connect to Excel</span></span>

<span data-ttu-id="89abd-121">如果没有安装 Excel 的连接组件，首先需要下载这些组件，然后才能从 Excel 导出数据或将数据导入 Excel。</span><span class="sxs-lookup"><span data-stu-id="89abd-121">Before you can import data from Excel or export data to Excel, you may have to download the connectivity components for Excel if they're not already installed.</span></span> <span data-ttu-id="89abd-122">默认情况下，没有安装 Excel 的连接组件。</span><span class="sxs-lookup"><span data-stu-id="89abd-122">The connectivity components for Excel are not installed by default.</span></span>

<span data-ttu-id="89abd-123">在此处下载用于 Excel 的最新版连接组件：[Microsoft Access 数据库引擎 2016 可再发行组件](https://www.microsoft.com/download/details.aspx?id=54920)。</span><span class="sxs-lookup"><span data-stu-id="89abd-123">Download the latest version of the connectivity components for Excel here: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).</span></span>
  
<span data-ttu-id="89abd-124">最新版组件可以打开 Excel 早期版本创建的文件。</span><span class="sxs-lookup"><span data-stu-id="89abd-124">The latest version of the components can open files created by earlier versions of Excel.</span></span>

<span data-ttu-id="89abd-125">请确保已下载 Access 数据库引擎 2016 可再发行组件，而不是 Microsoft Access 2016 Runtime   。</span><span class="sxs-lookup"><span data-stu-id="89abd-125">Make sure that you download the Access Database Engine 2016 *Redistributable* and not the Microsoft Access 2016 *Runtime*.</span></span>

<span data-ttu-id="89abd-126">如果计算机已安装 32 位版本的 Office，则必须安装 32 位版本的组件。</span><span class="sxs-lookup"><span data-stu-id="89abd-126">If the computer already has a 32-bit version of Office, then you have to install the 32-bit version of the components.</span></span> <span data-ttu-id="89abd-127">还必须确保在 32 位模式下运行 SSIS 包，或运行 32 位版本的导入和导出向导。</span><span class="sxs-lookup"><span data-stu-id="89abd-127">You also have to ensure that you run the SSIS package in 32-bit mode, or run the 32-bit version of the Import and Export Wizard.</span></span>

<span data-ttu-id="89abd-128">如果拥有 Office 365 订阅，则运行安装程序时可能会显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="89abd-128">If you have an Office 365 subscription, you may see an error message when you run the installer.</span></span> <span data-ttu-id="89abd-129">错误消息指出该下载项无法与 Office 即点即用组件并行安装。</span><span class="sxs-lookup"><span data-stu-id="89abd-129">The error indicates that you can't install the download side by side with Office click-to-run components.</span></span> <span data-ttu-id="89abd-130">若要绕过此错误消息，请打开命令提示符窗口并使用 `/quiet` 开关运行下载的 .EXE 文件，从而在安静模式下运行安装。</span><span class="sxs-lookup"><span data-stu-id="89abd-130">To bypass this error message, run the installation in quiet mode by opening a Command Prompt window and running the .EXE file that you downloaded with the `/quiet` switch.</span></span> <span data-ttu-id="89abd-131">例如：</span><span class="sxs-lookup"><span data-stu-id="89abd-131">For example:</span></span>

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

<span data-ttu-id="89abd-132">如果安装 2016 可再发行组件遇到问题，请改为从此处安装 2010 可再发行组件：[Microsoft Access 2010 可再发行组件](https://www.microsoft.com/download/details.aspx?id=13255)。</span><span class="sxs-lookup"><span data-stu-id="89abd-132">If you have trouble installing the 2016 redistributable, install the 2010 redistributable instead from here: [Microsoft Access Database Engine 2010 Redistributable](https://www.microsoft.com/download/details.aspx?id=13255).</span></span> <span data-ttu-id="89abd-133">（不再发行 Excel 2013。）</span><span class="sxs-lookup"><span data-stu-id="89abd-133">(There is no redistributable for Excel 2013.)</span></span>

## <a name="specify-excel"></a><a name="specify-excel"></a> <span data-ttu-id="89abd-134">指定 Excel</span><span class="sxs-lookup"><span data-stu-id="89abd-134">Specify Excel</span></span>

<span data-ttu-id="89abd-135">第一步需要指出希望连接到 Excel。</span><span class="sxs-lookup"><span data-stu-id="89abd-135">The first step is to indicate that you want to connect to Excel.</span></span>

### <a name="in-ssis"></a><span data-ttu-id="89abd-136">在 SSIS 中</span><span class="sxs-lookup"><span data-stu-id="89abd-136">In SSIS</span></span>
<span data-ttu-id="89abd-137">在 SSIS 中，创建 Excel 连接管理器以连接到 Excel 源或目标文件。</span><span class="sxs-lookup"><span data-stu-id="89abd-137">In SSIS, create an Excel Connection Manager to connect to the Excel source or destination file.</span></span> <span data-ttu-id="89abd-138">创建连接管理器有多种方法：</span><span class="sxs-lookup"><span data-stu-id="89abd-138">There are several ways to create the connection manager:</span></span>

-   <span data-ttu-id="89abd-139">在“连接管理器”区域，右键单击并选择“新建连接”   。</span><span class="sxs-lookup"><span data-stu-id="89abd-139">In the **Connection Managers** area, right-click and select **New connection**.</span></span> <span data-ttu-id="89abd-140">在“添加 SSIS 连接管理器”对话框中，选择“EXCEL”，然后选择“添加”    。</span><span class="sxs-lookup"><span data-stu-id="89abd-140">In the **Add SSIS Connection Manager** dialog box, select **EXCEL** and then **Add**.</span></span>
 
-   <span data-ttu-id="89abd-141">在“SSIS”菜单上，选择“新建连接”   。</span><span class="sxs-lookup"><span data-stu-id="89abd-141">On the **SSIS** menu, select **New connection**.</span></span> <span data-ttu-id="89abd-142">在“添加 SSIS 连接管理器”对话框中，选择“EXCEL”，然后选择“添加”    。</span><span class="sxs-lookup"><span data-stu-id="89abd-142">In the **Add SSIS Connection Manager** dialog box, select **EXCEL** and then **Add**.</span></span>

-   <span data-ttu-id="89abd-143">创建连接管理器的同时，在“Excel 源编辑器”或“Excel 目标编辑器”页配置“Excel 源”或“Excel 目标”      。</span><span class="sxs-lookup"><span data-stu-id="89abd-143">Create the connection manager at the same time that you configure the **Excel Source** or the **Excel Destination** on the **Connection manager** page of the **Excel Source Editor** or of the **Excel Destination Editor**.</span></span>

### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="89abd-144">在 SQL Server 导入和导出向导中</span><span class="sxs-lookup"><span data-stu-id="89abd-144">In the SQL Server Import and Export Wizard</span></span>
<span data-ttu-id="89abd-145">在导入和导出向导中，在“选择数据源”或“选择目标”页上，选择“数据源”列表中的“Microsoft Excel”     。</span><span class="sxs-lookup"><span data-stu-id="89abd-145">In the Import and Export Wizard, on the **Choose a Data Source** or **Choose a Destination** page, select **Microsoft Excel** in the **Data source** list.</span></span>

<span data-ttu-id="89abd-146">如果在数据源列表中看不到 Excel，请确保运行的是 32 位向导。</span><span class="sxs-lookup"><span data-stu-id="89abd-146">If you don't see Excel in the list of data sources, make sure you're running the 32-bit wizard.</span></span> <span data-ttu-id="89abd-147">Excel 连接组件通常是 32 位文件，在 64 位向导中不可见。</span><span class="sxs-lookup"><span data-stu-id="89abd-147">The Excel connectivity components are typically 32-bit files and aren't visible in the 64-bit wizard.</span></span>

## <a name="excel-file-and-file-path"></a><a name="excel-file"></a><span data-ttu-id="89abd-148">Excel 文件和文件路径</span><span class="sxs-lookup"><span data-stu-id="89abd-148">Excel file and file path</span></span>

<span data-ttu-id="89abd-149">提供的第一条信息是 Excel 文件的路径和文件名称。</span><span class="sxs-lookup"><span data-stu-id="89abd-149">The first piece of info to provide is the path and file name for the Excel file.</span></span> <span data-ttu-id="89abd-150">在 SSIS 包的“Excel 连接管理器编辑器”中提供此信息，或在导入和导出向导的“选择数据源”页或“选择目标”页中提供    。</span><span class="sxs-lookup"><span data-stu-id="89abd-150">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** or **Choose a Destination** page of the Import and Export Wizard.</span></span>

<span data-ttu-id="89abd-151">输入路径和文件名，格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="89abd-151">Enter the path and file name in the following format:</span></span>

-   <span data-ttu-id="89abd-152">针对本地计算机上的文件，指定 C:\\TestData.xlsx。</span><span class="sxs-lookup"><span data-stu-id="89abd-152">For a file on the local computer, **C:\\TestData.xlsx**.</span></span>

-   <span data-ttu-id="89abd-153">针对网络共享上的文件，指定 \\\\Sales\\Data\\TestData.xlsx。</span><span class="sxs-lookup"><span data-stu-id="89abd-153">For a file on a network share, **\\\\Sales\\Data\\TestData.xlsx**.</span></span>

<span data-ttu-id="89abd-154">或者，通过使用“打开”对话框，单击“浏览”定位电子表格   。</span><span class="sxs-lookup"><span data-stu-id="89abd-154">Or, click **Browse** to locate the spreadsheet by using the **Open** dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="89abd-155">无法连接到受密码保护的 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="89abd-155">You can't connect to a password-protected Excel file.</span></span>

## <a name="excel-version"></a><a name="excel-version"></a><span data-ttu-id="89abd-156">Excel 版本</span><span class="sxs-lookup"><span data-stu-id="89abd-156">Excel version</span></span>

<span data-ttu-id="89abd-157">提供的第二条消息是 Excel 文件版本。</span><span class="sxs-lookup"><span data-stu-id="89abd-157">The second piece of info to provide is the version of the Excel file.</span></span> <span data-ttu-id="89abd-158">在 SSIS 包的“Excel 连接管理器编辑器”中提供此信息，或在导入和导出向导的“选择数据源”页或“选择目标”页中提供    。</span><span class="sxs-lookup"><span data-stu-id="89abd-158">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** or **Choose a Destination** page of the Import and Export Wizard.</span></span>

<span data-ttu-id="89abd-159">选择用于创建文件的 Microsoft Excel 的版本，或另一可兼容的版本。</span><span class="sxs-lookup"><span data-stu-id="89abd-159">Select the version of Microsoft Excel that was used to create the file, or another compatible version.</span></span> <span data-ttu-id="89abd-160">例如，如果安装 2016 连接组件遇到问题，可安装 2010 组件，然后选择该列表中的“Microsoft Excel 2007-2010”  。</span><span class="sxs-lookup"><span data-stu-id="89abd-160">For example, if you had trouble installing the 2016 connectivity components, you can install the 2010 components and select **Microsoft Excel 2007-2010** in this list.</span></span>

<span data-ttu-id="89abd-161">如果只安装了旧版本的连接组件，则可能无法在此列表中选择新版本的 Excel。</span><span class="sxs-lookup"><span data-stu-id="89abd-161">You may not be able to select newer Excel versions in the list if you only have older versions of the connectivity components installed.</span></span> <span data-ttu-id="89abd-162">“Excel 版本”列表包括 SSIS 支持的所有 Excel 版本  。</span><span class="sxs-lookup"><span data-stu-id="89abd-162">The **Excel version** list includes all the versions of Excel supported by SSIS.</span></span> <span data-ttu-id="89abd-163">此列表中显示的项并不表示已安装必需的连接组件。</span><span class="sxs-lookup"><span data-stu-id="89abd-163">The presence of items in this list does not indicate that the required connectivity components are installed.</span></span> <span data-ttu-id="89abd-164">例如，即使没有安装 2016 连接组件，列表中仍会显示“Microsoft Excel 2016”  。</span><span class="sxs-lookup"><span data-stu-id="89abd-164">For example, **Microsoft Excel 2016** appears in the list even if you have not installed the 2016 connectivity components.</span></span>

## <a name="first-row-has-column-names"></a><a name="first-row"></a><span data-ttu-id="89abd-165">首行包含列名称</span><span class="sxs-lookup"><span data-stu-id="89abd-165">First row has column names</span></span>

<span data-ttu-id="89abd-166">如果要从 Excel 导入数据，则下一步是指示数据的首行是否包含列名称。</span><span class="sxs-lookup"><span data-stu-id="89abd-166">If you're importing data from Excel, the next step is to indicate whether the first row of the data contains column names.</span></span> <span data-ttu-id="89abd-167">在 SSIS 包的“Excel 连接管理器编辑器”中提供此信息，或在导入和导出向导的“选择数据源”页中提供   。</span><span class="sxs-lookup"><span data-stu-id="89abd-167">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** page of the Import and Export Wizard.</span></span>

-   <span data-ttu-id="89abd-168">如果因为源数据不具有列名称而禁用此选项，则向导将使用 F1、F2 等作为列标题。</span><span class="sxs-lookup"><span data-stu-id="89abd-168">If you disable this option because the source data doesn't contain column names, the wizard uses F1, F2, and so forth, as column headings.</span></span>
-   <span data-ttu-id="89abd-169">如果数据包含列名称，但禁用了此选项，则向导会导入列名称作为数据的首行。</span><span class="sxs-lookup"><span data-stu-id="89abd-169">If the data contains column names, but you disable this option, the wizard imports the column names as the first row of data.</span></span>
-   <span data-ttu-id="89abd-170">如果数据不包含列名称，但启用了此选项，则向导会将源数据的首行用作列名称。</span><span class="sxs-lookup"><span data-stu-id="89abd-170">If the data does not contain column names, but you enable this option, the wizard uses the first row of source data as the column names.</span></span> <span data-ttu-id="89abd-171">在此情况下，源数据的首行不再包含在数据本身当中。</span><span class="sxs-lookup"><span data-stu-id="89abd-171">In this case, the first row of source data is no longer included in the data itself.</span></span>

<span data-ttu-id="89abd-172">如果要从 Excel 导出数据，并且启用了此选项，则导出的数据的首行包括列名称。</span><span class="sxs-lookup"><span data-stu-id="89abd-172">If you're exporting data from Excel, and you enable this option, the first row of exported data includes the column names.</span></span>

## <a name="worksheets-and-ranges"></a><a name="sheets-ranges"></a><span data-ttu-id="89abd-173">工作表和范围</span><span class="sxs-lookup"><span data-stu-id="89abd-173">Worksheets and ranges</span></span>

<span data-ttu-id="89abd-174">以下有三种可用作数据的源或目标的 Excel 对象类型：工作表、已命名范围或用其地址指定的未命名单元格范围。</span><span class="sxs-lookup"><span data-stu-id="89abd-174">There are three types of Excel objects that you can use as the source or destination for your data: a worksheet, a named range, or an unnamed range of cells that you specify with its address.</span></span>

-   <span data-ttu-id="89abd-175">**工作表。**</span><span class="sxs-lookup"><span data-stu-id="89abd-175">**Worksheet.**</span></span> <span data-ttu-id="89abd-176">若要指定工作表，请将 `$` 字符附加到表名称的末尾，并用分隔符包围字符串 - 例如，[Sheet1$]  。</span><span class="sxs-lookup"><span data-stu-id="89abd-176">To specify a worksheet, append the `$` character to the end of the sheet name and add delimiters around the string - for example, **[Sheet1$]**.</span></span> <span data-ttu-id="89abd-177">或者，在现有表和视图的列表中寻找以 `$` 字符结尾的名称。</span><span class="sxs-lookup"><span data-stu-id="89abd-177">Or, look for a name that ends with the `$` character in the list of existing tables and views.</span></span>

-   <span data-ttu-id="89abd-178">**命名区域。**</span><span class="sxs-lookup"><span data-stu-id="89abd-178">**Named range.**</span></span> <span data-ttu-id="89abd-179">若要指定命名区域，请提供区域名称 - 例如，MyDataRange  。</span><span class="sxs-lookup"><span data-stu-id="89abd-179">To specify a named range, provide the range name - for example, **MyDataRange**.</span></span> <span data-ttu-id="89abd-180">或者，在现有表和视图的列表中寻找不是以 `$` 字符结尾的名称。</span><span class="sxs-lookup"><span data-stu-id="89abd-180">Or, look for a name that does not end with the `$` character in the list of existing tables and views.</span></span>
    
-   <span data-ttu-id="89abd-181">**未命名区域。**</span><span class="sxs-lookup"><span data-stu-id="89abd-181">**Unnamed range.**</span></span> <span data-ttu-id="89abd-182">若要指定未命名的单元格区域，请将 $ 字符附加到表名称的末尾，添加区域说明，并用分隔符包围字符串 - 例如， **[Sheet1$ A1: B4]** 。</span><span class="sxs-lookup"><span data-stu-id="89abd-182">To specify a range of cells that you haven't named, append the $ character to the end of the sheet name, add the range specification, and add delimiters around the string - for example, **[Sheet1$A1:B4]**.</span></span>

<span data-ttu-id="89abd-183">要选择或指定想要用作数据的源或目标的 Excel 对象类型，请执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="89abd-183">To select or specify the type of Excel object that you want to use as the source or destination for your data, do one of the following things:</span></span>

### <a name="in-ssis"></a><span data-ttu-id="89abd-184">在 SSIS 中</span><span class="sxs-lookup"><span data-stu-id="89abd-184">In SSIS</span></span>

<span data-ttu-id="89abd-185">在 SSIS 中，在“Excel 源编辑器”或“Excel 目标编辑器”的“连接管理器”页上，执行以下操作之一    ：</span><span class="sxs-lookup"><span data-stu-id="89abd-185">In SSIS, on the **Connection manager** page of the **Excel Source Editor** or of the **Excel Destination Editor**, do one of the following things:</span></span>

-   <span data-ttu-id="89abd-186">要使用“工作表”或“命名区域”，请选择“表或视图”作为“数据访问模式”     。</span><span class="sxs-lookup"><span data-stu-id="89abd-186">To use a **worksheet** or a **named range**, select **Table or view** as the **Data access mode**.</span></span> <span data-ttu-id="89abd-187">然后，在“Excel 表的名称”列表中，选择包含工作表或命名范围  。</span><span class="sxs-lookup"><span data-stu-id="89abd-187">Then, in the **Name of the Excel sheet** list, select the worksheet or named range.</span></span>

-   <span data-ttu-id="89abd-188">要使用用其地址指定的“未命名区域”，请选择“SQL 命令”作为“数据访问模式”    。</span><span class="sxs-lookup"><span data-stu-id="89abd-188">To use an **unnamed range** that you specify with its address, select **SQL command** as the **Data access mode**.</span></span> <span data-ttu-id="89abd-189">然后，在“SQL 命令文本”字段中，输入如下查询  ：</span><span class="sxs-lookup"><span data-stu-id="89abd-189">Then, in the **SQL command text** field, enter a query like the following example:</span></span>

    ```sql
    SELECT * FROM [Sheet1$A1:B5]
    ```

### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="89abd-190">在 SQL Server 导入和导出向导中</span><span class="sxs-lookup"><span data-stu-id="89abd-190">In the SQL Server Import and Export Wizard</span></span>
<span data-ttu-id="89abd-191">在导入和导出向导中，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="89abd-191">In the Import and Export Wizard, do one of the following things:</span></span>

-   <span data-ttu-id="89abd-192">从 Excel 导入时，执行以下操作之一  ：</span><span class="sxs-lookup"><span data-stu-id="89abd-192">When you're **importing** from Excel, do one of the following things:</span></span>

    -   <span data-ttu-id="89abd-193">要使用“工作表”或“命名区域”，请在“指定表副本或查询”页上，选择“从一个或多个表或视图复制数据”     。</span><span class="sxs-lookup"><span data-stu-id="89abd-193">To use a **worksheet** or a **named range**, on the **Specify table copy or query** page, select **Copy data from one or more tables or views**.</span></span> <span data-ttu-id="89abd-194">然后，在“选择源表和视图”页的“源”列中，选择源工作表和命名区域   。</span><span class="sxs-lookup"><span data-stu-id="89abd-194">Then, on the **Select Source Tables and Views** page, in the **Source** column, select the source worksheets and named ranges.</span></span>

    -   <span data-ttu-id="89abd-195">要使用用其地址指定的“未命名区域”，请在“指定表副本或查询”页上，选择“编写查询以指定要传输的数据”    。</span><span class="sxs-lookup"><span data-stu-id="89abd-195">To use an **unnamed range** that you specify with its address, on the **Specify table copy or query** page, select **Write a query to specify the data to transfer**.</span></span> <span data-ttu-id="89abd-196">然后，在“提供源查询”页，提供如下查询  ：</span><span class="sxs-lookup"><span data-stu-id="89abd-196">Then, on the **Provide a Source Query** page, provide a query similar to the following example:</span></span>

        ```sql
        SELECT * FROM [Sheet1$A1:B5]
        ```

-   <span data-ttu-id="89abd-197">导出到 Excel 时，执行以下操作之一  ：</span><span class="sxs-lookup"><span data-stu-id="89abd-197">When you're **exporting** to Excel, do one of the following things:</span></span>

    -   <span data-ttu-id="89abd-198">要使用“工作表”或“命名区域”，请在“选择源表和视图”页的“目标”列中，选择目标工作表和命名区域     。</span><span class="sxs-lookup"><span data-stu-id="89abd-198">To use a **worksheet** or a **named range**, on the **Select Source Tables and Views** page, in the **Destination** column, select the destination worksheets and named ranges.</span></span>

    -   <span data-ttu-id="89abd-199">要使用用其地址指定的“未命名区域”，请在“选择源表和视图”页的“目标”列中输入区域，格式如下所示（不含分隔符）：`Sheet1$A1:B5`。</span><span class="sxs-lookup"><span data-stu-id="89abd-199">To use an **unnamed range** that you specify with its address, on the **Select Source Tables and Views** page, in the **Destination** column, enter the range in the following format without delimiters: `Sheet1$A1:B5`.</span></span> <span data-ttu-id="89abd-200">该向导会添加分隔符。</span><span class="sxs-lookup"><span data-stu-id="89abd-200">The wizard adds the delimiters.</span></span>

<span data-ttu-id="89abd-201">选择或输入要导入或导出的 Excel 对象后，还可在向导的“选择源表和视图”页上执行以下操作  ：</span><span class="sxs-lookup"><span data-stu-id="89abd-201">After you select or enter the Excel objects to import or export, you can also do the following things on the **Select Source Tables and Views** page of the wizard:</span></span>

-   <span data-ttu-id="89abd-202">通过选择“编辑映射”查看源和目标之间的列映射  。</span><span class="sxs-lookup"><span data-stu-id="89abd-202">Review column mappings between source and destination by selecting **Edit Mappings**.</span></span>

-   <span data-ttu-id="89abd-203">通过选择“预览”预览示例数据以确认是否需要  。</span><span class="sxs-lookup"><span data-stu-id="89abd-203">Preview sample data to make sure it's what you expect by selecting **Preview**.</span></span>

## <a name="issues-with-data-types"></a><a name="issues-types"></a><span data-ttu-id="89abd-204">数据类型的问题</span><span class="sxs-lookup"><span data-stu-id="89abd-204">Issues with data types</span></span>

### <a name="data-types"></a><span data-ttu-id="89abd-205">数据类型</span><span class="sxs-lookup"><span data-stu-id="89abd-205">Data types</span></span>

<span data-ttu-id="89abd-206">Excel 驱动程序只识别有限的一组数据类型。</span><span class="sxs-lookup"><span data-stu-id="89abd-206">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="89abd-207">例如，所有数值列均解释为双精度 (DT_R8)，并且所有字符串列（除了 memo 列）均解释为 255 个字符的 Unicode 字符串 (DT_WSTR)。</span><span class="sxs-lookup"><span data-stu-id="89abd-207">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> <span data-ttu-id="89abd-208">SSIS 按如下所示方式映射 Excel 数据类型：</span><span class="sxs-lookup"><span data-stu-id="89abd-208">SSIS maps the Excel data types as follows:</span></span>

-   <span data-ttu-id="89abd-209">数值 - 双精度浮点 (DT_R8)</span><span class="sxs-lookup"><span data-stu-id="89abd-209">Numeric - double-precision float (DT_R8)</span></span>

-   <span data-ttu-id="89abd-210">货币 - 货币 (DT_CY)</span><span class="sxs-lookup"><span data-stu-id="89abd-210">Currency - currency (DT_CY)</span></span>

-   <span data-ttu-id="89abd-211">布尔 - 布尔 (DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="89abd-211">Boolean - Boolean (DT_BOOL)</span></span>

-   <span data-ttu-id="89abd-212">日期/时间 - 日期 (DT_DATE)</span><span class="sxs-lookup"><span data-stu-id="89abd-212">Date/time - datetime (DT_DATE)</span></span>

-   <span data-ttu-id="89abd-213">字符串 - Unicode 字符串，长度为 255 (DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="89abd-213">String - Unicode string, length 255 (DT_WSTR)</span></span>

-   <span data-ttu-id="89abd-214">Memo - Unicode 文本流 (DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="89abd-214">Memo - Unicode text stream (DT_NTEXT)</span></span>

### <a name="data-type-and-length-conversions"></a><span data-ttu-id="89abd-215">数据类型和长度转换</span><span class="sxs-lookup"><span data-stu-id="89abd-215">Data type and length conversions</span></span>

<span data-ttu-id="89abd-216">SSIS 不隐式转换数据类型。</span><span class="sxs-lookup"><span data-stu-id="89abd-216">SSIS does not implicitly convert data types.</span></span> <span data-ttu-id="89abd-217">因此，在将其加载到非 Excel 目标之前，可能需要使用“派生列”或“数据转换”转换来显式转换 Excel 数据，或在将它加载到 Excel 目标之前，从非 Excel 源转换数据。</span><span class="sxs-lookup"><span data-stu-id="89abd-217">As a result, you may have to use Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a destination other than Excel, or to convert data from a source other than Excel before loading it into an Excel destination.</span></span>

<span data-ttu-id="89abd-218">此处是一些可能必需的转换的示例：</span><span class="sxs-lookup"><span data-stu-id="89abd-218">Here are some examples of the conversions that may be required:</span></span>  
  
-   <span data-ttu-id="89abd-219">Unicode Excel 字符串列与具有特定代码页的非 Unicode 字符串列之间的转换。</span><span class="sxs-lookup"><span data-stu-id="89abd-219">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepage.</span></span>
  
-   <span data-ttu-id="89abd-220">在 255 个字符的 Excel 字符串列和不同长度的字符串列之间转换。</span><span class="sxs-lookup"><span data-stu-id="89abd-220">Conversion between 255-character Excel string columns and string columns of different lengths.</span></span>
  
-   <span data-ttu-id="89abd-221">双精度 Excel 数值列与其他类型的数值列之间的转换。</span><span class="sxs-lookup"><span data-stu-id="89abd-221">Conversion between double-precision Excel numeric columns and numeric columns of other types.</span></span>

> [!TIP]
> <span data-ttu-id="89abd-222">如果使用的是导入和导出向导，并且数据需要一些转换，则向导会配置必要的转换。</span><span class="sxs-lookup"><span data-stu-id="89abd-222">If you're using the Import and Export Wizard, and your data requires some of these conversions, the wizard configures the necessary conversions for you.</span></span> <span data-ttu-id="89abd-223">因此，即使想使用 SSIS 包时，使用导入和导出向导创建初始包也十分有用。</span><span class="sxs-lookup"><span data-stu-id="89abd-223">As a result, even when you want to use an SSIS package, it may be useful to create the initial package by using the Import and Export Wizard.</span></span> <span data-ttu-id="89abd-224">使用该向导帮助你创建和配置连接管理器、源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="89abd-224">Let the wizard create and configure connection managers, sources, transformations, and destinations for you.</span></span>

## <a name="issues-with-importing"></a><a name="issues-importing"></a><span data-ttu-id="89abd-225">导入的问题</span><span class="sxs-lookup"><span data-stu-id="89abd-225">Issues with importing</span></span>

### <a name="empty-rows"></a><span data-ttu-id="89abd-226">空行</span><span class="sxs-lookup"><span data-stu-id="89abd-226">Empty rows</span></span>

<span data-ttu-id="89abd-227">将工作表或命名区域指定为源时，该驱动程序都将读取从工作表或区域左上角第一个非空单元开始的连续单元块  。</span><span class="sxs-lookup"><span data-stu-id="89abd-227">When you specify a worksheet or a named range as the source, the driver reads the *contiguous* block of cells starting with the first non-empty cell in the upper-left corner of the worksheet or range.</span></span> <span data-ttu-id="89abd-228">因此，数据无需从行 1 开始，但在源数据中不能有空行。</span><span class="sxs-lookup"><span data-stu-id="89abd-228">As a result, your data doesn't have to start in row 1, but you can't have empty rows in the source data.</span></span> <span data-ttu-id="89abd-229">例如，列标头和数据行之间不能有空行，工作表顶部的标题后不能跟空行。</span><span class="sxs-lookup"><span data-stu-id="89abd-229">For example, you can't have an empty row between the column headers and the data rows, or a title followed by empty rows at the top of the worksheet.</span></span>

<span data-ttu-id="89abd-230">如果数据上面有空行，则不能将数据作为工作表进行查询。</span><span class="sxs-lookup"><span data-stu-id="89abd-230">If there are empty rows above your data, you can't query the data as a worksheet.</span></span> <span data-ttu-id="89abd-231">在 Excel 中，必须选择数据区域，然后为区域分配名称，并查询命名区域而非工作表。</span><span class="sxs-lookup"><span data-stu-id="89abd-231">In Excel, you have to select your range of data and assign a name to the range, and then query the named range instead of the worksheet.</span></span>

### <a name="missing-values"></a><span data-ttu-id="89abd-232">缺少值</span><span class="sxs-lookup"><span data-stu-id="89abd-232">Missing values</span></span>

<span data-ttu-id="89abd-233">Excel 驱动程序读取指定源中一定数量的行（默认情况下为八行）以推测每列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="89abd-233">The Excel driver reads a certain number of rows (by default, eight rows) in the specified source to guess at the data type of each column.</span></span> <span data-ttu-id="89abd-234">如果推测出列可能包含混合数据类型（尤其是混合了文本数据的数值数据时），驱动程序将决定采用占多数的数据类型，并对包含其他类型数据的单元返回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="89abd-234">When a column appears to contain mixed data types, especially numeric data mixed with text data, the driver decides in favor of the majority data type, and returns null values for cells that contain data of the other type.</span></span> <span data-ttu-id="89abd-235">（如果各种数据类型的数量相当，则采用数值类型。）Excel 工作表中大部分单元格格式设置选项不会影响此数据类型判断。</span><span class="sxs-lookup"><span data-stu-id="89abd-235">(In a tie, the numeric type wins.) Most cell formatting options in the Excel worksheet do not seem to affect this data type determination.</span></span>

<span data-ttu-id="89abd-236">可以通过指定导入模式将所有值导入为文本来修改 Excel 驱动程序的此行为。</span><span class="sxs-lookup"><span data-stu-id="89abd-236">You can modify this behavior of the Excel driver by specifying Import Mode to import all values as text.</span></span> <span data-ttu-id="89abd-237">若要指定导入模式，请在属性窗口中将 `IMEX=1` 添加到 Excel 连接管理器的连接字符串内的“扩展属性”值中  。</span><span class="sxs-lookup"><span data-stu-id="89abd-237">To specify Import Mode, add `IMEX=1` to the value of **Extended Properties** in the connection string of the Excel connection manager in the Properties window.</span></span> 

### <a name="truncated-text"></a><span data-ttu-id="89abd-238">截断的文本</span><span class="sxs-lookup"><span data-stu-id="89abd-238">Truncated text</span></span>

<span data-ttu-id="89abd-239">驱动程序在确定 Excel 列是否包含文本数据时，它将基于采样的最长值来选择数据类型（字符串或 memo）。</span><span class="sxs-lookup"><span data-stu-id="89abd-239">When the driver determines that an Excel column contains text data, the driver selects the data type (string or memo) based on the longest value that it samples.</span></span> <span data-ttu-id="89abd-240">如果驱动程序没有在其采样的行中发现任何长于 255 个字符的值，那么它会将该列视为 255 个字符的字符串的列而不是 memo 列。</span><span class="sxs-lookup"><span data-stu-id="89abd-240">If the driver does not discover any values longer than 255 characters in the rows that it samples, it treats the column as a 255-character string column instead of a memo column.</span></span> <span data-ttu-id="89abd-241">因此，长度超过 255 个字符的值可能会被截断。</span><span class="sxs-lookup"><span data-stu-id="89abd-241">Therefore, values longer than 255 characters may be truncated.</span></span>

<span data-ttu-id="89abd-242">要从备注列导入文件但不被截断，有以下两种选择：</span><span class="sxs-lookup"><span data-stu-id="89abd-242">To import data from a memo column without truncation, you have two options:</span></span>

-   <span data-ttu-id="89abd-243">请确保至少一个示例行中的备注列包含长于 255 个字符的值</span><span class="sxs-lookup"><span data-stu-id="89abd-243">Make sure that the memo column in at least one of the sampled rows contains a value longer than 255 characters</span></span>

-   <span data-ttu-id="89abd-244">增加驱动程序采样的行数，以包括这样的行。</span><span class="sxs-lookup"><span data-stu-id="89abd-244">Increase the number of rows sampled by the driver to include such a row.</span></span> <span data-ttu-id="89abd-245">可以通过增加以下注册表项下“TypeGuessRows”的值增加采样的行数  ：</span><span class="sxs-lookup"><span data-stu-id="89abd-245">You can increase the number of rows sampled by increasing the value of **TypeGuessRows** under the following registry key:</span></span>

| <span data-ttu-id="89abd-246">可再发行组件版本</span><span class="sxs-lookup"><span data-stu-id="89abd-246">Redistributable components version</span></span> | <span data-ttu-id="89abd-247">注册表项</span><span class="sxs-lookup"><span data-stu-id="89abd-247">Registry key</span></span> |
|---|---|
| <span data-ttu-id="89abd-248">Excel 2016</span><span class="sxs-lookup"><span data-stu-id="89abd-248">Excel 2016</span></span> | <span data-ttu-id="89abd-249">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel</span><span class="sxs-lookup"><span data-stu-id="89abd-249">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel</span></span> |
| <span data-ttu-id="89abd-250">Excel 2010</span><span class="sxs-lookup"><span data-stu-id="89abd-250">Excel 2010</span></span> | <span data-ttu-id="89abd-251">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel</span><span class="sxs-lookup"><span data-stu-id="89abd-251">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel</span></span> |
| | |

## <a name="issues-with-exporting"></a><a name="issues-exporting"></a><span data-ttu-id="89abd-252">导出的问题</span><span class="sxs-lookup"><span data-stu-id="89abd-252">Issues with exporting</span></span>

### <a name="create-a-new-destination-file"></a><span data-ttu-id="89abd-253">创建新的目标文件</span><span class="sxs-lookup"><span data-stu-id="89abd-253">Create a new destination file</span></span>

#### <a name="in-ssis"></a><span data-ttu-id="89abd-254">在 SSIS 中</span><span class="sxs-lookup"><span data-stu-id="89abd-254">In SSIS</span></span>

<span data-ttu-id="89abd-255">使用想要创建的新 Excel 文件的路径和文件名称创建 Excel 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="89abd-255">Create an Excel Connection Manager with the path and file name of the new Excel file that you want to create.</span></span> <span data-ttu-id="89abd-256">然后，在“Excel 目标编辑器”，针对“Excel 工作表名称”，选择“新建”以创建目标工作表    。</span><span class="sxs-lookup"><span data-stu-id="89abd-256">Then, in the **Excel Destination Editor**, for **Name of the Excel sheet**, select **New** to create the destination worksheet.</span></span> <span data-ttu-id="89abd-257">此时，SSIS 创建具有指定工作表的新 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="89abd-257">At this point, SSIS creates the new Excel file with the specified worksheet.</span></span>

#### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="89abd-258">在 SQL Server 导入和导出向导中</span><span class="sxs-lookup"><span data-stu-id="89abd-258">In the SQL Server Import and Export Wizard</span></span>

<span data-ttu-id="89abd-259">在“选择目标”页上，选择“浏览”   。</span><span class="sxs-lookup"><span data-stu-id="89abd-259">On the **Choose a Destination** page, select **Browse**.</span></span> <span data-ttu-id="89abd-260">在“打开”对话框中，导航到想要在其中创建新 Excel 文件的文件夹，提供新文件名称，然后选择“打开”   。</span><span class="sxs-lookup"><span data-stu-id="89abd-260">In the **Open** dialog box, navigate to the folder where you want the new Excel file to be created, provide a name for the new file, and then select **Open**.</span></span>

### <a name="export-to-a-large-enough-range"></a><span data-ttu-id="89abd-261">导出到足够大的区域</span><span class="sxs-lookup"><span data-stu-id="89abd-261">Export to a large enough range</span></span>

<span data-ttu-id="89abd-262">指定某个区域作为目标时，如果该区域具有的列比源数据少，则将收到错误消息  。</span><span class="sxs-lookup"><span data-stu-id="89abd-262">When you specify a range as the destination, an error occurs if the range has fewer *columns* than the source data.</span></span> <span data-ttu-id="89abd-263">但是，如果指定的区域具有的行比源数据少，则向导将继续写入没有错误的行并扩展区域定义以匹配新的行数  。</span><span class="sxs-lookup"><span data-stu-id="89abd-263">However, if the range that you specify has fewer *rows* than the source data, the wizard continues writing rows without error and extends the range definition to match the new number of rows.</span></span>

### <a name="export-long-text-values"></a><span data-ttu-id="89abd-264">导出长文本值</span><span class="sxs-lookup"><span data-stu-id="89abd-264">Export long text values</span></span>

<span data-ttu-id="89abd-265">若要将大于 255 个字符的字符串成功地保存到 Excel 列中，驱动程序必须将该目标列的数据类型识别为 **memo** ，而不是 **string**。</span><span class="sxs-lookup"><span data-stu-id="89abd-265">Before you can successfully save strings longer than 255 characters to an Excel column, the driver must recognize the data type of the destination column as **memo** and not **string**.</span></span>

-   <span data-ttu-id="89abd-266">如果现有目标表已包含数据行，则由驱动程序采样的前几行在备注列中必须包含至少一个值超过 255 个字符的实例。</span><span class="sxs-lookup"><span data-stu-id="89abd-266">If an existing destination table already contains rows of data, then the first few rows that are sampled by the driver must contain at least one instance of a value longer than 255 characters in the memo column.</span></span>

-   <span data-ttu-id="89abd-267">如果新目标表是在包设计或运行时创建的，或通过导入和导出向导创建的，则相应的 `CREATE TABLE` 语句必须使用 LONGTEXT（或其同义词之一）作为目标备注列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="89abd-267">If a new destination table is created during package design or at run time or by the Import and Export Wizard, then the `CREATE TABLE` statement must use LONGTEXT (or one of its synonyms) as the data type of the destination memo column.</span></span> <span data-ttu-id="89abd-268">在向导中，通过单击“列映射”页上的“创建目标表”选项旁的“编辑 SQL”，检查 `CREATE TABLE` 语句并对其进行修订\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="89abd-268">In the wizard, check the `CREATE TABLE` statement and revise it, if necessary, by clicking **Edit SQL** next to the **Create destination table** option on the **Column Mappings** page.</span></span>

## <a name="related-content"></a><span data-ttu-id="89abd-269">相关内容</span><span class="sxs-lookup"><span data-stu-id="89abd-269">Related content</span></span>

<span data-ttu-id="89abd-270">有关本文所述的组件和过程的详细信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="89abd-270">For more information about the components and procedures described in this article, see the following articles:</span></span>

### <a name="about-ssis"></a><span data-ttu-id="89abd-271">关于 SSIS</span><span class="sxs-lookup"><span data-stu-id="89abd-271">About SSIS</span></span>
[<span data-ttu-id="89abd-272">Excel 连接管理器</span><span class="sxs-lookup"><span data-stu-id="89abd-272">Excel Connection Manager</span></span>](connection-manager/excel-connection-manager.md)  
[<span data-ttu-id="89abd-273">Excel 源</span><span class="sxs-lookup"><span data-stu-id="89abd-273">Excel Source</span></span>](data-flow/excel-source.md)  
[<span data-ttu-id="89abd-274">Excel 目标</span><span class="sxs-lookup"><span data-stu-id="89abd-274">Excel Destination</span></span>](data-flow/excel-destination.md)  
[<span data-ttu-id="89abd-275">使用 Foreach 循环容器循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="89abd-275">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
[<span data-ttu-id="89abd-276">使用脚本任务处理 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="89abd-276">Working with Excel Files with the Script Task</span></span>](extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)

### <a name="about-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="89abd-277">关于 SQL Server 导入和导出向导</span><span class="sxs-lookup"><span data-stu-id="89abd-277">About the SQL Server Import and Export Wizard</span></span>
[<span data-ttu-id="89abd-278">连接到 Excel 数据源</span><span class="sxs-lookup"><span data-stu-id="89abd-278">Connect to an Excel Data Source</span></span>](/sql/integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard)  
[<span data-ttu-id="89abd-279">导入和导出向导的简单示例入门</span><span class="sxs-lookup"><span data-stu-id="89abd-279">Get started with this simple example of the Import and Export Wizard</span></span>](/sql/integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard)

### <a name="other-articles"></a><span data-ttu-id="89abd-280">其他文章</span><span class="sxs-lookup"><span data-stu-id="89abd-280">Other articles</span></span>
[<span data-ttu-id="89abd-281">将 Excel 数据导入 SQL Server 或 Azure SQL 数据库</span><span class="sxs-lookup"><span data-stu-id="89abd-281">Import data from Excel to SQL Server or Azure SQL Database</span></span>](/sql/relational-databases/import-export/import-data-from-excel-to-sql)  

