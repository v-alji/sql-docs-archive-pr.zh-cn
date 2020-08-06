---
title: SQL Server 代理属性（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: a67d5431be4025c18b11d6791b016fa83e957810
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590006"
---
# <a name="sql-server-agent-properties-general-page"></a><span data-ttu-id="18b0d-102">SQL Server 代理属性（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="18b0d-102">SQL Server Agent Properties (General Page)</span></span>
  <span data-ttu-id="18b0d-103">使用此页可以查看和修改代理服务的常规属性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="18b0d-103">Use this page to view and modify the general properties of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="18b0d-104">选项</span><span class="sxs-lookup"><span data-stu-id="18b0d-104">Options</span></span>  
 <span data-ttu-id="18b0d-105">**服务状态**</span><span class="sxs-lookup"><span data-stu-id="18b0d-105">**Service state**</span></span>  
 <span data-ttu-id="18b0d-106">显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务的当前状态。</span><span class="sxs-lookup"><span data-stu-id="18b0d-106">Displays the current state of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
 <span data-ttu-id="18b0d-107">**SQL Server 意外停止时自动重新启动**</span><span class="sxs-lookup"><span data-stu-id="18b0d-107">**Auto restart SQL Server if it stops unexpectedly**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="18b0d-108">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 意外停止，代理将重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="18b0d-108">Agent restarts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stops unexpectedly.</span></span>  
  
 <span data-ttu-id="18b0d-109">**SQL Server 代理意外停止时自动重新启动**</span><span class="sxs-lookup"><span data-stu-id="18b0d-109">**Auto restart SQL Server Agent if it stops unexpectedly**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="18b0d-110">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理意外停止，将重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="18b0d-110">restarts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stops unexpectedly.</span></span>  
  
 <span data-ttu-id="18b0d-111">**Filename**</span><span class="sxs-lookup"><span data-stu-id="18b0d-111">**Filename**</span></span>  
 <span data-ttu-id="18b0d-112">指定错误日志的文件名。</span><span class="sxs-lookup"><span data-stu-id="18b0d-112">Specify the file name for the error log.</span></span>  
  
 <span data-ttu-id="18b0d-113">**...**</span><span class="sxs-lookup"><span data-stu-id="18b0d-113">**...**</span></span>  
 <span data-ttu-id="18b0d-114">浏览至错误日志文件。</span><span class="sxs-lookup"><span data-stu-id="18b0d-114">Browse to the error log file.</span></span>  
  
 <span data-ttu-id="18b0d-115">**包含执行跟踪消息**</span><span class="sxs-lookup"><span data-stu-id="18b0d-115">**Include execution trace messages**</span></span>  
 <span data-ttu-id="18b0d-116">在错误日志中包含执行跟踪消息。</span><span class="sxs-lookup"><span data-stu-id="18b0d-116">Includes execution trace messages in the error log.</span></span> <span data-ttu-id="18b0d-117">跟踪消息提供了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理操作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="18b0d-117">Trace messages provide detailed information on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operation.</span></span> <span data-ttu-id="18b0d-118">因此，在选中此选项时，日志文件需要更多的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="18b0d-118">Therefore, the log file requires more disk space when this option is selected.</span></span> <span data-ttu-id="18b0d-119">只有在排除与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理有关的问题时才需要选中此选项。</span><span class="sxs-lookup"><span data-stu-id="18b0d-119">This option should only be selected while troubleshooting a problem that may involve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
 <span data-ttu-id="18b0d-120">**写入 OEM 文件**</span><span class="sxs-lookup"><span data-stu-id="18b0d-120">**Write OEM file**</span></span>  
 <span data-ttu-id="18b0d-121">以非 Unicode 文件的形式编写错误日志文件。</span><span class="sxs-lookup"><span data-stu-id="18b0d-121">Writes the error log file as a non-Unicode file.</span></span> <span data-ttu-id="18b0d-122">这可以减少日志文件占用的磁盘空间量。</span><span class="sxs-lookup"><span data-stu-id="18b0d-122">This reduces the amount of disk space consumed by the log file.</span></span> <span data-ttu-id="18b0d-123">不过，如果启用此选项，读取包含 Unicode 数据的消息时会有一定的难度。</span><span class="sxs-lookup"><span data-stu-id="18b0d-123">However, messages that include Unicode data may be more difficult to read when this option is enabled.</span></span>  
  
 <span data-ttu-id="18b0d-124">**Net send 收件人**</span><span class="sxs-lookup"><span data-stu-id="18b0d-124">**Net send recipient**</span></span>  
 <span data-ttu-id="18b0d-125">键入操作员的名称，该操作员负责接收针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理写入日志文件的消息的 net send 通知。</span><span class="sxs-lookup"><span data-stu-id="18b0d-125">Type the name of an operator to receive net send notification of messages that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent writes to the log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b0d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18b0d-126">See Also</span></span>  
 <span data-ttu-id="18b0d-127">[运算符](operators.md) </span><span class="sxs-lookup"><span data-stu-id="18b0d-127">[Operators](operators.md) </span></span>  
 [<span data-ttu-id="18b0d-128">SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="18b0d-128">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
