---
title: 配置“网络数据包大小”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default packet size
- size [SQL Server], packets
- packets [SQL Server], size
- network packet size option
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69e5963675349bceff6a0ee022f6dc28da03db59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689581"
---
# <a name="configure-the-network-packet-size-server-configuration-option"></a><span data-ttu-id="a3409-102">配置 network packet size 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="a3409-102">Configure the network packet size Server Configuration Option</span></span>
  <span data-ttu-id="a3409-103">本主题说明如何 `network packet size` 使用或在中配置服务器配置选项 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a3409-103">This topic describes how to configure the `network packet size` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a3409-104">`network packet size`选项设置在整个网络中使用的数据包大小（以字节为单位） () 。</span><span class="sxs-lookup"><span data-stu-id="a3409-104">The `network packet size` option sets the packet size (in bytes) that is used across the whole network.</span></span> <span data-ttu-id="a3409-105">数据包是具有固定大小的数据块区，用于在客户端与服务器之间传输请求和结果。</span><span class="sxs-lookup"><span data-stu-id="a3409-105">Packets are the fixed-size chunks of data that transfer requests and results between clients and servers.</span></span> <span data-ttu-id="a3409-106">默认数据包大小为 4,096 个字节。</span><span class="sxs-lookup"><span data-stu-id="a3409-106">The default packet size is 4,096 bytes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3409-107">除非您确信能够提高性能，否则不要更改数据包的大小。</span><span class="sxs-lookup"><span data-stu-id="a3409-107">Do not change the packet size unless you are certain that it will improve performance.</span></span> <span data-ttu-id="a3409-108">对于大多数应用程序而言，默认数据包大小为最佳数值。</span><span class="sxs-lookup"><span data-stu-id="a3409-108">For most applications, the default packet size is best.</span></span>  
  
 <span data-ttu-id="a3409-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a3409-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a3409-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a3409-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a3409-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a3409-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a3409-112">建议</span><span class="sxs-lookup"><span data-stu-id="a3409-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a3409-113">安全性</span><span class="sxs-lookup"><span data-stu-id="a3409-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a3409-114">**配置 network packet size 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="a3409-114">**To configure the network packet size option, using:**</span></span>  
  
     [<span data-ttu-id="a3409-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a3409-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a3409-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a3409-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a3409-117">**跟进：** [在配置网络数据包大小选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a3409-117">**Follow Up:**  [After you configure the network packet size option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a3409-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="a3409-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a3409-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a3409-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a3409-120">对于加密连接，network packet size 的最大值为 16,383 字节。</span><span class="sxs-lookup"><span data-stu-id="a3409-120">The maximum network packet size for encrypted connections is 16,383 bytes.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a3409-121">建议</span><span class="sxs-lookup"><span data-stu-id="a3409-121">Recommendations</span></span>  
  
-   <span data-ttu-id="a3409-122">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="a3409-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="a3409-123">如果应用程序进行大容量复制操作，或者发送或接收大量文本或图像数据时，数据包大小大于默认值可以提高效率，因为这样可以减少网络读写操作。</span><span class="sxs-lookup"><span data-stu-id="a3409-123">If an application does bulk copy operations or sends or receives large amounts of text or image data, a packet size larger than the default might improve efficiency because it results in fewer network read-and-write operations.</span></span> <span data-ttu-id="a3409-124">如果应用程序发送和接收的信息量较少，则可以将数据包大小设置为 512 字节，这对大多数数据传输足够了。</span><span class="sxs-lookup"><span data-stu-id="a3409-124">If an application sends and receives small amounts of information, the packet size can be set to 512 bytes, which is sufficient for most data transfers.</span></span>  
  
-   <span data-ttu-id="a3409-125">在使用不同网络协议的系统上，将网络数据包大小设置为最常用协议使用的大小。</span><span class="sxs-lookup"><span data-stu-id="a3409-125">On systems that are using different network protocols, set network packet size to the size for the most common protocol used.</span></span> <span data-ttu-id="a3409-126">如果网络协议支持更大的数据包，则使用 network packet size 选项可以提高网络性能。</span><span class="sxs-lookup"><span data-stu-id="a3409-126">The network packet size option improves network performance when network protocols support larger packets.</span></span> <span data-ttu-id="a3409-127">客户端应用程序可以覆盖此值。</span><span class="sxs-lookup"><span data-stu-id="a3409-127">Client applications can override this value.</span></span>  
  
-   <span data-ttu-id="a3409-128">您还可以调用 OLE DB、开放式数据库连接 (ODBC) 和 DB-Library 函数来请求更改数据包大小。</span><span class="sxs-lookup"><span data-stu-id="a3409-128">You can also call OLE DB, Open Database Connectivity (ODBC), and DB-Library functions request a change the packet size.</span></span> <span data-ttu-id="a3409-129">如果服务器无法支持所请求的数据包大小， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将向客户端发送警告消息。</span><span class="sxs-lookup"><span data-stu-id="a3409-129">If the server cannot support the requested packet size, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will send a warning message to the client.</span></span> <span data-ttu-id="a3409-130">在某些环境下，更改数据包大小可能导致通信链接故障，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3409-130">In some circumstances, changing the packet size might lead to a communication link failure, such as the following:</span></span>  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a3409-131">Security</span><span class="sxs-lookup"><span data-stu-id="a3409-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a3409-132">权限</span><span class="sxs-lookup"><span data-stu-id="a3409-132">Permissions</span></span>  
 <span data-ttu-id="a3409-133">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="a3409-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="a3409-134">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="a3409-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="a3409-135">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="a3409-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a3409-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a3409-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-network-packet-size-option"></a><span data-ttu-id="a3409-137">配置 network packet size 选项</span><span class="sxs-lookup"><span data-stu-id="a3409-137">To configure the network packet size option</span></span>  
  
1.  <span data-ttu-id="a3409-138">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="a3409-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a3409-139">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="a3409-139">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="a3409-140">在 **“网络”** 下，选择 **“网络数据包大小”** 框的值。</span><span class="sxs-lookup"><span data-stu-id="a3409-140">Under **Network**, select a value for the **Network Packet Size** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a3409-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a3409-141">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-network-packet-size-option"></a><span data-ttu-id="a3409-142">配置 network packet size 选项</span><span class="sxs-lookup"><span data-stu-id="a3409-142">To configure the network packet size option</span></span>  
  
1.  <span data-ttu-id="a3409-143">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a3409-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a3409-144">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a3409-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a3409-145">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a3409-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a3409-146">此示例说明了如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `network packet size` 选项的值设置为 `6500` 字节。</span><span class="sxs-lookup"><span data-stu-id="a3409-146">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `network packet size` option to `6500` bytes.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="a3409-147">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="a3409-147">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-network-packet-size-option"></a><a name="FollowUp"></a> <span data-ttu-id="a3409-148">跟进：在配置网络数据包大小选项之后</span><span class="sxs-lookup"><span data-stu-id="a3409-148">Follow Up: After you configure the network packet size option</span></span>  
 <span data-ttu-id="a3409-149">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="a3409-149">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3409-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3409-150">See Also</span></span>  
 <span data-ttu-id="a3409-151">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a3409-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="a3409-152">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a3409-152">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="a3409-153">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a3409-153">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
