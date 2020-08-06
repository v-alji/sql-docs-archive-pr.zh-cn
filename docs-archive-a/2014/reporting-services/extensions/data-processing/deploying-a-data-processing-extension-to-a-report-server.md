---
title: 如何：向报表服务器部署数据处理扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d606096b9f2060d3cf5b9cea1f95a5345e592383
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693645"
---
# <a name="how-to-deploy-a-data-processing-extension-to-a-report-server"></a><span data-ttu-id="26869-102">如何：向报表服务器部署数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="26869-102">How to: Deploy a Data Processing Extension to a Report Server</span></span>
  <span data-ttu-id="26869-103">报表服务器使用数据处理扩展插件来检索和处理所呈现报表中的数据。</span><span class="sxs-lookup"><span data-stu-id="26869-103">Report servers use data processing extensions for retrieving and processing data in rendered reports.</span></span> <span data-ttu-id="26869-104">您应将数据处理扩展插件程序集作为私有程序集部署到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="26869-104">You should deploy your data processing extension assembly to a report server as a private assembly.</span></span> <span data-ttu-id="26869-105">还需要在报表服务器配置文件 RSReportServer.config 中生成一个条目。</span><span class="sxs-lookup"><span data-stu-id="26869-105">You also need to make an entry in the report server configuration file, RSReportServer.config.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="26869-106">过程</span><span class="sxs-lookup"><span data-stu-id="26869-106">Procedures</span></span>  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a><span data-ttu-id="26869-107">部署数据处理扩展插件程序集</span><span class="sxs-lookup"><span data-stu-id="26869-107">To deploy a data processing extension assembly</span></span>  
  
1.  <span data-ttu-id="26869-108">将程序集从临时位置复制到您要在其上使用数据处理扩展插件的报表服务器的 bin 目录中。</span><span class="sxs-lookup"><span data-stu-id="26869-108">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the data processing extension.</span></span> <span data-ttu-id="26869-109">Report Server bin 目录的默认位置为 "%ProgramFiles%\Microsoft SQL Server \ MSRS10_50"。 \<*Instance Name*>\Reporting Services\reportserver\bin。</span><span class="sxs-lookup"><span data-stu-id="26869-109">The default location of the report server bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer\bin.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="26869-110">此步骤会妨碍升级到较新的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="26869-110">This step will prevent an upgrade to a newer instance of SQL Server.</span></span> <span data-ttu-id="26869-111">有关详细信息，请参阅 [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="26869-111">For more information, see [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
2.  <span data-ttu-id="26869-112">在复制程序集文件后，打开 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="26869-112">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="26869-113">RSReportServer.config 文件位于 ReportServer 目录中。</span><span class="sxs-lookup"><span data-stu-id="26869-113">The RSReportServer.config file is located in the ReportServer directory.</span></span> <span data-ttu-id="26869-114">还需要在配置文件中为数据处理扩展插件程序集文件生成一个条目。</span><span class="sxs-lookup"><span data-stu-id="26869-114">You need to make an entry in the configuration file for your data processing extension assembly file.</span></span> <span data-ttu-id="26869-115">可以使用 Visual Studio 或诸如记事本之类的简单文本编辑器打开此配置文件。</span><span class="sxs-lookup"><span data-stu-id="26869-115">You can open the configuration file with Visual Studio or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="26869-116">在 RSReportServer.config 文件中找到 `Data` 元素。</span><span class="sxs-lookup"><span data-stu-id="26869-116">Locate the `Data` element in the RSReportServer.config file.</span></span> <span data-ttu-id="26869-117">应当在以下位置为新创建的数据处理扩展插件生成一个条目：</span><span class="sxs-lookup"><span data-stu-id="26869-117">An entry for your newly created data processing extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="26869-118">为数据处理扩展插件添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="26869-118">Add an entry for your data processing extension.</span></span> <span data-ttu-id="26869-119">条目应包括具有 `Extension` 和 `Name` 的值的 `Type` 元素，可能类似如下所示：</span><span class="sxs-lookup"><span data-stu-id="26869-119">Your entry should include an `Extension` element with values for `Name` and `Type` and might look like the following:</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     <span data-ttu-id="26869-120">`Name` 的值为数据处理扩展插件的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="26869-120">The value for `Name` is the unique name of the data processing extension.</span></span> <span data-ttu-id="26869-121">`Type` 的值是以逗号分隔的列表，包括实现 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 和 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 接口的类的完全限定命名空间的条目，后跟程序集的名称（不包括 .dll 文件扩展名）。</span><span class="sxs-lookup"><span data-stu-id="26869-121">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IExtension> and <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfaces, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="26869-122">默认情况下，数据处理扩展插件是可见的。</span><span class="sxs-lookup"><span data-stu-id="26869-122">By default, data processing extensions are visible.</span></span> <span data-ttu-id="26869-123">若要在用户界面（如报表管理器）中隐藏扩展插件，请将 `Visible` 属性添加到 `Extension` 元素，并将其设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="26869-123">To hide an extension from user interfaces, such as Report Manager, add a `Visible` attribute to the `Extension` element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="26869-124">为自定义程序集添加一个用于向扩展插件授予 `FullTrust` 权限的代码组。</span><span class="sxs-lookup"><span data-stu-id="26869-124">Add a code group for your custom assembly that grants `FullTrust` permission for your extension.</span></span> <span data-ttu-id="26869-125">为此，需要将代码组添加到%ProgramFiles%\Microsoft SQL Server<MSRS10_50 中默认位于 rssrvpolicy.config 文件中 \\ 。 \<*Instance Name*>\Reporting Services\reportserver。</span><span class="sxs-lookup"><span data-stu-id="26869-125">You do this by adding the code group to the rssrvpolicy.config file located by default in %ProgramFiles%\Microsoft SQL Server\\<MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="26869-126">代码组可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="26869-126">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="26869-127">URL 成员身份只是您可以为数据处理扩展插件选择的众多成员条件之一。</span><span class="sxs-lookup"><span data-stu-id="26869-127">URL membership is only one of many membership conditions you might choose for your data processing extension.</span></span> <span data-ttu-id="26869-128">有关 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的代码访问安全性的详细信息，请参阅[安全开发 (Reporting Services)](../secure-development/secure-development-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="26869-128">For more information about code access security in [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md).</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="26869-129">验证部署</span><span class="sxs-lookup"><span data-stu-id="26869-129">Verifying the Deployment</span></span>  
 <span data-ttu-id="26869-130">您可以使用 Web 服务 <xref:ReportService2010.ReportingService2010.ListExtensions%2A> 方法来验证是否已将数据处理扩展插件成功部署到报表服务器中。</span><span class="sxs-lookup"><span data-stu-id="26869-130">You can verify whether your data processing extension was deployed successfully to the report server by using the Web service <xref:ReportService2010.ReportingService2010.ListExtensions%2A> method.</span></span> <span data-ttu-id="26869-131">您也可以打开报表管理器，验证扩展插件是否包括在可用数据源列表中。</span><span class="sxs-lookup"><span data-stu-id="26869-131">You can also open Report Manager and verify that your extension is included in the list of available data sources.</span></span> <span data-ttu-id="26869-132">有关报表管理器和数据源的详细信息，请参阅[创建、修改和删除共享数据源 (SSRS)](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="26869-132">For more information about Report Manager and data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26869-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26869-133">See Also</span></span>  
 <span data-ttu-id="26869-134">[部署数据处理扩展插件](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="26869-134">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="26869-135">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="26869-135">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="26869-136">[实现数据处理扩展插件](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="26869-136">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="26869-137">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="26869-137">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
