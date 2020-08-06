---
title: 将报表作为点击链接型报表链接到模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cb84f8036dbe5a1694628144f0b948452261ca75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578695"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a><span data-ttu-id="e2e60-102">将报表作为点击链接型报表链接到模型</span><span class="sxs-lookup"><span data-stu-id="e2e60-102">Link a Report to a Model as a Clickthrough Report</span></span>
  <span data-ttu-id="e2e60-103">您可以不使用默认的点击链接型报表模板，而创建报表生成器报表并将其链接到报表模型中的特定实体。</span><span class="sxs-lookup"><span data-stu-id="e2e60-103">Instead of using the default clickthrough report templates, you can create a Report Builder report and then link it to a specific entity in the report model.</span></span> <span data-ttu-id="e2e60-104">当查看报表的用户单击主报表中的交互式数据时，该报表便会显示为点击链接型报表。</span><span class="sxs-lookup"><span data-stu-id="e2e60-104">When the person viewing the report clicks the interactive data in the main report, this report is displayed as a clickthrough report.</span></span> <span data-ttu-id="e2e60-105">若要将报表链接到某个实体，请使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表管理器。</span><span class="sxs-lookup"><span data-stu-id="e2e60-105">To link a report to an entity, use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e2e60-106">报表中使用的主实体（或基实体）必须与报表所链接到的实体相同。</span><span class="sxs-lookup"><span data-stu-id="e2e60-106">The primary, or base, entity that is used in the report must to be the same entity to which the report is linked.</span></span>  
  
### <a name="to-start-report-manager-from-a-browser"></a><span data-ttu-id="e2e60-107">从浏览器启动报表管理器</span><span class="sxs-lookup"><span data-stu-id="e2e60-107">To start Report Manager from a browser</span></span>  
  
1.  <span data-ttu-id="e2e60-108">打开 [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e2e60-108">Open [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 or later.</span></span>  
  
2.  <span data-ttu-id="e2e60-109">在 Web 浏览器的地址栏中，键入报表管理器 URL。</span><span class="sxs-lookup"><span data-stu-id="e2e60-109">In the address bar of the Web browser, type the Report Manager URL.</span></span> <span data-ttu-id="e2e60-110">默认情况下，URL 是 http:// \<*ComputerName*> /reports。</span><span class="sxs-lookup"><span data-stu-id="e2e60-110">By default, the URL is http://\<*ComputerName*>/reports.</span></span>  
  
### <a name="to-create-a-customized-clickthrough-report"></a><span data-ttu-id="e2e60-111">创建自定义的点击链接型报表</span><span class="sxs-lookup"><span data-stu-id="e2e60-111">To create a customized clickthrough report</span></span>  
  
1.  <span data-ttu-id="e2e60-112">导航到要向其中添加自定义点击链接型报表的报表模型。</span><span class="sxs-lookup"><span data-stu-id="e2e60-112">Navigate to the report model to which you want to add the customized clickthrough report.</span></span>  
  
2.  <span data-ttu-id="e2e60-113">双击此报表模型。</span><span class="sxs-lookup"><span data-stu-id="e2e60-113">Double-click the report model.</span></span>  
  
3.  <span data-ttu-id="e2e60-114">单击 **“点击链接”**。</span><span class="sxs-lookup"><span data-stu-id="e2e60-114">Click **Clickthrough**.</span></span>  
  
4.  <span data-ttu-id="e2e60-115">选择要向其中附加自定义点击链接型报表的实体。</span><span class="sxs-lookup"><span data-stu-id="e2e60-115">Select the entity to which you want to attach the customized clickthrough report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2e60-116">此实体必须与自定义点击链接型报表的基实体相同。</span><span class="sxs-lookup"><span data-stu-id="e2e60-116">This entity must be the same as the base entity of the customized clickthrough report.</span></span>  
  
5.  <span data-ttu-id="e2e60-117">若要在单击选定实体的单个实例时显示此自定义报表，请单击单个实例报表 **“浏览”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="e2e60-117">To display the customized report when a single instance of the selected entity is clicked, click the Single instance report **Browse** button.</span></span>  
  
     <span data-ttu-id="e2e60-118">- 或 -</span><span class="sxs-lookup"><span data-stu-id="e2e60-118">-or-</span></span>  
  
     <span data-ttu-id="e2e60-119">若要在单击选定实体的多个实例时显示此自定义报表，请单击多个实例报表 **“浏览”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="e2e60-119">To display the customized report when a multiple instance of the selected entity is clicked, click the Multiple instance report **Browse** button.</span></span>  
  
6.  <span data-ttu-id="e2e60-120">选择该报表，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e2e60-120">Select the report and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="e2e60-121">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="e2e60-121">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e60-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2e60-122">See Also</span></span>  
 [<span data-ttu-id="e2e60-123">SSRS&#41;的点击链接型 &#40;报表</span><span class="sxs-lookup"><span data-stu-id="e2e60-123">Clickthrough Reports &#40;SSRS&#41;</span></span>](reports/clickthrough-reports-ssrs.md)  
  
  
