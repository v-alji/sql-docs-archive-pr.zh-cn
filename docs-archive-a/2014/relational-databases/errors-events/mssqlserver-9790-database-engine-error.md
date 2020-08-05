---
title: MSSQLSERVER_9790 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d6d065d4a0e841da3b5ecb84f902df17dcfd60c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581227"
---
# <a name="mssqlserver_9790"></a><span data-ttu-id="237c5-102">MSSQLSERVER_9790</span><span class="sxs-lookup"><span data-stu-id="237c5-102">MSSQLSERVER_9790</span></span>
    
## <a name="details"></a><span data-ttu-id="237c5-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="237c5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="237c5-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="237c5-104">Product Name</span></span>|<span data-ttu-id="237c5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="237c5-105">SQL Server</span></span>|  
|<span data-ttu-id="237c5-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="237c5-106">Event ID</span></span>|<span data-ttu-id="237c5-107">9790</span><span class="sxs-lookup"><span data-stu-id="237c5-107">9790</span></span>|  
|<span data-ttu-id="237c5-108">事件源</span><span class="sxs-lookup"><span data-stu-id="237c5-108">Event Source</span></span>|<span data-ttu-id="237c5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="237c5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="237c5-110">组件</span><span class="sxs-lookup"><span data-stu-id="237c5-110">Component</span></span>|<span data-ttu-id="237c5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="237c5-111">SQLEngine</span></span>|  
|<span data-ttu-id="237c5-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="237c5-112">Symbolic Name</span></span>|<span data-ttu-id="237c5-113">SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER</span><span class="sxs-lookup"><span data-stu-id="237c5-113">SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER</span></span>|  
|<span data-ttu-id="237c5-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="237c5-114">Message Text</span></span>|<span data-ttu-id="237c5-115">无法确定传入消息的路由。</span><span class="sxs-lookup"><span data-stu-id="237c5-115">Unable to route the incoming message.</span></span> <span data-ttu-id="237c5-116">包含路由信息的系统数据库 MSDB 处于 SINGLE USER 模式。</span><span class="sxs-lookup"><span data-stu-id="237c5-116">The system database MSDB containing routing information is in SINGLE USER mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="237c5-117">说明</span><span class="sxs-lookup"><span data-stu-id="237c5-117">Explanation</span></span>  
 <span data-ttu-id="237c5-118">尝试对从网络接收的消息进行分类时出错，因为 MSDB 数据库处于 SINGLE USER 模式。</span><span class="sxs-lookup"><span data-stu-id="237c5-118">An error occurred while trying to classify a message received off the wire because the MSDB database was in Single User mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="237c5-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="237c5-119">User Action</span></span>  
 <span data-ttu-id="237c5-120">使用 ALTER DATABASE 命令将 MSDB 更改为 MULTI USER 模式。</span><span class="sxs-lookup"><span data-stu-id="237c5-120">Change MSDB to be in MULTI USER mode with the ALTER DATABASE command.</span></span>  
  
  
