---
title: " (顺序选项卡) 的客户端协议属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client protocols [SQL Server]
ms.assetid: 64fd7135-1756-4885-bed9-9ab8997ecc6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a367cff3495389d1a707ed108ba75e1e736538b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688371"
---
# <a name="client-protocols-properties-order-tab"></a><span data-ttu-id="3705c-102">客户端协议属性（“顺序”选项卡）</span><span class="sxs-lookup"><span data-stu-id="3705c-102">Client Protocols Properties (Order Tab)</span></span>
  <span data-ttu-id="3705c-103">使用“客户端协议属性”\*\*\*\* 对话框中的“顺序”\*\*\*\* 页，可以查看和启用客户端协议。</span><span class="sxs-lookup"><span data-stu-id="3705c-103">Use the **Order**page on the **Client Protocols Properties** dialog box to view and enable the client protocols.</span></span>  
  
 <span data-ttu-id="3705c-104">单击某个协议，再单击 **“启用”** 或 **“禁用”** ，可以将所选协议移到 **“启用的协议”** 列表或 **“禁用的协议”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="3705c-104">Click a protocol, and then click **Enable** or **Disable** to move the selected protocol to the **Disabled Protocols** or **Enabled Protocols** list.</span></span>  
  
 <span data-ttu-id="3705c-105">将按协议列出的顺序尝试协议，首先尝试使用第一个列出的协议进行连接，然后使用第二个列出的协议，以此类推。通过单击向上键和向下键按钮，可以在“启用的协议”  列表中向上或向下移动协议。</span><span class="sxs-lookup"><span data-stu-id="3705c-105">Protocols are tried in the order listed, attempting to connect using the top protocol first, and then the second listed protocol, etc. Move protocols up or down the **Enabled Protocols** list, by clicking the up arrow and down arrow buttons.</span></span> <span data-ttu-id="3705c-106">从该计算机上的客户端连接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，将始终首先尝试使用“Shared Memory”  协议（如果已启用）。</span><span class="sxs-lookup"><span data-stu-id="3705c-106">When connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client on that computer, the **Shared Memory** protocol will always be tried first, if enabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3705c-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET SqlClient 不会使用这些设置。</span><span class="sxs-lookup"><span data-stu-id="3705c-107">These settings are not used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET SqlClient.</span></span> <span data-ttu-id="3705c-108">.NET SqlClient 的协议顺序依次为：TCP、命名管道。此顺序不能改变。</span><span class="sxs-lookup"><span data-stu-id="3705c-108">The protocol order for .NET SqlClient is first TCP, and then named pipes, which cannot be changed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3705c-109">选项</span><span class="sxs-lookup"><span data-stu-id="3705c-109">Options</span></span>  
 <span data-ttu-id="3705c-110">**“启用的协议”**</span><span class="sxs-lookup"><span data-stu-id="3705c-110">**Disabled Protocols**</span></span>  
 <span data-ttu-id="3705c-111">列出已安装但当前未使用的协议。</span><span class="sxs-lookup"><span data-stu-id="3705c-111">Lists protocols which are installed but are not currently used.</span></span>  
  
 <span data-ttu-id="3705c-112">**“禁用的协议”**</span><span class="sxs-lookup"><span data-stu-id="3705c-112">**Enabled Protocols**</span></span>  
 <span data-ttu-id="3705c-113">列出 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 此计算机上的客户端可以使用的协议。</span><span class="sxs-lookup"><span data-stu-id="3705c-113">Lists protocols which are available for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients on this computer.</span></span>  
  
 **>**  
 <span data-ttu-id="3705c-114">启用“禁用的协议”  框中当前突出显示的协议，会将其移到“启用的协议”  框中。</span><span class="sxs-lookup"><span data-stu-id="3705c-114">Enables the currently highlighted protocol in the **Disabled Protocols** box, moving it to the **Enabled Protocols** box.</span></span>  
  
 **\<**  
 <span data-ttu-id="3705c-115">禁用“启用的协议”  框中当前突出显示的协议，会将其移到“禁用的协议”  框中。</span><span class="sxs-lookup"><span data-stu-id="3705c-115">Disables the currently highlighted protocol in the **Enabled Protocols** box, moving it to the **Disabled Protocols** box.</span></span>  
  
 <span data-ttu-id="3705c-116">向上键</span><span class="sxs-lookup"><span data-stu-id="3705c-116">Up arrow</span></span>  
 <span data-ttu-id="3705c-117">在列表中向上移动突出显示的协议。</span><span class="sxs-lookup"><span data-stu-id="3705c-117">Moves the highlighted protocol up in the list.</span></span> <span data-ttu-id="3705c-118">这样就可以使网络库尝试使用所选协议进行连接的优先级提高。</span><span class="sxs-lookup"><span data-stu-id="3705c-118">This allows you to increase the priority in which the Net-Library will attempt to use the selected protocol for connections.</span></span>  
  
 <span data-ttu-id="3705c-119">向下键</span><span class="sxs-lookup"><span data-stu-id="3705c-119">Down arrow</span></span>  
 <span data-ttu-id="3705c-120">在列表中向下移动突出显示的协议。</span><span class="sxs-lookup"><span data-stu-id="3705c-120">Moves the highlighted protocol down in the list.</span></span> <span data-ttu-id="3705c-121">这样就可以使网络库尝试使用所选协议进行连接的优先级降低。</span><span class="sxs-lookup"><span data-stu-id="3705c-121">This allows you to decrease the priority in which the Net-Library will attempt to use the selected protocol for connections.</span></span>  
  
 <span data-ttu-id="3705c-122">**启用 Shared Memory 协议**</span><span class="sxs-lookup"><span data-stu-id="3705c-122">**Enable Shared Memory Protocol**</span></span>  
 <span data-ttu-id="3705c-123">从该计算机上的客户端连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，启用 Shared Memory 协议。在启用了该协议的情况下，始终首先尝试使用该协议。</span><span class="sxs-lookup"><span data-stu-id="3705c-123">Enables the shared memory protocol which is always tried first (if enabled), when connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client on that computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3705c-124">如果通过前缀或连接字符串的一部分指定了协议，则仅尝试使用指定的协议。</span><span class="sxs-lookup"><span data-stu-id="3705c-124">If the protocol is specified through a prefix or as part of the connection string, only the specified protocol is attempted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3705c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3705c-125">See Also</span></span>  
 [<span data-ttu-id="3705c-126">选择网络协议</span><span class="sxs-lookup"><span data-stu-id="3705c-126">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
