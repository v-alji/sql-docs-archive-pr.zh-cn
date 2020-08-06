---
title: 映射 CLR 参数数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
author: rothja
ms.author: jroth
ms.openlocfilehash: 7025c5180eac793534961af63df9ac701c95c03f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693977"
---
# <a name="mapping-clr-parameter-data"></a><span data-ttu-id="20740-102">映射 CLR 参数数据</span><span class="sxs-lookup"><span data-stu-id="20740-102">Mapping CLR Parameter Data</span></span>
  <span data-ttu-id="20740-103">下表列出了 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型、它们在公共语言运行时中的等效项 (CLR) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 `System.Data.SqlTypes` 命名空间中，以及它们在 .NET FRAMEWORK 中的本机 clr 等效项 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="20740-103">The following table lists [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, their equivalents in the common language runtime (CLR) for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the `System.Data.SqlTypes` namespace, and their native CLR equivalents in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="20740-104">**SQL Server 数据类型**</span><span class="sxs-lookup"><span data-stu-id="20740-104">**SQL Server data type**</span></span>|<span data-ttu-id="20740-105">类型（在 System.Data.SqlTypes 或 Microsoft.SqlServer.Types 中）</span><span class="sxs-lookup"><span data-stu-id="20740-105">Type (in System.Data.SqlTypes or Microsoft.SqlServer.Types)</span></span>|<span data-ttu-id="20740-106">**CLR 数据类型 (.NET Framework)**</span><span class="sxs-lookup"><span data-stu-id="20740-106">**CLR data type (.NET Framework)**</span></span>|  
|`bigint`|`SqlInt64`|<span data-ttu-id="20740-107">**Int64，可以为 Null\<Int64>**</span><span class="sxs-lookup"><span data-stu-id="20740-107">**Int64, Nullable\<Int64>**</span></span>|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|<span data-ttu-id="20740-108">**布尔值，可以为 Null\<Boolean>**</span><span class="sxs-lookup"><span data-stu-id="20740-108">**Boolean, Nullable\<Boolean>**</span></span>|  
|`char`|<span data-ttu-id="20740-109">无</span><span class="sxs-lookup"><span data-stu-id="20740-109">None</span></span>|<span data-ttu-id="20740-110">无</span><span class="sxs-lookup"><span data-stu-id="20740-110">None</span></span>|  
|`cursor`|<span data-ttu-id="20740-111">无</span><span class="sxs-lookup"><span data-stu-id="20740-111">None</span></span>|<span data-ttu-id="20740-112">无</span><span class="sxs-lookup"><span data-stu-id="20740-112">None</span></span>|  
|`date`|`SqlDateTime`|<span data-ttu-id="20740-113">**DateTime，可以为 Null\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="20740-113">**DateTime, Nullable\<DateTime>**</span></span>|  
|`datetime`|`SqlDateTime`|<span data-ttu-id="20740-114">**DateTime，可以为 Null\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="20740-114">**DateTime, Nullable\<DateTime>**</span></span>|  
|`datetime2`|<span data-ttu-id="20740-115">无</span><span class="sxs-lookup"><span data-stu-id="20740-115">None</span></span>|<span data-ttu-id="20740-116">**DateTime，可以为 Null\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="20740-116">**DateTime, Nullable\<DateTime>**</span></span>|  
|`DATETIMEOFFSET`|`None`|<span data-ttu-id="20740-117">**DateTimeOffset，可以为 Null\<DateTimeOffset>**</span><span class="sxs-lookup"><span data-stu-id="20740-117">**DateTimeOffset, Nullable\<DateTimeOffset>**</span></span>|  
|`decimal`|`SqlDecimal`|<span data-ttu-id="20740-118">**十进制，可以为 Null\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="20740-118">**Decimal, Nullable\<Decimal>**</span></span>|  
|`float`|`SqlDouble`|<span data-ttu-id="20740-119">**Double，可以为 Null\<Double>**</span><span class="sxs-lookup"><span data-stu-id="20740-119">**Double, Nullable\<Double>**</span></span>|  
|`geography`|`SqlGeography`<br /><br /> <span data-ttu-id="20740-120">`SqlGeography`是在 Microsoft.SqlServer.Types.dll 中定义的，它与 SQL Server 一起安装，并且可以从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [功能包](https://www.microsoft.com/download/details.aspx?id=53164)下载。</span><span class="sxs-lookup"><span data-stu-id="20740-120">`SqlGeography` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="20740-121">无</span><span class="sxs-lookup"><span data-stu-id="20740-121">None</span></span>|  
|`geometry`|`SqlGeometry`<br /><br /> <span data-ttu-id="20740-122">`SqlGeometry`是在 Microsoft.SqlServer.Types.dll 中定义的，它与 SQL Server 一起安装，并且可以从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [功能包](https://www.microsoft.com/download/details.aspx?id=53164)下载。</span><span class="sxs-lookup"><span data-stu-id="20740-122">`SqlGeometry` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="20740-123">无</span><span class="sxs-lookup"><span data-stu-id="20740-123">None</span></span>|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> <span data-ttu-id="20740-124">`SqlHierarchyId`是在 Microsoft.SqlServer.Types.dll 中定义的，它与 SQL Server 一起安装，并且可以从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [功能包](https://www.microsoft.com/download/details.aspx?id=53164)下载。</span><span class="sxs-lookup"><span data-stu-id="20740-124">`SqlHierarchyId` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="20740-125">无</span><span class="sxs-lookup"><span data-stu-id="20740-125">None</span></span>|  
|`image`|<span data-ttu-id="20740-126">无</span><span class="sxs-lookup"><span data-stu-id="20740-126">None</span></span>|<span data-ttu-id="20740-127">无</span><span class="sxs-lookup"><span data-stu-id="20740-127">None</span></span>|  
|`int`|`SqlInt32`|<span data-ttu-id="20740-128">**Int32，可以为 Null\<Int32>**</span><span class="sxs-lookup"><span data-stu-id="20740-128">**Int32, Nullable\<Int32>**</span></span>|  
|`money`|`SqlMoney`|<span data-ttu-id="20740-129">**十进制，可以为 Null\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="20740-129">**Decimal, Nullable\<Decimal>**</span></span>|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|<span data-ttu-id="20740-130">无</span><span class="sxs-lookup"><span data-stu-id="20740-130">None</span></span>|<span data-ttu-id="20740-131">无</span><span class="sxs-lookup"><span data-stu-id="20740-131">None</span></span>|  
|`numeric`|`SqlDecimal`|<span data-ttu-id="20740-132">**十进制，可以为 Null\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="20740-132">**Decimal, Nullable\<Decimal>**</span></span>|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> <span data-ttu-id="20740-133">`SQLChars` 更适用于数据传输和访问，而 `SQLString` 更适用于执行字符串运算。</span><span class="sxs-lookup"><span data-stu-id="20740-133">`SQLChars` is a better match for data transfer and access, and `SQLString` is a better match for performing String operations.</span></span>|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|<span data-ttu-id="20740-134">**Char、String、Char []，可以为 Null\<char>**</span><span class="sxs-lookup"><span data-stu-id="20740-134">**Char, String, Char[], Nullable\<char>**</span></span>|  
|`real`|<span data-ttu-id="20740-135">`SqlSingle`（`SqlSingle` 的范围，但大于 `real`）</span><span class="sxs-lookup"><span data-stu-id="20740-135">`SqlSingle` (the range of `SqlSingle`, however, is larger than `real`)</span></span>|<span data-ttu-id="20740-136">**单个，可以为 Null\<Single>**</span><span class="sxs-lookup"><span data-stu-id="20740-136">**Single, Nullable\<Single>**</span></span>|  
|`rowversion`|<span data-ttu-id="20740-137">无</span><span class="sxs-lookup"><span data-stu-id="20740-137">None</span></span>|`Byte[]`|  
|`smallint`|`SqlInt16`|<span data-ttu-id="20740-138">**Int16，可为 Null\<Int16>**</span><span class="sxs-lookup"><span data-stu-id="20740-138">**Int16, Nullable\<Int16>**</span></span>|  
|`smallmoney`|`SqlMoney`|<span data-ttu-id="20740-139">**十进制，可以为 Null\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="20740-139">**Decimal, Nullable\<Decimal>**</span></span>|  
|`sql_variant`|<span data-ttu-id="20740-140">无</span><span class="sxs-lookup"><span data-stu-id="20740-140">None</span></span>|`Object`|  
|`table`|<span data-ttu-id="20740-141">无</span><span class="sxs-lookup"><span data-stu-id="20740-141">None</span></span>|<span data-ttu-id="20740-142">无</span><span class="sxs-lookup"><span data-stu-id="20740-142">None</span></span>|  
|`text`|<span data-ttu-id="20740-143">无</span><span class="sxs-lookup"><span data-stu-id="20740-143">None</span></span>|<span data-ttu-id="20740-144">无</span><span class="sxs-lookup"><span data-stu-id="20740-144">None</span></span>|  
|`time`|<span data-ttu-id="20740-145">无</span><span class="sxs-lookup"><span data-stu-id="20740-145">None</span></span>|<span data-ttu-id="20740-146">**TimeSpan，可以为 Null\<TimeSpan>**</span><span class="sxs-lookup"><span data-stu-id="20740-146">**TimeSpan, Nullable\<TimeSpan>**</span></span>|  
|`timestamp`|<span data-ttu-id="20740-147">无</span><span class="sxs-lookup"><span data-stu-id="20740-147">None</span></span>|<span data-ttu-id="20740-148">无</span><span class="sxs-lookup"><span data-stu-id="20740-148">None</span></span>|  
|`tinyint`|`SqlByte`|<span data-ttu-id="20740-149">**字节，可以为 Null\<Byte>**</span><span class="sxs-lookup"><span data-stu-id="20740-149">**Byte, Nullable\<Byte>**</span></span>|  
|`uniqueidentifier`|`SqlGuid`|<span data-ttu-id="20740-150">**Guid，可以为 Null\<Guid>**</span><span class="sxs-lookup"><span data-stu-id="20740-150">**Guid, Nullable\<Guid>**</span></span>|  
|`User-defined type(UDT)`|<span data-ttu-id="20740-151">无</span><span class="sxs-lookup"><span data-stu-id="20740-151">None</span></span>|<span data-ttu-id="20740-152">绑定到相同程序集或依赖程序集中的用户定义类型的相同类。</span><span class="sxs-lookup"><span data-stu-id="20740-152">The same class that is bound to the user-defined type in the same assembly or a dependent assembly.</span></span>|  
|<span data-ttu-id="20740-153">**varbinary**</span><span class="sxs-lookup"><span data-stu-id="20740-153">**varbinary**</span></span>|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|<span data-ttu-id="20740-154">**byte、Byte []、可以为 Null\<byte>**</span><span class="sxs-lookup"><span data-stu-id="20740-154">**byte, Byte[], Nullable\<byte>**</span></span>|  
|`varchar`|<span data-ttu-id="20740-155">无</span><span class="sxs-lookup"><span data-stu-id="20740-155">None</span></span>|<span data-ttu-id="20740-156">无</span><span class="sxs-lookup"><span data-stu-id="20740-156">None</span></span>|  
|`xml`|`SqlXml`|<span data-ttu-id="20740-157">无</span><span class="sxs-lookup"><span data-stu-id="20740-157">None</span></span>|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a><span data-ttu-id="20740-158">使用 Out 参数的自动数据类型转换</span><span class="sxs-lookup"><span data-stu-id="20740-158">Automatic Data Type Conversion with Out Parameters</span></span>  
 <span data-ttu-id="20740-159">通过以 `out` 修饰符 (Microsoft Visual C#) 或 `<Out()> ByRef` (Microsoft Visual Basic) 来标记输入参数，CLR 方法可以将信息返回到发起调用的代码或程序。如果输入参数是 `System.Data.SqlTypes` 命名空间中的 CLR 数据类型，并且发起调用的程序指定其等效 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型作为输入参数，则会在 CLR 方法返回数据类型时自动发生类型转换。</span><span class="sxs-lookup"><span data-stu-id="20740-159">A CLR method can return information to the calling code or program by marking an input parameter with the `out` modifier (Microsoft Visual C#) or `<Out()> ByRef` (Microsoft Visual Basic) If the input parameter is a CLR data type in the `System.Data.SqlTypes` namespace, and the calling program specifies its equivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type as the input parameter, a type conversion occurs automatically when the CLR method returns the data type.</span></span>  
  
 <span data-ttu-id="20740-160">例如，以下 CLR 存储过程具有以 `SqlInt32` (C#) 或 `out` (Visual Basic) 进行标记的 `<Out()> ByRef` CLR 数据类型的输入参数：</span><span class="sxs-lookup"><span data-stu-id="20740-160">For example, the following CLR stored procedure has an input parameter of `SqlInt32` CLR data type that is marked with `out` (C#) or `<Out()> ByRef` (Visual Basic):</span></span>  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 <span data-ttu-id="20740-161">在数据库中生成和创建程序集之后，将用以下 Transact-SQL 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建存储过程，该 Transact-SQL 指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型 `int` 作为 OUTPUT 参数：</span><span class="sxs-lookup"><span data-stu-id="20740-161">After the assembly is built and created in the database, the stored procedure is created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the following Transact-SQL, which specifies a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of `int` as an OUTPUT parameter:</span></span>  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 <span data-ttu-id="20740-162">调用 CLR 存储过程时，`SqlInt32` 数据类型将自动转换到 `int` 数据类型，并返回到调用程序。</span><span class="sxs-lookup"><span data-stu-id="20740-162">When the CLR stored procedure is called, the `SqlInt32` data type is automatically converted to an `int` data type, and returned to the calling program.</span></span>  
  
 <span data-ttu-id="20740-163">但是，并非所有 CLR 数据类型都可以通过 out 参数自动转换到其等效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="20740-163">Not all CLR data types can be automatically converted to their equivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types through an out parameter, however.</span></span> <span data-ttu-id="20740-164">下表列出了这些例外类型。</span><span class="sxs-lookup"><span data-stu-id="20740-164">The following table lists these exceptions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="20740-165">**CLR 数据类型 (SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="20740-165">**CLR data type (SQL Server)**</span></span>|<span data-ttu-id="20740-166">**SQL Server 数据类型**</span><span class="sxs-lookup"><span data-stu-id="20740-166">**SQL Server data type**</span></span>|  
|`Decimal`|<span data-ttu-id="20740-167">smallmoney</span><span class="sxs-lookup"><span data-stu-id="20740-167">smallmoney</span></span>|  
|`SqlMoney`|<span data-ttu-id="20740-168">smallmoney</span><span class="sxs-lookup"><span data-stu-id="20740-168">smallmoney</span></span>|  
|`Decimal`|<span data-ttu-id="20740-169">money</span><span class="sxs-lookup"><span data-stu-id="20740-169">money</span></span>|  
|`DateTime`|<span data-ttu-id="20740-170">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="20740-170">smalldatetime</span></span>|  
|`SQLDateTime`|<span data-ttu-id="20740-171">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="20740-171">smalldatetime</span></span>|  
  
## <a name="change-history"></a><span data-ttu-id="20740-172">更改历史记录</span><span class="sxs-lookup"><span data-stu-id="20740-172">Change History</span></span>  
  
|<span data-ttu-id="20740-173">更新的内容</span><span class="sxs-lookup"><span data-stu-id="20740-173">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="20740-174">将 `SqlGeography`、`SqlGeometry` 和 `SqlHierarchyId` 类型添加到了映射表。</span><span class="sxs-lookup"><span data-stu-id="20740-174">Added `SqlGeography`, `SqlGeometry`, and `SqlHierarchyId` types to the mapping table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20740-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20740-175">See Also</span></span>  
 [<span data-ttu-id="20740-176">.NET Framework 中的 SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="20740-176">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
