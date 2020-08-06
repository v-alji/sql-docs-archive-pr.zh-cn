---
title: SQL Server 2014 的脱机文档
description: 了解如何安装 SQL Server 2014 的脱机文档。 使用 SQL Server Management Studio (SSMS) 查看脱机内容。
ms.prod: sql
ms.technology: install
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: markingmyname
ms.author: maghan
ms.reviewer: carlrab
ms.date: 07/19/2020
ms.openlocfilehash: bfd4adc658a203f8e2d22ef77ce0381084e36363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586071"
---
# <a name="install-sql-server-2014-offline-documentation"></a><span data-ttu-id="9add5-104">安装 SQL Server 2014 脱机文档</span><span class="sxs-lookup"><span data-stu-id="9add5-104">Install SQL Server 2014 offline documentation</span></span>

<span data-ttu-id="9add5-105">本文介绍如何下载和查看脱机 SQL Server 2014 内容。</span><span class="sxs-lookup"><span data-stu-id="9add5-105">This article describes how to download and view offline SQL Server 2014 content.</span></span> <span data-ttu-id="9add5-106">下载脱机内容后，便可在没有 Internet 连接的情况下访问文档（尽管最初下载时还是需要 Internet 连接）。</span><span class="sxs-lookup"><span data-stu-id="9add5-106">Offline content enables you to access the documentation without an internet connection (although an internet connection is initially required to download it).</span></span>

<span data-ttu-id="9add5-107">此方法涉及使用 SQL Server Management Studio (SSMS) 的 "**帮助**" 菜单访问 "帮助查看器" 实用工具 ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="9add5-107">The technique involves using the **Help** menu of SQL Server Management Studio (SSMS), to access the Help Viewer utility (HlpViewer.exe).</span></span>

<span data-ttu-id="9add5-108">脱机文档适用于2012-2019 范围内的 SQL Server 版本，还可能适用于其他更高版本。</span><span class="sxs-lookup"><span data-stu-id="9add5-108">Offline documentation is available for versions of SQL Server in the range of 2012-2019, and perhaps for additional later versions too.</span></span> <span data-ttu-id="9add5-109">虽然可以[联机查看早期版本的内容](https://docs.microsoft.com/previous-versions/sql/)，但在访问早期内容时，脱机方式非常便捷。</span><span class="sxs-lookup"><span data-stu-id="9add5-109">Although you can view content for [previous versions online](https://docs.microsoft.com/previous-versions/sql/), an offline option provides a convenient way to access the older content.</span></span>

- [<span data-ttu-id="9add5-110">SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="9add5-110">SQL Server 2014</span></span>](#sql-server-2014-offline-content)
- [<span data-ttu-id="9add5-111">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="9add5-111">SQL Server 2012</span></span>](#sql-server-2012-offline-content)

<span data-ttu-id="9add5-112">对于 SQL Server 2016 及更高版本，请参阅特定于版本的文档，以了解这些版本如何处理其脱机文档。</span><span class="sxs-lookup"><span data-stu-id="9add5-112">For SQL Server 2016 and later versions, see their version-specific documentation to learn how those versions handle their offline documentation.</span></span>

## <a name="sql-server-2014-offline-content"></a><span data-ttu-id="9add5-113">SQL Server 2014 脱机内容</span><span class="sxs-lookup"><span data-stu-id="9add5-113">SQL Server 2014 offline content</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9add5-114">SQL 2014 Transact-SQL 内容只能脱机使用。</span><span class="sxs-lookup"><span data-stu-id="9add5-114">SQL 2014 Transact-SQL content is only available offline.</span></span>

<span data-ttu-id="9add5-115">以下步骤说明如何加载 SQL Server 2014 的脱机内容。</span><span class="sxs-lookup"><span data-stu-id="9add5-115">The following steps explain how to load offline content for SQL Server 2014.</span></span>

1. <span data-ttu-id="9add5-116">从下载中心下载[适用于防火墙和代理受限环境的 Microsoft SQL Server 2014 产品文档](https://www.microsoft.com/download/details.aspx?id=42557)内容，并将它保存到文件夹中。</span><span class="sxs-lookup"><span data-stu-id="9add5-116">Download the [Product Documentation for Microsoft SQL Server 2014 for firewall and proxy restricted environments](https://www.microsoft.com/download/details.aspx?id=42557) content from the download center and save it to a folder.</span></span>

2. <span data-ttu-id="9add5-117">解压缩文件以查看 *.msha*文件。</span><span class="sxs-lookup"><span data-stu-id="9add5-117">Unzip the file to view the *.msha* file.</span></span>

   ![SQL Server 2014 帮助文档安装程序文件](../sql-server/media/sql-server-offline-documentation/sql-2014-help-content-setup-msha.png)

3. <span data-ttu-id="9add5-119">在 SSMS 中，选择“帮助”菜单上的“添加和删除帮助内容”。</span><span class="sxs-lookup"><span data-stu-id="9add5-119">In SSMS, select **Add and Remove Help Content** on the Help menu.</span></span>

   ![帮助查看器中的“添加和删除内容”](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   <span data-ttu-id="9add5-121">帮助查看器随即打开“管理内容”选项卡。</span><span class="sxs-lookup"><span data-stu-id="9add5-121">The Help Viewer opens to the Manage Content tab.</span></span>

4. <span data-ttu-id="9add5-122">如需安装最新的帮助内容，请选择“安装源”下的“磁盘”，然后选择省略号 (...)。</span><span class="sxs-lookup"><span data-stu-id="9add5-122">To install the latest help content, choose **Disk** under Installation source and then the ellipses (...).</span></span>

   ![帮助查看器上的“管理内容”>“磁盘”源](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > <span data-ttu-id="9add5-124">“管理内容”选项卡上的“本地存储路径”显示了内容在本地计算机上的位置。</span><span class="sxs-lookup"><span data-stu-id="9add5-124">The Local store path on the Manage Content tab shows where on the local computer the content is located.</span></span> <span data-ttu-id="9add5-125">如需更改位置，请选择“移动”，在“到”字段中输入其他文件夹路径，然后选择“确定”  。</span><span class="sxs-lookup"><span data-stu-id="9add5-125">To change the location, select **Move**, enter a different folder path in the **To** field, and then select **OK**.</span></span>
   <span data-ttu-id="9add5-126">如果在更改本地存储路径后帮助安装失败，请关闭并重新打开 Help Viewer。</span><span class="sxs-lookup"><span data-stu-id="9add5-126">If the help installation fails after changing the Local store path, close and reopen the Help Viewer.</span></span> <span data-ttu-id="9add5-127">确保本地存储路径中显示了新位置，然后重试安装。</span><span class="sxs-lookup"><span data-stu-id="9add5-127">Ensure the new location appears in the Local store path and then try the installation again.</span></span>

5. <span data-ttu-id="9add5-128">找到你用于解压缩内容的文件夹。</span><span class="sxs-lookup"><span data-stu-id="9add5-128">Locate the folder where you unzipped the content.</span></span> <span data-ttu-id="9add5-129">选择文件夹中的“HelpContentSetup.msha”文件，然后选择“打开”。</span><span class="sxs-lookup"><span data-stu-id="9add5-129">Select the **HelpContentSetup.msha** file in the folder then select **Open**.</span></span>

   ![打开 SQL Server 2014 的“Help Content Setup.msha”文件](../sql-server/media/sql-server-offline-documentation/sql-2014-open-msha.png)

6. <span data-ttu-id="9add5-131">在搜索栏中键入“sql server 2014”。</span><span class="sxs-lookup"><span data-stu-id="9add5-131">Type in *sql server 2014* in the search bar.</span></span> <span data-ttu-id="9add5-132">看到 SQL Server 2014 的内容后，选择要安装到帮助查看器的每个内容包（丛书）旁边的“添加”，然后选择“更新”。</span><span class="sxs-lookup"><span data-stu-id="9add5-132">Once you see the 2014 content available, select **Add** next to each content package (book) that you want to install to Help Viewer and then select **Update**.</span></span>

   ![帮助查看器中的 SQL Server 2014 丛书搜索屏幕](../sql-server/media/sql-server-offline-documentation/sql-2014-search.png)

   ![帮助查看器中的 SQL Server 2014 丛书添加和更新操作](../sql-server/media/sql-server-offline-documentation/sql-2014-add-update.png)

    > [!NOTE]
    > <span data-ttu-id="9add5-135">如果帮助查看器在添加内容时冻结 (挂起) ，请将%LOCALAPPDATA%\Microsoft\HelpViewer2.x\ 中的 Cache LastRefreshed = " \<mm/dd/yyyy> 00:00:00" 行更改 HlpViewer_SSMSx_en，将或 HlpViewer_VisualStudiox_en-settings 文件更改为将来的某个日期。</span><span class="sxs-lookup"><span data-stu-id="9add5-135">If the Help Viewer freezes (hangs) while adding content, change the Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" line in the %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings file to some date in the future.</span></span> <span data-ttu-id="9add5-136">有关此问题的详细信息，请参阅 [《Visual Studio 帮助查看器冻结》](/visualstudio/welcome-to-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="9add5-136">For more information about this issue, see [Visual Studio Help Viewer freezes](/visualstudio/welcome-to-visual-studio).</span></span>

7. <span data-ttu-id="9add5-137">可以在左侧的内容窗格下搜索“sql server 2014”，验证是否已安装 SQL Server 2014 内容。</span><span class="sxs-lookup"><span data-stu-id="9add5-137">You can verify that the SQL Server 2014 content installed by searching under the content pane on the left for *sql server 2014*.</span></span>

   ![SQL Server 2014 丛书已自动更新](../sql-server/media/sql-server-offline-documentation/sql-2014-content.png)

## <a name="sql-server-2012-offline-content"></a><span data-ttu-id="9add5-139">SQL Server 2012 脱机内容</span><span class="sxs-lookup"><span data-stu-id="9add5-139">SQL Server 2012 offline content</span></span>

<span data-ttu-id="9add5-140">以下步骤说明如何加载 SQL Server 2012 的脱机内容</span><span class="sxs-lookup"><span data-stu-id="9add5-140">The following steps explain how to load offline content for SQL Server 2012</span></span>

1. <span data-ttu-id="9add5-141">从下载中心下载[适用于防火墙和代理受限环境的 Microsoft SQL Server 2012 产品文档](https://www.microsoft.com/download/details.aspx?id=35750)内容，并将它保存到文件夹中。</span><span class="sxs-lookup"><span data-stu-id="9add5-141">Download the [Product Documentation for Microsoft SQL Server 2012 for firewall and proxy restricted environments](https://www.microsoft.com/download/details.aspx?id=35750) content from the download center and save it to a folder.</span></span>

2. <span data-ttu-id="9add5-142">解压缩文件以查看 *.msha*文件。</span><span class="sxs-lookup"><span data-stu-id="9add5-142">Unzip the file to view the *.msha* file.</span></span>

   ![SQL Server 2012 帮助内容安装程序文件](../sql-server/media/sql-server-offline-documentation/sql-2012-help-content-setup-msha.png)

3. <span data-ttu-id="9add5-144">在 SSMS 中，选择“帮助”菜单上的“添加和删除帮助内容”。</span><span class="sxs-lookup"><span data-stu-id="9add5-144">In SSMS, select **Add and Remove Help Content** on the Help menu.</span></span>

   ![帮助查看器中的“添加和删除内容”](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   <span data-ttu-id="9add5-146">帮助查看器随即打开“管理内容”选项卡。</span><span class="sxs-lookup"><span data-stu-id="9add5-146">The Help Viewer opens to the Manage Content tab.</span></span>

4. <span data-ttu-id="9add5-147">如需安装最新的帮助内容，请选择“安装源”下的“磁盘”，然后选择省略号 (...)。</span><span class="sxs-lookup"><span data-stu-id="9add5-147">To install the latest help content, choose **Disk** under Installation source and then the ellipses (...).</span></span>

   ![帮助查看器上的“管理内容”>“磁盘”源](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > <span data-ttu-id="9add5-149">“管理内容”选项卡上的“本地存储路径”显示了内容在本地计算机上的位置。</span><span class="sxs-lookup"><span data-stu-id="9add5-149">The Local store path on the Manage Content tab shows where on the local computer the content is located.</span></span> <span data-ttu-id="9add5-150">如需更改位置，请选择“移动”，在“到”字段中输入其他文件夹路径，然后选择“确定”  。</span><span class="sxs-lookup"><span data-stu-id="9add5-150">To change the location, select **Move**, enter a different folder path in the **To** field, and then select **OK**.</span></span>
   <span data-ttu-id="9add5-151">如果在更改本地存储路径后帮助安装失败，请关闭并重新打开 Help Viewer。</span><span class="sxs-lookup"><span data-stu-id="9add5-151">If the help installation fails after changing the Local store path, close and reopen the Help Viewer.</span></span> <span data-ttu-id="9add5-152">确保本地存储路径中显示了新位置，然后重试安装。</span><span class="sxs-lookup"><span data-stu-id="9add5-152">Ensure the new location appears in the Local store path and then try the installation again.</span></span>

5. <span data-ttu-id="9add5-153">找到你用于解压缩内容的文件夹。</span><span class="sxs-lookup"><span data-stu-id="9add5-153">Locate the folder where you unzipped the content.</span></span> <span data-ttu-id="9add5-154">选择文件夹中的“HelpContentSetup.msha”文件，然后选择“打开”。</span><span class="sxs-lookup"><span data-stu-id="9add5-154">Select the **HelpContentSetup.msha** file in the folder then select **Open**.</span></span>

   ![打开 SQL Server 2012 的“Help Content Setup.msha”文件](../sql-server/media/sql-server-offline-documentation/sql-2012-open-msha.png)

6. <span data-ttu-id="9add5-156">在搜索栏中键入“sql server 2012”。</span><span class="sxs-lookup"><span data-stu-id="9add5-156">Type in *sql server 2012* in the search bar.</span></span> <span data-ttu-id="9add5-157">看到 SQL Server 2012 的内容后，选择要安装到帮助查看器的每个内容包（丛书）旁边的“添加”，然后选择“更新”。</span><span class="sxs-lookup"><span data-stu-id="9add5-157">Once you see the 2012 content available, select **Add** next to each content package (book) that you want to install to Help Viewer and then select **Update**.</span></span>

   ![帮助查看器中的 SQL Server 2012 丛书搜索屏幕](../sql-server/media/sql-server-offline-documentation/sql-2012-search.png)

   ![帮助查看器中的 SQL Server 2012 丛书添加和更新操作](../sql-server/media/sql-server-offline-documentation/sql-2012-add-update.png)

    > [!NOTE]
    > <span data-ttu-id="9add5-160">如果帮助查看器在添加内容时冻结 (挂起) ，请将%LOCALAPPDATA%\Microsoft\HelpViewer2.x\ 中的 Cache LastRefreshed = " \<mm/dd/yyyy> 00:00:00" 行更改 HlpViewer_SSMSx_en，将或 HlpViewer_VisualStudiox_en-settings 文件更改为将来的某个日期。</span><span class="sxs-lookup"><span data-stu-id="9add5-160">If the Help Viewer freezes (hangs) while adding content, change the Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" line in the %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings file to some date in the future.</span></span> <span data-ttu-id="9add5-161">有关此问题的详细信息，请参阅 [《Visual Studio 帮助查看器冻结》](/visualstudio/welcome-to-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="9add5-161">For more information about this issue, see [Visual Studio Help Viewer freezes](/visualstudio/welcome-to-visual-studio).</span></span>

7. <span data-ttu-id="9add5-162">可以在左侧的内容窗格下搜索“sql server 2012”，验证是否已加载 SQL Server 2012 内容。</span><span class="sxs-lookup"><span data-stu-id="9add5-162">You can verify that the SQL Server 2012 content is loaded by searching under the content pane on the left for *sql server 2012*.</span></span>

   ![SQL Server 2012 文档已自动更新](../sql-server/media/sql-server-offline-documentation/sql-2012-content.png)

## <a name="view-offline-documentation"></a><span data-ttu-id="9add5-164">查看脱机文档</span><span class="sxs-lookup"><span data-stu-id="9add5-164">View offline documentation</span></span>

<span data-ttu-id="9add5-165">可以使用最新版本 SQL Server Management Studio (SSMS) 中的 "**帮助**" 菜单查看 SQL Server 帮助内容。</span><span class="sxs-lookup"><span data-stu-id="9add5-165">You can view SQL Server help content using the **HELP** menu in the latest version of SQL Server Management Studio (SSMS).</span></span>

### <a name="view-offline-help-content-in-ssms"></a><span data-ttu-id="9add5-166">在 SSMS 中查看脱机帮助内容</span><span class="sxs-lookup"><span data-stu-id="9add5-166">View offline help content in SSMS</span></span>

<span data-ttu-id="9add5-167">如需在 SSMS 中查看已安装的帮助内容，请从“帮助”菜单中选择“在帮助查看器中启动”，即可启动帮助查看器。</span><span class="sxs-lookup"><span data-stu-id="9add5-167">To view the installed help in SSMS, select **Launch in Help Viewer** from the Help menu, to launch the Help Viewer.</span></span>

   ![在帮助查看器中启动](../sql-server/media/sql-server-offline-documentation/helpviewer-view-offline.png)  

<span data-ttu-id="9add5-169">帮助查看器随即打开“管理内容”选项卡，并在左窗格中显示已安装的帮助目录。</span><span class="sxs-lookup"><span data-stu-id="9add5-169">Help Viewer opens to the Manage Content tab, with the installed help table of contents in the left pane.</span></span> <span data-ttu-id="9add5-170">选择目录中的文章，便可在右窗格显示文章内容。</span><span class="sxs-lookup"><span data-stu-id="9add5-170">select articles in the table of contents to display them in the right pane.</span></span>

> [!Important]
> <span data-ttu-id="9add5-171">如果看不到目录窗格，请在左侧边距上选择“目录”。</span><span class="sxs-lookup"><span data-stu-id="9add5-171">If the contents pane is not visible, select Contents on the left margin.</span></span> <span data-ttu-id="9add5-172">选择图钉图标，可使目录窗格保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="9add5-172">select the pushpin icon to keep the contents pane open.</span></span>  

   ![显示内容的帮助查看器](../sql-server/media/sql-server-offline-documentation/view-offline-all.png)
