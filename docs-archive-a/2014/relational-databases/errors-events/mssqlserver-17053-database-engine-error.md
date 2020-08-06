---
title: MSSQLSERVER_17053 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11137ba334b66f20c7d9a6caaaf7d1ef42c15dec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576797"
---
# <a name="mssqlserver_17053"></a><span data-ttu-id="96976-102">MSSQLSERVER_17053</span><span class="sxs-lookup"><span data-stu-id="96976-102">MSSQLSERVER_17053</span></span>
    
## <a name="details"></a><span data-ttu-id="96976-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="96976-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96976-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="96976-104">Product Name</span></span>|<span data-ttu-id="96976-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="96976-105">SQL Server</span></span>|  
|<span data-ttu-id="96976-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="96976-106">Event ID</span></span>|<span data-ttu-id="96976-107">17053</span><span class="sxs-lookup"><span data-stu-id="96976-107">17053</span></span>|  
|<span data-ttu-id="96976-108">事件源</span><span class="sxs-lookup"><span data-stu-id="96976-108">Event Source</span></span>|<span data-ttu-id="96976-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="96976-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="96976-110">组件</span><span class="sxs-lookup"><span data-stu-id="96976-110">Component</span></span>|<span data-ttu-id="96976-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="96976-111">SQLEngine</span></span>|  
|<span data-ttu-id="96976-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="96976-112">Symbolic Name</span></span>|<span data-ttu-id="96976-113">OS_ERROR</span><span class="sxs-lookup"><span data-stu-id="96976-113">OS_ERROR</span></span>|  
|<span data-ttu-id="96976-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="96976-114">Message Text</span></span>|<span data-ttu-id="96976-115">%ls:遇到操作系统错误 %ls。</span><span class="sxs-lookup"><span data-stu-id="96976-115">%ls: Operating system error %ls encountered.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="96976-116">说明</span><span class="sxs-lookup"><span data-stu-id="96976-116">Explanation</span></span>  
 <span data-ttu-id="96976-117">出现了一般性的操作系统错误。</span><span class="sxs-lookup"><span data-stu-id="96976-117">Generic operating system error occurred.</span></span>  <span data-ttu-id="96976-118">不清楚会出现什么状态。</span><span class="sxs-lookup"><span data-stu-id="96976-118">Not clear what the resulting state is.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="96976-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="96976-119">User Action</span></span>  
 <span data-ttu-id="96976-120">此错误通常伴随某个其他错误一起出现，应参考此错误以帮助诊断该故障。</span><span class="sxs-lookup"><span data-stu-id="96976-120">Usually this is in conjunction with some other error and should be used to help diagnose that failure.</span></span> <span data-ttu-id="96976-121">示例包括数据或日志文件读取或写入失败、注册表读取/写入操作或其他意外 Win32API 故障。</span><span class="sxs-lookup"><span data-stu-id="96976-121">Examples would include reads or writes to data or log files that fail, registry read/write operations, or other unexpected Win32API failures.</span></span>  
  
  
