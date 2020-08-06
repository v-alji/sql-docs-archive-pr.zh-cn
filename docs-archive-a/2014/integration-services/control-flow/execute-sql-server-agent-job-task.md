---
title: “执行 SQL Server 代理作业”任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqlserveragentjobtask.f1
helpviewer_keywords:
- Execute SQL Server Agent Job task [Integration Services]
- jobs [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d0c66eb7022312fa3ec3d161f63a9aee92b840f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587539"
---
# <a name="execute-sql-server-agent-job-task"></a><span data-ttu-id="00b07-102">“执行 SQL Server 代理作业”任务</span><span class="sxs-lookup"><span data-stu-id="00b07-102">Execute SQL Server Agent Job Task</span></span>
  <span data-ttu-id="00b07-103">“执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业”任务运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="00b07-103">The Execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job task runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="00b07-104">代理是一个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 服务，它运行那些已在 SQL Server 实例中定义的作业。</span><span class="sxs-lookup"><span data-stu-id="00b07-104">Agent is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows service that runs jobs that have been defined in an instance of SQL Server.</span></span> <span data-ttu-id="00b07-105">您可以创建作业来执行 Transact-SQL 语句和 ActiveX 脚本、执行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 和复制的维护任务或运行包。</span><span class="sxs-lookup"><span data-stu-id="00b07-105">You can create jobs that execute Transact-SQL statements and ActiveX scripts, perform [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and Replication maintenance tasks, or run packages.</span></span> <span data-ttu-id="00b07-106">还可以配置作业以监视 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并激发警报。</span><span class="sxs-lookup"><span data-stu-id="00b07-106">You can also configure a job to monitor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and fire alerts.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="00b07-107">代理作业通常用来自动执行需要重复执行的任务。</span><span class="sxs-lookup"><span data-stu-id="00b07-107">Agent jobs are typically used to automate tasks that you perform repeatedly.</span></span> <span data-ttu-id="00b07-108">有关详细信息，请参阅 [执行作业](../../ssms/agent/implement-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="00b07-108">For more information, see [Implement Jobs](../../ssms/agent/implement-jobs.md).</span></span>  
  
 <span data-ttu-id="00b07-109">通过使用“执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理”作业任务，包可以执行与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件有关的管理任务。</span><span class="sxs-lookup"><span data-stu-id="00b07-109">By using the Execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job task, a package can perform administrative tasks related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="00b07-110">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业可以运行系统存储过程（如 **sp_enum_dtspackages** ）来获取文件夹中包的列表。</span><span class="sxs-lookup"><span data-stu-id="00b07-110">For example, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job can run a system stored procedure such as **sp_enum_dtspackages** to obtain a list of packages in a folder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="00b07-111">代理必须处于运行状态，本地或多服务器管理作业才能自动运行。</span><span class="sxs-lookup"><span data-stu-id="00b07-111">Agent must be running before local or multiserver administrative jobs can run automatically.</span></span>  
  
 <span data-ttu-id="00b07-112">此任务封装 **sp_start_job** 系统过程并把 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业的名称作为参数传递给该过程。</span><span class="sxs-lookup"><span data-stu-id="00b07-112">This task encapsulates the **sp_start_job** system procedure and passes the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job to the procedure as an argument.</span></span> <span data-ttu-id="00b07-113">有关详细信息，请参阅 [sp_start_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="00b07-113">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
## <a name="configuring-the-execute-sql-server-agent-job-task"></a><span data-ttu-id="00b07-114">配置“执行 SQL Server 代理作业”任务</span><span class="sxs-lookup"><span data-stu-id="00b07-114">Configuring the Execute SQL Server Agent Job Task</span></span>  
 <span data-ttu-id="00b07-115">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="00b07-115">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="00b07-116">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="00b07-116">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="00b07-117">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="00b07-117">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="00b07-118">“执行 SQL Server 代理作业”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="00b07-118">Execute SQL Server Agent Job Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)  
  
 <span data-ttu-id="00b07-119">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="00b07-119">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="00b07-120">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="00b07-120">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
