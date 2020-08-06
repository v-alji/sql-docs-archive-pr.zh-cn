---
title: 更新资源（报表管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- updating resources
- resources [Reporting Services], updating
ms.assetid: d21f7493-bcf7-4e9e-9886-55ebdc1f1037
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0fca59e476c2820b715ff46729784edc562f74d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586315"
---
# <a name="update-a-resource-report-manager"></a><span data-ttu-id="84af7-102">更新资源（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="84af7-102">Update a Resource (Report Manager)</span></span>
  <span data-ttu-id="84af7-103">通过将资源替换为新资源，可以更新资源。</span><span class="sxs-lookup"><span data-stu-id="84af7-103">You can update a resource by replacing it with a newer version.</span></span> <span data-ttu-id="84af7-104">资源是存储在报表服务器上的项，包含您上载的文件中的内容。</span><span class="sxs-lookup"><span data-stu-id="84af7-104">Resources are items stored on a report server that contain content from a file that you upload.</span></span> <span data-ttu-id="84af7-105">通过向现有资源中导入新的文件内容或其他文件内容，即可替换现有资源。</span><span class="sxs-lookup"><span data-stu-id="84af7-105">You can replace an existing resource by importing new or different file content into the existing resource.</span></span> <span data-ttu-id="84af7-106">通过更新资源，可以在保留资源的现有属性和安全设置的同时更新内容。</span><span class="sxs-lookup"><span data-stu-id="84af7-106">Updating a resource provides a way to update content while preserving existing properties and security settings on the resource.</span></span>  
  
### <a name="to-update-a-resource"></a><span data-ttu-id="84af7-107">更新资源</span><span class="sxs-lookup"><span data-stu-id="84af7-107">To update a resource</span></span>  
  
1.  <span data-ttu-id="84af7-108">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="84af7-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="84af7-109">在报表管理器中，导航或搜索到要更新的资源。</span><span class="sxs-lookup"><span data-stu-id="84af7-109">In Report Manager, navigate to or search for the resource you want to update.</span></span>  
  
3.  <span data-ttu-id="84af7-110">单击该资源，将其在 **“视图”** 页中打开。</span><span class="sxs-lookup"><span data-stu-id="84af7-110">Click the resource to open it in the **View** page.</span></span>  
  
4.  <span data-ttu-id="84af7-111">单击 **“属性”** 以打开 **“常规”** 属性页。</span><span class="sxs-lookup"><span data-stu-id="84af7-111">Click **Properties** to open the **General** properties page.</span></span>  
  
5.  <span data-ttu-id="84af7-112">单击 **“替换”** 以打开 **“导入资源”** 页。</span><span class="sxs-lookup"><span data-stu-id="84af7-112">Click **Replace** to open the **Import Resource** page.</span></span>  
  
6.  <span data-ttu-id="84af7-113">单击“浏览” 。</span><span class="sxs-lookup"><span data-stu-id="84af7-113">Click **Browse**.</span></span>  
  
7.  <span data-ttu-id="84af7-114">选择要用于替换当前资源的文件。</span><span class="sxs-lookup"><span data-stu-id="84af7-114">Select the file that you want to use to replace the current resource.</span></span> <span data-ttu-id="84af7-115">您可以使用资源文件的更新版本，或指定其他名称或其他文件类型的文件。</span><span class="sxs-lookup"><span data-stu-id="84af7-115">You can use an updated version of the resource file, or specify a file with a different name or file type.</span></span>  
  
8.  <span data-ttu-id="84af7-116">单击 **“确定”** 上载资源文件，关闭 **“导入资源”** 页，再保存对报表服务器的更改。</span><span class="sxs-lookup"><span data-stu-id="84af7-116">Click **OK** to upload the resource file, close the **Import Resource** page, and save your changes to the report server.</span></span>  
  
 <span data-ttu-id="84af7-117">如果正在更新的资源包含某个报表中所使用的图像，则需要刷新该报表，才可以看到更新后的图像。</span><span class="sxs-lookup"><span data-stu-id="84af7-117">If the resource you are updating contains an image that is used in a report, you need to refresh the report to see the updated image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84af7-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84af7-118">See Also</span></span>  
 <span data-ttu-id="84af7-119">["内容" 页 &#40;报表管理器&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="84af7-119">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="84af7-120">[报表管理器 &#40;上传文件页&#41;](../upload-file-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="84af7-120">[Upload File Page &#40;Report Manager&#41;](../upload-file-page-report-manager.md) </span></span>  
 <span data-ttu-id="84af7-121">[将文件上传到文件夹](upload-files-to-a-folder.md) </span><span class="sxs-lookup"><span data-stu-id="84af7-121">[Upload Files to a Folder](upload-files-to-a-folder.md) </span></span>  
 [<span data-ttu-id="84af7-122">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="84af7-122">Report Manager F1 Help</span></span>](../report-manager-f1-help.md)  
  
  
