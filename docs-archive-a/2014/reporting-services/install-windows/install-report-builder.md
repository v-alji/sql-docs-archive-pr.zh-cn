---
title: 安装报表生成器 (报表生成器) 的独立版本 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ba8c132125f56ad833a71a1c82221e2bf28d13e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588329"
---
# <a name="install-the-stand-alone-version-of-report-builder-report-builder"></a><span data-ttu-id="d96ae-102">安装报表生成器的独立版本（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="d96ae-102">Install the Stand-Alone Version of Report Builder (Report Builder)</span></span>
  <span data-ttu-id="d96ae-103">你可以从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Microsoft 下载中心](https://www.microsoft.com/download/details.aspx?id=53613)上的功能包中安装报表生成器，也可以从一个位置（例如，已下载 ReportBuilder3_x86.msi 的 Windows Installer 包报表生成器的公用文件夹）安装。</span><span class="sxs-lookup"><span data-stu-id="d96ae-103">You can install Report Builder from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature pack on the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53613) or a location such as public folder to which the ReportBuilder3_x86.msi, the Windows Installer Package for Report Builder, has been downloaded.</span></span>  
  
 <span data-ttu-id="d96ae-104">还可以执行报表生成器的命令行安装，并提供参数以自定义安装。</span><span class="sxs-lookup"><span data-stu-id="d96ae-104">You can also perform a command line installation of Report Builder and provide arguments to customize the installation.</span></span> <span data-ttu-id="d96ae-105">除了标准的 MSI 内部参数以外，还可以使用报表生成器提供的自定义参数：RBINSTALLDIR 和 REPORTSERVERURL。</span><span class="sxs-lookup"><span data-stu-id="d96ae-105">In addition to the standard MSI intrinsic parameters, you can use the custom parameters that Report Builder provides: RBINSTALLDIR and REPORTSERVERURL.</span></span> <span data-ttu-id="d96ae-106">RBINSTALLDIR 指定报表生成器的根安装文件夹。</span><span class="sxs-lookup"><span data-stu-id="d96ae-106">RBINSTALLDIR specifies the root installation folder for Report Builder.</span></span> <span data-ttu-id="d96ae-107">REPORTSERVERURL 指定报表生成器用于在服务器上保存报表的默认报表服务器。</span><span class="sxs-lookup"><span data-stu-id="d96ae-107">REPORTSERVERURL specifies the default report server that Report Builder uses to save reports on the server.</span></span>  
  
 <span data-ttu-id="d96ae-108">如果要进行根本没有用户界面交互的完全静默安装，请指定 **/quiet** 选项。</span><span class="sxs-lookup"><span data-stu-id="d96ae-108">If you want a completely silent installation, with no user interface interaction at all, specify the **/quiet** option.</span></span> <span data-ttu-id="d96ae-109">根据设计，quiet 选项标志会隐藏安装错误。</span><span class="sxs-lookup"><span data-stu-id="d96ae-109">By design, the quiet option flag suppresses installation errors.</span></span> <span data-ttu-id="d96ae-110">因此，建议在使用 quiet 选项时包括 **/l** 选项，该选项指定进行日志记录。</span><span class="sxs-lookup"><span data-stu-id="d96ae-110">It is therefore recommended that you include the **/l** option, which specifies logging, when you use the quiet option.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d96ae-111">Windows Vista 和 Windows 7 安全功能需要提升权限以运行命令行操作，并将提示您提供运行命令行的权限。</span><span class="sxs-lookup"><span data-stu-id="d96ae-111">Windows Vista and Windows 7 security features require elevated permissions to run command line operations and will prompt for permission to run the command line.</span></span> <span data-ttu-id="d96ae-112">安装不是静默的。</span><span class="sxs-lookup"><span data-stu-id="d96ae-112">The installation is not silent.</span></span> <span data-ttu-id="d96ae-113">若要进行静默安装，您需要以管理员身份运行命令行。</span><span class="sxs-lookup"><span data-stu-id="d96ae-113">To make the installation silent, you need to run the command line as an administrator.</span></span>  
  
### <a name="to-install-report-builder-from-the-download-site"></a><span data-ttu-id="d96ae-114">从下载站点安装报表生成器</span><span class="sxs-lookup"><span data-stu-id="d96ae-114">To install Report Builder from the download site</span></span>  
  
1.  <span data-ttu-id="d96ae-115">请参阅[Microsoft SQL Server 2012 报表生成器](https://go.microsoft.com/fwlink/?LinkID=219138)并找到网页的报表生成器部分。</span><span class="sxs-lookup"><span data-stu-id="d96ae-115">Go to [Microsoft SQL Server 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkID=219138) and locate the Report Builder section of the Web page.</span></span>  
  
2.  <span data-ttu-id="d96ae-116">单击 " **X86 包**"。</span><span class="sxs-lookup"><span data-stu-id="d96ae-116">Click **X86 Package**.</span></span>  
  
3.  <span data-ttu-id="d96ae-117">在 "**文件下载**" 对话框中，单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="d96ae-117">In the **File Download** dialog box, click **Run**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d96ae-118">请仅下载来自可信来源的文件。</span><span class="sxs-lookup"><span data-stu-id="d96ae-118">Download only files from trusted sources.</span></span>  
  
4.  <span data-ttu-id="d96ae-119">在 Internet Explorer 对话框中，单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="d96ae-119">In the Internet Explorer dialog box, click **Run**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d96ae-120">请仅运行来自可信来源的文件。</span><span class="sxs-lookup"><span data-stu-id="d96ae-120">Run only files from trusted sources.</span></span>  
  
5.  <span data-ttu-id="d96ae-121">Microsoft SQL Server 报表生成器向导将会启动。</span><span class="sxs-lookup"><span data-stu-id="d96ae-121">The Microsoft SQL Server Report Builder Wizard is launched.</span></span>  
  
6.  <span data-ttu-id="d96ae-122">在 "**欢迎使用安装向导**" 页上，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="d96ae-122">On the **Welcome to the Installation Wizard** page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="d96ae-123">在 "**许可协议**" 页上，阅读协议，然后选择 "**我接受许可协议中的条款**" 选项。</span><span class="sxs-lookup"><span data-stu-id="d96ae-123">On the **License Agreement** page, read the agreement and then select the **I accept the terms in the license agreement** option.</span></span> <span data-ttu-id="d96ae-124">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96ae-124">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="d96ae-125">提供个人姓名和公司名称。</span><span class="sxs-lookup"><span data-stu-id="d96ae-125">Provide your personal name and company name.</span></span> <span data-ttu-id="d96ae-126">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96ae-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="d96ae-127">在 "**功能选择**" 页上，可以选择单击 "**浏览**" 或 "**磁盘成本**"。</span><span class="sxs-lookup"><span data-stu-id="d96ae-127">On the **Feature Selection** page, optionally click **Browse** or **Disk Cost**.</span></span> <span data-ttu-id="d96ae-128">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96ae-128">Click **Next**.</span></span>  
  
    -   <span data-ttu-id="d96ae-129">单击 "**浏览**" 查看报表生成器的默认位置并进行更新。</span><span class="sxs-lookup"><span data-stu-id="d96ae-129">Click **Browse** to see the default location of Report Builder and update it.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d96ae-130">报表生成器的默认安装文件夹是 \<drive> Program Files\Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="d96ae-130">The default installation folder for Report Builder is \<drive>Program Files\Microsoft SQL Server.</span></span>  
  
    -   <span data-ttu-id="d96ae-131">单击 "**磁盘开销**" 以了解报表生成器消耗的磁盘空间量。</span><span class="sxs-lookup"><span data-stu-id="d96ae-131">Click **Disk Cost** to learn how much disk space Report Builder consumes.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d96ae-132">如果某个卷没有足够数量的可用磁盘空间，则该卷会突出显示。</span><span class="sxs-lookup"><span data-stu-id="d96ae-132">If a volume does not have sufficient amount of free disk space, the volume is highlighted.</span></span>  
  
10. <span data-ttu-id="d96ae-133">在 **“默认的目标服务器”** 页上，如果目标报表服务器的 URL 与默认 URL 不同，则可选择提供前者。</span><span class="sxs-lookup"><span data-stu-id="d96ae-133">On the **Default Target Server** page, optionally provide the URL to the target report server if it is different from the default.</span></span> <span data-ttu-id="d96ae-134">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96ae-134">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d96ae-135">如果计划在报表生成器连接到某个报表服务器时使用它，则此时提供该报表服务器的 URL 将会非常方便。</span><span class="sxs-lookup"><span data-stu-id="d96ae-135">If you plan to work with Report Builder when it is connected to a report server, it is convenient to provide the URL to the server at this time.</span></span> <span data-ttu-id="d96ae-136">但是，在报表生成器中工作时，也可以从 "**选项**" 对话框执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d96ae-136">However, you can also do this from the **Options** dialog box when you are working in Report Builder.</span></span>  
  
11. <span data-ttu-id="d96ae-137">单击 "**安装**" 以完成报表生成器安装。</span><span class="sxs-lookup"><span data-stu-id="d96ae-137">Click **Install** to complete the installation of Report Builder.</span></span>  
  
### <a name="to-install-report-builder-from-a-share"></a><span data-ttu-id="d96ae-138">从共享位置安装报表生成器</span><span class="sxs-lookup"><span data-stu-id="d96ae-138">To install Report Builder from a share</span></span>  
  
1.  <span data-ttu-id="d96ae-139">请与管理员联系，以获得在本地计算机上安装报表生成器所要运行的 ReportBuilder3_x86.msi.msi 的位置。</span><span class="sxs-lookup"><span data-stu-id="d96ae-139">Contact your administrator for the location of ReportBuilder3_x86.msi.msi that you run to install Report Builder on your local computer.</span></span>  
  
2.  <span data-ttu-id="d96ae-140">浏览找到 ReportBuilder3_x86.msi.msi（报表生成器的 Windows Installer 包 (MSI)），然后单击它。</span><span class="sxs-lookup"><span data-stu-id="d96ae-140">Browse to locate the ReportBuilder3_x86.msi.msi, the Windows Installer Package (MSI) for Report Builder, and click it.</span></span>  
  
     <span data-ttu-id="d96ae-141">Microsoft SQL Server 报表生成器向导将会启动。</span><span class="sxs-lookup"><span data-stu-id="d96ae-141">The Microsoft SQL Server Report Builder Wizard is launched.</span></span>  
  
3.  <span data-ttu-id="d96ae-142">在 "**欢迎使用安装向导**" 页上，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="d96ae-142">On the **Welcome to the Installation Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="d96ae-143">在 "**许可协议**" 页上，阅读协议，然后选择 "**我接受许可协议中的条款**" 选项。</span><span class="sxs-lookup"><span data-stu-id="d96ae-143">On the **License Agreement** page, read the agreement and then select the **I accept the terms in the license agreement** option.</span></span> <span data-ttu-id="d96ae-144">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96ae-144">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="d96ae-145">提供个人姓名和公司名称。</span><span class="sxs-lookup"><span data-stu-id="d96ae-145">Provide your personal name and company name.</span></span> <span data-ttu-id="d96ae-146">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96ae-146">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="d96ae-147">在 "**功能选择**" 页上，可以选择单击 "**浏览**" 或 "**磁盘成本**"。</span><span class="sxs-lookup"><span data-stu-id="d96ae-147">On the **Feature Selection** page, optionally click **Browse** or **Disk Cost**.</span></span> <span data-ttu-id="d96ae-148">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96ae-148">Click **Next**.</span></span>  
  
    -   <span data-ttu-id="d96ae-149">单击 "**浏览**" 查看报表生成器的默认位置并进行更新。</span><span class="sxs-lookup"><span data-stu-id="d96ae-149">Click **Browse** to see the default location of Report Builder and update it.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d96ae-150">报表生成器的默认安装文件夹是 \<drive> Program Files\Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="d96ae-150">The default installation folder for Report Builder is \<drive>Program Files\Microsoft SQL Server.</span></span>  
  
    -   <span data-ttu-id="d96ae-151">单击 "**磁盘开销**" 以了解报表生成器消耗的磁盘空间量。</span><span class="sxs-lookup"><span data-stu-id="d96ae-151">Click **Disk Cost** to learn how much disk space Report Builder consumes.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d96ae-152">如果某个卷没有足够数量的可用磁盘空间，则该卷会突出显示。</span><span class="sxs-lookup"><span data-stu-id="d96ae-152">If a volume does not have sufficient amount of free disk space, the volume is highlighted.</span></span>  
  
7.  <span data-ttu-id="d96ae-153">在 **“默认的目标服务器”** 页上，如果目标报表服务器的 URL 与默认 URL 不同，则可选择提供前者。</span><span class="sxs-lookup"><span data-stu-id="d96ae-153">On the **Default Target Server** page, optionally provide the URL to the target report server if it is different from the default.</span></span> <span data-ttu-id="d96ae-154">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96ae-154">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d96ae-155">如果计划在报表生成器连接到某个报表服务器时使用它，则此时提供该报表服务器的 URL 将会非常方便。</span><span class="sxs-lookup"><span data-stu-id="d96ae-155">If you plan to work with Report Builder when it is connected to a report server, it is convenient to provide the URL to the server at this time.</span></span> <span data-ttu-id="d96ae-156">但是，在报表生成器中工作时，也可以从 "**选项**" 对话框执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d96ae-156">However, you can also do this from the **Options** dialog box when you are working in Report Builder.</span></span>  
  
8.  <span data-ttu-id="d96ae-157">单击 "**安装**" 以完成报表生成器安装。</span><span class="sxs-lookup"><span data-stu-id="d96ae-157">Click **Install** to complete the installation of Report Builder.</span></span>  
  
### <a name="to-install-report-builder-from-the-command-line"></a><span data-ttu-id="d96ae-158">从命令行安装报表生成器</span><span class="sxs-lookup"><span data-stu-id="d96ae-158">To install Report Builder from the command line</span></span>  
  
1.  <span data-ttu-id="d96ae-159">请参阅[Microsoft SQL Server 2012 报表生成器](https://go.microsoft.com/fwlink/?LinkID=219138)并找到报表生成器部分。</span><span class="sxs-lookup"><span data-stu-id="d96ae-159">Go to [Microsoft SQL Server 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkID=219138) and locate the Report Builder section.</span></span>  
  
2.  <span data-ttu-id="d96ae-160">单击 " **X86 包**"。</span><span class="sxs-lookup"><span data-stu-id="d96ae-160">Click **X86 Package**.</span></span>  
  
3.  <span data-ttu-id="d96ae-161">单击“保存”。</span><span class="sxs-lookup"><span data-stu-id="d96ae-161">Click Save.</span></span>  
  
4.  <span data-ttu-id="d96ae-162">（可选）浏览到要保存到的位置，验证 "**另存为**" 选项**Windows Installer 包**"，然后单击"**保存**"。</span><span class="sxs-lookup"><span data-stu-id="d96ae-162">Optionally, browse to the location to save to, verify the **Save as** option is **Windows Installer Package**, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="d96ae-163">在 **“开始”** 菜单上，单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="d96ae-163">On the **Start** menu, click **Run**.</span></span>  
  
6.  <span data-ttu-id="d96ae-164">在“打开”文本框中，键入 `cmd.`</span><span class="sxs-lookup"><span data-stu-id="d96ae-164">In the Open text box, type `cmd.`</span></span>  
  
7.  <span data-ttu-id="d96ae-165">在命令提示符窗口中，导航到要保存 ReportBuilder3_x86.msi 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d96ae-165">In the Command Prompt window, navigate to the folder where you saved ReportBuilder3_x86.msi.</span></span>  
  
8.  <span data-ttu-id="d96ae-166">使用以下格式键入命令：</span><span class="sxs-lookup"><span data-stu-id="d96ae-166">Type a command with the following format:</span></span>  
  
     `msiexec/i ReportBuilder3_.msi /option [value] [/option [value]]`  
  
     <span data-ttu-id="d96ae-167">安装报表生成器的两个特定选项为：RBINSTALLDIR 和 REPORTSERVERURL。</span><span class="sxs-lookup"><span data-stu-id="d96ae-167">The two options specific to installing Report Builder are: RBINSTALLDIR and REPORTSERVERURL.</span></span> <span data-ttu-id="d96ae-168">不需要在命令行中包含这些参数。</span><span class="sxs-lookup"><span data-stu-id="d96ae-168">It not required that you include these arguments in the command line.</span></span> <span data-ttu-id="d96ae-169">以下为基准命令：</span><span class="sxs-lookup"><span data-stu-id="d96ae-169">The following is the baseline command:</span></span>  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
9. <span data-ttu-id="d96ae-170">若要运行命令，请按 Enter。</span><span class="sxs-lookup"><span data-stu-id="d96ae-170">To run the command, press Enter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96ae-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d96ae-171">See Also</span></span>  
 <span data-ttu-id="d96ae-172">[安装、卸载和报表生成器支持](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="d96ae-172">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="d96ae-173">卸载报表生成器 &#40;报表生成器的独立版本&#41;</span><span class="sxs-lookup"><span data-stu-id="d96ae-173">Uninstall the Stand-Alone Version of Report Builder &#40;Report Builder&#41;</span></span>](install-report-builder.md)  
  
  
