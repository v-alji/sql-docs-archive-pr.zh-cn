---
title: 向 URL 添加超链接（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d3392c0b-7b62-4d27-bc04-2bd0c5487d08
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d3db3fc75feca1393e73e698f44db633f09e8dc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688588"
---
# <a name="add-a-hyperlink-to-a-url-report-builder-and-ssrs"></a><span data-ttu-id="4c880-102">向 URL 添加超链接（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4c880-102">Add a Hyperlink to a URL (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4c880-103">如果您希望用户能在报表中单击链接即可打开浏览器浏览您指定的 URL，则可向报表项添加一个超链接。</span><span class="sxs-lookup"><span data-stu-id="4c880-103">You can add a hyperlink to a report item when you want your users to be able to click a link in a report and open a browser to the URL that you specify.</span></span> <span data-ttu-id="4c880-104">超链接既可以是静态 URL，也可以是计算结果为 URL 的表达式。</span><span class="sxs-lookup"><span data-stu-id="4c880-104">A hyperlink can be a static URL or an expression that evaluates to a URL.</span></span> <span data-ttu-id="4c880-105">如果数据库中的某个字段包含 URL，则表达式可以包含该字段，从而为报表提供超链接的动态列表。</span><span class="sxs-lookup"><span data-stu-id="4c880-105">If you have a field in a database that contains URLs, the expression can contain that field, resulting in a dynamic list of hyperlinks in the report.</span></span> <span data-ttu-id="4c880-106">您可以向文本框、图像、图表和仪表添加超链接。</span><span class="sxs-lookup"><span data-stu-id="4c880-106">You can add hyperlinks to text boxes, images, charts, and gauges.</span></span> <span data-ttu-id="4c880-107">必须确保该用户对您提供的 URL 具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="4c880-107">You must ensure that the user has access to the URL that you provide.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="4c880-108">如果您和您的用户有权使用对报表服务器的 URL 请求来查看某一报表服务器上的报表，则您还可以指定指向这些报表的 URL。</span><span class="sxs-lookup"><span data-stu-id="4c880-108">You can also specify URLs to reports on any report server that you and your users have permission to view using URL requests to the report server.</span></span> <span data-ttu-id="4c880-109">例如，可以指定一个报表，并在用户首次查看该报表时隐藏文档结构图。</span><span class="sxs-lookup"><span data-stu-id="4c880-109">For example, you can specify a report and hide the document map for the user when they first view the report.</span></span> <span data-ttu-id="4c880-110">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312)中的 [URL 访问 (SSRS)](../url-access-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4c880-110">For more information, see [URL Access &#40;SSRS&#41;](../url-access-ssrs.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="4c880-111">还可以向具有 **“操作”** 属性的任何项的 URL 添加超链接，例如图表中的文本框、图像或计算序列。</span><span class="sxs-lookup"><span data-stu-id="4c880-111">You can add a hyperlink to a URL to any item that has an **Action** property, for example, a text box, an image, or a calculated series in a chart.</span></span> <span data-ttu-id="4c880-112">用户单击该报表项时，将执行您所定义的操作。</span><span class="sxs-lookup"><span data-stu-id="4c880-112">When the user clicks that report item, the action that you define takes place.</span></span> <span data-ttu-id="4c880-113">有关详细信息，请参阅[“操作属性”对话框（报表生成器和 SSRS）](../action-properties-dialog-box-report-builder-and-ssrs.md)和[指定外部项的路径（报表生成器和 SSRS）](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4c880-113">For more information, see the [Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) and [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="4c880-114">若要快速开始使用，请参阅[教程：设置文本格式（报表生成器）](../tutorial-format-text-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4c880-114">To quickly get started, see [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c880-115">绑定到数据集字段的链接容易被篡改。</span><span class="sxs-lookup"><span data-stu-id="4c880-115">Links that are bound to dataset fields can be vulnerable to tampering for malicious purposes.</span></span> <span data-ttu-id="4c880-116">有关详细信息，请参阅 msdn.microsoft.com 上 [联机丛书](../security/secure-reports-and-resources.md) 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][保护报表和资源](https://go.microsoft.com/fwlink/?LinkId=154888) 。</span><span class="sxs-lookup"><span data-stu-id="4c880-116">For more information, see [Secure Reports and Resources](../security/secure-reports-and-resources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
### <a name="to-add-a-hyperlink"></a><span data-ttu-id="4c880-117">添加超链接</span><span class="sxs-lookup"><span data-stu-id="4c880-117">To add a hyperlink</span></span>  
  
1.  <span data-ttu-id="4c880-118">在报表设计视图中，右键单击要添加链接的文本框、图像或图表，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="4c880-118">In report design view, right-click the text box, image, or chart to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="4c880-119">在“属性”对话框中，单击 **“操作”**。</span><span class="sxs-lookup"><span data-stu-id="4c880-119">In the Properties dialog box, click **Action**.</span></span>  
  
3.  <span data-ttu-id="4c880-120">选择 **“转到 URL”**。</span><span class="sxs-lookup"><span data-stu-id="4c880-120">Select **Go to URL**.</span></span> <span data-ttu-id="4c880-121">其他部分将显示在此选项的对话框中。</span><span class="sxs-lookup"><span data-stu-id="4c880-121">An additional section appears in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="4c880-122">在 **“选择 URL”** 中，键入或选择某一 URL 或者计算结果为某一 URL 的表达式，或者单击下拉箭头并单击包含 URL 的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="4c880-122">In **Select URL**, type or select a URL or an expression that evaluates to a URL, or click the drop-down arrow and click the name of a field that contains a URL.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="4c880-123">（可选）文本的格式不会自动设置为链接。</span><span class="sxs-lookup"><span data-stu-id="4c880-123">(Optional) The text is not automatically formatted as a link.</span></span> <span data-ttu-id="4c880-124">对于文本，很有必要更改文本的颜色和效果以指示该文本是一个链接。</span><span class="sxs-lookup"><span data-stu-id="4c880-124">For text, it is helpful to change the color and effect of the text to indicate that the text is a link.</span></span> <span data-ttu-id="4c880-125">例如，在功能区的“主页”选项卡中的 **“字体”** 部分中，将颜色更改为蓝色，并将效果更改为下划线。</span><span class="sxs-lookup"><span data-stu-id="4c880-125">For example, change the color to blue and the effect to underline in the **Font** section in the Home tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="4c880-126">若要测试该链接，请单击 **“运行”** 以预览报表，然后单击对其设置此链接的报表项。</span><span class="sxs-lookup"><span data-stu-id="4c880-126">To test the link, click **Run** to preview the report, and then click the report item that you set this link on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c880-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c880-127">See Also</span></span>  
 <span data-ttu-id="4c880-128">[交互式排序、文档结构图和链接 &#40;报表生成器和 SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4c880-128">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4c880-129">创建文档结构图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4c880-129">Create a Document Map &#40;Report Builder and SSRS&#41;</span></span>](create-a-document-map-report-builder-and-ssrs.md)  
  
  
