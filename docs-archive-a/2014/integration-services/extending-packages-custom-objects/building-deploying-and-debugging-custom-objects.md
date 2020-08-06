---
title: 生成、部署和调试自定义对象 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom objects [Integration Services]
ms.assetid: b03685bc-5398-4c3f-901a-1219c1098fbe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 13157fce4e5c7dd8987f4950a6b4250ea0e36094
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691811"
---
# <a name="building-deploying-and-debugging-custom-objects"></a><span data-ttu-id="e0d34-102">生成、部署和调试自定义对象</span><span class="sxs-lookup"><span data-stu-id="e0d34-102">Building, Deploying, and Debugging Custom Objects</span></span>
  <span data-ttu-id="e0d34-103">在为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的自定义对象编写代码后，必须生成和部署程序集，将该程序集集成到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中，使其可在包中使用，然后对其进行测试和调试。</span><span class="sxs-lookup"><span data-stu-id="e0d34-103">After you have written the code for a custom object for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you must build the assembly, deploy it, integrate it into [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer to make it available for use in packages, and test and debug it.</span></span>

##  <a name="steps-in-building-deploying-and-debugging-a-custom-object-for-integration-services"></a><a name="top"></a> <span data-ttu-id="e0d34-104">生成、部署和调试 Integration Services 自定义对象的步骤</span><span class="sxs-lookup"><span data-stu-id="e0d34-104">Steps in Building, Deploying, and Debugging a Custom Object for Integration Services</span></span>
 <span data-ttu-id="e0d34-105">您已编写了对象的自定义功能代码。</span><span class="sxs-lookup"><span data-stu-id="e0d34-105">You have already written the custom functionality for your object.</span></span> <span data-ttu-id="e0d34-106">现在必须对所编写的代码进行测试，使其可供用户使用。</span><span class="sxs-lookup"><span data-stu-id="e0d34-106">Now you have to test it and to make it available to users.</span></span> <span data-ttu-id="e0d34-107">对于可为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 创建的所有类型的自定义对象，步骤都非常相似。</span><span class="sxs-lookup"><span data-stu-id="e0d34-107">The steps are very similar for all the types of custom objects that you can create for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="e0d34-108">下面是生成、部署和调试自定义对象应遵循的步骤：</span><span class="sxs-lookup"><span data-stu-id="e0d34-108">Here are the steps that you follow in building, deploying, and debugging it:</span></span>

1.  <span data-ttu-id="e0d34-109">使用强名称为要生成的程序集[签名](#signing)。</span><span class="sxs-lookup"><span data-stu-id="e0d34-109">[Sign](#signing) the assembly to be generated with a strong name.</span></span>

2.  <span data-ttu-id="e0d34-110">[生成](#building)程序集。</span><span class="sxs-lookup"><span data-stu-id="e0d34-110">[Build](#building) the assembly.</span></span>

3.  <span data-ttu-id="e0d34-111">通过将程序集移动到或复制到适当的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 文件夹来[部署](#deploying)该程序集。</span><span class="sxs-lookup"><span data-stu-id="e0d34-111">[Deploy](#deploying) the assembly by moving or copying it to the appropriate [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] folder.</span></span>

4.  <span data-ttu-id="e0d34-112">在全局程序集缓存 (GAC) 中[安装](#installing)该程序集。</span><span class="sxs-lookup"><span data-stu-id="e0d34-112">[Install](#installing) the assembly in the global assembly cache (GAC).</span></span>

     <span data-ttu-id="e0d34-113">此对象自动添加到工具箱中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-113">The object is automatically added to the Toolbox.</span></span>

5.  <span data-ttu-id="e0d34-114">如有必要，对部署进行[故障排除](#troubleshooting)。</span><span class="sxs-lookup"><span data-stu-id="e0d34-114">[Troubleshoot](#troubleshooting) the deployment, if necessary.</span></span>

6.  <span data-ttu-id="e0d34-115">[测试](#testing)并调试代码。</span><span class="sxs-lookup"><span data-stu-id="e0d34-115">[Test](#testing) and debug your code.</span></span>

##  <a name="signing-the-assembly"></a><a name="signing"></a> <span data-ttu-id="e0d34-116">为程序集签名</span><span class="sxs-lookup"><span data-stu-id="e0d34-116">Signing the Assembly</span></span>
 <span data-ttu-id="e0d34-117">若要共享程序集，必须将其安装在全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-117">When an assembly is meant to be shared, it must be installed in the global assembly cache.</span></span> <span data-ttu-id="e0d34-118">程序集被添加到全局程序集缓存之后，可以由 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 这样的应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="e0d34-118">After the assembly has been added to the global assembly cache, the assembly can be used by applications such as [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="e0d34-119">全局程序集缓存要求必须使用强名称为程序集进行签名，这样可保证程序集是全局唯一的。</span><span class="sxs-lookup"><span data-stu-id="e0d34-119">A requirement of the global assembly cache is that the assembly must be signed with a strong name, which guarantees that an assembly is globally unique.</span></span> <span data-ttu-id="e0d34-120">强名称程序集有一个完全限定的名称，由程序集的名称、区域性、公钥及版本号组成。</span><span class="sxs-lookup"><span data-stu-id="e0d34-120">A strong-named assembly has a fully qualified name that includes the name, culture, public key, and version number of the assembly.</span></span> <span data-ttu-id="e0d34-121">运行库使用这些信息来定位程序集并将其与其他同名的程序集区分开。</span><span class="sxs-lookup"><span data-stu-id="e0d34-121">The runtime uses this information to locate the assembly and to differentiate it from other assemblies with the same name.</span></span>

 <span data-ttu-id="e0d34-122">若要使用强名称为程序集签名，必须首先具有或创建公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="e0d34-122">To sign an assembly with a strong name, you must first have or create a public/private key pair.</span></span> <span data-ttu-id="e0d34-123">这一对加密公钥和加密私钥用于在生成时创建强名称程序集。</span><span class="sxs-lookup"><span data-stu-id="e0d34-123">This public and private cryptographic key pair is used at build time to create a strong-named assembly.</span></span>

 <span data-ttu-id="e0d34-124">有关强名称的详细信息和为程序集签名所必须遵循的步骤，请参阅 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文档中的下列主题：</span><span class="sxs-lookup"><span data-stu-id="e0d34-124">For more information about strong names and on the steps that you must followto sign an assembly, see the following topics in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation:</span></span>

-   <span data-ttu-id="e0d34-125">强名称程序集</span><span class="sxs-lookup"><span data-stu-id="e0d34-125">Strong-Named Assemblies</span></span>

-   <span data-ttu-id="e0d34-126">创建密钥对</span><span class="sxs-lookup"><span data-stu-id="e0d34-126">Creating a Key Pair</span></span>

-   <span data-ttu-id="e0d34-127">使用强名称为程序集签名</span><span class="sxs-lookup"><span data-stu-id="e0d34-127">Signing an Assembly with a Strong Name</span></span>

 <span data-ttu-id="e0d34-128">在生成时，可以轻松在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中使用强名称为程序集签名。</span><span class="sxs-lookup"><span data-stu-id="e0d34-128">You can easily sign your assembly with a strong name in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] at build time.</span></span> <span data-ttu-id="e0d34-129">在 "**项目属性**" 对话框中，选择 "**签名**" 选项卡。选择对**程序集进行签名**的选项，然后提供密钥 ( .snk) 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="e0d34-129">In the **Project Properties** dialog box, select the **Signing** tab. Select the option to **Sign the assembly** and then provide the path of the key (.snk) file.</span></span>

##  <a name="building-the-assembly"></a><a name="building"></a> <span data-ttu-id="e0d34-130">生成程序集</span><span class="sxs-lookup"><span data-stu-id="e0d34-130">Building the Assembly</span></span>
 <span data-ttu-id="e0d34-131">为项目签名后，必须使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 的“生成”\*\*\*\* 菜单上可用的命令来生成或重新生成项目或解决方案。</span><span class="sxs-lookup"><span data-stu-id="e0d34-131">After signing the project, you must build or rebuild the project or the solution by using the commands available on the **Build** menu of [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="e0d34-132">您的解决方案可能包含单独的自定义用户界面项目，该项目也必须使用强名称签名，并且可以同时生成。</span><span class="sxs-lookup"><span data-stu-id="e0d34-132">Your solution may contain a separate project for a custom user interface, which must also be signed with a strong name, and can be built at the same time.</span></span>

 <span data-ttu-id="e0d34-133">执行下两个步骤（部署程序集并将其安装在全局程序集缓存中）的最简便方法是将这些步骤编写为 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中的生成后事件。</span><span class="sxs-lookup"><span data-stu-id="e0d34-133">The most convenient method for performing the next two steps-deploying the assembly and installing it in the global assembly cache-is to script these steps as a post-build event in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="e0d34-134">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 项目的项目属性的“编译”\*\*\*\* 页和 C# 项目的“生成事件”\*\*\*\* 页都提供可用的生成事件。</span><span class="sxs-lookup"><span data-stu-id="e0d34-134">Build events are available from the **Compile** page of Project Properties for a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] project, and from the **Build Events** page for a C# project.</span></span> <span data-ttu-id="e0d34-135">命令提示实用工具（如 gacutil.exe\*\*\*\*）需要完整路径。</span><span class="sxs-lookup"><span data-stu-id="e0d34-135">The full path is required for command prompt utilities such as **gacutil.exe**.</span></span> <span data-ttu-id="e0d34-136">包含空格的路径和展开为包含空格的路径的宏（如 $(TargetPath)）的前后都需要引号。</span><span class="sxs-lookup"><span data-stu-id="e0d34-136">Quotation marks are required both around paths that contain spaces and around macros such as $(TargetPath) that expand to paths that contain spaces.</span></span>

 <span data-ttu-id="e0d34-137">下面是自定义日志提供程序的生成后事件命令行的示例：</span><span class="sxs-lookup"><span data-stu-id="e0d34-137">Here is an example of a post-build event command line for a custom log provider:</span></span>

```
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -u $(TargetName)
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -i $(TargetFileName)
copy $(TargetFileName) "C:\Program Files\Microsoft SQL Server\120\DTS\LogProviders "
```

##  <a name="deploying-the-assembly"></a><a name="deploying"></a> <span data-ttu-id="e0d34-138">部署程序集</span><span class="sxs-lookup"><span data-stu-id="e0d34-138">Deploying the Assembly</span></span>
 <span data-ttu-id="e0d34-139">[!INCLUDE[ssIS](../../includes/ssis-md.md)]设计器通过枚举在安装时创建的一系列文件夹中的文件，找到可供包使用的自定义对象 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e0d34-139">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer locates the custom objects available for use in packages by enumerating the files found in a series of folders that are created when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span> <span data-ttu-id="e0d34-140">当使用默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装设置时，这组文件夹位于**C:\PROGRAM Files\Microsoft SQL Server\120\DTS**下。</span><span class="sxs-lookup"><span data-stu-id="e0d34-140">When the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation settings are used, this set of folders is located under **C:\Program Files\Microsoft SQL Server\120\DTS**.</span></span> <span data-ttu-id="e0d34-141">但是，如果为自定义对象创建安装程序，应检查**HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\120\SSIS\Setup\DtsPath**注册表项的值，以验证此文件夹的位置。</span><span class="sxs-lookup"><span data-stu-id="e0d34-141">However if you create a setup program for your custom object, you should check the value of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\Setup\DtsPath** registry key to verify the location of this folder.</span></span>

 <span data-ttu-id="e0d34-142">可以通过下面两种方式将程序集放入文件夹中：</span><span class="sxs-lookup"><span data-stu-id="e0d34-142">You can put the assembly in the folder in two ways:</span></span>

-   <span data-ttu-id="e0d34-143">在生成已编译的程序集后，将其移动或复制到相应的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-143">Move or copy the compiled assembly to the appropriate folder after building it.</span></span> <span data-ttu-id="e0d34-144">（为方便起见，可以在生成后事件中包含复制命令。）</span><span class="sxs-lookup"><span data-stu-id="e0d34-144">(For convenience, you can include the copy command in a Post-build Event.)</span></span>

-   <span data-ttu-id="e0d34-145">直接在相应的文件夹中生成程序集。</span><span class="sxs-lookup"><span data-stu-id="e0d34-145">Build the assembly directly in the appropriate folder.</span></span>

 <span data-ttu-id="e0d34-146">**C:\Program FILES\MICROSOFT SQL Server\120\DTS**下的下列部署文件夹用于各种类型的自定义对象：</span><span class="sxs-lookup"><span data-stu-id="e0d34-146">The following deployment folders under **C:\Program Files\Microsoft SQL Server\120\DTS** are used for the various types of custom objects:</span></span>

|<span data-ttu-id="e0d34-147">自定义对象</span><span class="sxs-lookup"><span data-stu-id="e0d34-147">Custom object</span></span>|<span data-ttu-id="e0d34-148">部署文件夹</span><span class="sxs-lookup"><span data-stu-id="e0d34-148">Deployment folder</span></span>|
|-------------------|-----------------------|
|<span data-ttu-id="e0d34-149">任务</span><span class="sxs-lookup"><span data-stu-id="e0d34-149">Task</span></span>|<span data-ttu-id="e0d34-150">任务</span><span class="sxs-lookup"><span data-stu-id="e0d34-150">Tasks</span></span>|
|<span data-ttu-id="e0d34-151">“ODBC 源编辑器”</span><span class="sxs-lookup"><span data-stu-id="e0d34-151">Connection manager</span></span>|<span data-ttu-id="e0d34-152">连接</span><span class="sxs-lookup"><span data-stu-id="e0d34-152">Connections</span></span>|
|<span data-ttu-id="e0d34-153">日志提供程序</span><span class="sxs-lookup"><span data-stu-id="e0d34-153">Log provider</span></span>|<span data-ttu-id="e0d34-154">LogProviders</span><span class="sxs-lookup"><span data-stu-id="e0d34-154">LogProviders</span></span>|
|<span data-ttu-id="e0d34-155">数据流组件</span><span class="sxs-lookup"><span data-stu-id="e0d34-155">Data flow component</span></span>|<span data-ttu-id="e0d34-156">PipelineComponents</span><span class="sxs-lookup"><span data-stu-id="e0d34-156">PipelineComponents</span></span>|

> [!NOTE]
>  <span data-ttu-id="e0d34-157">将程序集复制到这些文件夹中即可支持可用任务、连接管理器等的枚举。</span><span class="sxs-lookup"><span data-stu-id="e0d34-157">Assemblies are copied to these folders to support the enumeration of available tasks, connection managers, and so on.</span></span> <span data-ttu-id="e0d34-158">因此，您不一定要将只包含用于自定义对象的自定义用户界面的程序集部署到这些文件夹中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-158">Therefore you do not have to deploy assemblies that contain only the custom user interface for custom objects to these folders.</span></span>

##  <a name="installing-the-assembly-in-the-global-assembly-cache"></a><a name="installing"></a> <span data-ttu-id="e0d34-159">在全局程序集缓存中安装程序集</span><span class="sxs-lookup"><span data-stu-id="e0d34-159">Installing the Assembly in the Global Assembly Cache</span></span>
 <span data-ttu-id="e0d34-160">若要将任务程序集安装到全局程序集缓存 (GAC) 中，请使用命令行工具 gacutil.exe\*\*\*\*，或将程序集拖至 `%system%\assembly` 目录中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-160">To install the task assembly into the global assembly cache (GAC), use the command line tool **gacutil.exe**, or drag the assemblies to the `%system%\assembly` directory.</span></span> <span data-ttu-id="e0d34-161">为方便起见，还可以在生成事件后中调用 gacutil.exe\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0d34-161">For convenience, you can also include the call to **gacutil.exe** in a Post-build Event.</span></span>

 <span data-ttu-id="e0d34-162">下面的命令使用 gacutil.exe\*\*\*\* 将名为 MyTask.dll\*\* 的组件安装到 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-162">The following command installs a component named *MyTask.dll* into the GAC by using **gacutil.exe**.</span></span>

 `gacutil /iF MyTask.dll`

 <span data-ttu-id="e0d34-163">在安装新版本的自定义对象后，必须先关闭再重新打开 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器。</span><span class="sxs-lookup"><span data-stu-id="e0d34-163">You must close and reopen [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer after you install a new version of your custom object.</span></span> <span data-ttu-id="e0d34-164">如果已在全局程序集缓存中安装了早期版本的自定义对象，必须先删除这些对象再安装新版本。</span><span class="sxs-lookup"><span data-stu-id="e0d34-164">If you have installed earlier versions of your custom object in the global assembly cache, you must remove them before installing the new version.</span></span> <span data-ttu-id="e0d34-165">若要卸载程序集，请运行 gacutil.exe\*\*\*\* 并在 `/u` 选项中指定程序集名称。</span><span class="sxs-lookup"><span data-stu-id="e0d34-165">To uninstall an assembly, run **gacutil.exe** and specify the assembly name with the `/u` option.</span></span>

 <span data-ttu-id="e0d34-166">有关全局程序集缓存的详细信息，请参阅“[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 工具”中的“全局程序集缓存工具 (Gactutil.exe)”。</span><span class="sxs-lookup"><span data-stu-id="e0d34-166">For more information about the global assembly cache, see Global Assembly Cache Tool (Gactutil.exe) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Tools.</span></span>

##  <a name="troubleshooting-the-deployment"></a><a name="troubleshooting"></a> <span data-ttu-id="e0d34-167">对部署进行故障排除</span><span class="sxs-lookup"><span data-stu-id="e0d34-167">Troubleshooting the Deployment</span></span>
 <span data-ttu-id="e0d34-168">如果自定义对象显示在“工具箱”\*\*\*\* 或可用对象列表中，但无法将其添加到包中，可以尝试以下操作：</span><span class="sxs-lookup"><span data-stu-id="e0d34-168">If your custom object appears in the **Toolbox** or the list of available objects, but you are not able to add it to a package, try the following:</span></span>

1.  <span data-ttu-id="e0d34-169">在全局程序集缓存中查找该组件是否有多个版本。</span><span class="sxs-lookup"><span data-stu-id="e0d34-169">Look in the global assembly cache for multiple versions of your component.</span></span> <span data-ttu-id="e0d34-170">如果全局程序集缓存中存在该组件的多个版本，则设计器可能无法加载该组件。</span><span class="sxs-lookup"><span data-stu-id="e0d34-170">If there are multiple versions of the component in the global assembly cache, the designer may not be able to load your component.</span></span> <span data-ttu-id="e0d34-171">请删除全局程序集缓存中该程序集的所有实例，然后重新添加该程序集。</span><span class="sxs-lookup"><span data-stu-id="e0d34-171">Delete all instances of the assembly from the global assembly cache, and re-add the assembly.</span></span>

2.  <span data-ttu-id="e0d34-172">请确保部署文件夹中只存在一个程序集实例。</span><span class="sxs-lookup"><span data-stu-id="e0d34-172">Make sure that only a single instance of the assembly exists in the deployment folder.</span></span>

3.  <span data-ttu-id="e0d34-173">刷新工具箱。</span><span class="sxs-lookup"><span data-stu-id="e0d34-173">Refresh the Toolbox.</span></span>

4.  <span data-ttu-id="e0d34-174">将 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 附加到 devenv.exe\*\*\*\*，然后设置一个断点以单步执行初始化代码，确保不会发生异常。</span><span class="sxs-lookup"><span data-stu-id="e0d34-174">Attach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] to **devenv.exe** and set a breakpoint to step through your initialization code to ensure that no exceptions occur.</span></span>

##  <a name="testing-and-debugging-your-code"></a><a name="testing"></a> <span data-ttu-id="e0d34-175">测试并调试代码</span><span class="sxs-lookup"><span data-stu-id="e0d34-175">Testing and Debugging Your Code</span></span>
 <span data-ttu-id="e0d34-176">若要调试自定义对象的运行时方法，最简单的方法是在生成自定义对象后从 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 启动 dtexec.exe\*\*\*\*，然后运行使用该组件的包。</span><span class="sxs-lookup"><span data-stu-id="e0d34-176">The simplest approach to debugging the run-time methods of a custom object is to start **dtexec.exe** from [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] after building your custom object and run a package that uses the component.</span></span>

 <span data-ttu-id="e0d34-177">如果要调试组件的设计时方法（如方法），请在的 `Validate` 第二个实例中打开使用该组件的包 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，并附加到其**devenv.exe**进程。</span><span class="sxs-lookup"><span data-stu-id="e0d34-177">If you want to debug the component's design-time methods, such as the `Validate` method, open a package that uses the component in a second instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], and attach to its **devenv.exe** process.</span></span>

 <span data-ttu-id="e0d34-178">如果还希望在包已打开并在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中运行时调试组件的运行时方法，必须在包的执行过程中强制暂停，以便还能够附加到 DtsDebugHost.exe\*\*\*\* 进程。</span><span class="sxs-lookup"><span data-stu-id="e0d34-178">If you also want to debug the component's run-time methods when a package is open and running in [!INCLUDE[ssIS](../../includes/ssis-md.md)] designer, you must force a pause in the execution of the package so that you can also attach to the **DtsDebugHost.exe** process.</span></span>

#### <a name="to-debug-an-objects-run-time-methods-by-attaching-to-dtexecexe"></a><span data-ttu-id="e0d34-179">通过附加到 dtexec.exe 来调试对象的运行时方法</span><span class="sxs-lookup"><span data-stu-id="e0d34-179">To debug an object's run-time methods by attaching to dtexec.exe</span></span>

1.  <span data-ttu-id="e0d34-180">在调试配置中，按照本主题中的说明签名和生成项目，进行部署，然后安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-180">Sign and build your project in the Debug configuration, deploy it, and install it in the global assembly cache as described in this topic.</span></span>

2.  <span data-ttu-id="e0d34-181">在**项目属性**的 "**调试**" 选项卡上，选择 "**启动外部程序**" 作为 "**启动" 操作**，并查找**dtexec.exe**，默认情况下安装在 C:\Program Files\Microsoft SQL server\120\dts\binn。中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-181">On the **Debug** tab of **Project Properties**, select **Start external program** as the **Start Action**, and locate **dtexec.exe**, which is installed by default in C:\Program Files\Microsoft SQL Server\120\DTS\Binn.</span></span>

3.  <span data-ttu-id="e0d34-182">在“启动选项”\*\*\*\* 下的“命令行选项”\*\*\*\* 文本框中，输入运行使用了组件的包所需的命令行参数。</span><span class="sxs-lookup"><span data-stu-id="e0d34-182">In the **Command line options** text box, under **Start Options**, enter the command line arguments required to run a package that uses your component.</span></span> <span data-ttu-id="e0d34-183">通常，命令行参数包含 /F[ILE] 开关，后跟 .dtsx 文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="e0d34-183">Often the command-line argument will consist of the /F[ILE] switch followed by the path and file name of the .dtsx file.</span></span> <span data-ttu-id="e0d34-184">有关详细信息，请参阅 [dtexec Utility](../packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="e0d34-184">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span>

4.  <span data-ttu-id="e0d34-185">在组件的运行时方法源代码中根据需要设置断点。</span><span class="sxs-lookup"><span data-stu-id="e0d34-185">Set breakpoints in the source code where appropriate in the run-time methods of your component.</span></span>

5.  <span data-ttu-id="e0d34-186">运行您的项目。</span><span class="sxs-lookup"><span data-stu-id="e0d34-186">Run your project.</span></span>

#### <a name="to-debug-a-custom-objects-design-time-methods-by-attaching-to-sql-server-data-tools"></a><span data-ttu-id="e0d34-187">通过附加到 SQL Server Data Tools 来调试自定义对象的设计时方法</span><span class="sxs-lookup"><span data-stu-id="e0d34-187">To debug a custom object's design-time methods by attaching to SQL Server Data Tools</span></span>

1.  <span data-ttu-id="e0d34-188">在调试配置中，按照本主题中的说明签名和生成项目，进行部署，然后安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-188">Sign and build your project in the Debug configuration, deploy it, and install it in the global assembly cache as described in this topic.</span></span>

2.  <span data-ttu-id="e0d34-189">在自定义对象的设计时方法源代码中根据需要设置断点。</span><span class="sxs-lookup"><span data-stu-id="e0d34-189">Set breakpoints in the source code where appropriate in the design-time methods of your custom object.</span></span>

3.  <span data-ttu-id="e0d34-190">打开第二个 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 实例，并加载使用自定义对象的包所在的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="e0d34-190">Open a second instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and load an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains a package that uses the custom object.</span></span>

4.  <span data-ttu-id="e0d34-191">从 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 的第一个实例，附加到 devenv.exe\*\*\*\* 的第二个实例，其中包是通过从第一个实例的“调试”\*\*\*\* 菜单选择“附加到进程”\*\*\*\* 加载的。</span><span class="sxs-lookup"><span data-stu-id="e0d34-191">From the first instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], attach to the second instance of **devenv.exe** in which the package is loaded by selecting **Attach to Process** from the **Debug** menu of the first instance.</span></span>

5.  <span data-ttu-id="e0d34-192">从第二个 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 实例运行包。</span><span class="sxs-lookup"><span data-stu-id="e0d34-192">Run the package from the second instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>

#### <a name="to-debug-a-custom-objects-run-time-methods-by-attaching-to-sql-server-data-tools"></a><span data-ttu-id="e0d34-193">通过附加到 SQL Server Data Tools 来调试自定义对象的运行时方法</span><span class="sxs-lookup"><span data-stu-id="e0d34-193">To debug a custom object's run-time methods by attaching to SQL Server Data Tools</span></span>

1.  <span data-ttu-id="e0d34-194">完成上述过程中列出的步骤之后，在执行包时强制暂停，以便可附加到 DtsDebugHost.exe\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="e0d34-194">After you have completed the steps listed in the previous procedure, force a pause in the execution of your package so that you can attach to **DtsDebugHost.exe**.</span></span> <span data-ttu-id="e0d34-195">此强制暂停的方法是：向 `OnPreExecute` 事件添加断点，或向项目添加脚本任务并输入用于显示模式消息框的脚本。</span><span class="sxs-lookup"><span data-stu-id="e0d34-195">You can force this pause by adding a breakpoint to the `OnPreExecute` event, or by adding a Script task to your project and entering script that displays a modal message box.</span></span>

2.  <span data-ttu-id="e0d34-196">运行包。</span><span class="sxs-lookup"><span data-stu-id="e0d34-196">Run the package.</span></span> <span data-ttu-id="e0d34-197">出现暂停时，切换到已在其中打开代码项目的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 实例，并从“调试”\*\*\*\* 菜单中选择“附加到进程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0d34-197">When the pause occurs, switch to the instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in which your code project is open, and select **Attach to Process** from the **Debug** menu.</span></span> <span data-ttu-id="e0d34-198">请确保附加到在“类型”\*\*\*\* 列中列为“托管，x86”\*\*\*\* 的 DtsDebugHost.exe\*\*\*\* 实例，而不是只列为 x86\*\*\*\* 的实例。</span><span class="sxs-lookup"><span data-stu-id="e0d34-198">Make sure to attach to the instance of **DtsDebugHost.exe** listed as **Managed, x86** in the **Type** column, not to the instance listed as **x86** only.</span></span>

3.  <span data-ttu-id="e0d34-199">返回到暂停的包，并继续通过断点，或单击“确定”\*\*\*\* 来关闭脚本任务引发的消息框，并继续包的执行和调试。</span><span class="sxs-lookup"><span data-stu-id="e0d34-199">Return to the paused package and continue past the breakpoint, or click **OK** to dismiss the message box raised by the Script task, and continue package execution and debugging.</span></span>

<span data-ttu-id="e0d34-200">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e0d34-200">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e0d34-201">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="e0d34-201">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e0d34-202">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="e0d34-202">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e0d34-203">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="e0d34-203">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0d34-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0d34-204">See Also</span></span>
 <span data-ttu-id="e0d34-205">[开发自定义对象以用于 Integration Services](developing-custom-objects-for-integration-services.md) [保留自定义对象](persisting-custom-objects.md)[包开发的故障排除工具](../troubleshooting/troubleshooting-tools-for-package-development.md)</span><span class="sxs-lookup"><span data-stu-id="e0d34-205">[Developing Custom Objects for Integration Services](developing-custom-objects-for-integration-services.md) [Persisting Custom Objects](persisting-custom-objects.md) [Troubleshooting Tools for Package Development](../troubleshooting/troubleshooting-tools-for-package-development.md)</span></span>


