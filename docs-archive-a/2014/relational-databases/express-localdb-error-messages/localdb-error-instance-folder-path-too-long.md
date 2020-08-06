---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 32ae8ebe102008d08a6059328ed57cd118ece019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590829"
---
# <a name="localdb_error_instance_folder_path_too_long"></a><span data-ttu-id="86da8-102">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="86da8-102">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>
    
## <a name="details"></a><span data-ttu-id="86da8-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="86da8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86da8-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="86da8-104">Product Name</span></span>|<span data-ttu-id="86da8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="86da8-105">SQL Server</span></span>|  
|<span data-ttu-id="86da8-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="86da8-106">Event ID</span></span>|<span data-ttu-id="86da8-107">260</span><span class="sxs-lookup"><span data-stu-id="86da8-107">260</span></span>|  
|<span data-ttu-id="86da8-108">事件来源</span><span class="sxs-lookup"><span data-stu-id="86da8-108">Event Source</span></span>|<span data-ttu-id="86da8-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="86da8-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="86da8-110">组件</span><span class="sxs-lookup"><span data-stu-id="86da8-110">Component</span></span>|<span data-ttu-id="86da8-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="86da8-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="86da8-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="86da8-112">Message Text</span></span>|<span data-ttu-id="86da8-113">本地数据库实例文件夹的完整路径长度大于 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="86da8-113">The full path length of the Local Database instance folder is longer than MAX_PATH.</span></span> <span data-ttu-id="86da8-114">此实例必须存储在以下文件夹中：%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server 本地 DB\Instances \\<实例名称 \> 。</span><span class="sxs-lookup"><span data-stu-id="86da8-114">The instance must be stored in folder: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server Local DB\Instances\\<instance name\>.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="86da8-115">说明</span><span class="sxs-lookup"><span data-stu-id="86da8-115">Explanation</span></span>  
 <span data-ttu-id="86da8-116">应在其中存储该实例的路径的长度超过 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="86da8-116">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="86da8-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="86da8-117">User Action</span></span>  
 <span data-ttu-id="86da8-118">创建长度小于 MAX_PATH 的新路径。</span><span class="sxs-lookup"><span data-stu-id="86da8-118">Create a new path that is shorter than MAX_PATH.</span></span>  
  
  
