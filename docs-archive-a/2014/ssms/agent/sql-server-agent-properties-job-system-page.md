---
title: SQL Server 代理属性（“作业系统”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 743a8d558e97e9ad83cfc66e9ef1adf2e1bc0c2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590003"
---
# <a name="sql-server-agent-properties-job-system-page"></a><span data-ttu-id="b68a6-102">SQL Server 代理属性（“作业系统”页）</span><span class="sxs-lookup"><span data-stu-id="b68a6-102">SQL Server Agent Properties (Job System Page)</span></span>
  <span data-ttu-id="b68a6-103">使用此页可以查看和修改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务管理作业的方式。</span><span class="sxs-lookup"><span data-stu-id="b68a6-103">Use this page to view and modify how the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service manages jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b68a6-104">选项</span><span class="sxs-lookup"><span data-stu-id="b68a6-104">Options</span></span>  
 <span data-ttu-id="b68a6-105">**关闭超时间隔(秒)**</span><span class="sxs-lookup"><span data-stu-id="b68a6-105">**Shutdown time-out interval (in seconds)**</span></span>  
 <span data-ttu-id="b68a6-106">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在关闭作业之前等待作业完成的秒数。</span><span class="sxs-lookup"><span data-stu-id="b68a6-106">Specifies the number of seconds that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent waits for jobs to complete before shutting down.</span></span> <span data-ttu-id="b68a6-107">如果在指定间隔之后作业仍在运行，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将强制停止该作业。</span><span class="sxs-lookup"><span data-stu-id="b68a6-107">If the job is still running after the interval specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent forcefully stops the job.</span></span>  
  
 <span data-ttu-id="b68a6-108">**使用非管理员代理帐户**</span><span class="sxs-lookup"><span data-stu-id="b68a6-108">**Use a non-administrator proxy account**</span></span>  
 <span data-ttu-id="b68a6-109">为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理设置非管理员代理帐户。</span><span class="sxs-lookup"><span data-stu-id="b68a6-109">Sets a non-administrator proxy account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="b68a6-110">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]和更高版本支持多个代理，因此，此选项仅适用于管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之前的代理版本 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b68a6-110">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="b68a6-111">**用户名**</span><span class="sxs-lookup"><span data-stu-id="b68a6-111">**User name**</span></span>  
 <span data-ttu-id="b68a6-112">键入非管理员代理帐户的用户名。</span><span class="sxs-lookup"><span data-stu-id="b68a6-112">Type the name of the user for the non-administrator proxy account.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b68a6-113">支持多个代理，所以仅当管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]代理版本时此选项才适用。</span><span class="sxs-lookup"><span data-stu-id="b68a6-113">supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="b68a6-114">**密码**</span><span class="sxs-lookup"><span data-stu-id="b68a6-114">**Password**</span></span>  
 <span data-ttu-id="b68a6-115">键入非管理员代理帐户的用户密码。</span><span class="sxs-lookup"><span data-stu-id="b68a6-115">Type the password of the user for the non-administrator proxy account.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="b68a6-116">和更高版本支持多个代理，因此，仅当管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]代理版本时此选项才适用。</span><span class="sxs-lookup"><span data-stu-id="b68a6-116">and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="b68a6-117">**Domain**</span><span class="sxs-lookup"><span data-stu-id="b68a6-117">**Domain**</span></span>  
 <span data-ttu-id="b68a6-118">键入非管理性代理帐户的用户域。</span><span class="sxs-lookup"><span data-stu-id="b68a6-118">Type the domain of the user for the non-administrative proxy account.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b68a6-119">支持多个代理，所以仅当管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]代理版本时此选项才适用。</span><span class="sxs-lookup"><span data-stu-id="b68a6-119">supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68a6-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b68a6-120">See Also</span></span>  
 [<span data-ttu-id="b68a6-121">执行作业</span><span class="sxs-lookup"><span data-stu-id="b68a6-121">Implement Jobs</span></span>](implement-jobs.md)  
  
  
