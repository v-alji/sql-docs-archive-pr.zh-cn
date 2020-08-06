---
title: 使用升级顾问来准备升级 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server]
- upgrading SQL Server, Upgrade Advisor
- upgrading SQL Server, preparing to upgrade
- SQL Server Upgrade Advisor
- analyzing installations for upgrading [SQL Server]
ms.assetid: d85b0833-ddeb-42e3-9397-97ea60d521b7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e53d895cb19a172d0810ae9d6c2bda3406732da1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689703"
---
# <a name="use-upgrade-advisor-to-prepare-for-upgrades"></a><span data-ttu-id="014d5-102">使用升级顾问来准备升级</span><span class="sxs-lookup"><span data-stu-id="014d5-102">Use Upgrade Advisor to Prepare for Upgrades</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="014d5-103">升级顾问可以帮助您做好升级至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的准备。</span><span class="sxs-lookup"><span data-stu-id="014d5-103">Upgrade Advisor helps you prepare for upgrades to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="014d5-104">升级顾问分析早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中已安装的组件，然后生成报告，指出在升级之前或之后应解决的问题。</span><span class="sxs-lookup"><span data-stu-id="014d5-104">Upgrade Advisor analyzes installed components from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then generates a report that identifies issues to fix either before or after you upgrade.</span></span>  
  
## <a name="how-upgrade-advisor-works"></a><span data-ttu-id="014d5-105">升级顾问如何工作</span><span class="sxs-lookup"><span data-stu-id="014d5-105">How Upgrade Advisor Works</span></span>  
 <span data-ttu-id="014d5-106">运行升级顾问时，将显示“升级顾问”主页。</span><span class="sxs-lookup"><span data-stu-id="014d5-106">When you run Upgrade Advisor, the Upgrade Advisor Home page appears.</span></span> <span data-ttu-id="014d5-107">通过该主页，可以运行以下工具：</span><span class="sxs-lookup"><span data-stu-id="014d5-107">From the Home page, you can run the following tools:</span></span>  
  
-   <span data-ttu-id="014d5-108">升级顾问分析向导</span><span class="sxs-lookup"><span data-stu-id="014d5-108">Upgrade Advisor Analysis Wizard</span></span>  
  
-   <span data-ttu-id="014d5-109">升级顾问报表查看器</span><span class="sxs-lookup"><span data-stu-id="014d5-109">Upgrade Advisor Report Viewer</span></span>  
  
-   <span data-ttu-id="014d5-110">升级顾问帮助</span><span class="sxs-lookup"><span data-stu-id="014d5-110">Upgrade Advisor Help</span></span>  
  
 <span data-ttu-id="014d5-111">第一次使用升级顾问时，应运行升级顾问分析向导来分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="014d5-111">The first time that you use Upgrade Advisor, run the Upgrade Advisor Analysis Wizard to analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="014d5-112">该向导完成分析后，请使用升级顾问报表查看器查看生成的报表。</span><span class="sxs-lookup"><span data-stu-id="014d5-112">When the wizard finishes the analysis, view the resulting reports in the Upgrade Advisor Report Viewer.</span></span> <span data-ttu-id="014d5-113">每个报表中均有指向升级顾问帮助信息的链接，这些信息可帮助您修复已知问题或减少已知问题的影响。</span><span class="sxs-lookup"><span data-stu-id="014d5-113">Each report provides links to information in Upgrade Advisor Help that will help you fix or reduce the effect of the known issues.</span></span>  
  
## <a name="upgrade-advisor-analysis"></a><span data-ttu-id="014d5-114">升级顾问分析</span><span class="sxs-lookup"><span data-stu-id="014d5-114">Upgrade Advisor Analysis</span></span>  
 <span data-ttu-id="014d5-115">升级顾问会对以下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件进行分析：</span><span class="sxs-lookup"><span data-stu-id="014d5-115">Upgrade Advisor analyzes the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
 <span data-ttu-id="014d5-116">该分析会检查可以访问的对象，例如脚本、存储过程、触发器和跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="014d5-116">The analysis examines objects that can be accessed, such as scripts, stored procedures, triggers, and trace files.</span></span> <span data-ttu-id="014d5-117">升级顾问不能对桌面应用程序或加密的存储过程进行分析。</span><span class="sxs-lookup"><span data-stu-id="014d5-117">Upgrade Advisor cannot analyze desktop applications or encrypted stored procedures.</span></span>  
  
 <span data-ttu-id="014d5-118">输出的格式为 XML 报表。</span><span class="sxs-lookup"><span data-stu-id="014d5-118">Output is in the form of an XML report.</span></span> <span data-ttu-id="014d5-119">通过使用升级顾问报表查看器可查看 XML 报表。</span><span class="sxs-lookup"><span data-stu-id="014d5-119">View the XML report by using the Upgrade Advisor report viewer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="014d5-120">报表可能包含有“其他升级问题”项。</span><span class="sxs-lookup"><span data-stu-id="014d5-120">Reports might contain an "other upgrade issues" item.</span></span> <span data-ttu-id="014d5-121">此项链接至一个问题列表，其中列出的问题是升级顾问未检测到但却可能存在于服务器或应用程序中的问题。</span><span class="sxs-lookup"><span data-stu-id="014d5-121">This item links to a list of issues that are not detected by Upgrade Advisor, but might exist on your server or in your applications.</span></span> <span data-ttu-id="014d5-122">应查看无法检测的问题的列表，以确定是否由于这些无法检测的问题而必须更改服务器或应用程序。</span><span class="sxs-lookup"><span data-stu-id="014d5-122">You should review the list of undetectable issues and determine whether you must change your server or applications because of the undetectable issues.</span></span>  
  
## <a name="how-to-install-and-run-upgrade-advisor"></a><span data-ttu-id="014d5-123">如何安装和运行升级顾问</span><span class="sxs-lookup"><span data-stu-id="014d5-123">How to Install and Run Upgrade Advisor</span></span>  
 <span data-ttu-id="014d5-124">安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升级顾问的位置取决于您将分析的内容。</span><span class="sxs-lookup"><span data-stu-id="014d5-124">The location where you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor depends on what you will be analyzing.</span></span> <span data-ttu-id="014d5-125">升级顾问支持对除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之外的所有受支持组件进行远程分析。</span><span class="sxs-lookup"><span data-stu-id="014d5-125">Upgrade Advisor supports remote analysis of all supported components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="014d5-126">如果不扫描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的实例，则可在能够连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例并满足升级顾问先决条件的任何计算机中安装升级顾问。</span><span class="sxs-lookup"><span data-stu-id="014d5-126">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and that meets the Upgrade Advisor prerequisites.</span></span> <span data-ttu-id="014d5-127">有关详细信息，请参阅 [支持的版本升级](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="014d5-127">For more information, see [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).</span></span> <span data-ttu-id="014d5-128">如果要扫描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]实例，则必须在报表服务器上安装升级顾问。</span><span class="sxs-lookup"><span data-stu-id="014d5-128">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="014d5-129">升级顾问在功能包中提供。</span><span class="sxs-lookup"><span data-stu-id="014d5-129">Upgrade Advisor is available in a feature pack.</span></span>  
  
 <span data-ttu-id="014d5-130">安装和运行升级顾问的前提条件如下：</span><span class="sxs-lookup"><span data-stu-id="014d5-130">Prerequisites for installing and running Upgrade Advisor are as follows:</span></span>  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] <span data-ttu-id="014d5-131">SP2、Windows 7 SP1 和 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1。</span><span class="sxs-lookup"><span data-stu-id="014d5-131">SP2, Windows 7 SP1, and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span>  
  
-   <span data-ttu-id="014d5-132">Windows Installer（最低为 4.5 版）。</span><span class="sxs-lookup"><span data-stu-id="014d5-132">Windows Installer beginning with version 4.5.</span></span> <span data-ttu-id="014d5-133">你可以从[Windows Installer](https://www.microsoft.com/download/details.aspx?id=8483)网站安装 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="014d5-133">You can install Windows Installer from the [Windows Installer Web site](https://www.microsoft.com/download/details.aspx?id=8483).</span></span>  
  
-   <span data-ttu-id="014d5-134">Microsoft .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="014d5-134">Microsoft .NET Framework 4.</span></span> <span data-ttu-id="014d5-135">在产品媒体上提供 .NET Framework 4 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，并从[.NET Framework 4 下载页](https://go.microsoft.com/fwlink/?LinkId=209895)获取。</span><span class="sxs-lookup"><span data-stu-id="014d5-135">.NET Framework 4 is available on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] product media, and from the [.NET Framework 4 download page](https://go.microsoft.com/fwlink/?LinkId=209895).</span></span>  
  
    -   <span data-ttu-id="014d5-136">若要从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 介质安装 .NET Framework 4，请找到磁盘驱动器的根目录。</span><span class="sxs-lookup"><span data-stu-id="014d5-136">To install the .NET Framework 4 from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] media, locate the root of the disk drive.</span></span> <span data-ttu-id="014d5-137">然后双击 \redist 文件夹，再双击 DotNetFrameworks 文件夹，然后运行 dotNetFx40_Full_x86_x64.exe（对于 32 位操作系统或 64 位操作系统）。</span><span class="sxs-lookup"><span data-stu-id="014d5-137">Then, double-click the \redist folder, double-click the DotNetFrameworks folder, and run dotNetFx40_Full_x86_x64.exe (for 32-bit operating systems or for 64-bit operating systems).</span></span>  
  
 <span data-ttu-id="014d5-138">若要通过 Web 安装升级顾问，请单击下载页上的下载按钮。</span><span class="sxs-lookup"><span data-stu-id="014d5-138">To install Upgrade Advisor from the Web, click the download button on the download page.</span></span> <span data-ttu-id="014d5-139">随后可以立即运行安装程序，也可以保存 SQLUA.msi 文件并稍后运行它。</span><span class="sxs-lookup"><span data-stu-id="014d5-139">You can then run installation immediately, or save the SQLUA.msi file to run later.</span></span> <span data-ttu-id="014d5-140">如果要从产品光盘进行安装，请直接从产品磁盘运行 SQLUA.msi。</span><span class="sxs-lookup"><span data-stu-id="014d5-140">If you are installing from the product disc, run SQLUA.msi directly from the product disk.</span></span>  
  
 <span data-ttu-id="014d5-141">安装升级顾问之后，您可以从 "**开始**" 菜单中打开它：</span><span class="sxs-lookup"><span data-stu-id="014d5-141">After you install Upgrade Advisor, you can open it from the **Start** menu:</span></span>  
  
-   <span data-ttu-id="014d5-142">单击 "**开始**"，指向 "**所有程序**"，指向 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] ""，然后单击 " \*\* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 升级顾问\*\*"。</span><span class="sxs-lookup"><span data-stu-id="014d5-142">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], and then click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.</span></span>  
  
 <span data-ttu-id="014d5-143">有关详细信息，请参阅升级顾问下载和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 发行说明中包括的 Upgrade Advisor 文档。</span><span class="sxs-lookup"><span data-stu-id="014d5-143">For more information, see the Upgrade Advisor documentation included in the Upgrade Advisor download and the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Release Notes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014d5-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="014d5-144">See Also</span></span>  
 <span data-ttu-id="014d5-145">[使用 SQL Server 的多个版本和实例](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="014d5-145">[Work with Multiple Versions and Instances of SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span></span>  
 <span data-ttu-id="014d5-146">[支持的版本升级](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="014d5-146">[Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 [<span data-ttu-id="014d5-147">向后兼容性</span><span class="sxs-lookup"><span data-stu-id="014d5-147">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
