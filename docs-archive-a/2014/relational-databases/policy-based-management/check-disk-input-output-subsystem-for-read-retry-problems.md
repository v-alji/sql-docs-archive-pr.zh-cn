---
title: 检查磁盘输入输出子系统是否存在读取重试问题 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19809b1554e435600eb4eeae424bed17dc27bdbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682823"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a><span data-ttu-id="a51c7-102">检查磁盘 I/O 子系统是否存在读取重试问题</span><span class="sxs-lookup"><span data-stu-id="a51c7-102">Check Disk Input Output Subsystem for Read Retry Problems</span></span>
  <span data-ttu-id="a51c7-103">此规则检查事件日志中是否存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误消息 825。</span><span class="sxs-lookup"><span data-stu-id="a51c7-103">This rule checks the event log for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message 825.</span></span> <span data-ttu-id="a51c7-104">此错误消息指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法在第一次尝试时从磁盘读取数据。</span><span class="sxs-lookup"><span data-stu-id="a51c7-104">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] was unable to read data from the disk on the first try.</span></span> <span data-ttu-id="a51c7-105">此消息指示磁盘 I/O 子系统存在严重问题。</span><span class="sxs-lookup"><span data-stu-id="a51c7-105">This message indicates a major problem with the disk I/O subsystem.</span></span> <span data-ttu-id="a51c7-106">此消息当前不指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 问题。</span><span class="sxs-lookup"><span data-stu-id="a51c7-106">This message does not currently indicate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problem.</span></span> <span data-ttu-id="a51c7-107">但是，如果不解决此磁盘问题，可能导致数据丢失或数据库损坏。</span><span class="sxs-lookup"><span data-stu-id="a51c7-107">However, the disk problem could cause data loss or database corruption if it is not resolved.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="a51c7-108">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="a51c7-108">Best Practices Recommendations</span></span>  
 <span data-ttu-id="a51c7-109">下列操作可帮助您发现并解决基本的硬件问题：</span><span class="sxs-lookup"><span data-stu-id="a51c7-109">The following actions might help you discover and resolve the underlying hardware problem:</span></span>  
  
-   <span data-ttu-id="a51c7-110">查阅错误日志和此消息中的变量文本以获得说明问题的线索。</span><span class="sxs-lookup"><span data-stu-id="a51c7-110">Review the error log and the variable text in this message for clues that explain the problem.</span></span>  
  
-   <span data-ttu-id="a51c7-111">检查磁盘系统。</span><span class="sxs-lookup"><span data-stu-id="a51c7-111">Check the disk system.</span></span> <span data-ttu-id="a51c7-112">此问题可能与磁盘、磁盘控制器、阵列卡或磁盘驱动程序有关。</span><span class="sxs-lookup"><span data-stu-id="a51c7-112">The problem could be related to the disks, the disk controllers, array cards, or disk drivers.</span></span>  
  
-   <span data-ttu-id="a51c7-113">与磁盘制造商联系以获得用于检查磁盘系统状态的最新实用工具。</span><span class="sxs-lookup"><span data-stu-id="a51c7-113">Contact the disk manufacturer for the latest utilities for checking the status of the disk system.</span></span>  
  
-   <span data-ttu-id="a51c7-114">与磁盘制造商联系以获得最新的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="a51c7-114">Contact the disk manufacturer for the latest driver updates.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="a51c7-115">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="a51c7-115">For More Information</span></span>  
 [<span data-ttu-id="a51c7-116">MSSQLSERVER_825</span><span class="sxs-lookup"><span data-stu-id="a51c7-116">MSSQLSERVER_825</span></span>](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 <span data-ttu-id="a51c7-117">[SQL Server I/O Basics, Chapter 2（SQL Server I/O 基础知识第 2 章）](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="a51c7-117">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span></span>  
  
  
