---
title: MSSQLSERVER_945 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51284cdcf48f1bf713a853f9c87457cb5291cc4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581232"
---
# <a name="mssqlserver_945"></a><span data-ttu-id="a25f6-102">MSSQLSERVER_945</span><span class="sxs-lookup"><span data-stu-id="a25f6-102">MSSQLSERVER_945</span></span>
    
## <a name="details"></a><span data-ttu-id="a25f6-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a25f6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a25f6-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a25f6-104">Product Name</span></span>|<span data-ttu-id="a25f6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a25f6-105">SQL Server</span></span>|  
|<span data-ttu-id="a25f6-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a25f6-106">Event ID</span></span>|<span data-ttu-id="a25f6-107">945</span><span class="sxs-lookup"><span data-stu-id="a25f6-107">945</span></span>|  
|<span data-ttu-id="a25f6-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a25f6-108">Event Source</span></span>|<span data-ttu-id="a25f6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a25f6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a25f6-110">组件</span><span class="sxs-lookup"><span data-stu-id="a25f6-110">Component</span></span>|<span data-ttu-id="a25f6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a25f6-111">SQLEngine</span></span>|  
|<span data-ttu-id="a25f6-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="a25f6-112">Symbolic Name</span></span>|<span data-ttu-id="a25f6-113">DB_IS_SHUTDOWN</span><span class="sxs-lookup"><span data-stu-id="a25f6-113">DB_IS_SHUTDOWN</span></span>|  
|<span data-ttu-id="a25f6-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="a25f6-114">Message Text</span></span>|<span data-ttu-id="a25f6-115">由于文件不可访问，或者内存或磁盘空间不足，所以无法打开数据库“%.\*ls”。</span><span class="sxs-lookup"><span data-stu-id="a25f6-115">Database '%.\*ls' cannot be opened due to inaccessible files or insufficient memory or disk space.</span></span>  <span data-ttu-id="a25f6-116">有关详细信息，请参阅 SQL Server 错误日志。</span><span class="sxs-lookup"><span data-stu-id="a25f6-116">See the SQL Server error log for details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a25f6-117">说明</span><span class="sxs-lookup"><span data-stu-id="a25f6-117">Explanation</span></span>  
 <span data-ttu-id="a25f6-118">由于缺少文件或其他资源，因此无法访问数据库。</span><span class="sxs-lookup"><span data-stu-id="a25f6-118">The database could not be accessed because files or other resources are missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a25f6-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="a25f6-119">User Action</span></span>  
 <span data-ttu-id="a25f6-120">检查有关内存、磁盘空间或权限失败的其他信息的错误日志。</span><span class="sxs-lookup"><span data-stu-id="a25f6-120">Check the error log for additional information about memory, disk space, or permission failure.</span></span> <span data-ttu-id="a25f6-121">确认受影响数据库的 .mdf 和 .ndf 文件的位置，并确认由[!INCLUDE[ssDE](../../includes/ssde-md.md)]使用的帐户拥有访问这些文件的权限。</span><span class="sxs-lookup"><span data-stu-id="a25f6-121">Confirm the location of the .mdf and .ndf files for the affected database and confirm that the account used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] has permission to access those files.</span></span> <span data-ttu-id="a25f6-122">更正问题后，使用 ALTER DATABASE 将数据库设置为 ONLINE，从而重新启动数据库。</span><span class="sxs-lookup"><span data-stu-id="a25f6-122">After correcting the problem, restart the database by using ALTER DATABASE to set it ONLINE.</span></span>  
  
  
