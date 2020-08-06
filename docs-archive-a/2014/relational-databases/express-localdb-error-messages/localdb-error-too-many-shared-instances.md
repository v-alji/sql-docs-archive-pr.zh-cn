---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0896f3e70e6c65a1fcd0de4169249fb622e6b5f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577668"
---
# <a name="localdb_error_too_many_shared_instances"></a><span data-ttu-id="d7d0d-102">LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="d7d0d-102">LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES</span></span>
    
## <a name="details"></a><span data-ttu-id="d7d0d-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d7d0d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7d0d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d7d0d-104">Product Name</span></span>|<span data-ttu-id="d7d0d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d7d0d-105">SQL Server</span></span>|  
|<span data-ttu-id="d7d0d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d7d0d-106">Event ID</span></span>|<span data-ttu-id="d7d0d-107">287</span><span class="sxs-lookup"><span data-stu-id="d7d0d-107">287</span></span>|  
|<span data-ttu-id="d7d0d-108">事件来源</span><span class="sxs-lookup"><span data-stu-id="d7d0d-108">Event Source</span></span>|<span data-ttu-id="d7d0d-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="d7d0d-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="d7d0d-110">组件</span><span class="sxs-lookup"><span data-stu-id="d7d0d-110">Component</span></span>|<span data-ttu-id="d7d0d-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="d7d0d-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="d7d0d-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="d7d0d-112">Message Text</span></span>|<span data-ttu-id="d7d0d-113">共享的实例太多，无法生成唯一的用户实例名。</span><span class="sxs-lookup"><span data-stu-id="d7d0d-113">There are too many shared instance and we cannot generate unique User Instance Name.</span></span> <span data-ttu-id="d7d0d-114">请取消共享某些现有共享实例。</span><span class="sxs-lookup"><span data-stu-id="d7d0d-114">Unshare some of the existing shared instances.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7d0d-115">说明</span><span class="sxs-lookup"><span data-stu-id="d7d0d-115">Explanation</span></span>  
 <span data-ttu-id="d7d0d-116">共享的实例太多，无法生成唯一的用户实例名。</span><span class="sxs-lookup"><span data-stu-id="d7d0d-116">There are too many shared instance and we cannot generate unique User Instance Name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7d0d-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="d7d0d-117">User Action</span></span>  
 <span data-ttu-id="d7d0d-118">取消共享一个或多个共享的本地数据库运行时实例，然后重试。</span><span class="sxs-lookup"><span data-stu-id="d7d0d-118">Unshare one or more of the shared Local Database Runtime instances and try again.</span></span>  
  
  
