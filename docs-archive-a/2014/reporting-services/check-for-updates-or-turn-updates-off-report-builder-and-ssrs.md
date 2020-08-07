---
title: 检查更新或关闭更新 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9c69792d-d7c4-453b-ae2f-6d2d071d8606
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 088d41e71d770f746367f2760cff8ff67b15623c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586495"
---
# <a name="check-for-updates-or-turn-updates-off-report-builder-and-ssrs"></a><span data-ttu-id="624c4-102">检查更新或关闭更新（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="624c4-102">Check for Updates or Turn Updates Off (Report Builder and SSRS)</span></span>
  <span data-ttu-id="624c4-103">每次您打开一个报表时，报表生成器都将查看该报表中报表部件的已发布实例是否已在报表服务器上或与报表服务器相集成的 SharePoint 站点上更新。</span><span class="sxs-lookup"><span data-stu-id="624c4-103">Every time you open a report, Report Builder checks to see if the published instances of report parts in that report have been updated on the report server or SharePoint site integrated with a report server.</span></span> <span data-ttu-id="624c4-104">它还将检查报表部件的依赖项（如数据集和参数）的更改。</span><span class="sxs-lookup"><span data-stu-id="624c4-104">It also checks for changes in the report parts' dependent items, such as the dataset and parameters.</span></span> <span data-ttu-id="624c4-105">如果任何报表部件或其依赖关系已在站点或服务器上进行了更新，则报表中的信息栏将显示已更新部件的数量。</span><span class="sxs-lookup"><span data-stu-id="624c4-105">If any report parts or their dependencies have been updated on the site or server, an information bar in your report displays the number of updated parts.</span></span> <span data-ttu-id="624c4-106">您可以选择查看并接受或拒绝更新，或关闭信息栏。</span><span class="sxs-lookup"><span data-stu-id="624c4-106">You can choose to view and accept or reject the updates, or dismiss the information bar.</span></span>  
  
 <span data-ttu-id="624c4-107">您还可以禁用信息栏，这样，当更改报表部件的已发布实例时系统将不会通知您。</span><span class="sxs-lookup"><span data-stu-id="624c4-107">You can also disable the information bar and not be informed if published instances of report parts have changed.</span></span> <span data-ttu-id="624c4-108">这是一项用户设置；它将对您打开的所有报表禁用信息栏。</span><span class="sxs-lookup"><span data-stu-id="624c4-108">This is a user setting; it will be disabled for all reports that you open.</span></span> <span data-ttu-id="624c4-109">即使已禁用信息栏，也仍可以检查更新。</span><span class="sxs-lookup"><span data-stu-id="624c4-109">Even if you have disabled the information bar, you can still check for updates.</span></span>  
  
### <a name="to-turn-on-and-off-report-part-updates"></a><span data-ttu-id="624c4-110">打开和关闭报表部件更新</span><span class="sxs-lookup"><span data-stu-id="624c4-110">To turn on and off report part updates</span></span>  
  
1.  <span data-ttu-id="624c4-111">单击 "报表生成器" 按钮，然后单击 "**选项**"。</span><span class="sxs-lookup"><span data-stu-id="624c4-111">Click the Report Builder button, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="624c4-112">在 "**选项**" 对话框的 "**资源**" 选项卡中，选中或清除 "在**我的报表中显示报表部件的更新**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="624c4-112">In the **Options** dialog box, on the **Resources** tab, select or clear the **Show updates to report parts in my reports** check box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="624c4-113">这是一项用户设置。</span><span class="sxs-lookup"><span data-stu-id="624c4-113">This is a user setting.</span></span> <span data-ttu-id="624c4-114">它将对您打开的所有报表禁用信息栏。</span><span class="sxs-lookup"><span data-stu-id="624c4-114">It will be disabled for all reports that you open.</span></span>  
  
### <a name="to-check-for-updates"></a><span data-ttu-id="624c4-115">检查  更新的步骤</span><span class="sxs-lookup"><span data-stu-id="624c4-115">To check for updates</span></span>  
  
-   <span data-ttu-id="624c4-116">右键单击报表之外或表体中的设计图面，然后单击 "**检查更新**"。</span><span class="sxs-lookup"><span data-stu-id="624c4-116">Right-click the design surface outside the report, or in the report body, and click **Check for Updates**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="624c4-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="624c4-117">See Also</span></span>  
 <span data-ttu-id="624c4-118">[报表部件 &#40;报表生成器和 SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="624c4-118">[Report Parts &#40;Report Builder and SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="624c4-119">[发布和重新发布报表部件 &#40;报表生成器和 SSRS&#41;](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="624c4-119">[Publish and Republish Report Parts &#40;Report Builder and SSRS&#41;](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="624c4-120">[浏览查找报表部件和设置默认文件夹 &#40;报表生成器和 SSRS&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="624c4-120">[Browse for Report Parts and Set a Default Folder &#40;Report Builder and SSRS&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="624c4-121">[&#40;报表生成器和 SSRS 的报表部件疑难解答&#41;](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="624c4-121">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="624c4-122">报表生成器中的报表部件和数据集</span><span class="sxs-lookup"><span data-stu-id="624c4-122">Report Parts and Datasets in Report Builder</span></span>](report-data/report-parts-and-datasets-in-report-builder.md)  
  
  
