---
title: 注册标准 .NET Framework 数据提供程序 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- .NET Framework data providers for Reporting Services
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
ms.assetid: d92add64-e93c-4598-8508-55d1bc46acf6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fd26f9c7fa163d9e6005d42e24c7b1483987f3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687495"
---
# <a name="register-a-standard-net-framework-data-provider-ssrs"></a><span data-ttu-id="aed89-102">注册标准 .NET Framework 数据访问接口 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="aed89-102">Register a Standard .NET Framework Data Provider (SSRS)</span></span>
  <span data-ttu-id="aed89-103">若要使用第三方 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据提供程序检索 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表数据集的数据，需要在以下两个位置部署和注册 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据提供程序程序集：报表创作客户端和报表服务器。</span><span class="sxs-lookup"><span data-stu-id="aed89-103">To use a third-party [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider to retrieve data for a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report dataset, you need to deploy and register the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly in two locations: on the report authoring client and on the report server.</span></span> <span data-ttu-id="aed89-104">在报表创作客户端上，必须将数据访问接口注册为数据源类型并将其与查询设计器相关联。</span><span class="sxs-lookup"><span data-stu-id="aed89-104">On the report authoring client, you must register the data provider as a data source type and associate it with a query designer.</span></span> <span data-ttu-id="aed89-105">然后，可以在创建报表数据集时选择此数据访问接口作为数据源类型。</span><span class="sxs-lookup"><span data-stu-id="aed89-105">You can then select this data provider as a type of data source when you create a report dataset.</span></span> <span data-ttu-id="aed89-106">关联的查询设计器会打开，帮助您为此数据源类型创建查询。</span><span class="sxs-lookup"><span data-stu-id="aed89-106">The associated query designer opens to help you create queries for this data source type.</span></span> <span data-ttu-id="aed89-107">在报表服务器上，必须将该数据访问接口注册为数据源类型。</span><span class="sxs-lookup"><span data-stu-id="aed89-107">On the report server, you must register the data provider as a data source type.</span></span> <span data-ttu-id="aed89-108">然后，可以处理使用此数据访问接口从数据源检索数据的已发布报表。</span><span class="sxs-lookup"><span data-stu-id="aed89-108">You can then process published reports that retrieve data from a data source using this data provider.</span></span>  
  
 <span data-ttu-id="aed89-109">第三方数据提供程序不一定提供 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据处理扩展插件提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="aed89-109">Third-party data providers do not necessarily provide all the functionality available with the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extensions.</span></span> <span data-ttu-id="aed89-110">有关详细信息，请参阅 [Reporting Services 支持的数据源 (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="aed89-110">For more information, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span> <span data-ttu-id="aed89-111">若要了解扩展 .[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aed89-111">To learn about extending the functionality of a .[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]</span></span> <span data-ttu-id="aed89-112">数据提供程序的功能，请参阅 [实现数据处理扩展插件](../extensions/data-processing/implementing-a-data-processing-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="aed89-112">data provider, see [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md).</span></span>  
  
 <span data-ttu-id="aed89-113">安装和注册数据访问接口需要管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="aed89-113">You need administrator credentials to install and register data providers.</span></span>  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-server"></a><span data-ttu-id="aed89-114">在报表服务器上注册 .NET Framework 数据访问接口</span><span class="sxs-lookup"><span data-stu-id="aed89-114">Registering a .NET Framework Data Provider on the Report Server</span></span>  
 <span data-ttu-id="aed89-115">若要在报表服务器上处理使用此 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口的已发布报表，需要在报表服务器上安装其程序集。</span><span class="sxs-lookup"><span data-stu-id="aed89-115">In order to process published reports that use this [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider on the report server, you need to install the assembly on the report server.</span></span> <span data-ttu-id="aed89-116">必须修改两个配置文件。</span><span class="sxs-lookup"><span data-stu-id="aed89-116">You must modify two configuration files.</span></span> <span data-ttu-id="aed89-117">修改 rsreportserver.config 以注册数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="aed89-117">Modify rsreportserver.config to register the data provider.</span></span> <span data-ttu-id="aed89-118">修改 rssrvpolicy.config 以授予对程序集的代码访问安全权限。</span><span class="sxs-lookup"><span data-stu-id="aed89-118">Modify rssrvpolicy.config to grant code access security permissions for the assembly.</span></span>  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-server"></a><span data-ttu-id="aed89-119">在报表服务器上安装数据访问接口程序集</span><span class="sxs-lookup"><span data-stu-id="aed89-119">To install a data provider assembly on the report server</span></span>  
  
1.  <span data-ttu-id="aed89-120">在要在其上使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口的报表服务器上，导航到 bin 目录的默认位置。</span><span class="sxs-lookup"><span data-stu-id="aed89-120">Navigate to the default location of the bin directory on the report server on which you want to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="aed89-121">Report Server 的 bin 目录的默认位置为 *\<drive>* ： \Program Files\Microsoft SQL Server MSRS10_50 \ MSSQLSERVER\Reporting services\reportserver\bin。</span><span class="sxs-lookup"><span data-stu-id="aed89-121">The default location of the report server bin directory is *\<drive>*:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.</span></span>  
  
2.  <span data-ttu-id="aed89-122">将程序集从临时位置复制到报表服务器的 bin 目录中。</span><span class="sxs-lookup"><span data-stu-id="aed89-122">Copy your assembly from your staging location to the bin directory of the report server.</span></span> <span data-ttu-id="aed89-123">也可以选择将程序集加载到全局程序集缓存 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="aed89-123">Alternatively, you can load your assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="aed89-124">有关详细信息，请参阅 MSDN 上的 [SDK 文档中的](https://go.microsoft.com/fwlink/?linkid=63912) Working with Assemblies and the Global Assembly Cache [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] （使用程序集和全局程序集缓存）。</span><span class="sxs-lookup"><span data-stu-id="aed89-124">For more information, see [Working with Assemblies and the Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation on MSDN.</span></span>  
  
#### <a name="to-register-a-net-data-provider-on-the-report-server"></a><span data-ttu-id="aed89-125">在报表服务器上注册 .NET 数据访问接口</span><span class="sxs-lookup"><span data-stu-id="aed89-125">To register a .NET data provider on the report server</span></span>  
  
1.  <span data-ttu-id="aed89-126">在 bin 目录的 ReportServer 父目录中备份 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="aed89-126">Make a backup of the RSReportServer.config file in the ReportServer parent directory for bin.</span></span>  
  
2.  <span data-ttu-id="aed89-127">打开 RSReportServer.config。您可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或诸如记事本之类的简单文本编辑器打开该配置文件。</span><span class="sxs-lookup"><span data-stu-id="aed89-127">Open RSReportServer.config. You can open the configuration file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="aed89-128">在 RSReportServer.config 文件中找到 `Data` 元素。</span><span class="sxs-lookup"><span data-stu-id="aed89-128">Locate the `Data` element in the RSReportServer.config file.</span></span> <span data-ttu-id="aed89-129">应当在以下位置为 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口生成一个条目：</span><span class="sxs-lookup"><span data-stu-id="aed89-129">An entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="aed89-130">添加 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口的条目。</span><span class="sxs-lookup"><span data-stu-id="aed89-130">Add an entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span>  
  
    |<span data-ttu-id="aed89-131">Attribute</span><span class="sxs-lookup"><span data-stu-id="aed89-131">Attribute</span></span>|<span data-ttu-id="aed89-132">说明</span><span class="sxs-lookup"><span data-stu-id="aed89-132">Description</span></span>|  
    |---------------|-----------------|  
    |`Name`|<span data-ttu-id="aed89-133">提供数据访问接口的唯一名称，例如 **MyNETDataProvider**。</span><span class="sxs-lookup"><span data-stu-id="aed89-133">Provide a unique name for the data provider, for example, **MyNETDataProvider**.</span></span> <span data-ttu-id="aed89-134">`Name` 属性的最大长度是 255 个字符。</span><span class="sxs-lookup"><span data-stu-id="aed89-134">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="aed89-135">该名称在配置文件的 `Extension` 元素内的所有条目中必须唯一。</span><span class="sxs-lookup"><span data-stu-id="aed89-135">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="aed89-136">创建新数据源时，此处包含的值显示在数据源类型下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="aed89-136">The value you include here appears in the drop-down list of data source types when you create a new data source.</span></span>|  
    |`Type`|<span data-ttu-id="aed89-137">输入包括实现 <xref:System.Data.IDbConnection> 接口的类的完全限定命名空间在内的逗号分隔的列表，后跟 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据提供程序程序集的名称（不包含 .dll 文件扩展名）。</span><span class="sxs-lookup"><span data-stu-id="aed89-137">Enter a comma-separated list that includes the fully qualified namespace of the class that implements the <xref:System.Data.IDbConnection> interface, followed by the name of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly (not including the .dll file name extension).</span></span>|  
  
     <span data-ttu-id="aed89-138">例如，对于部署到报表服务器的 bin 目录中的 DLL，该条目应如下所示：</span><span class="sxs-lookup"><span data-stu-id="aed89-138">For example, the entry might resemble the following for a DLL deployed to the report server bin directory:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     <span data-ttu-id="aed89-139">如果将程序集加载到全局程序集缓存 (GAC) 中，必须提供强名称属性。</span><span class="sxs-lookup"><span data-stu-id="aed89-139">If you load your assembly into the global assembly cache (GAC), you must provide the strong name properties.</span></span> <span data-ttu-id="aed89-140">例如：</span><span class="sxs-lookup"><span data-stu-id="aed89-140">For example:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly,Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider"></a><span data-ttu-id="aed89-141">设置 .NET 数据访问接口的代码组策略</span><span class="sxs-lookup"><span data-stu-id="aed89-141">To set the code group policy for a .NET data provider</span></span>  
  
1.  <span data-ttu-id="aed89-142">在 bin 目录的 ReportServer 父目录中创建 rssrvpolicy.config 文件的备份副本。</span><span class="sxs-lookup"><span data-stu-id="aed89-142">Make a backup copy of the rssrvpolicy.config file in the ReportServer parent directory for bin.</span></span>  
  
2.  <span data-ttu-id="aed89-143">打开 rssrvpolicy.config。您可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或简单的文本编辑器（如记事本）打开该配置文件。</span><span class="sxs-lookup"><span data-stu-id="aed89-143">Open rssrvpolicy.config. You can open the configuration file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor such as Notepad.</span></span>  
  
3.  <span data-ttu-id="aed89-144">在 rssrvpolicy.config 文件中找到 `CodeGroup` 元素。</span><span class="sxs-lookup"><span data-stu-id="aed89-144">Locate the `CodeGroup` element in the rssrvpolicy.config file.</span></span>  
  
4.  <span data-ttu-id="aed89-145">为数据访问接口程序集添加授予 `FullTrust` 权限的代码组。</span><span class="sxs-lookup"><span data-stu-id="aed89-145">Add a code group for the data provider assembly that grants `FullTrust` permission.</span></span> <span data-ttu-id="aed89-146">该代码组应如下所示：</span><span class="sxs-lookup"><span data-stu-id="aed89-146">Your code group might resemble the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="aed89-147">URL 成员身份仅是您可能为数据访问接口选择的多个成员身份条件之一。</span><span class="sxs-lookup"><span data-stu-id="aed89-147">URL membership is only one of many membership conditions you might select for the data provider.</span></span>  
  
### <a name="verifying-the-deployment-and-registration"></a><span data-ttu-id="aed89-148">验证部署和注册</span><span class="sxs-lookup"><span data-stu-id="aed89-148">Verifying the Deployment and Registration</span></span>  
 <span data-ttu-id="aed89-149">打开报表管理器，然后验证可用数据源列表中是否包含该数据访问接口，从而验证是否已将该数据访问接口成功部署到报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="aed89-149">You can verify whether the data provider was deployed successfully to the report server by opening Report Manager and verifying that the data provider is included in the list of available data sources.</span></span> <span data-ttu-id="aed89-150">有关报表管理器和数据源的详细信息，请参阅[创建、修改和删除共享数据源 (SSRS)](create-modify-and-delete-shared-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="aed89-150">For more information about Report Manager and data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-designer-client"></a><span data-ttu-id="aed89-151">在报表设计器客户端上注册 .NET Framework 数据访问接口</span><span class="sxs-lookup"><span data-stu-id="aed89-151">Registering a .NET Framework Data Provider on the Report Designer Client</span></span>  
 <span data-ttu-id="aed89-152">若要创作使用此 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口作为数据源的报表，必须在运行报表设计器的客户端计算机上安装该程序集。</span><span class="sxs-lookup"><span data-stu-id="aed89-152">In order to author reports that use this [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider for a data source, you must install the assembly on your client computer that runs Report Designer.</span></span> <span data-ttu-id="aed89-153">必须修改两个配置文件。</span><span class="sxs-lookup"><span data-stu-id="aed89-153">You must modify two configuration files.</span></span> <span data-ttu-id="aed89-154">修改 RSReportDesigner.config 以将该数据访问接口注册为数据源，并使用通用查询设计器。</span><span class="sxs-lookup"><span data-stu-id="aed89-154">Modify RSReportDesigner.config to register the data provider as a data source and to use the generic query designer.</span></span> <span data-ttu-id="aed89-155">修改 RSPreviewPolicy.config 以授予对数据访问接口程序集的代码访问安全权限。</span><span class="sxs-lookup"><span data-stu-id="aed89-155">Modify RSPreviewPolicy.config to grant code access security permissions for the data provider assembly.</span></span>  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-designer-client"></a><span data-ttu-id="aed89-156">在报表设计器客户端上安装数据访问接口程序集</span><span class="sxs-lookup"><span data-stu-id="aed89-156">To install a data provider assembly on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="aed89-157">在要在其上使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口的报表设计器客户端上，导航到 PrivateAssemblies 目录的默认位置。</span><span class="sxs-lookup"><span data-stu-id="aed89-157">Navigate to the default location of the PrivateAssemblies directory on the Report Designer client on which you want to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="aed89-158">PrivateAssemblies 目录的默认位置为 *\<drive>* ： \Program Files\Microsoft Visual Studio 9.0 \ common7\ide\privateassemblies。</span><span class="sxs-lookup"><span data-stu-id="aed89-158">The default location of the PrivateAssemblies directory is *\<drive>*:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
2.  <span data-ttu-id="aed89-159">将程序集从临时位置复制到报表设计器客户端的 PrivateAssemblies 目录中。</span><span class="sxs-lookup"><span data-stu-id="aed89-159">Copy your assembly from your staging location to the PrivateAssemblies directory of the Report Designer client.</span></span> <span data-ttu-id="aed89-160">也可以选择将程序集加载到全局程序集缓存 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="aed89-160">Alternatively, you can load your assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="aed89-161">有关详细信息，请参阅 MSDN 上的 [SDK 文档中的](https://go.microsoft.com/fwlink/?linkid=63912) Working with Assemblies and the Global Assembly Cache [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] （使用程序集和全局程序集缓存）。</span><span class="sxs-lookup"><span data-stu-id="aed89-161">For more information, see [Working with Assemblies and the Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation on MSDN.</span></span>  
  
#### <a name="to-register-a-net-data-provider-on-the-report-designer-client"></a><span data-ttu-id="aed89-162">在报表设计器客户端上注册 .NET 数据访问接口</span><span class="sxs-lookup"><span data-stu-id="aed89-162">To register a .NET data provider on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="aed89-163">在 PrivateAssemblies 目录中创建 RSReportDesigner.config 文件的备份副本。</span><span class="sxs-lookup"><span data-stu-id="aed89-163">Make a backup copy of the RSReportDesigner.config file in the PrivateAssemblies directory.</span></span>  
  
2.  <span data-ttu-id="aed89-164">使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或诸如记事本之类的简单文本编辑器打开 RSReportDesigner.config。</span><span class="sxs-lookup"><span data-stu-id="aed89-164">Open RSReportDesigner.config with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor such as Notepad.</span></span>  
  
3.  <span data-ttu-id="aed89-165">在 RSReportDesigner.config 文件中找到 `Data` 元素。</span><span class="sxs-lookup"><span data-stu-id="aed89-165">Locate the `Data` element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="aed89-166">应当在以下位置为该数据访问接口生成一个条目：</span><span class="sxs-lookup"><span data-stu-id="aed89-166">An entry for the data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="aed89-167">添加该数据访问接口的条目。</span><span class="sxs-lookup"><span data-stu-id="aed89-167">Add an entry for the data provider.</span></span>  
  
    |<span data-ttu-id="aed89-168">Attribute</span><span class="sxs-lookup"><span data-stu-id="aed89-168">Attribute</span></span>|<span data-ttu-id="aed89-169">说明</span><span class="sxs-lookup"><span data-stu-id="aed89-169">Description</span></span>|  
    |---------------|-----------------|  
    |`Name`|<span data-ttu-id="aed89-170">提供数据访问接口的唯一名称，例如 **MyNETDataProvider**。</span><span class="sxs-lookup"><span data-stu-id="aed89-170">Provide a unique name for the data provider, for example, **MyNETDataProvider**.</span></span> <span data-ttu-id="aed89-171">`Name` 属性的最大长度是 255 个字符。</span><span class="sxs-lookup"><span data-stu-id="aed89-171">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="aed89-172">该名称在配置文件的 `Extension` 元素内的所有条目中必须唯一。</span><span class="sxs-lookup"><span data-stu-id="aed89-172">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="aed89-173">创建新数据源时，在此处包含的值显示在数据源类型下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="aed89-173">The value that you include here appears in the drop-down list of data source types when you create a new data source.</span></span>|  
    |`Type`|<span data-ttu-id="aed89-174">输入包括实现 <xref:System.Data.IDbConnection> 接口的类的完全限定命名空间在内的逗号分隔的列表，后跟 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据提供程序程序集的名称（不包含 .dll 文件扩展名）。</span><span class="sxs-lookup"><span data-stu-id="aed89-174">Enter a comma-separated list that includes the fully qualified namespace of the class that implements the <xref:System.Data.IDbConnection> interface, followed by the name of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly (not including the .dll file name extension).</span></span>|  
  
     <span data-ttu-id="aed89-175">例如，对于部署到 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的 PrivateAssemblies 目录中的 DLL，该条目应如下所示：</span><span class="sxs-lookup"><span data-stu-id="aed89-175">For example, the entry might resemble the following for a DLL deployed to the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] PrivateAssemblies directory:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     <span data-ttu-id="aed89-176">如果将程序集加载到 GAC 中，必须提供强名称属性。</span><span class="sxs-lookup"><span data-stu-id="aed89-176">If you load your assembly into the GAC, you must provide the strong name properties.</span></span> <span data-ttu-id="aed89-177">例如：</span><span class="sxs-lookup"><span data-stu-id="aed89-177">For example:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
5.  <span data-ttu-id="aed89-178">在 RSReportDesigner.config 文件中找到 `Designer` 元素。</span><span class="sxs-lookup"><span data-stu-id="aed89-178">Locate the `Designer` element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="aed89-179">应当在以下位置为 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口生成一个条目：</span><span class="sxs-lookup"><span data-stu-id="aed89-179">An entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Designer>  
          <Your data provider configuration information goes here>  
       </Designer>  
    </Extensions>  
    ```  
  
6.  <span data-ttu-id="aed89-180">将以下条目添加到 RSReportDesigner.config 文件中的 `Designer` 元素下。</span><span class="sxs-lookup"><span data-stu-id="aed89-180">Add the following entry to the RSReportDesigner.config file under the `Designer` element.</span></span> <span data-ttu-id="aed89-181">您只需要使用在以前的条目中提供的名称替换 `Name` 属性。</span><span class="sxs-lookup"><span data-stu-id="aed89-181">You need to replace only the `Name` attribute with the name that you provided in previous entries.</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider-on-the-report-designer-client"></a><span data-ttu-id="aed89-182">在报表设计器客户端上设置 .NET 数据访问接口的代码组策略</span><span class="sxs-lookup"><span data-stu-id="aed89-182">To set the code group policy for a .NET data provider on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="aed89-183">在 PrivateAssemblies 目录中创建 RSPreviewPolicy.config 文件的备份副本。</span><span class="sxs-lookup"><span data-stu-id="aed89-183">Make a backup copy of the RSPreviewPolicy.config file in the PrivateAssemblies directory.</span></span>  
  
2.  <span data-ttu-id="aed89-184">使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或诸如记事本之类的简单的文本编辑器打开 RSPreviewPolicy.config。</span><span class="sxs-lookup"><span data-stu-id="aed89-184">Open RSPreviewPolicy.config with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="aed89-185">在 RSPreviewPolicy.config 文件中找到 `CodeGroup` 元素。</span><span class="sxs-lookup"><span data-stu-id="aed89-185">Locate the `CodeGroup` element in the RSPreviewPolicy.config file.</span></span>  
  
4.  <span data-ttu-id="aed89-186">为 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口程序集添加授予 `FullTrust` 权限的代码组。</span><span class="sxs-lookup"><span data-stu-id="aed89-186">Add a code group for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly that grants `FullTrust` permission.</span></span> <span data-ttu-id="aed89-187">该代码组应如下所示：</span><span class="sxs-lookup"><span data-stu-id="aed89-187">Your code group might resemble the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    " C:\Program Files\Microsoft Visual Studio 9\Common7\IDE\PrivateAssemblies\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="aed89-188">URL 成员身份仅是您可能为数据访问接口选择的多个成员身份条件之一。</span><span class="sxs-lookup"><span data-stu-id="aed89-188">URL membership is only one of many membership conditions you might select for the data provider.</span></span>  
  
### <a name="verifying-the-deployment-and-registration-on-the-report-designer-client"></a><span data-ttu-id="aed89-189">在报表设计器客户端上验证部署和注册</span><span class="sxs-lookup"><span data-stu-id="aed89-189">Verifying the Deployment and Registration on the Report Designer Client</span></span>  
 <span data-ttu-id="aed89-190">必须先关闭本地计算机上的所有 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 实例，然后才能验证部署。</span><span class="sxs-lookup"><span data-stu-id="aed89-190">Before you can verify deployment, you must close all instances of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] on your local computer.</span></span> <span data-ttu-id="aed89-191">结束所有当前会话之后，可以在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]中创建一个新报表项目，以验证数据访问接口是否已成功部署到报表设计器。</span><span class="sxs-lookup"><span data-stu-id="aed89-191">After you have ended all current sessions, you can verify whether your data provider was deployed successfully to Report Designer by creating a new report project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="aed89-192">为报表创建新的数据集时，该数据访问接口应当包含在可用数据源类型列表中。</span><span class="sxs-lookup"><span data-stu-id="aed89-192">The data provider should be included in the list of available data source types when you create a new data set for your report.</span></span>  
  
## <a name="platform-considerations"></a><span data-ttu-id="aed89-193">平台注意事项</span><span class="sxs-lookup"><span data-stu-id="aed89-193">Platform Considerations</span></span>  
 <span data-ttu-id="aed89-194">在 64 位 (x64) 平台上， [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 在 32 位 WOW 模式下运行。</span><span class="sxs-lookup"><span data-stu-id="aed89-194">On a 64-bit (x64) platform, [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] runs in 32-bit WOW mode.</span></span> <span data-ttu-id="aed89-195">在 x64 平台上创作报表时，需要在报表创作客户端上安装 32 位数据访问接口，以便预览报表。</span><span class="sxs-lookup"><span data-stu-id="aed89-195">When you author reports on an x64 platform, you need 32-bit data providers installed on the report authoring client in order to preview your reports.</span></span> <span data-ttu-id="aed89-196">如果在同一系统上发布报表，则需要 x64 数据访问接口，以便使用报表管理器查看报表。</span><span class="sxs-lookup"><span data-stu-id="aed89-196">If you publish the report on the same system, you need x64 data providers to view the report with Report Manager.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="aed89-197">不受基于 [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]的平台支持。</span><span class="sxs-lookup"><span data-stu-id="aed89-197">is not supported for [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-based platforms.</span></span>  
  
 <span data-ttu-id="aed89-198">必须在每个平台上对随 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装的数据处理扩展插件进行本机编译，然后将其安装在正确位置。</span><span class="sxs-lookup"><span data-stu-id="aed89-198">The data processing extensions that are installed with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] must be compiled natively for each platform and installed in the correct locations.</span></span> <span data-ttu-id="aed89-199">如果注册自定义数据访问接口或标准 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口，则需要在对应平台上对其进行本机编译，然后将其安装在相应位置。</span><span class="sxs-lookup"><span data-stu-id="aed89-199">If you register a custom data provider or a standard [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider, it needs to be compiled natively for the appropriate platform and installed the appropriate locations.</span></span> <span data-ttu-id="aed89-200">如果在 32 位平台上运行，则必须为此 32 位平台编译数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="aed89-200">If you are running on a 32-bit platform, the data provider must be compiled for a 32-bit platform.</span></span> <span data-ttu-id="aed89-201">如果在 64 位平台上运行，则必须为此 64 位平台编译数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="aed89-201">If you are running on a 64-bit platform, the data provider must be compiled for the 64-bit platform.</span></span> <span data-ttu-id="aed89-202">不能在 64 位平台上使用采用 64 位接口包装的 32 位数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="aed89-202">You cannot use a 32-bit data provider wrapped with 64-bit interfaces on a 64 bit platform.</span></span> <span data-ttu-id="aed89-203">有关数据访问接口是否可在所安装平台上工作的信息，请查看您的第三方软件。</span><span class="sxs-lookup"><span data-stu-id="aed89-203">Check your third-party software for information about whether the data provider will work on the installed platform.</span></span> <span data-ttu-id="aed89-204">有关数据提供程序和平台支持的详细信息，请参阅 [Reporting Services 支持的数据源 (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="aed89-204">For more information about data providers and platform support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed89-205">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aed89-205">See Also</span></span>  
 <span data-ttu-id="aed89-206">[配置和管理报表服务器（SSRS 本机模式）](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="aed89-206">[Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="aed89-207">[实现数据处理扩展插件](../extensions/data-processing/implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="aed89-207">[Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="aed89-208">[Reporting Services 配置文件](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="aed89-208">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="aed89-209">Reporting Services 中的代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="aed89-209">Code Access Security in Reporting Services</span></span>](../extensions/secure-development/code-access-security-in-reporting-services.md)  
  
  
