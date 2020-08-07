---
title: 创建链接报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed5e70c9ff8179ae05186685e21303693fc9aed7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588267"
---
# <a name="create-a-linked-report"></a><span data-ttu-id="6ecbb-102">创建链接报表</span><span class="sxs-lookup"><span data-stu-id="6ecbb-102">Create a Linked Report</span></span>
  <span data-ttu-id="6ecbb-103">链接报表是提供对现有报表的访问点的报表服务器项。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-103">A linked report is a report server item that provides an access point to an existing report.</span></span> <span data-ttu-id="6ecbb-104">从概念上说，它与用于运行程序或打开文件的程序快捷方式类似。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-104">Conceptually, it is similar to a program shortcut that you use to run a program or open a file.</span></span>

 <span data-ttu-id="6ecbb-105">链接报表是从现有报表派生的，保留原始报表的报表定义。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-105">A linked report is derived from an existing report and retains the original's report definition.</span></span> <span data-ttu-id="6ecbb-106">链接报表始终会继承原始报表的报表布局和数据源属性。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-106">A linked report always inherits report layout and data source properties of the original report.</span></span> <span data-ttu-id="6ecbb-107">所有其他属性和设置都可以与原始报表不同，其中包括安全性、参数、位置、订阅和计划。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-107">All other properties and settings can be different from those of the original report, including security, parameters, location, subscriptions, and schedules.</span></span>

 <span data-ttu-id="6ecbb-108">如果希望创建现有报表的其他版本，则可以创建链接报表。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-108">You can create a linked report when you want to create additional versions of an existing report.</span></span> <span data-ttu-id="6ecbb-109">例如，可以使用一个区域销售额报表来为所有销售区域创建区域特定的报表。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-109">For example, you could use a single regional sales report to create region-specific reports for all of your sales territories.</span></span>

 <span data-ttu-id="6ecbb-110">虽然链接报表通常基于参数化报表，但并不一定需要使用参数化报表。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-110">Although linked reports are typically based on parameterized reports, a parameterized report is not required.</span></span> <span data-ttu-id="6ecbb-111">每当您想使用不同的设置部署现有报表时，都可以创建链接报表。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-111">You can create linked reports whenever you want to deploy an existing report with different settings.</span></span>

### <a name="to-create-a-linked-report"></a><span data-ttu-id="6ecbb-112">创建链接报表</span><span class="sxs-lookup"><span data-stu-id="6ecbb-112">To create a linked report</span></span>

1.  <span data-ttu-id="6ecbb-113">在报表管理器中，导航到包含想要链接到的报表的文件夹，然后打开选项菜单并单击 **“创建链接报表”**。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-113">In Report Manager, navigate to the folder containing the report that you want to link to, and then open the options menu can click **Create Linked Report**.</span></span>

2.  <span data-ttu-id="6ecbb-114">键入新链接报表的名称。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-114">Type a name for the new linked report.</span></span> <span data-ttu-id="6ecbb-115">根据需要，可以键入说明。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-115">Optionally type a description.</span></span>

3.  <span data-ttu-id="6ecbb-116">若要为报表选择不同的文件夹，请单击 **“更改位置”**。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-116">To select a different folder for the report, click **Change Location**.</span></span> <span data-ttu-id="6ecbb-117">单击要使用的文件夹，或者在 **“位置”** 框中键入文件夹名称。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-117">Click the folder you want to use, or type the folder name in the **Location** box.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)] <span data-ttu-id="6ecbb-118">如果没有选择不同的文件夹，则将在当前文件夹（链接报表所基于的报表的存储位置）中创建链接报表。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-118">If you do not select a different folder, the linked report is created in the current folder (where the report it is based on is stored).</span></span>

4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] <span data-ttu-id="6ecbb-119">将打开链接报表。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-119">The linked report opens.</span></span>

     <span data-ttu-id="6ecbb-120">链接报表的图标与报表服务器管理的其他项不同。</span><span class="sxs-lookup"><span data-stu-id="6ecbb-120">A linked report's icon differs from other items managed by a report server.</span></span> <span data-ttu-id="6ecbb-121">下面的图标表示链接报表：</span><span class="sxs-lookup"><span data-stu-id="6ecbb-121">The following icon indicates a linked report:</span></span>

     <span data-ttu-id="6ecbb-122">![链接报表图标](../media/hlp-16linked.gif "链接报表图标")</span><span class="sxs-lookup"><span data-stu-id="6ecbb-122">![Linked report icon](../media/hlp-16linked.gif "Linked report icon")</span></span>

## <a name="see-also"></a><span data-ttu-id="6ecbb-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ecbb-123">See Also</span></span>
 <span data-ttu-id="6ecbb-124">[打开并关闭报表 &#40;报表管理器&#41;"](../reports/open-and-close-a-report-report-manager.md) [新建链接报表" 页 &#40;报表管理器](../new-linked-report-page-report-manager.md)&#41;"[选择项位置" 页 &#40;](../choose-item-location-page-report-manager.md)报表管理器&#41;["常规属性" 页上，](../general-properties-page-reports-report-manager.md) &#40;[ssrs 报表管理器](../reporting-services-concepts-ssrs.md) [&#41;Reporting Services](../report-manager-ssrs-native-mode.md)</span><span class="sxs-lookup"><span data-stu-id="6ecbb-124">[Open and Close a Report &#40;Report Manager&#41;](../reports/open-and-close-a-report-report-manager.md) [New Linked Report Page &#40;Report Manager&#41;](../new-linked-report-page-report-manager.md) [Choose Item Location Page &#40;Report Manager&#41;](../choose-item-location-page-report-manager.md) [General Properties Page, Reports &#40;Report Manager&#41;](../general-properties-page-reports-report-manager.md) [Reporting Services Concepts &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md) [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md)</span></span>


