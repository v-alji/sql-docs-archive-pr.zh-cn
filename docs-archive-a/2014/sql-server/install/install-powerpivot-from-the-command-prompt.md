---
title: 从命令提示符安装 PowerPivot |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7f1f2b28-c9f5-49ad-934b-02f2fa6b9328
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 54f30142cdc2e39b3ec565d4f965fdad675405e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590524"
---
# <a name="install-powerpivot-from-the-command-prompt"></a><span data-ttu-id="0e35b-102">从命令提示符安装 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="0e35b-102">Install PowerPivot from the Command Prompt</span></span>
  <span data-ttu-id="0e35b-103">您可以从命令行运行安装程序以便安装 SQL Server PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="0e35b-103">You can run Setup from the command line to install SQL Server PowerPivot for SharePoint.</span></span> <span data-ttu-id="0e35b-104">您必须在命令中包含 `/ROLE` 参数并排除 `/FEATURES` 参数。</span><span class="sxs-lookup"><span data-stu-id="0e35b-104">You must include the `/ROLE` parameter in your command and exclude the `/FEATURES` parameter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0e35b-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="0e35b-105">Prerequisites</span></span>  
 <span data-ttu-id="0e35b-106">必须安装 SharePoint Server 2010 Enterprise Edition Service Pack 1 (SP1)。</span><span class="sxs-lookup"><span data-stu-id="0e35b-106">SharePoint Server 2010 enterprise edition with Service Pack 1 (SP1) must be installed.</span></span>  
  
 <span data-ttu-id="0e35b-107">您必须使用域帐户来设置 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="0e35b-107">You must use domain accounts to provision Analysis Services.</span></span>  
  
 <span data-ttu-id="0e35b-108">必须将计算机加入到 SharePoint 场所在的域中。</span><span class="sxs-lookup"><span data-stu-id="0e35b-108">The computer must be joined to the same domain as the SharePoint farm.</span></span>  
  
##  <a name="role-based-installation-options"></a><a name="Commands"></a><span data-ttu-id="0e35b-109">基于/ROLE 的安装选项</span><span class="sxs-lookup"><span data-stu-id="0e35b-109">/ROLE based installation options</span></span>  
 <span data-ttu-id="0e35b-110">对于 PowerPivot for SharePoint 部署，用 `/ROLE` 参数代替 `/FEATURES` 参数。</span><span class="sxs-lookup"><span data-stu-id="0e35b-110">For PowerPivot for SharePoint deployments, the `/ROLE` parameter is used in place of the `/FEATURES` parameter.</span></span> <span data-ttu-id="0e35b-111">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="0e35b-111">Valid values include:</span></span>  
  
-   `SPI_AS_ExistingFarm`  
  
-   `SPI_AS_NewFarm`  
  
 <span data-ttu-id="0e35b-112">这两个角色均安装使 PowerPivot for SharePoint 能够在 SharePoint 场中运行的应用程序、配置和部署文件。</span><span class="sxs-lookup"><span data-stu-id="0e35b-112">Both roles install application, configuration, and deployment files that enable a PowerPivot for SharePoint to run in a SharePoint farm.</span></span> <span data-ttu-id="0e35b-113">指定任何一个角色都将导致安装程序检查 SharePoint 集成所需的硬件和软件要求。</span><span class="sxs-lookup"><span data-stu-id="0e35b-113">Specifying either role will cause Setup to check for hardware and software requirements necessary for SharePoint integration.</span></span>  
  
 <span data-ttu-id="0e35b-114">“现有场”选项假定已经存在 SharePoint 场。</span><span class="sxs-lookup"><span data-stu-id="0e35b-114">The existing farm option assumes that a SharePoint farm is already in place.</span></span> <span data-ttu-id="0e35b-115">"新建场" 选项假设你将创建新的场;它支持在命令行语法中添加数据库引擎实例，以便可以将数据库引擎实例用作场的数据库服务器。</span><span class="sxs-lookup"><span data-stu-id="0e35b-115">The new farm option assumes that you will create a new farm; it supports the addition of a Database Engine instance in the command line syntax so that you can use the Database Engine instance as the farm's database server.</span></span>  
  
 <span data-ttu-id="0e35b-116">与以往的版本相比，所有的服务器配置任务都作为安装后的任务来执行。</span><span class="sxs-lookup"><span data-stu-id="0e35b-116">In contrast with the previous releases, all server configuration tasks are performed as post-installation tasks.</span></span> <span data-ttu-id="0e35b-117">如果要自动执行安装和配置步骤，则可以使用 PowerShell 来配置服务器。</span><span class="sxs-lookup"><span data-stu-id="0e35b-117">If you are automating installation and configuration steps, you can use PowerShell to configure the server.</span></span> <span data-ttu-id="0e35b-118">有关详细信息，请参阅[使用 Windows PowerShell 的 PowerPivot 配置](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="0e35b-118">For more information, see [PowerPivot Configuration using Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).</span></span>  
  
## <a name="example-commands"></a><span data-ttu-id="0e35b-119">示例命令</span><span class="sxs-lookup"><span data-stu-id="0e35b-119">Example Commands</span></span>  
 <span data-ttu-id="0e35b-120">下列示例说明了每个选项的用法。</span><span class="sxs-lookup"><span data-stu-id="0e35b-120">The following examples illustrate the usage of each option.</span></span> <span data-ttu-id="0e35b-121">示例1显示 `SPI_AS_ExistingFarm` 。</span><span class="sxs-lookup"><span data-stu-id="0e35b-121">Example 1 shows `SPI_AS_ExistingFarm`.</span></span>  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 <span data-ttu-id="0e35b-122">示例 2 演示 `SPI_AS_NewFarm`。</span><span class="sxs-lookup"><span data-stu-id="0e35b-122">Example 2 shows `SPI_AS_NewFarm`.</span></span> <span data-ttu-id="0e35b-123">请注意，它包括用于设置数据库引擎的参数。</span><span class="sxs-lookup"><span data-stu-id="0e35b-123">Notice that it includes parameters for provisioning the Database Engine.</span></span>  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_NewFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/SQLSVCACCOUNT=<DomainName\UserName> /SQLSVCPASSWORD=<StrongPassword> /SQLSYSADMINACCOUNTS=<DomainName\UserName> /AGTSVCACCOUNT=<DomainName\UserName> /AGTSVCPASSWORD=<StrongPassword> /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
##  <a name="modifying-the-command-syntax"></a><a name="Join"></a><span data-ttu-id="0e35b-124">修改命令语法</span><span class="sxs-lookup"><span data-stu-id="0e35b-124">Modifying the command syntax</span></span>  
 <span data-ttu-id="0e35b-125">使用以下步骤可以修改示例命令语法。</span><span class="sxs-lookup"><span data-stu-id="0e35b-125">Use the following steps to modify the example command syntax.</span></span>  
  
1.  <span data-ttu-id="0e35b-126">将以下命令复制到记事本中：</span><span class="sxs-lookup"><span data-stu-id="0e35b-126">Copy the following command into Notepad:</span></span>  
  
    ```cmd
    Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
    ```  
  
     <span data-ttu-id="0e35b-127">`/q` 参数以不显示用户界面的静默模式运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="0e35b-127">The `/q` parameter runs Setup in quiet mode, which suppresses the user interface.</span></span>  
  
     <span data-ttu-id="0e35b-128">如果为无人参与的安装指定了 `/IAcceptSQLServerLicenseTerms` 或 `/q` 参数，则 `/qs` 是必需的。</span><span class="sxs-lookup"><span data-stu-id="0e35b-128">The `/IAcceptSQLServerLicenseTerms` is required when the `/q` or `/qs` parameter is specified for un-attended installations.</span></span>  
  
     <span data-ttu-id="0e35b-129">`/action` 参数指示安装程序执行安装。</span><span class="sxs-lookup"><span data-stu-id="0e35b-129">The `/action` parameter instructs Setup to perform an installation.</span></span>  
  
     <span data-ttu-id="0e35b-130">`/role` 参数指示安装程序安装 PowerPivot for SharePoint 所需的 Analysis Services 程序和配置文件。</span><span class="sxs-lookup"><span data-stu-id="0e35b-130">The `/role` parameter instructs Setup to install the Analysis Services program and configuration files required for PowerPivot for SharePoint.</span></span> <span data-ttu-id="0e35b-131">此角色还检测并使用现有场连接信息来访问 SharePoint 配置数据库。</span><span class="sxs-lookup"><span data-stu-id="0e35b-131">This role also detects and uses the existing farm connectivity information to access the SharePoint configuration database.</span></span> <span data-ttu-id="0e35b-132">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="0e35b-132">This parameter is required.</span></span> <span data-ttu-id="0e35b-133">使用该参数（而非 `/features` 参数）指定要安装的组件。</span><span class="sxs-lookup"><span data-stu-id="0e35b-133">Use it instead of the `/features` parameter to specify the components to install.</span></span>  
  
     <span data-ttu-id="0e35b-134">`/instancename` 参数将“PowerPivot”指定为命名实例。</span><span class="sxs-lookup"><span data-stu-id="0e35b-134">The `/instancename` parameter specifies 'PowerPivot' as a named instance.</span></span> <span data-ttu-id="0e35b-135">此值是硬编码的，因此不能更改。</span><span class="sxs-lookup"><span data-stu-id="0e35b-135">This value is hard-coded and cannot be changed.</span></span> <span data-ttu-id="0e35b-136">出于教育目的在命令中指定该值，以便您知道该服务是如何安装的。</span><span class="sxs-lookup"><span data-stu-id="0e35b-136">It is specified in the command for educational purposes so that you know how the service is installed.</span></span>  
  
     <span data-ttu-id="0e35b-137">`/indicateprogress` 参数允许您在命令提示符窗口中监视进度。</span><span class="sxs-lookup"><span data-stu-id="0e35b-137">The `/indicateprogress` parameter allows you to monitor progress in the command prompt window.</span></span>  
  
2.  <span data-ttu-id="0e35b-138">`PID` 参数从命令中省略，该参数将导致安装 Evaluation 版本。</span><span class="sxs-lookup"><span data-stu-id="0e35b-138">The `PID` parameter is omitted from the command, which causes the Evaluation edition to be installed.</span></span> <span data-ttu-id="0e35b-139">如果您想要安装 Enterprise 版本，则将 PID 添加到您的安装程序命令中并且提供有效的产品密钥。</span><span class="sxs-lookup"><span data-stu-id="0e35b-139">If you want to install the Enterprise edition, add the PID to your Setup command and provide a valid product key.</span></span>  
  
    ```  
    /PID=<product key for an Enterprise installation>  
    ```  
  
3.  <span data-ttu-id="0e35b-140">将和的占位符替换为 \<domain\username> \<StrongPassword> 有效的用户帐户和密码。</span><span class="sxs-lookup"><span data-stu-id="0e35b-140">Replace the placeholders for \<domain\username> and \<StrongPassword>with valid user accounts and passwords.</span></span>  
  
     <span data-ttu-id="0e35b-141">`/assvaccount`和 **/assvcpassword**参数用于在 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 应用程序服务器上配置实例。</span><span class="sxs-lookup"><span data-stu-id="0e35b-141">The `/assvaccount` and **/assvcpassword** parameters are used to configure the [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance on the application server.</span></span> <span data-ttu-id="0e35b-142">请使用有效的帐户信息替换这些占位符。</span><span class="sxs-lookup"><span data-stu-id="0e35b-142">Replace these placeholders with valid account information.</span></span>  
  
     <span data-ttu-id="0e35b-143">**/Assysadminaccounts**参数必须设置为运行 SQL Server 安装程序的用户的标识。</span><span class="sxs-lookup"><span data-stu-id="0e35b-143">The **/assysadminaccounts** parameter must be set to the identity of the user who is running SQL Server Setup.</span></span> <span data-ttu-id="0e35b-144">您必须至少指定一个系统管理员。</span><span class="sxs-lookup"><span data-stu-id="0e35b-144">You must specify at least one system administrator.</span></span> <span data-ttu-id="0e35b-145">请注意，SQL Server 安装程序不再自动将 sysadmin 权限授予内置 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="0e35b-145">Note that SQL Server Setup no long grants automatic sysadmin permissions to members of the built-in Administrators group.</span></span>  
  
4.  <span data-ttu-id="0e35b-146">删除换行符。</span><span class="sxs-lookup"><span data-stu-id="0e35b-146">Remove line breaks.</span></span>  
  
5.  <span data-ttu-id="0e35b-147">选择整个命令，然后在 "编辑" 菜单中单击 "**复制**"。</span><span class="sxs-lookup"><span data-stu-id="0e35b-147">Select the entire command and then click **Copy** on the Edit menu.</span></span>  
  
6.  <span data-ttu-id="0e35b-148">打开管理员命令提示符。</span><span class="sxs-lookup"><span data-stu-id="0e35b-148">Open an administrator command prompt.</span></span> <span data-ttu-id="0e35b-149">为此，请单击 "**开始**"，右键单击命令提示符，然后选择 "以**管理员身份运行**"。</span><span class="sxs-lookup"><span data-stu-id="0e35b-149">To do this, click **Start**, right-click the command prompt, and select **Run as administrator**.</span></span>  
  
7.  <span data-ttu-id="0e35b-150">导航到包含 SQL Server 安装介质的驱动器或共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="0e35b-150">Navigate to the drive or shared folder that contains the SQL Server installation media.</span></span>  
  
8.  <span data-ttu-id="0e35b-151">将修正后的命令粘贴到命令行中。</span><span class="sxs-lookup"><span data-stu-id="0e35b-151">Paste the revised command into the command line.</span></span> <span data-ttu-id="0e35b-152">为此，请单击命令提示符窗口左上角的图标，指向 "**编辑**"，然后单击 "**粘贴**"。</span><span class="sxs-lookup"><span data-stu-id="0e35b-152">To do this, click the icon in the top left corner of the command prompt window, point to **Edit**, and then click **Paste**.</span></span>  
  
9. <span data-ttu-id="0e35b-153">按**enter**运行该命令。</span><span class="sxs-lookup"><span data-stu-id="0e35b-153">Press **Enter** to run the command.</span></span> <span data-ttu-id="0e35b-154">等待安装程序完成。</span><span class="sxs-lookup"><span data-stu-id="0e35b-154">Wait for setup to complete.</span></span> <span data-ttu-id="0e35b-155">您可以在命令提示符窗口中监视安装程序的进度。</span><span class="sxs-lookup"><span data-stu-id="0e35b-155">You can monitor Setup's progress in the command prompt window.</span></span>  
  
10. <span data-ttu-id="0e35b-156">若要验证安装，请检查 \Program Files\SQL Server\120\Setup Bootstrap\Log 处的 summary.txt 文件。</span><span class="sxs-lookup"><span data-stu-id="0e35b-156">To verify installation, check the summary.txt file at \Program Files\SQL Server\120\Setup Bootstrap\Log.</span></span> <span data-ttu-id="0e35b-157">如果服务器成功安装并且没有任何错误，最终的结果应显示“Passed”。</span><span class="sxs-lookup"><span data-stu-id="0e35b-157">Final result should say "Passed" if the server installed without errors.</span></span>  
  
11. <span data-ttu-id="0e35b-158">配置服务器。</span><span class="sxs-lookup"><span data-stu-id="0e35b-158">Configure the server.</span></span> <span data-ttu-id="0e35b-159">至少您必须部署解决方案，创建服务应用程序，并为各网站集启用功能。</span><span class="sxs-lookup"><span data-stu-id="0e35b-159">At a minimum, you must deploy solutions, create a service application, and enable the feature for each site collection.</span></span> <span data-ttu-id="0e35b-160">有关详细信息，请参阅[配置或修复 PowerPivot for SharePoint 2010 &#40;PowerPivot 配置工具&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)或[在管理中心中管理和配置 powerpivot 服务器](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)。</span><span class="sxs-lookup"><span data-stu-id="0e35b-160">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md) or [PowerPivot Server Administration and Configuration in Central Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e35b-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e35b-161">See Also</span></span>  
 <span data-ttu-id="0e35b-162">[配置 PowerPivot 服务帐户](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts) </span><span class="sxs-lookup"><span data-stu-id="0e35b-162">[Configure PowerPivot Service Accounts](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts) </span></span>  
 [<span data-ttu-id="0e35b-163">PowerPivot for SharePoint 2010 安装</span><span class="sxs-lookup"><span data-stu-id="0e35b-163">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
