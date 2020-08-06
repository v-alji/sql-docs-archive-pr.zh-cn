---
title: 作业活动监视器刷新 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5f290825f8a776c954ef802b184f7600aea5dc9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586675"
---
# <a name="job-activity-monitor-refresh"></a><span data-ttu-id="0a511-102">作业活动监视器刷新</span><span class="sxs-lookup"><span data-stu-id="0a511-102">Job Activity Monitor Refresh</span></span>
  <span data-ttu-id="0a511-103">使用 **“刷新设置”** 对话框可以配置作业活动监视器获取服务器活动最新信息的频率。</span><span class="sxs-lookup"><span data-stu-id="0a511-103">Use the **Refresh Settings** dialog box to configure how often Job Activity Monitor obtains new information about server activity.</span></span> <span data-ttu-id="0a511-104">作业活动监视器必须对所监视的服务器运行查询才能获取作业活动监视器网格的信息。</span><span class="sxs-lookup"><span data-stu-id="0a511-104">Job Activity Monitor must run queries on the monitored server to obtain information for the Job Activity Monitor grid.</span></span> <span data-ttu-id="0a511-105">当自动刷新间隔设置为小于 30 秒时，运行这些查询所用的时间可能会影响服务器性能。</span><span class="sxs-lookup"><span data-stu-id="0a511-105">When the auto-refresh interval is set to less than 30 seconds, the time used to run these queries can affect server performance.</span></span>  
  
 <span data-ttu-id="0a511-106">若要打开此对话框，请在作业活动监视器的 **“状态”** 部分中单击 **“查看刷新设置”** 。</span><span class="sxs-lookup"><span data-stu-id="0a511-106">To open this dialog, click **View refresh settings**, in the **Status** section of Job Activity Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0a511-107">选项</span><span class="sxs-lookup"><span data-stu-id="0a511-107">Options</span></span>  
 <span data-ttu-id="0a511-108">**自动刷新间隔**</span><span class="sxs-lookup"><span data-stu-id="0a511-108">**Auto-refresh every**</span></span>  
 <span data-ttu-id="0a511-109">选中此选项将启动活动监视器信息的自动刷新功能。</span><span class="sxs-lookup"><span data-stu-id="0a511-109">Check to initiate automatic refreshing of Activity Monitor information.</span></span> <span data-ttu-id="0a511-110">默认情况下，此功能为关闭状态。</span><span class="sxs-lookup"><span data-stu-id="0a511-110">This is off by default.</span></span>  
  
 <span data-ttu-id="0a511-111">**seconds**</span><span class="sxs-lookup"><span data-stu-id="0a511-111">**seconds**</span></span>  
 <span data-ttu-id="0a511-112">自动刷新的间隔秒数。</span><span class="sxs-lookup"><span data-stu-id="0a511-112">The number of seconds between auto-refresh attempts.</span></span> <span data-ttu-id="0a511-113">默认值为 60 秒。</span><span class="sxs-lookup"><span data-stu-id="0a511-113">Defaults to 60 seconds.</span></span> <span data-ttu-id="0a511-114">当设置为 5 秒或小于 5 秒时，则每隔 5 秒刷新一次。</span><span class="sxs-lookup"><span data-stu-id="0a511-114">Refreshes every 5 seconds when set to 5 or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a511-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a511-115">See Also</span></span>  
 [<span data-ttu-id="0a511-116">监视作业活动</span><span class="sxs-lookup"><span data-stu-id="0a511-116">Monitor Job Activity</span></span>](../../ssms/agent/monitor-job-activity.md)  
  
  
