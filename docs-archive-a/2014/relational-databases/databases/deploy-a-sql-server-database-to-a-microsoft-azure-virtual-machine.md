---
title: 将 SQL Server 数据库部署到 Microsoft Azure 虚拟机 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploymentwizard.deploymentsettings.f1
- sql12.swb.deploymentwizard.progress.f1
- sql11.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.f1
- sql12.swb.deploymentwizard.azuresignin.f1
- sql11.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.azuresignin.f1
- sql12.swb.deploymentwizard.f1
- sql12.swb.sqlvmdialog.f1
- sql11.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.results.f1
- sql11.swb.deploymentwizard.progress.f1
- sql12.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.sourcesettings.f1
- sql12.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.sourcesettings.f1
- sql11.swb.deploymentwizard.results.f1
- sql12.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.deploymentsettings.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
author: stevestein
ms.author: sstein
ms.openlocfilehash: d48c06db038a775811cba6705fbaf1d97a960f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691741"
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a><span data-ttu-id="adda9-102">将 SQL Server 数据库部署到 Microsoft Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="adda9-102">Deploy a SQL Server Database to a Microsoft Azure Virtual Machine</span></span>
  <span data-ttu-id="adda9-103">使用 "将**SQL Server 数据库部署到 AZURE VM** " 向导，将数据库从的实例部署 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AZURE 虚拟机 (VM) 。</span><span class="sxs-lookup"><span data-stu-id="adda9-103">Use the **Deploy a SQL Server Database to an Azure VM** wizard to deploy a database from an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in an Azure Virtual Machine (VM).</span></span> <span data-ttu-id="adda9-104">此向导利用完整数据库备份操作，因此可始终复制 SQL Server 用户数据库中的完整数据架构和数据。</span><span class="sxs-lookup"><span data-stu-id="adda9-104">The wizard utilizes a full database backup operation, so it always copies the complete database schema and the data from a SQL Server user database.</span></span> <span data-ttu-id="adda9-105">此向导还为您进行所有 Azure VM 配置，因此不需要预先配置 VM。</span><span class="sxs-lookup"><span data-stu-id="adda9-105">The wizard also does all of the Azure VM configuration for you, so no pre-configuration of the VM is required.</span></span>  
  
 <span data-ttu-id="adda9-106">您无法使用此向导进行差异备份，因为此向导将不会覆盖具有相同的数据库名称的现有数据库。</span><span class="sxs-lookup"><span data-stu-id="adda9-106">You cannot use the wizard for differential backups because the wizard will not overwrite an existing database that has the same database name.</span></span> <span data-ttu-id="adda9-107">若要替换 VM 上的现有数据库，必须先删除现有数据库或更改数据库名称。</span><span class="sxs-lookup"><span data-stu-id="adda9-107">To replace an existing database on the VM, you must first drop the existing database or change the database name.</span></span> <span data-ttu-id="adda9-108">如果在未提交的部署操作的数据库名称与 VM 上的现有数据库之间存在命名冲突，此向导将建议为未提交的数据库追加数据库名称以便您能完成操作。</span><span class="sxs-lookup"><span data-stu-id="adda9-108">If there is a naming conflict between the database name for an in-flight deploy operation and an existing database on the VM, the wizard will suggest an appended database name for the in-flight database to enable you to complete the operation.</span></span>  
  
##  <a name="before-you-begin"></a><a name="before_you_begin"></a> <span data-ttu-id="adda9-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="adda9-109">Before You Begin</span></span>  
 <span data-ttu-id="adda9-110">若要完成此向导，您必须能够提供以下信息并准备好以下这些配置设置：</span><span class="sxs-lookup"><span data-stu-id="adda9-110">To complete this wizard, you must be able to provide the following information and have these configuration settings in place:</span></span>  
  
-   <span data-ttu-id="adda9-111">与 Azure 订阅关联的 Microsoft 帐户详细信息。</span><span class="sxs-lookup"><span data-stu-id="adda9-111">The Microsoft account details associated with your Azure subscription.</span></span>  
  
-   <span data-ttu-id="adda9-112">你的 Azure 发布配置文件。</span><span class="sxs-lookup"><span data-stu-id="adda9-112">Your Azure publishing profile.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="adda9-113">SQL Server 当前支持发布配置文件版本 2.0。</span><span class="sxs-lookup"><span data-stu-id="adda9-113">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="adda9-114">要下载支持的发布配置文件版本，请参阅 [下载发布配置文件 2.0](https://go.microsoft.com/fwlink/?LinkId=396421)。</span><span class="sxs-lookup"><span data-stu-id="adda9-114">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
  
-   <span data-ttu-id="adda9-115">已上传到 Azure 订阅的管理证书。</span><span class="sxs-lookup"><span data-stu-id="adda9-115">The management certificate uploaded to your Azure subscription.</span></span>  
  
-   <span data-ttu-id="adda9-116">保存到运行向导的计算机上个人证书存储区中的管理证书。</span><span class="sxs-lookup"><span data-stu-id="adda9-116">The management certificate saved into the personal certificate store on the computer where the wizard is running.</span></span>  
  
-   <span data-ttu-id="adda9-117">您必须具有可供承载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的计算机使用的临时存储位置。</span><span class="sxs-lookup"><span data-stu-id="adda9-117">You must have a temporary storage location that is available to the computer where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is hosted.</span></span> <span data-ttu-id="adda9-118">该临时存储位置还必须可供运行向导的计算机使用。</span><span class="sxs-lookup"><span data-stu-id="adda9-118">The temporary storage location must also be available to the computer where the wizard is running.</span></span>  
  
-   <span data-ttu-id="adda9-119">如果将数据库部署到现有虚拟机，则必须将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例配置为侦听 TCP/IP 端口。</span><span class="sxs-lookup"><span data-stu-id="adda9-119">If you are deploying the database to an existing VM, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured to listen on a TCP/IP port.</span></span>  
  
-   <span data-ttu-id="adda9-120">你计划用于创建 VM 的 Azure VM 或库映像必须配置并运行 SQL Server 云适配器。</span><span class="sxs-lookup"><span data-stu-id="adda9-120">Either an Azure VM or Gallery image you plan to use for creation of the VM must have the SQL Server Cloud Adapter configured and running.</span></span>  
  
-   <span data-ttu-id="adda9-121">必须使用专用端口11435在 Azure 网关上配置 SQL Server 云适配器的开放终结点。</span><span class="sxs-lookup"><span data-stu-id="adda9-121">You must configure an open endpoint for your SQL Server Cloud Adapter on the Azure gateway with private port 11435.</span></span>  
  
 <span data-ttu-id="adda9-122">此外，如果您计划将数据库部署到现有的 Azure VM，则还必须能够提供：</span><span class="sxs-lookup"><span data-stu-id="adda9-122">In addition, if you plan to deploy your database into an existing Azure VM, you must also be able to provide:</span></span>  
  
-   <span data-ttu-id="adda9-123">承载该虚拟机的云服务的 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="adda9-123">The DNS name of the cloud service that hosts your VM.</span></span>  
  
-   <span data-ttu-id="adda9-124">虚拟机的管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="adda9-124">Administrator credentials for the VM.</span></span>  
  
-   <span data-ttu-id="adda9-125">对要部署的数据库具有备份操作员权限的凭据，它们来自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的源实例。</span><span class="sxs-lookup"><span data-stu-id="adda9-125">Credentials with Backup operator privileges on the database you plan to deploy, from the source instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="adda9-126">有关在 Azure 虚拟机中运行 SQL Server 的详细信息，请参阅[准备迁移到 Azure 虚拟机中的 SQL Server](https://msdn.microsoft.com/library/dn133142.aspx)。</span><span class="sxs-lookup"><span data-stu-id="adda9-126">For more information about running SQL Server in Azure virtual machines, see [Getting Ready to Migrate to SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133142.aspx).</span></span>  
  
 <span data-ttu-id="adda9-127">在运行 Windows Server 操作系统的计算机上，您必须使用以下配置设置来运行此向导：</span><span class="sxs-lookup"><span data-stu-id="adda9-127">On computers running Windows Server operating systems, you must use the following configuration settings to run this wizard:</span></span>  
  
-   <span data-ttu-id="adda9-128">禁用增强安全性配置：使用“服务器管理器”>“本地服务器”将 Internet Explorer 增强安全性配置 (ESC) 设置为“OFF”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="adda9-128">Turn off Enhanced Security Configuration:  Use Server Manager > Local Server to set Internet Explorer Enhanced Security Configuration (ESC) to **OFF**.</span></span>  
  
-   <span data-ttu-id="adda9-129">启用 JavaScript：“Internet Explorer”>“Internet 选项”>“安全性”>“客户级别”>“脚本”>“活动脚本”：“启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="adda9-129">Enable JavaScript:  Internet Explorer > Internet Options > Security > Customer Level > Scripting > Active Scripting: **Enable**.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="limitations"></a> <span data-ttu-id="adda9-130">限制和局限</span><span class="sxs-lookup"><span data-stu-id="adda9-130">Limitations and Restrictions</span></span>  
 <span data-ttu-id="adda9-131">针对此操作的数据库大小限制为 1 TB。</span><span class="sxs-lookup"><span data-stu-id="adda9-131">The database size limitation for this operation is 1 TB.</span></span>  
  
 <span data-ttu-id="adda9-132">适用于 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]的 SQL Server Management Studio 中提供了此部署功能。</span><span class="sxs-lookup"><span data-stu-id="adda9-132">This deployment feature is available in SQL Server Management Studio for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="adda9-133">此部署功能仅适用于用户数据库；不支持部署系统数据库。</span><span class="sxs-lookup"><span data-stu-id="adda9-133">This deployment feature is for use only with user databases; deploying system databases is not supported.</span></span>  
  
 <span data-ttu-id="adda9-134">此部署功能不支持与地缘组相关联的托管服务。</span><span class="sxs-lookup"><span data-stu-id="adda9-134">The deployment feature does not support hosted services that are associated with an Affinity Group.</span></span> <span data-ttu-id="adda9-135">例如，在此向导的 **“部署设置”** 页上无法选择与某一地缘组相关联的存储帐户以供使用。</span><span class="sxs-lookup"><span data-stu-id="adda9-135">For example, storage accounts associated with an Affinity Group cannot be selected for use on the **Deployment Settings** page of this wizard.</span></span>  
  
 <span data-ttu-id="adda9-136">虚拟机中的 SQL Server 版本必须等于或高于源 SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="adda9-136">The SQL Server version in the VM must be the same or later than the source SQL Server version.</span></span> <span data-ttu-id="adda9-137">可以使用此向导 SQL Server 可以部署到 Azure VM 的数据库版本：</span><span class="sxs-lookup"><span data-stu-id="adda9-137">SQL Server database versions that can be deployed to an Azure VM using this wizard:</span></span>  
  
-   <span data-ttu-id="adda9-138">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="adda9-138">SQL Server 2008</span></span>  
  
-   <span data-ttu-id="adda9-139">SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="adda9-139">SQL Server 2008 R2</span></span>  
  
-   <span data-ttu-id="adda9-140">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="adda9-140">SQL Server 2012</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 <span data-ttu-id="adda9-141">在 Azure VM 数据库中运行 SQL Server 数据库版本可部署到：</span><span class="sxs-lookup"><span data-stu-id="adda9-141">SQL Server database versions running in an Azure VM database can be deployed to:</span></span>  
  
-   <span data-ttu-id="adda9-142">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="adda9-142">SQL Server 2012</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 <span data-ttu-id="adda9-143">如果在未提交的部署操作的数据库名称与 VM 上的现有数据库之间存在命名冲突，此向导将建议为未提交的数据库追加数据库名称以便您能完成操作。</span><span class="sxs-lookup"><span data-stu-id="adda9-143">If there is a naming conflict between the database name for an in-flight deploy operation and an existing database on the VM, the wizard will suggest an appended database name for the in-flight database to enable you to complete the operation.</span></span>  
  
###  <a name="considerations-for-deploying-a-filestream-enabled-database-to-an-azure-vm"></a><a name="filestream"></a> <span data-ttu-id="adda9-144">用于将支持 FILESTREAM 的数据库部署到 Azure VM 的注意事项</span><span class="sxs-lookup"><span data-stu-id="adda9-144">Considerations for Deploying a FILESTREAM-enabled Database to an Azure VM</span></span>  
 <span data-ttu-id="adda9-145">在部署其 BLOBS 存储于 FILESTREAM 对象中的数据库时，请注意以下准则和限制：</span><span class="sxs-lookup"><span data-stu-id="adda9-145">Note the following guidelines and restrictions when deploying databases that have BLOBS stored in FILESTREAM objects:</span></span>  
  
-   <span data-ttu-id="adda9-146">部署功能不能将支持 FILESTREAM 的数据库部署到一个新的 VM 中。</span><span class="sxs-lookup"><span data-stu-id="adda9-146">The deployment feature cannot deploy a FILESTREAM-enabled database into a new VM.</span></span> <span data-ttu-id="adda9-147">如果在运行该向导前没有在 VM 中启用 FILESTREAM，则数据库还原操作将失败，并且向导操作将不能成功完成。</span><span class="sxs-lookup"><span data-stu-id="adda9-147">If FILESTREAM is not enabled in the VM before you run the wizard, the database restore operation will fail and the wizard operation will not be able to complete successfully.</span></span> <span data-ttu-id="adda9-148">若要成功部署使用 FILESTREAM 的数据库，请在启动该向导前在宿主 VM 上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="adda9-148">To successfully deploy a database that uses FILESTREAM, enable FILESTREAM in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the host VM before launching the wizard.</span></span> <span data-ttu-id="adda9-149">有关详细信息，请参阅 [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx)。</span><span class="sxs-lookup"><span data-stu-id="adda9-149">For more information, see [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx).</span></span>  
  
-   <span data-ttu-id="adda9-150">如果您的数据库使用内存中 OLTP，则无需对该数据库进行任何修改即可将它部署到 Azure VM 中。</span><span class="sxs-lookup"><span data-stu-id="adda9-150">If your database utilizes In-Memory OLTP, you can deploy the database to an Azure VM without any modifications to the database.</span></span> <span data-ttu-id="adda9-151">有关详细信息，请参阅 [内存中 OLTP（内存中优化）](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="adda9-151">For more information, see [In-Memory OLTP (In-Memory Optimization)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx).</span></span>  
  
###  <a name="considerations-for-geographic-distribution-of-assets"></a><a name="geography"></a><span data-ttu-id="adda9-152">针对资产的地理分布的注意事项</span><span class="sxs-lookup"><span data-stu-id="adda9-152">Considerations for Geographic Distribution of Assets</span></span>  
 <span data-ttu-id="adda9-153">请注意，以下资产必须位于相同地理区域中：</span><span class="sxs-lookup"><span data-stu-id="adda9-153">Note that the following assets must be located in the same geographic region:</span></span>  
  
-   <span data-ttu-id="adda9-154">云服务</span><span class="sxs-lookup"><span data-stu-id="adda9-154">Cloud Service</span></span>  
  
-   <span data-ttu-id="adda9-155">VM 位置</span><span class="sxs-lookup"><span data-stu-id="adda9-155">VM Location</span></span>  
  
-   <span data-ttu-id="adda9-156">数据磁盘存储服务</span><span class="sxs-lookup"><span data-stu-id="adda9-156">Data Disk Storage Service</span></span>  
  
 <span data-ttu-id="adda9-157">如果上面列出的资产未共置在一起，则该向导将无法成功完成。</span><span class="sxs-lookup"><span data-stu-id="adda9-157">If the assets listed above are not co-located, the wizard will not be able to complete successfully.</span></span>  
  
###  <a name="wizard-configuration-settings"></a><a name="configuration_settings"></a> <span data-ttu-id="adda9-158">向导配置设置</span><span class="sxs-lookup"><span data-stu-id="adda9-158">Wizard Configuration Settings</span></span>  
 <span data-ttu-id="adda9-159">使用以下配置详细信息可修改针对部署到 Azure VM 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库部署设置。</span><span class="sxs-lookup"><span data-stu-id="adda9-159">Use the following configuration details to modify settings for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database deployment to an Azure VM.</span></span>  
  
-   <span data-ttu-id="adda9-160">**配置文件的默认路径** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml</span><span class="sxs-lookup"><span data-stu-id="adda9-160">**Default path for the configuration file** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml</span></span>  
  
-   <span data-ttu-id="adda9-161">**配置文件结构**</span><span class="sxs-lookup"><span data-stu-id="adda9-161">**Configuration file structure**</span></span>  
  
    -   \<DeploymentSettings>  
  
        -   <span data-ttu-id="adda9-162"><OtherSettings</span><span class="sxs-lookup"><span data-stu-id="adda9-162"><OtherSettings</span></span>  
  
            -   <span data-ttu-id="adda9-163">TraceLevel = "Debug"\<!-- Logging level --></span><span class="sxs-lookup"><span data-stu-id="adda9-163">TraceLevel="Debug" \<!-- Logging level --></span></span>  
  
            -   <span data-ttu-id="adda9-164">BackupPath = " \\ \\ [server name] \\ [volume] \\ "\<!-- The last used path for backup. Used as default in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="adda9-164">BackupPath="\\\\[server name]\\[volume]\\" \<!-- The last used path for backup. Used as default in the wizard. --></span></span>  
  
            -   <span data-ttu-id="adda9-165">CleanupDisabled = False/>\<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). --></span><span class="sxs-lookup"><span data-stu-id="adda9-165">CleanupDisabled = False /> \<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). --></span></span>  
  
        -   <span data-ttu-id="adda9-166"><PublishProfile\<!-- The last used publish profile information. --></span><span class="sxs-lookup"><span data-stu-id="adda9-166"><PublishProfile \<!-- The last used publish profile information. --></span></span>  
  
            -   <span data-ttu-id="adda9-167">Certificate = "12A34B567890123ABCD4EF567A8"\<!-- The certificate for use in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="adda9-167">Certificate="12A34B567890123ABCD4EF567A8" \<!-- The certificate for use in the wizard. --></span></span>  
  
            -   <span data-ttu-id="adda9-168">订阅 = "1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx-67d8-90ef-ab12-xxxxxxxxxxxxx"\<!-- The subscription for use in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="adda9-168">Subscription="1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx" \<!-- The subscription for use in the wizard. --></span></span>  
  
            -   <span data-ttu-id="adda9-169">Name = "My 订阅"\<!-- The name of the subscription. --></span><span class="sxs-lookup"><span data-stu-id="adda9-169">Name="My Subscription" \<!-- The name of the subscription. --></span></span>  
  
            -   <span data-ttu-id="adda9-170">Publisher="" /></span><span class="sxs-lookup"><span data-stu-id="adda9-170">Publisher="" /></span></span>  
  
    -   \</DeploymentSettings>  
  
 <span data-ttu-id="adda9-171">**配置文件值**</span><span class="sxs-lookup"><span data-stu-id="adda9-171">**Configuration file values**</span></span>  
  
###  <a name="permissions"></a><a name="permissions"></a> <span data-ttu-id="adda9-172">权限</span><span class="sxs-lookup"><span data-stu-id="adda9-172">Permissions</span></span>  
 <span data-ttu-id="adda9-173">所部署的数据库必须处于正常状态，该数据库必须可供运行向导的用户帐户访问，而且该用户帐户必须拥有执行备份操作的权限。</span><span class="sxs-lookup"><span data-stu-id="adda9-173">The database being deployed must be in a normal state, the database must be accessible to the user account running the wizard, and the user account must have permissions to perform a backup operation.</span></span>  
  
##  <a name="using-the-deploy-database-to-azure-vm-wizard"></a><a name="launch_wizard"></a><span data-ttu-id="adda9-174">使用 "将数据库部署到 Azure VM" 向导</span><span class="sxs-lookup"><span data-stu-id="adda9-174">Using the Deploy Database to Azure VM Wizard</span></span>  
 <span data-ttu-id="adda9-175">**若要启动向导，则使用以下步骤：**</span><span class="sxs-lookup"><span data-stu-id="adda9-175">**To launch the wizard, use the following steps:**</span></span>  
  
1.  <span data-ttu-id="adda9-176">使用 SQL Server Management Studio 连接到具有要部署的数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="adda9-176">Use SQL Server Management Studio to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the database you want to deploy.</span></span>  
  
2.  <span data-ttu-id="adda9-177">在 **对象资源管理器**中，展开该实例名称，然后展开 **“数据库”** 节点。</span><span class="sxs-lookup"><span data-stu-id="adda9-177">In **Object Explorer**, expand the instance name, then expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="adda9-178">右键单击要部署的数据库，选择 "**任务**"，然后选择 "**将数据库部署到 Azure VM ...** "</span><span class="sxs-lookup"><span data-stu-id="adda9-178">Right-click the database you want to deploy, select **Tasks**, and then select **Deploy Database to Azure VM...**</span></span>  
  

  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="adda9-179">“简介”页</span><span class="sxs-lookup"><span data-stu-id="adda9-179">Introduction Page</span></span>  
 <span data-ttu-id="adda9-180">本页介绍如何将**SQL Server 数据库部署到 AZURE VM**向导。</span><span class="sxs-lookup"><span data-stu-id="adda9-180">This page describes the **Deploy a SQL Server Database to an Azure VM** wizard.</span></span>  
  
 <span data-ttu-id="adda9-181">**选项**</span><span class="sxs-lookup"><span data-stu-id="adda9-181">**Options**</span></span>  
  
-   <span data-ttu-id="adda9-182">**不再显示此页。**</span><span class="sxs-lookup"><span data-stu-id="adda9-182">**Do not show this page again.**</span></span> <span data-ttu-id="adda9-183">- 单击此复选框可以阻止在将来显示“简介”页。</span><span class="sxs-lookup"><span data-stu-id="adda9-183">- Click this check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="adda9-184">**下一步** - 继续到 **“源设置”** 页。</span><span class="sxs-lookup"><span data-stu-id="adda9-184">**Next** - Proceeds to the **Source Settings** page.</span></span>  
  
-   <span data-ttu-id="adda9-185">**取消**-取消操作并关闭向导。</span><span class="sxs-lookup"><span data-stu-id="adda9-185">**Cancel** - Cancels the operation and closes the wizard.</span></span>  
  
-   <span data-ttu-id="adda9-186">**Help** -启动向导的 MSDN 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="adda9-186">**Help** - Launches the MSDN Help topic for the wizard.</span></span>  
  
##  <a name="source-settings"></a><a name="Source_settings"></a><span data-ttu-id="adda9-187">源设置</span><span class="sxs-lookup"><span data-stu-id="adda9-187">Source Settings</span></span>  
 <span data-ttu-id="adda9-188">使用此页可连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 承载要部署到 AZURE VM 的数据库的实例。</span><span class="sxs-lookup"><span data-stu-id="adda9-188">Use this page to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the database you want to deploy to the Azure VM.</span></span> <span data-ttu-id="adda9-189">还将指定一个临时位置，以便在将文件传输到 Azure 之前从本地计算机保存文件。</span><span class="sxs-lookup"><span data-stu-id="adda9-189">You will also specify a temporary location for files to be saved from the local machine before they are transferred to Azure.</span></span> <span data-ttu-id="adda9-190">这可以是共享网络位置。</span><span class="sxs-lookup"><span data-stu-id="adda9-190">This can be a shared, network location.</span></span>  
  
 <span data-ttu-id="adda9-191">**选项**</span><span class="sxs-lookup"><span data-stu-id="adda9-191">**Options**</span></span>  
  
-   <span data-ttu-id="adda9-192">单击 "**连接 ...** "，然后为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 承载要部署的数据库的实例指定连接详细信息。</span><span class="sxs-lookup"><span data-stu-id="adda9-192">Click **Connect...** and then specify connection details for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the database to deploy.</span></span>  
  
-   <span data-ttu-id="adda9-193">使用 **“选择数据库”** 下拉列表来指定要部署的数据库。</span><span class="sxs-lookup"><span data-stu-id="adda9-193">Use the **Select Database** drop-down list to specify the database to deploy.</span></span>  
  
-   <span data-ttu-id="adda9-194">在 "**其他设置**" 字段中，指定可供 Azure VM 服务访问的共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="adda9-194">In the **Other Settings** field, specify a shared folder that will be accessible to the Azure VM service.</span></span>  
  
##  <a name="azure-sign-in"></a><a name="Azure_sign-in"></a><span data-ttu-id="adda9-195">Azure 登录</span><span class="sxs-lookup"><span data-stu-id="adda9-195">Azure Sign-in</span></span>  
 <span data-ttu-id="adda9-196">使用此页连接到 Azure 并提供管理证书或发布配置文件详细信息。</span><span class="sxs-lookup"><span data-stu-id="adda9-196">Use this page to connect to Azure and provide management certificate or publishing profile details.</span></span>  
  
 <span data-ttu-id="adda9-197">**选项**</span><span class="sxs-lookup"><span data-stu-id="adda9-197">**Options**</span></span>  
  
-   <span data-ttu-id="adda9-198">**管理证书**-使用此选项来指定本地证书存储区中与 Azure 中的管理证书匹配的证书。</span><span class="sxs-lookup"><span data-stu-id="adda9-198">**Management Certificate** - Use this option to specify a certificate from the local certificate store that matches the management certificate from Azure.</span></span>  
  
-   <span data-ttu-id="adda9-199">**发布配置文件**-如果已将发布配置文件下载到计算机，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="adda9-199">**Publishing Profile** - Use this option if you already have a publishing profile downloaded to your computer.</span></span>  
  
-   <span data-ttu-id="adda9-200">**登录**-使用此选项可以使用 Microsoft 帐户（例如，Live ID 或 Hotmail 帐户）登录到 Azure，以生成并下载新管理证书。</span><span class="sxs-lookup"><span data-stu-id="adda9-200">**Sign In** - Use this option to sign in to Azure using a Microsoft account - for example, a Live ID or Hotmail account - to generate and download a new management certificate.</span></span> <span data-ttu-id="adda9-201">请注意，每个订阅的证书数目是有限的。</span><span class="sxs-lookup"><span data-stu-id="adda9-201">Note that the number of certificates per subscription is limited.</span></span>  
  
-   <span data-ttu-id="adda9-202">**订阅**-选择、键入或粘贴与本地证书存储中的管理证书或发布配置文件相匹配的 AZURE 订阅 ID。</span><span class="sxs-lookup"><span data-stu-id="adda9-202">**Subscription** - Select, type, or paste your Azure subscription ID that matches the management certificate from the local certificate store or a publishing profile.</span></span>  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a><span data-ttu-id="adda9-203">部署设置页</span><span class="sxs-lookup"><span data-stu-id="adda9-203">Deployment Settings Page</span></span>  
 <span data-ttu-id="adda9-204">使用此页可以指定目标服务器并提供有关新数据库的详细信息。</span><span class="sxs-lookup"><span data-stu-id="adda9-204">Use this page to specify the destination server and to provide details about your new database.</span></span>  
  
 <span data-ttu-id="adda9-205">**选项**</span><span class="sxs-lookup"><span data-stu-id="adda9-205">**Options**</span></span>  
  
-   <span data-ttu-id="adda9-206">**Azure 虚拟机**-指定将承载 SQL Server 数据库的 VM 的详细信息：</span><span class="sxs-lookup"><span data-stu-id="adda9-206">**Azure Virtual Machine** - Specify details for the VM that will host the SQL Server database:</span></span>  
  
-   <span data-ttu-id="adda9-207">**云服务名称**-指定承载虚拟机的服务的名称。</span><span class="sxs-lookup"><span data-stu-id="adda9-207">**Cloud Service name** - Specify the name of the service that hosts the VM.</span></span> <span data-ttu-id="adda9-208">要创建新的云服务，请指定该服务的名称。</span><span class="sxs-lookup"><span data-stu-id="adda9-208">To create a new Cloud Service, specify a name for the new Cloud Service.</span></span>  
  
-   <span data-ttu-id="adda9-209">**虚拟机名称**-指定将承载 SQL Server 数据库的 VM 的名称。</span><span class="sxs-lookup"><span data-stu-id="adda9-209">**Virtual Machine name** - Specify the name of the VM that will host the SQL Server database.</span></span> <span data-ttu-id="adda9-210">若要创建新的 Azure VM，请指定新 VM 的名称。</span><span class="sxs-lookup"><span data-stu-id="adda9-210">To create a new Azure VM, specify a name for the new VM.</span></span>  
  
-   <span data-ttu-id="adda9-211">**设置**-使用 "设置" 按钮创建一个新的 VM 以托管 SQL Server 数据库。</span><span class="sxs-lookup"><span data-stu-id="adda9-211">**Settings** - Use the Settings button to create a new VM to host the SQL Server database.</span></span> <span data-ttu-id="adda9-212">如果使用的是现有虚拟机，您提供的信息将用于对您的凭据进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="adda9-212">If you are using an existing VM, the information you provide will be used to authenticate your credentials.</span></span>  
  
-   <span data-ttu-id="adda9-213">**存储帐户**-从下拉列表中选择存储帐户。</span><span class="sxs-lookup"><span data-stu-id="adda9-213">**Storage account** - Select the storage account from the drop-down list.</span></span> <span data-ttu-id="adda9-214">要创建新的存储帐户，请指定该帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="adda9-214">To create a new storage account, specify a name for the new account.</span></span> <span data-ttu-id="adda9-215">请注意，在下拉列表中将不会提供与某一地缘组相关联的存储帐户。</span><span class="sxs-lookup"><span data-stu-id="adda9-215">Note that storage accounts associated with an Affinity Group will not be available in the drop-down list.</span></span>  
  
-   <span data-ttu-id="adda9-216">**目标数据库**-指定目标数据库的详细信息。</span><span class="sxs-lookup"><span data-stu-id="adda9-216">**Target Database** - Specify details for the target database.</span></span>  
  
-   <span data-ttu-id="adda9-217">**服务器连接**-服务器的连接详细信息。</span><span class="sxs-lookup"><span data-stu-id="adda9-217">**Server Connection** - Connection details for the server.</span></span>  
  
-   <span data-ttu-id="adda9-218">**数据库**-指定或确认新数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="adda9-218">**Database** - Specify or confirm the name of a new database.</span></span> <span data-ttu-id="adda9-219">如果数据库名称在目标 SQL Server 实例上已存在，建议您修改该名称。</span><span class="sxs-lookup"><span data-stu-id="adda9-219">If the database name already exists on the destination SQL Server instance, we suggest that you specify a modified database name.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="adda9-220">摘要页</span><span class="sxs-lookup"><span data-stu-id="adda9-220">Summary Page</span></span>  
 <span data-ttu-id="adda9-221">使用此页可查看操作的指定设置。</span><span class="sxs-lookup"><span data-stu-id="adda9-221">Use this page to review the specified settings for the operation.</span></span> <span data-ttu-id="adda9-222">若要使用指定设置完成部署操作，请单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="adda9-222">To complete the deploy operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="adda9-223">若要取消部署操作并退出向导，请单击 "**取消**"。</span><span class="sxs-lookup"><span data-stu-id="adda9-223">To cancel the deploy operation and exit the wizard, click **Cancel**.</span></span>  
  
 <span data-ttu-id="adda9-224">将数据库详细信息部署到 Azure VM 上的 SQL Server 数据库可能需要手动步骤。</span><span class="sxs-lookup"><span data-stu-id="adda9-224">There may be manual steps required to deploy database details to the SQL Server database on the Azure VM.</span></span> <span data-ttu-id="adda9-225">将为您详细说明这些步骤。</span><span class="sxs-lookup"><span data-stu-id="adda9-225">These steps will be outlined in detail for you.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="adda9-226">结果页</span><span class="sxs-lookup"><span data-stu-id="adda9-226">Results Page</span></span>  
 <span data-ttu-id="adda9-227">此页将报告部署操作是成功还是失败，并显示每个操作的结果。</span><span class="sxs-lookup"><span data-stu-id="adda9-227">This page reports the success or failure of the deploy operation, showing the results of each action.</span></span> <span data-ttu-id="adda9-228">遇到了错误的任何操作都将在 **“结果”** 列中具有一个指示。</span><span class="sxs-lookup"><span data-stu-id="adda9-228">Any action that encountered an error will have an indication in the **Result** column.</span></span> <span data-ttu-id="adda9-229">单击该链接可以查看针对该操作的错误报告。</span><span class="sxs-lookup"><span data-stu-id="adda9-229">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="adda9-230">单击 **“完成”** 关闭向导。</span><span class="sxs-lookup"><span data-stu-id="adda9-230">Click **Finish** to close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adda9-231">另请参阅</span><span class="sxs-lookup"><span data-stu-id="adda9-231">See Also</span></span>  
 <span data-ttu-id="adda9-232">[SQL Server 的云适配器](../../database-engine/cloud-adapter-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="adda9-232">[Cloud Adapter for SQL Server](../../database-engine/cloud-adapter-for-sql-server.md) </span></span>  
 <span data-ttu-id="adda9-233">[数据库生命周期管理](../database-lifecycle-management.md) </span><span class="sxs-lookup"><span data-stu-id="adda9-233">[Database Lifecycle Management](../database-lifecycle-management.md) </span></span>  
 <span data-ttu-id="adda9-234">[导出数据层应用程序](../data-tier-applications/export-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="adda9-234">[Export a Data-tier Application](../data-tier-applications/export-a-data-tier-application.md) </span></span>  
 <span data-ttu-id="adda9-235">[导入 BACPAC 文件以创建新的用户数据库](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md) </span><span class="sxs-lookup"><span data-stu-id="adda9-235">[Import a BACPAC File to Create a New User Database](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md) </span></span>  
 <span data-ttu-id="adda9-236">[Azure SQL 数据库备份和还原](https://msdn.microsoft.com/library/azure/jj650016.aspx) </span><span class="sxs-lookup"><span data-stu-id="adda9-236">[Azure SQL Database Backup and Restore](https://msdn.microsoft.com/library/azure/jj650016.aspx) </span></span>  
 <span data-ttu-id="adda9-237">[在 Azure 虚拟机中部署 SQL Server](https://msdn.microsoft.com/library/dn133141.aspx) </span><span class="sxs-lookup"><span data-stu-id="adda9-237">[SQL Server Deployment in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133141.aspx) </span></span>  
 [<span data-ttu-id="adda9-238">准备迁移到 Azure 虚拟机中的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="adda9-238">Getting Ready to Migrate to SQL Server in Azure Virtual Machines</span></span>](https://msdn.microsoft.com/library/dn133142.aspx)  
  
  
