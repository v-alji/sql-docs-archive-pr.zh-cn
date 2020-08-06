---
title: 创建、更改和删除触发器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: stevestein
ms.author: sstein
ms.openlocfilehash: c2cdd1573c488fbe7b2309f656cd6bf42e82a527
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590679"
---
# <a name="creating-altering-and-removing-triggers"></a><span data-ttu-id="4cda6-102">创建、更改和删除触发器</span><span class="sxs-lookup"><span data-stu-id="4cda6-102">Creating, Altering, and Removing Triggers</span></span>
  <span data-ttu-id="4cda6-103">在 SMO 中，触发器由 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="4cda6-103">In SMO, triggers are represented by using the <xref:Microsoft.SqlServer.Management.Smo.Trigger> object.</span></span> <span data-ttu-id="4cda6-104">[!INCLUDE[tsql](../../../includes/tsql-md.md)]触发器对象的属性设置所激发的触发器时运行的代码 <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> 。</span><span class="sxs-lookup"><span data-stu-id="4cda6-104">The [!INCLUDE[tsql](../../../includes/tsql-md.md)] code that runs when the trigger that is fired is set by the <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> property of the Trigger object.</span></span> <span data-ttu-id="4cda6-105">使用 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 对象的其他属性（如 <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> 属性）可以设置触发器的类型。</span><span class="sxs-lookup"><span data-stu-id="4cda6-105">The type of trigger is set by using other properties of the <xref:Microsoft.SqlServer.Management.Smo.Trigger> object, such as the <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> property.</span></span> <span data-ttu-id="4cda6-106">这是一个布尔属性，它指定触发器是否由对父表上的记录所执行的 `UPDATE` 操作激发。</span><span class="sxs-lookup"><span data-stu-id="4cda6-106">This is a Boolean property that specifies whether the trigger is fired by an `UPDATE` of records on the parent table.</span></span>  
  
 <span data-ttu-id="4cda6-107"><xref:Microsoft.SqlServer.Management.Smo.Trigger> 对象表示传统的数据操作语言 (DML) 触发器。</span><span class="sxs-lookup"><span data-stu-id="4cda6-107">The <xref:Microsoft.SqlServer.Management.Smo.Trigger> object represents traditional, data manipulation language (DML) triggers.</span></span> <span data-ttu-id="4cda6-108">在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和更改版本中，也同样支持数据定义语言 (DDL) 触发器。</span><span class="sxs-lookup"><span data-stu-id="4cda6-108">In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and later versions, data definition language (DDL) triggers are also supported.</span></span> <span data-ttu-id="4cda6-109">DDL 触发器由 <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> 对象和 <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="4cda6-109">DDL triggers are represented by the <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> object and the <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cda6-110">示例</span><span class="sxs-lookup"><span data-stu-id="4cda6-110">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a><span data-ttu-id="4cda6-111">在 Visual Basic 中创建、更改和删除触发器</span><span class="sxs-lookup"><span data-stu-id="4cda6-111">Creating, Altering, and Removing a Trigger in Visual Basic</span></span>  
 <span data-ttu-id="4cda6-112">此代码示例演示如何在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库中名为 `Sales` 的现有表上创建并插入更新触发器。</span><span class="sxs-lookup"><span data-stu-id="4cda6-112">This code example shows how to create and insert an update trigger on an existing table, named `Sales`, in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="4cda6-113">当更新表或插入新记录时触发器会发送提醒消息。</span><span class="sxs-lookup"><span data-stu-id="4cda6-113">The trigger sends a reminder message when the table is updated or a new record is inserted.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTriggers1](SMO How to#SMO_VBTriggers1)]  -->  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a><span data-ttu-id="4cda6-114">在 Visual C# 中创建、更改和删除触发器</span><span class="sxs-lookup"><span data-stu-id="4cda6-114">Creating, Altering, and Removing a Trigger in Visual C#</span></span>  
 <span data-ttu-id="4cda6-115">此代码示例演示如何在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库中名为 `Sales` 的现有表上创建并插入更新触发器。</span><span class="sxs-lookup"><span data-stu-id="4cda6-115">This code example shows how to create and insert an update trigger on an existing table, named `Sales`, in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="4cda6-116">当更新表或插入新记录时触发器会发送提醒消息。</span><span class="sxs-lookup"><span data-stu-id="4cda6-116">The trigger sends a reminder message when the table is updated or a new record is inserted.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a><span data-ttu-id="4cda6-117">在 PowerShell 中创建、更改和删除触发器</span><span class="sxs-lookup"><span data-stu-id="4cda6-117">Creating, Altering, and Removing a Trigger in PowerShell</span></span>  
 <span data-ttu-id="4cda6-118">此代码示例演示如何在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库中名为 `Sales` 的现有表上创建并插入更新触发器。</span><span class="sxs-lookup"><span data-stu-id="4cda6-118">This code example shows how to create and insert an update trigger on an existing table, named `Sales`, in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="4cda6-119">当更新表或插入新记录时触发器会发送提醒消息。</span><span class="sxs-lookup"><span data-stu-id="4cda6-119">The trigger sends a reminder message when the table is updated or a new record is inserted.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = Get-Item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger -argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.
$tr.Create()  
  
#Remove the trigger.
$tr.Drop()  
```  
