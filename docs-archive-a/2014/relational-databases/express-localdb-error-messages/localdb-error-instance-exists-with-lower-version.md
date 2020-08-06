---
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa6db2af138bb2aeefb1a922e55db56c4ea821f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694482"
---
# <a name="localdb_error_instance_exists_with_lower_version"></a><span data-ttu-id="15a6c-102">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="15a6c-102">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span></span>
    
## <a name="details"></a><span data-ttu-id="15a6c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="15a6c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15a6c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="15a6c-104">Product Name</span></span>|<span data-ttu-id="15a6c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="15a6c-105">SQL Server</span></span>|  
|<span data-ttu-id="15a6c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="15a6c-106">Event ID</span></span>|<span data-ttu-id="15a6c-107">258</span><span class="sxs-lookup"><span data-stu-id="15a6c-107">258</span></span>|  
|<span data-ttu-id="15a6c-108">事件来源</span><span class="sxs-lookup"><span data-stu-id="15a6c-108">Event Source</span></span>|<span data-ttu-id="15a6c-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="15a6c-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="15a6c-110">组件</span><span class="sxs-lookup"><span data-stu-id="15a6c-110">Component</span></span>|<span data-ttu-id="15a6c-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="15a6c-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="15a6c-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="15a6c-112">Message Text</span></span>|<span data-ttu-id="15a6c-113">无法使用指定的版本创建本地数据库实例。</span><span class="sxs-lookup"><span data-stu-id="15a6c-113">Unable to create the Local Database instance with specified version.</span></span> <span data-ttu-id="15a6c-114">已存在同名的实例，但是它的版本低于指定的版本。</span><span class="sxs-lookup"><span data-stu-id="15a6c-114">An instance with the same name already exists, but it has lower version than the specified version.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="15a6c-115">说明</span><span class="sxs-lookup"><span data-stu-id="15a6c-115">Explanation</span></span>  
 <span data-ttu-id="15a6c-116">指定的实例已存在，但其版本低于请求的版本。</span><span class="sxs-lookup"><span data-stu-id="15a6c-116">The specified instance already exists but its version is lower than requested.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="15a6c-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="15a6c-117">User Action</span></span>  
 <span data-ttu-id="15a6c-118">删除现有实例，然后重试操作。</span><span class="sxs-lookup"><span data-stu-id="15a6c-118">Delete the existing instance and retry the operation.</span></span>  
  
  
