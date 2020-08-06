---
title: 文件连接管理器编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnectionmanager.f1
helpviewer_keywords:
- File Connection Manager Editor
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2f3261b836d4800787fc078b05b15e469d3c200d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589757"
---
# <a name="file-connection-manager-editor"></a><span data-ttu-id="03f4b-102">文件连接管理器编辑器</span><span class="sxs-lookup"><span data-stu-id="03f4b-102">File Connection Manager Editor</span></span>
  <span data-ttu-id="03f4b-103">可以使用 **“文件连接管理器编辑器”** 对话框指定用于连接文件或文件夹的属性。</span><span class="sxs-lookup"><span data-stu-id="03f4b-103">Use the **File Connection Manager Editor** dialog box to specify the properties used to connect to a file or a folder.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03f4b-104">通过在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的“属性”窗口中指定表达式，可以设置文件连接管理器的 ConnectionString 属性。</span><span class="sxs-lookup"><span data-stu-id="03f4b-104">You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="03f4b-105">但是，为了避免在使用表达式指定文件或文件夹时出现验证错误，请在 "**文件连接管理器编辑器**" 中，为 "**文件/文件夹**" 添加文件或文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="03f4b-105">However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File/Folder**, add a file or folder path.</span></span>  
  
 <span data-ttu-id="03f4b-106">若要了解有关文件连接管理器的详细信息，请参阅 [File Connection Manager](connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="03f4b-106">To learn more about the File connection manager, see [File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="03f4b-107">选项</span><span class="sxs-lookup"><span data-stu-id="03f4b-107">Options</span></span>  
 <span data-ttu-id="03f4b-108">**使用类型**</span><span class="sxs-lookup"><span data-stu-id="03f4b-108">**Usage Type**</span></span>  
 <span data-ttu-id="03f4b-109">指定“文件连接管理器”是连接到现有文件或文件夹，还是创建新的文件或文件夹。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="03f4b-109">Specify whether the **File Connection Manager** connects to an existing file or folder or creates a new file or folder.</span></span>  
  
|<span data-ttu-id="03f4b-110">值</span><span class="sxs-lookup"><span data-stu-id="03f4b-110">Value</span></span>|<span data-ttu-id="03f4b-111">说明</span><span class="sxs-lookup"><span data-stu-id="03f4b-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="03f4b-112">创建文件</span><span class="sxs-lookup"><span data-stu-id="03f4b-112">Create file</span></span>|<span data-ttu-id="03f4b-113">在运行时创建新文件。</span><span class="sxs-lookup"><span data-stu-id="03f4b-113">Create a new file at run time.</span></span>|  
|<span data-ttu-id="03f4b-114">现有文件</span><span class="sxs-lookup"><span data-stu-id="03f4b-114">Existing file</span></span>|<span data-ttu-id="03f4b-115">使用现有文件。</span><span class="sxs-lookup"><span data-stu-id="03f4b-115">Use an existing file.</span></span>|  
|<span data-ttu-id="03f4b-116">创建文件夹</span><span class="sxs-lookup"><span data-stu-id="03f4b-116">Create folder</span></span>|<span data-ttu-id="03f4b-117">在运行时创建新文件夹。</span><span class="sxs-lookup"><span data-stu-id="03f4b-117">Create a new folder at run time.</span></span>|  
|<span data-ttu-id="03f4b-118">现有文件夹</span><span class="sxs-lookup"><span data-stu-id="03f4b-118">Existing folder</span></span>|<span data-ttu-id="03f4b-119">使用现有文件夹。</span><span class="sxs-lookup"><span data-stu-id="03f4b-119">Use an existing folder.</span></span>|  
  
 <span data-ttu-id="03f4b-120">**文件/文件夹**</span><span class="sxs-lookup"><span data-stu-id="03f4b-120">**File / Folder**</span></span>  
 <span data-ttu-id="03f4b-121">对于“文件”\*\*\*\*，请指定要使用的文件。</span><span class="sxs-lookup"><span data-stu-id="03f4b-121">If **File**, specify the file to use.</span></span>  
  
 <span data-ttu-id="03f4b-122">对于 **“文件夹”**，请指定要使用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="03f4b-122">If **Folder**, specify the folder to use.</span></span>  
  
 <span data-ttu-id="03f4b-123">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="03f4b-123">**Browse**</span></span>  
 <span data-ttu-id="03f4b-124">通过使用“选择文件”\*\*\*\* 或“查找文件夹”\*\*\*\* 对话框选择文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="03f4b-124">Select the file or folder by using the **Select File** or **Browse for Folder** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f4b-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03f4b-125">See Also</span></span>  
 [<span data-ttu-id="03f4b-126">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="03f4b-126">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
