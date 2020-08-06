---
title: MSSQLSERVER_17142 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17142 (Database Engine error)
ms.assetid: 83a53507-ac76-4cb9-b116-daf6f42aea1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1331eded0592fb2b40d917e4b4008a6ecb779a3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689407"
---
# <a name="mssqlserver_17142"></a><span data-ttu-id="5fb52-102">MSSQLSERVER_17142</span><span class="sxs-lookup"><span data-stu-id="5fb52-102">MSSQLSERVER_17142</span></span>
    
## <a name="details"></a><span data-ttu-id="5fb52-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5fb52-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fb52-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5fb52-104">Product Name</span></span>|<span data-ttu-id="5fb52-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5fb52-105">SQL Server</span></span>|  
|<span data-ttu-id="5fb52-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5fb52-106">Event ID</span></span>|<span data-ttu-id="5fb52-107">17142</span><span class="sxs-lookup"><span data-stu-id="5fb52-107">17142</span></span>|  
|<span data-ttu-id="5fb52-108">事件源</span><span class="sxs-lookup"><span data-stu-id="5fb52-108">Event Source</span></span>|<span data-ttu-id="5fb52-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5fb52-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5fb52-110">组件</span><span class="sxs-lookup"><span data-stu-id="5fb52-110">Component</span></span>|<span data-ttu-id="5fb52-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5fb52-111">SQLEngine</span></span>|  
|<span data-ttu-id="5fb52-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="5fb52-112">Symbolic Name</span></span>|<span data-ttu-id="5fb52-113">INIT_SRVC_PAUSED</span><span class="sxs-lookup"><span data-stu-id="5fb52-113">INIT_SRVC_PAUSED</span></span>|  
|<span data-ttu-id="5fb52-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="5fb52-114">Message Text</span></span>|<span data-ttu-id="5fb52-115">SQL Server 服务已经暂停。</span><span class="sxs-lookup"><span data-stu-id="5fb52-115">SQL Server service has been paused.</span></span> <span data-ttu-id="5fb52-116">不允许进行新的连接。</span><span class="sxs-lookup"><span data-stu-id="5fb52-116">No new connections will be allowed.</span></span> <span data-ttu-id="5fb52-117">要恢复此服务，请使用 SQL 计算机管理器或控制面板中的服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="5fb52-117">To resume the service, use SQL Computer Manager or the Services application in Control Panel.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5fb52-118">说明</span><span class="sxs-lookup"><span data-stu-id="5fb52-118">Explanation</span></span>  
 <span data-ttu-id="5fb52-119">服务控制管理器暂停了 SQL Server 的服务。</span><span class="sxs-lookup"><span data-stu-id="5fb52-119">Service Control Manager paused SQL Server's service</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5fb52-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="5fb52-120">User Action</span></span>  
 <span data-ttu-id="5fb52-121">使用 SQL Server 配置管理器恢复 SQL Server 的服务。</span><span class="sxs-lookup"><span data-stu-id="5fb52-121">Resume SQL Server's service using SQL Server Configuration Manager.</span></span>  
  
  
