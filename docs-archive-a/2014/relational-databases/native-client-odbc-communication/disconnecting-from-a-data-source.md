---
title: 断开与数据源的连接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
author: rothja
ms.author: jroth
ms.openlocfilehash: 5db3b83ab65d854f3a4d2182d9a4a1314e097681
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586644"
---
# <a name="disconnecting-from-a-data-source"></a><span data-ttu-id="499b1-102">与数据源断开连接</span><span class="sxs-lookup"><span data-stu-id="499b1-102">Disconnecting from a Data Source</span></span>
  <span data-ttu-id="499b1-103">当应用程序使用完数据源后，它将调用**SQLDisconnect**。</span><span class="sxs-lookup"><span data-stu-id="499b1-103">When an application has finished using a data source, it calls **SQLDisconnect**.</span></span> <span data-ttu-id="499b1-104">**SQLDisconnect**释放在连接上分配的所有语句，并断开驱动程序与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="499b1-104">**SQLDisconnect** frees any statements that are allocated on the connection and disconnects the driver from the data source.</span></span> <span data-ttu-id="499b1-105">断开连接后，应用程序可以调用[SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md)来释放连接句柄。</span><span class="sxs-lookup"><span data-stu-id="499b1-105">After disconnecting, the application can call [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) to free the connection handle.</span></span> <span data-ttu-id="499b1-106">在退出之前，应用程序还会调用**SQLFreeHandle**来释放环境句柄。</span><span class="sxs-lookup"><span data-stu-id="499b1-106">Before exiting, an application also calls **SQLFreeHandle** to free the environment handle.</span></span>  
  
 <span data-ttu-id="499b1-107">断开连接后，应用程序可以重用分配的连接句柄，以连接到其他数据源或重新连接到同一个数据源。</span><span class="sxs-lookup"><span data-stu-id="499b1-107">After disconnecting, an application can reuse the allocated connection handle, either to connect to a different data source or reconnect to the same data source.</span></span> <span data-ttu-id="499b1-108">如果决定保持连接，而不是断开连接后重新连接，则要求应用程序编写人员考虑每种选择的相对成本。</span><span class="sxs-lookup"><span data-stu-id="499b1-108">The decision to remain connected instead of disconnecting and reconnecting later requires that the application writer consider the relative costs of each option.</span></span> <span data-ttu-id="499b1-109">连接到数据源并保持连接状态的开销可能相对较大，具体取决于连接介质。</span><span class="sxs-lookup"><span data-stu-id="499b1-109">Connecting to a data source and remaining connected can be relatively costly, depending on the connection medium.</span></span> <span data-ttu-id="499b1-110">权衡利弊时，应用程序还必须就同一数据源上存在其他操作的可能性以及这些操作的时间安排情况做出假设。</span><span class="sxs-lookup"><span data-stu-id="499b1-110">In making a trade-off, the application must also make assumptions about the probability and timing of additional operations on the same data source.</span></span> <span data-ttu-id="499b1-111">应用程序可能还必须使用多个连接。</span><span class="sxs-lookup"><span data-stu-id="499b1-111">An application may also have to use more than one connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="499b1-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="499b1-112">See Also</span></span>  
 [<span data-ttu-id="499b1-113">与 SQL Server &#40;ODBC&#41;通信</span><span class="sxs-lookup"><span data-stu-id="499b1-113">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
