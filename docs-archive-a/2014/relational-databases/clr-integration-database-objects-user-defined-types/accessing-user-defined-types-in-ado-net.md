---
title: 在 ADO.NET 中访问用户定义类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
ms.openlocfilehash: a94e333ad743ed07dff6b973ebfe227312a1cab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589144"
---
# <a name="accessing-user-defined-types-in-adonet"></a><span data-ttu-id="7cae5-102">在 ADO.NET 中访问用户定义类型</span><span class="sxs-lookup"><span data-stu-id="7cae5-102">Accessing User-Defined Types in ADO.NET</span></span>
  <span data-ttu-id="7cae5-103"> (Udt) 的用户定义类型是使用 .NET Framework 公共语言运行时支持的任何一种语言编写的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ， (CLR) 生成可验证代码。</span><span class="sxs-lookup"><span data-stu-id="7cae5-103">User-defined types (UDTs) are written using any of the languages supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) that produce verifiable code.</span></span> <span data-ttu-id="7cae5-104">这包括 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="7cae5-104">This includes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic.</span></span> <span data-ttu-id="7cae5-105">使用 UDT 可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中存储对象和自定义数据结构。</span><span class="sxs-lookup"><span data-stu-id="7cae5-105">UDTs allow objects and custom data structures to be stored in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="7cae5-106">数据公开为 .NET Framework 类或结构的公共成员，行为则由类或结构的方法来定义。</span><span class="sxs-lookup"><span data-stu-id="7cae5-106">The data is exposed as public members of a .NET Framework class or structure, and behaviors are defined by methods of the class or structure.</span></span> <span data-ttu-id="7cae5-107">UDT 可用作表的列定义、[!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理中的变量，还可用作 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函数或存储过程的参数。</span><span class="sxs-lookup"><span data-stu-id="7cae5-107">A UDT can be used as the column definition of a table, as a variable in a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, or as an argument of a [!INCLUDE[tsql](../../includes/tsql-md.md)] function or stored procedure.</span></span>  
  
 <span data-ttu-id="7cae5-108">在 ADO.NET 中，`System.Data.SqlClient` 访问接口以如下方式公开 UDT：</span><span class="sxs-lookup"><span data-stu-id="7cae5-108">In ADO.NET, the `System.Data.SqlClient` provider exposes UDTs in the following ways:</span></span>  
  
-   <span data-ttu-id="7cae5-109">作为对象通过 `System.Data.SqlClient.SqlDataReader`。</span><span class="sxs-lookup"><span data-stu-id="7cae5-109">Through the `System.Data.SqlClient.SqlDataReader` as an object.</span></span>  
  
-   <span data-ttu-id="7cae5-110">作为原始字节通过 `SqlDataReader`。</span><span class="sxs-lookup"><span data-stu-id="7cae5-110">Through the `SqlDataReader` as raw bytes.</span></span>  
  
-   <span data-ttu-id="7cae5-111">作为 `System.Data.SqlClient.SqlParameter` 对象的参数。</span><span class="sxs-lookup"><span data-stu-id="7cae5-111">As a parameter of a `System.Data.SqlClient.SqlParameter` object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7cae5-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="7cae5-112">In This Section</span></span>  
 [<span data-ttu-id="7cae5-113">检索 UDT 数据</span><span class="sxs-lookup"><span data-stu-id="7cae5-113">Retrieving UDT Data</span></span>](accessing-user-defined-types-retrieving-udt-data.md)  
 <span data-ttu-id="7cae5-114">介绍如何检索 UDT 数据和如何指定参数。</span><span class="sxs-lookup"><span data-stu-id="7cae5-114">Describes how to retrieve UDT data and how to specify parameters.</span></span>  
  
 [<span data-ttu-id="7cae5-115">使用 DataAdapter 更新 UDT 列</span><span class="sxs-lookup"><span data-stu-id="7cae5-115">Updating UDT Columns with DataAdapters</span></span>](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 <span data-ttu-id="7cae5-116">介绍如何在 `DataSets` 中使用 UDT 以及如何使用 `DataAdapters` 更新 UDT 数据。</span><span class="sxs-lookup"><span data-stu-id="7cae5-116">Describes how to work with UDTs in `DataSets` and how to update UDT data using `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cae5-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7cae5-117">See Also</span></span>  
 [<span data-ttu-id="7cae5-118">CLR 用户定义类型</span><span class="sxs-lookup"><span data-stu-id="7cae5-118">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
