---
title: 从数据馈送导入 (SSAS 表格) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0686e519-67c2-4f9b-8cd2-84a4871499ee
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7e5446effdcd01a3fe0eeb5dd14a1a61e97c417b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590974"
---
# <a name="import-from-a-data-feed-ssas-tabular"></a><span data-ttu-id="d9c72-102">从数据馈送导入（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="d9c72-102">Import from a Data Feed (SSAS Tabular)</span></span>
  <span data-ttu-id="d9c72-103">数据馈送是从联机数据源生成的流向目标文档或应用程序的一个或多个 XML 数据流。</span><span class="sxs-lookup"><span data-stu-id="d9c72-103">Data feeds are one or more XML data streams that are generated from an online data source and streamed to a destination document or application.</span></span> <span data-ttu-id="d9c72-104">可以通过使用“表导入向导”将数据从数据馈送导入模型中。</span><span class="sxs-lookup"><span data-stu-id="d9c72-104">You can import data from a data feed into your model by using the Table Import Wizard.</span></span>  
  
 <span data-ttu-id="d9c72-105">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="d9c72-105">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="d9c72-106">了解从数据馈送导入</span><span class="sxs-lookup"><span data-stu-id="d9c72-106">Understanding import from a data feed</span></span>](#prereq)  
  
-   [<span data-ttu-id="d9c72-107">从 Azure DataMarket 数据集导入数据</span><span class="sxs-lookup"><span data-stu-id="d9c72-107">Import data from an Azure DataMarket dataset</span></span>](#azure)  
  
-   [<span data-ttu-id="d9c72-108">从公共数据源或公司数据源导入数据馈送</span><span class="sxs-lookup"><span data-stu-id="d9c72-108">Import data feeds from public or corporate data sources</span></span>](#importdata)  
  
-   [<span data-ttu-id="d9c72-109">从 SharePoint 列表导入数据馈送</span><span class="sxs-lookup"><span data-stu-id="d9c72-109">Import data feeds from SharePoint lists</span></span>](#importlist)  
  
-   [<span data-ttu-id="d9c72-110">从 Reporting Services 报表导入数据馈送</span><span class="sxs-lookup"><span data-stu-id="d9c72-110">Import data feeds from Reporting Services Reports</span></span>](#importreport)  
  
##  <a name="understanding-import-from-a-data-feed"></a><a name="prereq"></a><span data-ttu-id="d9c72-111">了解从数据馈送导入</span><span class="sxs-lookup"><span data-stu-id="d9c72-111">Understanding import from a data feed</span></span>  
 <span data-ttu-id="d9c72-112">可以从以下数据馈送类型中将数据导入“表格模型”：</span><span class="sxs-lookup"><span data-stu-id="d9c72-112">You can import data into a Tabular Model from the following types of data feeds:</span></span>  
  
 <span data-ttu-id="d9c72-113">**Reporting Services 报表**</span><span class="sxs-lookup"><span data-stu-id="d9c72-113">**Reporting Services Report**</span></span>  
 <span data-ttu-id="d9c72-114">可以使用已发布到 Sharepoint 站点或报表服务器的 Reporting Services 报表作为模型中的数据源。</span><span class="sxs-lookup"><span data-stu-id="d9c72-114">You can use a Reporting Services report that has been published to a SharePoint site or a report server as a data source in a model.</span></span> <span data-ttu-id="d9c72-115">从 Reporting Services 报表导入数据时，您必须指定报表定义 (.rdl) 文件作为数据源。</span><span class="sxs-lookup"><span data-stu-id="d9c72-115">When importing data from a Reporting Services Report, you must specify a report definition (.rdl) file as a data source.</span></span>  
  
 <span data-ttu-id="d9c72-116">**Azure DataMarket 数据集**</span><span class="sxs-lookup"><span data-stu-id="d9c72-116">**Azure DataMarket Dataset**</span></span>  
 <span data-ttu-id="d9c72-117">Azure DataMarket 是一种提供单一市场和信息传递通道作为云服务的服务。</span><span class="sxs-lookup"><span data-stu-id="d9c72-117">Azure DataMarket is a service that provides a single marketplace and delivery channel for information as cloud services.</span></span> <span data-ttu-id="d9c72-118">Azure DataMarket 数据集要求一个帐户键，而不是 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d9c72-118">Azure DataMarket datasets require an account key instead of a Windows user account.</span></span>  
  
 <span data-ttu-id="d9c72-119">**Atom 馈送**</span><span class="sxs-lookup"><span data-stu-id="d9c72-119">**Atom feeds**</span></span>  
 <span data-ttu-id="d9c72-120">馈送必须是 Atom 馈送。</span><span class="sxs-lookup"><span data-stu-id="d9c72-120">The feed must be an Atom feed.</span></span> <span data-ttu-id="d9c72-121">不支持 RSS 馈送。</span><span class="sxs-lookup"><span data-stu-id="d9c72-121">RSS feeds are not supported.</span></span> <span data-ttu-id="d9c72-122">该馈送必须可供公开使用，或您必须有权基于您当前登录所用的 Windows 帐户连接到该馈送。</span><span class="sxs-lookup"><span data-stu-id="d9c72-122">The feed must either be publicly available or you must have permission to connect to it under the Windows account with which you are currently logged in.</span></span>  
  
 <span data-ttu-id="d9c72-123">在导入过程中只可一次将数据馈送中的数据添加到模型中。</span><span class="sxs-lookup"><span data-stu-id="d9c72-123">Data from a data feed is added into a model once during import.</span></span> <span data-ttu-id="d9c72-124">若要从馈送获取更新的数据，您可以从模型设计器刷新数据，或在将数据部署到 Analysis Services 生产实例后为模型配置数据刷新计划。</span><span class="sxs-lookup"><span data-stu-id="d9c72-124">To get updated data from the feed, you can either refresh the data from the model designer, or configure a data refresh schedule for the model after it is deployed to a production instance of Analysis Services.</span></span> <span data-ttu-id="d9c72-125">有关详细信息，请参阅 [处理数据（SSAS 表格）](process-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="d9c72-125">For more information, see [Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md).</span></span>  
  
##  <a name="import-data-from-an-azure-datamarket-dataset"></a><a name="azure"></a><span data-ttu-id="d9c72-126">从 Azure DataMarket 数据集导入数据</span><span class="sxs-lookup"><span data-stu-id="d9c72-126">Import data from an Azure DataMarket dataset</span></span>  
 <span data-ttu-id="d9c72-127">在模型中，可以将 Azure DataMarket 中的数据以表的形式导入。</span><span class="sxs-lookup"><span data-stu-id="d9c72-127">You can import data from an Azure DataMarket as a table in your model.</span></span>  
  
#### <a name="to-import-data-from-an-azure-datamarket-dataset"></a><span data-ttu-id="d9c72-128">从 Azure DataMarket 数据集中导入数据</span><span class="sxs-lookup"><span data-stu-id="d9c72-128">To import data from an Azure DataMarket dataset</span></span>  
  
1.  <span data-ttu-id="d9c72-129">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“模型”** 菜单，然后单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span> <span data-ttu-id="d9c72-130">将打开“表导入向导”。</span><span class="sxs-lookup"><span data-stu-id="d9c72-130">The Table Import Wizard opens.</span></span>  
  
2.  <span data-ttu-id="d9c72-131">在 **“连接数据源”** 页的 **“数据馈送”** 下，选择 **“Azure DataMarket 数据集”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-131">On the **Connect to a Data Source** page, under **Data Feeds**, select **Azure DataMarket Dataset**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="d9c72-132">在 **“连接到 DataMarket 数据集”** 页的 **“友好名称”** 中，为您要访问的馈送键入描述性名称。</span><span class="sxs-lookup"><span data-stu-id="d9c72-132">On the **Connect to an Azure DataMarket dataset** page, in **Friendly Name**, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="d9c72-133">如果您正在导入多个馈送或数据源，则将描述性名称用于连接可帮助您记住连接的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d9c72-133">If you are importing multiple feeds or data sources, using descriptive names for the connection can help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="d9c72-134">在 **“数据馈送 URL”** 中，键入数据馈送的地址。</span><span class="sxs-lookup"><span data-stu-id="d9c72-134">In **Data Feed URL**, type the address for the data feed.</span></span>  
  
5.  <span data-ttu-id="d9c72-135">在 **“安全设置”** 的 **“帐户键”** 中，键入帐户键。</span><span class="sxs-lookup"><span data-stu-id="d9c72-135">In **Security Settings**, in **Account Key**, type an account key.</span></span> <span data-ttu-id="d9c72-136">Analysis Services 使用帐户键来访问 DataMarket 订阅。</span><span class="sxs-lookup"><span data-stu-id="d9c72-136">Account keys are used by Analysis Services to access the DataMarket subscriptions.</span></span>  
  
6.  <span data-ttu-id="d9c72-137">单击 **“测试连接”** 确保馈送可用。</span><span class="sxs-lookup"><span data-stu-id="d9c72-137">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="d9c72-138">或者，还可以单击 **“高级”** 以便确认基本 URL 或服务文档 URL 包含提供馈送的查询或服务文档。</span><span class="sxs-lookup"><span data-stu-id="d9c72-138">Alternatively, you can also click **Advanced** to confirm that the Base URL or Service Document URL contains the query or service document that provides the feed.</span></span>  
  
7.  <span data-ttu-id="d9c72-139">单击 **“下一步”** 继续导入。</span><span class="sxs-lookup"><span data-stu-id="d9c72-139">Click **Next** to continue with the import.</span></span>  
  
8.  <span data-ttu-id="d9c72-140">在 **“模拟信息”** 页中，指定刷新数据时 Analysis Services 将用于连接到数据源的凭据，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-140">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span> <span data-ttu-id="d9c72-141">这些凭据不同于帐户键。</span><span class="sxs-lookup"><span data-stu-id="d9c72-141">These credentials are different from the Account Key.</span></span>  
  
9. <span data-ttu-id="d9c72-142">在向导的 **“选择表和视图”** 页的 **“友好名称”** 字段中，键入标识在导入数据后将包含这些数据的表的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="d9c72-142">In the **Select Tables and Views** page of the wizard, in the **Friendly Name** field, type a descriptive name that identifies the table that will contain this data after it is imported</span></span>  
  
10. <span data-ttu-id="d9c72-143">单击 **“预览并筛选”** 检查数据并更改列选择。</span><span class="sxs-lookup"><span data-stu-id="d9c72-143">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="d9c72-144">您不能限制在报表数据馈送中导入的行，但可以通过清除相应的复选框来删除列。</span><span class="sxs-lookup"><span data-stu-id="d9c72-144">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="d9c72-145">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="d9c72-145">Click **OK**.</span></span>  
  
11. <span data-ttu-id="d9c72-146">在 **“选择表和视图”** 页上，单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-146">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-public-or-corporate-data-sources"></a><a name="importdata"></a><span data-ttu-id="d9c72-147">从公共数据源或公司数据源导入数据馈送</span><span class="sxs-lookup"><span data-stu-id="d9c72-147">Import data feeds from public or corporate data sources</span></span>  
 <span data-ttu-id="d9c72-148">您可以访问公共馈送，也可以生成自定义数据服务，这些服务从专有或早期数据库系统生成 Atom 馈送。</span><span class="sxs-lookup"><span data-stu-id="d9c72-148">You can access public feeds or build custom data services that generate Atom feeds from proprietary or legacy database systems.</span></span>  
  
#### <a name="to-import-data-from-public-or-corporate-data-feeds"></a><span data-ttu-id="d9c72-149">从公共数据馈送或公司数据馈送导入数据</span><span class="sxs-lookup"><span data-stu-id="d9c72-149">To import data from public or corporate data feeds</span></span>  
  
1.  <span data-ttu-id="d9c72-150">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“模型”** 菜单，然后单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-150">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span> <span data-ttu-id="d9c72-151">将打开“表导入向导”。</span><span class="sxs-lookup"><span data-stu-id="d9c72-151">The Table Import Wizard opens.</span></span>  
  
2.  <span data-ttu-id="d9c72-152">在 **“连接数据源”** 页的 **“数据馈送”** 下，选择 **“其他馈送”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-152">On the **Connect to a Data Source** page, under **Data Feeds**, select **Other Feeds**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="d9c72-153">在 **“连接到数据馈送”** 页中，为您要访问的馈送键入描述性名称。</span><span class="sxs-lookup"><span data-stu-id="d9c72-153">On the **Connect to a Data Feed** page, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="d9c72-154">如果您正在导入多个馈送或数据源，则将描述性名称用于连接可帮助您记住连接的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d9c72-154">If you are importing multiple feeds or data sources, using descriptive names for the connection can help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="d9c72-155">在 **“数据馈送 URL”** 中，键入数据馈送的地址。</span><span class="sxs-lookup"><span data-stu-id="d9c72-155">In **Data Feed URL**, type the address for the data feed.</span></span> <span data-ttu-id="d9c72-156">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="d9c72-156">Valid values include the following:</span></span>  
  
    1.  <span data-ttu-id="d9c72-157">包含 Atom 数据的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d9c72-157">An XML document that contains the Atom data.</span></span> <span data-ttu-id="d9c72-158">例如，下面的 URL 指向 Open Government Data Initiative 网站上的公共馈送：</span><span class="sxs-lookup"><span data-stu-id="d9c72-158">For example, the following URL points to a public feed on the Open Government Data Initiative web site:</span></span>  
  
        ```  
        http://ogdi.cloudapp.net/v1/dc/banklocations/  
        ```  
  
    2.  <span data-ttu-id="d9c72-159">指定一个或多个馈送的 .atomsvc 文档。</span><span class="sxs-lookup"><span data-stu-id="d9c72-159">An .atomsvc document that specifies one or more feeds.</span></span> <span data-ttu-id="d9c72-160">.atomsvc 文档指向提供一个或多个馈送的服务或应用程序。</span><span class="sxs-lookup"><span data-stu-id="d9c72-160">An .atomsvc document points to a service or application that provides one or more feeds.</span></span> <span data-ttu-id="d9c72-161">每个馈送都指定为返回结果集的基础查询。</span><span class="sxs-lookup"><span data-stu-id="d9c72-161">Each feed is specified as a base query that returns the result set.</span></span>  
  
         <span data-ttu-id="d9c72-162">您可以指定一个 URL 地址，该地址指向 Web 服务器上的 .atomsvc 文档；也可以从您的计算机上的共享文件夹或本地文件夹打开文件。</span><span class="sxs-lookup"><span data-stu-id="d9c72-162">You can specify a URL address to an .atomsvc document that is on a web server or you can open the file from a shared or local folder on your computer.</span></span> <span data-ttu-id="d9c72-163">如果您在导出 Reporting Services 报表时将某一 .atomsvc 文档保存到您的计算机，则可能具有 .atomsvc 文档；或者，您可能在某人为您的 SharePoint 站点创建的数据馈送库中具有 .atomsvc 文档。</span><span class="sxs-lookup"><span data-stu-id="d9c72-163">You might have an .atomsvc document if you saved one to your computer while exporting a Reporting Services report, or you might have .atomsvc documents in a data feed library that someone created for your SharePoint site.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d9c72-164">建议您指定可通过某一 URL 地址或共享文件夹访问的 .atomsvc 文档，因为这样做以后，您可以在工作簿发布到 SharePoint 后在以后为该工作簿配置自动数据刷新。</span><span class="sxs-lookup"><span data-stu-id="d9c72-164">Specifying an .atomsvc document that can be accessed through a URL address or shared folder is recommended because it gives you the option of configuring automatic data refresh for the workbook later, after the workbook is published to SharePoint.</span></span> <span data-ttu-id="d9c72-165">如果您指定不位于您的本地计算机上的位置，则服务器可以重复使用相同的 URL 地址或网络文件夹来刷新数据。</span><span class="sxs-lookup"><span data-stu-id="d9c72-165">The server can re-use the same URL address or network folder to refresh data if you specify a location that is not local to your computer.</span></span>  
  
5.  <span data-ttu-id="d9c72-166">单击 **“测试连接”** 确保馈送可用。</span><span class="sxs-lookup"><span data-stu-id="d9c72-166">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="d9c72-167">或者，还可以单击 **“高级”** 以便确认基本 URL 或服务文档 URL 包含提供馈送的查询或服务文档。</span><span class="sxs-lookup"><span data-stu-id="d9c72-167">Alternatively, you can also click **Advanced** to confirm that the Base URL or Service Document URL contains the query or service document that provides the feed.</span></span>  
  
6.  <span data-ttu-id="d9c72-168">单击 **“下一步”** 继续导入。</span><span class="sxs-lookup"><span data-stu-id="d9c72-168">Click **Next** to continue with the import.</span></span>  
  
7.  <span data-ttu-id="d9c72-169">在 **“模拟信息”** 页中，指定刷新数据时 Analysis Services 将用于连接到数据源的凭据，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-169">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="d9c72-170">在向导的 **“选择表和视图”** 页的 **“友好名称”** 字段中，使用标识在导入数据后将包含这些数据的表的描述性名称替换“数据馈送内容”。</span><span class="sxs-lookup"><span data-stu-id="d9c72-170">In the **Select Tables and Views** page of the wizard, in the **Friendly Name** field, replace Data Feed Content with a descriptive name that identifies the table that will contain this data after it is imported</span></span>  
  
9. <span data-ttu-id="d9c72-171">单击 **“预览并筛选”** 检查数据并更改列选择。</span><span class="sxs-lookup"><span data-stu-id="d9c72-171">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="d9c72-172">您不能限制在报表数据馈送中导入的行，但可以通过清除相应的复选框来删除列。</span><span class="sxs-lookup"><span data-stu-id="d9c72-172">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="d9c72-173">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="d9c72-173">Click **OK**.</span></span>  
  
10. <span data-ttu-id="d9c72-174">在 **“选择表和视图”** 页上，单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-174">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-sharepoint-lists"></a><a name="importlist"></a><span data-ttu-id="d9c72-175">从 SharePoint 列表导入数据馈送</span><span class="sxs-lookup"><span data-stu-id="d9c72-175">Import data feeds from SharePoint lists</span></span>  
 <span data-ttu-id="d9c72-176">可以导入在 (SharePoint) 功能区上具有“作为数据馈送导出”\*\*\*\* 按钮的任何 SharePoint 列表。</span><span class="sxs-lookup"><span data-stu-id="d9c72-176">You can import any SharePoint list that has an **Export as Data Feed** button on the (SharePoint) ribbon.</span></span> <span data-ttu-id="d9c72-177">可以单击此按钮将列表作为馈送导出。</span><span class="sxs-lookup"><span data-stu-id="d9c72-177">You can click this button to export the list as a feed.</span></span>  
  
#### <a name="to-import-data-feeds-from-a-sharepoint-list"></a><span data-ttu-id="d9c72-178">从 SharePoint 列表导入数据馈送</span><span class="sxs-lookup"><span data-stu-id="d9c72-178">To import data feeds from a SharePoint list</span></span>  
  
1.  <span data-ttu-id="d9c72-179">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“模型”** 菜单，然后单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-179">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="d9c72-180">在 **“连接数据源”** 页的 **“数据馈送”** 下，选择 **“其他数据馈送”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-180">On the **Connect to a Data Source** page, under **Data Feeds**, select **Other Data Feeds**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="d9c72-181">在 **“连接到数据馈送”** 页中，为您要访问的馈送键入描述性名称。</span><span class="sxs-lookup"><span data-stu-id="d9c72-181">On the **Connect to a Data Feed** page, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="d9c72-182">如果您正在导入多个馈送或数据源，则将描述性名称用于连接可帮助您记住连接的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d9c72-182">If you are importing multiple feeds or data sources, using descriptive names for the connection might help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="d9c72-183">在 "数据馈送 URL" 中，键入列表数据服务的地址， \<server-name> 并将替换为您的 SharePoint 服务器的实际名称：</span><span class="sxs-lookup"><span data-stu-id="d9c72-183">In Data Feed URL, type an address to the list data service, replacing \<server-name> with the actual name of your SharePoint server:</span></span>  
  
    ```  
    http://<server-name>/_vti_bin/listdata.svc  
    ```  
  
5.  <span data-ttu-id="d9c72-184">单击 **“测试连接”** 确保馈送可用。</span><span class="sxs-lookup"><span data-stu-id="d9c72-184">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="d9c72-185">或者，还可以单击 **“高级”** 以便确认服务文档 URL 包含列表数据服务的地址。</span><span class="sxs-lookup"><span data-stu-id="d9c72-185">Alternatively, you can also click **Advanced** to confirm that the Service Document URL contains an address to the list data service.</span></span>  
  
6.  <span data-ttu-id="d9c72-186">单击 **“下一步”** 继续导入。</span><span class="sxs-lookup"><span data-stu-id="d9c72-186">Click **Next** to continue with the import.</span></span>  
  
7.  <span data-ttu-id="d9c72-187">在 **“模拟信息”** 页中，指定刷新数据时 Analysis Services 将用于连接到数据源的凭据，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-187">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="d9c72-188">在向导的 **“选择表和视图”** 页中，选择要导入的列表。</span><span class="sxs-lookup"><span data-stu-id="d9c72-188">In the **Select Tables and Views** page of the wizard, select the lists you want to import.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d9c72-189">只能导入包含列的列表。</span><span class="sxs-lookup"><span data-stu-id="d9c72-189">You can only import lists that contain columns.</span></span>  
  
9. <span data-ttu-id="d9c72-190">单击 **“预览并筛选”** 检查数据并更改列选择。</span><span class="sxs-lookup"><span data-stu-id="d9c72-190">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="d9c72-191">您不能限制在报表数据馈送中导入的行，但可以通过清除相应的复选框来删除列。</span><span class="sxs-lookup"><span data-stu-id="d9c72-191">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="d9c72-192">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="d9c72-192">Click **OK**.</span></span>  
  
10. <span data-ttu-id="d9c72-193">在 **“选择表和视图”** 页上，单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-193">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-reporting-services-reports"></a><a name="importreport"></a><span data-ttu-id="d9c72-194">从 Reporting Services 报表导入数据馈送</span><span class="sxs-lookup"><span data-stu-id="d9c72-194">Import data feeds from Reporting Services Reports</span></span>  
 <span data-ttu-id="d9c72-195">如果已部署 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Reporting Services，则可以使用 Atom 呈现扩展插件从现有报表生成数据馈送。</span><span class="sxs-lookup"><span data-stu-id="d9c72-195">If you have a deployment of [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Reporting Services, you can use the Atom rendering extension to generate a data feed from an existing report.</span></span>  
  
#### <a name="to-import-report-data-from-a-published-reporting-services-report"></a><span data-ttu-id="d9c72-196">从已发布的 Reporting Services 报表导入报表数据</span><span class="sxs-lookup"><span data-stu-id="d9c72-196">To import report data from a published Reporting Services report</span></span>  
  
1.  <span data-ttu-id="d9c72-197">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“模型”** 菜单，然后单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-197">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="d9c72-198">在 **“连接数据源”** 页的 **“数据馈送”** 下，选择 **“报表”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-198">On the **Connect to a Data Source** page, under **Data Feeds**, select **Report**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="d9c72-199">在“连接到 Microsoft SQL Server Reporting Services 报表”页的“友好的连接名称”中，键入您要访问的馈送的说明性名称。</span><span class="sxs-lookup"><span data-stu-id="d9c72-199">On the Connect to a Microsoft SQL Server Reporting Services Report page, in Friendly Connection Name, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="d9c72-200">如果您正在导入多个数据源，则为连接使用描述性名称可帮助您记住连接的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d9c72-200">If you are importing multiple data sources, using descriptive names for the connection might help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="d9c72-201">单击 **“浏览”** 并选择一个报表服务器。</span><span class="sxs-lookup"><span data-stu-id="d9c72-201">Click **Browse** and select a report server.</span></span>  
  
     <span data-ttu-id="d9c72-202">如果定期使用报表服务器上的报表，该服务器可能在 **“最近使用的站点和服务器”** 中列出。</span><span class="sxs-lookup"><span data-stu-id="d9c72-202">If you regularly use reports on a report server, the server might be listed in **Recent Sites and Servers**.</span></span> <span data-ttu-id="d9c72-203">否则，在“名称”中键入报表服务器的地址，然后单击 **“打开”** 以浏览报表服务器站点上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d9c72-203">Otherwise, in Name, type an address to a report server and click **Open** to browse the folders on the report server site.</span></span> <span data-ttu-id="d9c72-204">Report Server 的示例地址可能是 http:// \<computername> /reportserver。</span><span class="sxs-lookup"><span data-stu-id="d9c72-204">An example address for a report server might be http://\<computername>/reportserver.</span></span>  
  
5.  <span data-ttu-id="d9c72-205">选择报表，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-205">Select the report and click **Open**.</span></span> <span data-ttu-id="d9c72-206">或者，可以在 **“名称”** 文本框中粘贴指向报表的链接，包括完整路径和报表名称。</span><span class="sxs-lookup"><span data-stu-id="d9c72-206">Alternatively, you can paste a link to the report, including the full path and report name, in the **Name** text box.</span></span> <span data-ttu-id="d9c72-207">“表导入向导”将连接到该报表，然后在预览区域中呈现它。</span><span class="sxs-lookup"><span data-stu-id="d9c72-207">The Table Import wizard connects to the report and renders it in the preview area.</span></span>  
  
     <span data-ttu-id="d9c72-208">如果报表使用参数，则必须指定参数，否则无法创建报表连接。</span><span class="sxs-lookup"><span data-stu-id="d9c72-208">If the report uses parameters, you must specify a parameter or you cannot create the report connection.</span></span> <span data-ttu-id="d9c72-209">执行此操作时，只有与该参数值相关的行才会导入数据馈送。</span><span class="sxs-lookup"><span data-stu-id="d9c72-209">When you do so, only the rows related to the parameter value are imported in the data feed.</span></span>  
  
    1.  <span data-ttu-id="d9c72-210">使用报表中提供的列表框或组合框选择一个参数。</span><span class="sxs-lookup"><span data-stu-id="d9c72-210">Choose a parameter using the list box or combo box provided in the report.</span></span>  
  
    2.  <span data-ttu-id="d9c72-211">单击 **“查看报表”** 更新数据。</span><span class="sxs-lookup"><span data-stu-id="d9c72-211">Click **View Report** to update the data.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d9c72-212">查看报表会将所选参数与数据馈送定义一起保存。</span><span class="sxs-lookup"><span data-stu-id="d9c72-212">Viewing the report saves the parameters that you selected together with the data feed definition.</span></span>  
  
     <span data-ttu-id="d9c72-213">可以选择单击“高级”\*\*\*\* 为报表设置特定于提供程序的属性。</span><span class="sxs-lookup"><span data-stu-id="d9c72-213">Optionally, click **Advanced** to set provider-specific properties for the report.</span></span>  
  
6.  <span data-ttu-id="d9c72-214">单击 **“测试连接”** 确保报表可以作为数据馈送。</span><span class="sxs-lookup"><span data-stu-id="d9c72-214">Click **Test Connection** to make sure the report is available as a data feed.</span></span> <span data-ttu-id="d9c72-215">或者，还可以单击 **“高级”** 以确认 **“嵌入式服务文档”** 属性包含指定数据馈送连接的嵌入的 XML。</span><span class="sxs-lookup"><span data-stu-id="d9c72-215">Alternatively, you can also click **Advanced** to confirm that the **Inline Service Document** property contains embedded XML that specifies the data feed connection.</span></span>  
  
7.  <span data-ttu-id="d9c72-216">单击 **“下一步”** 继续导入。</span><span class="sxs-lookup"><span data-stu-id="d9c72-216">Click **Next** to continue with the import.</span></span>  
  
8.  <span data-ttu-id="d9c72-217">在 **“模拟信息”** 页中，指定刷新数据时 Analysis Services 将用于连接到数据源的凭据，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-217">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="d9c72-218">在向导的 **“选择表和视图”** 页中，选中要作为数据导入的报表部件旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="d9c72-218">In the **Select Tables and Views** page of the wizard, select the check box next to the report parts that you want to import as data.</span></span>  
  
     <span data-ttu-id="d9c72-219">有些报表可以包含多种部件，包括表、列表或图形。</span><span class="sxs-lookup"><span data-stu-id="d9c72-219">Some reports can contain multiple parts, including tables, lists, or graphs.</span></span>  
  
10. <span data-ttu-id="d9c72-220">在 **“友好名称”** 框中，键入模型中要用于保存数据馈送的表的名称。</span><span class="sxs-lookup"><span data-stu-id="d9c72-220">In the **Friendly name** box, type the name of the table where you want the data feed to be saved in your model.</span></span>  
  
     <span data-ttu-id="d9c72-221">如果未指定名称，默认情况下，将使用 Reporting Services 控件的名称：例如，Tablix1、Tablix2。</span><span class="sxs-lookup"><span data-stu-id="d9c72-221">The name of the Reporting Service control is used by default if no name has been assigned: for example, Tablix1, Tablix2.</span></span> <span data-ttu-id="d9c72-222">建议您在导入过程中更改此名称，以便可以更容易地识别导入数据馈送的源。</span><span class="sxs-lookup"><span data-stu-id="d9c72-222">We recommend that you change this name during import so that you can more easily identify the origin of the imported data feed.</span></span>  
  
11. <span data-ttu-id="d9c72-223">单击 **“预览并筛选”** 检查数据并更改列选择。</span><span class="sxs-lookup"><span data-stu-id="d9c72-223">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="d9c72-224">您不能限制在报表数据馈送中导入的行，但可以通过清除相应的复选框来删除列。</span><span class="sxs-lookup"><span data-stu-id="d9c72-224">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="d9c72-225">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="d9c72-225">Click **OK**.</span></span>  
  
12. <span data-ttu-id="d9c72-226">在 **“选择表和视图”** 页上，单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="d9c72-226">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c72-227">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9c72-227">See Also</span></span>  
 <span data-ttu-id="d9c72-228">[&#40;SSAS 表格&#41;支持的数据源](tabular-models/data-sources-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d9c72-228">[Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md) </span></span>  
 <span data-ttu-id="d9c72-229">[&#40;SSAS 表格&#41;支持的数据类型](tabular-models/data-types-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d9c72-229">[Data Types Supported &#40;SSAS Tabular&#41;](tabular-models/data-types-supported-ssas-tabular.md) </span></span>  
 <span data-ttu-id="d9c72-230">[模拟 &#40;SSAS 表格&#41;](tabular-models/impersonation-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d9c72-230">[Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md) </span></span>  
 <span data-ttu-id="d9c72-231">[&#40;SSAS 表格&#41;处理数据](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d9c72-231">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="d9c72-232">导入数据（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="d9c72-232">Import Data &#40;SSAS Tabular&#41;</span></span>](import-data-ssas-tabular.md)  
  
  
