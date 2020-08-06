---
title: 以编程方式枚举可用的包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically enumerate packages [SSIS]
- existence testing [Integration Services]
- enumerating packages [Integration Services]
ms.assetid: 254ec7ee-d3ff-4361-8995-46e9b9c4dc95
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 053f2e598b1cc18e68ee2182092188367ee7f10c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687959"
---
# <a name="enumerating-available-packages-programmatically"></a><span data-ttu-id="5f580-102">以编程方式枚举可用的包</span><span class="sxs-lookup"><span data-stu-id="5f580-102">Enumerating Available Packages Programmatically</span></span>
  <span data-ttu-id="5f580-103">以编程方式使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包时，您可能希望确定个别包或文件夹是否存在，或枚举可用于加载和执行的已保存的包。</span><span class="sxs-lookup"><span data-stu-id="5f580-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine whether an individual package or folder exists, or to enumerate the saved packages that are available to load and execute.</span></span> <span data-ttu-id="5f580-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空间的 <xref:Microsoft.SqlServer.Dts.Runtime> 类提供了多种满足这些要求的方法。</span><span class="sxs-lookup"><span data-stu-id="5f580-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>  
  
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a><span data-ttu-id="5f580-105">确定包或文件夹是否存在</span><span class="sxs-lookup"><span data-stu-id="5f580-105">Determining Whether a Package or Folder Exists</span></span>  
 <span data-ttu-id="5f580-106">若要以编程方式确定已保存的包是否存在，请先调用以下方法之一，然后再尝试加载和运行：</span><span class="sxs-lookup"><span data-stu-id="5f580-106">To determine programmatically whether a saved package exists, call one of the following methods before attempting to load and run it:</span></span>  
  
|<span data-ttu-id="5f580-107">存储位置</span><span class="sxs-lookup"><span data-stu-id="5f580-107">Storage Location</span></span>|<span data-ttu-id="5f580-108">调用的方法</span><span class="sxs-lookup"><span data-stu-id="5f580-108">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="5f580-109">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="5f580-109">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 <span data-ttu-id="5f580-110">若要以编程方式确定文件夹是否存在，请先调用以下方法之一，然后再尝试列出在其中存储的包：</span><span class="sxs-lookup"><span data-stu-id="5f580-110">To determine programmatically whether a folder exists before attempting to list the packages stored in it, call one of the following methods:</span></span>  
  
|<span data-ttu-id="5f580-111">存储位置</span><span class="sxs-lookup"><span data-stu-id="5f580-111">Storage Location</span></span>|<span data-ttu-id="5f580-112">调用的方法</span><span class="sxs-lookup"><span data-stu-id="5f580-112">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="5f580-113">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="5f580-113">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  
 [<span data-ttu-id="5f580-114">返回页首</span><span class="sxs-lookup"><span data-stu-id="5f580-114">Back to top</span></span>](#top)  
  
##  <a name="enumerating-available-packages"></a><a name="listing"></a> <span data-ttu-id="5f580-115">枚举可用的包</span><span class="sxs-lookup"><span data-stu-id="5f580-115">Enumerating Available Packages</span></span>  
 <span data-ttu-id="5f580-116">若要以编程方式获取已保存的包的列表，请调用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="5f580-116">To obtain a list of saved packages programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="5f580-117">存储位置</span><span class="sxs-lookup"><span data-stu-id="5f580-117">Storage Location</span></span>|<span data-ttu-id="5f580-118">调用的方法</span><span class="sxs-lookup"><span data-stu-id="5f580-118">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="5f580-119">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="5f580-119">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A>|  
  
 <span data-ttu-id="5f580-120">下面的示例是控制台应用程序，演示了这些方法的用法。</span><span class="sxs-lookup"><span data-stu-id="5f580-120">The following samples are console applications that demonstrate the use of these methods.</span></span>  
  
###  <a name="example-ssis-package-store"></a><a name="listing_store"></a> <span data-ttu-id="5f580-121">示例（SSIS 包存储区）</span><span class="sxs-lookup"><span data-stu-id="5f580-121">Example (SSIS Package Store)</span></span>  
 <span data-ttu-id="5f580-122">使用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A> 方法列出存储在 SSIS 包存储区中的包。</span><span class="sxs-lookup"><span data-stu-id="5f580-122">Use the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A> method to list packages stored in the SSIS Package Store.</span></span> <span data-ttu-id="5f580-123">SSIS 包存储区管理的默认存储位置为“文件系统”和 MSDB。</span><span class="sxs-lookup"><span data-stu-id="5f580-123">The default storage locations that are managed by the SSIS Package store are File System and MSDB.</span></span> <span data-ttu-id="5f580-124">可以在这些位置创建其他逻辑文件夹。</span><span class="sxs-lookup"><span data-stu-id="5f580-124">You can create additional logical folders within these locations.</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim sqlFolder As String  
    Dim sqlServer As String  
  
    Dim ssisApplication As Application  
    Dim sqlPackages As PackageInfos  
    Dim sqlPackage As PackageInfo  
  
    sqlServer = "."  
  
    ssisApplication = New Application()  
  
    ' Get packages stored in MSDB.  
    sqlFolder = "MSDB"  
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)  
    If sqlPackages.Count > 0 Then  
      Console.WriteLine("Packages stored in MSDB:")  
      For Each sqlPackage In sqlPackages  
        Console.WriteLine(sqlPackage.Name)  
      Next  
      Console.WriteLine()  
    End If  
  
    ' Get packages stored in the File System.  
    sqlFolder = "File System"  
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)  
    If sqlPackages.Count > 0 Then  
      Console.WriteLine("Packages stored in the File System:")  
      For Each sqlPackage In sqlPackages  
        Console.WriteLine(sqlPackage.Name)  
      Next  
    End If  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace EnumeratePackagesSSIS_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
  
      string sqlFolder;  
      string sqlServer;  
  
      Application ssisApplication;  
      PackageInfos sqlPackages;  
  
      sqlServer = ".";  
  
      ssisApplication = new Application();  
  
      // Get packages stored in MSDB.  
      sqlFolder = "MSDB";  
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);  
      if (sqlPackages.Count > 0)  
      {  
        Console.WriteLine("Packages stored in MSDB:");  
        foreach (PackageInfo sqlPackage in sqlPackages)  
        {  
          Console.WriteLine(sqlPackage.Name);  
        }  
        Console.WriteLine();  
      }  
  
      // Get packages stored in the File System.  
      sqlFolder = "File System";  
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);  
      if (sqlPackages.Count > 0)  
      {  
        Console.WriteLine("Packages stored in the File System:");  
        foreach (PackageInfo sqlPackage in sqlPackages)  
        {  
          Console.WriteLine(sqlPackage.Name);  
        }  
      }  
  
      Console.Read();  
  
    }  
  
  }  
  
}  
```  
  
 [<span data-ttu-id="5f580-125">返回页首</span><span class="sxs-lookup"><span data-stu-id="5f580-125">Back to top</span></span>](#top)  
  
###  <a name="example-sql-server"></a><a name="listing_sql"></a> <span data-ttu-id="5f580-126">示例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5f580-126">Example (SQL Server)</span></span>  
 <span data-ttu-id="5f580-127">使用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A> 方法列出在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 实例中存储的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="5f580-127">Use the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A> method to list [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that are stored in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim sqlFolder As String  
    Dim sqlServer As String  
    Dim sqlUser As String  
    Dim sqlPassword As String  
  
    Dim ssisApplication As Application  
    Dim sqlPackages As PackageInfos  
    Dim sqlPackage As PackageInfo  
  
    sqlFolder = String.Empty  
    sqlServer = "(local)"  
    sqlUser = String.Empty  
    sqlPassword = String.Empty  
  
    ssisApplication = New Application()  
  
    sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword)  
  
    For Each sqlPackage In sqlPackages  
      Console.WriteLine(sqlPackage.Name)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace EnumeratePackagesSql_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
  
      string sqlFolder;  
      string sqlServer;  
      string sqlUser;  
      string sqlPassword;  
  
      Application ssisApplication;  
      PackageInfos sqlPackages;  
  
      sqlFolder = String.Empty;  
      sqlServer = "(local)";  
      sqlUser = String.Empty;  
      sqlPassword = String.Empty;  
  
      ssisApplication = new Application();  
  
      sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword);  
  
      foreach (PackageInfo sqlPackage in sqlPackages)  
      {  
        Console.WriteLine(sqlPackage.Name);  
      }  
  
      Console.Read();  
  
    }  
  }  
}  
```  
  
 [<span data-ttu-id="5f580-128">返回页首</span><span class="sxs-lookup"><span data-stu-id="5f580-128">Back to top</span></span>](#top)  
  
<span data-ttu-id="5f580-129">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="5f580-129">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5f580-130">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="5f580-130">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5f580-131">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="5f580-131">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5f580-132">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="5f580-132">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f580-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f580-133">See Also</span></span>  
 [<span data-ttu-id="5f580-134">包管理（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="5f580-134">Package Management &#40;SSIS Service&#41;</span></span>](../service/package-management-ssis-service.md)  
  
  
