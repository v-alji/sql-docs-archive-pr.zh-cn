---
title: Analysis Services 和商业智能中&#39;的新增功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/07/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
author: minewiskan
ms.author: owend
ms.openlocfilehash: 18863a565b63ccc1a9bd2eb0e7619d4d133c5d33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579079"
---
# <a name="what39s-new-in-sql-server-2014-analysis-services"></a><span data-ttu-id="76918-102">SQL Server 2014 中的新增功能&#39;Analysis Services</span><span class="sxs-lookup"><span data-stu-id="76918-102">What&#39;s New in SQL Server 2014 Analysis Services</span></span>
  <span data-ttu-id="76918-103">除了添加支持多维模型的 Power View 报表的功能之外，与 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 以前的版本相比，没有任何变化。</span><span class="sxs-lookup"><span data-stu-id="76918-103">With exception to added functionality supporting Power View Reports against Multidimensional Models, [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is unchanged from the previous release.</span></span>

 <span data-ttu-id="76918-104">有关 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 此版本中其他产品和技术的详细信息，请参阅[SQL Server 2014 中的新增功能](../sql-server/what-s-new-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="76918-104">For information about other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies that are different in this release, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>

## <a name="updates-to-design-tool-installation"></a><span data-ttu-id="76918-105">设计工具安装更新</span><span class="sxs-lookup"><span data-stu-id="76918-105">Updates to Design Tool installation</span></span>
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] <span data-ttu-id="76918-106">for Business Intelligence (SSDT-BI)（以前称为 Business Intelligence Development Studio (BIDS)）用于创建 Analysis Services 模型、Reporting Services 报表和 Integration Services 包。</span><span class="sxs-lookup"><span data-stu-id="76918-106">for Business Intelligence (SSDT-BI), previously known as Business Intelligence Development Studio (BIDS), is used to create Analysis Services models, Reporting Services reports, and Integration Services packages.</span></span> <span data-ttu-id="76918-107">您可以从以下位置下载 SSDT-BI：</span><span class="sxs-lookup"><span data-stu-id="76918-107">You can download SSDT-BI from the following locations:</span></span>

-   [<span data-ttu-id="76918-108">下载 SSDT-BI for Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="76918-108">Download SSDT-BI for Visual Studio 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396526)

-   [<span data-ttu-id="76918-109">下载 SSDT-BI for Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="76918-109">Download SSDT-BI for Visual Studio 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=273673)

 <span data-ttu-id="76918-110">如果计算机上装有旧版 SSDT-BI 或 BIDS，则新版与旧版并行安装。</span><span class="sxs-lookup"><span data-stu-id="76918-110">If you have a prior version of SSDT-BI or BIDS installed on your computer, the newer version is installed side-by-side the previous version.</span></span> <span data-ttu-id="76918-111">在一个工作站上同时运行新版和旧版的设计工具是很常见的，这样可以修改与特定服务器版本关联的项目和解决方案。</span><span class="sxs-lookup"><span data-stu-id="76918-111">It's common to run newer and older versions of the design tools on a single workstation so that you can modify projects and solutions tied to specific versions of the server.</span></span>

> [!NOTE]
>  <span data-ttu-id="76918-112">有多个下载站点可下载 SSDT 的 Visual Studio 2012 和 Visual Studio 2013 版本。</span><span class="sxs-lookup"><span data-stu-id="76918-112">There are several download sites for the Visual Studio 2012 and Visual Studio 2013 versions of SSDT.</span></span> <span data-ttu-id="76918-113">大多不含 BI 项目模板。</span><span class="sxs-lookup"><span data-stu-id="76918-113">Most do not include the BI project templates.</span></span> <span data-ttu-id="76918-114">使用上面的链接可获得正确的版本。</span><span class="sxs-lookup"><span data-stu-id="76918-114">Using the links above will get you the correct version.</span></span> <span data-ttu-id="76918-115">如果你看到 "商业智能项目模板" 文件夹，你将知道 SSDT-BI 的版本是否正确。</span><span class="sxs-lookup"><span data-stu-id="76918-115">You'll know that you have the correct version of SSDT-BI if you see the Business Intelligence project templates folder.</span></span> <span data-ttu-id="76918-116">此文件夹包含 Analysis Services、Reporting Services 和 Integration Services 的项目模板。</span><span class="sxs-lookup"><span data-stu-id="76918-116">This folder contains the project templates for Analysis Services, Reporting Services and Integration Services.</span></span> <span data-ttu-id="76918-117">根据安装 SSDT-BI 的方式，可能还会看到一个 SQL Server 数据库项目模板。</span><span class="sxs-lookup"><span data-stu-id="76918-117">Depending on how you installed SSDT-BI, you might also see an additional project template for SQL Server databases.</span></span>

 <span data-ttu-id="76918-118">![SSDT 中的“新建项目模板”](media/ssdt-biprojects.png "SSDT 中的“新建项目模板”")</span><span class="sxs-lookup"><span data-stu-id="76918-118">![New Project templates in SSDT](media/ssdt-biprojects.png "New Project templates in SSDT")</span></span>

## <a name="features-recently-added-power-view-for-multidimensional-models"></a><span data-ttu-id="76918-119">最近添加的功能：用于多维模型的 Power View</span><span class="sxs-lookup"><span data-stu-id="76918-119">Features recently added: Power View for Multidimensional Models</span></span>
 <span data-ttu-id="76918-120">针对多维模型创建 Power View 报表的功能最先是在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 累积更新 4 中引入的。</span><span class="sxs-lookup"><span data-stu-id="76918-120">The ability to create Power View reports against multidimensional models was first introduced in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 4.</span></span> <span data-ttu-id="76918-121">用于多维模型的 Power View 现在包含在 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="76918-121">Power View for Multidimensional Models functionality is now included as part of [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>

 <span data-ttu-id="76918-122">**用于多维模型的 Power View 报表**</span><span class="sxs-lookup"><span data-stu-id="76918-122">**Power View Report for a Multidimensional Model**</span></span>

 <span data-ttu-id="76918-123">![Power View 报表](media/powerviewreport-wn.gif "Power View 报表")</span><span class="sxs-lookup"><span data-stu-id="76918-123">![Power View Report](media/powerviewreport-wn.gif "Power View Report")</span></span>

 <span data-ttu-id="76918-124">此功能通过使多维模型（也称为 OLAP 多维数据集）可以与最新客户端报告工具一起使用，帮助组织最大程度利用现有的 BI 投资。</span><span class="sxs-lookup"><span data-stu-id="76918-124">This functionality helps organizations maximize existing BI investments by enabling multidimensional models (also known as OLAP cubes) to be used with the latest client reporting tools.</span></span> <span data-ttu-id="76918-125">根据多维模型中的数据类型，用户可以方便地创建各种动态可视化对象，从表和矩阵到气泡图和地理图。</span><span class="sxs-lookup"><span data-stu-id="76918-125">Depending on the types of data in the multidimensional model, users can easily create a variety of dynamic visualizations from tables and matrices, to bubble charts and geographical maps.</span></span> <span data-ttu-id="76918-126">多维模型现在还支持使用数据分析表达式 (DAX) 进行查询。</span><span class="sxs-lookup"><span data-stu-id="76918-126">Multidimensional models now also support queries using Data Analysis Expressions (DAX).</span></span>

 <span data-ttu-id="76918-127">用于多维模型的 Power View 需要 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中的内置 Power View 报告功能（在 SharePoint 模式下）。</span><span class="sxs-lookup"><span data-stu-id="76918-127">Power View for Multidimensional Models requires the built-in Power View reporting capability in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (in SharePoint mode).</span></span> <span data-ttu-id="76918-128">其他版本的 Power View（特别是 Excel 2013 中的 Power View 外接程序）不支持多维模型。</span><span class="sxs-lookup"><span data-stu-id="76918-128">Other versions of Power View, specifically the Power View Add-in in Excel 2013, do not support multidimensional models.</span></span>

 <span data-ttu-id="76918-129">若要了解详细信息，请参阅[多维模型的 Power View](https://msdn.microsoft.com/library/dn140246.aspx)。</span><span class="sxs-lookup"><span data-stu-id="76918-129">To learn more, see [Power View for Multidimensional Models](https://msdn.microsoft.com/library/dn140246.aspx).</span></span>


