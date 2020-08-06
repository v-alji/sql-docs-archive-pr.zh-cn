---
title: System_function_schema 中不允许使用用户定义的函数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7242f9fda74288a2b7354ac0550ff4966e05c555
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694218"
---
# <a name="user-defined-functions-are-not-allowed-in-system_function_schema"></a><span data-ttu-id="c7b90-102">system_function_schema 中不允许使用用户定义函数</span><span class="sxs-lookup"><span data-stu-id="c7b90-102">User-defined functions are not allowed in system_function_schema</span></span>
  <span data-ttu-id="c7b90-103">升级顾问检测到由未记录的用户**system_function_schema**拥有的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="c7b90-103">The Upgrade Advisor detected user-defined functions that are owned by the undocumented user **system_function_schema**.</span></span> <span data-ttu-id="c7b90-104">不能通过指定此用户创建用户定义的系统功能。</span><span class="sxs-lookup"><span data-stu-id="c7b90-104">You cannot create a user-defined system function by specifying this user.</span></span> <span data-ttu-id="c7b90-105">**System_function_schema**用户名不存在，并且与此名称关联的用户 ID (UID = 4) 保留用于**sys**架构，且仅限内部使用。</span><span class="sxs-lookup"><span data-stu-id="c7b90-105">The **system_function_schema** user name does not exist, and the user ID that is associated with this name (UID = 4) is reserved for the **sys** schema and is restricted to internal use only.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c7b90-106">组件</span><span class="sxs-lookup"><span data-stu-id="c7b90-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c7b90-107">说明</span><span class="sxs-lookup"><span data-stu-id="c7b90-107">Description</span></span>  
 <span data-ttu-id="c7b90-108">系统对象存储和访问都已更改为以下方式：</span><span class="sxs-lookup"><span data-stu-id="c7b90-108">System object storage and access has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="c7b90-109">系统对象存储在只读**资源**数据库中，不允许直接更新系统对象。</span><span class="sxs-lookup"><span data-stu-id="c7b90-109">System objects are stored in the read-only **Resource** database, and direct system object updates are not permitted.</span></span>  
  
     <span data-ttu-id="c7b90-110">系统对象在逻辑上出现在每个数据库的**sys**架构中。</span><span class="sxs-lookup"><span data-stu-id="c7b90-110">System objects logically appear in the **sys** schema of every database.</span></span> <span data-ttu-id="c7b90-111">这样便保留了通过指定由单个部分组成的函数名称来从任何数据库调用系统函数的能力。</span><span class="sxs-lookup"><span data-stu-id="c7b90-111">This maintains the ability to invoke system functions from any database by specifying a one-part function name.</span></span> <span data-ttu-id="c7b90-112">例如，语句 `SELECT * FROM fn_helpcollations()` 可以从任何数据库运行。</span><span class="sxs-lookup"><span data-stu-id="c7b90-112">For example, the statement `SELECT * FROM fn_helpcollations()` can be run from any database.</span></span>  
  
-   <span data-ttu-id="c7b90-113">已删除未记录的用户**system_function_schema** 。</span><span class="sxs-lookup"><span data-stu-id="c7b90-113">The undocumented user **system_function_schema** has been removed.</span></span>  
  
-   <span data-ttu-id="c7b90-114">与**system_function_schema** (UID = 4) 关联的用户 ID 为**sys**架构保留，并且仅限内部使用。</span><span class="sxs-lookup"><span data-stu-id="c7b90-114">The user ID associated with **system_function_schema** (UID = 4) is reserved for the **sys** schema and is restricted to internal use only.</span></span>  
  
 <span data-ttu-id="c7b90-115">这些更改将对用户定义系统函数具有下列影响：</span><span class="sxs-lookup"><span data-stu-id="c7b90-115">These changes have the following effect on user-defined system functions:</span></span>  
  
-   <span data-ttu-id="c7b90-116">引用**system_function_schema** (DDL) 语句的数据定义语言将失败。</span><span class="sxs-lookup"><span data-stu-id="c7b90-116">Data Definition Language (DDL) statements that reference **system_function_schema** will fail.</span></span> <span data-ttu-id="c7b90-117">例如，语句 `CREATE FUNCTION system` _ `function` \_ `schema.fn` \_ `MySystemFunction` .。。不会成功。</span><span class="sxs-lookup"><span data-stu-id="c7b90-117">For example, the statement `CREATE FUNCTION system`_`function`\_`schema.fn`\_`MySystemFunction` ... will not succeed.</span></span>  
  
-   <span data-ttu-id="c7b90-118">升级到后 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ， **system_function_schema**拥有的现有对象仅包含在**master**数据库的**sys**架构中。</span><span class="sxs-lookup"><span data-stu-id="c7b90-118">After you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], existing objects that are owned by **system_function_schema** are contained only in the **sys** schema of the **master** database.</span></span> <span data-ttu-id="c7b90-119">由于无法修改系统对象，因此永远无法更改这些函数或将其从**master**数据库中删除。</span><span class="sxs-lookup"><span data-stu-id="c7b90-119">Because system objects cannot be modified, these functions can never be changed or dropped from the **master** database.</span></span> <span data-ttu-id="c7b90-120">另外，不能通过仅指定由单个部分组成的函数名称来从其他数据库中调用这些函数。</span><span class="sxs-lookup"><span data-stu-id="c7b90-120">Additionally, these functions cannot be invoked from other databases by specifying only a one-part function name.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c7b90-121">纠正措施</span><span class="sxs-lookup"><span data-stu-id="c7b90-121">Corrective Action</span></span>  
 <span data-ttu-id="c7b90-122">在升级之前，请完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="c7b90-122">Before you upgrade , complete the following tasks:</span></span>  
  
1.  <span data-ttu-id="c7b90-123">使用**sp_changeobjectowner**系统存储过程将现有用户定义函数的所有权更改为**dbo** 。</span><span class="sxs-lookup"><span data-stu-id="c7b90-123">Change the ownership of existing user-defined functions to **dbo** by using the **sp_changeobjectowner** system stored procedure.</span></span>  
  
2.  <span data-ttu-id="c7b90-124">考虑重命名函数，使其不使用前缀“fn_”。</span><span class="sxs-lookup"><span data-stu-id="c7b90-124">Consider renaming the function so that is does not use the prefix 'fn_'.</span></span> <span data-ttu-id="c7b90-125">这样会避免与当前或未来的系统函数发生潜在名称冲突。</span><span class="sxs-lookup"><span data-stu-id="c7b90-125">This will avoid potential name conflicts with current or future system functions.</span></span>  
  
3.  <span data-ttu-id="c7b90-126">将修改后的函数的副本添加到使用这些函数的每个数据库中。</span><span class="sxs-lookup"><span data-stu-id="c7b90-126">Add a copy of the modified functions in every database that uses them.</span></span>  
  
4.  <span data-ttu-id="c7b90-127">在包含用户定义函数 DDL 语句的所有脚本中，用**dbo**替换对**system_function_schema**的引用。</span><span class="sxs-lookup"><span data-stu-id="c7b90-127">Replace references to **system_function_schema** with **dbo** in all scripts that contain user-defined function DDL statements.</span></span>  
  
5.  <span data-ttu-id="c7b90-128">修改调用这些函数的脚本，以使用由两部分组成的名称 dbo **。**_function_name_或由三部分组成的名称_database_name_**。** 供.*function_name*。</span><span class="sxs-lookup"><span data-stu-id="c7b90-128">Modify scripts that invoke these functions to use either the two-part name dbo **.**_function_name_, or the three-part name _database_name_**.** dbo.*function_name*.</span></span>  
  
 <span data-ttu-id="c7b90-129">有关详细信息，请参阅 SQL Server 联机丛书的下列主题：</span><span class="sxs-lookup"><span data-stu-id="c7b90-129">For more information, see the following topics in SQL Server Books Online:</span></span>  
  
-   <span data-ttu-id="c7b90-130">“sp_changeobjectowner”</span><span class="sxs-lookup"><span data-stu-id="c7b90-130">"sp_changeobjectowner"</span></span>  
  
-   <span data-ttu-id="c7b90-131">“用户架构分离”</span><span class="sxs-lookup"><span data-stu-id="c7b90-131">"User-schema Separation"</span></span>  
  
-   <span data-ttu-id="c7b90-132">“Resource 数据库”</span><span class="sxs-lookup"><span data-stu-id="c7b90-132">"Resource Database"</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b90-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7b90-133">See Also</span></span>  
 <span data-ttu-id="c7b90-134">[SQL Server 2014 升级顾问 &#91;新&#93;](sql-server-2014-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="c7b90-134">[SQL Server 2014 Upgrade Advisor &#91;new&#93;](sql-server-2014-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="c7b90-135">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c7b90-135">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 <span data-ttu-id="c7b90-136">[删除修改系统对象的语句](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md) </span><span class="sxs-lookup"><span data-stu-id="c7b90-136">[Remove statements that modify system objects](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md) </span></span>  
 [<span data-ttu-id="c7b90-137">删除用于删除系统对象的语句</span><span class="sxs-lookup"><span data-stu-id="c7b90-137">Remove statements that drop system objects</span></span>](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
