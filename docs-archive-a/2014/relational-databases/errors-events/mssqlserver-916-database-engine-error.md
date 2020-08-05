---
title: MSSQLSERVER_916 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 916 (Database Engine error)
ms.assetid: 73eb6581-99fe-49a5-9b42-e239d7ffe27f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ee67c1e2f67c3c7903c67082ec3793d9d9820061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581233"
---
# <a name="mssqlserver_916"></a><span data-ttu-id="93fcf-102">MSSQLSERVER_916</span><span class="sxs-lookup"><span data-stu-id="93fcf-102">MSSQLSERVER_916</span></span>
    
## <a name="details"></a><span data-ttu-id="93fcf-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="93fcf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93fcf-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="93fcf-104">Product Name</span></span>|<span data-ttu-id="93fcf-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="93fcf-105">SQL Server</span></span>|  
|<span data-ttu-id="93fcf-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="93fcf-106">Event ID</span></span>|<span data-ttu-id="93fcf-107">916</span><span class="sxs-lookup"><span data-stu-id="93fcf-107">916</span></span>|  
|<span data-ttu-id="93fcf-108">事件源</span><span class="sxs-lookup"><span data-stu-id="93fcf-108">Event Source</span></span>|<span data-ttu-id="93fcf-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="93fcf-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="93fcf-110">组件</span><span class="sxs-lookup"><span data-stu-id="93fcf-110">Component</span></span>|<span data-ttu-id="93fcf-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="93fcf-111">SQLEngine</span></span>|  
|<span data-ttu-id="93fcf-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="93fcf-112">Symbolic Name</span></span>|<span data-ttu-id="93fcf-113">NOTUSER</span><span class="sxs-lookup"><span data-stu-id="93fcf-113">NOTUSER</span></span>|  
|<span data-ttu-id="93fcf-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="93fcf-114">Message Text</span></span>|<span data-ttu-id="93fcf-115">服务器主体 "%.\*ls" 无法在当前安全上下文下访问数据库 "%.\*ls"。</span><span class="sxs-lookup"><span data-stu-id="93fcf-115">The server principal "%.\*ls" is not able to access the database "%.\*ls" under the current security context.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="93fcf-116">说明</span><span class="sxs-lookup"><span data-stu-id="93fcf-116">Explanation</span></span>  
 <span data-ttu-id="93fcf-117">该登录名没有足够的权限，无法连接到命名的数据库。</span><span class="sxs-lookup"><span data-stu-id="93fcf-117">The login does not have sufficient permissions to connect to the named database.</span></span> <span data-ttu-id="93fcf-118">可以连接到此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例但在数据库中没有特定权限的登录名将获得 guest 用户的权限。</span><span class="sxs-lookup"><span data-stu-id="93fcf-118">Logins that can connect to this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but that do not have specific permissions in a database receive the permissions of the guest user.</span></span> <span data-ttu-id="93fcf-119">这是一项安全举措，为了防止一个数据库中的用户连接到他们没有权限的其他数据库。</span><span class="sxs-lookup"><span data-stu-id="93fcf-119">This is a security measure to prevent users in one database from connecting to other databases where they do not have privileges.</span></span> <span data-ttu-id="93fcf-120">当 guest 用户没有 CONNECT 权限而无法连接到命名数据库并且未设置可信属性时，会出现此错误消息。</span><span class="sxs-lookup"><span data-stu-id="93fcf-120">This error message can occur when the guest user does not have CONNECT permission to the named database and the trustworthy property is not set.</span></span> <span data-ttu-id="93fcf-121">当 guest 用户没有 CONNECT 权限而无法连接到命名数据库时，会出现此错误消息。</span><span class="sxs-lookup"><span data-stu-id="93fcf-121">This error message can occur when the guest user does not have CONNECT permission to the named database.</span></span>  
  
 <span data-ttu-id="93fcf-122">当对 msdb 数据库的 CONNECT 权限被拒绝或撤消时，如果对象资源管理器尝试显示每个数据库的“基于策略的管理”状态，则 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 可能收到此错误。</span><span class="sxs-lookup"><span data-stu-id="93fcf-122">When CONNECT permission to the msdb database is denied or revoked, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can receive this error when Object Explorer tries to show the Policy Based Management status of each database.</span></span> <span data-ttu-id="93fcf-123">对象资源管理器使用当前登录名的权限查询 msdb 数据库以获取此信息，这会导致错误。</span><span class="sxs-lookup"><span data-stu-id="93fcf-123">Object Explorer uses the permissions of the current login to query the msdb database for this information, which causes the error.</span></span> <span data-ttu-id="93fcf-124">还会出现以下错误信息：</span><span class="sxs-lookup"><span data-stu-id="93fcf-124">The following error message also occurs:</span></span>  
  
 <span data-ttu-id="93fcf-125">无法为此请求检索数据。</span><span class="sxs-lookup"><span data-stu-id="93fcf-125">Failed to retrieve data for this request.</span></span> <span data-ttu-id="93fcf-126">(Microsoft.SqlServer.Management.Sdk.Sfc)</span><span class="sxs-lookup"><span data-stu-id="93fcf-126">(Microsoft.SqlServer.Management.Sdk.Sfc)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="93fcf-127">用户操作</span><span class="sxs-lookup"><span data-stu-id="93fcf-127">User Action</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="93fcf-128">在采取此安全措施前，请确保您明确理解用户是在不同的数据库中验证身份的。</span><span class="sxs-lookup"><span data-stu-id="93fcf-128">Before circumventing this security measure be sure to have a clear understanding of users are authenticated in various databases.</span></span> <span data-ttu-id="93fcf-129">下面的方法可能会允许在一个数据库中具有权限的用户连接到其他数据库，这可能会向恶意用户公开数据。</span><span class="sxs-lookup"><span data-stu-id="93fcf-129">The following methods may allow users that have permissions in one database to connect to other databases which could expose data to a malicious user.</span></span> <span data-ttu-id="93fcf-130">在启用包含数据库后，以下步骤将允许一个数据库中的数据库所有者授予对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的其他数据库的访问权限。</span><span class="sxs-lookup"><span data-stu-id="93fcf-130">When contained databases are enabled, the following steps can allow database owners in one database to grant access to other database on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="93fcf-131">可以按以下方式之一连接到数据库：</span><span class="sxs-lookup"><span data-stu-id="93fcf-131">You can connect to the database in one of the following ways:</span></span>  
  
-   <span data-ttu-id="93fcf-132">向特定登录名授予针对命名数据库的访问权限。</span><span class="sxs-lookup"><span data-stu-id="93fcf-132">Grant the specific login access to the named database.</span></span> <span data-ttu-id="93fcf-133">下面的示例向登录名 `Adventure-Works\Larry` 授予针对 `msdb` 数据库的访问权限。</span><span class="sxs-lookup"><span data-stu-id="93fcf-133">The following example grants the login `Adventure-Works\Larry` access to the `msdb` database.</span></span>  
  
     <span data-ttu-id="93fcf-134">USE msdb ;</span><span class="sxs-lookup"><span data-stu-id="93fcf-134">USE msdb ;</span></span>  
  
     <span data-ttu-id="93fcf-135">GO</span><span class="sxs-lookup"><span data-stu-id="93fcf-135">GO</span></span>  
  
     <span data-ttu-id="93fcf-136">GRANT CONNECT TO [Adventure-Works\Larry] ;</span><span class="sxs-lookup"><span data-stu-id="93fcf-136">GRANT CONNECT TO [Adventure-Works\Larry] ;</span></span>  
  
-   <span data-ttu-id="93fcf-137">向 guest 用户授予针对在错误消息中指定的数据库的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="93fcf-137">Grant the CONNECT permission to the database named in the error message for the guest user.</span></span> <span data-ttu-id="93fcf-138">以下示例授予用户 `CONNECT` 对 `msdb` 数据库的 `guest` 权限。</span><span class="sxs-lookup"><span data-stu-id="93fcf-138">The following example grants the `CONNECT` permission to the `msdb` database for the user `guest`.</span></span>  
  
     <span data-ttu-id="93fcf-139">USE msdb ;</span><span class="sxs-lookup"><span data-stu-id="93fcf-139">USE msdb ;</span></span>  
  
     <span data-ttu-id="93fcf-140">GO</span><span class="sxs-lookup"><span data-stu-id="93fcf-140">GO</span></span>  
  
     <span data-ttu-id="93fcf-141">GRANT CONNECT TO guest ;</span><span class="sxs-lookup"><span data-stu-id="93fcf-141">GRANT CONNECT TO guest ;</span></span>  
  
-   <span data-ttu-id="93fcf-142">在验证了用户身份的数据库上启用 TRUSTWORTHY 属性。</span><span class="sxs-lookup"><span data-stu-id="93fcf-142">Enable the TRUSTWORTHY property on the database that has authenticated the user.</span></span>  
  
     `ALTER DATABASE AdventureWorks SET TRUSTWORTHY ON;`  
  
  
