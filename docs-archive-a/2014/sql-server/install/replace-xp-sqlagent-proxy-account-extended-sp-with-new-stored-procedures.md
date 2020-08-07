---
title: 使用新的存储过程替换 xp_sqlagent_proxy_account 扩展存储过程的使用情况 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- xp_sqlagent_proxy_account
ms.assetid: 0e3cc931-6237-41dd-bf0d-0c03f4d8fff2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d124ab73f4b4315550134f28ffad232b4a1c0ec2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588836"
---
# <a name="replace-usage-of-the-xp_sqlagent_proxy_account-extended-stored-procedure-with-new-stored-procedures"></a><span data-ttu-id="9323e-102">用新存储过程代替使用的 xp_sqlagent_proxy_account 扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="9323e-102">Replace usage of the xp_sqlagent_proxy_account extended stored procedure with new stored procedures</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9323e-103">代理支持多个代理帐户。</span><span class="sxs-lookup"><span data-stu-id="9323e-103">Agent supports multiple proxies.</span></span> <span data-ttu-id="9323e-104">您可使用一组新的存储过程来定义这些代理帐户。</span><span class="sxs-lookup"><span data-stu-id="9323e-104">You define these proxies by using a new set of stored procedures.</span></span> <span data-ttu-id="9323e-105">有关新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理存储过程的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的以下主题：</span><span class="sxs-lookup"><span data-stu-id="9323e-105">For more information about the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stored procedures, see the following topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   <span data-ttu-id="9323e-106">"sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-106">"sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-107">"sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-107">"sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-108">"sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-108">"sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-109">"sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-109">"sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-110">"sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-110">"sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-111">"sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-111">"sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-112">"sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-112">"sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-113">"sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-113">"sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-114">"sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-114">"sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-115">"sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-115">"sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="9323e-116">"sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="9323e-116">"sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9323e-117">升级到之后 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ，使用**xp_sqlagent_proxy_account**扩展存储过程的任何语句都将不起作用。</span><span class="sxs-lookup"><span data-stu-id="9323e-117">After you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], any statements that use the **xp_sqlagent_proxy_account** extended stored procedure will not work.</span></span> <span data-ttu-id="9323e-118">使用**sp_xp_cmdshell_proxy_account**而不是**xp_sqlagent_proxy_account**来设置**xp_cmdshell**的代理。</span><span class="sxs-lookup"><span data-stu-id="9323e-118">Use **sp_xp_cmdshell_proxy_account** instead of **xp_sqlagent_proxy_account** to set the proxy for **xp_cmdshell**.</span></span>  
  
## <a name="component"></a><span data-ttu-id="9323e-119">组件</span><span class="sxs-lookup"><span data-stu-id="9323e-119">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9323e-120">代理</span><span class="sxs-lookup"><span data-stu-id="9323e-120">Agent</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9323e-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9323e-121">See Also</span></span>  
 [<span data-ttu-id="9323e-122">SQL Server 代理升级问题</span><span class="sxs-lookup"><span data-stu-id="9323e-122">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
