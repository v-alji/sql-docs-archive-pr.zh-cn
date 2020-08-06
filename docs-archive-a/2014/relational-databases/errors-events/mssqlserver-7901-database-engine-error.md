---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fae6e55cbe7170f795aff85400da2c5cdaef780a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586710"
---
# <a name="mssqlserver_7901"></a><span data-ttu-id="d33ea-102">MSSQLSERVER_7901</span><span class="sxs-lookup"><span data-stu-id="d33ea-102">MSSQLSERVER_7901</span></span>
    
## <a name="details"></a><span data-ttu-id="d33ea-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d33ea-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d33ea-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d33ea-104">Product Name</span></span>|<span data-ttu-id="d33ea-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d33ea-105">SQL Server</span></span>|  
|<span data-ttu-id="d33ea-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d33ea-106">Event ID</span></span>|<span data-ttu-id="d33ea-107">7901</span><span class="sxs-lookup"><span data-stu-id="d33ea-107">7901</span></span>|  
|<span data-ttu-id="d33ea-108">事件源</span><span class="sxs-lookup"><span data-stu-id="d33ea-108">Event Source</span></span>|<span data-ttu-id="d33ea-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d33ea-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d33ea-110">组件</span><span class="sxs-lookup"><span data-stu-id="d33ea-110">Component</span></span>|<span data-ttu-id="d33ea-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d33ea-111">SQLEngine</span></span>|  
|<span data-ttu-id="d33ea-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="d33ea-112">Symbolic Name</span></span>|<span data-ttu-id="d33ea-113">DBCC2_DATABASE_IN_EMERGENCY_MODE</span><span class="sxs-lookup"><span data-stu-id="d33ea-113">DBCC2_DATABASE_IN_EMERGENCY_MODE</span></span>|  
|<span data-ttu-id="d33ea-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="d33ea-114">Message Text</span></span>|<span data-ttu-id="d33ea-115">未处理修复语句。</span><span class="sxs-lookup"><span data-stu-id="d33ea-115">The repair statement was not processed.</span></span> <span data-ttu-id="d33ea-116">当数据库处于紧急模式下时，不支持此级别的修复。</span><span class="sxs-lookup"><span data-stu-id="d33ea-116">This level of repair is not supported when the database is in emergency mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d33ea-117">说明</span><span class="sxs-lookup"><span data-stu-id="d33ea-117">Explanation</span></span>  
 <span data-ttu-id="d33ea-118">数据库处于紧急模式下，而且指定的修复级别不是 REPAIR_ALLOW_DATA_LOSS。</span><span class="sxs-lookup"><span data-stu-id="d33ea-118">The database is in emergency mode and a repair level other than REPAIR_ALLOW_DATA_LOSS has been specified.</span></span> <span data-ttu-id="d33ea-119">除非指定 REPAIR_ALLOW_DATA_LOSS，否则无法在紧急模式下进行修复。</span><span class="sxs-lookup"><span data-stu-id="d33ea-119">Repairs cannot be made in emergency mode unless REPAIR_ALLOW_DATA_LOSS is specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d33ea-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="d33ea-120">User Action</span></span>  
 <span data-ttu-id="d33ea-121">返回命令并指定 REPAIR_ALLOW_DATA_LOSS 选项。</span><span class="sxs-lookup"><span data-stu-id="d33ea-121">Rerun the command and specify the REPAIR_ALLOW_DATA_LOSS option.</span></span>  
  
  
