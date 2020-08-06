---
title: 重命名托管 SQL Server 独立实例的计算机 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- remote login errors [SQL Server]
- standalone computer names [SQL Server]
- names [SQL Server], standalone instances of SQL Server
- renaming standalone instances of SQL Server
- sysservers system table
- removing remote logins
- deleting remote logins
- dropping remote logins
ms.assetid: bbaf1445-b8a2-4ebf-babe-17d8cf20b037
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 079348921900a7cbf880027433280253df1a9e30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693041"
---
# <a name="rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server"></a><span data-ttu-id="c4115-102">重命名承载 SQL Server 独立实例的计算机</span><span class="sxs-lookup"><span data-stu-id="c4115-102">Rename a Computer that Hosts a Stand-Alone Instance of SQL Server</span></span>
  <span data-ttu-id="c4115-103">如果更改了运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的计算机的名称，则会在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动期间识别新名称。</span><span class="sxs-lookup"><span data-stu-id="c4115-103">When you change the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the new name is recognized during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span> <span data-ttu-id="c4115-104">不必再次运行安装程序以重置计算机名称。</span><span class="sxs-lookup"><span data-stu-id="c4115-104">You do not have to run Setup again to reset the computer name.</span></span> <span data-ttu-id="c4115-105">只需使用以下步骤对存储在 sys.servers 中并由系统函数 @@SERVERNAME 报告的系统元数据进行更新。</span><span class="sxs-lookup"><span data-stu-id="c4115-105">Instead, use the following steps to update system metadata that is stored in sys.servers and reported by the system function @@SERVERNAME.</span></span> <span data-ttu-id="c4115-106">更新系统元数据，以反映出使用 @@SERVERNAME 或从 sys.servers 中查询服务器名称的远程连接或应用程序的计算机名称的变化。</span><span class="sxs-lookup"><span data-stu-id="c4115-106">Update system metadata to reflect computer name changes for remote connections and applications that use @@SERVERNAME, or that query the server name from sys.servers.</span></span>  
  
 <span data-ttu-id="c4115-107">不能通过以下步骤重命名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="c4115-107">The following steps cannot be used to rename an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c4115-108">这些步骤只能用于重命名实例名中与计算机名称对应的部分。</span><span class="sxs-lookup"><span data-stu-id="c4115-108">They can be used only to rename the part of the instance name that corresponds to the computer name.</span></span> <span data-ttu-id="c4115-109">例如，可以将承载名为 Instance1 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的计算机称（名为 MB1）更改为其他名称，例如 MB2。</span><span class="sxs-lookup"><span data-stu-id="c4115-109">For example, you can change a computer named MB1 that hosts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named Instance1 to another name, such as MB2.</span></span> <span data-ttu-id="c4115-110">但是，名称中的实例部分 Instance1 将保持不变。</span><span class="sxs-lookup"><span data-stu-id="c4115-110">However, the instance part of the name, Instance1, will remain unchanged.</span></span> <span data-ttu-id="c4115-111">在此示例中， \\\\*ComputerName*\\*InstanceName* 将从 \\\MB1\Instance1 更改为 \\\MB2\Instance1。</span><span class="sxs-lookup"><span data-stu-id="c4115-111">In this example, the \\\\*ComputerName*\\*InstanceName* would be changed from \\\MB1\Instance1 to \\\MB2\Instance1.</span></span>  
  
 <span data-ttu-id="c4115-112">**开始之前**</span><span class="sxs-lookup"><span data-stu-id="c4115-112">**Before you begin**</span></span>  
  
 <span data-ttu-id="c4115-113">开始重命名过程之前，请查看下列信息：</span><span class="sxs-lookup"><span data-stu-id="c4115-113">Before you begin the renaming process, review the following information:</span></span>  
  
-   <span data-ttu-id="c4115-114">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集的一部分，则计算机的重命名过程不同于承载独立实例的计算机的重命名过程。</span><span class="sxs-lookup"><span data-stu-id="c4115-114">When an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, the computer renaming process differs from a computer that hosts a stand-alone instance.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c4115-115">不支持对复制所涉及的计算机进行重命名。</span><span class="sxs-lookup"><span data-stu-id="c4115-115">does not support renaming computers that are involved in replication, except when you use log shipping with replication.</span></span> <span data-ttu-id="c4115-116">如果主计算机永久丢失，则可以重命名日志传送中的辅助计算机。</span><span class="sxs-lookup"><span data-stu-id="c4115-116">The secondary computer in log shipping can be renamed if the primary computer is permanently lost.</span></span> <span data-ttu-id="c4115-117">有关详细信息，请参阅[日志传送和复制 (SQL Server)](../log-shipping/log-shipping-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c4115-117">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="c4115-118">如果重命名配置为使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的计算机，则 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]在计算机名称更改后可能不可用。</span><span class="sxs-lookup"><span data-stu-id="c4115-118">When you rename a computer that is configured to use [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] might not be available after the computer name change.</span></span> <span data-ttu-id="c4115-119">有关详细信息，请参阅 [重命名报表服务器计算机](../../reporting-services/report-server/rename-a-report-server-computer.md)。</span><span class="sxs-lookup"><span data-stu-id="c4115-119">For more information, see [Rename a Report Server Computer](../../reporting-services/report-server/rename-a-report-server-computer.md).</span></span>  
  
-   <span data-ttu-id="c4115-120">重命名配置为使用数据库镜像的计算机时，必须先关闭数据库镜像，然后才能执行重命名操作。</span><span class="sxs-lookup"><span data-stu-id="c4115-120">When you rename a computer that is configured to use database mirroring, you must turn off database mirroring before the renaming operation.</span></span> <span data-ttu-id="c4115-121">然后，使用新的计算机名称重新建立数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="c4115-121">Then, re-establish database mirroring with the new computer name.</span></span> <span data-ttu-id="c4115-122">数据库镜像的元数据将不会自动更新来反映新计算机名称。</span><span class="sxs-lookup"><span data-stu-id="c4115-122">Metadata for database mirroring will not be updated automatically to reflect the new computer name.</span></span> <span data-ttu-id="c4115-123">使用以下步骤更新系统元数据。</span><span class="sxs-lookup"><span data-stu-id="c4115-123">Use the following steps to update system metadata.</span></span>  
  
-   <span data-ttu-id="c4115-124">如果用户通过以硬编码方式引用计算机名称的 Windows 组连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，则用户可能无法再连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4115-124">Users who connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through a Windows group that uses a hard-coded reference to the computer name might not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c4115-125">重命名之后，如果 Windows 组指定的是旧计算机名称，则可能会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="c4115-125">This can occur after the rename if the Windows group specifies the old computer name.</span></span> <span data-ttu-id="c4115-126">若要确保这样的 Windows 组在重命名操作之后可以连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请更新 Windows 组以指定新计算机名称。</span><span class="sxs-lookup"><span data-stu-id="c4115-126">To ensure that such Windows groups have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connectivity following the renaming operation, update the Windows group to specify the new computer name.</span></span>  
  
 <span data-ttu-id="c4115-127">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 后，可使用新计算机名称连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4115-127">You can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the new computer name after you have restarted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c4115-128">为确保 @@SERVERNAME 返回本地服务器实例更新后的名称，应根据自己的方案手动运行以下过程。</span><span class="sxs-lookup"><span data-stu-id="c4115-128">To ensure that @@SERVERNAME returns the updated name of the local server instance, you should manually run the following procedure that applies to your scenario.</span></span> <span data-ttu-id="c4115-129">采用的过程取决于所更新的计算机承载的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的默认实例还是命名实例。</span><span class="sxs-lookup"><span data-stu-id="c4115-129">The procedure you use depends on whether you are updating a computer that hosts a default or named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-rename-a-computer-that-hosts-a-stand-alone-instance-of-ssnoversion"></a><span data-ttu-id="c4115-130">重命名托管独立实例的计算机 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4115-130">To rename a computer that hosts a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="c4115-131">对于承载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]默认实例的重命名计算机，请运行以下过程：</span><span class="sxs-lookup"><span data-stu-id="c4115-131">For a renamed computer that hosts a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run the following procedures:</span></span>  
  
    ```  
    sp_dropserver <old_name>;  
    GO  
    sp_addserver <new_name>, local;  
    GO  
    ```  
  
     <span data-ttu-id="c4115-132">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="c4115-132">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c4115-133">对于承载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]命名实例的重命名计算机，请运行以下过程：</span><span class="sxs-lookup"><span data-stu-id="c4115-133">For a renamed computer that hosts a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run the following procedures:</span></span>  
  
    ```  
    sp_dropserver <old_name\instancename>;  
    GO  
    sp_addserver <new_name\instancename>, local;  
    GO  
    ```  
  
     <span data-ttu-id="c4115-134">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="c4115-134">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="after-the-renaming-operation"></a><span data-ttu-id="c4115-135">重命名操作之后</span><span class="sxs-lookup"><span data-stu-id="c4115-135">After the Renaming Operation</span></span>  
 <span data-ttu-id="c4115-136">重命名计算机后，所有使用旧计算机名称的连接都必须通过使用新名称进行连接。</span><span class="sxs-lookup"><span data-stu-id="c4115-136">After a computer has been renamed, any connections that used the old computer name must connect by using the new name.</span></span>  
  
#### <a name="to-verify-that-the-renaming-operation-has-completed-successfully"></a><span data-ttu-id="c4115-137">验证是否已成功完成重命名操作</span><span class="sxs-lookup"><span data-stu-id="c4115-137">To verify that the renaming operation has completed successfully</span></span>  
  
-   <span data-ttu-id="c4115-138">通过 @@SERVERNAME 或 sys.servers 选择信息。</span><span class="sxs-lookup"><span data-stu-id="c4115-138">Select information from either @@SERVERNAME or sys.servers.</span></span> <span data-ttu-id="c4115-139">@@SERVERNAME 函数将返回新名称，sys.servers 表将显示该新名称。</span><span class="sxs-lookup"><span data-stu-id="c4115-139">The @@SERVERNAME function will return the new name, and the sys.servers table will show the new name.</span></span> <span data-ttu-id="c4115-140">以下示例演示了如何使用 @@SERVERNAME。</span><span class="sxs-lookup"><span data-stu-id="c4115-140">The following example shows the use of @@SERVERNAME.</span></span>  
  
    ```  
    SELECT @@SERVERNAME AS 'Server Name';  
    ```  
  
## <a name="additional-considerations"></a><span data-ttu-id="c4115-141">其他注意事项</span><span class="sxs-lookup"><span data-stu-id="c4115-141">Additional Considerations</span></span>  
 <span data-ttu-id="c4115-142">**远程登录名** - 如果计算机具有任何远程登录名，运行 **sp_dropserver** 可能会产生类似如下的错误：</span><span class="sxs-lookup"><span data-stu-id="c4115-142">**Remote Logins** - If the computer has any remote logins, running **sp_dropserver** might generate an error similar to the following:</span></span>  
  
 `Server: Msg 15190, Level 16, State 1, Procedure sp_dropserver, Line 44 There are still remote logins for the server 'SERVER1'.`  
  
 <span data-ttu-id="c4115-143">若要解决此错误，必须删除此服务器的远程登录。</span><span class="sxs-lookup"><span data-stu-id="c4115-143">To resolve the error, you must drop remote logins for this server.</span></span>  
  
#### <a name="to-drop-remote-logins"></a><span data-ttu-id="c4115-144">删除远程登录</span><span class="sxs-lookup"><span data-stu-id="c4115-144">To drop remote logins</span></span>  
  
-   <span data-ttu-id="c4115-145">对于默认实例，请运行以下过程：</span><span class="sxs-lookup"><span data-stu-id="c4115-145">For a default instance, run the following procedure:</span></span>  
  
    ```  
    sp_dropremotelogin old_name;  
    GO  
    ```  
  
-   <span data-ttu-id="c4115-146">对于命名实例，请运行以下过程：</span><span class="sxs-lookup"><span data-stu-id="c4115-146">For a named instance, run the following procedure:</span></span>  
  
    ```  
    sp_dropremotelogin old_name\instancename;  
    GO  
    ```  
  
 <span data-ttu-id="c4115-147">**链接服务器配置** - 链接服务器配置将受到计算机重命名操作的影响。</span><span class="sxs-lookup"><span data-stu-id="c4115-147">**Linked Server Configurations** - Linked server configurations will be affected by the computer renaming operation.</span></span> <span data-ttu-id="c4115-148">使用 `sp_addlinkedserver` 或 `sp_setnetname` 可更新计算机名称引用。</span><span class="sxs-lookup"><span data-stu-id="c4115-148">Use `sp_addlinkedserver` or `sp_setnetname` to update computer name references.</span></span> <span data-ttu-id="c4115-149">有关详细信息，请参阅 [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) 或 [sp_setnetname (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-setnetname-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c4115-149">For more information, see the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) or [sp_setnetname &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setnetname-transact-sql).</span></span>  
  
 <span data-ttu-id="c4115-150">**客户端别名** - 采用命名管道的客户端别名将受到计算机重命名操作的影响。</span><span class="sxs-lookup"><span data-stu-id="c4115-150">**Client Alias Names** - Client aliases that use named pipes will be affected by the computer renaming operation.</span></span> <span data-ttu-id="c4115-151">例如，如果创建了指向 SRVR1 的别名“PROD_SRVR”，而且该别名采用 Named Pipes 协议，则相应的管道名称将类似于 `\\SRVR1\pipe\sql\query`。</span><span class="sxs-lookup"><span data-stu-id="c4115-151">For example, if an alias "PROD_SRVR" was created to point to SRVR1 and uses the named pipes protocol, the pipe name will look like `\\SRVR1\pipe\sql\query`.</span></span> <span data-ttu-id="c4115-152">计算机重命名后，named pipe 的路径将不再有效。</span><span class="sxs-lookup"><span data-stu-id="c4115-152">After the computer is renamed, the path of the named pipe will no longer be valid and.</span></span> <span data-ttu-id="c4115-153">有关 Named Pipes 的详细信息，请参阅 [使用 Named Pipes 创建有效的连接字符串](https://go.microsoft.com/fwlink/?LinkId=111063)。</span><span class="sxs-lookup"><span data-stu-id="c4115-153">For more information about named pipes, see the [Creating a Valid Connection String Using Named Pipes](https://go.microsoft.com/fwlink/?LinkId=111063).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4115-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4115-154">See Also</span></span>  
 [<span data-ttu-id="c4115-155">安装 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="c4115-155">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
  
  
