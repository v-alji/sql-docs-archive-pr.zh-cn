---
title: 指定目标服务器&#39;s 位置 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], location
ms.assetid: 511ff311-21f5-4f2f-839f-b4deee26ec98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 938528ab78f0f457cde69d8fd4d5432cc14a79b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588804"
---
# <a name="specify-a-target-server39s-location-sql-server-management-studio"></a><span data-ttu-id="3f83e-102">指定目标服务器的位置 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3f83e-102">Specify a Target Server&#39;s Location (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3f83e-103">本主题介绍了如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]的多服务器管理配置中指定目标服务器的位置。</span><span class="sxs-lookup"><span data-stu-id="3f83e-103">This topic describes how to specify the location of a target server in a multiserver administration configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="3f83e-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3f83e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3f83e-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3f83e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3f83e-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3f83e-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3f83e-107">安全性</span><span class="sxs-lookup"><span data-stu-id="3f83e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3f83e-108">**若要指定目标服务器的位置，请使用：**</span><span class="sxs-lookup"><span data-stu-id="3f83e-108">**To specify a target server's location, using:**</span></span>  
  
     [<span data-ttu-id="3f83e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3f83e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3f83e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3f83e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3f83e-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="3f83e-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3f83e-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3f83e-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3f83e-113">执行此操作将编辑注册表。</span><span class="sxs-lookup"><span data-stu-id="3f83e-113">Performing this action edits the registry.</span></span> <span data-ttu-id="3f83e-114">建议不要手动编辑注册表，因为不适当或不正确的更改会导致严重的系统配置问题。</span><span class="sxs-lookup"><span data-stu-id="3f83e-114">Manual editing of the registry is not recommended because inappropriate or incorrect changes can cause serious configuration problems for your system.</span></span> <span data-ttu-id="3f83e-115">因此，只有有经验的用户才可以使用注册表编辑器程序编辑注册表。</span><span class="sxs-lookup"><span data-stu-id="3f83e-115">Therefore, only experienced users should use the Registry Editor program to edit the registry.</span></span> <span data-ttu-id="3f83e-116">有关详细信息，请参阅 Microsoft Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="3f83e-116">For more information, see the Microsoft Windows documentation.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3f83e-117">Security</span><span class="sxs-lookup"><span data-stu-id="3f83e-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3f83e-118">权限</span><span class="sxs-lookup"><span data-stu-id="3f83e-118">Permissions</span></span>  
 <span data-ttu-id="3f83e-119">要求具有 **sysadmin** 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="3f83e-119">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3f83e-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3f83e-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-target-servers-location"></a><span data-ttu-id="3f83e-121">指定目标服务器的位置</span><span class="sxs-lookup"><span data-stu-id="3f83e-121">To specify a target server's location</span></span>  
  
1.  <span data-ttu-id="3f83e-122">在 **“对象资源管理器”** 中，单击加号以展开要指定目标服务器的位置的 master 服务器。</span><span class="sxs-lookup"><span data-stu-id="3f83e-122">In **Object Explorer**, click the plus sign to expand the master server on which you want to specify a target server's location.</span></span>  
  
2.  <span data-ttu-id="3f83e-123">右键单击“SQL Server 代理”\*\*\*\*，指向“多服务器管理”\*\*\*\*，然后选择“管理目标服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3f83e-123">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and select **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="3f83e-124">右键单击某一目标服务器，再选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3f83e-124">Right-click a target server and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="3f83e-125">在 **“位置”** 框中，输入该服务器的位置，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="3f83e-125">In the **Location** box, enter a location for the server, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3f83e-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3f83e-126">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-target-servers-location"></a><span data-ttu-id="3f83e-127">指定目标服务器的位置</span><span class="sxs-lookup"><span data-stu-id="3f83e-127">To specify a target server's location</span></span>  
  
1.  <span data-ttu-id="3f83e-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="3f83e-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3f83e-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="3f83e-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3f83e-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="3f83e-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- enlists the current server into the AdventureWorks1 master server.   
    -- The location for the current server is Building 21, Room 309, Rack 5  
    EXEC dbo.sp_msx_enlist N'AdventureWorks2012',   
        N'Building 21, Room 309, Rack 5' ;  
    GO  
    ```  
  
 <span data-ttu-id="3f83e-131">有关详细信息，请参阅[&#40;transact-sql&#41;sp_msx_enlist ](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3f83e-131">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
  
