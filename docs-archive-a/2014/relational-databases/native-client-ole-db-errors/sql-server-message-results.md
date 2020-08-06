---
title: SQL Server 消息结果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: rothja
ms.author: jroth
ms.openlocfilehash: aa63445b81ec89b87523fa29c50817e128d48515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589536"
---
# <a name="sql-server-message-results"></a><span data-ttu-id="13063-102">SQL Server 消息结果</span><span class="sxs-lookup"><span data-stu-id="13063-102">SQL Server Message Results</span></span>
  <span data-ttu-id="13063-103">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在执行时不会生成 Native Client OLE DB 提供程序行集或受影响的行的计数：</span><span class="sxs-lookup"><span data-stu-id="13063-103">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements do not generate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets or a count of affected rows when executed:</span></span>  
  
-   <span data-ttu-id="13063-104">PRINT</span><span class="sxs-lookup"><span data-stu-id="13063-104">PRINT</span></span>  
  
-   <span data-ttu-id="13063-105">严重性级别为 10 或更低的 RAISERROR</span><span class="sxs-lookup"><span data-stu-id="13063-105">RAISERROR with a severity of 10 or lower</span></span>  
  
-   <span data-ttu-id="13063-106">DBCC</span><span class="sxs-lookup"><span data-stu-id="13063-106">DBCC</span></span>  
  
-   <span data-ttu-id="13063-107">SET SHOWPLAN</span><span class="sxs-lookup"><span data-stu-id="13063-107">SET SHOWPLAN</span></span>  
  
-   <span data-ttu-id="13063-108">SET STATISTICS</span><span class="sxs-lookup"><span data-stu-id="13063-108">SET STATISTICS</span></span>  
  
 <span data-ttu-id="13063-109">这些语句会返回一个或多个信息性消息，或者使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回信息性消息以替代行集或计数结果。</span><span class="sxs-lookup"><span data-stu-id="13063-109">These statements either return one or more informational messages or cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to return informational messages in place of rowset or count results.</span></span> <span data-ttu-id="13063-110">成功执行时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 提供程序将返回 S_OK，并且消息可供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB 提供程序使用者使用。</span><span class="sxs-lookup"><span data-stu-id="13063-110">On successful execution, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns S_OK, and the messages are available to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer.</span></span>  
  
 <span data-ttu-id="13063-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native client OLE DB 提供程序返回 S_OK 并在执行多个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或使用者执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序成员函数时提供一条或多条信息性消息。</span><span class="sxs-lookup"><span data-stu-id="13063-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns S_OK and has one or more informational messages available following the execution of many [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or the consumer execution of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function.</span></span>  
  
 <span data-ttu-id="13063-112">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 每次执行成员函数后，无论返回代码的值、是否存在返回的 IRowset 或 IMultipleResults 接口引用，或者是否缺少返回的**IRowset**或**IMultipleResults**接口引用或受影响的行的计数，Native Client OLE DB 提供程序使用者允许动态指定查询文本。</span><span class="sxs-lookup"><span data-stu-id="13063-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer allowing dynamic specification of query text should check error interfaces after every member function execution regardless of the value of the return code, the presence or absence of a returned **IRowset** or **IMultipleResults** interface reference, or a count of affected rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13063-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13063-113">See Also</span></span>  
 [<span data-ttu-id="13063-114">错误</span><span class="sxs-lookup"><span data-stu-id="13063-114">Errors</span></span>](errors.md)  
  
  
