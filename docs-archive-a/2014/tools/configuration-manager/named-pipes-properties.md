---
title: Named Pipes 属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80790c1cb8830a0fd132721f375a70d2574421b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586035"
---
# <a name="named-pipes-properties"></a><span data-ttu-id="cf67b-102">Named Pipes 属性</span><span class="sxs-lookup"><span data-stu-id="cf67b-102">Named Pipes Properties</span></span>
  <span data-ttu-id="cf67b-103">使用“命名管道属性”  对话框中的“协议”  页，可以在使用命名管道协议时查看或更改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听的命名管道。</span><span class="sxs-lookup"><span data-stu-id="cf67b-103">Use the **Protocol**page on the **Named Pipes Properties** dialog box to view or change the named pipe that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens to, when using the Named Pipes protocol.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf67b-104">才能启用或禁用该协议，或更改命名管道。</span><span class="sxs-lookup"><span data-stu-id="cf67b-104">must be restarted to enable or disable the protocol, or change the named pipe.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf67b-105">选项</span><span class="sxs-lookup"><span data-stu-id="cf67b-105">Options</span></span>  
 <span data-ttu-id="cf67b-106">**已启用**</span><span class="sxs-lookup"><span data-stu-id="cf67b-106">**Enabled**</span></span>  
 <span data-ttu-id="cf67b-107">可能的值为“是”  和“否”  。</span><span class="sxs-lookup"><span data-stu-id="cf67b-107">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="cf67b-108">**管道名称**</span><span class="sxs-lookup"><span data-stu-id="cf67b-108">**Pipe Name**</span></span>  
 <span data-ttu-id="cf67b-109">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听的命名管道。</span><span class="sxs-lookup"><span data-stu-id="cf67b-109">Specifies the named pipe on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens.</span></span> <span data-ttu-id="cf67b-110">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听： `\\.\pipe\sql\query` （对于默认实例）和 `\\.\pipe\MSSQL$<instancename>\sql\query` （对于命名实例）。</span><span class="sxs-lookup"><span data-stu-id="cf67b-110">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on: `\\.\pipe\sql\query` for the default instance and `\\.\pipe\MSSQL$<instancename>\sql\query` for a named instance.</span></span> <span data-ttu-id="cf67b-111">此字段最多允许 2047 个字符。</span><span class="sxs-lookup"><span data-stu-id="cf67b-111">This field is limited to 2047 characters.</span></span>  
  
## <a name="creating-an-alternate-named-pipe"></a><span data-ttu-id="cf67b-112">创建备用命名管道</span><span class="sxs-lookup"><span data-stu-id="cf67b-112">Creating an Alternate Named Pipe</span></span>  
 <span data-ttu-id="cf67b-113">若要更改命名管道，可以在 **“管道名称”** 框中键入新的管道名称，然后停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，再将其重新启动。</span><span class="sxs-lookup"><span data-stu-id="cf67b-113">To change the named pipe, type the new pipe name in the **Pipe Name** box and then stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cf67b-114">由于 **sql\query** 众所周知是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用的命名管道，更改管道可以有效地降低恶意程序攻击的风险。</span><span class="sxs-lookup"><span data-stu-id="cf67b-114">Since **sql\query** is well known as the named pipe used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], changing the pipe can help reduce the risk of attack by malicious programs.</span></span>  
  
### <a name="example"></a><span data-ttu-id="cf67b-115">示例</span><span class="sxs-lookup"><span data-stu-id="cf67b-115">Example</span></span>  
 <span data-ttu-id="cf67b-116">键入 **\\\\.\pipe\unit\app** 以侦听 **unit\app** 管道。</span><span class="sxs-lookup"><span data-stu-id="cf67b-116">Type **\\\\.\pipe\unit\app** to listen on the **unit\app** pipe.</span></span>  
  
 <span data-ttu-id="cf67b-117">键入 **\\\\.\pipe\acct** 以侦听 **acct** 管道。</span><span class="sxs-lookup"><span data-stu-id="cf67b-117">Type **\\\\.\pipe\acct** to listen on the **acct** pipe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf67b-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf67b-118">See Also</span></span>  
 <span data-ttu-id="cf67b-119">[启用或禁用服务器网络协议](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="cf67b-119">[Enable or Disable a Server Network Protocol](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span></span>  
 <span data-ttu-id="cf67b-120">[选择网络协议](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="cf67b-120">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="cf67b-121">使用命名管道创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="cf67b-121">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
