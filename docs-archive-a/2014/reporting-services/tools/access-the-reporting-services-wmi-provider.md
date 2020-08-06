---
title: 访问 Reporting Services WMI 提供程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services]
- programming [Reporting Services]
ms.assetid: 22cfbeb8-4ea3-4182-8f54-3341c771e87b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: db0848ae8c988229a1804bbd4b19e6c38b68c35f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692255"
---
# <a name="access-the-reporting-services-wmi-provider"></a><span data-ttu-id="17ea5-102">访问 Reporting Services WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="17ea5-102">Access the Reporting Services WMI Provider</span></span>
  <span data-ttu-id="17ea5-103">Reporting Services WMI 提供程序公开了两个 WMI 类，用于通过脚本管理本机模式报表服务器实例：</span><span class="sxs-lookup"><span data-stu-id="17ea5-103">The Reporting Services WMI provider exposes two WMI classes for administration of Native mode report server instances through scripting:</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="17ea5-104">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 版本开始，只有本机模式报表服务器才支持 WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="17ea5-104">Starting with the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] release, the WMI provider is supported for only native mode report servers.</span></span> <span data-ttu-id="17ea5-105">可以使用 SharePoint 管理中心页和 PowerShell 脚本管理 SharePoint 模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="17ea5-105">SharePoint mode report servers can be managed with SharePoint Central Administration pages and PowerShell scripts.</span></span>  
  
|<span data-ttu-id="17ea5-106">类</span><span class="sxs-lookup"><span data-stu-id="17ea5-106">Class</span></span>|<span data-ttu-id="17ea5-107">命名空间</span><span class="sxs-lookup"><span data-stu-id="17ea5-107">Namespace</span></span>|<span data-ttu-id="17ea5-108">说明</span><span class="sxs-lookup"><span data-stu-id="17ea5-108">Description</span></span>|  
|-----------|---------------|-----------------|  
|<span data-ttu-id="17ea5-109">MSReportServer_Instance</span><span class="sxs-lookup"><span data-stu-id="17ea5-109">MSReportServer_Instance</span></span>|<span data-ttu-id="17ea5-110">root\Microsoft\SqlServer\ReportServer\ RS_ *\<EncodedInstanceName>* \v11</span><span class="sxs-lookup"><span data-stu-id="17ea5-110">root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v11</span></span>|<span data-ttu-id="17ea5-111">为客户端提供连接到已安装的报表服务器所需的基本信息。</span><span class="sxs-lookup"><span data-stu-id="17ea5-111">Provides basic information required for a client to connect to an installed report server.</span></span>|  
|<span data-ttu-id="17ea5-112">MSReportServer_ConfigurationSetting</span><span class="sxs-lookup"><span data-stu-id="17ea5-112">MSReportServer_ConfigurationSetting</span></span>|<span data-ttu-id="17ea5-113">root\Microsoft\SqlServer\ReportServer\ RS_ *\<EncodedInstanceName>* \v11\Admin</span><span class="sxs-lookup"><span data-stu-id="17ea5-113">root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v11\Admin</span></span>|<span data-ttu-id="17ea5-114">表示报表服务器实例的安装和运行时参数。</span><span class="sxs-lookup"><span data-stu-id="17ea5-114">Represents the installation and run-time parameters of a report server instance.</span></span> <span data-ttu-id="17ea5-115">这些参数存储在报表服务器的配置文件中。</span><span class="sxs-lookup"><span data-stu-id="17ea5-115">These parameters are stored in the configuration file for the report server.</span></span><br /><br /> <span data-ttu-id="17ea5-116">**\*\* 重要提示 \*\*** 只有拥有管理权限才能访问此类。</span><span class="sxs-lookup"><span data-stu-id="17ea5-116">**\*\* Important \*\*** This class is only accessible with administrative privileges.</span></span>|  
  
 <span data-ttu-id="17ea5-117">以上每个类实例是为每个报表服务器实例创建的。</span><span class="sxs-lookup"><span data-stu-id="17ea5-117">An instance of each of the above classes is created for each report server instance.</span></span> <span data-ttu-id="17ea5-118">您可以使用任何 Microsoft 或第三方工具来访问报表服务器公开的 WMI 对象，包括 .NET Framework 本身公开的 WMI 编程接口。</span><span class="sxs-lookup"><span data-stu-id="17ea5-118">You can use any Microsoft or third party tools to access the WMI objects exposed by the report server, including WMI programming interfaces exposed by the .NET Framework itself.</span></span> <span data-ttu-id="17ea5-119">本主题介绍如何使用 PowerShell 命令 [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx)访问和使用 WMI 类实例。</span><span class="sxs-lookup"><span data-stu-id="17ea5-119">This topic describes how to access and use the WMI class instances with the PowerShell command [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx).</span></span>  
  
## <a name="determine-the-instance-name-in-the-namespace-string"></a><span data-ttu-id="17ea5-120">确定命名空间字符串中的实例名称</span><span class="sxs-lookup"><span data-stu-id="17ea5-120">Determine the Instance Name in the Namespace String</span></span>  
 <span data-ttu-id="17ea5-121">命名空间路径中针对 Reporting Services WMI 类的实例名称是您在安装命名 Reporting Services 实例时指定的实例名称的编码形式。</span><span class="sxs-lookup"><span data-stu-id="17ea5-121">The instance name in the namespace path for the Reporting Services WMI classes is an encoding of the instance names that you specify when installing the named Reporting Services instances.</span></span> <span data-ttu-id="17ea5-122">也就是说，对实例名称中的特殊字符进行编码。</span><span class="sxs-lookup"><span data-stu-id="17ea5-122">Namely, special characters in the instance names are encoded.</span></span> <span data-ttu-id="17ea5-123">例如，下划线 (_) 编码为“_5f”，这样，实例名称“My_Instance”在 WMI 命名空间路径中就编码为“My_5fInstance”。</span><span class="sxs-lookup"><span data-stu-id="17ea5-123">For example, an underline (_) is encoded as "_5f", so an instance name of "My_Instance" is encoded as "My_5fInstance" in the WMI namespace path.</span></span>  
  
 <span data-ttu-id="17ea5-124">若要列出 WMI 命名空间路径中报表服务器实例的编码实例名称，请使用以下 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="17ea5-124">To list the encoded instance names of your report server instances in the WMI namespace path, use the following PowerShell command:</span></span>  
  
```powershell
Get-WmiObject -Namespace root\Microsoft\SqlServer\ReportServer -Class __Namespace -ComputerName hostname | Select Name  
```  
  
## <a name="access-the-wmi-classes-using-powershell"></a><span data-ttu-id="17ea5-125">使用 PowerShell 访问 WMI 类</span><span class="sxs-lookup"><span data-stu-id="17ea5-125">Access the WMI Classes Using PowerShell</span></span>  
 <span data-ttu-id="17ea5-126">若要访问 WMI 类，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="17ea5-126">To access the WMI classes, run the following command:</span></span>  
  
```powershell
Get-WmiObject -Namespace <namespacename> -Class <classname> -ComputerName <hostname>  
```  
  
 <span data-ttu-id="17ea5-127">例如，若要访问主机 myrshost 的默认报表服务器实例上的 MSReportServer_ConfigurationSetting 类，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="17ea5-127">For example, to access the MSReportServer_ConfigurationSetting class on the default report server instance of the host myrshost, run the following command.</span></span> <span data-ttu-id="17ea5-128">默认报表服务器实例必须安装在 myrshost 上，这样此命令才会成功。</span><span class="sxs-lookup"><span data-stu-id="17ea5-128">The default report server instance must be installed on myrshost for this command to succeed.</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLSERER\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost  
```  
  
 <span data-ttu-id="17ea5-129">此命令语法会输出所有的类属性名称和值。</span><span class="sxs-lookup"><span data-stu-id="17ea5-129">This command syntax outputs all class property names and values.</span></span> <span data-ttu-id="17ea5-130">请注意，会返回 MSReportServer_ConfigurationSetting 类的所有实例，即使您在默认报表服务器实例 (RS_MSSQLSERVER) 的命名空间中访问此类也是如此。</span><span class="sxs-lookup"><span data-stu-id="17ea5-130">Note that all instances of the class MSReportServer_ConfigurationSetting is returned, even though you are accessing the class in the namespace of the default report server instance (RS_MSSQLSERVER).</span></span> <span data-ttu-id="17ea5-131">例如，如果 myrshost 上安装了默认报表服务器实例和名为 SHAREPOINT 的命名报表服务器实例，此命令将返回两个 WMI 对象并输出这两个报表服务器实例的属性名称和值。</span><span class="sxs-lookup"><span data-stu-id="17ea5-131">For example, if myrshost is installed with the default report server instance and a named report server instance called SHAREPOINT, this command will return two WMI objects and output the property names and values for both report server instances.</span></span>  
  
 <span data-ttu-id="17ea5-132">若要在返回多个实例时返回特定类实例，请使用 -Filter 参数基于值唯一的属性（如 InstanceName）对结果进行筛选。</span><span class="sxs-lookup"><span data-stu-id="17ea5-132">To return a specific class instance when multiple instances are returned, use the -Filter parameter to filter the results based on properties with unique values such as InstanceName.</span></span> <span data-ttu-id="17ea5-133">例如，若要仅返回默认报表服务器实例的 WMI 对象，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="17ea5-133">For example, to return only the WMI object for the default report server instance, use the following command:</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='MSSQLSERVER'"  
```  
  
## <a name="query-the-available-methods-and-properties"></a><span data-ttu-id="17ea5-134">查询可用的方法和属性</span><span class="sxs-lookup"><span data-stu-id="17ea5-134">Query the Available Methods and Properties</span></span>  
 <span data-ttu-id="17ea5-135">若要查看某个 Reporting Services WMI 类中有哪些可用的方法和属性，请将结果从 Get-WmiObject 管道传送到 Get-Member 命令。</span><span class="sxs-lookup"><span data-stu-id="17ea5-135">To see what methods and properties are available in one of the Reporting Services WMI classes, pipe the results from Get-WmiObject to the Get-Member command.</span></span> <span data-ttu-id="17ea5-136">例如：</span><span class="sxs-lookup"><span data-stu-id="17ea5-136">For example:</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost | Get-Member  
```  
  
 <span data-ttu-id="17ea5-137">有关 Reporting Services WMI 类的属性和方法的文档，请参阅 ...。</span><span class="sxs-lookup"><span data-stu-id="17ea5-137">For documentation on the properties and methods of the Reporting Services WMI classes, see ....</span></span>  
  
## <a name="use-a-wmi-method-or-property"></a><span data-ttu-id="17ea5-138">使用 WMI 方法或属性</span><span class="sxs-lookup"><span data-stu-id="17ea5-138">Use a WMI Method or Property</span></span>  
 <span data-ttu-id="17ea5-139">一旦您将 WMI 对象传送到 Reporting Services 类并且知道可用的方法和属性，就可以使用这些方法和属性。</span><span class="sxs-lookup"><span data-stu-id="17ea5-139">Once you have the WMI objects to the Reporting Services classes and know the available methods and properties, you can use these methods and properties.</span></span> <span data-ttu-id="17ea5-140">例如，如果您在 SharePoint 集成模式中有一个名为 SHAREPOINT 的命名报表服务器实例，可以使用以下命令序列检索 SharePoint 管理中心站点的 URL：</span><span class="sxs-lookup"><span data-stu-id="17ea5-140">For example, if you have a named report server instance in SharePoint integrated mode called SHAREPOINT, use the following command sequence to retrieve the URL for the SharePoint Central Administration site:</span></span>  
  
```powershell
$rsconfig = Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='SHAREPOINT'"  
$rsconfig.GetAdminSiteUrl()  
```  
  
## <a name="see-also"></a><span data-ttu-id="17ea5-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17ea5-141">See Also</span></span>
 <span data-ttu-id="17ea5-142">[Reporting Services WMI 提供程序库引用 &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="17ea5-142">[Reporting Services WMI Provider Library Reference &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="17ea5-143">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="17ea5-143">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
