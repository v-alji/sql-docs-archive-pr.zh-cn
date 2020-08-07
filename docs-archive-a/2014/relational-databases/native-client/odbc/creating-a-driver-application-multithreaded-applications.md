---
title: 多线程应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
author: rothja
ms.author: jroth
ms.openlocfilehash: b680086f76e0c1a1e8c8cfc2f4ef82099957b3fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589000"
---
# <a name="multithreaded-applications"></a><span data-ttu-id="d9f55-102">多线程应用程序</span><span class="sxs-lookup"><span data-stu-id="d9f55-102">Multithreaded Applications</span></span>
  <span data-ttu-id="d9f55-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序是多线程驱动程序。</span><span class="sxs-lookup"><span data-stu-id="d9f55-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver is a multithreaded driver.</span></span> <span data-ttu-id="d9f55-104">编写多线程应用程序是使用异步调用处理多个 ODBC 调用的替代方法。</span><span class="sxs-lookup"><span data-stu-id="d9f55-104">Writing a multithreaded application is an alternative to using asynchronous calls to process multiple ODBC calls.</span></span> <span data-ttu-id="d9f55-105">线程可以进行同步 ODBC 调用，而在第一个线程被阻塞以等待其调用的响应时可以处理其他线程。</span><span class="sxs-lookup"><span data-stu-id="d9f55-105">A thread can make a synchronous ODBC call, and other threads can process while the first thread is blocked waiting for the response to its call.</span></span> <span data-ttu-id="d9f55-106">此模型比进行异步调用效率更高，因为它避免了诸如网络流量的开销以及对 SQL_STILL_EXECUTING 执行重复的 ODBC 函数调用测试。</span><span class="sxs-lookup"><span data-stu-id="d9f55-106">This model is more efficient than making asynchronous calls because it eliminates overhead such as network traffic and making repeated ODBC function calls testing for SQL_STILL_EXECUTING.</span></span>  
  
 <span data-ttu-id="d9f55-107">异步模式仍是一种有效的处理方法。</span><span class="sxs-lookup"><span data-stu-id="d9f55-107">Asynchronous mode is still an effective method of processing.</span></span> <span data-ttu-id="d9f55-108">尽管多线程模型的性能不断改进，但是仍没有必要对异步应用程序进行重新编写。</span><span class="sxs-lookup"><span data-stu-id="d9f55-108">The performance improvements of a multithreaded model are not enough to justify rewriting asynchronous applications.</span></span> <span data-ttu-id="d9f55-109">如果用户正在转换使用 DB-Library 异步模型的 DB-Library 应用程序，将它们转换为 ODBC 异步模型更为容易。</span><span class="sxs-lookup"><span data-stu-id="d9f55-109">If users are converting DB-Library applications that use the DB-Library asynchronous model, it is easier to convert them to the ODBC asynchronous model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f55-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9f55-110">See Also</span></span>  
 [<span data-ttu-id="d9f55-111">创建 SQL Server Native Client ODBC 驱动程序应用程序</span><span class="sxs-lookup"><span data-stu-id="d9f55-111">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
  
