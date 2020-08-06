---
title: 与2008和 2008 R2 报表服务器集成的 SharePoint |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9f51c37-b071-45d0-baec-f82fa6db366f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0b12429a520a674f4bc3ec7626bb3885fc33c814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687420"
---
# <a name="sharepoint-integration-with-2008-and-2008-r2--report-servers"></a><span data-ttu-id="f1705-102">SharePoint 与 2008 和 2008 R2 报表服务器集成</span><span class="sxs-lookup"><span data-stu-id="f1705-102">SharePoint Integration with 2008 and 2008 R2  Report Servers</span></span>
  <span data-ttu-id="f1705-103"> 的  版本引入了一种体系结构，在此体系结构中，SharePoint 模式现在基于 SharePoint 共享服务。</span><span class="sxs-lookup"><span data-stu-id="f1705-103">The [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] release of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] introduced a architecture where SharePoint mode is now based on a SharePoint Shared service.</span></span> <span data-ttu-id="f1705-104">新功能的管理已在 SharePoint 管理中心的 "**管理服务**和**管理器服务应用程序**" 页上完成。</span><span class="sxs-lookup"><span data-stu-id="f1705-104">Management of the new functionality is completed in SharePoint Central administration on the **Manage Services** and **Manager Service Applications** pages.</span></span> <span data-ttu-id="f1705-105">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]用于 sharepoint 2010 的外接程序仍支持早期的 Sharepoint 集成体系结构 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ，以便可以将 sharepoint 2010 与 Report Server 的早期版本相集成。</span><span class="sxs-lookup"><span data-stu-id="f1705-105">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] previous architecture for SharePoint Integration is still supported with the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint 2010 products so you can integrate SharePoint 2010 with previous versions of a report server.</span></span>  
  
 <span data-ttu-id="f1705-106">您将用于管理旧体系结构的“SharePoint 管理中心”页在以下位置提供：</span><span class="sxs-lookup"><span data-stu-id="f1705-106">SharePoint Central Administration pages you would use to administer the older architecture are found in the following:</span></span>  
  
1.  <span data-ttu-id="f1705-107">从 SharePoint 管理中心，单击 "**常规应用程序设置**"。</span><span class="sxs-lookup"><span data-stu-id="f1705-107">From SharePoint Central Administration click **General Application Settings**.</span></span>  
  
2.  <span data-ttu-id="f1705-108">组\*\*SQL Server Reporting Services (2008 和 2008 R2) \*\*包含旧体系结构的链接和管理页面</span><span class="sxs-lookup"><span data-stu-id="f1705-108">The group **SQL Server Reporting Services (2008 and 2008 R2)** contains the links and management pages for the older architecture</span></span>  
  
## <a name="server-integration-architecture"></a><span data-ttu-id="f1705-109">服务器集成体系结构</span><span class="sxs-lookup"><span data-stu-id="f1705-109">Server Integration Architecture</span></span>  
 <span data-ttu-id="f1705-110">将报表服务器与 SharePoint 产品的实例集成后，项和属性将存储在 SharePoint 内容数据库中。</span><span class="sxs-lookup"><span data-stu-id="f1705-110">When you integrate a report server with an instance of a SharePoint product, items and properties are stored in the SharePoint content databases.</span></span> <span data-ttu-id="f1705-111">这在影响内容存储、保护及访问方式的各种服务器技术之间提供了更深层次的集成。</span><span class="sxs-lookup"><span data-stu-id="f1705-111">This provides a deeper level of integration between the server technologies that effects how content is stored, secured, and accessed.</span></span>  
  
 <span data-ttu-id="f1705-112">将报表项和报表属性存储在 SharePoint 内容数据库中，您将可以执行以下操作：浏览 SharePoint 库中的报表服务器内容类型；使用相同的权限级别和身份验证提供程序（用于对位于 SharePoint 站点上的其他业务文档进行访问控制）来保护报表项；使用协作和文档管理功能签入和签出报表以供修改；使用警报查明是否已更改某个报表项；在应用程序的页面和站点中嵌入或自定义报表查看器 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="f1705-112">Storing report items and properties in SharePoint content databases allows you to browse SharePoint libraries for report server content types, secure items using the same permission levels and authentication provider that controls access to other business documents hosted on a SharePoint site, use the collaboration and document management features to check reports in and out for modification, use alerts to find out if an item has changed, and embed or customize the Report Viewer Web part on pages and sites within the application.</span></span> <span data-ttu-id="f1705-113">如果您在 SharePoint 站点中有足够的权限，则还可以从共享数据源生成报表模型并使用报表生成器来创建报表。</span><span class="sxs-lookup"><span data-stu-id="f1705-113">If you have sufficient permissions within a SharePoint site, you can also generate report models from shared data sources and use Report Builder to create reports.</span></span>  
  
 <span data-ttu-id="f1705-114">报表服务器仍然提供所有数据处理、呈现及传递功能。</span><span class="sxs-lookup"><span data-stu-id="f1705-114">The report server continues to provide all data processing, rendering, and delivery.</span></span> <span data-ttu-id="f1705-115">它还支持关于快照和报表历史记录的所有计划报表处理。</span><span class="sxs-lookup"><span data-stu-id="f1705-115">It also supports all scheduled report processing for snapshots and report history.</span></span> <span data-ttu-id="f1705-116">从 SharePoint 站点打开报表时，报表服务器端点将依次执行以下操作：连接到报表服务器、创建会话、准备处理该报表、检索数据、将该报表合并到报表布局中、在报表查看器 Web 部件中显示该报表。</span><span class="sxs-lookup"><span data-stu-id="f1705-116">When you open a report from a SharePoint site, the Report Server endpoint connects to a report server, creates a session, prepares the report for processing, retrieves data, merges the report into the report layout, and displays it in the Report Viewer Web part.</span></span> <span data-ttu-id="f1705-117">在报表处于打开状态时，可以将报表导出为不同的应用程序格式，还可以通过深入到报表下层或一直单击到相关报表的方式实现数据交互。</span><span class="sxs-lookup"><span data-stu-id="f1705-117">While the report is open, you can export it to different application formats, or interact with data by drilling into underlying numbers or clicking through to a related report.</span></span> <span data-ttu-id="f1705-118">导出和报表交互操作均在报表服务器上进行。</span><span class="sxs-lookup"><span data-stu-id="f1705-118">Export and report interaction operations are performed on the report server.</span></span>  
  
 <span data-ttu-id="f1705-119">报表服务器与 SharePoint 进行操作和数据的同步并跟踪报表服务器所处理文件的有关信息。</span><span class="sxs-lookup"><span data-stu-id="f1705-119">The report server synchronizes operations and data with SharePoint and tracks information about the files it processes.</span></span> <span data-ttu-id="f1705-120">修改任何报表服务器项的属性或设置时，改动将存储在 SharePoint 数据库中，然后被复制到向报表服务器提供内部存储的报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="f1705-120">When you modify properties or settings for any report server item, the change is stored in a SharePoint database and then copied to a report server database that provides internal storage to a report server.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="f1705-121">相关内容</span><span class="sxs-lookup"><span data-stu-id="f1705-121">Related Content</span></span>  
 [<span data-ttu-id="f1705-122">在 SharePoint 中激活报表服务器和 Power View 集成功能</span><span class="sxs-lookup"><span data-stu-id="f1705-122">Activate the Report Server and Power View Integration Features in SharePoint</span></span>](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  
 <span data-ttu-id="f1705-123">描述如何激活与以前版本的报表服务器集成所需的报表服务器功能。</span><span class="sxs-lookup"><span data-stu-id="f1705-123">Describes how to activate the Report Server feature needed for integration with report servers from previous releases.</span></span>  
  
  
