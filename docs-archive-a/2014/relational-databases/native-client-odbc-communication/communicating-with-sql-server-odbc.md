---
title: 与 SQL Server (ODBC) 通信 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: rothja
ms.author: jroth
ms.openlocfilehash: c41ac2dcce9c5bdbdd351148d16bcaa8f067d22f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692402"
---
# <a name="communicating-with-sql-server-odbc"></a><span data-ttu-id="b5fee-102">与 SQL Server 通信 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="b5fee-102">Communicating with SQL Server (ODBC)</span></span>
  <span data-ttu-id="b5fee-103">对于要与实例通信的 ODBC 应用程序 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，它必须分配环境和连接句柄并连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="b5fee-103">For an ODBC application to communicate with an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it must allocate environment and connection handles and connect to the data source.</span></span> <span data-ttu-id="b5fee-104">在建立连接后，应用程序可以向服务器发送查询并处理任意结果集。</span><span class="sxs-lookup"><span data-stu-id="b5fee-104">After a connection is established, the application can send queries to the server and process any result sets.</span></span> <span data-ttu-id="b5fee-105">应用程序使用完数据源后，它断开与数据源的连接并释放连接句柄。</span><span class="sxs-lookup"><span data-stu-id="b5fee-105">When the application has finished using the data source, it disconnects from the data source and frees the connection handle.</span></span> <span data-ttu-id="b5fee-106">应用程序释放所有连接句柄后，将释放环境句柄。</span><span class="sxs-lookup"><span data-stu-id="b5fee-106">When the application has freed all its connection handles, it frees the environment handle.</span></span>  
  
 <span data-ttu-id="b5fee-107">一个应用程序可以与任意数目的数据源连接。</span><span class="sxs-lookup"><span data-stu-id="b5fee-107">An application can connect to any number of data sources.</span></span> <span data-ttu-id="b5fee-108">该应用程序可以使用多个驱动程序和多个数据源的组合、同一驱动程序和多个数据源的组合，甚至可以使用同一驱动程序和指向同一数据源的多个连接。</span><span class="sxs-lookup"><span data-stu-id="b5fee-108">The application can use a combination of drivers and data sources, the same driver and a combination of data sources, or even the same driver and multiple connections to the same data source.</span></span>  
  
 <span data-ttu-id="b5fee-109">你可以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 从 MSDN 上的[SQL Server 下载](https://go.microsoft.com/fwlink/?LinkId=62796)"页下载 Native Client ODBC 示例。</span><span class="sxs-lookup"><span data-stu-id="b5fee-109">You can download [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC samples from the [SQL Server Downloads](https://go.microsoft.com/fwlink/?LinkId=62796) page on MSDN.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5fee-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="b5fee-110">In This Section</span></span>  
  
-   [<span data-ttu-id="b5fee-111">分配环境句柄</span><span class="sxs-lookup"><span data-stu-id="b5fee-111">Allocating an Environment Handle</span></span>](allocating-an-environment-handle.md)  
  
-   [<span data-ttu-id="b5fee-112">分配连接句柄</span><span class="sxs-lookup"><span data-stu-id="b5fee-112">Allocating a Connection Handle</span></span>](allocating-a-connection-handle.md)  
  
-   [<span data-ttu-id="b5fee-113">SQL Server Native Client ODBC 数据源</span><span class="sxs-lookup"><span data-stu-id="b5fee-113">SQL Server Native Client ODBC Data Sources</span></span>](../../integration-services/connection-manager/data-sources.md)  
  
-   [<span data-ttu-id="b5fee-114">&#40;ODBC 连接到数据源&#41;</span><span class="sxs-lookup"><span data-stu-id="b5fee-114">Connecting to a Data Source &#40;ODBC&#41;</span></span>](connecting-to-a-data-source-odbc.md)  
  
-   [<span data-ttu-id="b5fee-115">与数据源断开连接</span><span class="sxs-lookup"><span data-stu-id="b5fee-115">Disconnecting from a Data Source</span></span>](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5fee-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5fee-116">See Also</span></span>  
 <span data-ttu-id="b5fee-117">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="b5fee-117">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="b5fee-118">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="b5fee-118">SQLSetEnvAttr</span></span>](../native-client-odbc-api/sqlsetenvattr.md)  
  
  
