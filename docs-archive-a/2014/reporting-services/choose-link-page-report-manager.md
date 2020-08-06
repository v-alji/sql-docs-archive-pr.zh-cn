---
title: 选择链接页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a89a555d-efa3-45d6-951e-db78ec6a2c8e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc40fe726555babee8d9940e198a93577bd6a09f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580059"
---
# <a name="choose-link-page-report-manager"></a><span data-ttu-id="8de65-102">“选择链接”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="8de65-102">Choose Link Page (Report Manager)</span></span>
  <span data-ttu-id="8de65-103">使用“选择链接”页可为当前所选链接报表选择要基于的不同报表。</span><span class="sxs-lookup"><span data-stu-id="8de65-103">Use the Choose Link page to choose a different report upon which to base the currently selected linked report.</span></span> <span data-ttu-id="8de65-104">链接报表基于已发布到报表服务器的其他报表。</span><span class="sxs-lookup"><span data-stu-id="8de65-104">Linked reports are based on other reports already published to a report server.</span></span> <span data-ttu-id="8de65-105">链接报表使用基础报表的布局和数据，但是其属性页与基础报表不同，以便您可以自定义参数属性、安全设置、名称、说明和位置。</span><span class="sxs-lookup"><span data-stu-id="8de65-105">A linked report uses the layout and data of the base report, but has separate property pages so that you can customize parameter properties, security settings, name, description, and location.</span></span>  
  
 <span data-ttu-id="8de65-106">通过“选择链接”页，可以选择另一个已发布的报表来与链接报表一起使用。</span><span class="sxs-lookup"><span data-stu-id="8de65-106">Through the Choose Link page, you can choose a different published report to use with the linked report.</span></span> <span data-ttu-id="8de65-107">更改链接信息不会影响链接报表的其他设置（例如安全性和参数设置）。</span><span class="sxs-lookup"><span data-stu-id="8de65-107">Other settings of the linked report (such as security and parameter settings) are unaffected by changes to the link information.</span></span> <span data-ttu-id="8de65-108">报表服务器将不验证您选择的内容，因此请确保所选报表具有的参数与您在链接报表上指定的参数相同。</span><span class="sxs-lookup"><span data-stu-id="8de65-108">The report server will not validate your selection, so be sure to choose a report that has the same parameters as those you specified on the linked report.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="8de65-109">导航</span><span class="sxs-lookup"><span data-stu-id="8de65-109">Navigation</span></span>  
 <span data-ttu-id="8de65-110">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="8de65-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-choose-link-page"></a><span data-ttu-id="8de65-111">打开“选择链接”页</span><span class="sxs-lookup"><span data-stu-id="8de65-111">To open the Choose Link page</span></span>  
  
1.  <span data-ttu-id="8de65-112">打开报表管理器，找到要更改的链接报表。</span><span class="sxs-lookup"><span data-stu-id="8de65-112">Open Report Manager, and locate the linked report you want to change.</span></span>  
  
2.  <span data-ttu-id="8de65-113">悬停在链接报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="8de65-113">Hover over the linked report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="8de65-114">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="8de65-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="8de65-115">这会打开该链接报表的 **“常规”** 属性页。</span><span class="sxs-lookup"><span data-stu-id="8de65-115">This opens the **General** properties page for the linked report.</span></span>  
  
4.  <span data-ttu-id="8de65-116">在 **“常规”** 选项卡上的属性页中单击 **“更改链接”**。</span><span class="sxs-lookup"><span data-stu-id="8de65-116">On the **General** tab, on the properties page, click **Change Link**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8de65-117">选项</span><span class="sxs-lookup"><span data-stu-id="8de65-117">Options</span></span>  
 <span data-ttu-id="8de65-118">**位置**</span><span class="sxs-lookup"><span data-stu-id="8de65-118">**Location**</span></span>  
 <span data-ttu-id="8de65-119">指定已发布报表的全名，包括文件夹路径和报表名称。</span><span class="sxs-lookup"><span data-stu-id="8de65-119">Specify the full name of the published report, including the folder path and report name.</span></span> <span data-ttu-id="8de65-120">您可以键入报表的全名，也可以使用树视图导航到要使用的报表。</span><span class="sxs-lookup"><span data-stu-id="8de65-120">You can type the full name of the report or use the tree view to navigate to the report you want to use.</span></span>  
  
 <span data-ttu-id="8de65-121">**树视图**</span><span class="sxs-lookup"><span data-stu-id="8de65-121">**Tree view**</span></span>  
 <span data-ttu-id="8de65-122">显示报表服务器文件夹层次结构中的所有文件夹。</span><span class="sxs-lookup"><span data-stu-id="8de65-122">Shows all of the folders in the report server folder hierarchy.</span></span> <span data-ttu-id="8de65-123">若要通过树视图来填写 **“位置”** 字段，请单击相应报表的名称。</span><span class="sxs-lookup"><span data-stu-id="8de65-123">To use the tree view to fill in the **Location** field, click the name of the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de65-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8de65-124">See Also</span></span>  
 <span data-ttu-id="8de65-125">[报表 &#40;报表管理器的 "常规属性" 页&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8de65-125">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="8de65-126">[报表管理器 &#40;的 "新建链接报表" 页&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8de65-126">[New Linked Report Page &#40;Report Manager&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span></span>  
 [<span data-ttu-id="8de65-127">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="8de65-127">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
