---
title: 包配置向导用户界面参考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.configwizard.selectobjects.f1
- sql12.dts.configwizard.selecconfigtype.f1
- sql12.dts.configwizard.finishdtsconfiguration.f1
- sql12.dts.configwizard.welcome.f1
ms.assetid: adca6938-6d5a-40ec-950e-dceb79d044fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 222c5f58ca4e942dd23909b433ab346c500fceed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590283"
---
# <a name="package-configuration-wizard-ui-reference"></a><span data-ttu-id="0e917-102">包配置向导用户界面参考</span><span class="sxs-lookup"><span data-stu-id="0e917-102">Package Configuration Wizard UI Reference</span></span>
  <span data-ttu-id="0e917-103">可以使用 **“包配置向导”** 创建在运行时更新 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包及其对象的属性的配置。</span><span class="sxs-lookup"><span data-stu-id="0e917-103">Use the **Package Configuration Wizard** to create configurations that update the properties of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and its objects at run time.</span></span> <span data-ttu-id="0e917-104">当您在 **“包配置组织程序”** 对话框中添加新配置或者修改现有配置时，将运行该向导。</span><span class="sxs-lookup"><span data-stu-id="0e917-104">This wizard runs when you add a new configuration or modify an existing one in the **Package Configurations Organizer** dialog box.</span></span> <span data-ttu-id="0e917-105">若要打开 **“包配置组织程序”** 对话框，请在 **上的** SSIS **菜单中选择** “包配置” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0e917-105">To open the **Package Configurations Organizer** dialog box, select **Package Configurations** on the **SSIS** menu in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0e917-106">有关详细信息，请参阅 [创建包配置](../../2014/integration-services/create-package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="0e917-106">For more information, see [Create Package Configurations](../../2014/integration-services/create-package-configurations.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e917-107">配置可用于包部署模型。</span><span class="sxs-lookup"><span data-stu-id="0e917-107">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="0e917-108">对于项目部署模型，参数用于代替配置。</span><span class="sxs-lookup"><span data-stu-id="0e917-108">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="0e917-109">项目部署模型使您可以将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="0e917-109">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="0e917-110">有关部署模型的详细信息，请参阅 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="0e917-110">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="0e917-111">以下部分介绍了该向导中的各页。</span><span class="sxs-lookup"><span data-stu-id="0e917-111">The following sections describe pages of the Wizard.</span></span>  
  
## <a name="welcome-to-the-package-configuration-wizard-page"></a><span data-ttu-id="0e917-112">“欢迎使用包配置向导”页</span><span class="sxs-lookup"><span data-stu-id="0e917-112">Welcome to the Package Configuration Wizard Page</span></span>  
 <span data-ttu-id="0e917-113">使用 **“SSIS 配置向导”** 可以创建在运行时更新包及其对象的属性的配置。</span><span class="sxs-lookup"><span data-stu-id="0e917-113">Use the **SSIS Configuration Wizard** to create configurations that update the properties of a package and its objects at run time.</span></span>  
  
### <a name="options"></a><span data-ttu-id="0e917-114">选项</span><span class="sxs-lookup"><span data-stu-id="0e917-114">Options</span></span>  
 <span data-ttu-id="0e917-115">**不再显示此页**</span><span class="sxs-lookup"><span data-stu-id="0e917-115">**Don't show this page again**</span></span>  
 <span data-ttu-id="0e917-116">下次打开向导时跳过欢迎页。</span><span class="sxs-lookup"><span data-stu-id="0e917-116">Skip the welcome page the next time you open the wizard.</span></span>  
  
 <span data-ttu-id="0e917-117">**Next**</span><span class="sxs-lookup"><span data-stu-id="0e917-117">**Next**</span></span>  
 <span data-ttu-id="0e917-118">转到向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="0e917-118">Go the next page in the wizard.</span></span>  
  
## <a name="select-configuration-type-page"></a><span data-ttu-id="0e917-119">“选择配置类型”页</span><span class="sxs-lookup"><span data-stu-id="0e917-119">Select Configuration Type Page</span></span>  
 <span data-ttu-id="0e917-120">使用 **“选择配置类型”** 页可以指定要创建的配置类型。</span><span class="sxs-lookup"><span data-stu-id="0e917-120">Use the **Select Configuration Type** page to specify the type of configuration to create.</span></span>  
  
 <span data-ttu-id="0e917-121">如果需要其他信息才能确定要使用的配置类型，则请参阅 [Package Configurations](../../2014/integration-services/package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="0e917-121">If you need additional information to determine which type of configuration to use, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
### <a name="static-options"></a><span data-ttu-id="0e917-122">静态选项</span><span class="sxs-lookup"><span data-stu-id="0e917-122">Static Options</span></span>  
 <span data-ttu-id="0e917-123">**配置类型**</span><span class="sxs-lookup"><span data-stu-id="0e917-123">**Configuration type**</span></span>  
 <span data-ttu-id="0e917-124">使用下列选项选择存储配置的源的类型：</span><span class="sxs-lookup"><span data-stu-id="0e917-124">Select the type of source in which to store the configuration, using the following options:</span></span>  
  
|<span data-ttu-id="0e917-125">值</span><span class="sxs-lookup"><span data-stu-id="0e917-125">Value</span></span>|<span data-ttu-id="0e917-126">说明</span><span class="sxs-lookup"><span data-stu-id="0e917-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e917-127">**XML 配置文件**</span><span class="sxs-lookup"><span data-stu-id="0e917-127">**XML configuration file**</span></span>|<span data-ttu-id="0e917-128">将配置存储为 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="0e917-128">Store the configuration as an XML file.</span></span> <span data-ttu-id="0e917-129">选择此值将显示 **“配置类型”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="0e917-129">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="0e917-130">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="0e917-130">**Environment variable**</span></span>|<span data-ttu-id="0e917-131">将配置存储在一个环境变量中。</span><span class="sxs-lookup"><span data-stu-id="0e917-131">Store the configuration in one of the environment variables.</span></span> <span data-ttu-id="0e917-132">选择此值将显示 **“配置类型”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="0e917-132">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="0e917-133">**注册表项**</span><span class="sxs-lookup"><span data-stu-id="0e917-133">**Registry entry**</span></span>|<span data-ttu-id="0e917-134">将配置存储在注册表中。</span><span class="sxs-lookup"><span data-stu-id="0e917-134">Store the configuration in the Registry.</span></span> <span data-ttu-id="0e917-135">选择此值将显示 **“配置类型”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="0e917-135">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="0e917-136">**父包变量**</span><span class="sxs-lookup"><span data-stu-id="0e917-136">**Parent package variable**</span></span>|<span data-ttu-id="0e917-137">将配置存储为包含该任务的包中的变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-137">Store the configuration as a variable in the package that contains the task.</span></span>  <span data-ttu-id="0e917-138">选择此值将显示 **“配置类型”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="0e917-138">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="0e917-139">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="0e917-139">**SQL Server**</span></span>|<span data-ttu-id="0e917-140">将配置存储在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]表中。</span><span class="sxs-lookup"><span data-stu-id="0e917-140">Store the configuration in a table in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0e917-141">选择此值将显示 **“配置类型”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="0e917-141">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
  
 <span data-ttu-id="0e917-142">**Next**</span><span class="sxs-lookup"><span data-stu-id="0e917-142">**Next**</span></span>  
 <span data-ttu-id="0e917-143">查看向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="0e917-143">View the next page in the wizard sequence.</span></span>  
  
### <a name="dynamic-options"></a><span data-ttu-id="0e917-144">动态选项</span><span class="sxs-lookup"><span data-stu-id="0e917-144">Dynamic Options</span></span>  
  
#### <a name="configuration-type-option--xml-configuration-file"></a><span data-ttu-id="0e917-145">配置类型选项 = XML 配置文件</span><span class="sxs-lookup"><span data-stu-id="0e917-145">Configuration Type Option = XML Configuration File</span></span>  
 <span data-ttu-id="0e917-146">**直接指定配置设置**</span><span class="sxs-lookup"><span data-stu-id="0e917-146">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="0e917-147">用于直接指定设置。</span><span class="sxs-lookup"><span data-stu-id="0e917-147">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="0e917-148">值</span><span class="sxs-lookup"><span data-stu-id="0e917-148">Value</span></span>|<span data-ttu-id="0e917-149">说明</span><span class="sxs-lookup"><span data-stu-id="0e917-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e917-150">**配置文件名**</span><span class="sxs-lookup"><span data-stu-id="0e917-150">**Configuration file name**</span></span>|<span data-ttu-id="0e917-151">键入向导生成的配置文件的路径。</span><span class="sxs-lookup"><span data-stu-id="0e917-151">Type the path of the configuration file that the wizard generates.</span></span>|  
|<span data-ttu-id="0e917-152">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="0e917-152">**Browse**</span></span>|<span data-ttu-id="0e917-153">使用 **“选择配置文件位置”** 对话框指定向导生成的配置文件的路径。</span><span class="sxs-lookup"><span data-stu-id="0e917-153">Use the **Select Configuration File Location** dialog box to specify the path of the configuration file that the wizard generates.</span></span> <span data-ttu-id="0e917-154">如果文件不存在，则向导将创建该文件。</span><span class="sxs-lookup"><span data-stu-id="0e917-154">If the file does not exist, it is created by the wizard.</span></span>|  
  
 <span data-ttu-id="0e917-155">**配置位置存储在一个环境变量中**</span><span class="sxs-lookup"><span data-stu-id="0e917-155">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="0e917-156">用于指定存储配置的环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-156">Use to specify the environment variable in which to store the configuration.</span></span>  
  
|<span data-ttu-id="0e917-157">值</span><span class="sxs-lookup"><span data-stu-id="0e917-157">Value</span></span>|<span data-ttu-id="0e917-158">说明</span><span class="sxs-lookup"><span data-stu-id="0e917-158">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e917-159">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="0e917-159">**Environment variable**</span></span>|<span data-ttu-id="0e917-160">从列表中选择环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-160">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-option--environment-variable"></a><span data-ttu-id="0e917-161">配置类型选项 = 环境变量</span><span class="sxs-lookup"><span data-stu-id="0e917-161">Configuration Type Option = Environment Variable</span></span>  
 <span data-ttu-id="0e917-162">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="0e917-162">**Environment variable**</span></span>  
 <span data-ttu-id="0e917-163">选择包含配置信息的环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-163">Select the environment variable that contains the configuration information.</span></span>  
  
#### <a name="configuration-type-option--registry-entry"></a><span data-ttu-id="0e917-164">配置类型选项 = 注册表项</span><span class="sxs-lookup"><span data-stu-id="0e917-164">Configuration Type Option = Registry Entry</span></span>  
 <span data-ttu-id="0e917-165">**直接指定配置设置**</span><span class="sxs-lookup"><span data-stu-id="0e917-165">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="0e917-166">用于直接指定设置。</span><span class="sxs-lookup"><span data-stu-id="0e917-166">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="0e917-167">值</span><span class="sxs-lookup"><span data-stu-id="0e917-167">Value</span></span>|<span data-ttu-id="0e917-168">说明</span><span class="sxs-lookup"><span data-stu-id="0e917-168">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e917-169">**注册表项**</span><span class="sxs-lookup"><span data-stu-id="0e917-169">**Registry entry**</span></span>|<span data-ttu-id="0e917-170">键入包含配置信息的注册表项。</span><span class="sxs-lookup"><span data-stu-id="0e917-170">Type the Registry key that contains the configuration information.</span></span> <span data-ttu-id="0e917-171">格式为 \<registry key>。</span><span class="sxs-lookup"><span data-stu-id="0e917-171">The format is \<registry key>.</span></span><br /><br /> <span data-ttu-id="0e917-172">该注册表项必须已经存在于 HKEY_CURRENT_USER 中并且具有一个名为 Value 的值。</span><span class="sxs-lookup"><span data-stu-id="0e917-172">The Registry key must already exist in HKEY_CURRENT_USER and have a value named Value.</span></span> <span data-ttu-id="0e917-173">该值可以是 DWORD 或一个字符串。</span><span class="sxs-lookup"><span data-stu-id="0e917-173">The value can be a DWORD or a string.</span></span><br /><br /> <span data-ttu-id="0e917-174">如果要使用不在 HKEY_CURRENT_USER 根目录下的注册表项，请使用 \<Registry key\registry key\\...> 格式来标识该项。</span><span class="sxs-lookup"><span data-stu-id="0e917-174">If you want to use a Registry key is not at the root of HKEY_CURRENT_USER, use the format \<Registry key\registry key\\...> to identify the key.</span></span>|  
  
 <span data-ttu-id="0e917-175">**配置位置存储在一个环境变量中**</span><span class="sxs-lookup"><span data-stu-id="0e917-175">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="0e917-176">用于指定存储配置的环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-176">Use to specify the environment variable to store the configuration in.</span></span>  
  
|<span data-ttu-id="0e917-177">值</span><span class="sxs-lookup"><span data-stu-id="0e917-177">Value</span></span>|<span data-ttu-id="0e917-178">说明</span><span class="sxs-lookup"><span data-stu-id="0e917-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e917-179">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="0e917-179">**Environment variable**</span></span>|<span data-ttu-id="0e917-180">从列表中选择环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-180">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-option--parent-package-variable"></a><span data-ttu-id="0e917-181">配置类型选项 = 父包变量</span><span class="sxs-lookup"><span data-stu-id="0e917-181">Configuration Type Option = Parent Package Variable</span></span>  
 <span data-ttu-id="0e917-182">**直接指定配置设置**</span><span class="sxs-lookup"><span data-stu-id="0e917-182">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="0e917-183">用于直接指定设置。</span><span class="sxs-lookup"><span data-stu-id="0e917-183">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="0e917-184">值</span><span class="sxs-lookup"><span data-stu-id="0e917-184">Value</span></span>|<span data-ttu-id="0e917-185">说明</span><span class="sxs-lookup"><span data-stu-id="0e917-185">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e917-186">**父变量**</span><span class="sxs-lookup"><span data-stu-id="0e917-186">**Parent variable**</span></span>|<span data-ttu-id="0e917-187">指定父包中包含配置信息的变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-187">Specify the variable in the parent package that contains the configuration information.</span></span>|  
  
 <span data-ttu-id="0e917-188">**配置位置存储在一个环境变量中**</span><span class="sxs-lookup"><span data-stu-id="0e917-188">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="0e917-189">用于指定存储配置的环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-189">Use to specify the environment variable that stores the configuration.</span></span>  
  
|<span data-ttu-id="0e917-190">值</span><span class="sxs-lookup"><span data-stu-id="0e917-190">Value</span></span>|<span data-ttu-id="0e917-191">说明</span><span class="sxs-lookup"><span data-stu-id="0e917-191">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e917-192">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="0e917-192">**Environment variable**</span></span>|<span data-ttu-id="0e917-193">从列表中选择环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-193">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-options--sql-server"></a><span data-ttu-id="0e917-194">配置类型选项 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="0e917-194">Configuration Type Options = SQL Server</span></span>  
 <span data-ttu-id="0e917-195">**直接指定配置设置**</span><span class="sxs-lookup"><span data-stu-id="0e917-195">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="0e917-196">用于直接指定设置。</span><span class="sxs-lookup"><span data-stu-id="0e917-196">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="0e917-197">值</span><span class="sxs-lookup"><span data-stu-id="0e917-197">Value</span></span>|<span data-ttu-id="0e917-198">说明</span><span class="sxs-lookup"><span data-stu-id="0e917-198">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e917-199">**Connection**</span><span class="sxs-lookup"><span data-stu-id="0e917-199">**Connection**</span></span>|<span data-ttu-id="0e917-200">从列表中选择连接，或者单击 **“新建”** 创建新连接。</span><span class="sxs-lookup"><span data-stu-id="0e917-200">Select a connection from the list, or click **New** to create a new connection.</span></span>|  
|<span data-ttu-id="0e917-201">**配置表**</span><span class="sxs-lookup"><span data-stu-id="0e917-201">**Configuration table**</span></span>|<span data-ttu-id="0e917-202">选择现有的表，或者单击 **“新建”** 编写用于创建新表的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="0e917-202">Select an existing table, or click **New** to write a SQL statement that creates a new table.</span></span>|  
|<span data-ttu-id="0e917-203">**配置筛选器**</span><span class="sxs-lookup"><span data-stu-id="0e917-203">**Configuration filter**</span></span>|<span data-ttu-id="0e917-204">选择现有配置名称或者键入新名称。</span><span class="sxs-lookup"><span data-stu-id="0e917-204">Select an existing configuration name or type a new name.</span></span><br /><br /> <span data-ttu-id="0e917-205">多个 SQL Server 配置可以存储在同一个表中，而且每个配置可以包括多个配置项。</span><span class="sxs-lookup"><span data-stu-id="0e917-205">Many SQL Server configurations can be stored in the same table, and each configuration can include multiple configuration items.</span></span><br /><br /> <span data-ttu-id="0e917-206">此用户定义值存储在表中以标识属于特定配置的配置项</span><span class="sxs-lookup"><span data-stu-id="0e917-206">This user-defined value is stored in the table to identify configuration items that belong to a particular configuration</span></span>|  
  
 <span data-ttu-id="0e917-207">**配置位置存储在一个环境变量中**</span><span class="sxs-lookup"><span data-stu-id="0e917-207">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="0e917-208">用于指定存储配置的环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-208">Use to specify the environment variable where the configuration is stored.</span></span>  
  
|<span data-ttu-id="0e917-209">值</span><span class="sxs-lookup"><span data-stu-id="0e917-209">Value</span></span>|<span data-ttu-id="0e917-210">说明</span><span class="sxs-lookup"><span data-stu-id="0e917-210">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e917-211">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="0e917-211">**Environment variable**</span></span>|<span data-ttu-id="0e917-212">从列表中选择环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e917-212">Select an environment variable from the list.</span></span>|  
  
## <a name="select-objects-to-export-page"></a><span data-ttu-id="0e917-213">“选择要导出的对象”页</span><span class="sxs-lookup"><span data-stu-id="0e917-213">Select Objects to Export Page</span></span>  
 <span data-ttu-id="0e917-214">使用 **“选择目标属性”** 或“选择要导出的属性”页可以指定配置包含的对象属性。</span><span class="sxs-lookup"><span data-stu-id="0e917-214">Use the **Select Target Property or Select Properties to Export** page to specify the object properties that the configuration contains.</span></span> <span data-ttu-id="0e917-215">只有在选择 XML 配置类型时，才能选择多个属性。</span><span class="sxs-lookup"><span data-stu-id="0e917-215">The ability to select multiple properties is available only if you select the XML configuration type.</span></span>  
  
### <a name="options"></a><span data-ttu-id="0e917-216">选项</span><span class="sxs-lookup"><span data-stu-id="0e917-216">Options</span></span>  
 <span data-ttu-id="0e917-217">**对象**</span><span class="sxs-lookup"><span data-stu-id="0e917-217">**Objects**</span></span>  
 <span data-ttu-id="0e917-218">展开包层次结构并选择要导出的属性。</span><span class="sxs-lookup"><span data-stu-id="0e917-218">Expand the package hierarchy and select the properties to export.</span></span>  
  
 <span data-ttu-id="0e917-219">**属性特性**</span><span class="sxs-lookup"><span data-stu-id="0e917-219">**Property attributes**</span></span>  
 <span data-ttu-id="0e917-220">查看属性的特性。</span><span class="sxs-lookup"><span data-stu-id="0e917-220">View the attributes of a property.</span></span>  
  
 <span data-ttu-id="0e917-221">**Next**</span><span class="sxs-lookup"><span data-stu-id="0e917-221">**Next**</span></span>  
 <span data-ttu-id="0e917-222">转到向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="0e917-222">Go to the next page in the wizard.</span></span>  
  
## <a name="completing-the-wizard-page"></a><span data-ttu-id="0e917-223">“完成向导”页</span><span class="sxs-lookup"><span data-stu-id="0e917-223">Completing the Wizard Page</span></span>  
 <span data-ttu-id="0e917-224">使用 **“完成向导”** 页可以提供配置的名称以及查看此向导用于创建配置的设置。</span><span class="sxs-lookup"><span data-stu-id="0e917-224">Use the **Completing the Wizard** page to provide a name for the configuration and view settings used by the wizard to create the configuration.</span></span> <span data-ttu-id="0e917-225">在向导完成之后，将显示 **“包配置组织程序”** ，其中列出了包的所有配置。</span><span class="sxs-lookup"><span data-stu-id="0e917-225">After the wizard completes, the **Package Configurations Organizer** is displayed, which lists all configurations for the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="0e917-226">选项</span><span class="sxs-lookup"><span data-stu-id="0e917-226">Options</span></span>  
 <span data-ttu-id="0e917-227">**配置名称**</span><span class="sxs-lookup"><span data-stu-id="0e917-227">**Configuration name**</span></span>  
 <span data-ttu-id="0e917-228">键入配置的名称。</span><span class="sxs-lookup"><span data-stu-id="0e917-228">Type the name of the configuration.</span></span>  
  
 <span data-ttu-id="0e917-229">**预览**</span><span class="sxs-lookup"><span data-stu-id="0e917-229">**Preview**</span></span>  
 <span data-ttu-id="0e917-230">查看此向导用于创建配置的设置。</span><span class="sxs-lookup"><span data-stu-id="0e917-230">View the settings used by the wizard to create the configuration.</span></span>  
  
 <span data-ttu-id="0e917-231">**“完成”**</span><span class="sxs-lookup"><span data-stu-id="0e917-231">**Finish**</span></span>  
 <span data-ttu-id="0e917-232">创建配置并退出 **包配置向导**。</span><span class="sxs-lookup"><span data-stu-id="0e917-232">Create the configuration and exit the **Package Configuration Wizard**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e917-233">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e917-233">See Also</span></span>  
 [<span data-ttu-id="0e917-234">创建包配置</span><span class="sxs-lookup"><span data-stu-id="0e917-234">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
  
