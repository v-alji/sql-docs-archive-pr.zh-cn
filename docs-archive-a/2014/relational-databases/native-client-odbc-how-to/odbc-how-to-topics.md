---
title: ODBC 操作指南主题 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 151f2066-1c37-410f-88f4-b27dfca66031
author: rothja
ms.author: jroth
ms.openlocfilehash: cfeb120b9fa1fedb5358b5e12dabed7835f9a6b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692381"
---
# <a name="odbc-how-to-topics"></a><span data-ttu-id="164d7-102">ODBC 操作指南主题</span><span class="sxs-lookup"><span data-stu-id="164d7-102">ODBC How-to Topics</span></span>
  <span data-ttu-id="164d7-103">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] odbc 驱动程序，您必须能够创建 odbc 数据源并确保服务器具有正确的目录存储过程版本。</span><span class="sxs-lookup"><span data-stu-id="164d7-103">To use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver, you must be able to create ODBC data sources and ensure that the server has the correct version of the catalog stored procedures.</span></span> <span data-ttu-id="164d7-104">若要为使用 SQL Server 的 ODBC 应用程序编码，您必须了解如何分配 ODBC 句柄、设置属性、连接到 SQL Server 实例、执行查询和处理结果。</span><span class="sxs-lookup"><span data-stu-id="164d7-104">To code an ODBC application that uses SQL Server, you must know how to allocate ODBC handles, set attributes, connect to an instance of SQL Server, execute queries, and process results.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="164d7-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="164d7-105">In This Section</span></span>  
  
-   [<span data-ttu-id="164d7-106">配置 SQL Server ODBC 驱动程序操作指南主题</span><span class="sxs-lookup"><span data-stu-id="164d7-106">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
-   [<span data-ttu-id="164d7-107">分配句柄并连接到 SQL Server &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="164d7-107">Allocate Handles and Connect to SQL Server &#40;ODBC&#41;</span></span>](allocate-handles-and-connect-to-sql-server-odbc.md)  
  
-   [<span data-ttu-id="164d7-108">&#40;ODBC&#41;执行查询操作指南主题</span><span class="sxs-lookup"><span data-stu-id="164d7-108">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](execute-queries/executing-queries-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="164d7-109">处理结果操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="164d7-109">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="164d7-110">使用游标操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="164d7-110">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](cursors/using-cursors-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="164d7-111">使用 Microsoft 分布式事务处理协调器 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="164d7-111">Use Microsoft Distributed Transaction Coordinator &#40;ODBC&#41;</span></span>](use-microsoft-distributed-transaction-coordinator-odbc.md)  
  
-   [<span data-ttu-id="164d7-112">运行存储过程操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="164d7-112">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="164d7-113">管理文本和图像列操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="164d7-113">Managing text and image Columns How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/managing-text-and-image-columns-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="164d7-114">分析 ODBC 驱动程序性能操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="164d7-114">Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-odbc.md)  
  
-   [<span data-ttu-id="164d7-115">&#40;ODBC&#41;处理 ODBC 错误</span><span class="sxs-lookup"><span data-stu-id="164d7-115">Process ODBC Errors &#40;ODBC&#41;</span></span>](process-odbc-errors-odbc.md)  
  
-   [<span data-ttu-id="164d7-116">SQL Server ODBC 驱动程序的大容量复制操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="164d7-116">Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;</span></span>](bulk-copy/bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="164d7-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="164d7-117">See Also</span></span>  
 [<span data-ttu-id="164d7-118">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="164d7-118">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
