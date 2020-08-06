---
title: 指定作业响应 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: stevestein
ms.author: sstein
ms.openlocfilehash: d41c5e1552a1ff16343bdb2c4e9feaafb51c5783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682657"
---
# <a name="specify-job-responses"></a><span data-ttu-id="18982-102">指定作业响应</span><span class="sxs-lookup"><span data-stu-id="18982-102">Specify Job Responses</span></span>
  <span data-ttu-id="18982-103">作业响应指定完成作业后 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="18982-103">Job responses specify actions that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service will take after a job completes.</span></span> <span data-ttu-id="18982-104">作业响应可确保数据库管理员知道作业完成的时间和作业运行频率。</span><span class="sxs-lookup"><span data-stu-id="18982-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="18982-105">典型的作业响应包括：</span><span class="sxs-lookup"><span data-stu-id="18982-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="18982-106">使用电子邮件、电子寻呼或 **net send** 消息通知操作员。</span><span class="sxs-lookup"><span data-stu-id="18982-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span>  
  
     <span data-ttu-id="18982-107">如果操作员必须执行后续操作，应使用其中的某种作业响应。</span><span class="sxs-lookup"><span data-stu-id="18982-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="18982-108">例如，当一个备份作业成功地完成之后，必须通知操作员取出备份磁带并将其存放在安全处。</span><span class="sxs-lookup"><span data-stu-id="18982-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="18982-109">将事件消息写入 Windows 应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="18982-109">Writing an event message to the Windows application log.</span></span>  
  
     <span data-ttu-id="18982-110">只能对失败的作业使用这种响应。</span><span class="sxs-lookup"><span data-stu-id="18982-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="18982-111">自动删除作业。</span><span class="sxs-lookup"><span data-stu-id="18982-111">Automatically deleting the job.</span></span>  
  
     <span data-ttu-id="18982-112">如果确信不需要再次运行该作业，可以使用这种作业响应。</span><span class="sxs-lookup"><span data-stu-id="18982-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="18982-113">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="18982-113">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="18982-114">**说明**</span><span class="sxs-lookup"><span data-stu-id="18982-114">**Description**</span></span>|<span data-ttu-id="18982-115">**主题**</span><span class="sxs-lookup"><span data-stu-id="18982-115">**Topic**</span></span>|  
|<span data-ttu-id="18982-116">描述如何向操作员通知作业状态。</span><span class="sxs-lookup"><span data-stu-id="18982-116">Describes how to notify an operator of job status.</span></span>|[<span data-ttu-id="18982-117">向操作员通知作业状态</span><span class="sxs-lookup"><span data-stu-id="18982-117">Notify an Operator of Job Status</span></span>](notify-an-operator-of-job-status.md)|  
|<span data-ttu-id="18982-118">介绍如何将作业状态写入 Windows 应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="18982-118">Describes how to write job status to the Windows application log.</span></span>|[<span data-ttu-id="18982-119">Write the Job Status to the Windows Application Log</span><span class="sxs-lookup"><span data-stu-id="18982-119">Write the Job Status to the Windows Application Log</span></span>](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="18982-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18982-120">See Also</span></span>  
 [<span data-ttu-id="18982-121">监视事件和响应事件</span><span class="sxs-lookup"><span data-stu-id="18982-121">Monitor and Respond to Events</span></span>](monitor-and-respond-to-events.md)  
  
  
