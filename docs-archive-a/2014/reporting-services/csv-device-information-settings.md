---
title: CSV 设备信息设置 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CSV [Reporting Services]
- device information settings [Reporting Services], CSV rendering
ms.assetid: f96f83a6-50bc-48ce-9fcd-fd9e1952d40a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00369f2da9b248bcf66d551b5066f4ccd54e42e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586494"
---
# <a name="csv-device-information-settings"></a><span data-ttu-id="29c1e-102">CSV 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="29c1e-102">CSV Device Information Settings</span></span>
  <span data-ttu-id="29c1e-103">通过用于 CSV 呈现扩展插件的设备信息设置，可以更改分隔符和限定符并指定换行符处理。</span><span class="sxs-lookup"><span data-stu-id="29c1e-103">The device information settings for the CSV rendering extension allow delimiters and qualifiers to be changed and line break handling to be specified.</span></span> <span data-ttu-id="29c1e-104">还可以提交文件的扩展名，以及指示编码和是否在输出中包括标题行。</span><span class="sxs-lookup"><span data-stu-id="29c1e-104">The extension of the file can also be submitted, as well as the encoding and inclusion of header rows in the output.</span></span> <span data-ttu-id="29c1e-105">由于分隔符可能是特殊字符，因此，如果将设置编写为 XML，则应在 CDATA 部分对它们进行编码。</span><span class="sxs-lookup"><span data-stu-id="29c1e-105">Because delimiters are likely to be special characters, you should encode them in a CDATA section, if the settings are written as XML.</span></span>  
  
 <span data-ttu-id="29c1e-106">下表列出以文本格式呈现时的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="29c1e-106">The following table lists the device information settings for rendering in Text format.</span></span>  
  
|<span data-ttu-id="29c1e-107">设置</span><span class="sxs-lookup"><span data-stu-id="29c1e-107">Setting</span></span>|<span data-ttu-id="29c1e-108">值</span><span class="sxs-lookup"><span data-stu-id="29c1e-108">Value</span></span>|  
|-------------|-----------|  
|`Encoding`|<span data-ttu-id="29c1e-109">.NET Framework 支持的字符编码的 Internet 编号分配机构 (IANA) 名称。</span><span class="sxs-lookup"><span data-stu-id="29c1e-109">The Internet Assigned Numbers Authority (IANA) name of a character encoding that is supported by the .NET Framework.</span></span> <span data-ttu-id="29c1e-110">默认值为 `UTF-8`。</span><span class="sxs-lookup"><span data-stu-id="29c1e-110">The default value is `UTF-8`.</span></span> <span data-ttu-id="29c1e-111">其他值的示例包括 ASCII、UTF-7 和 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="29c1e-111">Examples of other values include ASCII, UTF-7, and UTF-16.</span></span>|  
|`ExcelMode`|<span data-ttu-id="29c1e-112">指定目标输出面向 Excel。</span><span class="sxs-lookup"><span data-stu-id="29c1e-112">Specifies that the target output is for Excel.</span></span> <span data-ttu-id="29c1e-113">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="29c1e-113">The default value is `true`.</span></span>|  
|`FieldDelimiter`|<span data-ttu-id="29c1e-114">要放入结果中的分隔符字符串。</span><span class="sxs-lookup"><span data-stu-id="29c1e-114">The delimiter string to put in the result.</span></span> <span data-ttu-id="29c1e-115">默认值为逗号 (,)。</span><span class="sxs-lookup"><span data-stu-id="29c1e-115">The default value is a comma (,).</span></span> <span data-ttu-id="29c1e-116">当您在 URL 中传递此设备信息的值时，应对该值进行 URL 编码。</span><span class="sxs-lookup"><span data-stu-id="29c1e-116">You should URL encode the value of this device information when passing it on a URL.</span></span> <span data-ttu-id="29c1e-117">例如，作为分隔符的制表符应为“%09”。</span><span class="sxs-lookup"><span data-stu-id="29c1e-117">For example, a tab character as a delimiter should be "%09".</span></span><br /><br /> <span data-ttu-id="29c1e-118">可通过在配置文件中更改设备信息设置将默认字段分隔符更改为任何所需的字符，包括 TAB。</span><span class="sxs-lookup"><span data-stu-id="29c1e-118">You can change the default field delimiter to any character that you want, including TAB, by changing the device information settings in the configuration file.</span></span> <span data-ttu-id="29c1e-119">例如，若要使用 TAB，请将 FieldDelimiter 设置更新为 \<FieldDelimiter xml:space="preserve"> [选项卡]\</FieldDelimiter></span><span class="sxs-lookup"><span data-stu-id="29c1e-119">For example, to use TAB, update the FieldDelimiter setting to \<FieldDelimiter xml:space="preserve">[TAB]\</FieldDelimiter></span></span><br /><br /> <span data-ttu-id="29c1e-120">在此示例中，[TAB] 是实际的制表符，它表示在配置文件中将出现空白字符。</span><span class="sxs-lookup"><span data-stu-id="29c1e-120">In the example [TAB] is an actual tab character, which means that whitespace appears in the configuration file.</span></span> <span data-ttu-id="29c1e-121">“xml:space”属性告诉分析器保留空白字符。</span><span class="sxs-lookup"><span data-stu-id="29c1e-121">The "xml:space" attribute tells parsers to preserve whitespace.</span></span>|  
|`FileExtension`|<span data-ttu-id="29c1e-122">要放入结果中的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="29c1e-122">The file extension to put on the result.</span></span> <span data-ttu-id="29c1e-123">默认值为 `.CSV`。</span><span class="sxs-lookup"><span data-stu-id="29c1e-123">The default value is `.CSV`.</span></span> <span data-ttu-id="29c1e-124">如果同时指定了 `FileExtension` 和 `Extension`，将优先使用 `FileExtension`。</span><span class="sxs-lookup"><span data-stu-id="29c1e-124">If both `FileExtension` and `Extension` are specified then `FileExtension` will take precedence.</span></span>|  
|<span data-ttu-id="29c1e-125">**NoHeader**</span><span class="sxs-lookup"><span data-stu-id="29c1e-125">**NoHeader**</span></span>|<span data-ttu-id="29c1e-126">指示是否从输出中排除标题行。</span><span class="sxs-lookup"><span data-stu-id="29c1e-126">Indicates whether the header row is excluded from the output.</span></span> <span data-ttu-id="29c1e-127">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="29c1e-127">The default value is `false`.</span></span>|  
|`Qualifier`|<span data-ttu-id="29c1e-128">围绕着包含字段分隔符或记录分隔符的结果放置的限定符字符串。</span><span class="sxs-lookup"><span data-stu-id="29c1e-128">The qualifier string to put around results that contain the field delimiter or record delimiter.</span></span> <span data-ttu-id="29c1e-129">如果结果包含限定符，将重复此限定符。</span><span class="sxs-lookup"><span data-stu-id="29c1e-129">If the results contain the qualifier, the qualifier is repeated.</span></span> <span data-ttu-id="29c1e-130">`Qualifier` 设置必须与 `FieldDelimiter` 和 `RecordDelimiter` 设置不同。</span><span class="sxs-lookup"><span data-stu-id="29c1e-130">The `Qualifier` setting must be different from the `FieldDelimiter` and `RecordDelimiter` settings.</span></span> <span data-ttu-id="29c1e-131">默认值为引号 (")。</span><span class="sxs-lookup"><span data-stu-id="29c1e-131">The default value is a quotation mark (").</span></span>|  
|`RecordDelimiter`|<span data-ttu-id="29c1e-132">要放在每个记录末尾的记录分隔符。</span><span class="sxs-lookup"><span data-stu-id="29c1e-132">The record delimiter to put at the end of each record.</span></span> <span data-ttu-id="29c1e-133">默认值为 \<cr>\<lf>。</span><span class="sxs-lookup"><span data-stu-id="29c1e-133">The default value is \<cr>\<lf>.</span></span>|  
|<span data-ttu-id="29c1e-134">**SuppressLineBreaks**</span><span class="sxs-lookup"><span data-stu-id="29c1e-134">**SuppressLineBreaks**</span></span>|<span data-ttu-id="29c1e-135">指示是否在输出中包含从数据删除的换行符。</span><span class="sxs-lookup"><span data-stu-id="29c1e-135">Indicates whether line breaks are removed from the data included in the output.</span></span> <span data-ttu-id="29c1e-136">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="29c1e-136">The default value is `false`.</span></span> <span data-ttu-id="29c1e-137">如果值为 `true`，则 `FieldDelimiter`、`RecordDelimiter` 和 `Qualifier` 设置不能为空格字符。</span><span class="sxs-lookup"><span data-stu-id="29c1e-137">If the value is `true`, the `FieldDelimiter`, `RecordDelimiter`, and `Qualifier` settings cannot be a space character.</span></span>|  
|`UseFormattedValues`|<span data-ttu-id="29c1e-138">指示是否将格式化的字符串放入 CSV 输出中。</span><span class="sxs-lookup"><span data-stu-id="29c1e-138">Indicates whether formatted strings are put into the CSV output.</span></span> <span data-ttu-id="29c1e-139">默认值为 `true`（当 `ExcelMode` 为 `true` 时），否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="29c1e-139">The default value is `true` when `ExcelMode` is `true`; otherwise it is `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29c1e-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29c1e-140">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="29c1e-141">[将设备信息设置传递给呈现扩展插件](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="29c1e-141">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="29c1e-142">[在 RSReportServer.Config中自定义呈现扩展插件参数](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="29c1e-142">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="29c1e-143">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="29c1e-143">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  