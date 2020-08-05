---
title: 维护计划（管理连接）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.connections.f1
ms.assetid: 95ad9375-6584-423e-b9de-0e86782f8017
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b6b9f0c1652ead2f21567634b758ce81485b47b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580723"
---
# <a name="maintenance-plan-manage-connections"></a><span data-ttu-id="52404-102">维护计划（管理连接）</span><span class="sxs-lookup"><span data-stu-id="52404-102">Maintenance Plan (Manage Connections)</span></span>
  <span data-ttu-id="52404-103">使用 **“管理连接”** 对话框可以指定由维护计划使用的连接的属性。</span><span class="sxs-lookup"><span data-stu-id="52404-103">Use the **Manage Connections** dialog box to specify the properties of connections used by maintenance plans.</span></span> <span data-ttu-id="52404-104">在创建某个维护计划时，将会与创建该计划所在的服务器建立本地连接。</span><span class="sxs-lookup"><span data-stu-id="52404-104">When you create a maintenance plan, a local connection to the server where you created the plan is created.</span></span> <span data-ttu-id="52404-105">使用此连接，可以创建在此本地连接上执行工作的任务。</span><span class="sxs-lookup"><span data-stu-id="52404-105">Use this connection to create tasks that perform work on this local connection.</span></span> <span data-ttu-id="52404-106">如果需要的话，请使用 **“管理连接”** 对话框添加任务。</span><span class="sxs-lookup"><span data-stu-id="52404-106">When needed, use the **Manage Connections** dialog box to add them.</span></span> <span data-ttu-id="52404-107">配置其他连接后，它们将出现在每个任务的连接框中。</span><span class="sxs-lookup"><span data-stu-id="52404-107">When additional connections are configured they appear in the connections box for each task.</span></span>  
  
## <a name="options"></a><span data-ttu-id="52404-108">选项</span><span class="sxs-lookup"><span data-stu-id="52404-108">Options</span></span>  
 <span data-ttu-id="52404-109">**Server**</span><span class="sxs-lookup"><span data-stu-id="52404-109">**Server**</span></span>  
 <span data-ttu-id="52404-110">服务器实例。</span><span class="sxs-lookup"><span data-stu-id="52404-110">The server instance.</span></span>  
  
 <span data-ttu-id="52404-111">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="52404-111">**Authentication**</span></span>  
 <span data-ttu-id="52404-112">指示是用 Windows 身份验证还是用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证建立连接。</span><span class="sxs-lookup"><span data-stu-id="52404-112">Indicates whether the connection is made with Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52404-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52404-113">See Also</span></span>  
 [<span data-ttu-id="52404-114">维护计划</span><span class="sxs-lookup"><span data-stu-id="52404-114">Maintenance Plans</span></span>](maintenance-plans.md)  
  
  
