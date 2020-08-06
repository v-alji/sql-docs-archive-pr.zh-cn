---
title: 部署自定义程序集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3d88e1db844304b5cbb51f4af52b4715ef7e8c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693657"
---
# <a name="deploying-a-custom-assembly"></a><span data-ttu-id="7ce4f-102">部署自定义程序集</span><span class="sxs-lookup"><span data-stu-id="7ce4f-102">Deploying a Custom Assembly</span></span>
  <span data-ttu-id="7ce4f-103">若要在中部署自定义程序集 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，请将程序集放在报表设计器和 Report Server 的应用程序文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-103">To deploy a custom assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], place the assembly in the application folders of both Report Designer and the report server.</span></span> <span data-ttu-id="7ce4f-104">默认情况下，将在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中向自定义程序集授予 `Execution` 权限。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-104">By default, custom assemblies are granted `Execution` permission in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="7ce4f-105">若要向自定义程序集授予超过执行权限的特权，需要对报表服务器编辑 rssrvpolicy.config 配置文件，并对报表设计器预览窗口编辑 rspreviewpolicy.config 配置文件。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-105">To grant custom assemblies privileges beyond Execute permission, you will need to edit the rssrvpolicy.config configuration file for the report server and the rspreviewpolicy.config configuration file for the Report Designer preview window.</span></span> <span data-ttu-id="7ce4f-106">也可以选择将自定义程序集安装到全局程序集缓存 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-106">Alternatively, you can install your custom assembly in the global assembly cache (GAC).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ce4f-107">报表设计器有两种预览模式：“预览”选项卡以及在以 `DebugLocal` 模式下启动报表项目时启动的弹出式预览窗口。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-107">There are two preview modes for Report Designer: the Preview tab and the pop-up preview window that is launched when your report project is started in `DebugLocal` mode.</span></span> <span data-ttu-id="7ce4f-108">“预览”选项卡使用 `FullTrust` 权限集执行所有报表表达式，它不应用安全策略设置。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-108">The Preview tab executes all report expressions using the `FullTrust` permission set and does not apply security policy settings.</span></span> <span data-ttu-id="7ce4f-109">弹出式预览窗口旨在模拟报表服务器的功能，因此具有策略配置文件，您或管理员必须修改该文件才能在报表设计器中使用自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-109">The pop-up preview window is meant to simulate the report server functionality and therefore has a policy configuration file that you or an administrator must modify to use custom assemblies in Report Designer.</span></span> <span data-ttu-id="7ce4f-110">此弹出式预览还锁定自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-110">This pop-up preview also locks the custom assembly.</span></span> <span data-ttu-id="7ce4f-111">因此，您需要关闭预览窗口，才能修改或更新自定义程序集代码。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-111">Therefore, you need to close the preview window in order to modify or update your custom assembly code.</span></span>  
  
###### <a name="to-deploy-a-custom-assembly-in-reporting-services"></a><span data-ttu-id="7ce4f-112">在 Reporting Services 中部署自定义程序集</span><span class="sxs-lookup"><span data-stu-id="7ce4f-112">To deploy a custom assembly in Reporting Services</span></span>  
  
1.  <span data-ttu-id="7ce4f-113">将自定义程序集从生成位置复制到报表服务器的 bin 文件夹或报表设计器文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-113">Copy your custom assembly from your build location to the report server bin folder or the Report Designer folder.</span></span> <span data-ttu-id="7ce4f-114">报表服务器的 bin 文件夹的默认位置为 %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-114">The default location of the bin folder for the report server is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.</span></span> <span data-ttu-id="7ce4f-115">报表设计器的默认位置为 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-115">The default location of the Report Designer is %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
     <span data-ttu-id="7ce4f-116">通过将自定义程序集放入报表服务器 bin 文件夹中，您可以发布引用自定义程序集的报表；而通过将其放在报表设计器文件夹中，您可以在报表设计器中运行和调试引用自定义程序集的报表。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-116">Placing your custom assembly in the report server bin folder enables you to publish reports that reference your custom assembly, and placing it in the Report Designer folder enables you to run and debug reports that reference your custom assembly in Report Designer.</span></span>  
  
     <span data-ttu-id="7ce4f-117">如果您需要向自定义程序集代码授予超过默认执行权限的权限，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7ce4f-117">If you need to grant your custom assembly code permissions beyond the default execute permissions:</span></span>  
  
2.  <span data-ttu-id="7ce4f-118">打开相应的配置文件。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-118">Open the appropriate configuration file.</span></span> <span data-ttu-id="7ce4f-119">rssrvpolicy.config 的默认位置为 %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-119">The default location of rssrvpolicy.config is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer.</span></span> <span data-ttu-id="7ce4f-120">rspreviewpolicy.config 的默认位置为 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-120">The default location of rspreviewpolicy.config is %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
3.  <span data-ttu-id="7ce4f-121">为自定义程序集添加代码组。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-121">Add a code group for your custom assembly.</span></span> <span data-ttu-id="7ce4f-122">有关详细信息，请参阅[安全开发 (Reporting Services)](../extensions/secure-development/secure-development-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-122">For more information, see [Secure Development &#40;Reporting Services&#41;](../extensions/secure-development/secure-development-reporting-services.md).</span></span>  
  
## <a name="updating-custom-assemblies"></a><span data-ttu-id="7ce4f-123">更新自定义程序集</span><span class="sxs-lookup"><span data-stu-id="7ce4f-123">Updating Custom Assemblies</span></span>  
 <span data-ttu-id="7ce4f-124">有时，您可能需要更新当前正在由多个已发布报表引用的自定义程序集的版本。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-124">At some point, you may need to update a version of a custom assembly that is currently being referenced by several published reports.</span></span> <span data-ttu-id="7ce4f-125">如果该程序集已位于报表服务器的 bin 目录或报表服务器中，并且程序集的版本号以某种方式递增或更改，则当前发布的报表将不再正常工作。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-125">If that assembly already exists in the bin directory of the report server or Report Designer and the version number of the assembly is incremented or changed in some way, the currently published reports will no longer work properly.</span></span> <span data-ttu-id="7ce4f-126">您需要在报表定义的 `CodeModules` 元素中更新所引用的程序集的版本，并重新发布报表。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-126">You will need to update the version of the assembly that is referenced in the `CodeModules` element of the report definition and republish the reports.</span></span> <span data-ttu-id="7ce4f-127">如果您知道您将频繁地更新自定义程序集，并且您当前发布的报表需要引用新程序集，则您可能需要考虑在特定程序集的所有更新中使用同一个版本号。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-127">If you know that you will frequently update a custom assembly and your currently published reports need to reference the new assembly, you may want to consider using the same version number across all updates of a particular assembly.</span></span>  
  
 <span data-ttu-id="7ce4f-128">如果您不需要当前发布的报表引用程序集的新版本，则可以将自定义程序集部署到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-128">If you do not need your currently published reports to reference the new version of the assembly, you can deploy your custom assembly to the global assembly cache.</span></span> <span data-ttu-id="7ce4f-129">全局程序集缓存可以保持同一个程序集的多个版本，这样，您当前的报表可以引用程序集的前一个版本，而新发布的报表可以引用更新后的程序集。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-129">The global assembly cache can maintain multiple versions of the same assembly, so that your current reports can reference the previous version of your assembly and your newly published reports can reference the updated assembly.</span></span> <span data-ttu-id="7ce4f-130">此外，另一个方法是设置报表服务器的绑定重定向，以强制将旧程序集的所有请求重定向到新程序集。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-130">Yet another approach would be to set the binding redirect of the report server to force a redirect of all requests for the old assembly to the new assembly.</span></span> <span data-ttu-id="7ce4f-131">您需要修改报表服务器 Web.config 文件和报表服务器 ReportService.exe.config 文件。</span><span class="sxs-lookup"><span data-stu-id="7ce4f-131">You would need to modify the report server Web.config file and the report server ReportService.exe.config file.</span></span> <span data-ttu-id="7ce4f-132">该条目可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ce4f-132">The entry might look like the following:</span></span>  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ce4f-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ce4f-133">See Also</span></span>  
 <span data-ttu-id="7ce4f-134">[将自定义程序集用于报表](using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="7ce4f-134">[Using Custom Assemblies with Reports](using-custom-assemblies-with-reports.md) </span></span>  
 [<span data-ttu-id="7ce4f-135">使用程序集和全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="7ce4f-135">Working with Assemblies and the Global Assembly Cache</span></span>](https://go.microsoft.com/fwlink/?LinkId=63912)  
  
  
