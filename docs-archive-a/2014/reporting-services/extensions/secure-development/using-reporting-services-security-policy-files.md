---
title: 使用 Reporting Services 安全策略文件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- CodeGroup elements
- configuration files [Reporting Services]
- code access security [Reporting Services], security policies
- security policies [Reporting Services]
- security configuration files [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: 2280fff6-3de7-44b1-87da-5db0ec975928
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15c5422741137505bc29a2de861fca1420e455d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591135"
---
# <a name="using-reporting-services-security-policy-files"></a><span data-ttu-id="11985-102">使用 Reporting Services 安全策略文件</span><span class="sxs-lookup"><span data-stu-id="11985-102">Using Reporting Services Security Policy Files</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="11985-103">将组件安全策略信息存储在三个配置文件中，而这三个配置文件会在安装过程中复制到文件系统。</span><span class="sxs-lookup"><span data-stu-id="11985-103">stores component security policy information in three configuration files that are copied to the file system during setup.</span></span> <span data-ttu-id="11985-104">这些配置文件可以包含 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中代码程序集的内部使用安全策略和用户定义安全策略的组合。</span><span class="sxs-lookup"><span data-stu-id="11985-104">These configuration files can contain a combination of internal-use and user-defined security policies for code assemblies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="11985-105">三个配置文件与 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的三个安全对象组件相对应：报表服务器和 Windows 服务、报表管理器 Web 应用程序以及报表设计器预览窗口。</span><span class="sxs-lookup"><span data-stu-id="11985-105">The three configuration files correspond to three securable components in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]: The report server and Windows service, the Report Manager Web application, and the Report Designer preview window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11985-106">报表设计器有两种预览模式：预览选项卡以及在以 DebugLocal 模式启动报表项目时启动的弹出式预览窗口  。</span><span class="sxs-lookup"><span data-stu-id="11985-106">There are two preview modes for Report Designer: the preview tab and the pop-up preview window that is launched when your Report Project is started in **DebugLocal** mode.</span></span> <span data-ttu-id="11985-107">“预览”选项卡不是安全对象组件，不应用安全策略设置  。</span><span class="sxs-lookup"><span data-stu-id="11985-107">The **Preview** tab is not a securable component and does not apply security policy settings.</span></span> <span data-ttu-id="11985-108">预览窗口旨在模拟报表服务器的功能，因此具有策略配置文件，您或管理员必须修改该文件才能在报表设计器中使用自定义程序集和自定义扩展插件。</span><span class="sxs-lookup"><span data-stu-id="11985-108">The preview window is meant to simulate the report server functionality and therefore has a policy configuration file that you or an administrator must modify to use custom assemblies and custom extensions in Report Designer.</span></span>  
  
 <span data-ttu-id="11985-109">这些安全策略配置文件包含 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的程序集的安全类信息、一些默认的命名权限集以及代码组。</span><span class="sxs-lookup"><span data-stu-id="11985-109">The security policy configuration files contain security class information, some default named permission sets, and the code groups for assemblies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="11985-110">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的策略配置文件与 Security.config 文件相似，该 Security.config 文件确定与计算机和 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中的企业级策略关联的代码组层次结构和权限集。</span><span class="sxs-lookup"><span data-stu-id="11985-110">The policy configuration files of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] are similar to the Security.config file that determines the code group hierarchy and permission sets associated with machine and enterprise level policies in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="11985-111">该文件的位置是 C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config。</span><span class="sxs-lookup"><span data-stu-id="11985-111">The location of this file is C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config.</span></span>  
  
## <a name="policy-files-in-reporting-services"></a><span data-ttu-id="11985-112">Reporting Services 中的策略文件</span><span class="sxs-lookup"><span data-stu-id="11985-112">Policy Files in Reporting Services</span></span>  
 <span data-ttu-id="11985-113">下表列出了 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的策略配置文件、文件位置（假定默认安装）及其各自的功能。</span><span class="sxs-lookup"><span data-stu-id="11985-113">The following table lists the policy configuration files in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], their locations (assuming a default installation), and their respective functions.</span></span>  
  
|<span data-ttu-id="11985-114">文件名</span><span class="sxs-lookup"><span data-stu-id="11985-114">File name</span></span>|<span data-ttu-id="11985-115">位置（默认安装）</span><span class="sxs-lookup"><span data-stu-id="11985-115">Location (default installation)</span></span>|<span data-ttu-id="11985-116">说明</span><span class="sxs-lookup"><span data-stu-id="11985-116">Description</span></span>|  
|---------------|---------------------------------------|-----------------|  
|<span data-ttu-id="11985-117">rssrvpolicy.config</span><span class="sxs-lookup"><span data-stu-id="11985-117">rssrvpolicy.config</span></span>|<span data-ttu-id="11985-118">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer</span><span class="sxs-lookup"><span data-stu-id="11985-118">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer</span></span>|<span data-ttu-id="11985-119">报表服务器策略配置文件。</span><span class="sxs-lookup"><span data-stu-id="11985-119">The report server policy configuration file.</span></span> <span data-ttu-id="11985-120">在将报表部署到报表服务器之后，这些安全策略主要影响报表表达式和自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="11985-120">These security policies primarily affect report expressions and custom assemblies once a report is deployed to a report server.</span></span> <span data-ttu-id="11985-121">此策略文件还影响部署到报表服务器的自定义数据、传递、呈现和安全扩展插件。</span><span class="sxs-lookup"><span data-stu-id="11985-121">This policy file also affects custom data, delivery, rendering and security extensions deployed to the report server.</span></span>|  
|<span data-ttu-id="11985-122">rsmgrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="11985-122">rsmgrpolicy.config</span></span>|<span data-ttu-id="11985-123">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager</span><span class="sxs-lookup"><span data-stu-id="11985-123">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager</span></span>|<span data-ttu-id="11985-124">报表管理器策略配置文件。</span><span class="sxs-lookup"><span data-stu-id="11985-124">Report Manager policy configuration file.</span></span> <span data-ttu-id="11985-125">这些安全策略影响扩展报表管理器的所有程序集，例如用于自定义传递的订阅用户界面扩展插件。</span><span class="sxs-lookup"><span data-stu-id="11985-125">These security policies affect all assemblies that extend Report Manager; for example, subscription user interface extensions for custom delivery.</span></span>|  
|<span data-ttu-id="11985-126">rspreviewpolicy.config</span><span class="sxs-lookup"><span data-stu-id="11985-126">rspreviewpolicy.config</span></span>|<span data-ttu-id="11985-127">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies</span><span class="sxs-lookup"><span data-stu-id="11985-127">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies</span></span>|<span data-ttu-id="11985-128">报表设计器独立预览策略配置文件。</span><span class="sxs-lookup"><span data-stu-id="11985-128">The Report Designer stand-alone preview policy configuration file.</span></span> <span data-ttu-id="11985-129">这些安全策略影响预览和开发期间报表中使用的自定义程序集和报表表达式。</span><span class="sxs-lookup"><span data-stu-id="11985-129">These security policies affect custom assemblies and report expressions that are used in reports during preview and development.</span></span> <span data-ttu-id="11985-130">这些策略还影响部署到报表设计器的自定义扩展插件，例如事件处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="11985-130">These policies also affect custom extensions, such as data processing extensions, that are deployed to Report Designer.</span></span>|  
  
## <a name="modifying-configuration-files"></a><span data-ttu-id="11985-131">修改配置文件</span><span class="sxs-lookup"><span data-stu-id="11985-131">Modifying Configuration Files</span></span>  
 <span data-ttu-id="11985-132">将配置设置指定为 XML 元素或属性。</span><span class="sxs-lookup"><span data-stu-id="11985-132">Configuration settings are specified as either XML elements or attributes.</span></span> <span data-ttu-id="11985-133">如果您了解 XML 和配置文件，则可以使用文本编辑器或代码编辑器来修改可以由用户定义的设置。</span><span class="sxs-lookup"><span data-stu-id="11985-133">If you understand XML and configuration files, you can use a text or code editor to modify user-definable settings.</span></span> <span data-ttu-id="11985-134">安全配置文件包含有关与 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中策略级别关联的代码组层次结构和权限集的信息。</span><span class="sxs-lookup"><span data-stu-id="11985-134">Security configuration files contain information about the code group hierarchy and permission sets associated with a policy level in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="11985-135">建议先使用 .NET Framework 配置实用工具 (Mscorcfg.msc) 或代码访问安全性策略实用工具 (Caspol.exe) 来修改 Security.config 文件中的安全策略，以确保策略更改与策略文件的有效 XML 配置元素相对应。</span><span class="sxs-lookup"><span data-stu-id="11985-135">It is recommended that you use the .NET Framework Configuration Utility (Mscorcfg.msc) or Code Access Security Policy Utility (Caspol.exe) to modify security policies in the Security.config file first, so that policy changes correspond to valid XML configuration elements for policy files.</span></span> <span data-ttu-id="11985-136">完成该操作后，可以从 Security.config 中剪切新代码组和权限集并粘贴到要向其添加代码权限的组件的策略文件。</span><span class="sxs-lookup"><span data-stu-id="11985-136">Once you have done that, you can cut and paste the new code groups and permission sets from Security.config to the policy file for the component to which you are adding code permissions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="11985-137">进行更改之前应备份策略配置文件。</span><span class="sxs-lookup"><span data-stu-id="11985-137">You should backup your policy configuration files prior to making any changes.</span></span>  
  
 <span data-ttu-id="11985-138">使用此方法可完成两个任务。</span><span class="sxs-lookup"><span data-stu-id="11985-138">Using this approach accomplishes two things.</span></span> <span data-ttu-id="11985-139">首先，此方法使您能够使用可视化工具来为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 生成代码组和权限集。</span><span class="sxs-lookup"><span data-stu-id="11985-139">First, it enables you to use a visual tool to build your code groups and permission sets for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="11985-140">这比从头开始编写 XML 配置元素容易得多。</span><span class="sxs-lookup"><span data-stu-id="11985-140">This is much easier than writing XML configuration elements from scratch.</span></span> <span data-ttu-id="11985-141">其次，此方法确保不会用格式不正确的 XML 元素和属性损坏安全策略配置文件。</span><span class="sxs-lookup"><span data-stu-id="11985-141">Secondly, it ensures that you do not corrupt the security policy configuration files with malformed XML elements and attributes.</span></span> <span data-ttu-id="11985-142">有关代码访问安全性策略实用工具的详细信息，请参阅 MSDN 上的“Using Reporting Services Security Policy Files”（使用 Reporting Services 安全策略文件）。</span><span class="sxs-lookup"><span data-stu-id="11985-142">For more information about the Code Access Security Policy Utility, see Using Reporting Services Security Policy Files on MSDN.</span></span>  
  
 <span data-ttu-id="11985-143">在修改策略配置文件之前，您应该阅读本节和相关主题中的所有信息。</span><span class="sxs-lookup"><span data-stu-id="11985-143">Before modifying policy configuration files, you should read all the information available in this section and related topics.</span></span> <span data-ttu-id="11985-144">修改 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的策略配置可能对 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 组件如何执行外部代码模块具有重大的安全影响。</span><span class="sxs-lookup"><span data-stu-id="11985-144">Modifying the policy configuration of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] can have a significant security impact on how [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] components execute external code modules.</span></span>  
  
## <a name="placement-of-codegroup-elements-for-extensions"></a><span data-ttu-id="11985-145">扩展插件的 CodeGroup 元素的位置</span><span class="sxs-lookup"><span data-stu-id="11985-145">Placement of CodeGroup Elements for Extensions</span></span>  
 <span data-ttu-id="11985-146">安全策略文件中 CodeGroup 元素的位置非常重要。</span><span class="sxs-lookup"><span data-stu-id="11985-146">The placement of CodeGroup elements in a security policy file is important.</span></span> <span data-ttu-id="11985-147">对于您开发的扩展插件和自定义程序集，建议将自定义代码组紧靠在 URL 成员身份“$CodeGen$/\*”的现有条目的下面，如下所示：</span><span class="sxs-lookup"><span data-stu-id="11985-147">For extensions and custom assemblies that you develop, it is recommended that you place your custom code groups directly below the existing entry for the URL membership "$CodeGen$/\*", as indicated by the following:</span></span>  
  
```  
<CodeGroup  
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust">  
    <IMembershipCondition   
        class="UrlMembershipCondition"  
        version="1"  
        Url="$CodeGen$/*"  
    />  
</CodeGroup>  
<CodeGroup   
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust"  
    Name="MyCustomCodeGroup"  
    Description="Code group for my custom extension">  
        <IMembershipCondition class="UrlMembershipCondition"  
        version="1"  
        Url="C:\Program Files\Microsoft SQL Server\MSSQL\Reporting Services\ReportServer\bin\MyAssembly.dll"  
        />  
</CodeGroup>  
```  
  
 <span data-ttu-id="11985-148">可以逐个添加其他代码组。</span><span class="sxs-lookup"><span data-stu-id="11985-148">Additional code groups can be added one after another.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11985-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11985-149">See Also</span></span>  
 [<span data-ttu-id="11985-150">了解安全策略</span><span class="sxs-lookup"><span data-stu-id="11985-150">Understanding Security Policies</span></span>](understanding-security-policies.md)  
  
  
