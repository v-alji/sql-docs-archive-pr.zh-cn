---
title: 卸载 SQL Server 2014 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e6255f8e-a25e-4b3d-9310-c5da2f9c9333
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e72f153c28a1ccd827150eb3dddc0b52321518a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586129"
---
# <a name="uninstall-sql-server-2014"></a><span data-ttu-id="dd251-102">卸载 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="dd251-102">Uninstall SQL Server 2014</span></span>
  <span data-ttu-id="dd251-103">按照下面的主题执行可以完全卸载 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的现有实例，并且对系统进行准备以便您可以重新安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dd251-103">Follow the topics below to uninstall an existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] completely, and prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd251-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="dd251-104">In This Section</span></span>  
 [<span data-ttu-id="dd251-105">卸载现有 SQL Server 实例（安装程序）</span><span class="sxs-lookup"><span data-stu-id="dd251-105">Uninstall an Existing Instance of SQL Server &#40;Setup&#41;</span></span>](uninstall-an-existing-instance-of-sql-server-setup.md)  
 <span data-ttu-id="dd251-106">本主题介绍如何手动卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的独立实例。</span><span class="sxs-lookup"><span data-stu-id="dd251-106">This topic describes how to manually uninstall a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="dd251-107">卸载 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="dd251-107">Uninstall PowerPivot for SharePoint</span></span>](uninstall-power-pivot-for-sharepoint.md)  
 <span data-ttu-id="dd251-108">本主题介绍如何手动卸载 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="dd251-108">This topic describes how to manually uninstall PowerPivot for SharePoint.</span></span>  
  
 [<span data-ttu-id="dd251-109">卸载 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="dd251-109">Uninstall Reporting Services</span></span>](uninstall-reporting-services.md)  
 <span data-ttu-id="dd251-110">本主题介绍如何为 SharePoint 模式和本机模式服务器卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="dd251-110">This topic describes how to uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers for both SharePoint mode and Native mode servers.</span></span>  
  
 [<span data-ttu-id="dd251-111">卸载和删除 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="dd251-111">Uninstall and Remove Master Data Services</span></span>](uninstall-and-remove-master-data-services.md)  
 <span data-ttu-id="dd251-112">本主题介绍从本地计算机卸载和删除 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 的过程。</span><span class="sxs-lookup"><span data-stu-id="dd251-112">This topic describes the process of uninstalling and removing [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] from the local computer.</span></span>  
  
 [<span data-ttu-id="dd251-113">删除数据质量服务器对象</span><span class="sxs-lookup"><span data-stu-id="dd251-113">Remove Data Quality Server Objects</span></span>](remove-data-quality-server-objects.md)  
 <span data-ttu-id="dd251-114">本主题介绍如何在卸载 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 或者仅卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (DQS) 中的 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 组件后手动删除 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="dd251-114">This topic describes how to manually remove the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] objects after uninstalling either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or just the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] component in [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dd251-115">相关章节</span><span class="sxs-lookup"><span data-stu-id="dd251-115">Related Sections</span></span>  
  
-   [<span data-ttu-id="dd251-116">删除 SQL Server 故障转移群集实例（安装程序）</span><span class="sxs-lookup"><span data-stu-id="dd251-116">Remove a SQL Server Failover Cluster Instance &#40;Setup&#41;</span></span>](../failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)  
  
-   [<span data-ttu-id="dd251-117">在 SQL Server 故障转移群集中添加或删除节点（安装程序）</span><span class="sxs-lookup"><span data-stu-id="dd251-117">Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;</span></span>](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
-   [<span data-ttu-id="dd251-118">删除 SQL Server 2014 安装</span><span class="sxs-lookup"><span data-stu-id="dd251-118">Drop a SQL Server 2014 Installation</span></span>](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)  
  
## <a name="see-also"></a><span data-ttu-id="dd251-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd251-119">See Also</span></span>  
 <span data-ttu-id="dd251-120">[计划 SQL Server 安装](planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="dd251-120">[Planning a SQL Server Installation](planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="dd251-121">[安装 SQL Server 2014](../../database-engine/install-windows/install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dd251-121">[Install SQL Server 2014](../../database-engine/install-windows/install-sql-server.md) </span></span>  
 [<span data-ttu-id="dd251-122">升级到 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="dd251-122">Upgrade to SQL Server 2014</span></span>](../../database-engine/install-windows/upgrade-sql-server.md)  
  
  
