---
title: 包配置 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package configuration syntax [Integration Services]
- SQL Server Integration Services packages, configurations
- SSIS packages, configurations
- XML [Integration Services]
- Integration Services packages, configurations
- configuration syntax [Integration Services]
- indirect configurations [Integration Services]
- configurations [Integration Services]
- direct configurations [Integration Services]
- packages [Integration Services], configurations
ms.assetid: d20e0311-1fc9-4ddc-a381-6d127cf11b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d22dbfedcf4cf7084e1667586f9774926f3b2a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591475"
---
# <a name="package-configurations"></a><span data-ttu-id="6888f-102">包配置</span><span class="sxs-lookup"><span data-stu-id="6888f-102">Package Configurations</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="6888f-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供可用于在运行时更新属性值的包配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides package configurations that you can use to update the values of properties at run time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6888f-104">配置可用于包部署模型。</span><span class="sxs-lookup"><span data-stu-id="6888f-104">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="6888f-105">对于项目部署模型，参数用于代替配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-105">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="6888f-106">项目部署模型使您可以将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="6888f-106">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="6888f-107">有关部署模型的详细信息，请参阅 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="6888f-107">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="6888f-108">配置是添加到已完成包中的属性/值对。</span><span class="sxs-lookup"><span data-stu-id="6888f-108">A configuration is a property/value pair that you add to a completed package.</span></span> <span data-ttu-id="6888f-109">通常，在包开发期间您在包对象上创建包设置属性，然后将配置添加到包中。</span><span class="sxs-lookup"><span data-stu-id="6888f-109">Typically, you create a package set properties on the package objects during package development, and then add the configuration to the package.</span></span> <span data-ttu-id="6888f-110">当包运行时，它从配置中获取新的属性值。</span><span class="sxs-lookup"><span data-stu-id="6888f-110">When the package runs, it gets the new values of the property from the configuration.</span></span> <span data-ttu-id="6888f-111">例如，通过使用配置，您可以更改连接管理器的连接字符串，或者更新变量的值。</span><span class="sxs-lookup"><span data-stu-id="6888f-111">For example, by using a configuration, you can change the connection string of a connection manager, or update the value of a variable.</span></span>  
  
 <span data-ttu-id="6888f-112">包配置具有下列优点：</span><span class="sxs-lookup"><span data-stu-id="6888f-112">Package configurations provide the following benefits:</span></span>  
  
-   <span data-ttu-id="6888f-113">使用配置可以更轻松地将包从开发环境转移到生产环境中。</span><span class="sxs-lookup"><span data-stu-id="6888f-113">Configurations make it easier to move packages from a development environment to a production environment.</span></span> <span data-ttu-id="6888f-114">例如，配置可以更新源文件的路径，或者更改数据库或服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="6888f-114">For example, a configuration can update the path of a source file, or change the name of a database or server.</span></span>  
  
-   <span data-ttu-id="6888f-115">将包部署到多台不同的服务器时，配置非常有用。</span><span class="sxs-lookup"><span data-stu-id="6888f-115">Configurations are useful when you deploy packages to many different servers.</span></span> <span data-ttu-id="6888f-116">例如，用于每个已部署包的配置中的变量可以包含不同的磁盘空间，并且如果可用磁盘空间不满足此值，包将不会运行。</span><span class="sxs-lookup"><span data-stu-id="6888f-116">For example, a variable in the configuration for each deployed package can contain a different disk space value, and if the available disk space does not meet this value, the package does not run.</span></span>  
  
-   <span data-ttu-id="6888f-117">配置可以使包更加灵活。</span><span class="sxs-lookup"><span data-stu-id="6888f-117">Configurations make packages more flexible.</span></span> <span data-ttu-id="6888f-118">例如，配置可以更新在属性表达式中使用的变量的值。</span><span class="sxs-lookup"><span data-stu-id="6888f-118">For example, a configuration can update the value of a variable that is used in a property expression.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6888f-119">支持几种不同的存储包配置（例如 XML 文件、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库中的表以及环境变量和包变量）的方法。</span><span class="sxs-lookup"><span data-stu-id="6888f-119">supports several different methods of storing package configurations, such as XML files, tables in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, and environment and package variables.</span></span>  
  
 <span data-ttu-id="6888f-120">每个配置都是一个属性/值对。</span><span class="sxs-lookup"><span data-stu-id="6888f-120">Each configuration is a property/value pair.</span></span> <span data-ttu-id="6888f-121">XML 配置文件和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置类型可以包括多个配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-121">The XML configuration file and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration types can include multiple configurations.</span></span>  
  
 <span data-ttu-id="6888f-122">在创建用于安装包的包部署实用工具时将会包括这些配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-122">The configurations are included when you create a package deployment utility for installing packages.</span></span> <span data-ttu-id="6888f-123">在安装包时，可以在安装包的过程中更新配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-123">When you install the packages, the configurations can be updated as a step in the package installation.</span></span>  
  
## <a name="understanding-how-package-configurations-are-applied-at-run-time"></a><span data-ttu-id="6888f-124">了解在运行时如何应用包配置</span><span class="sxs-lookup"><span data-stu-id="6888f-124">Understanding How Package Configurations Are Applied at Run Time</span></span>  
 <span data-ttu-id="6888f-125">使用 **dtexec** 命令提示实用工具 (dtexec.exe) 运行部署的包时，该实用工具将应用两次包配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-125">When you use the **dtexec** command prompt utility (dtexec.exe) to run a deployed package, the utility applies package configurations twice.</span></span> <span data-ttu-id="6888f-126">该实用工具将在它应用在命令行上指定的选项之前和之后各应用一次包配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-126">The utility applies configurations both before and after it applies the options that you specified on command line.</span></span>  
  
 <span data-ttu-id="6888f-127">在实用工具加载和运行包时，事件的发生顺序如下：</span><span class="sxs-lookup"><span data-stu-id="6888f-127">As the utility loads and runs the package, events occur in the following order:</span></span>  
  
1.  <span data-ttu-id="6888f-128">**dtexec** 实用工具加载包。</span><span class="sxs-lookup"><span data-stu-id="6888f-128">The **dtexec** utility loads the package.</span></span>  
  
2.  <span data-ttu-id="6888f-129">该实用工具应用设计时在包中指定的配置，并根据在包中指定的顺序应用。</span><span class="sxs-lookup"><span data-stu-id="6888f-129">The utility applies the configurations that were specified in the package at design time and in the order that is specified in the package.</span></span> <span data-ttu-id="6888f-130">（唯一的例外是父包变量配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-130">(The one exception to this is the Parent Package Variables configurations.</span></span> <span data-ttu-id="6888f-131">该实用工具仅应用一次这些配置，并且是在过程的后面应用。）</span><span class="sxs-lookup"><span data-stu-id="6888f-131">The utility applies these configurations only once and later in the process.)</span></span>  
  
3.  <span data-ttu-id="6888f-132">该实用工具随后应用在命令行上指定的任何选项。</span><span class="sxs-lookup"><span data-stu-id="6888f-132">The utility then applies any options that you specified on the command line.</span></span>  
  
4.  <span data-ttu-id="6888f-133">该实用工具随后重新加载设计时在包中指定的配置，并根据在包中指定的顺序重新加载。</span><span class="sxs-lookup"><span data-stu-id="6888f-133">The utility then reloads the configurations that were specified in the package at design time and in the order specified in the package.</span></span> <span data-ttu-id="6888f-134">（同样，此规则唯一的例外是父包变量配置）。</span><span class="sxs-lookup"><span data-stu-id="6888f-134">(Again, the exception to this rule is the Parent Package Variables configurations).</span></span> <span data-ttu-id="6888f-135">该实用工具使用指定的任何命令行选项来重新加载配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-135">The utility uses any command-line options that were specified to reload the configurations.</span></span> <span data-ttu-id="6888f-136">因此，可能从不同位置重新加载不同值。</span><span class="sxs-lookup"><span data-stu-id="6888f-136">Therefore, different values might be reloaded from a different location.</span></span>  
  
5.  <span data-ttu-id="6888f-137">该实用程序应用父包变量配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-137">The utility applies the Parent Package Variable configurations.</span></span>  
  
6.  <span data-ttu-id="6888f-138">该实用工具运行包。</span><span class="sxs-lookup"><span data-stu-id="6888f-138">The utility runs the package.</span></span>  
  
 <span data-ttu-id="6888f-139">**dtexec** 实用工具应用配置的方式会影响以下命令行选项：</span><span class="sxs-lookup"><span data-stu-id="6888f-139">The way in which the **dtexec** utility applies configurations affects the following command-line options:</span></span>  
  
-   <span data-ttu-id="6888f-140">在运行时，可以使用 **/Connection** 或 **/Set** 选项从在设计时指定的位置之外的某个位置加载包配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-140">You can use the **/Connection** or **/Set** option at run time to load package configurations from a location other than the location that you specified at design time.</span></span>  
  
-   <span data-ttu-id="6888f-141">可以使用 **/ConfigFile** 选项加载在设计时未指定的其他配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-141">You can use the **/ConfigFile** option to load additional configurations that you did not specify at design time.</span></span>  
  
 <span data-ttu-id="6888f-142">但是，这些命令行选项确实存在一些限制：</span><span class="sxs-lookup"><span data-stu-id="6888f-142">However, these command-line options do have some restrictions:</span></span>  
  
-   <span data-ttu-id="6888f-143">不能使用 **/Set** 或 **/Connection** 选项替代同样由配置设置的单个值。</span><span class="sxs-lookup"><span data-stu-id="6888f-143">You cannot use the **/Set** or the **/Connection** option to override single values that are also set by a configuration.</span></span>  
  
-   <span data-ttu-id="6888f-144">不能使用 **/ConfigFile** 选项加载用来替换在设计时指定的配置的配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-144">You cannot use the **/ConfigFile** option to load configurations that replace the configurations that you specified at design time.</span></span>  
  
 <span data-ttu-id="6888f-145">有关这些选项的详细信息以及这些选项的行为与早期版本的不同之处 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] ，请参阅[SQL Server 2014 中 Integration Services 功能的行为更改](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="6888f-145">For more information about these options, and how the behavior of these options differs between [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] and earlier versions, see [Behavior Changes to Integration Services Features in SQL Server 2014](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
## <a name="package-configuration-types"></a><span data-ttu-id="6888f-146">包配置类型</span><span class="sxs-lookup"><span data-stu-id="6888f-146">Package Configuration Types</span></span>  
 <span data-ttu-id="6888f-147">下表介绍了包配置的类型。</span><span class="sxs-lookup"><span data-stu-id="6888f-147">The following table describes the package configuration types.</span></span>  
  
|<span data-ttu-id="6888f-148">类型</span><span class="sxs-lookup"><span data-stu-id="6888f-148">Type</span></span>|<span data-ttu-id="6888f-149">说明</span><span class="sxs-lookup"><span data-stu-id="6888f-149">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="6888f-150">XML 配置文件</span><span class="sxs-lookup"><span data-stu-id="6888f-150">XML configuration file</span></span>|<span data-ttu-id="6888f-151">XML 文件包含配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-151">An XML file contains the configurations.</span></span> <span data-ttu-id="6888f-152">XML 文件可以包括多个配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-152">The XML file can include multiple configurations.</span></span>|  
|<span data-ttu-id="6888f-153">环境变量</span><span class="sxs-lookup"><span data-stu-id="6888f-153">Environment variable</span></span>|<span data-ttu-id="6888f-154">环境变量包含配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-154">An environment variable contains the configuration.</span></span>|  
|<span data-ttu-id="6888f-155">注册表项</span><span class="sxs-lookup"><span data-stu-id="6888f-155">Registry entry</span></span>|<span data-ttu-id="6888f-156">注册表项包含配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-156">A Registry entry contains the configuration.</span></span>|  
|<span data-ttu-id="6888f-157">父包变量</span><span class="sxs-lookup"><span data-stu-id="6888f-157">Parent package variable</span></span>|<span data-ttu-id="6888f-158">包中的变量包含配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-158">A variable in the package contains the configuration.</span></span> <span data-ttu-id="6888f-159">此配置类型通常用于更新子包中的属性。</span><span class="sxs-lookup"><span data-stu-id="6888f-159">This configuration type is typically used to update properties in child packages.</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="6888f-160">表</span><span class="sxs-lookup"><span data-stu-id="6888f-160">table</span></span>|<span data-ttu-id="6888f-161">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库中的表包含配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-161">A table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database contains the configuration.</span></span> <span data-ttu-id="6888f-162">表可以包括多个配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-162">The table can include multiple configurations.</span></span>|  
  
### <a name="xml-configuration-files"></a><span data-ttu-id="6888f-163">XML 配置文件</span><span class="sxs-lookup"><span data-stu-id="6888f-163">XML Configuration Files</span></span>  
 <span data-ttu-id="6888f-164">如果选择 **“XML 配置文件”** 配置类型，您可以创建一个新的配置文件；重用现有文件并添加新的配置；也可以重用现有文件但覆盖现有文件的内容。</span><span class="sxs-lookup"><span data-stu-id="6888f-164">If you select the **XML configuration file** configuration type, you can create a new configuration file, reuse an existing file and add new configurations, or reuse an existing file but overwrite existing file content.</span></span>  
  
 <span data-ttu-id="6888f-165">XML 配置文件包括两部分：</span><span class="sxs-lookup"><span data-stu-id="6888f-165">An XML configuration file includes two sections:</span></span>  
  
-   <span data-ttu-id="6888f-166">包含有关配置文件信息的标题。</span><span class="sxs-lookup"><span data-stu-id="6888f-166">A heading that contains information about the configuration file.</span></span> <span data-ttu-id="6888f-167">此元素包括的属性有该文件的创建时间和该文件的创建者的姓名等。</span><span class="sxs-lookup"><span data-stu-id="6888f-167">This element includes attributes such as when the file was created and the name of the person who generated the file.</span></span>  
  
-   <span data-ttu-id="6888f-168">包含有关每个配置的信息的配置元素。</span><span class="sxs-lookup"><span data-stu-id="6888f-168">Configuration elements that contain information about each configuration.</span></span> <span data-ttu-id="6888f-169">此元素包括的特性有属性路径和属性的配置值等。</span><span class="sxs-lookup"><span data-stu-id="6888f-169">This element includes attributes such as the property path and the configured value of a property.</span></span>  
  
 <span data-ttu-id="6888f-170">下列 XML 代码说明了 XML 配置文件的语法。</span><span class="sxs-lookup"><span data-stu-id="6888f-170">The following XML code demonstrates the syntax of an XML configuration file.</span></span> <span data-ttu-id="6888f-171">此示例显示了一个名为 `MyVar`的整数变量的 Value 属性配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-171">This example shows a configuration for the Value property of an integer variable named `MyVar`.</span></span>  
  
```  
<?xml version="1.0"?>  
<DTSConfiguration>  
   <DTSConfigurationHeading>  
      <DTSConfigurationFileInfo  
          GeneratedBy="DomainName\UserName"  
          GeneratedFromPackageName="Package"  
          GeneratedFromPackageID="{2AF06766-817A-4E28-9878-0DE37A150648}"  
          GeneratedDate="2/01/2005 5:58:09 PM"/>  
   </DTSConfigurationHeading>  
   <Configuration ConfiguredType="Property" Path="\Package.Variables[User::MyVar].Value" ValueType="Int32">  
      <ConfiguredValue>0</ConfiguredValue>  
   </Configuration>  
</DTSConfiguration>  
  
```  
  
### <a name="registry-entry"></a><span data-ttu-id="6888f-172">注册表项</span><span class="sxs-lookup"><span data-stu-id="6888f-172">Registry Entry</span></span>  
 <span data-ttu-id="6888f-173">如果要使用注册表项存储配置，可以使用已有项或在 HKEY_CURRENT_USER 中创建新项。</span><span class="sxs-lookup"><span data-stu-id="6888f-173">If you want to use a Registry entry to store the configuration, you can either use an existing key or create a new key in HKEY_CURRENT_USER.</span></span> <span data-ttu-id="6888f-174">使用的注册表项必须具有名为 `Value` 的值。</span><span class="sxs-lookup"><span data-stu-id="6888f-174">The Registry key that you use must have a value named `Value`.</span></span> <span data-ttu-id="6888f-175">该值可以是 DWORD 或一个字符串。</span><span class="sxs-lookup"><span data-stu-id="6888f-175">The value can be a DWORD or a string.</span></span>  
  
 <span data-ttu-id="6888f-176">如果选择 **“注册表项”** 配置类型，请在“注册表项”框中键入注册表项的名称。</span><span class="sxs-lookup"><span data-stu-id="6888f-176">If you select the **Registry entry** configuration type, you type the name of the Registry key in the Registry entry box.</span></span> <span data-ttu-id="6888f-177">格式为 \<registry key>。</span><span class="sxs-lookup"><span data-stu-id="6888f-177">The format is \<registry key>.</span></span> <span data-ttu-id="6888f-178">如果要使用不在 HKEY_CURRENT_USER 根目录下的注册表项，请使用 \<Registry key\registry key\\...> 格式来标识该项。</span><span class="sxs-lookup"><span data-stu-id="6888f-178">If you want to use a Registry key that is not at the root of HKEY_CURRENT_USER, use the format \<Registry key\registry key\\...> to identify the key.</span></span> <span data-ttu-id="6888f-179">例如，若要使用 SSISPackages 中的 MyPackage 项，请键入 `SSISPackages\MyPackage`。</span><span class="sxs-lookup"><span data-stu-id="6888f-179">For example, to use the MyPackage key located in SSISPackages, type `SSISPackages\MyPackage`.</span></span>  
  
### <a name="sql-server"></a><span data-ttu-id="6888f-180">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6888f-180">SQL Server</span></span>  
 <span data-ttu-id="6888f-181">如果选择 **SQL Server** 配置类型，则需指定到要存储这些配置的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="6888f-181">If you select the **SQL Server** configuration type, you specify the connection to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database in which you want to store the configurations.</span></span> <span data-ttu-id="6888f-182">可以将配置保存到现有表，也可以在指定数据库中新建表。</span><span class="sxs-lookup"><span data-stu-id="6888f-182">You can save the configurations to an existing table or create a new table in the specified database.</span></span>  
  
 <span data-ttu-id="6888f-183">下面的 SQL 语句说明了包配置向导提供的默认 CREATE TABLE 语句。</span><span class="sxs-lookup"><span data-stu-id="6888f-183">The following SQL statement shows the default CREATE TABLE statement that the Package Configuration Wizard provides.</span></span>  
  
```  
CREATE TABLE [dbo].[SSIS Configurations]  
(  
ConfigurationFilter NVARCHAR(255) NOT NULL,  
ConfiguredValue NVARCHAR(255) NULL,  
PackagePath NVARCHAR(255) NOT NULL,  
ConfiguredValueType NVARCHAR(20) NOT NULL  
)  
  
```  
  
 <span data-ttu-id="6888f-184">您为配置提供的名称就是在 **ConfigurationFilter** 列中存储的值。</span><span class="sxs-lookup"><span data-stu-id="6888f-184">The name that you provide for the configuration is the value stored in the **ConfigurationFilter** column.</span></span>  
  
## <a name="direct-and-indirect-configurations"></a><span data-ttu-id="6888f-185">直接配置和间接配置</span><span class="sxs-lookup"><span data-stu-id="6888f-185">Direct and Indirect Configurations</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6888f-186">提供了直接配置和间接配置。</span><span class="sxs-lookup"><span data-stu-id="6888f-186">provides direct and indirect configurations.</span></span> <span data-ttu-id="6888f-187">如果直接指定配置， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 会在配置项和包对象属性之间创建直接链接。</span><span class="sxs-lookup"><span data-stu-id="6888f-187">If you specify configurations directly, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] creates a direct link between the configuration item and the package object property.</span></span> <span data-ttu-id="6888f-188">如果源的位置不更改，则直接配置是较好的选择。</span><span class="sxs-lookup"><span data-stu-id="6888f-188">Direct configurations are a better choice when the location of the source does not change.</span></span> <span data-ttu-id="6888f-189">例如，如果确定包中的所有部署都使用相同的文件路径，则可以指定一个 XML 配置文件。</span><span class="sxs-lookup"><span data-stu-id="6888f-189">For example, if you are sure that all deployments in the package use the same file path, you can specify an XML configuration file.</span></span>  
  
 <span data-ttu-id="6888f-190">间接配置使用环境变量。</span><span class="sxs-lookup"><span data-stu-id="6888f-190">Indirect configurations use environment variables.</span></span> <span data-ttu-id="6888f-191">配置不直接指定配置设置，而是指向环境变量，环境变量又包含配置值。</span><span class="sxs-lookup"><span data-stu-id="6888f-191">Instead of specifying the configuration setting directly, the configuration points to an environment variable, which in turn contains the configuration value.</span></span> <span data-ttu-id="6888f-192">如果对于包的每个部署，配置的位置都可以更改，则使用间接配置是较好的选择。</span><span class="sxs-lookup"><span data-stu-id="6888f-192">Using indirect configurations is a better choice when the location of the configuration can change for each deployment of a package.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6888f-193">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6888f-193">Related Tasks</span></span>  
 [<span data-ttu-id="6888f-194">创建包配置</span><span class="sxs-lookup"><span data-stu-id="6888f-194">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
## <a name="related-content"></a><span data-ttu-id="6888f-195">相关内容</span><span class="sxs-lookup"><span data-stu-id="6888f-195">Related Content</span></span>  
  
-   <span data-ttu-id="6888f-196">msdn.microsoft.com 上的技术文章 [理解 Integration Services 包配置](https://go.microsoft.com/fwlink/?LinkId=165643)</span><span class="sxs-lookup"><span data-stu-id="6888f-196">Technical article, [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="6888f-197">Www.sqlis.com 上的博客文章[在代码包配置中创建包](https://go.microsoft.com/fwlink/?LinkId=217663)。</span><span class="sxs-lookup"><span data-stu-id="6888f-197">Blog entry, [Creating packages in code - Package Configurations](https://go.microsoft.com/fwlink/?LinkId=217663), on www.sqlis.com.</span></span>  
  
-   <span data-ttu-id="6888f-198">Blogs.msdn.com 上的博客文章[API 示例-以编程方式将配置文件添加到包](https://go.microsoft.com/fwlink/?LinkId=217664)。</span><span class="sxs-lookup"><span data-stu-id="6888f-198">Blog entry, [API Sample - Programmatically add a configuration file to a package](https://go.microsoft.com/fwlink/?LinkId=217664), on blogs.msdn.com.</span></span>  
  
  
