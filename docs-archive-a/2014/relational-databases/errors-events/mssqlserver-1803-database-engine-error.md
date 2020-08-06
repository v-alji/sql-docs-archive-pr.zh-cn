---
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11302f882846c49c6e9998608967e7042ac9860c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587852"
---
# <a name="mssqlserver_1803"></a><span data-ttu-id="23a28-102">MSSQLSERVER_1803</span><span class="sxs-lookup"><span data-stu-id="23a28-102">MSSQLSERVER_1803</span></span>
    
## <a name="details"></a><span data-ttu-id="23a28-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="23a28-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23a28-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="23a28-104">Product Name</span></span>|<span data-ttu-id="23a28-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="23a28-105">SQL Server</span></span>|  
|<span data-ttu-id="23a28-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="23a28-106">Event ID</span></span>|<span data-ttu-id="23a28-107">1803</span><span class="sxs-lookup"><span data-stu-id="23a28-107">1803</span></span>|  
|<span data-ttu-id="23a28-108">事件源</span><span class="sxs-lookup"><span data-stu-id="23a28-108">Event Source</span></span>|<span data-ttu-id="23a28-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="23a28-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="23a28-110">组件</span><span class="sxs-lookup"><span data-stu-id="23a28-110">Component</span></span>|<span data-ttu-id="23a28-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="23a28-111">SQLEngine</span></span>|  
|<span data-ttu-id="23a28-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="23a28-112">Symbolic Name</span></span>|<span data-ttu-id="23a28-113">NO_SPACE</span><span class="sxs-lookup"><span data-stu-id="23a28-113">NO_SPACE</span></span>|  
|<span data-ttu-id="23a28-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="23a28-114">Message Text</span></span>|<span data-ttu-id="23a28-115">CREATE DATABASE 失败。</span><span class="sxs-lookup"><span data-stu-id="23a28-115">CREATE DATABASE failed.</span></span> <span data-ttu-id="23a28-116">主文件必须至少是 %d MB 才能容纳模型数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="23a28-116">Primary file must be at least %d MB to accommodate a copy of the model database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23a28-117">说明</span><span class="sxs-lookup"><span data-stu-id="23a28-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="23a28-118">通过制作 model 数据库的副本来创建数据库。</span><span class="sxs-lookup"><span data-stu-id="23a28-118">creates a database by making a copy of the model database.</span></span> <span data-ttu-id="23a28-119">然后 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重命名该副本，并将新数据库放大到请求的大小。</span><span class="sxs-lookup"><span data-stu-id="23a28-119">Then [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renames the copy, and enlarges the new database to the requested size.</span></span> <span data-ttu-id="23a28-120">此种情况下，用户尝试创建小于 model 数据库的数据库。</span><span class="sxs-lookup"><span data-stu-id="23a28-120">In this case, the user tried to create a database smaller than the model database.</span></span> <span data-ttu-id="23a28-121">此操作失败了，其原因是主数据文件小于 model 数据库，无法容纳 model 数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="23a28-121">The operation failed because the copy of the model database could not fit on the primary data file, because the file was smaller than the model database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23a28-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="23a28-122">User Action</span></span>  
 <span data-ttu-id="23a28-123">创建具有更大数据库文件大小的数据库。</span><span class="sxs-lookup"><span data-stu-id="23a28-123">Create the database by using a larger database file size.</span></span> <span data-ttu-id="23a28-124">如果希望收缩该数据库，请使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 DBCC SHRINKDATABASE 语句来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="23a28-124">Then shrink the database if you want by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or the DBCC SHRINKDATABASE statement.</span></span>  
  
  