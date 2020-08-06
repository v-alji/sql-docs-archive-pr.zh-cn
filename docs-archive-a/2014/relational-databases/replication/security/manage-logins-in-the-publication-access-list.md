---
title: 管理发布访问列表中的登录名 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- logins [SQL Server replication], managing
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b96e6f46403cf3a482f00a3f5155527177920967
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580115"
---
# <a name="manage-logins-in-the-publication-access-list"></a><span data-ttu-id="40304-102">管理发布访问列表中的登录名</span><span class="sxs-lookup"><span data-stu-id="40304-102">Manage Logins in the Publication Access List</span></span>
  <span data-ttu-id="40304-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中管理发布访问列表中的登录名。</span><span class="sxs-lookup"><span data-stu-id="40304-103">This topic describes how to manage logins in the Publication Access List in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="40304-104">对发布的访问是由发布访问列表 (PAL) 控制的。</span><span class="sxs-lookup"><span data-stu-id="40304-104">Access to a publication is controlled by the publication access list (PAL).</span></span> <span data-ttu-id="40304-105">可以在 PAL 中添加和删除登录名和组。</span><span class="sxs-lookup"><span data-stu-id="40304-105">Logins and groups can be added and removed from the PAL.</span></span>  
  
 <span data-ttu-id="40304-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="40304-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="40304-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="40304-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="40304-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="40304-108">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="40304-109">**管理发布访问列表中的登录名，使用：**</span><span class="sxs-lookup"><span data-stu-id="40304-109">**To manage logins in the Publication Access List, using:**</span></span>  
  
     [<span data-ttu-id="40304-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="40304-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="40304-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="40304-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="40304-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="40304-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="40304-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="40304-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="40304-114">在将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名添加到 PAL 前，必须将该登录名与发布数据库中的数据库用户关联。</span><span class="sxs-lookup"><span data-stu-id="40304-114">You must associate the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login with a database user in the publication database before you add the login to the PAL.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="40304-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="40304-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="40304-116">可使用“发布属性 - \<Publication>”对话框的“发布访问列表”页面上的发布访问列表 (PAL) 来管理登录名 。</span><span class="sxs-lookup"><span data-stu-id="40304-116">You use the publication access list (PAL) on the **Publication Access List** page of the **Publication Properties - \<Publication>** dialog box to manage logins.</span></span> <span data-ttu-id="40304-117">有关如何访问此对话框的详细信息，请参阅[查看和修改发布属性](../publish/view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="40304-117">For more information about how to access this dialog box, see [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-manage-logins-in-the-pal"></a><span data-ttu-id="40304-118">管理 PAL 中的登录名</span><span class="sxs-lookup"><span data-stu-id="40304-118">To manage logins in the PAL</span></span>  
  
1.  <span data-ttu-id="40304-119">在“发布属性 - \<Publication>”对话框的“发布访问列表”页面上，使用“添加”、“删除”和“全部删除”按钮在 PAL 中添加和删除登录名和组    。</span><span class="sxs-lookup"><span data-stu-id="40304-119">On the **Publication Access List** page of the **Publication Properties - \<Publication>** dialog box, use the **Add**, **Remove**, and **Remove All** buttons to add and remove logins and groups from the PAL.</span></span> <span data-ttu-id="40304-120">不要从 PAL 中删除 **distributor_admin** 。</span><span class="sxs-lookup"><span data-stu-id="40304-120">Do not remove **distributor_admin** from the PAL.</span></span> <span data-ttu-id="40304-121">复制将使用此帐户。</span><span class="sxs-lookup"><span data-stu-id="40304-121">This account is used by replication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="40304-122">如果使用远程分发服务器，则 PAL 中的帐户必须在发布服务器和分发服务器中都可用。</span><span class="sxs-lookup"><span data-stu-id="40304-122">If a remote Distributor is used, accounts in the PAL must be available at both the Publisher and the Distributor.</span></span> <span data-ttu-id="40304-123">帐户必须是在这两个服务器中定义的域帐户或本地帐户。</span><span class="sxs-lookup"><span data-stu-id="40304-123">The account must be either a domain account or a local account that is defined at both servers.</span></span> <span data-ttu-id="40304-124">与这两个登录名关联的密码必须相同。</span><span class="sxs-lookup"><span data-stu-id="40304-124">The passwords that are associated with both logins must be the same.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="40304-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="40304-125">Using Transact-SQL</span></span>  
  
#### <a name="to-view-groups-and-logins-that-belong-to-the-pal"></a><span data-ttu-id="40304-126">查看属于 PAL 的组和登录名</span><span class="sxs-lookup"><span data-stu-id="40304-126">To view groups and logins that belong to the PAL</span></span>  
  
1.  <span data-ttu-id="40304-127">在发布服务器上，对发布数据库执行 [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="40304-127">At the Publisher on the publication database, execute [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql).</span></span> <span data-ttu-id="40304-128">对于 " \*\* \@ 发布\*\*"，请指定发布名称。</span><span class="sxs-lookup"><span data-stu-id="40304-128">For **\@publication**, specify the publication name.</span></span> <span data-ttu-id="40304-129">这将显示有关 PAL 中组和登录名的信息。</span><span class="sxs-lookup"><span data-stu-id="40304-129">This displays information about the groups and logins in the PAL.</span></span>  
  
#### <a name="to-add-groups-and-logins-to-the-pal"></a><span data-ttu-id="40304-130">将组和登录名添加到 PAL</span><span class="sxs-lookup"><span data-stu-id="40304-130">To add groups and logins to the PAL</span></span>  
  
1.  <span data-ttu-id="40304-131">在发布服务器上，对发布数据库执行 [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="40304-131">At the Publisher on the publication database, execute [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql).</span></span> <span data-ttu-id="40304-132">对于 " \*\* \@ 发布**"，指定发布名称; 对于 " \*\* \@ 登录**名"，指定要添加的登录名或组名。</span><span class="sxs-lookup"><span data-stu-id="40304-132">For **\@publication**, specify the publication name; and for **\@login**, specify the name of the login or group that is being added.</span></span>  
  
#### <a name="to-remove-groups-and-logins-from-the-pal"></a><span data-ttu-id="40304-133">从 PAL 删除组和登录名</span><span class="sxs-lookup"><span data-stu-id="40304-133">To remove groups and logins from the PAL</span></span>  
  
1.  <span data-ttu-id="40304-134">在发布服务器上，对发布数据库执行 [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="40304-134">At the Publisher on the publication database, execute [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql).</span></span> <span data-ttu-id="40304-135">对于 " \*\* \@ 发布**"，指定发布名称; 对于 " \*\* \@ 登录**名"，指定要删除的登录名或组名。</span><span class="sxs-lookup"><span data-stu-id="40304-135">For **\@publication**, specify the publication name; and for **\@login**, specify the name of the login or group that is being removed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40304-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40304-136">See Also</span></span>  
 <span data-ttu-id="40304-137">[复制代理安全模式](replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="40304-137">[Replication Agent Security Model](replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="40304-138">[保护复制拓扑](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="40304-138">[Secure a Replication Topology](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="40304-139">保护发布服务器</span><span class="sxs-lookup"><span data-stu-id="40304-139">Secure the Publisher</span></span>](secure-the-publisher.md)  
  
  
