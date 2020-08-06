---
title: 步骤 2：启用和配置包配置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a804efcd84ebe563a13f61443fe19096788ca809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579630"
---
# <a name="step-2-enabling-and-configuring-package-configurations"></a><span data-ttu-id="94f12-102">步骤 2：启用和配置包配置</span><span class="sxs-lookup"><span data-stu-id="94f12-102">Step 2: Enabling and Configuring Package Configurations</span></span>
  <span data-ttu-id="94f12-103">在此任务中，您将项目转换为包部署模型并使用包配置向导配置包。</span><span class="sxs-lookup"><span data-stu-id="94f12-103">In this task, you will convert the project to the Package Deployment Model and enable package configurations using the Package Configuration Wizard.</span></span> <span data-ttu-id="94f12-104">您将使用该向导生成 XML 配置文件，该文件包含 Foreach 循环容器的 `Directory` 属性的配置设置。</span><span class="sxs-lookup"><span data-stu-id="94f12-104">You will use this wizard to generate an XML configuration file that contains configuration settings for the `Directory` property of the Foreach Loop container.</span></span> <span data-ttu-id="94f12-105">Directory 属性的值由新的包级别变量在运行时提供，您可以更新该变量。</span><span class="sxs-lookup"><span data-stu-id="94f12-105">The value of the Directory property is supplied by a new package-level variable that you can update at run time.</span></span> <span data-ttu-id="94f12-106">另外，将填充要在测试期间使用的新的示例数据文件夹。</span><span class="sxs-lookup"><span data-stu-id="94f12-106">Additionally, you will populate a new sample data folder to use during testing.</span></span>  
  
### <a name="to-create-a-new-package-level-variable-mapped-to-the-directory-property"></a><span data-ttu-id="94f12-107">创建映射到 Directory 属性的新的包级别变量</span><span class="sxs-lookup"><span data-stu-id="94f12-107">To create a new package-level variable mapped to the Directory property</span></span>  
  
1.  <span data-ttu-id="94f12-108">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击“控制流”\*\*\*\* 选项卡的背景。</span><span class="sxs-lookup"><span data-stu-id="94f12-108">Click the background of the **Control Flow** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="94f12-109">这会将要创建的变量的作用域设置为包。</span><span class="sxs-lookup"><span data-stu-id="94f12-109">This sets the scope for the variable you will create to the package.</span></span>  
  
2.  <span data-ttu-id="94f12-110">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 菜单中，选择“变量”  。</span><span class="sxs-lookup"><span data-stu-id="94f12-110">On the [!INCLUDE[ssIS](../includes/ssis-md.md)] menu, select **Variables**.</span></span>  
  
3.  <span data-ttu-id="94f12-111">在 **“变量”** 窗口中，单击 “添加变量” 图标。</span><span class="sxs-lookup"><span data-stu-id="94f12-111">In the **Variables** window, click the Add Variable icon.</span></span>  
  
4.  <span data-ttu-id="94f12-112">在“名称”\*\*\*\* 框中，键入 **varFolderName**。</span><span class="sxs-lookup"><span data-stu-id="94f12-112">In the **Name** box, type **varFolderName**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="94f12-113">变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="94f12-113">Variable names are case sensitive.</span></span>  
  
5.  <span data-ttu-id="94f12-114">验证 "**作用域**" 框是否显示包的名称，第5课。</span><span class="sxs-lookup"><span data-stu-id="94f12-114">Verify that the **Scope** box shows the name of the package, Lesson 5.</span></span>  
  
6.  <span data-ttu-id="94f12-115">将 `varFolderName` 变量的“数据类型”  框的值设置为“字符串”  。</span><span class="sxs-lookup"><span data-stu-id="94f12-115">Set the value of the **Data Type** box of the `varFolderName` variable to **String**.</span></span>  
  
7.  <span data-ttu-id="94f12-116">返回到“控制流”  选项卡，然后双击“文件夹中的 Foreach 文件”  容器。</span><span class="sxs-lookup"><span data-stu-id="94f12-116">Return to the **Control Flow** tab and double-click the **Foreach File in Folder** container.</span></span>  
  
8.  <span data-ttu-id="94f12-117">在 " **Foreach 循环编辑器**" 的 "**集合**" 页上，单击 "**表达式**"，然后单击省略号按钮 " \*\* ( ..." ) \*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-117">On the **Collection** page of the **Foreach Loop Editor**, click **Expressions**, and then click the ellipsis button **(...)**.</span></span>  
  
9. <span data-ttu-id="94f12-118">在 "**属性表达式编辑器**" 中，单击**属性**列表，然后选择 `Directory` 。</span><span class="sxs-lookup"><span data-stu-id="94f12-118">In the **Property Expressions Editor**, click in the **Property** list, and select `Directory`.</span></span>  
  
10. <span data-ttu-id="94f12-119">在 "**表达式**" 框中，单击省略号按钮 " \*\* ( ..." ) \*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-119">In the **Expression** box, click the ellipsis button **(...)**.</span></span>  
  
11. <span data-ttu-id="94f12-120">在“表达式生成器”\*\*\*\* 中，展开“变量”文件夹，然后将变量 **User::varFolderName** 拖到“表达式”\*\*\*\* 框中。</span><span class="sxs-lookup"><span data-stu-id="94f12-120">In the **Expression Builder**, expand the Variables folder, and drag the variable **User::varFolderName** to the **Expression** box.</span></span>  
  
12. <span data-ttu-id="94f12-121">单击“确定”\*\*\*\* 退出“表达式生成器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-121">Click **OK** to exit the **Expression Builder**.</span></span>  
  
13. <span data-ttu-id="94f12-122">单击“确定”\*\*\*\* 退出“属性表达式编辑器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-122">Click **OK** to exit the **Property Expressions Editor**.</span></span>  
  
14. <span data-ttu-id="94f12-123">单击“确定”\*\*\*\* 退出“Foreach 循环编辑器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-123">Click **OK** to exit the **Foreach Loop Editor**.</span></span>  
  
### <a name="to-enable-package-configurations"></a><span data-ttu-id="94f12-124">启用包配置</span><span class="sxs-lookup"><span data-stu-id="94f12-124">To enable package configurations</span></span>  
  
1.  <span data-ttu-id="94f12-125">在 "**项目" 菜单**上，单击 "**转换为包部署模型**"。</span><span class="sxs-lookup"><span data-stu-id="94f12-125">On the **Project Menu**, click **Convert to Package Deployment Model**.</span></span>  
  
2.  <span data-ttu-id="94f12-126">出现警告提示时单击“确定”\*\*\*\*，转换完成后，在“转换为包部署模型”\*\*\*\* 对话框中单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-126">Click **OK** on the warning prompt and, once the conversion is complete, click **OK** on the **Convert to Package Deployment Model** dialog.</span></span>  
  
3.  <span data-ttu-id="94f12-127">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击“控制流”\*\*\*\* 选项卡的背景。</span><span class="sxs-lookup"><span data-stu-id="94f12-127">Click the background of the **Control Flow** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
4.  <span data-ttu-id="94f12-128">在 **SSIS** 菜单上，单击 **“包配置”** 。</span><span class="sxs-lookup"><span data-stu-id="94f12-128">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
5.  <span data-ttu-id="94f12-129">在“包配置组织程序”\*\*\*\* 对话框中，选择“启用包配置”\*\*\*\*，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-129">In the **Package Configurations Organizer** dialog box, select **Enable Package Configurations**, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="94f12-130">在包配置向导的欢迎页中，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-130">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
7.  <span data-ttu-id="94f12-131">在“选择配置类型”  页上，确认“配置类型”  已设置为“XML 配置文件”  。</span><span class="sxs-lookup"><span data-stu-id="94f12-131">On the **Select Configuration Type** page, verify that the **Configuration type** is set to **XML configuration file**.</span></span>  
  
8.  <span data-ttu-id="94f12-132">在“选择配置类型”\*\*\*\* 页上，单击“浏览”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-132">On the **Select Configuration Type** page, click **Browse**.</span></span>  
  
9. <span data-ttu-id="94f12-133">默认情况下，“选择配置文件位置”\*\*\*\* 对话框将打开至项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="94f12-133">By default, the **Select Configuration File Location** dialog box will open to the project folder.</span></span>  
  
10. <span data-ttu-id="94f12-134">在“选择配置文件位置”\*\*\*\* 对话框的“文件名”\*\*\*\* 中，键入 **SSISTutorial**，然后单击“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-134">In the **Select Configuration File Location** dialog box, for **File name** type **SSISTutorial**, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="94f12-135">在 "**选择配置类型**" 页上，单击 "**下一步"。**</span><span class="sxs-lookup"><span data-stu-id="94f12-135">On the **Select Configuration Type** page, click **Next.**</span></span>  
  
12. <span data-ttu-id="94f12-136">在 "**选择要导出的属性**" 页上的 "**对象**" 窗格中，展开 "**变量**"，展开 " **varFolderName**"，展开 "**属性**"，然后选择 "**值**"。</span><span class="sxs-lookup"><span data-stu-id="94f12-136">On the **Select Properties to Export** page, in the **Objects** pane, expand **Variables**, expand **varFolderName**, expand **Properties**, and then select **Value**.</span></span>  
  
13. <span data-ttu-id="94f12-137">在“选择要导出的属性”\*\*\*\* 页上，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94f12-137">On the **Select Properties to Export** page, click **Next**.</span></span>  
  
14. <span data-ttu-id="94f12-138">在“完成向导”\*\*\*\* 页上，键入该配置的配置名称，例如 **SSIS Tutorial Directory configuration**。</span><span class="sxs-lookup"><span data-stu-id="94f12-138">On the **Completing the Wizard** page, type a configuration name for the configuration, such as **SSIS Tutorial Directory configuration**.</span></span> <span data-ttu-id="94f12-139">这是显示在“包配置组织程序”\*\*\*\* 对话框中的配置名称。</span><span class="sxs-lookup"><span data-stu-id="94f12-139">This is the configuration name that is displayed in the **Package Configuration Organizer** dialog box.</span></span>  
  
15. <span data-ttu-id="94f12-140">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="94f12-140">Click **Finish**.</span></span>  
  
16. <span data-ttu-id="94f12-141">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="94f12-141">Click **Close**.</span></span>  
  
17. <span data-ttu-id="94f12-142">向导将创建一个名为 Ssistutorial.dtsconfig. Datatransferconfig.dtsconfig 的配置文件，该配置文件包含变量的配置设置，后者 `value` 又设置了 `Directory` 枚举器的属性。</span><span class="sxs-lookup"><span data-stu-id="94f12-142">The wizard creates a configuration file, named SSISTutorial.dtsConfig, that contains configuration settings for the `value` of the variable that in turn sets the `Directory` property of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="94f12-143">配置文件通常包含有关包属性的复杂信息，但对于本教程，唯一的配置信息应当是</span><span class="sxs-lookup"><span data-stu-id="94f12-143">A configuration file typically contains complex information about the package properties, but for this tutorial the only configuration information should be</span></span>  
    > <span data-ttu-id="94f12-144"><Configuration ConfiguredType="Property"</span><span class="sxs-lookup"><span data-stu-id="94f12-144"><Configuration ConfiguredType="Property"</span></span>  
    > <span data-ttu-id="94f12-145">Path = "\Package.Variables [User：： varFolderName]。Properties [值] "ValueType =" String "\></span><span class="sxs-lookup"><span data-stu-id="94f12-145">Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"\></span></span>  
    >  \<ConfiguredValue>\</ConfiguredValue>  
    > <span data-ttu-id="94f12-146">\</Configuration>.</span><span class="sxs-lookup"><span data-stu-id="94f12-146">\</Configuration>.</span></span>  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a><span data-ttu-id="94f12-147">创建并填充新的示例数据文件夹</span><span class="sxs-lookup"><span data-stu-id="94f12-147">To create and populate a new sample data folder</span></span>  
  
1.  <span data-ttu-id="94f12-148">在 Windows 资源管理器中，在驱动器的根级别 (例如，C： \\) ，请创建名为的新文件夹 `New Sample Data` 。</span><span class="sxs-lookup"><span data-stu-id="94f12-148">In Windows Explorer, at the root level of your drive (for example, C:\\), create a new folder named `New Sample Data`.</span></span>  
  
2.  <span data-ttu-id="94f12-149">找到计算机上的示例文件并从文件夹复制其中的三个文件。</span><span class="sxs-lookup"><span data-stu-id="94f12-149">Locate the sample files on your computer and copy three of the files from the folder.</span></span>  
  
3.  <span data-ttu-id="94f12-150">在该 `New Sample Data` 文件夹中，粘贴复制的文件。</span><span class="sxs-lookup"><span data-stu-id="94f12-150">In the `New Sample Data` folder, paste the copied files.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="94f12-151">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="94f12-151">Next Task in Lesson</span></span>  
 [<span data-ttu-id="94f12-152">步骤 3：修改目录属性配置值</span><span class="sxs-lookup"><span data-stu-id="94f12-152">Step 3: Modifying the Directory Property Configuration Value</span></span>](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
  
