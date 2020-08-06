---
title: 对 Oracle 发布服务器进行故障排除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], troubleshooting
- troubleshooting [SQL Server replication], Oracle publishing
ms.assetid: be94f1c1-816b-4b1d-83f6-2fd6f5807ab7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4097b2c185b6dde307cd9b295d3b5b32f5797649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580119"
---
# <a name="troubleshooting-oracle-publishers"></a><span data-ttu-id="ca44d-102">对 Oracle 发布服务器进行故障排除</span><span class="sxs-lookup"><span data-stu-id="ca44d-102">Troubleshooting Oracle Publishers</span></span>
  <span data-ttu-id="ca44d-103">本主题列出配置和使用 Oracle 发布服务器时可能会引发的一系列问题。</span><span class="sxs-lookup"><span data-stu-id="ca44d-103">This topic lists a number of issues that might arise when configuring and using an Oracle Publisher.</span></span>  
  
## <a name="an-error-is-raised-regarding-oracle-client-and-networking-software"></a><span data-ttu-id="ca44d-104">引发关于 Oracle 客户端和网络软件的错误</span><span class="sxs-lookup"><span data-stu-id="ca44d-104">An Error Is Raised Regarding Oracle Client and Networking Software</span></span>  
 <span data-ttu-id="ca44d-105">用来在分发服务器上运行 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的帐户必须具有对 Oracle 客户端网络软件安装目录（以及所有子目录）的读取和执行权限。</span><span class="sxs-lookup"><span data-stu-id="ca44d-105">The account under which [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs on the Distributor must be granted read and execute permissions for the directory (and all subdirectories) in which the Oracle client networking software is installed.</span></span> <span data-ttu-id="ca44d-106">如果未授予权限或者未正确安装 Oracle 客户端组件，您将接收到下列错误消息：</span><span class="sxs-lookup"><span data-stu-id="ca44d-106">If the permissions are not granted or the Oracle client components are not installed properly, you will receive the following error message:</span></span>  
  
 <span data-ttu-id="ca44d-107">“用 [Microsoft OLE DB Provider for Oracle] 与服务器连接失败。</span><span class="sxs-lookup"><span data-stu-id="ca44d-107">"Connection to server failed with [Microsoft OLE DB Provider for Oracle].</span></span> <span data-ttu-id="ca44d-108">找不到 Oracle 客户端和网络组件。</span><span class="sxs-lookup"><span data-stu-id="ca44d-108">Oracle client and networking components were not found.</span></span> <span data-ttu-id="ca44d-109">这些组件由 Oracle 公司提供，属于 Oracle 7.3.3 版本或更高版本的客户端软件安装。</span><span class="sxs-lookup"><span data-stu-id="ca44d-109">These components are supplied by Oracle Corporation and are part of the Oracle Version 7.3.3 or later client software installation.</span></span> <span data-ttu-id="ca44d-110">访问接口在安装这些组件前无法运行。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-110">Provider is unable to function until these components are installed."</span></span>  
  
 <span data-ttu-id="ca44d-111">如果已在分发服务器中安装了 Oracle 客户端，则请确保在完成客户端安装后已将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 停止并重新启动。</span><span class="sxs-lookup"><span data-stu-id="ca44d-111">If an appropriate Oracle client has been installed at the Distributor, ensure that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] was stopped and then restarted after the client installation completed.</span></span> <span data-ttu-id="ca44d-112">这样要求是为了 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可以识别客户端组件。</span><span class="sxs-lookup"><span data-stu-id="ca44d-112">This is required in order for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to recognize the client components.</span></span>  
  
 <span data-ttu-id="ca44d-113">如果已验证授予了这些权限并正确安装组件，但依然存在此错误，请验证 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTC\MTxOCI 处的注册表设置是否正确：</span><span class="sxs-lookup"><span data-stu-id="ca44d-113">If you have verified that permissions are granted and that components are installed correctly, but this error persists, verify that the registry settings at HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTC\MTxOCI are correct:</span></span>  
  
-   <span data-ttu-id="ca44d-114">对于 Oracle 10g，正确设置为</span><span class="sxs-lookup"><span data-stu-id="ca44d-114">For Oracle 10g, the correct settings are</span></span>  
  
    -   <span data-ttu-id="ca44d-115">OracleOciLib = oci.dll</span><span class="sxs-lookup"><span data-stu-id="ca44d-115">OracleOciLib = oci.dll</span></span>  
  
    -   <span data-ttu-id="ca44d-116">OracleSqlLib = orasql10.dll</span><span class="sxs-lookup"><span data-stu-id="ca44d-116">OracleSqlLib = orasql10.dll</span></span>  
  
    -   <span data-ttu-id="ca44d-117">OracleXaLib = oraclient10.dll</span><span class="sxs-lookup"><span data-stu-id="ca44d-117">OracleXaLib = oraclient10.dll</span></span>  
  
-   <span data-ttu-id="ca44d-118">对于 Oracle 9i，正确设置为</span><span class="sxs-lookup"><span data-stu-id="ca44d-118">For Oracle 9i, the correct settings are</span></span>  
  
    -   <span data-ttu-id="ca44d-119">OracleOciLib = oci.dll</span><span class="sxs-lookup"><span data-stu-id="ca44d-119">OracleOciLib = oci.dll</span></span>  
  
    -   <span data-ttu-id="ca44d-120">OracleSqlLib = orasql9.dll</span><span class="sxs-lookup"><span data-stu-id="ca44d-120">OracleSqlLib = orasql9.dll</span></span>  
  
    -   <span data-ttu-id="ca44d-121">OracleXaLib = oraclient9.dll</span><span class="sxs-lookup"><span data-stu-id="ca44d-121">OracleXaLib = oraclient9.dll</span></span>  
  
## <a name="the-sql-server-distributor-cannot-connect-to-the-oracle-database-instance"></a><span data-ttu-id="ca44d-122">SQL Server 分发服务器无法连接到 Oracle 数据库实例</span><span class="sxs-lookup"><span data-stu-id="ca44d-122">The SQL Server Distributor Cannot Connect to the Oracle Database Instance</span></span>  
 <span data-ttu-id="ca44d-123">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器无法连接到 Oracle 发布服务器，请确保：</span><span class="sxs-lookup"><span data-stu-id="ca44d-123">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor cannot connect to the Oracle Publisher, ensure that:</span></span>  
  
-   <span data-ttu-id="ca44d-124">分发服务器上已安装必要的 Oracle 软件。</span><span class="sxs-lookup"><span data-stu-id="ca44d-124">The necessary Oracle software is installed on the Distributor.</span></span>  
  
-   <span data-ttu-id="ca44d-125">Oracle 数据库已联机，可用 SQL\*Plus 之类的工具与其连接。</span><span class="sxs-lookup"><span data-stu-id="ca44d-125">The Oracle database is online and you can connect to it using a tool like SQL\*Plus.</span></span>  
  
-   <span data-ttu-id="ca44d-126">复制操作用以连接到 Oracle 发布服务器的登录名具有足够权限。</span><span class="sxs-lookup"><span data-stu-id="ca44d-126">The login replication uses to connect to the Oracle Publisher has sufficient permissions.</span></span> <span data-ttu-id="ca44d-127">有关详细信息，请参阅[配置 Oracle 发布服务器](configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="ca44d-127">For more information, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
-   <span data-ttu-id="ca44d-128">Oracle 发布服务器配置过程中定义的 TNS 名称显示在 tnsnames.ora 文件中。</span><span class="sxs-lookup"><span data-stu-id="ca44d-128">The TNS names defined during configuration of the Oracle Publisher are listed in the tnsnames.ora file.</span></span>  
  
-   <span data-ttu-id="ca44d-129">已使用正确的 Oracle 主目录和路径。</span><span class="sxs-lookup"><span data-stu-id="ca44d-129">The correct Oracle Home and path are used.</span></span> <span data-ttu-id="ca44d-130">即使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器上只安装了一组 Oracle 二进制文件，也要确保正确设置与 Oracle 主目录相关的环境变量。</span><span class="sxs-lookup"><span data-stu-id="ca44d-130">Even if you have only one set of Oracle binaries installed on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor, ensure that the environment variables related to the Oracle Home are set properly.</span></span> <span data-ttu-id="ca44d-131">如果更改了环境变量值，必须停止并重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="ca44d-131">If you change environment variable values, you must stop and restart [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for the change to take effect.</span></span>  
  
 <span data-ttu-id="ca44d-132">有关配置和测试连接的详细信息，请参阅[配置 Oracle 发布服务器](configure-an-oracle-publisher.md)中的“在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器上安装和配置 Oracle 客户端网络软件”。</span><span class="sxs-lookup"><span data-stu-id="ca44d-132">For more information about configuring and testing connectivity, see "Installing and Configuring Oracle Client Networking Software on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor" in [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
## <a name="the-oracle-publisher-is-associated-with-another-distributor"></a><span data-ttu-id="ca44d-133">Oracle 发布服务器与另一分发服务器相关联</span><span class="sxs-lookup"><span data-stu-id="ca44d-133">The Oracle Publisher Is Associated with Another Distributor</span></span>  
 <span data-ttu-id="ca44d-134">一个 Oracle 发布服务器只能与一个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器相关联。</span><span class="sxs-lookup"><span data-stu-id="ca44d-134">An Oracle Publisher can only be associated with one [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span> <span data-ttu-id="ca44d-135">如果有不同的分发服务器与 Oracle 发布服务器相关联，则必须先删除它才能使用另一分发服务器。</span><span class="sxs-lookup"><span data-stu-id="ca44d-135">If a different Distributor is associated with the Oracle Publisher, it must be dropped before another Distributor can be used.</span></span> <span data-ttu-id="ca44d-136">如果未先删除该分发服务器，就会收到以下错误消息之一：</span><span class="sxs-lookup"><span data-stu-id="ca44d-136">If the Distributor is not dropped first, you will receive one of the following error messages:</span></span>  
  
-   <span data-ttu-id="ca44d-137">“Oracle 服务器实例‘\<*OraclePublisherName*>以前已配置为使用‘\<*SQLServerDistributorName*>’作为其分发服务器。</span><span class="sxs-lookup"><span data-stu-id="ca44d-137">"Oracle server instance '\<*OraclePublisherName*>' has been previously configured to use '\<*SQLServerDistributorName*>' as its Distributor.</span></span> <span data-ttu-id="ca44d-138">若要开始使用‘\<*NewSQLServerDistributorName*>作为其分发服务器，必须删除 Oracle 服务器实例上的当前复制配置，而这将删除该服务器实例上的所有发布。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-138">To begin using '\<*NewSQLServerDistributorName*>' as its Distributor, you must remove the current replication configuration on the Oracle server instance, which will delete all publications on that server instance."</span></span>  
  
-   <span data-ttu-id="ca44d-139">“已将 Oracle 服务器‘\<*OracleServerName*>指定为分发服务器‘\<*SQLServerDistributorName*>.\<DistributionDatabaseName>’上的发布服务器‘\<*OraclePublisherName*>’。</span><span class="sxs-lookup"><span data-stu-id="ca44d-139">"Oracle server '\<*OracleServerName*>' is already defined as publisher '\<*OraclePublisherName*>' on distributor '\<*SQLServerDistributorName*>.*\<DistributionDatabaseName>*'.</span></span> <span data-ttu-id="ca44d-140">请删除此发布服务器或删除公共同义词‘\<SynonymName>’，以便重新创建。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-140">Drop the publisher or drop the public synonym '*\<SynonymName>*' to recreate."</span></span>  
  
 <span data-ttu-id="ca44d-141">删除 Oracle 发布服务器时，会自动清除 Oracle 数据库中的复制对象。</span><span class="sxs-lookup"><span data-stu-id="ca44d-141">When an Oracle Publisher is dropped, the replication objects in the Oracle database are automatically cleaned up.</span></span> <span data-ttu-id="ca44d-142">但是，在某些情况下需要手动清除 Oracle 复制对象。</span><span class="sxs-lookup"><span data-stu-id="ca44d-142">However, manual cleanup of the Oracle replication objects is necessary in some cases.</span></span> <span data-ttu-id="ca44d-143">手动清除复制创建的 Oracle 复制对象：</span><span class="sxs-lookup"><span data-stu-id="ca44d-143">To manually clean up Oracle replication objects created by replication:</span></span>  
  
1.  <span data-ttu-id="ca44d-144">用 DBA 权限连接到 Oracle 发布服务器。</span><span class="sxs-lookup"><span data-stu-id="ca44d-144">Connect to the Oracle publisher with DBA permissions.</span></span>  
  
2.  <span data-ttu-id="ca44d-145">发出 SQL 命令 `DROP PUBLIC SYNONYM MSSQLSERVERDISTRIBUTOR;`。</span><span class="sxs-lookup"><span data-stu-id="ca44d-145">Issue the SQL command `DROP PUBLIC SYNONYM MSSQLSERVERDISTRIBUTOR;`.</span></span>  
  
3.  <span data-ttu-id="ca44d-146">发出 SQL 命令 `DROP USER <replication_administrative_user_schema>``CASCADE;`。</span><span class="sxs-lookup"><span data-stu-id="ca44d-146">Issue the SQL command `DROP USER <replication_administrative_user_schema>``CASCADE;`.</span></span>  
  
## <a name="sql-server-error-21663-is-raised-regarding-the-lack-of-a-primary-key"></a><span data-ttu-id="ca44d-147">引发关于缺少主键的 SQL Server 错误 21663</span><span class="sxs-lookup"><span data-stu-id="ca44d-147">SQL Server Error 21663 Is Raised Regarding the Lack of a Primary Key</span></span>  
 <span data-ttu-id="ca44d-148">事务发布中的项目必须具备有效的主键。</span><span class="sxs-lookup"><span data-stu-id="ca44d-148">Articles in transactional publications must have a valid primary key.</span></span> <span data-ttu-id="ca44d-149">如果它们不具备有效的主键，则在尝试添加项目时会收到以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="ca44d-149">If they do not have a valid primary key, you will receive the following error message when you attempt to add an article:</span></span>  
  
 <span data-ttu-id="ca44d-150">“找不到源表 [\<*TableOwner*>].[\<*TableName*>] 的有效主键”</span><span class="sxs-lookup"><span data-stu-id="ca44d-150">"No valid primary key found for source table [\<*TableOwner*>].[\<*TableName*>]"</span></span>  
  
 <span data-ttu-id="ca44d-151">有关主键要求的信息，请参阅主题 [Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md)中的“唯一索引和约束”部分。</span><span class="sxs-lookup"><span data-stu-id="ca44d-151">For information about requirements for primary keys, see the section "Unique Indexes and Constraints" in the topic [Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md).</span></span>  
  
## <a name="sql-server-error-21642-is-raised-regarding-a-duplicate-linked-server-login"></a><span data-ttu-id="ca44d-152">引发关于重复链接服务器登录名的 SQL Server 错误 21642</span><span class="sxs-lookup"><span data-stu-id="ca44d-152">SQL Server Error 21642 Is Raised Regarding a Duplicate Linked Server Login</span></span>  
 <span data-ttu-id="ca44d-153">在初始配置 Oracle 发布服务器时，会为发布服务器和分发服务器之间的连接创建一个链接服务器项。</span><span class="sxs-lookup"><span data-stu-id="ca44d-153">When an Oracle Publisher is initially configured, a linked server entry is created for the connection between the Publisher and the Distributor.</span></span> <span data-ttu-id="ca44d-154">该链接服务器的名称与 Oracle TNS 服务名称相同。</span><span class="sxs-lookup"><span data-stu-id="ca44d-154">The linked server has the same name as the Oracle TNS service name.</span></span> <span data-ttu-id="ca44d-155">如果尝试创建具有相同名称的链接服务器，则会显示以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="ca44d-155">If you attempt to create a linked server with the same name, the following error message is shown:</span></span>  
  
 <span data-ttu-id="ca44d-156">“异类发布服务器需要链接服务器。</span><span class="sxs-lookup"><span data-stu-id="ca44d-156">"Heterogeneous publishers require a linked server.</span></span> <span data-ttu-id="ca44d-157">已有一个名为“\<LinkedServerName>”的链接服务器。</span><span class="sxs-lookup"><span data-stu-id="ca44d-157">A linked server named '*\<LinkedServerName>*' already exists.</span></span> <span data-ttu-id="ca44d-158">请删除链接服务器或另选一个发布服务器名称。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-158">Please remove linked server or choose a different publisher name."</span></span>  
  
 <span data-ttu-id="ca44d-159">如果尝试直接创建链接服务器，或者预先删除了 Oracle 发布服务器和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器之间的关系，而当前在尝试重新配置它，就会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="ca44d-159">This error can occur if you attempt to create the linked server directly or if you have previously dropped the relationship between the Oracle Publisher and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor, and you are now attempting to reconfigure it.</span></span> <span data-ttu-id="ca44d-160">如果尝试重新配置发布服务器时收到此错误，请用 [sp_dropserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql) 删除链接服务器。</span><span class="sxs-lookup"><span data-stu-id="ca44d-160">If you receive this error while attempting to reconfigure the Publisher, drop the linked server with [sp_dropserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql).</span></span>  
  
 <span data-ttu-id="ca44d-161">如果需要通过链接服务器连接来连接到 Oracle 发布服务器，请创建另一个 TNS 服务名称，然后在调用 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) 时使用该名称。</span><span class="sxs-lookup"><span data-stu-id="ca44d-161">If you need to connect to the Oracle Publisher over a linked server connection, create another TNS service name, and then use this name when calling [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span> <span data-ttu-id="ca44d-162">有关创建 TNS 服务名称的信息，请参阅 Oracle 文档。</span><span class="sxs-lookup"><span data-stu-id="ca44d-162">For information about creating TNS service names, see the Oracle documentation.</span></span>  
  
## <a name="sql-server-error-21617-is-raised"></a><span data-ttu-id="ca44d-163">引发 SQL Server 错误 21617</span><span class="sxs-lookup"><span data-stu-id="ca44d-163">SQL Server Error 21617 Is Raised</span></span>  
 <span data-ttu-id="ca44d-164">Oracle 发布操作使用 Oracle 应用程序 SQL\*PLUS 将发布服务器支持代码包下载到 Oracle 数据库。</span><span class="sxs-lookup"><span data-stu-id="ca44d-164">Oracle publishing uses the Oracle application SQL\*PLUS to download the package of Publisher support code to the Oracle database.</span></span> <span data-ttu-id="ca44d-165">在尝试配置 Oracle 发布服务器之前，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将验证是否可以通过分发服务器上的系统路径来访问 SQL\*PLUS。</span><span class="sxs-lookup"><span data-stu-id="ca44d-165">Before attempting to configure the Oracle Publisher, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verifies that SQL\*PLUS is accessible through the system path on the Distributor.</span></span> <span data-ttu-id="ca44d-166">如果不能加载 SQL\*PLUS，将显示以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="ca44d-166">If SQL\*PLUS cannot be loaded, the following error message is shown:</span></span>  
  
 <span data-ttu-id="ca44d-167">“无法运行 SQL\*PLUS。</span><span class="sxs-lookup"><span data-stu-id="ca44d-167">"Unable to run SQL\*PLUS.</span></span> <span data-ttu-id="ca44d-168">请确保分发服务器上安装了最新版本的 Oracle 客户端代码。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-168">Make certain that a current version of the Oracle client code is installed at the distributor."</span></span>  
  
 <span data-ttu-id="ca44d-169">尝试在分发服务器上找到 SQL\*PLUS。</span><span class="sxs-lookup"><span data-stu-id="ca44d-169">Try to locate SQL\*PLUS on the Distributor.</span></span> <span data-ttu-id="ca44d-170">对于 Oracle 10g 客户端安装，此可执行文件的名称为 sqlplus.exe。</span><span class="sxs-lookup"><span data-stu-id="ca44d-170">For an Oracle 10g client install, the name of this executable is sqlplus.exe.</span></span> <span data-ttu-id="ca44d-171">它通常安装在 %ORACLE_HOME%/bin 中。</span><span class="sxs-lookup"><span data-stu-id="ca44d-171">It is typically installed in %ORACLE_HOME%/bin.</span></span> <span data-ttu-id="ca44d-172">若要验证 SQL\*PLUS 的路径是否显示在系统路径中，请检查系统变量 **Path** 的值：</span><span class="sxs-lookup"><span data-stu-id="ca44d-172">To verify that the path of SQL\*PLUS appears in the system path, examine the value of the system variable **Path**:</span></span>  
  
1.  <span data-ttu-id="ca44d-173">右键单击 **“我的电脑”** ，再单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="ca44d-173">Right-click **My Computer**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ca44d-174">单击 **“高级”** 选项卡，再单击 **“环境变量”** 。</span><span class="sxs-lookup"><span data-stu-id="ca44d-174">Click the **Advanced** tab, and then click **Environment variables**.</span></span>  
  
3.  <span data-ttu-id="ca44d-175">在 **“环境变量”** 对话框的 **“系统变量”** 列表中，选择 **Path** 变量，然后单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="ca44d-175">In the **Environment Variables** dialog box, in the **System variables** list, select the **Path** variable, and then click **Edit**.</span></span>  
  
4.  <span data-ttu-id="ca44d-176">在 **“编辑系统变量”** 对话框中：如果 **“变量值”** 文本框中未包含 sqlplus.exe 所在文件夹的路径，请编辑字符串以包含该路径。</span><span class="sxs-lookup"><span data-stu-id="ca44d-176">In the **Edit System Variable** dialog box: if the path to the folder that contains sqlplus.exe is not present in the **Variable value** text box, edit the string to include it.</span></span>  
  
5.  <span data-ttu-id="ca44d-177">在每个打开的对话框中，单击 **“确定”** 退出并保存更改。</span><span class="sxs-lookup"><span data-stu-id="ca44d-177">Click **OK** on each open dialog box to exit and save changes.</span></span>  
  
 <span data-ttu-id="ca44d-178">如果在分发服务器上找不到 sqlplus.exe，请在分发服务器上安装最新版本的 Oracle 客户端软件。</span><span class="sxs-lookup"><span data-stu-id="ca44d-178">If you cannot locate sqlplus.exe on the Distributor, install a current version of the Oracle client software at the Distributor.</span></span> <span data-ttu-id="ca44d-179">有关详细信息，请参阅[配置 Oracle 发布服务器](configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="ca44d-179">For more information, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
## <a name="sql-server-error-21620-is-raised"></a><span data-ttu-id="ca44d-180">引发 SQL Server 错误 21620</span><span class="sxs-lookup"><span data-stu-id="ca44d-180">SQL Server Error 21620 Is Raised</span></span>  
 <span data-ttu-id="ca44d-181">如果连接到的 Oracle 数据库版本低于 8.1 版，则 Oracle 发布操作要求安装在分发服务器上的 Oracle 客户端软件版本为 9 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ca44d-181">If you are connecting to an Oracle database earlier than version 8.1, Oracle publishing requires that the Oracle client software installed on the Distributor be from version 9.</span></span> <span data-ttu-id="ca44d-182">如果连接到的 Oracle 数据库版本是 8.1 版或更高版本，则建议 Oracle 客户端软件版本为 10 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ca44d-182">If you are connecting to an Oracle database that is version 8.1 or later, we recommend that the Oracle client software be version 10 or later.</span></span>  
  
 <span data-ttu-id="ca44d-183">尝试配置 Oracle 发布服务器之前，Oracle 发布操作将验证可通过分发服务器上的系统路径访问的 SQL\*PLUS 的版本是否为 9 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ca44d-183">Before attempting to configure the Oracle Publisher, Oracle publishing verifies that the version of SQL\*PLUS accessible through the system path on the Distributor is version 9 or later.</span></span> <span data-ttu-id="ca44d-184">如果不是，则显示以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="ca44d-184">If it is not, the following error message is shown:</span></span>  
  
 <span data-ttu-id="ca44d-185">“通过系统 Path 变量获得的 SQL\*PLUS 版本不够新，无法支持 Oracle 发布。</span><span class="sxs-lookup"><span data-stu-id="ca44d-185">"The version of SQL\*PLUS that is accessible through the system Path variable is not current enough to support Oracle publishing.</span></span> <span data-ttu-id="ca44d-186">请确保分发服务器上安装了最新版本的 Oracle 客户端代码。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-186">Make certain that a current version of the Oracle client code is installed at the distributor."</span></span>  
  
 <span data-ttu-id="ca44d-187">如果分发服务器上安装了多个版本的 Oracle 客户端软件，请确保最新版本至少为 9 版，且系统的 Path 变量首先引用此版本（Path 系统变量可以引用其他版本，但最新的版本必须出现在最前面）。</span><span class="sxs-lookup"><span data-stu-id="ca44d-187">If you have multiple versions of the Oracle client software installed on the Distributor, make sure that the most current version is at least version 9 and that the system path variable refers first to this version (references to other versions can appear as long as the most recent appears first).</span></span> <span data-ttu-id="ca44d-188">有关编辑系统的 Path 变量的详细信息，请参阅本主题前面的“引发 SQL Server 错误 21617”一节。</span><span class="sxs-lookup"><span data-stu-id="ca44d-188">For more information about editing the system path variable, see the section "SQL Server Error 21617 is Raised" earlier in this topic.</span></span>  
  
## <a name="sql-server-error-21624-or-error-21629-is-raised"></a><span data-ttu-id="ca44d-189">引发 SQL Server 错误 21624 或错误 21629</span><span class="sxs-lookup"><span data-stu-id="ca44d-189">SQL Server Error 21624 or Error 21629 Is Raised</span></span>  
 <span data-ttu-id="ca44d-190">对于 64 位分发服务器，Oracle 发布操作使用用于 Oracle 的 Oracle OLEDB 访问接口 (OraOLEDB.Oracle)。</span><span class="sxs-lookup"><span data-stu-id="ca44d-190">For 64-bit Distributors, Oracle publishing uses the Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle).</span></span> <span data-ttu-id="ca44d-191">确保分发服务器上安装并注册了 Oracle OLEDB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="ca44d-191">Make sure that the Oracle OLEDB provider is installed and registered on the Distributor.</span></span> <span data-ttu-id="ca44d-192">如果未安装并注册该访问接口，则会显示下列某条错误消息或同时显示这两条错误消息：</span><span class="sxs-lookup"><span data-stu-id="ca44d-192">If the provider is not installed and registered, one or both of the following error messages is shown:</span></span>  
  
-   <span data-ttu-id="ca44d-193">“在分发服务器 '%s' 上找不到已注册的 Oracle OLEDB 访问接口 OraOLEDB.Oracle。</span><span class="sxs-lookup"><span data-stu-id="ca44d-193">"Unable to locate the registered Oracle OLEDB provider, OraOLEDB.Oracle, at distributor '%s'.</span></span> <span data-ttu-id="ca44d-194">请确保在分发服务器上安装并注册了最新版本的 Oracle OLEDB 访问接口。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-194">Make certain that a current version of the Oracle OLEDB provider is installed and registered at the distributor."</span></span>  
  
-   <span data-ttu-id="ca44d-195">“指示 Oracle 的 Oracle OLEDB 访问接口 OraOLEDB.Oracle 已注册的 CLSID 注册表项不在分发服务器上。</span><span class="sxs-lookup"><span data-stu-id="ca44d-195">"The CLSID registry key indicating that the Oracle OLEDB Provider for Oracle, OraOLEDB.Oracle, has been registered is not present at the distributor.</span></span> <span data-ttu-id="ca44d-196">请确保在分发服务器上安装并注册了 Oracle OLEDB 访问接口。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-196">Make certain that the Oracle OLEDB provider is installed and registered at the distributor."</span></span>  
  
 <span data-ttu-id="ca44d-197">如果使用的是 Oracle 客户端软件 10g 版，则访问接口为 OraOLEDB10.dll；如果是 9i 版，则访问接口为 OraOLEDB.dll。</span><span class="sxs-lookup"><span data-stu-id="ca44d-197">If you are using Oracle client software version 10g, the provider is OraOLEDB10.dll; for version 9i, it is OraOLEDB.dll.</span></span> <span data-ttu-id="ca44d-198">访问接口将安装在 %ORACLE_HOME%\BIN（例如，C:\oracle\product\10.1.0\Client_1\bin）中。</span><span class="sxs-lookup"><span data-stu-id="ca44d-198">The provider is installed in %ORACLE_HOME%\BIN (for example, C:\oracle\product\10.1.0\Client_1\bin).</span></span> <span data-ttu-id="ca44d-199">如果确定分发服务器上未安装 Oracle OLEDB 访问接口，则从 Oracle 提供的 Oracle 客户端软件安装光盘上安装它。</span><span class="sxs-lookup"><span data-stu-id="ca44d-199">If you determine that the Oracle OLEDB provider is not installed on the Distributor, install it from the Oracle client software install disc provided by Oracle.</span></span> <span data-ttu-id="ca44d-200">有关详细信息，请参阅[配置 Oracle 发布服务器](configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="ca44d-200">For more information, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="ca44d-201">如果已安装 Oracle OLEDB 访问接口，请确保已将其注册。</span><span class="sxs-lookup"><span data-stu-id="ca44d-201">If the Oracle OLEDB provider is installed, make sure that it is registered.</span></span> <span data-ttu-id="ca44d-202">若要注册访问接口 DLL，请从安装 DLL 的目录中执行以下命令，然后停止并重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例：</span><span class="sxs-lookup"><span data-stu-id="ca44d-202">To register the provider DLL, execute the following command from the directory in which the DLL is installed, and then stop and restart the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance:</span></span>  
  
1.  <span data-ttu-id="ca44d-203">`regsvr32 OraOLEDB10.dll` 或 `regsvr32 OraOLEDB.dll`。</span><span class="sxs-lookup"><span data-stu-id="ca44d-203">`regsvr32 OraOLEDB10.dll` or `regsvr32 OraOLEDB.dll`.</span></span>  
  
## <a name="sql-server-error-21626-or-error-21627-is-raised"></a><span data-ttu-id="ca44d-204">引发 SQL Server 错误 21626 或错误 21627</span><span class="sxs-lookup"><span data-stu-id="ca44d-204">SQL Server Error 21626 or Error 21627 Is Raised</span></span>  
 <span data-ttu-id="ca44d-205">为了验证是否正确配置了 Oracle 发布环境， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 会尝试使用在配置过程中指定的登录凭据连接到 Oracle 发布服务器。</span><span class="sxs-lookup"><span data-stu-id="ca44d-205">To verify that the Oracle publishing environment is configured properly, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tries to connect to the Oracle Publisher with the login credentials you specified during configuration.</span></span> <span data-ttu-id="ca44d-206">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器不能连接到 Oracle 发布服务器，则会显示以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="ca44d-206">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor cannot connect to the Oracle Publisher, the following error message is shown:</span></span>  
  
-   <span data-ttu-id="ca44d-207">“无法使用 Oracle OLEDB 访问接口 OraOLEDB.Oracle 连接到 Oracle 数据库服务器 '%s'”。</span><span class="sxs-lookup"><span data-stu-id="ca44d-207">"Unable to connect to Oracle database server '%s' using the Oracle OLEDB provider OraOLEDB.Oracle."</span></span>  
  
 <span data-ttu-id="ca44d-208">如果显示此错误消息，请通过使用在 Oracle 发布服务器的配置过程中指定的登录名和密码直接运行 SQL\*PLUS，验证与 Oracle 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="ca44d-208">If this error message is shown, verify connectivity to the Oracle database by running SQL\*PLUS directly using the same login and password specified during configuration of the Oracle Publisher.</span></span> <span data-ttu-id="ca44d-209">有关详细信息，请参阅本主题前面的“SQL Server 分发服务器无法连接到 Oracle 数据库实例”部分。</span><span class="sxs-lookup"><span data-stu-id="ca44d-209">For more information, see the section "The SQL Server Distributor Cannot Connect to the Oracle Database Instance" earlier in this topic.</span></span>  
  
## <a name="sql-server-error-21628-is-raised"></a><span data-ttu-id="ca44d-210">引发 SQL Server 错误 21628</span><span class="sxs-lookup"><span data-stu-id="ca44d-210">SQL Server Error 21628 Is Raised</span></span>  
 <span data-ttu-id="ca44d-211">对于 64 位分发服务器，Oracle 发布操作使用用于 Oracle 的 Oracle OLEDB 访问接口 (OraOLEDB.Oracle)。</span><span class="sxs-lookup"><span data-stu-id="ca44d-211">For 64-bit Distributors, Oracle publishing uses the Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle).</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="ca44d-212">将创建注册表项，以允许 Oracle 访问接口与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]一起在进程中运行。</span><span class="sxs-lookup"><span data-stu-id="ca44d-212">creates a registry entry to allow the Oracle provider to run in process with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ca44d-213">如果读取或写入此注册表项时出现问题，则显示以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="ca44d-213">If there is a problem reading or writing this registry entry, the following error message is shown:</span></span>  
  
 <span data-ttu-id="ca44d-214">“无法更新分发服务器 '%s'的注册表，以允许 Oracle OLEDB 访问接口 OraOLEDB.Oracle 与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]一起在进程中运行。</span><span class="sxs-lookup"><span data-stu-id="ca44d-214">"Unable to update the registry of distributor '%s' to allow Oracle OLEDB provider OraOLEDB.Oracle to run in process with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ca44d-215">请确保当前登录名有权修改 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 拥有的注册表项。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-215">Make certain that current login is authorized to modify [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] owned registry keys."</span></span>  
  
 <span data-ttu-id="ca44d-216">Oracle 发布操作要求存在该注册表项，并且对于 64 位分发服务器，它必须设置为 **1** 。</span><span class="sxs-lookup"><span data-stu-id="ca44d-216">Oracle publishing requires the registry entry to exist and to be set to **1** for 64 bit Distributors.</span></span> <span data-ttu-id="ca44d-217">如果该注册表项不存在，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将会尝试创建它。</span><span class="sxs-lookup"><span data-stu-id="ca44d-217">If the entry does not exist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will attempt to create it.</span></span> <span data-ttu-id="ca44d-218">如果该注册表项存在，但设置为 **0**，则该设置不会改变；Oracle 发布服务器的配置操作将失败。</span><span class="sxs-lookup"><span data-stu-id="ca44d-218">If the entry exists, but is set to **0**, the setting will not be changed; the configuration of the Oracle Publisher will fail.</span></span>  
  
 <span data-ttu-id="ca44d-219">查看并修改注册表设置：</span><span class="sxs-lookup"><span data-stu-id="ca44d-219">To view and modify the registry setting:</span></span>  
  
1.  <span data-ttu-id="ca44d-220">单击 **“启动”** ，再单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="ca44d-220">Click **Start**, and then click **Run**.</span></span>  
  
2.  <span data-ttu-id="ca44d-221">在 **“运行”** 对话框中，键入 **regedit**，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ca44d-221">In the **Run** dialog box, type **regedit**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ca44d-222">导航到 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\\<InstanceName>\Providers。</span><span class="sxs-lookup"><span data-stu-id="ca44d-222">Navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\*\<InstanceName>* \Providers.</span></span>  
  
     <span data-ttu-id="ca44d-223">Providers 下应该包含一个名为 OraOLEDB.Oracle 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ca44d-223">Included under Providers should be a folder named OraOLEDB.Oracle.</span></span> <span data-ttu-id="ca44d-224">在此文件夹中应该有一个名为 **AllowInProcess**的 DWORD 值，它的值为 **1**。</span><span class="sxs-lookup"><span data-stu-id="ca44d-224">Within this folder should be the DWORD value name **AllowInProcess**, with a value of **1**.</span></span>  
  
4.  <span data-ttu-id="ca44d-225">如果发现 **AllowInProcess** 被设置为 **0**，请将其更新为 **1**：</span><span class="sxs-lookup"><span data-stu-id="ca44d-225">If you determine that **AllowInProcess** is set to **0**, update the registry entry to **1**:</span></span>  
  
    1.  <span data-ttu-id="ca44d-226">右键单击该注册表项，然后单击 **“修改”** 。</span><span class="sxs-lookup"><span data-stu-id="ca44d-226">Right-click the entry, and then click **Modify**.</span></span>  
  
    2.  <span data-ttu-id="ca44d-227">在 **“编辑字符串”** 对话框的 **“数值数据”** 字段中，键入 **1** 。</span><span class="sxs-lookup"><span data-stu-id="ca44d-227">In the **Edit String** dialog box, type **1** in the **Value data** field.</span></span>  
  
## <a name="sql-server-error-21684-is-raised"></a><span data-ttu-id="ca44d-228">引发 SQL Server 错误 21684</span><span class="sxs-lookup"><span data-stu-id="ca44d-228">SQL Server Error 21684 Is Raised</span></span>  
 <span data-ttu-id="ca44d-229">如果管理用户帐户没有足够权限，则会显示以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="ca44d-229">If the administrative user account does not have sufficient privileges, the following error message is shown:</span></span>  
  
 <span data-ttu-id="ca44d-230">“与 Oracle 发布服务器‘%s’管理员登录名关联的权限不足。”</span><span class="sxs-lookup"><span data-stu-id="ca44d-230">"The permissions associated with the administrator login for Oracle publisher '%s' are not sufficient."</span></span>  
  
 <span data-ttu-id="ca44d-231">若要验证授予用户的权限，请执行以下查询： `SELECT * from session_privs`。</span><span class="sxs-lookup"><span data-stu-id="ca44d-231">To verify the permissions granted to the user, execute the following query: `SELECT * from session_privs`.</span></span> <span data-ttu-id="ca44d-232">输出应与以下内容类似：</span><span class="sxs-lookup"><span data-stu-id="ca44d-232">The output should be similar to the following:</span></span>  
  
 `PRIVILEGE`  
  
 `------------------`  
  
 `CREATE SESSION`  
  
 `CREATE TABLE`  
  
 `CREATE PUBLIC SYNONYM`  
  
 `DROP PUBLIC SYNONYM`  
  
 `CREATE VIEW`  
  
 `CREATE SEQUENCE`  
  
 `CREATE PROCEDURE`  
  
 `CREATE TRIGGER`  
  
## <a name="you-encounter-permissions-issues-for-the-replication-user-schema"></a><span data-ttu-id="ca44d-233">遇到复制用户架构的权限问题</span><span class="sxs-lookup"><span data-stu-id="ca44d-233">You Encounter Permissions Issues for the Replication User Schema</span></span>  
 <span data-ttu-id="ca44d-234">复制用户架构必须具有[配置 Oracle 发布服务器](configure-an-oracle-publisher.md)中的“手动创建用户架构”所介绍的权限。</span><span class="sxs-lookup"><span data-stu-id="ca44d-234">The replication user schema must have the permissions described in "Creating the User Schema Manually" in [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
## <a name="oracle-error-ora-01000"></a><span data-ttu-id="ca44d-235">Oracle 错误 ORA-01000</span><span class="sxs-lookup"><span data-stu-id="ca44d-235">Oracle Error ORA-01000</span></span>  
 <span data-ttu-id="ca44d-236">向发布添加项目的过程中，复制在 Oracle 发布服务器上使用游标。</span><span class="sxs-lookup"><span data-stu-id="ca44d-236">Replication uses cursors on the Oracle Publisher during the process of adding articles to a publication.</span></span> <span data-ttu-id="ca44d-237">在此过程中，可能会超过发布服务器上可用的最大游标数。</span><span class="sxs-lookup"><span data-stu-id="ca44d-237">It is possible to exceed the maximum number of cursors available on the Publisher during this process.</span></span> <span data-ttu-id="ca44d-238">如果出现这种情况，会引发以下错误：</span><span class="sxs-lookup"><span data-stu-id="ca44d-238">If this occurs, the following error is raised:</span></span>  
  
 <span data-ttu-id="ca44d-239">“ORA-01000: 超过了最大打开游标数”</span><span class="sxs-lookup"><span data-stu-id="ca44d-239">"ORA-01000: maximum open cursors exceeded"</span></span>  
  
 <span data-ttu-id="ca44d-240">若要避免此问题，请确保将 Oracle 数据库中的 **max_open_cursors** 设置设为足够大的数字（至少为 1000）。</span><span class="sxs-lookup"><span data-stu-id="ca44d-240">To avoid this problem, ensure that the **max_open_cursors** setting in the Oracle databases is set to a sufficiently high number (at least 1000).</span></span> <span data-ttu-id="ca44d-241">有关此设置的详细信息，请参阅 Oracle 文档。</span><span class="sxs-lookup"><span data-stu-id="ca44d-241">For more information about this setting, see the Oracle documentation.</span></span>  
  
## <a name="oracle-error-ora-01555"></a><span data-ttu-id="ca44d-242">Oracle 错误 ORA-01555</span><span class="sxs-lookup"><span data-stu-id="ca44d-242">Oracle Error ORA-01555</span></span>  
 <span data-ttu-id="ca44d-243">下列 Oracle 数据库错误与快照复制无关；而与 Oracle 如何构造读取一致数据视图相关：</span><span class="sxs-lookup"><span data-stu-id="ca44d-243">The following Oracle database error is not related to snapshot replication; it is related to how Oracle constructs read-consistent views of data:</span></span>  
  
 <span data-ttu-id="ca44d-244">“ORA-01555: 快照太旧”</span><span class="sxs-lookup"><span data-stu-id="ca44d-244">"ORA-01555: Snapshot too old"</span></span>  
  
 <span data-ttu-id="ca44d-245">Oracle 使用名为“回滚段”的对象在发出 SQL 语句的时间点处构造读取一致数据视图。</span><span class="sxs-lookup"><span data-stu-id="ca44d-245">Using objects known as rollback segments, Oracle constructs read-consistent views of data as of the point in time a SQL statement is issued.</span></span> <span data-ttu-id="ca44d-246">回滚信息被其他并发会话覆盖时，可能出现“快照太旧”错误。</span><span class="sxs-lookup"><span data-stu-id="ca44d-246">A "snapshot too old" error might occur when rollback information is overwritten by other concurrent sessions.</span></span> <span data-ttu-id="ca44d-247">在 Oracle 9i 之前的版本中，推荐使用增加回滚段的大小和/或数量，并将较大事务分配给特定的回滚段来降低此错误的出现频率。</span><span class="sxs-lookup"><span data-stu-id="ca44d-247">Prior to Oracle 9i, the recommended method of reducing the frequency of this error was to increase the size and/or number of rollback segments, and to assign large transactions to a specific rollback segment.</span></span>  
  
 <span data-ttu-id="ca44d-248">在 Oracle 9i 中，Oracle 引入了 UNDO 表空间概念，这取代了回滚段。</span><span class="sxs-lookup"><span data-stu-id="ca44d-248">In Oracle 9i, Oracle introduced the UNDO tablespace concept, which replaces the rollback segment.</span></span> <span data-ttu-id="ca44d-249">若要避免 Oracle 9i 中出现“快照太旧”错误，建议您：</span><span class="sxs-lookup"><span data-stu-id="ca44d-249">To prevent the "snapshot too old" error in Oracle 9i, it is recommended that you:</span></span>  
  
-   <span data-ttu-id="ca44d-250">创建具有适当可用空间量的 UNDO 表空间。</span><span class="sxs-lookup"><span data-stu-id="ca44d-250">Create an UNDO tablespace with an appropriate amount of free space.</span></span>  
  
-   <span data-ttu-id="ca44d-251">对表空间设置保留保证空间（Oracle 10G 及更大）。</span><span class="sxs-lookup"><span data-stu-id="ca44d-251">Set the retention guarantee on the tablespace (Oracle 10G and greater).</span></span>  
  
-   <span data-ttu-id="ca44d-252">配置 Oracle 初始化参数 UNDO_MANAGEMENT 和 UNDO_RETENTION。</span><span class="sxs-lookup"><span data-stu-id="ca44d-252">Configure the Oracle initialization parameters UNDO_MANAGEMENT and UNDO_RETENTION.</span></span>  
  
 <span data-ttu-id="ca44d-253">有关避免出现“快照太旧”错误的详细信息，请参阅 Oracle 文档。</span><span class="sxs-lookup"><span data-stu-id="ca44d-253">For further details about avoiding the "snapshot too old" error, consult the Oracle documentation.</span></span>  
  
## <a name="oracle-error-ora-22285"></a><span data-ttu-id="ca44d-254">Oracle 错误 ORA-22285</span><span class="sxs-lookup"><span data-stu-id="ca44d-254">Oracle Error ORA-22285</span></span>  
 <span data-ttu-id="ca44d-255">如果表包括一个 BFILE 列，则该列的数据会存储于文件系统中。</span><span class="sxs-lookup"><span data-stu-id="ca44d-255">If a table includes a BFILE column, the data for the column is stored in the file system.</span></span> <span data-ttu-id="ca44d-256">必须使用以下语法授予复制管理用户帐户对存储数据的目录的访问权限：</span><span class="sxs-lookup"><span data-stu-id="ca44d-256">The replication administrative user account must be granted access to the directory in which the data is stored using the following syntax:</span></span>  
  
 `GRANT READ ON DIRECTORY <directory_name> TO <replication_administrative_user_schema>`  
  
 <span data-ttu-id="ca44d-257">如果未授予访问权限，日志读取器代理会引发下列错误：</span><span class="sxs-lookup"><span data-stu-id="ca44d-257">If access is not granted, the following error is raised by the Log Reader Agent:</span></span>  
  
 <span data-ttu-id="ca44d-258">“ORA-22285: 不存在用于 FILEOPEN 操作的目录或文件”</span><span class="sxs-lookup"><span data-stu-id="ca44d-258">"ORA-22285: non-existent directory or file for FILEOPEN operation"</span></span>  
  
## <a name="changes-are-made-that-require-reconfiguration-of-the-publisher"></a><span data-ttu-id="ca44d-259">进行了需要重新配置发布服务器的更改</span><span class="sxs-lookup"><span data-stu-id="ca44d-259">Changes Are Made That Require Reconfiguration of the Publisher</span></span>  
 <span data-ttu-id="ca44d-260">对复制元数据表或过程的更改需要删除并重新配置发布服务器。</span><span class="sxs-lookup"><span data-stu-id="ca44d-260">Changes to replication metadata tables or procedures require that you drop and reconfigure the Publisher.</span></span> <span data-ttu-id="ca44d-261">若要重新配置发布服务器，必须用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、Transact-SQL 或 RMO 删除发布服务器并再次配置它。</span><span class="sxs-lookup"><span data-stu-id="ca44d-261">To reconfigure the Publisher, you must drop the Publisher and configure it again using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], Transact-SQL, or RMO.</span></span> <span data-ttu-id="ca44d-262">有关配置发布服务器的信息，请参阅[配置 Oracle 发布服务器](configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="ca44d-262">For information about configuring the Publisher, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="ca44d-263">**删除 Oracle 发布服务器 (** SQL Server Management Studio **)**</span><span class="sxs-lookup"><span data-stu-id="ca44d-263">**To drop an Oracle Publisher (** SQL Server Management Studio **)**</span></span>  
  
1.  <span data-ttu-id="ca44d-264">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中连接到 Oracle 发布服务器的分发服务器并展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="ca44d-264">Connect to the Distributor for the Oracle Publisher in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and expand the server node.</span></span>  
  
2.  <span data-ttu-id="ca44d-265">右键单击 **“复制”** ，然后单击 **“分发服务器属性”** 。</span><span class="sxs-lookup"><span data-stu-id="ca44d-265">Right-click **Replication**, and then click **Distributor Properties**.</span></span>  
  
3.  <span data-ttu-id="ca44d-266">在 **“分发服务器属性”** 对话框中的 **“发布服务器”** 页上，清除 Oracle 发布服务器的复选框。</span><span class="sxs-lookup"><span data-stu-id="ca44d-266">On the **Publishers** page of the **Distributor Properties** dialog box, clear the check box for the Oracle Publisher.</span></span>  
  
4.  <span data-ttu-id="ca44d-267">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ca44d-267">Click **OK**.</span></span>  
  
 <span data-ttu-id="ca44d-268">**删除 Oracle 发布服务器 (Transact-SQL)**</span><span class="sxs-lookup"><span data-stu-id="ca44d-268">**To drop an Oracle Publisher (Transact-SQL)**</span></span>  
  
-   <span data-ttu-id="ca44d-269">执行 **sp_dropdistpublisher**。</span><span class="sxs-lookup"><span data-stu-id="ca44d-269">Execute **sp_dropdistpublisher**.</span></span> <span data-ttu-id="ca44d-270">有关详细信息，请参阅 [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ca44d-270">For more information, see [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca44d-271">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca44d-271">See Also</span></span>  
 <span data-ttu-id="ca44d-272">[配置 Oracle 发布服务器](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="ca44d-272">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="ca44d-273">Oracle 发布概述</span><span class="sxs-lookup"><span data-stu-id="ca44d-273">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
