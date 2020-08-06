---
title: Web 配置参考 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 71e72bdb45a29c29c2187c381f67a525f0bd51c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692977"
---
# <a name="web-configuration-reference-master-data-services"></a><span data-ttu-id="25bcc-102">Web 配置参考 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="25bcc-102">Web Configuration Reference (Master Data Services)</span></span>
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="25bcc-103">使用 Web.config 文件来包含使 Internet Information Services (IIS) 能够承载 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序和 Web 服务的配置设置。</span><span class="sxs-lookup"><span data-stu-id="25bcc-103">uses a Web.config file to contain the configuration settings that enable Internet Information Services (IIS) to host the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application and the Web service.</span></span> <span data-ttu-id="25bcc-104">此 Web.config 文件位于 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 安装路径的 WebApplication 文件夹。</span><span class="sxs-lookup"><span data-stu-id="25bcc-104">This Web.config file is located in the WebApplication folder of the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] installation path.</span></span> <span data-ttu-id="25bcc-105">有关路径和权限的详细信息，请参阅[文件夹和文件权限 (Master Data Services)](folder-and-file-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="25bcc-105">For more information about the path and permissions, see [Folder and File Permissions &#40;Master Data Services&#41;](folder-and-file-permissions-master-data-services.md).</span></span>  
  
## <a name="webconfig-elements"></a><span data-ttu-id="25bcc-106">Web.Config 元素</span><span class="sxs-lookup"><span data-stu-id="25bcc-106">Web.Config Elements</span></span>  
 <span data-ttu-id="25bcc-107">Web.config 文件 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] **\<masterDataServices>** 除了包含标准 IIS、.NET Framework、ASP.NET 和 WINDOWS COMMUNICATION FOUNDATION (WCF) 配置元素外，还包含一个自定义元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-107">The Web.config file contains a custom [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] element, **\<masterDataServices>**, in addition to standard IIS, .NET Framework, ASP.NET, and Windows Communication Foundation (WCF) configuration elements.</span></span> <span data-ttu-id="25bcc-108">下表描述了 Web.config 文件中包括的元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-108">The following table describes the elements included in the Web.config file.</span></span>  
  
|<span data-ttu-id="25bcc-109">配置元素</span><span class="sxs-lookup"><span data-stu-id="25bcc-109">Configuration Element</span></span>|<span data-ttu-id="25bcc-110">说明</span><span class="sxs-lookup"><span data-stu-id="25bcc-110">Description</span></span>|  
|---------------------------|-----------------|  
|`masterDataServices`|<span data-ttu-id="25bcc-111">自定义元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-111">Custom element.</span></span> <span data-ttu-id="25bcc-112">将 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web 服务连接到 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="25bcc-112">Connects the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web service to a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>|  
|`connectionStrings`|<span data-ttu-id="25bcc-113">ASP.NET 元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-113">ASP.NET element.</span></span> <span data-ttu-id="25bcc-114">有关详细信息，请参阅 MSDN Library 中的 [connectionStrings 元素（ASP.NET 设置架构）](https://go.microsoft.com/fwlink/?LinkId=178347) 。</span><span class="sxs-lookup"><span data-stu-id="25bcc-114">For more information, see [connectionStrings Element (ASP.NET Settings Schema)](https://go.microsoft.com/fwlink/?LinkId=178347) in the MSDN Library.</span></span>|  
|`system.web`|<span data-ttu-id="25bcc-115">ASP.NET 元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-115">ASP.NET element.</span></span> <span data-ttu-id="25bcc-116">有关详细信息，请参阅 MSDN Library 中的 [system.web 元素（ASP.NET 设置架构）](https://go.microsoft.com/fwlink/?LinkId=178348) 。</span><span class="sxs-lookup"><span data-stu-id="25bcc-116">For more information, see [system.web Element (ASP.NET Settings Schema)](https://go.microsoft.com/fwlink/?LinkId=178348) in the MSDN Library.</span></span>|  
|`startup`|<span data-ttu-id="25bcc-117">.NET Framework 元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-117">.NET Framework element.</span></span> <span data-ttu-id="25bcc-118">有关详细信息，请参阅 MSDN Library 中的[ \<startup> 元素](https://go.microsoft.com/fwlink/?LinkId=178349)。</span><span class="sxs-lookup"><span data-stu-id="25bcc-118">For more information, see [\<startup> Element](https://go.microsoft.com/fwlink/?LinkId=178349) in the MSDN Library.</span></span>|  
|`runtime`|<span data-ttu-id="25bcc-119">.NET Framework 元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-119">.NET Framework element.</span></span> <span data-ttu-id="25bcc-120">有关详细信息，请参阅 MSDN Library 中的[ \<runtime> 元素](https://go.microsoft.com/fwlink/?LinkId=178350)。</span><span class="sxs-lookup"><span data-stu-id="25bcc-120">For more information, see [\<runtime> Element](https://go.microsoft.com/fwlink/?LinkId=178350) in the MSDN Library.</span></span>|  
|`system.codedom`|<span data-ttu-id="25bcc-121">.NET Framework 元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-121">.NET Framework element.</span></span> <span data-ttu-id="25bcc-122">有关详细信息，请参阅 MSDN Library 中的[ \<system.codedom> 元素](https://go.microsoft.com/fwlink/?LinkId=178351)。</span><span class="sxs-lookup"><span data-stu-id="25bcc-122">For more information, see [\<system.codedom> Element](https://go.microsoft.com/fwlink/?LinkId=178351) in the MSDN Library.</span></span>|  
|`system.web.extensions`|<span data-ttu-id="25bcc-123">ASP.NET 元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-123">ASP.NET element.</span></span> <span data-ttu-id="25bcc-124">有关详细信息，请参阅 MSDN Library 中的 [system.web.extensions 元素（ASP.NET 设置架构）](https://go.microsoft.com/fwlink/?LinkId=178352) 。</span><span class="sxs-lookup"><span data-stu-id="25bcc-124">For more information, see [system.web.extensions Element (ASP.NET Settings Schema)](https://go.microsoft.com/fwlink/?LinkId=178352) in the MSDN Library.</span></span>|  
|`system.webServer`|<span data-ttu-id="25bcc-125">包含 IIS 元素的节组。</span><span class="sxs-lookup"><span data-stu-id="25bcc-125">Section group that contains IIS elements.</span></span> <span data-ttu-id="25bcc-126">有关详细信息，请参阅 MSDN Library 中的 [system.webServer 节组 \[IIS 7 设置架构\]](https://go.microsoft.com/fwlink/?LinkId=178353)。</span><span class="sxs-lookup"><span data-stu-id="25bcc-126">For more information, see [system.webServer Section Group \[IIS 7 Settings Schema\]](https://go.microsoft.com/fwlink/?LinkId=178353) in the MSDN Library.</span></span>|  
|`system.serviceModel`|<span data-ttu-id="25bcc-127">WCF 元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-127">WCF element.</span></span> <span data-ttu-id="25bcc-128">有关详细信息，请参阅 [\<system.serviceModel>](https://go.microsoft.com/fwlink/?LinkId=178354) MSDN 库中的。</span><span class="sxs-lookup"><span data-stu-id="25bcc-128">For more information, see [\<system.serviceModel>](https://go.microsoft.com/fwlink/?LinkId=178354) in the MSDN Library.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="25bcc-129">.NET Framework 元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-129">.NET Framework element.</span></span> <span data-ttu-id="25bcc-130">有关详细信息，请参阅 MSDN Library 中的[ \<system.diagnostics> 元素](https://go.microsoft.com/fwlink/?LinkId=178355)。</span><span class="sxs-lookup"><span data-stu-id="25bcc-130">For more information, see [\<system.diagnostics> Element](https://go.microsoft.com/fwlink/?LinkId=178355) in the MSDN Library.</span></span>|  
|`appSettings`|<span data-ttu-id="25bcc-131">ASP.NET 元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-131">ASP.NET element.</span></span> <span data-ttu-id="25bcc-132">有关详细信息，请参阅 MSDN Library 中的 [appSettings 元素（常规设置架构）](https://go.microsoft.com/fwlink/?LinkId=178356) 。</span><span class="sxs-lookup"><span data-stu-id="25bcc-132">For more information, see [appSettings Element (General Settings Schema)](https://go.microsoft.com/fwlink/?LinkId=178356) in the MSDN Library.</span></span>|  
  
## <a name="masterdataservices-element"></a><span data-ttu-id="25bcc-133">masterDataServices 元素</span><span class="sxs-lookup"><span data-stu-id="25bcc-133">masterDataServices Element</span></span>  
 <span data-ttu-id="25bcc-134">**\<masterDataServices>** 元素是一个自定义元素，用于将 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web 服务连接到 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="25bcc-134">The **\<masterDataServices>** element is a custom element that is used to connect a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web service to a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
### <a name="syntax"></a><span data-ttu-id="25bcc-135">语法</span><span class="sxs-lookup"><span data-stu-id="25bcc-135">Syntax</span></span>  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a><span data-ttu-id="25bcc-136">元素和属性</span><span class="sxs-lookup"><span data-stu-id="25bcc-136">Elements and Attributes</span></span>  
  
|<span data-ttu-id="25bcc-137">项</span><span class="sxs-lookup"><span data-stu-id="25bcc-137">Item</span></span>|<span data-ttu-id="25bcc-138">说明</span><span class="sxs-lookup"><span data-stu-id="25bcc-138">Description</span></span>|  
|----------|-----------------|  
|`instance`|<span data-ttu-id="25bcc-139">子元素。</span><span class="sxs-lookup"><span data-stu-id="25bcc-139">Child element.</span></span> <span data-ttu-id="25bcc-140">包含指定 Web 服务和数据库连接字符串信息的属性。</span><span class="sxs-lookup"><span data-stu-id="25bcc-140">Contains attributes that specify information for the Web service and database connection string.</span></span>|  
|`virtualPath`|<span data-ttu-id="25bcc-141">属性。</span><span class="sxs-lookup"><span data-stu-id="25bcc-141">Attribute.</span></span> <span data-ttu-id="25bcc-142">指定 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序和服务的虚拟路径。</span><span class="sxs-lookup"><span data-stu-id="25bcc-142">Specifies the virtual path of the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application and service.</span></span> <span data-ttu-id="25bcc-143">这对应于 `path` **\<application>** **\<site>** IIS ApplicationHost.config 文件中元素下的元素的属性。</span><span class="sxs-lookup"><span data-stu-id="25bcc-143">This corresponds to the `path` attribute of the **\<application>** element under the **\<site>** element in the IIS ApplicationHost.config file.</span></span>|  
|`siteName`|<span data-ttu-id="25bcc-144">属性。</span><span class="sxs-lookup"><span data-stu-id="25bcc-144">Attribute.</span></span> <span data-ttu-id="25bcc-145">指定承载 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序和服务的站点的名称。</span><span class="sxs-lookup"><span data-stu-id="25bcc-145">Specifies the name of the site that hosts the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application and service.</span></span> <span data-ttu-id="25bcc-146">这对应于 `name` **\<site>** **\<sites>** IIS ApplicationHost.config 文件中下的元素的属性。</span><span class="sxs-lookup"><span data-stu-id="25bcc-146">This corresponds to the `name` attribute of the **\<site>** element under **\<sites>** in the IIS ApplicationHost.config file.</span></span>|  
|`connectionName`|<span data-ttu-id="25bcc-147">属性。</span><span class="sxs-lookup"><span data-stu-id="25bcc-147">Attribute.</span></span> <span data-ttu-id="25bcc-148">指定要使用的连接的名称。</span><span class="sxs-lookup"><span data-stu-id="25bcc-148">Specifies the name of the connection to use.</span></span> <span data-ttu-id="25bcc-149">这与 `name` **\<add>** Web.config 中元素下的元素的属性相对应 **\<connectionStrings>** 。</span><span class="sxs-lookup"><span data-stu-id="25bcc-149">This corresponds to the `name` attribute of the **\<add>** element under the **\<connectionStrings>** element in Web.config.</span></span>|  
|`serviceName`|<span data-ttu-id="25bcc-150">属性。</span><span class="sxs-lookup"><span data-stu-id="25bcc-150">Attribute.</span></span> <span data-ttu-id="25bcc-151">指定 Web 服务的名称。</span><span class="sxs-lookup"><span data-stu-id="25bcc-151">Specifies the name of the Web service.</span></span> <span data-ttu-id="25bcc-152">这与 `name` **\<service>** Web.config 中元素下的元素的属性相对应 **\<services>** 。</span><span class="sxs-lookup"><span data-stu-id="25bcc-152">This corresponds to the `name` attribute of the **\<service>** element under the **\<services>** element in Web.config.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="25bcc-153">示例</span><span class="sxs-lookup"><span data-stu-id="25bcc-153">Example</span></span>  
 <span data-ttu-id="25bcc-154">下面的示例演示了 Contoso 站点上一个名为 MDS1 的服务和使用由 MDSDB 指定的连接字符串的 /MDS 路径。</span><span class="sxs-lookup"><span data-stu-id="25bcc-154">The following example demonstrates a service named MDS1 on the Contoso site and /MDS path using a connection string specified by MDSDB.</span></span>  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
