---
title: ) XMLA (处理错误和警告 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- inline errors [XMLA]
- SOAP faults [XML for Analysis]
- XML for Analysis, errors
- faults [XML for Analysis]
- messages [XML for Analysis]
- XMLA, errors
- warnings [XML for Analysis]
- inline warnings [XMLA]
ms.assetid: ab895282-098d-468e-9460-032598961f45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07b88d800237e5b4b06af0c1ff11cbd0af846600
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580968"
---
# <a name="handling-errors-and-warnings-xmla"></a><span data-ttu-id="7d7b6-102">处理错误和警告 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="7d7b6-102">Handling Errors and Warnings (XMLA)</span></span>
  <span data-ttu-id="7d7b6-103">如果 XML for Analysis (XMLA) [发现](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)或[执行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法调用未运行、运行成功但生成了错误或警告，或成功运行，但返回的结果包含错误，则需要进行错误处理。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-103">Error handling is required when an XML for Analysis (XMLA) [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) or [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method call does not run, runs successfully but generates errors or warnings, or runs successfully but returns results that contain errors.</span></span>  
  
|<span data-ttu-id="7d7b6-104">错误</span><span class="sxs-lookup"><span data-stu-id="7d7b6-104">Error</span></span>|<span data-ttu-id="7d7b6-105">报告</span><span class="sxs-lookup"><span data-stu-id="7d7b6-105">Reporting</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="7d7b6-106">XMLA 方法调用不能运行</span><span class="sxs-lookup"><span data-stu-id="7d7b6-106">The XMLA method call does not run</span></span>|[!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="7d7b6-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 返回包含失败详细信息的 SOAP 错误消息。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns a SOAP fault message that contains the details of the failure.</span></span><br /><br /> <span data-ttu-id="7d7b6-108">有关详细信息，请参阅[处理 SOAP 错误](#handling_soap_faults)一节。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-108">For more information, see the section, [Handling SOAP Faults](#handling_soap_faults).</span></span>|  
|<span data-ttu-id="7d7b6-109">方法调用运行成功，但生成了错误或警告</span><span class="sxs-lookup"><span data-stu-id="7d7b6-109">Errors or warnings on a successful method call</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="7d7b6-110">在包含方法调用结果的[root](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)元素的[Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)属性中，分别为每个错误或警告分别包含[错误](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)或[警告](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla)元素。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-110">includes an [error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) or [warning](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) element for each error or warning, respectively, in the [Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) property of the [root](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) element that contains the results of the method call.</span></span><br /><br /> <span data-ttu-id="7d7b6-111">有关详细信息，请参阅[处理错误和警告](#handling_errors_and_warnings)一节。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-111">For more information, see the section, [Handling Errors and Warnings](#handling_errors_and_warnings).</span></span>|  
|<span data-ttu-id="7d7b6-112">方法调用运行成功，但结果中包含错误</span><span class="sxs-lookup"><span data-stu-id="7d7b6-112">Errors in the result for a successful method call</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="7d7b6-113">`error` `warning` 在方法调用结果的相应[单元格或](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)[行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla)元素中，分别包含错误或警告的内联或元素。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-113">includes an inline `error` or `warning` element for the error or warning, respectively, within the appropriate [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) or [row](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) element of the results of the method call.</span></span><br /><br /> <span data-ttu-id="7d7b6-114">有关详细信息，请参阅[处理内联错误和警告](#handling_inline_errors_and_warnings)一节。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-114">For more information, see the section, [Handling Inline Errors and Warnings](#handling_inline_errors_and_warnings).</span></span>|  
  
##  <a name="handling-soap-faults"></a><a name="handling_soap_faults"></a><span data-ttu-id="7d7b6-115">处理 SOAP 错误</span><span class="sxs-lookup"><span data-stu-id="7d7b6-115">Handling SOAP Faults</span></span>  
 <span data-ttu-id="7d7b6-116">出现以下情况时，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会返回 SOAP 错误：</span><span class="sxs-lookup"><span data-stu-id="7d7b6-116">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns a SOAP fault when the following situations occur:</span></span>  
  
-   <span data-ttu-id="7d7b6-117">包含 XMLA 方法的 SOAP 消息格式不正确，或者无法由 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例验证。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-117">The SOAP message that contains the XMLA method was not well-formed or could not be validated by the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="7d7b6-118">出现与包含 XMLA 方法的 SOAP 消息有关的通信错误或其他错误。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-118">A communications or other error occurred involving the SOAP message that contains the XMLA method.</span></span>  
  
-   <span data-ttu-id="7d7b6-119">XMLA 方法未在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上运行。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-119">The XMLA method did not run on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="7d7b6-120">XMLstartA 的 SOAP 错误代码以“XMLForAnalysis”开头，后跟一个句号和十六进制的 HRESULT 结果代码。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-120">The SOAP fault codes for XMLstartA start with "XMLForAnalysis", followed by a period and the hexadecimal HRESULT result code.</span></span> <span data-ttu-id="7d7b6-121">例如，错误代码“`0x80000005`”的格式为“`XMLForAnalysis.0x80000005`”。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-121">For example, an error code of "`0x80000005`" is formatted as "`XMLForAnalysis.0x80000005`".</span></span> <span data-ttu-id="7d7b6-122">有关 SOAP 错误格式的详细信息，请参阅“W3C 简单对象访问协议 (SOAP) 1.1. 中的 SOAP 错误”。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-122">For more information about the SOAP fault format, see Soap Fault in the W3C Simple Object Access Protocol (SOAP) 1.1.</span></span>  
  
### <a name="fault-code-information"></a><span data-ttu-id="7d7b6-123">错误代码信息</span><span class="sxs-lookup"><span data-stu-id="7d7b6-123">Fault Code Information</span></span>  
 <span data-ttu-id="7d7b6-124">下表显示了 SOAP 响应详细信息部分包含的 XMLA 错误代码信息。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-124">The following table shows the XMLA fault code information that is contained in the detail section of the SOAP response.</span></span> <span data-ttu-id="7d7b6-125">这些列为 SOAP 错误详细信息部分中所包含的错误的属性。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-125">The columns are the attributes of an error in the detail section of a SOAP fault.</span></span>  
  
|<span data-ttu-id="7d7b6-126">列名称</span><span class="sxs-lookup"><span data-stu-id="7d7b6-126">Column name</span></span>|<span data-ttu-id="7d7b6-127">类型</span><span class="sxs-lookup"><span data-stu-id="7d7b6-127">Type</span></span>|<span data-ttu-id="7d7b6-128">说明</span><span class="sxs-lookup"><span data-stu-id="7d7b6-128">Description</span></span>|<span data-ttu-id="7d7b6-129">允许为 Null<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="7d7b6-129">Null allowed<sup>1</sup></span></span>|  
|-----------------|----------|-----------------|------------------------------|  
|`ErrorCode`|`UnsignedInt`|<span data-ttu-id="7d7b6-130">指示方法是成功还是失败的返回代码。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-130">Return code that indicates the success or failure of the method.</span></span> <span data-ttu-id="7d7b6-131">十六进制值必须转换为 `UnsignedInt` 值。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-131">The hexadecimal value must be converted to an `UnsignedInt` value.</span></span>|<span data-ttu-id="7d7b6-132">否</span><span class="sxs-lookup"><span data-stu-id="7d7b6-132">No</span></span>|  
|`WarningCode`|`UnsignedInt`|<span data-ttu-id="7d7b6-133">指示警告条件的返回代码。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-133">Return code that indicates a warning condition.</span></span> <span data-ttu-id="7d7b6-134">十六进制值必须转换为 `UnsignedInt` 值。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-134">The hexadecimal value must be converted to an `UnsignedInt` value.</span></span>|<span data-ttu-id="7d7b6-135">是</span><span class="sxs-lookup"><span data-stu-id="7d7b6-135">Yes</span></span>|  
|`Description`|`String`|<span data-ttu-id="7d7b6-136">由生成错误的组件返回的错误或警告的文本和说明。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-136">Error or warning text and description returned by the component that generated the error.</span></span>|<span data-ttu-id="7d7b6-137">是</span><span class="sxs-lookup"><span data-stu-id="7d7b6-137">Yes</span></span>|  
|`Source`|`String`|<span data-ttu-id="7d7b6-138">生成错误或警告的组件的名称。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-138">Name of the component that generated the error or warning.</span></span>|<span data-ttu-id="7d7b6-139">是</span><span class="sxs-lookup"><span data-stu-id="7d7b6-139">Yes</span></span>|  
|`HelpFile`|`String`|<span data-ttu-id="7d7b6-140">指向介绍错误或警告的“帮助”文件或主题的路径或 URL。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-140">Path or URL to the Help file or topic that describes the error or warning.</span></span>|<span data-ttu-id="7d7b6-141">是</span><span class="sxs-lookup"><span data-stu-id="7d7b6-141">Yes</span></span>|  
  
 <span data-ttu-id="7d7b6-142"><sup>1</sup>指示数据是否是必需的并且必须返回，或者数据是否是可选的，如果列不适用，则允许为空字符串。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-142"><sup>1</sup> Indicates whether the data is required and must be returned, or whether the data is optional and a null string is allowed if the column does not apply.</span></span>  
  
 <span data-ttu-id="7d7b6-143">下面列出了一个由于方法调用失败而出现的 SOAP 错误示例：</span><span class="sxs-lookup"><span data-stu-id="7d7b6-143">The following is an example of a SOAP fault that occurred when a method call failed:</span></span>  
  
```  
<?xml version="1.0"?>  
   <SOAP-ENV:Envelope  
   xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
   SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
      <SOAP-ENV:Fault>  
         <faultcode>XMLAnalysisError.0x80000005</faultcode>  
         <faultstring>The XML for Analysis provider encountered an error.</faultstring>  
         <faultactor>XML for Analysis Provider</faultactor>  
         <detail>  
<Error  
ErrorCode="2147483653"  
Description="An unexpected error has occurred."  
Source="XML for Analysis Provider"  
HelpFile="" />  
         </detail>  
      </SOAP-ENV:Fault>  
</SOAP-ENV:Envelope>  
```  
  
##  <a name="handling-errors-and-warnings"></a><a name="handling_errors_and_warnings"></a><span data-ttu-id="7d7b6-144">处理错误和警告</span><span class="sxs-lookup"><span data-stu-id="7d7b6-144">Handling Errors and Warnings</span></span>  
 <span data-ttu-id="7d7b6-145">如果运行某命令后出现以下情况，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会在该命令的 `Messages` 元素中返回 `root` 属性：</span><span class="sxs-lookup"><span data-stu-id="7d7b6-145">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns the `Messages` property in the `root` element for a command if the following situations occur after that command runs:</span></span>  
  
-   <span data-ttu-id="7d7b6-146">该方法本身没有失败，但在该方法调用成功后，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上出现了错误。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-146">The method itself did not fail, but a failure occurred on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance after the method call succeeded.</span></span>  
  
-   <span data-ttu-id="7d7b6-147"> 实例在该命令成功后返回一个警告。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-147">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance returns a warning when the command is successful.</span></span>  
  
 <span data-ttu-id="7d7b6-148"> 属性出现在  元素中包含的所有其他属性之后，该属性可包含一个或多个  元素。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-148">The `Messages` property follows all other properties that are contained by the `root` element, and can contain one or more `Message` elements.</span></span> <span data-ttu-id="7d7b6-149">而每个 `Message` 元素又可以包含一个 `error` 或 `warning` 元素，这些元素分别描述了指定命令产生的所有错误或警告。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-149">In turn, each `Message` element can contain either a single `error` or `warning` element describing any errors or warnings, respectively, that occurred for the specified command.</span></span>  
  
 <span data-ttu-id="7d7b6-150">有关属性中包含的错误和警告的详细信息 `Messages` ，请参阅[Messages 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-150">For more information about errors and warnings that are contained in the `Messages` property, see [Messages Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla).</span></span>  
  
### <a name="handling-errors-during-serialization"></a><span data-ttu-id="7d7b6-151">处理序列化期间发生的错误</span><span class="sxs-lookup"><span data-stu-id="7d7b6-151">Handling Errors During Serialization</span></span>  
 <span data-ttu-id="7d7b6-152">如果在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例已经开始序列化已成功运行命令的输出后发生错误，则会在错误发生时 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 返回不同命名空间中的[异常](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla)元素。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-152">If an error occurs after the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance has already begun serializing the output of a successfully run command, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an [Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) element in a different namespace at the point of the error.</span></span> <span data-ttu-id="7d7b6-153"> 实例随后会关闭所有已打开的元素，以确保发送到客户端的 XML 文档为有效文档。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-153">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance then closes all open elements so that the XML document sent to the client is a valid document.</span></span> <span data-ttu-id="7d7b6-154">该实例还会返回包含错误说明的 `Messages` 元素。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-154">The instance also returns a `Messages` element that contains the description of the error.</span></span>  
  
##  <a name="handling-inline-errors-and-warnings"></a><a name="handling_inline_errors_and_warnings"></a><span data-ttu-id="7d7b6-155">处理内联错误和警告</span><span class="sxs-lookup"><span data-stu-id="7d7b6-155">Handling Inline Errors and Warnings</span></span>  
 <span data-ttu-id="7d7b6-156">如果 XMLA 方法本身没有失败，但在 XMLA 方法调用成功后，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上出现了特定于该方法返回结果中的数据元素的错误，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会为命令返回内联 `error` 或 `warning`。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-156">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an inline `error` or `warning` for a command if the XMLA method itself did not fail, but an error specific to a data element in the results returned by the method occurred on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance after the XMLA method call succeeded.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="7d7b6-157">`error` `warning` 如果出现特定于单元格的问题或对使用 MDDataSet 数据类型的元素中包含的其他数据的问题（ `root` 如单元的安全性错误或格式设置错误）， [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla)则提供内联和元素。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-157">supplies inline `error` and `warning` elements if issues specific to a cell or to other data that are contained within a `root` element using the [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) data type occur, such as a security error or formatting error for a cell.</span></span> <span data-ttu-id="7d7b6-158">在这类情况下，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会在包含错误或警告的 `error` 或 `warning` 元素中返回 `Cell` 或 `row` 元素。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-158">In these cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an `error` or `warning` element in the `Cell` or `row` element that contains the error or warning, respectively.</span></span>  
  
 <span data-ttu-id="7d7b6-159">下面的示例说明了一个结果集，该结果集在 `Execute` 使用[语句](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)命令从方法返回的行集中包含错误。</span><span class="sxs-lookup"><span data-stu-id="7d7b6-159">The following example illustrates a result set that contains an error in the rowset returned from an `Execute` method using the [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command.</span></span>  
  
```  
<return>  
   ...  
   <root>  
      ...  
      <CellData>  
      ...  
         <Cell CellOrdinal="10">  
            <Value>  
               <Error>  
                  <ErrorCode>2148497527</ErrorCode>   
                  <Description>Security Error.</Description>   
               </Error>  
            </Value>  
         </Cell>  
      </CellData>  
      ...  
   </root>  
   ...  
</return>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d7b6-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d7b6-160">See Also</span></span>  
 [<span data-ttu-id="7d7b6-161">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="7d7b6-161">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
