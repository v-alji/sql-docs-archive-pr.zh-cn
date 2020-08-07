---
title: 卸载报表生成器 (报表生成器) 的独立版本 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cda13248d1aa14ee3d57a951872d3ad8ded17da9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589441"
---
# <a name="uninstall-the-stand-alone-version-of-report-builder-report-builder"></a><span data-ttu-id="945f0-102">卸载报表生成器的独立版本（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="945f0-102">Uninstall the Stand-Alone Version of Report Builder (Report Builder)</span></span>
  <span data-ttu-id="945f0-103">可以从控制面板或命令行卸载报表生成器的独立版本。</span><span class="sxs-lookup"><span data-stu-id="945f0-103">You can uninstall the stand-alone version of Report Builder from the control panel or the command line.</span></span> <span data-ttu-id="945f0-104">在未卸载 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] 的情况下，无法卸载报表生成器的 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="945f0-104">You cannot uninstall the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version of Report Builder without uninstalling [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="945f0-105">除了使用 /x 选项而不是 /i 选项外，从命令行卸载报表生成器所使用的语法与安装时使用的语法完全相同。</span><span class="sxs-lookup"><span data-stu-id="945f0-105">Uninstalling Report Builder from the command line uses syntax that is identical to the syntax you use to install Report Builder, except you use the /x option instead of the /i option.</span></span> <span data-ttu-id="945f0-106">用于卸载的命令行也可包括 /quiet 选项和其他标准选项。</span><span class="sxs-lookup"><span data-stu-id="945f0-106">Command lines for uninstalling can also include the /quiet option and other standard options.</span></span> <span data-ttu-id="945f0-107">如果已删除报表生成器 Windows Installer 包 (ReportBuilder3_x86.msi)，则无法轻松地使用命令行卸载报表生成器。</span><span class="sxs-lookup"><span data-stu-id="945f0-107">If the Report Builder Windows Installer Package (ReportBuilder3_x86.msi) has been removed, you cannot use the command line easily to uninstall Report Builder.</span></span> <span data-ttu-id="945f0-108">若要了解有关如何能够通过使用报表生成器的 GUID 将其删除的详细信息，请参阅 msdn 库中 msiexec 程序的文档。</span><span class="sxs-lookup"><span data-stu-id="945f0-108">To learn more about how you might be able to remove Report Builder by using its GUID, see the documentation for the msiexec program in the msdn library.</span></span>  
  
 <span data-ttu-id="945f0-109">如果报表生成器使用的文件夹中包含自定义文件，则在删除报表生成器时会保留这些文件夹和文件。</span><span class="sxs-lookup"><span data-stu-id="945f0-109">If folders used by Report Builder include custom files, the folders and the files are preserved when Report Builder is removed.</span></span> <span data-ttu-id="945f0-110">仅删除报表生成器文件。</span><span class="sxs-lookup"><span data-stu-id="945f0-110">Only the Report Builder files are removed.</span></span>  
  
### <a name="to-uninstall-report-builder-from-the-control-panel"></a><span data-ttu-id="945f0-111">从控制面板卸载报表生成器</span><span class="sxs-lookup"><span data-stu-id="945f0-111">To uninstall Report Builder from the control panel</span></span>  
  
1.  <span data-ttu-id="945f0-112">在 **“开始”** 菜单上，单击 **“控制面板”** 。</span><span class="sxs-lookup"><span data-stu-id="945f0-112">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="945f0-113">在“控制面板”中，单击 **“程序和功能”**。</span><span class="sxs-lookup"><span data-stu-id="945f0-113">In the Control Panel, click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="945f0-114">在“名称”\*\*\*\* 列表中找到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 报表生成器并单击它。</span><span class="sxs-lookup"><span data-stu-id="945f0-114">Locate [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Builder in the **Name** list and click it.</span></span>  
  
4.  <span data-ttu-id="945f0-115">单击“卸载”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="945f0-115">Click **Uninstall**.</span></span>  
  
5.  <span data-ttu-id="945f0-116">如果提示需要确认卸载报表生成器，请单击 **“是”**。</span><span class="sxs-lookup"><span data-stu-id="945f0-116">If prompted to confirm the uninstall of Report Builder, click **Yes**.</span></span>  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a><span data-ttu-id="945f0-117">从命令行卸载报表生成器</span><span class="sxs-lookup"><span data-stu-id="945f0-117">To uninstall Report Builder from the command line</span></span>  
  
1.  <span data-ttu-id="945f0-118">在 **“开始”** 菜单上，单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="945f0-118">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="945f0-119">在 "**打开**" 文本框中，键入`cmd.`</span><span class="sxs-lookup"><span data-stu-id="945f0-119">In the **Open** text box, type `cmd.`</span></span>  
  
3.  <span data-ttu-id="945f0-120">在命令提示符窗口中，导航到包含 ReportBuilder3_x86.msi 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="945f0-120">In the command prompt window, navigate to the folder with ReportBuilder3_x86.msi.</span></span>  
  
4.  <span data-ttu-id="945f0-121">键入如下基本命令行：</span><span class="sxs-lookup"><span data-stu-id="945f0-121">Type a basic command line such as the following:</span></span>  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 <span data-ttu-id="945f0-122">如果要包括日志记录，请使用如下命令行：</span><span class="sxs-lookup"><span data-stu-id="945f0-122">If you can to include logging, use a command line such as the following:</span></span>  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
1.  <span data-ttu-id="945f0-123">按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="945f0-123">Press **Enter**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="945f0-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="945f0-124">See Also</span></span>  
 <span data-ttu-id="945f0-125">[安装、卸载和报表生成器支持](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="945f0-125">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="945f0-126">安装报表生成器 &#40;报表生成器的独立版本&#41;</span><span class="sxs-lookup"><span data-stu-id="945f0-126">Install the Stand-Alone Version of Report Builder &#40;Report Builder&#41;</span></span>](install-report-builder.md)  
  
  
