---
title: CLR 集成自定义属性概述 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- custom attributes [CLR integration]
- attributes [CLR integration]
- common language runtime [SQL Server], attributes
- database objects [CLR integration], custom attributes
- building database objects [CLR integration], custom attributes
ms.assetid: ecf5c097-0972-48e2-a9c0-b695b7dd2820
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: aa0bf94ee27fd89a6aa690e0ff2f8e3295648946
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577823"
---
# <a name="overview-of-clr-integration-custom-attributes"></a><span data-ttu-id="d87be-102">CLR 集成自定义属性的概览</span><span class="sxs-lookup"><span data-stu-id="d87be-102">Overview of CLR Integration Custom Attributes</span></span>
  <span data-ttu-id="d87be-103">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的公共语言运行时 (CLR) 允许使用称为属性的描述性关键字。</span><span class="sxs-lookup"><span data-stu-id="d87be-103">The common language runtime (CLR) of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] allows the use of descriptive keywords, called attributes.</span></span> <span data-ttu-id="d87be-104">这些属性为许多元素（如方法和类）提供附加信息。</span><span class="sxs-lookup"><span data-stu-id="d87be-104">These attributes provide additional information for many elements, such as methods and classes.</span></span> <span data-ttu-id="d87be-105">这些属性与对象的元数据一同保存在程序集中，并且可用于向其他开发工具描述您的代码，或者可用于影响 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内的运行时行为。</span><span class="sxs-lookup"><span data-stu-id="d87be-105">The attributes are saved in the assembly with the metadata of the object, and can be used to describe your code to other development tools or to affect runtime behavior inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d87be-106">向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 注册 CLR 例程时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将派生有关该例程的一组属性。</span><span class="sxs-lookup"><span data-stu-id="d87be-106">When you register a CLR routine with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] derives a set of properties about the routine.</span></span> <span data-ttu-id="d87be-107">这些例程属性确定该例程的功能，包括是否可以对该例程编制索引。</span><span class="sxs-lookup"><span data-stu-id="d87be-107">These routine properties determine the capabilities of the routine, including whether the routine can be indexed.</span></span> <span data-ttu-id="d87be-108">例如，如果将 `DataAccess` 属性设置为 `DataAccessKind.Read`，您将能够访问 CLR 函数内的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户表中的数据。</span><span class="sxs-lookup"><span data-stu-id="d87be-108">For example, setting the `DataAccess` property to `DataAccessKind.Read` lets you access data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user tables inside a CLR function.</span></span> <span data-ttu-id="d87be-109">下面的示例演示一个简单的情况，在此情况下， `DataAccess` 属性设置为便于从用户表**table1**进行数据访问。</span><span class="sxs-lookup"><span data-stu-id="d87be-109">The following example shows a simple case in which the `DataAccess` property is set to facilitate data access from a user table **table1**.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public partial class UserDefinedFunctions  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static string func1()  
    {  
        // Open a connection and create a command  
        SqlConnection conn = new SqlConnection("context connection = true");  
        conn.Open();  
        SqlCommand cmd = conn.CreateCommand();  
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10";  
        // where table1 is a user table  
        // Execute this command   
        SqlDataReader rd = cmd.ExecuteReader();  
        // Set string ret_val to str_val returned from the query  
        string ret_val = rd.GetValue(0).ToString();  
        rd.Close();  
        return ret_val;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public partial Class UserDefinedFunctions  
    <SqlFunction(DataAccess = DataAccessKind.Read)> _   
    Public Shared Function func1() As String  
        ' Open a connection and create a command  
        Dim conn As SqlConnection = New SqlConnection("context connection = true")   
        conn.Open()  
        Dim cmd As SqlCommand =  conn.CreateCommand()   
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10"  
        ' where table1 is a user table  
        ' Execute this command   
        Dim rd As SqlDataReader =  cmd.ExecuteReader()   
        ' Set string ret_val to str_val returned from the query  
        Dim ret_val As String =  rd.GetValue(0).ToString()   
        rd.Close()  
        Return ret_val  
    End Function  
End Class  
```  
  
 <span data-ttu-id="d87be-110">对于 [!INCLUDE[tsql](../../includes/tsql-md.md)] 例程，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 从例程定义直接派生例程属性。</span><span class="sxs-lookup"><span data-stu-id="d87be-110">For [!INCLUDE[tsql](../../includes/tsql-md.md)] routines, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] derives routine properties directly from the routine definition.</span></span> <span data-ttu-id="d87be-111">对于 CLR 例程，该服务器派生这些属性时并不分析例程主体；</span><span class="sxs-lookup"><span data-stu-id="d87be-111">For CLR routines, the server does not analyze the body of the routine to derive these properties.</span></span> <span data-ttu-id="d87be-112">您可以使用采用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 语言实现的类和类成员的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="d87be-112">Instead, you can use custom attributes for classes and class members implemented in a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] language.</span></span>  
  
 <span data-ttu-id="d87be-113">在 `Microsoft.SqlServer.Server` 命名空间中定义 CLR 例程、用户定义类型和聚合所需的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="d87be-113">The custom attributes needed for CLR routines, user-defined types, and aggregates are defined in the `Microsoft.SqlServer.Server` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d87be-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d87be-114">See Also</span></span>  
 [<span data-ttu-id="d87be-115">CLR 例程的自定义属性</span><span class="sxs-lookup"><span data-stu-id="d87be-115">Custom Attributes for CLR Routines</span></span>](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
  
