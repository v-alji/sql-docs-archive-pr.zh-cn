---
title: 呈现数据（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a458fdf9-fb2a-4fee-9fbd-b38f36e91753
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc2757d308529c8b5a03e206a827fce7028edbfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691607"
---
# <a name="rendering-data-report-builder-and-ssrs"></a><span data-ttu-id="5db0e-102">呈现数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5db0e-102">Rendering Data (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5db0e-103">使用 HTML、MHTML、Word、Excel、PDF 或 Image 之类的布局呈现器时，数据和其组织保持不变。</span><span class="sxs-lookup"><span data-stu-id="5db0e-103">When using layout renderers, such as HTML, MHTML, Word, Excel, PDF or Image, the data and its organization remains unchanged.</span></span> <span data-ttu-id="5db0e-104">当使用逗号分隔值 (CSV) 或 XML 之类的数据呈现器格式导出时，不会呈现任何可视布局元素。</span><span class="sxs-lookup"><span data-stu-id="5db0e-104">When exporting using a data renderer format, such as Comma-Separated Value (CSV) or XML, no visual layout elements are rendered.</span></span> <span data-ttu-id="5db0e-105">呈现报表时，CSV 和 XML 会将某些规则应用到表体及其内容。</span><span class="sxs-lookup"><span data-stu-id="5db0e-105">CSV and XML apply certain rules to the report body and its contents when rendering the report.</span></span> <span data-ttu-id="5db0e-106">这些规则用于确定数据在这些格式中的呈现方式。</span><span class="sxs-lookup"><span data-stu-id="5db0e-106">These rules determine how the data is rendered in these formats.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="5db0e-107">可以使用数据呈现器执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5db0e-107">You can use data renderers to:</span></span>  
  
-   <span data-ttu-id="5db0e-108">导入到数据库。</span><span class="sxs-lookup"><span data-stu-id="5db0e-108">Import to a database.</span></span> <span data-ttu-id="5db0e-109">CSV 是一种可由包括 SQL Server 和 Microsoft Access 在内的许多数据库应用程序轻松导入的常用格式。</span><span class="sxs-lookup"><span data-stu-id="5db0e-109">CSV is a common format that is easily importable by many database applications including SQL Server and Microsoft Access.</span></span>  
  
-   <span data-ttu-id="5db0e-110">导入到 Excel。</span><span class="sxs-lookup"><span data-stu-id="5db0e-110">Import to Excel.</span></span> <span data-ttu-id="5db0e-111">使用 CSV 呈现器可将数据导出为不带可视布局的 Excel 格式。</span><span class="sxs-lookup"><span data-stu-id="5db0e-111">Use the CSV renderer to export your data to Excel without the visual layout.</span></span> <span data-ttu-id="5db0e-112">数据导出为 Excel 后，便可以使用标准的 Excel 工具，例如图表、公式和透视表。</span><span class="sxs-lookup"><span data-stu-id="5db0e-112">After your data is in Excel, you can take advantage of standard Excel tools such as charts, formulas, and pivot tables.</span></span>  
  
-   <span data-ttu-id="5db0e-113">XSLT 转换。</span><span class="sxs-lookup"><span data-stu-id="5db0e-113">XSLT transformations.</span></span> <span data-ttu-id="5db0e-114">可将 XSLT 应用到 XML 呈现器的输出。</span><span class="sxs-lookup"><span data-stu-id="5db0e-114">An XSLT can be applied to the output of the XML renderer.</span></span> <span data-ttu-id="5db0e-115">这种服务器端转换是一种可将数据转换为几乎任何格式的有效方法。</span><span class="sxs-lookup"><span data-stu-id="5db0e-115">This server-side transformation is a powerful technique to transform your data to virtually any format.</span></span>  
  
-   <span data-ttu-id="5db0e-116">数据交换/EDI。</span><span class="sxs-lookup"><span data-stu-id="5db0e-116">Data exchange/EDI.</span></span> <span data-ttu-id="5db0e-117">外部进程可以请求对报表进行 CSV 或 XML 呈现并使用这些数据。</span><span class="sxs-lookup"><span data-stu-id="5db0e-117">An external process can request a CSV or XML rendering of a report and consume that data.</span></span>  
  
 <span data-ttu-id="5db0e-118">控制数据呈现器格式的属性集不同于控制布局呈现器的属性集。</span><span class="sxs-lookup"><span data-stu-id="5db0e-118">Data renderer formats are controlled by a different set of properties than layout renderers.</span></span> <span data-ttu-id="5db0e-119">以下是 **“属性”** 窗格中仅适用于数据呈现器的属性集列表。</span><span class="sxs-lookup"><span data-stu-id="5db0e-119">The following is a list of properties set in the **Properties** pane that apply only to data renderers:</span></span>  
  
-   <span data-ttu-id="5db0e-120">DataElementOutput 属性用于控制在导出时数据中是否包含特定项。</span><span class="sxs-lookup"><span data-stu-id="5db0e-120">The DataElementOutput property controls whether or not a specific item is present in the data when exported.</span></span>  
  
-   <span data-ttu-id="5db0e-121">DataElementName 属性用于控制数据元素的名称。</span><span class="sxs-lookup"><span data-stu-id="5db0e-121">The DataElementName property controls the name of the data element.</span></span> <span data-ttu-id="5db0e-122">在 CSV 中，这用于控制 CSV 列标题的名称。</span><span class="sxs-lookup"><span data-stu-id="5db0e-122">In CSV, this controls the name of the CSV column header.</span></span> <span data-ttu-id="5db0e-123">在 XML 中，这将成为项的 XML 元素或属性的名称。</span><span class="sxs-lookup"><span data-stu-id="5db0e-123">In XML, this becomes the name of the XML element or attribute for the item.</span></span>  
  
-   <span data-ttu-id="5db0e-124">DataElementStyle 属性用于控制在 XML 中是否将报表项呈现为元素或特性。</span><span class="sxs-lookup"><span data-stu-id="5db0e-124">The DataElementStyle property controls, in XML, whether or not the report item is rendered as an element or an attribute.</span></span>  
  
 <span data-ttu-id="5db0e-125">CSV 导出选项可将报表数据另存为不带任何格式的以逗号分隔的纯文本文件。</span><span class="sxs-lookup"><span data-stu-id="5db0e-125">The CSV export option saves report data as comma-delimited plain text files, without any formatting.</span></span> <span data-ttu-id="5db0e-126">默认情况下，文件使用逗号 (,) 分隔各个字段和行，但可以使用设备信息设置配置此设置。</span><span class="sxs-lookup"><span data-stu-id="5db0e-126">By default, the file uses a comma (,) to delimit fields and rows but this setting is configurable using the Device Information Settings.</span></span> <span data-ttu-id="5db0e-127">生成的文件可以用电子表格程序（如 Office SharePoint Server）打开，也可以用作其他程序的导入格式。</span><span class="sxs-lookup"><span data-stu-id="5db0e-127">The resulting file can be opened in a spreadsheet program like Office SharePoint Server or used as an import format for other programs.</span></span> <span data-ttu-id="5db0e-128">.csv 文件可在诸如记事本之类的文本编辑器中打开。</span><span class="sxs-lookup"><span data-stu-id="5db0e-128">The .csv file opens in a text editor such as Notepad.</span></span> <span data-ttu-id="5db0e-129">如果以 URL 形式进行访问，则 .csv 文件将返回 **text/csv**的 MIME 类型。</span><span class="sxs-lookup"><span data-stu-id="5db0e-129">If accessed as a URL, the .csv file returns a MIME type of **text/csv**.</span></span> <span data-ttu-id="5db0e-130">这种 .csv 文件为 MIME 1.0 版文件。</span><span class="sxs-lookup"><span data-stu-id="5db0e-130">The files are MIME version 1.0.</span></span> <span data-ttu-id="5db0e-131">有关以 CSV 文件类型呈现报表的详细信息，请参阅[导出到 CSV 文件（报表生成器和 SSRS）](../report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5db0e-131">For more information about rendering your report in the CSV file type, see [Exporting to a CSV File &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5db0e-132">使用具有报表数据导出选项的 XML 文件可将报表另存为 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5db0e-132">The XML file with report data export option saves a report as an XML file.</span></span> <span data-ttu-id="5db0e-133">报表的 XML 架构特定于报表。</span><span class="sxs-lookup"><span data-stu-id="5db0e-133">The XML schema for the report is specific to the report.</span></span> <span data-ttu-id="5db0e-134">XML 导出选项不保存报表布局信息。</span><span class="sxs-lookup"><span data-stu-id="5db0e-134">The report layout information is not saved by the XML export option.</span></span> <span data-ttu-id="5db0e-135">使用此选项生成的 XML 可以导入到数据库、用作 XML 数据消息或发送到自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="5db0e-135">The XML generated using this option can be imported into a database, used as an XML data message, or sent to a custom application.</span></span> <span data-ttu-id="5db0e-136">有关以 XML 文件类型呈现报表的详细信息，请参阅[导出到 XML（报表生成器和 SSRS）](../report-builder/exporting-to-xml-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5db0e-136">For more information about rendering your report in the XML file type, see [Exporting to XML &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-xml-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db0e-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5db0e-137">See Also</span></span>  
 <span data-ttu-id="5db0e-138">[Reporting Services 中的分页（报表生成器和 SSRS）](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5db0e-138">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5db0e-139">[呈现行为（报表生成器和 SSRS）](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5db0e-139">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5db0e-140">[不同报表呈现扩展插件的交互功能（报表生成器和 SSRS）](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="5db0e-140">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="5db0e-141">[呈现报表项（报表生成器和 SSRS）](rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5db0e-141">[Rendering Report Items &#40;Report Builder and SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5db0e-142">[列出 &#40;报表生成器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5db0e-142">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5db0e-143">Reporting Services 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="5db0e-143">Reporting Services Device Information Settings</span></span>](https://go.microsoft.com/fwlink/?LinkId=102515)  
  
  
