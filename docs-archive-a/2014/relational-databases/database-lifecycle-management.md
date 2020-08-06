---
title: 数据库生命周期管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Data sync
- SQL Database
- Azure Training Kit
- Database development
- Database backup
- Database connection management
- Database community
- Backup and restore
- Database import and export
- SQL Data Sync
- Azure Service Dashboard
- SQL Server Management Studio
- Database management
- Database export
- SQL Server Data Tools
- SSMS
- SSDT
- Database migration
- Database connectivity
ms.assetid: 91da13a4-0eea-4e88-b608-dada881ff5f2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a2c469b23e1ce4134767920547297b23ec030cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589685"
---
# <a name="database-lifecycle-management"></a><span data-ttu-id="b7843-102">数据库生命周期管理</span><span class="sxs-lookup"><span data-stu-id="b7843-102">Database Lifecycle Management</span></span>
  <span data-ttu-id="b7843-103">数据库生命周期管理 (DLM) 是一种基于策略的方法，用于管理数据库和数据资产。</span><span class="sxs-lookup"><span data-stu-id="b7843-103">Database lifecycle management (DLM) is a policy-based approach to managing databases and data assets.</span></span> <span data-ttu-id="b7843-104">DLM 不是一种产品而是管理数据库应用程序的数据库架构、 数据和元数据的一套全面的方法。</span><span class="sxs-lookup"><span data-stu-id="b7843-104">DLM is not a product but a comprehensive approach to managing the database schema, data, and metadata for a database application.</span></span> <span data-ttu-id="b7843-105">拥有周密、积极主动的 DLM 方法，组织可以根据相应的性能、保护、可用性和成本的级别来管理数据资源。</span><span class="sxs-lookup"><span data-stu-id="b7843-105">A thoughtful and proactive approach to DLM enables an organization to manage data resources according to appropriate levels of performance, protection, availability, and cost.</span></span>  
  
 <span data-ttu-id="b7843-106">DLM 从项目设计和意图的讨论开始，接着进行数据库开发、测试、生成、部署、维护、监视和备份活动，以数据存档结束。</span><span class="sxs-lookup"><span data-stu-id="b7843-106">DLM begins with discussion of project design and intent, continues with database develop, test, build, deploy, maintain, monitor, and backup activities, and ends with data archive.</span></span> <span data-ttu-id="b7843-107">本主题提供 DLM 各阶段的概述，它从数据库开发开始，接着执行生成、部署和监视操作（图 1）。</span><span class="sxs-lookup"><span data-stu-id="b7843-107">This topic provides an overview of the stages of DLM that begin with database development and progress through build, deploy, and monitor actions (Figure 1).</span></span> <span data-ttu-id="b7843-108">此外还包括数据管理活动以及数据迁移操作（如导入/导出、备份、迁移和同步）。</span><span class="sxs-lookup"><span data-stu-id="b7843-108">Also included are data management activities, and data portability operations like import/export, backup, migrate, and sync.</span></span>  
  
 <span data-ttu-id="b7843-109">要查看完整主题，请参阅 [数据库生命周期管理 (DLM)](https://go.microsoft.com/fwlink/?LinkId=276949)。</span><span class="sxs-lookup"><span data-stu-id="b7843-109">To read the complete topic, see [Database Lifecycle Management (DLM)](https://go.microsoft.com/fwlink/?LinkId=276949).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7843-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7843-110">See Also</span></span>  
 <span data-ttu-id="b7843-111">[Azure 主页](https://www.windowsazure.com/) </span><span class="sxs-lookup"><span data-stu-id="b7843-111">[Azure Home Page](https://www.windowsazure.com/) </span></span>  
 <span data-ttu-id="b7843-112">[Azure 开发人员中心](https://www.windowsazure.com/develop/overview/) </span><span class="sxs-lookup"><span data-stu-id="b7843-112">[Azure Developer Center](https://www.windowsazure.com/develop/overview/) </span></span>  
 <span data-ttu-id="b7843-113">[Azure 管理中心](https://www.windowsazure.com/manage/overview/) </span><span class="sxs-lookup"><span data-stu-id="b7843-113">[Azure Manage Center](https://www.windowsazure.com/manage/overview/) </span></span>  
 <span data-ttu-id="b7843-114">[Azure 团队博客](https://www.windowsazure.com/community/blog/) </span><span class="sxs-lookup"><span data-stu-id="b7843-114">[Azure Team Blog](https://www.windowsazure.com/community/blog/) </span></span>  
 [<span data-ttu-id="b7843-115">Azure 支持选项</span><span class="sxs-lookup"><span data-stu-id="b7843-115">Azure Support Options</span></span>](https://www.windowsazure.com/support/contact/)  
  
