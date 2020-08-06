---
title: 创建、更改和删除默认值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: 747f7ff60122c5265cd68060063946a3e22d0301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692827"
---
# <a name="creating-altering-and-removing-defaults"></a><span data-ttu-id="0fe6a-102">创建、更改和删除默认值</span><span class="sxs-lookup"><span data-stu-id="0fe6a-102">Creating, Altering, and Removing Defaults</span></span>
  <span data-ttu-id="0fe6a-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理对象 (SMO) 中，默认约束由 <xref:Microsoft.SqlServer.Management.Smo.Default> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), the default constraint is represented by the <xref:Microsoft.SqlServer.Management.Smo.Default> object.</span></span>  
  
 <span data-ttu-id="0fe6a-104"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Default> 属性用于设置要插入的值。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-104">The <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Default> object is used to set the value to be inserted.</span></span> <span data-ttu-id="0fe6a-105">此值可以是常量，也可以是返回常量值的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，例如 GETDATE()。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-105">This can be a constant or a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement that returns a constant value, such as GETDATE().</span></span> <span data-ttu-id="0fe6a-106">不能通过使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 方法修改 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-106">The <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property cannot be modified by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="0fe6a-107">相反，必须删除并重新创建 <xref:Microsoft.SqlServer.Management.Smo.Default> 对象。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-107">Instead, the <xref:Microsoft.SqlServer.Management.Smo.Default> object must be dropped and re-created.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fe6a-108">示例</span><span class="sxs-lookup"><span data-stu-id="0fe6a-108">Example</span></span>  
 <span data-ttu-id="0fe6a-109">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-109">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="0fe6a-110">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-110">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a><span data-ttu-id="0fe6a-111">在 Visual Basic 中创建、更改和删除默认值</span><span class="sxs-lookup"><span data-stu-id="0fe6a-111">Creating, Altering, and Removing a Default in Visual Basic</span></span>  
 <span data-ttu-id="0fe6a-112">此代码示例演示如何创建一个简单文本形式的默认值和另一个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句形式的默认值。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-112">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="0fe6a-113">必须使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法将默认值附加到列，然后使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法将其分离。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-113">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaults1](SMO How to#SMO_VBDefaults1)]  -->  
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a><span data-ttu-id="0fe6a-114">在 Visual C# 中创建、更改和删除默认值</span><span class="sxs-lookup"><span data-stu-id="0fe6a-114">Creating, Altering, and Removing a Default in Visual C#</span></span>  
 <span data-ttu-id="0fe6a-115">此代码示例演示如何创建一个简单文本形式的默认值和另一个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句形式的默认值。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-115">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="0fe6a-116">必须使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法将默认值附加到列，然后使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法将其分离。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-116">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
```csharp
{
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a><span data-ttu-id="0fe6a-117">在 PowerShell 中创建、更改和删除默认值</span><span class="sxs-lookup"><span data-stu-id="0fe6a-117">Creating, Altering, and Removing a Default in PowerShell</span></span>  
 <span data-ttu-id="0fe6a-118">此代码示例演示如何创建一个简单文本形式的默认值和另一个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句形式的默认值。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-118">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="0fe6a-119">必须使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法将默认值附加到列，然后使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法将其分离。</span><span class="sxs-lookup"><span data-stu-id="0fe6a-119">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fe6a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fe6a-120">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
