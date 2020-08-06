---
title: 隐藏 SQL Server 数据库引擎的实例 | Microsoft Docs
ms.custom: ''
ms.date: 08/19/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], hiding instances
- hiding instances of Database Engine
ms.assetid: 392de21a-57fa-4a69-8237-ced8ca86ed1d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2b3287c5d4d747ccb3511461341d5aed8ff765d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688228"
---
# <a name="hide-an-instance-of-sql-server-database-engine"></a><span data-ttu-id="c6738-102">隐藏 SQL Server 数据库引擎的实例</span><span class="sxs-lookup"><span data-stu-id="c6738-102">Hide an Instance of SQL Server Database Engine</span></span>
  <span data-ttu-id="c6738-103">本主题说明如何使用 SQL Server 配置管理器在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中隐藏 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c6738-103">This topic describes how to hide an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c6738-104">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器服务来枚举安装在计算机上的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c6738-104">uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service to enumerate instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] installed on the computer.</span></span> <span data-ttu-id="c6738-105">这使客户端应用程序可以浏览服务器，并帮助客户端区别同一台计算机上的多个 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c6738-105">This enables client applications to browse for a server, and helps clients distinguish between multiple instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="c6738-106">您可以使用以下过程防止 SQL Server Browser 服务向尝试通过使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] “浏览” **按钮来查找实例的客户端计算机公开** 实例。</span><span class="sxs-lookup"><span data-stu-id="c6738-106">You can use the following procedure to prevent the SQL Server Browser service from exposing an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to client computers that try to locate the instance by using the **Browse** button.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c6738-107">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="c6738-107">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-hide-an-instance-of-the-sql-server-database-engine"></a><span data-ttu-id="c6738-108">隐藏 SQL Server 数据库引擎实例</span><span class="sxs-lookup"><span data-stu-id="c6738-108">To hide an instance of the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="c6738-109">在“SQL Server 配置管理器”中，展开“SQL Server 网络配置”，右键单击“\<server instance> 的协议”，然后选择“属性”。  </span><span class="sxs-lookup"><span data-stu-id="c6738-109">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, right-click **Protocols for** *\<server instance>*, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c6738-110">在 **“标志”** 选项卡的 **“隐藏实例”** 框中，选择 **“是”** ，然后单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="c6738-110">On the **Flags** tab, in the **HideInstance** box, select **Yes**, and then click **OK** to close the dialog box.</span></span> <span data-ttu-id="c6738-111">对于新连接，更改会立即生效。</span><span class="sxs-lookup"><span data-stu-id="c6738-111">The change takes effect immediately for new connections.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6738-112">备注</span><span class="sxs-lookup"><span data-stu-id="c6738-112">Remarks</span></span>  
 <span data-ttu-id="c6738-113">如果你隐藏命名实例，你将需要在连接字符串中提供端口号才能连接到隐藏的实例，即使浏览器服务正在运行也是如此。</span><span class="sxs-lookup"><span data-stu-id="c6738-113">If you hide a named instance, you will need to provide the port number in the connection string to connect to the hidden instance, even if the browser service is running.</span></span> <span data-ttu-id="c6738-114">对于命名隐藏实例，我们建议你使用静态端口而不是动态端口。</span><span class="sxs-lookup"><span data-stu-id="c6738-114">We recommend that you use a static port instead of a dynamic port for the named hidden instance.</span></span>  
  <span data-ttu-id="c6738-115">有关详细信息，请参阅[将服务器配置为侦听特定 TCP 端口（SQL Sever 配置管理器）](configure-a-server-to-listen-on-a-specific-tcp-port.md)。</span><span class="sxs-lookup"><span data-stu-id="c6738-115">For more information, see [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).</span></span>  
  
### <a name="clustering"></a><span data-ttu-id="c6738-116">群集</span><span class="sxs-lookup"><span data-stu-id="c6738-116">Clustering</span></span>  
 <span data-ttu-id="c6738-117">如果你隐藏群集命名实例，则群集服务可能无法连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c6738-117">If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c6738-118">这将导致群集实例的**IsAlive**检查失败，并 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将脱机。</span><span class="sxs-lookup"><span data-stu-id="c6738-118">This will cause the cluster instance's **IsAlive** check to fail and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will go offline.</span></span> <span data-ttu-id="c6738-119">我们建议在群集实例的所有节点中创建别名，以反映你为该实例配置的静态端口。</span><span class="sxs-lookup"><span data-stu-id="c6738-119">We recommend that you create an alias in all the nodes of the clustered instance to reflect the static port that you configured for the instance.</span></span>  
 <span data-ttu-id="c6738-120">有关详细信息，请参阅[创建或删除供客户端使用的服务器别名（SQL Server 配置管理器）](create-or-delete-a-server-alias-for-use-by-a-client.md)。</span><span class="sxs-lookup"><span data-stu-id="c6738-120">For more information, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
 <span data-ttu-id="c6738-121">如果隐藏群集命名实例，当 **LastConnect** 注册表项 (**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI11.0\LastConnect**) 具有的端口与[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在侦听的端口不同时，群集服务可能无法连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c6738-121">If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if the **LastConnect** registry key (**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI11.0\LastConnect**) has a different port than the port that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening on.</span></span> <span data-ttu-id="c6738-122">如果群集服务无法建立与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的连接，则你可能会看到类似于以下内容的错误：</span><span class="sxs-lookup"><span data-stu-id="c6738-122">If the cluster service is unable to make a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you might see an error similar to the following:</span></span>  
<span data-ttu-id="c6738-123">**事件 ID：1001：事件名称：故障转移群集资源死锁。**</span><span class="sxs-lookup"><span data-stu-id="c6738-123">**Event ID: 1001: Event Name: Failover clustering resource deadlock.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6738-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6738-124">See Also</span></span>  
 <span data-ttu-id="c6738-125">[服务器网络配置](server-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="c6738-125">[Server Network Configuration](server-network-configuration.md) </span></span>  
 <span data-ttu-id="c6738-126">[SQL 虚拟服务器客户端连接的说明](https://support.microsoft.com/kb/273673) </span><span class="sxs-lookup"><span data-stu-id="c6738-126">[Description of SQL Virtual Server client connections](https://support.microsoft.com/kb/273673) </span></span>  
 [<span data-ttu-id="c6738-127">如何将静态端口分配到 SQL Server 命名实例并避免常见缺陷</span><span class="sxs-lookup"><span data-stu-id="c6738-127">How to assign a static port to a SQL Server named instance - and avoid a common pitfall</span></span>](https://blogs.msdn.com/b/arvindsh/archive/2012/09/08/how-to-assign-a-static-port-to-a-sql-server-named-instance-and-avoid-a-common-pitfall.aspx)  
  
  
