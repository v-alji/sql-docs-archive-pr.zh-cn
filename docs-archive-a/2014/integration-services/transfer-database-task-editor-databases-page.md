---
title: 传输数据库任务编辑器 (数据库 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.database.f1
helpviewer_keywords:
- Transfer Database Task Editor
ms.assetid: ccdb74d0-4bea-420c-a726-2e0eb8957e0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df4452e28a32463a7825e9c64cfd053f98c53ee8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682351"
---
# <a name="transfer-database-task-editor-databases-page"></a><span data-ttu-id="3f601-102">传输数据库任务编辑器（“数据库”页）</span><span class="sxs-lookup"><span data-stu-id="3f601-102">Transfer Database Task Editor (Databases Page)</span></span>
  <span data-ttu-id="3f601-103">使用 **“传输数据库任务编辑器”** 对话框的 **“数据库”** 页可为传输数据库任务涉及的源数据库和目标数据库指定属性。</span><span class="sxs-lookup"><span data-stu-id="3f601-103">Use the **Databases** page of the **Transfer Database Task Editor** dialog box to specify properties for the source and destination databases involved in the Transfer Database task.</span></span> <span data-ttu-id="3f601-104">传输数据库任务将在两个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例之间复制或移动 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]数据库。</span><span class="sxs-lookup"><span data-stu-id="3f601-104">The Transfer Database task copies or moves a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database between two instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3f601-105">此任务还可以用来复制同一个服务器上的数据库。</span><span class="sxs-lookup"><span data-stu-id="3f601-105">This task can also be used to copy a database within the same server.</span></span> <span data-ttu-id="3f601-106">有关此任务的详细信息，请参阅 [传输数据库任务](control-flow/transfer-database-task.md)。</span><span class="sxs-lookup"><span data-stu-id="3f601-106">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3f601-107">选项</span><span class="sxs-lookup"><span data-stu-id="3f601-107">Options</span></span>  
 <span data-ttu-id="3f601-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="3f601-108">**SourceConnection**</span></span>  
 <span data-ttu-id="3f601-109">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与源服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="3f601-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="3f601-110">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="3f601-110">**DestinationConnection**</span></span>  
 <span data-ttu-id="3f601-111">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与目标服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="3f601-111">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="3f601-112">**DestinationDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="3f601-112">**DestinationDatabaseName**</span></span>  
 <span data-ttu-id="3f601-113">指定目标服务器上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3f601-113">Specify the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database on the destination server.</span></span>  
  
 <span data-ttu-id="3f601-114">若要使用源数据库名称自动填充此字段，请首先指定 **SourceConnection** 和 **SourceDatabaseName** 。</span><span class="sxs-lookup"><span data-stu-id="3f601-114">To automatically populate this field with the source database name, specify the **SourceConnection** and **SourceDatabaseName** first.</span></span>  
  
 <span data-ttu-id="3f601-115">若要重命名目标服务器上的数据库，请在此字段中键入新名称。</span><span class="sxs-lookup"><span data-stu-id="3f601-115">To rename the database on the destination server, type the new name in this field.</span></span>  
  
 <span data-ttu-id="3f601-116">**DestinationDatabaseFiles**</span><span class="sxs-lookup"><span data-stu-id="3f601-116">**DestinationDatabaseFiles**</span></span>  
 <span data-ttu-id="3f601-117">指定目标服务器上数据库文件的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="3f601-117">Specifies the names and locations of the database files on the destination server.</span></span>  
  
 <span data-ttu-id="3f601-118">若要使用源数据库文件的名称和位置自动填充此字段，请首先指定 **SourceConnection**、 **SourceDatabaseName**和 **SourceDatabaseFiles** 。</span><span class="sxs-lookup"><span data-stu-id="3f601-118">To automatically populate this field with the source database file names and locations, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first.</span></span>  
  
 <span data-ttu-id="3f601-119">若要对目标服务器上的数据库文件进行重命名或为其指定新位置，请使用源数据库信息填充此字段，再单击浏览按钮。</span><span class="sxs-lookup"><span data-stu-id="3f601-119">To rename the database files or to specify the new locations on the destination server, populate this field with the source database information, and then click the browse button.</span></span> <span data-ttu-id="3f601-120">在 **“目标数据库文件”** 对话框中，编辑 **“目标文件”** 、 **“目标文件夹”** 或 **“网络文件共享”** 。</span><span class="sxs-lookup"><span data-stu-id="3f601-120">In the **Destination database files** dialog box, edit the **Destination File**, **Destination Folder**, or **Network File Share**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f601-121">如果使用浏览按钮来定位数据库文件，则会使用本地驱动器表示法输入文件位置：例如，c:\\。</span><span class="sxs-lookup"><span data-stu-id="3f601-121">If you locate the database files by using the browse button, the file location is entered using the local drive notation: for example, c:\\.</span></span> <span data-ttu-id="3f601-122">您必须将其替换为网络共享表示法（包括计算机名称和共享名称）。</span><span class="sxs-lookup"><span data-stu-id="3f601-122">You must replace this with the network share notation, including the computer name and share name.</span></span> <span data-ttu-id="3f601-123">如果使用默认的管理共享，您必须使用 $ 表示法，并且必须具有对该共享位置的管理权限。</span><span class="sxs-lookup"><span data-stu-id="3f601-123">If the default administrative share is used, you must use the $ notation, and have administrative access to the share.</span></span>  
  
 <span data-ttu-id="3f601-124">**DestinationOverwrite**</span><span class="sxs-lookup"><span data-stu-id="3f601-124">**DestinationOverwrite**</span></span>  
 <span data-ttu-id="3f601-125">指定是否可以覆盖目标服务器上的数据库。</span><span class="sxs-lookup"><span data-stu-id="3f601-125">Specify whether the database on the destination server can be overwritten.</span></span>  
  
 <span data-ttu-id="3f601-126">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="3f601-126">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="3f601-127">值</span><span class="sxs-lookup"><span data-stu-id="3f601-127">Value</span></span>|<span data-ttu-id="3f601-128">说明</span><span class="sxs-lookup"><span data-stu-id="3f601-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3f601-129">**True**</span><span class="sxs-lookup"><span data-stu-id="3f601-129">**True**</span></span>|<span data-ttu-id="3f601-130">覆盖目标服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="3f601-130">Overwrite destination server database.</span></span>|  
|<span data-ttu-id="3f601-131">**False**</span><span class="sxs-lookup"><span data-stu-id="3f601-131">**False**</span></span>|<span data-ttu-id="3f601-132">不覆盖目标服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="3f601-132">Do not overwrite destination server database.</span></span>|  
  
> [!CAUTION]  
>  <span data-ttu-id="3f601-133">如果为 **DestinationOverwrite** 指定 **True**，则会覆盖目标服务器数据库中的数据，这可能导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="3f601-133">The data in the destination server database will be overwritten if you specify **True** for **DestinationOverwrite**, which may result in data loss.</span></span> <span data-ttu-id="3f601-134">若要避免数据丢失，请在执行传输数据库任务之前将目标服务器数据库备份到其他位置。</span><span class="sxs-lookup"><span data-stu-id="3f601-134">To avoid this, back up the destination server database to another location before executing the Transfer Database task.</span></span>  
  
 <span data-ttu-id="3f601-135">**Action**</span><span class="sxs-lookup"><span data-stu-id="3f601-135">**Action**</span></span>  
 <span data-ttu-id="3f601-136">指定该任务是将数据库“复制”到目标服务器还是“移动”到目标服务器   。</span><span class="sxs-lookup"><span data-stu-id="3f601-136">Specify whether the task will **Copy** or **Move** the database to the destination server.</span></span>  
  
 <span data-ttu-id="3f601-137">**方法**</span><span class="sxs-lookup"><span data-stu-id="3f601-137">**Method**</span></span>  
 <span data-ttu-id="3f601-138">指定是在源服务器上的数据库处于在线模式时执行任务还是在其处于离线模式时执行任务。</span><span class="sxs-lookup"><span data-stu-id="3f601-138">Specify whether the task will be executed while the database on the source server is in online or offline mode.</span></span>  
  
 <span data-ttu-id="3f601-139">若要使用离线模式传输数据库，运行包的用户必须是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="3f601-139">To transfer a database using offline mode, the user that runs the package must be a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="3f601-140">若要使用在线模式传输数据库，运行包的用户必须是 **sysadmin** 固定服务器角色的成员或是所选数据库的数据库所有者 (**dbo**)。</span><span class="sxs-lookup"><span data-stu-id="3f601-140">To transfer a database using the online mode, the user that runs the package must be a member of the **sysadmin** fixed server role, or the database owner (**dbo**) of the selected database.</span></span>  
  
 <span data-ttu-id="3f601-141">**SourceDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="3f601-141">**SourceDatabaseName**</span></span>  
 <span data-ttu-id="3f601-142">选择要复制或移动的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3f601-142">Select the name of the database to be copied or moved.</span></span>  
  
 <span data-ttu-id="3f601-143">**SourceDatabaseFiles**</span><span class="sxs-lookup"><span data-stu-id="3f601-143">**SourceDatabaseFiles**</span></span>  
 <span data-ttu-id="3f601-144">单击浏览按钮来选择数据库文件。</span><span class="sxs-lookup"><span data-stu-id="3f601-144">Click the browse button to select the database files.</span></span>  
  
 <span data-ttu-id="3f601-145">**ReattachSourceDatabase**</span><span class="sxs-lookup"><span data-stu-id="3f601-145">**ReattachSourceDatabase**</span></span>  
 <span data-ttu-id="3f601-146">指定在发生错误时该任务是否将尝试重新附加源数据库。</span><span class="sxs-lookup"><span data-stu-id="3f601-146">Specify whether the task will attempt to reattach the source database if a failure occurs.</span></span>  
  
 <span data-ttu-id="3f601-147">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="3f601-147">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="3f601-148">值</span><span class="sxs-lookup"><span data-stu-id="3f601-148">Value</span></span>|<span data-ttu-id="3f601-149">说明</span><span class="sxs-lookup"><span data-stu-id="3f601-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3f601-150">**True**</span><span class="sxs-lookup"><span data-stu-id="3f601-150">**True**</span></span>|<span data-ttu-id="3f601-151">重新附加源数据库。</span><span class="sxs-lookup"><span data-stu-id="3f601-151">Reattach source database.</span></span>|  
|<span data-ttu-id="3f601-152">**False**</span><span class="sxs-lookup"><span data-stu-id="3f601-152">**False**</span></span>|<span data-ttu-id="3f601-153">不重新附加源数据库。</span><span class="sxs-lookup"><span data-stu-id="3f601-153">Do not reattach source database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f601-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f601-154">See Also</span></span>  
 <span data-ttu-id="3f601-155">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3f601-155">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3f601-156">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="3f601-156">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="3f601-157">[传输数据库任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="3f601-157">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="3f601-158">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="3f601-158">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="3f601-159">SMO 连接管理器</span><span class="sxs-lookup"><span data-stu-id="3f601-159">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
