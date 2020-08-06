---
title: 错误消息 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: rothja
ms.author: jroth
ms.openlocfilehash: d004ba320b50896b6f57c5de335d7f7b3d33e87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692386"
---
# <a name="error-messages"></a><span data-ttu-id="9099a-102">错误消息</span><span class="sxs-lookup"><span data-stu-id="9099a-102">Error Messages</span></span>
  <span data-ttu-id="9099a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序返回的消息文本将放在**SQLGetDiagRec**的*MessageText*参数中。</span><span class="sxs-lookup"><span data-stu-id="9099a-103">The text of messages returned by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is placed in the *MessageText* parameter of **SQLGetDiagRec**.</span></span> <span data-ttu-id="9099a-104">错误源由消息标头指示：</span><span class="sxs-lookup"><span data-stu-id="9099a-104">The source of an error is indicated by the header of the message:</span></span>  
  
 <span data-ttu-id="9099a-105">[Microsoft][ODBC 驱动程序管理器]</span><span class="sxs-lookup"><span data-stu-id="9099a-105">[Microsoft][ODBC Driver Manager]</span></span>  
 <span data-ttu-id="9099a-106">这些错误由 ODBC 驱动程序管理器引发。</span><span class="sxs-lookup"><span data-stu-id="9099a-106">These errors are raised by the ODBC Driver Manager.</span></span>  
  
 <span data-ttu-id="9099a-107">[Microsoft][ODBC 游标库]</span><span class="sxs-lookup"><span data-stu-id="9099a-107">[Microsoft][ODBC Cursor Library]</span></span>  
 <span data-ttu-id="9099a-108">这些错误由 ODBC 游标库引发。</span><span class="sxs-lookup"><span data-stu-id="9099a-108">These errors are raised by the ODBC cursor library.</span></span>  
  
 <span data-ttu-id="9099a-109">[Microsoft][SQL Server Native Client]</span><span class="sxs-lookup"><span data-stu-id="9099a-109">[Microsoft][SQL Server Native Client]</span></span>  
 <span data-ttu-id="9099a-110">这些错误是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序引发的。</span><span class="sxs-lookup"><span data-stu-id="9099a-110">These errors are raised by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="9099a-111">如果没有名为 Net-Library 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的其他节点，驱动程序就会发生该错误。</span><span class="sxs-lookup"><span data-stu-id="9099a-111">If there are no other nodes with either the name of a Net-Library or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], then the error was encountered in the driver.</span></span>  
  
 <span data-ttu-id="9099a-112">微软[SQL Server Native Client][*Net-transportname*]</span><span class="sxs-lookup"><span data-stu-id="9099a-112">[Microsoft][SQL Server Native Client][*Net-Transportname*]</span></span>  
 <span data-ttu-id="9099a-113">这些错误由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 网络库引发，其中， *net net-transportname*是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端网络传输 (的显示名称，例如命名管道、共享内存、TCP/IP 套接字或通过) 。</span><span class="sxs-lookup"><span data-stu-id="9099a-113">These errors are raised by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Net-Library, where *Net-Transportname* is the display name of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network transport (for example, Named Pipes, Shared Memory, TCP/IP Sockets, or VIA).</span></span> <span data-ttu-id="9099a-114">错误消息的提醒内容含有调用的 Net-Library 函数以及 TDS 函数在基础网络 API 中调用的函数。</span><span class="sxs-lookup"><span data-stu-id="9099a-114">The remainder of the error message contains the Net-Library function called and the function called in the underlying network API by the TDS function.</span></span> <span data-ttu-id="9099a-115">返回的*pfNative*错误代码是基础网络协议堆栈中的错误代码。</span><span class="sxs-lookup"><span data-stu-id="9099a-115">The *pfNative* error code returned with these errors is the error code from the underlying network protocol stack.</span></span>  
  
 <span data-ttu-id="9099a-116">[Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]</span><span class="sxs-lookup"><span data-stu-id="9099a-116">[Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]</span></span>  
 <span data-ttu-id="9099a-117">这些错误由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 引发。</span><span class="sxs-lookup"><span data-stu-id="9099a-117">These errors are raised by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9099a-118">错误消息中的提醒内容是来自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的错误消息文本。</span><span class="sxs-lookup"><span data-stu-id="9099a-118">The remainder of the error message is the text of the error message from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9099a-119">返回的*pfNative*代码是来自的错误号 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9099a-119">The *pfNative* code returned with these errors is the error number from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9099a-120">若要详细了解 (的错误消息列表及其数字) 可以返回的错误消息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅中**master**数据库中**sysmessages**系统表的 "描述" 和 "错误" 列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9099a-120">For more information about a list of error messages (and their numbers) that can be returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the description and error columns of the **sysmessages** system table in the **master** database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9099a-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9099a-121">See Also</span></span>  
 [<span data-ttu-id="9099a-122">处理错误和消息</span><span class="sxs-lookup"><span data-stu-id="9099a-122">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
