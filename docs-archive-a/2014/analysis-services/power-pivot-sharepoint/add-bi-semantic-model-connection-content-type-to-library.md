---
title: 将 BI 语义模型连接内容类型添加到库 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 145505ed-50bc-4528-912b-2a5cd2566011
author: minewiskan
ms.author: owend
ms.openlocfilehash: ecd40193b382aa692beeadd55ab8f9388c328620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589919"
---
# <a name="add-a-bi-semantic-model-connection-content-type-to-a-library-powerpivot-for-sharepoint"></a><span data-ttu-id="7e52f-102">将 BI 语义模型连接内容类型添加到库 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="7e52f-102">Add a BI Semantic Model Connection Content Type to a Library (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="7e52f-103">BI 语义模型连接是在 SharePoint 中创建的，它提供对网络服务器上的 PowerPivot 工作簿或 Analysis Services 表格模型数据库中的商业智能语义模型数据的重定向。</span><span class="sxs-lookup"><span data-stu-id="7e52f-103">A BI semantic model connection is created in SharePoint and provides redirection to business intelligence semantic model data in a PowerPivot workbook or Analysis Services tabular model database on a network server.</span></span> <span data-ttu-id="7e52f-104">当您在 SharePoint 中创建 BI 语义模型连接之前，必须对文档库进行扩展以便允许创建 .bism 文件。</span><span class="sxs-lookup"><span data-stu-id="7e52f-104">Before you can create a BI semantic model connection in SharePoint, you must extend a document library to allow the creation of a .bism file.</span></span> <span data-ttu-id="7e52f-105">对于每个库，仅需执行此步骤一次，但对于您要从其创建 .bism 文件的任何库，您都将需要重复执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="7e52f-105">This step only needs to be performed once for each library, but you will need to repeat it for any library from which you want to create .bism files.</span></span> <span data-ttu-id="7e52f-106">作为最佳做法，建议您为存储 .bism 文件创建一个集中的库，以便可以在一个地方管理权限。</span><span class="sxs-lookup"><span data-stu-id="7e52f-106">Best practices recommend that you create a centralized library for storing .bism files so that you can manage permissions in one place.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e52f-107">如果您已使用 SharePoint 数据连接库，则 BI 语义模型连接内容类型将自动添加到该库模板中。</span><span class="sxs-lookup"><span data-stu-id="7e52f-107">If you already use SharePoint Data Connection Libraries, the BI Semantic Model Connection content type is automatically added to that library template.</span></span> <span data-ttu-id="7e52f-108">如果您使用的数据连接库已让您创建新的 BI 语义模型连接文档，则可以跳过本节中的这些步骤。</span><span class="sxs-lookup"><span data-stu-id="7e52f-108">You can skip the steps in this section if you use a data connection library that already lets you create new BI semantic model connection documents.</span></span>  
  
##  <a name="add-the-content-type-to-a-document-library"></a><a name="bkmk_addtype"></a> <span data-ttu-id="7e52f-109">向文档库添加内容类型</span><span class="sxs-lookup"><span data-stu-id="7e52f-109">Add the content type to a document library</span></span>  
 <span data-ttu-id="7e52f-110">您必须至少具有“管理列表”权限才能添加和配置内容类型。</span><span class="sxs-lookup"><span data-stu-id="7e52f-110">You must have at least the Manage Lists permission to add and configure a content type.</span></span> <span data-ttu-id="7e52f-111">此权限是“设计”权限级别和更高级别中所固有的。</span><span class="sxs-lookup"><span data-stu-id="7e52f-111">This permission is built into the Design permission level and above.</span></span>  
  
 <span data-ttu-id="7e52f-112">包含文档库的站点必须具有 PowerPivot for SharePoint 功能激活。</span><span class="sxs-lookup"><span data-stu-id="7e52f-112">The site that contains the document library must have feature activation for PowerPivot for SharePoint.</span></span> <span data-ttu-id="7e52f-113">有关详细信息，请参阅[在管理中心为网站集激活 PowerPivot 功能集成](activate-power-pivot-integration-for-site-collections-in-ca.md)。</span><span class="sxs-lookup"><span data-stu-id="7e52f-113">For more information, see [Activate PowerPivot Feature Integration for Site Collections in Central Administration](activate-power-pivot-integration-for-site-collections-in-ca.md).</span></span>  
  
1.  <span data-ttu-id="7e52f-114">打开要为其启用 BI 语义模型连接内容类型的文档库。</span><span class="sxs-lookup"><span data-stu-id="7e52f-114">Open the document library for which you want to enable the BI Semantic Model Connection content type.</span></span>  
  
2.  <span data-ttu-id="7e52f-115">在 SharePoint 功能区的“库工具”中，单击 **“库”**。</span><span class="sxs-lookup"><span data-stu-id="7e52f-115">On the SharePoint ribbon, in Library Tools, click **Library**.</span></span>  
  
3.  <span data-ttu-id="7e52f-116">单击 **“库设置”**。</span><span class="sxs-lookup"><span data-stu-id="7e52f-116">Click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="7e52f-117">在“常规设置”中，单击 **“高级设置”**。</span><span class="sxs-lookup"><span data-stu-id="7e52f-117">In General Settings, click **Advanced settings**.</span></span>  
  
5.  <span data-ttu-id="7e52f-118">在“内容类型”的“允许内容类型的管理?”部分中，</span><span class="sxs-lookup"><span data-stu-id="7e52f-118">In Content Types, in the "Allow management of content types?"</span></span> <span data-ttu-id="7e52f-119">单击 **“是”**。</span><span class="sxs-lookup"><span data-stu-id="7e52f-119">section, click **Yes**.</span></span>  
  
6.  <span data-ttu-id="7e52f-120">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="7e52f-120">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="7e52f-121">在“内容类型”部分中，单击 **“从现有网站内容类型添加”**。</span><span class="sxs-lookup"><span data-stu-id="7e52f-121">In the Content Types section, click **Add from existing site content types**.</span></span> <span data-ttu-id="7e52f-122">如果您看不到此页，则返回网站，在“库工具”中单击 **“库”** ，然后单击 **“库设置”**。</span><span class="sxs-lookup"><span data-stu-id="7e52f-122">If you do not see this page, go back to the site, click **Library** in Library Tools, and then click **Library Settings**.</span></span>  
  
8.  <span data-ttu-id="7e52f-123">在“内容类型”中，单击 **“从现有网站内容类型添加”**。</span><span class="sxs-lookup"><span data-stu-id="7e52f-123">In Content Types, click **Add from existing site content types**.</span></span>  
  
9. <span data-ttu-id="7e52f-124">在“从以下列表中选择网站内容类型:”中，选择 **“商业智能”**。</span><span class="sxs-lookup"><span data-stu-id="7e52f-124">In Select site content types from:, select **Business Intelligence**.</span></span>  
  
10. <span data-ttu-id="7e52f-125">在“可用网站内容类型”中，单击 **“BI 语义模型连接文件”**，然后单击 **“添加”** 将所选内容类型移至“要添加的内容类型”列表中。</span><span class="sxs-lookup"><span data-stu-id="7e52f-125">In Available Site Content Types, click **BI Semantic Model Connection File**, and then click **Add** to move the selected content type to the Content types to add list.</span></span>  
  
11. <span data-ttu-id="7e52f-126">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="7e52f-126">Click **OK**.</span></span>  
  
12. <span data-ttu-id="7e52f-127">若要验证您是否添加了此连接类型，请返回到库，然后单击库功能区的“文档”区域上的 **“新建文档”** 。</span><span class="sxs-lookup"><span data-stu-id="7e52f-127">To verify you added the content type, go back to the library and click **New Document** on the Documents area of the library ribbon.</span></span> <span data-ttu-id="7e52f-128">您应该会在“新建文档”列表中看到 **“BI 语义模型连接文件”** 。</span><span class="sxs-lookup"><span data-stu-id="7e52f-128">You should see **BI Semantic Model Connection File** in the New Documents list.</span></span>  
  
     <span data-ttu-id="7e52f-129">![SharePoint 库中的“新建文档”子菜单](../media/ssas-bismconnection-new.gif "SharePoint 库中的“新建文档”子菜单")</span><span class="sxs-lookup"><span data-stu-id="7e52f-129">![New Document submenu in a SharePoint library](../media/ssas-bismconnection-new.gif "New Document submenu in a SharePoint library")</span></span>  
  
 <span data-ttu-id="7e52f-130">在为库启用了 BI 语义模型连接内容类型后，您可以创建一个连接，用于提供对可供 Excel 或 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 报表使用的商业语义模型数据的重定向。</span><span class="sxs-lookup"><span data-stu-id="7e52f-130">After you enable the BI semantic model connection content type for a library, you can create a connection that provides redirection to business semantic model data that can be used by Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span> <span data-ttu-id="7e52f-131">从以下链接中进行选择，以了解有关下一步的详情：</span><span class="sxs-lookup"><span data-stu-id="7e52f-131">Choose from the following links to learn more about this next step:</span></span>  
  
 [<span data-ttu-id="7e52f-132">创建与 PowerPivot 工作簿的 BI 语义模型连接</span><span class="sxs-lookup"><span data-stu-id="7e52f-132">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)  
  
 [<span data-ttu-id="7e52f-133">Create a BI Semantic Model Connection to a Tabular Model Database</span><span class="sxs-lookup"><span data-stu-id="7e52f-133">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="7e52f-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e52f-134">See Also</span></span>  
 <span data-ttu-id="7e52f-135">[PowerPivot BI 语义模型连接 &#40; bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="7e52f-135">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 [<span data-ttu-id="7e52f-136">在 Excel 或 Reporting Services 中使用 BI 语义模型连接</span><span class="sxs-lookup"><span data-stu-id="7e52f-136">Use a BI Semantic Model Connection in Excel or Reporting Services</span></span>](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)  
  
  
