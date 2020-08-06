---
title: 复制架构更改 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bec2f363cd8c4f7dea45935568a88722b19323fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587350"
---
# <a name="replicate-schema-changes"></a><span data-ttu-id="b3365-102">复制架构更改</span><span class="sxs-lookup"><span data-stu-id="b3365-102">Replicate Schema Changes</span></span>
  <span data-ttu-id="b3365-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中复制架构更改。</span><span class="sxs-lookup"><span data-stu-id="b3365-103">This topic describes how to replicate schema changes in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b3365-104">如果对发布的项目进行以下架构更改，则会默认将其传播到 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器：</span><span class="sxs-lookup"><span data-stu-id="b3365-104">If you make the following schema changes to a published article, they are propagated, by default, to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="b3365-105">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="b3365-105">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="b3365-106">ALTER VIEW</span><span class="sxs-lookup"><span data-stu-id="b3365-106">ALTER VIEW</span></span>  
  
-   <span data-ttu-id="b3365-107">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="b3365-107">ALTER PROCEDURE</span></span>  
  
-   <span data-ttu-id="b3365-108">ALTER FUNCTION</span><span class="sxs-lookup"><span data-stu-id="b3365-108">ALTER FUNCTION</span></span>  
  
-   <span data-ttu-id="b3365-109">ALTER TRIGGER</span><span class="sxs-lookup"><span data-stu-id="b3365-109">ALTER TRIGGER</span></span>  
  
 <span data-ttu-id="b3365-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b3365-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b3365-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b3365-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b3365-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b3365-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="b3365-113">**复制架构更改，使用：**</span><span class="sxs-lookup"><span data-stu-id="b3365-113">**To replicate schema changes, using:**</span></span>  
  
     [<span data-ttu-id="b3365-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b3365-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b3365-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b3365-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b3365-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="b3365-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b3365-117">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b3365-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b3365-118">ALTER TABLE …DROP COLUMN 语句将始终复制到所有其订阅包含要被删除的列的订阅服务器，即使禁用对架构更改的复制也是如此。</span><span class="sxs-lookup"><span data-stu-id="b3365-118">The ALTER TABLE ... DROP COLUMN statement is always replicated to all Subscribers whose subscription contains the columns being dropped, even if you disable the replication of schema changes.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b3365-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b3365-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b3365-120">如果不想复制发布的架构更改，请在“发布属性 - \<Publication>”对话框中禁用对架构更改的复制。</span><span class="sxs-lookup"><span data-stu-id="b3365-120">If you do not want to replicate schema changes for a publication, disable the replication of schema changes in the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="b3365-121">有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b3365-121">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-disable-replication-of-schema-changes"></a><span data-ttu-id="b3365-122">禁用对架构更改的复制</span><span class="sxs-lookup"><span data-stu-id="b3365-122">To disable replication of schema changes</span></span>  
  
1.  <span data-ttu-id="b3365-123">在“发布属性 - \<Publication>”对话框的“订阅选项”页面上，将“复制架构更改”属性的值设置为 False   。</span><span class="sxs-lookup"><span data-stu-id="b3365-123">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, set the value of the **Replicate schema changes** property to **False**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="b3365-124">若要仅传播特定的架构更改，请在架构更改前将此属性设置为 **True** ，然后在更改后将其设置为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="b3365-124">To propagate only specific schema changes, set the property to **True** before a schema change, and then set it to **False** after the change is made.</span></span> <span data-ttu-id="b3365-125">相反，若要传播大多数架构更改，而不是一个给定更改，请在架构更改前将此属性设置为 **“False”** ，然后在更改后将其设置为 **“True”** 。</span><span class="sxs-lookup"><span data-stu-id="b3365-125">Conversely, to propagate most schema changes, but not a given change, set the property to **False** before the schema change, and then set it to **True** after the change is made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b3365-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b3365-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="b3365-127">可以使用复制存储过程来指定是否复制这些架构更改。</span><span class="sxs-lookup"><span data-stu-id="b3365-127">You can use replication stored procedures to specify whether these schema changes are replicated.</span></span> <span data-ttu-id="b3365-128">您使用的存储过程取决于发布的类型。</span><span class="sxs-lookup"><span data-stu-id="b3365-128">The stored procedure that you use depends on the type of publication.</span></span>  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a><span data-ttu-id="b3365-129">创建不复制架构更改的快照发布或事务发布</span><span class="sxs-lookup"><span data-stu-id="b3365-129">To create a snapshot or transactional publication that does not replicate schema changes</span></span>  
  
1.  <span data-ttu-id="b3365-130">在发布服务器上，对发布数据库执行[sp_addpublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)，并为\*\* \@ replicate_ddl**指定值**0\*\* 。</span><span class="sxs-lookup"><span data-stu-id="b3365-130">At the Publisher on the publication database, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), specifying a value of **0** for **\@replicate_ddl**.</span></span> <span data-ttu-id="b3365-131">有关详细信息，请参阅 [Create a Publication](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="b3365-131">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a><span data-ttu-id="b3365-132">创建不复制架构更改的合并发布</span><span class="sxs-lookup"><span data-stu-id="b3365-132">To create a merge publication that does not replicate schema changes</span></span>  
  
1.  <span data-ttu-id="b3365-133">在发布服务器上，对发布数据库执行[sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)，并为\*\* \@ replicate_ddl**指定值**0\*\* 。</span><span class="sxs-lookup"><span data-stu-id="b3365-133">At the Publisher on the publication database, execute [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying a value of **0** for **\@replicate_ddl**.</span></span> <span data-ttu-id="b3365-134">有关详细信息，请参阅 [Create a Publication](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="b3365-134">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="b3365-135">为快照发布或事务发布暂时禁用复制架构更改</span><span class="sxs-lookup"><span data-stu-id="b3365-135">To temporarily disable replicating schema changes for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="b3365-136">对于包含架构更改复制的发布，请执行[sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)，并为 " \*\* \@ 属性**" 指定值 " **replicate_ddl** "，将 "值" 的值指定为 " **0** \*\* \@ "。**</span><span class="sxs-lookup"><span data-stu-id="b3365-136">For a publication with replication of schema changes, execute [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **0** for **\@value**.</span></span>  
  
2.  <span data-ttu-id="b3365-137">对已发布对象执行 DDL 命令。</span><span class="sxs-lookup"><span data-stu-id="b3365-137">Execute the DDL command on the published object.</span></span>  
  
3.  <span data-ttu-id="b3365-138"> (可选) 通过执行[sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)来重新启用复制架构更改，将属性**的值**指定为 "\ \** \@ 属性**"，将值** \@ 指定为 \"\** **1** "。</span><span class="sxs-lookup"><span data-stu-id="b3365-138">(Optional) Re-enable replicating schema changes by executing [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **1** for **\@value**.</span></span>  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a><span data-ttu-id="b3365-139">为合并发布暂时禁用复制架构更改</span><span class="sxs-lookup"><span data-stu-id="b3365-139">To temporarily disable replicating schema changes for a merge publication</span></span>  
  
1.  <span data-ttu-id="b3365-140">对于包含架构更改复制的发布，请执行[sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)，并为 " \*\* \@ 属性**" 指定值 " **replicate_ddl** "，将 "值" 的值指定为 " **0** \*\* \@ "。**</span><span class="sxs-lookup"><span data-stu-id="b3365-140">For a publication with replication of schema changes, execute [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **0** for **\@value**.</span></span>  
  
2.  <span data-ttu-id="b3365-141">对已发布对象执行 DDL 命令。</span><span class="sxs-lookup"><span data-stu-id="b3365-141">Execute the DDL command on the published object.</span></span>  
  
3.  <span data-ttu-id="b3365-142"> (可选) 通过执行[sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)来重新启用复制架构更改，将属性**的值**指定为 "\ \** \@ 属性**"，将值** \@ 指定为 \"\** **1** "。</span><span class="sxs-lookup"><span data-stu-id="b3365-142">(Optional) Re-enable replicating schema changes by executing [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **1** for **\@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3365-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3365-143">See Also</span></span>  
 <span data-ttu-id="b3365-144">[对发布数据库进行架构更改](make-schema-changes-on-publication-databases.md) </span><span class="sxs-lookup"><span data-stu-id="b3365-144">[Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md) </span></span>  
 [<span data-ttu-id="b3365-145">对发布数据库进行架构更改</span><span class="sxs-lookup"><span data-stu-id="b3365-145">Make Schema Changes on Publication Databases</span></span>](make-schema-changes-on-publication-databases.md)  
  
  
