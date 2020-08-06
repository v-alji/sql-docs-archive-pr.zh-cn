---
title: 用户定义的类型要求 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UDTs [CLR integration], requirements
- serialization
- Native serialization format [CLR integration]
- attributes [CLR integration]
- XML serialization [CLR integration]
- user-defined types [CLR integration], requirements
- user-defined serialization [CLR integration]
- user-defined types [CLR integration], Native serialization
- UDTs [CLR integration], Native serialization
ms.assetid: bedc3372-50eb-40f2-bcf2-d6db6a63b7e6
author: rothja
ms.author: jroth
ms.openlocfilehash: d4e692a4523829713cd95daf62374f84a74b6584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578910"
---
# <a name="user-defined-type-requirements"></a><span data-ttu-id="2d6e9-102">用户定义类型要求</span><span class="sxs-lookup"><span data-stu-id="2d6e9-102">User-Defined Type Requirements</span></span>
  <span data-ttu-id="2d6e9-103">创建用户定义类型时，必须做出几个重要的设计决策， (UDT) 才能在中安装 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-103">You must make several important design decisions when creating a user-defined type (UDT) to be installed in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d6e9-104">对于大多数 UDT，建议将 UDT 作为结构创建，尽管也可以选择将其作为类创建。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-104">For most UDTs, creating the UDT as a structure is recommended, although creating it as a class is also an option.</span></span> <span data-ttu-id="2d6e9-105">UDT 定义必须符合用于创建 UDT 的规范，以使其能够注册到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-105">The UDT definition must conform to the specifications for creating UDTs in order for it to be registered with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="requirements-for-implementing-udts"></a><span data-ttu-id="2d6e9-106">实现 UDT 的要求</span><span class="sxs-lookup"><span data-stu-id="2d6e9-106">Requirements for Implementing UDTs</span></span>  
 <span data-ttu-id="2d6e9-107">为了在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中运行，您的 UDT 必须实现 UDT 定义中的以下要求：</span><span class="sxs-lookup"><span data-stu-id="2d6e9-107">To run in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], your UDT must implement the following requirements in the UDT definition:</span></span>  
  
 <span data-ttu-id="2d6e9-108">该 UDT 必须指定 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-108">The UDT must specify the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.</span></span> <span data-ttu-id="2d6e9-109">`System.SerializableAttribute` 可选用，但建议使用。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-109">The use of the `System.SerializableAttribute` is optional, but recommended.</span></span>  
  
-   <span data-ttu-id="2d6e9-110">UDT 必须通过创建公共的 `System.Data.SqlTypes.INullable`（在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 中为 `static`）`Shared` 方法，在类或结构中实现 `Null` 接口。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-110">The UDT must implement the `System.Data.SqlTypes.INullable` interface in the class or structure by creating a public `static` (`Shared` in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic) `Null` method.</span></span> <span data-ttu-id="2d6e9-111">默认情况下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是可识别 Null 的。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is null-aware by default.</span></span> <span data-ttu-id="2d6e9-112">这是为使在 UDT 中执行的代码能够识别 Null 值所必需的。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-112">This is necessary for code executing in the UDT to be able to recognize a null value.</span></span>  
  
-   <span data-ttu-id="2d6e9-113">UDT 必须包含支持从其进行分析的公共 `static`（或 `Shared`）`Parse` 方法以及用于转换到对象的字符串表示形式的 `ToString` 方法。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-113">The UDT must contain a public `static` (or `Shared`) `Parse` method that supports parsing from, and a public `ToString` method for converting to a string representation of the object.</span></span>  
  
-   <span data-ttu-id="2d6e9-114">具有用户定义序列化格式的 UDT 必须实现 `System.Data.IBinarySerialize` 接口并提供 `Read` 和 `Write` 方法。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-114">A UDT with a user-defined serialization format must implement the `System.Data.IBinarySerialize` interface and provide a `Read` and a `Write` method.</span></span>  
  
-   <span data-ttu-id="2d6e9-115">该 UDT 必须实现 `System.Xml.Serialization.IXmlSerializable`，或者所有公共字段和属性必须均属于 XML 可序列化类型或者使用 `XmlIgnore` 属性进行修饰（如果要求替代标准序列化）。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-115">The UDT must implement `System.Xml.Serialization.IXmlSerializable`, or all public fields and properties must be of types that are XML serializable or decorated with the `XmlIgnore` attribute if overriding standard serialization is required.</span></span>  
  
-   <span data-ttu-id="2d6e9-116">一个 UDT 对象必须只存在一个序列化。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-116">There must be only one serialization of a UDT object.</span></span> <span data-ttu-id="2d6e9-117">如果序列化或反序列化例程识别了某一特定对象的多个表示形式，则验证将失败。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-117">Validation fails if the serialize or deserialize routines recognize more than one representation of a particular object.</span></span>  
  
-   <span data-ttu-id="2d6e9-118">`SqlUserDefinedTypeAttribute.IsByteOrdered` 必须为 `true`，以便按字节顺序比较数据。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-118">`SqlUserDefinedTypeAttribute.IsByteOrdered` must be `true` to compare data in byte order.</span></span> <span data-ttu-id="2d6e9-119">如果未实现 IComparable 接口，并且 `SqlUserDefinedTypeAttribute.IsByteOrdered` 为 `false`，字节顺序比较将失败。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-119">If the IComparable interface is not implemented and `SqlUserDefinedTypeAttribute.IsByteOrdered` is `false`, byte order comparisons will fail.</span></span>  
  
-   <span data-ttu-id="2d6e9-120">在类中定义的 UDT 必须具有不采用任何参数的公共构造函数。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-120">A UDT defined in a class must have a public constructor that takes no arguments.</span></span> <span data-ttu-id="2d6e9-121">您可以选择创建其他重载类构造函数。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-121">You can optionally create additional overloaded class constructors.</span></span>  
  
-   <span data-ttu-id="2d6e9-122">该 UDT 必须将数据元素作为公共字段或属性过程公开。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-122">The UDT must expose data elements as public fields or property procedures.</span></span>  
  
-   <span data-ttu-id="2d6e9-123">公共名称的长度不能超过128个字符，并且必须符合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在[数据库标识符](../databases/database-identifiers.md)中定义的标识符的命名规则。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-123">Public names cannot be longer than 128 characters, and must conform to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] naming rules for identifiers as defined in [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="2d6e9-124">`sql_variant` 列不能包含 UDT 的实例。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-124">`sql_variant` columns cannot contain instances of a UDT.</span></span>  
  
-   <span data-ttu-id="2d6e9-125">继承的成员无法从 [!INCLUDE[tsql](../../includes/tsql-md.md)] 访问，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型系统不知道 UDT 中的继承层次结构。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-125">Inherited members are not accessible from [!INCLUDE[tsql](../../includes/tsql-md.md)] because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type system is not aware of the inheritance hierarchy among UDTs.</span></span> <span data-ttu-id="2d6e9-126">但是，您可以在创建类的结构时使用继承，并且可以在该类型的托管代码实现方式中调用此类方法。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-126">However, you can use inheritance when you structure your classes and you can call such methods in the managed code implementation of the type.</span></span>  
  
-   <span data-ttu-id="2d6e9-127">成员不能被重载，但类构造函数除外。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-127">Members cannot be overloaded, except for the class constructor.</span></span> <span data-ttu-id="2d6e9-128">如果您创建某一重载方法，则在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中注册程序集或创建类型时将不会引发错误。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-128">If you do create an overloaded method, no error is raised when you register the assembly or create the type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d6e9-129">在运行时将检测到重载的方法，而不是在创建类型时检测到。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-129">Detection of the overloaded method occurs at run time, not when the type is created.</span></span> <span data-ttu-id="2d6e9-130">只要永不调用重载的方法，重载的方法就可以存在于类中。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-130">Overloaded methods can exist in the class as long as they are never invoked.</span></span> <span data-ttu-id="2d6e9-131">一旦您调用重载的方法，就会引发错误。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-131">Once you invoke the overloaded method, an error is raised.</span></span>  
  
-   <span data-ttu-id="2d6e9-132">任何 `static`（或 `Shared`）成员都必须声明为常量或声明为只读。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-132">Any `static` (or `Shared`) members must be declared as constants or as read-only.</span></span> <span data-ttu-id="2d6e9-133">静态成员将无法改变。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-133">Static members cannot be mutable.</span></span>  
  
-   <span data-ttu-id="2d6e9-134">如果 `SqlUserDefinedTypeAttribute.MaxByteSize` 字段设置为 -1，则序列化 UDT 在大小上可达到大对象 (LOB) 大小限制（目前为 2 GB）。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-134">If the `SqlUserDefinedTypeAttribute.MaxByteSize` field is set to -1, the serialized UDT can be as large as the large object (LOB) size limit (currently 2 GB).</span></span> <span data-ttu-id="2d6e9-135">该 UDT 的大小不能超过在 `MaxByteSized` 字段中指定的值。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-135">The size of the UDT cannot exceed the value specified in the `MaxByteSized` field.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d6e9-136">尽管服务器并不使用它来比较性能，但您可以选择实现 `System.IComparable` 接口，该接口公开单个方法 `CompareTo`。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-136">Although it is not used by the server for performing comparisons, you can optionally implement the `System.IComparable` interface, which exposes a single method, `CompareTo`.</span></span> <span data-ttu-id="2d6e9-137">此方法用于客户端上希望精确比较或排序 UDT 值的情况中。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-137">This is used on the client side in situations in which it is desirable to accurately compare or order UDT values.</span></span>  
  
## <a name="native-serialization"></a><span data-ttu-id="2d6e9-138">本机序列化</span><span class="sxs-lookup"><span data-stu-id="2d6e9-138">Native Serialization</span></span>  
 <span data-ttu-id="2d6e9-139">为您的 UDT 选择正确的序列化属性取决于您正尝试创建的 UDT 的类型。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-139">Choosing the right serialization attributes for your UDT depends on the type of UDT you are trying to create.</span></span> <span data-ttu-id="2d6e9-140">此 `Native` 序列化格式利用一个非常简单的结构，该结构使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能够将 UDT 的有效本机表示形式存储于磁盘上。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-140">The `Native` serialization format utilizes a very simple structure that enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to store an efficient native representation of the UDT on disk.</span></span> <span data-ttu-id="2d6e9-141">如果 UDT 很简单并且只包含以下类型的字段，则建议采用 `Native` 格式：</span><span class="sxs-lookup"><span data-stu-id="2d6e9-141">The `Native` format is recommended if the UDT is simple and only contains fields of the following types:</span></span>  
  
 <span data-ttu-id="2d6e9-142">**bool**、 **byte**、 **sbyte**、 **short**、 **ushort**、 **int**、 **uint**、 **long**、 **ulong**、 **float**、 **double**、 **SqlByte**、 **SqlInt16**、 **SqlInt32**、 **SqlInt64**、 **SqlDateTime**、 **SqlSingle**、 **SqlDouble**、 **SqlMoney**、 **SqlBoolean**</span><span class="sxs-lookup"><span data-stu-id="2d6e9-142">**bool**, **byte**, **sbyte**, **short**, **ushort**, **int**, **uint**, **long**, **ulong**, **float**, **double**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, **SqlMoney**, **SqlBoolean**</span></span>  
  
 <span data-ttu-id="2d6e9-143">由上述类型的字段组成的值类型适用于 `Native` 格式（如 `structs` Visual c # 中的）， (或在 `Structures` Visual Basic) 中是已知的。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-143">Value types that are composed of fields of the above types are good candidates for `Native` format, such as `structs` in Visual C#, (or `Structures` as they are known in Visual Basic).</span></span> <span data-ttu-id="2d6e9-144">例如，使用 `Native` 序列化格式指定的 UDT 可包含也用 `Native` 格式指定的其他 UDT 的字段。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-144">For example, a UDT specified with the `Native` serialization format may contain a field of another UDT that was also specified with the `Native` format.</span></span> <span data-ttu-id="2d6e9-145">如果 UDT 定义更复杂并且包含不在上述列表中的数据类型，则必须改为指定 `UserDefined` 序列化格式。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-145">If the UDT definition is more complex and contains data types not on the above list, you must specify the `UserDefined` serialization format instead.</span></span>  
  
 <span data-ttu-id="2d6e9-146">`Native` 格式具有以下要求：</span><span class="sxs-lookup"><span data-stu-id="2d6e9-146">The `Native` format has the following requirements:</span></span>  
  
-   <span data-ttu-id="2d6e9-147">该类型不能指定 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize` 的值。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-147">The type must not specify a value for `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize`.</span></span>  
  
-   <span data-ttu-id="2d6e9-148">所有字段必须均可序列化。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-148">All fields must be serializable.</span></span>  
  
-   <span data-ttu-id="2d6e9-149">如果在类中而不是结构中定义该 UDT，则必须将 `System.Runtime.InteropServices.StructLayoutAttribute` 指定为 `StructLayout.LayoutKindSequential`。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-149">The `System.Runtime.InteropServices.StructLayoutAttribute` must be specified as `StructLayout.LayoutKindSequential` if the UDT is defined in a class and not a structure.</span></span> <span data-ttu-id="2d6e9-150">此属性控制数据字段的物理布局，并用来按照成员的出现顺序对它们进行布局。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-150">This attribute controls the physical layout of the data fields and is used to force the members to be laid out in the order in which they appear.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2d6e9-151">使用此属性确定具有多个值的 UDT 的字段顺序。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-151">uses this attribute to determine the field order for UDTs with multiple values.</span></span>  
  
 <span data-ttu-id="2d6e9-152">有关使用序列化定义的 UDT 的示例 `Native` ，请参阅[编写用户定义类型的代码](creating-user-defined-types-coding.md)中的 Point udt。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-152">For an example of a UDT defined with `Native` serialization, see the Point UDT in [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
## <a name="userdefined-serialization"></a><span data-ttu-id="2d6e9-153">UserDefined 序列化</span><span class="sxs-lookup"><span data-stu-id="2d6e9-153">UserDefined Serialization</span></span>  
 <span data-ttu-id="2d6e9-154">针对 `UserDefined` 属性的 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 格式设置为开发人员提供了对二进制格式的完全控制。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-154">The `UserDefined` format setting for the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` attribute gives the developer full control over the binary format.</span></span> <span data-ttu-id="2d6e9-155">在将 `Format` 特性属性指定为 `UserDefined` 时，必须在您的代码中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2d6e9-155">When specifying the `Format` attribute property as `UserDefined`, you must do the following in your code:</span></span>  
  
-   <span data-ttu-id="2d6e9-156">指定可选的 `IsByteOrdered` 特性属性。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-156">Specify the optional `IsByteOrdered` attribute property.</span></span> <span data-ttu-id="2d6e9-157">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-157">The default value is `false`.</span></span>  
  
-   <span data-ttu-id="2d6e9-158">指定 `MaxByteSize` 的 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 属性。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-158">Specify the `MaxByteSize` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.</span></span>  
  
-   <span data-ttu-id="2d6e9-159">编写代码，以便通过实现 `Read` 接口实现 UDT 的 `Write` 方法和 `System.Data.Sql.IBinarySerialize` 方法。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-159">Write code to implement `Read` and `Write` methods for the UDT by implementing the `System.Data.Sql.IBinarySerialize` interface.</span></span>  
  
 <span data-ttu-id="2d6e9-160">有关使用序列化定义的 UDT 的示例 `UserDefined` ，请参阅[编写用户定义类型的代码](creating-user-defined-types-coding.md)中的 Currency udt。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-160">For an example of a UDT defined with `UserDefined` serialization, see the Currency UDT in [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d6e9-161">为了编制索引，UDT 字段必须使用本机序列化或者是持久化的。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-161">UDT fields must use native serialization or be persisted in order to be indexed.</span></span>  
  
## <a name="serialization-attributes"></a><span data-ttu-id="2d6e9-162">序列化属性</span><span class="sxs-lookup"><span data-stu-id="2d6e9-162">Serialization Attributes</span></span>  
 <span data-ttu-id="2d6e9-163">属性确定如何使用序列化来构造 UDT 的存储表示形式以及如何按值将 UDT 传输到客户端。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-163">Attributes determine how serialization is used to construct the storage representation of UDTs and to transmit UDTs by value to the client.</span></span> <span data-ttu-id="2d6e9-164">在创建 UDT 时，您需要指定 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-164">You are required to specify the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` when creating the UDT.</span></span> <span data-ttu-id="2d6e9-165">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 属性指示类是 UDT 并且指定针对 UDT 的存储。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-165">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` attribute indicates that the class is a UDT and specifies the storage for the UDT.</span></span> <span data-ttu-id="2d6e9-166">您可以选择指定 `Serializable` 属性，尽管 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并不要求这样做。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-166">You can optionally specify the `Serializable` attribute, although [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not require this.</span></span>  
  
 <span data-ttu-id="2d6e9-167">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 具有以下属性。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-167">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` has the following properties.</span></span>  
  
 `Format`  
 <span data-ttu-id="2d6e9-168">指定序列化格式，根据 UDT 的数据类型，该格式可以是 `Native` 或 `UserDefined`。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-168">Specifies the serialization format, which can be `Native` or `UserDefined`, depending on the data types of the UDT.</span></span>  
  
 `IsByteOrdered`  
 <span data-ttu-id="2d6e9-169">一个 `Boolean` 值，确定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何对 UDT 执行二进制比较。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-169">A `Boolean` value that determines how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs binary comparisons on the UDT.</span></span>  
  
 `IsFixedLength`  
 <span data-ttu-id="2d6e9-170">指示此 UDT 的所有实例是否都具有相同的长度。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-170">Indicates whether all instances of this UDT are the same length.</span></span>  
  
 `MaxByteSize`  
 <span data-ttu-id="2d6e9-171">实例的最大大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-171">The maximum size of the instance, in bytes.</span></span> <span data-ttu-id="2d6e9-172">您在指定 `MaxByteSize` 时必须同时指定 `UserDefined` 序列化格式。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-172">You must specify `MaxByteSize` with the `UserDefined` serialization format.</span></span> <span data-ttu-id="2d6e9-173">对于指定了用户定义的序列化的 UDT，`MaxByteSize` 是指采用用户定义的序列化格式的 UDT 的总大小。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-173">For a UDT with user-defined serialization specified, `MaxByteSize` refers to the total size of the UDT in its serialized form as defined by the user.</span></span> <span data-ttu-id="2d6e9-174">`MaxByteSize` 的值必须处于 1 到 8000 的范围内，或者设置为 -1，以便指示 UDT 大于 8000 字节（总大小不能超过最大 LOB 大小）。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-174">The value of `MaxByteSize` must be in the range of 1 to 8000, or set to -1 to indicate that the UDT is greater than 8000 bytes (the total size cannot exceed the maximum LOB size).</span></span> <span data-ttu-id="2d6e9-175">考虑这样一个 UDT：它有一个由 10 个字符组成的字符串属性 (`System.Char`)。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-175">Consider a UDT with a property of a string of 10 characters (`System.Char`).</span></span> <span data-ttu-id="2d6e9-176">当使用 BinaryWriter 序列化 UDT 时，序列化字符串的总大小为 22 字节：每个 Unicode UTF-16 字符占 2 个字节，乘以最大字符数，再加上因序列化二进制流而导致的系统开销 2 个控制字节。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-176">When the UDT is serialized by using a BinaryWriter, the total size of the serialized string is 22 bytes: 2 bytes per Unicode UTF-16 character, multiplied by the maximum number of characters, plus 2 control bytes of overhead incurred from serializing a binary stream.</span></span> <span data-ttu-id="2d6e9-177">因此，在确定 `MaxByteSize` 的值时，必须考虑序列化之后的 UDT 的总大小：以二进制格式序列化的数据的大小加上因序列化而导致的系统开销。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-177">Therefore, when determining the value of `MaxByteSize`, the total size of the serialized UDT must be considered: the size of the data serialized in binary form plus the overhead incurred by serialization.</span></span>  
  
 `ValidationMethodName`  
 <span data-ttu-id="2d6e9-178">用于验证 UDT 的实例的方法的名称。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-178">The name of the method used to validate instances of the UDT.</span></span>  
  
### <a name="setting-isbyteordered"></a><span data-ttu-id="2d6e9-179">设置 IsByteOrdered</span><span class="sxs-lookup"><span data-stu-id="2d6e9-179">Setting IsByteOrdered</span></span>  
 <span data-ttu-id="2d6e9-180">如果将 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered` 属性设置为 `true`，则您实际上保证了可以使用已序列化的二进制数据对信息进行语义排序。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-180">When the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered` property is set to `true`, you are in effect guaranteeing that the serialized binary data can be used for semantic ordering of the information.</span></span> <span data-ttu-id="2d6e9-181">因此，以字节排序的 UDT 对象的每个实例只能有一种序列化表示形式。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-181">Thus, each instance of a byte-ordered UDT object can only have one serialized representation.</span></span> <span data-ttu-id="2d6e9-182">当在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中对序列化字节执行比较操作时，其结果应与在托管代码中执行同样的比较操作时的结果相同。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-182">When a comparison operation is performed in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the serialized bytes, its results should be the same as if the same comparison operation had taken place in managed code.</span></span> <span data-ttu-id="2d6e9-183">如果将 `IsByteOrdered` 设置为 `true`，则还支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="2d6e9-183">The following features are also supported when `IsByteOrdered` is set to `true`:</span></span>  
  
-   <span data-ttu-id="2d6e9-184">可以对此类型的列创建索引。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-184">The ability to create indexes on columns of this type.</span></span>  
  
-   <span data-ttu-id="2d6e9-185">可以对此类型的列创建主键和外键以及 CHECK 和 UNIQUE 约束。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-185">The ability to create primary and foreign keys as well as CHECK and UNIQUE constraints on columns of this type.</span></span>  
  
-   <span data-ttu-id="2d6e9-186">可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] ORDER BY、GROUP BY 和 PARTITION BY 子句。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-186">The ability to use [!INCLUDE[tsql](../../includes/tsql-md.md)] ORDER BY, GROUP BY, and PARTITION BY clauses.</span></span> <span data-ttu-id="2d6e9-187">此时，将使用该类型的二进制表示形式确定顺序。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-187">In these cases, the binary representation of the type is used to determine the order.</span></span>  
  
-   <span data-ttu-id="2d6e9-188">可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中使用比较运算符。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-188">The ability to use comparison operators in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
-   <span data-ttu-id="2d6e9-189">可以保持此类型的计算列。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-189">The ability to persist computed columns of this type.</span></span>  
  
 <span data-ttu-id="2d6e9-190">请注意，如果将 `Native` 设置为 `UserDefined`，`IsByteOrdered` 和 `true` 序列化格式将支持以下比较运算符：</span><span class="sxs-lookup"><span data-stu-id="2d6e9-190">Note that both the `Native` and `UserDefined` serialization formats support the following comparison operators when `IsByteOrdered` is set to `true`:</span></span>  
  
-   <span data-ttu-id="2d6e9-191">等于 (=)</span><span class="sxs-lookup"><span data-stu-id="2d6e9-191">Equal to (=)</span></span>  
  
-   <span data-ttu-id="2d6e9-192">不等于 (!=)</span><span class="sxs-lookup"><span data-stu-id="2d6e9-192">Not equal to (!=)</span></span>  
  
-   <span data-ttu-id="2d6e9-193">大于号 (>)</span><span class="sxs-lookup"><span data-stu-id="2d6e9-193">Greater than (>)</span></span>  
  
-   <span data-ttu-id="2d6e9-194">小于号 (\<)</span><span class="sxs-lookup"><span data-stu-id="2d6e9-194">Less than (\<)</span></span>  
  
-   <span data-ttu-id="2d6e9-195">大于或等于 (>=)</span><span class="sxs-lookup"><span data-stu-id="2d6e9-195">Greater than or equal to (>=)</span></span>  
  
-   <span data-ttu-id="2d6e9-196">小于或等于 (&lt;=)</span><span class="sxs-lookup"><span data-stu-id="2d6e9-196">Less than or equal to (<=)</span></span>  
  
### <a name="implementing-nullability"></a><span data-ttu-id="2d6e9-197">实现为 Null 性</span><span class="sxs-lookup"><span data-stu-id="2d6e9-197">Implementing Nullability</span></span>  
 <span data-ttu-id="2d6e9-198">除了正确指定程序集的属性外，类还必须支持为 Null 性。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-198">In addition to specifying the attributes for your assemblies correctly, your class must also support nullability.</span></span> <span data-ttu-id="2d6e9-199">加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 UDT 是可识别 Null 的，但为使 UDT 能够识别某一 Null 值，该类必须实现 `INullable` 接口。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-199">UDTs loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are null-aware, but in order for the UDT to recognize a null value, the class must implement the `INullable` interface.</span></span> <span data-ttu-id="2d6e9-200">有关如何在 UDT 中实现为空性的详细信息和示例，请参阅[编写用户定义类型的代码](creating-user-defined-types-coding.md)。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-200">For more information and an example of how to implement nullability in a UDT, see [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
### <a name="string-conversions"></a><span data-ttu-id="2d6e9-201">字符串转换</span><span class="sxs-lookup"><span data-stu-id="2d6e9-201">String Conversions</span></span>  
 <span data-ttu-id="2d6e9-202">为了支持与 UDT 之间的字符串转换，必须在类中提供 `Parse` 方法和 `ToString` 方法。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-202">To support string conversion to and from the UDT, you must provide a `Parse` method and a `ToString` method in your class.</span></span> <span data-ttu-id="2d6e9-203">`Parse` 方法允许字符串转换为 UDT。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-203">The `Parse` method allows a string to be converted into a UDT.</span></span> <span data-ttu-id="2d6e9-204">它必须声明为 `static`（在 Visual Basic 中则为 `Shared`），并且采用 `System.Data.SqlTypes.SqlString` 类型的参数。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-204">It must be declared as `static` (or `Shared` in Visual Basic), and take a parameter of type `System.Data.SqlTypes.SqlString`.</span></span> <span data-ttu-id="2d6e9-205">有关如何实现和方法的详细信息和示例 `Parse` `ToString` ，请参阅[编写用户定义类型的代码](creating-user-defined-types-coding.md)。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-205">For more information and an example of how to implement the `Parse` and `ToString` methods, see [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
## <a name="xml-serialization"></a><span data-ttu-id="2d6e9-206">XML 序列化</span><span class="sxs-lookup"><span data-stu-id="2d6e9-206">XML Serialization</span></span>  
 <span data-ttu-id="2d6e9-207">UDT 必须通过符合针对 XML 序列化的约定，支持与 `xml` 数据类型之间的转换。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-207">UDTs must support conversion to and from the `xml` data type by conforming to the contract for XML serialization.</span></span> <span data-ttu-id="2d6e9-208">`System.Xml.Serialization` 命名空间包含用于将对象序列化为 XML 格式文档或流的类。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-208">The `System.Xml.Serialization` namespace contains classes that are used to serialize objects into XML format documents or streams.</span></span> <span data-ttu-id="2d6e9-209">您可以选择通过使用 `xml` 接口（该接口为 XML 序列化和反序列化提供自定义格式），实现 `IXmlSerializable` 序列化。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-209">You can choose to implement `xml` serialization by using the `IXmlSerializable` interface, which provides custom formatting for XML serialization and deserialization.</span></span>  
  
 <span data-ttu-id="2d6e9-210">除了执行从 UDT 到 `xml` 的显式转换外，XML 序列化使您能够：</span><span class="sxs-lookup"><span data-stu-id="2d6e9-210">In addition to performing explicit conversions from UDT to `xml`, XML serialization enables you to:</span></span>  
  
-   <span data-ttu-id="2d6e9-211">在转换到 `Xquery` 数据类型后使用 UDT 实例的 `xml` 值。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-211">Use `Xquery` over values of UDT instances after conversion to the `xml` data type.</span></span>  
  
-   <span data-ttu-id="2d6e9-212">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的具有本机 XML Web 服务的参数化查询和 Web 方法中使用 UDT。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-212">Use UDTs in parameterized queries and Web methods with Native XML Web Services in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="2d6e9-213">使用 UDT 可以接收 XML 数据的大容量加载。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-213">Use UDTs to receive a bulk load of XML data.</span></span>  
  
-   <span data-ttu-id="2d6e9-214">序列化包含具有 UDT 列的表的数据集。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-214">Serialize DataSets that contain tables with UDT columns.</span></span>  
  
 <span data-ttu-id="2d6e9-215">UDT 在 FOR XML 查询中不序列化。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-215">UDTs are not serialized in FOR XML queries.</span></span> <span data-ttu-id="2d6e9-216">若要执行显示 UDT 的 XML 序列化的 FOR XML 查询，请在 SELECT 语句中显式将每个 UDT 列转换为 `xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-216">To execute a FOR XML query that displays the XML serialization of UDTs, explicitly convert each UDT column to the `xml` data type in the SELECT statement.</span></span> <span data-ttu-id="2d6e9-217">您还可以显式将列转换为 `varbinary`、`varchar` 或 `nvarchar`。</span><span class="sxs-lookup"><span data-stu-id="2d6e9-217">You can also explicitly convert the columns to `varbinary`, `varchar`, or `nvarchar`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d6e9-218">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d6e9-218">See Also</span></span>  
 [<span data-ttu-id="2d6e9-219">创建用户定义类型</span><span class="sxs-lookup"><span data-stu-id="2d6e9-219">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
  
  
