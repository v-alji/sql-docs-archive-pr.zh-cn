---
title: “通知操作员”任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed5158a4ec5cfe8374fedbb2afbca1294b58f05e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693421"
---
# <a name="notify-operator-task"></a><span data-ttu-id="0108d-102">“通知操作员”任务</span><span class="sxs-lookup"><span data-stu-id="0108d-102">Notify Operator Task</span></span>
  <span data-ttu-id="0108d-103">“通知操作员”任务将通知消息发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理操作员。</span><span class="sxs-lookup"><span data-stu-id="0108d-103">The Notify Operator task sends notification messages to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operators.</span></span> <span data-ttu-id="0108d-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理操作员是可以接收电子通知的人或组的别名。</span><span class="sxs-lookup"><span data-stu-id="0108d-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator is an alias for a person or group that can receive electronic notifications.</span></span> <span data-ttu-id="0108d-105">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 操作员的详细信息，请参阅 [操作员](../../ssms/agent//operators.md)。</span><span class="sxs-lookup"><span data-stu-id="0108d-105">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operators, see [Operators](../../ssms/agent//operators.md).</span></span>  
  
 <span data-ttu-id="0108d-106">通过使用“通知操作员”任务，包可以通过电子邮件、寻呼程序或 **net send**通知一个或多个操作员。</span><span class="sxs-lookup"><span data-stu-id="0108d-106">By using the Notify Operator task, a package can notify one or more operators via e-mail, pager, or **net send**.</span></span> <span data-ttu-id="0108d-107">可以用不同的方式通知各个操作员。</span><span class="sxs-lookup"><span data-stu-id="0108d-107">Each operator can be notified by different methods.</span></span> <span data-ttu-id="0108d-108">例如，用电子邮件和寻呼程序通知操作员 A，而用寻呼程序和 **net send**通知操作员 B。</span><span class="sxs-lookup"><span data-stu-id="0108d-108">For example, OperatorA is notified by e-mail and pager, and OperatorB is notified by pager and **net send**.</span></span> <span data-ttu-id="0108d-109">接收来自此任务的通知的操作员必须是“通知操作员”任务的 **OperatorNotify** 集合的成员。</span><span class="sxs-lookup"><span data-stu-id="0108d-109">The operators who receive notifications from the task must be members of the **OperatorNotify** collection on the Notify Operator task.</span></span>  
  
 <span data-ttu-id="0108d-110">“通知操作员”任务是唯一一个不封装 Transact-SQL 语句或 DBCC 命令的数据库维护任务。</span><span class="sxs-lookup"><span data-stu-id="0108d-110">The Notify Operator task is the only database maintenance task that does not encapsulate a Transact-SQL statement or a DBCC command.</span></span>  
  
## <a name="configuration-of-the-notify-operator-task"></a><span data-ttu-id="0108d-111">“通知操作员”任务的配置</span><span class="sxs-lookup"><span data-stu-id="0108d-111">Configuration of the Notify Operator Task</span></span>  
 <span data-ttu-id="0108d-112">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="0108d-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="0108d-113">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="0108d-113">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="0108d-114">有关可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="0108d-114">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="0108d-115">“通知操作员”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="0108d-115">Notify Operator Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 <span data-ttu-id="0108d-116">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="0108d-116">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="0108d-117">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="0108d-117">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
