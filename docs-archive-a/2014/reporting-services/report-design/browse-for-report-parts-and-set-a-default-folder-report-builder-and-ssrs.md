---
title: 浏览查找报表部件和设置默认文件夹（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5cf38068-65d1-4fe8-81f3-a404d8fbc663
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6605a23732799ec07b3dbe8481e88c91b18ebe5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578643"
---
# <a name="browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs"></a><span data-ttu-id="ce6fa-102">浏览查找报表部件和设置默认文件夹（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ce6fa-102">Browse for Report Parts and Set a Default Folder (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ce6fa-103">创建报表的最简单方式是从报表部件库将现有报表部件（如表和图表）添加到您的报表。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-103">The easiest way to create a report is to add existing report parts, such as tables and charts, to your report from the Report Part Gallery.</span></span> <span data-ttu-id="ce6fa-104">将报表部件添加到报表时，还将添加它正常工作所需的所有内容。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-104">When you add a report part to your report, you are also adding everything it must have to work.</span></span> <span data-ttu-id="ce6fa-105">例如，显示数据的任何报表部件都依赖于数据集，即对某数据源的查询和连接。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-105">For example, any report part that displays data depends on a dataset, that is, a query and a connection to a data source.</span></span> <span data-ttu-id="ce6fa-106">将报表部件添加到报表后，可以根据需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-106">After you add the report part to your report, you can modify it as much as you need.</span></span>  
  
 <span data-ttu-id="ce6fa-107">您可以设置一个默认文件夹，以便将报表部件发布到报表服务器或者与报表服务器相集成的 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-107">You can set a default folder to publish report parts to the report server or SharePoint site integrated with a report server.</span></span>  
  
 <span data-ttu-id="ce6fa-108">有关详细信息，请参阅 [报表部件（报表生成器和 SSRS）](../report-parts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-108">For more information, see [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-browse-for-report-parts"></a><span data-ttu-id="ce6fa-109">查找报表部件</span><span class="sxs-lookup"><span data-stu-id="ce6fa-109">To browse for report parts</span></span>  
  
1.  <span data-ttu-id="ce6fa-110">在 **“插入”** 菜单上，单击 **“报表部件”** 。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-110">On the **Insert** menu, click **Report Parts**.</span></span>  
  
     <span data-ttu-id="ce6fa-111">如果尚未建立连接，请单击 **“连接到报表服务器”** ，然后输入名称。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-111">If you are not already connected, click **Connect to a report server**, and enter the name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ce6fa-112">您必须连接到报表服务器以便查找报表部件。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-112">You must be connected to a report server to browse for report parts.</span></span>  
  
2.  <span data-ttu-id="ce6fa-113">可以通过指定有关报表部件的详细信息来缩小搜索范围。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-113">You can narrow your search by specifying details about the report part.</span></span> <span data-ttu-id="ce6fa-114">在 **“搜索”** 框中键入所有或部分名称和说明，或单击 **“添加条件”** 以添加以下任意字段的值：</span><span class="sxs-lookup"><span data-stu-id="ce6fa-114">Type all or part of the name and description in the **Search** box, or click **Add Criteria** and add values for any or all of these fields:</span></span>  
  
    -   <span data-ttu-id="ce6fa-115">创建者</span><span class="sxs-lookup"><span data-stu-id="ce6fa-115">Created by</span></span>  
  
    -   <span data-ttu-id="ce6fa-116">创建日期</span><span class="sxs-lookup"><span data-stu-id="ce6fa-116">Date created</span></span>  
  
    -   <span data-ttu-id="ce6fa-117">上次修改日期</span><span class="sxs-lookup"><span data-stu-id="ce6fa-117">Date last modified</span></span>  
  
    -   <span data-ttu-id="ce6fa-118">上次修改者</span><span class="sxs-lookup"><span data-stu-id="ce6fa-118">Last modified by</span></span>  
  
    -   <span data-ttu-id="ce6fa-119">服务器文件夹</span><span class="sxs-lookup"><span data-stu-id="ce6fa-119">Server folder</span></span>  
  
    -   <span data-ttu-id="ce6fa-120">类型</span><span class="sxs-lookup"><span data-stu-id="ce6fa-120">Type</span></span>  
  
     <span data-ttu-id="ce6fa-121">例如，若要查找图像，请单击 **“添加条件”** ，然后单击 **“类型”** 。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-121">For example, to find an image, click **Add Criteria**, and then click **Type**.</span></span> <span data-ttu-id="ce6fa-122">在下拉框中，选中 **“图像”** 复选框，按 Enter 键，然后单击“搜索”放大镜。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-122">In the dropdown box, select the **Image** check box, press ENTER, and then click the Search magnifying glass.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ce6fa-123">对于“创建者”和“上次修改者”值，搜索用户的用户名，正如它在报表服务器上显示的那样   。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-123">For the **Created by** and **Last modified by** values, search for the person's user name as it is represented on the report server.</span></span>  
  
### <a name="to-set-a-default-folder-for-report-parts"></a><span data-ttu-id="ce6fa-124">为报表部件设置默认文件夹</span><span class="sxs-lookup"><span data-stu-id="ce6fa-124">To set a default folder for report parts</span></span>  
  
1.  <span data-ttu-id="ce6fa-125">单击 **“报表生成器”** ，然后单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-125">Click **Report Builder**, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="ce6fa-126">在“选项”对话框的“设置”选项卡中，在“默认将报表部件发布到此文件夹”文本框中键入文件夹名称    。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-126">In the **Options** dialog box, on the **Settings** tab, type a folder name in the **Publish report parts to this folder by default** textbox.</span></span>  
  
 <span data-ttu-id="ce6fa-127">如果此文件夹不存在且您具有在报表服务器上创建文件夹的权限，报表生成器将创建此文件夹。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-127">Report Builder will create this folder if you have permissions to create folders on the report server and the folder does not exist yet.</span></span>  
  
 <span data-ttu-id="ce6fa-128">不需要重新启动报表生成器，此设置就能生效。</span><span class="sxs-lookup"><span data-stu-id="ce6fa-128">You do not need to restart Report Builder for this setting to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6fa-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce6fa-129">See Also</span></span>  
 <span data-ttu-id="ce6fa-130">[检查更新或关闭更新 &#40;报表生成器和 SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ce6fa-130">[Check for Updates or Turn Updates Off &#40;Report Builder and SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ce6fa-131">[报表部件（报表生成器和 SSRS）](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ce6fa-131">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ce6fa-132">[报表生成器中的报表部件和数据集](../report-data/report-parts-and-datasets-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ce6fa-132">[Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) </span></span>  
 <span data-ttu-id="ce6fa-133">[&#40;报表生成器和 SSRS 的报表部件疑难解答&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ce6fa-133">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ce6fa-134">发布和重新发布报表部件（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ce6fa-134">Publish and Republish Report Parts &#40;Report Builder and SSRS&#41;</span></span>](publish-and-republish-report-parts-report-builder-and-ssrs.md)  
  
  
