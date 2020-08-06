---
title: 检查磁盘输入和输出子系统是否存在 IO 延迟问题 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a0ae8dc0d1a93f8150ccbeab73ed8aa918d1f495
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689336"
---
# <a name="check-disk-input-and-output-subsystem-for-io-delay-problems"></a><span data-ttu-id="789ca-102">检查磁盘输入和输出子系统是否存在 IO 延迟问题</span><span class="sxs-lookup"><span data-stu-id="789ca-102">Check Disk Input and Output Subsystem for IO Delay Problems</span></span>
  <span data-ttu-id="789ca-103">此规则检查计算机事件日志中是否存在错误消息 833。</span><span class="sxs-lookup"><span data-stu-id="789ca-103">This rule checks the event log for error message 833.</span></span> <span data-ttu-id="789ca-104">该消息指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已从磁盘发出读取或写入请求，并且表明该请求返回所用的时间已超过 15 秒。</span><span class="sxs-lookup"><span data-stu-id="789ca-104">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued a read or write request from disk, and that the request has taken longer than 15 seconds to return.</span></span> <span data-ttu-id="789ca-105">此错误由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 报告，表示磁盘 I/O 子系统有问题。</span><span class="sxs-lookup"><span data-stu-id="789ca-105">This error is reported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and indicates a problem with the disk I/O subsystem.</span></span> <span data-ttu-id="789ca-106">延迟此长度的时间可能会严重损坏 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 环境的性能。</span><span class="sxs-lookup"><span data-stu-id="789ca-106">Delays this long can severely damage the performance of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="789ca-107">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="789ca-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="789ca-108">通过检查系统事件日志获得硬件相关错误消息来纠正引错误。</span><span class="sxs-lookup"><span data-stu-id="789ca-108">Troubleshoot this error by examining the system event log for hardware-related error messages.</span></span> <span data-ttu-id="789ca-109">并且，如果有特定于硬件的日志，也要进行检查。</span><span class="sxs-lookup"><span data-stu-id="789ca-109">Also, examine hardware-specific logs if they are available.</span></span>  
  
 <span data-ttu-id="789ca-110">使用性能监视器检查以下计数器：</span><span class="sxs-lookup"><span data-stu-id="789ca-110">Use Performance Monitor to examine the following counters:</span></span>  
  
-   <span data-ttu-id="789ca-111">Average Disk Sec/Transfer</span><span class="sxs-lookup"><span data-stu-id="789ca-111">Average Disk Sec/Transfer</span></span>  
  
-   <span data-ttu-id="789ca-112">Average Disk Queue Length</span><span class="sxs-lookup"><span data-stu-id="789ca-112">Average Disk Queue Length</span></span>  
  
-   <span data-ttu-id="789ca-113">当前的磁盘队列长度</span><span class="sxs-lookup"><span data-stu-id="789ca-113">Current Disk Queue Length</span></span>  
  
 <span data-ttu-id="789ca-114">例如，运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机上的 Average Disk Sec/Transfer 时间通常少于 15 毫秒。</span><span class="sxs-lookup"><span data-stu-id="789ca-114">For example, the Average Disk Sec/Transfer time on a computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is typically less than 15 milliseconds.</span></span> <span data-ttu-id="789ca-115">如果 Average Disk Sec/Transfer 值增加，则表示磁盘 I/O 子系统未能完全满足 I/O 需求。</span><span class="sxs-lookup"><span data-stu-id="789ca-115">If the Average Disk Sec/Transfer value increases, this indicates that the disk I/O subsystem is not optimally keeping up with the I/O demand.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="789ca-116">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="789ca-116">For More Information</span></span>  
 [<span data-ttu-id="789ca-117">MSSQLSERVER_833</span><span class="sxs-lookup"><span data-stu-id="789ca-117">MSSQLSERVER_833</span></span>](../errors-events/mssqlserver-833-database-engine-error.md)  
  
 [<span data-ttu-id="789ca-118">Microsoft 知识库文章 897284</span><span class="sxs-lookup"><span data-stu-id="789ca-118">Microsoft Knowledge Base article 897284</span></span>](https://go.microsoft.com/fwlink/?linkid=117743)  
  
 <span data-ttu-id="789ca-119">[SQL Server I/O Basics, Chapter 2（SQL Server I/O 基础知识第 2 章）](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="789ca-119">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span></span>  
  
  
