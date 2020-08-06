---
title: 省略可选 Web 服务对象的值 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3858f73e1b332acfa1a1bbc640007f6f0884abff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688536"
---
# <a name="omitting-values-for-optional-web-service-objects"></a><span data-ttu-id="24114-102">省略可选 Web 服务对象的值</span><span class="sxs-lookup"><span data-stu-id="24114-102">Omitting Values for Optional Web Service Objects</span></span>
  <span data-ttu-id="24114-103">多个报表服务器 Web 服务复杂类型的属性具有名为“Specified”属性的伴随属性。</span><span class="sxs-lookup"><span data-stu-id="24114-103">Properties of several of the Report Server Web service complex types have an accompanying property known as the Specified property.</span></span> <span data-ttu-id="24114-104">该属性的名称由原始属性名称再加上“Specified”构成。</span><span class="sxs-lookup"><span data-stu-id="24114-104">The name of the property consists of the original property name with the word "Specified" appended to it.</span></span> <span data-ttu-id="24114-105">具有此属性则指示原始属性的值有时可以省略。</span><span class="sxs-lookup"><span data-stu-id="24114-105">The presence of this property indicates that a value for the original property may sometimes be omitted.</span></span> <span data-ttu-id="24114-106">这是从 Web 服务描述语言 (WSDL) 转换到 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 代理类的直接结果。</span><span class="sxs-lookup"><span data-stu-id="24114-106">This is a direct result of the translation from the Web Service Description Language (WSDL) to a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] proxy class.</span></span> <span data-ttu-id="24114-107">例如，复杂类型 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> 的 Web 服务属性 <xref:ReportService2010.DataSourceDefinition> 具有名为 <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> 的伴随属性。</span><span class="sxs-lookup"><span data-stu-id="24114-107">For example, the Web service property <xref:ReportService2010.DataSourceDefinition.Enabled%2A> of the complex type <xref:ReportService2010.DataSourceDefinition> has an accompanying property named <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>.</span></span> <span data-ttu-id="24114-108">如果要生成应用程序而不想设置 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> 属性的值，则不必提供 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> 的值；此时将使用 `true` 的默认值。</span><span class="sxs-lookup"><span data-stu-id="24114-108">If you are building an application and do not want to set a value for the <xref:ReportService2010.DataSourceDefinition.Enabled%2A> property, you do not have to supply a value for <xref:ReportService2010.DataSourceDefinition.Enabled%2A>; the default value of `true` is used.</span></span> <span data-ttu-id="24114-109">但是，仍然需要将 <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="24114-109">However, you still need to set <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> to `false`.</span></span> <span data-ttu-id="24114-110">如果提供了 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> 属性的值，则需要将 <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> 设置为等于 `true`。</span><span class="sxs-lookup"><span data-stu-id="24114-110">If you supply a value for the <xref:ReportService2010.DataSourceDefinition.Enabled%2A> property, you need to set <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> equal to `true`.</span></span> <span data-ttu-id="24114-111">这是对可写属性而言的。</span><span class="sxs-lookup"><span data-stu-id="24114-111">This is the case for writable properties.</span></span> <span data-ttu-id="24114-112">对于只读属性，不需要执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="24114-112">For read-only properties, you do not need to take any action.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="24114-113">未能使用上述方法指定属性可能会导致不可预知的 Web 服务行为。</span><span class="sxs-lookup"><span data-stu-id="24114-113">Failure to specify a property using the above-mentioned technique can result in unpredictable Web service behavior.</span></span>  
  
 <span data-ttu-id="24114-114">通常要求您处理其他指定属性的数据类型为 `Boolean` 、 `DateTime` 和 `Enumeration` 。</span><span class="sxs-lookup"><span data-stu-id="24114-114">The data types that usually require you to handle the additional Specified property are `Boolean`, `DateTime`, and `Enumeration`.</span></span>  
  
 <span data-ttu-id="24114-115">有关示例，请参阅 <xref:ReportService2010.ReportingService2010.CreateDataSource%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="24114-115">For an example, see <xref:ReportService2010.ReportingService2010.CreateDataSource%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24114-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24114-116">See Also</span></span>  
 <span data-ttu-id="24114-117">[使用 Web 服务和 .NET Framework 生成应用程序](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="24114-117">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="24114-118">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="24114-118">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
