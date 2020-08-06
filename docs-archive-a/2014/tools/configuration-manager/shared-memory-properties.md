---
title: 共享内存属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6275215afdb6de3aa134dbffe74aa22b9e7b6f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590464"
---
# <a name="shared-memory-properties"></a><span data-ttu-id="c7eca-102">shared memory 属性</span><span class="sxs-lookup"><span data-stu-id="c7eca-102">Shared Memory Properties</span></span>
  <span data-ttu-id="c7eca-103">使用“共享内存属性”对话框的“协议”页可以启用或禁用共享内存协议。  </span><span class="sxs-lookup"><span data-stu-id="c7eca-103">Use the **Protocol**page on the **Shared Memory Properties** dialog box to enable or disable the shared memory protocol.</span></span> <span data-ttu-id="c7eca-104">Shared Memory 是可供使用的最简单协议，没有可配置的设置。</span><span class="sxs-lookup"><span data-stu-id="c7eca-104">Shared memory is the simplest protocol to use and has no configurable settings.</span></span> <span data-ttu-id="c7eca-105">由于使用 Shared Memory 协议的客户端仅可以连接到在同一台计算机运行的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，因此它对于大多数数据库活动而言是没有用的。</span><span class="sxs-lookup"><span data-stu-id="c7eca-105">Because clients using the shared memory protocol can only connect to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance running on the same computer, it is not useful for most database activity.</span></span> <span data-ttu-id="c7eca-106">如果怀疑其他协议配置有误，请使用 Shared Memory 协议进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="c7eca-106">Use the shared memory protocol for troubleshooting when you suspect the other protocols are configured incorrectly.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c7eca-107">才能启用或禁用该协议。</span><span class="sxs-lookup"><span data-stu-id="c7eca-107">must be restarted to enable or disable the protocol.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c7eca-108">选项</span><span class="sxs-lookup"><span data-stu-id="c7eca-108">Options</span></span>  
 <span data-ttu-id="c7eca-109">**已启用**</span><span class="sxs-lookup"><span data-stu-id="c7eca-109">**Enabled**</span></span>  
 <span data-ttu-id="c7eca-110">可能的值为“是”  和“否”  。</span><span class="sxs-lookup"><span data-stu-id="c7eca-110">Possible values are **Yes** and **No**.</span></span> <span data-ttu-id="c7eca-111">默认情况下，Shared Memory 协议是启用的。</span><span class="sxs-lookup"><span data-stu-id="c7eca-111">The shared memory protocol is enabled by default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7eca-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7eca-112">See Also</span></span>  
 <span data-ttu-id="c7eca-113">[选择网络协议](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="c7eca-113">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="c7eca-114">使用 Shared Memory 协议创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="c7eca-114">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
