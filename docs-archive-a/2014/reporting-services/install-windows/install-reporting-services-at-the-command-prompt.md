---
title: 命令提示符安装 Reporting Services SharePoint 模式和本机模式 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b2101c40c5136e89d4e30d9551187a2b63672da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682742"
---
# <a name="command-prompt-installation-of-reporting-services-sharepoint-mode-and-native-mode"></a><span data-ttu-id="7917b-102">从命令提示符处安装 Reporting Services SharePoint 模式和本机模式</span><span class="sxs-lookup"><span data-stu-id="7917b-102">Command Prompt Installation of Reporting Services SharePoint Mode and Native Mode</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="7917b-103">支持从 SQL Server 安装程序进行命令行安装。</span><span class="sxs-lookup"><span data-stu-id="7917b-103">supports a command-line installation from the SQL Server setup program.</span></span> <span data-ttu-id="7917b-104">本主题包含特定于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的若干命令行安装示例。</span><span class="sxs-lookup"><span data-stu-id="7917b-104">This topic contains several examples of command-line installations that are specific to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="7917b-105">有关适用于所有 SQL Server 组件的命令行选项的完整说明，请参阅[在命令提示符下安装 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="7917b-105">For a complete description of the command-line options available for all SQL Server components, see [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span> <span data-ttu-id="7917b-106">本主题不介绍用于 SharePoint 产品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序的命令行选项。</span><span class="sxs-lookup"><span data-stu-id="7917b-106">This topic does not describe command-line options for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span> <span data-ttu-id="7917b-107">有关该外接程序的命令行安装的信息，请参阅 [使用安装文件 rsSharePoint.msi 安装外接程序](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint)。</span><span class="sxs-lookup"><span data-stu-id="7917b-107">For information on command installation of the add-in, see [Install the add-in using the installation file rsSharePoint.msi](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint).</span></span>  
  
 <span data-ttu-id="7917b-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式 |[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式</span><span class="sxs-lookup"><span data-stu-id="7917b-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>  
  
## <a name="rsinstallmode-native-mode"></a><span data-ttu-id="7917b-109">RSINSTALLMODE（本机模式）</span><span class="sxs-lookup"><span data-stu-id="7917b-109">RSINSTALLMODE (Native Mode)</span></span>  
 <span data-ttu-id="7917b-110">用于安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的主要输入设置是 **/RSINSTALLMODE** 输入设置。</span><span class="sxs-lookup"><span data-stu-id="7917b-110">The primary input setting for installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is the **/RSINSTALLMODE** input setting.</span></span> <span data-ttu-id="7917b-111">该设置具有两个选项： **DefaultNativeMode** 和 **FilesOnlyMode**</span><span class="sxs-lookup"><span data-stu-id="7917b-111">The setting has two options: **DefaultNativeMode** and **FilesOnlyMode**</span></span>  
  
 <span data-ttu-id="7917b-112">如果安装包括 SQL Server 数据库引擎，则默认 RSINSTALLMODE 为 DefaultNativeMode。如果安装不包括 SQL Server 数据库引擎，则默认 RSINSTALLMODE 为 FilesOnlyMode。如果选择了 DefaultNativeMode 但安装不包括 SQL Server 数据库引擎，则安装会自动将 RSINSTALLMODE 更改为 FilesOnlyMode。</span><span class="sxs-lookup"><span data-stu-id="7917b-112">If the installation includes the SQL Server Database engine, the default RSINSTALLMODE is DefaultNativeMode.If the installation does not include the SQL Server Database engine, the default RSINSTALLMODE is FilesOnlyMode.If you choose DefaultNativeMode but the installation does not include the SQL Server Database engine, the installation automatically changes the RSINSTALLMODE to FilesOnlyMode.</span></span> <span data-ttu-id="7917b-113">有关输入设置的详细信息，请参阅[从命令提示符安装 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="7917b-113">For more information on the input settings, see [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
## <a name="rsshpinstallmode-sharepoint-mode"></a><span data-ttu-id="7917b-114">RSSHPINSTALLMODE（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="7917b-114">RSSHPINSTALLMODE (SharePoint Mode)</span></span>  
 <span data-ttu-id="7917b-115">用于在 SharePoint 模式下安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的输入设置是 **/RSSHPINSTALLMODE**。</span><span class="sxs-lookup"><span data-stu-id="7917b-115">The input setting to install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode is **/RSSHPINSTALLMODE**.</span></span> <span data-ttu-id="7917b-116">该输入设置具有一个选项：SharePointFilesOnlyMode。</span><span class="sxs-lookup"><span data-stu-id="7917b-116">The input setting has one option: SharePointFilesOnlyMode.</span></span> <span data-ttu-id="7917b-117">此选项将安装 SharePoint 模式所需的所有文件，但以下安装需要进行配置。</span><span class="sxs-lookup"><span data-stu-id="7917b-117">The option installs all the files needed for SharePoint mode but, configuration is required following installation.</span></span> <span data-ttu-id="7917b-118">使用 SharePoint 管理中心完成其他配置步骤。</span><span class="sxs-lookup"><span data-stu-id="7917b-118">The additional configuration steps are completed using SharePoint Central Administration.</span></span> <span data-ttu-id="7917b-119">有关详细信息，请参见 [安装用于 SharePoint 2010 的 Reporting Services SharePoint 模式](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="7917b-119">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>  
  
## <a name="examples-of-sharepoint-mode-installation"></a><span data-ttu-id="7917b-120">SharePoint 模式安装示例</span><span class="sxs-lookup"><span data-stu-id="7917b-120">Examples of SharePoint Mode Installation</span></span>  
 <span data-ttu-id="7917b-121">下面的示例将在 SharePoint 模式中安装 SQL Server 数据库引擎服务和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以及 SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序 (RS_SHPWFE)。</span><span class="sxs-lookup"><span data-stu-id="7917b-121">The following example installs SQL Server the database engine service and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode as well as the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint (RS_SHPWFE).</span></span>  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 <span data-ttu-id="7917b-122">下面的示例仅安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="7917b-122">The following example installs only [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="*****" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
 <span data-ttu-id="7917b-123">下面的示例将安装包括 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式和 SharePoint 模式在内的所有 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="7917b-123">The following example installs all of the SQL Server features, including both [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode and SharePoint mode.</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT, RS_SHP,RS_SHPWFE,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSSHPINSTALLMODE="SharePointFilesOnlyMode" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="examples-of-sharepoint-mode-upgrade"></a><span data-ttu-id="7917b-124">SharePoint 模式升级示例</span><span class="sxs-lookup"><span data-stu-id="7917b-124">Examples of SharePoint Mode Upgrade</span></span>  
 <span data-ttu-id="7917b-125">下面的示例将升级 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="7917b-125">The following example upgrades [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="7917b-126">**RSUPGRADEPASSWORD** 是现有 Report Server 服务帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="7917b-126">**RSUPGRADEPASSWORD** is the password of the existing Report Server service account.</span></span> <span data-ttu-id="7917b-127">RSUPGRADEPASSWORD 是升级方案中必需的字段，除非 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务帐户是内置帐户。</span><span class="sxs-lookup"><span data-stu-id="7917b-127">RSUPGRADEPASSWORD is a required field in an upgrade scenario unless the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account is a built-in account.</span></span>  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[ACCOUNTPASSSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="******"  
```  
  
 <span data-ttu-id="7917b-128">下面的示例可用于升级基于 SharePoint 共享服务体系结构的 SharePoint 模式安装。</span><span class="sxs-lookup"><span data-stu-id="7917b-128">The following example can be used to upgrade a SharePoint Mode installation that is based on the SharePoint shared service architecture.</span></span> <span data-ttu-id="7917b-129">该示例使用 ALLOWUPGRADEFORSSRSSHAREPOINTMODE 开关。</span><span class="sxs-lookup"><span data-stu-id="7917b-129">The example uses switch ALLOWUPGRADEFORSSRSSHAREPOINTMODE.</span></span> <span data-ttu-id="7917b-130">升级不基于共享服务体系结构的旧版本不需要该开关：</span><span class="sxs-lookup"><span data-stu-id="7917b-130">The switch is not needed for upgrading older versions that are not based on the shared service architecture:</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="****" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```  
  
## <a name="examples-of-native-mode-installation"></a><span data-ttu-id="7917b-131">本机模式安装示例</span><span class="sxs-lookup"><span data-stu-id="7917b-131">Examples of Native Mode Installation</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="see-also"></a><span data-ttu-id="7917b-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7917b-132">See Also</span></span>  
 <span data-ttu-id="7917b-133">[从命令提示符安装 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="7917b-133">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="7917b-134">[SysPrep 参数](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep) </span><span class="sxs-lookup"><span data-stu-id="7917b-134">[SysPrep Parameters](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep) </span></span>  
 [<span data-ttu-id="7917b-135">从命令提示符安装 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="7917b-135">Install PowerPivot from the Command Prompt</span></span>](../../sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
  
