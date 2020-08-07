---
title: MSSQLSERVER_5237 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 224317e290ce15aaed979129733b6273b3b663df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589585"
---
# <a name="mssqlserver_5237"></a><span data-ttu-id="f4ed6-102">MSSQLSERVER_5237</span><span class="sxs-lookup"><span data-stu-id="f4ed6-102">MSSQLSERVER_5237</span></span>
    
## <a name="details"></a><span data-ttu-id="f4ed6-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f4ed6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4ed6-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f4ed6-104">Product Name</span></span>|<span data-ttu-id="f4ed6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f4ed6-105">SQL Server</span></span>|  
|<span data-ttu-id="f4ed6-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f4ed6-106">Event ID</span></span>|<span data-ttu-id="f4ed6-107">5237</span><span class="sxs-lookup"><span data-stu-id="f4ed6-107">5237</span></span>|  
|<span data-ttu-id="f4ed6-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f4ed6-108">Event Source</span></span>|<span data-ttu-id="f4ed6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f4ed6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f4ed6-110">组件</span><span class="sxs-lookup"><span data-stu-id="f4ed6-110">Component</span></span>|<span data-ttu-id="f4ed6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f4ed6-111">SQLEngine</span></span>|  
|<span data-ttu-id="f4ed6-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f4ed6-112">Symbolic Name</span></span>|<span data-ttu-id="f4ed6-113">DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE</span><span class="sxs-lookup"><span data-stu-id="f4ed6-113">DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE</span></span>|  
|<span data-ttu-id="f4ed6-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f4ed6-114">Message Text</span></span>|<span data-ttu-id="f4ed6-115">由于内部查询错误，对对象 'NAME' (对象 ID 为 O_ID)进行的 DBCC 跨行集检查失败。</span><span class="sxs-lookup"><span data-stu-id="f4ed6-115">DBCC cross-rowset check failed for object 'NAME' (object ID O_ID) due to an internal query error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f4ed6-116">说明</span><span class="sxs-lookup"><span data-stu-id="f4ed6-116">Explanation</span></span>  
 <span data-ttu-id="f4ed6-117">因出现内部错误，DBCC 无法通过执行查询来检查索引视图。</span><span class="sxs-lookup"><span data-stu-id="f4ed6-117">An internal error resulted in DBCC not being able to execute the query to check indexed views.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f4ed6-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="f4ed6-118">User Action</span></span>  
 <span data-ttu-id="f4ed6-119">重新运行 DBCC 命令。</span><span class="sxs-lookup"><span data-stu-id="f4ed6-119">Rerun the DBCC command.</span></span>  
  
  
