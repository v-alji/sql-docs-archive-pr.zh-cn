---
title: 查看 Integration Services 服务器上的包列表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 47b30f9ea0b2abae73f9260b873b7c8436c423eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682367"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a><span data-ttu-id="b9fa0-102">查看 Integration Services 服务器上的包列表</span><span class="sxs-lookup"><span data-stu-id="b9fa0-102">View the List of Packages on the Integration Services Server</span></span>
  <span data-ttu-id="b9fa0-103">可以使用以下两种方式之一来查看存储在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器上的包列表。</span><span class="sxs-lookup"><span data-stu-id="b9fa0-103">You can view the list of packages that are stored on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server in one of two ways.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="b9fa0-104">access</span><span class="sxs-lookup"><span data-stu-id="b9fa0-104">access</span></span>  
 <span data-ttu-id="b9fa0-105">若要查看在服务器上存储的包的列表，请查询视图 [catalog.packages（SSISDB 数据库）](/sql/integration-services/system-views/catalog-packages-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="b9fa0-105">To view the list of packages that are stored on the server, query the view, [catalog.packages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-packages-ssisdb-database).</span></span>  
  
 <span data-ttu-id="b9fa0-106">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中</span><span class="sxs-lookup"><span data-stu-id="b9fa0-106">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span></span>  
 <span data-ttu-id="b9fa0-107">若要使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中的对象资源管理器查看服务器上存储的包，请遵循以下过程。</span><span class="sxs-lookup"><span data-stu-id="b9fa0-107">To view packages stored on the server by using Object Explorer in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], follow the procedure below.</span></span>  
  
### <a name="to-view-packages-using-ssmanstudiofull"></a><span data-ttu-id="b9fa0-108">使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9fa0-108">To view packages using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span></span>  
  
1.  <span data-ttu-id="b9fa0-109">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="b9fa0-109">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="b9fa0-110">也就是说，连接到承载 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 数据库的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="b9fa0-110">That is, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="b9fa0-111">在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。</span><span class="sxs-lookup"><span data-stu-id="b9fa0-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="b9fa0-112">展开 **“Integration Services 目录”** 节点以显示 **SSISDB** 节点。</span><span class="sxs-lookup"><span data-stu-id="b9fa0-112">Expand the **Integration Services Catalogs** node to display the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="b9fa0-113">展开 **SSISDB** 节点以显示一个或多个文件夹的列表。</span><span class="sxs-lookup"><span data-stu-id="b9fa0-113">Expand the **SSISDB** node to display a list of one or more folders.</span></span> <span data-ttu-id="b9fa0-114">每个文件夹包含 **“项目”** 文件夹中的一个或多个项目，而每个项目包含 **“包”** 文件夹中的一个或多个包。</span><span class="sxs-lookup"><span data-stu-id="b9fa0-114">Each folder contains one or more projects in the **Projects** folder, and each project contains one more packages in the **Packages** folder.</span></span>  
  
  
