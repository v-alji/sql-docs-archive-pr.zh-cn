---
title: 配置客户端协议 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default protocols
- network protocols [SQL Server], client configuration
- TCP/IP [SQL Server], client protocols
- disabling client protocols
- ordering protocols [SQL Server]
- protocols [SQL Server], order for client computers
- configure client protocols
- client protocols [SQL Server]
- protocols [SQL Server], client configuration
ms.assetid: 3dfa2702-ba65-43b4-a777-6727846e133a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2eb223815c3e3af50813e02d3ded60573c327155
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591594"
---
# <a name="configure-client-protocols"></a><span data-ttu-id="b0844-102">配置客户端协议</span><span class="sxs-lookup"><span data-stu-id="b0844-102">Configure Client Protocols</span></span>
  <span data-ttu-id="b0844-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 配置管理器在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中配置客户端应用程序使用的客户端协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-103">This topic describes how to configure client protocols used by client applications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="b0844-104">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持使用 TCP/IP 网络协议和 Named Pipes 协议的客户端通信。</span><span class="sxs-lookup"><span data-stu-id="b0844-104">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports client communication with the TCP/IP network protocol and the named pipes protocol.</span></span> <span data-ttu-id="b0844-105">如果客户端正在连接到同一计算机上的[!INCLUDE[ssDE](../../includes/ssde-md.md)]实例，则还可使用 Shared Memory 协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-105">The shared memory protocol is also available if the client is connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="b0844-106">通常有三种选择协议的方法。</span><span class="sxs-lookup"><span data-stu-id="b0844-106">There are three common methods of selecting the protocol.</span></span>  
  
-   <span data-ttu-id="b0844-107">通过在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中设置协议顺序，将所有的客户端应用程序配置为使用相同的网络协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-107">Configure all client applications to use the same network protocol by setting the protocol order in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
-   <span data-ttu-id="b0844-108">通过创建别名，将单个客户端应用程序配置为使用不同的网络协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-108">Configure a single client application to use a different network protocol by creating an alias.</span></span> <span data-ttu-id="b0844-109">有关详细信息，请参阅[创建或删除供客户端使用的服务器别名（SQL Server 配置管理器）](create-or-delete-a-server-alias-for-use-by-a-client.md)。</span><span class="sxs-lookup"><span data-stu-id="b0844-109">For more information, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
-   <span data-ttu-id="b0844-110">有些客户端应用程序（例如 sqlcmd.exe）可以在连接字符串中指定协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-110">Some client applications, such as sqlcmd.exe, can specify the protocol as part of the connection string.</span></span> <span data-ttu-id="b0844-111">有关详细信息，请参阅[使用 sqlcmd 连接到数据库引擎](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="b0844-111">For more information, see [Connect to the Database Engine With sqlcmd](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b0844-112">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="b0844-112">Using SQL Server Configuration Manager</span></span>  
  
###  <a name="to-enable-or-disable-a-client-protocol"></a><a name="EnableDisable"></a><span data-ttu-id="b0844-113">启用或禁用客户端协议</span><span class="sxs-lookup"><span data-stu-id="b0844-113">To enable or disable a client protocol</span></span>  
  
1.  <span data-ttu-id="b0844-114">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，展开“SQL Server Native Client 配置”，右键单击“客户端协议”，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="b0844-114">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b0844-115">单击 **“禁用的协议”** 框中的协议，再单击 **“启用”** 来启用协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-115">Click a protocol in the **Disabled Protocols** box, and then click **Enable**, to enable a protocol.</span></span>  
  
3.  <span data-ttu-id="b0844-116">单击 **“启用的协议”** 框中的协议，再单击 **“禁用”** 来禁用协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-116">Click a protocol in the **Enabled Protocols** box, and then click **Disable**, to disable a protocol.</span></span>  
  
###  <a name="to-change-the-default-protocol-or-the-protocol-order-for-client-computers"></a><a name="ChangeDefault"></a><span data-ttu-id="b0844-117">更改客户端计算机的默认协议或协议顺序</span><span class="sxs-lookup"><span data-stu-id="b0844-117">To change the default protocol or the protocol order for client computers</span></span>  
  
1.  <span data-ttu-id="b0844-118">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，展开“SQL Server Native Client 配置”，右键单击“客户端协议”，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="b0844-118">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b0844-119">在 **“启用的协议”** 框中，单击 **“上移”** 或 **“下移”** 更改尝试连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时尝试使用的协议的顺序。</span><span class="sxs-lookup"><span data-stu-id="b0844-119">In the **Enabled Protocols** box, click **Move Up** or **Move Down**, to change the order in which protocols are tried, when attempting to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b0844-120">**“启用的协议”** 框中最上面的协议是默认协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-120">The top protocol in the **Enabled Protocols** box is the default protocol.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b0844-121">配置管理器可以为服务器别名配置和默认客户端网络库创建注册表项。</span><span class="sxs-lookup"><span data-stu-id="b0844-121">Configuration Manager creates registry entries for the server alias configurations and default client network library.</span></span> <span data-ttu-id="b0844-122">但是，该应用程序并不安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端网络库或网络协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-122">However, the application does not install either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network libraries or the network protocols.</span></span> <span data-ttu-id="b0844-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端网络库是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装期间安装的；网络协议则是在安装 Microsoft Windows 的过程中进行安装的（或者通过“控制面板”中的“网络”安装）。</span><span class="sxs-lookup"><span data-stu-id="b0844-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network libraries are installed during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup; the network protocols are installed as part of Microsoft Windows Setup (or through **Networks** in **Control Panel**).</span></span> <span data-ttu-id="b0844-124">在安装 Windows 的过程中可能不会安装特定的网络协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-124">A particular network protocol may not be available as part of Windows Setup.</span></span> <span data-ttu-id="b0844-125">有关安装这些网络协议的详细信息，请参阅供应商文档。</span><span class="sxs-lookup"><span data-stu-id="b0844-125">For more information about installing these network protocols, see the vendor documentation.</span></span>  
  
###  <a name="to-configure-a-client-to-use-tcpip"></a><a name="Configure"></a><span data-ttu-id="b0844-126">将客户端配置为使用 TCP/IP</span><span class="sxs-lookup"><span data-stu-id="b0844-126">To configure a client to use TCP/IP</span></span>  
  
1.  <span data-ttu-id="b0844-127">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，展开“SQL Server Native Client 配置”，右键单击“客户端协议”，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="b0844-127">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b0844-128">尝试连接到 SQL Server 时，单击 **“启用的协议”** 框中的向上或向下箭头可以更改尝试协议的顺序。</span><span class="sxs-lookup"><span data-stu-id="b0844-128">In the **Enabled Protocols** box, click the up and down arrows to change the order in which protocols are tried, when attempting to connect to SQL Server.</span></span> <span data-ttu-id="b0844-129">**“启用的协议”** 框中最上面的协议是默认协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-129">The top protocol in the **Enabled Protocols** box is the default protocol.</span></span>  
  
 <span data-ttu-id="b0844-130">通过选中 **“启用的共享内存协议”** 复选框，单独启用共享内存协议。</span><span class="sxs-lookup"><span data-stu-id="b0844-130">The shared memory protocol is enabled separately by checking the **Enabled Shared Memory Protocol** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0844-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0844-131">See Also</span></span>  
 [<span data-ttu-id="b0844-132">配置“远程登录超时值”服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="b0844-132">Configure the remote login timeout Server Configuration Option</span></span>](configure-the-remote-login-timeout-server-configuration-option.md)  
  
  
