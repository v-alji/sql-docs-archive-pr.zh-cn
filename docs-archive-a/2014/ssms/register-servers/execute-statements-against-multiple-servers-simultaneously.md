---
title: 同时对多个服务器执行语句
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- executing queries against multiple servers
- queries [SQL Server], multiserver
ms.assetid: 197760f3-0a06-43de-8162-69c27d3fbe56
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b94775029a1501d3e894d84ef4a027fc1595dc10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690292"
---
# <a name="execute-statements-against-multiple-servers-simultaneously-sql-server-management-studio"></a><span data-ttu-id="d092b-102">Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d092b-102">Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)</span></span>
  <span data-ttu-id="d092b-103">本主题说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，通过以下方法同时查询多个服务器：创建一个本地服务器组，或者创建一个中央管理服务器以及一个或多个服务器组，在这些组中创建一个或多个已注册的服务器，然后查询整个组。</span><span class="sxs-lookup"><span data-stu-id="d092b-103">This topic describes how to query multiple servers at the same time in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by creating a local server group, or a Central Management Server and one or more server groups, and one or more registered servers within the groups, and then querying the complete group.</span></span> <span data-ttu-id="d092b-104">可以将查询返回的结果合并到单个结果窗格中，也可以在单独结果窗格中返回这些结果。</span><span class="sxs-lookup"><span data-stu-id="d092b-104">The results that are returned by the query can be combined into a single results pane, or can be returned in separate results panes.</span></span> <span data-ttu-id="d092b-105">结果集可能包含额外的列，即每个服务器上的查询所使用的服务器名和登录名。</span><span class="sxs-lookup"><span data-stu-id="d092b-105">The results set can include additional columns for the server name and the login that is used by the query on each server.</span></span> <span data-ttu-id="d092b-106">只能使用 Windows 身份验证来注册中央管理服务器和从属服务器。</span><span class="sxs-lookup"><span data-stu-id="d092b-106">Central Management Servers and subordinate servers can be registered by using only Windows Authentication.</span></span> <span data-ttu-id="d092b-107">可以使用 Windows 身份验证或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证来注册本地服务器组中的服务器。</span><span class="sxs-lookup"><span data-stu-id="d092b-107">Servers in local server groups can be registered by using Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d092b-108">在执行以下过程之前，请先创建中央管理服务器和服务器组。</span><span class="sxs-lookup"><span data-stu-id="d092b-108">Before you execute the following procedures, create a Central Management Server and server groups.</span></span> <span data-ttu-id="d092b-109">有关详细信息，请参阅[创建中央管理服务器和服务器组 (SQL Server Management Studio)](create-a-central-management-server-and-server-group.md)。</span><span class="sxs-lookup"><span data-stu-id="d092b-109">For more information, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md).</span></span>  
  
 <span data-ttu-id="d092b-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d092b-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d092b-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d092b-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d092b-112">安全性</span><span class="sxs-lookup"><span data-stu-id="d092b-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d092b-113">**若要对多个服务器执行语句，请使用：**</span><span class="sxs-lookup"><span data-stu-id="d092b-113">**To execute statements against multiple servers, using:**</span></span>  
  
     [<span data-ttu-id="d092b-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d092b-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d092b-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="d092b-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d092b-116">Security</span><span class="sxs-lookup"><span data-stu-id="d092b-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d092b-117">权限</span><span class="sxs-lookup"><span data-stu-id="d092b-117">Permissions</span></span>  
 <span data-ttu-id="d092b-118">由于中央管理服务器维护的连接是在用户的上下文中通过使用 Windows 身份验证执行的，因此它们在各个已注册的服务器上的有效权限可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="d092b-118">Because the connections maintained by a Central Management Server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary.</span></span> <span data-ttu-id="d092b-119">例如，用户可能是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A 实例上 sysadmin 固定服务器角色的成员，但仅具有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B 实例的有限权限。</span><span class="sxs-lookup"><span data-stu-id="d092b-119">For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d092b-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d092b-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-execute-statements-against-multiple-configuration-targets-simultaneously"></a><span data-ttu-id="d092b-121">同时对多个配置目标执行语句</span><span class="sxs-lookup"><span data-stu-id="d092b-121">To execute statements against multiple configuration targets simultaneously</span></span>  
  
1.  <span data-ttu-id="d092b-122">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 **“视图”** 菜单上，单击 **“已注册的服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="d092b-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="d092b-123">展开一个中央管理服务器，右键单击某个服务器组，指向“连接”\*\*\*\*，然后单击“新建查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d092b-123">Expand a Central Management Server, right-click a server group, point to **Connect**, and then click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d092b-124">在查询编辑器中，键入并执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，例如：</span><span class="sxs-lookup"><span data-stu-id="d092b-124">In Query Editor, type and execute a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, such as the following:</span></span>  
  
    ```  
    USE master  
    GO  
    SELECT * FROM sysdatabases;  
    GO  
    ```  
  
     <span data-ttu-id="d092b-125">默认情况下，结果窗格合并来自服务器组中所有服务器的查询结果。</span><span class="sxs-lookup"><span data-stu-id="d092b-125">By default, the results pane will combine the query results from all the servers in the server group.</span></span>  
  
#### <a name="to-change-the-multiserver-results-options"></a><span data-ttu-id="d092b-126">更改多服务器结果选项</span><span class="sxs-lookup"><span data-stu-id="d092b-126">To change the multiserver results options</span></span>  
  
1.  <span data-ttu-id="d092b-127">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的 **“工具”** 菜单中，单击 **“选项”**。</span><span class="sxs-lookup"><span data-stu-id="d092b-127">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="d092b-128">依次展开 **“查询结果”** 和 **“SQL Server”**，然后单击 **“多服务器结果”**。</span><span class="sxs-lookup"><span data-stu-id="d092b-128">Expand **Query Results**, expand **SQL Server**, and then click **Multiserver Results**.</span></span>  
  
3.  <span data-ttu-id="d092b-129">在 **“多服务器结果”** 页上，指定所需的选项设置，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="d092b-129">On the **Multiserver Results** page, specify the option settings that you want, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d092b-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d092b-130">See Also</span></span>  
 [<span data-ttu-id="d092b-131">使用中央管理服务器管理多台服务器</span><span class="sxs-lookup"><span data-stu-id="d092b-131">Administer Multiple Servers Using Central Management Servers</span></span>](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
