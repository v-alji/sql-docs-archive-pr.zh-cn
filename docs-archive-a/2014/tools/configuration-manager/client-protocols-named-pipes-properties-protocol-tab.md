---
title: 客户端协议 - 命名管道属性（“协议”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: stevestein
ms.author: sstein
ms.openlocfilehash: 169b6d98212c724b8d6c43615ae2fa7eba9cfc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687400"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a><span data-ttu-id="0ee67-102">客户端协议 - Named Pipes 属性（“协议”选项卡）</span><span class="sxs-lookup"><span data-stu-id="0ee67-102">Client Protocols - Named Pipes Properties (Protocol Tab)</span></span>
  <span data-ttu-id="0ee67-103">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，使用“Named Pipes 属性”  对话框中的“协议”  选项卡可以查看或修改默认管道的说明。</span><span class="sxs-lookup"><span data-stu-id="0ee67-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager use the **Protocol** tab on the **Named Pipes Properties** dialog box to view or modify the description of default pipe.</span></span> <span data-ttu-id="0ee67-104">若要连接到其他管道，请在 **“默认管道”** 框中键入该管道。</span><span class="sxs-lookup"><span data-stu-id="0ee67-104">To connect to a different pipe, type the pipe in the **Default Pipe** box.</span></span> <span data-ttu-id="0ee67-105">有关连接字符串的详细信息，请参阅 [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)。</span><span class="sxs-lookup"><span data-stu-id="0ee67-105">For more information about connection strings, see [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ee67-106">选项</span><span class="sxs-lookup"><span data-stu-id="0ee67-106">Options</span></span>  
 <span data-ttu-id="0ee67-107">**“默认管道”**</span><span class="sxs-lookup"><span data-stu-id="0ee67-107">**Default Pipe**</span></span>  
 <span data-ttu-id="0ee67-108">指定 Named Pipes 网络库用来尝试连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]目标实例的默认管道。</span><span class="sxs-lookup"><span data-stu-id="0ee67-108">Specifies the default pipe the Named Pipes Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ee67-109">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听： `\\.\pipe\sql\query`</span><span class="sxs-lookup"><span data-stu-id="0ee67-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on: `\\.\pipe\sql\query`</span></span>  
  
 <span data-ttu-id="0ee67-110">若要连接到默认管道，请输入 `sql\query`</span><span class="sxs-lookup"><span data-stu-id="0ee67-110">To connect to the default pipe, enter `sql\query`</span></span>  
  
 <span data-ttu-id="0ee67-111">**已启用**</span><span class="sxs-lookup"><span data-stu-id="0ee67-111">**Enabled**</span></span>  
 <span data-ttu-id="0ee67-112">可能的值为“是”  和“否”  。</span><span class="sxs-lookup"><span data-stu-id="0ee67-112">Possible values are **Yes** and **No**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee67-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ee67-113">See Also</span></span>  
 [<span data-ttu-id="0ee67-114">选择网络协议</span><span class="sxs-lookup"><span data-stu-id="0ee67-114">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
