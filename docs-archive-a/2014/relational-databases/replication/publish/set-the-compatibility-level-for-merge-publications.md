---
title: 设置合并发布的兼容级别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], replication
- backward compatibility [SQL Server], replication
- publications [SQL Server replication], backward compatibility
ms.assetid: db47ac73-948b-4d77-b272-bb3565135ea5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04ad80b0c99e7282ff2acfa459a08665efbdee1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591249"
---
# <a name="set-the-compatibility-level-for-merge-publications"></a><span data-ttu-id="85402-102">设置合并发布的兼容级别</span><span class="sxs-lookup"><span data-stu-id="85402-102">Set the Compatibility Level for Merge Publications</span></span>
  <span data-ttu-id="85402-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中设置合并发布的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="85402-103">This topic describes how to set the compatibility level for merge publications in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="85402-104">合并复制使用发布兼容级别来确定给定数据库中的发布可以使用哪些功能。</span><span class="sxs-lookup"><span data-stu-id="85402-104">Merge replication uses the publication compatibility level to determine which features can be used by publications in a given database.</span></span>  
  
 <span data-ttu-id="85402-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="85402-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="85402-106">**设置合并发布的兼容级别，使用：**</span><span class="sxs-lookup"><span data-stu-id="85402-106">**To set the compatibility level for merge publications, using:**</span></span>  
  
     [<span data-ttu-id="85402-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="85402-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="85402-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="85402-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="85402-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="85402-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="85402-110">在新建发布向导的 **“订阅服务器类型”** 页上设置兼容级别。</span><span class="sxs-lookup"><span data-stu-id="85402-110">Set the compatibility level on the **Subscriber Types** page of the New Publication Wizard.</span></span> <span data-ttu-id="85402-111">有关访问本向导的详细信息，请参阅 [Create a Publication](create-a-publication.md)中设置合并发布的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="85402-111">For more information on accessing this wizard, see [Create a Publication](create-a-publication.md).</span></span> <span data-ttu-id="85402-112">创建了发布快照后，可以提高兼容级别但不能降低兼容级别。</span><span class="sxs-lookup"><span data-stu-id="85402-112">After a publication snapshot is created, the compatibility level can be increased but cannot be decreased.</span></span> <span data-ttu-id="85402-113">在“发布属性 - \<Publication>”对话框的“常规”页上提高兼容性级别。</span><span class="sxs-lookup"><span data-stu-id="85402-113">Increase the compatibility level on the **General** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="85402-114">有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="85402-114">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="85402-115">如果要提高发布兼容级别，则运行该兼容级别的早期版本的服务器上的所有现有订阅都将不能同步。</span><span class="sxs-lookup"><span data-stu-id="85402-115">If you increase the publication compatibility level, any existing subscriptions at servers running versions prior to the compatibility level will no longer be able to synchronize.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85402-116">由于兼容级别具有其他发布属性的含义，并且项目属性对这些含义有效。因此，请不要使用同一个对话框更改兼容级别和其他属性。</span><span class="sxs-lookup"><span data-stu-id="85402-116">Because the compatibility level has implications for other publication properties and for which article properties are valid, do not change the compatibility level and other properties in the same use of the dialog box.</span></span> <span data-ttu-id="85402-117">应该在更改属性后重新生成发布的快照。</span><span class="sxs-lookup"><span data-stu-id="85402-117">The snapshot for the publication should be regenerated after the property is changed.</span></span>  
  
#### <a name="to-set-the-publication-compatibility-level"></a><span data-ttu-id="85402-118">设置发布兼容级别</span><span class="sxs-lookup"><span data-stu-id="85402-118">To set the publication compatibility level</span></span>  
  
-   <span data-ttu-id="85402-119">在新建发布向导的 **“订阅服务器类型”** 页上，选择发布应支持的订阅服务器类型。</span><span class="sxs-lookup"><span data-stu-id="85402-119">On the **Subscriber Types** page of the New Publication Wizard, select the types of Subscribers that the publication should support.</span></span>  
  
#### <a name="to-increase-the-publication-compatibility-level"></a><span data-ttu-id="85402-120">提高发布兼容级别</span><span class="sxs-lookup"><span data-stu-id="85402-120">To increase the publication compatibility level</span></span>  
  
-   <span data-ttu-id="85402-121">在“发布属性 - \<Publication>”对话框的“常规”页上，选择**兼容性级别**。</span><span class="sxs-lookup"><span data-stu-id="85402-121">On the **General** page of the **Publication Properties - \<Publication>** dialog box, select for **Compatibility level**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="85402-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="85402-122">Using Transact-SQL</span></span>  
 <span data-ttu-id="85402-123">可以在创建发布时以编程方式设置合并发布的兼容级别，或者以后以编程方式进行修改。</span><span class="sxs-lookup"><span data-stu-id="85402-123">The compatibility level for a merge publication can either be set programmatically when a publication is created or modified programmatically at a later time.</span></span> <span data-ttu-id="85402-124">可使用复制存储过程来设置或更改此发布属性。</span><span class="sxs-lookup"><span data-stu-id="85402-124">You can use replication stored procedures to set or change this publication property.</span></span>  
  
#### <a name="to-set-the-publication-compatibility-level-for-a-merge-publication"></a><span data-ttu-id="85402-125">设置合并发布的发布兼容级别</span><span class="sxs-lookup"><span data-stu-id="85402-125">To set the publication compatibility level for a merge publication</span></span>  
  
1.  <span data-ttu-id="85402-126">在发布服务器上，对[transact-sql&#41;执行 sp_addmergepublication &#40;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)，并为指定一个值， **@publication_compatibility_level** 以使该发布与的早期版本兼容 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="85402-126">At the Publisher, execute [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying a value for **@publication_compatibility_level** to make the publication compatible with older versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="85402-127">有关详细信息，请参阅 [Create a Publication](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="85402-127">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-publication-compatibility-level-of-a-merge-publication"></a><span data-ttu-id="85402-128">更改合并发布的发布兼容级别</span><span class="sxs-lookup"><span data-stu-id="85402-128">To change the publication compatibility level of a merge publication</span></span>  
  
1.  <span data-ttu-id="85402-129">执行[sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)，为指定**publication_compatibility_level** ， **@property** 并为指定相应的发布兼容级别 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="85402-129">Execute [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying **publication_compatibility_level** for **@property** and the appropriate publication compatibility level for **@value**.</span></span>  
  
#### <a name="to-determine-the-publication-compatibility-level-of-a-merge-publication"></a><span data-ttu-id="85402-130">确定合并发布的发布兼容级别</span><span class="sxs-lookup"><span data-stu-id="85402-130">To determine the publication compatibility level of a merge publication</span></span>  
  
1.  <span data-ttu-id="85402-131">执行 [sp_helpmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，并指定所需的发布。</span><span class="sxs-lookup"><span data-stu-id="85402-131">Execute [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying the desired publication.</span></span>  
  
2.  <span data-ttu-id="85402-132">在结果集的 **backward_comp_level** 列中找到发布兼容级别。</span><span class="sxs-lookup"><span data-stu-id="85402-132">Locate the publication compatibility level in the **backward_comp_level** column in the result set.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="85402-133">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="85402-133">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="85402-134">该示例创建合并发布并设置发布兼容级别。</span><span class="sxs-lookup"><span data-stu-id="85402-134">This example creates a merge publication and sets the publication compatibility level.</span></span>  
  
```  
-- To avoid storing the login and password in the script file, the values   
-- are passed into SQLCMD as scripting variables. For information about   
-- how to use scripting variables on the command line and in SQL Server  
-- Management Studio, see the "Executing Replication Scripts" section in  
-- the topic "Programming Replication Using System Stored Procedures".  
  
--Add a new merge publication.  
DECLARE @publicationDB AS sysname;  
DECLARE @publication AS sysname;  
DECLARE @login AS sysname;  
DECLARE @password AS sysname;  
SET @publicationDB = N'AdventureWorks2012';   
SET @publication = N'AdvWorksSalesOrdersMerge'   
SET @login = $(Login);  
SET @password = $(Password);  
  
-- Create a new merge publication.   
USE [AdventureWorks2012]  
EXEC sp_addmergepublication   
@publication = @publication,   
-- Set the compatibility level to SQL Server 2014.  
@publication_compatibility_level = '120RTM';   
  
-- Create the snapshot job for the publication.  
EXEC sp_addpublication_snapshot   
@publication = @publication,  
@job_login = @login,  
@job_password = @password;  
GO  
```  
  
 <span data-ttu-id="85402-135">该示例更改合并发布的发布兼容级别。</span><span class="sxs-lookup"><span data-stu-id="85402-135">This example changes the publication compatibility level for the merge publication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85402-136">如果发布使用任何要求采用特定兼容级别的功能，则可能不允许更改发布兼容级别。</span><span class="sxs-lookup"><span data-stu-id="85402-136">Changing the publication compatibility level might not be allowed if the publication uses any features that require a particular compatibility level.</span></span> <span data-ttu-id="85402-137">有关详细信息，请参阅[复制的向后兼容性](../replication-backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="85402-137">For more information, see [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
  
-- Change the publication compatibility level to   
-- SQL Server 2012.  
EXEC sp_changemergepublication   
@publication = @publication,   
@property = N'publication_compatibility_level',   
@value = N'110RTM';  
GO  
  
```  
  
 <span data-ttu-id="85402-138">该示例返回合并发布的当前发布兼容级别。</span><span class="sxs-lookup"><span data-stu-id="85402-138">This example returns the current publication compatibility level for the merge publication.</span></span>  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
EXEC sp_helpmergepublication   
@publication = @publication;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="85402-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85402-139">See Also</span></span>  
 [<span data-ttu-id="85402-140">创建发布</span><span class="sxs-lookup"><span data-stu-id="85402-140">Create a Publication</span></span>](create-a-publication.md)  
  
  
