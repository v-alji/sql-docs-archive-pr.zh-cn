---
title: MSSQLSERVER_1101 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 631b0ab1466815cbacfd71b4f9fd714fabd0f7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589666"
---
# <a name="mssqlserver_1101"></a><span data-ttu-id="2e9bb-102">MSSQLSERVER_1101</span><span class="sxs-lookup"><span data-stu-id="2e9bb-102">MSSQLSERVER_1101</span></span>
    
## <a name="details"></a><span data-ttu-id="2e9bb-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="2e9bb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e9bb-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="2e9bb-104">Product Name</span></span>|<span data-ttu-id="2e9bb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2e9bb-105">SQL Server</span></span>|  
|<span data-ttu-id="2e9bb-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2e9bb-106">Event ID</span></span>|<span data-ttu-id="2e9bb-107">1101</span><span class="sxs-lookup"><span data-stu-id="2e9bb-107">1101</span></span>|  
|<span data-ttu-id="2e9bb-108">事件源</span><span class="sxs-lookup"><span data-stu-id="2e9bb-108">Event Source</span></span>|<span data-ttu-id="2e9bb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2e9bb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2e9bb-110">组件</span><span class="sxs-lookup"><span data-stu-id="2e9bb-110">Component</span></span>|<span data-ttu-id="2e9bb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2e9bb-111">SQLEngine</span></span>|  
|<span data-ttu-id="2e9bb-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="2e9bb-112">Symbolic Name</span></span>|<span data-ttu-id="2e9bb-113">NOALLOCPG</span><span class="sxs-lookup"><span data-stu-id="2e9bb-113">NOALLOCPG</span></span>|  
|<span data-ttu-id="2e9bb-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="2e9bb-114">Message Text</span></span>|<span data-ttu-id="2e9bb-115">由于文件组“%.\*ls”中的磁盘空间不足，无法为数据库“%.\*ls”分配新页。</span><span class="sxs-lookup"><span data-stu-id="2e9bb-115">Could not allocate a new page for database '%.\*ls' because of insufficient disk space in filegroup '%.\*ls'.</span></span> <span data-ttu-id="2e9bb-116">请删除文件组中的对象、将其他文件添加到文件组或者为文件组中的现有文件启用自动增长，以便增加必要的空间。</span><span class="sxs-lookup"><span data-stu-id="2e9bb-116">Create the necessary space by dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2e9bb-117">说明</span><span class="sxs-lookup"><span data-stu-id="2e9bb-117">Explanation</span></span>  
 <span data-ttu-id="2e9bb-118">文件组中没有可用的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="2e9bb-118">No disk space available in a filegroup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2e9bb-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="2e9bb-119">User Action</span></span>  
 <span data-ttu-id="2e9bb-120">以下操作可能会使空间在文件组中可用。</span><span class="sxs-lookup"><span data-stu-id="2e9bb-120">The following actions may make space available in the filegroup.</span></span>  
  
-   <span data-ttu-id="2e9bb-121">打开 AUTOGROW。</span><span class="sxs-lookup"><span data-stu-id="2e9bb-121">Turn on AUTOGROW.</span></span>  
  
-   <span data-ttu-id="2e9bb-122">向文件组添加更多文件。</span><span class="sxs-lookup"><span data-stu-id="2e9bb-122">Add more files to the file group.</span></span>  
  
-   <span data-ttu-id="2e9bb-123">通过删除文件组中不必要的索引或表来释放磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="2e9bb-123">Free up disk space by dropping unnecessary indexes or tables in the filegroup.</span></span>  
  
  
