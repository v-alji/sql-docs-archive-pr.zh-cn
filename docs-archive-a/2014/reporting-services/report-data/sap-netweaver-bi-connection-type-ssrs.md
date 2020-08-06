---
title: SAP NetWeaver BI 连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f985856b-31d5-4e56-844b-8a8ee38da67e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42806e370e20257f5de9e49d4f59dd3bb7793f20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694264"
---
# <a name="sap-netweaver-bi-connection-type-ssrs"></a><span data-ttu-id="d8244-102">SAP NetWeaver BI 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="d8244-102">SAP NetWeaver BI Connection Type (SSRS)</span></span>
  <span data-ttu-id="d8244-103">若要在报表中包含来自 SAP NetWeaver® Business Intelligence 外部数据源的数据，您必须拥有一个基于 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]类型的报表数据源的数据集。</span><span class="sxs-lookup"><span data-stu-id="d8244-103">To include data from a SAP NetWeaver® Business Intelligence external data source in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].</span></span> <span data-ttu-id="d8244-104">此内置数据源类型基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].NET Framework Data Provider 1.0 的数据扩展插件。</span><span class="sxs-lookup"><span data-stu-id="d8244-104">This built-in data source type is based on the data extension for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].</span></span>  
  
 <span data-ttu-id="d8244-105">利用此数据扩展插件，可以从 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 外部数据源中定义的 InfoCubes、MultiProviders（虚拟 InfoCubes）和基于 Web 的查询中检索多维数据。</span><span class="sxs-lookup"><span data-stu-id="d8244-105">This data extension enables you to retrieve multidimensional data from InfoCubes, MultiProviders (virtual InfoCubes), and Web-enabled queries that are defined on a [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] external data source.</span></span>  
  
 <span data-ttu-id="d8244-106">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="d8244-106">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="d8244-107">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d8244-107">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="supported-versions"></a><a name="support"></a><span data-ttu-id="d8244-108">支持的版本</span><span class="sxs-lookup"><span data-stu-id="d8244-108">Supported Versions</span></span>  
 <span data-ttu-id="d8244-109">已针对 SAP BW 3.5 和 7.0 开发了数据提供程序并进行了测试。</span><span class="sxs-lookup"><span data-stu-id="d8244-109">The data provider has been developed for and tested against SAP BW 3.5 and 7.0.</span></span>  
  
-   <span data-ttu-id="d8244-110">SAP BW 3.5 和 7.0 的支持包 20</span><span class="sxs-lookup"><span data-stu-id="d8244-110">Support Package 20 for SAP BW 3.5 and 7.0</span></span>  
  
 <span data-ttu-id="d8244-111">对于 Windows 集成身份验证，已针对以下系统开发了提供程序并进行了测试。</span><span class="sxs-lookup"><span data-stu-id="d8244-111">For Windows Integrated Authentication the provider was developed for and tested against the following systems.</span></span>  
  
-   <span data-ttu-id="d8244-112">SAP 门户 6.40 支持包 20</span><span class="sxs-lookup"><span data-stu-id="d8244-112">SAP Portals 6.40 Support Package 20</span></span>  
  
-   <span data-ttu-id="d8244-113">SAP 门户7.0 支持包11</span><span class="sxs-lookup"><span data-stu-id="d8244-113">SAP Portals 7.0 Support Package 11</span></span>  
  
-   <span data-ttu-id="d8244-114">SAP Duet 1.0</span><span class="sxs-lookup"><span data-stu-id="d8244-114">SAP Duet 1.0</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="d8244-115">连接字符串</span><span class="sxs-lookup"><span data-stu-id="d8244-115">Connection String</span></span>  
 <span data-ttu-id="d8244-116">请联系数据库管理员，获取连接信息以及用于连接到数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="d8244-116">Contact the database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="d8244-117">下面的连接字符串示例指定使用端口 8000 的服务器上的 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 数据源，以及使用 SOAP 的 Internet 上的 XML for Analysis Services (XMLA)：</span><span class="sxs-lookup"><span data-stu-id="d8244-117">The following connection string example specifies an [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source on a server using port 8000 and XML for Analysis Services (XMLA) over the Internet using SOAP:</span></span>  
  
```  
DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla  
```  
  
 <span data-ttu-id="d8244-118">有关更多连接字符串的示例，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="d8244-118">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="d8244-119">凭据</span><span class="sxs-lookup"><span data-stu-id="d8244-119">Credentials</span></span>  
 <span data-ttu-id="d8244-120">执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。</span><span class="sxs-lookup"><span data-stu-id="d8244-120">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="d8244-121">报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。</span><span class="sxs-lookup"><span data-stu-id="d8244-121">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="d8244-122">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="d8244-122">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
  
##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="d8244-123">请求</span><span class="sxs-lookup"><span data-stu-id="d8244-123">Queries</span></span>  
 <span data-ttu-id="d8244-124">可以在设计模式或查询模式下使用图形查询设计器，通过浏览数据源中的基础数据结构来生成多维表达式 (MDX) 查询。</span><span class="sxs-lookup"><span data-stu-id="d8244-124">You can use the graphical query designer in Design or Query mode to build a Multidimensional Expression (MDX) query by browsing the underlying data structures on the data source.</span></span> <span data-ttu-id="d8244-125">在设计时，您可以采用交互方式从查询设计器中运行查询，以查看结果。</span><span class="sxs-lookup"><span data-stu-id="d8244-125">At design time, you can interactively run a query from the query designer to see the results.</span></span> <span data-ttu-id="d8244-126">生成的查询定义了数据集中的字段。</span><span class="sxs-lookup"><span data-stu-id="d8244-126">The query you build defines fields in the dataset.</span></span> <span data-ttu-id="d8244-127">在运行时，将从数据源返回实际数据。</span><span class="sxs-lookup"><span data-stu-id="d8244-127">At run time, the actual data is returned from the data source.</span></span> <span data-ttu-id="d8244-128">使用图形查询设计器执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d8244-128">Use the graphical query designer to perform the following actions:</span></span>  
  
-   <span data-ttu-id="d8244-129">在设计模式下，将维度、成员、成员属性和关键数字从数据源拖至“数据”窗格，以生成多维表达式 (MDX) 查询。</span><span class="sxs-lookup"><span data-stu-id="d8244-129">In Design mode, drag dimensions, members, member properties, and key figures from the data source onto a Data pane to build a Multidimensional Expression (MDX) query.</span></span> <span data-ttu-id="d8244-130">将计算成员从“计算成员”窗格拖至“数据”窗格，以定义附加数据集字段。</span><span class="sxs-lookup"><span data-stu-id="d8244-130">Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.</span></span>  
  
-   <span data-ttu-id="d8244-131">在查询模式下，将维度、成员、成员属性和关键数字拖至“查询”窗格或在“查询”窗格中直接键入 MDX 文本。</span><span class="sxs-lookup"><span data-stu-id="d8244-131">In Query mode, drag dimensions, members, member properties, and key figures onto the Query pane or type MDX text directly into the Query pane.</span></span> <span data-ttu-id="d8244-132">将计算成员从“计算成员”窗格拖至“数据”窗格，以定义附加数据集字段。</span><span class="sxs-lookup"><span data-stu-id="d8244-132">Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.</span></span>  
  
 <span data-ttu-id="d8244-133">生成查询时，查询设计器会自动向 MDX 查询添加默认属性。</span><span class="sxs-lookup"><span data-stu-id="d8244-133">As you build queries, the query designer automatically adds default properties to the MDX query.</span></span> <span data-ttu-id="d8244-134">若要包含默认属性之外的属性，必须手动修改 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="d8244-134">To include properties other than default properties, you must manually modify the MDX query.</span></span>  
  
 <span data-ttu-id="d8244-135">有关使用此查询设计器的详细信息，请参阅 [SAP NetWeaver BI 查询设计器用户界面（报表生成器）](../sap-netweaver-bi-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="d8244-135">For more information about working with this query designer, see [SAP NetWeaver BI Query Designer User Interface &#40;Report Builder&#41;](../sap-netweaver-bi-query-designer-user-interface-report-builder.md).</span></span>  
  
  
  
##  <a name="extended-field-properties"></a><a name="Extended"></a> <span data-ttu-id="d8244-136">扩展字段属性</span><span class="sxs-lookup"><span data-stu-id="d8244-136">Extended Field Properties</span></span>  
 <span data-ttu-id="d8244-137">[!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 数据源支持扩展字段属性。</span><span class="sxs-lookup"><span data-stu-id="d8244-137">The [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source supports extended field properties.</span></span> <span data-ttu-id="d8244-138">扩展字段属性是除了通过数据处理扩展插件为数据集字段定义的 `Value` 和 `IsMissing` 之外的其他属性。</span><span class="sxs-lookup"><span data-stu-id="d8244-138">Extended field properties are properties in addition to `Value` and `IsMissing` that are defined for a dataset field by the data processing extension.</span></span> <span data-ttu-id="d8244-139">扩展属性包括预定义属性和自定义属性。</span><span class="sxs-lookup"><span data-stu-id="d8244-139">Extended properties include predefined properties and custom properties.</span></span> <span data-ttu-id="d8244-140">预定义属性是对多个数据源通用的属性。</span><span class="sxs-lookup"><span data-stu-id="d8244-140">Predefined properties are properties common to multiple data sources.</span></span> <span data-ttu-id="d8244-141">自定义属性对于每个数据源都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d8244-141">Custom properties are unique to each data source.</span></span>  
  
### <a name="working-with-field-properties"></a><span data-ttu-id="d8244-142">使用字段属性</span><span class="sxs-lookup"><span data-stu-id="d8244-142">Working with Field Properties</span></span>  
 <span data-ttu-id="d8244-143">扩展字段属性不作为可拖至报表布局的项出现在“报表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="d8244-143">Extended field properties do not appear in the Report Data pane as items that you can drag onto your report layout.</span></span> <span data-ttu-id="d8244-144">不过，您可以将该属性的父字段拖至报表中，然后将默认属性由 `Value` 更改为要使用的属性。</span><span class="sxs-lookup"><span data-stu-id="d8244-144">Instead, you drag the parent field of the property onto the report and then change the default property from `Value` to the property you want to use.</span></span> <span data-ttu-id="d8244-145">例如，如果在 MDX 查询设计器中通过将一个级别从“元数据”窗格放至“查询”窗格创建了字段名“日历年/月级别 01”，则需要在表达式中使用以下语法来引用自定义扩展属性“长名称”\*\*\*\*\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="d8244-145">For example, if the field name **Calendar Year/Month Level 01** is created in an MDX query designer by dropping a level from the Metadata pane onto the Query pane, you would refer to the custom extended property **Long Name** in an expression using the following syntax:</span></span>  
  
 `=Fields!Calendar_Year_Month_Level_01("Long Name")`  
  
 <span data-ttu-id="d8244-146">当您将光标悬停在“元数据”窗格中的某个字段上时，扩展字段属性的名称便会显示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="d8244-146">The name for an extended field property appears in the ToolTip when you hover over a field in the Metadata pane.</span></span> <span data-ttu-id="d8244-147">有关可用于浏览基础数据的查询设计器的详细信息，请参阅 [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="d8244-147">For more information about the query designers you can use to explore the underlying data, see [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8244-148">仅当数据源在报表运行和为其数据集检索数据的情况下提供扩展字段属性的值时，这些值才存在。</span><span class="sxs-lookup"><span data-stu-id="d8244-148">Values exist for extended field properties only if the data source provides these values when your report runs and retrieves the data for its datasets.</span></span> <span data-ttu-id="d8244-149">然后，您可以使用下面所述的语法引用任意表达式中的这些 `Field` 属性值。</span><span class="sxs-lookup"><span data-stu-id="d8244-149">You can then refer to those `Field` property values from any expression using the syntax described below.</span></span> <span data-ttu-id="d8244-150">但是，由于这些字段特定于此数据访问接口，而不是报表定义语言的一部分，因此，对这些值所做的更改不会随报表定义一同保存。</span><span class="sxs-lookup"><span data-stu-id="d8244-150">However, because these fields are specific to this data provider and not part of the report definition language, changes that you make to these values are not saved with the report definition.</span></span>  
  
 <span data-ttu-id="d8244-151">使用以下两种语法中的一种可以在表达式中引用预定义扩展属性：</span><span class="sxs-lookup"><span data-stu-id="d8244-151">Use either of the following syntaxes to refer to predefined extended properties in an expression:</span></span>  
  
-   <span data-ttu-id="d8244-152">*Fields!FieldName.PropertyName*</span><span class="sxs-lookup"><span data-stu-id="d8244-152">*Fields!FieldName.PropertyName*</span></span>  
  
-   <span data-ttu-id="d8244-153">\*区域!FieldName ( "PropertyName" ) \*</span><span class="sxs-lookup"><span data-stu-id="d8244-153">*Fields!FieldName("PropertyName")*</span></span>  
  
 <span data-ttu-id="d8244-154">可以使用以下语法在表达式中引用自定义扩展属性：</span><span class="sxs-lookup"><span data-stu-id="d8244-154">Use the following syntax to refer to custom extended properties in an expression:</span></span>  
  
-   <span data-ttu-id="d8244-155">\*区域!FieldName ( "PropertyName" ) \*</span><span class="sxs-lookup"><span data-stu-id="d8244-155">*Fields!FieldName("PropertyName")*</span></span>  
  
  
  
### <a name="predefined-field-properties"></a><span data-ttu-id="d8244-156">预定义的字段属性</span><span class="sxs-lookup"><span data-stu-id="d8244-156">Predefined Field Properties</span></span>  
 <span data-ttu-id="d8244-157">下表提供了可以用于 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 数据源的预定义字段属性的列表。</span><span class="sxs-lookup"><span data-stu-id="d8244-157">The following table provides a list of predefined field properties that you can use for an [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source.</span></span>  
  
|<span data-ttu-id="d8244-158">**Property**</span><span class="sxs-lookup"><span data-stu-id="d8244-158">**Property**</span></span>|<span data-ttu-id="d8244-159">**Type**</span><span class="sxs-lookup"><span data-stu-id="d8244-159">**Type**</span></span>|<span data-ttu-id="d8244-160">**说明或所需的值**</span><span class="sxs-lookup"><span data-stu-id="d8244-160">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|<span data-ttu-id="d8244-161">指定字段的数据值。</span><span class="sxs-lookup"><span data-stu-id="d8244-161">Specifies the data value of the field.</span></span>|  
|`IsMissing`|`Boolean`|<span data-ttu-id="d8244-162">指示是否在结果数据集中找到了该字段。</span><span class="sxs-lookup"><span data-stu-id="d8244-162">Indicates whether the field was found in the resulting data set.</span></span>|  
|`FormattedValue`|`String`|<span data-ttu-id="d8244-163">返回关键数字的格式值。</span><span class="sxs-lookup"><span data-stu-id="d8244-163">Returns a formatted value for a key figure.</span></span>|  
|`BackgroundColor`|`String`|<span data-ttu-id="d8244-164">返回数据库中为该字段定义的背景颜色。</span><span class="sxs-lookup"><span data-stu-id="d8244-164">Returns the background color defined in the database for the field.</span></span>|  
|`Color`|`String`|<span data-ttu-id="d8244-165">返回数据库中为该项定义的前景色。</span><span class="sxs-lookup"><span data-stu-id="d8244-165">Returns the foreground color defined in the database for the item.</span></span>|  
|`Key`|`Object`|<span data-ttu-id="d8244-166">返回级别的键。</span><span class="sxs-lookup"><span data-stu-id="d8244-166">Returns the key for a level.</span></span>|  
|`LevelNumber`|`Integer`|<span data-ttu-id="d8244-167">针对父子层次结构返回级别号或维度编号。</span><span class="sxs-lookup"><span data-stu-id="d8244-167">For parent-child hierarchies, returns the level or dimension number.</span></span>|  
|`ParentUniqueName`|`String`|<span data-ttu-id="d8244-168">针对父子层次结构返回父级的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="d8244-168">For parent-child hierarchies, returns a fully qualified name of the parent level.</span></span>|  
|`UniqueName`|`String`|<span data-ttu-id="d8244-169">返回级别的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="d8244-169">Returns the fully qualified name of a level.</span></span> <span data-ttu-id="d8244-170">例如，雇员的 `UniqueName` 值可能是 *[0D_Company]. [10D_Department]。[11]*。</span><span class="sxs-lookup"><span data-stu-id="d8244-170">For example, the `UniqueName` value for an employee might be *[0D_Company].[10D_Department].[11]*.</span></span>|  
  
 <span data-ttu-id="d8244-171">有关在表达式中使用字段和字段属性的详细信息，请参阅[表达式中的内置集合（报表生成器和 SSRS）](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="d8244-171">For more information about using fields and field properties in an expression, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="d8244-172">注释</span><span class="sxs-lookup"><span data-stu-id="d8244-172">Remarks</span></span>  
 <span data-ttu-id="d8244-173">不是所有的报表传递模式都受到此数据访问接口的支持。</span><span class="sxs-lookup"><span data-stu-id="d8244-173">Not all report delivery modes are supported by this data provider.</span></span> <span data-ttu-id="d8244-174">此数据处理扩展插件不支持通过数据驱动订阅传递报表。</span><span class="sxs-lookup"><span data-stu-id="d8244-174">Delivering reports through data-driven subscriptions is not supported for this data processing extension.</span></span> <span data-ttu-id="d8244-175">有关详细信息，请参阅[使用外部数据源提供订阅方数据（数据驱动订阅）](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="d8244-175">For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).</span></span>  
  
 <span data-ttu-id="d8244-176">有关详细信息，请参阅 [Using SQL Server 2008 Reporting Services with SAP NetWeaver Business Intelligence](https://go.microsoft.com/fwlink/?LinkId=167352)（使用具有 SAP NetWeaver Business Intelligence 的 SQL Server 2008 Reporting Services）。</span><span class="sxs-lookup"><span data-stu-id="d8244-176">For more information, see [Using SQL Server 2008 Reporting Services with SAP NetWeaver Business Intelligence](https://go.microsoft.com/fwlink/?LinkId=167352).</span></span>  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="d8244-177">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="d8244-177">How-To Topics</span></span>  
 <span data-ttu-id="d8244-178">本节包含使用数据连接、数据源和数据集的分步说明。</span><span class="sxs-lookup"><span data-stu-id="d8244-178">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="d8244-179">添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d8244-179">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="d8244-180">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d8244-180">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="d8244-181">向数据集添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d8244-181">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="related-sections"></a><a name="Related"></a><span data-ttu-id="d8244-182">相关部分</span><span class="sxs-lookup"><span data-stu-id="d8244-182">Related Sections</span></span>  
 <span data-ttu-id="d8244-183">文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。</span><span class="sxs-lookup"><span data-stu-id="d8244-183">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="d8244-184">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d8244-184">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="d8244-185">提供访问报表数据的概述。</span><span class="sxs-lookup"><span data-stu-id="d8244-185">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="d8244-186">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="d8244-186">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="d8244-187">提供有关数据连接和数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="d8244-187">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="d8244-188">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d8244-188">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="d8244-189">提供有关嵌入数据集和共享数据集的信息。</span><span class="sxs-lookup"><span data-stu-id="d8244-189">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="d8244-190">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d8244-190">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="d8244-191">提供有关查询生成的数据集字段集合的信息。</span><span class="sxs-lookup"><span data-stu-id="d8244-191">Provides information about the dataset field collection generated by the query.</span></span>  
  
 [<span data-ttu-id="d8244-192">Reporting Services 支持的数据源 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="d8244-192">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
 <span data-ttu-id="d8244-193">提供有关每个数据扩展插件的平台和版本支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d8244-193">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="d8244-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8244-194">See Also</span></span>  
 <span data-ttu-id="d8244-195">[报表参数 &#40;报表生成器和报表设计器&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="d8244-195">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="d8244-196">[对数据进行筛选、分组和排序 &#40;报表生成器和 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d8244-196">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d8244-197">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d8244-197">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
