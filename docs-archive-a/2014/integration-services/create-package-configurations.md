---
title: 创建包配置 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, configurations
- Package Configurations Organizer dialog box
- SSIS packages, configurations
- Integration Services packages, configurations
- configurations [Integration Services]
- packages [Integration Services], configurations
- deploying packages [Integration Services], configurations
ms.assetid: 91ac0347-f908-44f5-bd3d-115790223af4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58c93242c9ef51a5e00076bd367e46b43187098e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580803"
---
# <a name="create-package-configurations"></a><span data-ttu-id="7a76e-102">创建包配置</span><span class="sxs-lookup"><span data-stu-id="7a76e-102">Create Package Configurations</span></span>
  <span data-ttu-id="7a76e-103">使用 **“包配置组织程序”** 对话框和包配置向导，可以创建包配置。</span><span class="sxs-lookup"><span data-stu-id="7a76e-103">You create package configurations by using the **Package Configuration Organizer** dialog box and the Package Configuration Wizard.</span></span> <span data-ttu-id="7a76e-104">若要访问这些工具，请在 **中单击** “SSIS” **菜单上的** “包配置” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7a76e-104">To access these tools, click **Package Configurations** on the **SSIS** menu in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a76e-105">还可以通过单击 "**配置**" 属性旁的省略号按钮，访问 "**包配置组织**程序"。</span><span class="sxs-lookup"><span data-stu-id="7a76e-105">You can also access the **Package Configuration Organizer**, by clicking the ellipsis button next to the **Configuration** property.</span></span> <span data-ttu-id="7a76e-106">“配置”选项出现在包的属性窗口中。</span><span class="sxs-lookup"><span data-stu-id="7a76e-106">The Configuration property appears in the properties window for the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a76e-107">配置可用于包部署模型。</span><span class="sxs-lookup"><span data-stu-id="7a76e-107">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="7a76e-108">对于项目部署模型，参数用于代替配置。</span><span class="sxs-lookup"><span data-stu-id="7a76e-108">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="7a76e-109">项目部署模型使您可以将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="7a76e-109">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="7a76e-110">有关部署模型的详细信息，请参阅 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="7a76e-110">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="7a76e-111">在 **“包配置组织程序”** 对话框中，可以启用包以使用配置、添加和删除配置以及设置加载配置的首选顺序。</span><span class="sxs-lookup"><span data-stu-id="7a76e-111">In the **Package Configuration Organizer** dialog box, you can enable packages to use configurations, add and delete configurations, and set the preferred order in which configurations should be loaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a76e-112">如果包配置按照首选顺序加载，则配置按照从 **“包配置组织程序”** 对话框中显示的列表顶部到列表底部的顺序进行加载。</span><span class="sxs-lookup"><span data-stu-id="7a76e-112">When package configurations load in the preferred order, configurations load from the top of the list shown in the **Package Configuration Organizer** dialog box to the bottom of the list.</span></span> <span data-ttu-id="7a76e-113">但是，在运行时，包配置可能不会按照首选顺序加载。</span><span class="sxs-lookup"><span data-stu-id="7a76e-113">However, at run time, package configurations might not load in the preferred order.</span></span> <span data-ttu-id="7a76e-114">尤其是，父包配置将在其他类型的配置之后加载。</span><span class="sxs-lookup"><span data-stu-id="7a76e-114">In particular, parent package configurations load after configurations of other types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a76e-115">如果多个配置设置相同的对象属性，则在运行时使用最后加载的值。</span><span class="sxs-lookup"><span data-stu-id="7a76e-115">If multiple configurations set the same object property, the value loaded last is used at run time.</span></span>  
  
 <span data-ttu-id="7a76e-116">从 **“包配置组织程序”** 对话框中，可以运行包配置向导，该向导将指导您完成创建配置的步骤。</span><span class="sxs-lookup"><span data-stu-id="7a76e-116">From the **Package Configuration Organizer** dialog box, you run the Package Configuration Wizard, which guides you through the steps to create a configuration.</span></span> <span data-ttu-id="7a76e-117">若要运行包配置向导，请在 **“包配置组织程序”** 对话框中添加新配置，或编辑现有的配置。</span><span class="sxs-lookup"><span data-stu-id="7a76e-117">To run the Package Configuration Wizard, add a new configuration in the **Package Configurations Organizer** dialog box or edit an existing one.</span></span> <span data-ttu-id="7a76e-118">在向导的各页上，您可以选择配置类型，选择是直接访问配置还是使用环境变量，以及选择要在配置中保存的属性。</span><span class="sxs-lookup"><span data-stu-id="7a76e-118">On the wizard pages, you choose the configuration type, select whether you want to access the configuration directly or use environment variables, and select the properties to save in the configuration.</span></span>  
  
 <span data-ttu-id="7a76e-119">以下示例在包配置向导的“完成向导”页中出现变量和包时显示它们的目标属性。</span><span class="sxs-lookup"><span data-stu-id="7a76e-119">The following example shows the target properties of a variable and a package as they appear on the Completing the Wizard page of the Package Configuration Wizard.:</span></span>  
  
 <span data-ttu-id="7a76e-120">\Package.Variables[User::TodaysDate].Properties[RaiseChangedEvent]</span><span class="sxs-lookup"><span data-stu-id="7a76e-120">\Package.Variables[User::TodaysDate].Properties[RaiseChangedEvent]</span></span>  
  
 <span data-ttu-id="7a76e-121">\Package.Properties[MaximumErrorCount]</span><span class="sxs-lookup"><span data-stu-id="7a76e-121">\Package.Properties[MaximumErrorCount]</span></span>  
  
 <span data-ttu-id="7a76e-122">\Package.Properties[LoggingMode]</span><span class="sxs-lookup"><span data-stu-id="7a76e-122">\Package.Properties[LoggingMode]</span></span>  
  
 <span data-ttu-id="7a76e-123">\Package.Properties[LocaleID]</span><span class="sxs-lookup"><span data-stu-id="7a76e-123">\Package.Properties[LocaleID]</span></span>  
  
 <span data-ttu-id="7a76e-124">\Package\My SQL Task.Variables[User::varTableName].Properties[Value]</span><span class="sxs-lookup"><span data-stu-id="7a76e-124">\Package\My SQL Task.Variables[User::varTableName].Properties[Value]</span></span>  
  
 <span data-ttu-id="7a76e-125">在此示例中，配置将更新以下属性：</span><span class="sxs-lookup"><span data-stu-id="7a76e-125">In this example, the configuration updates these properties:</span></span>  
  
-   <span data-ttu-id="7a76e-126">用户定义变量 `TodaysDate`的 RaiseChangedEvent 属性。</span><span class="sxs-lookup"><span data-stu-id="7a76e-126">The RaiseChangedEvent property of user-defined variable, `TodaysDate`.</span></span>  
  
-   <span data-ttu-id="7a76e-127">包的 MaximumErrorCount、LoggingMode 和 LocaleID 属性。</span><span class="sxs-lookup"><span data-stu-id="7a76e-127">The MaximumErrorCount, LoggingMode, and LocaleID properties of the package.</span></span>  
  
-   <span data-ttu-id="7a76e-128">用户定义变量 `varTableName`在“我的 SQL 任务”的作用域内的 Value 属性。</span><span class="sxs-lookup"><span data-stu-id="7a76e-128">The Value property of user-defined variable, `varTableName`, within scope of the task, My SQL Task.</span></span>  
  
 <span data-ttu-id="7a76e-129">“\Package”表示根，句点 (.) 分隔用于定义配置所更新属性的路径的对象。</span><span class="sxs-lookup"><span data-stu-id="7a76e-129">The "\Package" represents the root, and periods (.) separate the objects that define the path to the property that the configuration updates.</span></span> <span data-ttu-id="7a76e-130">变量和属性的名称用括号括起。</span><span class="sxs-lookup"><span data-stu-id="7a76e-130">The names of variables and properties are enclosed in brackets.</span></span> <span data-ttu-id="7a76e-131">配置中始终使用术语“包”，而与包名称无关；但是，路径中的所有其他对象都使用其用户定义名称。</span><span class="sxs-lookup"><span data-stu-id="7a76e-131">The term Package is always used in configuration, regardless of the package name; however, all other objects in the path use their user-defined names.</span></span>  
  
 <span data-ttu-id="7a76e-132">在向导完成后，新的配置将添加到 **“包配置组织程序”** 对话框的配置列表中。</span><span class="sxs-lookup"><span data-stu-id="7a76e-132">After the wizard finishes, the new configuration is added to the configuration list in the **Package Configuration Organizer** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a76e-133">包配置向导的最后一页“完成向导”列出了配置中的目标属性。</span><span class="sxs-lookup"><span data-stu-id="7a76e-133">The last page in the Package Configuration Wizard, Completing the Wizard, lists the target properties in the configuration.</span></span> <span data-ttu-id="7a76e-134">如果希望通过使用 **dtexec** 命令提示符实用工具在运行包时更新属性，则可以通过运行包配置向导来生成表示属性路径的字符串，然后将它们复制并粘贴到命令提示符窗口中，以便用于 **dtexec**的设置选项。</span><span class="sxs-lookup"><span data-stu-id="7a76e-134">If you want to update properties when you run packages by using the **dtexec** command prompt utility, you can generate the strings that represent the property paths by running the Package Configuration Wizard and then copy and paste them into the command prompt window for use with the set option of **dtexec.**</span></span>  
  
 <span data-ttu-id="7a76e-135">下表介绍 **“包配置组织程序”** 对话框的配置列表中的各列。</span><span class="sxs-lookup"><span data-stu-id="7a76e-135">The following table describes the columns in the configuration list in the **Package Configuration Organizer** dialog box.</span></span>  
  
|<span data-ttu-id="7a76e-136">列</span><span class="sxs-lookup"><span data-stu-id="7a76e-136">Column</span></span>|<span data-ttu-id="7a76e-137">说明</span><span class="sxs-lookup"><span data-stu-id="7a76e-137">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7a76e-138">**配置名称**</span><span class="sxs-lookup"><span data-stu-id="7a76e-138">**Configuration Name**</span></span>|<span data-ttu-id="7a76e-139">配置的名称。</span><span class="sxs-lookup"><span data-stu-id="7a76e-139">The name of the configuration.</span></span>|  
|<span data-ttu-id="7a76e-140">**配置类型**</span><span class="sxs-lookup"><span data-stu-id="7a76e-140">**Configuration Type**</span></span>|<span data-ttu-id="7a76e-141">配置类型。</span><span class="sxs-lookup"><span data-stu-id="7a76e-141">The configuration type.</span></span>|  
|<span data-ttu-id="7a76e-142">**配置字符串**</span><span class="sxs-lookup"><span data-stu-id="7a76e-142">**Configuration String**</span></span>|<span data-ttu-id="7a76e-143">配置的位置。</span><span class="sxs-lookup"><span data-stu-id="7a76e-143">The location of the configuration.</span></span> <span data-ttu-id="7a76e-144">位置可以是路径、环境变量、注册表项、父包变量名或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="7a76e-144">The location can be a path, an environment variable, a Registry key, a parent package variable name, or a table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="7a76e-145">**目标对象**</span><span class="sxs-lookup"><span data-stu-id="7a76e-145">**Target Object**</span></span>|<span data-ttu-id="7a76e-146">其属性具有配置的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="7a76e-146">The name of the object with a property that has a configuration.</span></span> <span data-ttu-id="7a76e-147">如果配置是 XML 配置文件，则该列为空，因为该配置可以更新多个对象。</span><span class="sxs-lookup"><span data-stu-id="7a76e-147">If the configuration is an XML configuration file, the column is blank, because the configuration can update multiple objects.</span></span>|  
|<span data-ttu-id="7a76e-148">**目标属性**</span><span class="sxs-lookup"><span data-stu-id="7a76e-148">**Target Property**</span></span>|<span data-ttu-id="7a76e-149">属性的名称。</span><span class="sxs-lookup"><span data-stu-id="7a76e-149">The name of the property.</span></span> <span data-ttu-id="7a76e-150">如果配置写入 XML 配置文件或 SQL Server 表，则列为空，因为配置可以更新多个对象。</span><span class="sxs-lookup"><span data-stu-id="7a76e-150">If the configuration writes to an XML configuration file or a SQL Server table, the column is blank, because the configuration can update multiple objects.</span></span>|  
  
### <a name="to-create-a-package-configuration"></a><span data-ttu-id="7a76e-151">创建包配置</span><span class="sxs-lookup"><span data-stu-id="7a76e-151">To create a package configuration</span></span>  
  
1.  <span data-ttu-id="7a76e-152">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="7a76e-152">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="7a76e-153">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="7a76e-153">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="7a76e-154">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击 **“控制流”** 、 **“数据流”** 、 **“事件处理程序”** 或 **“包资源管理器”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7a76e-154">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow**, **Data Flow**, **Event Handler**, or **Package Explorer** tab.</span></span>  
  
4.  <span data-ttu-id="7a76e-155">在 **SSIS** 菜单上，单击 **“包配置”** 。</span><span class="sxs-lookup"><span data-stu-id="7a76e-155">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
5.  <span data-ttu-id="7a76e-156">在 **“包配置组织程序”** 对话框中，选择 **“启用包配置”** ，再单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="7a76e-156">In the **Package Configuration Organizer** dialog box, select **Enable package configurations**, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="7a76e-157">在“包配置向导”页的欢迎页上，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="7a76e-157">On the welcome page of the Package Configuration Wizard page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="7a76e-158">在“选择配置类型”页上，指定配置类型，然后设置与该配置类型相关的属性。</span><span class="sxs-lookup"><span data-stu-id="7a76e-158">On the Select Configuration Type page, specify the configuration type, and then set the properties that are relevant to the configuration type.</span></span> <span data-ttu-id="7a76e-159">有关详细信息，请参阅 [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="7a76e-159">For more information, see [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md).</span></span>  
  
8.  <span data-ttu-id="7a76e-160">在“选择要导出的属性”页上，选择要在配置中包括的包对象的属性。</span><span class="sxs-lookup"><span data-stu-id="7a76e-160">On the Select Properties to Export page, select the properties of package objects to include in the configuration.</span></span> <span data-ttu-id="7a76e-161">如果配置类型只支持一个属性，则此向导页的标题是“选择目标属性”。</span><span class="sxs-lookup"><span data-stu-id="7a76e-161">If the configuration type supports only one property, the title of this wizard page is Select Target Property.</span></span> <span data-ttu-id="7a76e-162">有关详细信息，请参阅 [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="7a76e-162">For more information, see [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a76e-163">只有 **XML 配置文件**和 **SQL Server** 配置类型支持在一个配置中包括多个属性。</span><span class="sxs-lookup"><span data-stu-id="7a76e-163">Only the **XML Configuration File** and **SQL Server** configuration types support including multiple properties in a configuration.</span></span>  
  
9. <span data-ttu-id="7a76e-164">在“完成向导”页上，键入配置的名称，然后单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="7a76e-164">On the Completing the Wizard page, type the name of the configuration, and then click **Finish**.</span></span>  
  
10. <span data-ttu-id="7a76e-165">查看 **“包配置组织程序”** 对话框中的配置。</span><span class="sxs-lookup"><span data-stu-id="7a76e-165">View the configuration in the **Package Configuration Organizer** dialog box.</span></span>  
  
11. <span data-ttu-id="7a76e-166">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="7a76e-166">Click **Close**.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="7a76e-167">外部资源</span><span class="sxs-lookup"><span data-stu-id="7a76e-167">External Resources</span></span>  
  
-   <span data-ttu-id="7a76e-168">msdn.microsoft.com 上的技术文章 [理解 Integration Services 包配置](https://go.microsoft.com/fwlink/?LinkId=165643)</span><span class="sxs-lookup"><span data-stu-id="7a76e-168">Technical article, [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="7a76e-169">Www.sqlis.com 上的博客文章[在代码包配置中创建包](https://go.microsoft.com/fwlink/?LinkId=217663)。</span><span class="sxs-lookup"><span data-stu-id="7a76e-169">Blog entry, [Creating packages in code - Package Configurations](https://go.microsoft.com/fwlink/?LinkId=217663), on www.sqlis.com.</span></span>  
  
-   <span data-ttu-id="7a76e-170">Blogs.msdn.com 上的博客文章[API 示例-以编程方式将配置文件添加到包](https://go.microsoft.com/fwlink/?LinkId=217664)。</span><span class="sxs-lookup"><span data-stu-id="7a76e-170">Blog entry, [API Sample - Programmatically add a configuration file to a package](https://go.microsoft.com/fwlink/?LinkId=217664), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a76e-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a76e-171">See Also</span></span>  
 <span data-ttu-id="7a76e-172">[包配置](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="7a76e-172">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="7a76e-173">[包部署 &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md) </span><span class="sxs-lookup"><span data-stu-id="7a76e-173">[Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md) </span></span>  
 [<span data-ttu-id="7a76e-174">以编程方式使用变量</span><span class="sxs-lookup"><span data-stu-id="7a76e-174">Working with Variables Programmatically</span></span>](building-packages-programmatically/working-with-variables-programmatically.md)  
  
  
