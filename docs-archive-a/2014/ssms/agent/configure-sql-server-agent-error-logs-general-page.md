---
title: 配置 SQL Server 代理错误日志（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd4c083ea7e7d220d5da20594079b7679c0bb724
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588242"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a><span data-ttu-id="8bc42-102">配置 SQL Server 代理错误日志（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="8bc42-102">Configure SQL Server Agent Error Logs (General Page)</span></span>
  <span data-ttu-id="8bc42-103">使用此屏幕可以查看和更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志记录的设置。</span><span class="sxs-lookup"><span data-stu-id="8bc42-103">Use this screen to view and update settings for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logging.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8bc42-104">选项</span><span class="sxs-lookup"><span data-stu-id="8bc42-104">Options</span></span>  
 <span data-ttu-id="8bc42-105">**错误日志文件**</span><span class="sxs-lookup"><span data-stu-id="8bc42-105">**Error log file**</span></span>  
 <span data-ttu-id="8bc42-106">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将写入错误日志的文件。</span><span class="sxs-lookup"><span data-stu-id="8bc42-106">Specifies the file to which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent writes error logs.</span></span>  
  
 <span data-ttu-id="8bc42-107">**...**</span><span class="sxs-lookup"><span data-stu-id="8bc42-107">**...**</span></span>  
 <span data-ttu-id="8bc42-108">浏览至错误日志文件。</span><span class="sxs-lookup"><span data-stu-id="8bc42-108">Browse to the error log file.</span></span>  
  
 <span data-ttu-id="8bc42-109">**写入 OEM 错误日志**</span><span class="sxs-lookup"><span data-stu-id="8bc42-109">**Write OEM error log**</span></span>  
 <span data-ttu-id="8bc42-110">以非 Unicode 文件的形式编写错误日志文件。</span><span class="sxs-lookup"><span data-stu-id="8bc42-110">Writes the error log file as a non-Unicode file.</span></span> <span data-ttu-id="8bc42-111">这可以减少日志文件占用的磁盘空间量。</span><span class="sxs-lookup"><span data-stu-id="8bc42-111">This reduces the amount of disk space consumed by the log file.</span></span> <span data-ttu-id="8bc42-112">不过，如果启用此选项，读取包含 Unicode 数据的消息时会有一定的难度。</span><span class="sxs-lookup"><span data-stu-id="8bc42-112">However, messages that include Unicode data may be more difficult to read when this option is enabled.</span></span>  
  
 <span data-ttu-id="8bc42-113">**错误**</span><span class="sxs-lookup"><span data-stu-id="8bc42-113">**Errors**</span></span>  
 <span data-ttu-id="8bc42-114">仅将错误和信息性消息写入日志文件。</span><span class="sxs-lookup"><span data-stu-id="8bc42-114">Writes only errors and informational messages to the log file.</span></span>  
  
 <span data-ttu-id="8bc42-115">**警告**</span><span class="sxs-lookup"><span data-stu-id="8bc42-115">**Warnings**</span></span>  
 <span data-ttu-id="8bc42-116">仅将警告和信息性消息写入日志文件。</span><span class="sxs-lookup"><span data-stu-id="8bc42-116">Writes only warnings and informational messages to the log file.</span></span>  
  
 <span data-ttu-id="8bc42-117">**信息**</span><span class="sxs-lookup"><span data-stu-id="8bc42-117">**Information**</span></span>  
 <span data-ttu-id="8bc42-118">仅将信息性消息写入日志文件。</span><span class="sxs-lookup"><span data-stu-id="8bc42-118">Writes only informational messages to the log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc42-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bc42-119">See Also</span></span>  
 [<span data-ttu-id="8bc42-120">SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="8bc42-120">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
