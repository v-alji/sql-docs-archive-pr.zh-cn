---
title: 执行包实用工具 (DtExecUI) 的 UI 参考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtexecui.general.f1
- sql12.dts.dtexecui.executionoptions.f1
- sql12.dts.dtexecui.configuration.f1
- sql12.dts.dtexecui.setvalues.f1
- sql12.dts.dtexecui.commandline.f1
- sql12.dts.dtexecui.commandfiles.f1
- sql12.dts.dtexecui.verification.f1
- sql12.dts.dtexecui.datasources.f1
- sql12.dts.dtexecui.reporting.f1
- sql12.dts.dtexecui.logging.f1
helpviewer_keywords:
- DTExecUI utility
ms.assetid: 3d71df39-126b-4c8e-bd77-128bbd5b0887
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 13601983a4ab841a2b64ff8e4fc722fcf5ae496c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587897"
---
# <a name="execute-package-utility-dtexecui-ui-reference"></a><span data-ttu-id="46d0d-102">执行包实用工具 (DtExecUI) UI 参考</span><span class="sxs-lookup"><span data-stu-id="46d0d-102">Execute Package Utility (DtExecUI) UI Reference</span></span>
  <span data-ttu-id="46d0d-103">使用 **“执行包实用工具”** 来运行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-103">Use the **Execute Package Utility** to run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="46d0d-104">该实用工具运行存储在以下三个位置之一的包：[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库、[!INCLUDE[ssIS](../../includes/ssis-md.md)] 包存储区和文件系统。</span><span class="sxs-lookup"><span data-stu-id="46d0d-104">The utility runs packages that are stored in one of three locations: [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span> <span data-ttu-id="46d0d-105">此用户界面 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] `dtexecui` 是使用**DTExec**命令提示工具运行包的替代方法，可通过在命令提示符下打开或在命令提示符下键入。</span><span class="sxs-lookup"><span data-stu-id="46d0d-105">This user interface, which can be opened from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or by typing `dtexecui` at a command prompt, is an alternative to running packages by using the **DTExec** command prompt tool.</span></span>  
  
 <span data-ttu-id="46d0d-106">包与 **dtexecui.exe** 实用工具在同一个进程中执行。</span><span class="sxs-lookup"><span data-stu-id="46d0d-106">Packages execute in the same process as the **dtexecui.exe** utility.</span></span> <span data-ttu-id="46d0d-107">由于此实用工具为 32 位工具，因此，在 64 位环境中使用 **dtexecui.exe** 运行的包是在 Windows on Win32 (WOW) 中运行的。</span><span class="sxs-lookup"><span data-stu-id="46d0d-107">Because this utility is a 32-bit tool, packages run by using **dtexecui.exe** in a 64-bit environment run in Windows on Win32 (WOW).</span></span> <span data-ttu-id="46d0d-108">当在 64 位计算机上使用 dtexecui.exe 实用工具开发和测试命令时，应该首先在 64 位模式下使用 64 位版本的 **dtexec.exe** 测试该命令，然后在生产服务器中部署或安排这些命令。</span><span class="sxs-lookup"><span data-stu-id="46d0d-108">When developing and testing commands by using the dtexecui.exe utility on a 64-bit computer, you should test the commands in 64-bit mode by using the 64-bit version of **dtexec.exe** before deploying or scheduling the commands on a production server.</span></span>  
  
 <span data-ttu-id="46d0d-109">“执行包实用工具”  是用于 **DTExec** 命令提示工具的图形用户界面。</span><span class="sxs-lookup"><span data-stu-id="46d0d-109">The **Execute Package Utility** is a graphical user interface for the **DTExec** command prompt tool.</span></span> <span data-ttu-id="46d0d-110">通过指定的选项运行包时，此用户界面可使配置选项的工作变得更轻松，并会自动汇集传递到 **DTExec** 命令提示工具的命令行。</span><span class="sxs-lookup"><span data-stu-id="46d0d-110">The user interface makes it easy to configure options and it automatically assembles the command line that is passed to the **DTExec** command prompt tool when you run the package from the specified options.</span></span>  
  
 <span data-ttu-id="46d0d-111">“执行包实用工具”  还可用于汇集在直接运行 **DTExec** 时所用的命令行。</span><span class="sxs-lookup"><span data-stu-id="46d0d-111">The **Execute Package Utility** can also be used to assemble command lines that you use when running **DTExec** directly.</span></span>  
  
### <a name="to-open-execute-package-utility-in-sql-server-management-studio"></a><span data-ttu-id="46d0d-112">打开 SQL Server Management Studio 中的执行包实用工具</span><span class="sxs-lookup"><span data-stu-id="46d0d-112">To open Execute Package Utility in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="46d0d-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 **“视图”** 菜单中，单击 **“对象资源管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="46d0d-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="46d0d-114">在对象资源管理器中，单击 **“连接”** ，然后单击 **“Integration Services”** 。</span><span class="sxs-lookup"><span data-stu-id="46d0d-114">In Object Explorer, click **Connect**, and then click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="46d0d-115">在 **“连接到服务器”** 对话框中的 **“服务器名称”** 列表中输入服务器名称，然后单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="46d0d-115">In the **Connect to Server** dialog box, enter the server name in the **Server name** list, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="46d0d-116">展开“已存储的包”  文件夹和子文件夹，右键单击要运行的包，然后单击“运行包”  。</span><span class="sxs-lookup"><span data-stu-id="46d0d-116">Expand the **Stored Package**s folder and subfolders, right-click the package you want to run, and then click **Run Package**.</span></span>  
  
### <a name="to-open-the-execute-package-utility-at-the-command-prompt"></a><span data-ttu-id="46d0d-117">在命令提示符下打开执行包实用工具</span><span class="sxs-lookup"><span data-stu-id="46d0d-117">To open the Execute Package Utility at the Command Prompt</span></span>  
  
-   <span data-ttu-id="46d0d-118">在命令提示符窗口中，运行 `dtexecui`。</span><span class="sxs-lookup"><span data-stu-id="46d0d-118">In a command prompt window, run `dtexecui`.</span></span>  
  
 <span data-ttu-id="46d0d-119">以下各节描述了 **“执行包实用工具”** 对话框的各页。</span><span class="sxs-lookup"><span data-stu-id="46d0d-119">The following sections describe pages of the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="general-page"></a><span data-ttu-id="46d0d-120">“常规”页</span><span class="sxs-lookup"><span data-stu-id="46d0d-120">General Page</span></span>  
 <span data-ttu-id="46d0d-121">使用 **“执行包实用工具”** 对话框的 **“常规”** 页，可以指定包的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="46d0d-121">Use the **General** page of the **Execute Package Utility** dialog box to specify a package name and location.</span></span>  
  
 <span data-ttu-id="46d0d-122">执行包实用工具 (dtexecui.exe) 始终在本地计算机上运行包，即使包保存在远程服务器上也是如此。</span><span class="sxs-lookup"><span data-stu-id="46d0d-122">The Execute Package utility (dtexecui.exe) always runs a package on the local computer, even if the package is saved on a remote server.</span></span> <span data-ttu-id="46d0d-123">如果远程包使用同样保存在远程服务器上的配置文件，那么执行包实用工具可能找不到配置，包将失败。</span><span class="sxs-lookup"><span data-stu-id="46d0d-123">If the remote package uses configuration files that also are saved on the remote server, then the Execute Package utility may not locate the configurations and the package fails.</span></span> <span data-ttu-id="46d0d-124">若要避免此问题，必须使用通用命名约定 (UNC) 共享名称（如 \\\myserver\myfile）引用配置。</span><span class="sxs-lookup"><span data-stu-id="46d0d-124">To avoid this problem, the configurations must be referenced by using a Universal Naming Convention (UNC) share name like \\\myserver\myfile.</span></span>  
  
### <a name="static-options"></a><span data-ttu-id="46d0d-125">静态选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-125">Static Options</span></span>  
 <span data-ttu-id="46d0d-126">**包源**</span><span class="sxs-lookup"><span data-stu-id="46d0d-126">**Package source**</span></span>  
 <span data-ttu-id="46d0d-127">使用以下选项指定要运行的包的位置：</span><span class="sxs-lookup"><span data-stu-id="46d0d-127">Specify the location of the package to run, using the following options:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46d0d-128">值</span><span class="sxs-lookup"><span data-stu-id="46d0d-128">Value</span></span>|<span data-ttu-id="46d0d-129">说明</span><span class="sxs-lookup"><span data-stu-id="46d0d-129">Description</span></span>|  
|<span data-ttu-id="46d0d-130">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="46d0d-130">**SQL Server**</span></span>|<span data-ttu-id="46d0d-131">当包驻留在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时选择此选项。</span><span class="sxs-lookup"><span data-stu-id="46d0d-131">Select this option when the package resides in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="46d0d-132">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="46d0d-132">Specify an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and provide a user name and password for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="46d0d-133">每个用户名和密码会将 /USER username 和 /PASSWORD password 选项添加到命令提示符     。</span><span class="sxs-lookup"><span data-stu-id="46d0d-133">Each user name and password adds the **/USER** _username_ and **/PASSWORD** _password_ options to the command prompt.</span></span>|  
|<span data-ttu-id="46d0d-134">**文件系统**</span><span class="sxs-lookup"><span data-stu-id="46d0d-134">**File system**</span></span>|<span data-ttu-id="46d0d-135">当包驻留在文件系统时选择此选项。</span><span class="sxs-lookup"><span data-stu-id="46d0d-135">Select this option when the package resides in the file system.</span></span>|  
|<span data-ttu-id="46d0d-136">**SSIS 包存储区**</span><span class="sxs-lookup"><span data-stu-id="46d0d-136">**SSIS Package Store**</span></span>|<span data-ttu-id="46d0d-137">当包驻留在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包存储区时选择此选项。</span><span class="sxs-lookup"><span data-stu-id="46d0d-137">Select this option when the package resides in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store.</span></span>|  
  
 <span data-ttu-id="46d0d-138">上述选择的每一项都包括以下一组选项：</span><span class="sxs-lookup"><span data-stu-id="46d0d-138">Each of these selections has the following set of options.</span></span>  
  
 <span data-ttu-id="46d0d-139">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-139">**Execute**</span></span>  
 <span data-ttu-id="46d0d-140">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-140">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-141">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-141">**Close**</span></span>  
 <span data-ttu-id="46d0d-142">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-142">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
### <a name="dynamic-options"></a><span data-ttu-id="46d0d-143">动态选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-143">Dynamic Options</span></span>  
  
#### <a name="package-source--sql-server"></a><span data-ttu-id="46d0d-144">包源 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="46d0d-144">Package Source = SQL Server</span></span>  
 <span data-ttu-id="46d0d-145">**Server**</span><span class="sxs-lookup"><span data-stu-id="46d0d-145">**Server**</span></span>  
 <span data-ttu-id="46d0d-146">输入包驻留的服务器的名称，或者从列表中选择服务器。</span><span class="sxs-lookup"><span data-stu-id="46d0d-146">Type the name of the server where the package resides, or select a server from the list.</span></span>  
  
 <span data-ttu-id="46d0d-147">**登录到服务器**</span><span class="sxs-lookup"><span data-stu-id="46d0d-147">**Log on to the server**</span></span>  
 <span data-ttu-id="46d0d-148">指定包使用 Windows 身份验证还是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="46d0d-148">Specify whether the package should use Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="46d0d-149">为了实现更好的安全性，建议使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="46d0d-149">Windows Authentication is recommended for better security.</span></span> <span data-ttu-id="46d0d-150">使用 Windows 身份验证时无需指定用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="46d0d-150">With Windows Authentication you do not have to specify a user name and password.</span></span>  
  
 <span data-ttu-id="46d0d-151">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="46d0d-151">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="46d0d-152">选择此选项，可以使用 Windows 身份验证，并使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 用户帐户登录。</span><span class="sxs-lookup"><span data-stu-id="46d0d-152">Select this option to use Windows Authentication and log on using a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
 <span data-ttu-id="46d0d-153">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="46d0d-153">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="46d0d-154">选择此选项，可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="46d0d-154">Select this option to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="46d0d-155">当用户使用指定的登录名和密码从不可信连接进行连接时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将通过检查是否已设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录帐户以及指定的密码是否与以前记录的密码匹配，来进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="46d0d-155">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="46d0d-156">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 找不到登录帐户，则身份验证会失败，用户将收到错误消息。</span><span class="sxs-lookup"><span data-stu-id="46d0d-156">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot find the login account, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="46d0d-157">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="46d0d-157">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="46d0d-158">**包**</span><span class="sxs-lookup"><span data-stu-id="46d0d-158">**Package**</span></span>  
 <span data-ttu-id="46d0d-159">键入包的名称或者单击省略号按钮 (…)，使用“选择 SSIS 包”对话框定位包   。</span><span class="sxs-lookup"><span data-stu-id="46d0d-159">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the **Select an SSIS Package** dialog box.</span></span>  
  
#### <a name="package-source--file-system"></a><span data-ttu-id="46d0d-160">包源 = 文件系统</span><span class="sxs-lookup"><span data-stu-id="46d0d-160">Package Source = File System</span></span>  
 <span data-ttu-id="46d0d-161">**包**</span><span class="sxs-lookup"><span data-stu-id="46d0d-161">**Package**</span></span>  
 <span data-ttu-id="46d0d-162">键入包的名称或者单击省略号按钮 (…) ，使用“打开”对话框定位包  。</span><span class="sxs-lookup"><span data-stu-id="46d0d-162">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the Open dialog box.</span></span> <span data-ttu-id="46d0d-163">默认情况下，该对话框仅列出扩展名为 .dtsx 的文件。</span><span class="sxs-lookup"><span data-stu-id="46d0d-163">By default, the dialog box lists only files that have the .dtsx extension.</span></span>  
  
#### <a name="package-source--ssis-package-store"></a><span data-ttu-id="46d0d-164">包源 = SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="46d0d-164">Package Source = SSIS Package Store</span></span>  
 <span data-ttu-id="46d0d-165">**Server**</span><span class="sxs-lookup"><span data-stu-id="46d0d-165">**Server**</span></span>  
 <span data-ttu-id="46d0d-166">输入包驻留的计算机的名称，或者从列表中选择计算机。</span><span class="sxs-lookup"><span data-stu-id="46d0d-166">Type the name of the computer where the package resides, or select a computer from the list.</span></span>  
  
 <span data-ttu-id="46d0d-167">**登录到服务器**</span><span class="sxs-lookup"><span data-stu-id="46d0d-167">**Log on to the server**</span></span>  
 <span data-ttu-id="46d0d-168">指定包是否使用 Microsoft Windows 身份验证连接到包源。</span><span class="sxs-lookup"><span data-stu-id="46d0d-168">Specify whether the package should use Microsoft Windows Authentication to connect to the package source.</span></span> <span data-ttu-id="46d0d-169">为了实现更好的安全性，建议使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="46d0d-169">Windows Authentication is recommended for better security.</span></span> <span data-ttu-id="46d0d-170">使用 Windows 身份验证时无需指定用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="46d0d-170">With Windows Authentication you do not have to specify a user name and password.</span></span>  
  
 <span data-ttu-id="46d0d-171">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="46d0d-171">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="46d0d-172">选择此选项可以使用 Windows 身份验证，并使用 Microsoft Windows 用户帐户登录。</span><span class="sxs-lookup"><span data-stu-id="46d0d-172">Select this option to use Windows Authentication and log on using a Microsoft Windows user account.</span></span>  
  
 <span data-ttu-id="46d0d-173">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="46d0d-173">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="46d0d-174">在运行存储于“SSIS 包存储区”  的包时，此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="46d0d-174">This option is not available when you run a package stored in the **SSIS Package Store**.</span></span>  
  
 <span data-ttu-id="46d0d-175">**包**</span><span class="sxs-lookup"><span data-stu-id="46d0d-175">**Package**</span></span>  
 <span data-ttu-id="46d0d-176">键入包的名称或者单击省略号按钮 (…)，使用“选择 SSIS 包”对话框定位包   。</span><span class="sxs-lookup"><span data-stu-id="46d0d-176">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the **Select an SSIS Package** dialog box.</span></span>  
  
## <a name="configurations-page"></a><span data-ttu-id="46d0d-177">配置页</span><span class="sxs-lookup"><span data-stu-id="46d0d-177">Configurations Page</span></span>  
 <span data-ttu-id="46d0d-178">可以使用 **“执行包实用工具”** 对话框的 **“配置”** 页，选择在运行时加载的配置文件并指定它们的加载顺序。</span><span class="sxs-lookup"><span data-stu-id="46d0d-178">Use the **Configurations** page of the **Execute Package Utility** dialog box to select the configuration files to load at run time, and to specify the order in which they load.</span></span>  
  
### <a name="options"></a><span data-ttu-id="46d0d-179">选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-179">Options</span></span>  
 <span data-ttu-id="46d0d-180">**配置文件**</span><span class="sxs-lookup"><span data-stu-id="46d0d-180">**Configuration files**</span></span>  
 <span data-ttu-id="46d0d-181">列出包使用的配置。</span><span class="sxs-lookup"><span data-stu-id="46d0d-181">Lists the configurations that the package uses.</span></span> <span data-ttu-id="46d0d-182">每个配置文件都会向命令提示符中添加 **/CONFIGFILE filename** 选项。</span><span class="sxs-lookup"><span data-stu-id="46d0d-182">Each configuration file adds a **/CONFIGFILE filename** option to the command prompt.</span></span>  
  
 <span data-ttu-id="46d0d-183">**箭头键**</span><span class="sxs-lookup"><span data-stu-id="46d0d-183">**Arrow keys**</span></span>  
 <span data-ttu-id="46d0d-184">在列表中选择配置文件，然后使用右侧的箭头键更改加载顺序。</span><span class="sxs-lookup"><span data-stu-id="46d0d-184">Select a configuration file in the list, and use the arrow keys at right to change the loading order.</span></span> <span data-ttu-id="46d0d-185">将从列表顶部开始按顺序加载配置。</span><span class="sxs-lookup"><span data-stu-id="46d0d-185">Configurations load in order starting from the top of the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46d0d-186">如果多个配置修改了同一个属性，则使用最后加载的配置。</span><span class="sxs-lookup"><span data-stu-id="46d0d-186">If multiple configurations modify the same property, the configuration that loads last is used.</span></span>  
  
 <span data-ttu-id="46d0d-187">**添加**</span><span class="sxs-lookup"><span data-stu-id="46d0d-187">**Add**</span></span>  
 <span data-ttu-id="46d0d-188">单击此项可以使用“打开”  对话框添加配置。</span><span class="sxs-lookup"><span data-stu-id="46d0d-188">Click to add configurations using the **Open** dialog box.</span></span> <span data-ttu-id="46d0d-189">默认情况下，该对话框只列出具有 .dtsconfig 扩展名的文件。</span><span class="sxs-lookup"><span data-stu-id="46d0d-189">By default, the dialog box lists only files that have the .dtsconfig extension.</span></span>  
  
 <span data-ttu-id="46d0d-190">**删除**</span><span class="sxs-lookup"><span data-stu-id="46d0d-190">**Remove**</span></span>  
 <span data-ttu-id="46d0d-191">在列表中选择配置文件，再单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="46d0d-191">Select a configuration file in the list and then click **Remove**.</span></span>  
  
 <span data-ttu-id="46d0d-192">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-192">**Execute**</span></span>  
 <span data-ttu-id="46d0d-193">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-193">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-194">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-194">**Close**</span></span>  
 <span data-ttu-id="46d0d-195">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-195">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="command-files-page"></a><span data-ttu-id="46d0d-196">“命令文件”页</span><span class="sxs-lookup"><span data-stu-id="46d0d-196">Command Files Page</span></span>  
 <span data-ttu-id="46d0d-197">可以使用 **“执行包实用工具”** 对话框的 **“命令文件”** 页选择在运行时加载的命令文件。</span><span class="sxs-lookup"><span data-stu-id="46d0d-197">Use the **Command Files** page of the **Execute Package Utility** dialog box to select the command files to load at run time.</span></span>  
  
### <a name="options"></a><span data-ttu-id="46d0d-198">选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-198">Options</span></span>  
 <span data-ttu-id="46d0d-199">**命令文件**</span><span class="sxs-lookup"><span data-stu-id="46d0d-199">**Command files**</span></span>  
 <span data-ttu-id="46d0d-200">列出包使用的命令文件。</span><span class="sxs-lookup"><span data-stu-id="46d0d-200">Lists the command files that the package uses.</span></span> <span data-ttu-id="46d0d-201">一个包可以使用多个文件来设置命令行选项。</span><span class="sxs-lookup"><span data-stu-id="46d0d-201">A package can use multiple files to set command-line options.</span></span>  
  
 <span data-ttu-id="46d0d-202">**箭头键**</span><span class="sxs-lookup"><span data-stu-id="46d0d-202">**Arrow keys**</span></span>  
 <span data-ttu-id="46d0d-203">在列表中选择命令文件，然后使用右侧的箭头键更改加载顺序。</span><span class="sxs-lookup"><span data-stu-id="46d0d-203">Select a command file in the list, and use the arrow keys at right to change the loading order.</span></span> <span data-ttu-id="46d0d-204">将从列表顶部开始按顺序加载命令文件。</span><span class="sxs-lookup"><span data-stu-id="46d0d-204">Command files load in order, starting from the top of the list.</span></span>  
  
 <span data-ttu-id="46d0d-205">**添加**</span><span class="sxs-lookup"><span data-stu-id="46d0d-205">**Add**</span></span>  
 <span data-ttu-id="46d0d-206">单击此项可以使用“打开”  对话框添加命令文件。</span><span class="sxs-lookup"><span data-stu-id="46d0d-206">Click to add a command file, using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="46d0d-207">**删除**</span><span class="sxs-lookup"><span data-stu-id="46d0d-207">**Remove**</span></span>  
 <span data-ttu-id="46d0d-208">在文本框中选择命令文件，然后使用“删除”按钮删除该文件  。</span><span class="sxs-lookup"><span data-stu-id="46d0d-208">Select a command file in the text box, and then remove it using the **Remove** button.</span></span>  
  
 <span data-ttu-id="46d0d-209">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-209">**Execute**</span></span>  
 <span data-ttu-id="46d0d-210">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-210">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-211">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-211">**Close**</span></span>  
 <span data-ttu-id="46d0d-212">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-212">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="connection-managers-page"></a><span data-ttu-id="46d0d-213">“连接管理器”页</span><span class="sxs-lookup"><span data-stu-id="46d0d-213">Connection Managers Page</span></span>  
 <span data-ttu-id="46d0d-214">可以使用 **“执行包实用工具”** 对话框的 **“连接管理器”** 页，编辑包使用的连接管理器的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="46d0d-214">Use the **Connection Managers** page of the **Execute Package Utility** dialog box to edit the connection strings of the connection managers that the package uses.</span></span>  
  
### <a name="options"></a><span data-ttu-id="46d0d-215">选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-215">Options</span></span>  
 <span data-ttu-id="46d0d-216">**连接管理器**</span><span class="sxs-lookup"><span data-stu-id="46d0d-216">**Connection Manager**</span></span>  
 <span data-ttu-id="46d0d-217">选中其复选框后，“连接字符串”  列即会变为可编辑状态。</span><span class="sxs-lookup"><span data-stu-id="46d0d-217">Select its check box to make the **Connection String** column editable.</span></span>  
  
 <span data-ttu-id="46d0d-218">**说明**</span><span class="sxs-lookup"><span data-stu-id="46d0d-218">**Description**</span></span>  
 <span data-ttu-id="46d0d-219">查看每个连接管理器的说明。</span><span class="sxs-lookup"><span data-stu-id="46d0d-219">View a description for each connection manager.</span></span> <span data-ttu-id="46d0d-220">无法编辑说明。</span><span class="sxs-lookup"><span data-stu-id="46d0d-220">Descriptions cannot be edited.</span></span>  
  
 <span data-ttu-id="46d0d-221">**连接字符串**</span><span class="sxs-lookup"><span data-stu-id="46d0d-221">**Connection String**</span></span>  
 <span data-ttu-id="46d0d-222">编辑连接管理器的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="46d0d-222">Edit the connection string for a connection manager.</span></span> <span data-ttu-id="46d0d-223">只有选中 **“连接管理器”** 复选框时，此字段才是可编辑的。</span><span class="sxs-lookup"><span data-stu-id="46d0d-223">This field is editable only when the **Connection Manager** check box is selected.</span></span>  
  
 <span data-ttu-id="46d0d-224">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-224">**Execute**</span></span>  
 <span data-ttu-id="46d0d-225">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-225">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-226">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-226">**Close**</span></span>  
 <span data-ttu-id="46d0d-227">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-227">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="execution-options-page"></a><span data-ttu-id="46d0d-228">“执行选项”页</span><span class="sxs-lookup"><span data-stu-id="46d0d-228">Execution Options Page</span></span>  
 <span data-ttu-id="46d0d-229">可以使用“执行包实用工具”对话框的“执行选项”页指定包的运行时选项。</span><span class="sxs-lookup"><span data-stu-id="46d0d-229">Use the **Execution Options** page of the **Execute Package Utility** dialog box to specify run-time options for the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="46d0d-230">选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-230">Options</span></span>  
 <span data-ttu-id="46d0d-231">**发生验证警告时包失败**</span><span class="sxs-lookup"><span data-stu-id="46d0d-231">**Fail package on validation warnings**</span></span>  
 <span data-ttu-id="46d0d-232">指示如果发生验证警告包是否失败。</span><span class="sxs-lookup"><span data-stu-id="46d0d-232">Indicate whether the package fails if a validation warning occurs.</span></span>  
  
 <span data-ttu-id="46d0d-233">**验证但不执行包**</span><span class="sxs-lookup"><span data-stu-id="46d0d-233">**Validate package without executing**</span></span>  
 <span data-ttu-id="46d0d-234">指示是否只验证包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-234">Indicate whether the package is validated only.</span></span>  
  
 <span data-ttu-id="46d0d-235">**最大并发可执行文件数**</span><span class="sxs-lookup"><span data-stu-id="46d0d-235">**Maximum concurrent executables**</span></span>  
 <span data-ttu-id="46d0d-236">指示是否要指定包中可以同时运行的可执行文件的最大数量。</span><span class="sxs-lookup"><span data-stu-id="46d0d-236">Indicate whether you want to specify the maximum number of executables that can run in the package at the same time.</span></span> <span data-ttu-id="46d0d-237">选中此复选框后，可以使用数字调整框指定可执行文件的最大数量。</span><span class="sxs-lookup"><span data-stu-id="46d0d-237">After you select this check box, use the spin box to specify the maximum number of executables.</span></span>  
  
 <span data-ttu-id="46d0d-238">**启用包检查点**</span><span class="sxs-lookup"><span data-stu-id="46d0d-238">**Enable package checkpoints**</span></span>  
 <span data-ttu-id="46d0d-239">指示是否启用包检查点。</span><span class="sxs-lookup"><span data-stu-id="46d0d-239">Indicate whether to enable package checkpoints.</span></span>  
  
 <span data-ttu-id="46d0d-240">**检查点文件**</span><span class="sxs-lookup"><span data-stu-id="46d0d-240">**Checkpoint file**</span></span>  
 <span data-ttu-id="46d0d-241">如果启用包检查点，则列出包所使用的检查点文件。</span><span class="sxs-lookup"><span data-stu-id="46d0d-241">List the checkpoint file the package uses, if you enable package checkpoints.</span></span>  
  
 <span data-ttu-id="46d0d-242">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="46d0d-242">**Browse**</span></span>  
 <span data-ttu-id="46d0d-243">如果启用了包检查点，则单击浏览按钮 (…) 可以通过“打开”对话框查找检查点文件   。</span><span class="sxs-lookup"><span data-stu-id="46d0d-243">Click the browse button **(...)** to locate the checkpoint file using the **Open** dialog box, if you enable package checkpoints.</span></span> <span data-ttu-id="46d0d-244">如果已经指定了检查点文件，将用所选文件替换该文件。</span><span class="sxs-lookup"><span data-stu-id="46d0d-244">If a checkpoint file is already specified, it is replaced by the selected file.</span></span>  
  
 <span data-ttu-id="46d0d-245">**覆盖重新启动选项**</span><span class="sxs-lookup"><span data-stu-id="46d0d-245">**Override restart options**</span></span>  
 <span data-ttu-id="46d0d-246">指示是否覆盖重新启动选项（如果启用了包检查点）。</span><span class="sxs-lookup"><span data-stu-id="46d0d-246">Indicate whether to override restart options, if you enable package checkpoints.</span></span>  
  
 <span data-ttu-id="46d0d-247">**重新启动选项**</span><span class="sxs-lookup"><span data-stu-id="46d0d-247">**Restart option**</span></span>  
 <span data-ttu-id="46d0d-248">选择如何使用检查点（如果覆盖了重新启动选项）。</span><span class="sxs-lookup"><span data-stu-id="46d0d-248">Select how to use checkpoints, if you override restart options.</span></span>  
  
 <span data-ttu-id="46d0d-249">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-249">**Execute**</span></span>  
 <span data-ttu-id="46d0d-250">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-250">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-251">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-251">**Close**</span></span>  
 <span data-ttu-id="46d0d-252">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-252">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="reporting-page"></a><span data-ttu-id="46d0d-253">“报告”页</span><span class="sxs-lookup"><span data-stu-id="46d0d-253">Reporting Page</span></span>  
 <span data-ttu-id="46d0d-254">可以使用 **“执行包实用工具”** 对话框的 **“报告”** 页指定与包有关的事件和信息，以便在包运行时记录到控制台。</span><span class="sxs-lookup"><span data-stu-id="46d0d-254">Use the **Reporting** page of the **Execute Package Utility** dialog box to specify the events and information about the package to log to the console when the package runs.</span></span>  
  
### <a name="options"></a><span data-ttu-id="46d0d-255">选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-255">Options</span></span>  
 <span data-ttu-id="46d0d-256">**控制台事件**</span><span class="sxs-lookup"><span data-stu-id="46d0d-256">**Console events**</span></span>  
 <span data-ttu-id="46d0d-257">指示要报告的事件和消息类型。</span><span class="sxs-lookup"><span data-stu-id="46d0d-257">Indicate the events and types of messages to report.</span></span>  
  
 <span data-ttu-id="46d0d-258">无 </span><span class="sxs-lookup"><span data-stu-id="46d0d-258">**None**</span></span>  
 <span data-ttu-id="46d0d-259">选择此选项将不进行报告。</span><span class="sxs-lookup"><span data-stu-id="46d0d-259">Select for no reporting.</span></span>  
  
 <span data-ttu-id="46d0d-260">**错误**</span><span class="sxs-lookup"><span data-stu-id="46d0d-260">**Errors**</span></span>  
 <span data-ttu-id="46d0d-261">选择此选项将报告错误消息。</span><span class="sxs-lookup"><span data-stu-id="46d0d-261">Select to report error messages.</span></span>  
  
 <span data-ttu-id="46d0d-262">**警告**</span><span class="sxs-lookup"><span data-stu-id="46d0d-262">**Warnings**</span></span>  
 <span data-ttu-id="46d0d-263">选择此选项将报告警告消息。</span><span class="sxs-lookup"><span data-stu-id="46d0d-263">Select to report warning messages.</span></span>  
  
 <span data-ttu-id="46d0d-264">**自定义事件**</span><span class="sxs-lookup"><span data-stu-id="46d0d-264">**Custom Events**</span></span>  
 <span data-ttu-id="46d0d-265">选择此选项将报告自定义事件消息。</span><span class="sxs-lookup"><span data-stu-id="46d0d-265">Select to report custom event messages.</span></span>  
  
 <span data-ttu-id="46d0d-266">**管道事件**</span><span class="sxs-lookup"><span data-stu-id="46d0d-266">**Pipeline Events**</span></span>  
 <span data-ttu-id="46d0d-267">选择此选项将报告数据流事件消息。</span><span class="sxs-lookup"><span data-stu-id="46d0d-267">Select to report data flow events messages.</span></span>  
  
 <span data-ttu-id="46d0d-268">**信息**</span><span class="sxs-lookup"><span data-stu-id="46d0d-268">**Information**</span></span>  
 <span data-ttu-id="46d0d-269">选择此选项将报告信息性消息。</span><span class="sxs-lookup"><span data-stu-id="46d0d-269">Select to report information messages.</span></span>  
  
 <span data-ttu-id="46d0d-270">**详细**</span><span class="sxs-lookup"><span data-stu-id="46d0d-270">**Verbose**</span></span>  
 <span data-ttu-id="46d0d-271">选择此选项将使用详细报告。</span><span class="sxs-lookup"><span data-stu-id="46d0d-271">Select to use verbose reporting.</span></span>  
  
 <span data-ttu-id="46d0d-272">**控制台日志记录**</span><span class="sxs-lookup"><span data-stu-id="46d0d-272">**Console logging**</span></span>  
 <span data-ttu-id="46d0d-273">指定在发生所选事件时要写入日志的信息。</span><span class="sxs-lookup"><span data-stu-id="46d0d-273">Specify the information that you want written to the log when the selected event occurs.</span></span>  
  
 <span data-ttu-id="46d0d-274">**名称**</span><span class="sxs-lookup"><span data-stu-id="46d0d-274">**Name**</span></span>  
 <span data-ttu-id="46d0d-275">选择此选项将报告创建包的人员的姓名。</span><span class="sxs-lookup"><span data-stu-id="46d0d-275">Select to report the name of the person who created the package.</span></span>  
  
 <span data-ttu-id="46d0d-276">**计算机**</span><span class="sxs-lookup"><span data-stu-id="46d0d-276">**Computer**</span></span>  
 <span data-ttu-id="46d0d-277">选择此选项将报告运行包的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="46d0d-277">Select to report the name of the computer the package is running on.</span></span>  
  
 <span data-ttu-id="46d0d-278">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="46d0d-278">**Operator**</span></span>  
 <span data-ttu-id="46d0d-279">选择此选项将报告启动包的人员的姓名。</span><span class="sxs-lookup"><span data-stu-id="46d0d-279">Select to report the name of the person who started the package.</span></span>  
  
 <span data-ttu-id="46d0d-280">**源名称**</span><span class="sxs-lookup"><span data-stu-id="46d0d-280">**Source name**</span></span>  
 <span data-ttu-id="46d0d-281">选择此选项将报告包名称。</span><span class="sxs-lookup"><span data-stu-id="46d0d-281">Select to report the package name.</span></span>  
  
 <span data-ttu-id="46d0d-282">**源 GUID**</span><span class="sxs-lookup"><span data-stu-id="46d0d-282">**Source GUID**</span></span>  
 <span data-ttu-id="46d0d-283">选择此选项将报告包 GUID。</span><span class="sxs-lookup"><span data-stu-id="46d0d-283">Select to report the package GUID.</span></span>  
  
 <span data-ttu-id="46d0d-284">**执行 GUID**</span><span class="sxs-lookup"><span data-stu-id="46d0d-284">**Execution GUID**</span></span>  
 <span data-ttu-id="46d0d-285">选择此选项将报告包执行实例的 GUID。</span><span class="sxs-lookup"><span data-stu-id="46d0d-285">Select to report the GUID of the package execution instance.</span></span>  
  
 <span data-ttu-id="46d0d-286">**消息**</span><span class="sxs-lookup"><span data-stu-id="46d0d-286">**Message**</span></span>  
 <span data-ttu-id="46d0d-287">选择此选项将报告消息。</span><span class="sxs-lookup"><span data-stu-id="46d0d-287">Select to report messages.</span></span>  
  
 <span data-ttu-id="46d0d-288">**开始时间和结束时间**</span><span class="sxs-lookup"><span data-stu-id="46d0d-288">**Start time and end time**</span></span>  
 <span data-ttu-id="46d0d-289">选择此选项将报告包开始和完成的时间。</span><span class="sxs-lookup"><span data-stu-id="46d0d-289">Select to report when the package began and finished.</span></span>  
  
 <span data-ttu-id="46d0d-290">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-290">**Execute**</span></span>  
 <span data-ttu-id="46d0d-291">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-291">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-292">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-292">**Close**</span></span>  
 <span data-ttu-id="46d0d-293">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-293">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="logging-page"></a><span data-ttu-id="46d0d-294">“日志记录”页</span><span class="sxs-lookup"><span data-stu-id="46d0d-294">Logging Page</span></span>  
 <span data-ttu-id="46d0d-295">可以使用 **“执行包实用工具”** 对话框的 **“日志记录”** 页，将包设置为可在运行时使用日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="46d0d-295">Use the **Logging** page of the **Execute Package Utility** dialog box to make log providers available to the package at run time.</span></span> <span data-ttu-id="46d0d-296">提供包日志提供程序类型和连接到日志的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="46d0d-296">Provide the package log provider type and the connection string for connecting to the log.</span></span> <span data-ttu-id="46d0d-297">对于每个日志提供程序项，在命令提示符下都会添加一个 **/LOGGER**_classid_ 选项。</span><span class="sxs-lookup"><span data-stu-id="46d0d-297">Each log provider entry adds a **/LOGGER**_classid_ option to the command prompt.</span></span>  
  
### <a name="options"></a><span data-ttu-id="46d0d-298">选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-298">Options</span></span>  
 <span data-ttu-id="46d0d-299">**日志提供程序**</span><span class="sxs-lookup"><span data-stu-id="46d0d-299">**Log Provider**</span></span>  
 <span data-ttu-id="46d0d-300">从该列表中选择日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="46d0d-300">Select a log provider from the list.</span></span>  
  
 <span data-ttu-id="46d0d-301">**配置字符串**</span><span class="sxs-lookup"><span data-stu-id="46d0d-301">**Configuration String**</span></span>  
 <span data-ttu-id="46d0d-302">从指向日志位置的包中选择连接管理器的名称，或键入连接到日志提供程序的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="46d0d-302">Select the name of the connection manager from the package that points to the log location, or type the connection string for connecting to the log provider.</span></span>  
  
 <span data-ttu-id="46d0d-303">**删除**</span><span class="sxs-lookup"><span data-stu-id="46d0d-303">**Remove**</span></span>  
 <span data-ttu-id="46d0d-304">选择一个日志提供程序，再单击此项将删除该日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="46d0d-304">Select a log provider and click to remove it.</span></span>  
  
 <span data-ttu-id="46d0d-305">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-305">**Execute**</span></span>  
 <span data-ttu-id="46d0d-306">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-306">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-307">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-307">**Close**</span></span>  
 <span data-ttu-id="46d0d-308">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-308">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="set-values-page"></a><span data-ttu-id="46d0d-309">“设置值”页</span><span class="sxs-lookup"><span data-stu-id="46d0d-309">Set Values Page</span></span>  
 <span data-ttu-id="46d0d-310">可以使用 **“执行包实用工具”** 对话框的 **“设置值”** 页，通过键入属性路径和属性值来设置包、可执行文件、连接、变量和日志提供程序的属性值。</span><span class="sxs-lookup"><span data-stu-id="46d0d-310">Use the **Set Values** page of the **Execute Package Utility** dialog box to set the property values of packages, executables, connections, variables, and log providers by typing the paths of properties and the property values.</span></span> <span data-ttu-id="46d0d-311">对于每个路径项，在命令提示符下都会添加一个 **/SET**_propertypath;value_ 选项。</span><span class="sxs-lookup"><span data-stu-id="46d0d-311">Each path entry adds a **/SET**_propertypath;value_ option to the command prompt.</span></span>  
  
### <a name="options"></a><span data-ttu-id="46d0d-312">选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-312">Options</span></span>  
 <span data-ttu-id="46d0d-313">**属性路径**</span><span class="sxs-lookup"><span data-stu-id="46d0d-313">**Property Path**</span></span>  
 <span data-ttu-id="46d0d-314">键入属性的路径。</span><span class="sxs-lookup"><span data-stu-id="46d0d-314">Type the path of the property.</span></span> <span data-ttu-id="46d0d-315">在路径语法中，反斜杠 (\\) 用于指示其后面为容器项，句点 (.) 用于指示其后面为属性项，而括号用于指示集合成员。</span><span class="sxs-lookup"><span data-stu-id="46d0d-315">The path syntax uses a backslash (\\) to indicate that the following item is a container, the period (.) to indicate the following item is a property, and brackets to indicate a collection member.</span></span> <span data-ttu-id="46d0d-316">成员可以通过其索引或其名称进行标识。</span><span class="sxs-lookup"><span data-stu-id="46d0d-316">The member can be identified by its index or its name.</span></span> <span data-ttu-id="46d0d-317">例如，包变量的属性路径可以是 \Package.Variables[MyVariable].Value。</span><span class="sxs-lookup"><span data-stu-id="46d0d-317">For example, the property path of a package variable is \Package.Variables[MyVariable].Value.</span></span>  
  
 <span data-ttu-id="46d0d-318">**值**</span><span class="sxs-lookup"><span data-stu-id="46d0d-318">**Value**</span></span>  
 <span data-ttu-id="46d0d-319">键入属性的值。</span><span class="sxs-lookup"><span data-stu-id="46d0d-319">Type the value of the property.</span></span>  
  
 <span data-ttu-id="46d0d-320">**删除**</span><span class="sxs-lookup"><span data-stu-id="46d0d-320">**Remove**</span></span>  
 <span data-ttu-id="46d0d-321">在选择属性路径后单击此项将删除相应的属性路径。</span><span class="sxs-lookup"><span data-stu-id="46d0d-321">Select a property path and click to remove it.</span></span>  
  
 <span data-ttu-id="46d0d-322">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-322">**Execute**</span></span>  
 <span data-ttu-id="46d0d-323">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-323">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-324">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-324">**Close**</span></span>  
 <span data-ttu-id="46d0d-325">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-325">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="verification-page"></a><span data-ttu-id="46d0d-326">“验证”页</span><span class="sxs-lookup"><span data-stu-id="46d0d-326">Verification Page</span></span>  
 <span data-ttu-id="46d0d-327">可以使用 **“执行包”** 对话框的 **“验证”** 页设置对包进行验证的条件。</span><span class="sxs-lookup"><span data-stu-id="46d0d-327">Use the **Verification** page of the **Execute Package** dialog box to set criteria for verifying the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="46d0d-328">选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-328">Options</span></span>  
 <span data-ttu-id="46d0d-329">**仅执行已签名的包**</span><span class="sxs-lookup"><span data-stu-id="46d0d-329">**Execute only signed packages**</span></span>  
 <span data-ttu-id="46d0d-330">选择此项将仅执行已签名的包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-330">Select to execute only packages that have been signed.</span></span>  
  
 <span data-ttu-id="46d0d-331">**验证包内部版本**</span><span class="sxs-lookup"><span data-stu-id="46d0d-331">**Verify package build**</span></span>  
 <span data-ttu-id="46d0d-332">选择此项可以验证包内部版本。</span><span class="sxs-lookup"><span data-stu-id="46d0d-332">Select to verify the package build.</span></span>  
  
 <span data-ttu-id="46d0d-333">构建</span><span class="sxs-lookup"><span data-stu-id="46d0d-333">Build</span></span>  
 <span data-ttu-id="46d0d-334">指定与内部版本相关联的内部版本序号。</span><span class="sxs-lookup"><span data-stu-id="46d0d-334">Specify the sequential Build number associated with the build.</span></span>  
  
 <span data-ttu-id="46d0d-335">**验证包 ID**</span><span class="sxs-lookup"><span data-stu-id="46d0d-335">**Verify package ID**</span></span>  
 <span data-ttu-id="46d0d-336">选择此项可以验证包 ID。</span><span class="sxs-lookup"><span data-stu-id="46d0d-336">Select to verify the package ID.</span></span>  
  
 <span data-ttu-id="46d0d-337">包 ID</span><span class="sxs-lookup"><span data-stu-id="46d0d-337">Package ID</span></span>  
 <span data-ttu-id="46d0d-338">指定包标识号。</span><span class="sxs-lookup"><span data-stu-id="46d0d-338">Specify the package identification number.</span></span>  
  
 <span data-ttu-id="46d0d-339">**验证版本 ID**</span><span class="sxs-lookup"><span data-stu-id="46d0d-339">**Verify version ID**</span></span>  
 <span data-ttu-id="46d0d-340">选择此项可以验证版本 ID。</span><span class="sxs-lookup"><span data-stu-id="46d0d-340">Select to verify the version ID.</span></span>  
  
 <span data-ttu-id="46d0d-341">版本 ID</span><span class="sxs-lookup"><span data-stu-id="46d0d-341">Version ID</span></span>  
 <span data-ttu-id="46d0d-342">指定版本标识号。</span><span class="sxs-lookup"><span data-stu-id="46d0d-342">Specify the version identification number.</span></span>  
  
 <span data-ttu-id="46d0d-343">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-343">**Execute**</span></span>  
 <span data-ttu-id="46d0d-344">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-344">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-345">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-345">**Close**</span></span>  
 <span data-ttu-id="46d0d-346">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-346">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="command-line-page"></a><span data-ttu-id="46d0d-347">“命令行”页</span><span class="sxs-lookup"><span data-stu-id="46d0d-347">Command Line Page</span></span>  
 <span data-ttu-id="46d0d-348">可以使用 **“执行包实用工具”** 对话框的 **“命令行”** 节点，编辑由不同对话框创建的选项生成的命令行。</span><span class="sxs-lookup"><span data-stu-id="46d0d-348">Use the **Command Line** node of the **Execute Package Utility** dialog box to edit the command line that has been generated by the options created by the various dialogs.</span></span>  
  
### <a name="options"></a><span data-ttu-id="46d0d-349">选项</span><span class="sxs-lookup"><span data-stu-id="46d0d-349">Options</span></span>  
 <span data-ttu-id="46d0d-350">**还原原始选项**</span><span class="sxs-lookup"><span data-stu-id="46d0d-350">**Restore the original options**</span></span>  
 <span data-ttu-id="46d0d-351">单击此项可将命令行还原为其原始状态。</span><span class="sxs-lookup"><span data-stu-id="46d0d-351">Click to restore the command line to its original state.</span></span> <span data-ttu-id="46d0d-352">如果你使用“手动编辑命令行”  选项进行了修改，然后要还原原始命令行选项，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="46d0d-352">Use this option if you have made modifications using the **Edit the command line manually** option and want to restore the original command-line options.</span></span>  
  
 <span data-ttu-id="46d0d-353">**手动编辑命令行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-353">**Edit the command line manually**</span></span>  
 <span data-ttu-id="46d0d-354">单击此项可在“命令行”  文本框中编辑命令行。</span><span class="sxs-lookup"><span data-stu-id="46d0d-354">Click to edit the command line in the **Command line** text box.</span></span>  
  
 <span data-ttu-id="46d0d-355">**命令行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-355">**Command line**</span></span>  
 <span data-ttu-id="46d0d-356">显示当前的命令行。</span><span class="sxs-lookup"><span data-stu-id="46d0d-356">Displays the current command line.</span></span> <span data-ttu-id="46d0d-357">如果您选择了手动编辑命令行的选项，则可编辑该命令行。</span><span class="sxs-lookup"><span data-stu-id="46d0d-357">Editable if you selected the option to edit the command line manually.</span></span>  
  
 <span data-ttu-id="46d0d-358">**执行**</span><span class="sxs-lookup"><span data-stu-id="46d0d-358">**Execute**</span></span>  
 <span data-ttu-id="46d0d-359">单击此项可运行包。</span><span class="sxs-lookup"><span data-stu-id="46d0d-359">Click to run the package.</span></span>  
  
 <span data-ttu-id="46d0d-360">**关闭**</span><span class="sxs-lookup"><span data-stu-id="46d0d-360">**Close**</span></span>  
 <span data-ttu-id="46d0d-361">单击此项可关闭“执行包实用工具”  对话框。</span><span class="sxs-lookup"><span data-stu-id="46d0d-361">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d0d-362">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46d0d-362">See Also</span></span>  
 [<span data-ttu-id="46d0d-363">dtexec 实用工具</span><span class="sxs-lookup"><span data-stu-id="46d0d-363">dtexec Utility</span></span>](dtexec-utility.md)  
  
  
