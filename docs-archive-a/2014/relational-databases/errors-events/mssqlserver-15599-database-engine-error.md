---
title: MSSQLSERVER_15599 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 15f1b3eb6d97837f1c1c4a9944535cade5b31300
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589643"
---
# <a name="mssqlserver_15599"></a><span data-ttu-id="c86be-102">MSSQLSERVER_15599</span><span class="sxs-lookup"><span data-stu-id="c86be-102">MSSQLSERVER_15599</span></span>
    
## <a name="details"></a><span data-ttu-id="c86be-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="c86be-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c86be-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="c86be-104">Product Name</span></span>|<span data-ttu-id="c86be-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c86be-105">SQL Server</span></span>|  
|<span data-ttu-id="c86be-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="c86be-106">Event ID</span></span>|<span data-ttu-id="c86be-107">15599</span><span class="sxs-lookup"><span data-stu-id="c86be-107">15599</span></span>|  
|<span data-ttu-id="c86be-108">事件源</span><span class="sxs-lookup"><span data-stu-id="c86be-108">Event Source</span></span>|<span data-ttu-id="c86be-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c86be-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c86be-110">组件</span><span class="sxs-lookup"><span data-stu-id="c86be-110">Component</span></span>|<span data-ttu-id="c86be-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c86be-111">SQLEngine</span></span>|  
|<span data-ttu-id="c86be-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="c86be-112">Symbolic Name</span></span>|<span data-ttu-id="c86be-113">SEC_LOCAL_TEMP_AUDIT_PERMISSIONS</span><span class="sxs-lookup"><span data-stu-id="c86be-113">SEC_LOCAL_TEMP_AUDIT_PERMISSIONS</span></span>|  
|<span data-ttu-id="c86be-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="c86be-114">Message Text</span></span>|<span data-ttu-id="c86be-115">不能对本地临时对象设置审核和权限。</span><span class="sxs-lookup"><span data-stu-id="c86be-115">Auditing and permissions can't be set on local temporary objects.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c86be-116">说明</span><span class="sxs-lookup"><span data-stu-id="c86be-116">Explanation</span></span>  
 <span data-ttu-id="c86be-117">为本地或全局临时对象设置审核和权限不起作用。</span><span class="sxs-lookup"><span data-stu-id="c86be-117">Auditing and permissions do not have any effect when set for local or global temp objects.</span></span> <span data-ttu-id="c86be-118">这些语句不会导致错误（操作将返回成功消息），但是不起作用。</span><span class="sxs-lookup"><span data-stu-id="c86be-118">The statements do not result in an error (the operations will return success), but have no effect.</span></span>  
  
 <span data-ttu-id="c86be-119">此行为尚未更改，但是从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 开始，会显示此信息性消息提醒用户。</span><span class="sxs-lookup"><span data-stu-id="c86be-119">This behavior has not changed, however beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this informational message alerts the user.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c86be-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="c86be-120">User Action</span></span>  
 <span data-ttu-id="c86be-121">不需要执行任何操作，但是请考虑删除尝试对本地或全局临时对象设置审核或权限的语句。</span><span class="sxs-lookup"><span data-stu-id="c86be-121">No action is necessary, but consider removing statements that attempt to set auditing or permissions on local or global temp objects.</span></span>  
  
  
