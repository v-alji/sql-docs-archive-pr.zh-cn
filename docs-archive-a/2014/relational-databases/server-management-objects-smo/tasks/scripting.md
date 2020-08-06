---
title: 脚本 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- dependencies [SMO]
- scripts [SMO]
ms.assetid: 13a35511-3987-426b-a3b7-3b2e83900dc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf46798597de021976cefa943a17500e773f9274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689820"
---
# <a name="scripting"></a><span data-ttu-id="00fc4-102">脚本编写</span><span class="sxs-lookup"><span data-stu-id="00fc4-102">Scripting</span></span>
  <span data-ttu-id="00fc4-103">SMO 中的脚本撰写由 <xref:Microsoft.SqlServer.Management.Smo.Scripter> 对象及其子对象控制，或由各个对象的 `Script` 方法控制。</span><span class="sxs-lookup"><span data-stu-id="00fc4-103">Scripting in SMO is controlled by the <xref:Microsoft.SqlServer.Management.Smo.Scripter> object and its child objects, or the `Script` method on individual objects.</span></span> <span data-ttu-id="00fc4-104"><xref:Microsoft.SqlServer.Management.Smo.Scripter>对象控制对实例上对象的依赖关系的映射 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="00fc4-104">The <xref:Microsoft.SqlServer.Management.Smo.Scripter> object controls the mapping out of dependency relationships for objects on an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="00fc4-105">使用 <xref:Microsoft.SqlServer.Management.Smo.Scripter> 对象及其子对象进行的高级脚本撰写是一个由三个阶段组成的过程：</span><span class="sxs-lookup"><span data-stu-id="00fc4-105">Advanced scripting by using the <xref:Microsoft.SqlServer.Management.Smo.Scripter> object and its child objects is a three phase process:</span></span>  
  
1.  <span data-ttu-id="00fc4-106">发现</span><span class="sxs-lookup"><span data-stu-id="00fc4-106">Discovery</span></span>  
  
2.  <span data-ttu-id="00fc4-107">生成列表</span><span class="sxs-lookup"><span data-stu-id="00fc4-107">List generation</span></span>  
  
3.  <span data-ttu-id="00fc4-108">脚本生成</span><span class="sxs-lookup"><span data-stu-id="00fc4-108">Script generation</span></span>  
  
 <span data-ttu-id="00fc4-109">发现阶段使用 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> 对象。</span><span class="sxs-lookup"><span data-stu-id="00fc4-109">The discovery phase uses the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> object.</span></span> <span data-ttu-id="00fc4-110">如果给定对象的 URN 列表，则 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> 方法将为该 URN 列表中的对象返回 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> 对象。</span><span class="sxs-lookup"><span data-stu-id="00fc4-110">Given an URN list of objects, the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> object returns a <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> object for the objects in the URN list.</span></span> <span data-ttu-id="00fc4-111">布尔*fParents*参数用于选择是要发现指定对象的父对象还是子对象。</span><span class="sxs-lookup"><span data-stu-id="00fc4-111">The Boolean *fParents* parameter is used to select whether the parents or the children of the specified object are to be discovered.</span></span> <span data-ttu-id="00fc4-112">在此阶段可以修改依赖关系树。</span><span class="sxs-lookup"><span data-stu-id="00fc4-112">The dependency tree can be modified at this stage.</span></span>  
  
 <span data-ttu-id="00fc4-113">在生成列表阶段，会传入该树并返回生成的列表。</span><span class="sxs-lookup"><span data-stu-id="00fc4-113">In the list generation phase, the tree is passed in and the resulting list is returned.</span></span> <span data-ttu-id="00fc4-114">此对象列表是按脚本撰写顺序排列的，可以对其进行操作。</span><span class="sxs-lookup"><span data-stu-id="00fc4-114">This object list is in scripting order and can be manipulated.</span></span>  
  
 <span data-ttu-id="00fc4-115">生成列表阶段使用 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A> 方法返回 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>。</span><span class="sxs-lookup"><span data-stu-id="00fc4-115">The list generation phases use the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A> method to return a <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>.</span></span> <span data-ttu-id="00fc4-116">在此阶段可以修改 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>。</span><span class="sxs-lookup"><span data-stu-id="00fc4-116">The <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> can be modified at this stage.</span></span>  
  
 <span data-ttu-id="00fc4-117">第三阶段也是最后一个阶段，在此阶段中，使用指定的列表和脚本撰写选项生成脚本。</span><span class="sxs-lookup"><span data-stu-id="00fc4-117">In the third and final phase, a script is generated with the specified list and scripting options.</span></span> <span data-ttu-id="00fc4-118">结果以 <xref:System.Collections.Specialized.StringCollection> 系统对象的形式返回。</span><span class="sxs-lookup"><span data-stu-id="00fc4-118">The result is returned as a <xref:System.Collections.Specialized.StringCollection> system object.</span></span> <span data-ttu-id="00fc4-119">在此阶段中，接下来会从 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> 对象和属性（如 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> 和 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A>）的项集合中提取依赖对象的名称。</span><span class="sxs-lookup"><span data-stu-id="00fc4-119">In this phase the dependent object names are then extracted from the Items collection of the <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> object and properties such as <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> and <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00fc4-120">示例</span><span class="sxs-lookup"><span data-stu-id="00fc4-120">Example</span></span>  
 <span data-ttu-id="00fc4-121">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="00fc4-121">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="00fc4-122">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="00fc4-122">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
 <span data-ttu-id="00fc4-123">此代码示例需要对 System.Collections.Specialized 命名空间使用 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="00fc4-123">This code example requires an `Imports` statement for the System.Collections.Specialized namespace.</span></span> <span data-ttu-id="00fc4-124">请将此语句与其他 Imports 语句一同插入在应用程序中的任何声明代码前。</span><span class="sxs-lookup"><span data-stu-id="00fc4-124">Insert this with the other Imports statements, before any declarations in the application.</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
Imports System.Collections.Specialized  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-basic"></a><span data-ttu-id="00fc4-125">在 Visual Basic 中撰写数据库依赖项的脚本</span><span class="sxs-lookup"><span data-stu-id="00fc4-125">Scripting Out the Dependencies for a Database in Visual Basic</span></span>  
 <span data-ttu-id="00fc4-126">此代码示例说明如何发现依赖项并循环访问列表以显示结果。</span><span class="sxs-lookup"><span data-stu-id="00fc4-126">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
  
Public Class A  
   Public Shared Sub Main()  
      ' database name  
      Dim dbName As [String] = "AdventureWorksLT2012"   ' database name  
  
      ' Connect to the local, default instance of SQL Server.   
      Dim srv As New Server()  
  
      ' Reference the database.    
      Dim db As Database = srv.Databases(dbName)  
  
      ' Define a Scripter object and set the required scripting options.   
      Dim scrp As New Scripter(srv)  
      scrp.Options.ScriptDrops = False  
      scrp.Options.WithDependencies = True  
      scrp.Options.Indexes = True   ' To include indexes  
      scrp.Options.DriAllConstraints = True   ' to include referential constraints in the script  
  
      ' Iterate through the tables in database and script each one. Display the script.  
      For Each tb As Table In db.Tables  
         ' check if the table is not a system table  
         If tb.IsSystemObject = False Then  
            Console.WriteLine("-- Scripting for table " + tb.Name)  
  
            ' Generating script for table tb  
            Dim sc As System.Collections.Specialized.StringCollection = scrp.Script(New Urn() {tb.Urn})  
            For Each st As String In sc  
               Console.WriteLine(st)  
            Next  
            Console.WriteLine("--")  
         End If  
      Next  
   End Sub  
End Class  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-c"></a><span data-ttu-id="00fc4-127">在 Visual C# 中撰写数据库依赖项的脚本</span><span class="sxs-lookup"><span data-stu-id="00fc4-127">Scripting Out the Dependencies for a Database in Visual C#</span></span>  
 <span data-ttu-id="00fc4-128">此代码示例说明如何发现依赖项并循环访问列表以显示结果。</span><span class="sxs-lookup"><span data-stu-id="00fc4-128">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
  
public class A {  
   public static void Main() {   
      String dbName = "AdventureWorksLT2012"; // database name  
  
      // Connect to the local, default instance of SQL Server.   
      Server srv = new Server();  
  
      // Reference the database.    
      Database db = srv.Databases[dbName];  
  
      // Define a Scripter object and set the required scripting options.   
      Scripter scrp = new Scripter(srv);  
      scrp.Options.ScriptDrops = false;  
      scrp.Options.WithDependencies = true;  
      scrp.Options.Indexes = true;   // To include indexes  
      scrp.Options.DriAllConstraints = true;   // to include referential constraints in the script  
  
      // Iterate through the tables in database and script each one. Display the script.     
      foreach (Table tb in db.Tables) {   
         // check if the table is not a system table  
         if (tb.IsSystemObject == false) {  
            Console.WriteLine("-- Scripting for table " + tb.Name);  
  
            // Generating script for table tb  
            System.Collections.Specialized.StringCollection sc = scrp.Script(new Urn[]{tb.Urn});  
            foreach (string st in sc) {  
               Console.WriteLine(st);  
            }  
            Console.WriteLine("--");  
         }  
      }   
   }  
}  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-powershell"></a><span data-ttu-id="00fc4-129">在 PowerShell 中撰写数据库依赖项的脚本</span><span class="sxs-lookup"><span data-stu-id="00fc4-129">Scripting Out the Dependencies for a Database in PowerShell</span></span>  
 <span data-ttu-id="00fc4-130">此代码示例说明如何发现依赖项并循环访问列表以显示结果。</span><span class="sxs-lookup"><span data-stu-id="00fc4-130">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
# Create a Scripter object and set the required scripting options.  
$scrp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Scripter -ArgumentList (Get-Item .)  
$scrp.Options.ScriptDrops = $false  
$scrp.Options.WithDependencies = $true  
$scrp.Options.IncludeIfNotExists = $true  
  
# Set the path context to the tables in AdventureWorks2012.  
CD Databases\AdventureWorks2012\Tables  
  
foreach ($Item in Get-ChildItem)  
 {    
 $scrp.Script($Item)  
 }  
```  
