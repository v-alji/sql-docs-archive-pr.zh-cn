---
title: 基于报表生成数据馈送（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 340191396aaaa92fe14fe8c3c6b42539a713eb45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577354"
---
# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a><span data-ttu-id="bf4c7-102">从报表生成数据馈送（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="bf4c7-102">Generate Data Feeds from a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="bf4c7-103">你可以从报表生成与 Atom 兼容的数据馈送，然后在可使用数据馈送的应用程序（例如 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 客户端）中使用数据馈送。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-103">You can generate Atom-compliant data feeds from reports, and then use the data feeds in applications, such as the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] client, that can consume data feeds.</span></span>  
  
 <span data-ttu-id="bf4c7-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Atom 呈现扩展插件可生成 Atom 服务文档，该文档列出报表中可用的数据馈送。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-104">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Atom rendering extension generates an Atom service document that lists the data feeds available from a report.</span></span> <span data-ttu-id="bf4c7-105">该文档为报表中的每个数据区域至少列出一个数据馈送。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-105">The document lists at least one data feed for each data region in the report.</span></span> <span data-ttu-id="bf4c7-106">根据数据区域的类型以及数据区域显示的数据， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 可以自数据区域生成多个数据馈送。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-106">Depending on the type of data region and the data that the data region displays, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] might generate multiple data feeds from a data region.</span></span>  
  
 <span data-ttu-id="bf4c7-107">Atom 服务文档为每个数据馈送包含一个唯一标识符，在 URL 中使用该标识符可以查看数据馈送的内容。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-107">Atom service document contains a unique identifier for each the data feed and you use the identifier in a URL to view the content of the data feed.</span></span>  
  
 <span data-ttu-id="bf4c7-108">有关详细信息，请参阅[从报表生成数据馈送 &#40;报表生成器和 SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-108">For more information, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a><span data-ttu-id="bf4c7-109">生成 Atom 服务文档</span><span class="sxs-lookup"><span data-stu-id="bf4c7-109">To generate an Atom service document</span></span>  
  
1.  <span data-ttu-id="bf4c7-110">从报表管理器的 **“主页”** 导航至要从其生成数据馈送的报表。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-110">From the Report Manager **Home** page, navigate to the report from which you want to generate data feeds.</span></span>  
  
2.  <span data-ttu-id="bf4c7-111">单击该报表。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-111">Click the report.</span></span>  
  
     <span data-ttu-id="bf4c7-112">该报表将运行。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-112">The report is run.</span></span>  
  
3.  <span data-ttu-id="bf4c7-113">在工具栏上，单击“导出到数据馈送”图标。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-113">On the toolbar, click the Export to Data Feed icon.</span></span>  
  
     <span data-ttu-id="bf4c7-114">将出现一条消息，询问是要保存还是要打开包含数据馈送的 Atom 文档。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-114">A message appears asking you if you want to save or open the atom document that contains the data feed.</span></span>  
  
4.  <span data-ttu-id="bf4c7-115">单击 **“保存”** 可以将文档保存到文件系统，单击 **“打开”** 可以在保存前查看文档内容。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-115">Click **Save** to save the document to the file system, or click **Open** to view the document content before saving.</span></span> <span data-ttu-id="bf4c7-116">**默认情况下，文档将在浏览器中打开。**</span><span class="sxs-lookup"><span data-stu-id="bf4c7-116">**By default, the document opens in a browser.**</span></span>  
  
5.  <span data-ttu-id="bf4c7-117">找到保存文档的位置。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-117">Browse to the location to save the document.</span></span>  
  
6.  <span data-ttu-id="bf4c7-118">或者更改文档的名称。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-118">Optionally, change the name of the document.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bf4c7-119">默认情况下，文档名称就是报表名称。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-119">By default, the document name is the report name.</span></span>  
  
7.  <span data-ttu-id="bf4c7-120">确认文档类型为 **“ATOMSVC 文件”**，然后单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-120">Verify the document type is **ATOMSVC File**, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="bf4c7-121">或者，在浏览器或者文本编辑器或 XML 编辑器中打开该 .atomsvc 文件。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-121">Optionally, open the .atomsvc file in a browser or text or XML editor.</span></span>  
  
### <a name="to-view-an-atom-compliant-data-feed"></a><span data-ttu-id="bf4c7-122">查看与 Atom 兼容的数据馈送</span><span class="sxs-lookup"><span data-stu-id="bf4c7-122">To view an Atom-compliant data feed</span></span>  
  
1.  <span data-ttu-id="bf4c7-123">如果 Atom 服务文档尚未打开，则找到该文档并在 Internet Explorer 之类的浏览器中打开它。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-123">If the Atom service document is not already open, locate it and open it in a browser such as Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="bf4c7-124">将您要查看的数据馈送的 URL 从 Atom 服务文档复制到浏览器。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-124">Copy the URL of the data feed that you want to view from the Atom service document to the browser.</span></span>  
  
     <span data-ttu-id="bf4c7-125">该 URL 的格式如下：</span><span class="sxs-lookup"><span data-stu-id="bf4c7-125">The format of the URL is the following:</span></span>  
  
 `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
1.  <span data-ttu-id="bf4c7-126">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-126">Press ENTER.</span></span>  
  
     <span data-ttu-id="bf4c7-127">将出现一条消息，询问是要保存还是要打开包含数据馈送的 Atom 文档。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-127">A message appears asking you if you want to save or open the atom document that contains the data feed.</span></span>  
  
2.  <span data-ttu-id="bf4c7-128">单击 **“保存”** 可以将文档保存到文件系统，单击 **“打开”** 可以在保存前查看数据馈送。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-128">Click **Save** to save the document to the file system, or click **Open** to view the data feed before saving.</span></span>  
  
3.  <span data-ttu-id="bf4c7-129">找到保存文档的位置。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-129">Browse to the location to save the document.</span></span>  
  
4.  <span data-ttu-id="bf4c7-130">或者更改文档的名称。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-130">Optionally, change the name of the document.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bf4c7-131">默认情况下，文档名称就是报表名称。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-131">By default the document name is the report name.</span></span> <span data-ttu-id="bf4c7-132">如果该 Atom 服务文档具有多个数据馈送，默认情况下它们全都使用相同的名称，即报表名称。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-132">If the Atom service document has multiple feeds, by default all use the same name, the report name.</span></span> <span data-ttu-id="bf4c7-133">为了区分它们，请重命名这些数据馈送以便使用有意义的名称。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-133">To differentiate them, rename them to use meaningful names.</span></span>  
  
5.  <span data-ttu-id="bf4c7-134">确认文档类型为 **“ATOM 文件”**，然后单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-134">Verify the document type is **ATOM File**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="bf4c7-135">或者，在浏览器或者文本编辑器或 XML 编辑器中打开该 .atom 文件。</span><span class="sxs-lookup"><span data-stu-id="bf4c7-135">Optionally, open the .atom file in a browser or text editor or XML editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf4c7-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf4c7-136">See Also</span></span>  
 [<span data-ttu-id="bf4c7-137">导出报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bf4c7-137">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](export-reports-report-builder-and-ssrs.md)  
  
  
