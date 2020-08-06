---
title: 作业属性：新建作业 (通知 "页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30eca88943b48bd81bd38e236711d19ee7ec4503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577994"
---
# <a name="job-properties-new-job-notifications-page"></a><span data-ttu-id="0c233-102">作业属性：新建作业（“通知”页）</span><span class="sxs-lookup"><span data-stu-id="0c233-102">Job Properties: New Job (Notifications Page)</span></span>
  <span data-ttu-id="0c233-103">使用此页可以设置在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作业完成时代理要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="0c233-103">Use this page to set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0c233-104">选项</span><span class="sxs-lookup"><span data-stu-id="0c233-104">Options</span></span>  
 <span data-ttu-id="0c233-105">**电子邮件**</span><span class="sxs-lookup"><span data-stu-id="0c233-105">**E-mail**</span></span>  
 <span data-ttu-id="0c233-106">选择此选项将在作业完成时发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="0c233-106">Select this option to send e-mail when the job completes.</span></span> <span data-ttu-id="0c233-107">选择此选项后，选择要通知的操作员以及触发该通知的条件：“当作业成功时”\*\*\*\*；“当作业失败时”\*\*\*\*；或“当作业完成时”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c233-107">After selecting this option, choose the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="0c233-108">**第**</span><span class="sxs-lookup"><span data-stu-id="0c233-108">**Page**</span></span>  
 <span data-ttu-id="0c233-109">选择此选项将在作业完成时将电子邮件发送到操作员的寻呼程序。</span><span class="sxs-lookup"><span data-stu-id="0c233-109">Select this option to send e-mail to an operator's pager when the job completes.</span></span> <span data-ttu-id="0c233-110">选择此选项后，指定要通知的操作员以及触发该通知的条件：“当作业成功时”\*\*\*\*；“当作业失败时”\*\*\*\*；或“当作业完成时”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c233-110">After selecting this option, specify the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="0c233-111">**Net send**</span><span class="sxs-lookup"><span data-stu-id="0c233-111">**Net send**</span></span>  
 <span data-ttu-id="0c233-112">选择此选项将在作业完成时通过 net send 通知操作员。</span><span class="sxs-lookup"><span data-stu-id="0c233-112">Select this option to use net send to notify an operator when the job completes.</span></span> <span data-ttu-id="0c233-113">选择此选项后，指定要通知的操作员以及触发该通知的条件：“当作业成功时”\*\*\*\*；“当作业失败时”\*\*\*\*；或“当作业完成时”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c233-113">After selecting this option, specify the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="0c233-114">**写入 Windows 应用程序事件日志**</span><span class="sxs-lookup"><span data-stu-id="0c233-114">**Write to the Windows Application event log**</span></span>  
 <span data-ttu-id="0c233-115">选择此选项将在作业完成时将条目写入到应用程序事件日志中。</span><span class="sxs-lookup"><span data-stu-id="0c233-115">Select this option to write an entry in the application event log when the job completes.</span></span> <span data-ttu-id="0c233-116">选择此选项后，指定导致写入条目的条件：“当作业成功时”\*\*\*\*；“当作业失败时”\*\*\*\*；或“当作业完成时”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c233-116">After selecting this option, specify the condition that will cause the entry to be written: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="0c233-117">**自动删除作业**</span><span class="sxs-lookup"><span data-stu-id="0c233-117">**Automatically delete job**</span></span>  
 <span data-ttu-id="0c233-118">选择此选项将在作业完成时删除该作业。</span><span class="sxs-lookup"><span data-stu-id="0c233-118">Select this option to delete the job when the job completes.</span></span> <span data-ttu-id="0c233-119">选择此选项后，指定触发删除作业的条件：“当作业成功时”\*\*\*\*；“当作业失败时”\*\*\*\*；或“当作业完成时”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c233-119">After selecting this option, specify the condition that will trigger deletion of the job: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c233-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c233-120">See Also</span></span>  
 <span data-ttu-id="0c233-121">[执行作业](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="0c233-121">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="0c233-122">配置 SQL Server 代理邮件以使用数据库邮件</span><span class="sxs-lookup"><span data-stu-id="0c233-122">Configure SQL Server Agent Mail to Use Database Mail</span></span>](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  
