---
title: 创建、更改和删除规则 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- rules [SMO]
ms.assetid: 16981459-524e-4b39-a899-4370eaf763cc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7742a9cb718bdde4f268d5226c45eba475f44ddd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588955"
---
# <a name="creating-altering-and-removing-rules"></a><span data-ttu-id="8bba0-102">创建、更改和删除规则</span><span class="sxs-lookup"><span data-stu-id="8bba0-102">Creating, Altering, and Removing Rules</span></span>
  <span data-ttu-id="8bba0-103">在 SMO 中，规则由 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="8bba0-103">In SMO, rules are represented by the <xref:Microsoft.SqlServer.Management.Smo.Rule> object.</span></span> <span data-ttu-id="8bba0-104">规则是由 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 属性进行定义的，该属性是包含使用运算符或谓词（如，IN、LIKE 或 BETWEEN）的条件表达式的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="8bba0-104">The rule is defined by the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property, which is a text string that contains a condition expression that uses operators or predicates, such as IN, LIKE, or BETWEEN.</span></span> <span data-ttu-id="8bba0-105">规则不能引用列或其他数据库对象。</span><span class="sxs-lookup"><span data-stu-id="8bba0-105">A rule cannot reference columns or other database objects.</span></span> <span data-ttu-id="8bba0-106">可以包括不引用数据库对象的内置函数。</span><span class="sxs-lookup"><span data-stu-id="8bba0-106">Built-in functions that do not reference database objects can be included.</span></span>  
  
 <span data-ttu-id="8bba0-107"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 属性中的定义必须包含引用输入的数据值的变量。</span><span class="sxs-lookup"><span data-stu-id="8bba0-107">The definition in the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property must contain a variable that refers to the data value entered.</span></span> <span data-ttu-id="8bba0-108">创建规则时，可以使用任何名称或符号表示值，但第一个字符必须是 \@ 符号。</span><span class="sxs-lookup"><span data-stu-id="8bba0-108">Any name or symbol can be used to represent the value when creating the rule, but the first character must be the \@ symbol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bba0-109">示例</span><span class="sxs-lookup"><span data-stu-id="8bba0-109">Example</span></span>  
 <span data-ttu-id="8bba0-110">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="8bba0-110">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="8bba0-111">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="8bba0-111">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-basic"></a><span data-ttu-id="8bba0-112">在 Visual Basic 中创建、更改和删除规则</span><span class="sxs-lookup"><span data-stu-id="8bba0-112">Creating, Altering, and Removing a Rule in Visual Basic</span></span>  
 <span data-ttu-id="8bba0-113">此代码示例说明如何创建规则，将其附加到列，修改 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象的属性，从列中分离规则，以及删除规则。</span><span class="sxs-lookup"><span data-stu-id="8bba0-113">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="8bba0-114">使用完整的程序集路径指定 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象的 `Dim` 语句，以便在使用 System.Data 程序集中的 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象时避免含糊歧义。</span><span class="sxs-lookup"><span data-stu-id="8bba0-114">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBRules1](SMO How to#SMO_VBRules1)]  -->  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-c"></a><span data-ttu-id="8bba0-115">在 Visual C# 中创建、更改和删除规则</span><span class="sxs-lookup"><span data-stu-id="8bba0-115">Creating, Altering, and Removing a Rule in Visual C#</span></span>  
 <span data-ttu-id="8bba0-116">此代码示例说明如何创建规则，将其附加到列，修改 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象的属性，从列中分离规则，以及删除规则。</span><span class="sxs-lookup"><span data-stu-id="8bba0-116">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="8bba0-117">使用完整的程序集路径指定 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象的 `Dim` 语句，以便在使用 System.Data 程序集中的 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象时避免含糊歧义。</span><span class="sxs-lookup"><span data-stu-id="8bba0-117">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
            //Note that the full namespace must be given for the Rule type to differentiate it from other Rule types.   
            Microsoft.SqlServer.Management.Smo.Rule ru;  
            ru = new Rule(db, "TestRule", "Production");  
            //Set the TextHeader and TextBody properties to define the rule.   
            ru.TextHeader = "CREATE RULE [Production].[TestRule] AS";  
            ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())";  
            //Create the rule on the instance of SQL Server.   
            ru.Create();  
            //Bind the rule to a column in the Product table by supplying the table, schema, and   
            //column as arguments in the BindToColumn method.   
            ru.BindToColumn("Product", "SellEndDate", "Production");  
            //Unbind from the column before removing the rule from the database.   
            ru.UnbindFromColumn("Product", "SellEndDate", "Production");  
            ru.Drop();  
  
        }  
```  
  
## <a name="creating-altering-and-removing-a-rule-in-powershell"></a><span data-ttu-id="8bba0-118">在 PowerShell 中创建、更改和删除规则</span><span class="sxs-lookup"><span data-stu-id="8bba0-118">Creating, Altering, and Removing a Rule in PowerShell</span></span>  
 <span data-ttu-id="8bba0-119">此代码示例说明如何创建规则，将其附加到列，修改 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象的属性，从列中分离规则，以及删除规则。</span><span class="sxs-lookup"><span data-stu-id="8bba0-119">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="8bba0-120">使用完整的程序集路径指定 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象的 `Dim` 语句，以便在使用 System.Data 程序集中的 <xref:Microsoft.SqlServer.Management.Smo.Rule> 对象时避免含糊歧义。</span><span class="sxs-lookup"><span data-stu-id="8bba0-120">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a Rule object variable by supplying the parent database, name and schema in the constructor.
$ru = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Rule -argumentlist $db, "TestRule", "Production"  
  
#Set the TextHeader and TextBody properties to define the rule.
$ru.TextHeader = "CREATE RULE [Production].[TestRule] AS"  
$ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())"  
  
#Create the rule on the instance of SQL Server.
$ru.Create()  
  
# Bind the rule to a column in the Product table by supplying the table, schema, and column as arguments in the BindToColumn method.
$ru.BindToColumn("Product", "SellEndDate", "Production")  
  
#Unbind from the column before removing the rule from the database.
$ru.UnbindFromColumn("Product", "SellEndDate", "Production")  
$ru.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bba0-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bba0-121">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Rule>  
