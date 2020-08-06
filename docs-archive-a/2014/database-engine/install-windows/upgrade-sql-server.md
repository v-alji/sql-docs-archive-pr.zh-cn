---
title: 升级到 SQL Server 2014 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
ms.assetid: 5064e35b-b70d-4a0b-a9e9-fff04162f9d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 857bbd6d7269b7675653b11a9d7c0acd07927f62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689017"
---
# <a name="upgrade-to-sql-server-2014"></a><span data-ttu-id="9f08a-102">升级到 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="9f08a-102">Upgrade to SQL Server 2014</span></span>
  <span data-ttu-id="9f08a-103">您可以将 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 实例升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9f08a-103">You can upgrade instances of, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9f08a-104">在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序以升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]前，查看 [SQL Server 2014 升级技术指南](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf) （PDF 下载），查看此节中有关升级过程的主题，然后阅读 [SQL Server 2014 发布说明](https://go.microsoft.com/fwlink/?LinkID=296445)。</span><span class="sxs-lookup"><span data-stu-id="9f08a-104">Before running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], check out the [SQL Server 2014 Upgrade Technical Guide](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf) (PDF download), review the topics about the upgrade process in this section, and read the [SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f08a-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="9f08a-105">In This Section</span></span>  
 <span data-ttu-id="9f08a-106">本部分包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="9f08a-106">This section contains the following topics:</span></span>  
  
-   [<span data-ttu-id="9f08a-107">支持的版本和版本升级</span><span class="sxs-lookup"><span data-stu-id="9f08a-107">Supported Version and Edition Upgrades</span></span>](supported-version-and-edition-upgrades.md)  
  
-   [<span data-ttu-id="9f08a-108">使用升级顾问来准备升级</span><span class="sxs-lookup"><span data-stu-id="9f08a-108">Use Upgrade Advisor to Prepare for Upgrades</span></span>](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
-   [<span data-ttu-id="9f08a-109">使用 Distributed Replay 实用工具准备升级</span><span class="sxs-lookup"><span data-stu-id="9f08a-109">Use the Distributed Replay Utility to Prepare for Upgrades</span></span>](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)  
  
-   [<span data-ttu-id="9f08a-110">升级 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="9f08a-110">Upgrade Analysis Services</span></span>](upgrade-analysis-services.md)  
  
-   [<span data-ttu-id="9f08a-111">升级数据库引擎</span><span class="sxs-lookup"><span data-stu-id="9f08a-111">Upgrade Database Engine</span></span>](upgrade-database-engine.md)  
  
-   [<span data-ttu-id="9f08a-112">升级 Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="9f08a-112">Upgrade Data Quality Services</span></span>](upgrade-data-quality-services.md)  
  
-   [<span data-ttu-id="9f08a-113">升级 Integration Services</span><span class="sxs-lookup"><span data-stu-id="9f08a-113">Upgrade Integration Services</span></span>](../../integration-services/install-windows/upgrade-integration-services.md)  
  
-   [<span data-ttu-id="9f08a-114">升级 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="9f08a-114">Upgrade Master Data Services</span></span>](upgrade-master-data-services.md)  
  
-   [<span data-ttu-id="9f08a-115">升级 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="9f08a-115">Upgrade PowerPivot for SharePoint</span></span>](upgrade-power-pivot-for-sharepoint.md)  
  
-   [<span data-ttu-id="9f08a-116">升级复制的数据库</span><span class="sxs-lookup"><span data-stu-id="9f08a-116">Upgrade Replicated Databases</span></span>](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
-   [<span data-ttu-id="9f08a-117">升级和迁移 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="9f08a-117">Upgrade and Migrate Reporting Services</span></span>](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)  
  
-   [<span data-ttu-id="9f08a-118">升级 SQL Server 管理工具</span><span class="sxs-lookup"><span data-stu-id="9f08a-118">Upgrade SQL Server Management Tools</span></span>](upgrade-sql-server-management-tools.md)  
  
-   [<span data-ttu-id="9f08a-119">升级操作指南主题</span><span class="sxs-lookup"><span data-stu-id="9f08a-119">Upgrade How-to Topics</span></span>](../../../2014/sql-server/install/upgrade-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="9f08a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f08a-120">See Also</span></span>  
 <span data-ttu-id="9f08a-121">[升级数据库引擎](upgrade-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="9f08a-121">[Upgrade Database Engine](upgrade-database-engine.md) </span></span>  
 <span data-ttu-id="9f08a-122">[升级 Analysis Services](upgrade-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9f08a-122">[Upgrade Analysis Services](upgrade-analysis-services.md) </span></span>  
 <span data-ttu-id="9f08a-123">[升级和迁移 Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="9f08a-123">[Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span></span>  
 <span data-ttu-id="9f08a-124">[升级 Integration Services](../../integration-services/install-windows/upgrade-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="9f08a-124">[Upgrade Integration Services](../../integration-services/install-windows/upgrade-integration-services.md) </span></span>  
 <span data-ttu-id="9f08a-125">[升级复制的数据库](../../database-engine/install-windows/upgrade-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="9f08a-125">[Upgrade Replicated Databases](../../database-engine/install-windows/upgrade-replicated-databases.md) </span></span>  
 <span data-ttu-id="9f08a-126">[升级 Master Data Services](upgrade-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9f08a-126">[Upgrade Master Data Services](upgrade-master-data-services.md) </span></span>  
 <span data-ttu-id="9f08a-127">[SQL Server 2012 最佳做法分析器](https://www.microsoft.com/download/details.aspx?id=29302) </span><span class="sxs-lookup"><span data-stu-id="9f08a-127">[SQL Server 2012 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=29302) </span></span>  
 <span data-ttu-id="9f08a-128">[SQL Server 2008 R2 最佳做法分析器](https://www.microsoft.com/download/details.aspx?id=436) </span><span class="sxs-lookup"><span data-stu-id="9f08a-128">[SQL Server 2008 R2 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=436) </span></span>  
 [<span data-ttu-id="9f08a-129">向后兼容性</span><span class="sxs-lookup"><span data-stu-id="9f08a-129">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
