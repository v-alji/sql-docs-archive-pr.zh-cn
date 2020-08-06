---
title: 从 Oracle 数据库创建发布 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], Oracle databases
- Oracle publishing [SQL Server replication], configuring
ms.assetid: b3812746-14b0-4b22-809e-b4a95e1c8083
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 29e299e6f2a3b271fe682b319a2f22a671cbd19d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693734"
---
# <a name="create-a-publication-from-an-oracle-database"></a><span data-ttu-id="2f745-102">从 Oracle 数据库创建发布</span><span class="sxs-lookup"><span data-stu-id="2f745-102">Create a Publication from an Oracle Database</span></span>
  <span data-ttu-id="2f745-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中从 Oracle 数据库创建发布。</span><span class="sxs-lookup"><span data-stu-id="2f745-103">This topic describes how to create a publication from an Oracle database in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2f745-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2f745-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2f745-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2f745-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2f745-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="2f745-106">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="2f745-107">**从 Oracle 数据库创建发布，使用：**</span><span class="sxs-lookup"><span data-stu-id="2f745-107">**To create a publication from an Oracle database, using:**</span></span>  
  
     [<span data-ttu-id="2f745-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2f745-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2f745-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2f745-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2f745-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="2f745-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="2f745-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="2f745-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="2f745-112">在创建发布之前，必须在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器上安装 Oracle 软件，并配置 Oracle 数据库。</span><span class="sxs-lookup"><span data-stu-id="2f745-112">Before creating a publication, you must install Oracle software on the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor, and you must configure the Oracle database.</span></span> <span data-ttu-id="2f745-113">有关详细信息，请参阅[配置 Oracle 发布服务器](../non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="2f745-113">For more information, see [Configure an Oracle Publisher](../non-sql/configure-an-oracle-publisher.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2f745-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2f745-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2f745-115">可以使用新建发布向导，从 Oracle 数据库创建快照发布或事务发布。</span><span class="sxs-lookup"><span data-stu-id="2f745-115">Create a snapshot or transactional publication from an Oracle Database with the New Publication Wizard.</span></span>  
  
 <span data-ttu-id="2f745-116">首次从 Oracle 数据库创建发布时，必须在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器上标识 Oracle 发布服务器（对于来自同一数据库的后续发布，不需要执行此操作）。</span><span class="sxs-lookup"><span data-stu-id="2f745-116">The first time you create a publication from an Oracle database, you must identify the Oracle Publisher at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor (you do not need to do this for subsequent publications from the same database.).</span></span> <span data-ttu-id="2f745-117">标识 Oracle 发布服务器的操作可以从新建发布向导或“分发服务器属性 - \<Distributor>”对话框中完成；本主题介绍了“分发服务器属性 - \<Distributor>”对话框。 </span><span class="sxs-lookup"><span data-stu-id="2f745-117">Identifying the Oracle Publisher can be accomplished from the New Publication Wizard or the **Distributor Properties - \<Distributor>** dialog box; this topic shows the **Distributor Properties - \<Distributor>** dialog box.</span></span>  
  
#### <a name="to-identify-the-oracle-publisher-at-the-sql-server-distributor"></a><span data-ttu-id="2f745-118">在 SQL Server 分发服务器上标识 Oracle 发布服务器</span><span class="sxs-lookup"><span data-stu-id="2f745-118">To identify the Oracle Publisher at the SQL Server Distributor</span></span>  
  
1.  <span data-ttu-id="2f745-119">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，连接到要将 Oracle 发布服务器用作分发服务器的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="2f745-119">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that the Oracle Publisher will use as a Distributor, and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2f745-120">右键单击 **“复制”** 文件夹，然后单击 **“分发服务器属性”** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-120">Right-click the **Replication** folder, and then click **Distributor Properties**.</span></span>  
  
3.  <span data-ttu-id="2f745-121">在“分发服务器属性 - \<Distributor>”对话框的“发布服务器”页上，依次单击“添加”和“添加 Oracle 发布服务器”。   </span><span class="sxs-lookup"><span data-stu-id="2f745-121">On the **Publishers** page of the **Distributor Properties - \<Distributor>** dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span>  
  
4.  <span data-ttu-id="2f745-122">在 **“连接到服务器”** 对话框中，单击 **“选项”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="2f745-122">In the **Connect to Server** dialog box, click the **Options** button.</span></span>  
  
5.  <span data-ttu-id="2f745-123">在 **“登录”** 选项卡上：</span><span class="sxs-lookup"><span data-stu-id="2f745-123">On the **Login** tab:</span></span>  
  
    1.  <span data-ttu-id="2f745-124">输入 Oracle 数据库实例名称，或者选择 **“服务器实例”** 组合框中的 **“浏览更多”** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-124">Enter the Oracle database instance name or select **Browse for more** in the **Server instance** combo box.</span></span>  
  
    2.  <span data-ttu-id="2f745-125">选择 **“Oracle 标准身份验证”** （建议）或 **“Windows 身份验证”** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-125">Select **Oracle Standard Authentication** (recommended) or **Windows Authentication**.</span></span>  
  
         <span data-ttu-id="2f745-126">如果选择了 **“Windows 身份验证”** ，则必须将 Oracle 服务器配置为允许使用 Windows 凭据进行连接（有关详细信息，请参阅 Oracle 文档），并且当前必须使用为复制管理用户架构指定的同一 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 帐户进行登录。</span><span class="sxs-lookup"><span data-stu-id="2f745-126">If you select **Windows Authentication**: the Oracle server must be configured to allow connections using Windows credentials (for more information, see the Oracle documentation); and you must be currently logged in with the same [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows account you specified for the replication administrative user schema.</span></span>  
  
    3.  <span data-ttu-id="2f745-127">如果选择 **“Oracle 标准身份验证”** ，则在配置过程中，请输入在 Oracle 发布服务器上创建的复制管理用户架构的登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="2f745-127">If you select **Oracle Standard Authentication**, enter the login and password of the replication administrative user schema you created on the Oracle Publisher during configuration.</span></span>  
  
6.  <span data-ttu-id="2f745-128">在 **“连接属性”** 选项卡上，选择 **“网关”** 或 **“完整”** 发布服务器类型。</span><span class="sxs-lookup"><span data-stu-id="2f745-128">On the **Connection Properties** tab, select a Publisher type of **Gateway** or **Complete**.</span></span>  
  
     <span data-ttu-id="2f745-129">**“完整”** 选项用于为快照和事务发布提供所支持的完整的 Oracle 发布功能集。</span><span class="sxs-lookup"><span data-stu-id="2f745-129">The **Complete** option is designed to provide snapshot and transactional publications with the complete set of supported features for Oracle publishing.</span></span> <span data-ttu-id="2f745-130">**“网关”** 选项提供特定的设计优化，以提高复制作为系统间的网关时的性能。</span><span class="sxs-lookup"><span data-stu-id="2f745-130">The **Gateway** option provides specific design optimizations to improve performance for cases where replication serves as a gateway between systems.</span></span> <span data-ttu-id="2f745-131">如果计划在多个事务发布中发布同一个表，则无法使用 **“网关”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2f745-131">The **Gateway** option cannot be used if you plan to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="2f745-132">如果选择 **“网关”** ，则一个表可以最多出现在一个事务发布中或出现在任意数量的快照发布中。</span><span class="sxs-lookup"><span data-stu-id="2f745-132">A table can appear in at most one transactional publication and any number of snapshot publications if you select **Gateway**.</span></span>  
  
7.  <span data-ttu-id="2f745-133">单击 **“连接”** ，创建到 Oracle 发布服务器的连接，并配置该连接以进行复制。</span><span class="sxs-lookup"><span data-stu-id="2f745-133">Click **Connect**, which creates a connection to the Oracle Publisher and configures it for replication.</span></span> <span data-ttu-id="2f745-134">“连接至服务器”对话框将关闭，你将返回到“分发服务器属性 - \<Distributor>”对话框。 </span><span class="sxs-lookup"><span data-stu-id="2f745-134">The **Connect to Server** dialog box closes and you are returned to the **Distributor Properties - \<Distributor>** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f745-135">如果网络配置出现问题，则在此将收到一条错误。</span><span class="sxs-lookup"><span data-stu-id="2f745-135">If there are any problems with the network configuration, you will receive an error at this point.</span></span> <span data-ttu-id="2f745-136">如果连接 Oracle 数据库时遇到问题，请参阅 [Troubleshooting Oracle Publishers](../non-sql/troubleshooting-oracle-publishers.md)中的“SQL Server 分发服务器无法连接到 Oracle 数据库实例”部分。</span><span class="sxs-lookup"><span data-stu-id="2f745-136">If you experience problems connecting to the Oracle database, see the section "The SQL Server Distributor cannot connect to the Oracle database instance" in [Troubleshooting Oracle Publishers](../non-sql/troubleshooting-oracle-publishers.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-create-a-publication-from-an-oracle-database"></a><span data-ttu-id="2f745-137">从 Oracle 数据库创建发布</span><span class="sxs-lookup"><span data-stu-id="2f745-137">To create a publication from an Oracle database</span></span>  
  
1.  <span data-ttu-id="2f745-138">连接到要将 Oracle 发布服务器用作分发服务器的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="2f745-138">Connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that the Oracle Publisher will use as a Distributor, and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2f745-139">展开 **“复制”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="2f745-139">Expand the **Replication** folder.</span></span>  
  
3.  <span data-ttu-id="2f745-140">右键单击 **“本地发布”** 文件夹，然后单击 **“新建 Oracle 发布”** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-140">Right-click the **Local Publications** folder, and then click **New Oracle Publication**.</span></span>  
  
4.  <span data-ttu-id="2f745-141">在新建发布向导的 **“Oracle 发布服务器”** 页上，选择 Oracle 发布服务器。</span><span class="sxs-lookup"><span data-stu-id="2f745-141">On the **Oracle Publisher** page of the New Publication Wizard, select the Oracle Publisher.</span></span> <span data-ttu-id="2f745-142">如果未显示 Oracle 发布服务器，请单击 **“添加 Oracle 发布服务器”** ，逐步执行上一过程中的步骤。</span><span class="sxs-lookup"><span data-stu-id="2f745-142">If the Oracle Publisher is not displayed, click **Add Oracle Publisher**, which takes you through the steps from the previous procedure.</span></span>  
  
5.  <span data-ttu-id="2f745-143">在 **“发布类型”** 页上，选择 **“快照发布”** 或 **“事务发布”** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-143">On the **Publication Type** page, select **Snapshot publication** or **Transactional publication**.</span></span>  
  
6.  <span data-ttu-id="2f745-144">在 **“项目”** 页上，选择要发布的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="2f745-144">On the **Articles** page, select the database objects you want to publish.</span></span>  
  
     <span data-ttu-id="2f745-145">也可以通过展开表并清除一个或多个列的复选框，来筛选掉表列。</span><span class="sxs-lookup"><span data-stu-id="2f745-145">Optionally, filter out table columns by expanding a table and then clearing the checkbox for one or more columns.</span></span> <span data-ttu-id="2f745-146">单击 **“项目属性”** 可以查看和修改项目属性，还可以根据需要指定备用数据类型映射。</span><span class="sxs-lookup"><span data-stu-id="2f745-146">Click **Article Properties** to view and modify article properties and to specify alternative data type mappings if necessary.</span></span> <span data-ttu-id="2f745-147">有关数据类型映射的详细信息，请参阅[为 Oracle 发布服务器指定数据类型映射](specify-data-type-mappings-for-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="2f745-147">For more information about data type mappings, see [Specify Data Type Mappings for an Oracle Publisher](specify-data-type-mappings-for-an-oracle-publisher.md).</span></span>  
  
7.  <span data-ttu-id="2f745-148">也可以在 **“筛选表行”** 页上，应用筛选器发布一个或多个表的数据子集。</span><span class="sxs-lookup"><span data-stu-id="2f745-148">On the **Filter Table Rows** page, optionally apply filters to publish a subset of data from one or more tables.</span></span>  
  
8.  <span data-ttu-id="2f745-149">仅在创建所有对象并将所有所需数据添加到订阅数据库后，才能清除 **“快照代理”** 页上的 **“立即创建快照”** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-149">On the **Snapshot Agent** page, clear **Create a snapshot immediately** only if you have created all objects and added all required data in the subscription database.</span></span>  
  
9. <span data-ttu-id="2f745-150">在 **“代理安全性”** 页上，指定快照代理（适用于所有发布）和日志读取器代理（适用于事务发布）的凭据。</span><span class="sxs-lookup"><span data-stu-id="2f745-150">On the **Agent Security** page, specify credentials for the Snapshot Agent (for all publications) and the Log Reader Agent (for transactional publications).</span></span> <span data-ttu-id="2f745-151">代理将使用指定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Windows 帐户上下文运行并连接到 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 分发服务器。</span><span class="sxs-lookup"><span data-stu-id="2f745-151">The agents run and make connections to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor using the context of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows account you specify.</span></span> <span data-ttu-id="2f745-152">代理使用指定为复制管理用户架构的帐户上下文建立到 Oracle 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="2f745-152">The agents make connections to the Oracle database using the context of the account you specified as the replication administrative user schema.</span></span> <span data-ttu-id="2f745-153">有关详细信息，请参阅[配置 Oracle 发布服务器](../non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="2f745-153">For more information, see [Configure an Oracle Publisher](../non-sql/configure-an-oracle-publisher.md).</span></span>  
  
     <span data-ttu-id="2f745-154">有关每个代理所需权限的详细信息，请参阅 [Replication Agent Security Model](../security/replication-agent-security-model.md) 和 [Replication Security Best Practices](../security/replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="2f745-154">For more information about the permissions required by each agent, see [Replication Agent Security Model](../security/replication-agent-security-model.md) and [Replication Security Best Practices](../security/replication-security-best-practices.md).</span></span>  
  
10. <span data-ttu-id="2f745-155">在 **“向导操作”** 页上，根据需要，可以选择为发布编写脚本。</span><span class="sxs-lookup"><span data-stu-id="2f745-155">On the **Wizard Actions** page, optionally script the publication.</span></span> <span data-ttu-id="2f745-156">有关详细信息，请参阅 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="2f745-156">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
11. <span data-ttu-id="2f745-157">在 **“完成该向导”** 页上，指定发布的名称。</span><span class="sxs-lookup"><span data-stu-id="2f745-157">On the **Complete the Wizard** page, specify a name for the publication.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2f745-158">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2f745-158">Using Transact-SQL</span></span>  
 <span data-ttu-id="2f745-159">在将 Oracle 数据库配置为发布服务器后，可以使用系统存储过程创建事务发布或快照发布，方法与从 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 发布服务器创建发布相同。</span><span class="sxs-lookup"><span data-stu-id="2f745-159">After the Oracle database has been configured as a Publisher, you can create a transactional or snapshot publication the same way that you would from a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publisher, by using system stored procedures.</span></span>  
  
#### <a name="to-create-an-oracle-publication"></a><span data-ttu-id="2f745-160">创建 Oracle 发布</span><span class="sxs-lookup"><span data-stu-id="2f745-160">To create an Oracle Publication</span></span>  
  
1.  <span data-ttu-id="2f745-161">将 Oracle 数据库配置为发布服务器。</span><span class="sxs-lookup"><span data-stu-id="2f745-161">Configure the Oracle database as a Publisher.</span></span> <span data-ttu-id="2f745-162">有关详细信息，请参阅[配置 Oracle 发布服务器](../non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="2f745-162">For more information, see [Configure an Oracle Publisher](../non-sql/configure-an-oracle-publisher.md).</span></span>  
  
2.  <span data-ttu-id="2f745-163">如果不存在远程分发服务器，请配置远程分发服务器。</span><span class="sxs-lookup"><span data-stu-id="2f745-163">If a remote Distributor does not exist, configure the remote Distributor.</span></span> <span data-ttu-id="2f745-164">有关详细信息，请参阅 [Configure Publishing and Distribution](../configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="2f745-164">For more information, see [Configure Publishing and Distribution](../configure-publishing-and-distribution.md).</span></span>  
  
3.  <span data-ttu-id="2f745-165">在 Oracle 发布服务器将使用的远程分发服务器上，执行 [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f745-165">At the remote Distributor that the Oracle Publisher will use, execute [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql).</span></span> <span data-ttu-id="2f745-166">指定 (TNS 的 Oracle 数据库实例的透明网络基底) 名称 **@publisher** ，并将的值 `ORACLE` 指定 `ORACLE GATEWAY` 为或 **@publisher_type** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-166">Specify the Transparent Network Substrate (TNS) name of the Oracle database instance for **@publisher** and a value of `ORACLE` or `ORACLE GATEWAY` for **@publisher_type**.</span></span> <span data-ttu-id="2f745-167">`Specify` 从 Oracle 发布服务器连接到远程 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器时使用的以下安全模式之一：</span><span class="sxs-lookup"><span data-stu-id="2f745-167">`Specify` the security mode used when connecting from the Oracle Publisher to the remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor as one of the following:</span></span>  
  
    -   <span data-ttu-id="2f745-168">若要使用 Oracle 标准身份验证（默认值），请将 **@security_mode** 指定值 **@security_mode**，并将 **@login**和 **@password**中从 Oracle 数据库创建发布。</span><span class="sxs-lookup"><span data-stu-id="2f745-168">To use Oracle Standard Authentication, the default, specify a value of **0** for **@security_mode**, the login of the replication administrative user schema you created on the Oracle Publisher during configuration for **@login**, and the password for **@password**.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="2f745-169">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="2f745-169">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="2f745-170">如果将凭据存储在脚本文件中，则必须确保文件的安全以防受到未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="2f745-170">If you store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="2f745-171">若要使用 Windows 身份验证，请将 **@security_mode** 指定值 **@security_mode**中从 Oracle 数据库创建发布。</span><span class="sxs-lookup"><span data-stu-id="2f745-171">To use Windows Authentication, specify a value of **1** for **@security_mode**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2f745-172">若要使用 Windows 身份验证，Oracle 服务器必须配置为允许使用 Windows 凭据的连接（有关更多信息，请参见 Oracle 文档）；而且，您当前必须使用为复制管理用户架构指定的同一 Microsoft Windows 帐户登录到计算机。</span><span class="sxs-lookup"><span data-stu-id="2f745-172">To use Windows Authentication, the Oracle server must be configured to allow connections using Windows credentials (for more information, see the Oracle documentation); and you must be currently logged in with the same Microsoft Windows account you specified for the replication administrative user schema..</span></span>  
  
4.  <span data-ttu-id="2f745-173">为发布数据库创建日志读取器代理作业。</span><span class="sxs-lookup"><span data-stu-id="2f745-173">Create a Log Reader Agent job for the publication database.</span></span>  
  
    -   <span data-ttu-id="2f745-174">如果不确定是否存在针对某个已发布数据库的日志读取器代理作业，请在该 Oracle 发布服务器使用的分发服务器的分发数据库中执行 [sp_helplogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f745-174">If you are unsure whether a Log Reader Agent job exists for a published database, execute [sp_helplogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql) at the Distributor used by the Oracle Publisher on the distribution database.</span></span> <span data-ttu-id="2f745-175">指定 Oracle 发布服务器的名称 **@publisher** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-175">Specify the name of the Oracle Publisher for **@publisher**.</span></span> <span data-ttu-id="2f745-176">如果结果集为空，则必须创建一个日志读取器代理作业。</span><span class="sxs-lookup"><span data-stu-id="2f745-176">If the result set is empty, then a Log Reader Agent job must be created.</span></span>  
  
    -   <span data-ttu-id="2f745-177">如果已经存在针对该发布数据库的日志读取器代理作业，请继续执行步骤 5。</span><span class="sxs-lookup"><span data-stu-id="2f745-177">If a Log Reader Agent job already exists for the publication database, proceed to step 5.</span></span>  
  
    -   <span data-ttu-id="2f745-178">在该 Oracle 发布服务器使用的分发服务器的分发数据库中，执行 [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f745-178">At the Distributor used by the Oracle Publisher on the distribution database, execute [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql).</span></span> <span data-ttu-id="2f745-179">指定为和运行代理所用的 Windows 凭据 **@job_login** **@job_password** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-179">Specify the Windows credentials under which the agent runs for **@job_login** and **@job_password**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2f745-180">**@job_login**参数必须与步骤3中提供的登录名匹配。</span><span class="sxs-lookup"><span data-stu-id="2f745-180">The **@job_login** parameter must match the login supplied in step 3.</span></span> <span data-ttu-id="2f745-181">不要提供发布服务器安全信息。</span><span class="sxs-lookup"><span data-stu-id="2f745-181">Do not supply publisher security information.</span></span> <span data-ttu-id="2f745-182">日志读取器代理使用步骤 3 中提供的安全信息连接到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="2f745-182">The Log Reader agent connects to the Publisher using the security information provided in step 3.</span></span>  
  
5.  <span data-ttu-id="2f745-183">在分发服务器上的分发数据库中，执行 [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) 以创建发布。</span><span class="sxs-lookup"><span data-stu-id="2f745-183">At the Distributor on the distribution database, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) to create the publication.</span></span> <span data-ttu-id="2f745-184">有关详细信息，请参阅 [Create a Publication](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="2f745-184">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
6.  <span data-ttu-id="2f745-185">在分发服务器上的分发数据库中，执行 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f745-185">At the Distributor on the distribution database, execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql).</span></span> <span data-ttu-id="2f745-186">为指定在步骤4中使用的发布名称 **@publication** ，并为和运行快照代理所用的 Windows 凭据 **@job_name** **@password** 。</span><span class="sxs-lookup"><span data-stu-id="2f745-186">Specify the publication name used in step 4 for **@publication** and the Windows credentials under which the Snapshot Agent runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="2f745-187">若要在连接到发布服务器时使用 Oracle 标准身份验证，还必须将 **@security_mode** 指定值 **@publisher_security_mode** 值，并为 **@publisher_login** 和 **@publisher_password**中从 Oracle 数据库创建发布。</span><span class="sxs-lookup"><span data-stu-id="2f745-187">To use Oracle Standard Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher_security_mode** and the Oracle login information for **@publisher_login** and **@publisher_password**.</span></span> <span data-ttu-id="2f745-188">此操作将为发布创建一个快照代理作业。</span><span class="sxs-lookup"><span data-stu-id="2f745-188">This creates a Snapshot Agent job for the publication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f745-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f745-189">See Also</span></span>  
 <span data-ttu-id="2f745-190">[配置 Oracle 发布服务器](../non-sql/configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="2f745-190">[Configure an Oracle Publisher](../non-sql/configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="2f745-191">[发布数据和数据库对象](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="2f745-191">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="2f745-192">[为 Oracle 发布服务器配置事务集作业（复制 Transact-SQL 编程）](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="2f745-192">[Configure the Transaction Set Job for an Oracle Publisher &#40;Replication Transact-SQL Programming&#41;](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="2f745-193">[Oracle 发布概述](../non-sql/oracle-publishing-overview.md) </span><span class="sxs-lookup"><span data-stu-id="2f745-193">[Oracle Publishing Overview](../non-sql/oracle-publishing-overview.md) </span></span>  
 [<span data-ttu-id="2f745-194">授予 Oracle 权限的脚本</span><span class="sxs-lookup"><span data-stu-id="2f745-194">Script to Grant Oracle Permissions</span></span>](../non-sql/script-to-grant-oracle-permissions.md)  
  
  
