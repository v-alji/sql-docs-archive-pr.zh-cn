---
title: 将文件上载到文件夹 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfb595ed6059436d17cb82262f5d1975a8397dbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586314"
---
# <a name="upload-files-to-a-folder"></a><span data-ttu-id="fbe9a-102">将文件上载到文件夹</span><span class="sxs-lookup"><span data-stu-id="fbe9a-102">Upload Files to a Folder</span></span>
  <span data-ttu-id="fbe9a-103">您可以从文件系统上载文件，然后将其作为托管项存储在报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-103">You can upload files from the file system and store them as managed items in a report server database.</span></span> <span data-ttu-id="fbe9a-104">上载文件时的情况因文件类型而异。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-104">What happens when you upload a file depends on the file type.</span></span>

-   <span data-ttu-id="fbe9a-105">上载 .rdl 文件相当于发布报表。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-105">Uploading an .rdl file is equivalent to publishing a report.</span></span>

-   <span data-ttu-id="fbe9a-106">上载其他任何文件会将该文件作为单个二进制对象添加到报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-106">Uploading any other file adds it to the report server database as a single binary object.</span></span> <span data-ttu-id="fbe9a-107">这些文件作为资源发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-107">These files are published to a report server as a resource.</span></span> <span data-ttu-id="fbe9a-108">资源可以是任意类型的文件。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-108">Resources can be any file type.</span></span> <span data-ttu-id="fbe9a-109">如果文件扩展名与某已知的 MIME 类型相符，则将使用该 MIME 类型的图标来标识资源类型。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-109">If the file extension matches a known MIME type, an icon for that MIME type is used to identify the resource type.</span></span> <span data-ttu-id="fbe9a-110">否则，将使用通用文件图标表示资源。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-110">Otherwise, a generic file icon indicates a resource.</span></span>

> [!NOTE]
>  <span data-ttu-id="fbe9a-111">不能上载报表数据源 (.rds) 文件来创建共享数据源。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-111">You cannot upload a report data source (.rds) file to create a shared data source.</span></span> <span data-ttu-id="fbe9a-112">.rds 文件仅用于报表设计器中。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-112">An .rds file is used only in Report Designer.</span></span> <span data-ttu-id="fbe9a-113">对于通过报表管理器定义和管理的共享数据源项，.rds 文件不提供相关内容。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-113">It cannot provide the content for a shared data source item that you define and manage through Report Manager.</span></span> <span data-ttu-id="fbe9a-114">作为上载的替代方法，可以编写一个基于 .rds 文件创建共享数据源的脚本。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-114">As an alternative to uploading, you can write a script that creates a shared data source based on a .rds file.</span></span>

 <span data-ttu-id="fbe9a-115">上载项的最大文件大小由 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]确定。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-115">The maximum file size for uploaded items is determined by [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span></span> <span data-ttu-id="fbe9a-116">默认情况下，最大大小为 4 MB。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-116">By default, the maximum size is 4 megabytes (MB).</span></span>

 <span data-ttu-id="fbe9a-117">上载到报表服务器数据库的文件将使用以下图标直观地显示在文件夹层次结构中：</span><span class="sxs-lookup"><span data-stu-id="fbe9a-117">Visually, files that you upload to a report server database are represented in the folder hierarchy with the following icons.</span></span>

 <span data-ttu-id="fbe9a-118">![报表图标](../media/hlp-16doc.gif "报表图标")报表图标</span><span class="sxs-lookup"><span data-stu-id="fbe9a-118">![Report icon](../media/hlp-16doc.gif "Report icon") report icon</span></span>

 <span data-ttu-id="fbe9a-119">![模型图标](../media/model-icon.gif "模型图标")报表模型图标</span><span class="sxs-lookup"><span data-stu-id="fbe9a-119">![Model icon](../media/model-icon.gif "Model icon") report model icon</span></span>

 <span data-ttu-id="fbe9a-120">![通用资源图标](../media/hlp-16file.gif "通用资源图标")通用资源图标</span><span class="sxs-lookup"><span data-stu-id="fbe9a-120">![generic resource icon](../media/hlp-16file.gif "generic resource icon") generic resource icon</span></span>

 <span data-ttu-id="fbe9a-121">上载文件时，文件将始终放入当前所选的文件夹。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-121">When you upload a file, it is always placed in the folder that is currently selected.</span></span> <span data-ttu-id="fbe9a-122">您可以首先定位到要包含项的文件夹，也可以先上载文件再将其移至最终位置。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-122">You can navigate to the folder that you want to contain the item first, or you can upload a file and then move it to a final location later.</span></span>

 <span data-ttu-id="fbe9a-123">若要上载文件，请使用报表管理器。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-123">To upload a file, use Report Manager.</span></span> <span data-ttu-id="fbe9a-124">能否将文件上载到报表服务器取决于您的角色分配中包括哪些任务。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-124">Whether you can upload files to a report server depends on tasks that are part of your role assignment.</span></span> <span data-ttu-id="fbe9a-125">如果您使用的是默认安全性，本地管理员可以向报表服务器中添加项。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-125">If you are using default security, local administrators can add items to a report server.</span></span> <span data-ttu-id="fbe9a-126">如果启用了“我的报表”，则拥有“我的报表”文件夹的任何用户都有权将项上载到该文件夹中。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-126">If My Reports is enabled, any user who has a My Reports folder has permission to upload items to that folder.</span></span> <span data-ttu-id="fbe9a-127">如果您使用自定义角色分配，角色分配必须包括支持管理文件夹的任务。</span><span class="sxs-lookup"><span data-stu-id="fbe9a-127">If you use custom role assignments, the role assignment must include tasks that support folder management.</span></span>

|<span data-ttu-id="fbe9a-128">要执行此操作</span><span class="sxs-lookup"><span data-stu-id="fbe9a-128">To do this</span></span>|<span data-ttu-id="fbe9a-129">需包含的任务</span><span class="sxs-lookup"><span data-stu-id="fbe9a-129">Include these tasks</span></span>|
|----------------|-------------------------|
|<span data-ttu-id="fbe9a-130">将 .rdl 文件上载到文件夹中</span><span class="sxs-lookup"><span data-stu-id="fbe9a-130">Upload an .rdl file to a folder</span></span>|<span data-ttu-id="fbe9a-131">管理报表</span><span class="sxs-lookup"><span data-stu-id="fbe9a-131">Manage reports</span></span>|
|<span data-ttu-id="fbe9a-132">将任何文件作为二进制对象上载</span><span class="sxs-lookup"><span data-stu-id="fbe9a-132">Upload any file as a binary object</span></span>|<span data-ttu-id="fbe9a-133">管理资源</span><span class="sxs-lookup"><span data-stu-id="fbe9a-133">Manage resources</span></span>|
|<span data-ttu-id="fbe9a-134">查看文件夹的内容</span><span class="sxs-lookup"><span data-stu-id="fbe9a-134">View the contents of a folder</span></span>|<span data-ttu-id="fbe9a-135">查看资源，查看报表</span><span class="sxs-lookup"><span data-stu-id="fbe9a-135">View resources, View reports</span></span>|

## <a name="see-also"></a><span data-ttu-id="fbe9a-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbe9a-136">See Also</span></span>
 <span data-ttu-id="fbe9a-137">[报表管理器 &#40;SSRS 本机模式&#41;] .。。/report-manager-ssrs-native-mode.md) [授予对本机模式报表服务器](../security/granting-permissions-on-a-native-mode-report-server.md)[任务和权限](../security/tasks-and-permissions.md)的权限[&#40;报表管理器上传文件或报表&#41;](../reports/upload-a-file-or-report-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="fbe9a-137">[Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md) [Granting Permissions on a Native Mode Report Server](../security/granting-permissions-on-a-native-mode-report-server.md) [Tasks and Permissions](../security/tasks-and-permissions.md) [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md)</span></span>


