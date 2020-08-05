---
title: 维护计划（服务器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.server.f1
- sql12.swb.maint.servers.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c971edc9b641846068313f47ca410715ec552014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580719"
---
# <a name="maintenance-plan-servers"></a><span data-ttu-id="d902f-102">维护计划（服务器）</span><span class="sxs-lookup"><span data-stu-id="d902f-102">Maintenance Plan (Servers)</span></span>
  <span data-ttu-id="d902f-103">使用 **“服务器”** 对话框可以选择要在其上运行维护计划的服务器。</span><span class="sxs-lookup"><span data-stu-id="d902f-103">Use the **Servers** dialog box to select the servers where you want to run the maintenance plan.</span></span>  
  
 <span data-ttu-id="d902f-104">必须配置包含一台主服务器和一台或多台目标服务器的多服务器环境，才能创建多服务器维护计划。</span><span class="sxs-lookup"><span data-stu-id="d902f-104">A multiserver environment containing one master server and one or more target servers must be configured to create a multiserver maintenance plan.</span></span> <span data-ttu-id="d902f-105">在多服务器维护计划中，应将本地服务器配置为主服务器。</span><span class="sxs-lookup"><span data-stu-id="d902f-105">For multiserver maintenance plans, the local server should be configured as a master server.</span></span> <span data-ttu-id="d902f-106">在多服务器环境中，此对话框显示 **(local)** 主服务器和所有相应的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="d902f-106">In multiserver environments, this dialog box displays the **(local)** master server and all corresponding target servers.</span></span> <span data-ttu-id="d902f-107">将为本地服务器创建一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="d902f-107">One [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job is created for the local server.</span></span> <span data-ttu-id="d902f-108">此功能是处于启用还是禁用状态，取决于你是否选择了 **(local)** 服务器。</span><span class="sxs-lookup"><span data-stu-id="d902f-108">It is enabled or disabled depending on whether you select the **(local)** server.</span></span> <span data-ttu-id="d902f-109">如果选择了目标服务器，将创建一个多服务器作业，并且该作业将下载到每个选定的目标服务器上。</span><span class="sxs-lookup"><span data-stu-id="d902f-109">If target servers are selected, a multiserver job is created and downloaded to each of the selected target servers.</span></span> <span data-ttu-id="d902f-110">如果未选择任何目标服务器，则会删除该多服务器作业。</span><span class="sxs-lookup"><span data-stu-id="d902f-110">If no target servers are selected, the multiserver job is deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d902f-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d902f-111">See Also</span></span>  
 <span data-ttu-id="d902f-112">[维护计划](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="d902f-112">[Maintenance Plans](maintenance-plans.md) </span></span>  
 <span data-ttu-id="d902f-113">[创建多服务器环境](../../ssms/agent/create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="d902f-113">[Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="d902f-114">[设置主服务器](../../ssms/agent/make-a-master-server.md) </span><span class="sxs-lookup"><span data-stu-id="d902f-114">[Make a Master Server](../../ssms/agent/make-a-master-server.md) </span></span>  
 [<span data-ttu-id="d902f-115">设置目标服务器</span><span class="sxs-lookup"><span data-stu-id="d902f-115">Make a Target Server</span></span>](../../ssms/agent/make-a-target-server.md)  
  
  
