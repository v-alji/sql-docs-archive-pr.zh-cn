---
title: 将报表或模型绑定到共享数据源 (SSRS)| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 596caba042d476173b3c49d1ad18e79d0827fe89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688603"
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a><span data-ttu-id="47924-102">将报表或模型绑定到共享数据源 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="47924-102">Bind a Report or Model to a Shared Data Source (SSRS)</span></span>
  <span data-ttu-id="47924-103">在某些情况下，例如将报表或模型从测试服务器移到生产服务器时，最好将文件保存到本地计算机，然后将其上载到其他报表服务器。</span><span class="sxs-lookup"><span data-stu-id="47924-103">In some situations, such as when you move a report or model from a test server to a production server, you might want to save the file to your local computer and then upload it to a different report server.</span></span> <span data-ttu-id="47924-104">将报表或模型上载到新服务器时，需要将其重新绑定到存储在新报表服务器上的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="47924-104">When you upload the report or model to the new server, you need to rebind it to a shared data source that is stored on the new report server.</span></span> <span data-ttu-id="47924-105">如果不重新绑定报表或模型，在从新报表服务器对其进行访问时，报表或模型将无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="47924-105">If you don't rebind the report or model, it will not work correctly when accessed from the new report server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47924-106">在将报表或模型重新绑定到共享数据源之前，报表服务器或 SharePoint 库中必须已经存在该数据源。</span><span class="sxs-lookup"><span data-stu-id="47924-106">Before rebinding a report or model to a shared data source, the data source must already exist on the report server or SharePoint library.</span></span> <span data-ttu-id="47924-107">有关数据源的详细信息，请参阅[创建、修改和删除共享数据源 (SSRS)](create-modify-and-delete-shared-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="47924-107">For more information about data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a><span data-ttu-id="47924-108">将报表或模型绑定到在本机模式下运行的报表服务器上的共享数据源</span><span class="sxs-lookup"><span data-stu-id="47924-108">To bind a report or model to a shared data source on a report server running in native mode</span></span>  
  
1.  <span data-ttu-id="47924-109">在 **报表管理器**中，单击已上载到服务器的报表或模型的名称。</span><span class="sxs-lookup"><span data-stu-id="47924-109">In **Report Manager**, click the name of the report or model that you uploaded to the server.</span></span>  
  
     <span data-ttu-id="47924-110">将打开“属性”选项卡。</span><span class="sxs-lookup"><span data-stu-id="47924-110">The Properties tab opens.</span></span>  
  
2.  <span data-ttu-id="47924-111">单击 **“数据源”**。</span><span class="sxs-lookup"><span data-stu-id="47924-111">Click **Data Sources**.</span></span>  
  
3.  <span data-ttu-id="47924-112">单击 **“浏览”**，然后导航到要绑定报表或模型的数据源。</span><span class="sxs-lookup"><span data-stu-id="47924-112">Click **Browse**, and then navigate to the data source to which you want to bind the report or model.</span></span>  
  
4.  <span data-ttu-id="47924-113">选择数据源，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="47924-113">Select the data source and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="47924-114">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="47924-114">Click **Apply**.</span></span>  
  
     <span data-ttu-id="47924-115">此时，报表或模型已绑定到您选择的数据源。</span><span class="sxs-lookup"><span data-stu-id="47924-115">The report or model is now bound to the data source that you selected.</span></span>  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a><span data-ttu-id="47924-116">将报表或模型绑定到在 SharePoint 集成模式下运行的报表服务器上的共享数据源</span><span class="sxs-lookup"><span data-stu-id="47924-116">To bind a report or model to a shared data source on a report server running in SharePoint integrated mode</span></span>  
  
1.  <span data-ttu-id="47924-117">如果尚未打开库，请在“快速启动”栏上单击其名称。</span><span class="sxs-lookup"><span data-stu-id="47924-117">If the library is not already open, click its name on the Quick Launch bar.</span></span> <span data-ttu-id="47924-118">如果未显示库的名称，请单击 **“查看所有网站内容”**，然后单击库的名称。</span><span class="sxs-lookup"><span data-stu-id="47924-118">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="47924-119">指向报表或模型，然后单击向下箭头。</span><span class="sxs-lookup"><span data-stu-id="47924-119">Point to the report or model and click the down arrow.</span></span>  
  
3.  <span data-ttu-id="47924-120">单击 **“管理数据源”**。</span><span class="sxs-lookup"><span data-stu-id="47924-120">Click **Manage Data Sources**.</span></span>  
  
4.  <span data-ttu-id="47924-121">单击 **“dataSource1”**。</span><span class="sxs-lookup"><span data-stu-id="47924-121">Click **dataSource1**.</span></span>  
  
5.  <span data-ttu-id="47924-122">在 **“连接类型”** 区域中，确认已选中 **“共享数据源”** 。</span><span class="sxs-lookup"><span data-stu-id="47924-122">In the **Connection Type** area, verify that **Shared data source** is selected.</span></span>  
  
6.  <span data-ttu-id="47924-123">在“数据源链接”区域中，单击省略号 (...) 按钮\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="47924-123">In the **Data Source Link** area, click the ellipsis (...) button.</span></span>  
  
7.  <span data-ttu-id="47924-124">找到要使用的数据源。</span><span class="sxs-lookup"><span data-stu-id="47924-124">Locate the data source you want to use.</span></span>  
  
8.  <span data-ttu-id="47924-125">选择数据源并单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="47924-125">Select the data source and **click OK**.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="47924-126">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="47924-126">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47924-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47924-127">See Also</span></span>  
 <span data-ttu-id="47924-128">[报表管理器 &#40;上传文件或报表&#41;](../reports/upload-a-file-or-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="47924-128">[Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md) </span></span>  
 <span data-ttu-id="47924-129">[在 SharePoint 模式下将文档上传到 SharePoint 库 &#40;Reporting Services&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="47924-129">[Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="47924-130">[在 SharePoint 集成模式下创建和管理共享数据源 &#40;Reporting Services&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="47924-130">[Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="47924-131">[创建、删除或修改共享数据源 &#40;报表管理器&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="47924-131">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="47924-132">[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="47924-132">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="47924-133">Reporting Services 支持的数据源 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="47924-133">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
