---
title: SQL Server 代理属性（“历史记录”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: stevestein
ms.author: sstein
ms.openlocfilehash: d67ff3da97e11292abcac03958fe1e423b35d7d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590005"
---
# <a name="sql-server-agent-properties-history-page"></a><span data-ttu-id="71b5c-102">SQL Server 代理属性（“历史记录”页）</span><span class="sxs-lookup"><span data-stu-id="71b5c-102">SQL Server Agent Properties (History Page)</span></span>
  <span data-ttu-id="71b5c-103">使用此页可以查看和修改用于管理 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务历史记录日志的设置。</span><span class="sxs-lookup"><span data-stu-id="71b5c-103">Use this page to view and modify settings for managing the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service history log.</span></span>  
  
## <a name="options"></a><span data-ttu-id="71b5c-104">选项</span><span class="sxs-lookup"><span data-stu-id="71b5c-104">Options</span></span>  
 <span data-ttu-id="71b5c-105">**限制作业历史记录日志的大小**</span><span class="sxs-lookup"><span data-stu-id="71b5c-105">**Limit size of job history log**</span></span>  
 <span data-ttu-id="71b5c-106">对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在日志中保留的作业历史记录信息量设置限制。</span><span class="sxs-lookup"><span data-stu-id="71b5c-106">Sets limits for the amount of job history information that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains in the log.</span></span>  
  
 <span data-ttu-id="71b5c-107">**作业历史记录日志的最大大小(行)**</span><span class="sxs-lookup"><span data-stu-id="71b5c-107">**Maximum job history log size (in rows)**</span></span>  
 <span data-ttu-id="71b5c-108">设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理保留的最大行数。</span><span class="sxs-lookup"><span data-stu-id="71b5c-108">Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains.</span></span> <span data-ttu-id="71b5c-109">如果日志包含的行数增大到此数值，则在输入新行时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理会删除日志中最早的行。</span><span class="sxs-lookup"><span data-stu-id="71b5c-109">When the log grows to contain this number of rows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent removes the oldest rows in the log as new rows are entered.</span></span>  
  
 <span data-ttu-id="71b5c-110">**每个作业的最大作业历史记录行数**</span><span class="sxs-lookup"><span data-stu-id="71b5c-110">**Maximum job history rows per job**</span></span>  
 <span data-ttu-id="71b5c-111">设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理为每个作业保留的最大行数。</span><span class="sxs-lookup"><span data-stu-id="71b5c-111">Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains per job.</span></span> <span data-ttu-id="71b5c-112">如果特定作业历史记录包含的行数增大到此数值，则在输入新行时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理会删除日志中最早的行。</span><span class="sxs-lookup"><span data-stu-id="71b5c-112">When the history for a particular job grows to contain this number of rows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent removes the oldest rows in the log as new rows are entered.</span></span>  
  
 <span data-ttu-id="71b5c-113">**删除代理历史记录**</span><span class="sxs-lookup"><span data-stu-id="71b5c-113">**Remove agent history**</span></span>  
 <span data-ttu-id="71b5c-114">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将删除在日志中保留的时间超过指定时间长度的项。</span><span class="sxs-lookup"><span data-stu-id="71b5c-114">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will remove entries that have been in the log longer than a specified length of time.</span></span> <span data-ttu-id="71b5c-115">这是用来删除历史记录的一次性操作。</span><span class="sxs-lookup"><span data-stu-id="71b5c-115">This is a one-time execution to remove the history.</span></span> <span data-ttu-id="71b5c-116">如果需要重复发生的作业，则创建并安排具有清除作业的维护计划。</span><span class="sxs-lookup"><span data-stu-id="71b5c-116">If a reoccurring job is needed, create and schedule a maintenance plan with a cleanup job.</span></span>  
  
 <span data-ttu-id="71b5c-117">**保留时间超过**</span><span class="sxs-lookup"><span data-stu-id="71b5c-117">**Older than**</span></span>  
 <span data-ttu-id="71b5c-118">设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将保留项多久。</span><span class="sxs-lookup"><span data-stu-id="71b5c-118">Sets the amount of time that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will retain entries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b5c-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71b5c-119">See Also</span></span>  
 [<span data-ttu-id="71b5c-120">SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="71b5c-120">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
