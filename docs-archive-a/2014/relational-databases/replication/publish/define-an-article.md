---
title: 定义项目 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], defining
- sp_addmergearticle
- adding articles
- sp_addarticle
- articles [SQL Server replication], adding
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d7ff1f5f516d438ed07a203223acf32970a7961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591256"
---
# <a name="define-an-article"></a><span data-ttu-id="3748e-102">定义项目</span><span class="sxs-lookup"><span data-stu-id="3748e-102">Define an Article</span></span>
  <span data-ttu-id="3748e-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定义项目。</span><span class="sxs-lookup"><span data-stu-id="3748e-103">This topic describes how to define an article in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="3748e-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3748e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3748e-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3748e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3748e-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3748e-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3748e-107">安全性</span><span class="sxs-lookup"><span data-stu-id="3748e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3748e-108">**定义项目，使用：**</span><span class="sxs-lookup"><span data-stu-id="3748e-108">**To define an article, using:**</span></span>  
  
     [<span data-ttu-id="3748e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3748e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3748e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3748e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="3748e-111">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="3748e-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3748e-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="3748e-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3748e-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3748e-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3748e-114">项目名称不能包含以下任何字符：%、\*、[、]、|、:、"、?</span><span class="sxs-lookup"><span data-stu-id="3748e-114">Article names cannot include any of the following characters: % , \* , [ , ] , | , : , " , ?</span></span> <span data-ttu-id="3748e-115">, ' , \ , / , \< , >.</span><span class="sxs-lookup"><span data-stu-id="3748e-115">, ' , \ , / , \< , >.</span></span> <span data-ttu-id="3748e-116">如果数据库中的对象包括任意上述字符，并且您希望复制它们，那么必须指定一个不同于相应对象名称的项目名称。</span><span class="sxs-lookup"><span data-stu-id="3748e-116">If objects in the database include any of these characters and you want to replicate them, you must specify an article name that is different from the object name.</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3748e-117">Security</span><span class="sxs-lookup"><span data-stu-id="3748e-117">Security</span></span>  
 <span data-ttu-id="3748e-118">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="3748e-118">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="3748e-119">如果必须存储凭据，请使用 [Windows .NET Framework 提供的](https://go.microsoft.com/fwlink/?LinkId=34733) Cryptographic Services [!INCLUDE[msCoName](../../../includes/msconame-md.md)] （加密服务）。</span><span class="sxs-lookup"><span data-stu-id="3748e-119">If you must store credentials, use the [cryptographic services](https://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3748e-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3748e-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3748e-121">可以使用新建发布向导创建发布和定义项目。</span><span class="sxs-lookup"><span data-stu-id="3748e-121">Create publications and define articles with the New Publication Wizard.</span></span> <span data-ttu-id="3748e-122">创建发布之后，可在“发布属性 - \<Publication>”对话框中查看和修改发布属性。</span><span class="sxs-lookup"><span data-stu-id="3748e-122">After a publication is created, view and modify publication properties in the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="3748e-123">有关从 Oracle 数据库创建发布的信息，请参阅[从 Oracle 数据库创建发布](create-a-publication-from-an-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-123">For information about creating a publication from an Oracle database, see [Create a Publication from an Oracle Database](create-a-publication-from-an-oracle-database.md).</span></span>  
  
#### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="3748e-124">创建发布和定义项目</span><span class="sxs-lookup"><span data-stu-id="3748e-124">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="3748e-125">在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="3748e-125">Connect to the Publisher in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="3748e-126">展开 **“复制”** 文件夹，再右键单击 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3748e-126">Expand the **Replication** folder, and then right-click the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="3748e-127">单击 **“新建发布”** 。</span><span class="sxs-lookup"><span data-stu-id="3748e-127">Click **New Publication**.</span></span>  
  
4.  <span data-ttu-id="3748e-128">按照新建发布向导中的页完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="3748e-128">Follow the pages in the New Publication Wizard to:</span></span>  
  
    -   <span data-ttu-id="3748e-129">如果尚未在服务器上配置分发，请指定分发服务器。</span><span class="sxs-lookup"><span data-stu-id="3748e-129">Specify a Distributor if distribution has not been configured on the server.</span></span> <span data-ttu-id="3748e-130">有关如何配置分发的详细信息，请参阅[配置发布和分发](../configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-130">For more information about configuring distribution, see [Configure Publishing and Distribution](../configure-publishing-and-distribution.md).</span></span>  
  
         <span data-ttu-id="3748e-131">如果在 **“分发服务器”** 页上指定将发布服务器用作其自己的分发服务器（本地分发服务器），而未将服务器配置为分发服务器，则新建发布向导将配置该服务器。</span><span class="sxs-lookup"><span data-stu-id="3748e-131">If you specify on the **Distributor** page that the Publisher server will act as its own Distributor (a local Distributor), and the server is not configured as a Distributor, the New Publication Wizard will configure the server.</span></span> <span data-ttu-id="3748e-132">在 **“快照文件夹”** 页中指定分发服务器的快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="3748e-132">You will specify a default snapshot folder for the Distributor on the **Snapshot Folder** page.</span></span> <span data-ttu-id="3748e-133">快照文件夹只是指定共享的目录。向此文件夹中执行读写操作的代理必须对其具有足够的访问权限。</span><span class="sxs-lookup"><span data-stu-id="3748e-133">The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it.</span></span> <span data-ttu-id="3748e-134">有关正确保护文件夹的详细信息，请参阅[保护快照文件夹](../security/secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-134">For more information about securing the folder appropriately, see [Secure the Snapshot Folder](../security/secure-the-snapshot-folder.md).</span></span>  
  
         <span data-ttu-id="3748e-135">如果指定另一台服务器作为分发服务器，则必须在 **“管理密码”** 页上输入密码来连接发布服务器和分发服务器。</span><span class="sxs-lookup"><span data-stu-id="3748e-135">If you specify that another server should act as the Distributor, you must enter a password on the **Administrative Password** page for connections made from the Publisher to the Distributor.</span></span> <span data-ttu-id="3748e-136">此密码必须与在远程分发服务器上启用发布服务器时所指定的密码相匹配。</span><span class="sxs-lookup"><span data-stu-id="3748e-136">This password must match the password specified when the Publisher was enabled at the remote Distributor.</span></span>  
  
         <span data-ttu-id="3748e-137">有关详细信息，请参阅 [Configure Distribution](../configure-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-137">For more information, see [Configure Distribution](../configure-distribution.md).</span></span>  
  
    -   <span data-ttu-id="3748e-138">选择发布数据库。</span><span class="sxs-lookup"><span data-stu-id="3748e-138">Choose a publication database.</span></span>  
  
    -   <span data-ttu-id="3748e-139">选择发布类型。</span><span class="sxs-lookup"><span data-stu-id="3748e-139">Select a publication type.</span></span> <span data-ttu-id="3748e-140">有关详细信息，请参阅[复制类型](../types-of-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-140">For more information, see [Types of Replication](../types-of-replication.md).</span></span>  
  
    -   <span data-ttu-id="3748e-141">指定要发布的数据和数据库对象；（可选）筛选来自表项目的列，并设置项目属性。</span><span class="sxs-lookup"><span data-stu-id="3748e-141">Specify data and database objects to publish; optionally filter columns from table articles, and set article properties.</span></span>  
  
    -   <span data-ttu-id="3748e-142">可选择筛选来自表项目的行。</span><span class="sxs-lookup"><span data-stu-id="3748e-142">Optionally filter rows from table articles.</span></span> <span data-ttu-id="3748e-143">有关详细信息，请参阅[筛选已发布数据](filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-143">For more information, see [Filter Published Data](filter-published-data.md).</span></span>  
  
    -   <span data-ttu-id="3748e-144">设置快照代理调度。</span><span class="sxs-lookup"><span data-stu-id="3748e-144">Set the Snapshot Agent schedule.</span></span>  
  
    -   <span data-ttu-id="3748e-145">指定运行下列复制代理和进行连接的凭证：</span><span class="sxs-lookup"><span data-stu-id="3748e-145">Specify the credentials under which the following replication agents run and make connections:</span></span>  
  
         <span data-ttu-id="3748e-146">\- 用于所有发布的快照代理。</span><span class="sxs-lookup"><span data-stu-id="3748e-146">\- Snapshot Agent for all publications.</span></span>  
  
         <span data-ttu-id="3748e-147">\- 用于所有事务发布的日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="3748e-147">\- Log Reader Agent for all transactional publications.</span></span>  
  
         <span data-ttu-id="3748e-148">\- 用于允许更新订阅的事务发布的队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="3748e-148">\- Queue Reader Agent for transactional publications that allow updating subscriptions.</span></span>  
  
         <span data-ttu-id="3748e-149">有关详细信息，请参阅 [Replication Agent Security Model](../security/replication-agent-security-model.md) 和 [Replication Security Best Practices](../security/replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-149">For more information, see [Replication Agent Security Model](../security/replication-agent-security-model.md) and [Replication Security Best Practices](../security/replication-security-best-practices.md).</span></span>  
  
    -   <span data-ttu-id="3748e-150">（可选）编写发布脚本。</span><span class="sxs-lookup"><span data-stu-id="3748e-150">Optionally script the publication.</span></span> <span data-ttu-id="3748e-151">有关详细信息，请参阅 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-151">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
    -   <span data-ttu-id="3748e-152">指定发布的名称。</span><span class="sxs-lookup"><span data-stu-id="3748e-152">Specify a name for the publication.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3748e-153">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3748e-153">Using Transact-SQL</span></span>  
 <span data-ttu-id="3748e-154">在创建发布后，可以使用复制存储过程以编程方式创建项目。</span><span class="sxs-lookup"><span data-stu-id="3748e-154">After a publication has been created, articles can be created programmatically using replication stored procedures.</span></span> <span data-ttu-id="3748e-155">用于创建项目的存储过程取决于要为其定义项目的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="3748e-155">The stored procedures used to create an article will depend on the type of publication for which the article is being defined.</span></span> <span data-ttu-id="3748e-156">有关详细信息，请参阅 [Create a Publication](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-156">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-define-an-article-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="3748e-157">为快照发布或事务发布定义项目</span><span class="sxs-lookup"><span data-stu-id="3748e-157">To define an article for a Snapshot or Transactional Publication</span></span>  
  
1.  <span data-ttu-id="3748e-158">在发布服务器上，对发布数据库执行 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3748e-158">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="3748e-159">指定项目所属的**发布的名称、项目 \@ **的名称、要为** \@ source_object**发布的数据库对象以及\*\* \@ \*\*任何其他可选参数。</span><span class="sxs-lookup"><span data-stu-id="3748e-159">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and any other optional parameters.</span></span> <span data-ttu-id="3748e-160">使用\*\* \@ source_owner**指定对象的架构所有权（如果不是**dbo\*\*）。</span><span class="sxs-lookup"><span data-stu-id="3748e-160">Use **\@source_owner** to specify the schema ownership of the object, if not **dbo**.</span></span> <span data-ttu-id="3748e-161">如果项目不是基于日志的表项目，则指定\*\* \@ 类型\*\*的项目类型; 有关详细信息，请参阅[指定项目类型 &#40;复制 transact-sql 编程&#41;](specify-article-types-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-161">If the article is not a log-based table article, specify the article type for **\@type**; for more information, see [Specify Article Types &#40;Replication Transact-SQL Programming&#41;](specify-article-types-replication-transact-sql-programming.md).</span></span>  
  
2.  <span data-ttu-id="3748e-162">若要水平筛选表中的行或查看项目，请使用 [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) 来定义筛选子句。</span><span class="sxs-lookup"><span data-stu-id="3748e-162">To horizontally filter rows in a table or view an article, use [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) to define the filter clause.</span></span> <span data-ttu-id="3748e-163">有关详细信息，请参阅 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-163">For more information, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
3.  <span data-ttu-id="3748e-164">若要垂直筛选表中的列或查看项目，请使用 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3748e-164">To vertically filter columns in a table or view an article, use [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql).</span></span> <span data-ttu-id="3748e-165">有关详细信息，请参阅 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-165">For more information, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
4.  <span data-ttu-id="3748e-166">如果已经筛选出了项目，请执行 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="3748e-166">Execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) if the article is filtered.</span></span>  
  
5.  <span data-ttu-id="3748e-167">如果发布已具有订阅，并且 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) 在 **immediate_sync** 列中返回 **0** 值，必须调用 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 将项目添加到每个现有订阅。</span><span class="sxs-lookup"><span data-stu-id="3748e-167">If the publication has existing subscriptions and [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) returns a value of **0** in the **immediate_sync** column, you must call [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) to add the article to each existing subscription.</span></span>  
  
6.  <span data-ttu-id="3748e-168">如果发布已具有请求订阅，可在发布服务器上执行 [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) 为现有请求订阅创建只包含新项目的新快照。</span><span class="sxs-lookup"><span data-stu-id="3748e-168">If the publication has existing pull subscriptions, execute [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) at the Publisher to create a new snapshot for existing pull subscriptions that contains just the new article.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3748e-169">对于没有使用快照进行初始化的订阅，不需要执行 [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) ，因为该过程由 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)执行。</span><span class="sxs-lookup"><span data-stu-id="3748e-169">For subscriptions that are not initialized using a snapshot, you do not need to execute [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) as this procedure is executed by [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span>  
  
#### <a name="to-define-an-article-for-a-merge-publication"></a><span data-ttu-id="3748e-170">为合并发布定义项目</span><span class="sxs-lookup"><span data-stu-id="3748e-170">To define an article for a Merge Publication</span></span>  
  
1.  <span data-ttu-id="3748e-171">在发布服务器上，对发布数据库执行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3748e-171">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="3748e-172">指定发布的名称、项目名称\*\* \@ **和** \@ 项目**名称，以及要为** \@ source_object\*\*发布的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="3748e-172">Specify the name of the publication for **\@publication**, a name for the article name for **\@article**, and the object being published for **\@source_object**.</span></span> <span data-ttu-id="3748e-173">若要水平筛选表行，请指定\*\* \@ subset_filterclause\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="3748e-173">To horizontally filter table rows, specify a value for **\@subset_filterclause**.</span></span> <span data-ttu-id="3748e-174">有关详细信息，请参阅 [定义和修改合并项目的参数化行筛选器](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) 和 [定义和修改静态行筛选器](define-and-modify-a-static-row-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-174">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) and [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span> <span data-ttu-id="3748e-175">如果项目不是表项目，请指定\*\* \@ 类型\*\*的项目类型。</span><span class="sxs-lookup"><span data-stu-id="3748e-175">If the article is not a table article, specify the article type for **\@type**.</span></span> <span data-ttu-id="3748e-176">有关详细信息，请参阅[指定项目类型（复制 Transact-SQL 编程）](specify-article-types-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-176">For more information, see [Specify Article Types &#40;Replication Transact-SQL Programming&#41;](specify-article-types-replication-transact-sql-programming.md).</span></span>  
  
2.  <span data-ttu-id="3748e-177">（可选）在发布服务器上，对发布数据库执行 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) 以在两个项目之间定义一个联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="3748e-177">(Optional) At the Publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) to define a join filter between two articles.</span></span> <span data-ttu-id="3748e-178">有关详细信息，请参阅 [定义和修改合并项目间的联接筛选器](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-178">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
3.  <span data-ttu-id="3748e-179">（可选）在发布服务器上的发布数据库中，执行 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 可筛选表列。</span><span class="sxs-lookup"><span data-stu-id="3748e-179">(Optional) At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) to filter table columns.</span></span> <span data-ttu-id="3748e-180">有关详细信息，请参阅 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="3748e-180">For more information, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="3748e-181">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3748e-181">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="3748e-182">本例为某个事务发布定义了一个基于 `Product` 表的项目，其中项目在水平和垂直两个方向上进行了筛选。</span><span class="sxs-lookup"><span data-stu-id="3748e-182">This example defines an article based on the `Product` table for a transactional publication, where the article is filtered both horizontally and vertically.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="3748e-183">本例为某个合并发布定义项目，其中 `SalesOrderHeader` 项目基于 **SalesPersonID**进行静态筛选，而 `SalesOrderDetail` 项目则基于 `SalesOrderHeader`进行联接筛选。</span><span class="sxs-lookup"><span data-stu-id="3748e-183">This example defines articles for a merge publication, where the `SalesOrderHeader` article is statically filtered based on **SalesPersonID**, and the `SalesOrderDetail` article is join filtered based on `SalesOrderHeader`.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="3748e-184">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="3748e-184">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="3748e-185">可以使用复制管理对象 (RMO) 以编程方式定义项目。</span><span class="sxs-lookup"><span data-stu-id="3748e-185">You can define articles programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="3748e-186">用来定义项目的 RMO 类取决于要为其定义项目的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="3748e-186">The RMO classes that you use to define an article depend on the type of publication for which the article is defined.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="3748e-187">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="3748e-187">Examples (RMO)</span></span>  
 <span data-ttu-id="3748e-188">下例向一个事务发布添加一个带有行和列筛选器的项目。</span><span class="sxs-lookup"><span data-stu-id="3748e-188">The following example adds an article with row and column filters to a transactional publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 <span data-ttu-id="3748e-189">下例将三个项目添加到一个合并发布。</span><span class="sxs-lookup"><span data-stu-id="3748e-189">The following example adds three articles to a merge publication.</span></span> <span data-ttu-id="3748e-190">这些项目具有列筛选器，而且使用两个联接筛选器来将一个参数化行筛选器传播给其他项目。</span><span class="sxs-lookup"><span data-stu-id="3748e-190">The articles have column filters, and two join filters are used to propagate a parameterized row filter to the other articles.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## <a name="see-also"></a><span data-ttu-id="3748e-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3748e-191">See Also</span></span>  
 <span data-ttu-id="3748e-192">[Create a Publication](create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="3748e-192">[Create a Publication](create-a-publication.md) </span></span>  
 <span data-ttu-id="3748e-193">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="3748e-193">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="3748e-194">[向现有发布添加项目和从中删除项目](add-articles-to-and-drop-articles-from-existing-publications.md) </span><span class="sxs-lookup"><span data-stu-id="3748e-194">[Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md) </span></span>  
 <span data-ttu-id="3748e-195">[筛选已发布数据](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="3748e-195">[Filter Published Data](filter-published-data.md) </span></span>  
 <span data-ttu-id="3748e-196">[发布数据和数据库对象](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="3748e-196">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="3748e-197">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="3748e-197">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
