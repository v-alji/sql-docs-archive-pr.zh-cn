---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 300f9753b721bc3e0a821a6b77929a9bec09312b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577674"
---
# <a name="localdb_error_instance_already_shared"></a><span data-ttu-id="24bba-102">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span><span class="sxs-lookup"><span data-stu-id="24bba-102">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span></span>
    
## <a name="details"></a><span data-ttu-id="24bba-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="24bba-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24bba-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="24bba-104">Product Name</span></span>|<span data-ttu-id="24bba-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="24bba-105">SQL Server</span></span>|  
|<span data-ttu-id="24bba-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="24bba-106">Event ID</span></span>|<span data-ttu-id="24bba-107">284</span><span class="sxs-lookup"><span data-stu-id="24bba-107">284</span></span>|  
|<span data-ttu-id="24bba-108">事件来源</span><span class="sxs-lookup"><span data-stu-id="24bba-108">Event Source</span></span>|<span data-ttu-id="24bba-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="24bba-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="24bba-110">组件</span><span class="sxs-lookup"><span data-stu-id="24bba-110">Component</span></span>|<span data-ttu-id="24bba-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="24bba-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="24bba-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="24bba-112">Message Text</span></span>|<span data-ttu-id="24bba-113">指定的本地数据库实例已经共享。</span><span class="sxs-lookup"><span data-stu-id="24bba-113">The specified Local Database Instance is already shared.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="24bba-114">说明</span><span class="sxs-lookup"><span data-stu-id="24bba-114">Explanation</span></span>  
 <span data-ttu-id="24bba-115">已使用不同的共享名称共享指定的本地数据库实例。</span><span class="sxs-lookup"><span data-stu-id="24bba-115">The specified Local Database Instance is already shared with a different shared name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="24bba-116">用户操作</span><span class="sxs-lookup"><span data-stu-id="24bba-116">User Action</span></span>  
 <span data-ttu-id="24bba-117">在使用不同的共享名称再次共享此共享实例之前，先取消共享此实例。</span><span class="sxs-lookup"><span data-stu-id="24bba-117">Unshare the shared instance before sharing it again with a different shared name.</span></span>  
  
  
