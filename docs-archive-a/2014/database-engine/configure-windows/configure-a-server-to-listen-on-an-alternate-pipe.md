---
title: 配置服务器以侦听备用管道 (SQL Server 配置管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 57d70cf4cd1d7474b895aeb8cb144c885e8a0f99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577840"
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe-sql-server-configuration-manager"></a><span data-ttu-id="c2f0c-102">配置服务器以侦听备用管道（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="c2f0c-102">Configure a Server to Listen on an Alternate Pipe (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="c2f0c-103">本主题说明如何使用 SQL Server 配置管理器在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中将服务器配置为侦听备用管道。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-103">This topic describes how to configure a server to listen on an alternate pipe in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="c2f0c-104">默认情况下， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的默认实例侦听命名管道 \\\\.\pipe\sql\query。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-104">By default, the default instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] listens on named pipe \\\\.\pipe\sql\query.</span></span> <span data-ttu-id="c2f0c-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 和 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 的命名实例侦听其他管道。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-105">Named instances of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssEW](../../includes/ssew-md.md)] listen on other pipes.</span></span>  
  
 <span data-ttu-id="c2f0c-106">使用客户端应用程序连接到特定的命名管道的方式有三种：</span><span class="sxs-lookup"><span data-stu-id="c2f0c-106">There are three ways to connect to a specific named pipe with a client application:</span></span>  
  
-   <span data-ttu-id="c2f0c-107">在服务器上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-107">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server.</span></span>  
  
-   <span data-ttu-id="c2f0c-108">在客户端上创建别名，指定命名管道。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-108">Create an alias on the client, specifying the named pipe.</span></span>  
  
-   <span data-ttu-id="c2f0c-109">对客户端进行编程，以便使用自定义连接字符串进行连接。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-109">Program the client to connect using a custom connection string.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c2f0c-110">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="c2f0c-110">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a><span data-ttu-id="c2f0c-111">配置 SQL Server 数据库引擎使用的命名管道</span><span class="sxs-lookup"><span data-stu-id="c2f0c-111">To configure the named pipe used by the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="c2f0c-112">在 SQL Server 配置管理器的控制台窗格中，展开“SQL Server 网络配置”，然后单击以展开“\<instance name> 的协议” 。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-112">In SQL Server Configuration Manager, in the console pane, expand **SQL Server Network Configuration**, and then click expand **Protocols for** *\<instance name>*.</span></span>  
  
2.  <span data-ttu-id="c2f0c-113">在详细信息窗格中，右键单击“命名管道”，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-113">In the details pane, right-click **Named Pipes**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="c2f0c-114">在 **“协议”** 选项卡的 **“管道名称”** 框中，键入希望 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 侦听的管道，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-114">On the **Protocol** tab, in the **Pipe Name** box, type the pipe you want the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="c2f0c-115">在控制台窗格中，单击“SQL Server 服务”。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-115">In the console pane, click **SQL Server Services**.</span></span>  
  
5.  <span data-ttu-id="c2f0c-116">在详细信息窗格中，右键单击“SQL Server(\<instance name>)”，然后单击“重新启动”以停止并重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-116">In the details pane, right-click **SQL Server (**\<instance name>**)** and then click **Restart**, to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c2f0c-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听备用管道时，使用客户端应用程序连接到特定的命名管道的方式有三种：</span><span class="sxs-lookup"><span data-stu-id="c2f0c-117">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening on an alternate pipe, there are three ways to connect to a specific named pipe with a client application:</span></span>  
  
-   <span data-ttu-id="c2f0c-118">在服务器上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-118">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server.</span></span>  
  
-   <span data-ttu-id="c2f0c-119">在客户端上创建别名，指定命名管道。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-119">Create an alias on the client, specifying the named pipe.</span></span>  
  
-   <span data-ttu-id="c2f0c-120">对客户端进行编程，以便使用自定义连接字符串进行连接。</span><span class="sxs-lookup"><span data-stu-id="c2f0c-120">Program the client to connect using a custom connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f0c-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2f0c-121">See Also</span></span>  
 <span data-ttu-id="c2f0c-122">[创建或删除供客户端使用的服务器别名（SQL Server 配置管理器）](create-or-delete-a-server-alias-for-use-by-a-client.md) </span><span class="sxs-lookup"><span data-stu-id="c2f0c-122">[Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md) </span></span>  
 [<span data-ttu-id="c2f0c-123">服务器网络配置</span><span class="sxs-lookup"><span data-stu-id="c2f0c-123">Server Network Configuration</span></span>](server-network-configuration.md)  
  
  
