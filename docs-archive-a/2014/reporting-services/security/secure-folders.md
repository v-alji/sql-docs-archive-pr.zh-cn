---
title: 保护文件夹 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- high-security folders [Reporting Services]
- low-security folders
- folders [Reporting Services], security
- security [Reporting Services], folders
ms.assetid: 0fd91f77-0143-476b-9af0-87293be78e44
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483b3108713032b3aaf566208f39f6c2f705da1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579455"
---
# <a name="secure-folders"></a><span data-ttu-id="f499d-102">保护文件夹</span><span class="sxs-lookup"><span data-stu-id="f499d-102">Secure Folders</span></span>
  <span data-ttu-id="f499d-103">文件夹的安全性是保护报表服务器中所有内容的基础。</span><span class="sxs-lookup"><span data-stu-id="f499d-103">Folder security is the foundation for securing all content in a report server.</span></span> <span data-ttu-id="f499d-104">由于安全性在整个文件夹结构中是可继承的，因此您可以将文件夹层次结构中或大或小的不同部分指定为允许某些类型的访问。</span><span class="sxs-lookup"><span data-stu-id="f499d-104">Because security is inherited throughout the folder structure, you can designate large or small sections of the folder hierarchy to allow for certain kinds of access.</span></span>  
  
 <span data-ttu-id="f499d-105">安全性较高的文件夹可用来存储机密报表或用作临时区域；例如，在将报表移到最终位置之前，可以在某个文件夹中测试这些报表。</span><span class="sxs-lookup"><span data-stu-id="f499d-105">High-security folders can be used to store confidential reports or as staging areas; for example, you can have a folder that you use to test reports before moving them to a final location.</span></span> <span data-ttu-id="f499d-106">若要控制对此区域的访问，您可以定义一个只允许报表作者添加和删除项的角色分配，并定义一个允许测试人员运行报表但不能添加或删除项的角色分配。</span><span class="sxs-lookup"><span data-stu-id="f499d-106">To control access to this area, you can define one role assignment that allows only report authors to add and delete items, and a second role assignment that allows testers to run reports but not to add or remove items.</span></span> <span data-ttu-id="f499d-107">由于这些角色分配是明确地为测试人员和报表作者定义的，因此其他用户不能访问该文件夹（本地系统管理员除外）。</span><span class="sxs-lookup"><span data-stu-id="f499d-107">Because the role assignments are defined explicitly for testers and report authors, no other users (except for local system administrators) can access the folder.</span></span>  
  
 <span data-ttu-id="f499d-108">安全性较低的文件夹可用来存储希望易于访问的报表。</span><span class="sxs-lookup"><span data-stu-id="f499d-108">Low-security folders can be used to store reports that you want to be easily accessible.</span></span>  
  
 <span data-ttu-id="f499d-109">文件夹安全性构成了项级安全性的基础，其基点是报表服务器文件夹层次结构的根节点（即主文件夹）。</span><span class="sxs-lookup"><span data-stu-id="f499d-109">Folder security forms the basis of item-level security, starting with the root node of the report server folder hierarchy, the Home folder.</span></span> <span data-ttu-id="f499d-110">由于安全性是可继承的，因此，建议您对主文件夹设置限制相当严格的安全策略。</span><span class="sxs-lookup"><span data-stu-id="f499d-110">Because security is inherited, it is advisable to set a fairly restrictive security policy on the Home folder.</span></span> <span data-ttu-id="f499d-111">在主文件夹角色分配中使用“浏览者”角色，即可通过提供只读访问来做到这一点  。</span><span class="sxs-lookup"><span data-stu-id="f499d-111">Using the **Browser** role in Home folder role assignments does exactly that by providing view-only access.</span></span>  
  
## <a name="tasks-and-folder-access"></a><span data-ttu-id="f499d-112">任务和文件夹访问权限</span><span class="sxs-lookup"><span data-stu-id="f499d-112">Tasks and Folder Access</span></span>  
 <span data-ttu-id="f499d-113">在为文件夹创建角色分配时，请考虑下表中列出的任务：</span><span class="sxs-lookup"><span data-stu-id="f499d-113">When creating role assignments for folders, consider the tasks listed in the following table.</span></span>  
  
|<span data-ttu-id="f499d-114">选择此任务</span><span class="sxs-lookup"><span data-stu-id="f499d-114">Select this task</span></span>|<span data-ttu-id="f499d-115">授予以下操作权限</span><span class="sxs-lookup"><span data-stu-id="f499d-115">To give permission to</span></span>|  
|----------------------|---------------------------|  
|<span data-ttu-id="f499d-116">查看文件夹</span><span class="sxs-lookup"><span data-stu-id="f499d-116">View folders</span></span>|<span data-ttu-id="f499d-117">查看文件夹的层次结构和只读属性（指示文件夹的创建时间与修改时间）。</span><span class="sxs-lookup"><span data-stu-id="f499d-117">View the folder hierarchy and read-only properties that indicate when the folder was created and modified.</span></span><br /><br /> <span data-ttu-id="f499d-118">除非将用户分配到的角色中还包括“查看报表”、“查看模型”、“查看资源”和“查看数据源”任务，否则用户无法查看文件夹中的项。</span><span class="sxs-lookup"><span data-stu-id="f499d-118">Users cannot view items in the folder unless they are assigned to roles that also include the following tasks: "View reports," "View models", "View resources," and "View data sources."</span></span>|  
|<span data-ttu-id="f499d-119">管理文件夹</span><span class="sxs-lookup"><span data-stu-id="f499d-119">Manage folders</span></span>|<span data-ttu-id="f499d-120">查看文件夹属性、更改名称或说明，或将文件夹移到另一位置。</span><span class="sxs-lookup"><span data-stu-id="f499d-120">View folder properties, change the name or description, or move the folder to another location.</span></span> <span data-ttu-id="f499d-121">此任务允许用户创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="f499d-121">This task allows users to create folders.</span></span>|  
|<span data-ttu-id="f499d-122">管理报表</span><span class="sxs-lookup"><span data-stu-id="f499d-122">Manage reports</span></span>|<span data-ttu-id="f499d-123">将报表从文件系统添加到文件夹，以及将报表从报表设计器发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f499d-123">Add reports from the file system to a folder and publish reports from Report Designer to the report server.</span></span>|  
|<span data-ttu-id="f499d-124">管理数据源</span><span class="sxs-lookup"><span data-stu-id="f499d-124">Manage data sources</span></span>|<span data-ttu-id="f499d-125">向文件夹中添加新的共享数据源项，以及更改现有的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="f499d-125">Add new shared data source items to a folder and change existing shared data sources.</span></span>|  
|<span data-ttu-id="f499d-126">设置项的安全性</span><span class="sxs-lookup"><span data-stu-id="f499d-126">Set security on items</span></span>|<span data-ttu-id="f499d-127">创建和修改控制文件夹访问权限的角色分配。</span><span class="sxs-lookup"><span data-stu-id="f499d-127">Create and modify role assignments that control access to the folder.</span></span> <span data-ttu-id="f499d-128">此任务必须与“查看文件夹”或“管理文件夹”任务一起使用。</span><span class="sxs-lookup"><span data-stu-id="f499d-128">This task must be used with either "View folders" or "Manage folders."</span></span> <span data-ttu-id="f499d-129">否则，此任务不会有任何作用，因为用户无法选择项。</span><span class="sxs-lookup"><span data-stu-id="f499d-129">If it is not, it will have no effect because the user will not be able to select the item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f499d-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f499d-130">See Also</span></span>  
 <span data-ttu-id="f499d-131">[保护报表和资源](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="f499d-131">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="f499d-132">[保护共享数据源项](secure-shared-data-source-items.md) </span><span class="sxs-lookup"><span data-stu-id="f499d-132">[Secure Shared Data Source Items](secure-shared-data-source-items.md) </span></span>  
 [<span data-ttu-id="f499d-133">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="f499d-133">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
