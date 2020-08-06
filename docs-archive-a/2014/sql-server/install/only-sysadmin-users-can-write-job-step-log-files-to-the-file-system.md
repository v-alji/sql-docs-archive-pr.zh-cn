---
title: 只有 sysadmin 用户才能将作业步骤日志文件写入文件系统 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e2bf5095ac1e6b67f6c6f3f87444879913916e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587147"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a><span data-ttu-id="84d67-102">只有 sysadmin 用户才能将作业步骤日志文件写入文件系统</span><span class="sxs-lookup"><span data-stu-id="84d67-102">Only sysadmin users can write job step log files to the file system</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="84d67-103">可以为每个作业步骤写入一个日志。</span><span class="sxs-lookup"><span data-stu-id="84d67-103">optionally writes a log for each job step.</span></span>  
  
## <a name="component"></a><span data-ttu-id="84d67-104">组件</span><span class="sxs-lookup"><span data-stu-id="84d67-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="84d67-105">代理</span><span class="sxs-lookup"><span data-stu-id="84d67-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="84d67-106">说明</span><span class="sxs-lookup"><span data-stu-id="84d67-106">Description</span></span>  
 <span data-ttu-id="84d67-107">在中 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对于由**sysadmin**固定服务器角色的成员所拥有的作业，代理可以将日志写入文件系统。</span><span class="sxs-lookup"><span data-stu-id="84d67-107">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write logs to the file system for jobs that are owned by members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="84d67-108">如果作业所有者不是**sysadmin**角色的成员，并且如果启用了代理帐户，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理可以使用代理帐户的凭据将日志写入文件系统。</span><span class="sxs-lookup"><span data-stu-id="84d67-108">If the job owner is not a member of the **sysadmin** role and if the proxy account is enabled, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write logs to the file system by using the credentials of the proxy account.</span></span>  
  
 <span data-ttu-id="84d67-109">升级后，不属于**sysadmin**固定服务器角色成员的用户所拥有的作业将无法再将日志写入文件系统。</span><span class="sxs-lookup"><span data-stu-id="84d67-109">After you upgrade, jobs that are owned by users who are not members of the **sysadmin** fixed server role can no longer write logs to the file system.</span></span> <span data-ttu-id="84d67-110">相反，这些用户可以选择将其日志写入**msdb**数据库中的表的选项。</span><span class="sxs-lookup"><span data-stu-id="84d67-110">Instead, these users can select the option to write their logs to a table in the **msdb** database.</span></span> <span data-ttu-id="84d67-111">**Sysadmin**角色的成员仍可以将日志文件写入文件系统。</span><span class="sxs-lookup"><span data-stu-id="84d67-111">Members of the **sysadmin** role can still write log files to the file system.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="84d67-112">纠正措施</span><span class="sxs-lookup"><span data-stu-id="84d67-112">Corrective Action</span></span>  
 <span data-ttu-id="84d67-113">升级后，不属于**sysadmin**角色成员的用户所拥有的作业将继续运行，但不会创建日志。</span><span class="sxs-lookup"><span data-stu-id="84d67-113">After you upgrade, jobs that are owned by users who are not members of the **sysadmin** role will continue to run, but logs will not be created.</span></span> <span data-ttu-id="84d67-114">若要将作业步骤记录到表中，不是**sysadmin**角色成员的用户必须手动更新其作业。</span><span class="sxs-lookup"><span data-stu-id="84d67-114">To log job steps to a table, users who are not members of the **sysadmin** role must manually update their jobs.</span></span>  
  
 <span data-ttu-id="84d67-115">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“创建作业”、“创建作业步骤”和“处理多个作业步骤”主题。</span><span class="sxs-lookup"><span data-stu-id="84d67-115">For more information, see the topics "Creating Jobs," "Creating Job Steps," and "Handling Multiple Job Steps" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d67-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84d67-116">See Also</span></span>  
 [<span data-ttu-id="84d67-117">SQL Server 代理升级问题</span><span class="sxs-lookup"><span data-stu-id="84d67-117">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
