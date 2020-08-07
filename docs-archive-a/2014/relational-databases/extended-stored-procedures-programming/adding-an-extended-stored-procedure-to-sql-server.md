---
title: 将扩展存储过程添加到 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], adding
- adding extended stored procedures
- collations [SQL Server], extended stored procedures
ms.assetid: 10f1bb74-3b43-4efd-b7ab-7a85a8600a50
author: rothja
ms.author: jroth
ms.openlocfilehash: 03ac8c2a0fa9ce77db59d50b3a7b9da42415e013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589096"
---
# <a name="adding-an-extended-stored-procedure-to-sql-server"></a><span data-ttu-id="01e08-102">将扩展存储过程添加到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="01e08-102">Adding an Extended Stored Procedure to SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="01e08-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="01e08-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="01e08-104">包含扩展存储过程函数的 DLL 充当对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的扩展。</span><span class="sxs-lookup"><span data-stu-id="01e08-104">A DLL that contains extended stored procedure functions acts as an extension to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="01e08-105">若要安装此 DLL，请将文件复制到一个目录中，例如包含标准 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL 文件的目录 (C:\Program FILES\MICROSOFT SQL Server\MSSQL12.0.*x*默认) 。</span><span class="sxs-lookup"><span data-stu-id="01e08-105">To install the DLL, copy the file to a directory, such as the one that contains the standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL files (C:\Program Files\Microsoft SQL Server\MSSQL12.0.*x*\MSSQL\Binn by default).</span></span>  
  
 <span data-ttu-id="01e08-106">在将扩展存储过程 DLL 复制到服务器之后，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统管理员必须将 DLL 中的每个扩展存储过程函数注册到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="01e08-106">After the extended stored procedure DLL has been copied to the server, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator must register to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] each extended stored procedure function in the DLL.</span></span> <span data-ttu-id="01e08-107">可以使用 sp_addextendedproc 系统存储过程完成该操作。</span><span class="sxs-lookup"><span data-stu-id="01e08-107">This is done using the sp_addextendedproc system stored procedure.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="01e08-108">在将扩展存储过程添加到服务器并将执行权限授予其他用户之前，系统管理员应当对它进行彻底检查，确保它不包含有害或恶意的代码。</span><span class="sxs-lookup"><span data-stu-id="01e08-108">The system administrator should thoroughly review an extended stored procedure to ensure that it does not contain harmful or malicious code before adding it to the server and granting execute permissions to other users.</span></span>  <span data-ttu-id="01e08-109">验证所有用户的输入。</span><span class="sxs-lookup"><span data-stu-id="01e08-109">Validate all user input.</span></span> <span data-ttu-id="01e08-110">验证之前，不要串联用户输入。</span><span class="sxs-lookup"><span data-stu-id="01e08-110">Do not concatenate user input before validating it.</span></span> <span data-ttu-id="01e08-111">绝对不要执行根据尚未验证的用户输入构造的命令。</span><span class="sxs-lookup"><span data-stu-id="01e08-111">Never execute a command constructed from unvalidated user input.</span></span>  
  
 <span data-ttu-id="01e08-112">sp_addextendedproc 的第一个参数指定函数的名称，第二个参数指定包含该函数的 DLL 的名称。</span><span class="sxs-lookup"><span data-stu-id="01e08-112">The first parameter of sp_addextendedproc specifies the name of the function, and the second parameter specifies the name of the DLL in which that function resides.</span></span> <span data-ttu-id="01e08-113">建议指定 DLL 的完整路径。</span><span class="sxs-lookup"><span data-stu-id="01e08-113">It is recommended that you specify the complete path of the DLL.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="01e08-114">升级到 SQL Server 2005 或更高版本后，未使用完整路径注册的现有 DLL 将无法工作。</span><span class="sxs-lookup"><span data-stu-id="01e08-114">Existing DLLs that were not registered with a complete path will not work after upgrading to SQL Server 2005 or later.</span></span> <span data-ttu-id="01e08-115">若要更正该问题，请使用 sp_dropextendedproc 撤消注册 DLL，然后使用 sp_addextendedproc 注册，并指定完整路径。</span><span class="sxs-lookup"><span data-stu-id="01e08-115">To correct the problem, use sp_dropextendedproc to unregister the DLL, and then reregister it with sp_addextendedproc, specifying the complete path.</span></span>  
  
 <span data-ttu-id="01e08-116">在 `sp_addextendedproc` 中指定的函数名称必须与 DLL 中的函数名称完全相同，包括大小写。</span><span class="sxs-lookup"><span data-stu-id="01e08-116">The name of the function specified in `sp_addextendedproc` must be exactly the same, including the case, as the function's name in the DLL.</span></span> <span data-ttu-id="01e08-117">例如，该命令将函数 `xp_hello,`（位于名为 `xp_hello.dll` 的 DLL 中）注册为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 扩展存储过程：</span><span class="sxs-lookup"><span data-stu-id="01e08-117">For example, this command registers a function `xp_hello,` located in a dll named `xp_hello.dll`, as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extended stored procedure:</span></span>  
  
```  
sp_addextendedproc 'xp_hello', 'c:\Program Files\Microsoft SQL Server\MSSQL12.0.MSSQLSERVER\MSSQL\Binn\xp_hello.dll';  
```  
  
 <span data-ttu-id="01e08-118">如果在 `sp_addextendedproc` 中指定的函数名称与 DLL 中的函数名称不完全匹配，则新名称将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中注册，但该名称是不可使用的。</span><span class="sxs-lookup"><span data-stu-id="01e08-118">If the name of the function specified in `sp_addextendedproc` does not exactly match the function name in the DLL, the new name will be registered in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the name will not be usable.</span></span> <span data-ttu-id="01e08-119">例如，尽管 `xp_Hello` 注册为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 位于中的扩展存储过程，但 `xp_hello.dll` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果稍后使用调用函数，将无法在 DLL 中查找函数 `xp_Hello` 。</span><span class="sxs-lookup"><span data-stu-id="01e08-119">For example, although `xp_Hello` is registered as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extended stored procedure located in `xp_hello.dll`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not be able to find the function in the DLL if you use `xp_Hello` to call the function later.</span></span>  
  
```  
--Register the function (xp_hello) with an initial upper case  
sp_addextendedproc 'xp_Hello', 'c:\xp_hello.dll';  
  
--Use the newly registered name to call the function  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
--This is the error message  
Server: Msg 17750, Level 16, State 1, Procedure xp_Hello, Line 1  
Could not load the DLL xp_hello.dll, or one of the DLLs it references. Reason: 127(The specified procedure could not be found.).  
```  
  
 <span data-ttu-id="01e08-120">如果在 `sp_addextendedproc` 中指定的函数名称与 DLL 中的函数名称完全匹配，并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的排序规则是不区分大小写的，则用户可以使用该名称的小写和大写字母的任意组合来调用此扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="01e08-120">If the name of the function specified in `sp_addextendedproc` matches exactly the function name in the DLL, and the collation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is case-insensitive, the user can call the extended stored procedure using any combination of lower- and upper-case letters of the name.</span></span>  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will succeed in calling xp_hello  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HelLO @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
```  
  
 <span data-ttu-id="01e08-121">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的排序规则是区分大小写的，那么，如果用不同的大小写形式调用此扩展存储过程，即使它是以与 DLL 中的函数完全相同的名称和排序规则注册的，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仍将无法调用该过程。</span><span class="sxs-lookup"><span data-stu-id="01e08-121">When the collation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is case-sensitive, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not be able to call the extended stored procedure -- even if it was registered with exactly the same name and collation as the function in the DLL -- if the procedure is called with a different case.</span></span>  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will result in an error  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
  
--This is the error  
Server: Msg 2812, Level 16, State 62, Line 1  
```  
  
 <span data-ttu-id="01e08-122">不需要停止和重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="01e08-122">It is not necessary to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e08-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01e08-123">See Also</span></span>  
 <span data-ttu-id="01e08-124">[sp_addextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="01e08-124">[sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span></span>  
 [<span data-ttu-id="01e08-125">sp_dropextendedproc (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="01e08-125">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
