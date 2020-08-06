---
title: Reporting Services 中的 SharePoint 库传递 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], report delivery
- delivering reports [Reporting Services]
- subscriptions [Reporting Services], SharePoint library delivery
ms.assetid: cb4e4f71-f2d5-475a-9284-ea324c93c7de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5ff109781233ca0c56db0c03ed37bdd13e6e75d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692646"
---
# <a name="sharepoint-library-delivery-in-reporting-services"></a><span data-ttu-id="d5d2b-102">Reporting Services 中的 SharePoint 库传递</span><span class="sxs-lookup"><span data-stu-id="d5d2b-102">SharePoint Library Delivery in Reporting Services</span></span>
  <span data-ttu-id="d5d2b-103">配置为 SharePoint 集成模式的报表服务器包含可用于向 SharePoint 库中发送报表的传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-103">A report server that is configured for SharePoint integration includes a delivery extension that you can use to send a report to a SharePoint library.</span></span>  
  
 <span data-ttu-id="d5d2b-104">若要使用 SharePoint 传递扩展插件，必须在 SharePoint 站点上的应用程序页中创建一个订阅，然后选择 **“SharePoint 文档库”** 作为传递类型。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-104">To use the SharePoint delivery extension, you must create a subscription from an application page on a SharePoint site, and then select **SharePoint document library** as the delivery type.</span></span> <span data-ttu-id="d5d2b-105">不能为在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 或报表管理器中创建的订阅使用 SharePoint 传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-105">You cannot use the SharePoint delivery extension for subscriptions that you create in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or Report Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5d2b-106">如果报表服务器在本机模式下运行，则传递扩展插件不支持将报表传递到 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-106">The delivery extension does not support the delivery of reports to a SharePoint site if the report server is running in native mode.</span></span> <span data-ttu-id="d5d2b-107">如果尝试通过编程方式为本机模式报表服务器调用传递扩展插件，则服务器将返回 `rsDeliveryExtensionNotFound` 错误，并在报表服务器日志文件中记录 `rsOperationNotSupportedSharePointMode` 错误。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-107">If you attempt to call the delivery extension programmatically for a native mode report server, the server will return the `rsDeliveryExtensionNotFound` error and log the `rsOperationNotSupportedSharePointMode` error in the report server log files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5d2b-108">要求</span><span class="sxs-lookup"><span data-stu-id="d5d2b-108">Requirements</span></span>  
 <span data-ttu-id="d5d2b-109">关于将呈现的报表传递到库的要求包括以下几点：</span><span class="sxs-lookup"><span data-stu-id="d5d2b-109">Requirements for delivering rendered reports to a library include the following:</span></span>  
  
-   <span data-ttu-id="d5d2b-110">必须将报表服务器配置为 SharePoint 集成模式。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-110">The report server must be configured for SharePoint integration mode.</span></span>  
  
-   <span data-ttu-id="d5d2b-111">必须在报表服务器上安装和配置 SharePoint 传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-111">The report server must have the SharePoint delivery extension installed and configured.</span></span>  
  
-   <span data-ttu-id="d5d2b-112">报表必须是报表定义 (.rdl) 文件。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-112">The report must be a report definition (.rdl) file.</span></span> <span data-ttu-id="d5d2b-113">不能通过订阅传递其他报表服务器内容类型，如模型或资源。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-113">You cannot deliver other report server content types, such as models or resources, through a subscription.</span></span> <span data-ttu-id="d5d2b-114">不能订阅使用模型作为数据源的特别报告。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-114">You cannot subscribe to ad hoc reports that use models as a data source.</span></span>  
  
-   <span data-ttu-id="d5d2b-115">报表必须使用已存储凭据。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-115">The report must use stored credentials.</span></span> <span data-ttu-id="d5d2b-116">无论对于何种传递类型，这都是对报表创建订阅的必备条件。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-116">This is a prerequisite for creating any subscription on a report, regardless of the delivery type.</span></span>  
  
-   <span data-ttu-id="d5d2b-117">目标必须是 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-117">The destination must be a SharePoint library.</span></span> <span data-ttu-id="d5d2b-118">选择目标库时，必须选择位于同一 SharePoint 站点上的库。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-118">When choosing a target library, you must choose one that is on the same SharePoint site.</span></span> <span data-ttu-id="d5d2b-119">不能将报表传递到位于相同网站集内的其他服务器或其他站点。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-119">You cannot deliver a report to a library on another server or another site within the same site collection.</span></span>  
  
 <span data-ttu-id="d5d2b-120">传递报表的过程中不传递属性和元数据。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-120">Properties and metadata are not part of report delivery.</span></span> <span data-ttu-id="d5d2b-121">首次传递报表时，报表会继承包含该报表的文件夹或列表的安全设置。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-121">When the report is delivered for the first time, it inherits the security settings of the folder or list that contains it.</span></span> <span data-ttu-id="d5d2b-122">如果您随后修改安全设置或设置报表属性，这些设置会保留不变。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-122">If you subsequently modify security settings or set report properties, those settings are retained.</span></span> <span data-ttu-id="d5d2b-123">订阅仅刷新存储在指定位置的报表。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-123">The subscription just refreshes the report that is stored at the specified location.</span></span>  
  
## <a name="sharepoint-permissions"></a><span data-ttu-id="d5d2b-124">SharePoint 权限</span><span class="sxs-lookup"><span data-stu-id="d5d2b-124">SharePoint Permissions</span></span>  
 <span data-ttu-id="d5d2b-125">若要创建订阅，必须对报表拥有“查看项”权限。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-125">To create the subscription, you must have View Items permission on the report.</span></span> <span data-ttu-id="d5d2b-126">若要传递报表，必须对要传入报表的库拥有“添加项”权限。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-126">To deliver the report, you must have Add Items permission on the library to which the report is delivered.</span></span>  
  
## <a name="how-to-create-modify-and-delete-subscriptions"></a><span data-ttu-id="d5d2b-127">如何创建、修改和删除订阅</span><span class="sxs-lookup"><span data-stu-id="d5d2b-127">How to Create, Modify and Delete Subscriptions</span></span>  
  
1.  <span data-ttu-id="d5d2b-128">转到从中访问报表的 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-128">Go to the SharePoint site from which you access the report.</span></span>  
  
2.  <span data-ttu-id="d5d2b-129">选择报表，单击它旁边的向下箭头，然后选择 **“管理订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-129">Select the report, click the down arrow next to the report, and select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="d5d2b-130">单击 **“创建”** 、 **“编辑”** 或 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-130">Click **Create**, **Edit**, or **Delete**.</span></span>  
  
 <span data-ttu-id="d5d2b-131">有关“管理订阅”列表的状态消息中显示有关订阅的当前信息，包括订阅是否成功以及上次运行订阅的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-131">A Status message on the Manage Subscriptions list displays current information about the subscription, including whether it succeeded and the date and time the subscription last ran.</span></span>  
  
## <a name="setting-delivery-options"></a><span data-ttu-id="d5d2b-132">设置传递选项</span><span class="sxs-lookup"><span data-stu-id="d5d2b-132">Setting Delivery Options</span></span>  
 <span data-ttu-id="d5d2b-133">可以为将报表传递到 SharePoint 库的订阅设置下列传递选项。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-133">You can set the following delivery options on a subscription that delivers a report to a SharePoint library.</span></span>  
  
 <span data-ttu-id="d5d2b-134">呈现输出格式</span><span class="sxs-lookup"><span data-stu-id="d5d2b-134">Render output format</span></span>  
 <span data-ttu-id="d5d2b-135">指定用以传递报表的应用程序格式。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-135">Specify the application format in which you want the report delivered.</span></span> <span data-ttu-id="d5d2b-136">在传递报表前使用该格式呈现报表。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-136">The report is rendered in this format before delivery.</span></span> <span data-ttu-id="d5d2b-137">您选择的输出格式将确定默认文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-137">The output format you select will determine the default file extension.</span></span>  
  
 <span data-ttu-id="d5d2b-138">可从中进行选择的输出格式列表包含报表服务器上安装的一组呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-138">The list of output formats you can select from is the set of rendering extensions that are installed on the report server.</span></span>  
  
 <span data-ttu-id="d5d2b-139">请注意，不能指定仅供内部使用的输出格式，也不能指定在 SharePoint 集成模式下运行的报表服务器不支持的输出格式。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-139">Note that you cannot specify output formats that are for internal use only, or that are not supported for report servers that run in SharePoint integrated mode.</span></span> <span data-ttu-id="d5d2b-140">这些格式包括 Null、RGDI 和 HTMLOWC。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-140">These formats include Null, RGDI and HTMLOWC.</span></span>  
  
 <span data-ttu-id="d5d2b-141">文件名和扩展名</span><span class="sxs-lookup"><span data-stu-id="d5d2b-141">File name and extension</span></span>  
 <span data-ttu-id="d5d2b-142">指定要在目标库中为报表显示的文件名和扩展名。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-142">Specify the file name and extension of the report as you want it to appear in the target library.</span></span> <span data-ttu-id="d5d2b-143">如果不指定文件扩展名，则报表服务器会根据报表输出格式创建一个扩展名。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-143">If you do not specify a file extension, the report server will create one based on the report output format.</span></span> <span data-ttu-id="d5d2b-144">此值是必需的。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-144">This value is required.</span></span> <span data-ttu-id="d5d2b-145">文件名中不得包含下列字符：: \ / \* ?</span><span class="sxs-lookup"><span data-stu-id="d5d2b-145">The file name must not include the following characters: : \ / \* ?</span></span> <span data-ttu-id="d5d2b-146">" \< > | # { } %</span><span class="sxs-lookup"><span data-stu-id="d5d2b-146">" \< > | # { } %</span></span>  
  
 <span data-ttu-id="d5d2b-147">标题</span><span class="sxs-lookup"><span data-stu-id="d5d2b-147">Title</span></span>  
 <span data-ttu-id="d5d2b-148">为目标库中的报表指定可选的 `Title` 属性。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-148">Specifies an optional `Title` property for the report in the target library.</span></span> <span data-ttu-id="d5d2b-149">该属性是库中存储的所有项的标准属性。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-149">This is a standard property for all items stored in a library.</span></span> <span data-ttu-id="d5d2b-150">用户可以指定在 SharePoint 站点上查看库内容时是显示还是隐藏该属性。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-150">Users can specify whether to show or hide this property when viewing library contents on a SharePoint site.</span></span>  
  
 <span data-ttu-id="d5d2b-151">路径</span><span class="sxs-lookup"><span data-stu-id="d5d2b-151">Path</span></span>  
 <span data-ttu-id="d5d2b-152">指定一个指向 SharePoint 库的完全限定 URL，包括 SharePoint Web 应用程序和站点。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-152">Specifies a fully qualified URL to the SharePoint library, including the SharePoint Web application and site.</span></span> <span data-ttu-id="d5d2b-153">例如： <http://mySharePointWeb/MySite/MyDocLib> ; 其中 " <http://mySharePointWeb> " 指示 Web 应用程序，"我的网站" 是 sharepoint 站点，而 "MyDocLib" 是要在其中传递报表的 sharepoint 库。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-153">For example: <http://mySharePointWeb/MySite/MyDocLib>; where "<http://mySharePointWeb>" indicates the Web application, "MySite" is the SharePoint site, and "MyDocLib" is the SharePoint library where the report will be delivered.</span></span>  
  
 <span data-ttu-id="d5d2b-154">不能指定页、站点或列表。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-154">You cannot specify a page, site, or list.</span></span> <span data-ttu-id="d5d2b-155">目标容器必须是同一站点上或同一场中的库。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-155">The target container must be a library in the same site or farm.</span></span>  
  
 <span data-ttu-id="d5d2b-156">覆盖选项</span><span class="sxs-lookup"><span data-stu-id="d5d2b-156">Overwrite options</span></span>  
 <span data-ttu-id="d5d2b-157">指定处理订阅时是否使用更新的版本替换具有相同名称和扩展名的文件。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-157">Specifies whether a file with the same name and extension is replaced by a newer version when the subscription is processed.</span></span> <span data-ttu-id="d5d2b-158">如果希望使用更新的版本替换现有文件，请选择 **“覆盖”** 。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-158">Choose **Overwrite** if you want to replace an existing file with a newer version.</span></span> <span data-ttu-id="d5d2b-159">如果不希望订阅替换文件，请选择 **“无”** 。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-159">Choose **None** if you do not want the subscription to replace a file.</span></span> <span data-ttu-id="d5d2b-160">在这种情况下，如果存在具有目标名称和扩展名的文件，则不进行传递。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-160">In this case, no delivery will occur if a file exists with the target name and extension.</span></span> <span data-ttu-id="d5d2b-161">如果希望通过在文件名末尾追加数字来添加同一文件的连续版本，请选择 **“Autoincrement”** 。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-161">Choose **Autoincrement** if you want to add successive versions of the same file by appending a number at the end of the file name.</span></span>  
  
 <span data-ttu-id="d5d2b-162">自动复制</span><span class="sxs-lookup"><span data-stu-id="d5d2b-162">Autocopy</span></span>  
 <span data-ttu-id="d5d2b-163">如果使用自动复制功能将一个文件的最新版本自动复制到多个位置，在启用“覆盖”的情况下则会复制此文件  。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-163">If you are using the Autocopy feature to automatically copy the latest version of a file to multiple locations, the file will be copied if **Overwrite** is enabled.</span></span> <span data-ttu-id="d5d2b-164">如果使用了**自动增量**或**None**，则传递将失败，并且会 `rsDeliveryError` 发生错误。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-164">If you used **Autoincrement** or **None**, the delivery will fail and the `rsDeliveryError` error will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d2b-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5d2b-165">See Also</span></span>  
 <span data-ttu-id="d5d2b-166">[创建和管理 SharePoint 模式报表服务器的订阅](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="d5d2b-166">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span></span>  
 <span data-ttu-id="d5d2b-167">[订阅和传递 (Reporting Services)](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="d5d2b-167">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="d5d2b-168">为报表数据源指定凭据和连接信息</span><span class="sxs-lookup"><span data-stu-id="d5d2b-168">Specify Credential and Connection Information for Report Data Sources</span></span>](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
