---
title: Reporting Services 中的代码访问安全性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services]
- permission sets [Reporting Services]
- evidence [Reporting Services]
- code access security [Reporting Services], about code access security
- named permission sets [Reporting Services]
ms.assetid: 97480368-1fc3-4c32-b1b0-63edfb54e472
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ebe023b13a003895845bbb119f0bc93a0d01203a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591767"
---
# <a name="code-access-security-in-reporting-services"></a><span data-ttu-id="ecf07-102">Reporting Services 中的代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="ecf07-102">Code Access Security in Reporting Services</span></span>
  <span data-ttu-id="ecf07-103">代码访问安全性以下面几个核心概念为中心：证据、代码组和命名权限集。</span><span class="sxs-lookup"><span data-stu-id="ecf07-103">Code access security centers on these core concepts: evidence, code groups, and named permission sets.</span></span> <span data-ttu-id="ecf07-104">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中，报表管理器、报表设计器和报表服务器组件均有一个策略文件，该文件用来为自定义程序集配置代码访问安全性，还用来配置数据扩展插件、传递扩展插件、呈现扩展插件和安全扩展插件。</span><span class="sxs-lookup"><span data-stu-id="ecf07-104">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], the Report Manager, Report Designer, and Report Server components each have a policy file that configures code access security for custom assemblies as well as data, delivery, rendering, and security extensions.</span></span> <span data-ttu-id="ecf07-105">下面几节提供了代码访问安全性的概述。</span><span class="sxs-lookup"><span data-stu-id="ecf07-105">The following sections provide an overview of code access security.</span></span> <span data-ttu-id="ecf07-106">有关本节中所涵盖主题的更详细信息，请参阅 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 文档中的“安全策略模型”。</span><span class="sxs-lookup"><span data-stu-id="ecf07-106">For more detailed information about the topics covered in this section, see "Security Policy Model" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ecf07-107">使用代码访问安全性的原因在于，尽管报表服务器基于 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 技术而构建，但是典型的 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 应用程序和报表服务器之间有着显著的区别。</span><span class="sxs-lookup"><span data-stu-id="ecf07-107">uses code access security because, although the report server is built on [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] technology, there is a substantial difference between a typical [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] application and the report server.</span></span> <span data-ttu-id="ecf07-108">典型的 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 应用程序不执行用户代码。</span><span class="sxs-lookup"><span data-stu-id="ecf07-108">A typical [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] application does not execute user code.</span></span> <span data-ttu-id="ecf07-109">相比之下，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 使用开放式可扩展体系结构，该体系结构允许用户使用报表定义语言的 Code 元素来针对报表定义文件编程，并在自定义程序集内进行专用功能开发，以供报表使用  。</span><span class="sxs-lookup"><span data-stu-id="ecf07-109">In contrast, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses an open and extensible architecture that allows users to program against the report definition files using the **Code** element of the Report Definition Language and to develop specialized functionality into a custom assembly for use in reports.</span></span> <span data-ttu-id="ecf07-110">此外，开发人员可以设计和部署功能强大的扩展插件来增强报表服务器的功能。</span><span class="sxs-lookup"><span data-stu-id="ecf07-110">Furthermore, developers can design and deploy powerful extensions that enhance the capabilities of the report server.</span></span> <span data-ttu-id="ecf07-111">由于具有这种强大的功能和灵活性，因此将需要提供尽可能多的保护和安全性。</span><span class="sxs-lookup"><span data-stu-id="ecf07-111">With this power and flexibility comes the need to provide as much protection and security as possible.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ecf07-112">开发人员可以使用其报表中的任何 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 程序集并在本机调用部署到全局程序集缓存中的所有程序集功能。</span><span class="sxs-lookup"><span data-stu-id="ecf07-112">developers can use any [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly in their reports and natively call upon all of the functionality of assemblies deployed to the global assembly cache.</span></span> <span data-ttu-id="ecf07-113">报表服务器唯一能够控制的内容就是向报表表达式和已加载的自定义程序集授予的权限。</span><span class="sxs-lookup"><span data-stu-id="ecf07-113">The only thing that the report server can control is what permissions are given for report expressions and loaded custom assemblies.</span></span> <span data-ttu-id="ecf07-114">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中，自定义程序集在默认情况下接收仅 Execute 权限  。</span><span class="sxs-lookup"><span data-stu-id="ecf07-114">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], custom assemblies receive **Execute**-only permissions by default.</span></span>  
  
## <a name="evidence"></a><span data-ttu-id="ecf07-115">证据</span><span class="sxs-lookup"><span data-stu-id="ecf07-115">Evidence</span></span>  
 <span data-ttu-id="ecf07-116">证据是公共语言运行时 (CLR) 用来为代码程序集确定安全策略的信息。</span><span class="sxs-lookup"><span data-stu-id="ecf07-116">Evidence is the information that the common language runtime (CLR) uses to determine a security policy for code assemblies.</span></span> <span data-ttu-id="ecf07-117">证据向公共语言运行时指示代码具有特定的特征。</span><span class="sxs-lookup"><span data-stu-id="ecf07-117">Evidence indicates to the runtime that code has a particular characteristic.</span></span> <span data-ttu-id="ecf07-118">证据的常见形式包括数字签名和程序集位置，</span><span class="sxs-lookup"><span data-stu-id="ecf07-118">Common forms of evidence include digital signatures and the location of an assembly.</span></span> <span data-ttu-id="ecf07-119">但也可以自定义设计证据来表示其他对应用程序有意义的信息。</span><span class="sxs-lookup"><span data-stu-id="ecf07-119">Evidence can also be custom designed to represent other information that is meaningful to the application.</span></span>  
  
 <span data-ttu-id="ecf07-120">程序集和应用程序域都接收基于证据的权限。</span><span class="sxs-lookup"><span data-stu-id="ecf07-120">Both assemblies and application domains receive permissions based on evidence.</span></span> <span data-ttu-id="ecf07-121">例如，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 尝试访问的程序集的位置是一种常见形式的弱名称程序集证据。</span><span class="sxs-lookup"><span data-stu-id="ecf07-121">For example, the location of an assembly that [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is attempting to access is one common form of evidence for weak-named assemblies.</span></span> <span data-ttu-id="ecf07-122">这样的证据称作 URL 证据。</span><span class="sxs-lookup"><span data-stu-id="ecf07-122">This is known as URL evidence.</span></span> <span data-ttu-id="ecf07-123">部署到报表服务器上的自定义数据处理扩展插件的 URL 证据可以是“C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll”。</span><span class="sxs-lookup"><span data-stu-id="ecf07-123">URL evidence for a custom data processing extension deployed to a report server might be "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll".</span></span> <span data-ttu-id="ecf07-124">程序集的强名称或数字签名是另一种常见形式的证据。</span><span class="sxs-lookup"><span data-stu-id="ecf07-124">The strong name or digital signature of an assembly is another common form of evidence.</span></span> <span data-ttu-id="ecf07-125">在这种情况下，证据是程序集的公钥信息。</span><span class="sxs-lookup"><span data-stu-id="ecf07-125">In this case, the evidence is the public key information for an assembly.</span></span>  
  
## <a name="code-groups"></a><span data-ttu-id="ecf07-126">代码组</span><span class="sxs-lookup"><span data-stu-id="ecf07-126">Code Groups</span></span>  
 <span data-ttu-id="ecf07-127">代码组是代码的逻辑分组，该分组具有指定的成员身份条件。</span><span class="sxs-lookup"><span data-stu-id="ecf07-127">A code group is a logical grouping of code that has a specified condition for membership.</span></span> <span data-ttu-id="ecf07-128">所有满足成员身份条件的代码均包括在该组中。</span><span class="sxs-lookup"><span data-stu-id="ecf07-128">Any code that meets the membership condition is included in the group.</span></span> <span data-ttu-id="ecf07-129">管理员通过管理代码组及其关联权限集来配置安全策略。</span><span class="sxs-lookup"><span data-stu-id="ecf07-129">Administrators configure a security policy by managing code groups and their associated permission sets.</span></span>  
  
 <span data-ttu-id="ecf07-130">代码组的成员身份条件基于证据。</span><span class="sxs-lookup"><span data-stu-id="ecf07-130">A membership condition for a code group is based on evidence.</span></span> <span data-ttu-id="ecf07-131">例如，代码组的 URL 成员身份基于 URL 证据。</span><span class="sxs-lookup"><span data-stu-id="ecf07-131">For example, a URL membership for a code group is based on URL evidence.</span></span> <span data-ttu-id="ecf07-132">公共语言运行时 (CLR) 使用标识特征（如 URL 证据）来描述代码并确定是否已符合组的成员身份条件。</span><span class="sxs-lookup"><span data-stu-id="ecf07-132">The common language runtime (CLR) uses identifying characteristics such as URL evidence to describe the code and to determine whether a group's membership condition has been met.</span></span> <span data-ttu-id="ecf07-133">例如，如果代码组的成员身份条件是“程序集 C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll 中的代码”，则公共语言运行时会检查证据以确定代码是否源自该位置。</span><span class="sxs-lookup"><span data-stu-id="ecf07-133">For example, if the membership condition of a code group is "code in the assembly C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll", the runtime examines the evidence to determine whether the code originates from that location.</span></span> <span data-ttu-id="ecf07-134">这种类型的代码组的配置条目示例看上去可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="ecf07-134">An example of a configuration entry for this type of code group might look like the following:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="FullTrust"  
   Name="MyCodeGroup"  
   Description="Code group for my data processing extension">  
      <IMembershipCondition class="UrlMembershipCondition"  
         version="1"  
         Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll"  
       />  
</CodeGroup>  
```  
  
 <span data-ttu-id="ecf07-135">您应当与系统管理员或应用程序开发专家一起来确定代码访问安全性的类型以及自定义程序集或 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 扩展插件所需的代码组。</span><span class="sxs-lookup"><span data-stu-id="ecf07-135">You should work with your system administrator or application deployment expert to determine the type of code access security and code groups that your custom assemblies or [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extensions require.</span></span>  
  
## <a name="named-permission-sets"></a><span data-ttu-id="ecf07-136">命名权限集</span><span class="sxs-lookup"><span data-stu-id="ecf07-136">Named Permission Sets</span></span>  
 <span data-ttu-id="ecf07-137">命名权限集是管理员可以将其与某个代码组关联的权限集。</span><span class="sxs-lookup"><span data-stu-id="ecf07-137">A named permission set is a set of permissions that administrators can associate with a code group.</span></span> <span data-ttu-id="ecf07-138">大多数命名权限集都至少包含一个权限、一个名称以及对该权限集的说明。</span><span class="sxs-lookup"><span data-stu-id="ecf07-138">Most named permission sets consist of at least one permission, a name, and description for the permission set.</span></span> <span data-ttu-id="ecf07-139">管理员可以使用命名权限集来创建或修改代码组的安全策略。</span><span class="sxs-lookup"><span data-stu-id="ecf07-139">Administrators can use named permission sets to establish or modify the security policy for code groups.</span></span> <span data-ttu-id="ecf07-140">可以将多个代码组与同一个命名权限集关联。</span><span class="sxs-lookup"><span data-stu-id="ecf07-140">More than one code group can be associated with the same named permission set.</span></span> <span data-ttu-id="ecf07-141">CLR 提供内置的命名权限集，其中包括 Nothing、Execution、Internet、LocalIntranet、Everything 和 FullTrust       。</span><span class="sxs-lookup"><span data-stu-id="ecf07-141">The CLR provides built-in named permission sets; among these are **Nothing**, **Execution**, **Internet**, **LocalIntranet**, **Everything**, and **FullTrust**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecf07-142">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的自定义数据扩展插件、传递扩展插件、呈现扩展插件和安全扩展插件必须以 FullTrust 权限集运行  。</span><span class="sxs-lookup"><span data-stu-id="ecf07-142">Custom data, delivery, rendering, and security extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] must run under the **FullTrust** permission set.</span></span> <span data-ttu-id="ecf07-143">可以与系统管理员一起为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 扩展插件添加适当的代码组和成员身份条件。</span><span class="sxs-lookup"><span data-stu-id="ecf07-143">Work with your system administrator to add the appropriate code group and membership conditions for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extensions.</span></span>  
  
 <span data-ttu-id="ecf07-144">可以将自定义的权限级别与那些和报表一起使用的自定义程序集相关联。</span><span class="sxs-lookup"><span data-stu-id="ecf07-144">You can associate your own custom levels of permissions for custom assemblies that you use with reports.</span></span> <span data-ttu-id="ecf07-145">例如，如果您希望允许程序集访问特定的文件，则可以新建一个具有特定文件 I/O 访问权限的命名权限集，然后将该权限集分配给您的代码组。</span><span class="sxs-lookup"><span data-stu-id="ecf07-145">For example, if you want to allow an assembly to access a specific file, you can create a new named permission set with specific file I/O access and then assign the permission set to your code group.</span></span> <span data-ttu-id="ecf07-146">下面的权限集向 MyFile.xml 文件授予只读访问权限：</span><span class="sxs-lookup"><span data-stu-id="ecf07-146">The following permission set grants read-only access to the file MyFile.xml:</span></span>  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="MyNewFilePermissionSet"  
   Description="A special permission set that grants read access to my file.">  
    <IPermission class="FileIOPermission"  
       version="1"  
       Read="C:\MyFile.xml"/>  
    <IPermission class="SecurityPermission"  
       version="1"  
       Flags="Assertion, Execution"/>  
</PermissionSet>  
```  
  
 <span data-ttu-id="ecf07-147">被授予此权限集的代码组看上去可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="ecf07-147">A code group that you grant this permission set might look like the following:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="MyNewFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\MyCustomAssembly.dll"/>  
</CodeGroup>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ecf07-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ecf07-148">See Also</span></span>  
 [<span data-ttu-id="ecf07-149">安全开发 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="ecf07-149">Secure Development &#40;Reporting Services&#41;</span></span>](secure-development-reporting-services.md)  
  
  
