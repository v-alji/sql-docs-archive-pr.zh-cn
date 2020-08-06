---
title: Analysis Services 中使用的工具和应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36bbcbca4323a9ce327b5fa89398dfb20da319c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578478"
---
# <a name="tools-and-applications-used-in-analysis-services"></a><span data-ttu-id="83cf3-102">在 Analysis Services 中使用的工具和应用程序</span><span class="sxs-lookup"><span data-stu-id="83cf3-102">Tools and applications used in Analysis Services</span></span>
  <span data-ttu-id="83cf3-103">找到您将需要用于生成 Analysis Services 模型以及用于在 Analysis Services 实例上管理关联数据库的工具和应用程序。</span><span class="sxs-lookup"><span data-stu-id="83cf3-103">Find the tools and applications you'll need for building Analysis Services models, and managing the associated databases on an Analysis Services instance.</span></span>

## <a name="analysis-services-model-designers"></a><span data-ttu-id="83cf3-104">Analysis Services 模型设计器</span><span class="sxs-lookup"><span data-stu-id="83cf3-104">Analysis Services Model Designers</span></span>
 <span data-ttu-id="83cf3-105">表格和多维模型是从 Visual Studio shell 内部生成的一个解决方案中的项目模板创建。</span><span class="sxs-lookup"><span data-stu-id="83cf3-105">Tabular and multidimensional models are created from project templates in a solution built inside the Visual Studio shell.</span></span> <span data-ttu-id="83cf3-106">项目模板提供用于创建模型、多维数据集、维度和包含 Analysis Services 解决方案的角色的设计器。</span><span class="sxs-lookup"><span data-stu-id="83cf3-106">The project template provides the designers for creating models, cubes, dimensions, and roles that comprise an Analysis Services solution.</span></span>

### <a name="download-sql-server-data-tools-for-business-intelligence-ssdt-bi"></a><span data-ttu-id="83cf3-107">下载 SQL Server Data Tools for Business Intelligence (SSDT-BI)</span><span class="sxs-lookup"><span data-stu-id="83cf3-107">Download SQL Server Data Tools for Business Intelligence (SSDT-BI)</span></span>
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] <span data-ttu-id="83cf3-108">for Business Intelligence (SSDT-BI)（以前称为 Business Intelligence Development Studio (BIDS)）用于创建 Analysis Services 模型、Reporting Services 报表和 Integration Services 包。</span><span class="sxs-lookup"><span data-stu-id="83cf3-108">for Business Intelligence (SSDT-BI), previously known as Business Intelligence Development Studio (BIDS), is used to create Analysis Services models, Reporting Services reports, and Integration Services packages.</span></span> <span data-ttu-id="83cf3-109">您可以从以下位置下载 SSDT-BI：</span><span class="sxs-lookup"><span data-stu-id="83cf3-109">You can download SSDT-BI from the following locations:</span></span>

-   [<span data-ttu-id="83cf3-110">下载 SSDT-BI for Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="83cf3-110">Download SSDT-BI for Visual Studio 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396526)

-   [<span data-ttu-id="83cf3-111">下载 SSDT-BI for Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="83cf3-111">Download SSDT-BI for Visual Studio 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=273673)

 <span data-ttu-id="83cf3-112">如果计算机上装有旧版 SSDT-BI 或 BIDS，则新版与旧版并行安装。</span><span class="sxs-lookup"><span data-stu-id="83cf3-112">If you have a prior version of SSDT-BI or BIDS installed on your computer, the newer version is installed side-by-side the previous version.</span></span> <span data-ttu-id="83cf3-113">在一个工作站上同时运行新版和旧版的设计工具是很常见的，这样可以修改与特定服务器版本关联的项目和解决方案。</span><span class="sxs-lookup"><span data-stu-id="83cf3-113">It's common to run newer and older versions of the design tools on a single workstation so that you can modify projects and solutions tied to specific versions of the server.</span></span>

> [!NOTE]
>  <span data-ttu-id="83cf3-114">有多个下载站点可下载 SSDT 的 Visual Studio 2012 和 Visual Studio 2013 版本。</span><span class="sxs-lookup"><span data-stu-id="83cf3-114">There are several download sites for the Visual Studio 2012 and Visual Studio 2013 versions of SSDT.</span></span> <span data-ttu-id="83cf3-115">大多不含 BI 项目模板。</span><span class="sxs-lookup"><span data-stu-id="83cf3-115">Most do not include the BI project templates.</span></span> <span data-ttu-id="83cf3-116">使用上面的链接可获得正确的版本。</span><span class="sxs-lookup"><span data-stu-id="83cf3-116">Using the links above will get you the correct version.</span></span> <span data-ttu-id="83cf3-117">如果你看到 "商业智能项目模板" 文件夹，你将知道 SSDT-BI 的版本是否正确。</span><span class="sxs-lookup"><span data-stu-id="83cf3-117">You'll know that you have the correct version of SSDT-BI if you see the Business Intelligence project templates folder.</span></span> <span data-ttu-id="83cf3-118">此文件夹包含 Analysis Services、Reporting Services 和 Integration Services 的项目模板。</span><span class="sxs-lookup"><span data-stu-id="83cf3-118">This folder contains the project templates for Analysis Services, Reporting Services and Integration Services.</span></span> <span data-ttu-id="83cf3-119">根据安装 SSDT-BI 的方式，可能还会看到一个 SQL Server 数据库项目模板。</span><span class="sxs-lookup"><span data-stu-id="83cf3-119">Depending on how you installed SSDT-BI, you might also see an additional project template for SQL Server databases.</span></span>

 <span data-ttu-id="83cf3-120">![SSDT 中的“新建项目模板”](media/ssdt-biprojects.png "SSDT 中的“新建项目模板”")</span><span class="sxs-lookup"><span data-stu-id="83cf3-120">![New Project templates in SSDT](media/ssdt-biprojects.png "New Project templates in SSDT")</span></span>

## <a name="administrative-tools"></a><span data-ttu-id="83cf3-121">管理工具</span><span class="sxs-lookup"><span data-stu-id="83cf3-121">Administrative tools</span></span>

### <a name="sql-server-management-studio"></a><span data-ttu-id="83cf3-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="83cf3-122">SQL Server Management Studio</span></span>
 <span data-ttu-id="83cf3-123">Management Studio 是所有 SQL Server 功能（包括 Analysis Services）的主要管理工具。</span><span class="sxs-lookup"><span data-stu-id="83cf3-123">Management Studio is the primary administration tool for all SQL Server features, including Analysis Services.</span></span> <span data-ttu-id="83cf3-124">SQL Server Management Studio 是可选组件。</span><span class="sxs-lookup"><span data-stu-id="83cf3-124">SQL Server Management Studio is an optional component.</span></span> <span data-ttu-id="83cf3-125">如果你在 Windows Server 2012 的应用程序页面上未看见该组件与其他 SQL Server 应用程序一并列出，则运行 SQL Server 安装程序，将其添加到你的安装中。</span><span class="sxs-lookup"><span data-stu-id="83cf3-125">If you don't see it with other SQL Server applications on the Apps page in Windows Server 2012, run SQL Server Setup to add it to your installation.</span></span>

### <a name="sql-server-profiler"></a><span data-ttu-id="83cf3-126">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="83cf3-126">SQL Server Profiler</span></span>
 <span data-ttu-id="83cf3-127">SQL Server Profiler 提供一种便捷方法，用以监视连接、MDX 查询执行和其他服务器操作，但从官方角度来说，不推荐使用此方法。</span><span class="sxs-lookup"><span data-stu-id="83cf3-127">Although it's officially deprecated, SQL Server Profiler provides an easy way to monitor connections, MDX query execution, and other server operations.</span></span> <span data-ttu-id="83cf3-128">SQL Server Profiler 将按默认安装。</span><span class="sxs-lookup"><span data-stu-id="83cf3-128">SQL Server Profiler is installed by default.</span></span> <span data-ttu-id="83cf3-129">可在 Windows Server 2012 中的应用程序上一并找到此组件与 SQL Server 应用程序。</span><span class="sxs-lookup"><span data-stu-id="83cf3-129">You can find it with SQL Server applications on Apps in Windows Server 2012.</span></span>

### <a name="powershell"></a><span data-ttu-id="83cf3-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="83cf3-130">PowerShell</span></span>
 <span data-ttu-id="83cf3-131">可以使用 PowerShell 命令执行许多管理任务。</span><span class="sxs-lookup"><span data-stu-id="83cf3-131">You can use PowerShell commands to perform many administrative tasks.</span></span> <span data-ttu-id="83cf3-132">有关详细信息，请参阅 [Analysis Services PowerShell](analysis-services-powershell.md) 。</span><span class="sxs-lookup"><span data-stu-id="83cf3-132">See [Analysis Services PowerShell](analysis-services-powershell.md) for more information.</span></span>

### <a name="community-and-third-party-tools"></a><span data-ttu-id="83cf3-133">社区和第三方工具</span><span class="sxs-lookup"><span data-stu-id="83cf3-133">Community and Third-party tools</span></span>
 <span data-ttu-id="83cf3-134">检查 [Analysis Services codeplex 页面](https://sqlsrvanalysissrvcs.codeplex.com/) 是否具有社区代码示例。</span><span class="sxs-lookup"><span data-stu-id="83cf3-134">Check the [Analysis Services codeplex page](https://sqlsrvanalysissrvcs.codeplex.com/) for community code samples.</span></span> <span data-ttu-id="83cf3-135">为支持 Analysis Services 的第三方工具查找建议时，[论坛](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices)非常有用。</span><span class="sxs-lookup"><span data-stu-id="83cf3-135">[Forums](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) can be helpful when seeking recommendations for third-party tools that support Analysis Services.</span></span>
