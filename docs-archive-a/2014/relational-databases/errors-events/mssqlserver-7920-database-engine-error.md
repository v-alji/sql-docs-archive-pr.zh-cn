---
title: MSSQLSERVER_7920 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7920 (Database Engine error)
ms.assetid: d16290ea-3875-4148-8d53-057bfee00438
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d8084a0542e9163ad72623336a909e65ca7617f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587409"
---
# <a name="mssqlserver_7920"></a><span data-ttu-id="8e48a-102">MSSQLSERVER_7920</span><span class="sxs-lookup"><span data-stu-id="8e48a-102">MSSQLSERVER_7920</span></span>
    
## <a name="details"></a><span data-ttu-id="8e48a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="8e48a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e48a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8e48a-104">Product Name</span></span>|<span data-ttu-id="8e48a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8e48a-105">SQL Server</span></span>|  
|<span data-ttu-id="8e48a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8e48a-106">Event ID</span></span>|<span data-ttu-id="8e48a-107">7920</span><span class="sxs-lookup"><span data-stu-id="8e48a-107">7920</span></span>|  
|<span data-ttu-id="8e48a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8e48a-108">Event Source</span></span>|<span data-ttu-id="8e48a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8e48a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8e48a-110">组件</span><span class="sxs-lookup"><span data-stu-id="8e48a-110">Component</span></span>|<span data-ttu-id="8e48a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8e48a-111">SQLEngine</span></span>|  
|<span data-ttu-id="8e48a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="8e48a-112">Symbolic Name</span></span>|<span data-ttu-id="8e48a-113">DBCC2_SUMMARY_ENTRIES</span><span class="sxs-lookup"><span data-stu-id="8e48a-113">DBCC2_SUMMARY_ENTRIES</span></span>|  
|<span data-ttu-id="8e48a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="8e48a-114">Message Text</span></span>|<span data-ttu-id="8e48a-115">已在系统目录中为数据库 ID D_ID 处理 ENTRY_COUNT 项。</span><span class="sxs-lookup"><span data-stu-id="8e48a-115">Processed ENTRY_COUNT entries in system catalog for database ID D_ID.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8e48a-116">说明</span><span class="sxs-lookup"><span data-stu-id="8e48a-116">Explanation</span></span>  
 <span data-ttu-id="8e48a-117">这是由 DBCC CHECKALLOC 以外的所有 DBCC CHECK 命令返回的信息性消息。</span><span class="sxs-lookup"><span data-stu-id="8e48a-117">This is an informational message returned by all DBCC CHECK commands except DBCC CHECKALLOC.</span></span> <span data-ttu-id="8e48a-118">返回值是所检查的总行集数。</span><span class="sxs-lookup"><span data-stu-id="8e48a-118">The value returned is the total number of rowsets checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8e48a-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="8e48a-119">User Action</span></span>  
 <span data-ttu-id="8e48a-120">无</span><span class="sxs-lookup"><span data-stu-id="8e48a-120">None</span></span>  
  
  
