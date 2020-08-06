---
title: 更改程序集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: c22ca979675d3b7f263e3bc6de0c41c134a1abcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691244"
---
# <a name="altering-an-assembly"></a><span data-ttu-id="dffba-102">改变程序集</span><span class="sxs-lookup"><span data-stu-id="dffba-102">Altering an Assembly</span></span>
  <span data-ttu-id="dffba-103">可以使用 ALTER ASSEMBLY 语句从较新版本更新已在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中注册的程序集。</span><span class="sxs-lookup"><span data-stu-id="dffba-103">Assemblies that have been registered in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can be updated from a more recent version using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="dffba-104">若要更新程序集，可按照如下语法使用 ALTER ASSEMBLY 语句：</span><span class="sxs-lookup"><span data-stu-id="dffba-104">To update an assembly, use the ALTER ASSEMBLY statement with the following syntax:</span></span>  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 <span data-ttu-id="dffba-105">ALTER ASSEMBLY 不中断当前正在运行且正在使用此程序集的进程；这些进程使用未经更改的程序集继续执行。</span><span class="sxs-lookup"><span data-stu-id="dffba-105">ALTER ASSEMBLY does not disrupt currently running processes that are using the assembly; the processes continue executing with the unaltered assembly.</span></span> <span data-ttu-id="dffba-106">ALTER ASSEMBLY 不能用于更改公共语言运行时 (CLR) 函数、聚合函数、存储过程和触发器的签名。</span><span class="sxs-lookup"><span data-stu-id="dffba-106">ALTER ASSEMBLY cannot be used to change the signatures of common language runtime (CLR) functions, aggregate functions, stored procedures, and triggers.</span></span> <span data-ttu-id="dffba-107">只要未更改签名或属性，就可以向程序集添加新的公共方法，以任何方式修改专用方法以及修改公共方法。</span><span class="sxs-lookup"><span data-stu-id="dffba-107">New public methods can be added to the assembly, private methods can be modified in any way, and public methods can be modified as long as signatures or attributes are not changed.</span></span> <span data-ttu-id="dffba-108">不能使用 ALTER ASSEMBLY 更改本机序列化用户定义类型（包含数据成员或基类）内包含的字段。</span><span class="sxs-lookup"><span data-stu-id="dffba-108">Fields that are contained within a native-serialized user-defined type, including data members or base classes, cannot be changed by using ALTER ASSEMBLY.</span></span> <span data-ttu-id="dffba-109">不支持所有其他更改。</span><span class="sxs-lookup"><span data-stu-id="dffba-109">All other changes are unsupported.</span></span> <span data-ttu-id="dffba-110">有关详细信息，请参阅[ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dffba-110">For more information, see [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
## <a name="changing-the-permission-set-of-an-assembly"></a><span data-ttu-id="dffba-111">更改程序集的权限集</span><span class="sxs-lookup"><span data-stu-id="dffba-111">Changing the Permission Set of an Assembly</span></span>  
 <span data-ttu-id="dffba-112">还可以使用 ALTER ASSEMBLY 语句更改程序集的权限集。</span><span class="sxs-lookup"><span data-stu-id="dffba-112">The permission set of an assembly can also be changed using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="dffba-113">以下语句将 SQLCLRTest 程序集的权限集更改为 `EXTERNAL_ACCESS`。</span><span class="sxs-lookup"><span data-stu-id="dffba-113">The following statement changes the permission set of the SQLCLRTest assembly to `EXTERNAL_ACCESS`.</span></span>  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 <span data-ttu-id="dffba-114">如果将程序集的权限集从 `SAFE` 更改为 `EXTERNAL_ACCESS` 或 `UNSAFE`，则首先必须创建非对称密钥和具有 `EXTERNAL ACCESS ASSEMBLY` 权限或 `UNSAFE ASSEMBLY` 权限的相应登录名。</span><span class="sxs-lookup"><span data-stu-id="dffba-114">If the permission set of an assembly is being changed from `SAFE` to `EXTERNAL_ACCESS` or `UNSAFE`, an asymmetric key and corresponding login with `EXTERNAL ACCESS ASSEMBLY` permission or `UNSAFE ASSEMBLY` permission for the assembly must first be created.</span></span> <span data-ttu-id="dffba-115">有关详细信息，请参阅 [Creating an Assembly](creating-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="dffba-115">For more information, see [Creating an Assembly](creating-an-assembly.md).</span></span>  
  
## <a name="adding-the-source-code-of-an-assembly"></a><span data-ttu-id="dffba-116">添加程序集的源代码</span><span class="sxs-lookup"><span data-stu-id="dffba-116">Adding the Source Code of an Assembly</span></span>  
 <span data-ttu-id="dffba-117">CREATE ASSEMBLY 中不存在 ALTER ASSEMBLY 语法中的 ADD FILE 子句。</span><span class="sxs-lookup"><span data-stu-id="dffba-117">The ADD FILE clause in the ALTER ASSEMBLY syntax is not present in CREATE ASSEMBLY.</span></span> <span data-ttu-id="dffba-118">您可以使用该子句来添加源代码或与程序集关联的任何其他文件。</span><span class="sxs-lookup"><span data-stu-id="dffba-118">You can use it to add source code or any other files associated with an assembly.</span></span> <span data-ttu-id="dffba-119">这些文件将从其原始位置复制并存储到数据库的系统表中。</span><span class="sxs-lookup"><span data-stu-id="dffba-119">The files are copied from their original locations and stored in system tables in the database.</span></span> <span data-ttu-id="dffba-120">如果您需要重新创建或记录 UDT 的当前版本，这样可确保源代码或其他文件随时备用。</span><span class="sxs-lookup"><span data-stu-id="dffba-120">This ensures that you always have source code or other files on hand should you ever need to re-create or document the current version of the UDT.</span></span>  
  
 <span data-ttu-id="dffba-121">以下语句添加 Point UDT 的 Point.cs 类源代码。</span><span class="sxs-lookup"><span data-stu-id="dffba-121">The following statement adds the Point.cs class source code for the Point UDT.</span></span> <span data-ttu-id="dffba-122">这会复制 Point.cs 文件中包含的文本并用名称“PointSource”将其存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="dffba-122">This copies the text contained in the Point.cs file and stores it in the database under the name "PointSource".</span></span>  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a><span data-ttu-id="dffba-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dffba-123">See Also</span></span>  
 <span data-ttu-id="dffba-124">[管理 CLR 集成程序集](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="dffba-124">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="dffba-125">[创建程序集](creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="dffba-125">[Creating an Assembly](creating-an-assembly.md) </span></span>  
 <span data-ttu-id="dffba-126">[删除程序集](dropping-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="dffba-126">[Dropping an Assembly](dropping-an-assembly.md) </span></span>  
 [<span data-ttu-id="dffba-127">ALTER ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dffba-127">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
  
