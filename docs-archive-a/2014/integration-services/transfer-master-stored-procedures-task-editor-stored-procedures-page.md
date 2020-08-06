---
title: 传输主存储过程任务编辑器 ("存储过程" 页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f9fad408b54d4ef27d4c5d06b0d352f366ad9c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690714"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a><span data-ttu-id="bff7e-102">传输主存储过程任务编辑器（“存储过程”页）</span><span class="sxs-lookup"><span data-stu-id="bff7e-102">Transfer Master Stored Procedures Task Editor (Stored Procedures Page)</span></span>
  <span data-ttu-id="bff7e-103">可以使用“传输主存储过程任务编辑器”对话框的“存储过程”页，指定用于将一个或多个用户定义存储过程从一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中的 **master** 数据库复制到另一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中的 **master** 数据库的属性。</span><span class="sxs-lookup"><span data-stu-id="bff7e-103">Use the **Stored Procedures** page of the **Transfer Master Stored Procedures Task Editor** dialog box to specify properties for copying one or more user-defined stored procedures from the **master** database in one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to a **master** database in another instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bff7e-104">有关此任务的详细信息，请参阅 [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md)。</span><span class="sxs-lookup"><span data-stu-id="bff7e-104">For more information about this task, see [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bff7e-105">此任务只将 **dbo** 拥有的用户定义存储过程从源服务器上的 **master** 数据库传递到目标服务器上的 **master** 数据库。</span><span class="sxs-lookup"><span data-stu-id="bff7e-105">This task transfers only user-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server.</span></span> <span data-ttu-id="bff7e-106">若要在目标服务器上创建存储过程，必须在目标服务器上的 **master** 数据库中授予用户 CREATE PROCEDURE 权限，或者用户必须为目标服务器上 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="bff7e-106">Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bff7e-107">选项</span><span class="sxs-lookup"><span data-stu-id="bff7e-107">Options</span></span>  
 <span data-ttu-id="bff7e-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="bff7e-108">**SourceConnection**</span></span>  
 <span data-ttu-id="bff7e-109">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与源服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="bff7e-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="bff7e-110">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="bff7e-110">**DestinationConnection**</span></span>  
 <span data-ttu-id="bff7e-111">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与目标服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="bff7e-111">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="bff7e-112">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="bff7e-112">**IfObjectExists**</span></span>  
 <span data-ttu-id="bff7e-113">选择该任务应如何处理目标服务器上的 **master** 数据库中已经存在的同名用户定义存储过程。</span><span class="sxs-lookup"><span data-stu-id="bff7e-113">Select how the task should handle user-defined stored procedures of the same name that already exist in the **master** database on the destination server.</span></span>  
  
 <span data-ttu-id="bff7e-114">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="bff7e-114">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="bff7e-115">值</span><span class="sxs-lookup"><span data-stu-id="bff7e-115">Value</span></span>|<span data-ttu-id="bff7e-116">说明</span><span class="sxs-lookup"><span data-stu-id="bff7e-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bff7e-117">**FailTask**</span><span class="sxs-lookup"><span data-stu-id="bff7e-117">**FailTask**</span></span>|<span data-ttu-id="bff7e-118">如果目标服务器上的 **master** 数据库中已存在同名的存储过程，则任务失败。</span><span class="sxs-lookup"><span data-stu-id="bff7e-118">Task fails if stored procedures of the same name already exist in the **master** database on the destination server.</span></span>|  
|<span data-ttu-id="bff7e-119">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="bff7e-119">**Overwrite**</span></span>|<span data-ttu-id="bff7e-120">任务将覆盖目标服务器上的 **master** 数据库中的同名存储过程。</span><span class="sxs-lookup"><span data-stu-id="bff7e-120">Task overwrites stored procedures of the same name in the **master** database on the destination server.</span></span>|  
|<span data-ttu-id="bff7e-121">**Skip**</span><span class="sxs-lookup"><span data-stu-id="bff7e-121">**Skip**</span></span>|<span data-ttu-id="bff7e-122">任务将跳过目标服务器上的 **master** 数据库中存在的同名存储过程。</span><span class="sxs-lookup"><span data-stu-id="bff7e-122">Task skips stored procedures of the same name that exist in the **master** database on the destination server.</span></span>|  
  
 <span data-ttu-id="bff7e-123">**TransferAllStoredProcedures**</span><span class="sxs-lookup"><span data-stu-id="bff7e-123">**TransferAllStoredProcedures**</span></span>  
 <span data-ttu-id="bff7e-124">选择是否应将源服务器上 **master** 数据库中的所有用户定义存储过程复制到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="bff7e-124">Select whether all user-defined stored procedures in the **master** database on the source server should be copied to the destination server.</span></span>  
  
|<span data-ttu-id="bff7e-125">值</span><span class="sxs-lookup"><span data-stu-id="bff7e-125">Value</span></span>|<span data-ttu-id="bff7e-126">说明</span><span class="sxs-lookup"><span data-stu-id="bff7e-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bff7e-127">**True**</span><span class="sxs-lookup"><span data-stu-id="bff7e-127">**True**</span></span>|<span data-ttu-id="bff7e-128">复制 **master** 数据库中的所有用户定义存储过程。</span><span class="sxs-lookup"><span data-stu-id="bff7e-128">Copy all user-defined stored procedures in the **master** database.</span></span>|  
|<span data-ttu-id="bff7e-129">**False**</span><span class="sxs-lookup"><span data-stu-id="bff7e-129">**False**</span></span>|<span data-ttu-id="bff7e-130">仅复制指定的存储过程。</span><span class="sxs-lookup"><span data-stu-id="bff7e-130">Copy only the specified stored procedures.</span></span>|  
  
 <span data-ttu-id="bff7e-131">**StoredProceduresList**</span><span class="sxs-lookup"><span data-stu-id="bff7e-131">**StoredProceduresList**</span></span>  
 <span data-ttu-id="bff7e-132">选择应将源服务器上 **master** 数据库中的哪些用户定义存储过程复制到目标 **master** 数据库。</span><span class="sxs-lookup"><span data-stu-id="bff7e-132">Select which user-defined stored procedures in the **master** database on the source server should be copied to the destination **master** database.</span></span> <span data-ttu-id="bff7e-133">只有在 **TransferAllStoredProcedures** 设置为 **False**时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="bff7e-133">This option is only available when **TransferAllStoredProcedures** is set to **False**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bff7e-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bff7e-134">See Also</span></span>  
 <span data-ttu-id="bff7e-135">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bff7e-135">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="bff7e-136">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="bff7e-136">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="bff7e-137">[传输主存储过程任务编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="bff7e-137">[Transfer Master Stored Procedures Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="bff7e-138">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="bff7e-138">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="bff7e-139">SMO 连接管理器</span><span class="sxs-lookup"><span data-stu-id="bff7e-139">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
