---
title: SQL Server 数据库引擎 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server]
- SQL Server Database Engine
ms.assetid: 65e2f424-1386-45a6-8912-bd053f434073
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a6c243115e940f7af085c0068d2ca5c277aa5162
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577806"
---
# <a name="sql-server-database-engine"></a><span data-ttu-id="9457e-102">SQL Server 数据库引擎</span><span class="sxs-lookup"><span data-stu-id="9457e-102">SQL Server Database Engine</span></span>
  <span data-ttu-id="9457e-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] 是用于存储、处理和保护数据的核心服务。</span><span class="sxs-lookup"><span data-stu-id="9457e-103">The [!INCLUDE[ssDE](../includes/ssde-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="9457e-104">利用 [!INCLUDE[ssDE](../includes/ssde-md.md)] 可控制访问权限并快速处理事务，从而满足企业内要求极高而且需要处理大量数据的应用需要。</span><span class="sxs-lookup"><span data-stu-id="9457e-104">The [!INCLUDE[ssDE](../includes/ssde-md.md)] provides controlled access and rapid transaction processing to meet the requirements of the most demanding data consuming applications within your enterprise.</span></span>

 <span data-ttu-id="9457e-105">使用 [!INCLUDE[ssDE](../includes/ssde-md.md)] 创建用于联机事务处理或联机分析处理数据的关系数据库。</span><span class="sxs-lookup"><span data-stu-id="9457e-105">Use the [!INCLUDE[ssDE](../includes/ssde-md.md)] to create relational databases for online transaction processing or online analytical processing data.</span></span> <span data-ttu-id="9457e-106">这包括创建用于存储数据的表和用于查看、管理和保护数据安全的数据库对象（如索引、视图和存储过程）。</span><span class="sxs-lookup"><span data-stu-id="9457e-106">This includes creating tables for storing data, and database objects such as indexes, views, and stored procedures for viewing, managing, and securing data.</span></span> <span data-ttu-id="9457e-107">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 管理数据库对象，使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 捕获服务器事件。</span><span class="sxs-lookup"><span data-stu-id="9457e-107">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to manage the database objects, and [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to capture server events.</span></span>

 <span data-ttu-id="9457e-108">**按区域浏览内容**![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标")[新增功能 (数据库引擎) ](whats-new-in-sql-server-2016.md)</span><span class="sxs-lookup"><span data-stu-id="9457e-108">**Browse Content by Area** ![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [What's New (Database Engine)](whats-new-in-sql-server-2016.md)</span></span>

 <span data-ttu-id="9457e-109">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标") [SQL Server 数据库引擎向后兼容性](sql-server-database-engine-backward-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="9457e-109">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [SQL Server Database Engine Backward Compatibility](sql-server-database-engine-backward-compatibility.md)</span></span>

 <span data-ttu-id="9457e-110">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标") [SQL Server 管理工具向后兼容性](../../2014/database-engine/sql-server-management-tools-backward-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="9457e-110">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [SQL Server Management Tools Backward Compatibility](../../2014/database-engine/sql-server-management-tools-backward-compatibility.md)</span></span>

 <span data-ttu-id="9457e-111">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标")[数据库功能和任务](../../2014/database-engine/database-engine-features-and-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="9457e-111">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Database Features and Tasks](../../2014/database-engine/database-engine-features-and-tasks.md)</span></span>

 <span data-ttu-id="9457e-112">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标")[技术参考](../../2014/database-engine/technical-reference-database-engine.md)</span><span class="sxs-lookup"><span data-stu-id="9457e-112">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Technical Reference](../../2014/database-engine/technical-reference-database-engine.md)</span></span>

 <span data-ttu-id="9457e-113">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标") [transact-sql 参考](/sql/t-sql/language-reference)</span><span class="sxs-lookup"><span data-stu-id="9457e-113">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Transact-SQL Reference](/sql/t-sql/language-reference)</span></span>

 <span data-ttu-id="9457e-114">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标") [XQuery 引用](/sql/xquery/xquery-language-reference-sql-server)</span><span class="sxs-lookup"><span data-stu-id="9457e-114">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [XQuery Reference](/sql/xquery/xquery-language-reference-sql-server)</span></span>

## <a name="see-also"></a><span data-ttu-id="9457e-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9457e-115">See Also</span></span>
 [<span data-ttu-id="9457e-116">SQL Server 资源中心</span><span class="sxs-lookup"><span data-stu-id="9457e-116">SQL Server Resource Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=219676)


