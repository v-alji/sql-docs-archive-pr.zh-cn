---
title: 设置属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SMO [SQL Server], properties
- SQL Server Management Objects, properties
- properties [SMO]
ms.assetid: 342569ba-d2f7-44d2-8f3f-ae9c701c7f0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: de381f8e4e9dfe9f6590638742e988f866ccabdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691162"
---
# <a name="setting-properties"></a><span data-ttu-id="706ed-102">设置属性</span><span class="sxs-lookup"><span data-stu-id="706ed-102">Setting Properties</span></span>
  <span data-ttu-id="706ed-103">属性是存储有关对象的说明性信息的值。</span><span class="sxs-lookup"><span data-stu-id="706ed-103">Properties are values that store descriptive information about the object.</span></span> <span data-ttu-id="706ed-104">例如， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 配置选项由 <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> 对象的属性表示。</span><span class="sxs-lookup"><span data-stu-id="706ed-104">For example, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuration options are represented by the <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> object's properties.</span></span> <span data-ttu-id="706ed-105">使用属性集合可以直接或间接访问属性。</span><span class="sxs-lookup"><span data-stu-id="706ed-105">Properties can be accessed either directly or indirectly by using the property collection.</span></span> <span data-ttu-id="706ed-106">直接访问属性使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="706ed-106">Accessing properties directly uses the following syntax:</span></span>  
  
 `objInstance.PropertyName`  
  
 <span data-ttu-id="706ed-107">可以修改或检索属性值，具体取决于该属性是拥有读/写访问权限还是只读访问权限。</span><span class="sxs-lookup"><span data-stu-id="706ed-107">A property value can be modified or retrieved depending on whether the property has read/write access or read-only access.</span></span> <span data-ttu-id="706ed-108">此外，还必须在创建对象之前设置某些特定属性。</span><span class="sxs-lookup"><span data-stu-id="706ed-108">It is also necessary to set certain properties before an object can be created.</span></span> <span data-ttu-id="706ed-109">有关详细信息，请参阅特定对象的 SMO 参考资料。</span><span class="sxs-lookup"><span data-stu-id="706ed-109">For more information, see the SMO reference for the particular object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="706ed-110">某一对象的子对象集合显示为该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="706ed-110">Collections of child objects appear as the property of an object.</span></span> <span data-ttu-id="706ed-111">例如，`Tables` 集合是 `Server` 对象的属性。</span><span class="sxs-lookup"><span data-stu-id="706ed-111">For example, the `Tables` collection is a property of a `Server` object.</span></span> <span data-ttu-id="706ed-112">有关详细信息，请参阅 [Using Collections](using-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="706ed-112">For more information, see [Using Collections](using-collections.md).</span></span>  
  
 <span data-ttu-id="706ed-113">对象的属性是属性集合的成员。</span><span class="sxs-lookup"><span data-stu-id="706ed-113">The properties of an object are members of the Properties collection.</span></span> <span data-ttu-id="706ed-114">属性集合可用于遍历对象的每个属性。</span><span class="sxs-lookup"><span data-stu-id="706ed-114">The Properties collection can be used to iterate through every property of an object.</span></span>  
  
 <span data-ttu-id="706ed-115">有时某一属性不可用，其原因如下：</span><span class="sxs-lookup"><span data-stu-id="706ed-115">Sometimes a property is not available for the following reasons:</span></span>  
  
-   <span data-ttu-id="706ed-116">服务器版本不支持该属性，例如当尝试在旧版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 上访问表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]新功能的属性时。</span><span class="sxs-lookup"><span data-stu-id="706ed-116">The server version does not support the property, such as if you try to access a property that represents a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] feature on an older version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="706ed-117">服务器未提供该属性的相应数据，例如当尝试访问表示尚未安装的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 组件的属性时。</span><span class="sxs-lookup"><span data-stu-id="706ed-117">The server does not provide data for the property, such as if you try to access a property that represents a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] component that is not installed.</span></span>  
  
 <span data-ttu-id="706ed-118">通过捕获 <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> 和 <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException> SMO 异常，可以处理上述情况。</span><span class="sxs-lookup"><span data-stu-id="706ed-118">You can handle these circumstances by catching the <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> and the <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException> SMO exceptions.</span></span>  
  
## <a name="setting-default-initialization-fields"></a><span data-ttu-id="706ed-119">设置默认的初始化字段</span><span class="sxs-lookup"><span data-stu-id="706ed-119">Setting Default Initialization Fields</span></span>  
 <span data-ttu-id="706ed-120">SMO 检索对象时将执行优化功能。</span><span class="sxs-lookup"><span data-stu-id="706ed-120">SMO performs an optimization when retrieving objects.</span></span> <span data-ttu-id="706ed-121">通过在以下状态之间进行缩放，此优化功能最大程度地减少了加载的属性数目：</span><span class="sxs-lookup"><span data-stu-id="706ed-121">The optimization minimizes the number of properties loaded by automatically scaling between the following states:</span></span>  
  
1.  <span data-ttu-id="706ed-122">部分加载。</span><span class="sxs-lookup"><span data-stu-id="706ed-122">Partially loaded.</span></span> <span data-ttu-id="706ed-123">首次引用某一对象时，该对象具有最少的可用属性（例如 Name 和 Schema）。</span><span class="sxs-lookup"><span data-stu-id="706ed-123">When an object is first referenced it has a minimum of properties available (such as Name and Schema).</span></span>  
  
2.  <span data-ttu-id="706ed-124">完全加载。</span><span class="sxs-lookup"><span data-stu-id="706ed-124">Fully loaded.</span></span> <span data-ttu-id="706ed-125">当引用任一属性时，将初始化剩余属性中可快速加载的属性并使其可用。</span><span class="sxs-lookup"><span data-stu-id="706ed-125">When any property is referenced, the remaining properties that are quick to load, are initialized and are made available.</span></span>  
  
3.  <span data-ttu-id="706ed-126">占用大量内存的属性。</span><span class="sxs-lookup"><span data-stu-id="706ed-126">Properties that use lots of memory.</span></span> <span data-ttu-id="706ed-127">剩余的不可用属性占用大量内存，并将 <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> 属性值设置为 True（例如 <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>）。</span><span class="sxs-lookup"><span data-stu-id="706ed-127">The remaining unavailable properties use lots of memory and have an <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> property value of true (such as <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>).</span></span> <span data-ttu-id="706ed-128">只有专门引用这些属性时才会进行加载。</span><span class="sxs-lookup"><span data-stu-id="706ed-128">These properties are loaded only when specifically referenced.</span></span>  
  
 <span data-ttu-id="706ed-129">除在部分加载状态中提供的属性之外，如果应用程序的确还需要提取额外属性，则会提交检索这些额外属性的查询，并向上扩展到完全加载状态。</span><span class="sxs-lookup"><span data-stu-id="706ed-129">If your application does fetch extra properties, besides the ones provided in the partially loaded state, it submits a query to retrieve these extra properties and scales up to the fully loaded state.</span></span> <span data-ttu-id="706ed-130">这可能会在客户端和服务器之间造成不必要的通信流量。</span><span class="sxs-lookup"><span data-stu-id="706ed-130">This can cause unnecessary traffic between the client and server.</span></span> <span data-ttu-id="706ed-131">调用 <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> 方法可以实现更多优化。</span><span class="sxs-lookup"><span data-stu-id="706ed-131">More optimization can be achieved by calling the <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method.</span></span> <span data-ttu-id="706ed-132">使用 <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> 方法可以指定在初始化对象时加载的属性。</span><span class="sxs-lookup"><span data-stu-id="706ed-132">The <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method allows specification of the properties that are loaded when the object is initialized.</span></span>  
  
 <span data-ttu-id="706ed-133"><xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> 方法设置其余应用程序或重置应用程序后的属性加载行为。</span><span class="sxs-lookup"><span data-stu-id="706ed-133">The <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method sets the property loading behavior for the rest of application or until it is reset.</span></span> <span data-ttu-id="706ed-134">您可以使用 <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> 方法保存原始行为，并根据需要还原。</span><span class="sxs-lookup"><span data-stu-id="706ed-134">You can save the original behavior by using the <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> method and restore it as required.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="706ed-135">示例</span><span class="sxs-lookup"><span data-stu-id="706ed-135">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="getting-and-setting-a-property-in-visual-basic"></a><span data-ttu-id="706ed-136">在 Visual Basic 中获取和设置属性</span><span class="sxs-lookup"><span data-stu-id="706ed-136">Getting and Setting a Property in Visual Basic</span></span>  
 <span data-ttu-id="706ed-137">此代码示例演示如何获取 <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Information> 属性，以及如何将 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> 属性的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 属性设置为 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 枚举类型的 `ExecuteSql` 成员。</span><span class="sxs-lookup"><span data-stu-id="706ed-137">This code example shows how to get the <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Information> object and how to set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property to the `ExecuteSql` member of the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> enumerated type.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties1](SMO How to#SMO_VBProperties1)]  -->  
  
## <a name="getting-and-setting-a-property-in-visual-c"></a><span data-ttu-id="706ed-138">在 Visual C# 中获取和设置属性</span><span class="sxs-lookup"><span data-stu-id="706ed-138">Getting and Setting a Property in Visual C#</span></span>  
 <span data-ttu-id="706ed-139">此代码示例演示如何获取 <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Information> 属性，以及如何将 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> 属性的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 属性设置为 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 枚举类型的 `ExecuteSql` 成员。</span><span class="sxs-lookup"><span data-stu-id="706ed-139">This code example shows how to get the <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Information> object and how to set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property to the `ExecuteSql` member of the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> enumerated type.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Get a property.   
Console.WriteLine(srv.Information.Version);   
//Set a property.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-basic"></a><span data-ttu-id="706ed-140">在 Visual Basic 中创建对象之前设置各种属性</span><span class="sxs-lookup"><span data-stu-id="706ed-140">Setting Various Properties Before an Object is Created in Visual Basic</span></span>  
 <span data-ttu-id="706ed-141">此代码示例演示如何直接设置 <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Table> 属性，以及如何在创建 <xref:Microsoft.SqlServer.Management.Smo.Table> 对象之前创建和添加列。</span><span class="sxs-lookup"><span data-stu-id="706ed-141">This code example shows how to directly set the <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Table> object, and how to create and add columns before you create the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties2](SMO How to#SMO_VBProperties2)]  -->  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-c"></a><span data-ttu-id="706ed-142">在 Visual C# 中创建对象之前设置各种属性</span><span class="sxs-lookup"><span data-stu-id="706ed-142">Setting Various Properties Before an Object is Created in Visual C#</span></span>  
 <span data-ttu-id="706ed-143">此代码示例演示如何直接设置 <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Table> 属性，以及如何在创建 <xref:Microsoft.SqlServer.Management.Smo.Table> 对象之前创建和添加列。</span><span class="sxs-lookup"><span data-stu-id="706ed-143">This code example shows how to directly set the <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Table> object, and how to create and add columns before you create the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Create a new table in the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
Table tb;   
//Specify the parent database, table schema, and the table name in the constructor.   
tb = new Table(db, "Test_Table", "HumanResources");   
//Add columns because the table requires columns before it can be created.   
Column c1;   
//Specify the parent table, the column name, and data type in the constructor.   
c1 = new Column(tb, "ID", DataType.Int);   
tb.Columns.Add(c1);   
c1.Nullable = false;   
c1.Identity = true;   
c1.IdentityIncrement = 1;   
c1.IdentitySeed = 0;   
Column c2;   
c2 = new Column(tb, "Name", DataType.NVarChar(100));   
c2.Nullable = false;   
tb.Columns.Add(c2);   
tb.AnsiNullsStatus = true;   
//Create the table on the instance of SQL Server.   
tb.Create();   
}  
```  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-basic"></a><span data-ttu-id="706ed-144">在 Visual Basic 中遍历对象的所有属性</span><span class="sxs-lookup"><span data-stu-id="706ed-144">Iterating Through All Properties of an Object in Visual Basic</span></span>  
 <span data-ttu-id="706ed-145">此代码示例遍历 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 对象的 `Properties` 集合，并将其显示在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的输出屏幕上。</span><span class="sxs-lookup"><span data-stu-id="706ed-145">This code example iterates through the `Properties` collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object and displays them on the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Output screen.</span></span>  
  
 <span data-ttu-id="706ed-146">在本示例中，由于 <xref:Microsoft.SqlServer.Management.Smo.Property> 对象同时也是 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 关键字，因此将该对象置于方括号中。</span><span class="sxs-lookup"><span data-stu-id="706ed-146">In the example, the <xref:Microsoft.SqlServer.Management.Smo.Property> object has been put in square parentheses because it is also a [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] keyword.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties3](SMO How to#SMO_VBProperties3)]  -->  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-c"></a><span data-ttu-id="706ed-147">在 Visual C# 中遍历对象的所有属性</span><span class="sxs-lookup"><span data-stu-id="706ed-147">Iterating Through All Properties of an Object in Visual C#</span></span>  
 <span data-ttu-id="706ed-148">此代码示例遍历 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 对象的 `Properties` 集合，并将其显示在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的输出屏幕上。</span><span class="sxs-lookup"><span data-stu-id="706ed-148">This code example iterates through the `Properties` collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object and displays them on the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Output screen.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Set properties on the uspGetEmployeedManagers stored procedure on the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
StoredProcedure sp;   
sp = db.StoredProcedures("uspGetEmployeeManagers");   
sp.AnsiNullsStatus = false;   
sp.QuotedIdentifierStatus = false;   
//Iterate through the properties of the stored procedure and display.   
  Property p;   
  foreach ( p in sp.Properties) {   
    Console.WriteLine(p.Name + p.Value);   
  }   
}  
```  
  
## <a name="setting-default-initialization-fields-in-visual-basic"></a><span data-ttu-id="706ed-149">在 Visual Basic 中设置默认的初始化字段</span><span class="sxs-lookup"><span data-stu-id="706ed-149">Setting Default Initialization Fields in Visual Basic</span></span>  
 <span data-ttu-id="706ed-150">此代码示例演示如何使 SMO 程序中初始化的对象属性的数目降到最低。</span><span class="sxs-lookup"><span data-stu-id="706ed-150">This code example shows how to minimize the number of object properties initialized in an SMO program.</span></span> <span data-ttu-id="706ed-151">您必须包括 `using System.Collections.Specialized`; 语句，以便使用 <xref:System.Collections.Specialized.StringCollection> 对象。</span><span class="sxs-lookup"><span data-stu-id="706ed-151">You have to include the `using System.Collections.Specialized`; statement to use the <xref:System.Collections.Specialized.StringCollection> object.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="706ed-152">可用于将发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的语句的数目和此优化进行比较。</span><span class="sxs-lookup"><span data-stu-id="706ed-152">can be used to compare the number statements sent to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with this optimization.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaultInitFields1](SMO How to#SMO_VBDefaultInitFields1)]  -->  
  
## <a name="setting-default-initialization-fields-in-visual-c"></a><span data-ttu-id="706ed-153">在 Visual C# 中设置默认的初始化字段</span><span class="sxs-lookup"><span data-stu-id="706ed-153">Setting Default Initialization Fields in Visual C#</span></span>  
 <span data-ttu-id="706ed-154">此代码示例演示如何使 SMO 程序中初始化的对象属性的数目降到最低。</span><span class="sxs-lookup"><span data-stu-id="706ed-154">This code example shows how to minimize the number of object properties initialized in an SMO program.</span></span> <span data-ttu-id="706ed-155">您必须包括 `using System.Collections.Specialized`; 语句，以便使用 <xref:System.Collections.Specialized.StringCollection> 对象。</span><span class="sxs-lookup"><span data-stu-id="706ed-155">You have to include the `using System.Collections.Specialized`; statement to use the <xref:System.Collections.Specialized.StringCollection> object.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="706ed-156">可用于将发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的语句的数目和此优化进行比较。</span><span class="sxs-lookup"><span data-stu-id="706ed-156">can be used to compare the number statements sent to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with this optimization.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Assign the Table object type to a System.Type object variable.   
Table tb;   
Type typ;   
tb = new Table();   
typ = tb.GetType;   
//Assign the current default initialization fields for the Table object type to a   
//StringCollection object variable.   
StringCollection sc;   
sc = srv.GetDefaultInitFields(typ);   
//Set the default initialization fields for the Table object type to the CreateDate property.   
srv.SetDefaultInitFields(typ, "CreateDate");   
//Retrieve the Schema, Name, and CreateDate properties for every table in AdventureWorks2012.   
   //Note that the improvement in performance can be viewed in SQL Server Profiler.   
foreach ( tb in db.Tables) {   
   Console.WriteLine(tb.Schema + "." + tb.Name + " " + tb.CreateDate);   
}   
//Set the default initialization fields for the Table object type back to the original settings.   
srv.SetDefaultInitFields(typ, sc);   
}  
```  
  
  
