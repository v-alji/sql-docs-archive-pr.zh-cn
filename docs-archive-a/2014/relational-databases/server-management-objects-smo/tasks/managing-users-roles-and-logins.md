---
title: 管理用户、角色和登录名 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
author: stevestein
ms.author: sstein
ms.openlocfilehash: bb53e7b4a5748e46c7cb147e1cda50652d8b8805
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588948"
---
# <a name="managing-users-roles-and-logins"></a><span data-ttu-id="8bbb1-102">管理用户、角色和登录名</span><span class="sxs-lookup"><span data-stu-id="8bbb1-102">Managing Users, Roles, and Logins</span></span>
  <span data-ttu-id="8bbb1-103">在 SMO 中，登录名由 <xref:Microsoft.SqlServer.Management.Smo.Login> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-103">In SMO, logins are represented by the <xref:Microsoft.SqlServer.Management.Smo.Login> object.</span></span> <span data-ttu-id="8bbb1-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中存在登录名时，可将其添加到服务器角色中。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-104">When the logon exists in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it can be added to a server role.</span></span> <span data-ttu-id="8bbb1-105">服务器角色由 <xref:Microsoft.SqlServer.Management.Smo.ServerRole> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-105">The server role is represented by the <xref:Microsoft.SqlServer.Management.Smo.ServerRole> object.</span></span> <span data-ttu-id="8bbb1-106">数据库角色由 <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> 对象表示，而应用程序角色由 <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-106">The database role is represented by the <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> object and the application role is represented by the <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> object.</span></span>  
  
 <span data-ttu-id="8bbb1-107">与服务器级别关联的特权将作为 <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> 对象的属性列出。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-107">Privileges associated with the server level are listed as properties of the <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> object.</span></span> <span data-ttu-id="8bbb1-108">服务器级别特权可以对各个登录帐户授予、拒绝或从各个登录帐户撤消。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-108">The server level privileges can be granted to, denied to, or revoked from individual logon accounts.</span></span>  
  
 <span data-ttu-id="8bbb1-109">每个 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象都有一个指定数据库中所有用户的 <xref:Microsoft.SqlServer.Management.Smo.UserCollection> 对象。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-109">Every <xref:Microsoft.SqlServer.Management.Smo.Database> object has a <xref:Microsoft.SqlServer.Management.Smo.UserCollection> object that specifies all users in the database.</span></span> <span data-ttu-id="8bbb1-110">每个用户都与一个登录名相关联。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-110">Each user is associated with a logon.</span></span> <span data-ttu-id="8bbb1-111">一个登录名可以与多个数据库中的用户相关联。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-111">One logon can be associated with users in more than one database.</span></span> <span data-ttu-id="8bbb1-112"><xref:Microsoft.SqlServer.Management.Smo.Login> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 方法可用于列出与登录名关联的每个数据库中的所有用户。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-112">The <xref:Microsoft.SqlServer.Management.Smo.Login> object's <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method can be used to list all users in every database that is associated with the logon.</span></span> <span data-ttu-id="8bbb1-113">另外，<xref:Microsoft.SqlServer.Management.Smo.User> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Login> 属性可指定与用户关联的登录名。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-113">Alternatively, the <xref:Microsoft.SqlServer.Management.Smo.User> object's <xref:Microsoft.SqlServer.Management.Smo.Login> property specifies the logon that is associated with the user.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="8bbb1-114">数据库还具有指定一组数据库级别特权的角色，用户可利用这些特权执行特定任务。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-114">databases also have roles that specify a set of database level privileges that let a user perform specific tasks.</span></span> <span data-ttu-id="8bbb1-115">与服务器角色不同，数据库角色不是固定的。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-115">Unlike server roles, database roles are not fixed.</span></span> <span data-ttu-id="8bbb1-116">可以创建、修改和删除数据库角色。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-116">They can be created, modified, and removed.</span></span> <span data-ttu-id="8bbb1-117">可以将特权和用户分配给数据库角色以进行大容量管理。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-117">Privileges and users can be assigned to a database role for bulk administration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bbb1-118">示例</span><span class="sxs-lookup"><span data-stu-id="8bbb1-118">Example</span></span>  
 <span data-ttu-id="8bbb1-119">对于下面的代码示例，您必须选择编程环境、编程模板和编程语言才能创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-119">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="8bbb1-120">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-120">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="enumerating-logins-and-associated-users-in-visual-basic"></a><span data-ttu-id="8bbb1-121">在 Visual Basic 中枚举登录名和关联的用户</span><span class="sxs-lookup"><span data-stu-id="8bbb1-121">Enumerating Logins and Associated Users in Visual Basic</span></span>  
 <span data-ttu-id="8bbb1-122">数据库中的每个用户都与一个登录名相关联。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-122">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="8bbb1-123">该登录名可以与多个数据库中的用户相关联。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-123">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="8bbb1-124">此代码示例说明如何调用 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Login> 方法以列出与登录名关联的所有数据库用户。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-124">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="8bbb1-125">该示例将在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库中创建一个登录名和用户以确保有要枚举的映射信息。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-125">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLogins1](SMO How to#SMO_VBLogins1)]  -->  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a><span data-ttu-id="8bbb1-126">在 Visual C# 中枚举登录名和关联的用户</span><span class="sxs-lookup"><span data-stu-id="8bbb1-126">Enumerating Logins and Associated Users in Visual C#</span></span>  
 <span data-ttu-id="8bbb1-127">数据库中的每个用户都与一个登录名相关联。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-127">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="8bbb1-128">该登录名可以与多个数据库中的用户相关联。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-128">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="8bbb1-129">此代码示例说明如何调用 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Login> 方法以列出与登录名关联的所有数据库用户。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-129">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="8bbb1-130">该示例将在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库中创建一个登录名和用户以确保有要枚举的映射信息。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-130">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
```csharp
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a><span data-ttu-id="8bbb1-131">在 PowerShell 中枚举登录名和关联的用户</span><span class="sxs-lookup"><span data-stu-id="8bbb1-131">Enumerating Logins and Associated Users in PowerShell</span></span>  
 <span data-ttu-id="8bbb1-132">数据库中的每个用户都与一个登录名相关联。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-132">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="8bbb1-133">该登录名可以与多个数据库中的用户相关联。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-133">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="8bbb1-134">此代码示例说明如何调用 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Login> 方法以列出与登录名关联的所有数据库用户。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-134">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="8bbb1-135">该示例将在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库中创建一个登录名和用户以确保有要枚举的映射信息。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-135">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database object  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a><span data-ttu-id="8bbb1-136">管理角色和用户</span><span class="sxs-lookup"><span data-stu-id="8bbb1-136">Managing Roles and Users</span></span>  
 <span data-ttu-id="8bbb1-137">该示例演示如何管理角色和用户。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-137">This sample demonstrates how to how to manage roles and users.</span></span> <span data-ttu-id="8bbb1-138">第一个示例使用 C#，第二个示例使用 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="8bbb1-138">The first sample uses C#, the second Visual Basic.</span></span> <span data-ttu-id="8bbb1-139">这些示例需要引用以下程序集：</span><span class="sxs-lookup"><span data-stu-id="8bbb1-139">These samples need to reference the following assemblies:</span></span>  
  
-   <span data-ttu-id="8bbb1-140">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="8bbb1-140">Microsoft.SqlServer.Smo.dll</span></span>  
  
-   <span data-ttu-id="8bbb1-141">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="8bbb1-141">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span>  
  
-   <span data-ttu-id="8bbb1-142">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="8bbb1-142">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
-   <span data-ttu-id="8bbb1-143">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="8bbb1-143">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
```csharp
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```  
  
 <span data-ttu-id="8bbb1-144">这是 Visual Basic 版本：</span><span class="sxs-lookup"><span data-stu-id="8bbb1-144">This is the Visual Basic version:</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Smo  
  
Public Class A  
   Public Shared Sub Main()  
      Dim svr As New Server()  
      Dim db As New Database(svr, "TESTDB")  
      db.Create()  
  
      ' Creating Logins  
      Dim login As New Login(svr, "Login1")  
      login.LoginType = LoginType.SqlLogin  
      login.Create("password@1")  
  
      Dim login2 As New Login(svr, "Login2")  
      login2.LoginType = LoginType.SqlLogin  
      login2.Create("password@1")  
  
      ' Creating Users in the database for the logins created  
      Dim user1 As New User(db, "User1")  
      user1.Login = "Login1"  
      user1.Create()  
  
      Dim user2 As New User(db, "User2")  
      user2.Login = "Login2"  
      user2.Create()  
  
      ' Creating database permission Sets  
      Dim dbPermSet As New DatabasePermissionSet(DatabasePermission.AlterAnySchema)  
      dbPermSet.Add(DatabasePermission.AlterAnyUser)  
  
      Dim dbPermSet2 As New DatabasePermissionSet(DatabasePermission.CreateType)  
      dbPermSet2.Add(DatabasePermission.CreateSchema)  
      dbPermSet2.Add(DatabasePermission.CreateTable)  
  
      ' Creating Database roles  
      Dim role1 As New DatabaseRole(db, "Role1")  
      role1.Create()  
  
      Dim role2 As New DatabaseRole(db, "Role2")  
      role2.Create()  
  
      ' Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name)  
      db.Grant(dbPermSet2, role2.Name)  
  
      ' Adding members (Users / Roles) to Role  
      role1.AddMember("User1")  
  
      role2.AddMember("User2")  
  
      ' Role1 becomes a member of Role2  
      role2.AddMember("Role1")  
  
      ' Enumerating through explicit permissions granted to Role1  
      ' enumerates all database permissions for the Grantee  
      Dim dbPermsRole1 As DatabasePermissionInfo() = db.EnumDatabasePermissions("Role1")  
      For Each dbp As DatabasePermissionInfo In dbPermsRole1  
         Console.WriteLine(dbp.Grantee + " has " & dbp.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine(" ")  
   End Sub  
End Class  
```  
