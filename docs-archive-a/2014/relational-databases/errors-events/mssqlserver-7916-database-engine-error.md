---
title: MSSQLSERVER_7916 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21b31eedf61369d9c4d1cfdfd5f53eebd3f5341c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587411"
---
# <a name="mssqlserver_7916"></a><span data-ttu-id="6a574-102">MSSQLSERVER_7916</span><span class="sxs-lookup"><span data-stu-id="6a574-102">MSSQLSERVER_7916</span></span>
    
## <a name="details"></a><span data-ttu-id="6a574-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6a574-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a574-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6a574-104">Product Name</span></span>|<span data-ttu-id="6a574-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a574-105">SQL Server</span></span>|  
|<span data-ttu-id="6a574-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6a574-106">Event ID</span></span>|<span data-ttu-id="6a574-107">7916</span><span class="sxs-lookup"><span data-stu-id="6a574-107">7916</span></span>|  
|<span data-ttu-id="6a574-108">事件源</span><span class="sxs-lookup"><span data-stu-id="6a574-108">Event Source</span></span>|<span data-ttu-id="6a574-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6a574-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6a574-110">组件</span><span class="sxs-lookup"><span data-stu-id="6a574-110">Component</span></span>|<span data-ttu-id="6a574-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6a574-111">SQLEngine</span></span>|  
|<span data-ttu-id="6a574-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="6a574-112">Symbolic Name</span></span>|<span data-ttu-id="6a574-113">DBCC2_REPAIR_RECORD_DELETED</span><span class="sxs-lookup"><span data-stu-id="6a574-113">DBCC2_REPAIR_RECORD_DELETED</span></span>|  
|<span data-ttu-id="6a574-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="6a574-114">Message Text</span></span>|<span data-ttu-id="6a574-115">修复:对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE），页 P_ID，槽 S_ID 的记录已删除。</span><span class="sxs-lookup"><span data-stu-id="6a574-115">Repair: Deleted record for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), on page P_ID, slot S_ID.</span></span> <span data-ttu-id="6a574-116">将重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="6a574-116">Indexes will be rebuilt.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6a574-117">说明</span><span class="sxs-lookup"><span data-stu-id="6a574-117">Explanation</span></span>  
 <span data-ttu-id="6a574-118">这是来自 REPAIR 的信息性消息，指示已将指定记录从页中删除。</span><span class="sxs-lookup"><span data-stu-id="6a574-118">This is an information messages from REPAIR that indicates the specified record was deleted from the page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6a574-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="6a574-119">User Action</span></span>  
 <span data-ttu-id="6a574-120">无</span><span class="sxs-lookup"><span data-stu-id="6a574-120">None</span></span>  
  
  
