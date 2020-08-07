---
title: 从 Microsoft Access (Reporting Services) 导入报表 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862d8b90f3c91dffda35971677db7fdc231c1b63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589451"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a><span data-ttu-id="1f70e-102">从 Microsoft Access 导入报表 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="1f70e-102">Import Reports from Microsoft Access (Reporting Services)</span></span>
  <span data-ttu-id="1f70e-103">在报表设计器中，可以从 [!INCLUDE[msCoName](../includes/msconame-md.md)] Access 数据库或项目中导入报表。</span><span class="sxs-lookup"><span data-stu-id="1f70e-103">In Report Designer, you can import reports from a [!INCLUDE[msCoName](../includes/msconame-md.md)] Access database or project.</span></span> <span data-ttu-id="1f70e-104">必须在安装报表设计器的计算机上安装 Access 2002 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="1f70e-104">Access 2002 or a later version must be installed on the same computer on which Report Designer is installed.</span></span>  
  
 <span data-ttu-id="1f70e-105">使用导入功能时，将导入数据库或项目文件中的所有报表。</span><span class="sxs-lookup"><span data-stu-id="1f70e-105">When you use the import feature, all reports in the database or project file are imported.</span></span> <span data-ttu-id="1f70e-106">如果 Access 文件中包含多个报表，您可能需要创建一个单独的报表项目，以便将报表导入到其中，然后在主报表项目中打开各个 RDL 文件。</span><span class="sxs-lookup"><span data-stu-id="1f70e-106">If your Access file contains many reports, you may want to create a separate report project into which to import the reports, and then open the individual RDL files in your main report project.</span></span> <span data-ttu-id="1f70e-107">将报表导入到报表设计器后，可以对报表进行编辑。</span><span class="sxs-lookup"><span data-stu-id="1f70e-107">You can edit the reports after they are imported into Report Designer.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="1f70e-108">并不支持所有的 Access 报表对象。</span><span class="sxs-lookup"><span data-stu-id="1f70e-108">does not support all Access report objects.</span></span> <span data-ttu-id="1f70e-109">未转换的项将显示在 "**任务列表**" 窗口中。</span><span class="sxs-lookup"><span data-stu-id="1f70e-109">Items that are not converted are displayed in the **Task List** window.</span></span> <span data-ttu-id="1f70e-110">有关详细信息，请参阅[支持的 Access 报表功能 &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1f70e-110">For more information, see [Supported Access Report Features &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).</span></span>  
  
### <a name="to-import-reports-from-microsoft-access"></a><span data-ttu-id="1f70e-111">从 Microsoft Access 导入报表</span><span class="sxs-lookup"><span data-stu-id="1f70e-111">To import reports from Microsoft Access</span></span>  
  
1.  <span data-ttu-id="1f70e-112">打开或创建一个项目，报表将导入其中。</span><span class="sxs-lookup"><span data-stu-id="1f70e-112">Open or create a project into which to import the reports.</span></span>  
  
2.  <span data-ttu-id="1f70e-113">在 "**项目**" 菜单上，指向 "**导入报表**"，然后单击 " **Microsoft Access**"。</span><span class="sxs-lookup"><span data-stu-id="1f70e-113">On the **Project** menu, point to **Import Reports**, and then click **Microsoft Access**.</span></span> <span data-ttu-id="1f70e-114">或者，在解决方案资源管理器中右键单击项目，指向 "**导入报表**"，然后单击 " **Microsoft Access**"。</span><span class="sxs-lookup"><span data-stu-id="1f70e-114">Alternatively, right-click the project in Solution Explorer, point to **Import Reports**, and then click **Microsoft Access**.</span></span>  
  
3.  <span data-ttu-id="1f70e-115">在 "**打开**" 对话框中，选择包含报表的 Access 数据库 ( .mdb、.accdb) 或 project ( .adp) ，然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="1f70e-115">In the **Open** dialog box, select the Access database (.mdb, .accdb) or project (.adp) that contains the reports, and then click **Open**.</span></span> <span data-ttu-id="1f70e-116">数据库或项目文件中的所有报表将被导入，并在解决方案资源管理器的“报表”文件夹中列出。</span><span class="sxs-lookup"><span data-stu-id="1f70e-116">All the reports in the database or project file are imported and listed in the Reports folder in Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="1f70e-117">检查 "**任务列表**" 窗口中是否存在生成错误。</span><span class="sxs-lookup"><span data-stu-id="1f70e-117">Check the **Task List** window for build errors.</span></span> <span data-ttu-id="1f70e-118">若要查看 "**任务列表**" 窗口，请打开 "**视图**" 菜单，指向 "**其他窗口**"，再单击 "**任务列表**"。</span><span class="sxs-lookup"><span data-stu-id="1f70e-118">To view the **Task List** window, open the **View** menu, point to **Other Windows**, and then click **Task List**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f70e-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f70e-119">See Also</span></span>  
 [<span data-ttu-id="1f70e-120">使用报表设计器设计报表 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="1f70e-120">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
