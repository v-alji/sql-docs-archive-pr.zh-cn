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
# <a name="install-sql-server-2014-offline-documentation"></a>安装 SQL Server 2014 脱机文档

本文介绍如何下载和查看脱机 SQL Server 2014 内容。 下载脱机内容后，便可在没有 Internet 连接的情况下访问文档（尽管最初下载时还是需要 Internet 连接）。

此方法涉及使用 SQL Server Management Studio (SSMS) 的 "**帮助**" 菜单访问 "帮助查看器" 实用工具 ( # A0) 。

脱机文档适用于2012-2019 范围内的 SQL Server 版本，还可能适用于其他更高版本。 虽然可以[联机查看早期版本的内容](https://docs.microsoft.com/previous-versions/sql/)，但在访问早期内容时，脱机方式非常便捷。

- [SQL Server 2014](#sql-server-2014-offline-content)
- [SQL Server 2012](#sql-server-2012-offline-content)

对于 SQL Server 2016 及更高版本，请参阅特定于版本的文档，以了解这些版本如何处理其脱机文档。

## <a name="sql-server-2014-offline-content"></a>SQL Server 2014 脱机内容

> [!IMPORTANT]
> SQL 2014 Transact-SQL 内容只能脱机使用。

以下步骤说明如何加载 SQL Server 2014 的脱机内容。

1. 从下载中心下载[适用于防火墙和代理受限环境的 Microsoft SQL Server 2014 产品文档](https://www.microsoft.com/download/details.aspx?id=42557)内容，并将它保存到文件夹中。

2. 解压缩文件以查看 *.msha*文件。

   ![SQL Server 2014 帮助文档安装程序文件](../sql-server/media/sql-server-offline-documentation/sql-2014-help-content-setup-msha.png)

3. 在 SSMS 中，选择“帮助”菜单上的“添加和删除帮助内容”。

   ![帮助查看器中的“添加和删除内容”](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   帮助查看器随即打开“管理内容”选项卡。

4. 如需安装最新的帮助内容，请选择“安装源”下的“磁盘”，然后选择省略号 (...)。

   ![帮助查看器上的“管理内容”>“磁盘”源](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > “管理内容”选项卡上的“本地存储路径”显示了内容在本地计算机上的位置。 如需更改位置，请选择“移动”，在“到”字段中输入其他文件夹路径，然后选择“确定”  。
   如果在更改本地存储路径后帮助安装失败，请关闭并重新打开 Help Viewer。 确保本地存储路径中显示了新位置，然后重试安装。

5. 找到你用于解压缩内容的文件夹。 选择文件夹中的“HelpContentSetup.msha”文件，然后选择“打开”。

   ![打开 SQL Server 2014 的“Help Content Setup.msha”文件](../sql-server/media/sql-server-offline-documentation/sql-2014-open-msha.png)

6. 在搜索栏中键入“sql server 2014”。 看到 SQL Server 2014 的内容后，选择要安装到帮助查看器的每个内容包（丛书）旁边的“添加”，然后选择“更新”。

   ![帮助查看器中的 SQL Server 2014 丛书搜索屏幕](../sql-server/media/sql-server-offline-documentation/sql-2014-search.png)

   ![帮助查看器中的 SQL Server 2014 丛书添加和更新操作](../sql-server/media/sql-server-offline-documentation/sql-2014-add-update.png)

    > [!NOTE]
    > 如果帮助查看器在添加内容时冻结 (挂起) ，请将%LOCALAPPDATA%\Microsoft\HelpViewer2.x\ 中的 Cache LastRefreshed = " \<mm/dd/yyyy> 00:00:00" 行更改 HlpViewer_SSMSx_en，将或 HlpViewer_VisualStudiox_en-settings 文件更改为将来的某个日期。 有关此问题的详细信息，请参阅 [《Visual Studio 帮助查看器冻结》](/visualstudio/welcome-to-visual-studio)。

7. 可以在左侧的内容窗格下搜索“sql server 2014”，验证是否已安装 SQL Server 2014 内容。

   ![SQL Server 2014 丛书已自动更新](../sql-server/media/sql-server-offline-documentation/sql-2014-content.png)

## <a name="sql-server-2012-offline-content"></a>SQL Server 2012 脱机内容

以下步骤说明如何加载 SQL Server 2012 的脱机内容

1. 从下载中心下载[适用于防火墙和代理受限环境的 Microsoft SQL Server 2012 产品文档](https://www.microsoft.com/download/details.aspx?id=35750)内容，并将它保存到文件夹中。

2. 解压缩文件以查看 *.msha*文件。

   ![SQL Server 2012 帮助内容安装程序文件](../sql-server/media/sql-server-offline-documentation/sql-2012-help-content-setup-msha.png)

3. 在 SSMS 中，选择“帮助”菜单上的“添加和删除帮助内容”。

   ![帮助查看器中的“添加和删除内容”](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   帮助查看器随即打开“管理内容”选项卡。

4. 如需安装最新的帮助内容，请选择“安装源”下的“磁盘”，然后选择省略号 (...)。

   ![帮助查看器上的“管理内容”>“磁盘”源](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > “管理内容”选项卡上的“本地存储路径”显示了内容在本地计算机上的位置。 如需更改位置，请选择“移动”，在“到”字段中输入其他文件夹路径，然后选择“确定”  。
   如果在更改本地存储路径后帮助安装失败，请关闭并重新打开 Help Viewer。 确保本地存储路径中显示了新位置，然后重试安装。

5. 找到你用于解压缩内容的文件夹。 选择文件夹中的“HelpContentSetup.msha”文件，然后选择“打开”。

   ![打开 SQL Server 2012 的“Help Content Setup.msha”文件](../sql-server/media/sql-server-offline-documentation/sql-2012-open-msha.png)

6. 在搜索栏中键入“sql server 2012”。 看到 SQL Server 2012 的内容后，选择要安装到帮助查看器的每个内容包（丛书）旁边的“添加”，然后选择“更新”。

   ![帮助查看器中的 SQL Server 2012 丛书搜索屏幕](../sql-server/media/sql-server-offline-documentation/sql-2012-search.png)

   ![帮助查看器中的 SQL Server 2012 丛书添加和更新操作](../sql-server/media/sql-server-offline-documentation/sql-2012-add-update.png)

    > [!NOTE]
    > 如果帮助查看器在添加内容时冻结 (挂起) ，请将%LOCALAPPDATA%\Microsoft\HelpViewer2.x\ 中的 Cache LastRefreshed = " \<mm/dd/yyyy> 00:00:00" 行更改 HlpViewer_SSMSx_en，将或 HlpViewer_VisualStudiox_en-settings 文件更改为将来的某个日期。 有关此问题的详细信息，请参阅 [《Visual Studio 帮助查看器冻结》](/visualstudio/welcome-to-visual-studio)。

7. 可以在左侧的内容窗格下搜索“sql server 2012”，验证是否已加载 SQL Server 2012 内容。

   ![SQL Server 2012 文档已自动更新](../sql-server/media/sql-server-offline-documentation/sql-2012-content.png)

## <a name="view-offline-documentation"></a>查看脱机文档

可以使用最新版本 SQL Server Management Studio (SSMS) 中的 "**帮助**" 菜单查看 SQL Server 帮助内容。

### <a name="view-offline-help-content-in-ssms"></a>在 SSMS 中查看脱机帮助内容

如需在 SSMS 中查看已安装的帮助内容，请从“帮助”菜单中选择“在帮助查看器中启动”，即可启动帮助查看器。

   ![在帮助查看器中启动](../sql-server/media/sql-server-offline-documentation/helpviewer-view-offline.png)  

帮助查看器随即打开“管理内容”选项卡，并在左窗格中显示已安装的帮助目录。 选择目录中的文章，便可在右窗格显示文章内容。

> [!Important]
> 如果看不到目录窗格，请在左侧边距上选择“目录”。 选择图钉图标，可使目录窗格保持打开状态。  

   ![显示内容的帮助查看器](../sql-server/media/sql-server-offline-documentation/view-offline-all.png)
