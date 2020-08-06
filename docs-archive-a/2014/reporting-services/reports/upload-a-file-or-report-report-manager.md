---
title: 上传文件或报表（报表管理器）| Microsoft Docs
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
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 119e2b22976dc227e017b81a59b698cf9eb7457f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579476"
---
# <a name="upload-a-file-or-report-report-manager"></a><span data-ttu-id="0507c-102">上载文件或报表（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="0507c-102">Upload a File or Report (Report Manager)</span></span>
  <span data-ttu-id="0507c-103">报表管理器提供上载功能，因而您可以将报表、模型以及其他文件添加到报表服务器而不必从客户端应用程序发布这些项。</span><span class="sxs-lookup"><span data-stu-id="0507c-103">Report Manager provides an upload feature so that you can add reports, models, and other files to a report server without having to publish those items from a client application.</span></span> <span data-ttu-id="0507c-104">从文件系统上载的文件会存储为报表服务器上的项。</span><span class="sxs-lookup"><span data-stu-id="0507c-104">Files that you upload from the file system are stored as items on the report server.</span></span> <span data-ttu-id="0507c-105">所上载的文件类型决定存储方式：</span><span class="sxs-lookup"><span data-stu-id="0507c-105">The type of file you upload determines how it is stored:</span></span>  
  
-   <span data-ttu-id="0507c-106">.rdl 文件存储为报表。</span><span class="sxs-lookup"><span data-stu-id="0507c-106">.rdl files are stored as reports.</span></span>  
  
-   <span data-ttu-id="0507c-107">.smdl 文件存储为报表模型。</span><span class="sxs-lookup"><span data-stu-id="0507c-107">.smdl files are stored as report models.</span></span>  
  
-   <span data-ttu-id="0507c-108">包括共享数据源 (.rds) 文件在内的所有其他文件都上载为资源。</span><span class="sxs-lookup"><span data-stu-id="0507c-108">All other files, including shared data source (.rds) files, are uploaded as resources.</span></span> <span data-ttu-id="0507c-109">报表服务器不会处理资源，但是如果报表服务器支持 MIME 文件类型，则可以通过报表管理器来查看资源。</span><span class="sxs-lookup"><span data-stu-id="0507c-109">Resources are not processed by a report server, but can be viewed in Report Manager if the report server supports the MIME type of the file.</span></span>  
  
### <a name="to-upload-a-file-or-report"></a><span data-ttu-id="0507c-110">上载文件或报表</span><span class="sxs-lookup"><span data-stu-id="0507c-110">To upload a file or report</span></span>  
  
1.  <span data-ttu-id="0507c-111">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="0507c-111">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="0507c-112">在报表管理器中，导航到 "**内容**" 页。</span><span class="sxs-lookup"><span data-stu-id="0507c-112">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="0507c-113">导航到要向其中添加项的文件夹。</span><span class="sxs-lookup"><span data-stu-id="0507c-113">Navigate to the folder to which you want to add an item.</span></span>  
  
3.  <span data-ttu-id="0507c-114">单击 **“上载文件”**。</span><span class="sxs-lookup"><span data-stu-id="0507c-114">Click **Upload File**.</span></span>  
  
4.  <span data-ttu-id="0507c-115">单击 **“浏览”** 以选择要上载的文件。</span><span class="sxs-lookup"><span data-stu-id="0507c-115">Click **Browse** to select a file to upload.</span></span> <span data-ttu-id="0507c-116">可以上载报表定义文件、图像、文档或任何要在报表服务器上可用的文件。</span><span class="sxs-lookup"><span data-stu-id="0507c-116">You can upload a report definition file, an image, a document, or any file that you want to make available on the report server.</span></span>  
  
5.  <span data-ttu-id="0507c-117">键入新项的名称。</span><span class="sxs-lookup"><span data-stu-id="0507c-117">Type a name for the new item.</span></span> <span data-ttu-id="0507c-118">项名称可以包括空格，但不能包括保留字符: ; ?</span><span class="sxs-lookup"><span data-stu-id="0507c-118">An item name can include spaces, but cannot include the reserved characters: ; ?</span></span> <span data-ttu-id="0507c-119">： \@ & = +，$/\* \< > |。</span><span class="sxs-lookup"><span data-stu-id="0507c-119">: \@ & = + , $ / \* \< > |.</span></span>  
  
6.  <span data-ttu-id="0507c-120">若要用新项替换现有项，请选择 **“如果该项已存在，则覆盖该项”**。</span><span class="sxs-lookup"><span data-stu-id="0507c-120">If you want to replace an existing item with the new item, select **Overwrite item if it exists**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0507c-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0507c-121">See Also</span></span>  
 <span data-ttu-id="0507c-122">[创建、删除或修改共享数据源 &#40;报表管理器&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0507c-122">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="0507c-123">["内容" 页 &#40;报表管理器&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0507c-123">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="0507c-124">[报表管理器 &#40;上传文件页&#41;](../upload-file-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0507c-124">[Upload File Page &#40;Report Manager&#41;](../upload-file-page-report-manager.md) </span></span>  
 [<span data-ttu-id="0507c-125">将文件上载到文件夹</span><span class="sxs-lookup"><span data-stu-id="0507c-125">Upload Files to a Folder</span></span>](../report-server/upload-files-to-a-folder.md)  
  
  
