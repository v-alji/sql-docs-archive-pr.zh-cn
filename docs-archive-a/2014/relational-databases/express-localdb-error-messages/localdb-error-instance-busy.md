---
title: LOCALDB_ERROR_INSTANCE_BUSY |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 0ed9d0f8-3297-4e31-a3e9-4a827f381789
author: stevestein
ms.author: sstein
ms.openlocfilehash: c587ada5f08d3743f4fe7eafccfc923c38a2b7b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581195"
---
# <a name="localdb_error_instance_busy"></a><span data-ttu-id="74f1b-102">LOCALDB_ERROR_INSTANCE_BUSY</span><span class="sxs-lookup"><span data-stu-id="74f1b-102">LOCALDB_ERROR_INSTANCE_BUSY</span></span>
    
## <a name="details"></a><span data-ttu-id="74f1b-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="74f1b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74f1b-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="74f1b-104">Product Name</span></span>|<span data-ttu-id="74f1b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="74f1b-105">SQL Server</span></span>|  
|<span data-ttu-id="74f1b-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="74f1b-106">Event ID</span></span>|<span data-ttu-id="74f1b-107">274</span><span class="sxs-lookup"><span data-stu-id="74f1b-107">274</span></span>|  
|<span data-ttu-id="74f1b-108">事件来源</span><span class="sxs-lookup"><span data-stu-id="74f1b-108">Event Source</span></span>|<span data-ttu-id="74f1b-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="74f1b-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="74f1b-110">组件</span><span class="sxs-lookup"><span data-stu-id="74f1b-110">Component</span></span>|<span data-ttu-id="74f1b-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="74f1b-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="74f1b-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="74f1b-112">Message Text</span></span>|<span data-ttu-id="74f1b-113">无法执行本地数据库实例上请求的操作，因为指定的实例已被使用。</span><span class="sxs-lookup"><span data-stu-id="74f1b-113">Requested operation on Local Database instance cannot be performed because specified instance is currently in use.</span></span> <span data-ttu-id="74f1b-114">请停止该实例后重试。</span><span class="sxs-lookup"><span data-stu-id="74f1b-114">Stop the instance and try again.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="74f1b-115">说明</span><span class="sxs-lookup"><span data-stu-id="74f1b-115">Explanation</span></span>  
 <span data-ttu-id="74f1b-116">指定的实例正在运行。</span><span class="sxs-lookup"><span data-stu-id="74f1b-116">The specified instance is running.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="74f1b-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="74f1b-117">User Action</span></span>  
 <span data-ttu-id="74f1b-118">停止指定的本地数据库运行时实例并重试。</span><span class="sxs-lookup"><span data-stu-id="74f1b-118">Stop the specified Local Database Runtime instance and try again.</span></span>  
  
  
