---
title: 查询表达式和统一资源名称 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- query expressions
- unique resource names
- URN
ms.assetid: e0d30dbe-7daf-47eb-8412-1b96792b6fb9
author: stevestein
ms.author: sstein
ms.openlocfilehash: db6e311dd7d8a824b0e2f22e538e15eefa9fd9ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581349"
---
# <a name="query-expressions-and-uniform-resource-names"></a><span data-ttu-id="c5430-102">查询表达式和统一资源名称</span><span class="sxs-lookup"><span data-stu-id="c5430-102">Query Expressions and Uniform Resource Names</span></span>
  <span data-ttu-id="c5430-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理对象 (SMO) 模型和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 管理单元使用与 XPath 表达式相似的两种类型的表达式。</span><span class="sxs-lookup"><span data-stu-id="c5430-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object (SMO) models and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins use two types of expression strings that are similar to XPath expressions.</span></span> <span data-ttu-id="c5430-104">查询表达式是指定一组条件的字符串，用于枚举对象模型层次结构中的一个或多个对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-104">Query expressions are strings that specify a set of criteria used to enumerate one or more objects in an object model hierarchy.</span></span> <span data-ttu-id="c5430-105">统一资源名称 (URN) 是一种特定类型的查询表达式字符串，用于唯一标识单个对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-105">A Uniform Resource Name (URN) is a specific type of query expression string that uniquely identifies a single object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5430-106">语法</span><span class="sxs-lookup"><span data-stu-id="c5430-106">Syntax</span></span>  
  
```
      Object1  
      [<FilterExpression1>]/ ... /ObjectN[<FilterExpressionN>]<FilterExpression>::=  
<PropertyExpression> [and <PropertyExpression>][...n]  
  
<PropertyExpression>::=@BooleanPropertyName=true()  
 | @BooleanPropertyName=false()  
 | contains(@StringPropertyName, 'PatternString')  
  | @StringPropertyName='String'  
 | @DatePropertyName=datetime('DateString')  
 | is_null(@PropertyName)  
 | not(<PropertyExpression>)  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5430-107">参数</span><span class="sxs-lookup"><span data-stu-id="c5430-107">Arguments</span></span>  
 <span data-ttu-id="c5430-108">*Object*</span><span class="sxs-lookup"><span data-stu-id="c5430-108">*Object*</span></span>  
 <span data-ttu-id="c5430-109">指定在表达式字符串的节点表示的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="c5430-109">Specifies the type of object that is represented at that node of the expression string.</span></span> <span data-ttu-id="c5430-110">每个对象表示那些 SMO 对象模型名称空间中的一个集合类：</span><span class="sxs-lookup"><span data-stu-id="c5430-110">Each object represents a collection class from these SMO object model namespaces:</span></span>  
  
 <xref:Microsoft.SqlServer.Management.Smo>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Agent>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Mail>  
  
 <xref:Microsoft.SqlServer.Management.Dmf>  
  
 <xref:Microsoft.SqlServer.Management.Facets>  
  
 <xref:Microsoft.SqlServer.Management.RegisteredServers>  
  
 <xref:Microsoft.SqlServer.Management.Smo.RegSvrEnum>  
  
 <span data-ttu-id="c5430-111">例如，为 **ServerCollection** 类指定“服务器”，为 **DatabaseCollection** 类指定“数据库”。</span><span class="sxs-lookup"><span data-stu-id="c5430-111">For example, specify Server for the **ServerCollection** class, Database for the **DatabaseCollection** class.</span></span>  
  
 <span data-ttu-id="c5430-112">\@*PropertyName*</span><span class="sxs-lookup"><span data-stu-id="c5430-112">\@*PropertyName*</span></span>  
 <span data-ttu-id="c5430-113">指定与\*\*“对象”中指定的对象相关联的类的其中一个属性的名称。</span><span class="sxs-lookup"><span data-stu-id="c5430-113">Specifies the name of one of the properties of the class that is associated with the object specified in *Object*.</span></span> <span data-ttu-id="c5430-114">属性名必须以字符 \@ 为前缀。</span><span class="sxs-lookup"><span data-stu-id="c5430-114">The name of the property must be prefixed with the \@ character.</span></span> <span data-ttu-id="c5430-115">例如，对 Database\*\*\*\* 类的 IsAnsiNull\*\*\*\* 属性指定 \@IsAnsiNull。</span><span class="sxs-lookup"><span data-stu-id="c5430-115">For example, specify \@IsAnsiNull for the **Database** class property **IsAnsiNull**.</span></span>  
  
 <span data-ttu-id="c5430-116">\@*BooleanPropertyName*=true()</span><span class="sxs-lookup"><span data-stu-id="c5430-116">\@*BooleanPropertyName*=true()</span></span>  
 <span data-ttu-id="c5430-117">枚举指定的布尔属性设置为 TRUE 的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-117">Enumerates all objects where the specified Boolean property is set to TRUE.</span></span>  
  
 <span data-ttu-id="c5430-118">\@*BooleanPropertyName*=false()</span><span class="sxs-lookup"><span data-stu-id="c5430-118">\@*BooleanPropertyName*=false()</span></span>  
 <span data-ttu-id="c5430-119">枚举指定的布尔属性设置为 FALSE 的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-119">Enumerates all objects where the specified Boolean property is set to FALSE.</span></span>  
  
 <span data-ttu-id="c5430-120">contains(\@StringPropertyName**, 'PatternString**')</span><span class="sxs-lookup"><span data-stu-id="c5430-120">contains(\@*StringPropertyName*, '*PatternString*')</span></span>  
 <span data-ttu-id="c5430-121">枚举指定的字符串属性中包含“*PatternString*”中指定的一组字符（至少出现一次）的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-121">Enumerates all objects where the specified string property contains at least one occurrence of the set of characters that is specified in '*PatternString*'.</span></span>  
  
 <span data-ttu-id="c5430-122">\@*StringPropertyName*='*PatternString*'</span><span class="sxs-lookup"><span data-stu-id="c5430-122">\@*StringPropertyName*='*PatternString*'</span></span>  
 <span data-ttu-id="c5430-123">枚举指定字符串属性的值与在“*PatternString*”中指定的字符模式完全相同的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-123">Enumerates all objects where the value of the specified string property is exactly the same as the character pattern that is specified in '*PatternString*'.</span></span>  
  
 <span data-ttu-id="c5430-124">\@*DatePropertyName*= datetime('*DateString*')</span><span class="sxs-lookup"><span data-stu-id="c5430-124">\@*DatePropertyName*= datetime('*DateString*')</span></span>  
 <span data-ttu-id="c5430-125">枚举指定日期属性的值与在“*DateString*”中指定的日期相匹配的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-125">Enumerates all objects where the value of the specified date property matches the date that is specified in '*DateString*'.</span></span> <span data-ttu-id="c5430-126">*DateString* 必须遵循格式 yyyy-mm-dd hh:mi:ss.mmm</span><span class="sxs-lookup"><span data-stu-id="c5430-126">*DateString* must follow the format yyyy-mm-dd hh:mi:ss.mmm</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c5430-127">yyyy</span><span class="sxs-lookup"><span data-stu-id="c5430-127">yyyy</span></span>|<span data-ttu-id="c5430-128">四位数年份。</span><span class="sxs-lookup"><span data-stu-id="c5430-128">Four digit year.</span></span>|  
|<span data-ttu-id="c5430-129">mm</span><span class="sxs-lookup"><span data-stu-id="c5430-129">mm</span></span>|<span data-ttu-id="c5430-130">两位数月份（01 到 12）。</span><span class="sxs-lookup"><span data-stu-id="c5430-130">Two digit month (01 through 12).</span></span>|  
|<span data-ttu-id="c5430-131">dd</span><span class="sxs-lookup"><span data-stu-id="c5430-131">dd</span></span>|<span data-ttu-id="c5430-132">两位数日期（01 到 31）。</span><span class="sxs-lookup"><span data-stu-id="c5430-132">Two digit date (01 through 31).</span></span>|  
|<span data-ttu-id="c5430-133">hh</span><span class="sxs-lookup"><span data-stu-id="c5430-133">hh</span></span>|<span data-ttu-id="c5430-134">24 小时制的两位数小时（01 到 23）。</span><span class="sxs-lookup"><span data-stu-id="c5430-134">Two digit hour using a 24 hour clock (01 through 23).</span></span>|  
|<span data-ttu-id="c5430-135">mi</span><span class="sxs-lookup"><span data-stu-id="c5430-135">mi</span></span>|<span data-ttu-id="c5430-136">两位数分钟（01 到 59）。</span><span class="sxs-lookup"><span data-stu-id="c5430-136">Two digit minutes (01 through 59).</span></span>|  
|<span data-ttu-id="c5430-137">ss</span><span class="sxs-lookup"><span data-stu-id="c5430-137">ss</span></span>|<span data-ttu-id="c5430-138">两位数秒数（01 到 59）。</span><span class="sxs-lookup"><span data-stu-id="c5430-138">Two digit seconds (01 through 59).</span></span>|  
|<span data-ttu-id="c5430-139">mmm</span><span class="sxs-lookup"><span data-stu-id="c5430-139">mmm</span></span>|<span data-ttu-id="c5430-140">毫秒数（001 到 999）。</span><span class="sxs-lookup"><span data-stu-id="c5430-140">Number of milliseconds (001 through 999).</span></span>|  
  
 <span data-ttu-id="c5430-141">可以按照存储在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中的任何日期格式，计算以此格式指定的日期。</span><span class="sxs-lookup"><span data-stu-id="c5430-141">The dates that are specified in this format can be evaluated against any date format that is stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c5430-142">is_null(\@PropertyName\*\*)</span><span class="sxs-lookup"><span data-stu-id="c5430-142">is_null(\@*PropertyName*)</span></span>  
 <span data-ttu-id="c5430-143">枚举指定属性的值为 NULL 的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-143">Enumerates all objects where the specified property has a value of NULL.</span></span>  
  
 <span data-ttu-id="c5430-144">未 (\<*PropertyExpression*>) </span><span class="sxs-lookup"><span data-stu-id="c5430-144">not(\<*PropertyExpression*>)</span></span>  
 <span data-ttu-id="c5430-145">对 *PropertyExpression*的计算值求反，枚举与 *PropertyExpression*中指定的条件不匹配的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-145">Negates the evaluation value of the *PropertyExpression*, enumerating all objects that do not match the condition specified in *PropertyExpression*.</span></span> <span data-ttu-id="c5430-146">例如，not(contains(\@Name, 'xyz')) 枚举名称中不含字符串 xyz 的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-146">For example, not(contains(\@Name, 'xyz')) enumerates all objects that do not have the string xyz in their names.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5430-147">备注</span><span class="sxs-lookup"><span data-stu-id="c5430-147">Remarks</span></span>  
 <span data-ttu-id="c5430-148">查询表达式是一些字符串，用于枚举 SMO 模型层次结构中的节点。</span><span class="sxs-lookup"><span data-stu-id="c5430-148">Query expressions are strings that enumerate the nodes in an SMO model hierarchy.</span></span> <span data-ttu-id="c5430-149">每个节点有一个筛选表达式，指定用于确定要枚举该节点的哪些对象的条件。</span><span class="sxs-lookup"><span data-stu-id="c5430-149">Each node has a filter expression that specifies the criteria for determining which objects at that node are enumerated.</span></span> <span data-ttu-id="c5430-150">查询表达式在 XPath 表达式语言上建模。</span><span class="sxs-lookup"><span data-stu-id="c5430-150">Query expressions are modeled on the XPath expression language.</span></span> <span data-ttu-id="c5430-151">查询表达式实现了 XPath 支持的一小部分表达式，还具有 XPath 中不提供的一些扩展。</span><span class="sxs-lookup"><span data-stu-id="c5430-151">Query expressions implement a small subset of the expressions that are supported by XPath, and also have some extensions that are not found in XPath.</span></span> <span data-ttu-id="c5430-152">XPath 表达式是一些字符串，指定用于枚举 XML 文档中的一个或多个标记的一组条件。</span><span class="sxs-lookup"><span data-stu-id="c5430-152">XPath expressions are strings that specify a set of criteria that are used to enumerate one or more of the tags in an XML document.</span></span> <span data-ttu-id="c5430-153">有关 XPath 的详细信息，请参阅 [W3C XPath Language](http://www.w3.org/TR/xpath20/)（W3C Xpath 语言）。</span><span class="sxs-lookup"><span data-stu-id="c5430-153">For more information about XPath, see [W3C XPath Language](http://www.w3.org/TR/xpath20/).</span></span>  
  
 <span data-ttu-id="c5430-154">查询表达式必须以对服务器对象的绝对引用开头。</span><span class="sxs-lookup"><span data-stu-id="c5430-154">Query expressions must start with an absolute reference to the Server object.</span></span> <span data-ttu-id="c5430-155">不允许使用以 / 开头的相对表达式。</span><span class="sxs-lookup"><span data-stu-id="c5430-155">Relative expressions with a leading / are not allowed.</span></span> <span data-ttu-id="c5430-156">查询表达式中指定的对象的顺序必须遵循相关对象模型中集合对象的层次结构。</span><span class="sxs-lookup"><span data-stu-id="c5430-156">The sequence of objects that are specified in a query expression must follow the hierarchy of collection objects in the associated object model.</span></span> <span data-ttu-id="c5430-157">例如，引用 Microsoft.SqlServer.Management.Smo 命令空间中对象的查询表达式必须从服务器节点开始，接下来才是数据库节点等。</span><span class="sxs-lookup"><span data-stu-id="c5430-157">For example, a query expression that references objects in the Microsoft.SqlServer.Management.Smo namespace must start with a Server node followed by a Database node, and so on.</span></span>  
  
 <span data-ttu-id="c5430-158">如果 *\<FilterExpression>* 没有为对象指定，则会枚举该节点的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-158">If a *\<FilterExpression>* is not specified for an object, all the objects at that node are enumerated.</span></span>  
  
## <a name="uniform-resource-names-urn"></a><span data-ttu-id="c5430-159">统一资源名称 (URN)</span><span class="sxs-lookup"><span data-stu-id="c5430-159">Uniform Resource Names (URN)</span></span>  
 <span data-ttu-id="c5430-160">URN 是查询表达式的子集。</span><span class="sxs-lookup"><span data-stu-id="c5430-160">URNs are a subset of query expressions.</span></span> <span data-ttu-id="c5430-161">每个 URN 形成对单个对象的完全限定引用。</span><span class="sxs-lookup"><span data-stu-id="c5430-161">Each URN forms a fully-qualified reference to a single object.</span></span> <span data-ttu-id="c5430-162">典型的 URN 使用 Name 属性来标识每个节点的单个对象。</span><span class="sxs-lookup"><span data-stu-id="c5430-162">A typical URN uses the Name property to identify a single object at each node.</span></span> <span data-ttu-id="c5430-163">例如，该 URN 引用一个特定列：</span><span class="sxs-lookup"><span data-stu-id="c5430-163">For example, this URN refers to a specific column:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[@Name='SalesPerson' and @Schema='Sales']/Column[@Name='SalesPersonID']  
```  
  
## <a name="examples"></a><span data-ttu-id="c5430-164">示例</span><span class="sxs-lookup"><span data-stu-id="c5430-164">Examples</span></span>  
  
### <a name="a-enumerating-objects-using-false"></a><span data-ttu-id="c5430-165">A.</span><span class="sxs-lookup"><span data-stu-id="c5430-165">A.</span></span> <span data-ttu-id="c5430-166">使用 false() 枚举对象</span><span class="sxs-lookup"><span data-stu-id="c5430-166">Enumerating objects using false()</span></span>  
 <span data-ttu-id="c5430-167">此查询表达式枚举 **MyComputer** 上默认实例中 **AutoClose**属性设置为 False 的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="c5430-167">This query expression enumerates all the databases that have the **AutoClose** attribute set to false in the default instance on **MyComputer**.</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@AutoClose=false()]  
```  
  
### <a name="b-enumerating-objects-using-contains"></a><span data-ttu-id="c5430-168">B.</span><span class="sxs-lookup"><span data-stu-id="c5430-168">B.</span></span> <span data-ttu-id="c5430-169">使用 contains 枚举对象</span><span class="sxs-lookup"><span data-stu-id="c5430-169">Enumerating objects using contains</span></span>  
 <span data-ttu-id="c5430-170">此查询表达式枚举所有区分大小写、并且名称中包含“m”的数据库。</span><span class="sxs-lookup"><span data-stu-id="c5430-170">This query expression enumerates all the databases that are case-insensitive and have the character 'm' in their name.</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@CaseSensitive=false() and contains(@Name, 'm')]   
```  
  
### <a name="c-enumerating-objects-using-not"></a><span data-ttu-id="c5430-171">C.</span><span class="sxs-lookup"><span data-stu-id="c5430-171">C.</span></span> <span data-ttu-id="c5430-172">使用 not 枚举对象</span><span class="sxs-lookup"><span data-stu-id="c5430-172">Enumerating objects using not</span></span>  
 <span data-ttu-id="c5430-173">此查询表达式枚举不在 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] Production **架构中、而且表名中包含“History”一词的所有** 表：</span><span class="sxs-lookup"><span data-stu-id="c5430-173">This query expression enumerates all of [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] tables that are not in the **Production** schema and contain the word History in the table name:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[not(@Schema='Production') and contains(@Name, 'History')]  
```  
  
### <a name="d-not-supplying-a-filter-expression-for-the-final-node"></a><span data-ttu-id="c5430-174">D.</span><span class="sxs-lookup"><span data-stu-id="c5430-174">D.</span></span> <span data-ttu-id="c5430-175">不为最终节点提供筛选表达式</span><span class="sxs-lookup"><span data-stu-id="c5430-175">Not supplying a filter expression for the final node</span></span>  
 <span data-ttu-id="c5430-176">此查询表达式枚举 **AdventureWorks2012.Sales.SalesPerson** 表中的所有列：</span><span class="sxs-lookup"><span data-stu-id="c5430-176">This query expression enumerates all the columns in the **AdventureWorks2012.Sales.SalesPerson** table:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@Schema='Sales' and @Name='SalesPerson']/Columns  
```  
  
### <a name="e-enumerating-objects-using-datetime"></a><span data-ttu-id="c5430-177">E.</span><span class="sxs-lookup"><span data-stu-id="c5430-177">E.</span></span> <span data-ttu-id="c5430-178">使用 datetime 枚举对象</span><span class="sxs-lookup"><span data-stu-id="c5430-178">Enumerating objects using datetime</span></span>  
 <span data-ttu-id="c5430-179">此查询表达式枚举 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库中于特定时间创建的所有表：</span><span class="sxs-lookup"><span data-stu-id="c5430-179">This query expression enumerates all the tables that are created in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database at a specific time:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@CreateDate=datetime('2008-03-21 19:49:32.647')]  
```  
  
### <a name="f-enumerating-objects-using-is_null"></a><span data-ttu-id="c5430-180">F.</span><span class="sxs-lookup"><span data-stu-id="c5430-180">F.</span></span> <span data-ttu-id="c5430-181">使用 is_null 枚举对象</span><span class="sxs-lookup"><span data-stu-id="c5430-181">Enumerating objects using is_null</span></span>  
 <span data-ttu-id="c5430-182">此查询表达式枚举 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库中上次修改日期属性不为 Null 的所有表：</span><span class="sxs-lookup"><span data-stu-id="c5430-182">This query expression enumerates all the tables in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database that do not have NULL for their date last modified property:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[Not(is_null(@DateLastModified))]  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5430-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5430-183">See Also</span></span>  
 <span data-ttu-id="c5430-184">[Invoke-policyevaluation cmdlet](../database-engine/invoke-policyevaluation-cmdlet.md) </span><span class="sxs-lookup"><span data-stu-id="c5430-184">[Invoke-PolicyEvaluation cmdlet](../database-engine/invoke-policyevaluation-cmdlet.md) </span></span>  
 [<span data-ttu-id="c5430-185">SQL Server Audit（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="c5430-185">SQL Server Audit &#40;Database Engine&#41;</span></span>](../relational-databases/security/auditing/sql-server-audit-database-engine.md)  
