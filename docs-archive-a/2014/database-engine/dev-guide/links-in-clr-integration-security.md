---
title: CLR 集成安全性中的链接 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-access links [CLR integration]
- security [CLR integration]
- invocation links [CLR integration]
- gated links [CLR integration]
ms.assetid: 168efd01-d12e-4bdf-a1b3-0b5c76474eaf
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 52a4f8084a8a90384c8916f2219faaf2c138b11c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694083"
---
# <a name="links-in-clr-integration-security"></a><span data-ttu-id="25ebf-102">CLR 集成安全性中的链接</span><span class="sxs-lookup"><span data-stu-id="25ebf-102">Links in CLR Integration Security</span></span>
  <span data-ttu-id="25ebf-103">本节介绍使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或某种托管语言的用户代码片段怎样才能在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中相互调用。</span><span class="sxs-lookup"><span data-stu-id="25ebf-103">This section describes how pieces of user code can call each other in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], either in [!INCLUDE[tsql](../../includes/tsql-md.md)] or in one of the managed languages.</span></span> <span data-ttu-id="25ebf-104">对象之间的这些关系称为链接。</span><span class="sxs-lookup"><span data-stu-id="25ebf-104">These relationships between objects are referred to as links.</span></span>  
  
## <a name="invocation-links"></a><span data-ttu-id="25ebf-105">调用链接</span><span class="sxs-lookup"><span data-stu-id="25ebf-105">Invocation Links</span></span>  
 <span data-ttu-id="25ebf-106">调用链接对应于代码调用，该调用要么来自调用对象的用户（比如调用存储过程的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批），要么来自公共语言运行库 (CLR) 存储过程或函数。</span><span class="sxs-lookup"><span data-stu-id="25ebf-106">Invocation links correspond to a code invocation, either from a user calling an object (such as a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch calling a stored procedure), or a common language runtime (CLR) stored procedure or function.</span></span> <span data-ttu-id="25ebf-107">调用链接将导致检查对被调用方的 `EXECUTE` 权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-107">Invocation links cause an `EXECUTE` permission on the callee to be checked.</span></span>  
  
## <a name="table-access-links"></a><span data-ttu-id="25ebf-108">表访问链接</span><span class="sxs-lookup"><span data-stu-id="25ebf-108">Table-Access Links</span></span>  
 <span data-ttu-id="25ebf-109">表访问链接对应于在表、视图或表值函数中检索或修改值。</span><span class="sxs-lookup"><span data-stu-id="25ebf-109">Table access links correspond to retrieving or modifying values in a table, view, or a table-valued function.</span></span> <span data-ttu-id="25ebf-110">它们类似于调用链接，但它们在 SELECT、INSERT、UPDATE 和 DELETE 权限方面有较粗粒度的访问控制权。</span><span class="sxs-lookup"><span data-stu-id="25ebf-110">They are similar to invocation links, except that they have a finer-grained access control in terms of SELECT, INSERT, UPDATE, and DELETE permissions.</span></span>  
  
## <a name="gated-links"></a><span data-ttu-id="25ebf-111">封闭链接</span><span class="sxs-lookup"><span data-stu-id="25ebf-111">Gated Links</span></span>  
 <span data-ttu-id="25ebf-112">门链接意味着，在执行期间，一旦已建立对象关系，则不跨越该对象关系检查权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-112">Gated links mean that during execution, permissions are not checked across the object relationship once it has been established.</span></span> <span data-ttu-id="25ebf-113">如果两个对象之间有一个封闭链接 (例如，对象**x**和对象**y**) ，则仅在创建对象**x**时检查对象**y**上和从对象**y**访问的其他对象的权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-113">When there is a gated link between two objects (for example, object **x** and object **y**), permissions on object **y** and other objects accessed from object **y** are checked only at the creation time of object **x**.</span></span> <span data-ttu-id="25ebf-114">在创建对象**x**时，将根据 `REFERENCE` **x**的所有者对**y**检查权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-114">At the creation time of object **x**, `REFERENCE` permission is checked on **y** against the owner of **x**.</span></span> <span data-ttu-id="25ebf-115">在执行时， (例如，当有人调用 object **x**) 时，不会针对其静态引用的**y**或其他对象检查权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-115">At execution time, (for example, when someone calls object **x**), there are no permissions checked against **y** or other objects it references statically.</span></span> <span data-ttu-id="25ebf-116">执行时，将对照对象**x**本身来检查适当的权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-116">At execution time, an appropriate permission will be checked against object **x** itself.</span></span>  
  
 <span data-ttu-id="25ebf-117">门链接始终与两个对象之间的元数据依赖性配合使用。</span><span class="sxs-lookup"><span data-stu-id="25ebf-117">Gated links are always used in conjunction with a metadata dependency between two objects.</span></span> <span data-ttu-id="25ebf-118">该元数据依赖性是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目录中建立的关系，它使得只要另一个对象依赖于某个对象则无法删除该对象。</span><span class="sxs-lookup"><span data-stu-id="25ebf-118">This metadata dependency is a relationship established in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] catalogs that prevents an object from being dropped as long as another object depends on it.</span></span>  
  
 <span data-ttu-id="25ebf-119">如果向很多依赖性对象授权是不合适或不可管理的，则需要使用门链接。</span><span class="sxs-lookup"><span data-stu-id="25ebf-119">Gated links are useful when it is not appropriate or manageable to give permissions to many dependent objects.</span></span> <span data-ttu-id="25ebf-120">在定义到 CLR 程序集（例如，CLR 过程、触发器、函数、类型和聚合）的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 入口点的对象与其中定义它们的程序集之间引入了门链接。</span><span class="sxs-lookup"><span data-stu-id="25ebf-120">Gated links are introduced between objects that define [!INCLUDE[tsql](../../includes/tsql-md.md)] entry points into CLR assemblies (for example, CLR procedures, triggers, functions, types, and aggregates) and the assemblies from which they are defined.</span></span> <span data-ttu-id="25ebf-121">对应这些对象的门安全性暗含如下法则：为了调用在 CLR 程序集中定义的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 入口点，调用方只需对该 [!INCLUDE[tsql](../../includes/tsql-md.md)] 入口点有合适的权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-121">Gated security against these objects implies that in order to invoke a [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point defined in a CLR assembly, the caller only needs an appropriate permission on that [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point.</span></span> <span data-ttu-id="25ebf-122">调用方不必对该程序集或它静态引用的任何其他程序集拥有权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-122">The caller is not required to have permissions on that assembly or any other assemblies it statically references.</span></span> <span data-ttu-id="25ebf-123">在创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 入口点时将检查程序集上的权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-123">The permissions on the assembly are checked at creation time of the [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point.</span></span>  
  
## <a name="sql-server-authorization-based-security"></a><span data-ttu-id="25ebf-124">SQL Server 基于授权的安全性</span><span class="sxs-lookup"><span data-stu-id="25ebf-124">SQL Server Authorization-Based Security</span></span>  
 <span data-ttu-id="25ebf-125">下面是对调用基于 CLR 的数据库对象和这些对象之间的调用进行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全检查所基于的基本规则；前三个规则定义了将检查哪些权限和根据哪个对象进行检查；第四个规则定义了根据哪个执行上下文来检查权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-125">The following are the basic rules behind the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security checks for invocations of and between CLR-based database objects; the first three rules define which permissions are checked and against which object; the fourth rule defines which execution context the permission is checked against.</span></span>  
  
1.  <span data-ttu-id="25ebf-126">所有调用都需要 `EXECUTE` 权限，除非调用发生在相同对象内；这意味着相同程序集内的调用不需要进行任何权限检查。</span><span class="sxs-lookup"><span data-stu-id="25ebf-126">All invocations require `EXECUTE` permission unless the invocations occur within the same object; this means that calls within the same assembly do not require any permission checks.</span></span> <span data-ttu-id="25ebf-127">权限检查在执行时进行。</span><span class="sxs-lookup"><span data-stu-id="25ebf-127">The permission is checked at execution time.</span></span>  
  
2.  <span data-ttu-id="25ebf-128">创建调用对象时，门链接需要拥有对被调用方的 `REFERENCE` 权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-128">Gated links require `REFERENCE` permission against the callee when the calling object is created.</span></span> <span data-ttu-id="25ebf-129">创建对象时，系统将检查调用对象的所有者是否有此权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-129">The permission is checked for the owner of the calling object when the object is created.</span></span>  
  
3.  <span data-ttu-id="25ebf-130">表访问链接需要拥有对被访问的表或视图的相应的 `SELECT`、`INSERT`、`UPDATE` 或 `DELETE` 权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-130">Table-access links require the corresponding `SELECT`, `INSERT`, `UPDATE`, or `DELETE` permission against the table or view being accessed.</span></span>  
  
4.  <span data-ttu-id="25ebf-131">系统根据当前执行上下文检查此权限。</span><span class="sxs-lookup"><span data-stu-id="25ebf-131">The permission is checked against the current execution context.</span></span> <span data-ttu-id="25ebf-132">可以用不同于调用方的执行上下文创建过程和函数。</span><span class="sxs-lookup"><span data-stu-id="25ebf-132">Procedures and functions can be created with an execution context that is different from the caller.</span></span> <span data-ttu-id="25ebf-133">程序集始终以根据它定义的过程、函数或触发器的执行上下文来创建。</span><span class="sxs-lookup"><span data-stu-id="25ebf-133">Assemblies are always created with the execution context of the procedure, function, or trigger that is defined against it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ebf-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25ebf-134">See Also</span></span>  
 [<span data-ttu-id="25ebf-135">CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="25ebf-135">CLR Integration Security</span></span>](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
