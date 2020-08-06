---
title: MSSQLSERVER_5231 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 68f40ac3a566280526757bd8b83c784954ba3dde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687904"
---
# <a name="mssqlserver_5231"></a><span data-ttu-id="e8108-102">MSSQLSERVER_5231</span><span class="sxs-lookup"><span data-stu-id="e8108-102">MSSQLSERVER_5231</span></span>
    
## <a name="details"></a><span data-ttu-id="e8108-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="e8108-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e8108-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="e8108-104">Product Name</span></span>|<span data-ttu-id="e8108-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e8108-105">SQL Server</span></span>|  
|<span data-ttu-id="e8108-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e8108-106">Event ID</span></span>|<span data-ttu-id="e8108-107">5231</span><span class="sxs-lookup"><span data-stu-id="e8108-107">5231</span></span>|  
|<span data-ttu-id="e8108-108">事件源</span><span class="sxs-lookup"><span data-stu-id="e8108-108">Event Source</span></span>|<span data-ttu-id="e8108-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e8108-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e8108-110">组件</span><span class="sxs-lookup"><span data-stu-id="e8108-110">Component</span></span>|<span data-ttu-id="e8108-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e8108-111">SQLEngine</span></span>|  
|<span data-ttu-id="e8108-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="e8108-112">Symbolic Name</span></span>|<span data-ttu-id="e8108-113">DBCC4_DEADLOCK_SKIPPED_OBJECT</span><span class="sxs-lookup"><span data-stu-id="e8108-113">DBCC4_DEADLOCK_SKIPPED_OBJECT</span></span>|  
|<span data-ttu-id="e8108-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="e8108-114">Message Text</span></span>|<span data-ttu-id="e8108-115">对象 ID O_ID （对象“NAME”）：尝试锁定此对象以进行检查时出现死锁。</span><span class="sxs-lookup"><span data-stu-id="e8108-115">Object ID O_ID (object 'NAME'): A deadlock occurred while trying to lock this object for checking.</span></span> <span data-ttu-id="e8108-116">已跳过此对象，不会处理它。</span><span class="sxs-lookup"><span data-stu-id="e8108-116">This object has been skipped and will not be processed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e8108-117">说明</span><span class="sxs-lookup"><span data-stu-id="e8108-117">Explanation</span></span>  
 <span data-ttu-id="e8108-118">在 DBCC 尝试锁定该对象时出现死锁，而且 DBCC 被选作死锁牺牲品。</span><span class="sxs-lookup"><span data-stu-id="e8108-118">A deadlock occurred when DBCC was trying to lock the object, and DBCC was chosen as the deadlock victim.</span></span> <span data-ttu-id="e8108-119">不会处理该对象。</span><span class="sxs-lookup"><span data-stu-id="e8108-119">The object will not be processed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e8108-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="e8108-120">User Action</span></span>  
 <span data-ttu-id="e8108-121">无</span><span class="sxs-lookup"><span data-stu-id="e8108-121">None</span></span>  
  
  
