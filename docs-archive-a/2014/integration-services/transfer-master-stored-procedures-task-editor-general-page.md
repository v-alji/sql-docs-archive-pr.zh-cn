---
title: 传输主存储过程任务编辑器 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a25a5c9c6ed3802e21ac522e94163ce5fb9e8c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690716"
---
# <a name="transfer-master-stored-procedures-task-editor-general-page"></a><span data-ttu-id="2480f-102">传输主存储过程任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="2480f-102">Transfer Master Stored Procedures Task Editor (General Page)</span></span>
  <span data-ttu-id="2480f-103">可以使用 **“传输主存储过程任务编辑器”** 对话框的 **“常规”** 页，对传输主存储过程任务进行命名和说明。</span><span class="sxs-lookup"><span data-stu-id="2480f-103">Use the **General** page of the **Transfer Master Stored Procedures Task Editor** dialog box to name and describe the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="2480f-104">有关此任务的详细信息，请参阅 [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md)。</span><span class="sxs-lookup"><span data-stu-id="2480f-104">For more information about this task, see [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2480f-105">此任务只将 **dbo** 拥有的用户定义存储过程从源服务器上的 **master** 数据库传递到目标服务器上的 **master** 数据库。</span><span class="sxs-lookup"><span data-stu-id="2480f-105">This task transfers only user-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server.</span></span> <span data-ttu-id="2480f-106">若要在目标服务器上创建存储过程，必须在目标服务器上的 **master** 数据库中授予用户 CREATE PROCEDURE 权限，或者用户必须为目标服务器上 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="2480f-106">Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2480f-107">选项</span><span class="sxs-lookup"><span data-stu-id="2480f-107">Options</span></span>  
 <span data-ttu-id="2480f-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="2480f-108">**Name**</span></span>  
 <span data-ttu-id="2480f-109">为传输主存储过程任务键入唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="2480f-109">Type a unique name for the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="2480f-110">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="2480f-110">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2480f-111">任务名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2480f-111">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="2480f-112">**说明**</span><span class="sxs-lookup"><span data-stu-id="2480f-112">**Description**</span></span>  
 <span data-ttu-id="2480f-113">键入传输主存储过程任务的说明。</span><span class="sxs-lookup"><span data-stu-id="2480f-113">Type a description of the Transfer Master Stored Procedures task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2480f-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2480f-114">See Also</span></span>  
 <span data-ttu-id="2480f-115">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2480f-115">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="2480f-116">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="2480f-116">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="2480f-117">[传输主存储过程任务编辑器 &#40;"存储过程" 页&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md) </span><span class="sxs-lookup"><span data-stu-id="2480f-117">[Transfer Master Stored Procedures Task Editor &#40;Stored Procedures Page&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md) </span></span>  
 [<span data-ttu-id="2480f-118">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="2480f-118">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
