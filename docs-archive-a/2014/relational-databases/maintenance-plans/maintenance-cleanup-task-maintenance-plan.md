---
title: “清除维护”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.cleanup.f1
helpviewer_keywords:
- Maintenance Cleanup Task dialog box
ms.assetid: 022b679c-6799-4c13-9185-814224a20412
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9023881ff5cf5ba5ddd8c61aa179c5881162bf44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587375"
---
# <a name="maintenance-cleanup-task-maintenance-plan"></a><span data-ttu-id="4d7df-102">“清除维护”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="4d7df-102">Maintenance Cleanup Task (Maintenance Plan)</span></span>
  <span data-ttu-id="4d7df-103">使用 **“‘清除维护’任务”** 可以删除与维护计划相关的旧文件，包括由维护计划文件和数据库备份文件创建的文本报告。</span><span class="sxs-lookup"><span data-stu-id="4d7df-103">Use the **Maintenance Cleanup Task** to remove old files related to maintenance plans, including text reports created by maintenance plans and database backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d7df-104">“清除维护”任务不会自动删除指定目录的子文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="4d7df-104">The Maintenance Cleanup task does not automatically delete files in the subfolders of the specified directory.</span></span> <span data-ttu-id="4d7df-105">此功能减少了使用清除维护任务删除文件的恶意攻击的可能性。</span><span class="sxs-lookup"><span data-stu-id="4d7df-105">This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span> <span data-ttu-id="4d7df-106">如果要删除一级子文件夹中的文件，必须选择“包括一级子文件夹”。</span><span class="sxs-lookup"><span data-stu-id="4d7df-106">If you want to delete files in first-level subfolders, you must select **Include first-level subfolders**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4d7df-107">选项</span><span class="sxs-lookup"><span data-stu-id="4d7df-107">Options</span></span>  
 <span data-ttu-id="4d7df-108">**Connection**</span><span class="sxs-lookup"><span data-stu-id="4d7df-108">**Connection**</span></span>  
 <span data-ttu-id="4d7df-109">显示当前的连接。</span><span class="sxs-lookup"><span data-stu-id="4d7df-109">Displays the current connection.</span></span>  
  
 <span data-ttu-id="4d7df-110">**新建**</span><span class="sxs-lookup"><span data-stu-id="4d7df-110">**New**</span></span>  
 <span data-ttu-id="4d7df-111">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="4d7df-111">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="4d7df-112">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="4d7df-112">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="4d7df-113">**备份文件**</span><span class="sxs-lookup"><span data-stu-id="4d7df-113">**Backup files**</span></span>  
 <span data-ttu-id="4d7df-114">删除备份文件。</span><span class="sxs-lookup"><span data-stu-id="4d7df-114">Delete backup files.</span></span>  
  
 <span data-ttu-id="4d7df-115">**维护计划文本报告**</span><span class="sxs-lookup"><span data-stu-id="4d7df-115">**Maintenance Plan text reports**</span></span>  
 <span data-ttu-id="4d7df-116">删除以前运行的维护计划的文本报告。</span><span class="sxs-lookup"><span data-stu-id="4d7df-116">Delete text reports of previously run maintenance plans.</span></span>  
  
 <span data-ttu-id="4d7df-117">**删除特定文件**</span><span class="sxs-lookup"><span data-stu-id="4d7df-117">**Delete specific file**</span></span>  
 <span data-ttu-id="4d7df-118">删除在“文件名”框中提供的特定文件。</span><span class="sxs-lookup"><span data-stu-id="4d7df-118">Delete the specific file provided in the **File name** box.</span></span>  
  
 <span data-ttu-id="4d7df-119">**文件名**</span><span class="sxs-lookup"><span data-stu-id="4d7df-119">**File name**</span></span>  
 <span data-ttu-id="4d7df-120">要删除的文件的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="4d7df-120">Path and name of the file to be deleted.</span></span>  
  
 <span data-ttu-id="4d7df-121">**搜索文件夹并根据扩展名删除文件**</span><span class="sxs-lookup"><span data-stu-id="4d7df-121">**Search folder and delete files based on an extension**</span></span>  
 <span data-ttu-id="4d7df-122">删除指定文件夹中带有指定扩展名的所有文件。</span><span class="sxs-lookup"><span data-stu-id="4d7df-122">Delete all files with the specified extension in the specified folder.</span></span> <span data-ttu-id="4d7df-123">使用此选项可一次删除多个文件，例如 Tuesday 文件夹中带有 .bak 扩展名的所有备份文件。</span><span class="sxs-lookup"><span data-stu-id="4d7df-123">Use this to delete multiple files at once, such as all backup files with the .bak extension, in the Tuesday folder.</span></span>  
  
 <span data-ttu-id="4d7df-124">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="4d7df-124">**Folder**</span></span>  
 <span data-ttu-id="4d7df-125">要删除的文件所在的文件夹的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="4d7df-125">Path and name of the folder containing the files to be deleted.</span></span>  
  
 <span data-ttu-id="4d7df-126">**文件扩展名**</span><span class="sxs-lookup"><span data-stu-id="4d7df-126">**File extension**</span></span>  
 <span data-ttu-id="4d7df-127">提供要删除的文件的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="4d7df-127">Provide the file extension of the files to be deleted.</span></span>  
  
 <span data-ttu-id="4d7df-128">**包括一级子文件夹**</span><span class="sxs-lookup"><span data-stu-id="4d7df-128">**Include first-level subfolders**</span></span>  
 <span data-ttu-id="4d7df-129">从“文件夹”下的一级子文件夹中删除具有为“文件扩展名”指定的扩展名的文件。</span><span class="sxs-lookup"><span data-stu-id="4d7df-129">Delete files with the extension specified for **File extension** from first-level subfolders under **Folder**.</span></span>  
  
 <span data-ttu-id="4d7df-130">**在任务运行时根据文件保留时间删除文件**</span><span class="sxs-lookup"><span data-stu-id="4d7df-130">**Delete files based on the age of the file at task run time**</span></span>  
 <span data-ttu-id="4d7df-131">通过在“删除文件，如果其保留时间超过”框中提供数字和时间单位，指定将要删除的文件所要保留的最短时间。</span><span class="sxs-lookup"><span data-stu-id="4d7df-131">Specify the minimum age of the files that you want to delete by providing a number, and unit of time in the **Delete files older than the following** box.</span></span>  
  
 <span data-ttu-id="4d7df-132">**删除文件，如果其保留时间超过**</span><span class="sxs-lookup"><span data-stu-id="4d7df-132">**Delete files older than the following**</span></span>  
 <span data-ttu-id="4d7df-133">通过提供数字和时间单位（天、周、月或年），指定将要删除的文件所要保留的最短时间。</span><span class="sxs-lookup"><span data-stu-id="4d7df-133">Specify the minimum age of the files that you want to delete by providing a number, and unit of time (Day, Week, Month, or Year).</span></span> <span data-ttu-id="4d7df-134">保留时间长于指定时间长度的文件将被删除。</span><span class="sxs-lookup"><span data-stu-id="4d7df-134">Files older than the time frame specified will be deleted.</span></span>  
  
 <span data-ttu-id="4d7df-135">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="4d7df-135">**View T-SQL**</span></span>  
 <span data-ttu-id="4d7df-136">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="4d7df-136">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d7df-137">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="4d7df-137">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="4d7df-138">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="4d7df-138">New Connection Dialog Box</span></span>  
 <span data-ttu-id="4d7df-139">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="4d7df-139">**Connection name**</span></span>  
 <span data-ttu-id="4d7df-140">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="4d7df-140">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="4d7df-141">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="4d7df-141">**Select or enter a server name**</span></span>  
 <span data-ttu-id="4d7df-142">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="4d7df-142">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="4d7df-143">**...**</span><span class="sxs-lookup"><span data-stu-id="4d7df-143">**...**</span></span>  
 <span data-ttu-id="4d7df-144">选择以查看可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="4d7df-144">Select to view the list of available servers.</span></span>  
  
 <span data-ttu-id="4d7df-145">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="4d7df-145">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="4d7df-146">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="4d7df-146">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="4d7df-147">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="4d7df-147">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="4d7df-148">使用 Microsoft Windows 身份验证连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="4d7df-148">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="4d7df-149">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="4d7df-149">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="4d7df-150">使用 SQL Server 身份验证连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="4d7df-150">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using SQL Server Authentication.</span></span> <span data-ttu-id="4d7df-151">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="4d7df-151">This option is not available.</span></span>  
  
 <span data-ttu-id="4d7df-152">**用户名**</span><span class="sxs-lookup"><span data-stu-id="4d7df-152">**User name**</span></span>  
 <span data-ttu-id="4d7df-153">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="4d7df-153">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="4d7df-154">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="4d7df-154">This option is not available.</span></span>  
  
 <span data-ttu-id="4d7df-155">**密码**</span><span class="sxs-lookup"><span data-stu-id="4d7df-155">**Password**</span></span>  
 <span data-ttu-id="4d7df-156">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="4d7df-156">Provide a password to use when authenticating.</span></span> <span data-ttu-id="4d7df-157">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="4d7df-157">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7df-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d7df-158">See Also</span></span>  
 [<span data-ttu-id="4d7df-159">维护计划</span><span class="sxs-lookup"><span data-stu-id="4d7df-159">Maintenance Plans</span></span>](maintenance-plans.md)  
  
  
