---
title: 在 SharePoint 模式下将文档上载到 SharePoint 库 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- SharePoint integration [Reporting Services], content management
- uploading reports [Reporting Services]
ms.assetid: 93bd1b19-061b-409f-8dc2-ec416b2f4b39
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 74b39f90cd90dc8a92a5f10168d98f165c211c51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692207"
---
# <a name="upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="cf93d-102">将文档上载到 SharePoint 库（SharePoint 模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="cf93d-102">Upload Documents to a SharePoint Library (Reporting Services in SharePoint Mode)</span></span>
  <span data-ttu-id="cf93d-103">您可以将报表定义和报表模型上载到 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="cf93d-103">You can upload report definitions and report models to a SharePoint library.</span></span> <span data-ttu-id="cf93d-104">上载报表服务器项时，您必须选择一个库或库中的一个文件夹。</span><span class="sxs-lookup"><span data-stu-id="cf93d-104">When uploading a report server item, you must select a library or a folder within a library.</span></span> <span data-ttu-id="cf93d-105">不能将报表服务器项上载到某个列表或页。</span><span class="sxs-lookup"><span data-stu-id="cf93d-105">You cannot upload a report server item to a list or page.</span></span>  
  
 <span data-ttu-id="cf93d-106">不能上载数据源 (.rds) 文件。</span><span class="sxs-lookup"><span data-stu-id="cf93d-106">You cannot upload a data source (.rds) file.</span></span> <span data-ttu-id="cf93d-107">但是，可以从设计工具（如报表设计器）中向 SharePoint 库发布 .rds 文件。</span><span class="sxs-lookup"><span data-stu-id="cf93d-107">However, you can publish .rds files from a design tool, such as Report Designer, to a SharePoint library.</span></span> <span data-ttu-id="cf93d-108">在发布期间，将根据解决方案中的原始 .rds 文件创建一个新的 .rsds 文件。</span><span class="sxs-lookup"><span data-stu-id="cf93d-108">During publication, a new .rsds file is created from the original .rds file in the solution.</span></span> <span data-ttu-id="cf93d-109">您也可以在 SharePoint 库中创建一个新的 .rsds 文件，然后在上载的报表和模型中设置数据源连接属性以使用新的连接。</span><span class="sxs-lookup"><span data-stu-id="cf93d-109">You can also create a new .rsds file in a SharePoint library and then set data source connection properties in the uploaded reports and models to use the new connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf93d-110">报表服务器必须配置为使用 SharePoint 模式，且 SharePoint 产品的实例必须安装了 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 外接程序，此外接程序提供了从 SharePoint 站点中存储和访问报表服务器项的程序文件。</span><span class="sxs-lookup"><span data-stu-id="cf93d-110">The report server must be configured for SharePoint mode, and the instance of the SharePoint product must have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in that provides program files for storing and accessing report server items from a SharePoint site.</span></span>  
  
 <span data-ttu-id="cf93d-111">若要将文档上载到库中，您必须拥有站点级别的“添加项”权限。</span><span class="sxs-lookup"><span data-stu-id="cf93d-111">To upload a document to a library, you must have the "Add Items" permission at the site level.</span></span> <span data-ttu-id="cf93d-112">如果您使用的是默认安全设置，将对拥有“完全控制”级别权限的“所有者” \*\*\*\* 组成员和拥有“参与讨论”级别权限的“成员” \*\*\*\* 组授予该权限。</span><span class="sxs-lookup"><span data-stu-id="cf93d-112">If you are using default security settings, this permission is granted to members of the **Owners** group who have the Full Control level of permission and to the **Members** group who have the Contribute level of permission.</span></span>  
  
### <a name="to-add-a-report-definition-or-report-model-to-a-library"></a><span data-ttu-id="cf93d-113">向库中添加报表定义或报表模型</span><span class="sxs-lookup"><span data-stu-id="cf93d-113">To add a report definition or report model to a library</span></span>  
  
1.  <span data-ttu-id="cf93d-114">打开库或库中的某个文件夹。</span><span class="sxs-lookup"><span data-stu-id="cf93d-114">Open the library or a folder within a library.</span></span> <span data-ttu-id="cf93d-115">如果库尚未打开，请在“快速启动”上单击其名称。</span><span class="sxs-lookup"><span data-stu-id="cf93d-115">If the library is not already open, click its name on the Quick Launch.</span></span> <span data-ttu-id="cf93d-116">如果未显示库的名称，请单击 **“查看所有网站内容”**，然后单击库的名称。</span><span class="sxs-lookup"><span data-stu-id="cf93d-116">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="cf93d-117">在 **“上载”** 菜单中，单击 **“上载文档”**。</span><span class="sxs-lookup"><span data-stu-id="cf93d-117">On the **Upload** menu, click **Upload document**.</span></span>  
  
3.  <span data-ttu-id="cf93d-118">若要上传单个报表或报表模型文件，请选择报表定义 (.rdl) 或报表模型 (.smdl) 文件，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf93d-118">To upload a single report or report model file, select a report definition (.rdl) or report model (.smdl) file and then click **OK**.</span></span>  
  
     <span data-ttu-id="cf93d-119">如果报表定义使用共享数据源 (.rsds) 文件存储与外部数据源的连接信息，则可以同时上载 .rdl 和 .rsds 文件。</span><span class="sxs-lookup"><span data-stu-id="cf93d-119">If the report definition uses a shared data source (.rsds) file to store connection information to an external data source, you can upload the .rdl and the .rsds file at the same time.</span></span> <span data-ttu-id="cf93d-120">为此，请单击 **“上载多个文档”**，指定这两个文件，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="cf93d-120">To do this, click **Upload Multiple Documents**, specify both files, and then click **OK**.</span></span>  
  
 <span data-ttu-id="cf93d-121">如果您上载的报表包含对共享数据源、报表模型或子报表的引用，则文件上载后这些引用将会断开。</span><span class="sxs-lookup"><span data-stu-id="cf93d-121">If you upload a report that contains references to shared data sources, report models, or subreports, the references will be broken in the report when the files are uploaded.</span></span> <span data-ttu-id="cf93d-122">有关如何重置引用的详细信息，请参阅[创建和管理共享数据源（SharePoint 集成模式下的 Reporting Services）](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="cf93d-122">For more information about how to reset the references, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
 <span data-ttu-id="cf93d-123">上载报表后，它将在打开时按需运行，并从数据源检索实时数据。</span><span class="sxs-lookup"><span data-stu-id="cf93d-123">When you upload a report, it runs on demand when you open it, retrieving live data from the data source.</span></span> <span data-ttu-id="cf93d-124">您可以将报表配置为按计划检索数据或使用缓存数据。</span><span class="sxs-lookup"><span data-stu-id="cf93d-124">You can configure the report to retrieve data on a schedule or use cached data.</span></span> <span data-ttu-id="cf93d-125">有关详细信息，请参阅[设置处理选项（SharePoint 集成模式下的 Reporting Services）](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="cf93d-125">For more information, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
 <span data-ttu-id="cf93d-126">报表可以包含参数以便用户能够筛选数据。</span><span class="sxs-lookup"><span data-stu-id="cf93d-126">A report can contain parameters so that users can filter data.</span></span> <span data-ttu-id="cf93d-127">您可以将参数配置为使用特定值或更改参数对用户的显示方式。</span><span class="sxs-lookup"><span data-stu-id="cf93d-127">You can configure the parameters to use specific values or change how they appear to the user.</span></span> <span data-ttu-id="cf93d-128">有关详细信息，请参阅[在已发布报表上设置参数（SharePoint 集成模式下的 Reporting Services）](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="cf93d-128">For more information, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf93d-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf93d-129">See Also</span></span>  
 <span data-ttu-id="cf93d-130">[将报表发布到 SharePoint 库](reports/publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="cf93d-130">[Publish a Report to a SharePoint Library](reports/publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="cf93d-131">[将共享数据源发布到 SharePoint 库](reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="cf93d-131">[Publish a Shared Data Source to a SharePoint Library](reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span></span>  
 [<span data-ttu-id="cf93d-132">在 SharePoint 站点上授予对报表服务器项的权限</span><span class="sxs-lookup"><span data-stu-id="cf93d-132">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
