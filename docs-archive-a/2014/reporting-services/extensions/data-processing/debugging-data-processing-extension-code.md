---
title: 调试数据处理扩展插件代码 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bf7490145f91ee8b3cfc2357c34010bed593ed9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581132"
---
# <a name="debugging-data-processing-extension-code"></a><span data-ttu-id="dd59b-102">调试数据处理扩展插件代码</span><span class="sxs-lookup"><span data-stu-id="dd59b-102">Debugging Data Processing Extension Code</span></span>
  <span data-ttu-id="dd59b-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供了一些可以帮助分析数据处理扩展插件代码和查找其中错误的调试工具。</span><span class="sxs-lookup"><span data-stu-id="dd59b-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your data processing extension code and locate errors in it.</span></span> <span data-ttu-id="dd59b-104">哪个工具效果最佳取决于您试图完成的任务。</span><span class="sxs-lookup"><span data-stu-id="dd59b-104">The tool that works best will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="dd59b-105">此示例使用 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dd59b-105">This example uses [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].</span></span>  
  
#### <a name="to-debug-your-data-processing-extension-code"></a><span data-ttu-id="dd59b-106">调试数据处理扩展插件代码</span><span class="sxs-lookup"><span data-stu-id="dd59b-106">To debug your data processing extension code</span></span>  
  
1.  <span data-ttu-id="dd59b-107">启动 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] 并打开数据处理扩展插件项目。</span><span class="sxs-lookup"><span data-stu-id="dd59b-107">Launch [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)], and open your data processing extension project.</span></span>  
  
2.  <span data-ttu-id="dd59b-108">生成项目，并将数据处理扩展插件程序集以及随附的 .pdb 文件部署到报表设计器。</span><span class="sxs-lookup"><span data-stu-id="dd59b-108">Build the project, and deploy your data processing extension assembly and the accompanying .pdb file to the Report Designer.</span></span> <span data-ttu-id="dd59b-109">有关部署的详细信息，请参阅[如何：将数据处理扩展插件部署到报表设计器](deploying-a-data-processing-extension-to-report-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="dd59b-109">For more information about deployment, see [How to: Deploy a Data Processing Extension to Report Designer](deploying-a-data-processing-extension-to-report-designer.md).</span></span>  
  
3.  <span data-ttu-id="dd59b-110">在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中打开新的报表项目，同时在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的一个单独窗口中让数据处理扩展插件代码处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="dd59b-110">Open a new Report Project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] while leaving your data processing extension code open in a separate window of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
4.  <span data-ttu-id="dd59b-111">导航到 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中包含数据处理扩展插件项目的窗口，并在代码中设置一些断点。</span><span class="sxs-lookup"><span data-stu-id="dd59b-111">Navigate to the window of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] that contains your data processing extension project and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="dd59b-112">在数据处理扩展插件项目窗口仍保持活动状态的同时，在“调试”菜单上，单击“附加到进程”   。</span><span class="sxs-lookup"><span data-stu-id="dd59b-112">With the data processing extension project window still active, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="dd59b-113">“附加到进程”对话框会打开  。</span><span class="sxs-lookup"><span data-stu-id="dd59b-113">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="dd59b-114">从进程列表中，选择与报表项目对应的 devenv.exe 进程并单击“附加”  。</span><span class="sxs-lookup"><span data-stu-id="dd59b-114">From the list of processes, select the devenv.exe process that corresponds to your Report Project and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="dd59b-115">使用报表项目的“报表数据”选项卡定义报表数据源  。</span><span class="sxs-lookup"><span data-stu-id="dd59b-115">Define your report data source using the **Report Data** tab of the Report Project.</span></span> <span data-ttu-id="dd59b-116">您最有可能使用一般性查询设计器来针对自定义数据源执行查询。</span><span class="sxs-lookup"><span data-stu-id="dd59b-116">You will most likely use the generic Query Designer to execute a query against your custom data source.</span></span> <span data-ttu-id="dd59b-117">这将调用调试器并执行对应于断点的代码。</span><span class="sxs-lookup"><span data-stu-id="dd59b-117">This should invoke the debugger and execute code corresponding to your break points.</span></span>  
  
8.  <span data-ttu-id="dd59b-118">使用 F11 键分步执行代码。</span><span class="sxs-lookup"><span data-stu-id="dd59b-118">Step through your code using the F11 key.</span></span> <span data-ttu-id="dd59b-119">有关使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 进行调试的详细信息，请参阅 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文档。</span><span class="sxs-lookup"><span data-stu-id="dd59b-119">For more information about using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] for debugging, see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd59b-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd59b-120">See Also</span></span>  
 <span data-ttu-id="dd59b-121">[部署数据处理扩展插件](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="dd59b-121">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="dd59b-122">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="dd59b-122">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="dd59b-123">[实现数据处理扩展插件](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="dd59b-123">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="dd59b-124">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="dd59b-124">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
