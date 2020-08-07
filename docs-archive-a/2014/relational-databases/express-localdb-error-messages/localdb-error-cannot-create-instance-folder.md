---
title: LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 626b73d3-a257-4b45-82fb-c6299faa0001
author: stevestein
ms.author: sstein
ms.openlocfilehash: b127bedb0dc13c0b8b5a238a8ef104ca9a00bd85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589110"
---
# <a name="localdb_error_cannot_create_instance_folder"></a><span data-ttu-id="a7fd8-102">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="a7fd8-102">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span></span>
    
## <a name="details"></a><span data-ttu-id="a7fd8-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a7fd8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7fd8-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a7fd8-104">Product Name</span></span>|<span data-ttu-id="a7fd8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a7fd8-105">SQL Server</span></span>|  
|<span data-ttu-id="a7fd8-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a7fd8-106">Event ID</span></span>|<span data-ttu-id="a7fd8-107">256</span><span class="sxs-lookup"><span data-stu-id="a7fd8-107">256</span></span>|  
|<span data-ttu-id="a7fd8-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a7fd8-108">Event Source</span></span>|<span data-ttu-id="a7fd8-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="a7fd8-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="a7fd8-110">组件</span><span class="sxs-lookup"><span data-stu-id="a7fd8-110">Component</span></span>|<span data-ttu-id="a7fd8-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="a7fd8-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="a7fd8-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="a7fd8-112">Message Text</span></span>|<span data-ttu-id="a7fd8-113">无法在以下位置创建本地数据库实例的文件夹：%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server 本地 DB\Instances \\<实例名称 \> 。</span><span class="sxs-lookup"><span data-stu-id="a7fd8-113">Cannot create folder for the Local Database instance at: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server Local DB\Instances\\<instance name\>.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a7fd8-114">说明</span><span class="sxs-lookup"><span data-stu-id="a7fd8-114">Explanation</span></span>  
 <span data-ttu-id="a7fd8-115">不能在 %userprofile% 下创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="a7fd8-115">A folder cannot be created under %userprofile%.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a7fd8-116">用户操作</span><span class="sxs-lookup"><span data-stu-id="a7fd8-116">User Action</span></span>  
  
