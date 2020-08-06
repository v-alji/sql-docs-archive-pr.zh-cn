---
title: 使用同义词 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e8416dc3daea3b173fae92e5454a8a65c399e53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591208"
---
# <a name="using-synonyms"></a><span data-ttu-id="8d5b6-102">使用同义词</span><span class="sxs-lookup"><span data-stu-id="8d5b6-102">Using Synonyms</span></span>
  <span data-ttu-id="8d5b6-103">同义词是架构范围内的对象的另一名称。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-103">A synonym is an alternative name for a schema-scoped object.</span></span> <span data-ttu-id="8d5b6-104">在 SMO 中，同义词由 <xref:Microsoft.SqlServer.Management.Smo.Synonym> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-104">In SMO, synonyms are represented by the <xref:Microsoft.SqlServer.Management.Smo.Synonym> object.</span></span> <span data-ttu-id="8d5b6-105"><xref:Microsoft.SqlServer.Management.Smo.Synonym> 对象是 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象的子对象。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-105">The <xref:Microsoft.SqlServer.Management.Smo.Synonym> object is a child of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span> <span data-ttu-id="8d5b6-106">这意味着同义词仅在定义它们的数据库范围内有效。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-106">This means that synonyms are valid only within the scope of the database in which they are defined.</span></span> <span data-ttu-id="8d5b6-107">但是，同义词可以引用位于另一个数据库或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]远程实例上的对象。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-107">However, the synonym can refer to objects on another database, or on a remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8d5b6-108">具有另一名称的对象称为基对象。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-108">The object that is given an alternative name is known as the base object.</span></span> <span data-ttu-id="8d5b6-109"><xref:Microsoft.SqlServer.Management.Smo.Synonym> 对象的名称属性即为提供给基对象的另一名称。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-109">The name property of the <xref:Microsoft.SqlServer.Management.Smo.Synonym> object is the alternative name given to the base object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d5b6-110">示例</span><span class="sxs-lookup"><span data-stu-id="8d5b6-110">Example</span></span>  
 <span data-ttu-id="8d5b6-111">对于下面的代码示例，您必须选择编程环境、编程模板和编程语言才能创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-111">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="8d5b6-112">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-112">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-synonym-in-visual-basic"></a><span data-ttu-id="8d5b6-113">在 Visual Basic 中创建同义词</span><span class="sxs-lookup"><span data-stu-id="8d5b6-113">Creating a Synonym in Visual Basic</span></span>  
 <span data-ttu-id="8d5b6-114">代码示例演示了如何为架构范围内的对象创建同义词或备用名称。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-114">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="8d5b6-115">通过使用同义词，客户端应用程序可以使用对基对象的单一引用，而不必使用由多部分组成的名称来引用基对象。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-115">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBSynonyms1](SMO How to#SMO_VBSynonyms1)]  -->  
  
## <a name="creating-a-synonym-in-visual-c"></a><span data-ttu-id="8d5b6-116">在 Visual C# 中创建同义词</span><span class="sxs-lookup"><span data-stu-id="8d5b6-116">Creating a Synonym in Visual C#</span></span>  
 <span data-ttu-id="8d5b6-117">代码示例演示了如何为架构范围内的对象创建同义词或备用名称。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-117">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="8d5b6-118">通过使用同义词，客户端应用程序可以使用对基对象的单一引用，而不必使用由多部分组成的名称来引用基对象。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-118">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a><span data-ttu-id="8d5b6-119">在 PowerShell 中创建同义词</span><span class="sxs-lookup"><span data-stu-id="8d5b6-119">Creating a Synonym in PowerShell</span></span>  
 <span data-ttu-id="8d5b6-120">代码示例演示了如何为架构范围内的对象创建同义词或备用名称。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-120">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="8d5b6-121">通过使用同义词，客户端应用程序可以使用对基对象的单一引用，而不必使用由多部分组成的名称来引用基对象。</span><span class="sxs-lookup"><span data-stu-id="8d5b6-121">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym -ArgumentList $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d5b6-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d5b6-122">See Also</span></span>  
 [<span data-ttu-id="8d5b6-123">CREATE SYNONYM (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8d5b6-123">CREATE SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-synonym-transact-sql)  
