---
title: 升级 Data Quality Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: f396666b-7754-4efc-9507-0fd114cc32d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9d2544df341a831f2f676ec58150ed64a800fb96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580356"
---
# <a name="upgrade-data-quality-services"></a><span data-ttu-id="cc131-102">升级 Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="cc131-102">Upgrade Data Quality Services</span></span>
  <span data-ttu-id="cc131-103">本主题的信息介绍如何将现有 Data Quality Services (DQS) 安装升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2。</span><span class="sxs-lookup"><span data-stu-id="cc131-103">This topic provides information on how to upgrade your existing installation of Data Quality Services (DQS) to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="cc131-104">在将 DQS 中的数据质量服务器升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]时，您还必须升级 DQS 数据库架构。</span><span class="sxs-lookup"><span data-stu-id="cc131-104">As part of upgrading your Data Quality Server in DQS to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must also upgrade the DQS databases schema.</span></span>  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="cc131-105">您必须先备份 DQS 数据库，然后才能升级 DQS，以防止在架构升级过程中出现任何意外数据损失。</span><span class="sxs-lookup"><span data-stu-id="cc131-105">You must back up your DQS databases before upgrading DQS to prevent any accidental data loss during the schema upgrade.</span></span> <span data-ttu-id="cc131-106">有关备份 DQS 数据库的信息，请参阅 [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="cc131-106">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).</span></span>  
> -   <span data-ttu-id="cc131-107">通过使用当前或早期版本的数据质量客户端或 Integration Services 中的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] DQS 清除转换 [，你可以连接](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) 版数据质量服务器，执行你的数据质量任务。</span><span class="sxs-lookup"><span data-stu-id="cc131-107">You can connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Data Quality Server by using the current or an earlier version of Data Quality Client or the [DQS Cleansing Transformation](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) in Integration Services to perform your data quality tasks.</span></span>  
> -   <span data-ttu-id="cc131-108">在将 Data Quality Services 和 Master Data Services 升级到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] CTP2 后，您可以使用用于 Excel 的 Master Data Services 外接程序的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 版本继续进行。</span><span class="sxs-lookup"><span data-stu-id="cc131-108">You can continue using the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel after upgrading Data Quality Services and Master Data Services to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="cc131-109">但是，在升级到 SQL Server 2014 CTP2 后，用于 Excel 的 Master Data Services 外接程序的任何早期版本都无法使用。</span><span class="sxs-lookup"><span data-stu-id="cc131-109">However, any earlier version of the Master Data Services Add-In for Excel will not work after upgrading to SQL Server 2014 CTP2.</span></span> <span data-ttu-id="cc131-110">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 您可以从 [此处](https://go.microsoft.com/fwlink/?LinkId=328664)下载用于 Excel 的 Master Data Services 外接程序的  SP1 版本。</span><span class="sxs-lookup"><span data-stu-id="cc131-110">You can download the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel from [here](https://go.microsoft.com/fwlink/?LinkId=328664).</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="cc131-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="cc131-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="cc131-112">您必须作为 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 计算机上 Administrators 组的成员登录。</span><span class="sxs-lookup"><span data-stu-id="cc131-112">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="cc131-113">您的 Windows 用户帐户必须是安装了 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 的 SQL Server 实例中 sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="cc131-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
##  <a name="upgrading-dqs"></a><a name="Upgrade"></a> <span data-ttu-id="cc131-114">升级 DQS</span><span class="sxs-lookup"><span data-stu-id="cc131-114">Upgrading DQS</span></span>  
 <span data-ttu-id="cc131-115">要升级 DQS：</span><span class="sxs-lookup"><span data-stu-id="cc131-115">To upgrade DQS:</span></span>  
  
1.  <span data-ttu-id="cc131-116">首先备份 DQS 数据库，然后再启动升级过程。</span><span class="sxs-lookup"><span data-stu-id="cc131-116">Back up your DQS databases before you start the upgrade process.</span></span> <span data-ttu-id="cc131-117">有关备份 DQS 数据库的信息，请参阅 [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="cc131-117">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).</span></span>  
  
2.  <span data-ttu-id="cc131-118">将安装 DQS 的 SQL 实例升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cc131-118">Upgrade the SQL Server instance where DQS is installed to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    1.  <span data-ttu-id="cc131-119">运行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="cc131-119">Run the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="cc131-120">在左窗格中，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="cc131-120">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="cc131-121">在右侧窗格中，单击 "**从 SQL Server 2005 升级，SQL Server 2008"，SQL Server 2008 R2 或 SQL Server 2012**。</span><span class="sxs-lookup"><span data-stu-id="cc131-121">In the right pane, click **Upgrade from SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 or SQL Server 2012**.</span></span>  
  
    4.  <span data-ttu-id="cc131-122">完成安装向导。</span><span class="sxs-lookup"><span data-stu-id="cc131-122">Complete the Setup wizard.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cc131-123">这会将您的 SQL Server 实例升级为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，而且如果此计算机以前安装过数据质量客户端，还会安装最新的数据质量客户端。</span><span class="sxs-lookup"><span data-stu-id="cc131-123">This will upgrade your SQL Server instance to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and also install the latest Data Quality Client, if Data Quality Client was previously installed on this computer.</span></span> <span data-ttu-id="cc131-124">如果您在其他计算机上安装了数据质量客户端，您必须在那些计算机上运行步骤 2 的这些分步骤，安装最新版的数据质量客户端。</span><span class="sxs-lookup"><span data-stu-id="cc131-124">If you have Data Quality Client installed on other computers, you must run the sub steps in Step 2 on those computers to install the current version of Data Quality Client.</span></span> <span data-ttu-id="cc131-125">安装向导会安装与现有的数据质量客户端并存的当前版本数据质量客户端。</span><span class="sxs-lookup"><span data-stu-id="cc131-125">The Setup wizard installs the current version of Data Quality Client alongside the existing version of Data Quality Client.</span></span> <span data-ttu-id="cc131-126">升级完 DQS 数据架构后，通过使用当前或早期版本的数据质量客户端，您可以连接 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版数据质量服务器。</span><span class="sxs-lookup"><span data-stu-id="cc131-126">After you upgrade the DQS databases schema, you can connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Data Quality Server by using the current or an earlier version of Data Quality Client.</span></span>  
  
3.  <span data-ttu-id="cc131-127">升级 DQS 数据库架构。</span><span class="sxs-lookup"><span data-stu-id="cc131-127">Upgrade the DQS databases schema.</span></span>  
  
    1.  <span data-ttu-id="cc131-128">作为管理员启动命令提示符。</span><span class="sxs-lookup"><span data-stu-id="cc131-128">Start Command Prompt as an administrator.</span></span>  
  
    2.  <span data-ttu-id="cc131-129">在命令提示符下，将目录更改为 DQSInstaller.exe 出现的位置。</span><span class="sxs-lookup"><span data-stu-id="cc131-129">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="cc131-130">对于 SQL Server 的默认实例，DQSInstaller.exe 文件将出现在 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn 下：</span><span class="sxs-lookup"><span data-stu-id="cc131-130">For the default instance of SQL Server, the DQSInstaller.exe file is available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
        ```  
        cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
        ```  
  
    3.  <span data-ttu-id="cc131-131">在命令提示符下，键入以下命令，再按 Enter：</span><span class="sxs-lookup"><span data-stu-id="cc131-131">At the command prompt, type the following command, and press ENTER:</span></span>  
  
        ```  
        dqsinstaller.exe -upgrade  
        ```  
  
    4.  <span data-ttu-id="cc131-132">安装程序会提示您在继续操作之前备份 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="cc131-132">The installer prompts you for backing up the DQS databases before proceeding.</span></span> <span data-ttu-id="cc131-133">如果已经备份 DQS 数据库，请键入 `Y` 或 `Yes`，然后按 Enter 以继续升级。</span><span class="sxs-lookup"><span data-stu-id="cc131-133">If you have already backed up your DQS databases, type `Y` or `Yes`, and then press ENTER to continue with the upgrade.</span></span>  
  
    5.  <span data-ttu-id="cc131-134">在成功升级 DQS 数据库架构之后，将显示一条完成消息。</span><span class="sxs-lookup"><span data-stu-id="cc131-134">A completion message is displayed after successful upgrade of the DQS databases schema.</span></span>  
  
##  <a name="verifying-the-dqs-databases-schema-upgrade"></a><a name="Verify"></a> <span data-ttu-id="cc131-135">验证 DQS 数据库架构升级</span><span class="sxs-lookup"><span data-stu-id="cc131-135">Verifying the DQS Databases Schema Upgrade</span></span>  
 <span data-ttu-id="cc131-136">要验证是否成功升级了 DQS 数据库架构，您可以查询每个数据库中的 A_DB_VERSION 表来检查 DQS_MAIN 和 DQS_PROJECTS 数据库中的当前版本。</span><span class="sxs-lookup"><span data-stu-id="cc131-136">To verify that DQS databases schema have successfully upgraded, you can check the current version in the DQS_MAIN and DQS_PROJECTS databases by querying the A_DB_VERSION table in each database.</span></span> <span data-ttu-id="cc131-137">为此，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="cc131-137">To do so:</span></span>  
  
1.  <span data-ttu-id="cc131-138">启动 SQL Server Management Studio 并连接到包含升级的 DQS 数据库架构的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="cc131-138">Start SQL Server Management Studio, and connect to the SQL Server instance that contains the upgraded DQS databases schema.</span></span>  
  
2.  <span data-ttu-id="cc131-139">运行以下查询：</span><span class="sxs-lookup"><span data-stu-id="cc131-139">Run the following query:</span></span>  
  
    ```  
    SELECT * FROM DQS_MAIN.dbo.A_DB_VERSION WHERE STATUS=2;  
    SELECT * FROM DQS_PROJECTS.dbo.A_DB_VERSION WHERE STATUS=2;  
    ```  
  
3.  <span data-ttu-id="cc131-140">输出将为每个升级显示一条信息，并显示升级的日期。</span><span class="sxs-lookup"><span data-stu-id="cc131-140">The output will display an entry for each upgrade along with the date of the upgrade.</span></span> <span data-ttu-id="cc131-141">最新日期的最大 VERSION_ID 和 ASSEMBLY_VERSION 是当前版本。</span><span class="sxs-lookup"><span data-stu-id="cc131-141">The maximum VERSION_ID and ASSEMBLY_VERSION on the latest date is the current version.</span></span> <span data-ttu-id="cc131-142">STATUS 列中的值为 2 时指示成功。</span><span class="sxs-lookup"><span data-stu-id="cc131-142">A value of 2 in the STATUS column indicates success.</span></span> <span data-ttu-id="cc131-143">如果发生错误，错误将在 ERROR 列中列出。</span><span class="sxs-lookup"><span data-stu-id="cc131-143">If an error has occurred, the error will be listed in the ERROR column.</span></span> <span data-ttu-id="cc131-144">示例输出：</span><span class="sxs-lookup"><span data-stu-id="cc131-144">A sample output:</span></span>  
  
    |<span data-ttu-id="cc131-145">ID</span><span class="sxs-lookup"><span data-stu-id="cc131-145">ID</span></span>|<span data-ttu-id="cc131-146">UPGRADE_DATE</span><span class="sxs-lookup"><span data-stu-id="cc131-146">UPGRADE_DATE</span></span>|<span data-ttu-id="cc131-147">VERSION_ID</span><span class="sxs-lookup"><span data-stu-id="cc131-147">VERSION_ID</span></span>|<span data-ttu-id="cc131-148">ASSEMBLY_VERSION</span><span class="sxs-lookup"><span data-stu-id="cc131-148">ASSEMBLY_VERSION</span></span>|<span data-ttu-id="cc131-149">USER_NAME</span><span class="sxs-lookup"><span data-stu-id="cc131-149">USER_NAME</span></span>|<span data-ttu-id="cc131-150">状态</span><span class="sxs-lookup"><span data-stu-id="cc131-150">STATUS</span></span>|<span data-ttu-id="cc131-151">ERROR</span><span class="sxs-lookup"><span data-stu-id="cc131-151">ERROR</span></span>|  
    |--------|-------------------|-----------------|-----------------------|----------------|------------|-----------|  
    |<span data-ttu-id="cc131-152">1000</span><span class="sxs-lookup"><span data-stu-id="cc131-152">1000</span></span>|<span data-ttu-id="cc131-153">2013-08-11 05:26:39.567</span><span class="sxs-lookup"><span data-stu-id="cc131-153">2013-08-11 05:26:39.567</span></span>|<span data-ttu-id="cc131-154">1200</span><span class="sxs-lookup"><span data-stu-id="cc131-154">1200</span></span>|<span data-ttu-id="cc131-155">11.0.3000.0</span><span class="sxs-lookup"><span data-stu-id="cc131-155">11.0.3000.0</span></span>|\<DOMAIN\UserName>|<span data-ttu-id="cc131-156">2</span><span class="sxs-lookup"><span data-stu-id="cc131-156">2</span></span>||  
    |<span data-ttu-id="cc131-157">1001</span><span class="sxs-lookup"><span data-stu-id="cc131-157">1001</span></span>|<span data-ttu-id="cc131-158">2013-09-19 15:09:37.750</span><span class="sxs-lookup"><span data-stu-id="cc131-158">2013-09-19 15:09:37.750</span></span>|<span data-ttu-id="cc131-159">1600</span><span class="sxs-lookup"><span data-stu-id="cc131-159">1600</span></span>|<span data-ttu-id="cc131-160">12.0.xxxx.0</span><span class="sxs-lookup"><span data-stu-id="cc131-160">12.0.xxxx.0</span></span>|\<DOMAIN\UserName>|<span data-ttu-id="cc131-161">2</span><span class="sxs-lookup"><span data-stu-id="cc131-161">2</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="cc131-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc131-162">See Also</span></span>  
 <span data-ttu-id="cc131-163">[安装 Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="cc131-163">[Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md) </span></span>  
 <span data-ttu-id="cc131-164">[删除 Data Quality Server 对象](../../sql-server/install/remove-data-quality-server-objects.md) </span><span class="sxs-lookup"><span data-stu-id="cc131-164">[Remove Data Quality Server Objects](../../sql-server/install/remove-data-quality-server-objects.md) </span></span>  
 [<span data-ttu-id="cc131-165">升级到 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="cc131-165">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
  
  
