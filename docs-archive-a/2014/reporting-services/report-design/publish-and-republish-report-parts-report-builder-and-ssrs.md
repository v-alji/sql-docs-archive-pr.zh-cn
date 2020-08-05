---
title: 发布和重新发布报表部件（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 92dce484-f39b-403c-9caf-d8772bc3aca3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 95fd5e3f7519c6a0d4a6f08cb9bcbf2507d32aaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580576"
---
# <a name="publish-and-republish-report-parts-report-builder-and-ssrs"></a><span data-ttu-id="4073e-102">发布和重新发布报表部件（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4073e-102">Publish and Republish Report Parts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4073e-103">您可以使用默认设置将报表部件发布到默认位置中，或者，您可以编辑名称和说明之类的报表部件元数据，并且将其保存在报表服务器上的其他位置。</span><span class="sxs-lookup"><span data-stu-id="4073e-103">You can publish a report part with default settings in a default location, or you can edit report part metadata such as name and description, and save it somewhere else on a report server.</span></span> <span data-ttu-id="4073e-104">如果您具有正确的权限，还可以将报表部件保存到与报表服务器集成的 SharePoint 站点上。</span><span class="sxs-lookup"><span data-stu-id="4073e-104">You can also save it to a SharePoint site that is integrated with a report server if you have the correct permissions.</span></span>  
  
 <span data-ttu-id="4073e-105">您可以将报表部件与它所依赖的、嵌入其中的数据集一起发布，也可以单独发布数据集。</span><span class="sxs-lookup"><span data-stu-id="4073e-105">You can publish just the report part, with the dataset that it depends on embedded in it, or you can publish the dataset separately.</span></span> <span data-ttu-id="4073e-106">如果单独发布数据集，它将成为共享数据集，并且报表部件将与其链接。</span><span class="sxs-lookup"><span data-stu-id="4073e-106">If you publish the dataset separately, it becomes a shared dataset, and the report part links to it.</span></span> <span data-ttu-id="4073e-107">有关详细信息，请参阅 [报表生成器中的报表部件和数据集](../report-data/report-parts-and-datasets-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4073e-107">For more information, see [Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="4073e-108">您可以重新发布现有的报表部件。</span><span class="sxs-lookup"><span data-stu-id="4073e-108">You can republish an existing report part.</span></span> <span data-ttu-id="4073e-109">如果您具有权限，则可以将报表部件的原始实例保存在服务器上, 即使您没有创建它。</span><span class="sxs-lookup"><span data-stu-id="4073e-109">If you have permissions, you can save over the original instance of the report part on the server, even if you didn't create it.</span></span> <span data-ttu-id="4073e-110">您还可以将其发布为新的报表部件，并且将它保存在相同或不同的位置。</span><span class="sxs-lookup"><span data-stu-id="4073e-110">You can also publish it as a new report part and save it either in the same or a different location.</span></span>  
  
### <a name="to-publish-a-report-part"></a><span data-ttu-id="4073e-111">发布报表部件</span><span class="sxs-lookup"><span data-stu-id="4073e-111">To publish a report part</span></span>  
  
1.  <span data-ttu-id="4073e-112">在报表生成器菜单上，单击 **“发布报表部件”**。</span><span class="sxs-lookup"><span data-stu-id="4073e-112">On the Report Builder menu, click **Publish Report Parts**.</span></span>  
  
     <span data-ttu-id="4073e-113">如果您没有连接到某一报表服务器，则系统将会提示您进行连接。</span><span class="sxs-lookup"><span data-stu-id="4073e-113">If you are not connected to a report server, you will be prompted to connect.</span></span> <span data-ttu-id="4073e-114">如果您无法连接到报表服务器，则不能发布报表部件。</span><span class="sxs-lookup"><span data-stu-id="4073e-114">If you cannot connect to a report server, you cannot publish report parts.</span></span>  
  
2.  <span data-ttu-id="4073e-115">若要使用默认设置将报表部件保存到默认位置，请单击 **“使用默认设置发布所有报表部件”**。</span><span class="sxs-lookup"><span data-stu-id="4073e-115">To save your report parts with default settings to the default location, click **Publish all report parts with default settings**.</span></span>  
  
     <span data-ttu-id="4073e-116">否则，单击 **“在发布前查看和修改报表部件”**。</span><span class="sxs-lookup"><span data-stu-id="4073e-116">Otherwise, click **Review and modify report parts before publishing**.</span></span>  
  
3.  <span data-ttu-id="4073e-117">编辑报表部件名称和说明：双击名称以便编辑它，然后在“说明”\*\*\*\* 字段中单击以便添加说明。</span><span class="sxs-lookup"><span data-stu-id="4073e-117">Edit the report part name and description: Double-click the name to edit it and click in the **Description** field to add a description.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4073e-118">最好提供报表部件名称和说明，以便在搜索时帮助用户识别它。</span><span class="sxs-lookup"><span data-stu-id="4073e-118">It is a good idea to give the report part name and description, to help people identify it when searching.</span></span> <span data-ttu-id="4073e-119">对于整个路径而言，报表部件名称的最大长度是 260 个字符，包括服务器上文件夹的名称，后随报表部件的实际名称。</span><span class="sxs-lookup"><span data-stu-id="4073e-119">The maximum length for the name of a report part is 260 characters for the entire path, including the names of the folders on the server, followed by the actual name of the report part.</span></span>  
  
4.  <span data-ttu-id="4073e-120">若要将报表部件保存到默认位置外的其他文件夹，请单击 **“浏览”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="4073e-120">To save your report part to a folder other than the default, click the **Browse** button.</span></span>  
  
5.  <span data-ttu-id="4073e-121">在您为报表中的所有报表部件都设置了选项之后，请单击 **“发布”**。</span><span class="sxs-lookup"><span data-stu-id="4073e-121">When you have set the options for all the report parts in the report, click **Publish**.</span></span>  
  
     <span data-ttu-id="4073e-122">在发布报表部件后，对话框将显示哪些报表部件已成功发布，哪些未成功发布。</span><span class="sxs-lookup"><span data-stu-id="4073e-122">After you publish the report parts, the dialog box shows which were successfully published and which were not.</span></span> <span data-ttu-id="4073e-123">对于未能发布的报表部件，您可以在 **“发布报表部件”** 对话框中查看详细信息。</span><span class="sxs-lookup"><span data-stu-id="4073e-123">You can view details in the **Publish Report Parts** dialog box for the report parts that failed to publish.</span></span>  
  
6.  <span data-ttu-id="4073e-124">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="4073e-124">Click **Close**.</span></span>  
  
### <a name="to-republish-a-report-part"></a><span data-ttu-id="4073e-125">重新发布报表部件</span><span class="sxs-lookup"><span data-stu-id="4073e-125">To republish a report part</span></span>  
  
1.  <span data-ttu-id="4073e-126">按照前面的过程发布报表部件。</span><span class="sxs-lookup"><span data-stu-id="4073e-126">Follow the previous procedure for publishing a report part.</span></span>  
  
2.  <span data-ttu-id="4073e-127">在 **“发布报表部件”** 对话框中，如果您单击 **“作为报表部件的新副本发布”**，则报表生成器将不会保存在服务器的现有报表部件上，而将改为创建另一个报表部件。</span><span class="sxs-lookup"><span data-stu-id="4073e-127">In the **Publish Report Parts** dialog box, if you click **Publish as a New Copy of the Report Part**, Report Builder will not save over the existing report part on the server, but will create another report part instead.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4073e-128">如果您将其作为新的报表部件发布，则该报表部件将具有新的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4073e-128">If you publish it as a new report part, it will have a new unique ID.</span></span> <span data-ttu-id="4073e-129">如果原始报表部件发生更改，它将不再接收更新。</span><span class="sxs-lookup"><span data-stu-id="4073e-129">It will no longer receive updates if the original report part changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4073e-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4073e-130">See Also</span></span>  
 <span data-ttu-id="4073e-131">[报表部件 &#40;报表生成器和 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4073e-131">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4073e-132">[报表生成器中的报表部件和数据集](../report-data/report-parts-and-datasets-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4073e-132">[Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) </span></span>  
 <span data-ttu-id="4073e-133">[&#40;报表生成器和 SSRS 的报表部件疑难解答&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4073e-133">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4073e-134">[检查更新或关闭更新 &#40;报表生成器和 SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4073e-134">[Check for Updates or Turn Updates Off &#40;Report Builder and SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4073e-135">浏览查找报表部件和设置默认文件夹（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4073e-135">Browse for Report Parts and Set a Default Folder &#40;Report Builder and SSRS&#41;</span></span>](browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md)  
  
  
