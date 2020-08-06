---
title: 创建存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9a997244a2d54cca8732196107dd21927b5f9e2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689657"
---
# <a name="creating-stored-procedures"></a><span data-ttu-id="11d6f-102">创建存储过程</span><span class="sxs-lookup"><span data-stu-id="11d6f-102">Creating Stored Procedures</span></span>
  <span data-ttu-id="11d6f-103">所有存储过程必须与公共语言运行时 (CLR) 或组件对象模型 (COM) 类相关联才能使用。</span><span class="sxs-lookup"><span data-stu-id="11d6f-103">All stored procedures must be associated with a common language runtime (CLR) or Component Object Model (COM) class in order to be used.</span></span> <span data-ttu-id="11d6f-104">类必须安装在服务器上（通常以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX®动态链接库 (DLL 的形式）) ，并在服务器或数据库中注册为程序集 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="11d6f-104">The class must be installed on the server - usually in the form of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® dynamic link library (DLL) - and registered as an assembly on the server or in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="11d6f-105">存储过程将在服务器或数据库中注册。</span><span class="sxs-lookup"><span data-stu-id="11d6f-105">Stored procedures are registered on a server or on a database.</span></span> <span data-ttu-id="11d6f-106">服务器存储过程可以从任何查询上下文进行调用。</span><span class="sxs-lookup"><span data-stu-id="11d6f-106">Server stored procedures can be called from any query context.</span></span> <span data-ttu-id="11d6f-107">而只有当数据库上下文是定义存储过程时所针对的数据库时，才能访问数据库存储过程。</span><span class="sxs-lookup"><span data-stu-id="11d6f-107">Database stored procedures can only be accessed if the database context is the database under which the stored procedure is defined.</span></span> <span data-ttu-id="11d6f-108">如果一个程序集内的函数调用了另一个程序集内的函数，则必须在相同的上下文（服务器或数据库）中注册这两个程序集。</span><span class="sxs-lookup"><span data-stu-id="11d6f-108">If functions in one assembly call functions in a different assembly, you must register both assemblies in the same context (server or database).</span></span> <span data-ttu-id="11d6f-109">对于服务器或服务器上的已部署 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库，可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 来注册程序集。</span><span class="sxs-lookup"><span data-stu-id="11d6f-109">For a server or a deployed [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database on a server, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to register an assembly.</span></span> <span data-ttu-id="11d6f-110">对于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目，可以使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 设计器在项目中注册程序集。</span><span class="sxs-lookup"><span data-stu-id="11d6f-110">For an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you can use [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Designer to register an assembly in the project.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="11d6f-111">COM 程序集可能会造成安全风险。</span><span class="sxs-lookup"><span data-stu-id="11d6f-111">COM assemblies might pose a security risk.</span></span> <span data-ttu-id="11d6f-112">由于此风险和其他注意事项， [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]中不推荐使用 COM 程序集。</span><span class="sxs-lookup"><span data-stu-id="11d6f-112">Due to this risk and other considerations, COM assemblies were deprecated in [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)].</span></span> <span data-ttu-id="11d6f-113">未来版本可能不支持 COM 程序集。</span><span class="sxs-lookup"><span data-stu-id="11d6f-113">COM assemblies might not be supported in future releases.</span></span>  
  
## <a name="registering-a-server-assembly"></a><span data-ttu-id="11d6f-114">注册服务器程序集</span><span class="sxs-lookup"><span data-stu-id="11d6f-114">Registering a Server Assembly</span></span>  
 <span data-ttu-id="11d6f-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的对象资源管理器中，服务器程序集列在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例下面的“程序集”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="11d6f-115">In Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], server assemblies are listed in the Assemblies folder under an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="11d6f-116">服务器程序集可以同时包含 .NET (CLR) 程序集和 COM 库。</span><span class="sxs-lookup"><span data-stu-id="11d6f-116">Server assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-server-assembly"></a><span data-ttu-id="11d6f-117">创建服务器程序集</span><span class="sxs-lookup"><span data-stu-id="11d6f-117">To create a server assembly</span></span>  
  
1.  <span data-ttu-id="11d6f-118">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]在对象资源管理器中展开的实例，右键单击 "**程序集**" 文件夹，然后单击 "**新建程序集**"。</span><span class="sxs-lookup"><span data-stu-id="11d6f-118">Expand the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly**.</span></span> <span data-ttu-id="11d6f-119">这会显示 "**注册服务器程序集**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="11d6f-119">This displays the **Register Server Assembly** dialog box.</span></span>  
  
2.  <span data-ttu-id="11d6f-120">对于**类型**，指定程序集的类型：</span><span class="sxs-lookup"><span data-stu-id="11d6f-120">For **Type** specify the type of assembly:</span></span>  
  
    -   <span data-ttu-id="11d6f-121">对于托管代码 (CLR) DLL，请指定 .NET 程序集。</span><span class="sxs-lookup"><span data-stu-id="11d6f-121">For a managed code (CLR) DLL, specify .NET Assembly.</span></span>  
  
    -   <span data-ttu-id="11d6f-122">对于本机代码 (COM) DLL，请指定 COM DLL。</span><span class="sxs-lookup"><span data-stu-id="11d6f-122">For a native code (COM) DLL, specify COM DLL.</span></span>  
  
3.  <span data-ttu-id="11d6f-123">对于 "**文件名**"，请指定包含存储过程的 DLL。</span><span class="sxs-lookup"><span data-stu-id="11d6f-123">For **File name**, specify the DLL containing the stored procedures.</span></span>  
  
4.  <span data-ttu-id="11d6f-124">对于 "**程序集名称**"，请指定程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="11d6f-124">For **Assembly name**, specify a name for the assembly.</span></span>  
  
5.  <span data-ttu-id="11d6f-125">如果这是要用于调试存储过程的库的调试版本，请选中 "**包括调试信息**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="11d6f-125">If this is a debug build of the library that you are going to use to debug stored procedures, select the **Include debug information** check box.</span></span> <span data-ttu-id="11d6f-126">有关调试存储过程的详细信息，请参阅[调试存储过程](debugging-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="11d6f-126">For more information about debugging stored procedures, see [Debugging Stored Procedures](debugging-stored-procedures.md).</span></span>  
  
6.  <span data-ttu-id="11d6f-127">您可以单击 **"确定"** 以立即注册程序集，或在对话框工具栏上单击 "**脚本**" 菜单上的命令，以将注册操作编写为查询窗口、文件或剪贴板的脚本。</span><span class="sxs-lookup"><span data-stu-id="11d6f-127">You can click **OK** to register the assembly immediately, or on the dialog box toolbar, you can click a command on the **Script** menu to script the registration action to a query window, a file, or the Clipboard.</span></span>  
  
 <span data-ttu-id="11d6f-128">注册服务器程序集之后，可以通过在对象资源管理器中右键单击该程序集，然后单击 "**属性**" 来配置该程序集。</span><span class="sxs-lookup"><span data-stu-id="11d6f-128">After you register a server assembly, you can configure it by right-clicking the assembly in Object Explorer and then clicking **Properties**.</span></span>  
  
## <a name="registering-a-database-assembly-on-the-server"></a><span data-ttu-id="11d6f-129">在服务器上注册数据库程序集</span><span class="sxs-lookup"><span data-stu-id="11d6f-129">Registering a Database Assembly on the Server</span></span>  
 <span data-ttu-id="11d6f-130">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的对象资源管理器中，数据库程序集将列在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库下面的“程序集”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="11d6f-130">In Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], database assemblies are listed in the Assemblies folder under an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="11d6f-131">数据库程序集可以同时包含 .NET (CLR) 程序集和 COM 库。</span><span class="sxs-lookup"><span data-stu-id="11d6f-131">Database assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-database-assembly-on-a-server"></a><span data-ttu-id="11d6f-132">在服务器上创建数据库程序集</span><span class="sxs-lookup"><span data-stu-id="11d6f-132">To create a database assembly on a server</span></span>  
  
1.  <span data-ttu-id="11d6f-133">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]在对象资源管理器中展开数据库实例，右键单击 "**程序集**" 文件夹，然后单击 "**新建程序集**"。</span><span class="sxs-lookup"><span data-stu-id="11d6f-133">Expand the instance the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly**.</span></span> <span data-ttu-id="11d6f-134">这会显示 "**注册数据库程序集**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="11d6f-134">This displays the **Register Database Assembly** dialog box.</span></span>  
  
2.  <span data-ttu-id="11d6f-135">对于**类型**，指定程序集的类型：</span><span class="sxs-lookup"><span data-stu-id="11d6f-135">For **Type** specify the type of assembly:</span></span>  
  
    -   <span data-ttu-id="11d6f-136">对于托管代码 (CLR) DLL，请指定 .NET 程序集。</span><span class="sxs-lookup"><span data-stu-id="11d6f-136">For a managed code (CLR) DLL, specify .NET Assembly.</span></span>  
  
    -   <span data-ttu-id="11d6f-137">对于本机代码 (COM) DLL，请指定 COM DLL。</span><span class="sxs-lookup"><span data-stu-id="11d6f-137">For a native code (COM) DLL), specify COM DLL.</span></span>  
  
3.  <span data-ttu-id="11d6f-138">对于 "**文件名**"，请指定包含存储过程的 DLL。</span><span class="sxs-lookup"><span data-stu-id="11d6f-138">For **File name**, specify the DLL containing the stored procedures.</span></span>  
  
4.  <span data-ttu-id="11d6f-139">对于 "**程序集名称**"，请指定程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="11d6f-139">For **Assembly name**, specify a name for the assembly.</span></span>  
  
5.  <span data-ttu-id="11d6f-140">如果这是要用于调试存储过程的库的调试版本，请选中 "**包括调试信息**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="11d6f-140">If this is a debug build of the library that you are going to use to debug stored procedures, select the **Include debug information** check box.</span></span> <span data-ttu-id="11d6f-141">有关调试存储过程的详细信息，请参阅[调试存储过程](debugging-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="11d6f-141">For more information about debugging stored procedures, see [Debugging Stored Procedures](debugging-stored-procedures.md).</span></span>  
  
6.  <span data-ttu-id="11d6f-142">您可以单击 **"确定"** 以立即注册程序集，或在对话框工具栏上单击 "**脚本**" 菜单上的命令，以将注册操作编写为查询窗口、文件或剪贴板的脚本。</span><span class="sxs-lookup"><span data-stu-id="11d6f-142">You can click **OK** to register the assembly immediately, or on the dialog box toolbar, you can click a command on the **Script** menu to script the registration action to a query window, a file, or the Clipboard.</span></span>  
  
 <span data-ttu-id="11d6f-143">注册数据库程序集之后，可以通过在对象资源管理器中右键单击该程序集，然后单击 "**属性**" 来配置该程序集。</span><span class="sxs-lookup"><span data-stu-id="11d6f-143">After you register a database assembly, you can configure it by right-clicking the assembly in Object Explorer and then clicking **Properties**.</span></span>  
  
## <a name="registering-a-database-assembly-in-a-project"></a><span data-ttu-id="11d6f-144">在项目中注册数据库程序集</span><span class="sxs-lookup"><span data-stu-id="11d6f-144">Registering a Database Assembly in a Project</span></span>  
 <span data-ttu-id="11d6f-145">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的解决方案资源管理器中，数据库程序集列在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目下面的“程序集”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="11d6f-145">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], database assemblies are listed in the Assemblies folder under an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="11d6f-146">数据库程序集可以同时包含 .NET (CLR) 程序集和 COM 库。</span><span class="sxs-lookup"><span data-stu-id="11d6f-146">Database assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a><span data-ttu-id="11d6f-147">在 Analysis Service 项目中创建数据库程序集</span><span class="sxs-lookup"><span data-stu-id="11d6f-147">To create a database assembly in an Analysis Service project</span></span>  
  
1.  <span data-ttu-id="11d6f-148">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]在对象资源管理器中展开数据库实例，右键单击 "**程序集**" 文件夹，然后单击 "**新建程序集引用**"。</span><span class="sxs-lookup"><span data-stu-id="11d6f-148">Expand the instance the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly Reference**.</span></span> <span data-ttu-id="11d6f-149">此时将显示 "**添加引用**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="11d6f-149">This displays the **Add Reference** dialog box.</span></span> <span data-ttu-id="11d6f-150">"**添加引用**" 对话框的 " **.net** " 选项卡列出了现有的 .net (CLR) 程序集，而 "**项目**" 选项卡列出项目。</span><span class="sxs-lookup"><span data-stu-id="11d6f-150">The **.NET** tab of the **Add Reference** dialog box lists existing .NET (CLR) assemblies, while the **Projects** tab lists projects.</span></span>  
  
2.  <span data-ttu-id="11d6f-151">您可以单击现有的组件或项目，然后单击 "**添加**" 以将其添加到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="11d6f-151">You can click an existing component or project and then click **Add** to add it to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="11d6f-152">若要添加对 COM DLL 的引用，请单击 "**浏览**" 选项卡查找该文件。</span><span class="sxs-lookup"><span data-stu-id="11d6f-152">To add a reference to a COM DLL, click the **Browse** tab to find the file.</span></span> <span data-ttu-id="11d6f-153">"**选定的项目和组件**" 列表显示你要添加到项目中的每个组件的名称、类型、版本和位置。</span><span class="sxs-lookup"><span data-stu-id="11d6f-153">The **Selected projects and components** list shows the name, type, version, and location for each component that you are adding to the project.</span></span>  
  
3.  <span data-ttu-id="11d6f-154">完成选择要添加的组件后，单击 **"确定"** 将其添加到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="11d6f-154">When you are finished selecting components to add, click **OK** to add them to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
## <a name="script-format-for-an-assembly"></a><span data-ttu-id="11d6f-155">程序集的脚本格式</span><span class="sxs-lookup"><span data-stu-id="11d6f-155">Script Format For an Assembly</span></span>  
 <span data-ttu-id="11d6f-156">注册 .NET 程序集的操作相当简单。</span><span class="sxs-lookup"><span data-stu-id="11d6f-156">Registering a .NET assembly is fairly simple.</span></span> <span data-ttu-id="11d6f-157">.NET 程序集将使用以下格式以二进制格式添加到数据库：</span><span class="sxs-lookup"><span data-stu-id="11d6f-157">A .NET assembly is added to a database in binary format using the following format:</span></span>  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11d6f-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11d6f-158">See Also</span></span>  
 <span data-ttu-id="11d6f-159">[多维模型程序集管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="11d6f-159">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="11d6f-160">定义存储过程</span><span class="sxs-lookup"><span data-stu-id="11d6f-160">Defining Stored Procedures</span></span>](defining-stored-procedures.md)  
  
  
