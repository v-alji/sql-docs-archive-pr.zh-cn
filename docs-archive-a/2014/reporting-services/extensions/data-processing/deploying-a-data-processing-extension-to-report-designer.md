---
title: 如何向报表设计器部署数据处理扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: 3614e601-004e-4a16-8388-836ffd67e9dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56bd56e9d8eeeeff1781f22b42cf0eb1ce706fa4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693637"
---
# <a name="how-to-deploy-a-data-processing-extension-to-report-designer"></a><span data-ttu-id="4d8f9-102">如何：向报表设计器部署数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="4d8f9-102">How to: Deploy a Data Processing Extension to Report Designer</span></span>
  <span data-ttu-id="4d8f9-103">报表设计器在您设计报表时使用数据处理扩展插件检索和处理数据。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-103">Report Designer uses data processing extensions for retrieving and processing data while you are designing reports.</span></span> <span data-ttu-id="4d8f9-104">您应将数据处理扩展插件程序集作为专用程序集部署到报表设计器。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-104">You should deploy your data processing extension assembly to Report Designer as a private assembly.</span></span> <span data-ttu-id="4d8f9-105">还需要在报表设计器配置文件 RSReportDesigner.config 中生成一个条目。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-105">You also need to make an entry in the Report Designer configuration file, RSReportDesigner.config.</span></span>  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a><span data-ttu-id="4d8f9-106">部署数据处理扩展插件程序集</span><span class="sxs-lookup"><span data-stu-id="4d8f9-106">To deploy a data processing extension assembly</span></span>  
  
1.  <span data-ttu-id="4d8f9-107">将程序集从临时位置复制到报表设计器目录中。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-107">Copy your assembly from your staging location to the Report Designer directory.</span></span> <span data-ttu-id="4d8f9-108">报表服务器目录的默认位置为 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-108">The default location of the Report Designer directory is C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
2.  <span data-ttu-id="4d8f9-109">在复制程序集文件后，打开 RSReportDesigner.config 文件。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-109">After the assembly file is copied, open the RSReportDesigner.config file.</span></span> <span data-ttu-id="4d8f9-110">RSReportDesigner.config 文件也位于报表设计器目录中。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-110">The RSReportDesigner.config file is also located in the Report Designer directory.</span></span> <span data-ttu-id="4d8f9-111">还需要在配置文件中为数据处理扩展插件程序集文件生成一个条目。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-111">You need to make an entry in the configuration file for your data processing extension assembly file.</span></span> <span data-ttu-id="4d8f9-112">可以使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或简单文本编辑器（如记事本）打开配置文件。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-112">You can open the configuration file with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or with a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="4d8f9-113">在 RSReportDesigner.config 文件中找到 **Data** 元素。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-113">Locate the **Data** element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="4d8f9-114">应当在以下位置为新创建的数据处理扩展插件生成一个条目：</span><span class="sxs-lookup"><span data-stu-id="4d8f9-114">An entry for your newly created data processing extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="4d8f9-115">为数据处理扩展插件添加一个条目，该条目**Extension**包含具有 `Name` 、 `Type` 和属性的值的扩展元素 `Visible` 。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-115">Add an entry for your data processing extension which includes an **Extension** element with values for the `Name`, `Type`, and `Visible` attributes.</span></span> <span data-ttu-id="4d8f9-116">您的条目可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="4d8f9-116">Your entry might look like the following:</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="4d8f9-117">`Name` 的值为数据处理扩展插件的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-117">The value for `Name` is the unique name of the data processing extension.</span></span> <span data-ttu-id="4d8f9-118">`Type` 的值是以逗号分隔的列表，包括实现 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 和 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 接口的类的完全限定命名空间的条目，后跟程序集的名称（不包括 .dll 文件扩展名）。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-118">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IExtension> and <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfaces, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="4d8f9-119">默认情况下，数据处理扩展插件是可见的。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-119">By default, data processing extensions are visible.</span></span> <span data-ttu-id="4d8f9-120">若要从用户界面（如报表设计器）中隐藏扩展插件，请将 `Visible` 属性添加到**extension**元素，并将其设置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-120">To hide an extension from user interfaces, such as Report Designer, add a `Visible` attribute to the **Extension** element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="4d8f9-121">最后，为自定义程序集添加一个代码组，以便为扩展插件授予 FullTrust 权限  。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-121">Finally, add a code group for your custom assembly that grants **FullTrust** permission for your extension.</span></span> <span data-ttu-id="4d8f9-122">要完成该操作，将该代码组添加到 rspreviewpolicy.config 文件中即可，该文件在默认情况下位于 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies 中。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-122">You do this by adding the code group to the rspreviewpolicy.config file located by default in C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span> <span data-ttu-id="4d8f9-123">代码组可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="4d8f9-123">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="4d8f9-124">URL 成员身份只是您可以为数据处理扩展插件选择的众多成员条件之一。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-124">URL membership is only one of many membership conditions you might choose for your data processing extension.</span></span> <span data-ttu-id="4d8f9-125">有关 [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)] 中的代码访问安全性的详细信息，请参阅[安全开发 (Reporting Services)](../secure-development/secure-development-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="4d8f9-125">For more information about code access security in [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="generic-query-designer"></a><span data-ttu-id="4d8f9-126">通用查询设计器</span><span class="sxs-lookup"><span data-stu-id="4d8f9-126">Generic Query Designer</span></span>  
 <span data-ttu-id="4d8f9-127">报表设计器提供了可用于自定义数据处理扩展插件的通用查询设计器。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-127">Report Designer provides a generic query designer that you can use with custom data processing extensions.</span></span> <span data-ttu-id="4d8f9-128">该设计器包含两个窗格：查询窗格和结果窗格。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-128">This designer consists of two panes: a query pane and a results pane.</span></span> <span data-ttu-id="4d8f9-129">您可以使用该通用设计器编写图形界面不支持的查询。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-129">You can use the generic designer to write queries that are not supported by the graphical interface.</span></span> <span data-ttu-id="4d8f9-130">与图形查询设计器不同的是，通用查询设计器不检查查询语法或调整查询的结构。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-130">Unlike the graphical query designer, the generic query designer does not check query syntax or restructure the query.</span></span>  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a><span data-ttu-id="4d8f9-131">为自定义扩展插件启用通用查询设计器</span><span class="sxs-lookup"><span data-stu-id="4d8f9-131">To enable the generic query designer for a custom extension</span></span>  
  
-   <span data-ttu-id="4d8f9-132">将以下条目添加到**设计器**元素下的 RSReportDesigner.config 文件中，并将该属性替换为 `Name` 在以前的条目中提供的名称。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-132">Add the following entry to the RSReportDesigner.config file under the **Designer** element, replacing the `Name` attribute with the name that you provided in previous entries.</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="4d8f9-133">验证部署</span><span class="sxs-lookup"><span data-stu-id="4d8f9-133">Verifying the Deployment</span></span>  
 <span data-ttu-id="4d8f9-134">必须先关闭本地计算机上的所有 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 实例，然后才能验证部署。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-134">Before you can verify deployment, you must close all instances of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] on your local computer.</span></span> <span data-ttu-id="4d8f9-135">结束所有当前会话之后，可以在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中创建一个新报表项目，以验证数据处理扩展插件是否已成功部署到报表设计器。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-135">After you have ended all current sessions, you can verify whether your data processing extension was deployed successfully to Report Designer by creating a new report project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="4d8f9-136">为报表创建新的数据集时，您的扩展插件应当包括在可用数据源类型列表中。</span><span class="sxs-lookup"><span data-stu-id="4d8f9-136">Your extension should be included in the list of available data source types when you create a new data set for your report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8f9-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d8f9-137">See Also</span></span>  
 <span data-ttu-id="4d8f9-138">[部署数据处理扩展插件](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="4d8f9-138">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="4d8f9-139">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="4d8f9-139">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="4d8f9-140">[实现数据处理扩展插件](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="4d8f9-140">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="4d8f9-141">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="4d8f9-141">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
