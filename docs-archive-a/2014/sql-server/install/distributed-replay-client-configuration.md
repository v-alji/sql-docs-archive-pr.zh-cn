---
title: Distributed Replay 客户端配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 53124029483c25ed7894b279283e1de02c647350
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591104"
---
# <a name="distributed-replay-client-configuration"></a><span data-ttu-id="495f1-102">Distributed Replay 客户端配置</span><span class="sxs-lookup"><span data-stu-id="495f1-102">Distributed Replay Client Configuration</span></span>
  <span data-ttu-id="495f1-103">使用 **安装向导的** “Distributed Replay 客户端配置” [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 页可以指定您希望向其授予针对 Distributed Replay 客户端服务的管理权限的用户。</span><span class="sxs-lookup"><span data-stu-id="495f1-103">Use the **Distributed Replay Client Configuration** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify the users you want to grant administrative permissions to for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="495f1-104">具有管理权限的用户将可以不受限制地访问 Distributed Replay 客户端服务。</span><span class="sxs-lookup"><span data-stu-id="495f1-104">Users that have administrative permissions will have unlimited access to the Distributed Replay client service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="495f1-105">选项</span><span class="sxs-lookup"><span data-stu-id="495f1-105">Options</span></span>  
 <span data-ttu-id="495f1-106">**控制器名称**</span><span class="sxs-lookup"><span data-stu-id="495f1-106">**Controller Name**</span></span>  
 <span data-ttu-id="495f1-107">这是一个可选参数，默认值为 \<*blank*> 。</span><span class="sxs-lookup"><span data-stu-id="495f1-107">This is an optional parameter, and the default value is \<*blank*>.</span></span>  
  
 <span data-ttu-id="495f1-108">输入客户端计算机将与 Distributed Replay 客户端服务进行通信的控制器的名称。</span><span class="sxs-lookup"><span data-stu-id="495f1-108">Enter the name of the controller that the client computer will communicate with for the Distributed Replay client service.</span></span> <span data-ttu-id="495f1-109">注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="495f1-109">Note the following:</span></span>  
  
-   <span data-ttu-id="495f1-110">名称必须为完全限定域名 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="495f1-110">The name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="495f1-111">例如，位于 Microsoft 的产品层次结构中名为 server1 的主机必须具有 server1.products.microsoft.com 的 FQDN。</span><span class="sxs-lookup"><span data-stu-id="495f1-111">For example, a host called server1 in the products hierarchy at Microsoft may have an FQDN of server1.products.microsoft.com.</span></span>  
  
-   <span data-ttu-id="495f1-112">如果您已经设置了一个控制器，则在配置每个客户端时输入该控制器的名称。</span><span class="sxs-lookup"><span data-stu-id="495f1-112">If you have already set up a controller, enter the name of the controller while configuring each client.</span></span>  
  
-   <span data-ttu-id="495f1-113">如果您尚未设置控制器，则可以将控制器名称保留为空。</span><span class="sxs-lookup"><span data-stu-id="495f1-113">If you have net yet set up a controller, you can leave the controller name blank.</span></span> <span data-ttu-id="495f1-114">但是，您必须在 **“客户端配置”** 文件中手动输入控制器名称。</span><span class="sxs-lookup"><span data-stu-id="495f1-114">However, you must manually enter the controller name in the **client configuration** file.</span></span>  
  
 <span data-ttu-id="495f1-115">**工作目录**</span><span class="sxs-lookup"><span data-stu-id="495f1-115">**Working Directory**</span></span>  
 <span data-ttu-id="495f1-116">为 Distributed Replay 客户端服务指定工作目录。</span><span class="sxs-lookup"><span data-stu-id="495f1-116">Specify the working directory for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="495f1-117">默认工作目录为 \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\。</span><span class="sxs-lookup"><span data-stu-id="495f1-117">The default working directory is \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.</span></span>  
  
 <span data-ttu-id="495f1-118">**默认目录**</span><span class="sxs-lookup"><span data-stu-id="495f1-118">**Result Directory**</span></span>  
 <span data-ttu-id="495f1-119">为 Distributed Replay 客户端服务指定结果目录。</span><span class="sxs-lookup"><span data-stu-id="495f1-119">Specify the result directory for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="495f1-120">默认结果目录为 \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\。</span><span class="sxs-lookup"><span data-stu-id="495f1-120">The default result directory is \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.</span></span>  
  
  
