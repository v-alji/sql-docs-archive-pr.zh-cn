---
title: 传输登录名任务编辑器 (登录页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.logins.f1
helpviewer_keywords:
- Transfer Logins Task Editor
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33fea6c78df75b7eebe8987f952dce33bdc4407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591944"
---
# <a name="transfer-logins-task-editor-logins-page"></a><span data-ttu-id="0ea18-102">传输登录名任务编辑器（“登录名”页）</span><span class="sxs-lookup"><span data-stu-id="0ea18-102">Transfer Logins Task Editor (Logins Page)</span></span>
  <span data-ttu-id="0ea18-103">可以使用 **“传输登录名任务编辑器”** 对话框的 **“登录名”** 页，指定用于将一个或多个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录名从一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例复制到另一个实例的属性。</span><span class="sxs-lookup"><span data-stu-id="0ea18-103">Use the **Logins** page of the **Transfer Logins Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="0ea18-104">有关此任务的详细信息，请参阅 [Transfer Logins Task](control-flow/transfer-logins-task.md)。</span><span class="sxs-lookup"><span data-stu-id="0ea18-104">For more information about this task, see [Transfer Logins Task](control-flow/transfer-logins-task.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0ea18-105">执行传输登录名任务时，在目标服务器上创建的登录名将具有随机的密码，并且密码处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="0ea18-105">When the Transfer Logins task is executed, logins are created on the destination server with random passwords and the passwords are disabled.</span></span> <span data-ttu-id="0ea18-106">只有在 **sysadmin** 固定服务器角色的某个成员更改并启用这些登录名的密码后，才可使用这些登录名。</span><span class="sxs-lookup"><span data-stu-id="0ea18-106">To use these logins, a member of the **sysadmin** fixed server role must change the passwords and then enable them.</span></span> <span data-ttu-id="0ea18-107">无法传输 **sa** 登录名。</span><span class="sxs-lookup"><span data-stu-id="0ea18-107">The **sa** login cannot be transferred.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ea18-108">选项</span><span class="sxs-lookup"><span data-stu-id="0ea18-108">Options</span></span>  
 <span data-ttu-id="0ea18-109">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="0ea18-109">**SourceConnection**</span></span>  
 <span data-ttu-id="0ea18-110">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与源服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="0ea18-110">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="0ea18-111">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="0ea18-111">**DestinationConnection**</span></span>  
 <span data-ttu-id="0ea18-112">从列表中选择一个 SMO 连接管理器，或单击“\<New connection...>”以创建到目标服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="0ea18-112">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="0ea18-113">**LoginsToTransfer**</span><span class="sxs-lookup"><span data-stu-id="0ea18-113">**LoginsToTransfer**</span></span>  
 <span data-ttu-id="0ea18-114">选择要从源服务器复制到目标服务器的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="0ea18-114">Select the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins to copy from the source to the destination server.</span></span> <span data-ttu-id="0ea18-115">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="0ea18-115">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="0ea18-116">值</span><span class="sxs-lookup"><span data-stu-id="0ea18-116">Value</span></span>|<span data-ttu-id="0ea18-117">说明</span><span class="sxs-lookup"><span data-stu-id="0ea18-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0ea18-118">**AllLogins**</span><span class="sxs-lookup"><span data-stu-id="0ea18-118">**AllLogins**</span></span>|<span data-ttu-id="0ea18-119">源服务器上的所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录名都将复制到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="0ea18-119">All [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins on the source server will be copied to the destination server.</span></span>|  
|<span data-ttu-id="0ea18-120">**SelectedLogins**</span><span class="sxs-lookup"><span data-stu-id="0ea18-120">**SelectedLogins**</span></span>|<span data-ttu-id="0ea18-121">只有通过 **LoginsList** 指定的登录名才会复制到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="0ea18-121">Only logins specified with **LoginsList** will be copied to the destination server.</span></span>|  
|<span data-ttu-id="0ea18-122">**AllLoginsFromSelectedDatabases**</span><span class="sxs-lookup"><span data-stu-id="0ea18-122">**AllLoginsFromSelectedDatabases**</span></span>|<span data-ttu-id="0ea18-123">通过 **DatabasesList** 指定的数据库中的所有登录名都将复制到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="0ea18-123">All logins from the databases specified with **DatabasesList** will be copied to the destination server.</span></span>|  
  
 <span data-ttu-id="0ea18-124">**LoginsList**</span><span class="sxs-lookup"><span data-stu-id="0ea18-124">**LoginsList**</span></span>  
 <span data-ttu-id="0ea18-125">选择源服务器上要复制到目标服务器的登录名。</span><span class="sxs-lookup"><span data-stu-id="0ea18-125">Select the logins on the source server to be copied to the destination server.</span></span> <span data-ttu-id="0ea18-126">只有为 **LoginsToTransfer** 选择了 **SelectedLogins**时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="0ea18-126">This option is only available when **SelectedLogins** is selected for **LoginsToTransfer**.</span></span>  
  
 <span data-ttu-id="0ea18-127">**DatabasesList**</span><span class="sxs-lookup"><span data-stu-id="0ea18-127">**DatabasesList**</span></span>  
 <span data-ttu-id="0ea18-128">选择源服务器上包含要复制到目标服务器的登录名的数据库。</span><span class="sxs-lookup"><span data-stu-id="0ea18-128">Select the databases on the source server that contain logins to be copied to the destination server.</span></span> <span data-ttu-id="0ea18-129">只有为 **LoginsToTransfer** 选择了 **AllLoginsFromSelectedDatabases**时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="0ea18-129">This option is only available when **AllLoginsFromSelectedDatabases** is selected for **LoginsToTransfer**.</span></span>  
  
 <span data-ttu-id="0ea18-130">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="0ea18-130">**IfObjectExists**</span></span>  
 <span data-ttu-id="0ea18-131">选择该任务应如何处理目标服务器上已经存在的同名登录名。</span><span class="sxs-lookup"><span data-stu-id="0ea18-131">Select how the task should handle logins of the same name that already exist on the destination server.</span></span>  
  
 <span data-ttu-id="0ea18-132">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="0ea18-132">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="0ea18-133">值</span><span class="sxs-lookup"><span data-stu-id="0ea18-133">Value</span></span>|<span data-ttu-id="0ea18-134">说明</span><span class="sxs-lookup"><span data-stu-id="0ea18-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0ea18-135">**FailTask**</span><span class="sxs-lookup"><span data-stu-id="0ea18-135">**FailTask**</span></span>|<span data-ttu-id="0ea18-136">如果目标服务器上已存在同名的登录名，则任务失败。</span><span class="sxs-lookup"><span data-stu-id="0ea18-136">Task fails if logins of the same name already exist on the destination server.</span></span>|  
|<span data-ttu-id="0ea18-137">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="0ea18-137">**Overwrite**</span></span>|<span data-ttu-id="0ea18-138">任务将覆盖目标服务器上同名的登录名。</span><span class="sxs-lookup"><span data-stu-id="0ea18-138">Task overwrites logins of the same name on the destination server.</span></span>|  
|<span data-ttu-id="0ea18-139">**Skip**</span><span class="sxs-lookup"><span data-stu-id="0ea18-139">**Skip**</span></span>|<span data-ttu-id="0ea18-140">任务将跳过目标服务器上存在的同名登录名。</span><span class="sxs-lookup"><span data-stu-id="0ea18-140">Task skips logins of the same name that exist on the destination server.</span></span>|  
  
 <span data-ttu-id="0ea18-141">**CopySids**</span><span class="sxs-lookup"><span data-stu-id="0ea18-141">**CopySids**</span></span>  
 <span data-ttu-id="0ea18-142">选择是否应将与登录名相关联的安全标识符复制到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="0ea18-142">Select whether the security identifiers associated with the logins should be copied to the destination server.</span></span> <span data-ttu-id="0ea18-143">如果传输登录名任务与传输数据库任务一起使用，则必须将**CopySids** 设置为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="0ea18-143">**CopySids** must be set to **True** if the Transfer Logins task is used along with the Transfer Database task.</span></span> <span data-ttu-id="0ea18-144">否则，传输的数据库将不能识别复制的登录名。</span><span class="sxs-lookup"><span data-stu-id="0ea18-144">Otherwise, the copied logins will not be recognized by the transferred database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea18-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ea18-145">See Also</span></span>  
 <span data-ttu-id="0ea18-146">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0ea18-146">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="0ea18-147">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="0ea18-147">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="0ea18-148">[传输登录名任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="0ea18-148">[Transfer Logins Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="0ea18-149">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="0ea18-149">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="0ea18-150">[SMO 连接管理器](connection-manager/smo-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0ea18-150">[SMO Connection Manager](connection-manager/smo-connection-manager.md) </span></span>  
 <span data-ttu-id="0ea18-151">[强密码](../relational-databases/security/strong-passwords.md) </span><span class="sxs-lookup"><span data-stu-id="0ea18-151">[Strong Passwords](../relational-databases/security/strong-passwords.md) </span></span>  
 [<span data-ttu-id="0ea18-152">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="0ea18-152">Security Considerations for a SQL Server Installation</span></span>](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
