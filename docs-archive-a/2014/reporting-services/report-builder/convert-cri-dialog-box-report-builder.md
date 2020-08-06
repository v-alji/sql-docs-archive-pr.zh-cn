---
title: “转换 CRI”对话框（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10008"
helpviewer_keywords:
- CRI
- custom report items
ms.assetid: 2a3f2ac6-667e-4498-8b73-9c40beb993f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 97a6c14b9486b2cc82d514bd7a7fa8210bc22204
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578691"
---
# <a name="convert-cri-dialog-box-report-builder"></a><span data-ttu-id="795be-102">“转换 CRI”对话框（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="795be-102">Convert CRI Dialog Box (Report Builder)</span></span>
  <span data-ttu-id="795be-103">该报表包含其中有不受支持的功能的自定义报表项 (CRI)。</span><span class="sxs-lookup"><span data-stu-id="795be-103">This report contains custom report items (CRIs) with unsupported features.</span></span> <span data-ttu-id="795be-104">CRI 是对报表定义语言 (RDL) 的扩展，它支持用于显示报表中的数据的自定义对象。</span><span class="sxs-lookup"><span data-stu-id="795be-104">CRIs are extensions to the Report Definition Language (RDL) that support custom objects that display data in a report.</span></span> <span data-ttu-id="795be-105">CRI 包含由第三方软件供应商提供的设计时和运行时组件。</span><span class="sxs-lookup"><span data-stu-id="795be-105">CRIs include design-time and run-time components that are supplied by third-party software vendors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="795be-106">对于是否选择在报表服务器上支持自定义报表项，需要由系统管理员决定。</span><span class="sxs-lookup"><span data-stu-id="795be-106">Choosing to support custom report items on a report server is a decision made by the system administrator.</span></span> <span data-ttu-id="795be-107">若要查看报表中的 CRI，必须将 CRI 组件安装在报表创作客户端上以预览报表，并将其安装在报表服务器上以查看已发布或上载的报表。</span><span class="sxs-lookup"><span data-stu-id="795be-107">To view CRIs in a report, the CRI components must be installed on the report authoring client to preview a report and on the report server to view a published or uploaded report.</span></span> <span data-ttu-id="795be-108">有关详细信息，请参阅 [Custom Report Items](../custom-report-items/custom-report-items.md)和第三方软件供应商提供的文档。</span><span class="sxs-lookup"><span data-stu-id="795be-108">For more information, see [Custom Report Items](../custom-report-items/custom-report-items.md), and documentation from the third-party software vendor.</span></span>  
  
 <span data-ttu-id="795be-109">某些 CRI 可以转换为采用新的报表定义格式的报表项。</span><span class="sxs-lookup"><span data-stu-id="795be-109">Some CRIs can be converted to report items in the new report definition format.</span></span> <span data-ttu-id="795be-110">打开报表时，系统会提示您是否升级报表。</span><span class="sxs-lookup"><span data-stu-id="795be-110">When you open the report, you are prompted whether to upgrade.</span></span> <span data-ttu-id="795be-111">使用以下信息可以决定是否转换该报表中的 CRI：</span><span class="sxs-lookup"><span data-stu-id="795be-111">Use the following information to decide whether to convert the CRIs in this report:</span></span>  
  
-   <span data-ttu-id="795be-112">**是** 选择 **“是”** 将转换报表中所有可以转换的 CRI。</span><span class="sxs-lookup"><span data-stu-id="795be-112">**Yes** Choose **Yes** to convert all the CRIs in the report, where possible.</span></span> <span data-ttu-id="795be-113">无法升级 CRI 中不受支持的功能，也不能从报表定义文件中删除它们。</span><span class="sxs-lookup"><span data-stu-id="795be-113">Unsupported features in the CRIs cannot be upgraded and are removed from the report definition file.</span></span> <span data-ttu-id="795be-114">有关不支持的功能的列表，请参阅 [升级报表](../install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="795be-114">For the list of unsupported features, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span> <span data-ttu-id="795be-115">查看报表时，可能看到 CRI 在报表中的显示方式存在差异。</span><span class="sxs-lookup"><span data-stu-id="795be-115">When you view the report, you might see differences in the way the CRI displays in the report.</span></span>  
  
-   <span data-ttu-id="795be-116">**否** ：如果不希望转换报表中的 CRI，请选择 **“否”** 。</span><span class="sxs-lookup"><span data-stu-id="795be-116">**No** Choose **No** when you do not want to convert the CRIs in the report.</span></span> <span data-ttu-id="795be-117">当前版本中的报表处理器无法显示这些 CRI。</span><span class="sxs-lookup"><span data-stu-id="795be-117">These CRIs cannot be displayed by the report processor in their current version.</span></span> <span data-ttu-id="795be-118">如果您的系统管理员计划安装从第三方软件供应商那里得到的且与新报表定义格式兼容的新版本 CRI，则应当选择 **“否”** 。</span><span class="sxs-lookup"><span data-stu-id="795be-118">If your system administrator is planning to install a new version of the CRI from the third-party software vendor that is compatible with the new report definition format, you should choose **No**.</span></span> <span data-ttu-id="795be-119">在使用新版本以前，CRI 将作为带有红色 X 的空文本框显示在报表中。</span><span class="sxs-lookup"><span data-stu-id="795be-119">Until new versions are available, the CRIs display in the report as an empty text box with a red X.</span></span>  
  
 <span data-ttu-id="795be-120">在任一情况下，报表将升级到新的报表定义格式，并将原始报表的备份副本另存为 *\<Report Name>* `-` 备份 .rdl。</span><span class="sxs-lookup"><span data-stu-id="795be-120">In either case, the report is upgraded to the new report definition format and a backup copy of the original report is saved as *\<Report Name>* `-` Backup.rdl.</span></span> <span data-ttu-id="795be-121">如果在报表创作工具中保存报表，则会以新的报表定义格式保存升级的报表。</span><span class="sxs-lookup"><span data-stu-id="795be-121">If you save the report in your report authoring tool, you are saving the upgraded report in the new report definition format.</span></span> <span data-ttu-id="795be-122">如果发布报表，则报表首先保存在您的计算机上，然后发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="795be-122">If you publish the report, the report is first saved on your computer, and then published to the report server.</span></span> <span data-ttu-id="795be-123">您需要将报表的升级版本发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="795be-123">You are publishing the upgraded version of the report to the report server.</span></span>  
  
 <span data-ttu-id="795be-124">如果不保存报表，则原始报表将保持不变。</span><span class="sxs-lookup"><span data-stu-id="795be-124">If you do not save the report, the original report remains unchanged.</span></span> <span data-ttu-id="795be-125">但是，不能在比 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 的 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 更高的版本中或在使用此报表定义格式的报表创作环境中编辑该报表。</span><span class="sxs-lookup"><span data-stu-id="795be-125">However, you cannot edit this report in a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] later version of [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or a report authoring environment that uses this report definition format.</span></span> <span data-ttu-id="795be-126">对于报表的原始版本，通过使用报表管理器将它上载到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更高版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器，可以继续运行它。</span><span class="sxs-lookup"><span data-stu-id="795be-126">You can continue to run the original version of the report by uploading it to a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server by using Report Manager.</span></span> <span data-ttu-id="795be-127">有关详细信息，请参阅[上传文件或报表（报表管理器）](../reports/upload-a-file-or-report-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="795be-127">For more information, see [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  
 <span data-ttu-id="795be-128">对于上载而不是发布到报表服务器的报表，报表处理器将在第一次使用该报表时确定是否可以将它升级。</span><span class="sxs-lookup"><span data-stu-id="795be-128">For reports that you upload instead of publish to a report server, the report processor determines whether the report can be upgraded on first use.</span></span> <span data-ttu-id="795be-129">对于无法升级的报表，将以向后兼容模式对其进行处理，并像在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的早期版本中那样继续显示它们。</span><span class="sxs-lookup"><span data-stu-id="795be-129">Reports that cannot be upgraded are processed in backward-compatibility mode, and continue to display as they did in the earlier version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="795be-130">有关更多信息，请参见 [Upgrade Reports](../install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="795be-130">For more information, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
 <span data-ttu-id="795be-131">若要标识报表、报表服务器或报表创作环境的当前报表定义格式，请参阅[查找报表定义架构版本 (SSRS)](../reports/find-the-report-definition-schema-version-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="795be-131">To identify the current report definition format for a report, for a report server, or for your report authoring environment, see [Find the Report Definition Schema Version &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795be-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="795be-132">See Also</span></span>  
 [<span data-ttu-id="795be-133">用于对话框、窗格和向导的报表生成器帮助</span><span class="sxs-lookup"><span data-stu-id="795be-133">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
