---
title: 部署传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4a4e33266c8d3a27ce2a4ab5f568bdee349720f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591789"
---
# <a name="deploying-a-delivery-extension"></a><span data-ttu-id="0cb9b-102">部署传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="0cb9b-102">Deploying a Delivery Extension</span></span>
  <span data-ttu-id="0cb9b-103">传递扩展插件以 XML 配置文件的形式提供其配置信息。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-103">Delivery extensions supply their configuration information in the form of an XML configuration file.</span></span> <span data-ttu-id="0cb9b-104">该 XML 文件符合为传递扩展插件定义的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-104">The XML file conforms to the XML schema defined for delivery extensions.</span></span> <span data-ttu-id="0cb9b-105">传递扩展插件提供用于设置和修改配置文件的基础结构。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-105">Delivery extensions provide infrastructure for setting and modifying the configuration file.</span></span>  
  
 <span data-ttu-id="0cb9b-106">如果替换或升级某一传递扩展插件，则引用该传递扩展插件的所有订阅仍保持有效。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-106">If a delivery extension is replaced or upgraded, all subscriptions that reference the delivery extension remain valid.</span></span>  
  
 <span data-ttu-id="0cb9b-107">在将 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件写入和编译到某一 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 库中后，必须将该扩展插件复制到相应的目录中，并且向适当的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配置文件添加一个条目，以便报表服务器可以定位它。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-107">After you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension into a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you must copy the extension to the appropriate directory and add an entry to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration file so the report server can locate it.</span></span>  
  
## <a name="configuration-file-extension-element"></a><span data-ttu-id="0cb9b-108">配置文件扩展插件元素</span><span class="sxs-lookup"><span data-stu-id="0cb9b-108">Configuration-File Extension Element</span></span>  
 <span data-ttu-id="0cb9b-109">您部署到报表服务器的传递扩展插件需要作为配置文件中的 `Extension` 元素输入。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-109">Delivery extensions that you deploy to the report server need to be entered as `Extension` elements in the configuration file.</span></span> <span data-ttu-id="0cb9b-110">用于报表服务器的配置文件是 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-110">The configuration file for the report server is RSReportServer.config.</span></span>  
  
 <span data-ttu-id="0cb9b-111">下表介绍传递扩展插件的 `Extension` 元素的属性。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-111">The following table describes the attributes for the `Extension` element for delivery extensions.</span></span>  
  
|<span data-ttu-id="0cb9b-112">Attribute</span><span class="sxs-lookup"><span data-stu-id="0cb9b-112">Attribute</span></span>|<span data-ttu-id="0cb9b-113">说明</span><span class="sxs-lookup"><span data-stu-id="0cb9b-113">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="0cb9b-114">扩展插件的唯一名称（例如，“Report Server E-Mail”用于电子邮件传递扩展插件，“Report Server FileShare”用于文件共享传递扩展插件）。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-114">A unique name for the extension (for example, "Report Server E-Mail" for the e-mail delivery extension or "Report Server FileShare" for the file share delivery extension).</span></span> <span data-ttu-id="0cb9b-115">`Name` 属性的最大长度是 255 个字符。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-115">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="0cb9b-116">该名称在配置文件的 `Extension` 元素内的所有条目中必须唯一。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-116">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="0cb9b-117">如果存在重复的名称，则报表服务器返回错误。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-117">If a duplicate name is present, the report server returns an error.</span></span>|  
|`Type`|<span data-ttu-id="0cb9b-118">以逗号分隔的列表，其中包含完全限定的命名空间以及程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-118">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|`Visible`|<span data-ttu-id="0cb9b-119">值为 `false` 指示在用户界面中将不显示传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-119">A value of `false` indicates that the delivery extension should not be visible in user interfaces.</span></span> <span data-ttu-id="0cb9b-120">如果未包含此属性，则默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-120">If the attribute is not included, the default value is `true`.</span></span>|  
  
 <span data-ttu-id="0cb9b-121">有关 RSReportServer.config 文件的详细信息，请参阅 [Reporting Services 配置文件](../../report-server/reporting-services-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-121">For more information about the RSReportServer.config file, see [Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md).</span></span>  
  
## <a name="deploying-the-extension-to-the-report-server"></a><span data-ttu-id="0cb9b-122">将扩展插件部署到报表服务器</span><span class="sxs-lookup"><span data-stu-id="0cb9b-122">Deploying the Extension to the Report Server</span></span>  
 <span data-ttu-id="0cb9b-123">报表服务器使用传递扩展插件处理和传递通知或报表。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-123">The report server uses delivery extensions for processing and delivering notifications or reports.</span></span> <span data-ttu-id="0cb9b-124">您应将传递扩展插件程序集作为专用程序集部署到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-124">You should deploy your delivery extension assembly to the report server as a private assembly.</span></span> <span data-ttu-id="0cb9b-125">还需要在报表服务器配置文件 RSReportServer.config 中生成一个条目。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-125">You also need to make an entry in the report server configuration file, RSReportServer.config.</span></span>  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a><span data-ttu-id="0cb9b-126">将传递扩展插件程序集部署到报表服务器</span><span class="sxs-lookup"><span data-stu-id="0cb9b-126">To deploy a deliver extension assembly to a report server</span></span>  
  
1.  <span data-ttu-id="0cb9b-127">将程序集从临时位置复制到您要在其上使用此传递扩展插件的报表服务器的 bin 目录中。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-127">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the delivery extension.</span></span> <span data-ttu-id="0cb9b-128">Report Server bin 目录的默认位置为 "%ProgramFiles%\Microsoft SQL Server \ MSRS10_50"。 \<InstanceName>\Reporting Services\reportserver\bin。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-128">The default location of the report server bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer\bin.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0cb9b-129">如果您在尝试覆盖现有传递扩展插件程序集，则必须首先停止报表服务器服务，然后复制更新的程序集。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-129">If you are attempting to overwrite an existing delivery extension assembly, you must first stop the Report Server service before copying the updated assembly.</span></span> <span data-ttu-id="0cb9b-130">在复制程序集后重新启动您的服务。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-130">Restart your service after the assembly is through copying.</span></span>  
  
2.  <span data-ttu-id="0cb9b-131">在复制程序集文件后，打开 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-131">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="0cb9b-132">RSReportServer.config 文件位于%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 中。 \<InstanceName>\Reporting Services\ReportServer 目录。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-132">The RSReportServer.config file is located in the %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer directory.</span></span> <span data-ttu-id="0cb9b-133">还需要在配置文件中为传递扩展插件程序集文件生成一个条目。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-133">You need to make an entry in the configuration file for your delivery extension assembly file.</span></span> <span data-ttu-id="0cb9b-134">您可以使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或简单的文本编辑器（如记事本）打开该配置文件。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-134">You can open the configuration file with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="0cb9b-135">在 RSReportServer.config 文件中找到 `Delivery` 元素。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-135">Locate the `Delivery` element in the RSReportServer.config file.</span></span> <span data-ttu-id="0cb9b-136">应当在以下位置为新创建的传递扩展插件生成一个条目：</span><span class="sxs-lookup"><span data-stu-id="0cb9b-136">An entry for your newly created delivery extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="0cb9b-137">为您的传递扩展插件添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-137">Add an entry for your delivery extension.</span></span> <span data-ttu-id="0cb9b-138">您的条目应包括具有用于 `Extension` 和 `Name` 的值的 `Type` 元素，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cb9b-138">Your entry should include an `Extension` element with values for `Name` and `Type`, and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="0cb9b-139">`Name` 的值是传递扩展插件的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-139">The value for `Name` is the unique name of the delivery extension.</span></span> <span data-ttu-id="0cb9b-140">`Type` 的值是逗号分隔的列表，包括实现 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 接口的类的完全限定命名空间的条目，后随程序集的名称（不包括 .dll 文件扩展名）。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-140">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="0cb9b-141">默认情况下，传递扩展插件是可见的。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-141">By default, delivery extensions are visible.</span></span> <span data-ttu-id="0cb9b-142">若要在用户界面（如报表管理器）中隐藏扩展插件，请将 `Visible` 属性添加到 `Extension` 元素，并将其设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-142">To hide an extension from user interfaces, such as Report Manager, add a `Visible` attribute to the `Extension` element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="0cb9b-143">最后，为您的自定义程序集添加一个代码组，以便为您的传递扩展插件授予 `FullTrust` 权限。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-143">Finally, add a code group for your custom assembly that grants `FullTrust` permission for your delivery extension.</span></span> <span data-ttu-id="0cb9b-144">为此，需要将代码组添加到%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 中默认位于 rssrvpolicy.config 文件中。 \<InstanceName>\Reporting Services\reportserver。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-144">You do this by adding the code group to the rssrvpolicy.config file located by default in %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="0cb9b-145">代码组可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cb9b-145">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     <span data-ttu-id="0cb9b-146">URL 成员身份仅是您可能为传递扩展插件选择的多个成员身份条件之一。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-146">URL membership is only one of many membership conditions you might choose for your delivery extension.</span></span> <span data-ttu-id="0cb9b-147">有关 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 中的代码访问安全性的详细信息，请参阅[安全开发 (Reporting Services)](../secure-development/secure-development-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="0cb9b-147">For more information about code access security in [!INCLUDE[ssRS](../../../includes/ssrs.md)], see.[Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="deploying-the-extension-to-report-manager"></a><span data-ttu-id="0cb9b-148">将扩展插件部署到报表管理器</span><span class="sxs-lookup"><span data-stu-id="0cb9b-148">Deploying the Extension to Report Manager</span></span>  
 <span data-ttu-id="0cb9b-149">如果您的传递扩展插件实现 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> 接口，则该传递扩展插件可用于报表管理器订阅页。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-149">If your delivery extension implements the <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> interface, your delivery extension can be used with the Report Manager Subscription page.</span></span> <span data-ttu-id="0cb9b-150">为了使该订阅用户界面可用，需要将扩展插件部署到报表管理器。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-150">To make the subscription user interface available, you need to deploy your extension to Report Manager.</span></span>  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a><span data-ttu-id="0cb9b-151">将传递扩展插件程序集部署到报表管理器</span><span class="sxs-lookup"><span data-stu-id="0cb9b-151">To deploy a deliver extension assembly to Report Manager</span></span>  
  
1.  <span data-ttu-id="0cb9b-152">将程序集从临时位置复制到报表管理器的 bin 目录中。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-152">Copy your assembly from your staging location to the bin directory of Report Manager.</span></span> <span data-ttu-id="0cb9b-153">报表管理器 bin 目录的默认位置为 "%ProgramFiles%\Microsoft SQL Server \ MSRS10_50"。 \<InstanceName>\Reporting Services\reportmanager\bin。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-153">The default location of the Report Manager bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportManager\bin.</span></span>  
  
2.  <span data-ttu-id="0cb9b-154">在复制程序集文件后，打开 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-154">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="0cb9b-155">RSReportServer.config 文件位于%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 中。 \<InstanceName>\Reporting Services\ReportServer 目录。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-155">The RSReportServer.config file is located in the %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer directory.</span></span> <span data-ttu-id="0cb9b-156">还需要在配置文件中为传递扩展插件程序集文件生成一个条目。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-156">You need to make an entry in the configuration file for your delivery extension assembly file.</span></span> <span data-ttu-id="0cb9b-157">您可以使用 Visual Studio .NET 或诸如记事本之类的简单文本编辑器打开此配置文件。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-157">You can open the configuration file with Visual Studio .NET or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="0cb9b-158">在 RSReportServer.config 文件中找到 `DeliveryUI` 元素。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-158">Locate the `DeliveryUI` element in the RSReportServer.config file.</span></span> <span data-ttu-id="0cb9b-159">应当在以下位置为新创建的传递扩展插件生成一个条目：</span><span class="sxs-lookup"><span data-stu-id="0cb9b-159">An entry for your newly created delivery extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="0cb9b-160">为您的传递扩展插件添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-160">Add an entry for your delivery extension.</span></span> <span data-ttu-id="0cb9b-161">条目应包括具有 `Extension` 和 `Name` 的值的 `Type` 元素，可能类似如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cb9b-161">Your entry should include an `Extension` element with values for `Name` and `Type` and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="0cb9b-162">`Name` 的值是传递扩展插件的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-162">The value for `Name` is the unique name of the delivery extension.</span></span> <span data-ttu-id="0cb9b-163">`Type` 的值是逗号分隔的列表，包括实现 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> 接口的类的完全限定命名空间的条目，后随程序集的名称（不包括 .dll 文件扩展名）。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-163">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> interface, followed by the name of your assembly (not including the .dll file extension).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0cb9b-164">对于报表服务器和报表管理器配置文件条目，`Name` 属性的值必须相同。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-164">The value of the `Name` attribute must be identical for both the Report Server and Report Manager configuration file entries.</span></span> <span data-ttu-id="0cb9b-165">如果它们不同，则您的服务器配置将无效。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-165">If they are not identical, your server configuration is not valid.</span></span>  
  
     <span data-ttu-id="0cb9b-166">最后，为您的自定义程序集添加一个代码组，以便为您的传递扩展插件授予 `FullTrust` 权限。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-166">Finally, add a code group for your custom assembly that grants `FullTrust` permission for your delivery extension.</span></span> <span data-ttu-id="0cb9b-167">为此，需要将代码组添加到默认位于 C:\Program Files\Microsoft SQL Server \ MSRS10_50 的 RSmgrpolicy.config 文件中。 \<InstanceName>\Reporting Services\reportmanager。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-167">You do this by adding the code group to the RSmgrpolicy.config file located by default in C:\Program Files\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportManager.</span></span> <span data-ttu-id="0cb9b-168">代码组可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cb9b-168">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     <span data-ttu-id="0cb9b-169">URL 成员身份仅是您可能为传递扩展插件选择的多个成员身份条件之一。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-169">URL membership is only one of many membership conditions you might choose for your delivery extension.</span></span> <span data-ttu-id="0cb9b-170">有关中的代码访问安全性的详细信息 [!INCLUDE[ssRS](../../../includes/ssrs.md)] ，请参阅[安全开发 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="0cb9b-170">For more information about code access security in [!INCLUDE[ssRS](../../../includes/ssrs.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="0cb9b-171">验证部署</span><span class="sxs-lookup"><span data-stu-id="0cb9b-171">Verifying the Deployment</span></span>  
 <span data-ttu-id="0cb9b-172">您可以使用 Web 服务 <xref:ReportService2010.ReportingService2010.ListExtensions%2A> 方法，验证是否已向报表服务器成功地部署了传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-172">You can verify whether your delivery extension was deployed successfully to the report server by using the Web service <xref:ReportService2010.ReportingService2010.ListExtensions%2A> method.</span></span> <span data-ttu-id="0cb9b-173">还可以打开报表管理器，并验证您的扩展插件是否包括在用于订阅的可用传递扩展插件列表中。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-173">You can also open Report Manager and verify that your extension is included in the list of available delivery extensions for a subscription.</span></span> <span data-ttu-id="0cb9b-174">有关报表管理器和订阅的详细信息，请参阅[订阅和传递 &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb9b-174">For more information about Report Manager and subscriptions, see [Subscriptions and Delivery &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb9b-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cb9b-175">See Also</span></span>  
 <span data-ttu-id="0cb9b-176">[实现传递扩展插件](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="0cb9b-176">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="0cb9b-177">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="0cb9b-177">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
