---
title: 在自定义程序集中断言权限 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cba3c0b74712b6b4d0f6b5c58925cfd562f0df77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576534"
---
# <a name="asserting-permissions-in-custom-assemblies"></a><span data-ttu-id="6868d-102">在自定义程序集中断言权限</span><span class="sxs-lookup"><span data-stu-id="6868d-102">Asserting Permissions in Custom Assemblies</span></span>
  <span data-ttu-id="6868d-103">默认情况下，自定义程序集代码以受限的 Execution 权限集运行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6868d-103">By default, custom assembly code runs with the limited **Execution** permission set.</span></span> <span data-ttu-id="6868d-104">在某些情况下，您可能想要实现对您的安全系统内的受保护资源（例如文件或注册表）进行安全调用的自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="6868d-104">In some cases, you may wish to implement a custom assembly that makes secured calls to protected resources within your security system (such as a file or the registry).</span></span> <span data-ttu-id="6868d-105">为此，您必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6868d-105">In order to accomplish this, you must do the following:</span></span>  
  
1.  <span data-ttu-id="6868d-106">标识代码为进行安全调用所需的确切权限。</span><span class="sxs-lookup"><span data-stu-id="6868d-106">Identify the exact permissions that your code needs in order to make the secured call.</span></span> <span data-ttu-id="6868d-107">如果此方法是库的一部分 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ，则此信息应包括在方法文档中。</span><span class="sxs-lookup"><span data-stu-id="6868d-107">If this method is part of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] library, this information should be included in the method documentation.</span></span>  
  
2.  <span data-ttu-id="6868d-108">修改报表服务器策略配置文件，以便向自定义程序集授予所需的权限。</span><span class="sxs-lookup"><span data-stu-id="6868d-108">Modify the report server policy configuration files in order to grant the custom assembly the required permissions.</span></span> <span data-ttu-id="6868d-109">有关安全策略配置文件的详细信息，请参阅[使用 Reporting Services 安全策略文件](../extensions/secure-development/using-reporting-services-security-policy-files.md)。</span><span class="sxs-lookup"><span data-stu-id="6868d-109">For more information about the security policy configuration files, see [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).</span></span>  
  
3.  <span data-ttu-id="6868d-110">将所需权限断言为按其进行安全调用的方法的一部分。</span><span class="sxs-lookup"><span data-stu-id="6868d-110">Assert the required permissions as part of the method in which the secure call is made.</span></span> <span data-ttu-id="6868d-111">这是必需的，因为报表服务器调用的自定义程序集代码属于报表表达式宿主程序集，默认以 Execution 权限运行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6868d-111">This is required because the custom assembly code that is called by the report server is part of the report expression host assembly, which runs with **Execution** permission by default.</span></span> <span data-ttu-id="6868d-112">Execution 权限集允许代码运行，但无法使用受保护的资源\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6868d-112">The **Execution** permission set enables code to run, but not to use protected resources.</span></span>  
  
4.  <span data-ttu-id="6868d-113">如果自定义程序集使用强名称签名，请使用 AllowPartiallyTrustedCallersAttribute 标记该自定义程序集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6868d-113">Mark the custom assembly with **AllowPartiallyTrustedCallersAttribute** if it is signed with a strong name.</span></span> <span data-ttu-id="6868d-114">这是必需的，因为自定义程序集是从报表表达式宿主程序集中的报表表达式调用的，默认情况下，将不向该报表表达式宿主程序集授予 FullTrust；因此，它是“部分信任的”调用方\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6868d-114">This is required because custom assemblies are called from a report expression that is part of the report expression host assembly, which, by default, is not granted **FullTrust**; thus it is a "partially trusted" caller.</span></span> <span data-ttu-id="6868d-115">有关详细信息，请参阅[使用具有强名称的自定义程序集](using-strong-named-custom-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="6868d-115">For more information, see [Using Strong-Named Custom Assemblies](using-strong-named-custom-assemblies.md).</span></span>  
  
## <a name="implementing-a-secure-call"></a><span data-ttu-id="6868d-116">实现安全调用</span><span class="sxs-lookup"><span data-stu-id="6868d-116">Implementing a Secure Call</span></span>  
 <span data-ttu-id="6868d-117">您可以修改策略配置文件，以便向您的程序集授予特定的权限。</span><span class="sxs-lookup"><span data-stu-id="6868d-117">You can modify the policy configuration files to grant your assembly specific permissions.</span></span> <span data-ttu-id="6868d-118">例如，如果您正在编写用于处理货币换算的自定义程序集，则可能需要从某一文件读取当前外币汇率。</span><span class="sxs-lookup"><span data-stu-id="6868d-118">For example, if you were writing a custom assembly to handle currency conversion, you might need to read the current currency exchange rates from a file.</span></span> <span data-ttu-id="6868d-119">为了检索汇率信息，需要将一个附加的安全权限 FileIOPermission 添加到该程序集的权限集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6868d-119">To retrieve the rate information, you would need to add an additional security permission, **FileIOPermission**, to your permission set for the assembly.</span></span> <span data-ttu-id="6868d-120">您可以在策略配置文件中输入以下附加内容：</span><span class="sxs-lookup"><span data-stu-id="6868d-120">You can make the following additional entry in the policy configuration file:</span></span>  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 <span data-ttu-id="6868d-121">然后，添加引用该权限集的代码组：</span><span class="sxs-lookup"><span data-stu-id="6868d-121">You then add a code group that references that permission set:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 <span data-ttu-id="6868d-122">为使您的代码可以获取相应权限，必须在自定义程序集代码内断言该权限。</span><span class="sxs-lookup"><span data-stu-id="6868d-122">In order for your code to acquire the appropriate permission, you must assert the permission within your custom assembly code.</span></span> <span data-ttu-id="6868d-123">例如，如果您想要添加对某一 XML 文件 C:\CurrencyRates.xml 的只读访问，则必须向您的方法添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="6868d-123">For example, if you want to add read-only access to an XML file, C:\CurrencyRates.xml, you must add the following code to your method:</span></span>  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 <span data-ttu-id="6868d-124">还可以将断言作为方法属性添加：</span><span class="sxs-lookup"><span data-stu-id="6868d-124">You can also add the assertion as a method attribute:</span></span>  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 <span data-ttu-id="6868d-125">有关详细信息，请参阅 .NET Framework 开发人员指南中的“.NET Framework 安全性”。</span><span class="sxs-lookup"><span data-stu-id="6868d-125">For more information, see ".NET Framework Security" in the .NET Framework Developer's Guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6868d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6868d-126">See Also</span></span>  
 [<span data-ttu-id="6868d-127">将自定义程序集用于报表</span><span class="sxs-lookup"><span data-stu-id="6868d-127">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
