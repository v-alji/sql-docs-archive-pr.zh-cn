---
title: 删除项目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], dropping
- sp_droparticle
- sp_dropmergearticle
- deleting articles
- removing articles
- dropping articles
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 082f90d33c2b8dedfae34dcada9b3935bed134ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578808"
---
# <a name="delete-an-article"></a><span data-ttu-id="f161f-102">删除项目</span><span class="sxs-lookup"><span data-stu-id="f161f-102">Delete an Article</span></span>
  <span data-ttu-id="f161f-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中删除项目。</span><span class="sxs-lookup"><span data-stu-id="f161f-103">This topic describes how to delete an article in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or Replication Management Objects (RMO).</span></span> <span data-ttu-id="f161f-104">有关删除项目时使用的条件以及删除项目是否需要新的快照或重新初始化订阅的信息，请参阅[向现有发布添加项目和从中删除项目](add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="f161f-104">For information about the conditions under which articles can be dropped and whether dropping an article requires a new snapshot or the reinitialization of subscriptions, see [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f161f-105">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f161f-105">Using Transact-SQL</span></span>  
 <span data-ttu-id="f161f-106">可以使用复制存储过程以编程方式删除项目。</span><span class="sxs-lookup"><span data-stu-id="f161f-106">Articles can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="f161f-107">使用的存储过程取决于项目所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="f161f-107">The stored procedures that you use depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-delete-an-article-from-a-snapshot-or-transactional-publication"></a><span data-ttu-id="f161f-108">从快照或事务发布中删除项目</span><span class="sxs-lookup"><span data-stu-id="f161f-108">To delete an article from a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="f161f-109">执行 [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) 以从由 \@publication 指定的发布中删除由 \@article 指定的项目\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f161f-109">Execute [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) to delete an article, specified by **\@article**, from a publication, specified by **\@publication**.</span></span> <span data-ttu-id="f161f-110">将\*\* \@ force_invalidate_snapshot**的值指定为**1\*\* 。</span><span class="sxs-lookup"><span data-stu-id="f161f-110">Specify a value of **1** for **\@force_invalidate_snapshot**.</span></span>  
  
2.  <span data-ttu-id="f161f-111">（可选）若要从数据库完全删除已发布的对象，请在发布服务器上对发布数据库执行 `DROP <objectname>` 命令。</span><span class="sxs-lookup"><span data-stu-id="f161f-111">(Optional) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.</span></span>  
  
#### <a name="to-delete-an-article-from-a-merge-publication"></a><span data-ttu-id="f161f-112">从合并发布删除项目</span><span class="sxs-lookup"><span data-stu-id="f161f-112">To delete an article from a merge publication</span></span>  
  
1.  <span data-ttu-id="f161f-113">执行 [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) 以从由 \@publication 指定的发布中删除由 \@article 指定的项目\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f161f-113">Execute [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) to delete an article, specified by **\@article**, from a publication, specified by **\@publication**.</span></span> <span data-ttu-id="f161f-114">如有必要，请将\*\* \@ force_invalidate_snapshot**的值指定为**1\*\* ，并将\*\* \@ force_reinit_subscription**的值指定为**1\*\* 。</span><span class="sxs-lookup"><span data-stu-id="f161f-114">If necessary, specify a value of **1** for **\@force_invalidate_snapshot** and a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="f161f-115">（可选）若要从数据库完全删除已发布的对象，请在发布服务器上对发布数据库执行 `DROP <objectname>` 命令。</span><span class="sxs-lookup"><span data-stu-id="f161f-115">(Optional) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f161f-116">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f161f-116">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="f161f-117">下面的示例将从事务发布中删除项目。</span><span class="sxs-lookup"><span data-stu-id="f161f-117">The following example deletes an article from a transactional publication.</span></span> <span data-ttu-id="f161f-118">因为此更改使现有快照失效，所以为\*\* \@ force_invalidate_snapshot**参数指定了值**1\*\* 。</span><span class="sxs-lookup"><span data-stu-id="f161f-118">Because this change invalidates the existing snapshot, a value of **1** is specified for the **\@force_invalidate_snapshot** parameter.</span></span>  
  
 [!code-sql[HowTo#sp_droparticle](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droparticle)]  
  
 <span data-ttu-id="f161f-119">下面的示例将从合并发布中删除两个项目。</span><span class="sxs-lookup"><span data-stu-id="f161f-119">The following example deletes two articles from a merge publication.</span></span> <span data-ttu-id="f161f-120">由于这些更改使现有快照失效，因此为\*\* \@ force_invalidate_snapshot**参数指定了值**1\*\* 。</span><span class="sxs-lookup"><span data-stu-id="f161f-120">Because these changes invalidate the existing snapshot, a value of **1** is specified for the **\@force_invalidate_snapshot** parameter.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergearticle)]
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergearticles.sql#sp_dropmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="f161f-121">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="f161f-121">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="f161f-122">可以使用复制管理对象 (RMO) 以编程方式删除项目。</span><span class="sxs-lookup"><span data-stu-id="f161f-122">You can delete articles programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="f161f-123">用于删除项目的 RMO 类取决于该项目所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="f161f-123">The RMO classes you use to delete an article depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-delete-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="f161f-124">删除属于快照发布或事务发布的项目</span><span class="sxs-lookup"><span data-stu-id="f161f-124">To delete an article that belongs to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="f161f-125">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="f161f-125">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="f161f-126">创建的 <xref:Microsoft.SqlServer.Replication.TransArticle> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="f161f-126">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransArticle> class.</span></span>  
  
3.  <span data-ttu-id="f161f-127">设置 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="f161f-127">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="f161f-128">为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置步骤 1 中的连接。</span><span class="sxs-lookup"><span data-stu-id="f161f-128">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="f161f-129">检查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 属性以验证该项目是否存在。</span><span class="sxs-lookup"><span data-stu-id="f161f-129">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the article exists.</span></span> <span data-ttu-id="f161f-130">如果此属性的值为 `false`，则步骤 3 中的项目属性定义不正确或此项目不存在。</span><span class="sxs-lookup"><span data-stu-id="f161f-130">If the value of this property is `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="f161f-131">调用 <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f161f-131">Call the <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> method.</span></span>  
  
7.  <span data-ttu-id="f161f-132">关闭所有连接。</span><span class="sxs-lookup"><span data-stu-id="f161f-132">Close all connections.</span></span>  
  
#### <a name="to-delete-an-article-that-belongs-to-a-merge-publication"></a><span data-ttu-id="f161f-133">删除属于合并发布的项目</span><span class="sxs-lookup"><span data-stu-id="f161f-133">To delete an article that belongs to a merge publication</span></span>  
  
1.  <span data-ttu-id="f161f-134">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="f161f-134">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="f161f-135">创建的 <xref:Microsoft.SqlServer.Replication.MergeArticle> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="f161f-135">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="f161f-136">设置 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="f161f-136">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="f161f-137">为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置步骤 1 中的连接。</span><span class="sxs-lookup"><span data-stu-id="f161f-137">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="f161f-138">检查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 属性以验证该项目是否存在。</span><span class="sxs-lookup"><span data-stu-id="f161f-138">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the article exists.</span></span> <span data-ttu-id="f161f-139">如果此属性的值为 `false`，则步骤 3 中的项目属性定义不正确或此项目不存在。</span><span class="sxs-lookup"><span data-stu-id="f161f-139">If the value of this property is `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="f161f-140">调用 <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f161f-140">Call the <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> method.</span></span>  
  
7.  <span data-ttu-id="f161f-141">关闭所有连接。</span><span class="sxs-lookup"><span data-stu-id="f161f-141">Close all connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f161f-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f161f-142">See Also</span></span>  
 <span data-ttu-id="f161f-143">[向现有发布添加项目和从中删除项目](add-articles-to-and-drop-articles-from-existing-publications.md) </span><span class="sxs-lookup"><span data-stu-id="f161f-143">[Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md) </span></span>  
 [<span data-ttu-id="f161f-144">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="f161f-144">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
