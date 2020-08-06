---
title: PowerShell 中的 SQL Server 标识符 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- PowerShell [SQL Server], identifiers
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- identifiers [SQL Server], PowerShell
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 651099b0-33b4-453a-a864-b067f21eb8b9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c54fb352fb17c099bda78c80f00f91dbba428f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688957"
---
# <a name="sql-server-identifiers-in-powershell"></a><span data-ttu-id="54dee-102">PowerShell 中的 SQL Server 标识符</span><span class="sxs-lookup"><span data-stu-id="54dee-102">SQL Server Identifiers in PowerShell</span></span>
  <span data-ttu-id="54dee-103">用于 Windows PowerShell 的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序使用 Windows PowerShell 路径中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 标识符。</span><span class="sxs-lookup"><span data-stu-id="54dee-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell uses [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers in Windows PowerShell paths.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="54dee-104">标识符可包含 Windows PowerShell 不支持在路径中使用的字符。</span><span class="sxs-lookup"><span data-stu-id="54dee-104">identifiers can contain characters that Windows PowerShell does not support in paths.</span></span> <span data-ttu-id="54dee-105">在 Windows PowerShell 路径中使用标识符时，必须对这些字符进行转义或者对它们使用特殊的编码。</span><span class="sxs-lookup"><span data-stu-id="54dee-105">You must escape these characters or use special encoding for them when using the identifiers in Windows PowerShell paths.</span></span>  
  
## <a name="sql-server-identifiers-in-windows-powershell-paths"></a><span data-ttu-id="54dee-106">Windows PowerShell 路径中的 SQL Server 标识符</span><span class="sxs-lookup"><span data-stu-id="54dee-106">SQL Server Identifiers in Windows PowerShell Paths</span></span>  
 <span data-ttu-id="54dee-107">Windows PowerShell 提供程序使用类似于 Windows 文件系统路径的路径结构来公开数据层次结构。</span><span class="sxs-lookup"><span data-stu-id="54dee-107">Windows PowerShell providers expose data hierarchies using a path structure similar to that used for the Windows file system.</span></span> <span data-ttu-id="54dee-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序实现了 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象的路径。</span><span class="sxs-lookup"><span data-stu-id="54dee-108">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider implements paths to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span> <span data-ttu-id="54dee-109">对于 [!INCLUDE[ssDE](../includes/ssde-md.md)]，驱动器设置为 SQLSERVER:，第一个文件夹设置为 \SQL，数据库对象作为容器和项来引用。</span><span class="sxs-lookup"><span data-stu-id="54dee-109">For the [!INCLUDE[ssDE](../includes/ssde-md.md)], the drive is set to SQLSERVER:, the first folder is set to \SQL, and the database objects are referenced as containers and items.</span></span> <span data-ttu-id="54dee-110">这是 Purchasing 架构中 Vendor 表的路径，该架构位于默认 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 实例的 [!INCLUDE[ssDE](../includes/ssde-md.md)]数据库中：</span><span class="sxs-lookup"><span data-stu-id="54dee-110">This is the path to the Vendor table in the Purchasing schema of the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database in a default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)]:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="54dee-111">标识符是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象的名称，如表名或列名。</span><span class="sxs-lookup"><span data-stu-id="54dee-111">identifiers are the names of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects, such as table or column names.</span></span> <span data-ttu-id="54dee-112">共有两种类型的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 标识符：</span><span class="sxs-lookup"><span data-stu-id="54dee-112">There are two types of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers:</span></span>  
  
-   <span data-ttu-id="54dee-113">常规标识符限制为一组在 Windows PowerShell 路径中同样受到支持的字符。</span><span class="sxs-lookup"><span data-stu-id="54dee-113">Regular identifiers are limited to a set of characters that are also supported in Windows PowerShell paths.</span></span> <span data-ttu-id="54dee-114">无需更改这些名称，即可在 Windows PowerShell 路径中使用它们。</span><span class="sxs-lookup"><span data-stu-id="54dee-114">These names can be used in Windows PowerShell paths without being changed.</span></span>  
  
-   <span data-ttu-id="54dee-115">分隔标识符可以使用 Windows PowerShell 路径名称中不支持的字符。</span><span class="sxs-lookup"><span data-stu-id="54dee-115">Delimited identifiers can use characters not supported in Windows PowerShell path names.</span></span> <span data-ttu-id="54dee-116">如果用中括号将分隔标识符括起来 ([IdentifierName])，则可以将它们称为带中括号的标识符；如果将它们用双引号引起来，则可以将它们称为带引号的标识符 ("IdentifierName")。</span><span class="sxs-lookup"><span data-stu-id="54dee-116">Delimited identifiers are called bracketed identifiers if they are enclosed in brackets ([IdentifierName]) and quoted identifiers if they are enclosed in double quotes ("IdentifierName").</span></span> <span data-ttu-id="54dee-117">如果分隔标识符使用 Windows PowerShell 路径中不支持的字符，那么，必须先对这些字符进行编码或转义，才能将标识符用作容器名称或项名称。</span><span class="sxs-lookup"><span data-stu-id="54dee-117">If a delimited identifier uses characters not supported in Windows PowerShell paths, the characters must either be encoded or escaped before using the identifier as a container or item name.</span></span> <span data-ttu-id="54dee-118">可以针对所有字符进行编码。</span><span class="sxs-lookup"><span data-stu-id="54dee-118">Encoding works for all characters.</span></span> <span data-ttu-id="54dee-119">而某些字符（如冒号字符 (:)）则不能进行转义。</span><span class="sxs-lookup"><span data-stu-id="54dee-119">Some characters, such as the colon character (:), cannot be escaped.</span></span>  
  
## <a name="sql-server-identifiers-in-cmdlets"></a><span data-ttu-id="54dee-120">cmdlet 中的 SQL Server 标识符</span><span class="sxs-lookup"><span data-stu-id="54dee-120">SQL Server Identifiers in cmdlets</span></span>  
 <span data-ttu-id="54dee-121">某些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet 具有一个将标识符作为输入的参数。</span><span class="sxs-lookup"><span data-stu-id="54dee-121">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets have a parameter that takes an identifier as input.</span></span> <span data-ttu-id="54dee-122">参数值通常以带引号的字符串常量或以字符串变量形式提供。</span><span class="sxs-lookup"><span data-stu-id="54dee-122">The parameter values are typically supplied as quoted string constants or in string variables.</span></span> <span data-ttu-id="54dee-123">如果标识符以字符串常量或变量形式提供，则不会与 Windows PowerShell 支持的字符集发生冲突。</span><span class="sxs-lookup"><span data-stu-id="54dee-123">When identifiers are supplied as string constants or in variables, there is no conflict with the set of characters that are supported by Windows PowerShell.</span></span>  
  
## <a name="sql-server-identifier-tasks"></a><span data-ttu-id="54dee-124">SQL Server 标识符任务</span><span class="sxs-lookup"><span data-stu-id="54dee-124">SQL Server Identifier Tasks</span></span>  
  
|<span data-ttu-id="54dee-125">任务说明</span><span class="sxs-lookup"><span data-stu-id="54dee-125">Task Description</span></span>|<span data-ttu-id="54dee-126">主题</span><span class="sxs-lookup"><span data-stu-id="54dee-126">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="54dee-127">介绍如何指定一个实例名称，包括运行该实例的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="54dee-127">Describes how to specify an instance name, including the name of the computer the instance is running on.</span></span>|[<span data-ttu-id="54dee-128">在 SQL Server PowerShell 提供程序中指定实例</span><span class="sxs-lookup"><span data-stu-id="54dee-128">Specify Instances in the SQL Server PowerShell Provider</span></span>](sql-server-powershell-provider.md)|  
|<span data-ttu-id="54dee-129">介绍如何为 Windows PowerShell 路径中不支持的分隔标识符中的字符指定十六进制编码。</span><span class="sxs-lookup"><span data-stu-id="54dee-129">Describes how to specify the hexadecimal encoding for characters in delimited identifiers that are not supported in Windows PowerShell paths.</span></span> <span data-ttu-id="54dee-130">此外还介绍了如何解码十六进制字符。</span><span class="sxs-lookup"><span data-stu-id="54dee-130">Also describes how to decode the hexadecimal characters.</span></span>|[<span data-ttu-id="54dee-131">对 SQL Server 标识符进行编码和解码</span><span class="sxs-lookup"><span data-stu-id="54dee-131">Encode and Decode SQL Server Identifiers</span></span>](encode-and-decode-sql-server-identifiers.md)|  
|<span data-ttu-id="54dee-132">介绍如何为 PowerShell 路径中不支持的字符使用 Windows PowerShell 转义符。</span><span class="sxs-lookup"><span data-stu-id="54dee-132">Describes how to use the Windows PowerShell escape character for characters not supported in PowerShell paths.</span></span>|[<span data-ttu-id="54dee-133">对 SQL Server 标识符进行转义</span><span class="sxs-lookup"><span data-stu-id="54dee-133">Escape SQL Server Identifiers</span></span>](escape-sql-server-identifiers.md)|  
  
## <a name="see-also"></a><span data-ttu-id="54dee-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54dee-134">See Also</span></span>  
 <span data-ttu-id="54dee-135">[SQL Server PowerShell 提供程序](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="54dee-135">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="54dee-136">[SQL Server PowerShell](sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="54dee-136">[SQL Server PowerShell](sql-server-powershell.md) </span></span>  
 [<span data-ttu-id="54dee-137">数据库标识符</span><span class="sxs-lookup"><span data-stu-id="54dee-137">Database Identifiers</span></span>](../relational-databases/databases/database-identifiers.md)  
  
  
