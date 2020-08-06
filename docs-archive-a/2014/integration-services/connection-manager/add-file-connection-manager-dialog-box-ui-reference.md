---
title: “添加文件连接管理器”对话框 UI 参考 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnection.f1
helpviewer_keywords:
- Add File Connection Manager
ms.assetid: 9370bfb5-5993-4ad8-a9cd-2de53f320f34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 044d8e2eaae9db17d7155cb354f8d009750f44d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692472"
---
# <a name="add-file-connection-manager-dialog-box-ui-reference"></a><span data-ttu-id="b2454-102">“添加文件连接管理器”对话框 UI 参考</span><span class="sxs-lookup"><span data-stu-id="b2454-102">Add File Connection Manager Dialog Box UI Reference</span></span>
  <span data-ttu-id="b2454-103">可以使用 **“添加文件连接管理器”** 对话框定义与一组文件或文件夹的连接。</span><span class="sxs-lookup"><span data-stu-id="b2454-103">Use the **Add File Connection Manager** dialog box to define a connection to a group of files or folders.</span></span>  
  
 <span data-ttu-id="b2454-104">若要了解有关多文件连接管理器的详细信息，请参阅 [Multiple Files Connection Manager](multiple-files-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="b2454-104">To learn more about the Multiple Files connection manager, see [Multiple Files Connection Manager](multiple-files-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2454-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的内置任务和数据流组件不使用多文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b2454-105">The built-in tasks and data flow components in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not use the Multiple Files connection manager.</span></span> <span data-ttu-id="b2454-106">但是，可以在脚本任务或脚本组件中使用此连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b2454-106">However, you can use this connection manager in the Script task or Script component.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b2454-107">选项</span><span class="sxs-lookup"><span data-stu-id="b2454-107">Options</span></span>  
 <span data-ttu-id="b2454-108">**使用类型**</span><span class="sxs-lookup"><span data-stu-id="b2454-108">**Usage type**</span></span>  
 <span data-ttu-id="b2454-109">指定要用于多个文件连接管理器的文件类型。</span><span class="sxs-lookup"><span data-stu-id="b2454-109">Specify the type of files to use for the multiple files connection manager.</span></span>  
  
|<span data-ttu-id="b2454-110">值</span><span class="sxs-lookup"><span data-stu-id="b2454-110">Value</span></span>|<span data-ttu-id="b2454-111">说明</span><span class="sxs-lookup"><span data-stu-id="b2454-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b2454-112">**创建文件**</span><span class="sxs-lookup"><span data-stu-id="b2454-112">**Create files**</span></span>|<span data-ttu-id="b2454-113">连接管理器将创建文件。</span><span class="sxs-lookup"><span data-stu-id="b2454-113">The connection manager will create the files.</span></span>|  
|<span data-ttu-id="b2454-114">**现有文件**</span><span class="sxs-lookup"><span data-stu-id="b2454-114">**Existing files**</span></span>|<span data-ttu-id="b2454-115">连接管理器将使用现有文件。</span><span class="sxs-lookup"><span data-stu-id="b2454-115">The connection manager will use existing files.</span></span>|  
|<span data-ttu-id="b2454-116">**创建文件夹**</span><span class="sxs-lookup"><span data-stu-id="b2454-116">**Create folders**</span></span>|<span data-ttu-id="b2454-117">连接管理器将创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="b2454-117">The connection manager will create the folders.</span></span>|  
|<span data-ttu-id="b2454-118">**现有文件夹**</span><span class="sxs-lookup"><span data-stu-id="b2454-118">**Existing folders**</span></span>|<span data-ttu-id="b2454-119">连接管理器将使用现有文件夹。</span><span class="sxs-lookup"><span data-stu-id="b2454-119">The connection manager will use existing folders.</span></span>|  
  
 <span data-ttu-id="b2454-120">**文件/文件夹**</span><span class="sxs-lookup"><span data-stu-id="b2454-120">**Files / Folders**</span></span>  
 <span data-ttu-id="b2454-121">查看使用下面介绍的按钮所添加的文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="b2454-121">View the files or folders that you have added by using the buttons described as follows.</span></span>  
  
 <span data-ttu-id="b2454-122">**添加**</span><span class="sxs-lookup"><span data-stu-id="b2454-122">**Add**</span></span>  
 <span data-ttu-id="b2454-123">通过使用“选择文件”  对话框添加文件，或者通过使用“查找文件夹”  对话框添加文件夹。</span><span class="sxs-lookup"><span data-stu-id="b2454-123">Add a file by using the **Select Files** dialog box, or add a folder by using the **Browse for Folder** dialog box.</span></span>  
  
 <span data-ttu-id="b2454-124">**编辑**</span><span class="sxs-lookup"><span data-stu-id="b2454-124">**Edit**</span></span>  
 <span data-ttu-id="b2454-125">选择一个文件或文件夹，再通过使用“选择文件”  或“查找文件夹”  对话框，将其替换为另一个文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="b2454-125">Select a file or folder, and then replace it with a different file or folder by using the **Select Files** or **Browse for Folder** dialog box.</span></span>  
  
 <span data-ttu-id="b2454-126">**删除**</span><span class="sxs-lookup"><span data-stu-id="b2454-126">**Remove**</span></span>  
 <span data-ttu-id="b2454-127">选择一个文件或文件夹，再通过使用“删除”  按钮将其从列表中删除。</span><span class="sxs-lookup"><span data-stu-id="b2454-127">Select a file or folder, and then remove it from the list by using the **Remove** button.</span></span>  
  
 <span data-ttu-id="b2454-128">**箭头按钮**</span><span class="sxs-lookup"><span data-stu-id="b2454-128">**Arrow buttons**</span></span>  
 <span data-ttu-id="b2454-129">选择一个文件或文件夹，再使用箭头按钮将它上移或下移以指定访问顺序。</span><span class="sxs-lookup"><span data-stu-id="b2454-129">Select a file or folder, and then use the arrow buttons to move it up or down to specify the sequence of access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2454-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2454-130">See Also</span></span>  
 [<span data-ttu-id="b2454-131">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="b2454-131">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
  
  
