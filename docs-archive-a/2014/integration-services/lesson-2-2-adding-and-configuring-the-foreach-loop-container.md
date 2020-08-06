---
title: 步骤 2：添加和配置 Foreach 循环容器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de5e8875c43edda618ccef4839c88c3b84a003cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578311"
---
# <a name="step-2-adding-and-configuring-the-foreach-loop-container"></a><span data-ttu-id="27d42-102">步骤 2：添加和配置 Foreach 循环容器</span><span class="sxs-lookup"><span data-stu-id="27d42-102">Step 2: Adding and Configuring the Foreach Loop Container</span></span>
  <span data-ttu-id="27d42-103">在本任务中，将添加循环访问平面文件的文件夹的功能，并将第 1 课中使用的同一数据流转换应用于其中的每个平面文件。</span><span class="sxs-lookup"><span data-stu-id="27d42-103">In this task, you will add the ability to loop through a folder of flat files and apply the same data flow transformation used in Lesson 1 to each of those flat files.</span></span> <span data-ttu-id="27d42-104">实现方法是将 Foreach 循环容器添加到控制流中并进行配置。</span><span class="sxs-lookup"><span data-stu-id="27d42-104">You do this by adding and configuring a Foreach Loop container to the control flow.</span></span>  
  
 <span data-ttu-id="27d42-105">所添加的 Foreach 循环容器必须能够连接到该文件夹中的每个平面文件。</span><span class="sxs-lookup"><span data-stu-id="27d42-105">The Foreach Loop container that you add must be able to connect to each flat file in the folder.</span></span> <span data-ttu-id="27d42-106">由于该文件夹中的所有文件都具有相同的格式，因此，Foreach 循环容器可以使用同一平面文件连接管理器来连接其中的每个文件。</span><span class="sxs-lookup"><span data-stu-id="27d42-106">Because all the files in the folder have the same format, the Foreach Loop container can use the same Flat File connection manager to connect to each of these files.</span></span> <span data-ttu-id="27d42-107">该容器所使用的平面文件连接管理器与您在第 1 课中创建的平面文件连接管理器相同。</span><span class="sxs-lookup"><span data-stu-id="27d42-107">The Flat File connection manager that the container will use is the same Flat File connection manager that you created in Lesson 1.</span></span>  
  
 <span data-ttu-id="27d42-108">目前，第 1 课中的平面文件连接管理器只连接一个特定的平面文件。</span><span class="sxs-lookup"><span data-stu-id="27d42-108">Currently, the Flat File connection manager from Lesson 1 connects to only one, specific flat file.</span></span> <span data-ttu-id="27d42-109">若要循环地连接该文件夹中的每个平面文件，必须同时对 Foreach 循环容器和平面文件连接管理器进行如下配置：</span><span class="sxs-lookup"><span data-stu-id="27d42-109">To iteratively connect to each flat file in the folder, you will have to configure both the Foreach Loop container and the Flat File connection manager as follows:</span></span>  
  
-   <span data-ttu-id="27d42-110">**Foreach 循环容器** ：将该容器的枚举值映射为用户定义的包变量。</span><span class="sxs-lookup"><span data-stu-id="27d42-110">**Foreach Loop container:** You will map the enumerated value of the container to a user-defined package variable.</span></span> <span data-ttu-id="27d42-111">然后，该容器将使用此用户定义变量来动态修改平面文件连接管理器的 `ConnectionString` 属性，并循环连接该文件夹中的每个平面文件。</span><span class="sxs-lookup"><span data-stu-id="27d42-111">The container will then use this user-defined variable to dynamically modify the `ConnectionString` property of the Flat File connection manager and iteratively connect to each flat file in the folder.</span></span>  
  
-   <span data-ttu-id="27d42-112">**平面文件连接管理器：** 您将修改在第1课中创建的连接管理器，方法是使用用户定义的变量填充连接管理器的 `ConnectionString` 属性。</span><span class="sxs-lookup"><span data-stu-id="27d42-112">**Flat File connection manager:** You will modify the connection manager that was created in Lesson 1 by using a user-defined variable to populate the connection manager's `ConnectionString` property.</span></span>  
  
 <span data-ttu-id="27d42-113">本任务中的过程向您显示如何创建和修改 Foreach 循环容器以使用用户定义的包变量，以及如何将数据流任务添加到该循环中。</span><span class="sxs-lookup"><span data-stu-id="27d42-113">The procedures in this task show you how to create and modify the Foreach Loop container to use a user-defined package variable and to add the data flow task to the loop.</span></span> <span data-ttu-id="27d42-114">您将了解改平面文件连接管理器，以便在下一任务中使用用户定义的变量。</span><span class="sxs-lookup"><span data-stu-id="27d42-114">You will learn how to modify the Flat File connection manager to use a user-defined variable in the next task.</span></span>  
  
 <span data-ttu-id="27d42-115">在对该包进行这些修改后，当该包运行时，Foreach 循环容器将循环访问示例数据文件夹中的文件集合。</span><span class="sxs-lookup"><span data-stu-id="27d42-115">After you have made these modifications to the package, when the package is run, the Foreach Loop Container will iterate through the collection of files in the Sample Data folder.</span></span> <span data-ttu-id="27d42-116">每次找到一个与条件相匹配的文件时，Foreach 循环容器都会用文件名填充用户定义的变量，将用户定义的变量映射到 Sample Currency Data 平面文件连接管理器的 `ConnectionString` 属性，然后对该文件运行数据流。</span><span class="sxs-lookup"><span data-stu-id="27d42-116">Each time a file is found that matches the criteria, the Foreach Loop Container will populate the user-defined variable with the file name, map the user-defined variable to the `ConnectionString` property of the Sample Currency Data Flat File connection manager, and then run the data flow against that file.</span></span> <span data-ttu-id="27d42-117">因此，在 Foreach 循环的每次迭代中，数据流任务都将使用一个不同的平面文件。</span><span class="sxs-lookup"><span data-stu-id="27d42-117">Therefore, in each iteration of the Foreach Loop the Data Flow task will consume a different flat file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27d42-118">由于 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 区分控制流和数据流，因此添加到控制流的任何循环都不需要对数据流进行修改。</span><span class="sxs-lookup"><span data-stu-id="27d42-118">Because [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separates control flow from data flow, any looping that you add to the control flow will not require modification to the data flow.</span></span> <span data-ttu-id="27d42-119">因此，无需更改在第 1 课中创建的数据流。</span><span class="sxs-lookup"><span data-stu-id="27d42-119">Therefore, the data flow that you created in Lesson 1 does not have to be changed.</span></span>  
  
### <a name="to-add-a-foreach-loop-container"></a><span data-ttu-id="27d42-120">添加 Foreach 循环容器</span><span class="sxs-lookup"><span data-stu-id="27d42-120">To add a Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="27d42-121">在“SQL Server Data Tools”\*\*\*\* 中，单击“控制流”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="27d42-121">In **SQL Server Data Tools**, click the **Control Flow** tab.</span></span>  
  
2.  <span data-ttu-id="27d42-122">在“SSIS 工具箱”  中，展开“容器”  ，然后将“Foreach 循环容器”  拖到“控制流”  选项卡的设计图面上。</span><span class="sxs-lookup"><span data-stu-id="27d42-122">In the **SSIS Toolbox**, expand **Containers**, and then drag a **Foreach Loop Container** onto the design surface of the **Control Flow** tab.</span></span>  
  
3.  <span data-ttu-id="27d42-123">右键单击新添加的“Foreach 循环容器”\*\*\*\*，然后选择“编辑”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27d42-123">Right-click the newly added **Foreach Loop Container** and select **Edit**.</span></span>  
  
4.  <span data-ttu-id="27d42-124">在 " **Foreach 循环编辑器**" 对话框的 "**常规**" 页上，对于 "**名称**"，输入 `Foreach File in Folder` 。</span><span class="sxs-lookup"><span data-stu-id="27d42-124">In the **Foreach Loop Editor** dialog box, on the **General** page, for **Name**, enter `Foreach File in Folder`.</span></span> <span data-ttu-id="27d42-125">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="27d42-125">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="27d42-126">右键单击 "Foreach 循环容器"，单击 "**属性**"，然后在 "属性窗口中，验证 `LocaleID` 属性是否设置为"\*\*英语 (美国 ") \*\*"。</span><span class="sxs-lookup"><span data-stu-id="27d42-126">Right-click the Foreach Loop container, click **Properties**, and in the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a><span data-ttu-id="27d42-127">为 Foreach 循环容器配置枚举器</span><span class="sxs-lookup"><span data-stu-id="27d42-127">To configure the enumerator for the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="27d42-128">双击文件夹中的 "Foreach 文件" 以重新打开 " **Foreach 循环编辑器**"。</span><span class="sxs-lookup"><span data-stu-id="27d42-128">Double-click Foreach File in Folder to reopen the **Foreach Loop Editor**.</span></span>  
  
2.  <span data-ttu-id="27d42-129">单击“集合”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27d42-129">Click **Collection**.</span></span>  
  
3.  <span data-ttu-id="27d42-130">在“集合”  页上，选择“Foreach 文件枚举器”  。</span><span class="sxs-lookup"><span data-stu-id="27d42-130">On the **Collection** page, select **Foreach File Enumerator**.</span></span>  
  
4.  <span data-ttu-id="27d42-131">在“枚举器配置”\*\*\*\* 组中，单击“浏览”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27d42-131">In the **Enumerator configuration** group, click **Browse**.</span></span>  
  
5.  <span data-ttu-id="27d42-132">在“浏览文件夹”\*\*\*\* 对话框中，找到计算机上包含 Currency_\*.txt 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="27d42-132">In the **Browse for Folder** dialog box, locate the folder on your machine that contains the Currency_\*.txt files.</span></span>  
  
     <span data-ttu-id="27d42-133">此示例数据与 [!INCLUDE[ssIS](../includes/ssis-md.md)] 课程包一起提供。</span><span class="sxs-lookup"><span data-stu-id="27d42-133">This sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="27d42-134">要下载示例数据和课程包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="27d42-134">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="27d42-135">导航到 [Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="27d42-135">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="27d42-136">单击 "**下载**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="27d42-136">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="27d42-137">单击超链接 " https://msftisprodsamples.codeplex.com/downloads/get/578097 " SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="27d42-137">Click the  HYPERLINK "https://msftisprodsamples.codeplex.com/downloads/get/578097" SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
6.  <span data-ttu-id="27d42-138">在“文件”\*\*\*\* 框中，键入 **Currency_\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="27d42-138">In the **Files** box, type **Currency_\*.txt**.</span></span>  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a><span data-ttu-id="27d42-139">将枚举器映射为用户定义的变量</span><span class="sxs-lookup"><span data-stu-id="27d42-139">To map the enumerator to a user-defined variable</span></span>  
  
1.  <span data-ttu-id="27d42-140">单击“变量映射”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27d42-140">Click **Variable Mappings**.</span></span>  
  
2.  <span data-ttu-id="27d42-141">在 "**变量映射**" 页上的 "**变量**" 列中，单击空单元格，然后选择 **\<New Variable...>** 。</span><span class="sxs-lookup"><span data-stu-id="27d42-141">On the **Variable Mappings** page, in the **Variable** column, click the empty cell and select **\<New Variable...>**.</span></span>  
  
3.  <span data-ttu-id="27d42-142">在 "**添加变量**" 对话框中，为 "**名称**" 键入 `varFileName` 。</span><span class="sxs-lookup"><span data-stu-id="27d42-142">In the **Add Variable** dialog box, for **Name**, type `varFileName`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="27d42-143">变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="27d42-143">Variable names are case sensitive.</span></span>  
  
4.  <span data-ttu-id="27d42-144">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="27d42-144">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="27d42-145">再次单击“确定”\*\*\*\*，退出“Foreach 循环编辑器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="27d42-145">Click **OK** again to exit the **Foreach Loop Editor** dialog box.</span></span>  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a><span data-ttu-id="27d42-146">将数据流任务添加到循环中</span><span class="sxs-lookup"><span data-stu-id="27d42-146">To add the data flow task to the loop</span></span>  
  
-   <span data-ttu-id="27d42-147">将**提取示例货币数据**数据流任务拖到现在已重命名的 Foreach 循环容器上 `Foreach File in Folder` 。</span><span class="sxs-lookup"><span data-stu-id="27d42-147">Drag the **Extract Sample Currency Data** data flow task onto the Foreach Loop container now renamed `Foreach File in Folder`.</span></span>  
  
## <a name="next-lesson-task"></a><span data-ttu-id="27d42-148">下一课程任务</span><span class="sxs-lookup"><span data-stu-id="27d42-148">Next Lesson Task</span></span>  
 [<span data-ttu-id="27d42-149">步骤 3：修改平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="27d42-149">Step 3: Modifying the Flat File Connection Manager</span></span>](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a><span data-ttu-id="27d42-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27d42-150">See Also</span></span>  
 <span data-ttu-id="27d42-151">[配置 Foreach 循环容器](control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="27d42-151">[Configure a Foreach Loop Container](control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="27d42-152">使用包中的变量</span><span class="sxs-lookup"><span data-stu-id="27d42-152">Use Variables in Packages</span></span>](use-variables-in-packages.md)  
  
