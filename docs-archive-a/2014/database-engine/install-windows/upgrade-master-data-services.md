---
title: 升级 Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a0f137d6ca5a68a72e381780505ec8c93ae3c740
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580354"
---
# <a name="upgrade-master-data-services"></a><span data-ttu-id="73cf5-102">升级 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="73cf5-102">Upgrade Master Data Services</span></span>
  <span data-ttu-id="73cf5-103">有四种升级到 Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 的方案。</span><span class="sxs-lookup"><span data-stu-id="73cf5-103">There are four scenarios for upgrading to Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="73cf5-104">请选择适用于您情况的方案。</span><span class="sxs-lookup"><span data-stu-id="73cf5-104">Choose the scenario that fits your situation.</span></span>  
  
-   [<span data-ttu-id="73cf5-105">升级（不升级数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="73cf5-105">Upgrade without Database Engine Upgrade</span></span>](#noengine)  
  
-   [<span data-ttu-id="73cf5-106">升级（升级数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="73cf5-106">Upgrade with Database Engine Upgrade</span></span>](#engine)  
  
-   [<span data-ttu-id="73cf5-107">在两台计算机上执行升级的方案</span><span class="sxs-lookup"><span data-stu-id="73cf5-107">Upgrade in Two-Computer Scenario</span></span>](#twocomputer)  
  
-   [<span data-ttu-id="73cf5-108">通过从备份还原数据库升级</span><span class="sxs-lookup"><span data-stu-id="73cf5-108">Upgrade with Restoring a Database from Backup</span></span>](#restore)  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="73cf5-109">不支持从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 版升级到 CTP2 版。</span><span class="sxs-lookup"><span data-stu-id="73cf5-109">Upgrading from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 release to the CTP2 release is not supported.</span></span>  
> -   <span data-ttu-id="73cf5-110">在执行任何升级之前备份您的数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-110">Back up your database before performing any upgrade.</span></span>  
> -   <span data-ttu-id="73cf5-111">升级过程将重新创建存储过程并对 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]所使用的表进行升级。</span><span class="sxs-lookup"><span data-stu-id="73cf5-111">The upgrade process recreates stored procedures and upgrades tables used by [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="73cf5-112">您对这些组件中的任何一个所做的任何自定义内容可能会丢失。</span><span class="sxs-lookup"><span data-stu-id="73cf5-112">Any customizations you have made to either of these components may be lost.</span></span>  
> -   <span data-ttu-id="73cf5-113">模型部署包只能在创建它们的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中使用。</span><span class="sxs-lookup"><span data-stu-id="73cf5-113">Model deployment packages can be used only in the edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] they were created in.</span></span> <span data-ttu-id="73cf5-114">不能将在中创建的模型部署包部署 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 到中 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-114">You cannot deploy model deployment packages created in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
> -   <span data-ttu-id="73cf5-115">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 在将 Master Data Services 和 Data Quality Services 升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 后，您可以使用用于 Excel 的 Master Data Services 外接程序的  SP1 版本继续进行。</span><span class="sxs-lookup"><span data-stu-id="73cf5-115">You can continue using the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel after upgrading Master Data Services and Data Quality Services to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="73cf5-116">但是，在升级到 SQL Server 2014 CTP2 后，用于 Excel 的 Master Data Services 外接程序的任何早期版本都无法使用。</span><span class="sxs-lookup"><span data-stu-id="73cf5-116">However, any earlier version of the Master Data Services Add-In for Excel will not work after upgrading to SQL Server 2014 CTP2.</span></span> <span data-ttu-id="73cf5-117">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 您可以从 [此处](https://go.microsoft.com/fwlink/?LinkId=328664)下载用于 Excel 的 Master Data Services 外接程序的  SP1 版本。</span><span class="sxs-lookup"><span data-stu-id="73cf5-117">You can download the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel from [here](https://go.microsoft.com/fwlink/?LinkId=328664).</span></span>  
  
##  <a name="upgrade-without-database-engine-upgrade"></a><a name="noengine"></a> <span data-ttu-id="73cf5-118">升级（不升级数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="73cf5-118">Upgrade without Database Engine Upgrade</span></span>  
 <span data-ttu-id="73cf5-119">此方案可被视为并行安装，因为 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 均并行安装在同一台计算机或不同的计算机上。</span><span class="sxs-lookup"><span data-stu-id="73cf5-119">This scenario can be considered a side-by-side installation, because both [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] are installed in parallel, on either the same computer or separate computers.</span></span>  
  
 <span data-ttu-id="73cf5-120">在此方案中，您继续使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 承载 MDS 数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-120">In this scenario you continue to use [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to host your MDS database.</span></span> <span data-ttu-id="73cf5-121">但是，必须升级 MDS 数据库的架构，然后创建 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序来访问 MDS 数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-121">However, you must upgrade the schema of the MDS database, and then create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application to access the MDS database.</span></span> <span data-ttu-id="73cf5-122">MDS 数据库不再可以由 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Web 应用程序访问。</span><span class="sxs-lookup"><span data-stu-id="73cf5-122">The MDS database can no longer be accessed by the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] web application.</span></span>  
  
 <span data-ttu-id="73cf5-123">如果选择在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 同一台计算机上安装和早期版本的 SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) ，则可以这样做，因为文件安装在不同的位置。</span><span class="sxs-lookup"><span data-stu-id="73cf5-123">If you choose to install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) on the same computer, you can do so because the files are installed in a different location.</span></span>  
  
-   <span data-ttu-id="73cf5-124">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，默认情况下这些文件安装在驱动器:\Program Files\Microsoft SQL Server\120\Master Data Services 中。</span><span class="sxs-lookup"><span data-stu-id="73cf5-124">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span>  
  
-   <span data-ttu-id="73cf5-125">在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中，默认情况下这些文件安装在驱动器:\Program Files\Microsoft SQL Server\110\Master Data Services 中。</span><span class="sxs-lookup"><span data-stu-id="73cf5-125">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\110\Master Data Services.</span></span>  
  
-   <span data-ttu-id="73cf5-126">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中，默认情况下这些文件安装在驱动器:\Program Files\Microsoft SQL Server\Master Data Services 中。</span><span class="sxs-lookup"><span data-stu-id="73cf5-126">In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\Master Data Services.</span></span>  
  
 <span data-ttu-id="73cf5-127">若要执行此任务，请完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="73cf5-127">To perform this task, complete the following steps.</span></span>  
  
1.  <span data-ttu-id="73cf5-128">安装 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 和所需的任何其他功能。</span><span class="sxs-lookup"><span data-stu-id="73cf5-128">Install [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] and any other features you want.</span></span>  
  
    1.  <span data-ttu-id="73cf5-129">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-129">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="73cf5-130">在左窗格中，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-130">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-131">在右窗格中，单击“全新 SQL Server 独立安装或向现有安装添加功能”。</span><span class="sxs-lookup"><span data-stu-id="73cf5-131">In the right pane, click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
    4.  <span data-ttu-id="73cf5-132">在 **“功能选择”** 页上，选择 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 和要安装的任何其他功能。</span><span class="sxs-lookup"><span data-stu-id="73cf5-132">On the **Feature Selection** page, select **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** and any other features you want to install.</span></span>  
  
    5.  <span data-ttu-id="73cf5-133">完成向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-133">Complete the wizard.</span></span>  
  
2.  <span data-ttu-id="73cf5-134">安装完成后，升级 MDS 数据库架构。</span><span class="sxs-lookup"><span data-stu-id="73cf5-134">When the installation is complete, upgrade the MDS database schema.</span></span>  
  
    1.  <span data-ttu-id="73cf5-135">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-135">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="73cf5-136">若要升级 MDS 数据库架构，您必须以在创建 MDS 数据库时指定的管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="73cf5-136">To upgrade the MDS database schema, you must be logged in as the Administrator Account that was specified when the MDS database was created.</span></span> <span data-ttu-id="73cf5-137">在 MDS 数据库的 mdm.tblUser 中，此用户的 **ID** 值为 **1**。</span><span class="sxs-lookup"><span data-stu-id="73cf5-137">In the MDS database, in mdm.tblUser, this user has the **ID** value of **1**.</span></span> <span data-ttu-id="73cf5-138">有关更改此用户的信息，请参阅[更改系统管理员帐户 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-138">For information on changing this user, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
    2.  <span data-ttu-id="73cf5-139">在左窗格中单击 **“数据库配置”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-139">In the left pane, click **Database Configuration**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-140">在右侧窗格中，单击 "**选择数据库**" 并指定 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 数据库实例的信息。</span><span class="sxs-lookup"><span data-stu-id="73cf5-140">In the right pane, click **Select Database** and specify the information for your [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database instance.</span></span>  
  
    4.  <span data-ttu-id="73cf5-141">单击 **“升级数据库”** 以启动 **“升级数据库向导”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-141">Click **Upgrade Database** to start the **Upgrade Database Wizard**.</span></span> <span data-ttu-id="73cf5-142">有关详细信息，请参阅[升级数据库向导（Master Data Services 配置管理器）](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-142">For more information, see [Upgrade Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="73cf5-143">升级完成时，创建一个 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-143">When the upgrade is complete, create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application.</span></span>  
  
    1.  <span data-ttu-id="73cf5-144">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-144">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
    2.  <span data-ttu-id="73cf5-145">在左窗格中单击 **“Web 配置”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-145">In the left pane, click **Web Configuration**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-146">在右窗格中，从 **“网站”** 列表选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="73cf5-146">In the right pane, from the **Website** list, select one of the following options:</span></span>  
  
        -   <span data-ttu-id="73cf5-147">**“默认网站”** ，然后单击 **“创建应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-147">**Default Web Site**, then click **Create Application**.</span></span>  
  
        -   <span data-ttu-id="73cf5-148">**“创建新站点”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-148">**Create new site**.</span></span> <span data-ttu-id="73cf5-149">创建网站时，将自动创建新的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-149">A new web application is automatically created when the website is created.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="73cf5-150">在 SQL Server 2014 版 Master Data Services 配置管理器中，您可以选择 SQL Server 早期版本（[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]）的现有 MDS Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-150">Your existing MDS web application from an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) is available for selection in the SQL Server 2014 version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="73cf5-151">您不能选择现有 Web 应用程序，而是必须为 MDS 创建一个 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-151">You must not select the existing web application, and instead must create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application for MDS.</span></span> <span data-ttu-id="73cf5-152">否则，在您尝试将 Web 应用程序与升级的 MDS 数据库关联时，您会收到错误，指出无法访问请求的页面，因为该页的相关配置数据无效。</span><span class="sxs-lookup"><span data-stu-id="73cf5-152">Otherwise, you will receive an error when you try to associate the web application with the upgraded MDS database stating that the requested page cannot be accessed because the related configuration data for the page is invalid.</span></span>  
        >   
        >  <span data-ttu-id="73cf5-153">如果您要为 MDS Web 应用程序使用与现有（[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]）Web 应用程序相同的名字（别名），您必须首先从 IIS 中删除该 Web 应用程序和关联的应用程序池，然后使用 SQL Server 2014 版 Master Data Services 配置管理器创建同名的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-153">If you want to use the same name (alias) for MDS web application as your existing ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) web application, you must first delete the web application and the associated application pool from IIS, and then create a web application with the same name using SQL Server 2014 version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="73cf5-154">有关从 IIS 删除 Web 应用程序和应用程序池的信息，请参阅 [删除应用程序 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) 和 [删除应用程序池 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-154">For information about removing web application and application pools from IIS, see [Remove an Application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) and [Remove an Application Pool (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).</span></span>  
  
4.  <span data-ttu-id="73cf5-155">现在将新 Web 应用程序与已升级的 MDS 数据库关联。</span><span class="sxs-lookup"><span data-stu-id="73cf5-155">Now associate the new web application with the upgraded MDS database.</span></span>  
  
    1.  <span data-ttu-id="73cf5-156">在 **“将应用程序与数据库相关联”** 部分中，单击 **“选择”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-156">In the **Associate Application with Database** section, click **Select**.</span></span>  
  
    2.  <span data-ttu-id="73cf5-157">选择 MDS 数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-157">Select the MDS database.</span></span>  
  
    3.  <span data-ttu-id="73cf5-158">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="73cf5-158">Click **Apply**.</span></span>  
  
##  <a name="upgrade-with-database-engine-upgrade"></a><a name="engine"></a> <span data-ttu-id="73cf5-159">升级（升级数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="73cf5-159">Upgrade with Database Engine Upgrade</span></span>  
 <span data-ttu-id="73cf5-160">在此方案中，您同时将数据库引擎和 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 应用程序从 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 SQL Server 2012 升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-160">In this scenario you will upgrade both the database engine and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] application from [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or SQL Server 2012 to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="73cf5-161">若要执行此任务，请完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="73cf5-161">To perform this task, complete the following steps.</span></span>  
  
1.  <span data-ttu-id="73cf5-162">仅适用于 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]：打开“控制面板” > “程序和功能”，然后卸载 Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-162">**For [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] only**: Open **Control Panel** > **Programs and Features** and uninstall Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span>  
  
2.  <span data-ttu-id="73cf5-163">将数据引擎升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-163">Upgrade the database engine to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    1.  <span data-ttu-id="73cf5-164">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-164">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="73cf5-165">在左窗格中，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-165">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-166">在右侧窗格中，单击 "**从 SQL Server 2005 升级，SQL Server 2008"，SQL Server 2008 R2 或 SQL Server 2012**。</span><span class="sxs-lookup"><span data-stu-id="73cf5-166">In the right pane, click **Upgrade from SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 or SQL Server 2012**.</span></span>  
  
    4.  <span data-ttu-id="73cf5-167">完成向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-167">Complete the wizard.</span></span>  
  
3.  <span data-ttu-id="73cf5-168">\*\* [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 仅适用于\*\*：升级完成时，添加 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 功能。</span><span class="sxs-lookup"><span data-stu-id="73cf5-168">**For [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] only**: When the upgrade is complete, add the **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** feature.</span></span>  
  
    1.  <span data-ttu-id="73cf5-169">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-169">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="73cf5-170">在左窗格中，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-170">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-171">在右窗格中，单击“全新 SQL Server 独立安装或向现有安装添加功能”。</span><span class="sxs-lookup"><span data-stu-id="73cf5-171">In the right pane, click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
    4.  <span data-ttu-id="73cf5-172">在向导的 "**安装类型**" 页上，选择 "向**现有实例中添加功能**" 选项，然后选择安装 MDS 数据库的实例。</span><span class="sxs-lookup"><span data-stu-id="73cf5-172">On the **Installation Type** page of the wizard, select the **Add features to an existing instance** option, and choose the instance where MDS database is installed.</span></span>  
  
    5.  <span data-ttu-id="73cf5-173">在 "**功能选择**" 页上的 "**共享功能**" 下，选择 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-173">On the **Feature Selection** page, under **Shared Features**, select **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]**.</span></span>  
  
    6.  <span data-ttu-id="73cf5-174">完成向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-174">Complete the wizard.</span></span>  
  
4.  <span data-ttu-id="73cf5-175">升级 MDS 数据库架构。</span><span class="sxs-lookup"><span data-stu-id="73cf5-175">Upgrade the MDS database schema.</span></span>  
  
    1.  <span data-ttu-id="73cf5-176">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-176">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="73cf5-177">若要升级 MDS 数据库架构，您必须以在创建 MDS 数据库时指定的管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="73cf5-177">To upgrade the MDS database schema, you must be logged in as the Administrator Account that was specified when the MDS database was created.</span></span> <span data-ttu-id="73cf5-178">在 MDS 数据库的 mdm.tblUser 中，此用户的 **ID** 值为 **1**。</span><span class="sxs-lookup"><span data-stu-id="73cf5-178">In the MDS database, in mdm.tblUser, this user has the **ID** value of **1**.</span></span> <span data-ttu-id="73cf5-179">有关更改此用户的信息，请参阅[更改系统管理员帐户 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-179">For information on changing this user, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
    2.  <span data-ttu-id="73cf5-180">在左窗格中单击 **“数据库配置”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-180">In the left pane, click **Database Configuration**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-181">在右侧窗格中，单击 "**选择数据库**" 并指定数据库实例的信息。</span><span class="sxs-lookup"><span data-stu-id="73cf5-181">In the right pane, click **Select Database** and specify the information for your database instance.</span></span>  
  
    4.  <span data-ttu-id="73cf5-182">单击 **“升级数据库”** 以启动 **“升级数据库向导”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-182">Click **Upgrade Database** to start the **Upgrade Database Wizard**.</span></span> <span data-ttu-id="73cf5-183">有关详细信息，请参阅[升级数据库向导（Master Data Services 配置管理器）](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-183">For more information, see [Upgrade Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
    5.  <span data-ttu-id="73cf5-184">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="73cf5-184">Click **Apply**.</span></span>  
  
5.  <span data-ttu-id="73cf5-185">升级完成时，创建一个 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-185">When the upgrade is complete, create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application.</span></span>  
  
    1.  <span data-ttu-id="73cf5-186">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-186">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
    2.  <span data-ttu-id="73cf5-187">在左窗格中单击 **“Web 配置”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-187">In the left pane, click **Web Configuration**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-188">在右窗格中，从 **“网站”** 列表选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="73cf5-188">In the right pane, from the **Website** list, select one of the following options:</span></span>  
  
        -   <span data-ttu-id="73cf5-189">**“默认网站”** ，然后单击 **“创建应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-189">**Default Web Site**, then click **Create Application**.</span></span>  
  
        -   <span data-ttu-id="73cf5-190">**“创建新站点”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-190">**Create new site**.</span></span> <span data-ttu-id="73cf5-191">创建网站时，将自动创建新的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-191">A new web application is automatically created when the website is created.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="73cf5-192">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版 Master Data Services 配置管理器中，您可以选择 SQL Server 早期版本（[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]）的现有 MDS Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-192">Your existing MDS web application from an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) is available for selection in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="73cf5-193">您不能选择现有 Web 应用程序，而是必须为 MDS 创建一个 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-193">You must not select the existing web application, and instead must create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application for MDS.</span></span> <span data-ttu-id="73cf5-194">否则，在您尝试将 Web 应用程序与升级的 MDS 数据库关联时，您会收到错误，指出无法访问请求的页面，因为该页的相关配置数据无效。</span><span class="sxs-lookup"><span data-stu-id="73cf5-194">Otherwise, you will receive an error when you try to associate the web application with the upgraded MDS database stating that the requested page cannot be accessed because the related configuration data for the page is invalid.</span></span>  
        >   
        >  <span data-ttu-id="73cf5-195">如果您要为 MDS Web 应用程序使用与现有（[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]）Web 应用程序相同的名字（别名），您必须首先从 IIS 中删除该 Web 应用程序和关联的应用程序池，然后使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版 Master Data Services 配置管理器创建同名的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-195">If you want to use the same name (alias) for MDS web application as your existing ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) web application, you must first delete the web application and the associated application pool from IIS, and then create a web application with the same name using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="73cf5-196">有关从 IIS 删除 Web 应用程序和应用程序池的信息，请参阅 [删除应用程序 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) 和 [删除应用程序池 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-196">For information about removing web application and application pools from IIS, see [Remove an Application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) and [Remove an Application Pool (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).</span></span>  
  
6.  <span data-ttu-id="73cf5-197">现在将新 Web 应用程序与已升级的 MDS 数据库关联。</span><span class="sxs-lookup"><span data-stu-id="73cf5-197">Now associate the new web application with the upgraded MDS database.</span></span>  
  
    1.  <span data-ttu-id="73cf5-198">在 **“将应用程序与数据库相关联”** 部分中，单击 **“选择”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-198">In the **Associate Application with Database** section, click **Select**.</span></span>  
  
    2.  <span data-ttu-id="73cf5-199">选择 MDS 数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-199">Select the MDS database.</span></span>  
  
    3.  <span data-ttu-id="73cf5-200">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="73cf5-200">Click **Apply**.</span></span>  
  
##  <a name="upgrade-in-two-computer-scenario"></a><a name="twocomputer"></a> <span data-ttu-id="73cf5-201">在两台计算机上执行升级的方案</span><span class="sxs-lookup"><span data-stu-id="73cf5-201">Upgrade in Two-Computer Scenario</span></span>  
 <span data-ttu-id="73cf5-202">此方案涉及升级在两台计算机上安装 SQL Server 的系统：一台计算机安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，另一台计算机安装 SQL Server 2008 R2 或 SQL Server 2012。</span><span class="sxs-lookup"><span data-stu-id="73cf5-202">This scenario involves upgrading a system in which SQL Server is installed on two computers: one with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], and the other with SQL Server 2008 R2 or SQL Server 2012.</span></span>  
  
 <span data-ttu-id="73cf5-203">如果安装 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，您将继续分别使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 在一台计算机上承载 MDS 数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-203">If [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] is installed, you continue to use [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] respectively to host your MDS database on one computer.</span></span> <span data-ttu-id="73cf5-204">但是，必须升级 MDS 数据库的架构，然后使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序来访问 MDS 数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-204">However, you must upgrade the schema of the MDS database, and then use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application to access the MDS database.</span></span> <span data-ttu-id="73cf5-205">MDS 数据库不再可以由 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Web 应用程序访问。</span><span class="sxs-lookup"><span data-stu-id="73cf5-205">The MDS database can no longer be accessed by the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] web application.</span></span>  
  
-   <span data-ttu-id="73cf5-206">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，默认情况下这些文件安装在驱动器:\Program Files\Microsoft SQL Server\120\Master Data Services 中。</span><span class="sxs-lookup"><span data-stu-id="73cf5-206">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span>  
  
-   <span data-ttu-id="73cf5-207">在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中，默认情况下这些文件安装在驱动器:\Program Files\Microsoft SQL Server\110\Master Data Services 中。</span><span class="sxs-lookup"><span data-stu-id="73cf5-207">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\110\Master Data Services.</span></span>  
  
-   <span data-ttu-id="73cf5-208">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中，默认情况下这些文件安装在驱动器:\Program Files\Microsoft SQL Server\Master Data Services 中。</span><span class="sxs-lookup"><span data-stu-id="73cf5-208">In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\Master Data Services.</span></span>  
  
 <span data-ttu-id="73cf5-209">若要执行此任务，请完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="73cf5-209">To perform this task, complete the following steps.</span></span>  
  
1.  <span data-ttu-id="73cf5-210">安装 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 和所需的任何其他功能。</span><span class="sxs-lookup"><span data-stu-id="73cf5-210">Install [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] and any other features you want.</span></span>  
  
    1.  <span data-ttu-id="73cf5-211">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-211">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="73cf5-212">在左窗格中，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-212">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-213">在右窗格中，单击“全新 SQL Server 独立安装或向现有安装添加功能”。</span><span class="sxs-lookup"><span data-stu-id="73cf5-213">In the right pane, click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
    4.  <span data-ttu-id="73cf5-214">在 **“功能选择”** 页上，选择 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 和要安装的任何其他功能。</span><span class="sxs-lookup"><span data-stu-id="73cf5-214">On the **Feature Selection** page, select **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** and any other features you want to install.</span></span>  
  
    5.  <span data-ttu-id="73cf5-215">完成向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-215">Complete the wizard.</span></span>  
  
2.  <span data-ttu-id="73cf5-216">安装完成后，升级 MDS 数据库架构。</span><span class="sxs-lookup"><span data-stu-id="73cf5-216">When the installation is complete, upgrade the MDS database schema.</span></span>  
  
    1.  <span data-ttu-id="73cf5-217">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-217">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="73cf5-218">若要升级 MDS 数据库架构，您必须以在创建 MDS 数据库时指定的管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="73cf5-218">To upgrade the MDS database schema, you must be logged in as the Administrator Account that was specified when the MDS database was created.</span></span> <span data-ttu-id="73cf5-219">在 MDS 数据库的 mdm.tblUser 中，此用户的 **ID** 值为 **1**。</span><span class="sxs-lookup"><span data-stu-id="73cf5-219">In the MDS database, in mdm.tblUser, this user has the **ID** value of **1**.</span></span> <span data-ttu-id="73cf5-220">有关更改此用户的信息，请参阅[更改系统管理员帐户 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-220">For information on changing this user, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
    2.  <span data-ttu-id="73cf5-221">在左窗格中单击 **“数据库配置”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-221">In the left pane, click **Database Configuration**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-222">在右侧窗格中，单击 "**选择数据库**"，然后在另 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 一 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 台计算机上安装或数据库实例的信息（如果在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 其他计算机上安装了或） [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-222">In the right pane, click **Select Database** and specify the information for your [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database instance on the other computer, if [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] is installed on the other computer.</span></span>  
  
    4.  <span data-ttu-id="73cf5-223">单击 **“升级数据库”** 以启动 **“升级数据库向导”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-223">Click **Upgrade Database** to start the **Upgrade Database Wizard**.</span></span> <span data-ttu-id="73cf5-224">有关详细信息，请参阅[升级数据库向导（Master Data Services 配置管理器）](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-224">For more information, see [Upgrade Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="73cf5-225">升级完成时，创建一个 SQL Server 2014 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-225">When the upgrade is complete, create a SQL Server 2014 web application.</span></span>  
  
    1.  <span data-ttu-id="73cf5-226">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-226">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
    2.  <span data-ttu-id="73cf5-227">在左窗格中单击 **“Web 配置”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-227">In the left pane, click **Web Configuration**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-228">在右窗格中，从 **“网站”** 列表选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="73cf5-228">In the right pane, from the **Website** list, select one of the following options:</span></span>  
  
        -   <span data-ttu-id="73cf5-229">**“默认网站”** ，然后单击 **“创建应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-229">**Default Web Site**, then click **Create Application**.</span></span>  
  
        -   <span data-ttu-id="73cf5-230">**“创建新站点”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-230">**Create new site**.</span></span> <span data-ttu-id="73cf5-231">创建网站时，将自动创建新的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-231">A new web application is automatically created when the website is created.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="73cf5-232">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版 Master Data Services 配置管理器中，您可以选择 SQL Server 早期版本（[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]）的现有 MDS Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-232">Your existing MDS web application from an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) is available for selection in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="73cf5-233">您不能选择现有 Web 应用程序，而是必须为 MDS 创建一个 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-233">You must not select the existing web application, and instead must create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application for MDS.</span></span> <span data-ttu-id="73cf5-234">否则，在您尝试将 Web 应用程序与升级的 MDS 数据库关联时，您会收到错误，指出无法访问请求的页面，因为该页的相关配置数据无效。</span><span class="sxs-lookup"><span data-stu-id="73cf5-234">Otherwise, you will receive an error when you try to associate the web application with the upgraded MDS database stating that the requested page cannot be accessed because the related configuration data for the page is invalid.</span></span>  
        >   
        >  <span data-ttu-id="73cf5-235">如果您要为 MDS Web 应用程序使用与现有（[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]）Web 应用程序相同的名字（别名），您必须首先从 IIS 中删除该 Web 应用程序和关联的应用程序池，然后使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版 Master Data Services 配置管理器创建同名的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-235">If you want to use the same name (alias) for MDS web application as your existing ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) web application, you must first delete the web application and the associated application pool from IIS, and then create a web application with the same name using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="73cf5-236">有关从 IIS 删除 Web 应用程序和应用程序池的信息，请参阅 [删除应用程序 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) 和 [删除应用程序池 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-236">For information about removing web application and application pools from IIS, see [Remove an Application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) and [Remove an Application Pool (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).</span></span>  
  
4.  <span data-ttu-id="73cf5-237">现在将 Web 应用程序与已升级的 MDS 数据库关联。</span><span class="sxs-lookup"><span data-stu-id="73cf5-237">Now associate the web application with the upgraded MDS database.</span></span>  
  
    1.  <span data-ttu-id="73cf5-238">在 **“将应用程序与数据库相关联”** 部分中，单击 **“选择”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-238">In the **Associate Application with Database** section, click **Select**.</span></span>  
  
    2.  <span data-ttu-id="73cf5-239">选择 MDS 数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-239">Select the MDS database.</span></span>  
  
    3.  <span data-ttu-id="73cf5-240">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="73cf5-240">Click **Apply**.</span></span>  
  
##  <a name="upgrade-with-restoring-a-database-from-backup"></a><a name="restore"></a> <span data-ttu-id="73cf5-241">通过从备份还原数据库升级</span><span class="sxs-lookup"><span data-stu-id="73cf5-241">Upgrade with Restoring a Database from Backup</span></span>  
 <span data-ttu-id="73cf5-242">在此方案中，[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 与 SQL Server 2008 R2 或 SQL Server 2012 安装在同一台或两台不同的计算机上。</span><span class="sxs-lookup"><span data-stu-id="73cf5-242">In this scenario, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is installed along with SQL Server 2008 R2 or SQL Server 2012 on the same computer or two different computers.</span></span> <span data-ttu-id="73cf5-243">另外，在升级前，在低于 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 的版本上备份数据库，必须还原该数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-243">Also, a database was backed up on a version earlier than the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 release, prior to upgrade, and the database has to be restored.</span></span>  
  
-   <span data-ttu-id="73cf5-244">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，默认情况下这些文件安装在驱动器:\Program Files\Microsoft SQL Server\120\Master Data Services 中。</span><span class="sxs-lookup"><span data-stu-id="73cf5-244">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span>  
  
-   <span data-ttu-id="73cf5-245">在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中，默认情况下这些文件安装在驱动器:\Program Files\Microsoft SQL Server\110\Master Data Services 中。</span><span class="sxs-lookup"><span data-stu-id="73cf5-245">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\110\Master Data Services.</span></span>  
  
-   <span data-ttu-id="73cf5-246">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中，默认情况下这些文件安装在驱动器:\Program Files\Microsoft SQL Server\Master Data Services 中。</span><span class="sxs-lookup"><span data-stu-id="73cf5-246">In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\Master Data Services.</span></span>  
  
 <span data-ttu-id="73cf5-247">若要执行此任务，请完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="73cf5-247">To perform this task, complete the following steps.</span></span>  
  
1.  <span data-ttu-id="73cf5-248">安装 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 和所需的任何其他功能。</span><span class="sxs-lookup"><span data-stu-id="73cf5-248">Install [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] and any other features you want.</span></span>  
  
    1.  <span data-ttu-id="73cf5-249">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-249">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="73cf5-250">在左窗格中，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-250">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-251">在右窗格中，单击“全新 SQL Server 独立安装或向现有安装添加功能”。</span><span class="sxs-lookup"><span data-stu-id="73cf5-251">In the right pane, click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
    4.  <span data-ttu-id="73cf5-252">在 **“功能选择”** 页上，选择 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 和要安装的任何其他功能。</span><span class="sxs-lookup"><span data-stu-id="73cf5-252">On the **Feature Selection** page, select **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** and any other features you want to install.</span></span>  
  
    5.  <span data-ttu-id="73cf5-253">完成向导。</span><span class="sxs-lookup"><span data-stu-id="73cf5-253">Complete the wizard.</span></span>  
  
2.  <span data-ttu-id="73cf5-254">还原已备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-254">Restore the database that was backed up.</span></span>  
  
3.  <span data-ttu-id="73cf5-255">安装完成后，升级 MDS 数据库架构。</span><span class="sxs-lookup"><span data-stu-id="73cf5-255">When the installation is complete, upgrade the MDS database schema.</span></span>  
  
    1.  <span data-ttu-id="73cf5-256">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-256">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="73cf5-257">若要升级 MDS 数据库架构，您必须以在创建 MDS 数据库时指定的管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="73cf5-257">To upgrade the MDS database schema, you must be logged in as the Administrator Account that was specified when the MDS database was created.</span></span> <span data-ttu-id="73cf5-258">在 MDS 数据库的 mdm.tblUser 中，此用户的 **ID** 值为 **1**。</span><span class="sxs-lookup"><span data-stu-id="73cf5-258">In the MDS database, in mdm.tblUser, this user has the **ID** value of **1**.</span></span> <span data-ttu-id="73cf5-259">有关更改此用户的信息，请参阅[更改系统管理员帐户 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-259">For information on changing this user, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
    2.  <span data-ttu-id="73cf5-260">在左窗格中单击 **“数据库配置”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-260">In the left pane, click **Database Configuration**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-261">在右侧窗格中，单击 "**选择数据库**" 并指定 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 数据库实例的信息。</span><span class="sxs-lookup"><span data-stu-id="73cf5-261">In the right pane, click **Select Database** and specify the information for your [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database instance.</span></span>  
  
    4.  <span data-ttu-id="73cf5-262">单击 **“升级数据库”** 以启动 **“升级数据库向导”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-262">Click **Upgrade Database** to start the **Upgrade Database Wizard**.</span></span> <span data-ttu-id="73cf5-263">有关详细信息，请参阅[升级数据库向导（Master Data Services 配置管理器）](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-263">For more information, see [Upgrade Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
4.  <span data-ttu-id="73cf5-264">升级完成时，创建一个 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-264">When the upgrade is complete, create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application.</span></span>  
  
    1.  <span data-ttu-id="73cf5-265">打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73cf5-265">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
    2.  <span data-ttu-id="73cf5-266">在左窗格中单击 **“Web 配置”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-266">In the left pane, click **Web Configuration**.</span></span>  
  
    3.  <span data-ttu-id="73cf5-267">在右窗格中，从 **“网站”** 列表选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="73cf5-267">In the right pane, from the **Website** list, select one of the following options:</span></span>  
  
        -   <span data-ttu-id="73cf5-268">**“默认网站”** ，然后单击 **“创建应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-268">**Default Web Site**, then click **Create Application**.</span></span>  
  
        -   <span data-ttu-id="73cf5-269">**“创建新站点”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-269">**Create new site**.</span></span> <span data-ttu-id="73cf5-270">创建网站时，将自动创建新的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-270">A new web application is automatically created when the website is created.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="73cf5-271">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版 Master Data Services 配置管理器中，您可以选择 SQL Server 早期版本（[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]）的现有 MDS Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-271">Your existing MDS web application from an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) is available for selection in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="73cf5-272">您不能选择现有 Web 应用程序，而是必须为 MDS 创建一个 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-272">You must not select the existing web application, and instead must create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application for MDS.</span></span> <span data-ttu-id="73cf5-273">否则，在您尝试将 Web 应用程序与升级的 MDS 数据库关联时，您会收到错误，指出无法访问请求的页面，因为该页的相关配置数据无效。</span><span class="sxs-lookup"><span data-stu-id="73cf5-273">Otherwise, you will receive an error when you try to associate the web application with the upgraded MDS database stating that the requested page cannot be accessed because the related configuration data for the page is invalid.</span></span>  
        >   
        >  <span data-ttu-id="73cf5-274">如果您要为 MDS Web 应用程序使用与现有（[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]）Web 应用程序相同的名字（别名），您必须首先从 IIS 中删除该 Web 应用程序和关联的应用程序池，然后使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版 Master Data Services 配置管理器创建同名的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-274">If you want to use the same name (alias) for MDS web application as your existing ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) web application, you must first delete the web application and the associated application pool from IIS, and then create a web application with the same name using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="73cf5-275">有关从 IIS 删除 Web 应用程序和应用程序池的信息，请参阅 [删除应用程序 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) 和 [删除应用程序池 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538)。</span><span class="sxs-lookup"><span data-stu-id="73cf5-275">For information about removing web application and application pools from IIS, see [Remove an Application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) and [Remove an Application Pool (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).</span></span>  
  
5.  <span data-ttu-id="73cf5-276">现在将新 Web 应用程序与已升级的 MDS 数据库关联。</span><span class="sxs-lookup"><span data-stu-id="73cf5-276">Now associate the new web application with the upgraded MDS database.</span></span>  
  
    1.  <span data-ttu-id="73cf5-277">在 **“将应用程序与数据库相关联”** 部分中，单击 **“选择”** 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-277">In the **Associate Application with Database** section, click **Select**.</span></span>  
  
    2.  <span data-ttu-id="73cf5-278">选择 MDS 数据库。</span><span class="sxs-lookup"><span data-stu-id="73cf5-278">Select the MDS database.</span></span>  
  
    3.  <span data-ttu-id="73cf5-279">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="73cf5-279">Click **Apply**.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="73cf5-280">疑难解答</span><span class="sxs-lookup"><span data-stu-id="73cf5-280">Troubleshooting</span></span>  
 <span data-ttu-id="73cf5-281">**问题：** 打开 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web 应用程序时，将显示 "客户端版本与数据库版本不兼容" 错误消息。</span><span class="sxs-lookup"><span data-stu-id="73cf5-281">**Issue:** When you open the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, a "client version is not compatible with the database version" error message is displayed.</span></span>  
  
 <span data-ttu-id="73cf5-282">**解决方案：** 当 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 主数据管理器 web 应用程序尝试访问已升级到 Master Data Services 的数据库时，会出现此问题 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="73cf5-282">**Solution:** This issue occurs when a [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Master Data Manager web application tries to access a database that has been upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Master Data Services.</span></span> <span data-ttu-id="73cf5-283">您必须改用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73cf5-283">You must use a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application instead.</span></span>  
  
 <span data-ttu-id="73cf5-284">如果您在升级 MDS 数据库架构时没有在 IIS 中停止并重新启动 **“MDS 应用程序池”** ，则也可能出现此问题。</span><span class="sxs-lookup"><span data-stu-id="73cf5-284">This issue may also occur if you did not stop and restart the **MDS Application Pool** in IIS when upgrading the MDS database schema.</span></span> <span data-ttu-id="73cf5-285">重新启动 **“MDS 应用程序池”** 可解决此问题。</span><span class="sxs-lookup"><span data-stu-id="73cf5-285">Restart the **MDS Application Pool** to correct the issue.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cf5-286">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73cf5-286">See Also</span></span>  
 [<span data-ttu-id="73cf5-287">安装 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="73cf5-287">Install Master Data Services</span></span>](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
