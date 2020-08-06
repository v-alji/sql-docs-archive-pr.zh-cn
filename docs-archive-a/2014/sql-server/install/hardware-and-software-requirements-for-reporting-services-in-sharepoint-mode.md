---
title: SharePoint 模式下 Reporting Services 的硬件和软件要求 |Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a4fc19b2871d7d5731649c61a8d5231d7e3479dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590549"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="4e643-102">SharePoint 模式下的 Reporting Services 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="4e643-102">Hardware and Software Requirements for Reporting Services in SharePoint Mode</span></span>

  <span data-ttu-id="4e643-103">本主题介绍 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在 SharePoint 模式下运行的先决条件、硬件要求和安装注意事项。</span><span class="sxs-lookup"><span data-stu-id="4e643-103">This topic describes prerequisites, hardware requirements, and installation considerations for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] running in SharePoint mode.</span></span> <span data-ttu-id="4e643-104">因为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式需要 SharePoint 服务器，大多数要求均基于 SharePoint 环境。</span><span class="sxs-lookup"><span data-stu-id="4e643-104">Because [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode requires a SharePoint server, most of the requirements are based on the SharePoint environment.</span></span> <span data-ttu-id="4e643-105">对于本机模式的报表服务器，您的硬件应满足运行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的最低硬件和软件要求。</span><span class="sxs-lookup"><span data-stu-id="4e643-105">For native mode report servers, your hardware should meet minimum hardware and software requirements for running [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="4e643-106">有关详细信息，请参阅 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4e643-106">For more information, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="4e643-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="4e643-107">Prerequisites</span></span>](#bkmk_prereq)  
  
-   [<span data-ttu-id="4e643-108">报表服务器数据库要求</span><span class="sxs-lookup"><span data-stu-id="4e643-108">Report Server Database Requirements</span></span>](#bkmk_report_server_database)  
  
-   [<span data-ttu-id="4e643-109">Power View 要求</span><span class="sxs-lookup"><span data-stu-id="4e643-109">Power View Requirements</span></span>](#bkmk_powerview)  
  
-   [<span data-ttu-id="4e643-110">详细信息</span><span class="sxs-lookup"><span data-stu-id="4e643-110">More Information</span></span>](#bkmk_more_information)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="4e643-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="4e643-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="4e643-112">对于本地安装，在安装 SharePoint 和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 期间登录的帐户需要是本地操作系统 administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="4e643-112">For local installations, the account logged in during installation of SharePoint and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] needs to be a member of the administrators group in the local operating system.</span></span> <span data-ttu-id="4e643-113">该安装帐户不需要是 SharePoint 场 administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="4e643-113">The setup account does not need to be a member of the SharePoint farm administrators group.</span></span>  
  
     <span data-ttu-id="4e643-114">有关详细信息，请参阅 [SharePoint 2013 中的帐户权限和安全设置](https://technet.microsoft.com/library/cc678863.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4e643-114">For more information, see [Account permissions and security settings in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx).</span></span>  
  
-   <span data-ttu-id="4e643-115">在 SharePoint 模式下运行的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 要求 SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="4e643-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] running in SharePoint mode requires SharePoint Server.</span></span> <span data-ttu-id="4e643-116">有关 SharePoint 要求和配置的详细信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="4e643-116">For more information about SharePoint requirements and configurations, see the following:</span></span>  
  
    -   <span data-ttu-id="4e643-117">[ (SharePoint 2013) 的硬件和软件要求](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)</span><span class="sxs-lookup"><span data-stu-id="4e643-117">[Hardware and software requirements (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)</span></span>  
  
    -   [<span data-ttu-id="4e643-118">SharePoint Server 2013 的容量管理和大小调整</span><span class="sxs-lookup"><span data-stu-id="4e643-118">Capacity management and sizing for SharePoint Server 2013</span></span>](https://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [<span data-ttu-id="4e643-119">针对商业智能的软件要求 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="4e643-119">Software requirements for business intelligence (SharePoint 2013)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   <span data-ttu-id="4e643-120">[硬件和软件要求 (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))</span><span class="sxs-lookup"><span data-stu-id="4e643-120">[Hardware and software requirements (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))</span></span>  
  
    -   <span data-ttu-id="4e643-121">[SharePoint Server 2010 的容量管理和大小](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))</span><span class="sxs-lookup"><span data-stu-id="4e643-121">[Capacity management and sizing for SharePoint Server 2010](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))</span></span>  
  
-   <span data-ttu-id="4e643-122">如果要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 升级或更新现有 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]SharePoint 安装，请参阅 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)的最低硬件和软件要求。</span><span class="sxs-lookup"><span data-stu-id="4e643-122">If you want to upgrade or update existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint installation with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="4e643-123">验证是否已在 Windows 服务器管理器中启动 **“SharePoint 2013 管理”** 服务。</span><span class="sxs-lookup"><span data-stu-id="4e643-123">Verify the **SharePoint 2013 Administration** service is started in Windows Server Manager.</span></span>  
  
###  <a name="report-server-database-requirements"></a><a name="bkmk_report_server_database"></a><span data-ttu-id="4e643-124">报表服务器数据库要求</span><span class="sxs-lookup"><span data-stu-id="4e643-124">Report Server Database Requirements</span></span>  
  
-   <span data-ttu-id="4e643-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和 SharePoint 产品及技术均使用 SQL Server 关系数据库来存储应用程序数据。</span><span class="sxs-lookup"><span data-stu-id="4e643-125">Both [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and SharePoint products and technologies use SQL Server relational databases to store application data.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] <span data-ttu-id="4e643-126">需要兼容的 SQL Server 版本的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="4e643-126">requires an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] of a compatible SQL Server edition.</span></span> <span data-ttu-id="4e643-127">有关硬件和软件要求的详细信息，请参阅 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4e643-127">For more information on hardware and software requirements, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   <span data-ttu-id="4e643-128">SharePoint 产品可以使用现有的数据库实例。</span><span class="sxs-lookup"><span data-stu-id="4e643-128">SharePoint products can use an existing database instance.</span></span> <span data-ttu-id="4e643-129">如果未安装 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，则 SharePoint 产品安装程序将安装 SQL Server Express Edition 以用于 SharePoint 应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="4e643-129">If an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not installed, the SharePoint Products Setup program installs SQL Server Express Edition for the SharePoint application databases.</span></span>  
  
-   <span data-ttu-id="4e643-130">报表服务器实例不能将 SQL Server Express Edition 用于其数据库。</span><span class="sxs-lookup"><span data-stu-id="4e643-130">The report server instance cannot use the SQL Server Express Edition for its database.</span></span> <span data-ttu-id="4e643-131">但是，由 SharePoint 产品安装的 SQL Server Express Edition 实例可与其他数据库引擎版本并存。</span><span class="sxs-lookup"><span data-stu-id="4e643-131">However, the SQL Server Express Edition instance installed by the SharePoint product can exist side-by-side with other Database Engine editions.</span></span>  
  
##  <a name="sscrescent-requirements"></a><a name="bkmk_powerview"></a><span data-ttu-id="4e643-132">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]要求</span><span class="sxs-lookup"><span data-stu-id="4e643-132">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Requirements</span></span>

 <span data-ttu-id="4e643-133">查看 Office.Microsoft.com 上的最新 [Power View 文档](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="4e643-133">Review the most up-to-date [Power View documentation](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) on Office.Microsoft.com.</span></span> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="4e643-134">现在是 Microsoft Excel 2013 的一个功能，并且是 Microsoft SharePoint Server 2010 和 2013 Enterprise Edition 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services 外接程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e643-134">is a feature of Microsoft Excel 2013, and is part of the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services add-in for Microsoft SharePoint Server 2010 and 2013 Enterprise Editions.</span></span>  
  
##  <a name="more-information"></a><a name="bkmk_more_information"></a> <span data-ttu-id="4e643-135">详细信息</span><span class="sxs-lookup"><span data-stu-id="4e643-135">More Information</span></span>

 <span data-ttu-id="4e643-136">有关 SharePoint 更改的信息，请参阅[sharepoint 2010 到 sharepoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (的更改 https://technet.microsoft.com/library/ff607742(office.15).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="4e643-136">For information on SharePoint changes, see [Changes from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx).</span></span>  
  
 <span data-ttu-id="4e643-137">[SQL Server 2014 发行说明](https://go.microsoft.com/fwlink/?LinkID=296445)。</span><span class="sxs-lookup"><span data-stu-id="4e643-137">[SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
