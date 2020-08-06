---
title: 步骤 4：添加包配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e04a5321-63d5-4ec5-85b9-cb4eaf6c87f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 416cf17f967a145fccef1341b77f71a02ff3f3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586831"
---
# <a name="step-4-adding-package-configurations"></a><span data-ttu-id="6664e-102">步骤 4：添加包配置</span><span class="sxs-lookup"><span data-stu-id="6664e-102">Step 4: Adding Package Configurations</span></span>
  <span data-ttu-id="6664e-103">在此任务中，将配置添加到每个包。</span><span class="sxs-lookup"><span data-stu-id="6664e-103">In this task, you will add a configuration to each package.</span></span> <span data-ttu-id="6664e-104">在运行时，配置更新包属性和包对象的值。</span><span class="sxs-lookup"><span data-stu-id="6664e-104">Configurations update the values of package properties and package objects at run time.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6664e-105">提供了各种配置类型。</span><span class="sxs-lookup"><span data-stu-id="6664e-105">provides a variety of configuration types.</span></span> <span data-ttu-id="6664e-106">您可以将配置存储在环境变量、注册表项、用户定义变量、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 表和 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="6664e-106">You can store configurations in environment variables, registry entries, user-defined variables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables, and XML files.</span></span> <span data-ttu-id="6664e-107">为了提供更大的灵活性， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 支持使用间接配置。</span><span class="sxs-lookup"><span data-stu-id="6664e-107">To provide additional flexibility, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] supports the use of indirect configurations.</span></span> <span data-ttu-id="6664e-108">这意味着可使用环境变量指定配置的位置，而配置又指定实际值。</span><span class="sxs-lookup"><span data-stu-id="6664e-108">This means that you use an environment variable to specify the location of the configuration, which in turn specifies the actual values.</span></span> <span data-ttu-id="6664e-109">Deployment Tutorial 项目中的包使用 XML 配置文件和间接配置的组合。</span><span class="sxs-lookup"><span data-stu-id="6664e-109">The packages in the Deployment Tutorial project use a combination of XML configuration files and indirect configurations.</span></span> <span data-ttu-id="6664e-110">一个 XML 配置文件可以包括多个属性的配置，并且在适当的时候还可以被多个包引用。</span><span class="sxs-lookup"><span data-stu-id="6664e-110">An XML configuration file can include configurations for multiple properties, and when appropriate, can be referenced by multiple packages.</span></span> <span data-ttu-id="6664e-111">在本教程中，对于每个包都将使用单独的配置文件。</span><span class="sxs-lookup"><span data-stu-id="6664e-111">In this tutorial, you will use a separate configuration file for each package.</span></span>  
  
 <span data-ttu-id="6664e-112">配置文件通常包含敏感信息，如连接字符串。</span><span class="sxs-lookup"><span data-stu-id="6664e-112">Configuration files frequently contain sensitive information such as connection strings.</span></span> <span data-ttu-id="6664e-113">因此，您应该使用访问控制列表 (ACL) 限制对存储这些文件的位置或文件夹的访问，并仅向被允许运行包的用户或帐户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="6664e-113">Therefore, you should use an access control list (ACL) to restrict access to the location or folder where you store the files, and give access only to users or accounts that are permitted to run packages.</span></span> <span data-ttu-id="6664e-114">有关详细信息，请参阅 [访问包使用的文件](../../2014/integration-services/access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="6664e-114">For more information, see [Access to Files Used by Packages](../../2014/integration-services/access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="6664e-115">这些包（即 DataTransfer 和 LoadXMLData，在上一任务中已添加到 Deployment Tutorial 项目）需要有配置，才能在部署到目标服务器后成功运行。</span><span class="sxs-lookup"><span data-stu-id="6664e-115">The packages (DataTransfer and LoadXMLData) that you added to the Deployment Tutorial project in the previous task need configurations to run successfully after they are deployed to the target server.</span></span> <span data-ttu-id="6664e-116">若要实现配置，请首先为 XML 配置文件创建间接配置，再创建 XML 配置文件。</span><span class="sxs-lookup"><span data-stu-id="6664e-116">To implement configurations, you will first create the indirect configurations for the XML configuration files, and then you will create the XML configuration files.</span></span>  
  
 <span data-ttu-id="6664e-117">您将创建两个配置文件，即 DataTransferConfig.dtsConfig 和 LoadXMLData.dtsConfig。</span><span class="sxs-lookup"><span data-stu-id="6664e-117">You will create two configuration files, DataTransferConfig.dtsConfig and LoadXMLData.dtsConfig.</span></span> <span data-ttu-id="6664e-118">这些文件包含更新包中属性（指定包所用的数据文件和日志文件的位置）的“名称-值”对。</span><span class="sxs-lookup"><span data-stu-id="6664e-118">These files contain name-value pairs that update the properties in packages that specify the location of the data and log files used by the package.</span></span> <span data-ttu-id="6664e-119">稍后，作为部署过程中的一个步骤，您将更新配置文件中的值，以反映文件在目标计算机上的新位置。</span><span class="sxs-lookup"><span data-stu-id="6664e-119">Later, as a step in the deployment process, you will update the values in the configuration files to reflect the new location of the files on the destination computer.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6664e-120">识别出 DataTransferConfig.dtsConfig 和 LoadXMLData.dtsConfig 是 DataTransfer 和 LoadXMLData 包的依赖项，在下一课中创建部署捆绑包时它会自动包括配置文件。</span><span class="sxs-lookup"><span data-stu-id="6664e-120">recognizes that the DataTransferConfig.dtsConfig and LoadXMLData.dtsConfig are dependencies of the DataTransfer and LoadXMLData packages, and automatically includes the configuration files when you create the deployment bundle in the next lesson.</span></span>  
  
### <a name="to-create-indirect-configuration-for-the-datatransfer-package"></a><span data-ttu-id="6664e-121">为 DataTransfer 包创建间接配置</span><span class="sxs-lookup"><span data-stu-id="6664e-121">To create indirect configuration for the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="6664e-122">在解决方案资源管理器中，双击 DataTransfer.dtsx。</span><span class="sxs-lookup"><span data-stu-id="6664e-122">In Solution Explorer, double-click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="6664e-123">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，在控制流设计图面背景中的任意位置单击。</span><span class="sxs-lookup"><span data-stu-id="6664e-123">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="6664e-124">在 **SSIS** 菜单上，单击 **“包配置”** 。</span><span class="sxs-lookup"><span data-stu-id="6664e-124">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="6664e-125">在“包配置管理器”对话框中，选择“启用包配置”（如果尚未选择），再单击“添加”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-125">In the **Package Configuration Organize**r dialog box, select **Enable package configurations** if it is not already selected, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="6664e-126">在包配置向导的欢迎页中，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6664e-126">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="6664e-127">在 "选择配置类型" 页上，选择 "**配置类型**" 列表中的 " **XML 配置文件**"，选择 "**配置位置存储在一个环境变量**中" 选项，然后键入 `DataTransfer,` 或选择列表中的**DataTransfer**环境变量。</span><span class="sxs-lookup"><span data-stu-id="6664e-127">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list, select the **Configuration location is stored in an environment variable** option, and type `DataTransfer,` or select the **DataTransfer** environment variable in the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6664e-128">为了使该环境变量在列表中可用，您最好在添加该变量后重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="6664e-128">To make the environment variable available in the list, you may have to restart your computer after adding the variable.</span></span> <span data-ttu-id="6664e-129">如果不希望重新启动计算机，则可以键入该环境变量的名称。</span><span class="sxs-lookup"><span data-stu-id="6664e-129">If you do not want to restart the computer, you can type the name of the environment variable.</span></span>  
  
7.  <span data-ttu-id="6664e-130">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6664e-130">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="6664e-131">在“完成向导”页上，在“配置名称”框中键入“DataTransfer EV Configuration”，在“预览”窗格中查看配置内容，然后单击“完成”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-131">On the Completing the Wizard page, type **DataTransfer EV Configuration** in the **Configuration name** box, review the configuration contents in the **Preview** pane, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="6664e-132">关闭“包配置管理器”对话框。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-132">Close the **Package Configuration Organize**r dialog box.</span></span>  
  
### <a name="to-create-the-xml-configuration-for-the-datatransfer-package"></a><span data-ttu-id="6664e-133">为 DataTransfer 包创建 XML 配置</span><span class="sxs-lookup"><span data-stu-id="6664e-133">To create the XML configuration for the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="6664e-134">在解决方案资源管理器中，双击 DataTransfer.dtsx。</span><span class="sxs-lookup"><span data-stu-id="6664e-134">In Solution Explorer, double-click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="6664e-135">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，在控制流设计图面背景中的任意位置单击。</span><span class="sxs-lookup"><span data-stu-id="6664e-135">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="6664e-136">在 **SSIS** 菜单上，单击 **“包配置”** 。</span><span class="sxs-lookup"><span data-stu-id="6664e-136">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="6664e-137">在“包配置管理器”对话框中，选中“启用包配置”复选框，然后单击“添加”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-137">In the Package Configuration Organizer dialog box, select the **Enable Package Configurations** check-box, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="6664e-138">在包配置向导的欢迎页中，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6664e-138">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="6664e-139">在“选择配置类型”页上，选择“配置类型”列表中的“XML 配置文件”后，单击“浏览”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-139">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list and then click **Browse**.</span></span>  
  
7.  <span data-ttu-id="6664e-140">在“选择配置文件位置”对话框中，导航到 C:\DeploymentTutorial，在“文件名”框中键入“DataTransferConfig”，然后单击“保存”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-140">In **Select Configuration File Location** dialog box, navigate to C:\DeploymentTutorial and type **DataTransferConfig** in the **File name** box, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="6664e-141">在“选择配置类型”页上，单击“下一步”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-141">On the Select Configuration Type page, click **Next**.</span></span>  
  
9. <span data-ttu-id="6664e-142">在“选择要导出的属性”页上，依次展开“DataTransfer”、“连接管理器”、“部署 Tutorial 日志”和“属性”，然后选中“连接字符串”复选框。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-142">On the Select Properties to Export page, expand DataTransfer, Connection Managers, Deployment Tutorial Log, and Properties, and then select the **Connection String** check-box.</span></span>  
  
10. <span data-ttu-id="6664e-143">在“连接管理器”内，展开“NewCustomers”后，选中“连接字符串”复选框。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-143">Within Connection Managers, expand NewCustomers, and then select the **Connection String** check-box.</span></span>  
  
11. <span data-ttu-id="6664e-144">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6664e-144">Click **Next**.</span></span>  
  
12. <span data-ttu-id="6664e-145">在“完成向导”页上，在“配置名称”框中键入“DataTransfer 配置”，查看配置的内容，然后单击“完成”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-145">On the Completing the Wizard page, type **DataTransfer Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="6664e-146">在“包配置管理器”对话框中，验证是否第一个列出“DataTransfer EV 配置”，第二个列出“DataTransfer 配置”，然后单击“关闭”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-146">In the **Package Configuration Organizer** dialog box, verify that DataTransfer EV Configuration is listed first, and DataTransfer Configuration is listed second, and then click **Close**.</span></span>  
  
### <a name="to-create-indirect-configuration-for-the-loadxmldata-package"></a><span data-ttu-id="6664e-147">为 LoadXMLData 包创建间接配置</span><span class="sxs-lookup"><span data-stu-id="6664e-147">To create indirect configuration for the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="6664e-148">在解决方案资源管理器中，双击 LoadXMLData.dtsx。</span><span class="sxs-lookup"><span data-stu-id="6664e-148">In Solution Explorer, double-click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="6664e-149">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，在控制流设计图面背景中的任意位置单击。</span><span class="sxs-lookup"><span data-stu-id="6664e-149">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="6664e-150">在 **SSIS** 菜单上，单击 **“包配置”** 。</span><span class="sxs-lookup"><span data-stu-id="6664e-150">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="6664e-151">在“包配置管理器”对话框中，单击“添加”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-151">In the **Package Configuration Organize**r dialog box, Click **Add**.</span></span>  
  
5.  <span data-ttu-id="6664e-152">在包配置向导的欢迎页中，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6664e-152">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="6664e-153">在 "选择配置类型" 页上，选择 "**配置类型**" 列表中的 " **XML 配置文件**"，选择 "**配置位置存储在环境变量**中" 选项，键入 `LoadXMLData` 或选择 `LoadXMLData` 列表中的环境变量。</span><span class="sxs-lookup"><span data-stu-id="6664e-153">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list, select the **Configuration location is stored in an environment variable** option, type `LoadXMLData` or select the `LoadXMLData` environment variable in the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6664e-154">为了使该环境变量在列表中可用，您最好在添加该变量后重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="6664e-154">To make the environment variable available in the list, you may have to restart your computer after adding the variable.</span></span>  
  
7.  <span data-ttu-id="6664e-155">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6664e-155">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="6664e-156">在“完成向导”页上，在“配置名称”框中键入“LoadXMLData EV 配置”，查看配置的内容，然后单击“完成”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-156">On the Completing the Wizard page, type **LoadXMLData EV Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
### <a name="to-create-the-xml-configuration-for-the-loadxmldata-package"></a><span data-ttu-id="6664e-157">为 LoadXMLData 包创建 XML 配置</span><span class="sxs-lookup"><span data-stu-id="6664e-157">To create the XML configuration for the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="6664e-158">在解决方案资源管理器中，双击 LoadXMLData.dtsx。</span><span class="sxs-lookup"><span data-stu-id="6664e-158">In Solution Explorer, double-click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="6664e-159">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，在控制流设计图面背景中的任意位置单击。</span><span class="sxs-lookup"><span data-stu-id="6664e-159">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="6664e-160">在 **SSIS** 菜单上，单击 **“包配置”** 。</span><span class="sxs-lookup"><span data-stu-id="6664e-160">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="6664e-161">在“包配置管理器”对话框中，选中“启用包配置”复选框，然后单击“添加”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-161">In the Package Configuration Organizer dialog box, select the **Enable Package Configurations** check-box, and click **Add**.</span></span>  
  
5.  <span data-ttu-id="6664e-162">在包配置向导的欢迎页中，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6664e-162">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="6664e-163">在“选择配置类型”页上，选择“配置类型”列表中的“XML 配置文件”，然后单击“浏览”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-163">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list and click **Browse**.</span></span>  
  
7.  <span data-ttu-id="6664e-164">在“选择配置文件位置”对话框中，导航到 C:\DeploymentTutorial，在“文件名”框中键入“LoadXMLDataConfig”，然后单击“保存”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-164">In **Select Configuration File Location** dialog box, navigate to C:\DeploymentTutorial and type **LoadXMLDataConfig** in the **File name** box, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="6664e-165">在“选择配置类型”页上，单击“下一步”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-165">On the Select Configuration Type page, click **Next**.</span></span>  
  
9. <span data-ttu-id="6664e-166">在“选择要导出的属性”页上，依次展开“LoadXMLData”、“可执行文件”、“加载 XML 数据”和“属性”，然后选中“[XMLSource].[XMLData]”和“[XMLSource].[XMLSchemaDefinition]”复选框。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-166">On the Select Properties to Export page, expand LoadXMLData, Executables, Load XML Data, and Properties, and then select the **[XMLSource].[XMLData]** and **[XMLSource].[XMLSchemaDefinition]** check boxes.</span></span>  
  
10. <span data-ttu-id="6664e-167">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6664e-167">Click **Next**.</span></span>  
  
11. <span data-ttu-id="6664e-168">在“完成向导”页上，在“配置名称”框中键入“LoadXMLData 配置”，查看配置的内容，然后单击“完成”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-168">On the Completing the Wizard page, type **LoadXMLData Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
12. <span data-ttu-id="6664e-169">在“包配置管理器”对话框中，验证是否第一个列出“LoadXMLData EV 配置”，第二个列出“LoadXMLData 配置”，然后单击“关闭”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6664e-169">In the **Package Configuration Organizer** dialog box, verify that the LoadXMLData EV Configuration is listed first, and the LoadXMLData Configuration is listed second, and then click **Close**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6664e-170">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="6664e-170">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6664e-171">步骤 5：测试更新的包</span><span class="sxs-lookup"><span data-stu-id="6664e-171">Step 5: Testing the Updated Packages</span></span>](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
<span data-ttu-id="6664e-172">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6664e-172">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6664e-173">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="6664e-173">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6664e-174">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="6664e-174">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6664e-175">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="6664e-175">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6664e-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6664e-176">See Also</span></span>  
 <span data-ttu-id="6664e-177">[包配置](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="6664e-177">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="6664e-178">[创建包配置](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="6664e-178">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 [<span data-ttu-id="6664e-179">对包使用的文件的访问</span><span class="sxs-lookup"><span data-stu-id="6664e-179">Access to Files Used by Packages</span></span>](../../2014/integration-services/access-to-files-used-by-packages.md)  
  
  
