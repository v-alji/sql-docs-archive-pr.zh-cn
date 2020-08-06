---
title: remote admin connections 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c17cf278d18444c5b93d4f4b7e0a3da8dbfb671e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589873"
---
# <a name="remote-admin-connections-server-configuration-option"></a><span data-ttu-id="5e14d-102">remote admin connections 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="5e14d-102">remote admin connections Server Configuration Option</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5e14d-103">提供了专用管理员连接 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="5e14d-103">provides a dedicated administrator connection (DAC).</span></span> <span data-ttu-id="5e14d-104">DAC 允许管理员访问运行的服务器以执行诊断函数或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，或对服务器上的问题进行故障排除，即使服务器已锁定或在非正常状态下运行并且不响应 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 连接。</span><span class="sxs-lookup"><span data-stu-id="5e14d-104">The DAC lets an administrator access a running server to execute diagnostic functions or [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, or to troubleshoot problems on the server, even when the server is locked or running in an abnormal state and not responding to a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] connection.</span></span> <span data-ttu-id="5e14d-105">默认情况下，只有服务器上的客户端可以使用 DAC。</span><span class="sxs-lookup"><span data-stu-id="5e14d-105">By default, the DAC is only available from a client on the server.</span></span> <span data-ttu-id="5e14d-106">若要在远程计算机上启用客户端应用程序以使用 DAC，请使用 sp_configure 的远程管理连接选项。</span><span class="sxs-lookup"><span data-stu-id="5e14d-106">To enable client applications on remote computers to use the DAC, use the remote admin connections option of sp_configure.</span></span>  
  
 <span data-ttu-id="5e14d-107">默认情况下，DAC 仅侦听环回 IP 地址 (127.0.0.1) 端口 1434。</span><span class="sxs-lookup"><span data-stu-id="5e14d-107">By default, the DAC only listens on the loop-back IP address (127.0.0.1), port 1434.</span></span> <span data-ttu-id="5e14d-108">如果 TCP 端口 1434 不可用，在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 启动时将动态分配一个 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="5e14d-108">If TCP port 1434 is not available, a TCP port is dynamically assigned when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] starts up.</span></span> <span data-ttu-id="5e14d-109">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的多个实例安装在一台计算机上时，请查看错误日志以了解 TCP 端口号。</span><span class="sxs-lookup"><span data-stu-id="5e14d-109">When more than one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, check the error log for the TCP port number.</span></span>  
  
 <span data-ttu-id="5e14d-110">下表将列出远程管理连接选项的可能值。</span><span class="sxs-lookup"><span data-stu-id="5e14d-110">The following table lists the possible values for the remote admin connections option.</span></span>  
  
|<span data-ttu-id="5e14d-111">值</span><span class="sxs-lookup"><span data-stu-id="5e14d-111">Value</span></span>|<span data-ttu-id="5e14d-112">说明</span><span class="sxs-lookup"><span data-stu-id="5e14d-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e14d-113">0</span><span class="sxs-lookup"><span data-stu-id="5e14d-113">0</span></span>|<span data-ttu-id="5e14d-114">指明仅允许本地连接使用 DAC。</span><span class="sxs-lookup"><span data-stu-id="5e14d-114">Indicates only local connections are allowed by using the DAC.</span></span>|  
|<span data-ttu-id="5e14d-115">1</span><span class="sxs-lookup"><span data-stu-id="5e14d-115">1</span></span>|<span data-ttu-id="5e14d-116">指明允许远程连接使用 DAC。</span><span class="sxs-lookup"><span data-stu-id="5e14d-116">Indicates remote connections are allowed by using the DAC.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5e14d-117">示例</span><span class="sxs-lookup"><span data-stu-id="5e14d-117">Example</span></span>  
 <span data-ttu-id="5e14d-118">以下示例表示远程计算机可以使用 DAC。</span><span class="sxs-lookup"><span data-stu-id="5e14d-118">The following example enables the DAC from a remote computer.</span></span>  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e14d-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e14d-119">See Also</span></span>  
 [<span data-ttu-id="5e14d-120">用于数据库管理员的诊断连接</span><span class="sxs-lookup"><span data-stu-id="5e14d-120">Diagnostic Connection for Database Administrators</span></span>](diagnostic-connection-for-database-administrators.md)  
  
  
