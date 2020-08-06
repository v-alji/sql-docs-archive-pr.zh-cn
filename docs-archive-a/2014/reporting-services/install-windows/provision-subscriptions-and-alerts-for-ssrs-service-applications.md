---
title: 用于 SSRS 服务应用程序的设置订阅和警报 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Shared Service
- SharePoint Mode [Reporting Services]
- SharePoint Mode
- Reporting Services Service Application
- SSRS service application
ms.assetid: d0de3f1f-4887-47fb-bacf-46aaad74c4be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c09033b6a31295b8fbe42058cba9059f5d05629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694308"
---
# <a name="provision-subscriptions-and-alerts-for-ssrs-service-applications"></a><span data-ttu-id="4a194-102">用于 SSRS 服务应用程序的设置订阅和警报</span><span class="sxs-lookup"><span data-stu-id="4a194-102">Provision Subscriptions and Alerts for SSRS Service Applications</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="4a194-103">订阅和数据警报需要 SQL Server 代理，还需配置 SQL Server 代理权限。</span><span class="sxs-lookup"><span data-stu-id="4a194-103">subscriptions and data alerts require SQL Server Agent and require the configuration of permissions for SQL Server Agent.</span></span> <span data-ttu-id="4a194-104">如果您看到指示“需要 SQL Server 代理”的错误消息，而您已验证 SQL Server 代理正在运行，则您需要更新或验证权限。</span><span class="sxs-lookup"><span data-stu-id="4a194-104">If you see error messages that indicate SQL Server Agent is required and you have verified SQL Server Agent is running, then update or verify permissions.</span></span> <span data-ttu-id="4a194-105">本主题限于 SharePoint 模式中的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，并说明使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅来更新 SQL Server 代理权限的三种方式。</span><span class="sxs-lookup"><span data-stu-id="4a194-105">The scope of this topic is [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode and the topic describes three ways you can update the permissions of SQL Server Agent with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions.</span></span> <span data-ttu-id="4a194-106">对于服务应用程序、msdb 和 master 数据库中的对象，在本主题的步骤中使用的凭据必须具有足够的权限来将执行权限授予 RSExecRole。</span><span class="sxs-lookup"><span data-stu-id="4a194-106">The credentials you use for the steps in this topic need to have sufficient permissions to grant execute permissions to the RSExecRole for objects in the service application, msdb, and master databases.</span></span>

||
|-|
|<span data-ttu-id="4a194-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="4a194-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="4a194-108">![对服务应用程序数据库的 SQL 代理权限](../../../2014/sql-server/install/media/rs-provisionsqlagent.gif "对服务应用程序数据库的 SQL 代理权限")</span><span class="sxs-lookup"><span data-stu-id="4a194-108">![SQL Agent permissions to Service Application DBs](../../../2014/sql-server/install/media/rs-provisionsqlagent.gif "SQL Agent permissions to Service Application DBs")</span></span>

||<span data-ttu-id="4a194-109">说明</span><span class="sxs-lookup"><span data-stu-id="4a194-109">Description</span></span>|
|------|-----------------|
|<span data-ttu-id="4a194-110">**1**</span><span class="sxs-lookup"><span data-stu-id="4a194-110">**1**</span></span>|<span data-ttu-id="4a194-111">承载 Reporting Services 服务应用程序数据库的 SQL Server 数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="4a194-111">The instance of SQL Server Database engine that is hosting the Reporting Services service application databases.</span></span>|
|<span data-ttu-id="4a194-112">**2**</span><span class="sxs-lookup"><span data-stu-id="4a194-112">**2**</span></span>|<span data-ttu-id="4a194-113">SQL 数据库引擎实例的 SQL Server 代理实例。</span><span class="sxs-lookup"><span data-stu-id="4a194-113">The instance of SQL Server agent for the instance of the SQL database engine.</span></span>|
|<span data-ttu-id="4a194-114">**3**</span><span class="sxs-lookup"><span data-stu-id="4a194-114">**3**</span></span>|<span data-ttu-id="4a194-115">Reporting Services 服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="4a194-115">The Reporting Services service application databases.</span></span> <span data-ttu-id="4a194-116">基于用于创建服务应用程序的信息的名称。</span><span class="sxs-lookup"><span data-stu-id="4a194-116">The names are based on the information used for creating the service application.</span></span> <span data-ttu-id="4a194-117">下面是示例数据库的名称：</span><span class="sxs-lookup"><span data-stu-id="4a194-117">The following are example database names:</span></span><br /><br /> <span data-ttu-id="4a194-118">ReportingService_2fbae157295d49df86d0b85760c704b0</span><span class="sxs-lookup"><span data-stu-id="4a194-118">ReportingService_2fbae157295d49df86d0b85760c704b0</span></span><br /><br /> <span data-ttu-id="4a194-119">ReportingService_2fbae157295d49df86d0b85760c704b0_Alerting</span><span class="sxs-lookup"><span data-stu-id="4a194-119">ReportingService_2fbae157295d49df86d0b85760c704b0_Alerting</span></span><br /><br /> <span data-ttu-id="4a194-120">ReportingService_2fbae157295d49df86d0b85760c704b0TempDB</span><span class="sxs-lookup"><span data-stu-id="4a194-120">ReportingService_2fbae157295d49df86d0b85760c704b0TempDB</span></span>|
|<span data-ttu-id="4a194-121">**4**</span><span class="sxs-lookup"><span data-stu-id="4a194-121">**4**</span></span>|<span data-ttu-id="4a194-122">SQL Server 数据库引擎实例的 master 和 MSDB 数据库。</span><span class="sxs-lookup"><span data-stu-id="4a194-122">The master and MSDB database of the instance of the SQL Server Database engine.</span></span>|

 <span data-ttu-id="4a194-123">使用以下三种方法之一更新权限：</span><span class="sxs-lookup"><span data-stu-id="4a194-123">Use one the following three methods to update the permissions:</span></span>

1.  <span data-ttu-id="4a194-124">在 **“设置、订阅和警报”** 页上，键入凭据并单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4a194-124">From the **Provisions and Subscriptions and Alerts** page, type credentials and click **ok**.</span></span>

2.  <span data-ttu-id="4a194-125">在“设置、订阅和警报”页上单击 **“下载脚本”** 按钮，以便下载可用于配置权限的 transact SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="4a194-125">From the Provisions and Subscriptions and Alerts page, click the **Download Script** button to download a transact SQL script that can be used to configure permissions.</span></span>

3.  <span data-ttu-id="4a194-126">运行 PowerShell cmdlet，以便生成可用于配置权限的 transact SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="4a194-126">Run a PowerShell cmdlet to build a transact SQL script that can be used to configure permissions.</span></span>

### <a name="to-update-permissions-using-the-provision-page"></a><span data-ttu-id="4a194-127">使用“设置”页更新权限</span><span class="sxs-lookup"><span data-stu-id="4a194-127">To update permissions using the provision page</span></span>

1.  <span data-ttu-id="4a194-128">在 SharePoint 管理中心内，在 **“应用程序管理”** 组中单击 **“管理服务应用程序”**</span><span class="sxs-lookup"><span data-stu-id="4a194-128">From SharePoint Central Administration, in the **Application Management** group click **Manage Service Applications**</span></span>

2.  <span data-ttu-id="4a194-129">在列表中找到您的服务应用程序，然后单击该应用程序的名称或者单击 **“类型”** 列以选择该服务应用程序，接着单击 SharePoint 功能区中的 **“管理”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="4a194-129">Find your service application in the list and click the name of the application or click the **Type** column to select the services application and click the **Manage** button in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="4a194-130">在 **“管理 Reporting Services 应用程序”** 页上，单击 **“设置订阅和警报”** 。</span><span class="sxs-lookup"><span data-stu-id="4a194-130">On the **Manage Reporting Services Application** page, click **Provision Subscriptions and Alerts**.</span></span>

4.  <span data-ttu-id="4a194-131">如果 SharePoint 管理员具有针对 Master 数据库和服务应用程序数据库的足够权限，请键入那些凭据。</span><span class="sxs-lookup"><span data-stu-id="4a194-131">If the SharePoint administrator has enough privileges to the Master database and the service application databases, type those credentials.</span></span>

5.  <span data-ttu-id="4a194-132">单击 **“确定”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="4a194-132">Click the **OK** button.</span></span>

##  <a name="to-download-the-transact-sql-script"></a><a name="bkmk_download"></a> <span data-ttu-id="4a194-133">下载 Transact-SQL 脚本</span><span class="sxs-lookup"><span data-stu-id="4a194-133">To download the Transact-SQL Script</span></span>

1.  <span data-ttu-id="4a194-134">在 SharePoint 管理中心内，在 **“应用程序管理”** 组中单击 **“管理服务应用程序”**</span><span class="sxs-lookup"><span data-stu-id="4a194-134">From SharePoint Central Administration, in the **Application Management** group click **Manage Service Applications**</span></span>

2.  <span data-ttu-id="4a194-135">在列表中找到您的服务应用程序，然后单击该应用程序的名称或者单击 **“类型”** 列以选择该服务应用程序，接着单击 SharePoint 功能区中的 **“管理”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="4a194-135">Find your service application in the list and click the name of the application or click the **Type** column to select the services application and click the **Manage** button in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="4a194-136">在 **“管理 Reporting Services 应用程序”** 页上，单击 **“设置订阅和警报”** 。</span><span class="sxs-lookup"><span data-stu-id="4a194-136">On the **Manage Reporting Services Application** page, click **Provision Subscriptions and Alerts**.</span></span>

4.  <span data-ttu-id="4a194-137">在 **“查看状态”** 区域中，验证 SQL Server 代理是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="4a194-137">In the **View Status** area, verify SQL Server Agent is running.</span></span>

5.  <span data-ttu-id="4a194-138">单击 **“下载脚本”** ，以便下载可以在 SQL Server Management Studio 中运行的 transact SQL 脚本，从而授予权限。</span><span class="sxs-lookup"><span data-stu-id="4a194-138">Click **Download Script** to download a transact SQL script you can run in SQL Server Management studio to grant permissions.</span></span> <span data-ttu-id="4a194-139">创建的脚本文件的名称将包含你的 Reporting Services 服务应用程序的名称，例如 **[服务应用程序的名称]-GrantRights.sql**。</span><span class="sxs-lookup"><span data-stu-id="4a194-139">The script file name that is created will contain the name of your Reporting Services service application name, for example **[name of the service application]-GrantRights.sql**.</span></span>

### <a name="to-generate-the-transact-sql-statement-with-powershell"></a><span data-ttu-id="4a194-140">利用 PowerShell 生成 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="4a194-140">To generate the Transact-SQL statement with PowerShell</span></span>

1.  <span data-ttu-id="4a194-141">您也可以在 SharePoint 2010 Management Shell 中使用 Windows PowerShell cmdlet 创建 Transact-SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="4a194-141">You can also use a Windows PowerShell cmdlet in the SharePoint 2010 Management Shell to create the Transact-SQL script.</span></span>

2.  <span data-ttu-id="4a194-142">在 **“开始”** 菜单上，单击 **“所有程序”** 。</span><span class="sxs-lookup"><span data-stu-id="4a194-142">On the **Start** menu, click **All Programs**.</span></span>

3.  <span data-ttu-id="4a194-143">展开 **“Microsoft SharePoint 2010 产品”** ，然后单击 **“SharePoint 2010 Management Shell”**。</span><span class="sxs-lookup"><span data-stu-id="4a194-143">Expand **Microsoft SharePoint 2010 Products** and click **SharePoint 2010 Management Shell**.</span></span>

4.  <span data-ttu-id="4a194-144">通过替换报表服务器数据库的名称、应用程序池帐户和语句路径来更新下面的 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a194-144">Update the following PowerShell cmdlet by replacing the name of the report server database, application pool account, and the path of the statement.</span></span>

     <span data-ttu-id="4a194-145">**cmdlet 的语法：** `Get-SPRSDatabaseRightsScript -DatabaseName <ReportingServices database name> -UserName <app pool account> -IsWindowsUser | Out-File <path of statement>`</span><span class="sxs-lookup"><span data-stu-id="4a194-145">**Syntax of cmdlet:** `Get-SPRSDatabaseRightsScript -DatabaseName <ReportingServices database name> -UserName <app pool account> -IsWindowsUser | Out-File <path of statement>`</span></span>

     <span data-ttu-id="4a194-146">**示例 cmdlet：** `Get-SPRSDatabaseRightsScript -DatabaseName ReportingService_46fd00359f894b828907b254e3f6257c -UserName "NT AUTHORITY\NETWORK SERVICE" -IsWindowsUser | Out-File c:\SQLServerAgentrights.sql`</span><span class="sxs-lookup"><span data-stu-id="4a194-146">**Sample cmdlet:** `Get-SPRSDatabaseRightsScript -DatabaseName ReportingService_46fd00359f894b828907b254e3f6257c -UserName "NT AUTHORITY\NETWORK SERVICE" -IsWindowsUser | Out-File c:\SQLServerAgentrights.sql`</span></span>

## <a name="using-the-transact-sql-script"></a><span data-ttu-id="4a194-147">使用 Transact-SQL 脚本</span><span class="sxs-lookup"><span data-stu-id="4a194-147">Using the Transact-SQL Script</span></span>
 <span data-ttu-id="4a194-148">以下过程可用于通过“设置”页下载的脚本或使用 PowerShell 创建的脚本。</span><span class="sxs-lookup"><span data-stu-id="4a194-148">The following procedures can be used with scripts download from the provisions page or scripts created using PowerShell.</span></span>

#### <a name="to-load-the-transact-sql-script-in-sql-server-management-studio"></a><span data-ttu-id="4a194-149">在 SQL Server Management Studio 中加载 Transact-SQL 脚本</span><span class="sxs-lookup"><span data-stu-id="4a194-149">To load the Transact-SQL script in SQL Server Management Studio</span></span>

1.  <span data-ttu-id="4a194-150">若要打开 SQL Server Management Studio，请在 "**开始**" 菜单上单击 " **Microsoft SQL Server 2012** "，然后单击 " **SQL Server Management Studio**"。</span><span class="sxs-lookup"><span data-stu-id="4a194-150">To open SQL Server Management Studio, on the **Start** menu, click **Microsoft SQL Server 2012** and click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="4a194-151">在 **“连接到服务器”** 对话框中，设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="4a194-151">In the **Connect to Server** dialog box set the following options:</span></span>

    -   <span data-ttu-id="4a194-152">在 **“服务器类型”** 列表中，选择 **“数据库引擎”**</span><span class="sxs-lookup"><span data-stu-id="4a194-152">In the **Server type** list, select **Database Engine**</span></span>

    -   <span data-ttu-id="4a194-153">在 **“服务器名称”** 中键入要在其上配置 SQL Server 代理的 SQL Server 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="4a194-153">In **Server Name**, type the name of the SQL Server instance on which you want to configure SQL Server Agent.</span></span>

    -   <span data-ttu-id="4a194-154">选择身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="4a194-154">Select an authentication mode.</span></span>

    -   <span data-ttu-id="4a194-155">如果使用 SQL Server 身份验证进行连接，请提供登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="4a194-155">If connecting using SQL Server Authentication, provide a login and password.</span></span>

3.  <span data-ttu-id="4a194-156">单击“连接”  。</span><span class="sxs-lookup"><span data-stu-id="4a194-156">Click **Connect**.</span></span>

#### <a name="to-run-the-transact-sql-statement"></a><span data-ttu-id="4a194-157">运行 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="4a194-157">To run the Transact-SQL statement</span></span>

1.  <span data-ttu-id="4a194-158">在 SQL Server Management Studio 的工具栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4a194-158">On the toolbar of SQL Server Management Studio, click **New Query**.</span></span>

2.  <span data-ttu-id="4a194-159">在 **“文件”** 菜单上，单击 **“打开”** ，然后单击 **“文件”** 。</span><span class="sxs-lookup"><span data-stu-id="4a194-159">On the **File** menu, click **Open**, and then click **File**.</span></span>

3.  <span data-ttu-id="4a194-160">定位到保存 SharePoint 2010 Management Shell 中生成的 Transact-SQL 语句的文件夹。</span><span class="sxs-lookup"><span data-stu-id="4a194-160">Navigate to the folder where you saved the Transact-SQL statement that you generated in SharePoint 2010 Management Shell.</span></span>

4.  <span data-ttu-id="4a194-161">单击该文件，然后单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="4a194-161">Click the file and then click **Open**.</span></span>

     <span data-ttu-id="4a194-162">该语句将添加到查询窗口。</span><span class="sxs-lookup"><span data-stu-id="4a194-162">The statement is added to the query window.</span></span>

5.  <span data-ttu-id="4a194-163">单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="4a194-163">Click **Execute**.</span></span>


