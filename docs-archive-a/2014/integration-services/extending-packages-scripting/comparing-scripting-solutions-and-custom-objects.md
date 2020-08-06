---
title: 比较脚本解决方案与自定义对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- managed tasks [Integration Services]
- Script task [Integration Services], vs. custom managed tasks
- SSIS Script task, vs. custom managed tasks
- custom tasks [Integration Services], scripts
ms.assetid: c0aea822-a21e-44e1-a3d3-8777bd0a1c34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: acf6faf9cdd78e951b8298c4e3b144d3444fb1ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578353"
---
# <a name="comparing-scripting-solutions-and-custom-objects"></a><span data-ttu-id="7a097-102">比较脚本解决方案与自定义对象</span><span class="sxs-lookup"><span data-stu-id="7a097-102">Comparing Scripting Solutions and Custom Objects</span></span>
  <span data-ttu-id="7a097-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 脚本任务或脚本组件可实现许多可用于自定义托管任务或数据流组件的相同功能。</span><span class="sxs-lookup"><span data-stu-id="7a097-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Script task or Script component can implement much of the same functionality that is possible in a custom managed task or data flow component.</span></span> <span data-ttu-id="7a097-104">下面是有助于您根据需要选择相应的任务类型的一些注意事项：</span><span class="sxs-lookup"><span data-stu-id="7a097-104">Here are some considerations to help you choose the appropriate type of task for your needs:</span></span>  
  
-   <span data-ttu-id="7a097-105">如果配置或功能特定于单个包，则应使用脚本任务或脚本组件，而不是开发自定义对象。</span><span class="sxs-lookup"><span data-stu-id="7a097-105">If the configuration or functionality is specific to an individual package, you should use the Script task or the Script component instead of a developing a custom object.</span></span>  
  
-   <span data-ttu-id="7a097-106">如果功能是一般功能，并可在将来供其他包和其他开发人员使用，则应创建自定义对象，而不是使用脚本解决方案。</span><span class="sxs-lookup"><span data-stu-id="7a097-106">If the functionality is generic, and might be used in the future for other packages and by other developers, you should create a custom object instead of using a scripting solution.</span></span> <span data-ttu-id="7a097-107">您可以在任何包中使用自定义对象，而脚本只能在为其创建的包中使用。</span><span class="sxs-lookup"><span data-stu-id="7a097-107">You can use a custom object in any package, whereas a script can be used only in the package for which it was created.</span></span>  
  
-   <span data-ttu-id="7a097-108">如果将在同一个包中重新使用代码，则应考虑创建一个自定义对象。</span><span class="sxs-lookup"><span data-stu-id="7a097-108">If the code will be reused within the same package, you should consider creating a custom object.</span></span> <span data-ttu-id="7a097-109">将一个脚本任务或组件的代码复制到另一个脚本任务或组件，将导致多个代码副本的维护和更新更加困难，从而降低可维护性。</span><span class="sxs-lookup"><span data-stu-id="7a097-109">Copying code from one Script task or component to another leads to reduced maintainability by making it more difficult to maintain and update multiple copies of the code.</span></span>  
  
-   <span data-ttu-id="7a097-110">如果实现将随时间而发生变化，则可考虑使用自定义对象。</span><span class="sxs-lookup"><span data-stu-id="7a097-110">If the implementation will change over time, consider using a custom object.</span></span> <span data-ttu-id="7a097-111">自定义对象的开发和部署可以独立于父包，而对脚本解决方案所做的更新则需要重新部署整个包。</span><span class="sxs-lookup"><span data-stu-id="7a097-111">Custom objects can be developed and deployed separately from the parent package, whereas an update made to a scripting solution requires the redeployment of the whole package.</span></span>  
  
<span data-ttu-id="7a097-112">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="7a097-112">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7a097-113">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="7a097-113">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7a097-114">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="7a097-114">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7a097-115">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="7a097-115">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a097-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a097-116">See Also</span></span>  
 [<span data-ttu-id="7a097-117">用自定义对象扩展包</span><span class="sxs-lookup"><span data-stu-id="7a097-117">Extending Packages with Custom Objects</span></span>](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  
