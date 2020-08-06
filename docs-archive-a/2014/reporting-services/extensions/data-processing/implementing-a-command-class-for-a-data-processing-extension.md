---
title: 为数据处理扩展插件实现 Command 类 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f07b9beb798b1cd33ec2fee6af890a09a516b2f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693636"
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a><span data-ttu-id="20810-102">为数据处理扩展插件实现 Command 类</span><span class="sxs-lookup"><span data-stu-id="20810-102">Implementing a Command Class for a Data Processing Extension</span></span>
  <span data-ttu-id="20810-103">Command 对象表述请求并将其传递到数据源上  。</span><span class="sxs-lookup"><span data-stu-id="20810-103">The **Command** object formulates a request and passes it on to the data source.</span></span> <span data-ttu-id="20810-104">命令文本可以采用多种不同的语法形式，包括文本和 XML。</span><span class="sxs-lookup"><span data-stu-id="20810-104">The command text can take many different syntactical forms, including text and XML.</span></span> <span data-ttu-id="20810-105">如果返回结果，则 Command 对象将结果作为 DataReader 对象返回   。</span><span class="sxs-lookup"><span data-stu-id="20810-105">If results are returned, the **Command** object returns results as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="20810-106">若要创建某一 Command 类，请实现 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>。</span><span class="sxs-lookup"><span data-stu-id="20810-106">To create a **Command** class, implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>.</span></span> <span data-ttu-id="20810-107">实现 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 方法以便将结果集作为 DataReader 对象返回  。</span><span class="sxs-lookup"><span data-stu-id="20810-107">Implement the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method to return a result set as a **DataReader** object.</span></span> <span data-ttu-id="20810-108">Command 类的 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 方法应包括采用 <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> 枚举作为参数的实现。</span><span class="sxs-lookup"><span data-stu-id="20810-108">The <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method of your **Command** class should include an implementation that takes a <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> enumeration as an argument.</span></span> <span data-ttu-id="20810-109">如果您将数据处理扩展插件部署到报表设计器，则提供在 <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> 方法中处理 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 事例的实现。</span><span class="sxs-lookup"><span data-stu-id="20810-109">If you deploy your data processing extension to Report Designer, provide an implementation that handles a <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> case in the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="20810-110">仅架构实现用于向报表设计器提供字段列表。</span><span class="sxs-lookup"><span data-stu-id="20810-110">A schema-only implementation is used to supply Report Designer with a fields list.</span></span> <span data-ttu-id="20810-111"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 方法返回的 DataReader 对象需要为结果集中的字段（或列）包含类型和名称信息。</span><span class="sxs-lookup"><span data-stu-id="20810-111">The **DataReader** object returned by the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method needs to contain type and name information for the fields, or columns, in your result set.</span></span>  
  
 <span data-ttu-id="20810-112">或者，也可以使用 Command 类来实现 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>。</span><span class="sxs-lookup"><span data-stu-id="20810-112">Optionally, your **Command** class can implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>.</span></span> <span data-ttu-id="20810-113">这一接口使实现类可以分析某一查询并返回该查询中参数的列表。</span><span class="sxs-lookup"><span data-stu-id="20810-113">This interface enables an implementing class to analyze a query and return a list of parameters in the query.</span></span> <span data-ttu-id="20810-114"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> 接口的这一功能仅用于报表设计器中。</span><span class="sxs-lookup"><span data-stu-id="20810-114">The functionality of the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> interface is only used in Report Designer.</span></span> <span data-ttu-id="20810-115">实现 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> 后，只要某一报表在预览模式下运行，就可以提示报表设计器的用户输入参数。</span><span class="sxs-lookup"><span data-stu-id="20810-115">When you implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>, you enable users of Report Designer to be prompted for parameters whenever a report is run in preview mode.</span></span> <span data-ttu-id="20810-116">此外，可以在“数据集”对话框的“参数”选项卡中查看这些参数   。</span><span class="sxs-lookup"><span data-stu-id="20810-116">In addition, you can view the parameters in the **Parameters** tab of the **Data Set** dialog.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20810-117">如果您的自定义数据处理扩展插件不支持参数，则不应实现 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>。</span><span class="sxs-lookup"><span data-stu-id="20810-117">You should not implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> if your custom data processing extension does not support parameters.</span></span>  
  
 <span data-ttu-id="20810-118">有关 Command 类实现的示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="20810-118">For a sample **Command** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20810-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20810-119">See Also</span></span>  
 <span data-ttu-id="20810-120">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="20810-120">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="20810-121">[实现数据处理扩展插件](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="20810-121">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="20810-122">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="20810-122">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
