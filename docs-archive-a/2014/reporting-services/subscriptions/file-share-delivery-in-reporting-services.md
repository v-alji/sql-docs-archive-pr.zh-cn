---
title: Reporting Services 中的文件共享传递 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
ms.assetid: 9f338dd3-f68a-4355-b9d7-9b25dacf3b5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bba83a89612f8601adedd827edad0e587d096d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590558"
---
# <a name="file-share-delivery-in-reporting-services"></a><span data-ttu-id="8fa4c-102">Reporting Services 中的文件共享传递</span><span class="sxs-lookup"><span data-stu-id="8fa4c-102">File Share Delivery in Reporting Services</span></span>
  <span data-ttu-id="8fa4c-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 包含文件共享传递扩展插件，以便你可以将报表传递到文件夹。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] includes a file share delivery extension so that you can deliver a report to a folder.</span></span> <span data-ttu-id="8fa4c-104">默认情况下会提供文件共享传递扩展插件，并且不需要进行其他配置。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-104">The file share delivery extension is available by default and requires no additional configuration.</span></span> <span data-ttu-id="8fa4c-105">为了成功传递文件，必须设置对共享文件夹的写访问权限。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-105">In order for file delivery to succeed, you must set write access permissions on the shared folder.</span></span> <span data-ttu-id="8fa4c-106">此外，需要访问报表的用户还必须对共享文件夹具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-106">In addition, users who require access to the reports must have read permissions on the shared folder.</span></span>  
  
 <span data-ttu-id="8fa4c-107">若要将报表分发到文件共享位置，需要定义标准订阅或数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-107">To distribute a report to a file share, you define either a standard subscription or a data-driven subscription.</span></span> <span data-ttu-id="8fa4c-108">一次只能订阅并请求传递一个报表。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-108">You can subscribe to and request delivery for only one report at a time.</span></span> <span data-ttu-id="8fa4c-109">若要了解如何在数据驱动订阅中使用文件共享传递，请参阅[创建数据驱动订阅（SSRS 教程）](../create-a-data-driven-subscription-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-109">To learn how to use file share delivery in a data-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span> <span data-ttu-id="8fa4c-110">此外，运行远程文件共享订阅的帐户需要本地登录 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 计算机的权限。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-110">Additionally, the account that runs remote file share subscriptions requires rights to log on locally on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] computer.</span></span>  
  
||  
|-|  
|<span data-ttu-id="8fa4c-111">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="8fa4c-111">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="8fa4c-112">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="8fa4c-112">In this topic:</span></span>  
  
-   [<span data-ttu-id="8fa4c-113">传递到共享文件夹的报表的特征</span><span class="sxs-lookup"><span data-stu-id="8fa4c-113">Characteristics of a Report That is Delivered to a Shared Folder</span></span>](#bkmk_Characteristics)  
  
-   [<span data-ttu-id="8fa4c-114">目标文件夹</span><span class="sxs-lookup"><span data-stu-id="8fa4c-114">Target Folders</span></span>](#bkmk_target_folders)  
  
-   [<span data-ttu-id="8fa4c-115">文件格式</span><span class="sxs-lookup"><span data-stu-id="8fa4c-115">File Formats</span></span>](#bkmk_file_formats)  
  
-   [<span data-ttu-id="8fa4c-116">文件选项</span><span class="sxs-lookup"><span data-stu-id="8fa4c-116">File Options</span></span>](#bkmk_file_options)  
  
##  <a name="characteristics-of-a-report-that-is-delivered-to-a-shared-folder"></a><a name="bkmk_Characteristics"></a><span data-ttu-id="8fa4c-117">传递到共享文件夹的报表的特征</span><span class="sxs-lookup"><span data-stu-id="8fa4c-117">Characteristics of a Report That is Delivered to a Shared Folder</span></span>  
 <span data-ttu-id="8fa4c-118">与报表服务器承载和管理的报表不同，传递到共享文件夹的报表是静态的文件。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-118">Unlike reports that are hosted and managed by a report server, reports that are delivered to a shared folder are static files.</span></span> <span data-ttu-id="8fa4c-119">为报表定义的交互功能在作为文件存储到文件系统中的报表上不起作用。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-119">Interactive features that are defined for the report do not work for reports that are stored as files on the file system.</span></span> <span data-ttu-id="8fa4c-120">交互功能将表示为静态元素。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-120">Interaction features are represented as static elements.</span></span> <span data-ttu-id="8fa4c-121">例如，如果传递矩阵报表，结果文件只能显示报表的顶级视图；您不能通过展开行和列来查看支持数据。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-121">For example, if you deliver a matrix report, the resulting file shows the top-level view of the report; you cannot expand rows and columns to view supporting data.</span></span> <span data-ttu-id="8fa4c-122">如果报表中包含图表，则图表将使用默认的显示方式。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-122">If the report includes charts, the default presentation is used.</span></span> <span data-ttu-id="8fa4c-123">如果报表链接到其他报表，则链接呈现为静态文本。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-123">If the report links through to another report, the link is rendered as static text.</span></span> <span data-ttu-id="8fa4c-124">若要在传递的报表中保留交互功能，请改用电子邮件传递。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-124">If you want to retain interactive features in a delivered report, use e-mail delivery instead.</span></span> <span data-ttu-id="8fa4c-125">有关详细信息，请参阅 [Reporting Services 中的电子邮件传递](e-mail-delivery-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-125">For more information, see [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md).</span></span>  
  
##  <a name="target-folders"></a><a name="bkmk_target_folders"></a><span data-ttu-id="8fa4c-126">目标文件夹</span><span class="sxs-lookup"><span data-stu-id="8fa4c-126">Target Folders</span></span>  
 <span data-ttu-id="8fa4c-127">如果所定义的订阅使用文件共享传递，则必须指定现有文件夹作为目标文件夹。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-127">When defining a subscription that uses file share delivery, you must specify an existing folder as the target folder.</span></span> <span data-ttu-id="8fa4c-128">报表服务器不会在文件系统上创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-128">The report server does not create folders on the file system.</span></span> <span data-ttu-id="8fa4c-129">您指定的文件夹必须可通过网络连接进行访问。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-129">The folder that you specify must be accessible over a network connection.</span></span>  
  
 <span data-ttu-id="8fa4c-130">验证将查看共享文件夹中报表的用户是否具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-130">Verify that users who will view the reports in the shared folder have Read permission.</span></span>  
  
 <span data-ttu-id="8fa4c-131">在订阅中指定目标文件夹时，请使用包含计算机网络名称的通用命名约定 (UNC) 格式。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-131">When specifying the target folder in a subscription, use Uniform Naming Convention (UNC) format that includes the computer's network name.</span></span> <span data-ttu-id="8fa4c-132">不能在文件夹路径中包含尾随反斜杠。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-132">Do not include trailing backslashes in the folder path.</span></span> <span data-ttu-id="8fa4c-133">下面是一个 UNC 路径的示例：</span><span class="sxs-lookup"><span data-stu-id="8fa4c-133">The following example illustrates a UNC path:</span></span>  
  
```  
\\<servername>\reportarchive\operations\2003  
```  
  
 <span data-ttu-id="8fa4c-134">当您创建该文件夹时，请考虑所需的连接限制。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-134">When you create the folder, consider the connection limits you require.</span></span> <span data-ttu-id="8fa4c-135">报表服务器需要两种连接，但是您必须包括足够的连接才能容纳其他要打开共享文件夹中的报表的用户。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-135">The report server requires two connections, but you must include enough connections to accommodate additional users who want to open reports on the shared folder.</span></span>  
  
##  <a name="file-formats"></a><a name="bkmk_file_formats"></a> <span data-ttu-id="8fa4c-136">文件格式</span><span class="sxs-lookup"><span data-stu-id="8fa4c-136">File Formats</span></span>  
 <span data-ttu-id="8fa4c-137">在呈现报表时可以使用多种文件格式，如 HTML 或 Excel。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-137">Reports can be rendered in a variety of file formats, such as HTML or Excel.</span></span> <span data-ttu-id="8fa4c-138">若要按特定文件格式保存报表，请在创建订阅时选择相应的呈现格式。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-138">To save the report in a specific file format, select that rendering format when creating your subscription.</span></span> <span data-ttu-id="8fa4c-139">例如，如果选择 **Excel** ，则会将报表保存为 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 格式。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-139">For example, choosing **Excel** saves the report as a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] file.</span></span> <span data-ttu-id="8fa4c-140">虽然您可以选择任意支持的呈现格式，但对于不同的格式，呈现文件的优劣效果会有所不同。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-140">Although you can choose from any supported rendering format, some formats work better than others when rendering to a file.</span></span>  
  
 <span data-ttu-id="8fa4c-141">对于文件共享传递，请选择以单一文件传递报表的格式，其中，所有图像和相关内容都包含在报表内。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-141">For file share delivery, choose a format that delivers the report in a single file, where all images and related content are included in the report.</span></span> <span data-ttu-id="8fa4c-142">适用的格式包括 Web 存档、PDF、TIFF 和 Excel。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-142">Suitable formats include Web archive, PDF, TIFF, and Excel.</span></span> <span data-ttu-id="8fa4c-143">请避免使用 HTML4.0。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-143">Avoid HTML4.0.</span></span> <span data-ttu-id="8fa4c-144">如果报表中包括图像，则 HTML 4.0 格式不会将图像包括在文件中。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-144">If your report includes images, the HTML 4.0 formats will not include them in the file.</span></span>  
  
##  <a name="file-options"></a><a name="bkmk_file_options"></a> <span data-ttu-id="8fa4c-145">文件选项</span><span class="sxs-lookup"><span data-stu-id="8fa4c-145">File Options</span></span>  
 <span data-ttu-id="8fa4c-146">创建订阅时，可以通过选择有关选项来确定文件名的创建方式，以及是否在以后用更新的版本替代它。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-146">When you create a subscription, you can choose options that determine how the file name is created and whether it is replaced by newer versions over time.</span></span> <span data-ttu-id="8fa4c-147">完全限定的文件名有三部分：名称、扩展名和文本/数字，将文本/数字追加到文件末尾可以创建唯一的文件名。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-147">A fully qualified file name has three parts: a name, an extension, and text or a number that is appended to the file to create a unique file name.</span></span> <span data-ttu-id="8fa4c-148">覆盖选项确定了是否在文件名末尾添加文本或数字。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-148">Overwrite options determine whether the text or number is added to the file name.</span></span>  
  
 <span data-ttu-id="8fa4c-149">文件名基于报表名称，但您可以在订阅中提供自定义名称。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-149">The file name is based on the report name, but you can provide a custom name in the subscription.</span></span> <span data-ttu-id="8fa4c-150">扩展名是可选的，但如果指定它的话，报表服务器将创建对应于呈现格式的扩展名。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-150">The extension is optional, but if you specify it, the report server will create an extension that corresponds to the rendering format.</span></span>  
  
 <span data-ttu-id="8fa4c-151">您可以指定覆盖选项对每个报表传递重复使用相同的文件名或者创建新文件。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-151">You can specify overwrite options to reuse the same file name for each report delivery or to create a new file.</span></span> <span data-ttu-id="8fa4c-152">若要覆盖文件，必须使用相同的文件名和扩展名。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-152">To overwrite the file, you must use the same file name and extension.</span></span>  
  
 <span data-ttu-id="8fa4c-153">为每个传递创建唯一的文件的另一种方法是在文件名中包含时间戳。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-153">An alternative approach to creating unique files for every delivery is to include a timestamp in the file name.</span></span> <span data-ttu-id="8fa4c-154">若要执行此操作，请将“”`@timestamp`变量添加到文件名中（例如，CompanySales@timestamp\*\*）。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-154">To do this, add the `@timestamp` variable to the file name (for example, *CompanySales@timestamp*).</span></span> <span data-ttu-id="8fa4c-155">采用这种方法，文件名的定义是唯一的，因此永远不会被覆盖。</span><span class="sxs-lookup"><span data-stu-id="8fa4c-155">With this approach, the file name is unique by definition, so it will never be overwritten.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fa4c-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8fa4c-156">See Also</span></span>  
 [<span data-ttu-id="8fa4c-157">在纯模式下创建、修改和删除标准订阅 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8fa4c-157">Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;</span></span>](create-and-manage-subscriptions-for-native-mode-report-servers.md)  
  
  
