---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5095a50f257abafb6ebde97bb32c57bc71fc4e09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587418"
---
# <a name="mssqlserver_5554"></a><span data-ttu-id="7a1e2-102">MSSQLSERVER_5554</span><span class="sxs-lookup"><span data-stu-id="7a1e2-102">MSSQLSERVER_5554</span></span>
    
## <a name="details"></a><span data-ttu-id="7a1e2-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="7a1e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7a1e2-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="7a1e2-104">Product Name</span></span>|<span data-ttu-id="7a1e2-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7a1e2-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7a1e2-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="7a1e2-106">Event ID</span></span>|<span data-ttu-id="7a1e2-107">5554</span><span class="sxs-lookup"><span data-stu-id="7a1e2-107">5554</span></span>|  
|<span data-ttu-id="7a1e2-108">事件源</span><span class="sxs-lookup"><span data-stu-id="7a1e2-108">Event Source</span></span>|<span data-ttu-id="7a1e2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7a1e2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7a1e2-110">组件</span><span class="sxs-lookup"><span data-stu-id="7a1e2-110">Component</span></span>|<span data-ttu-id="7a1e2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7a1e2-111">SQLEngine</span></span>|  
|<span data-ttu-id="7a1e2-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="7a1e2-112">Symbolic Name</span></span>|<span data-ttu-id="7a1e2-113">FS_MINIVER_OVERFLOW</span><span class="sxs-lookup"><span data-stu-id="7a1e2-113">FS_MINIVER_OVERFLOW</span></span>|  
|<span data-ttu-id="7a1e2-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="7a1e2-114">Message Text</span></span>|<span data-ttu-id="7a1e2-115">单个文件的版本总数已达到文件系统所设置的最大限制。</span><span class="sxs-lookup"><span data-stu-id="7a1e2-115">The total number of versions for a single file has reached the maximum limit set by the file system.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7a1e2-116">说明</span><span class="sxs-lookup"><span data-stu-id="7a1e2-116">Explanation</span></span>  
 <span data-ttu-id="7a1e2-117">在多个活动的结果集 (MARS) 或触发器方案中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 都使用由操作系统指定的最低版本。</span><span class="sxs-lookup"><span data-stu-id="7a1e2-117">In multiple active result sets (MARS) or trigger scenarios, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the miniversion specified by the operating system.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7a1e2-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="7a1e2-118">User Action</span></span>  
 <span data-ttu-id="7a1e2-119">尝试避免对同一事务中的数据进行重复更新。</span><span class="sxs-lookup"><span data-stu-id="7a1e2-119">Try to avoid repeated updates to the data in the same transaction.</span></span>  
  
  
