---
title: "\"执行包\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageexecute.f1
- sql12.ssis.ssms.executepackage.f1
ms.assetid: 4f7a806d-4867-4d1f-bc65-b00c1caee7b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b60381054c781cd59f0a9d434710663b72d616c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587497"
---
# <a name="execute-package-dialog-box"></a><span data-ttu-id="d8dec-102">Execute Package Dialog Box</span><span class="sxs-lookup"><span data-stu-id="d8dec-102">Execute Package Dialog Box</span></span>
  <span data-ttu-id="d8dec-103">使用 **“执行包”** 对话框可以运行在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器上存储的包。</span><span class="sxs-lookup"><span data-stu-id="d8dec-103">Use the **Execute Package** dialog box to run a package that is stored on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="d8dec-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包可以包含在环境变量中存储的值的参数。</span><span class="sxs-lookup"><span data-stu-id="d8dec-104">An [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package may contain parameters that values stored in environment variables.</span></span> <span data-ttu-id="d8dec-105">在执行此类包之前，您必须指定将使用哪一环境来提供环境变量值。</span><span class="sxs-lookup"><span data-stu-id="d8dec-105">Before executing such a package, you must specify which environment will be used to provide the environment variable values.</span></span> <span data-ttu-id="d8dec-106">一个项目可以包含多个环境，但只能使用一个环境在执行时绑定环境变量值。</span><span class="sxs-lookup"><span data-stu-id="d8dec-106">A project may contain multiple environments, but only one environment can be used for binding environment variable values at the time of execution.</span></span> <span data-ttu-id="d8dec-107">如果在包中未使用任何环境变量，则不要求环境。</span><span class="sxs-lookup"><span data-stu-id="d8dec-107">If no environment variables are used in the package, an environment is not required.</span></span>  
  
 <span data-ttu-id="d8dec-108">您希望做什么？</span><span class="sxs-lookup"><span data-stu-id="d8dec-108">What do you want to do?</span></span>  
  
-   [<span data-ttu-id="d8dec-109">打开“执行包”对话框</span><span class="sxs-lookup"><span data-stu-id="d8dec-109">Open the Execute Package dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="d8dec-110">设置“常规”页上的选项</span><span class="sxs-lookup"><span data-stu-id="d8dec-110">Set the Options on the General page</span></span>](#general)  
  
-   [<span data-ttu-id="d8dec-111">设置“参数”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="d8dec-111">Set the Options on the Parameters tab</span></span>](#parameters)  
  
-   [<span data-ttu-id="d8dec-112">设置“连接管理器”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="d8dec-112">Set the Options on the Connection Managers tab</span></span>](#connection)  
  
-   [<span data-ttu-id="d8dec-113">设置“高级”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="d8dec-113">Set the Options on the Advanced tab</span></span>](#advanced)  
  
-   [<span data-ttu-id="d8dec-114">编写“执行包”对话框中选项的脚本</span><span class="sxs-lookup"><span data-stu-id="d8dec-114">Scripting the Options in the Execute Package Dialog Box</span></span>](#script)  
  
##  <a name="open-the-execute-package-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="d8dec-115">打开“执行包”对话框</span><span class="sxs-lookup"><span data-stu-id="d8dec-115">Open the Execute Package dialog box</span></span>  
  
1.  <span data-ttu-id="d8dec-116">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="d8dec-116">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="d8dec-117">正在连接到承载 SSISDB 数据库的 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="d8dec-117">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="d8dec-118">在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。</span><span class="sxs-lookup"><span data-stu-id="d8dec-118">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="d8dec-119">展开 **“SSISDB”** 节点。</span><span class="sxs-lookup"><span data-stu-id="d8dec-119">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="d8dec-120">展开包含您要运行的包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d8dec-120">Expand the folder that contains the package you want to run.</span></span>  
  
5.  <span data-ttu-id="d8dec-121">右键单击该包，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="d8dec-121">Right-click the package, and then click **Execute**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="d8dec-122">设置“常规”页上的选项</span><span class="sxs-lookup"><span data-stu-id="d8dec-122">Set the Options on the General page</span></span>  
 <span data-ttu-id="d8dec-123">选择 **“环境”** 以便指定适用于运行的包的环境。</span><span class="sxs-lookup"><span data-stu-id="d8dec-123">Select **Environment** to specify the environment that is applied with the package is run.</span></span>  
  
##  <a name="set-the-options-on-the-parameters-tab"></a><a name="parameters"></a> <span data-ttu-id="d8dec-124">设置“参数”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="d8dec-124">Set the Options on the Parameters tab</span></span>  
 <span data-ttu-id="d8dec-125">使用 **“参数”** 选项卡可以修改在包运行时使用的参数值。</span><span class="sxs-lookup"><span data-stu-id="d8dec-125">Use the **Parameters** tab to modify the parameter values that are used when the package runs.</span></span>  
  
##  <a name="set-the-options-on-the-connection-managers-tab"></a><a name="connection"></a> <span data-ttu-id="d8dec-126">设置“连接管理器”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="d8dec-126">Set the Options on the Connection Managers tab</span></span>  
 <span data-ttu-id="d8dec-127">使用“连接管理器”选项卡可以设置包连接管理器的属性。</span><span class="sxs-lookup"><span data-stu-id="d8dec-127">Use the Connection Managers tab to set the properties of the package connection manager(s).</span></span>  
  
##  <a name="set-the-options-on-the-advanced-tab"></a><a name="advanced"></a> <span data-ttu-id="d8dec-128">设置“高级”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="d8dec-128">Set the Options on the Advanced tab</span></span>  
 <span data-ttu-id="d8dec-129">使用“高级”选项卡可以管理属性和其他包设置。</span><span class="sxs-lookup"><span data-stu-id="d8dec-129">Use the Advanced tab to manage properties and other package settings.</span></span>  
  
 <span data-ttu-id="d8dec-130">“添加”  、“编辑”  、“删除”</span><span class="sxs-lookup"><span data-stu-id="d8dec-130">**Add**, **Edit**, **Remove**</span></span>  
 <span data-ttu-id="d8dec-131">单击以便添加、编辑或删除某一属性。</span><span class="sxs-lookup"><span data-stu-id="d8dec-131">Click to add, edit, or remove a property.</span></span>  
  
 <span data-ttu-id="d8dec-132">**日志记录级别**</span><span class="sxs-lookup"><span data-stu-id="d8dec-132">**Logging level**</span></span>  
 <span data-ttu-id="d8dec-133">选择用于执行包的日志记录级别。</span><span class="sxs-lookup"><span data-stu-id="d8dec-133">Select the logging level for the package execution.</span></span> <span data-ttu-id="d8dec-134">有关详细信息，请参阅 [catalog.set_execution_parameter_value（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="d8dec-134">For more information, see [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database).</span></span>  
  
 <span data-ttu-id="d8dec-135">**出错时转储**</span><span class="sxs-lookup"><span data-stu-id="d8dec-135">**Dump on errors**</span></span>  
 <span data-ttu-id="d8dec-136">指定在包执行过程中发生错误时是否创建一个转储文件。</span><span class="sxs-lookup"><span data-stu-id="d8dec-136">Specify whether a dump file is created when errors occur during the package execution.</span></span> <span data-ttu-id="d8dec-137">有关详细信息，请参阅 [生成包执行的转储文件](troubleshooting/generating-dump-files-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="d8dec-137">For more information, see [Generating Dump Files for Package Execution](troubleshooting/generating-dump-files-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="d8dec-138">**32 位运行时**</span><span class="sxs-lookup"><span data-stu-id="d8dec-138">**32-bit runtime**</span></span>  
 <span data-ttu-id="d8dec-139">指定包将在 32 位系统上执行。</span><span class="sxs-lookup"><span data-stu-id="d8dec-139">Specify that the package will execute on a 32-bit system.</span></span>  
  
##  <a name="scripting-the-options-in-the-execute-package-dialog-box"></a><a name="script"></a> <span data-ttu-id="d8dec-140">编写“执行包”对话框中选项的脚本</span><span class="sxs-lookup"><span data-stu-id="d8dec-140">Scripting the Options in the Execute Package Dialog Box</span></span>  
 <span data-ttu-id="d8dec-141">在您处于 **“执行包”** 对话框中时，还可以使用工具栏上的 **“脚本”** 按钮为您编写 [!INCLUDE[tsql](../includes/tsql-md.md)] 代码。</span><span class="sxs-lookup"><span data-stu-id="d8dec-141">While you are in the **Execute Package** dialog box, you can also use the **Script** button on the toolbar to write [!INCLUDE[tsql](../includes/tsql-md.md)] code for you.</span></span> <span data-ttu-id="d8dec-142">生成的脚本使用与你在“执行包”  对话框中选择的相同选项调用存储过程 [catalog.start_execution（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="d8dec-142">The generated script calls the stored procedures [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) with the same options that you have selected in the **Execute Package** dialog box.</span></span> <span data-ttu-id="d8dec-143">该脚本出现在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]的新脚本窗口中。</span><span class="sxs-lookup"><span data-stu-id="d8dec-143">The script appears in a new script window in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
  
