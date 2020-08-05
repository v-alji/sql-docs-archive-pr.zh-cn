---
title: MSSQLSERVER_3271 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3271 (Database Engine error)
ms.assetid: 21b8de4b-6624-4163-9561-1a6cc8fe3d51
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56bdb5875dbba3fbe5037a308d713170a9b6f9ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581256"
---
# <a name="mssqlserver_3271"></a><span data-ttu-id="417df-102">MSSQLSERVER_3271</span><span class="sxs-lookup"><span data-stu-id="417df-102">MSSQLSERVER_3271</span></span>
    
## <a name="details"></a><span data-ttu-id="417df-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="417df-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="417df-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="417df-104">Product Name</span></span>|<span data-ttu-id="417df-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="417df-105">SQL Server</span></span>|  
|<span data-ttu-id="417df-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="417df-106">Event ID</span></span>|<span data-ttu-id="417df-107">3271</span><span class="sxs-lookup"><span data-stu-id="417df-107">3271</span></span>|  
|<span data-ttu-id="417df-108">事件源</span><span class="sxs-lookup"><span data-stu-id="417df-108">Event Source</span></span>|<span data-ttu-id="417df-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="417df-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="417df-110">组件</span><span class="sxs-lookup"><span data-stu-id="417df-110">Component</span></span>|<span data-ttu-id="417df-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="417df-111">SQLEngine</span></span>|  
|<span data-ttu-id="417df-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="417df-112">Symbolic Name</span></span>|<span data-ttu-id="417df-113">DMPIO_IO_ERROR</span><span class="sxs-lookup"><span data-stu-id="417df-113">DMPIO_IO_ERROR</span></span>|  
|<span data-ttu-id="417df-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="417df-114">Message Text</span></span>|<span data-ttu-id="417df-115">在文件 "%ls:" 上发生不可恢复的 I/O 错误: %ls。</span><span class="sxs-lookup"><span data-stu-id="417df-115">A nonrecoverable I/O error occurred on file "%ls:" %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="417df-116">说明</span><span class="sxs-lookup"><span data-stu-id="417df-116">Explanation</span></span>  
 <span data-ttu-id="417df-117">这是一个一般错误，是在操作系统在备份或还原操作过程中执行 I/O 的同时引发错误时出现的。</span><span class="sxs-lookup"><span data-stu-id="417df-117">This is a general error that occurs when the operating system raises an error while performing I/O during a backup or restore operation.</span></span> <span data-ttu-id="417df-118">在大多数情况下，原因仅仅是备份介质已满。</span><span class="sxs-lookup"><span data-stu-id="417df-118">In most situations the cause is simply that the backup medium is full.</span></span>  
  
 <span data-ttu-id="417df-119">该错误可能包含来自操作系统的其他文本，指示磁盘已满。</span><span class="sxs-lookup"><span data-stu-id="417df-119">The error may include additional text from the operating system indicating that the disk is full.</span></span> <span data-ttu-id="417df-120">在使用第三方备份软件执行备份或还原操作时，可能会出现指示备份失败的其他消息。</span><span class="sxs-lookup"><span data-stu-id="417df-120">When performing a backup or restore operation with third-party backup software an additional message may occur indicating that the backup failed.</span></span> <span data-ttu-id="417df-121">该消息可能与以下文本类似：</span><span class="sxs-lookup"><span data-stu-id="417df-121">The message may look similar to the following text:</span></span>  
  
```  
"2005-08-02 16:05:16.04 spid55 Error: 18210, Severity: 16, State: 1.  
 2005-08-02 16:05:16.04 spid55 BackupVirtualDeviceFile  
::RequestDurableMedia: Flush failure on backup device 'VDINULL'.   
Operating system error 995(The I/O operation has been aborted because   
of either a thread exit or an application request.)."  
```  
  
 <span data-ttu-id="417df-122">这指示备份软件要求终止备份或还原操作。</span><span class="sxs-lookup"><span data-stu-id="417df-122">This is an indication that the backup software requested a termination of the backup or restore operation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="417df-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="417df-123">User Action</span></span>  
 <span data-ttu-id="417df-124">根据需要执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="417df-124">Perform the following tasks as appropriate:</span></span>  
  
-   <span data-ttu-id="417df-125">检查基础系统错误消息和在此错误前面的 SQL Server 错误消息以查明失败的原因。</span><span class="sxs-lookup"><span data-stu-id="417df-125">Review the underlying system error messages and SQL Server error messages preceding this one to identify the cause of the failure.</span></span>  
  
-   <span data-ttu-id="417df-126">确保备份和还原介质具有足够的空间。</span><span class="sxs-lookup"><span data-stu-id="417df-126">Ensure that the backup and restore medium has sufficient space.</span></span>  
  
-   <span data-ttu-id="417df-127">更正由第三方备份和还原软件引发的任何错误。</span><span class="sxs-lookup"><span data-stu-id="417df-127">Correct any errors raised by third-party backup and restore software.</span></span>  
  
  
