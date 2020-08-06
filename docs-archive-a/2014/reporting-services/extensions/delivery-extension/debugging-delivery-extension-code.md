---
title: 调试传递扩展插件代码 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], debugging
- debugging delivery extensions [Reporting Services]
- troubleshooting [Reporting Services], delivery extensions
ms.assetid: a7d959da-5005-4a50-aca7-2cef36aa9947
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb80ac97f5c0e346b208784f1fa5b857ff93ef57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693619"
---
# <a name="debugging-delivery-extension-code"></a><span data-ttu-id="fedc1-102">调试传递扩展插件代码</span><span class="sxs-lookup"><span data-stu-id="fedc1-102">Debugging Delivery Extension Code</span></span>
  <span data-ttu-id="fedc1-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供了一些调试工具，有助于分析传递扩展插件代码并定位其中的错误。</span><span class="sxs-lookup"><span data-stu-id="fedc1-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your delivery extension code and locate errors in it.</span></span> <span data-ttu-id="fedc1-104">哪个工具效果最佳取决于您试图完成的任务。</span><span class="sxs-lookup"><span data-stu-id="fedc1-104">The tool that works best will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="fedc1-105">此示例使用 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fedc1-105">This example uses [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].</span></span>  
  
#### <a name="to-debug-your-delivery-extension-code"></a><span data-ttu-id="fedc1-106">调试传递扩展插件代码</span><span class="sxs-lookup"><span data-stu-id="fedc1-106">To debug your delivery extension code</span></span>  
  
1.  <span data-ttu-id="fedc1-107">启动 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] 并打开传递扩展插件项目。</span><span class="sxs-lookup"><span data-stu-id="fedc1-107">Launch [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] and open your delivery extension project.</span></span>  
  
2.  <span data-ttu-id="fedc1-108">生成项目，并将传递扩展插件程序集以及随附的 .pdb 文件部署到报表服务器和报表管理器。</span><span class="sxs-lookup"><span data-stu-id="fedc1-108">Build the project and deploy your delivery extension assembly and the accompanying .pdb file to the report server and Report Manager.</span></span> <span data-ttu-id="fedc1-109">有关部署的详细信息，请参阅[部署传递扩展插件](deploying-a-delivery-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="fedc1-109">For more information about deployment, see [Deploying a Delivery Extension](deploying-a-delivery-extension.md).</span></span>  
  
3.  <span data-ttu-id="fedc1-110">如果您编写了订阅用户界面以扩展报表管理器，请打开 Internet Explorer 并导航到报表管理器，同时在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中保持传递扩展插件代码处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="fedc1-110">If you have written a subscription user interface to extend Report Manager, open Internet Explorer and navigate to Report Manager while leaving your delivery extension code open in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="fedc1-111">如果没有为报表管理器部署订阅用户界面，则只需打开客户端应用程序，从中可以使用 SOAP API 调用传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="fedc1-111">If you do not have a subscription user interface deployed for Report Manager, simply open the client application from which you call your delivery extension using the SOAP API.</span></span>  
  
4.  <span data-ttu-id="fedc1-112">导航到 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 和传递扩展插件项目，并在代码中设置一些断点。</span><span class="sxs-lookup"><span data-stu-id="fedc1-112">Navigate to [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and your delivery extension project, and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="fedc1-113">在传递扩展插件项目的窗口仍保持活动状态的同时，在“调试”菜单中单击“附加到进程”   。</span><span class="sxs-lookup"><span data-stu-id="fedc1-113">With the delivery extension project still the active window, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="fedc1-114">“附加到进程”对话框会打开  。</span><span class="sxs-lookup"><span data-stu-id="fedc1-114">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="fedc1-115">从进程列表中，选择 aspnet_wp.exe 进程（如果应用程序是在 IIS 6.0 中部署的，请选择 w3wp.exe），然后单击“附加”  。</span><span class="sxs-lookup"><span data-stu-id="fedc1-115">From the list of processes, select the aspnet_wp.exe process (or w3wp.exe if your application is deployed on IIS 6.0), and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="fedc1-116">使用传递扩展插件定义新订阅。</span><span class="sxs-lookup"><span data-stu-id="fedc1-116">Define a new subscription using your delivery extension.</span></span> <span data-ttu-id="fedc1-117">您最可能使用报表管理器或 SOAP API。</span><span class="sxs-lookup"><span data-stu-id="fedc1-117">You will most likely use Report Manager or the SOAP API.</span></span> <span data-ttu-id="fedc1-118">这将调用调试器并执行对应于断点的代码。</span><span class="sxs-lookup"><span data-stu-id="fedc1-118">This should invoke the debugger and execute code corresponding to your break points.</span></span>  
  
8.  <span data-ttu-id="fedc1-119">使用 F11 键分步执行代码  。</span><span class="sxs-lookup"><span data-stu-id="fedc1-119">Step through your code using the **F11** key.</span></span> <span data-ttu-id="fedc1-120">有关使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 进行调试的详细信息，请参阅 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文档。</span><span class="sxs-lookup"><span data-stu-id="fedc1-120">For more information about using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] for debugging, see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fedc1-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fedc1-121">See Also</span></span>  
 <span data-ttu-id="fedc1-122">[实现传递扩展插件](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="fedc1-122">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="fedc1-123">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="fedc1-123">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
