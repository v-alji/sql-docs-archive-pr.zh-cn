---
title: CLR 用户定义类型 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
author: rothja
ms.author: jroth
ms.openlocfilehash: e4e19323eeac9e0a1148924543f71aa7de5619b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591405"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="40529-102">CLR 用户定义类型</span><span class="sxs-lookup"><span data-stu-id="40529-102">CLR User-Defined Types</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="40529-103">用于创建基于以 .NET Framework 公共语言运行时 (CLR) 创建的程序集而编写的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="40529-103">gives you the ability to create database objects that are programmed against an assembly created in the.NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="40529-104">数据库对象包括触发器、存储过程、函数、聚合函数和类型，它们可以利用 CLR 提供的丰富的编程模型。</span><span class="sxs-lookup"><span data-stu-id="40529-104">Database objects that can take advantage of the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40529-105">默认情况下，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中关闭了执行 CLR 代码的功能。</span><span class="sxs-lookup"><span data-stu-id="40529-105">The ability to execute CLR code is set to OFF by default in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="40529-106">可以使用**sp_configure**系统存储过程来启用 CLR。</span><span class="sxs-lookup"><span data-stu-id="40529-106">The CLR can be enabled by using the **sp_configure** system stored procedure.</span></span>  
  
 <span data-ttu-id="40529-107">从开始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，你可以使用用户定义的类型 (udt) 来扩展服务器的标量类型系统，从而能够在数据库中存储 CLR 对象 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="40529-107">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you can use user-defined types (UDTs) to extend the scalar type system of the server, enabling storage of CLR objects in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="40529-108">UDT 可以包含多个元素，还可以有行为，这使它们与由单个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据类型组成的传统别名数据类型区分开来。</span><span class="sxs-lookup"><span data-stu-id="40529-108">UDTs can contain multiple elements and can have behaviors, differentiating them from the traditional alias data types which consist of a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system data type.</span></span>  
  
 <span data-ttu-id="40529-109">因为 UDT 作为整体供系统访问，所以其对复杂数据类型的使用可能会对性能有负面影响。</span><span class="sxs-lookup"><span data-stu-id="40529-109">Because UDTs are accessed by the system as a whole, their use for complex data types may negatively impact performance.</span></span> <span data-ttu-id="40529-110">通常，使用传统的行和表可以对复杂数据进行最佳建模。</span><span class="sxs-lookup"><span data-stu-id="40529-110">Complex data is generally best modeled using traditional rows and tables.</span></span> <span data-ttu-id="40529-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 UDT 非常适合以下各项：</span><span class="sxs-lookup"><span data-stu-id="40529-111">UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are well suited to the following:</span></span>  
  
-   <span data-ttu-id="40529-112">日期、时间、货币和扩展数字类型</span><span class="sxs-lookup"><span data-stu-id="40529-112">Date, time, currency, and extended numeric types</span></span>  
  
-   <span data-ttu-id="40529-113">地理空间应用程序</span><span class="sxs-lookup"><span data-stu-id="40529-113">Geospatial applications</span></span>  
  
-   <span data-ttu-id="40529-114">编码或加密数据</span><span class="sxs-lookup"><span data-stu-id="40529-114">Encoded or encrypted data</span></span>  
  
 <span data-ttu-id="40529-115">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中开发 UDT 的过程由以下步骤组成：</span><span class="sxs-lookup"><span data-stu-id="40529-115">The process of developing UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="40529-116">**编码和生成定义 UDT 的程序集。**</span><span class="sxs-lookup"><span data-stu-id="40529-116">**Code and build the assembly that defines the UDT.**</span></span> <span data-ttu-id="40529-117">使用生成可验证代码的 .NET Framework 公共语言运行时 (CLR) 所支持的任何语言都可以定义 UDT，</span><span class="sxs-lookup"><span data-stu-id="40529-117">UDTs are defined using any of the languages supported by the.NET Framework common language runtime (CLR) that produce verifiable code.</span></span> <span data-ttu-id="40529-118">这包括 Visual C# 和 Visual Basic .NET。</span><span class="sxs-lookup"><span data-stu-id="40529-118">This includes Visual C# and Visual Basic .NET.</span></span> <span data-ttu-id="40529-119">数据作为 .NET Framework 类或结构的字段和属性公开，其行为由类或结构的方法定义。</span><span class="sxs-lookup"><span data-stu-id="40529-119">The data is exposed as fields and properties of a .NET Framework class or structure, and behaviors are defined by methods of the class or structure.</span></span>  
  
2.  <span data-ttu-id="40529-120">**注册程序集。**</span><span class="sxs-lookup"><span data-stu-id="40529-120">**Register the assembly.**</span></span> <span data-ttu-id="40529-121">可以通过在数据库项目中使用 Visual Studio 用户界面，或通过使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY 语句（该语句将包含类或结构的程序集复制到数据库中），来部署 UDT。</span><span class="sxs-lookup"><span data-stu-id="40529-121">UDTs can be deployed through the Visual Studio user interface in a database project, or by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY statement, which copies the assembly containing the class or structure into a database.</span></span>  
  
3.  <span data-ttu-id="40529-122">**在 SQL Server 中创建 UDT。**</span><span class="sxs-lookup"><span data-stu-id="40529-122">**Create the UDT in SQL Server.**</span></span> <span data-ttu-id="40529-123">一旦程序集加载到宿主数据库中，则使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE 语句创建 UDT，并将该类或结构的成员作为此 UDT 的成员公开。</span><span class="sxs-lookup"><span data-stu-id="40529-123">Once an assembly is loaded into a host database, you use the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE statement to create a UDT and expose the members of the class or structure as members of the UDT.</span></span> <span data-ttu-id="40529-124">UDT 仅在单个数据库的上下文中存在，一旦注册，则不依赖于从其创建它们的外部文件。</span><span class="sxs-lookup"><span data-stu-id="40529-124">UDTs exist only in the context of a single database, and, once registered, have no dependencies on the external files from which they were created.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="40529-125">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前，不支持从 .NET Framework 程序集创建的 UDT。</span><span class="sxs-lookup"><span data-stu-id="40529-125">Before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], UDTs created from .NET Framework assemblies were not supported.</span></span> <span data-ttu-id="40529-126">不过，你仍然可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sp_addtype**来使用别名数据类型。</span><span class="sxs-lookup"><span data-stu-id="40529-126">However, you can still use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alias data types by using **sp_addtype**.</span></span> <span data-ttu-id="40529-127">本机 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户定义数据类型和 UDT 都可以用 CREATE TYPE 语法创建。</span><span class="sxs-lookup"><span data-stu-id="40529-127">The CREATE TYPE syntax can be used for creating both native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined data types and UDTs.</span></span>  
  
4.  <span data-ttu-id="40529-128">**使用 UDT 创建表、变量或参数**从开始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，用户定义类型可用作表的列定义、批处理中的变量 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，或者用作 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函数或存储过程的参数。</span><span class="sxs-lookup"><span data-stu-id="40529-128">**Create tables, variables, or parameters using the UDT** Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a user-defined type can be used as the column definition of a table, as a variable in a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, or as an argument of a [!INCLUDE[tsql](../../includes/tsql-md.md)] function or stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40529-129">本节内容</span><span class="sxs-lookup"><span data-stu-id="40529-129">In This Section</span></span>  
 [<span data-ttu-id="40529-130">创建用户定义类型</span><span class="sxs-lookup"><span data-stu-id="40529-130">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
 <span data-ttu-id="40529-131">描述如何创建 UDT。</span><span class="sxs-lookup"><span data-stu-id="40529-131">Describes how to create UDTs.</span></span>  
  
 [<span data-ttu-id="40529-132">在 SQL Server 中注册用户定义类型</span><span class="sxs-lookup"><span data-stu-id="40529-132">Registering User-Defined Types in SQL Server</span></span>](registering-user-defined-types-in-sql-server.md)  
 <span data-ttu-id="40529-133">描述如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中注册和管理 UDT。</span><span class="sxs-lookup"><span data-stu-id="40529-133">Describes how to register and manage UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="40529-134">使用 SQL Server 中的用户定义类型</span><span class="sxs-lookup"><span data-stu-id="40529-134">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
 <span data-ttu-id="40529-135">描述如何使用 UDT 创建查询。</span><span class="sxs-lookup"><span data-stu-id="40529-135">Describes how to create queries using UDTs.</span></span>  
  
 [<span data-ttu-id="40529-136">在 ADO.NET 中访问用户定义类型</span><span class="sxs-lookup"><span data-stu-id="40529-136">Accessing User-Defined Types in ADO.NET</span></span>](accessing-user-defined-types-in-ado-net.md)  
 <span data-ttu-id="40529-137">描述如何在 ADO.NET 中使用用于 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 来处理 UDT。</span><span class="sxs-lookup"><span data-stu-id="40529-137">Describes how to work with UDTs using the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in ADO.NET.</span></span>  
  
  
