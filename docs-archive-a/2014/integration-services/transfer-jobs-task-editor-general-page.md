---
title: 传输作业任务编辑器 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.general.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: 96531920-92d4-4a3b-a38a-6f0c8bc78ada
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d824c1904b8a3ffd0078f778a78dea898ab53577
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682348"
---
# <a name="transfer-jobs-task-editor-general-page"></a><span data-ttu-id="b1ded-102">传输作业任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="b1ded-102">Transfer Jobs Task Editor (General Page)</span></span>
  <span data-ttu-id="b1ded-103">可以使用 **“传输作业任务编辑器”** 对话框的 **“常规”** 页，对传输作业任务进行命名和说明。</span><span class="sxs-lookup"><span data-stu-id="b1ded-103">Use the **General** page of the **Transfer Jobs Task Editor** dialog box to name and describe the Transfer Jobs task.</span></span> <span data-ttu-id="b1ded-104">有关传输作业任务的详细信息，请参阅 [Transfer Jobs Task](control-flow/transfer-jobs-task.md)。</span><span class="sxs-lookup"><span data-stu-id="b1ded-104">For more information about the Transfer Jobs task, see [Transfer Jobs Task](control-flow/transfer-jobs-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1ded-105">只有目标服务器上 **sysadmin** 固定服务器角色或某个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理固定数据库角色的成员才能在其中成功创建作业。</span><span class="sxs-lookup"><span data-stu-id="b1ded-105">Only members of the **sysadmin** fixed server role or one of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles on the destination server can successfully create jobs there.</span></span> <span data-ttu-id="b1ded-106">若要访问源服务器上的作业，用户必须是该服务器上 **SQLAgentUserRole** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="b1ded-106">To access jobs on the source server, users must be a member of at least the **SQLAgentUserRole** fixed database role there.</span></span> <span data-ttu-id="b1ded-107">有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理的固定数据库角色及其权限的详细信息，请参阅 [SQL Server 代理固定数据库角色](../ssms/agent/sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="b1ded-107">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles and their permissions, see [SQL Server Agent Fixed Database Roles](../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b1ded-108">选项</span><span class="sxs-lookup"><span data-stu-id="b1ded-108">Options</span></span>  
 <span data-ttu-id="b1ded-109">**名称**</span><span class="sxs-lookup"><span data-stu-id="b1ded-109">**Name**</span></span>  
 <span data-ttu-id="b1ded-110">为传输作业任务键入唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="b1ded-110">Type a unique name for the Transfer Jobs task.</span></span> <span data-ttu-id="b1ded-111">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="b1ded-111">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1ded-112">任务名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="b1ded-112">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="b1ded-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="b1ded-113">**Description**</span></span>  
 <span data-ttu-id="b1ded-114">键入传输作业任务的说明。</span><span class="sxs-lookup"><span data-stu-id="b1ded-114">Type a description of the Transfer Jobs task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ded-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b1ded-115">See Also</span></span>  
 <span data-ttu-id="b1ded-116">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b1ded-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b1ded-117">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="b1ded-117">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="b1ded-118">[传输作业任务编辑器 &#40;作业 "页面&#41;](../../2014/integration-services/transfer-jobs-task-editor-jobs-page.md) </span><span class="sxs-lookup"><span data-stu-id="b1ded-118">[Transfer Jobs Task Editor &#40;Jobs Page&#41;](../../2014/integration-services/transfer-jobs-task-editor-jobs-page.md) </span></span>  
 [<span data-ttu-id="b1ded-119">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="b1ded-119">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
