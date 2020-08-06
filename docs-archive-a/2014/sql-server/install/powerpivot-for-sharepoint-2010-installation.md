---
title: PowerPivot for SharePoint 2010 安装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 8d47dde7-c941-4280-a934-e2fe3f9a938f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ba04dfdc69b1c510a800c062586e45f8873c8e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589414"
---
# <a name="powerpivot-for-sharepoint-2010-installation"></a><span data-ttu-id="6569c-102">PowerPivot for SharePoint 2010 安装</span><span class="sxs-lookup"><span data-stu-id="6569c-102">PowerPivot for SharePoint 2010 Installation</span></span>
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] <span data-ttu-id="6569c-103">是为您发布到 SharePoint 的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 工作簿提供查询处理和管理控制的服务器组件的集合。</span><span class="sxs-lookup"><span data-stu-id="6569c-103">is a collection of server components that provide query processing and management control over [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks that you publish to SharePoint.</span></span> <span data-ttu-id="6569c-104">组件包括 Analysis Services 引擎和 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系统服务。</span><span class="sxs-lookup"><span data-stu-id="6569c-104">Services include the Analysis Services engine and [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6569c-105">有关 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以及与 SharePoint Server 2013 的安装的信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="6569c-105">For information regarding [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] and installation with SharePoint Server 2013, see the following:</span></span>  
>   
>  -   <span data-ttu-id="6569c-106">[SQL Server 服务安装概述](../../../2014/sql-server/install/overview-of-sql-server-servicing-installation.md)的 "SQL SERVER 2012 SP1" 部分。</span><span class="sxs-lookup"><span data-stu-id="6569c-106">The "SQL Server 2012 SP1" section of [Overview of SQL Server Servicing Installation](../../../2014/sql-server/install/overview-of-sql-server-servicing-installation.md).</span></span>  
  
 <span data-ttu-id="6569c-107">Analysis Services 为包含 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 数据的 Excel 工作簿提供服务器端处理。</span><span class="sxs-lookup"><span data-stu-id="6569c-107">Analysis Services provides server-side processing for Excel workbooks that contain [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data.</span></span> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="6569c-108">系统服务与 Analysis Services 一起工作，从而添加 SharePoint 集成、负载平衡和连接管理。</span><span class="sxs-lookup"><span data-stu-id="6569c-108">System Service works alongside Analysis Services, adding SharePoint integration, load balancing and connection management.</span></span> [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]<span data-ttu-id="6569c-109">通过将其大型数据处理能力与 Excel 提供的数据呈现服务相结合来扩展 Excel Services。</span><span class="sxs-lookup"><span data-stu-id="6569c-109">extends Excel Services by pairing its large scale data processing capability with the data rendering services that Excel provides.</span></span>  
  
 <span data-ttu-id="6569c-110">若要安装 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]，请使用 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 安装介质。</span><span class="sxs-lookup"><span data-stu-id="6569c-110">To install [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], use the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]installation media.</span></span>  
  
 <span data-ttu-id="6569c-111">有关高级部署方案的说明，请参阅[部署清单： Reporting Services、Power View 和 PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)和[部署清单：通过将 PowerPivot 服务器添加到 SharePoint 2010 场进行扩展](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)。</span><span class="sxs-lookup"><span data-stu-id="6569c-111">For instructions on advanced deployment scenarios, see [Deployment Checklist: Reporting Services, Power View, and PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) and [Deployment Checklist: Scale-out by adding PowerPivot Servers to a SharePoint 2010 farm](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6569c-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="6569c-112">In This Section</span></span>  
 [<span data-ttu-id="6569c-113">安装 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="6569c-113">Install PowerPivot for SharePoint 2010</span></span>](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)  
  
 [<span data-ttu-id="6569c-114">在 SharePoint 服务器上安装 Analysis Services OLE DB 访问接口</span><span class="sxs-lookup"><span data-stu-id="6569c-114">Install the Analysis Services OLE DB Provider on SharePoint Servers</span></span>](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 [<span data-ttu-id="6569c-115">在运行管理中心的 Web 前端服务器上安装 ADOMD.NET</span><span class="sxs-lookup"><span data-stu-id="6569c-115">Install ADOMD.NET on Web Front-End Servers Running Central Administration</span></span>](../../../2014/sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)  
  
 [<span data-ttu-id="6569c-116">安装 ADO.NET Data Services 以支持 SharePoint 列表的数据馈送导出</span><span class="sxs-lookup"><span data-stu-id="6569c-116">Install ADO.NET Data Services to support data feed exports of SharePoint lists</span></span>](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md)  
  
 [<span data-ttu-id="6569c-117">从命令提示符安装 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="6569c-117">Install PowerPivot from the Command Prompt</span></span>](../../../2014/sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
 [<span data-ttu-id="6569c-118">卸载 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="6569c-118">Uninstall PowerPivot for SharePoint</span></span>](../../../2014/sql-server/install/uninstall-power-pivot-for-sharepoint.md)  
  
 [<span data-ttu-id="6569c-119">修复 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="6569c-119">Repair PowerPivot for SharePoint</span></span>](../../../2014/sql-server/install/repair-powerpivot-for-sharepoint.md)  
  
 [<span data-ttu-id="6569c-120">初始配置 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="6569c-120">Initial Configuration &#40;PowerPivot for SharePoint&#41;</span></span>](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
## <a name="see-also"></a><span data-ttu-id="6569c-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6569c-121">See Also</span></span>  
 [<span data-ttu-id="6569c-122">在管理中心中管理和配置 PowerPivot 服务器</span><span class="sxs-lookup"><span data-stu-id="6569c-122">PowerPivot Server Administration and Configuration in Central Administration</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)  
  
  
