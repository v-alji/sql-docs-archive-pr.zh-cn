---
title: " (SSAS 表格) Power View 报表属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 51205c2d-b6ce-4b92-afd2-58e399a81691
author: minewiskan
ms.author: owend
ms.openlocfilehash: e85d91578e5c3f4b47f56eeb86aa738e37e8f59b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683097"
---
# <a name="power-view-reporting-properties-ssas-tabular"></a><span data-ttu-id="ce38e-102">Power View 报表属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ce38e-102">Power View Reporting Properties (SSAS Tabular)</span></span>
  [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="ce38e-103">为数据分析员、业务决策者和信息工作者之类的业务用户提供直观的即席生成报表功能。</span><span class="sxs-lookup"><span data-stu-id="ce38e-103">provides intuitive ad-hoc reporting for business users such as data analysts, business decision makers, and information workers.</span></span> <span data-ttu-id="ce38e-104">用户可轻松地从基于 PowerPivot 库中发布的 PowerPivot 工作簿的表格模型或使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 创建然后部署到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Services 实例的表格模型中创建数据视图，并与之交互。</span><span class="sxs-lookup"><span data-stu-id="ce38e-104">They can easily create and interact with views of data from tabular models based on PowerPivot workbooks published in a PowerPivot Gallery, or tabular models authored by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and then deployed to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Services instances.</span></span> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="ce38e-105">是一种从 SharePoint Server 2010 或更高版本启动的基于浏览器的 Silverlight 应用程序。</span><span class="sxs-lookup"><span data-stu-id="ce38e-105">is a browser-based Silverlight application launched from SharePoint Server 2010 or later.</span></span>  
  
 <span data-ttu-id="ce38e-106">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中创建表格模型项目时，可以配置一些对于 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 报告来说唯一的报告属性。</span><span class="sxs-lookup"><span data-stu-id="ce38e-106">When authoring tabular model projects in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], you can configure certain reporting properties unique to [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span> <span data-ttu-id="ce38e-107">本节中的主题说明如何优化模型，以提高 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]中的报表体验。</span><span class="sxs-lookup"><span data-stu-id="ce38e-107">Topics in this section describe how to optimize a model to improve the reporting experience in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ce38e-108">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ce38e-108">Related Tasks</span></span>  
  
|<span data-ttu-id="ce38e-109">主题</span><span class="sxs-lookup"><span data-stu-id="ce38e-109">Topic</span></span>|<span data-ttu-id="ce38e-110">说明</span><span class="sxs-lookup"><span data-stu-id="ce38e-110">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ce38e-111">配置 Power View 报表的默认字段集（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ce38e-111">Configure Default Field Set for Power View Reports &#40;SSAS Tabular&#41;</span></span>](power-view-configure-default-field-set-for-reports.md)|<span data-ttu-id="ce38e-112">说明如何配置默认字段集；该字段集是一个列和度量值的预定义列表，当在报表字段列表中选择表时，这些列和度量值会自动添加到 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 报表画布中。</span><span class="sxs-lookup"><span data-stu-id="ce38e-112">Describes how to configure a Default Field Set; a predefined list of columns and measures that are automatically added to a [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] report canvas when the table is selected in the report field list.</span></span>|  
|[<span data-ttu-id="ce38e-113">为 Power View 报表配置表行为属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ce38e-113">Configure Table Behavior Properties for Power View Reports &#40;SSAS Tabular&#41;</span></span>](power-view-configure-table-behavior-properties-for-reports.md)|<span data-ttu-id="ce38e-114">说明如何配置以更高粒度级别展示详细信息行的表行为属性。</span><span class="sxs-lookup"><span data-stu-id="ce38e-114">Describes how to configure table behavior properties that expose detail rows at a more granular level.</span></span> <span data-ttu-id="ce38e-115">设置表行为属性会更改详细信息行的分组行为，并为图块、卡片和图表布局中的标识信息生成更好的默认位置。</span><span class="sxs-lookup"><span data-stu-id="ce38e-115">Setting table behavior properties changes the grouping behavior of detail rows and produces a better default placement of identifying information in tile, card, and chart layouts.</span></span>|  
  
  
