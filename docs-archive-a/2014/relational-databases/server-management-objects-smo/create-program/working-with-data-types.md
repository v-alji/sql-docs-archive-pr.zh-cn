---
title: 使用数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbffc1c59eb12fa0f448a7fcb26157d5e18dba3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578750"
---
# <a name="working-with-data-types"></a><span data-ttu-id="e09e0-102">使用数据类型</span><span class="sxs-lookup"><span data-stu-id="e09e0-102">Working with Data Types</span></span>
  <span data-ttu-id="e09e0-103">数据具有很多类型和不同的大小，例如具有定义长度的字符串、具有特定精度的数字或者作为具有其自身规则集的其他对象的用户定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="e09e0-103">Data comes in many types and sizes, such as a string that has a defined length, a number that has specific accuracy, or a user-defined data type that is another object that has its own set of rules.</span></span> <span data-ttu-id="e09e0-104"><xref:Microsoft.SqlServer.Management.Smo.DataType>对象对数据类型进行分类，以便能够正确地对其进行处理 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e09e0-104">The <xref:Microsoft.SqlServer.Management.Smo.DataType> object classifies the type of data so that it can be handled correctly by [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e09e0-105"><xref:Microsoft.SqlServer.Management.Smo.DataType> 对象与接受数据的对象关联。</span><span class="sxs-lookup"><span data-stu-id="e09e0-105">The <xref:Microsoft.SqlServer.Management.Smo.DataType> object is associated with objects that accept data.</span></span> <span data-ttu-id="e09e0-106">以下 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理对象 (SMO) 接受必须由 <xref:Microsoft.SqlServer.Management.Smo.DataType> 对象属性定义的数据：</span><span class="sxs-lookup"><span data-stu-id="e09e0-106">The following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) objects accept data that must be defined by a <xref:Microsoft.SqlServer.Management.Smo.DataType> object property:</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 <span data-ttu-id="e09e0-107">可以通过若干方式设置接受数据的对象的 `DataType` 属性。</span><span class="sxs-lookup"><span data-stu-id="e09e0-107">The `DataType` property for objects that accept data can be set in several ways.</span></span>  
  
-   <span data-ttu-id="e09e0-108">使用默认构造函数，并显式指定 <xref:Microsoft.SqlServer.Management.Smo.DataType> 对象属性。</span><span class="sxs-lookup"><span data-stu-id="e09e0-108">Use the default constructor and specify <xref:Microsoft.SqlServer.Management.Smo.DataType> object properties explicitly</span></span>  
  
-   <span data-ttu-id="e09e0-109">使用重载的构造函数，并指定 <xref:Microsoft.SqlServer.Management.Smo.DataType> 属性作为参数。</span><span class="sxs-lookup"><span data-stu-id="e09e0-109">Use an overloaded constructor and specify the <xref:Microsoft.SqlServer.Management.Smo.DataType> properties as parameters.</span></span>  
  
-   <span data-ttu-id="e09e0-110">在对象构造函数中内联指定 <xref:Microsoft.SqlServer.Management.Smo.DataType>。</span><span class="sxs-lookup"><span data-stu-id="e09e0-110">Specify the <xref:Microsoft.SqlServer.Management.Smo.DataType> inline in the object constructor.</span></span>  
  
-   <span data-ttu-id="e09e0-111">使用 <xref:Microsoft.SqlServer.Management.Smo.DataType> 类的静态成员之一，例如 `Int`。</span><span class="sxs-lookup"><span data-stu-id="e09e0-111">Use one of the static members of the <xref:Microsoft.SqlServer.Management.Smo.DataType> class, for example `Int`.</span></span> <span data-ttu-id="e09e0-112">实际上，这将返回 <xref:Microsoft.SqlServer.Management.Smo.DataType> 对象的实例。</span><span class="sxs-lookup"><span data-stu-id="e09e0-112">This will in fact return an instance of a <xref:Microsoft.SqlServer.Management.Smo.DataType> object.</span></span>  
  
 <span data-ttu-id="e09e0-113"><xref:Microsoft.SqlServer.Management.Smo.DataType> 对象具有定义数据类型的几个属性。</span><span class="sxs-lookup"><span data-stu-id="e09e0-113">The <xref:Microsoft.SqlServer.Management.Smo.DataType> object has several properties that define the type of data.</span></span> <span data-ttu-id="e09e0-114">例如，<xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 属性指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e09e0-114">For example, the <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> property specifies the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type.</span></span> <span data-ttu-id="e09e0-115">在 <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 枚举中列出了表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型的常量值。</span><span class="sxs-lookup"><span data-stu-id="e09e0-115">The constant values that represent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types are listed in the <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> enumeration.</span></span> <span data-ttu-id="e09e0-116">这是指诸如 `varchar`、`nchar`、`currency`、`integer`、`float` 和 `datetime` 这样的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e09e0-116">This refers to data types such as `varchar`, `nchar`, `currency`, `integer`, `float`, and `datetime`.</span></span>  
  
 <span data-ttu-id="e09e0-117">确立数据类型时，必须为数据设置具体的属性。</span><span class="sxs-lookup"><span data-stu-id="e09e0-117">When the data type is established, specific properties must be set for the data.</span></span> <span data-ttu-id="e09e0-118">例如，如果它是 `nchar` 类型，则必须在 `Length` 属性中设置字符串数据的长度。</span><span class="sxs-lookup"><span data-stu-id="e09e0-118">For example, if it is an `nchar` type, the length of the string data must be set in the `Length` property.</span></span> <span data-ttu-id="e09e0-119">对数字值同样如此，这时必须指定精度和小数位数。</span><span class="sxs-lookup"><span data-stu-id="e09e0-119">The same applies for numeric values, where you would have to specify precision and scale.</span></span>  
  
 <span data-ttu-id="e09e0-120"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 和 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> 数据类型引用的对象包含由用户定义的数据类型的定义。</span><span class="sxs-lookup"><span data-stu-id="e09e0-120"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> and <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> data types refer to objects that contain the definition of the type of data defined by the user.</span></span> <span data-ttu-id="e09e0-121"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 基于来自 <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 枚举的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e09e0-121">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> is based on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types from the <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> enumeration.</span></span> <span data-ttu-id="e09e0-122"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>基于 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .net 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e09e0-122">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> is based on [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET data types.</span></span> <span data-ttu-id="e09e0-123">通常，它们表示由于组织定义的业务规则而被数据库频繁重用的特定类型的数据。</span><span class="sxs-lookup"><span data-stu-id="e09e0-123">Typically, these would represent data of a specific type that is frequently reused by the database because of business rules defined by the organization.</span></span> <span data-ttu-id="e09e0-124">例如，存储资金数量和货币币种的数据类型对于处理多种货币的公司将会非常有用。</span><span class="sxs-lookup"><span data-stu-id="e09e0-124">For example, a data type that stores an amount of money and a currency denominator would be helpful in a company that deals in multiple currencies.</span></span>  
  
 <span data-ttu-id="e09e0-125"><xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 枚举包含 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支持的所有数据类型的列表。</span><span class="sxs-lookup"><span data-stu-id="e09e0-125">The <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> enumeration contains a list of all the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-supported data types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e09e0-126">示例</span><span class="sxs-lookup"><span data-stu-id="e09e0-126">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a><span data-ttu-id="e09e0-127">使用 Visual Basic 中构造函数的规范构造 DataType 对象</span><span class="sxs-lookup"><span data-stu-id="e09e0-127">Constructing a DataType Object with the Specification in the Constructor in Visual Basic</span></span>  
 <span data-ttu-id="e09e0-128">该代码示例显示如何使用构造函数创建基于不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型的数据类型实例。</span><span class="sxs-lookup"><span data-stu-id="e09e0-128">This code example shows how to use the constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e09e0-129"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 和 XML 类型全都需要名称值以标识对象。</span><span class="sxs-lookup"><span data-stu-id="e09e0-129">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes1](SMO How to#SMO_VBDataTypes1)]  -->  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a><span data-ttu-id="e09e0-130">使用 Visual C# 中构造函数的规范构造 DataType 对象</span><span class="sxs-lookup"><span data-stu-id="e09e0-130">Constructing a DataType Object with the Specification in the Constructor in Visual C#</span></span>  
 <span data-ttu-id="e09e0-131">该代码示例显示如何使用构造函数创建基于不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型的数据类型实例。</span><span class="sxs-lookup"><span data-stu-id="e09e0-131">This code example shows how to use the constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e09e0-132"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 和 XML 类型全都需要名称值以标识对象。</span><span class="sxs-lookup"><span data-stu-id="e09e0-132">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
```  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguments specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a><span data-ttu-id="e09e0-133">使用 Visual Basic 中的默认构造函数构造 DataType 对象</span><span class="sxs-lookup"><span data-stu-id="e09e0-133">Constructing a DataType Object by Using the Default Constructor in Visual Basic</span></span>  
 <span data-ttu-id="e09e0-134">该代码示例显示如何使用默认构造函数创建基于不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型的数据类型实例。</span><span class="sxs-lookup"><span data-stu-id="e09e0-134">This code example shows how to use the default constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="e09e0-135">然后使用这些属性指定数据类型。</span><span class="sxs-lookup"><span data-stu-id="e09e0-135">The properties are then used to specify the data type.</span></span>  
  
 <span data-ttu-id="e09e0-136">**注意**<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 和 XML 类型都需要名称值以标识对象。</span><span class="sxs-lookup"><span data-stu-id="e09e0-136">**Note** The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes2](SMO How to#SMO_VBDataTypes2)]  -->  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a><span data-ttu-id="e09e0-137">使用 Visual C# 中的默认构造函数构造 DataType 对象</span><span class="sxs-lookup"><span data-stu-id="e09e0-137">Constructing a DataType Object by Using the Default Constructor in Visual C#</span></span>  
 <span data-ttu-id="e09e0-138">该代码示例显示如何使用默认构造函数创建基于不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型的数据类型实例。</span><span class="sxs-lookup"><span data-stu-id="e09e0-138">This code example shows how to use the default constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="e09e0-139">然后使用这些属性指定数据类型。</span><span class="sxs-lookup"><span data-stu-id="e09e0-139">The properties are then used to specify the data type.</span></span>  
  
 <span data-ttu-id="e09e0-140">**注意**<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 和 XML 类型都需要名称值以标识对象。</span><span class="sxs-lookup"><span data-stu-id="e09e0-140">**Note** The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
```  
{   
//Declare and create a DataType object variable.   
DataType dt;   
dt = new DataType();   
//Define the data type by setting the SqlDataType property.   
dt.SqlDataType = SqlDataType.VarChar;   
//The VarChar data type requires a value for the MaximumLength property.   
dt.MaximumLength = 100;   
}  
```  
  
  
