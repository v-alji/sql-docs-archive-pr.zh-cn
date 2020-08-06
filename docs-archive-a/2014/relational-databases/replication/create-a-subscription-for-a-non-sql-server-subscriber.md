---
title: 为非 SQL Server 订阅服务器创建订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], non-SQL Server Subscribers
- Subscribers [SQL Server replication], non-SQL Server Subscribers
- non-SQL Server Subscribers, subscriptions
ms.assetid: 5020ee68-b988-4d57-8066-67d183e61237
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 31a7d1e52c53cb858039f1fd0ed403f255ad5ca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688833"
---
# <a name="create-a-subscription-for-a-non-sql-server-subscriber"></a><span data-ttu-id="879a6-102">为非 SQL Server 订阅服务器创建订阅</span><span class="sxs-lookup"><span data-stu-id="879a6-102">Create a Subscription for a Non-SQL Server Subscriber</span></span>
  <span data-ttu-id="879a6-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中为非 SQL Server 订阅服务器创建订阅。</span><span class="sxs-lookup"><span data-stu-id="879a6-103">This topic describes how to create a subscription for a non-SQL Server Subscriber in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="879a6-104">事务复制和快照复制支持向非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器发布数据。</span><span class="sxs-lookup"><span data-stu-id="879a6-104">Transactional and snapshot replication support publishing data to non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers.</span></span> <span data-ttu-id="879a6-105">有关支持的订阅服务器平台的信息，请参阅 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)中为非 SQL Server 订阅服务器创建订阅。</span><span class="sxs-lookup"><span data-stu-id="879a6-105">For information about supported Subscriber platforms, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
 <span data-ttu-id="879a6-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="879a6-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="879a6-107">**为非 SQL Server 订阅服务器创建订阅，使用：**</span><span class="sxs-lookup"><span data-stu-id="879a6-107">**To create a subscription for a non-SQL Server Subscriber, using:**</span></span>  
  
     [<span data-ttu-id="879a6-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="879a6-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="879a6-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="879a6-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="879a6-110">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="879a6-110">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="879a6-111">若要为非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器创建订阅，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="879a6-111">To create a subscription for a non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber:</span></span>  
  
1.  <span data-ttu-id="879a6-112">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分发服务器上安装并配置适当的客户端软件和 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="879a6-112">Install and configure the appropriate client software and OLE DB provider(s) on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor.</span></span> <span data-ttu-id="879a6-113">有关详细信息，请参阅 [Oracle Subscribers](non-sql/oracle-subscribers.md) 和 [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-113">For more information, see [Oracle Subscribers](non-sql/oracle-subscribers.md) and [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md).</span></span>  
  
2.  <span data-ttu-id="879a6-114">使用新建发布向导创建发布。</span><span class="sxs-lookup"><span data-stu-id="879a6-114">Create a publication using the New Publication Wizard.</span></span> <span data-ttu-id="879a6-115">有关创建发布的详细信息，请参阅[创建发布](publish/create-a-publication.md)和[从 Oracle 数据库创建发布](publish/create-a-publication-from-an-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-115">For more information about creating publications, see [Create a Publication](publish/create-a-publication.md) and [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).</span></span> <span data-ttu-id="879a6-116">在新建发布向导中指定下列选项：</span><span class="sxs-lookup"><span data-stu-id="879a6-116">Specify the following options in the New Publication Wizard:</span></span>  
  
    -   <span data-ttu-id="879a6-117">在 **“发布类型”** 页上，选择 **“快照发布”** 或 **“事务发布”** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-117">On the **Publication Type** page, select **Snapshot publication** or **Transactional publication**.</span></span>  
  
    -   <span data-ttu-id="879a6-118">在 **“快照代理”** 页上，清除 **“立即创建快照”** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-118">On the **Snapshot Agent** page, clear **Create a snapshot immediately**.</span></span>  
  
         <span data-ttu-id="879a6-119">在为非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器启用发布之后，再创建快照，这样可以确保快照代理生成适合非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器的快照和初始化脚本。</span><span class="sxs-lookup"><span data-stu-id="879a6-119">You create the snapshot after the publication is enabled for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers to ensure that the Snapshot Agent generates a snapshot and initialization scripts that are suitable for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers.</span></span>  
  
3.  <span data-ttu-id="879a6-120">通过“发布属性 - \<PublicationName>”对话框为非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器启用发布。</span><span class="sxs-lookup"><span data-stu-id="879a6-120">Enable the publication for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers using the **Publication Properties - \<PublicationName>** dialog box.</span></span> <span data-ttu-id="879a6-121">有关此步骤的详细信息，请参阅 [Publication Properties, Subscription Options](publication-properties-subscription-options.md) 。</span><span class="sxs-lookup"><span data-stu-id="879a6-121">See [Publication Properties, Subscription Options](publication-properties-subscription-options.md) for more information about this step.</span></span>  
  
4.  <span data-ttu-id="879a6-122">使用新建订阅向导创建订阅。</span><span class="sxs-lookup"><span data-stu-id="879a6-122">Create a subscription using the New Subscription Wizard.</span></span> <span data-ttu-id="879a6-123">本主题提供了有关此步骤的详细信息。</span><span class="sxs-lookup"><span data-stu-id="879a6-123">This topic provides more information about this step.</span></span>  
  
5.  <span data-ttu-id="879a6-124">（可选）将 **pre_creation_cmd** 项目属性更改为在订阅服务器上保留表。</span><span class="sxs-lookup"><span data-stu-id="879a6-124">(Optional) Change the **pre_creation_cmd** article property to retain tables at the Subscriber.</span></span> <span data-ttu-id="879a6-125">本主题提供了有关此步骤的详细信息。</span><span class="sxs-lookup"><span data-stu-id="879a6-125">This topic provides more information about this step.</span></span>  
  
6.  <span data-ttu-id="879a6-126">为发布生成快照。</span><span class="sxs-lookup"><span data-stu-id="879a6-126">Generate a snapshot for the publication.</span></span> <span data-ttu-id="879a6-127">本主题提供了有关此步骤的详细信息。</span><span class="sxs-lookup"><span data-stu-id="879a6-127">This topic provides more information about this step.</span></span>  
  
7.  <span data-ttu-id="879a6-128">同步订阅。</span><span class="sxs-lookup"><span data-stu-id="879a6-128">Synchronize the subscription.</span></span> <span data-ttu-id="879a6-129">有关详细信息，请参阅 [同步推送订阅](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-129">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-enable-a-publication-for-non-sql-server-subscribers"></a><span data-ttu-id="879a6-130">为非 SQL Server 订阅服务器启用发布</span><span class="sxs-lookup"><span data-stu-id="879a6-130">To enable a publication for non-SQL Server Subscribers</span></span>  
  
1.  <span data-ttu-id="879a6-131">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="879a6-131">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="879a6-132">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="879a6-132">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="879a6-133">右键单击发布，再单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-133">Right-click the publication, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="879a6-134">在 **“订阅选项”** 页上，为选项 **“允许非 SQL Server 订阅服务器”** 选择 **True**值。</span><span class="sxs-lookup"><span data-stu-id="879a6-134">On the **Subscription Options** page, select a value of **True** for the option **Allow non-SQL Server Subscribers**.</span></span> <span data-ttu-id="879a6-135">选择此选项可更改多个属性，从而可以使发布与非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器兼容。</span><span class="sxs-lookup"><span data-stu-id="879a6-135">Selecting this option changes a number of properties so that the publication is compatible with non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="879a6-136">选择 **True** 会将 **pre_creation_cmd** 项目属性的值设置为“drop”。</span><span class="sxs-lookup"><span data-stu-id="879a6-136">Selecting **True** sets the value of the **pre_creation_cmd** article property to 'drop'.</span></span> <span data-ttu-id="879a6-137">此设置指定，如果复制与项目中某个表的名称相匹配，则复制应删除订阅服务器上对应的表。</span><span class="sxs-lookup"><span data-stu-id="879a6-137">This setting specifies that replication should drop a table at the Subscriber if it matches the name of the table in the article.</span></span> <span data-ttu-id="879a6-138">如果要保留订阅服务器上的现有表，则可以对每个项目使用 [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) 存储过程，并为 **pre_creation_cmd**指定值“none”： `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`。</span><span class="sxs-lookup"><span data-stu-id="879a6-138">If you have existing tables at the Subscriber that you want to keep, use the [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) stored procedure for each article; specify a value 'none' for **pre_creation_cmd**: `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] <span data-ttu-id="879a6-139">系统将会提示为发布创建新快照。</span><span class="sxs-lookup"><span data-stu-id="879a6-139">You will be prompted to create a new snapshot for the publication.</span></span> <span data-ttu-id="879a6-140">如果不想在此时创建快照，可以在以后使用下一个“如何”过程中介绍的步骤创建快照。</span><span class="sxs-lookup"><span data-stu-id="879a6-140">If you do not want to create one at this time, use the steps described in the next "how to" procedure at a later time.</span></span>  
  
#### <a name="to-create-a-subscription-for-a-non-sql-server-subscriber"></a><span data-ttu-id="879a6-141">为非 SQL Server 订阅服务器创建订阅</span><span class="sxs-lookup"><span data-stu-id="879a6-141">To create a subscription for a non-SQL Server Subscriber</span></span>  
  
1.  <span data-ttu-id="879a6-142">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="879a6-142">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
2.  <span data-ttu-id="879a6-143">右键单击相应的发布，再单击 **“新建订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-143">Right-click the appropriate publication, and then click **New Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="879a6-144">在 **“分发代理位置”** 页上，确保已选中 **“在分发服务器上运行所有代理”** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-144">On the **Distribution Agent Location** page, ensure **Run all agents at the Distributor** is selected.</span></span> <span data-ttu-id="879a6-145">非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器不支持在订阅服务器上运行代理。</span><span class="sxs-lookup"><span data-stu-id="879a6-145">Non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers do not support running agents at the Subscriber.</span></span>  
  
4.  <span data-ttu-id="879a6-146">在 **“订阅服务器”** 页上，单击 **“添加订阅服务器”** ，再单击 **“添加非 SQL Server 订阅服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-146">On the **Subscribers** page, click **Add Subscriber** and then click **Add Non-SQL Server Subscriber**.</span></span>  
  
5.  <span data-ttu-id="879a6-147">在 **“添加非 SQL Server 订阅服务器”** 对话框中，选择订阅服务器的类型。</span><span class="sxs-lookup"><span data-stu-id="879a6-147">In the **Add Non-SQL Server Subscriber** dialog box, select the type of Subscriber.</span></span>  
  
6.  <span data-ttu-id="879a6-148">在 **“数据源名称”** 中输入值：</span><span class="sxs-lookup"><span data-stu-id="879a6-148">Enter a value in **Data source name**:</span></span>  
  
    -   <span data-ttu-id="879a6-149">对于 Oracle，该值是您配置的透明网络底层 (TNS) 的名称。</span><span class="sxs-lookup"><span data-stu-id="879a6-149">For Oracle, this is the transparent network substrate (TNS) name you configured.</span></span>  
  
    -   <span data-ttu-id="879a6-150">对于 IBM，该值可以是任意名称。</span><span class="sxs-lookup"><span data-stu-id="879a6-150">For IBM, this can be any name.</span></span> <span data-ttu-id="879a6-151">通常指定订阅服务器的网络地址。</span><span class="sxs-lookup"><span data-stu-id="879a6-151">It is typical to specify the network address of the Subscriber.</span></span>  
  
     <span data-ttu-id="879a6-152">此向导并不验证此步骤中输入的数据源名称和步骤 9 中指定的凭据。</span><span class="sxs-lookup"><span data-stu-id="879a6-152">The data source name entered in this step and the credentials specified in step 9 are not validated by this wizard.</span></span> <span data-ttu-id="879a6-153">直到为订阅运行分发代理后复制才会使用它们。</span><span class="sxs-lookup"><span data-stu-id="879a6-153">They are not used by replication until the Distribution Agent runs for the subscription.</span></span> <span data-ttu-id="879a6-154">请确保所有的值已通过使用客户端工具（如 Oracle 的 **sqlplus** ）连接到订阅服务器进行了测试。</span><span class="sxs-lookup"><span data-stu-id="879a6-154">Ensure that all values have been tested by connecting to the Subscriber using a client tool (such as **sqlplus** for Oracle).</span></span> <span data-ttu-id="879a6-155">有关详细信息，请参阅 [Oracle Subscribers](non-sql/oracle-subscribers.md) 和 [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-155">For more information, see [Oracle Subscribers](non-sql/oracle-subscribers.md) and [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md).</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] <span data-ttu-id="879a6-156">在该向导的 **“订阅服务器”** 页上，订阅服务器现在显示在 **“订阅服务器”** 列中，并在 **“订阅数据库”** 列中显示只读 **“(默认目标)”** ：</span><span class="sxs-lookup"><span data-stu-id="879a6-156">On the **Subscribers** page of the wizard, the Subscriber is now displayed in the **Subscriber** column with a read-only **(default destination)** in the **Subscription Database** column:</span></span>  
  
    -   <span data-ttu-id="879a6-157">对于 Oracle，一个服务器最多只有一个数据库，因此不必指定数据库。</span><span class="sxs-lookup"><span data-stu-id="879a6-157">For Oracle, a server has at most one database, so it is not necessary to specify the database.</span></span>  
  
    -   <span data-ttu-id="879a6-158">对于 IBM DB2，该数据库是在 DB2 连接字符串的“初始目录”  属性中指定的，DB2 连接字符串可以在此过程后面介绍的 **“其他连接选项”** 字段中输入。</span><span class="sxs-lookup"><span data-stu-id="879a6-158">For IBM DB2, the database is specified in the **Initial Catalog** property of the DB2 connection string, which can be entered in the **Additional connection options** field described later in this process.</span></span>  
  
8.  <span data-ttu-id="879a6-159">在 "**分发代理安全**" 页上，单击 "订阅者" 旁边的 "属性" **)  (按钮**，以访问**分发代理安全性**"对话框。</span><span class="sxs-lookup"><span data-stu-id="879a6-159">On the **Distribution Agent Security** page, click the properties button (**...**) next to the Subscriber to access the **Distribution Agent Security** dialog box.</span></span>  
  
9. <span data-ttu-id="879a6-160">在 **“分发代理安全性”** 对话框中：</span><span class="sxs-lookup"><span data-stu-id="879a6-160">In the **Distribution Agent Security** dialog box:</span></span>  
  
    -   <span data-ttu-id="879a6-161">在 **“进程帐户”** 、 **“密码”** 和 **“确认密码”** 字段中输入运行分发代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户和密码，与分发服务器建立本地连接。</span><span class="sxs-lookup"><span data-stu-id="879a6-161">In the **Process account**, **Password**, and **Confirm password** fields, enter the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account and password under which the Distribution Agent should run and make local connections to the Distributor.</span></span>  
  
         <span data-ttu-id="879a6-162">该帐户需要下列最低权限：分发数据库中 **db_owner** 固定数据库角色的成员、发布访问列表 (PAL) 的成员、快照共享上的读取权限、OLE DB 访问接口的安装目录上的读取权限。</span><span class="sxs-lookup"><span data-stu-id="879a6-162">The account requires these minimum permissions: member of the **db_owner** fixed database role in the distribution database; member of the publication access list (PAL); read permissions on the snapshot share; and read permission on the install directory of the OLE DB provider.</span></span> <span data-ttu-id="879a6-163">有关 PAL 的详细信息，请参阅[保护发布服务器](security/secure-the-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-163">For more information about the PAL, see [Secure the Publisher](security/secure-the-publisher.md).</span></span>  
  
    -   <span data-ttu-id="879a6-164">在 **“连接到订阅服务器”** 下的 **“登录名”** 、 **“密码”** 和 **“确认密码”** 字段中，输入用于连接到订阅服务器的登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="879a6-164">Under **Connect to the Subscriber**, in the **Login**, **Password**, and **Confirm password** fields, enter the login and password that should be used to connect to the Subscriber.</span></span> <span data-ttu-id="879a6-165">该登录名应该已配置好且应该具有足够的权限可以在订阅数据库中创建对象。</span><span class="sxs-lookup"><span data-stu-id="879a6-165">This login should already be configured and should have sufficient permissions to create objects in the subscription database.</span></span>  
  
    -   <span data-ttu-id="879a6-166">在 **“其他连接选项”** 字段中，以连接字符串的形式为订阅服务器指定任意连接选项（Oracle 不需要其他选项）。</span><span class="sxs-lookup"><span data-stu-id="879a6-166">In the **Additional connection options** field, specify any connection options for the Subscriber in the form of a connection string (Oracle does not require additional options).</span></span> <span data-ttu-id="879a6-167">应使用分号分隔每个选项。</span><span class="sxs-lookup"><span data-stu-id="879a6-167">Each option should be separated by a semi-colon.</span></span> <span data-ttu-id="879a6-168">下面是 DB2 连接字符串的示例（分行符是为了阅读方便）：</span><span class="sxs-lookup"><span data-stu-id="879a6-168">The following is an example of a DB2 connection string (line breaks are for readability):</span></span>  
  
        ```  
        Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
        PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
        Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
        Persist Security Info=False;Connection Pooling=True;  
        ```  
  
         <span data-ttu-id="879a6-169">字符串中的大多数选项都特定于正在配置的 DB2 服务器，但是应始终将“将二进制数作为字符处理”  选项设置为 **False**。</span><span class="sxs-lookup"><span data-stu-id="879a6-169">Most of the options in the string are specific to the DB2 server you are configuring, but the **Process Binary as Character** option should always be set to **False**.</span></span> <span data-ttu-id="879a6-170">需要为“初始目录”  选项指定一个值以标识订阅数据库。</span><span class="sxs-lookup"><span data-stu-id="879a6-170">A value is required for the **Initial Catalog** option to identify the subscription database.</span></span>  
  
10. <span data-ttu-id="879a6-171">在 **“同步计划”** 页上，从 **“代理计划”** 菜单中为分发代理选择一个计划（计划通常为 **“连续运行”** ）。</span><span class="sxs-lookup"><span data-stu-id="879a6-171">On the **Synchronization Schedule** page, select a schedule for the Distribution Agent from the **Agent Schedule** menu (the schedule is typically **Run continuously**).</span></span>  
  
11. <span data-ttu-id="879a6-172">在 **“初始化订阅”** 页上，指定是否应该初始化订阅。如果应该，指定何时初始化：</span><span class="sxs-lookup"><span data-stu-id="879a6-172">On the **Initialize Subscriptions** page, specify whether the subscription should be initialized and, if so, when it should be initialized:</span></span>  
  
    -   <span data-ttu-id="879a6-173">仅在已创建了所有对象并且在订阅数据库中添加了所有需要的数据时才能清除 **“初始化”** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-173">Clear **Initialize** only if you have created all objects and added all required data in the subscription database.</span></span>  
  
    -   <span data-ttu-id="879a6-174">在 **“初始化时间”** 列的下拉列表中选择 **“立即”** ，可以让分发代理在此向导完成后将快照文件传输到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="879a6-174">Select **Immediately** from the drop-down list in the **Initialize When** column to have the Distribution Agent transfer snapshot files to the Subscriber after this wizard is completed.</span></span> <span data-ttu-id="879a6-175">如果选择 **“首先同步”** ，代理则会在下次计划运行的时候传输文件。</span><span class="sxs-lookup"><span data-stu-id="879a6-175">Select **At first synchronization** to have the agent transfer the files the next time it is scheduled to run.</span></span>  
  
12. <span data-ttu-id="879a6-176">在 **“向导操作”** 页上，为订阅编写脚本（可选）。</span><span class="sxs-lookup"><span data-stu-id="879a6-176">On the **Wizard Actions** page, optionally script the subscription.</span></span> <span data-ttu-id="879a6-177">有关详细信息，请参阅 [Scripting Replication](scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-177">For more information, see [Scripting Replication](scripting-replication.md).</span></span>  
  
#### <a name="to-retain-tables-at-the-subscriber"></a><span data-ttu-id="879a6-178">在订阅服务器上保留表</span><span class="sxs-lookup"><span data-stu-id="879a6-178">To retain tables at the Subscriber</span></span>  
  
-   <span data-ttu-id="879a6-179">默认情况下，为非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器启用发布会将 **pre_creation_cmd** 项目属性的值设置为“drop”。</span><span class="sxs-lookup"><span data-stu-id="879a6-179">By default, enabling a publication for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers sets the value of the **pre_creation_cmd** article property to 'drop'.</span></span> <span data-ttu-id="879a6-180">此设置指定，如果复制与项目中某个表的名称相匹配，则复制应删除订阅服务器上对应的表。</span><span class="sxs-lookup"><span data-stu-id="879a6-180">This setting specifies that replication should drop a table at the Subscriber if it matches the name of the table in the article.</span></span> <span data-ttu-id="879a6-181">如果要保留订阅服务器上的现有表，则可以对每个项目使用 [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) 存储过程，并为 **pre_creation_cmd**指定值“none”。</span><span class="sxs-lookup"><span data-stu-id="879a6-181">If you have existing tables at the Subscriber that you want to keep, use the [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) stored procedure for each article; specify a value 'none' for **pre_creation_cmd**.</span></span> <span data-ttu-id="879a6-182">`sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.</span><span class="sxs-lookup"><span data-stu-id="879a6-182">`sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.</span></span>  
  
#### <a name="to-generate-a-snapshot-for-the-publication"></a><span data-ttu-id="879a6-183">为发布生成快照</span><span class="sxs-lookup"><span data-stu-id="879a6-183">To generate a snapshot for the publication</span></span>  
  
1.  <span data-ttu-id="879a6-184">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="879a6-184">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
2.  <span data-ttu-id="879a6-185">右键单击发布，再单击 **“查看快照代理状态”** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-185">Right-click the publication, and then click **View Snapshot Agent Status**.</span></span>  
  
3.  <span data-ttu-id="879a6-186">在“查看快照代理状态 - \<Publication>”对话框中，单击“启动”。 </span><span class="sxs-lookup"><span data-stu-id="879a6-186">In the **View Snapshot Agent Status - \<Publication>** dialog box, click **Start**.</span></span>  
  
 <span data-ttu-id="879a6-187">快照代理生成快照后，将显示一条消息，如“[100%] 已生成 17 个项目的快照”。</span><span class="sxs-lookup"><span data-stu-id="879a6-187">When the Snapshot Agent finishes generating the snapshot, a message is displayed, such as "[100%] A snapshot of 17 article(s) was generated."</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="879a6-188">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="879a6-188">Using Transact-SQL</span></span>  
 <span data-ttu-id="879a6-189">您可以使用复制存储过程以编程的方式创建对非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器的推送订阅。</span><span class="sxs-lookup"><span data-stu-id="879a6-189">You can create push subscriptions to non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers programmatically using replication stored procedures.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="879a6-190">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="879a6-190">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="879a6-191">如果必须在脚本文件中存储凭据，则必须保护文件以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="879a6-191">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
#### <a name="to-create-a-push-subscription-for-a-transactional-or-snapshot-publication-to-a-non-sql-server-subscriber"></a><span data-ttu-id="879a6-192">创建对非 SQL Server 订阅服务器的事务发布或快照发布的推送订阅。</span><span class="sxs-lookup"><span data-stu-id="879a6-192">To create a push subscription for a transactional or snapshot publication to a non-SQL Server Subscriber</span></span>  
  
1.  <span data-ttu-id="879a6-193">在发布服务器和分发服务器上安装非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器的最新 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="879a6-193">Install the most recent OLE DB provider for the non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber at both the Publisher and Distributor.</span></span> <span data-ttu-id="879a6-194">有关 OLE DB 访问接口的复制要求，请参阅 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)、 [Oracle Subscribers](non-sql/oracle-subscribers.md)和 [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-194">For the replication requirements for an OLE DB provider, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md), [Oracle Subscribers](non-sql/oracle-subscribers.md), [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md).</span></span>  
  
2.  <span data-ttu-id="879a6-195">在发布服务器的发布数据库中，通过执行 [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) 验证发布是否支持非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="879a6-195">At the Publisher on the publication database, verify that the publication supports non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers by executing [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span>  
  
    -   <span data-ttu-id="879a6-196">如果 `enabled_for_het_sub` 的值为 1，则支持非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="879a6-196">If the value of `enabled_for_het_sub` is 1, non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers are supported.</span></span>  
  
    -   <span data-ttu-id="879a6-197">如果的值 `enabled_for_het_sub` 为0，则执行[Sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)， `enabled_for_het_sub` **@property** 并 `true` 为指定 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-197">If the value of `enabled_for_het_sub` is 0, execute [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `enabled_for_het_sub` for **@property** and `true` for **@value**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="879a6-198">在将 `enabled_for_het_sub` 更改为 `true` 之前，必须删除发布的任何现有订阅。</span><span class="sxs-lookup"><span data-stu-id="879a6-198">Before changing `enabled_for_het_sub` to `true`, you must drop any existing subscriptions to the publication.</span></span> <span data-ttu-id="879a6-199">当发布还支持更新订阅时，无法将 `enabled_for_het_sub` 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="879a6-199">You cannot set `enabled_for_het_sub` to `true` when the publication also supports updating subscriptions.</span></span> <span data-ttu-id="879a6-200">更改 `enabled_for_het_sub` 将影响其他发布属性。</span><span class="sxs-lookup"><span data-stu-id="879a6-200">Changing `enabled_for_het_sub` will affect other publication properties.</span></span> <span data-ttu-id="879a6-201">有关详细信息，请参阅 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-201">For more information, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
3.  <span data-ttu-id="879a6-202">在发布服务器的发布数据库中，执行 [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="879a6-202">At the Publisher on the publication database, execute [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="879a6-203">指定 **@publication** 、 **@subscriber** 、值为\*\* (默认目标) \*\* ，为 **@destination_db** **推送**值，将值 **@subscription_type** 3 指定 **@subscriber_type** (指定 OLE DB 提供程序) 。</span><span class="sxs-lookup"><span data-stu-id="879a6-203">Specify **@publication**, **@subscriber**, a value of **(default destination)** for **@destination_db**, a value of **push** for **@subscription_type**, and a value of 3 for **@subscriber_type** (specifies an OLE DB provider).</span></span>  
  
4.  <span data-ttu-id="879a6-204">在发布服务器的发布数据库中，执行 [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="879a6-204">At the Publisher on the publication database, execute [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="879a6-205">指定下列各项：</span><span class="sxs-lookup"><span data-stu-id="879a6-205">Specify the following:</span></span>  
  
    -   <span data-ttu-id="879a6-206">**@subscriber**和 **@publication** 参数。</span><span class="sxs-lookup"><span data-stu-id="879a6-206">The **@subscriber**and **@publication** parameters.</span></span>  
  
    -   <span data-ttu-id="879a6-207">\*\* (的默认目标) \*\* **@subscriber_db** 的值</span><span class="sxs-lookup"><span data-stu-id="879a6-207">A value of **(default destination)** for **@subscriber_db**,</span></span>  
  
    -   <span data-ttu-id="879a6-208">、、、和的非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据源的 **@subscriber_provider** 属性 **@subscriber_datasrc** **@subscriber_location** **@subscriber_provider_string** **@subscriber_catalog** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-208">The properties of the non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source for **@subscriber_provider**, **@subscriber_datasrc**, **@subscriber_location**, **@subscriber_provider_string**, and **@subscriber_catalog**.</span></span>  
  
    -   <span data-ttu-id="879a6-209">[!INCLUDE[msCoName](../../includes/msconame-md.md)]分发服务器上的分发代理针对和运行时所用的 Windows 凭据 **@job_login** **@job_password** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-209">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows credentials under which the Distribution Agent at the Distributor runs for **@job_login** and **@job_password**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="879a6-210">使用 Windows 集成身份验证进行的连接始终使用和指定的 Windows 凭据 **@job_login** **@job_password** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-210">Connections made using Windows Integrated Authentication always use the Windows credentials specified by **@job_login** and **@job_password**.</span></span> <span data-ttu-id="879a6-211">分发代理始终使用 Windows 集成身份验证与分发服务器建立本地连接。</span><span class="sxs-lookup"><span data-stu-id="879a6-211">The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication.</span></span> <span data-ttu-id="879a6-212">默认情况下，该代理将使用 Windows 集成身份验证连接到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="879a6-212">By default, the agent will connect to the Subscriber using Windows Integrated Authentication.</span></span>  
  
    -   <span data-ttu-id="879a6-213">的值为**0** **@subscriber_security_mode** ，并为和的 OLE DB 提供程序登录信息 **@subscriber_login** **@subscriber_password** 。</span><span class="sxs-lookup"><span data-stu-id="879a6-213">A value of **0** for **@subscriber_security_mode** and the OLE DB provider login information for **@subscriber_login** and **@subscriber_password**.</span></span>  
  
    -   <span data-ttu-id="879a6-214">该订阅的分发代理作业计划。</span><span class="sxs-lookup"><span data-stu-id="879a6-214">A schedule for the Distribution Agent job for this subscription.</span></span> <span data-ttu-id="879a6-215">有关详细信息，请参阅 [Specify Synchronization Schedules](specify-synchronization-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-215">For more information, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="879a6-216">用远程分发服务器在发布服务器上创建推送订阅时，为所有参数（包括 *job_login* 和 *job_password*）提供的值将以纯文本格式发送到分发服务器。</span><span class="sxs-lookup"><span data-stu-id="879a6-216">When creating a push subscription at a Publisher with a remote Distributor, the values supplied for all parameters, including *job_login* and *job_password*, are sent to the Distributor as plain text.</span></span> <span data-ttu-id="879a6-217">在执行此存储过程之前，应该对发布服务器及其远程分发服务器之间的连接进行加密。</span><span class="sxs-lookup"><span data-stu-id="879a6-217">You should encrypt the connection between the Publisher and its remote Distributor before executing this stored procedure.</span></span> <span data-ttu-id="879a6-218">有关详细信息，请参阅[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="879a6-218">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879a6-219">另请参阅</span><span class="sxs-lookup"><span data-stu-id="879a6-219">See Also</span></span>  
 <span data-ttu-id="879a6-220">[IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="879a6-220">[IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md) </span></span>  
 <span data-ttu-id="879a6-221">[Oracle Subscribers](non-sql/oracle-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="879a6-221">[Oracle Subscribers](non-sql/oracle-subscribers.md) </span></span>  
 <span data-ttu-id="879a6-222">[其他非 SQL Server 订阅服务器](non-sql/other-non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="879a6-222">[Other Non-SQL Server Subscribers](non-sql/other-non-sql-server-subscribers.md) </span></span>  
 <span data-ttu-id="879a6-223">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="879a6-223">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="879a6-224">复制安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="879a6-224">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
