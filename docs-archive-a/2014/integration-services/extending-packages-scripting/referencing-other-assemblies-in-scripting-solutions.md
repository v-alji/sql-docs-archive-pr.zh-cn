---
title: 引用脚本解决方案中的其他程序集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 685bbaa62da88e84cd848eb49dcf5bedb03d5390
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578954"
---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a><span data-ttu-id="3396f-102">引用脚本解决方案中的其他程序集</span><span class="sxs-lookup"><span data-stu-id="3396f-102">Referencing Other Assemblies in Scripting Solutions</span></span>
  <span data-ttu-id="3396f-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 类库为脚本开发人员提供了一组强大的工具，用于在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包中实现自定义功能。</span><span class="sxs-lookup"><span data-stu-id="3396f-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class library provides the script developer with a powerful set of tools for implementing custom functionality in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="3396f-104">脚本任务和脚本组件还可以使用自定义托管程序集。</span><span class="sxs-lookup"><span data-stu-id="3396f-104">The Script task and the Script component can also use custom managed assemblies.</span></span>

> [!NOTE]
>  <span data-ttu-id="3396f-105">若要使包能够使用 Web 服务中的对象和方法，可使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 中提供的“添加 Web 引用”命令。</span><span class="sxs-lookup"><span data-stu-id="3396f-105">To enable your packages to use the objects and methods from a Web service, use the **Add Web Reference** command available in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="3396f-106">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的早期版本中，必须生成代理类才能使用 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="3396f-106">In earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you had to generate a proxy class to use a Web service.</span></span>

## <a name="using-a-managed-assembly"></a><span data-ttu-id="3396f-107">使用托管程序集</span><span class="sxs-lookup"><span data-stu-id="3396f-107">Using a Managed Assembly</span></span>
 <span data-ttu-id="3396f-108">对于 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，若要在设计时查找托管程序集，必须执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="3396f-108">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to find a managed assembly at design time, you must do the following steps:</span></span>

1.  <span data-ttu-id="3396f-109">将托管程序集存储在计算机上的任何文件夹中。</span><span class="sxs-lookup"><span data-stu-id="3396f-109">Store the managed assembly in any folder on your computer.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="3396f-110">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的早期版本中，只能添加对存储在 %windir%\Microsoft.NET\Framework\vx.x.xxxxx 文件夹或 %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies 文件夹中的托管程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="3396f-110">In earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you could only add a reference to a managed assembly that was stored in the %windir%\Microsoft.NET\Framework\vx.x.xxxxx folder or the %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies folder.</span></span>

2.  <span data-ttu-id="3396f-111">添加对托管程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="3396f-111">Add a reference to the managed assembly.</span></span>

     <span data-ttu-id="3396f-112">若要添加引用，请在 VSTA 的“添加引用”  对话框的“浏览”  选项卡中查找和添加托管程序集。</span><span class="sxs-lookup"><span data-stu-id="3396f-112">To add the reference, in VSTA, in the **Add Reference** dialog box, on the **Browse** tab, locate and add the managed assembly.</span></span>

 <span data-ttu-id="3396f-113">对于 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，若要在运行时查找托管程序集，必须执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="3396f-113">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to find the managed assembly at run time, you must do the following steps:</span></span>

1.  <span data-ttu-id="3396f-114">用强名称为托管程序集签名。</span><span class="sxs-lookup"><span data-stu-id="3396f-114">Sign the managed assembly with a strong name.</span></span>

2.  <span data-ttu-id="3396f-115">将程序集安装到运行包的计算机的全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="3396f-115">Install the assembly in the global assembly cache on the computer on which the package is run.</span></span>

     <span data-ttu-id="3396f-116">有关详细信息，请参阅[生成、部署和调试自定义对象](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="3396f-116">For more information, see [Building, Deploying, and Debugging Custom Objects](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).</span></span>

## <a name="using-the-microsoft-net-framework-class-library"></a><span data-ttu-id="3396f-117">使用 Microsoft .NET Framework 类库</span><span class="sxs-lookup"><span data-stu-id="3396f-117">Using the Microsoft .NET Framework Class Library</span></span>
 <span data-ttu-id="3396f-118">脚本任务和脚本组件能够利用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 类库公开的所有其他对象和功能。</span><span class="sxs-lookup"><span data-stu-id="3396f-118">The Script task and the Script component can take advantage of all the other objects and functionality exposed by the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class library.</span></span> <span data-ttu-id="3396f-119">例如，使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 可以检索有关环境的信息，并与运行包的计算机进行交互。</span><span class="sxs-lookup"><span data-stu-id="3396f-119">For example, by using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can retrieve information about your environment and interact with the computer that is running the package.</span></span>

 <span data-ttu-id="3396f-120">下表介绍了一些比较常用的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 类：</span><span class="sxs-lookup"><span data-stu-id="3396f-120">This list describes several of the more frequently used [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes:</span></span>

-   <span data-ttu-id="3396f-121">`System.Data`包含 ADO.NET 体系结构。</span><span class="sxs-lookup"><span data-stu-id="3396f-121">`System.Data` Contains the ADO.NET architecture.</span></span>

-   <span data-ttu-id="3396f-122">`System.IO`提供文件系统和流的接口。</span><span class="sxs-lookup"><span data-stu-id="3396f-122">`System.IO` Provides an interface to the file system and streams.</span></span>

-   <span data-ttu-id="3396f-123">`System.Windows.Forms`提供窗体创建。</span><span class="sxs-lookup"><span data-stu-id="3396f-123">`System.Windows.Forms` Provides form creation.</span></span>

-   <span data-ttu-id="3396f-124">`System.Text.RegularExpressions`提供用于处理正则表达式的类。</span><span class="sxs-lookup"><span data-stu-id="3396f-124">`System.Text.RegularExpressions` Provides classes for working with regular expressions.</span></span>

-   <span data-ttu-id="3396f-125">`System.Environment`返回有关本地计算机、当前用户、计算机和用户设置的信息。</span><span class="sxs-lookup"><span data-stu-id="3396f-125">`System.Environment` Returns information about the local computer, the current user, and computer and user settings.</span></span>

-   <span data-ttu-id="3396f-126">`System.Net`提供网络通信。</span><span class="sxs-lookup"><span data-stu-id="3396f-126">`System.Net` Provides network communications.</span></span>

-   <span data-ttu-id="3396f-127">`System.DirectoryServices`公开 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="3396f-127">`System.DirectoryServices` Exposes Active Directory.</span></span>

-   <span data-ttu-id="3396f-128">`System.Drawing`提供了大量的图像操作库。</span><span class="sxs-lookup"><span data-stu-id="3396f-128">`System.Drawing` Provides extensive image manipulation libraries.</span></span>

-   <span data-ttu-id="3396f-129">`System.Threading`启用多线程编程。</span><span class="sxs-lookup"><span data-stu-id="3396f-129">`System.Threading` Enables multithreaded programming.</span></span>

 <span data-ttu-id="3396f-130">有关 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的详细信息，请参阅 MSDN Library。</span><span class="sxs-lookup"><span data-stu-id="3396f-130">For more information about the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], see the MSDN Library.</span></span>

<span data-ttu-id="3396f-131">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="3396f-131">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="3396f-132">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="3396f-132">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="3396f-133">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="3396f-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="3396f-134">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="3396f-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="3396f-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3396f-135">See Also</span></span>
 [<span data-ttu-id="3396f-136">用脚本扩展包</span><span class="sxs-lookup"><span data-stu-id="3396f-136">Extending Packages with Scripting</span></span>](extending-packages-with-scripting.md)


