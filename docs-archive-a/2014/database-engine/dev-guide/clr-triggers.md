---
title: CLR 触发器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- inserted tables
- database objects [CLR integration], triggers
- common language runtime [SQL Server], triggers
- updated columns
- building database objects [CLR integration], triggers
- triggers [CLR integration]
- deleted tables
- EventData property
- SqlTriggerContext class
- transactions [CLR integration]
ms.assetid: 302a4e4a-3172-42b6-9cc0-4a971ab49c1c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 91f12b0d97d2e2065c5bb08d175253c22dffb032
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579731"
---
# <a name="clr-triggers"></a><span data-ttu-id="87dad-102">CLR 触发器</span><span class="sxs-lookup"><span data-stu-id="87dad-102">CLR Triggers</span></span>
  <span data-ttu-id="87dad-103">由于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 与 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 公共语言运行时 (CLR) 集成，因此，您可以使用任何 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 语言来创建 CLR 触发器。</span><span class="sxs-lookup"><span data-stu-id="87dad-103">Because of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integration with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR), you can use any [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] language to create CLR triggers.</span></span> <span data-ttu-id="87dad-104">本部分包含通过 CLR 集成实现的触发器的特定信息。</span><span class="sxs-lookup"><span data-stu-id="87dad-104">This section covers information specific to triggers implemented with CLR integration.</span></span> <span data-ttu-id="87dad-105">有关触发器的完整讨论，请参阅[DDL 触发器](../../relational-databases/triggers/ddl-triggers.md)。</span><span class="sxs-lookup"><span data-stu-id="87dad-105">For a complete discussion of triggers, see [DDL Triggers](../../relational-databases/triggers/ddl-triggers.md).</span></span>  
  
## <a name="what-are-triggers"></a><span data-ttu-id="87dad-106">什么是触发器？</span><span class="sxs-lookup"><span data-stu-id="87dad-106">What Are Triggers?</span></span>  
 <span data-ttu-id="87dad-107">触发器是特殊类型的存储过程，可在执行某个语言事件时自动运行。</span><span class="sxs-lookup"><span data-stu-id="87dad-107">A trigger is a special type of stored procedure that automatically runs when a language event executes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="87dad-108">包括两种常规类型的触发器：数据操作语言 (DML) 触发器和数据定义语言 (DDL) 触发器。</span><span class="sxs-lookup"><span data-stu-id="87dad-108">includes two general types of triggers: data manipulation language (DML) and data definition language (DDL) triggers.</span></span> <span data-ttu-id="87dad-109">当 `INSERT`、`UPDATE` 或 `DELETE` 语句修改指定表或视图中的数据时，可以使用 DML 触发器。</span><span class="sxs-lookup"><span data-stu-id="87dad-109">DML triggers can be used when `INSERT`, `UPDATE`, or `DELETE` statements modify data in a specified table or view.</span></span> <span data-ttu-id="87dad-110">DDL 触发器激发存储过程以响应各种 DDL 语句，这些语句主要以 `CREATE`、`ALTER` 和 `DROP` 开头。</span><span class="sxs-lookup"><span data-stu-id="87dad-110">DDL triggers fire stored procedures in response to a variety of DDL statements, which are primarily statements that begin with `CREATE`, `ALTER`, and `DROP`.</span></span> <span data-ttu-id="87dad-111">DDL 触发器可用于管理任务，例如审核和控制数据库操作。</span><span class="sxs-lookup"><span data-stu-id="87dad-111">DDL triggers can be used for administrative tasks, such as auditing and regulating database operations.</span></span>  
  
## <a name="unique-capabilities-of-clr-triggers"></a><span data-ttu-id="87dad-112">CLR 触发器的特有功能</span><span class="sxs-lookup"><span data-stu-id="87dad-112">Unique Capabilities of CLR Triggers</span></span>  
 <span data-ttu-id="87dad-113">采用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 编写的触发器具有如下功能：确定已使用 `UPDATE(column)` 和 `COLUMNS_UPDATED()` 函数更新激发视图或表中的哪些列。</span><span class="sxs-lookup"><span data-stu-id="87dad-113">Triggers written in [!INCLUDE[tsql](../../includes/tsql-md.md)] have the capability of determining which columns from the firing view or table have been updated by using the `UPDATE(column)` and `COLUMNS_UPDATED()` functions.</span></span>  
  
 <span data-ttu-id="87dad-114">以 CLR 语言编写的触发器在若干重大方面均不同于其他 CLR 集成对象。</span><span class="sxs-lookup"><span data-stu-id="87dad-114">Triggers written in a CLR language differ from other CLR integration objects in several significant ways.</span></span> <span data-ttu-id="87dad-115">CLR 触发器可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="87dad-115">CLR triggers can:</span></span>  
  
-   <span data-ttu-id="87dad-116">引用 `INSERTED` 和 `DELETED` 表中的数据</span><span class="sxs-lookup"><span data-stu-id="87dad-116">Reference data in the `INSERTED` and `DELETED` tables</span></span>  
  
-   <span data-ttu-id="87dad-117">确定因 `UPDATE` 操作而修改了哪些列</span><span class="sxs-lookup"><span data-stu-id="87dad-117">Determine which columns have been modified as a result of an `UPDATE` operation</span></span>  
  
-   <span data-ttu-id="87dad-118">访问有关执行 DDL 语句所影响的数据库对象的信息。</span><span class="sxs-lookup"><span data-stu-id="87dad-118">Access information about database objects affected by the execution of DDL statements.</span></span>  
  
 <span data-ttu-id="87dad-119">这些功能采用查询语言在内部提供，或者由 `SqlTriggerContext` 类提供。</span><span class="sxs-lookup"><span data-stu-id="87dad-119">These capabilities are provided inherently in the query language, or by the `SqlTriggerContext` class.</span></span> <span data-ttu-id="87dad-120">有关 CLR 集成的优点以及如何在托管代码和之间进行选择的信息 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，请参阅[Clr 集成概述](../../relational-databases/clr-integration/clr-integration-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="87dad-120">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../../relational-databases/clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="using-the-sqltriggercontext-class"></a><span data-ttu-id="87dad-121">使用 SqlTriggerContext 类</span><span class="sxs-lookup"><span data-stu-id="87dad-121">Using the SqlTriggerContext Class</span></span>  
 <span data-ttu-id="87dad-122">`SqlTriggerContext` 类不能公开构造，只能通过访问 CLR 触发器主体中的 `SqlContext.TriggerContext` 属性获取。</span><span class="sxs-lookup"><span data-stu-id="87dad-122">The `SqlTriggerContext` class cannot be publicly constructed and can only be obtained by accessing the `SqlContext.TriggerContext` property within the body of a CLR trigger.</span></span> <span data-ttu-id="87dad-123">通过调用 `SqlTriggerContext` 属性可以从活动的 `SqlContext` 中获取 `SqlContext.TriggerContext` 类：</span><span class="sxs-lookup"><span data-stu-id="87dad-123">The `SqlTriggerContext` class can be obtained from the active `SqlContext` by calling the `SqlContext.TriggerContext` property:</span></span>  
  
 `SqlTriggerContext myTriggerContext = SqlContext.TriggerContext;`  
  
 <span data-ttu-id="87dad-124">`SqlTriggerContext` 类提供有关触发器的上下文信息。</span><span class="sxs-lookup"><span data-stu-id="87dad-124">The `SqlTriggerContext` class provides context information about the trigger.</span></span> <span data-ttu-id="87dad-125">该上下文信息包括导致触发器被激发的操作的类型，以及在 UPDATE 操作中进行了修改的列，如果是 DDL 触发器，则还包括描述触发操作的 XML `EventData` 结构。</span><span class="sxs-lookup"><span data-stu-id="87dad-125">This contextual information includes the type of action that caused the trigger to fire, which columns were modified in an UPDATE operation, and, in the case of a DDL trigger, an XML `EventData` structure which describes the triggering operation.</span></span> <span data-ttu-id="87dad-126">有关详细信息，请参阅[EVENTDATA &#40;transact-sql&#41;](/sql/t-sql/functions/eventdata-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="87dad-126">For more information, see [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql).</span></span>  
  
### <a name="determining-the-trigger-action"></a><span data-ttu-id="87dad-127">确定触发器操作</span><span class="sxs-lookup"><span data-stu-id="87dad-127">Determining the Trigger Action</span></span>  
 <span data-ttu-id="87dad-128">获取 `SqlTriggerContext` 之后，可以使用它来确定导致触发器被激发的操作类型。</span><span class="sxs-lookup"><span data-stu-id="87dad-128">Once you have obtained a `SqlTriggerContext`, you can use it to determine the type of action that caused the trigger to fire.</span></span> <span data-ttu-id="87dad-129">该信息可通过 `TriggerAction` 类的 `SqlTriggerContext` 属性获得。</span><span class="sxs-lookup"><span data-stu-id="87dad-129">This information is available through the `TriggerAction` property of the `SqlTriggerContext` class.</span></span>  
  
 <span data-ttu-id="87dad-130">对于 DML 触发器，`TriggerAction` 属性可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="87dad-130">For DML triggers, the `TriggerAction` property can be one of the following values:</span></span>  
  
-   <span data-ttu-id="87dad-131">TriggerAction.Update (0x1)</span><span class="sxs-lookup"><span data-stu-id="87dad-131">TriggerAction.Update (0x1)</span></span>  
  
-   <span data-ttu-id="87dad-132">TriggerAction.Insert (0x2)</span><span class="sxs-lookup"><span data-stu-id="87dad-132">TriggerAction.Insert (0x2)</span></span>  
  
-   <span data-ttu-id="87dad-133">TriggerAction.Delete(0x3)</span><span class="sxs-lookup"><span data-stu-id="87dad-133">TriggerAction.Delete(0x3)</span></span>  
  
-   <span data-ttu-id="87dad-134">对于 DDL 触发器，可能的 TriggerAction 值的列表要长得多。</span><span class="sxs-lookup"><span data-stu-id="87dad-134">For DDL triggers, the list of possible TriggerAction values is considerably longer.</span></span> <span data-ttu-id="87dad-135">有关详细信息，请参阅 .NET Framework SDK 中的“TriggerAction 枚举”。</span><span class="sxs-lookup"><span data-stu-id="87dad-135">Please see "TriggerAction Enumeration" in the .NET Framework SDK for more information.</span></span>  
  
### <a name="using-the-inserted-and-deleted-tables"></a><span data-ttu-id="87dad-136">使用插入的和删除的表</span><span class="sxs-lookup"><span data-stu-id="87dad-136">Using the Inserted and Deleted Tables</span></span>  
 <span data-ttu-id="87dad-137">DML 触发器语句使用两种特殊的表：**插入**的表和**已删除**的表。</span><span class="sxs-lookup"><span data-stu-id="87dad-137">Two special tables are used in DML trigger statements: the **inserted** table and the **deleted** table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="87dad-138">会自动创建和管理这两种表。</span><span class="sxs-lookup"><span data-stu-id="87dad-138">automatically creates and manages these tables.</span></span> <span data-ttu-id="87dad-139">您可以使用这两种临时表来测试特定数据修改的影响以及设置 DML 触发器操作条件；但是，不能直接更改表中的数据。</span><span class="sxs-lookup"><span data-stu-id="87dad-139">You can use these temporary tables to test the effects of certain data modifications and to set conditions for DML trigger actions; however, you cannot alter the data in the tables directly.</span></span>  
  
 <span data-ttu-id="87dad-140">CLR 触发器可以通过 CLR 进程内提供程序访问**插入**的和**删除**的表。</span><span class="sxs-lookup"><span data-stu-id="87dad-140">CLR triggers can access the **inserted** and **deleted** tables through the CLR in-process provider.</span></span> <span data-ttu-id="87dad-141">这是通过从 SqlContext 对象获取 `SqlCommand` 对象来完成的。</span><span class="sxs-lookup"><span data-stu-id="87dad-141">This is done by obtaining a `SqlCommand` object from the SqlContext object.</span></span> <span data-ttu-id="87dad-142">例如：</span><span class="sxs-lookup"><span data-stu-id="87dad-142">For example:</span></span>  
  
 <span data-ttu-id="87dad-143">C#</span><span class="sxs-lookup"><span data-stu-id="87dad-143">C#</span></span>  
  
```  
SqlConnection connection = new SqlConnection ("context connection = true");  
connection.Open();  
SqlCommand command = connection.CreateCommand();  
command.CommandText = "SELECT * from " + "inserted";  
```  
  
 <span data-ttu-id="87dad-144">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87dad-144">Visual Basic</span></span>  
  
```  
Dim connection As New SqlConnection("context connection=true")  
Dim command As SqlCommand  
connection.Open()  
command = connection.CreateCommand()  
command.CommandText = "SELECT * FROM " + "inserted"  
```  
  
### <a name="determining-updated-columns"></a><span data-ttu-id="87dad-145">确定更新的列</span><span class="sxs-lookup"><span data-stu-id="87dad-145">Determining Updated Columns</span></span>  
 <span data-ttu-id="87dad-146">可以使用 `ColumnCount` 对象的 `SqlTriggerContext` 属性确定 UPDATE 操作已修改的列数。</span><span class="sxs-lookup"><span data-stu-id="87dad-146">You can determine the number of columns that were modified by an UPDATE operation by using the `ColumnCount` property of the `SqlTriggerContext` object.</span></span> <span data-ttu-id="87dad-147">此外，还可以使用 `IsUpdatedColumn` 方法，该方法采用列序号作为输入参数，以便确定是否已更新列。</span><span class="sxs-lookup"><span data-stu-id="87dad-147">You can use the `IsUpdatedColumn` method, which takes the column ordinal as an input parameter, to determine whether the column was updated.</span></span> <span data-ttu-id="87dad-148">`True` 值指示已更新此列。</span><span class="sxs-lookup"><span data-stu-id="87dad-148">A `True` value indicates that the column has been updated.</span></span>  
  
 <span data-ttu-id="87dad-149">例如，以下代码段（摘自本主题后面的 EmailAudit 触发器）列出所有已更新的列：</span><span class="sxs-lookup"><span data-stu-id="87dad-149">For example, this code snippet (from the EmailAudit trigger later in this topic) lists all of the columns updated:</span></span>  
  
 <span data-ttu-id="87dad-150">C#</span><span class="sxs-lookup"><span data-stu-id="87dad-150">C#</span></span>  
  
```  
reader = command.ExecuteReader();  
reader.Read();  
for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
{  
   pipe.Send("Updated column "  
      + reader.GetName(columnNumber) + "? "  
   + triggContext.IsUpdatedColumn(columnNumber).ToString());  
 }  
  
 reader.Close();  
```  
  
 <span data-ttu-id="87dad-151">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87dad-151">Visual Basic</span></span>  
  
```  
reader = command.ExecuteReader()  
reader.Read()  
Dim columnNumber As Integer  
  
For columnNumber=0 To triggContext.ColumnCount-1  
  
   pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
   "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
Next  
  
reader.Close()  
```  
  
### <a name="accessing-eventdata-for-clr-ddl-triggers"></a><span data-ttu-id="87dad-152">访问 DDL 触发器的 EventData</span><span class="sxs-lookup"><span data-stu-id="87dad-152">Accessing EventData for CLR DDL Triggers</span></span>  
 <span data-ttu-id="87dad-153">像常规触发器一样，DDL 触发器将激发存储过程以响应事件。</span><span class="sxs-lookup"><span data-stu-id="87dad-153">DDL triggers, like regular triggers, fire stored procedures in response to an event.</span></span> <span data-ttu-id="87dad-154">但与 DML 触发器不同的是，它们不会为响应针对表或视图的 UPDATE、INSERT 或 DELETE 语句而激发，</span><span class="sxs-lookup"><span data-stu-id="87dad-154">But unlike DML triggers, they do not fire in response to UPDATE, INSERT, or DELETE statements on a table or view.</span></span> <span data-ttu-id="87dad-155">而是为响应各种 DDL 语句而激发，这些语句主要以 CREATE、ALTER 和 DROP 开头。</span><span class="sxs-lookup"><span data-stu-id="87dad-155">Instead, they fire in response to a variety of DDL statements, which are primarily statements that begin with CREATE, ALTER, and DROP.</span></span> <span data-ttu-id="87dad-156">DDL 触发器可用于管理任务，例如审核和监视数据库操作和架构更改。</span><span class="sxs-lookup"><span data-stu-id="87dad-156">DDL triggers can be used for administrative tasks, such as auditing and monitoring of database operations and schema changes.</span></span>  
  
 <span data-ttu-id="87dad-157">`EventData` 类的 `SqlTriggerContext` 属性提供了有关激发 DDL 触发器的事件的信息。</span><span class="sxs-lookup"><span data-stu-id="87dad-157">Information about an event that fires a DDL trigger is available in the `EventData` property of the `SqlTriggerContext` class.</span></span> <span data-ttu-id="87dad-158">该属性包含一个 `xml` 值。</span><span class="sxs-lookup"><span data-stu-id="87dad-158">This property contains an `xml` value.</span></span> <span data-ttu-id="87dad-159">xml 架构包括下列相关信息：</span><span class="sxs-lookup"><span data-stu-id="87dad-159">The xml schema includes information about:</span></span>  
  
-   <span data-ttu-id="87dad-160">事件时间。</span><span class="sxs-lookup"><span data-stu-id="87dad-160">The time of the event.</span></span>  
  
-   <span data-ttu-id="87dad-161">在执行触发器期间，连接的系统进程 ID (SPID)。</span><span class="sxs-lookup"><span data-stu-id="87dad-161">The System Process ID (SPID) of the connection during which the trigger executed.</span></span>  
  
-   <span data-ttu-id="87dad-162">激发触发器的事件类型。</span><span class="sxs-lookup"><span data-stu-id="87dad-162">The type of event that fired the trigger.</span></span>  
  
 <span data-ttu-id="87dad-163">然后，根据事件类型，该架构还包括其他信息，例如事件发生所在的数据库、发生事件的相关对象以及事件的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="87dad-163">Then, depending on the event type, the schema includes additional information, such as the database in which the event occurred, the object against which the event occurred, and the [!INCLUDE[tsql](../../includes/tsql-md.md)] command of the event.</span></span>  
  
 <span data-ttu-id="87dad-164">在下面的示例中，以下 DDL 触发器返回原始 `EventData` 属性。</span><span class="sxs-lookup"><span data-stu-id="87dad-164">In the following example, the following DDL trigger returns the raw `EventData` property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87dad-165">此处显示了如何使用 `SqlPipe` 对象发送结果和消息，此示例仅用于说明用途，通常，建议您不要将此示例用作对 CLR 触发器进行编程的生产代码。</span><span class="sxs-lookup"><span data-stu-id="87dad-165">Sending results and messages through the `SqlPipe` object is shown here for illustrative purposes only and is generally discouraged for production code when programming CLR triggers.</span></span> <span data-ttu-id="87dad-166">可能返回其他意外数据，并导致应用程序错误。</span><span class="sxs-lookup"><span data-stu-id="87dad-166">Additional data returned may be unexpected and lead to application errors.</span></span>  
  
 <span data-ttu-id="87dad-167">C#</span><span class="sxs-lookup"><span data-stu-id="87dad-167">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   public static void DropTableTrigger()  
   {  
       SqlTriggerContext triggContext = SqlContext.TriggerContext;             
  
       switch(triggContext.TriggerAction)  
       {  
           case TriggerAction.DropTable:  
           SqlContext.Pipe.Send("Table dropped! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
  
           default:  
           SqlContext.Pipe.Send("Something happened! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
       }  
   }  
}  
```  
  
 <span data-ttu-id="87dad-168">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87dad-168">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    Public Shared Sub DropTableTrigger()  
        Dim triggContext As SqlTriggerContext  
        triggContext = SqlContext.TriggerContext  
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.DropTable  
              SqlContext.Pipe.Send("Table dropped! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
           Case Else  
              SqlContext.Pipe.Send("Something else happened! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
        End Select  
    End Sub  
End Class     
```  
  
 <span data-ttu-id="87dad-169">下面的示例输出是 `EventData` 事件激发 DDL 触发器之后的 `CREATE TABLE` 属性值：</span><span class="sxs-lookup"><span data-stu-id="87dad-169">The following sample output is the `EventData` property value after a DDL trigger fired by a `CREATE TABLE` event:</span></span>  
  
 `<EVENT_INSTANCE><PostTime>2004-04-16T21:17:16.160</PostTime><SPID>58</SPID><EventType>CREATE_TABLE</EventType><ServerName>MACHINENAME</ServerName><LoginName>MYDOMAIN\myname</LoginName><UserName>MYDOMAIN\myname</UserName><DatabaseName>AdventureWorks</DatabaseName><SchemaName>dbo</SchemaName><ObjectName>UserName</ObjectName><ObjectType>TABLE</ObjectType><TSQLCommand><SetOptions ANSI_NULLS="ON" ANSI_NULL_DEFAULT="ON" ANSI_PADDING="ON" QUOTED_IDENTIFIER="ON" ENCRYPTED="FALSE" /><CommandText>create table dbo.UserName  
(  
 UserName varchar(50),  
 RealName varchar(50)  
)  
</CommandText></TSQLCommand></EVENT_INSTANCE>`  
  
 <span data-ttu-id="87dad-170">除通过 `SqlTriggerContext` 类访问的信息以外，查询仍可以引用在进程内执行的命令的文本中的`COLUMNS_UPDATED` 和插入的/删除的内容。</span><span class="sxs-lookup"><span data-stu-id="87dad-170">In addition to the information accessible through the `SqlTriggerContext` class, queries can still refer to `COLUMNS_UPDATED` and inserted/deleted within the text of a command executed in-process.</span></span>  
  
## <a name="sample-clr-trigger"></a><span data-ttu-id="87dad-171">示例 CLR 触发器</span><span class="sxs-lookup"><span data-stu-id="87dad-171">Sample CLR Trigger</span></span>  
 <span data-ttu-id="87dad-172">在本示例中，请考虑这样一种情况：允许用户选择他们需要的任何 ID，但是您希望知道哪些用户专门输入了电子邮件地址作为 ID。</span><span class="sxs-lookup"><span data-stu-id="87dad-172">In this example, consider the scenario in which you let the user choose any ID they want, but you want to know the users that specifically entered an e-mail address as an ID.</span></span> <span data-ttu-id="87dad-173">以下触发器将检测该信息并将其记录到审核表。</span><span class="sxs-lookup"><span data-stu-id="87dad-173">The following trigger would detect that information and log it to an audit table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87dad-174">此处显示了如何使用 `SqlPipe` 对象发送结果和消息，此示例仅用于说明用途，通常，建议您不要将此示例用作生产代码。</span><span class="sxs-lookup"><span data-stu-id="87dad-174">Sending results and messages through the `SqlPipe` object is shown here for illustrative purposes only and is generally discouraged for production code.</span></span> <span data-ttu-id="87dad-175">返回的额外数据可能并非预期并可能导致应用程序错误。</span><span class="sxs-lookup"><span data-stu-id="87dad-175">Additional data returned may be unexpected and lead to application errors</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   [SqlTrigger(Name = @"EmailAudit", Target = "[dbo].[Users]", Event = "FOR INSERT, UPDATE, DELETE")]  
   public static void EmailAudit()  
   {  
      string userName;  
      string realName;  
      SqlCommand command;  
      SqlTriggerContext triggContext = SqlContext.TriggerContext;  
      SqlPipe pipe = SqlContext.Pipe;  
      SqlDataReader reader;  
  
      switch (triggContext.TriggerAction)  
      {  
         case TriggerAction.Insert:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
            reader.Close();  
  
            if (IsValidEMailAddress(userName))  
            {  
               command = new SqlCommand(  
                  @"INSERT [dbo].[UserNameAudit] VALUES ('"  
                  + userName + @"', '" + realName + @"');",  
                  connection);  
               pipe.Send(command.CommandText);  
               command.ExecuteNonQuery();  
               pipe.Send("You inserted: " + userName);  
            }  
         }  
  
         break;  
  
         case TriggerAction.Update:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
  
            pipe.Send(@"You updated: '" + userName + @"' - '"  
               + realName + @"'");  
  
            for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
            {  
               pipe.Send("Updated column "  
                  + reader.GetName(columnNumber) + "? "  
                  + triggContext.IsUpdatedColumn(columnNumber).ToString());  
            }  
  
            reader.Close();  
         }  
  
         break;  
  
         case TriggerAction.Delete:  
            using (SqlConnection connection  
               = new SqlConnection(@"context connection=true"))  
               {  
                  connection.Open();  
                  command = new SqlCommand(@"SELECT * FROM DELETED;",  
                     connection);  
                  reader = command.ExecuteReader();  
  
                  if (reader.HasRows)  
                  {  
                     pipe.Send(@"You deleted the following rows:");  
                     while (reader.Read())  
                     {  
                        pipe.Send(@"'" + reader.GetString(0)  
                        + @"', '" + reader.GetString(1) + @"'");  
                     }  
  
                     reader.Close();  
  
                     //alternately, to just send a tabular resultset back:  
                     //pipe.ExecuteAndSend(command);  
                  }  
                  else  
                  {  
                     pipe.Send("No rows affected.");  
                  }  
               }  
  
               break;  
            }  
        }  
  
     public static bool IsValidEMailAddress(string email)  
     {  
         return Regex.IsMatch(email, @"^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$");  
     }  
}  
```  
  
 <span data-ttu-id="87dad-176">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87dad-176">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Text.RegularExpressions  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    <SqlTrigger(Name:="EmailAudit", Target:="[dbo].[Users]", Event:="FOR INSERT, UPDATE, DELETE")> _  
    Public Shared Sub EmailAudit()  
        Dim userName As String  
        Dim realName As String  
        Dim command As SqlCommand  
        Dim triggContext As SqlTriggerContext  
        Dim pipe As SqlPipe  
        Dim reader As SqlDataReader    
  
        triggContext = SqlContext.TriggerContext      
        pipe = SqlContext.Pipe    
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.Insert  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 reader.Close()  
  
                 If IsValidEmailAddress(userName) Then  
                     command = New SqlCommand("INSERT [dbo].[UserNameAudit] VALUES ('" & _  
                       userName & "', '" & realName & "');", connection)  
  
                    pipe.Send(command.CommandText)  
                    command.ExecuteNonQuery()  
                    pipe.Send("You inserted: " & userName)  
  
                 End If  
              End Using  
  
           Case TriggerAction.Update  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 pipe.Send("You updated: " & userName & " - " & realName)  
  
                 Dim columnNumber As Integer  
  
                 For columnNumber=0 To triggContext.ColumnCount-1  
  
                    pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
                      "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
                 Next  
  
                 reader.Close()  
              End Using  
  
           Case TriggerAction.Delete  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM DELETED;", connection)  
  
                 reader = command.ExecuteReader()  
  
                 If reader.HasRows Then  
                    pipe.Send("You deleted the following rows:")  
  
                    While reader.Read()  
  
                       pipe.Send( reader.GetString(0) & ", " & reader.GetString(1) )  
  
                    End While   
  
                    reader.Close()  
  
                    ' Alternately, just send a tabular resultset back:  
                    ' pipe.ExecuteAndSend(command)  
  
                 Else  
                   pipe.Send("No rows affected.")  
                 End If  
  
              End Using   
        End Select  
    End Sub  
  
    Public Shared Function IsValidEMailAddress(emailAddress As String) As Boolean  
  
       return Regex.IsMatch(emailAddress, "^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$")  
    End Function      
End Class  
```  
  
 <span data-ttu-id="87dad-177">假定存在具有以下定义的两个表：</span><span class="sxs-lookup"><span data-stu-id="87dad-177">Assuming two tables exist with the following definitions:</span></span>  
  
```  
CREATE TABLE Users  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
);  
GO CREATE TABLE UserNameAudit  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
)  
```  
  
 <span data-ttu-id="87dad-178">[!INCLUDE[tsql](../../includes/tsql-md.md)]在中创建触发器的语句如下所示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，并且假定已在**SQLCLRTest**当前数据库中注册程序集 SQLCLRTest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="87dad-178">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that creates the trigger in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is as follows, and assumes assembly **SQLCLRTest** is already registered in the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
```  
CREATE TRIGGER EmailAudit  
ON Users  
FOR INSERT, UPDATE, DELETE  
AS  
EXTERNAL NAME SQLCLRTest.CLRTriggers.EmailAudit  
```  
  
## <a name="validating-and-canceling-invalid-transactions"></a><span data-ttu-id="87dad-179">验证和取消无效事务</span><span class="sxs-lookup"><span data-stu-id="87dad-179">Validating and Canceling Invalid Transactions</span></span>  
 <span data-ttu-id="87dad-180">使用触发器验证和取消无效 INSERT、UPDATE 或 DELETE 事务或防止对数据库架构进行更改，这一用法很常见。</span><span class="sxs-lookup"><span data-stu-id="87dad-180">Using triggers to validate and cancel invalid INSERT, UPDATE, or DELETE transactions or to prevent changes to your database schema is common.</span></span> <span data-ttu-id="87dad-181">如果操作不满足验证条件，将验证逻辑并入触发器并回滚当前事务可以实现上述目的。</span><span class="sxs-lookup"><span data-stu-id="87dad-181">This can be accomplished by incorporating validation logic into your trigger and then rolling back the current transaction if the action does not meet the validation criteria.</span></span>  
  
 <span data-ttu-id="87dad-182">当在触发器内部调用 `Transaction.Rollback` 方法或带有“TRANSACTION ROLLBACK”命令文本的 SqlCommand 时，将引发异常并显示不明确的错误消息，必须在 try/catch 块中包装此方法或命令。</span><span class="sxs-lookup"><span data-stu-id="87dad-182">When called within a trigger, the `Transaction.Rollback` method or a SqlCommand with the command text "TRANSACTION ROLLBACK" throws an exception with an ambiguous error message and must be wrapped in a try/catch block.</span></span> <span data-ttu-id="87dad-183">您会看到如下错误消息：</span><span class="sxs-lookup"><span data-stu-id="87dad-183">The error message you see is similar to the following:</span></span>  
  
```  
Msg 6549, Level 16, State 1, Procedure trig_InsertValidator, Line 0  
A .NET Framework error occurred during execution of user defined routine or aggregate 'trig_InsertValidator':   
System.Data.SqlClient.SqlException: Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting... User transaction, if any, will be rolled back.  
```  
  
 <span data-ttu-id="87dad-184">应出现该异常，而且需要 try/catch 块才能继续执行代码。</span><span class="sxs-lookup"><span data-stu-id="87dad-184">This exception is expected and the try/catch block is necessary for code execution to continue.</span></span> <span data-ttu-id="87dad-185">当完成执行触发器代码时，将引发另一个异常。</span><span class="sxs-lookup"><span data-stu-id="87dad-185">When the trigger code finishes execution, another exception is raised</span></span>  
  
```  
Msg 3991, Level 16, State 1, Procedure trig_InsertValidator, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate "trig_InsertValidator" has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting.  
The statement has been terminated.  
```  
  
 <span data-ttu-id="87dad-186">此异常也是预期行为，并且执行激发触发器操作的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句前后的 try/catch 块是必需的，以便继续执行。</span><span class="sxs-lookup"><span data-stu-id="87dad-186">This exception is also expected, and a try/catch block around the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that performs the action that fires the trigger is necessary so that execution can continue.</span></span> <span data-ttu-id="87dad-187">尽管引发了两个异常，仍可以回滚事务，并且更改不会提交到表中。</span><span class="sxs-lookup"><span data-stu-id="87dad-187">Despite the two exceptions thrown, the transaction is rolled back and the changes are not committed to the table.</span></span> <span data-ttu-id="87dad-188">CLR 触发器和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 触发器之间的主要区别在于：[!INCLUDE[tsql](../../includes/tsql-md.md)] 触发器可以在回滚事务之后继续执行更多工作。</span><span class="sxs-lookup"><span data-stu-id="87dad-188">A major difference between CLR triggers and [!INCLUDE[tsql](../../includes/tsql-md.md)] triggers is that [!INCLUDE[tsql](../../includes/tsql-md.md)] triggers can continue to perform more work after the transaction is rolled back.</span></span>  
  
### <a name="example"></a><span data-ttu-id="87dad-189">示例</span><span class="sxs-lookup"><span data-stu-id="87dad-189">Example</span></span>  
 <span data-ttu-id="87dad-190">下面的触发器对表执行简单的 INSERT 语句验证。</span><span class="sxs-lookup"><span data-stu-id="87dad-190">The following trigger performs simple validation of INSERT statements on a table.</span></span> <span data-ttu-id="87dad-191">如果插入的整数值等于 1，则回滚事务，并且该值不会插入到表中。</span><span class="sxs-lookup"><span data-stu-id="87dad-191">If the inserted integer value is equal to one, the transaction is rolled back and the value is not inserted into the table.</span></span> <span data-ttu-id="87dad-192">所有其他整数值将插入到表中。</span><span class="sxs-lookup"><span data-stu-id="87dad-192">All other integer values are inserted into the table.</span></span> <span data-ttu-id="87dad-193">请注意，`Transaction.Rollback` 方法前后存在 try/catch 块。</span><span class="sxs-lookup"><span data-stu-id="87dad-193">Note the try/catch block around the `Transaction.Rollback` method.</span></span> <span data-ttu-id="87dad-194">[!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本创建测试表、程序集和托管存储过程。</span><span class="sxs-lookup"><span data-stu-id="87dad-194">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script creates a test table, assembly, and managed stored procedure.</span></span> <span data-ttu-id="87dad-195">请注意，两个 INSERT 语句包装在 try/catch 块中，这样可以捕获在完成执行触发器时所引发的异常。</span><span class="sxs-lookup"><span data-stu-id="87dad-195">Note that the two INSERT statements are wrapped in a try/catch block so that the exception thrown when the trigger finishes execution is caught.</span></span>  
  
 <span data-ttu-id="87dad-196">C#</span><span class="sxs-lookup"><span data-stu-id="87dad-196">C#</span></span>  
  
```  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class Triggers  
{  
    // Enter existing table or view for the target and uncomment the attribute line  
    // [Microsoft.SqlServer.Server.SqlTrigger (Name="trig_InsertValidator", Target="Table1", Event="FOR INSERT")]  
    public static void trig_InsertValidator()  
    {  
        using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
        {  
            SqlCommand command;  
            SqlDataReader reader;  
            int value;  
  
            // Open the connection.  
            connection.Open();  
  
            // Get the inserted value.  
            command = new SqlCommand(@"SELECT * FROM INSERTED", connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            value = (int)reader[0];  
            reader.Close();  
  
            // Rollback the transaction if a value of 1 was inserted.  
            if (1 == value)  
            {  
                try  
                {  
                    // Get the current transaction and roll it back.  
                    Transaction trans = Transaction.Current;  
                    trans.Rollback();                      
                }  
                catch (SqlException ex)  
                {  
                    // Catch the expected exception.                      
                }  
            }  
            else  
            {  
                // Perform other actions here.  
            }  
  
            // Close the connection.  
            connection.Close();              
        }  
    }  
}  
```  
  
 <span data-ttu-id="87dad-197">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87dad-197">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class Triggers  
' Enter existing table or view for the target and uncomment the attribute line  
' <Microsoft.SqlServer.Server.SqlTrigger(Name:="trig_InsertValidator", Target:="Table1", Event:="FOR INSERT")> _  
Public Shared Sub  trig_InsertValidator ()  
    Using connection As New SqlConnection("context connection=true")  
  
        Dim command As SqlCommand  
        Dim reader As SqlDataReader  
        Dim value As Integer  
  
        ' Open the connection.  
        connection.Open()  
  
        ' Get the inserted value.  
        command = New SqlCommand("SELECT * FROM INSERTED", connection)  
        reader = command.ExecuteReader()  
        reader.Read()  
        value = CType(reader(0), Integer)  
        reader.Close()  
  
        ' Rollback the transaction if a value of 1 was inserted.  
        If value = 1 Then  
  
            Try  
                ' Get the current transaction and roll it back.  
                Dim trans As Transaction  
                trans = Transaction.Current  
                trans.Rollback()  
  
            Catch ex As SqlException  
  
                ' Catch the exception.                      
            End Try  
        Else  
  
            ' Perform other actions here.  
        End If  
  
        ' Close the connection.  
        connection.Close()  
    End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="87dad-198">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87dad-198">Transact-SQL</span></span>  
  
```  
-- Create the test table, assembly, and trigger.  
CREATE TABLE Table1(c1 int);  
go  
  
CREATE ASSEMBLY ValidationTriggers from 'E:\programming\ ValidationTriggers.dll';  
go  
  
CREATE TRIGGER trig_InsertValidator  
ON Table1  
FOR INSERT  
AS EXTERNAL NAME ValidationTriggers.Triggers.trig_InsertValidator;  
go  
  
-- Use a Try/Catch block to catch the expected exception  
BEGIN TRY  
   INSERT INTO Table1 VALUES(42)  
   INSERT INTO Table1 VALUES(1)  
END TRY  
BEGIN CATCH  
  SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
END CATCH;  
  
-- Clean up.  
DROP TRIGGER trig_InsertValidator;  
DROP ASSEMBLY ValidationTriggers;  
DROP TABLE Table1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="87dad-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87dad-199">See Also</span></span>  
 <span data-ttu-id="87dad-200">[CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87dad-200">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="87dad-201">[DML 触发器](../../relational-databases/triggers/dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="87dad-201">[DML Triggers](../../relational-databases/triggers/dml-triggers.md) </span></span>  
 <span data-ttu-id="87dad-202">[DDL 触发器](../../relational-databases/triggers/ddl-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="87dad-202">[DDL Triggers](../../relational-databases/triggers/ddl-triggers.md) </span></span>  
 <span data-ttu-id="87dad-203">[TRY...CATCH (Transact-SQL)](/sql/t-sql/language-elements/try-catch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87dad-203">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span></span>  
 <span data-ttu-id="87dad-204">[通过公共语言运行时 &#40;CLR&#41; 集成生成数据库对象](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md) </span><span class="sxs-lookup"><span data-stu-id="87dad-204">[Building Database Objects with Common Language Runtime &#40;CLR&#41; Integration](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md) </span></span>  
 [<span data-ttu-id="87dad-205">EVENTDATA (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="87dad-205">EVENTDATA &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
