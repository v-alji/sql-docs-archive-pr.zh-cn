---
title: MSSQLSERVER_17204 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c63f0b3d2aff8b909e3a7fc841c9038cf95a475e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581272"
---
# <a name="mssqlserver_17204"></a><span data-ttu-id="f33de-102">MSSQLSERVER_17204</span><span class="sxs-lookup"><span data-stu-id="f33de-102">MSSQLSERVER_17204</span></span>
    
## <a name="details"></a><span data-ttu-id="f33de-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f33de-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f33de-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f33de-104">Product Name</span></span>|<span data-ttu-id="f33de-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f33de-105">SQL Server</span></span>|  
|<span data-ttu-id="f33de-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f33de-106">Event ID</span></span>|<span data-ttu-id="f33de-107">17204</span><span class="sxs-lookup"><span data-stu-id="f33de-107">17204</span></span>|  
|<span data-ttu-id="f33de-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f33de-108">Event Source</span></span>|<span data-ttu-id="f33de-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f33de-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f33de-110">组件</span><span class="sxs-lookup"><span data-stu-id="f33de-110">Component</span></span>|<span data-ttu-id="f33de-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f33de-111">SQLEngine</span></span>|  
|<span data-ttu-id="f33de-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f33de-112">Symbolic Name</span></span>|<span data-ttu-id="f33de-113">DBLKIO_DEVOPENFAILED</span><span class="sxs-lookup"><span data-stu-id="f33de-113">DBLKIO_DEVOPENFAILED</span></span>|  
|<span data-ttu-id="f33de-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f33de-114">Message Text</span></span>|<span data-ttu-id="f33de-115">%ls:无法打开文件号 %d 的文件 %ls。</span><span class="sxs-lookup"><span data-stu-id="f33de-115">%ls: Could not open file %ls for file number %d.</span></span>  <span data-ttu-id="f33de-116">操作系统错误: %ls。</span><span class="sxs-lookup"><span data-stu-id="f33de-116">OS error: %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f33de-117">说明</span><span class="sxs-lookup"><span data-stu-id="f33de-117">Explanation</span></span>  
 <span data-ttu-id="f33de-118">SQL Server 由于指定错误而无法打开指定的文件。</span><span class="sxs-lookup"><span data-stu-id="f33de-118">SQL Server was unable to open the specified file due to the specified error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f33de-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="f33de-119">User Action</span></span>  
 <span data-ttu-id="f33de-120">诊断并更正操作系统，然后重试该操作。</span><span class="sxs-lookup"><span data-stu-id="f33de-120">Diagnose and correct the operating system, then retry the operation.</span></span>  
  
  
