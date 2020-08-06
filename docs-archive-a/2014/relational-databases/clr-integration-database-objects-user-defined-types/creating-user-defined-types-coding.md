---
title: 编写用户定义类型的代码 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [CLR integration]
- UDTs [CLR integration], coding
- UserDefined serialization format [CLR integration]
- Point UDT
- Parse method
- null values [CLR integration]
- ToString method
- ValidatePoint method
- attributes [CLR integration]
- coding user-defined types [CLR integration]
- Read method
- Write method
- nullability [CLR integration]
- user-defined types [CLR integration], coding
- Currency UDT
- validating UDT values
- exposing UDT properties [CLR integration]
ms.assetid: 1e5b43b3-4971-45ee-a591-3f535e2ac722
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e88c4d8162e5c7c921f5c5062f5b3c23df40a2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578911"
---
# <a name="coding-user-defined-types"></a><span data-ttu-id="be439-102">用户定义类型编码</span><span class="sxs-lookup"><span data-stu-id="be439-102">Coding User-Defined Types</span></span>
  <span data-ttu-id="be439-103">编写用户定义类型 (UDT) 的定义时，必须根据是要将 UDT 作为类还是作为结构实现以及您所选择的格式和序列化选项来实现各种功能。</span><span class="sxs-lookup"><span data-stu-id="be439-103">When coding your user-defined type (UDT) definition, you must implement various features, depending on whether you are implementing the UDT as a class or a structure, as well as on the format and serialization options you have chosen.</span></span>  
  
 <span data-ttu-id="be439-104">本节中的示例说明了如何将 `Point` UDT 作为 `struct`（在 Visual Basic 中为 `Structure`）实现。</span><span class="sxs-lookup"><span data-stu-id="be439-104">The example in this section illustrates implementing a `Point` UDT as a `struct` (or `Structure` in Visual Basic).</span></span> <span data-ttu-id="be439-105">`Point` UDT 由作为属性过程实现的 X 和 Y 坐标组成。</span><span class="sxs-lookup"><span data-stu-id="be439-105">The `Point` UDT consists of X and Y coordinates implemented as property procedures.</span></span>  
  
 <span data-ttu-id="be439-106">定义 UDT 时需要下列命名空间：</span><span class="sxs-lookup"><span data-stu-id="be439-106">The following namespaces are required when defining a UDT:</span></span>  
  
```vb  
Imports System  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
```  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
```  
  
 <span data-ttu-id="be439-107">`Microsoft.SqlServer.Server` 命名空间包含 UDT 的各种属性所需的对象，`System.Data.SqlTypes` 命名空间包含表示程序集可用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机数据类型的类。</span><span class="sxs-lookup"><span data-stu-id="be439-107">The `Microsoft.SqlServer.Server` namespace contains the objects required for various attributes of your UDT, and the `System.Data.SqlTypes` namespace contains the classes that represent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types available to the assembly.</span></span> <span data-ttu-id="be439-108">当然，还可能存在程序集正常运行所需的其他命名空间。</span><span class="sxs-lookup"><span data-stu-id="be439-108">There may of course be additional namespaces that your assembly requires in order to function correctly.</span></span> <span data-ttu-id="be439-109">`Point` UDT 还使用 `System.Text` 命名空间来处理字符串。</span><span class="sxs-lookup"><span data-stu-id="be439-109">The `Point` UDT also uses the `System.Text` namespace for working with strings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be439-110">不再支持执行使用 `/clr:pure` 编译的 Visual C++ 数据库对象（例如 UDT）。</span><span class="sxs-lookup"><span data-stu-id="be439-110">Visual C++ database objects, such as UDTs, compiled with `/clr:pure` are not supported for execution.</span></span>  
  
## <a name="specifying-attributes"></a><span data-ttu-id="be439-111">指定属性</span><span class="sxs-lookup"><span data-stu-id="be439-111">Specifying Attributes</span></span>  
 <span data-ttu-id="be439-112">属性确定如何使用序列化来构造 UDT 的存储表示形式以及如何按值将 UDT 传输到客户端。</span><span class="sxs-lookup"><span data-stu-id="be439-112">Attributes determine how serialization is used to construct the storage representation of UDTs and to transmit UDTs by value to the client.</span></span>  
  
 <span data-ttu-id="be439-113">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 是必需的。</span><span class="sxs-lookup"><span data-stu-id="be439-113">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` is required.</span></span> <span data-ttu-id="be439-114">`Serializable` 属性是可选项。</span><span class="sxs-lookup"><span data-stu-id="be439-114">The `Serializable` attribute is optional.</span></span> <span data-ttu-id="be439-115">您也可以指定 `Microsoft.SqlServer.Server.SqlFacetAttribute` 以提供有关 UDT 的返回类型的信息。</span><span class="sxs-lookup"><span data-stu-id="be439-115">You can also specify the `Microsoft.SqlServer.Server.SqlFacetAttribute` to provide information about the return type of a UDT.</span></span> <span data-ttu-id="be439-116">有关详细信息，请参阅 [CLR 例程的自定义属性](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)。</span><span class="sxs-lookup"><span data-stu-id="be439-116">For more information, see [Custom Attributes for CLR Routines](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).</span></span>  
  
### <a name="point-udt-attributes"></a><span data-ttu-id="be439-117">Point UDT 属性</span><span class="sxs-lookup"><span data-stu-id="be439-117">Point UDT Attributes</span></span>  
 <span data-ttu-id="be439-118">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 将 `Point` UDT 的存储格式设置为 `Native`。</span><span class="sxs-lookup"><span data-stu-id="be439-118">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` sets the storage format for the `Point` UDT to `Native`.</span></span> <span data-ttu-id="be439-119">`IsByteOrdered` 设置为 `true`，这样可以保证在 SQL Server 中的比较结果相同，就像在托管代码中进行相同的比较一样。</span><span class="sxs-lookup"><span data-stu-id="be439-119">`IsByteOrdered` is set to `true`, which guarantees that the results of comparisons are the same in SQL Server as if the same comparison had taken place in managed code.</span></span> <span data-ttu-id="be439-120">UDT 实现 `System.Data.SqlTypes.INullable` 接口以使 UDT 能够识别 Null 值。</span><span class="sxs-lookup"><span data-stu-id="be439-120">The UDT implements the `System.Data.SqlTypes.INullable` interface to make the UDT null aware.</span></span>  
  
 <span data-ttu-id="be439-121">下面的代码段显示了 `Point` UDT 的属性。</span><span class="sxs-lookup"><span data-stu-id="be439-121">The following code fragment shows the attributes for the `Point` UDT.</span></span>  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True)> _  
  Public Structure Point  
    Implements INullable  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true)]  
public struct Point : INullable  
{  
```  
  
## <a name="implementing-nullability"></a><span data-ttu-id="be439-122">实现为 Null 性</span><span class="sxs-lookup"><span data-stu-id="be439-122">Implementing Nullability</span></span>  
 <span data-ttu-id="be439-123">除了为您的程序集正确指定属性外，UDT 还必须支持为 Null 性。</span><span class="sxs-lookup"><span data-stu-id="be439-123">In addition to specifying the attributes for your assemblies correctly, your UDT must also support nullability.</span></span> <span data-ttu-id="be439-124">加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 UDT 是能够识别 Null 的，但为使 UDT 识别 Null 值，UDT 必须实现 `System.Data.SqlTypes.INullable` 接口。</span><span class="sxs-lookup"><span data-stu-id="be439-124">UDTs loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are null-aware, but in order for the UDT to recognize a null value, the UDT must implement the `System.Data.SqlTypes.INullable` interface.</span></span>  
  
 <span data-ttu-id="be439-125">您必须创建一个名为 `IsNull` 的属性，需要该属性才能从 CLR 代码中确定一个值是否为 Null。</span><span class="sxs-lookup"><span data-stu-id="be439-125">You must create a property named `IsNull`, which is needed to determine whether a value is null from within CLR code.</span></span> <span data-ttu-id="be439-126">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发现 UDT 的 Null 实例时，会使用正常的 Null 处理方法来保留 UDT。</span><span class="sxs-lookup"><span data-stu-id="be439-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finds a null instance of a UDT, the UDT is persisted using normal null-handling methods.</span></span> <span data-ttu-id="be439-127">如果服务器不必序列化或反序列化 UDT，它不会在这些方面浪费时间；此外，它也不会浪费空间来存储 Null UDT。</span><span class="sxs-lookup"><span data-stu-id="be439-127">The server does not waste time serializing or deserializing the UDT if it does not have to, and it does not waste space to store a null UDT.</span></span> <span data-ttu-id="be439-128">每次从 CLR 中引入 UDT 时都会执行这种 Null 检查，也就是说，始终都应可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL 构造来检查有无 Null UDT。</span><span class="sxs-lookup"><span data-stu-id="be439-128">This check for nulls is performed every time a UDT is brought over from the CLR, which means that using the [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL construct to check for null UDTs should always work.</span></span> <span data-ttu-id="be439-129">服务器也使用 `IsNull` 属性来测试实例是否为 Null。</span><span class="sxs-lookup"><span data-stu-id="be439-129">The `IsNull` property is also used by the server to test whether an instance is null.</span></span> <span data-ttu-id="be439-130">一旦服务器确定 UDT 为 Null，它便可以使用其本机 Null 处理方法。</span><span class="sxs-lookup"><span data-stu-id="be439-130">Once the server determines that the UDT is null, it can use its native null handling.</span></span>  
  
 <span data-ttu-id="be439-131">`get()` 的 `IsNull` 方法绝非特殊。</span><span class="sxs-lookup"><span data-stu-id="be439-131">The `get()` method of `IsNull` is not special-cased in any way.</span></span> <span data-ttu-id="be439-132">如果 `Point` 变量 `@p` 为 `Null`，则默认情况下 `@p.IsNull` 的计算结果将为“NULL”而不是“1”。</span><span class="sxs-lookup"><span data-stu-id="be439-132">If a `Point` variable `@p` is `Null`, then `@p.IsNull` will, by default, evaluate to "NULL", not "1".</span></span> <span data-ttu-id="be439-133">这是因为 `SqlMethod(OnNullCall)` 方法的 `IsNull get()` 属性默认为 False。</span><span class="sxs-lookup"><span data-stu-id="be439-133">This is because the `SqlMethod(OnNullCall)` attribute of the `IsNull get()` method defaults to false.</span></span> <span data-ttu-id="be439-134">因为对象为 `Null`，因此请求属性时，不会反序列化该对象，不会调用该方法，而且会返回默认值“NULL”。</span><span class="sxs-lookup"><span data-stu-id="be439-134">Because the object is `Null`, when the property is requested the object is not deserialized, the method is not called, and a default value of "NULL" is returned.</span></span>  
  
### <a name="example"></a><span data-ttu-id="be439-135">示例</span><span class="sxs-lookup"><span data-stu-id="be439-135">Example</span></span>  
 <span data-ttu-id="be439-136">在下面的示例中，`is_Null` 变量是私有的并且保存了 UDT 实例的 Null 状态。</span><span class="sxs-lookup"><span data-stu-id="be439-136">In the following example, the `is_Null` variable is private and holds the state of null for the instance of the UDT.</span></span> <span data-ttu-id="be439-137">您的代码必须保留 `is_Null` 的相应值。</span><span class="sxs-lookup"><span data-stu-id="be439-137">Your code must maintain an appropriate value for `is_Null`.</span></span> <span data-ttu-id="be439-138">UDT 还必须具有一个名为 `Null` 的静态属性，该属性返回 UDT 的 Null 值实例。</span><span class="sxs-lookup"><span data-stu-id="be439-138">The UDT must also have a static property named `Null` that returns a null value instance of the UDT.</span></span> <span data-ttu-id="be439-139">这样，如果该实例在数据库中确实为 Null，UDT 便可返回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="be439-139">This allows the UDT to return a null value if the instance is indeed null in the database.</span></span>  
  
```vb  
Private is_Null As Boolean  
  
Public ReadOnly Property IsNull() As Boolean _  
   Implements INullable.IsNull  
    Get  
        Return (is_Null)  
    End Get  
End Property  
  
Public Shared ReadOnly Property Null() As Point  
    Get  
        Dim pt As New Point  
        pt.is_Null = True  
        Return (pt)  
    End Get  
End Property  
```  
  
```csharp  
private bool is_Null;  
  
public bool IsNull  
{  
    get  
    {  
        return (is_Null);  
    }  
}  
  
public static Point Null  
{  
    get  
    {  
        Point pt = new Point();  
        pt.is_Null = true;  
        return pt;  
    }  
}  
```  
  
### <a name="is-null-vs-isnull"></a><span data-ttu-id="be439-140">IS NULL 与 IsNull 的比较</span><span class="sxs-lookup"><span data-stu-id="be439-140">IS NULL vs. IsNull</span></span>  
 <span data-ttu-id="be439-141">假定有一个表包含架构 Points(id int, location Point)，其中 `Point` 为 CLR UDT，并且有如下查询：</span><span class="sxs-lookup"><span data-stu-id="be439-141">Consider a table that contains the schema Points(id int, location Point), where `Point` is a CLR UDT, and the following queries:</span></span>  
  
```  
--Query 1  
SELECT ID  
FROM Points  
WHERE NOT (location IS NULL) -- Or, WHERE location IS NOT NULL;  
```  
  
```  
--Query 2:  
SELECT ID  
FROM Points  
WHERE location.IsNull = 0;  
```  
  
 <span data-ttu-id="be439-142">这两个查询都返回具有非 `Null` 位置的点的 ID。</span><span class="sxs-lookup"><span data-stu-id="be439-142">Both queries return the IDs of points with non-`Null` locations.</span></span> <span data-ttu-id="be439-143">在 Query 1 中，使用的是正常 Null 处理方法，不需要反序列化 UDT。</span><span class="sxs-lookup"><span data-stu-id="be439-143">In Query 1, normal null-handling is used, and there no deserialization of UDTs is required.</span></span> <span data-ttu-id="be439-144">另一方面，Query 2 必须反序列化每个非 `Null` 对象并调入 CLR 以获取 `IsNull` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="be439-144">Query 2, on the other hand, has to deserialize each non-`Null` object and call into the CLR to obtain the value of the `IsNull` property.</span></span> <span data-ttu-id="be439-145">显然，使用 `IS NULL` 会产生更高的性能，并且始终都不应从 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码中读取 UDT 的 `IsNull` 属性。</span><span class="sxs-lookup"><span data-stu-id="be439-145">Clearly, using `IS NULL` will exhibit better performance and there should never be a reason to read the `IsNull` property of a UDT from [!INCLUDE[tsql](../../includes/tsql-md.md)] code.</span></span>  
  
 <span data-ttu-id="be439-146">那么，`IsNull` 属性的用途是什么？</span><span class="sxs-lookup"><span data-stu-id="be439-146">So, what is the use of the `IsNull` property?</span></span> <span data-ttu-id="be439-147">首先，从 CLR 代码中确定值是否为 `Null` 时需要它。</span><span class="sxs-lookup"><span data-stu-id="be439-147">First, it is needed to determine whether a value is `Null` from within CLR code.</span></span> <span data-ttu-id="be439-148">其次，服务器需要使用一种方法来测试实例是否为 `Null`，因此服务器会使用该属性。</span><span class="sxs-lookup"><span data-stu-id="be439-148">Second, the server needs a way to test whether an instance is `Null`, so this property is used by the server.</span></span> <span data-ttu-id="be439-149">服务器确定该实例为 `Null` 之后，便可以使用其本机 Null 处理方法对该实例进行处理。</span><span class="sxs-lookup"><span data-stu-id="be439-149">After it determines it is `Null`, then it can use its native null handling to handle it.</span></span>  
  
## <a name="implementing-the-parse-method"></a><span data-ttu-id="be439-150">实现 Parse 方法</span><span class="sxs-lookup"><span data-stu-id="be439-150">Implementing the Parse Method</span></span>  
 <span data-ttu-id="be439-151">`Parse` 和 `ToString` 方法用于转换成 UDT 的字符串表示形式和从 UDT 的字符串表示形式进行转换。</span><span class="sxs-lookup"><span data-stu-id="be439-151">The `Parse` and `ToString` methods allow for conversions to and from string representations of the UDT.</span></span> <span data-ttu-id="be439-152">`Parse` 方法允许字符串转换为 UDT。</span><span class="sxs-lookup"><span data-stu-id="be439-152">The `Parse` method allows a string to be converted into a UDT.</span></span> <span data-ttu-id="be439-153">它必须声明为 `static`（在 Visual Basic 中则为 `Shared`），并且采用 `System.Data.SqlTypes.SqlString` 类型的参数。</span><span class="sxs-lookup"><span data-stu-id="be439-153">It must be declared as `static` (or `Shared` in Visual Basic), and take a parameter of type `System.Data.SqlTypes.SqlString`.</span></span>  
  
 <span data-ttu-id="be439-154">下面的代码实现了 `Parse` UDT 的 `Point` 方法，该方法将 X 坐标和 Y 坐标分隔开。</span><span class="sxs-lookup"><span data-stu-id="be439-154">The following code implements the `Parse` method for the `Point` UDT, which separates out the X and Y coordinates.</span></span> <span data-ttu-id="be439-155">`Parse` 具有一个 `System.Data.SqlTypes.SqlString` 类型的参数，并假定以逗号分隔字符串的形式提供 X 和 Y 值。</span><span class="sxs-lookup"><span data-stu-id="be439-155">The `Parse` method has a single argument of type `System.Data.SqlTypes.SqlString`, and assumes that X and Y values are supplied as a comma-delimited string.</span></span> <span data-ttu-id="be439-156">将 `Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` 属性设置为 `false` 可防止从 Point 的 Null 实例中调用 `Parse` 方法。</span><span class="sxs-lookup"><span data-stu-id="be439-156">Setting the `Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` attribute to `false` prevents the `Parse` method from being called from a null instance of Point.</span></span>  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
    return pt;  
}  
```  
  
## <a name="implementing-the-tostring-method"></a><span data-ttu-id="be439-157">实现 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="be439-157">Implementing the ToString Method</span></span>  
 <span data-ttu-id="be439-158">`ToString` 方法用于将 `Point` UDT 转换为字符串值。</span><span class="sxs-lookup"><span data-stu-id="be439-158">The `ToString` method converts the `Point` UDT to a string value.</span></span> <span data-ttu-id="be439-159">在此情况下，对于 `Point` 类型的 Null 实例，将返回字符串“NULL”。</span><span class="sxs-lookup"><span data-stu-id="be439-159">In this case, the string "NULL" is returned for a Null instance of the `Point` type.</span></span> <span data-ttu-id="be439-160">`ToString` 方法执行的操作与 `Parse` 方法相反，它使用 `System.Text.StringBuilder` 返回由 X 和 Y 坐标值组成的逗号分隔 `System.String`。</span><span class="sxs-lookup"><span data-stu-id="be439-160">The `ToString` method reverses the `Parse` method by using a `System.Text.StringBuilder` to return a comma-delimited `System.String` consisting of the X and Y coordinate values.</span></span> <span data-ttu-id="be439-161">由于**InvokeIfReceiverIsNull**默认为 false，因此不需要检查的 null 实例 `Point` 。</span><span class="sxs-lookup"><span data-stu-id="be439-161">Because **InvokeIfReceiverIsNull** defaults to false, the check for a null instance of `Point` is unnecessary.</span></span>  
  
```vb  
Private _x As Int32  
Private _y As Int32  
  
Public Overrides Function ToString() As String  
    If Me.IsNull Then  
        Return "NULL"  
    Else  
        Dim builder As StringBuilder = New StringBuilder  
        builder.Append(_x)  
        builder.Append(",")  
        builder.Append(_y)  
        Return builder.ToString  
    End If  
End Function  
```  
  
```csharp  
private Int32 _x;  
private Int32 _y;  
  
public override string ToString()  
{  
    if (this.IsNull)  
        return "NULL";  
    else  
    {  
        StringBuilder builder = new StringBuilder();  
        builder.Append(_x);  
        builder.Append(",");  
        builder.Append(_y);  
        return builder.ToString();  
    }  
}  
```  
  
## <a name="exposing-udt-properties"></a><span data-ttu-id="be439-162">公开 UDT 属性</span><span class="sxs-lookup"><span data-stu-id="be439-162">Exposing UDT Properties</span></span>  
 <span data-ttu-id="be439-163">`Point` UDT 公开了作为 `System.Int32` 类型的公共读写属性实现的 X 和 Y 坐标。</span><span class="sxs-lookup"><span data-stu-id="be439-163">The `Point` UDT exposes X and Y coordinates that are implemented as public read-write properties of type `System.Int32`.</span></span>  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _x = Value  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _y = Value  
    End Set  
End Property  
```  
  
```csharp  
public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    set   
    {  
        _x = value;  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        _y = value;  
    }  
}  
```  
  
## <a name="validating-udt-values"></a><span data-ttu-id="be439-164">验证 UDT 值</span><span class="sxs-lookup"><span data-stu-id="be439-164">Validating UDT Values</span></span>  
 <span data-ttu-id="be439-165">处理 UDT 数据时，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]会自动将二进制值转换为 UDT 值。</span><span class="sxs-lookup"><span data-stu-id="be439-165">When working with UDT data, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] automatically converts binary values to UDT values.</span></span> <span data-ttu-id="be439-166">该转换过程包括检查值是否符合类型的序列化格式和确保可以正确地反序列化值。</span><span class="sxs-lookup"><span data-stu-id="be439-166">This conversion process involves checking that values are appropriate for the serialization format of the type and ensuring that the value can be deserialized correctly.</span></span> <span data-ttu-id="be439-167">这样就确保了值可以转换回二进制形式。</span><span class="sxs-lookup"><span data-stu-id="be439-167">This ensures that the value can be converted back to binary form.</span></span> <span data-ttu-id="be439-168">对于采用字节顺序的 UDT，这样还可以确保产生的二进制值与原始二进制值匹配。</span><span class="sxs-lookup"><span data-stu-id="be439-168">In the case of byte-ordered UDTs, this also ensures that the resulting binary value matches the original binary value.</span></span> <span data-ttu-id="be439-169">这会防止在数据库中保留无效值。</span><span class="sxs-lookup"><span data-stu-id="be439-169">This prevents invalid values from being persisted in the database.</span></span> <span data-ttu-id="be439-170">在某些情况下，只进行这种级别的检查可能是不够的。</span><span class="sxs-lookup"><span data-stu-id="be439-170">In some cases, this level of checking may be inadequate.</span></span> <span data-ttu-id="be439-171">当要求 UDT 值在预期的域或范围之内时可能需要进行其他验证。</span><span class="sxs-lookup"><span data-stu-id="be439-171">Additional validation may be required when UDT values are required to be in an expected domain or range.</span></span> <span data-ttu-id="be439-172">例如，实现日期的 UDT 可能要求日值为特定的有效值范围内的正数。</span><span class="sxs-lookup"><span data-stu-id="be439-172">For example, a UDT that implements a date might require the day value to be a positive number that falls within a certain range of valid values.</span></span>  
  
 <span data-ttu-id="be439-173">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName` 的 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 属性可用于提供在将数据分配给 UDT 或转换为 UDT 时服务器运行的验证方法的名称。</span><span class="sxs-lookup"><span data-stu-id="be439-173">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` allows you to supply the name of a validation method that the server runs when data is assigned to a UDT or converted to a UDT.</span></span> <span data-ttu-id="be439-174">运行 bcp 实用工具、BULK INSERT、DBCC CHECKDB、DBCC CHECKFILEGROUP、DBCC CHECKTABLE、分布式查询和表格格式数据流 (TDS) 远程过程调用 (RPC) 操作期间也会调用 `ValidationMethodName`。</span><span class="sxs-lookup"><span data-stu-id="be439-174">`ValidationMethodName` is also called during the running of the bcp utility, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, distributed query, and tabular data stream (TDS) remote procedure call (RPC) operations.</span></span> <span data-ttu-id="be439-175">`ValidationMethodName` 的默认值为 Null，表示没有验证方法。</span><span class="sxs-lookup"><span data-stu-id="be439-175">The default value for `ValidationMethodName` is null, indicating that there is no validation method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="be439-176">示例</span><span class="sxs-lookup"><span data-stu-id="be439-176">Example</span></span>  
 <span data-ttu-id="be439-177">下面的代码段显示了 `Point` 类的声明，该声明指定了 `ValidationMethodName` 的 `ValidatePoint`。</span><span class="sxs-lookup"><span data-stu-id="be439-177">The following code fragment shows the declaration for the `Point` class, which specifies a `ValidationMethodName` of `ValidatePoint`.</span></span>  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True, _  
  ValidationMethodName:="ValidatePoint")> _  
  Public Structure Point  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true,   
  ValidationMethodName = "ValidatePoint")]  
public struct Point : INullable  
{  
```  
  
 <span data-ttu-id="be439-178">如果指定了验证方法，则必须具有如下面的代码段所示的签名。</span><span class="sxs-lookup"><span data-stu-id="be439-178">If a validation method is specified, it must have a signature that looks like the following code fragment.</span></span>  
  
```vb  
Private Function ValidationFunction() As Boolean  
    If (validation logic here) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidationFunction()  
{  
    if (validation logic here)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
 <span data-ttu-id="be439-179">验证方法可具有任意作用域，如果值有效，它应返回 `true`，否则应返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="be439-179">The validation method can have any scope and should return `true` if the value is valid, and `false` otherwise.</span></span> <span data-ttu-id="be439-180">如果此方法返回 `false` 或引发异常，则该值将被视为无效并且会出现错误。</span><span class="sxs-lookup"><span data-stu-id="be439-180">If the method returns `false` or throws an exception, the value is treated as not valid and an error is raised.</span></span>  
  
 <span data-ttu-id="be439-181">在下面的示例中，代码仅允许零值或大于 X 和 Y 坐标的值。</span><span class="sxs-lookup"><span data-stu-id="be439-181">In the example below, the code allows only values of zero or greater the X and Y coordinates.</span></span>  
  
```vb  
Private Function ValidatePoint() As Boolean  
    If (_x >= 0) And (_y >= 0) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidatePoint()  
{  
    if ((_x >= 0) && (_y >= 0))  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
### <a name="validation-method-limitations"></a><span data-ttu-id="be439-182">验证方法限制</span><span class="sxs-lookup"><span data-stu-id="be439-182">Validation Method Limitations</span></span>  
 <span data-ttu-id="be439-183">服务器是在执行转换时调用验证方法，而不是在通过设置个别属性插入数据时或在使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT 语句插入数据时调用验证方法。</span><span class="sxs-lookup"><span data-stu-id="be439-183">The server calls the validation method when the server is performing conversions, not when data is inserted by setting individual properties or when data is inserted using a [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT statement.</span></span>  
  
 <span data-ttu-id="be439-184">`Parse`如果希望在所有情况下都执行验证方法，则必须从属性 setter 和方法中显式调用验证方法。</span><span class="sxs-lookup"><span data-stu-id="be439-184">You must explicitly call the validation method from property setters and the `Parse` method if you want the validation method to execute in all situations.</span></span> <span data-ttu-id="be439-185">并不要求这样做，在某些情况下可能甚至不需要这样做。</span><span class="sxs-lookup"><span data-stu-id="be439-185">This is not a requirement, and in some cases may not even be desirable.</span></span>  
  
### <a name="parse-validation-example"></a><span data-ttu-id="be439-186">Parse 验证示例</span><span class="sxs-lookup"><span data-stu-id="be439-186">Parse Validation Example</span></span>  
 <span data-ttu-id="be439-187">若要确保 `ValidatePoint` 在类中调用方法 `Point` ，必须从 `Parse` 方法和设置 X 和 Y 坐标值的属性过程中调用它。</span><span class="sxs-lookup"><span data-stu-id="be439-187">To ensure that the `ValidatePoint` method is invoked in the `Point` class, you must call it from the `Parse` method and from the property procedures that set the X and Y coordinate values.</span></span> <span data-ttu-id="be439-188">下面的代码段演示如何 `ValidatePoint` 从函数调用验证方法 `Parse` 。</span><span class="sxs-lookup"><span data-stu-id="be439-188">The following code fragment shows how to call the `ValidatePoint` validation method from the `Parse` function.</span></span>  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
  
    ' Call ValidatePoint to enforce validation  
    ' for string conversions.  
    If Not pt.ValidatePoint() Then  
        Throw New ArgumentException("Invalid XY coordinate values.")  
    End If  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
  
    // Call ValidatePoint to enforce validation  
    // for string conversions.  
    if (!pt.ValidatePoint())   
        throw new ArgumentException("Invalid XY coordinate values.");  
    return pt;  
}  
```  
  
### <a name="property-validation-example"></a><span data-ttu-id="be439-189">属性验证示例</span><span class="sxs-lookup"><span data-stu-id="be439-189">Property Validation Example</span></span>  
 <span data-ttu-id="be439-190">下面的代码段演示如何 `ValidatePoint` 从设置 X 和 Y 坐标的属性过程调用验证方法。</span><span class="sxs-lookup"><span data-stu-id="be439-190">The following code fragment shows how to call the `ValidatePoint` validation method from the property procedures that set the X and Y coordinates.</span></span>  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _x  
        _x = Value  
        If Not ValidatePoint() Then  
            _x = temp  
            Throw New ArgumentException("Invalid X coordinate value.")  
        End If  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _y  
        _y = Value  
        If Not ValidatePoint() Then  
            _y = temp  
            Throw New ArgumentException("Invalid Y coordinate value.")  
        End If  
    End Set  
End Property  
```  
  
```csharp  
    public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    // Call ValidatePoint to ensure valid range of Point values.  
    set   
    {  
        Int32 temp = _x;  
        _x = value;  
        if (!ValidatePoint())  
        {  
            _x = temp;  
            throw new ArgumentException("Invalid X coordinate value.");  
        }  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        Int32 temp = _y;  
        _y = value;  
        if (!ValidatePoint())  
        {  
            _y = temp;  
            throw new ArgumentException("Invalid Y coordinate value.");  
        }  
    }  
}  
```  
  
## <a name="coding-udt-methods"></a><span data-ttu-id="be439-191">UDT 方法编码</span><span class="sxs-lookup"><span data-stu-id="be439-191">Coding UDT Methods</span></span>  
 <span data-ttu-id="be439-192">编写 UDT 方法时，请考虑所用的算法是否可能会随时间的推移而改变。</span><span class="sxs-lookup"><span data-stu-id="be439-192">When coding UDT methods, consider whether the algorithm used could possibly change over time.</span></span> <span data-ttu-id="be439-193">如果可能改变的话，最好考虑为您的 UDT 所用的方法创建一个单独的类。</span><span class="sxs-lookup"><span data-stu-id="be439-193">If so, you may want to consider creating a separate class for the methods your UDT uses.</span></span> <span data-ttu-id="be439-194">如果算法发生变化，则可以使用新代码重新编译该类并将程序集加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，而不会影响 UDT。</span><span class="sxs-lookup"><span data-stu-id="be439-194">If the algorithm changes, you can recompile the class with the new code and load the assembly into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without affecting the UDT.</span></span> <span data-ttu-id="be439-195">在许多情况下，都可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 语句重新加载 UDT，但这可能会使现有数据出现问题。</span><span class="sxs-lookup"><span data-stu-id="be439-195">In many cases UDTs can be reloaded using the [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement, but that could potentially cause problems with existing data.</span></span> <span data-ttu-id="be439-196">例如， `Currency` **AdventureWorks**示例数据库中包含的 UDT 使用**ConvertCurrency**函数转换货币值，该函数在单独的类中实现。</span><span class="sxs-lookup"><span data-stu-id="be439-196">For example, the `Currency` UDT included with the **AdventureWorks** sample database uses a **ConvertCurrency** function to convert currency values, which is implemented in a separate class.</span></span> <span data-ttu-id="be439-197">在未来，转换算法可能会发生不可预知的变化，或者可能需要新的功能。</span><span class="sxs-lookup"><span data-stu-id="be439-197">It is possible that conversion algorithms may change in unpredictable ways in the future, or that new functionality may be required.</span></span> <span data-ttu-id="be439-198">在规划将来的更改时，将**ConvertCurrency**函数与 `Currency` UDT 实现分离可提供更大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="be439-198">Separating the **ConvertCurrency** function from the `Currency` UDT implementation provides greater flexibility when planning for future changes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="be439-199">示例</span><span class="sxs-lookup"><span data-stu-id="be439-199">Example</span></span>  
 <span data-ttu-id="be439-200">`Point`类包含三种用于计算距离的简单方法：**距离**、 **DistanceFrom**和**DistanceFromXY**。</span><span class="sxs-lookup"><span data-stu-id="be439-200">The `Point` class contains three simple methods for calculating distance: **Distance**, **DistanceFrom** and **DistanceFromXY**.</span></span> <span data-ttu-id="be439-201">每个方法均返回一个 `double`，分别计算的是从 `Point` 到零的距离，从指定点到 `Point` 的距离，以及从指定的 X 和 Y 坐标到 `Point` 的距离。</span><span class="sxs-lookup"><span data-stu-id="be439-201">Each returns a `double` calculating the distance from `Point` to zero, the distance from a specified point to `Point`, and the distance from specified X and Y coordinates to `Point`.</span></span> <span data-ttu-id="be439-202">每个调用**DistanceFromXY**的**距离**和**DistanceFrom** ，并演示如何对每个方法使用不同的参数。</span><span class="sxs-lookup"><span data-stu-id="be439-202">**Distance** and **DistanceFrom** each call **DistanceFromXY**, and demonstrate how to use different arguments for each method.</span></span>  
  
```vb  
' Distance from 0 to Point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function Distance() As Double  
    Return DistanceFromXY(0, 0)  
End Function  
  
' Distance from Point to the specified point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFrom(ByVal pFrom As Point) As Double  
    Return DistanceFromXY(pFrom.X, pFrom.Y)  
End Function  
  
' Distance from Point to the specified x and y values.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFromXY(ByVal ix As Int32, ByVal iy As Int32) _  
    As Double  
    Return Math.Sqrt(Math.Pow(ix - _x, 2.0) + Math.Pow(iy - _y, 2.0))  
End Function  
```  
  
```csharp  
// Distance from 0 to Point.  
[SqlMethod(OnNullCall = false)]  
public Double Distance()  
{  
    return DistanceFromXY(0, 0);  
}  
  
// Distance from Point to the specified point.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFrom(Point pFrom)  
{  
    return DistanceFromXY(pFrom.X, pFrom.Y);  
}  
  
// Distance from Point to the specified x and y values.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFromXY(Int32 iX, Int32 iY)  
{  
    return Math.Sqrt(Math.Pow(iX - _x, 2.0) + Math.Pow(iY - _y, 2.0));  
}  
```  
  
### <a name="using-sqlmethod-attributes"></a><span data-ttu-id="be439-203">使用 SqlMethod 属性</span><span class="sxs-lookup"><span data-stu-id="be439-203">Using SqlMethod Attributes</span></span>  
 <span data-ttu-id="be439-204">`Microsoft.SqlServer.Server.SqlMethodAttribute` 类提供了一些自定义属性，这些属性可用于标记方法定义以便指定 Null 调用行为的确定性以及指定方法是否为赋值函数。</span><span class="sxs-lookup"><span data-stu-id="be439-204">The `Microsoft.SqlServer.Server.SqlMethodAttribute` class provides custom attributes that can be used to mark method definitions in order to specify determinism, on null call behavior, and to specify whether a method is a mutator.</span></span> <span data-ttu-id="be439-205">使用的是这些属性的默认值，仅在需要非默认值时才使用自定义特性。</span><span class="sxs-lookup"><span data-stu-id="be439-205">Default values for these properties are assumed, and the custom attribute is only used when a non-default value is needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be439-206">`SqlMethodAttribute` 类继承自 `SqlFunctionAttribute` 类，因此 `SqlMethodAttribute` 继承了 `FillRowMethodName` 中的 `TableDefinition` 和 `SqlFunctionAttribute` 字段。</span><span class="sxs-lookup"><span data-stu-id="be439-206">The `SqlMethodAttribute` class inherits from the `SqlFunctionAttribute` class, so `SqlMethodAttribute` inherits the `FillRowMethodName` and `TableDefinition` fields from `SqlFunctionAttribute`.</span></span> <span data-ttu-id="be439-207">这意味着可以编写一个不属于此情况的表值方法。</span><span class="sxs-lookup"><span data-stu-id="be439-207">This implies that it is possible to write a table-valued method, which is not the case.</span></span> <span data-ttu-id="be439-208">方法会编译和程序集，但 `IEnumerable` 在运行时将引发有关返回类型的错误，并返回以下消息： " \<name> 程序集" "中类" "的方法、属性或字段" " \<class> \<assembly> 具有无效的返回类型。</span><span class="sxs-lookup"><span data-stu-id="be439-208">The method compiles and the assembly deploys, but an error about the `IEnumerable` return type is raised at runtime with the following message: "Method, property, or field '\<name>' in class '\<class>' in assembly '\<assembly>' has invalid return type."</span></span>  
  
 <span data-ttu-id="be439-209">下表说明了可以在 UDT 方法中使用的部分相关 `Microsoft.SqlServer.Server.SqlMethodAttribute` 属性，并列出了其默认值。</span><span class="sxs-lookup"><span data-stu-id="be439-209">The following table describes some of the relevant `Microsoft.SqlServer.Server.SqlMethodAttribute` properties that can be used in UDT methods, and lists their default values.</span></span>  
  
 <span data-ttu-id="be439-210">DataAccess</span><span class="sxs-lookup"><span data-stu-id="be439-210">DataAccess</span></span>  
 <span data-ttu-id="be439-211">指示函数是否需要访问存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地实例中的用户数据。</span><span class="sxs-lookup"><span data-stu-id="be439-211">Indicates whether the function involves access to user data stored in the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="be439-212">默认值为 `DataAccessKind`.`None`。</span><span class="sxs-lookup"><span data-stu-id="be439-212">Default is `DataAccessKind`.`None`.</span></span>  
  
 <span data-ttu-id="be439-213">IsDeterministic</span><span class="sxs-lookup"><span data-stu-id="be439-213">IsDeterministic</span></span>  
 <span data-ttu-id="be439-214">指示在输入值相同且数据库状态相同的情况下函数是否会生成相同的输出值。</span><span class="sxs-lookup"><span data-stu-id="be439-214">Indicates whether the function produces the same output values given the same input values and the same database state.</span></span> <span data-ttu-id="be439-215">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="be439-215">Default is `false`.</span></span>  
  
 <span data-ttu-id="be439-216">IsMutator</span><span class="sxs-lookup"><span data-stu-id="be439-216">IsMutator</span></span>  
 <span data-ttu-id="be439-217">指示方法是否在 UDT 实例中引起状态变化。</span><span class="sxs-lookup"><span data-stu-id="be439-217">Indicates whether the method causes a state change in the UDT instance.</span></span> <span data-ttu-id="be439-218">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="be439-218">Default is `false`.</span></span>  
  
 <span data-ttu-id="be439-219">IsPrecise</span><span class="sxs-lookup"><span data-stu-id="be439-219">IsPrecise</span></span>  
 <span data-ttu-id="be439-220">指示函数是否涉及不精确的计算，如浮点运算。</span><span class="sxs-lookup"><span data-stu-id="be439-220">Indicates whether the function involves imprecise computations, such as floating point operations.</span></span> <span data-ttu-id="be439-221">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="be439-221">Default is `false`.</span></span>  
  
 <span data-ttu-id="be439-222">OnNullCall</span><span class="sxs-lookup"><span data-stu-id="be439-222">OnNullCall</span></span>  
 <span data-ttu-id="be439-223">指示在指定 Null 引用输入参数时是否调用此方法。</span><span class="sxs-lookup"><span data-stu-id="be439-223">Indicates whether the method is called when null reference input arguments are specified.</span></span> <span data-ttu-id="be439-224">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="be439-224">Default is `true`.</span></span>  
  
### <a name="example"></a><span data-ttu-id="be439-225">示例</span><span class="sxs-lookup"><span data-stu-id="be439-225">Example</span></span>  
 <span data-ttu-id="be439-226">使用 `Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` 属性可以标记允许 UDT 实例状态改变的方法。</span><span class="sxs-lookup"><span data-stu-id="be439-226">The `Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` property allows you to mark a method that allows a change in the state of an instance of a UDT.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="be439-227">不允许在一个 UPDATE 语句的 SET 子句中设置两个 UDT 属性。</span><span class="sxs-lookup"><span data-stu-id="be439-227">does not allow you to set two UDT properties in the SET clause of one UPDATE statement.</span></span> <span data-ttu-id="be439-228">然而，您可以将一个方法标记为更改两个成员的赋值函数。</span><span class="sxs-lookup"><span data-stu-id="be439-228">However, you can have a method marked as a mutator that changes the two members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be439-229">在查询中不允许使用赋值函数方法。</span><span class="sxs-lookup"><span data-stu-id="be439-229">Mutator methods are not allowed in queries.</span></span> <span data-ttu-id="be439-230">这些方法只能在赋值语句或数据修改语句中调用。</span><span class="sxs-lookup"><span data-stu-id="be439-230">They can be called only in assignment statements or data modification statements.</span></span> <span data-ttu-id="be439-231">如果标记为赋值函数的方法不返回 `void`（在 Visual Basic 中则是不为 `Sub`），则 CREATE TYPE 将失败并出错。</span><span class="sxs-lookup"><span data-stu-id="be439-231">If a method marked as mutator does not return `void` (or is not a `Sub` in Visual Basic), CREATE TYPE fails with an error.</span></span>  
  
 <span data-ttu-id="be439-232">下面的语句假定存在一个具有 `Triangles` 方法的 `Rotate` UDT。</span><span class="sxs-lookup"><span data-stu-id="be439-232">The following statement assumes the existence of a `Triangles` UDT that has a `Rotate` method.</span></span> <span data-ttu-id="be439-233">下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 更新语句调用该 `Rotate` 方法：</span><span class="sxs-lookup"><span data-stu-id="be439-233">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] update statement invokes the `Rotate` method:</span></span>  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 <span data-ttu-id="be439-234">`Rotate` 方法是使用将 `SqlMethod` 设置为 `IsMutator` 的 `true` 属性来修饰的，因此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以将该方法标记为赋值函数方法。</span><span class="sxs-lookup"><span data-stu-id="be439-234">The `Rotate` method is decorated with the `SqlMethod` attribute setting `IsMutator` to `true` so that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can mark the method as a mutator method.</span></span> <span data-ttu-id="be439-235">该代码还将 `OnNullCall` 设置为 `false`，这将向服务器指示，如果任何输入参数为 Null 引用，该方法将返回 Null 引用（在 Visual Basic 中为 `Nothing`）。</span><span class="sxs-lookup"><span data-stu-id="be439-235">The code also sets `OnNullCall` to `false`, which indicates to the server that the method returns a null reference (`Nothing` in Visual Basic) if any of the input parameters are null references.</span></span>  
  
```vb  
<SqlMethod(IsMutator:=True, OnNullCall:=False)> _  
Public Sub Rotate(ByVal anglex as Double, _  
  ByVal angley as Double, ByVal anglez As Double)   
   RotateX(anglex)  
   RotateY(angley)  
   RotateZ(anglez)  
End Sub  
```  
  
```csharp  
[SqlMethod(IsMutator = true, OnNullCall = false)]  
public void Rotate(double anglex, double angley, double anglez)   
{  
   RotateX(anglex);  
   RotateY(angley);  
   RotateZ(anglez);  
}  
```  
  
## <a name="implementing-a-udt-with-a-user-defined-format"></a><span data-ttu-id="be439-236">采用用户定义的格式实现 UDT</span><span class="sxs-lookup"><span data-stu-id="be439-236">Implementing a UDT with a User-Defined Format</span></span>  
 <span data-ttu-id="be439-237">采用用户定义的格式实现 UDT 时，必须实现 `Read` 和 `Write` 方法，这两个方法实现了 Microsoft.SqlServer.Server.IBinarySerialize 接口以处理 UDT 数据的序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="be439-237">When implementing a UDT with a user-defined format, you must implement `Read` and `Write` methods that implement the Microsoft.SqlServer.Server.IBinarySerialize interface to handle serializing and deserializing UDT data.</span></span> <span data-ttu-id="be439-238">还必须指定 `MaxByteSize` 的 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 属性。</span><span class="sxs-lookup"><span data-stu-id="be439-238">You must also specify the `MaxByteSize` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.</span></span>  
  
### <a name="the-currency-udt"></a><span data-ttu-id="be439-239">Currency UDT</span><span class="sxs-lookup"><span data-stu-id="be439-239">The Currency UDT</span></span>  
 <span data-ttu-id="be439-240">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 开始，随 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 安装的 CLR 示例附带了 `Currency` UDT。</span><span class="sxs-lookup"><span data-stu-id="be439-240">The `Currency` UDT is included with the CLR samples that can be installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="be439-241">`Currency` UDT 支持采用特定区域性的货币体系来处理货币金额。</span><span class="sxs-lookup"><span data-stu-id="be439-241">The `Currency` UDT supports handling amounts of money in the monetary system of a particular culture.</span></span> <span data-ttu-id="be439-242">您必须定义两个字段：一个表示 `string` 的 `CultureInfo`，用于指定货币的发行者（例如 en-us）；一个表示 `decimal` 的 `CurrencyValue`，即货币金额。</span><span class="sxs-lookup"><span data-stu-id="be439-242">You must define two fields: a `string` for `CultureInfo`, which specifies who issued the currency (en-us, for example) and a `decimal` for `CurrencyValue`, the amount of money.</span></span>  
  
 <span data-ttu-id="be439-243">尽管服务器并不使用它来执行比较，但 `Currency` UDT 实现了 `System.IComparable` 接口，该接口公开了一个方法 `System.IComparable.CompareTo`。</span><span class="sxs-lookup"><span data-stu-id="be439-243">Although it is not used by the server for performing comparisons, the `Currency` UDT implements the `System.IComparable` interface, which exposes a single method, `System.IComparable.CompareTo`.</span></span> <span data-ttu-id="be439-244">在需要精确比较或排序区域性中的货币值的情况下，在客户端会使用此方法。</span><span class="sxs-lookup"><span data-stu-id="be439-244">This is used on the client side in situations where it is desirable to accurately compare or order currency values within cultures.</span></span>  
  
 <span data-ttu-id="be439-245">在 CLR 中运行的代码将区域性与货币值分开比较。</span><span class="sxs-lookup"><span data-stu-id="be439-245">Code running in the CLR compares the culture separately from the currency value.</span></span> <span data-ttu-id="be439-246">对于 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码，通过执行下列操作来确定如何比较：</span><span class="sxs-lookup"><span data-stu-id="be439-246">For [!INCLUDE[tsql](../../includes/tsql-md.md)] code, the following actions determine the comparison:</span></span>  
  
1.  <span data-ttu-id="be439-247">将 `IsByteOrdered` 属性设置为 True，它指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用磁盘上的持久化二进制表示形式进行比较。</span><span class="sxs-lookup"><span data-stu-id="be439-247">Set the `IsByteOrdered` attribute to true, which tells [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use the persisted binary representation on disk for comparisons.</span></span>  
  
2.  <span data-ttu-id="be439-248">使用 `Write` UDT 的 `Currency` 方法确定 UDT 在磁盘上的保留方式，从而确定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 运算如何比较和排序 UDT 值。</span><span class="sxs-lookup"><span data-stu-id="be439-248">Use the `Write` method for the `Currency` UDT to determine how the UDT is persisted on disk and therefore how UDT values are compared and ordered for [!INCLUDE[tsql](../../includes/tsql-md.md)] operations.</span></span>  
  
3.  <span data-ttu-id="be439-249">采用以下二进制格式保存 `Currency` UDT：</span><span class="sxs-lookup"><span data-stu-id="be439-249">Save the `Currency` UDT using the following binary format:</span></span>  
  
    1.  <span data-ttu-id="be439-250">将区域性另存为 UTF-16 编码的字符串并用第 0-19 个字节表示，右侧以 Null 字符填充。</span><span class="sxs-lookup"><span data-stu-id="be439-250">Save the culture as a UTF-16 encoded string for bytes 0-19 with padding to the right with null characters.</span></span>  
  
    2.  <span data-ttu-id="be439-251">使用第 20 个字节及以后的字节包含货币的十进制值。</span><span class="sxs-lookup"><span data-stu-id="be439-251">Use bytes 20 and above to contain the decimal value of the currency.</span></span>  
  
 <span data-ttu-id="be439-252">填充的目的是为了确保区域性与货币值完全分开，以便在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码中将一个 UDT 与另一个 UDT 进行比较时，区域性字节与区域性字节相比较，货币字节值与货币字节值相比较。</span><span class="sxs-lookup"><span data-stu-id="be439-252">The purpose of the padding is to ensure that the culture is completely separated from the currency value, so that when one UDT is compared against another in [!INCLUDE[tsql](../../includes/tsql-md.md)] code, culture bytes are compared against culture bytes, and currency byte values are compared against currency byte values.</span></span>  
  
 <span data-ttu-id="be439-253">有关 UDT 的完整代码列表 `Currency` ，请按照[SQL Server 数据库引擎示例](https://msftengprodsamples.codeplex.com/)中有关安装 CLR 示例的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="be439-253">For the complete code listing for the `Currency` UDT, follow the directions for installing the CLR samples in [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).</span></span>  
  
### <a name="currency-attributes"></a><span data-ttu-id="be439-254">Currency 属性</span><span class="sxs-lookup"><span data-stu-id="be439-254">Currency Attributes</span></span>  
 <span data-ttu-id="be439-255">`Currency` UDT 定义有以下属性。</span><span class="sxs-lookup"><span data-stu-id="be439-255">The `Currency` UDT is defined with the following attributes.</span></span>  
  
```vb  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedType( _  
    Microsoft.SqlServer.Server.Format.UserDefined, _  
    IsByteOrdered:=True, MaxByteSize:=32), _  
    CLSCompliant(False)> _  
Public Structure Currency  
Implements INullable, IComparable, _  
Microsoft.SqlServer.Server.IBinarySerialize  
```  
  
```csharp  
[Serializable]  
[SqlUserDefinedType(Format.UserDefined,   
    IsByteOrdered = true, MaxByteSize = 32)]  
    [CLSCompliant(false)]  
    public struct Currency : INullable, IComparable, IBinarySerialize  
    {  
```  
  
## <a name="creating-read-and-write-methods-with-ibinaryserialize"></a><span data-ttu-id="be439-256">创建带有 IBinarySerialize 的 Read 和 Write 方法</span><span class="sxs-lookup"><span data-stu-id="be439-256">Creating Read and Write Methods with IBinarySerialize</span></span>  
 <span data-ttu-id="be439-257">当您选择 `UserDefined` 序列化格式时，还必须实现 `IBinarySerialize` 接口并创建您自己的 `Read` 和 `Write` 方法。</span><span class="sxs-lookup"><span data-stu-id="be439-257">When you choose `UserDefined` serialization format, you also must implement the `IBinarySerialize` interface and create your own `Read` and `Write` methods.</span></span> <span data-ttu-id="be439-258">`Currency` UDT 中的下列过程使用 `System.IO.BinaryReader` 和 `System.IO.BinaryWriter` 来从 UDT 中读取数据和向其中写入数据。</span><span class="sxs-lookup"><span data-stu-id="be439-258">The following procedures from the `Currency` UDT use the `System.IO.BinaryReader` and `System.IO.BinaryWriter` to read from and write to the UDT.</span></span>  
  
```vb  
' IBinarySerialize methods  
' The binary layout is as follow:  
'    Bytes 0 - 19: Culture name, padded to the right with null  
'    characters, UTF-16 encoded  
'    Bytes 20+: Decimal value of money  
' If the culture name is empty, the currency is null.  
Public Sub Write(ByVal w As System.IO.BinaryWriter) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
    If Me.IsNull Then  
        w.Write(nullMarker)  
        w.Write(System.Convert.ToDecimal(0))  
        Return  
    End If  
  
    If cultureName.Length > cultureNameMaxSize Then  
        Throw New ApplicationException(String.Format(CultureInfo.CurrentUICulture, _  
           "{0} is an invalid culture name for currency as it is too long.", cultureNameMaxSize))  
    End If  
  
    Dim paddedName As String = cultureName.PadRight(cultureNameMaxSize, CChar(vbNullChar))  
  
    For i As Integer = 0 To cultureNameMaxSize - 1  
        w.Write(paddedName(i))  
    Next i  
  
    ' Normalize decimal value to two places  
    currencyVal = Decimal.Floor(currencyVal * 100) / 100  
    w.Write(currencyVal)  
End Sub  
  
Public Sub Read(ByVal r As System.IO.BinaryReader) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
    Dim name As Char() = r.ReadChars(cultureNameMaxSize)  
    Dim stringEnd As Integer = Array.IndexOf(name, CChar(vbNullChar))  
  
    If stringEnd = 0 Then  
        cultureName = Nothing  
        Return  
    End If  
  
    cultureName = New String(name, 0, stringEnd)  
    currencyVal = r.ReadDecimal()  
End Sub  
  
```  
  
```csharp  
// IBinarySerialize methods  
// The binary layout is as follow:  
//    Bytes 0 - 19:Culture name, padded to the right   
//    with null characters, UTF-16 encoded  
//    Bytes 20+:Decimal value of money  
// If the culture name is empty, the currency is null.  
public void Write(System.IO.BinaryWriter w)  
{  
    if (this.IsNull)  
    {  
        w.Write(nullMarker);  
        w.Write((decimal)0);  
        return;  
    }  
  
    if (cultureName.Length > cultureNameMaxSize)  
    {  
        throw new ApplicationException(string.Format(  
            CultureInfo.InvariantCulture,   
            "{0} is an invalid culture name for currency as it is too long.",   
            cultureNameMaxSize));  
    }  
  
    String paddedName = cultureName.PadRight(cultureNameMaxSize, '\0');  
    for (int i = 0; i < cultureNameMaxSize; i++)  
    {  
        w.Write(paddedName[i]);  
    }  
  
    // Normalize decimal value to two places  
    currencyValue = Decimal.Floor(currencyValue * 100) / 100;  
    w.Write(currencyValue);  
}  
public void Read(System.IO.BinaryReader r)  
{  
    char[] name = r.ReadChars(cultureNameMaxSize);  
    int stringEnd = Array.IndexOf(name, '\0');  
  
    if (stringEnd == 0)  
    {  
        cultureName = null;  
        return;  
    }  
  
    cultureName = new String(name, 0, stringEnd);  
    currencyValue = r.ReadDecimal();  
}  
```  
  
 <span data-ttu-id="be439-259">有关 UDT 的完整代码列表 `Currency` ，请参阅[SQL Server 数据库引擎示例](https://msftengprodsamples.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="be439-259">For the complete code listing for the `Currency` UDT, see [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be439-260">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be439-260">See Also</span></span>  
 [<span data-ttu-id="be439-261">创建用户定义类型</span><span class="sxs-lookup"><span data-stu-id="be439-261">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
  
