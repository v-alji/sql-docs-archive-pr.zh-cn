---
title: LOCALDB_ERROR_WAIT_TIMEOUT |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: e5b55efa-daa1-4c39-aa71-eeb7707ed601
author: stevestein
ms.author: sstein
ms.openlocfilehash: e3668b32fb48a3e12c33dc15224467307c696af4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682844"
---
# <a name="localdb_error_wait_timeout"></a><span data-ttu-id="22ed0-102">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22ed0-102">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>
    
## <a name="details"></a><span data-ttu-id="22ed0-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="22ed0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22ed0-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="22ed0-104">Product Name</span></span>|<span data-ttu-id="22ed0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="22ed0-105">SQL Server</span></span>|  
|<span data-ttu-id="22ed0-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22ed0-106">Event ID</span></span>|<span data-ttu-id="22ed0-107">277</span><span class="sxs-lookup"><span data-stu-id="22ed0-107">277</span></span>|  
|<span data-ttu-id="22ed0-108">事件来源</span><span class="sxs-lookup"><span data-stu-id="22ed0-108">Event Source</span></span>|<span data-ttu-id="22ed0-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="22ed0-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="22ed0-110">组件</span><span class="sxs-lookup"><span data-stu-id="22ed0-110">Component</span></span>|<span data-ttu-id="22ed0-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="22ed0-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="22ed0-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="22ed0-112">Message Text</span></span>|<span data-ttu-id="22ed0-113">本地数据库实例 API 方法内发生超时。</span><span class="sxs-lookup"><span data-stu-id="22ed0-113">Timeout occurred inside the Local Database instance API method.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="22ed0-114">说明</span><span class="sxs-lookup"><span data-stu-id="22ed0-114">Explanation</span></span>  
 <span data-ttu-id="22ed0-115">试图获取同步锁定时发生超时。</span><span class="sxs-lookup"><span data-stu-id="22ed0-115">A time-out occurred while trying to acquire synchronization locks.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="22ed0-116">用户操作</span><span class="sxs-lookup"><span data-stu-id="22ed0-116">User Action</span></span>  
 <span data-ttu-id="22ed0-117">再次重试请求的操作。</span><span class="sxs-lookup"><span data-stu-id="22ed0-117">Retry the requested operation again.</span></span>  
  
  
