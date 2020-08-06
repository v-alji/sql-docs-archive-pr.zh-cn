---
title: IBM DB2 订阅服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, IBM DB2
- data types [SQL Server replication], non-SQL Server Subscribers
- IBM DB2 Subscribers
- mapping data types [SQL Server replication]
- heterogeneous Subscribers, IBM DB2
ms.assetid: a1a27b1e-45dd-4d7d-b6c0-2b608ed175f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54263e75c0f4c7da7c6d9c24ea499c202372aa64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690549"
---
# <a name="ibm-db2-subscribers"></a><span data-ttu-id="8cf4e-102">IBM DB2 Subscribers</span><span class="sxs-lookup"><span data-stu-id="8cf4e-102">IBM DB2 Subscribers</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="8cf4e-103">支持通过 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host Integration Server 附带的 OLE DB 访问接口对 IBM DB2/AS 400、DB2/MVS 和 DB2/通用数据库进行的推送订阅。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-103">supports push subscriptions to IBM DB2/AS 400, DB2/MVS, and DB2/Universal Database through the OLE DB providers that are included with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host Integration Server.</span></span>  
  
## <a name="configuring-an-ibm-db2-subscriber"></a><span data-ttu-id="8cf4e-104">配置 IBM DB2 订阅服务器</span><span class="sxs-lookup"><span data-stu-id="8cf4e-104">Configuring an IBM DB2 Subscriber</span></span>  
 <span data-ttu-id="8cf4e-105">若要配置 IBM DB2 订阅服务器，请按下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="8cf4e-105">To configure an IBM DB2 Subscriber, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8cf4e-106">在分发服务器上安装最新版本的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for DB2：</span><span class="sxs-lookup"><span data-stu-id="8cf4e-106">Install the latest version of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for DB2 on the Distributor:</span></span>  
  
    -   <span data-ttu-id="8cf4e-107">如果使用的是 [!INCLUDE[ssEnterpriseEd11](../../../includes/ssenterpriseed11-md.md)]，请在 [SQL Server 2008 下载](https://go.microsoft.com/fwlink/?LinkId=149256) 网页的 **Related Downloads** （相关下载）部分中，单击指向最新版本的 Microsoft SQL Server 2008 功能包的链接。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-107">If you are using [!INCLUDE[ssEnterpriseEd11](../../../includes/ssenterpriseed11-md.md)], on the [SQL Server 2008 Downloads](https://go.microsoft.com/fwlink/?LinkId=149256) Web page, in the **Related Downloads** section, click the link to the latest version of the Microsoft SQL Server 2008 Feature Pack.</span></span> <span data-ttu-id="8cf4e-108">在 **Microsoft SQL Server 2008 Feature Pack** （Microsoft SQL Server 2008 功能包）网页中，搜索 **Microsoft OLE DB Provider for DB2**。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-108">On the **Microsoft SQL Server 2008 Feature Pack** Web page, search for **Microsoft OLE DB Provider for DB2**.</span></span>  
  
    -   <span data-ttu-id="8cf4e-109">如果使用的是 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Standard，则安装最新版本的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] (HIS) 服务器，其中包含了该访问接口。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-109">If you are using [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Standard, install the latest version of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] (HIS) server, which includes the provider.</span></span>  
  
     <span data-ttu-id="8cf4e-110">除了安装访问接口外，我们还建议您安装数据访问工具（默认情况下，它是下载 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 时安装的），下一步将使用该工具。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-110">In addition to installing the provider, we recommend that you install the Data Access Tool, which is used in the next step (it is installed by default with the download for [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Enterprise).</span></span> <span data-ttu-id="8cf4e-111">有关安装和使用数据访问工具的详细信息，请参阅访问接口文档或 HIS 文档。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-111">For more information about installing and using the Data Access Tool, see the provider documentation or the HIS documentation.</span></span>  
  
2.  <span data-ttu-id="8cf4e-112">为订阅服务器创建连接字符串。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-112">Create a connection string for the Subscriber.</span></span> <span data-ttu-id="8cf4e-113">可以在任何文本编辑器中创建连接字符串，但是建议您使用数据访问工具来创建。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-113">The connection string can be created in any text editor, but we recommend that you use the Data Access Tool.</span></span> <span data-ttu-id="8cf4e-114">在数据访问工具中创建字符串：</span><span class="sxs-lookup"><span data-stu-id="8cf4e-114">To create the string in the Data Access Tool:</span></span>  
  
    1.  <span data-ttu-id="8cf4e-115">依次单击 **“开始”** 、 **“程序”** 、 **“Microsoft OLE DB Provider for DB2”** 、 **“数据访问工具”** 。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-115">Click **Start**, **Programs**, **Microsoft OLE DB Provider for DB2**, and then **Data Access Tool**.</span></span>  
  
    2.  <span data-ttu-id="8cf4e-116">在 **“数据访问工具”** 中，按照步骤提供 DB2 服务器的相关信息。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-116">In the **Data Access Tool**, follow the steps to provide information about the DB2 server.</span></span> <span data-ttu-id="8cf4e-117">当使用此工具完成操作后，就创建了一个包含相关连接字符串的通用数据链接 (UDL)（复制实际使用的不是 UDL，而是连接字符串）。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-117">When you complete the tool, a universal data link (UDL) is created with an associated connection string (the UDL is not actually used by replication, but the connection string is).</span></span>  
  
    3.  <span data-ttu-id="8cf4e-118">访问连接字符串：右键单击数据访问工具中的 UDL 并选择 **“显示连接字符串”** 。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-118">Access the connection string: right-click the UDL in the Data Access Tool and select **Display Connection String**.</span></span>  
  
     <span data-ttu-id="8cf4e-119">连接字符串类似于（使用换行符是为了方便阅读）：</span><span class="sxs-lookup"><span data-stu-id="8cf4e-119">The connection string will be similar to (line breaks are for readability):</span></span>  
  
    ```  
    Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
    PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
    Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
    Persist Security Info=False;Connection Pooling=True;  
    ```  
  
     <span data-ttu-id="8cf4e-120">字符串中的大多数选项都特定于正在配置的 DB2 服务器，但是应始终将 `Process Binary as Character` 选项设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-120">Most of the options in the string are specific to the DB2 server you are configuring, but the `Process Binary as Character` option should always be set to `False`.</span></span> <span data-ttu-id="8cf4e-121">需要为 `Initial Catalog` 选项指定值以标识订阅数据库。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-121">A value is required for the `Initial Catalog` option to identify the subscription database.</span></span> <span data-ttu-id="8cf4e-122">创建订阅时将在新建订阅向导中输入该连接字符串。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-122">The connection string will be entered in the New Subscription Wizard when you create the subscription.</span></span>  
  
3.  <span data-ttu-id="8cf4e-123">创建快照发布或事务发布，为非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器启用该发布，然后为订阅服务器创建推送订阅。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-123">Create a snapshot or transactional publication, enable it for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, and then create a push subscription for the Subscriber.</span></span> <span data-ttu-id="8cf4e-124">有关详细信息，请参阅 [为非 SQL Server 订阅服务器创建订阅](../create-a-subscription-for-a-non-sql-server-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-124">For more information, see [Create a Subscription for a Non-SQL Server Subscriber](../create-a-subscription-for-a-non-sql-server-subscriber.md).</span></span>  
  
4.  <span data-ttu-id="8cf4e-125">（可选）为一个或多个项目指定自定义创建脚本。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-125">Optionally, specify a custom creation script for one or more articles.</span></span> <span data-ttu-id="8cf4e-126">在发布表时，为该表创建 CREATE TABLE 脚本。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-126">When a table is published, a CREATE TABLE script is created for that table.</span></span> <span data-ttu-id="8cf4e-127">对于非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器，该脚本采用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 方言创建，然后由分发代理翻译成较通用的 SQL 方言后应用于订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-127">For non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, the script is created in the [!INCLUDE[tsql](../../../includes/tsql-md.md)] dialect, and it is then translated to a more generic SQL dialect by the Distribution Agent before being applied at the Subscriber.</span></span> <span data-ttu-id="8cf4e-128">若要指定自定义创建脚本，请修改现有的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本或创建使用 DB2 SQL 方言的完整脚本；如果创建 DB2 脚本，请使用 **bypass_translation** 指令，这样分发代理无需转换脚本即可将其应用于订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-128">To specify a custom creation script, either modify the existing [!INCLUDE[tsql](../../../includes/tsql-md.md)] script or create a complete script that uses the DB2 SQL dialect; if a DB2 script is created, use the **bypass_translation** directive so that the Distribution Agent will apply the script at the Subscriber without translation.</span></span>  
  
     <span data-ttu-id="8cf4e-129">修改脚本的原因很多，但最常见的原因是要更改数据类型映射。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-129">Scripts can be modified for a number of reasons, but the most common reason is to alter data type mappings.</span></span> <span data-ttu-id="8cf4e-130">有关详细信息，请参阅本主题的“数据类型映射注意事项”部分。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-130">For more information, see the "Data Type Mapping Considerations" section in this topic.</span></span> <span data-ttu-id="8cf4e-131">如果修改 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本，应只限于对数据类型映射进行更改（而且脚本不应包含任何注释）。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-131">If you modify the [!INCLUDE[tsql](../../../includes/tsql-md.md)] script, changes should be restricted to data type mapping changes (and the script should not contain any comments).</span></span> <span data-ttu-id="8cf4e-132">如果需要进行重大更改，请创建 DB2 脚本。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-132">If more substantial changes are required, create a DB2 script.</span></span>  
  
     <span data-ttu-id="8cf4e-133">**修改项目脚本并将其作为自定义创建脚本提供**</span><span class="sxs-lookup"><span data-stu-id="8cf4e-133">**To modify an article script and supply it as a custom creation script**</span></span>  
  
    1.  <span data-ttu-id="8cf4e-134">为发布生成快照后，定位到该发布的快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-134">After the snapshot has been generated for the publication, navigate to the snapshot folder for the publication.</span></span>  
  
    2.  <span data-ttu-id="8cf4e-135">找到名称与项目名称（如 MyArticle.sch）相同的 .sch 文件。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-135">Locate the .sch file with the same name as the article, such as MyArticle.sch.</span></span>  
  
    3.  <span data-ttu-id="8cf4e-136">使用记事本或其他文本编辑器打开此文件。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-136">Open this file using Notepad or another text editor.</span></span>  
  
    4.  <span data-ttu-id="8cf4e-137">修改此文件并将其保存到其他目录。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-137">Modify the file and save it to a different directory.</span></span>  
  
    5.  <span data-ttu-id="8cf4e-138">执行 sp_changearticle，为 *creation_script* 属性指定文件路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-138">Execute sp_changearticle, specifying the file path and name for the *creation_script* property.</span></span> <span data-ttu-id="8cf4e-139">有关详细信息，请参阅 [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-139">For more information, see [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span>  
  
     <span data-ttu-id="8cf4e-140">**创建项目脚本并将其作为自定义创建脚本提供**</span><span class="sxs-lookup"><span data-stu-id="8cf4e-140">**To create an article script and supply it as a custom creation script**</span></span>  
  
    1.  <span data-ttu-id="8cf4e-141">使用 DB2 SQL 方言创建项目脚本。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-141">Create an article script using the DB2 SQL dialect.</span></span> <span data-ttu-id="8cf4e-142">请确保该文件的第一行为 **bypass_translation**，并且该行不包含任何其他内容。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-142">Ensure the first line of the file is **bypass_translation**, with nothing else on the line.</span></span>  
  
    2.  <span data-ttu-id="8cf4e-143">执行 sp_changearticle，为 *creation_script* 属性指定文件路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-143">Execute sp_changearticle, specifying the file path and name for the *creation_script* property.</span></span>  
  
## <a name="considerations-for-ibm-db2-subscribers"></a><span data-ttu-id="8cf4e-144">IBM DB2 订阅服务器的注意事项</span><span class="sxs-lookup"><span data-stu-id="8cf4e-144">Considerations for IBM DB2 Subscribers</span></span>  
 <span data-ttu-id="8cf4e-145">除了 [Non-SQL Server Subscribers](non-sql-server-subscribers.md)主题中所述注意事项外，在向 DB2 订阅服务器复制时，请考虑以下问题：</span><span class="sxs-lookup"><span data-stu-id="8cf4e-145">In addition to the considerations covered in the topic [Non-SQL Server Subscribers](non-sql-server-subscribers.md), consider the following issues when replicating to DB2 Subscribers:</span></span>  
  
-   <span data-ttu-id="8cf4e-146">每个复制的表的数据和索引都分配到一个 DB2 表空间。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-146">The data and indexes for each replicated table are assigned to a DB2 tablespace.</span></span> <span data-ttu-id="8cf4e-147">DB2 表空间的页大小决定表空间中表的最大列数和最大行大小。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-147">The page size of a DB2 tablespace controls the maximum number of columns and the maximum row size of the tables belonging to the tablespace.</span></span> <span data-ttu-id="8cf4e-148">应确保与复制的表关联的表空间与表的复制列数和最大行大小适当。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-148">Ensure that the tablespace associated with replicated tables is appropriate based on the number of replicated columns and the maximum row size of the tables.</span></span>  
  
-   <span data-ttu-id="8cf4e-149">如果表中有一个或多个主键列的数据类型为 DECIMAL(32-38, 0-38) 或 NUMERIC(32-38, 0-38)，请勿使用事务复制向 DB2 订阅服务器发布表。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-149">Do not publish tables to DB2 Subscribers using transactional replication if one or more primary key columns in the table is of data type DECIMAL(32-38, 0-38) or NUMERIC(32-38, 0-38).</span></span> <span data-ttu-id="8cf4e-150">事务复制使用主键标识行，这可能会导致失败，因为这些数据类型在订阅服务器上均映射为 VARCHAR(41)。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-150">Transactional replication identifies rows using the primary key; this can result in failures because these data types are mapped to VARCHAR(41) at the Subscriber.</span></span> <span data-ttu-id="8cf4e-151">可以使用快照复制发布包含使用这些数据类型的主键的表。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-151">Tables with primary keys that use these data types can be published using snapshot replication.</span></span>  
  
-   <span data-ttu-id="8cf4e-152">如果要在订阅服务器上预创建表，而不是让复制创建这些表，请使用“仅支持复制”选项。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-152">If you want to pre-create tables at the Subscriber, rather than having replication create them, use the replication support only option.</span></span> <span data-ttu-id="8cf4e-153">有关详细信息，请参阅 [初始化事务订阅（不使用快照）](../initialize-a-transactional-subscription-without-a-snapshot.md)中手动初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-153">For more information, see [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
-   <span data-ttu-id="8cf4e-154">与 DB2 相比，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 允许使用更长的表名称和列名称：</span><span class="sxs-lookup"><span data-stu-id="8cf4e-154">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] allows longer table names and column names than DB2:</span></span>  
  
    -   <span data-ttu-id="8cf4e-155">如果发布数据库中有表的名称长度超过订阅服务器上 DB2 版本所支持的长度，请为 destination_table 项目属性指定一个备用名称。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-155">If the publication database includes tables with names longer than those supported on the DB2 version at the Subscriber, specify an alternative name for the destination_table article property.</span></span> <span data-ttu-id="8cf4e-156">有关创建发布时设置属性的详细信息，请参阅[创建发布](../publish/create-a-publication.md)和[定义项目](../publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-156">For more information about setting properties when creating a publication, see [Create a Publication](../publish/create-a-publication.md) and [Define an Article](../publish/define-an-article.md).</span></span>  
  
    -   <span data-ttu-id="8cf4e-157">不能指定备用列名称。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-157">It is not possible to specify alternative column names.</span></span> <span data-ttu-id="8cf4e-158">必须确保已发布的表所包含的列名称长度均不超过订阅服务器上 DB2 版本所支持的长度。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-158">You must ensure that published tables do not include column names longer than those supported on the DB2 version at the Subscriber.</span></span>  
  
## <a name="mapping-data-types-from-sql-server-to-ibm-db2"></a><span data-ttu-id="8cf4e-159">将 SQL Server 中的数据类型映射到 IBM DB2</span><span class="sxs-lookup"><span data-stu-id="8cf4e-159">Mapping Data Types from SQL Server to IBM DB2</span></span>  
 <span data-ttu-id="8cf4e-160">下表显示了将数据复制到运行 IBM DB2 的订阅服务器上时使用的数据类型映射。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-160">The following table shows the data type mappings that are used when data is replicated to a Subscriber running IBM DB2.</span></span>  
  
|<span data-ttu-id="8cf4e-161">SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="8cf4e-161">SQL Server data type</span></span>|<span data-ttu-id="8cf4e-162">IBM DB2 数据类型</span><span class="sxs-lookup"><span data-stu-id="8cf4e-162">IBM DB2 data type</span></span>|  
|--------------------------|-----------------------|  
|`bigint`|<span data-ttu-id="8cf4e-163">DECIMAL(19,0)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-163">DECIMAL(19,0)</span></span>|  
|`binary(1-254)`|<span data-ttu-id="8cf4e-164">CHAR(1-254) FOR BIT DATA</span><span class="sxs-lookup"><span data-stu-id="8cf4e-164">CHAR(1-254) FOR BIT DATA</span></span>|  
|`binary(255-8000)`|<span data-ttu-id="8cf4e-165">VARCHAR(255-8000) FOR BIT DATA</span><span class="sxs-lookup"><span data-stu-id="8cf4e-165">VARCHAR(255-8000) FOR BIT DATA</span></span>|  
|`bit`|<span data-ttu-id="8cf4e-166">SMALLINT</span><span class="sxs-lookup"><span data-stu-id="8cf4e-166">SMALLINT</span></span>|  
|`char(1-254)`|<span data-ttu-id="8cf4e-167">CHAR(1-254)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-167">CHAR(1-254)</span></span>|  
|`char(255-8000)`|<span data-ttu-id="8cf4e-168">VARCHAR(255-8000)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-168">VARCHAR(255-8000)</span></span>|  
|`date`|<span data-ttu-id="8cf4e-169">DATE</span><span class="sxs-lookup"><span data-stu-id="8cf4e-169">DATE</span></span>|  
|`datetime`|<span data-ttu-id="8cf4e-170">TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="8cf4e-170">TIMESTAMP</span></span>|  
|`datetime2(0-7)`|<span data-ttu-id="8cf4e-171">VARCHAR(27)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-171">VARCHAR(27)</span></span>|  
|`datetimeoffset(0-7)`|<span data-ttu-id="8cf4e-172">VARCHAR(34)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-172">VARCHAR(34)</span></span>|  
|`decimal(1-31, 0-31)`|<span data-ttu-id="8cf4e-173">DECIMAL(1-31, 0-31)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-173">DECIMAL(1-31, 0-31)</span></span>|  
|`decimal(32-38, 0-38)`|<span data-ttu-id="8cf4e-174">VARCHAR(41)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-174">VARCHAR(41)</span></span>|  
|`float(53)`|<span data-ttu-id="8cf4e-175">DOUBLE</span><span class="sxs-lookup"><span data-stu-id="8cf4e-175">DOUBLE</span></span>|  
|`float`|<span data-ttu-id="8cf4e-176">FLOAT</span><span class="sxs-lookup"><span data-stu-id="8cf4e-176">FLOAT</span></span>|  
|`geography`|<span data-ttu-id="8cf4e-177">IMAGE</span><span class="sxs-lookup"><span data-stu-id="8cf4e-177">IMAGE</span></span>|  
|`geometry`|<span data-ttu-id="8cf4e-178">IMAGE</span><span class="sxs-lookup"><span data-stu-id="8cf4e-178">IMAGE</span></span>|  
|`hierarchyid`|<span data-ttu-id="8cf4e-179">IMAGE</span><span class="sxs-lookup"><span data-stu-id="8cf4e-179">IMAGE</span></span>|  
|`image`|<span data-ttu-id="8cf4e-180">对于位数据<sup>1</sup> ，VARCHAR (0) </span><span class="sxs-lookup"><span data-stu-id="8cf4e-180">VARCHAR(0) FOR BIT DATA<sup>1</sup></span></span>|  
|`into`|<span data-ttu-id="8cf4e-181">INT</span><span class="sxs-lookup"><span data-stu-id="8cf4e-181">INT</span></span>|  
|`money`|<span data-ttu-id="8cf4e-182">DECIMAL(19,4)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-182">DECIMAL(19,4)</span></span>|  
|`nchar(1-4000)`|<span data-ttu-id="8cf4e-183">VARCHAR(1-4000)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-183">VARCHAR(1-4000)</span></span>|  
|`ntext`|<span data-ttu-id="8cf4e-184">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8cf4e-184">VARCHAR(0)<sup>1</sup></span></span>|  
|`numeric(1-31, 0-31)`|<span data-ttu-id="8cf4e-185">DECIMAL(1-31,0-31)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-185">DECIMAL(1-31,0-31)</span></span>|  
|`numeric(32-38, 0-38)`|<span data-ttu-id="8cf4e-186">VARCHAR(41)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-186">VARCHAR(41)</span></span>|  
|`nvarchar(1-4000)`|<span data-ttu-id="8cf4e-187">VARCHAR(1-4000)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-187">VARCHAR(1-4000)</span></span>|  
|`nvarchar(max)`|<span data-ttu-id="8cf4e-188">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8cf4e-188">VARCHAR(0)<sup>1</sup></span></span>|  
|`real`|<span data-ttu-id="8cf4e-189">REAL</span><span class="sxs-lookup"><span data-stu-id="8cf4e-189">REAL</span></span>|  
|`smalldatetime`|<span data-ttu-id="8cf4e-190">TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="8cf4e-190">TIMESTAMP</span></span>|  
|`smallint`|<span data-ttu-id="8cf4e-191">SMALLINT</span><span class="sxs-lookup"><span data-stu-id="8cf4e-191">SMALLINT</span></span>|  
|`smallmoney`|<span data-ttu-id="8cf4e-192">DECIMAL(10,4)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-192">DECIMAL(10,4)</span></span>|  
|`sql_variant`|<span data-ttu-id="8cf4e-193">空值</span><span class="sxs-lookup"><span data-stu-id="8cf4e-193">N/A</span></span>|  
|`sysname`|<span data-ttu-id="8cf4e-194">VARCHAR(128)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-194">VARCHAR(128)</span></span>|  
|`text`|<span data-ttu-id="8cf4e-195">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8cf4e-195">VARCHAR(0)<sup>1</sup></span></span>|  
|`time(0-7)`|<span data-ttu-id="8cf4e-196">VARCHAR(16)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-196">VARCHAR(16)</span></span>|  
|`timestamp`|<span data-ttu-id="8cf4e-197">CHAR(8) FOR BIT DATA</span><span class="sxs-lookup"><span data-stu-id="8cf4e-197">CHAR(8) FOR BIT DATA</span></span>|  
|`tinyint`|<span data-ttu-id="8cf4e-198">SMALLINT</span><span class="sxs-lookup"><span data-stu-id="8cf4e-198">SMALLINT</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="8cf4e-199">CHAR(38)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-199">CHAR(38)</span></span>|  
|`varbinary(1-8000)`|<span data-ttu-id="8cf4e-200">VARCHAR(1-8000) FOR BIT DATA</span><span class="sxs-lookup"><span data-stu-id="8cf4e-200">VARCHAR(1-8000) FOR BIT DATA</span></span>|  
|`varchar(1-8000)`|<span data-ttu-id="8cf4e-201">VARCHAR(1-8000)</span><span class="sxs-lookup"><span data-stu-id="8cf4e-201">VARCHAR(1-8000)</span></span>|  
|`varbinary(max)`|<span data-ttu-id="8cf4e-202">对于位数据<sup>1</sup> ，VARCHAR (0) </span><span class="sxs-lookup"><span data-stu-id="8cf4e-202">VARCHAR(0) FOR BIT DATA<sup>1</sup></span></span>|  
|`varchar(max)`|<span data-ttu-id="8cf4e-203">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8cf4e-203">VARCHAR(0)<sup>1</sup></span></span>|  
|`xml`|<span data-ttu-id="8cf4e-204">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8cf4e-204">VARCHAR(0)<sup>1</sup></span></span>|  
  
 <span data-ttu-id="8cf4e-205"><sup>1</sup>请参阅下一节，了解有关映射到 VARCHAR (0) 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-205"><sup>1</sup> See the next section for more information about mappings to VARCHAR(0).</span></span>  
  
### <a name="data-type-mapping-considerations"></a><span data-ttu-id="8cf4e-206">数据类型映射注意事项</span><span class="sxs-lookup"><span data-stu-id="8cf4e-206">Data Type Mapping Considerations</span></span>  
 <span data-ttu-id="8cf4e-207">复制到 DB2 订阅服务器时，请考虑下列数据类型映射问题：</span><span class="sxs-lookup"><span data-stu-id="8cf4e-207">Consider the following data type mapping issues when replicating to DB2 Subscribers:</span></span>  
  
-   <span data-ttu-id="8cf4e-208">将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `char` 、 `varchar` 、 `binary` 和分别映射 `varbinary` 到 db2 CHAR、varchar、CHAR for bit data 和 varchar for bit data 时，复制会将 DB2 数据类型的长度设置为与类型的长度相同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-208">When mapping [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `char`, `varchar`, `binary` and `varbinary` to DB2 CHAR, VARCHAR, CHAR FOR BIT DATA, and VARCHAR FOR BIT DATA, respectively, replication sets the length of the DB2 data type to be the same as that of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type.</span></span>  
  
     <span data-ttu-id="8cf4e-209">这样，只要 DB2 页大小约束足够大，能容纳最大行大小，就可以在订阅服务器上成功创建已生成的表。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-209">This allows the generated table to be successfully created at the Subscriber, as long as the DB2 page size constraint is large enough to accommodate the maximum size of the row.</span></span> <span data-ttu-id="8cf4e-210">请确保用于访问 DB2 数据库的登录帐户具有访问表空间的权限，这些表空间具有足够大小可以存放向 DB2 复制的表。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-210">Ensure that the login used to access the DB2 database has permissions to access table spaces of a sufficient size for the tables being replicated to DB2.</span></span>  
  
-   <span data-ttu-id="8cf4e-211">DB2 可以支持 32 KB 大的 VARCHAR 列，因此可以将某些 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大型对象列适当映射到 DB2 VARCHAR 列。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-211">DB2 can support VARCHAR columns as large as 32 kilobytes (KB); therefore it is possible that some [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] large object columns can be appropriately mapped to DB2 VARCHAR columns.</span></span> <span data-ttu-id="8cf4e-212">但是，复制用于 DB2 的 OLE DB 访问接口不支持将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大型对象映射到 DB2 大型对象。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-212">However, the OLE DB provider that replication uses for DB2 does not support mapping [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] large objects to DB2 large objects.</span></span> <span data-ttu-id="8cf4e-213">出于此原因， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `text` `varchar(max)` `ntext` `nvarchar(max)` 在生成的创建脚本中，、、和列映射到 VARCHAR (0) 。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-213">For this reason, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `text`, `varchar(max)`, `ntext`, and `nvarchar(max)` columns are mapped to VARCHAR(0) in the generated create scripts.</span></span> <span data-ttu-id="8cf4e-214">在将脚本应用于订阅服务器之前，必须将长度值 0 更改为一个适当的值。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-214">The length value of 0 must be changed to an appropriate value prior to applying the script to the Subscriber.</span></span> <span data-ttu-id="8cf4e-215">如果不更改数据类型长度，则当试图在 DB2 订阅服务器上创建表时，DB2 会产生错误 604（错误 604 表示数据类型的精度或长度属性无效）。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-215">If the data type length is not changed, DB2 will raise error 604 when the table create is attempted at the DB2 Subscriber (error 604 indicates that the precision or length attribute of a data type is not valid).</span></span>  
  
     <span data-ttu-id="8cf4e-216">请根据您对要复制的源表的了解来确定是否适于将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大型对象映射到可变长度的 DB2 项，并在自定义创建脚本中指定适当的最大长度。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-216">Based upon your knowledge of the source table that you are replicating, determine whether it is appropriate to map a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] large object to a variable length DB2 item, and specify an appropriate maximum length in a custom creation script.</span></span> <span data-ttu-id="8cf4e-217">有关指定自定义创建脚本的信息，请参阅本主题中“配置 IBM DB2 订阅服务器”部分的步骤 5。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-217">For information about specifying a custom creation script, see step 5 in the section "Configuring an IBM DB2 Subscriber" in this topic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8cf4e-218">DB2 类型的指定长度（与其他列长度组合时）不能超过由为表数据分配的 DB2 表空间限定的最大行大小。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-218">The specified length for the DB2 type, when combined with other column lengths, cannot exceed the maximum row size based upon the DB2 table space that the table data is assigned to.</span></span>  
  
     <span data-ttu-id="8cf4e-219">如果对于某个大型对象列没有适当的映射，请考虑对项目使用列筛选，以避免复制该列。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-219">If there is no appropriate mapping for a large object column, consider using column filtering on the article so that the column is not replicated.</span></span> <span data-ttu-id="8cf4e-220">有关详细信息，请参阅[筛选已发布数据](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-220">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
-   <span data-ttu-id="8cf4e-221">复制 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `nchar` 和 `nvarchar` 到 DB2 CHAR 和 VARCHAR 时，复制为 db2 类型使用的长度说明符与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 类型相同。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-221">When replicating [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `nchar` and `nvarchar` to DB2 CHAR and VARCHAR, replication uses the same length-specifier for the DB2 type as for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type.</span></span> <span data-ttu-id="8cf4e-222">但是，数据类型长度对于生成的 DB2 表而言可能太小。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-222">However, the data type length might too small for the generated DB2 table.</span></span>  
  
     <span data-ttu-id="8cf4e-223">在某些 DB2 环境中， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `char` 数据项并不限于单字节字符; CHAR 或 VARCHAR 项的长度必须考虑到这一点。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-223">In some DB2 environments, a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `char` data item is not restricted to single-byte characters; the length of a CHAR or VARCHAR item must take this into account.</span></span> <span data-ttu-id="8cf4e-224">如果需要，还必须考虑到“移入” \*\* 字符和“移出” \*\* 字符。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-224">You must also take into account *shift in* and *shift out* characters if they are needed.</span></span> <span data-ttu-id="8cf4e-225">如果要使用 `nchar` 和列复制表 `nvarchar` ，则可能需要在自定义创建脚本中为数据类型指定更大的最大长度。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-225">If you are replicating tables with `nchar` and `nvarchar` columns, you might need to specify a larger maximum length for the data type in a custom creation script.</span></span> <span data-ttu-id="8cf4e-226">有关指定自定义创建脚本的信息，请参阅本主题中“配置 IBM DB2 订阅服务器”部分的步骤 5。</span><span class="sxs-lookup"><span data-stu-id="8cf4e-226">For information about specifying a custom creation script, see step 5 in the section "Configuring an IBM DB2 Subscriber" in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cf4e-227">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8cf4e-227">See Also</span></span>  
 <span data-ttu-id="8cf4e-228">[Non-SQL Server Subscribers](non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="8cf4e-228">[Non-SQL Server Subscribers](non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="8cf4e-229">订阅发布</span><span class="sxs-lookup"><span data-stu-id="8cf4e-229">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
  
  
