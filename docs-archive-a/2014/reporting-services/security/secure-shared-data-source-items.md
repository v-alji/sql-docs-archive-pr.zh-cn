---
title: 保护共享数据源项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
- security [Reporting Services], data sources
ms.assetid: 7299e498-0a1a-4821-a22a-5199bb773ce0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4177834a90e2852f4079e3b2bf5a1dd85b9cd51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587171"
---
# <a name="secure-shared-data-source-items"></a><span data-ttu-id="729e9-102">保护共享数据源项</span><span class="sxs-lookup"><span data-stu-id="729e9-102">Secure Shared Data Source Items</span></span>
  <span data-ttu-id="729e9-103">您可以设置共享数据源项的安全性，以允许或禁止对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="729e9-103">You can set security on a shared data source item to enable or disable access to it.</span></span>  
  
 <span data-ttu-id="729e9-104">如果用户对共享数据源拥有最基本的访问权限（例如，通过“浏览者”角色授予的访问权限）并且还为该用户授予了查看报表本身的权限，则该用户可以查看使用该项的报表的列表  。</span><span class="sxs-lookup"><span data-stu-id="729e9-104">A user who has minimal access to a shared data source (for example, the access granted through the **Browser** role) can view the list of reports that use the item, provided the user is also authorized to view the reports themselves.</span></span>  
  
 <span data-ttu-id="729e9-105">拥有其他访问权限的用户（例如，通过“内容管理员”角色授予的访问权限）可以查看和设置共享数据源的属性  。</span><span class="sxs-lookup"><span data-stu-id="729e9-105">A user who has additional access (such as that granted through the **Content Manager** role) can view and set properties for the shared data source.</span></span>  
  
 <span data-ttu-id="729e9-106">若要设置安全性，应创建相应的角色分配，以指定对共享数据源拥有访问权限的用户帐户或组帐户。</span><span class="sxs-lookup"><span data-stu-id="729e9-106">To set security, you create a role assignment that specifies which user or group account has access to the shared data source.</span></span> <span data-ttu-id="729e9-107">对共享数据源项具有访问权限的用户可以更改该项的名称、说明、连接字符串或凭据信息。</span><span class="sxs-lookup"><span data-stu-id="729e9-107">Users who have access to a shared data source item can change its name, description, connection string, or credential information.</span></span>  
  
## <a name="tasks-and-access-to-items"></a><span data-ttu-id="729e9-108">任务以及对项的访问权限</span><span class="sxs-lookup"><span data-stu-id="729e9-108">Tasks and Access to Items</span></span>  
 <span data-ttu-id="729e9-109">在创建角色分配时，请使用包含以下任务的角色来为用户和组分配适当的权限：</span><span class="sxs-lookup"><span data-stu-id="729e9-109">When creating role assignments, use a role that has these tasks to assign appropriate permissions to users and groups.</span></span>  
  
|<span data-ttu-id="729e9-110">选择此任务</span><span class="sxs-lookup"><span data-stu-id="729e9-110">Select this task</span></span>|<span data-ttu-id="729e9-111">授权用户以下权限</span><span class="sxs-lookup"><span data-stu-id="729e9-111">To give users permission to</span></span>|  
|----------------------|---------------------------------|  
|<span data-ttu-id="729e9-112">查看数据源</span><span class="sxs-lookup"><span data-stu-id="729e9-112">View data sources</span></span>|<span data-ttu-id="729e9-113">在文件夹层次结构中查看共享数据源项。</span><span class="sxs-lookup"><span data-stu-id="729e9-113">View the shared data source item in the folder hierarchy.</span></span> <span data-ttu-id="729e9-114">如果不包含此任务，则用户将无法查看项，用户可能无法了解数据源是否可用。</span><span class="sxs-lookup"><span data-stu-id="729e9-114">Without this task, the item is not visible to users and they may not be aware that the data source is available.</span></span>|  
|<span data-ttu-id="729e9-115">管理数据源</span><span class="sxs-lookup"><span data-stu-id="729e9-115">Manage data sources</span></span>|<span data-ttu-id="729e9-116">查看用于指定名称、说明和连接信息的属性。</span><span class="sxs-lookup"><span data-stu-id="729e9-116">View properties that specify the name, description, and connection information.</span></span> <span data-ttu-id="729e9-117">此任务还用于在文件夹层次结构中显示共享数据源项。</span><span class="sxs-lookup"><span data-stu-id="729e9-117">This task is also used to display a shared data source item in the folder hierarchy.</span></span> <span data-ttu-id="729e9-118">如果选择此任务，则可以省略“查看数据源”任务。</span><span class="sxs-lookup"><span data-stu-id="729e9-118">If you choose this task, you can omit the "View data sources" task.</span></span>|  
|<span data-ttu-id="729e9-119">设置项的安全性</span><span class="sxs-lookup"><span data-stu-id="729e9-119">Set security on items</span></span>|<span data-ttu-id="729e9-120">创建和修改控制共享数据源访问权限的角色分配。</span><span class="sxs-lookup"><span data-stu-id="729e9-120">Create and modify role assignments that control access to the shared data source.</span></span> <span data-ttu-id="729e9-121">此任务必须与“查看数据源”或“管理数据源”任务一起使用。</span><span class="sxs-lookup"><span data-stu-id="729e9-121">This task must be used with either "View data source" or "Manage data sources" tasks.</span></span> <span data-ttu-id="729e9-122">否则，由于用户无法选择项，此任务将不会发挥任何作用。</span><span class="sxs-lookup"><span data-stu-id="729e9-122">If it is not, it has no effect because the user cannot select the item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="729e9-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="729e9-123">See Also</span></span>  
 <span data-ttu-id="729e9-124">[管理报表数据源](../report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="729e9-124">[Manage Report Data Sources](../report-data/manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="729e9-125">[保护文件夹](secure-folders.md) </span><span class="sxs-lookup"><span data-stu-id="729e9-125">[Secure Folders](secure-folders.md) </span></span>  
 <span data-ttu-id="729e9-126">[保护报表和资源](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="729e9-126">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="729e9-127">[授予对本机模式报表服务器的权限](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="729e9-127">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="729e9-128">在 Reporting Services 数据源中存储凭据</span><span class="sxs-lookup"><span data-stu-id="729e9-128">Store Credentials in a Reporting Services Data Source</span></span>](../report-data/store-credentials-in-a-reporting-services-data-source.md)  
  
  
