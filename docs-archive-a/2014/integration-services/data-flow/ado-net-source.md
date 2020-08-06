---
title: ADO NET 源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.f1
helpviewer_keywords:
- ADO.NET source
- sources [Integration Services], ADO.NET
- sources [Integration Services], DataReader
- .NET Framework [Integration Services]
- DataReader source
ms.assetid: 2a2f1750-2cda-4dda-9dca-623a96a6b3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb50a6171ed29fc5328663d8ce9992e0462e02f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692467"
---
# <a name="ado-net-source"></a><span data-ttu-id="be903-102">ADO NET 源</span><span class="sxs-lookup"><span data-stu-id="be903-102">ADO NET Source</span></span>
  <span data-ttu-id="be903-103">ADO NET 源使用来自 .NET 提供程序的数据，并使这些数据对数据流可用。</span><span class="sxs-lookup"><span data-stu-id="be903-103">The ADO NET source consumes data from a .NET provider and makes the data available to the data flow.</span></span>  
  
 <span data-ttu-id="be903-104">可使用 ADO NET 源连接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="be903-104">You can use the ADO NET source to connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="be903-105">不支持使用 OLE DB 连接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="be903-105">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span> <span data-ttu-id="be903-106">有关 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 的详细信息，请参阅[通用指导原则和限制（Azure SQL 数据库）](https://go.microsoft.com/fwlink/?LinkId=248228)。</span><span class="sxs-lookup"><span data-stu-id="be903-106">For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see [General Guidelines and Limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="be903-107">数据类型支持</span><span class="sxs-lookup"><span data-stu-id="be903-107">Data Type Support</span></span>  
 <span data-ttu-id="be903-108">源会将未映射到特定 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型的任意数据类型转换为 DT_NTEXT [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="be903-108">The source converts any data type that does not map to a specific [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to the DT_NTEXT [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="be903-109">即使数据类型为 `System.Object`，也会发生此转换。</span><span class="sxs-lookup"><span data-stu-id="be903-109">This conversion occurs even if the data type is `System.Object`.</span></span>  
  
 <span data-ttu-id="be903-110">可以将 DT_NTEXT 数据类型更改为 DT_WSTR 数据类型，也可以将 DT_WSTR 更改为 DT_NTEXT。</span><span class="sxs-lookup"><span data-stu-id="be903-110">You can change the DT_NTEXT data type to the DT_WSTR data type, or the change DT_WSTR to DT_NTEXT.</span></span> <span data-ttu-id="be903-111">通过在 ADO NET 源的 **“高级编辑器”** 对话框中设置 **DataType** 属性可更改数据类型。</span><span class="sxs-lookup"><span data-stu-id="be903-111">You change data types by setting the **DataType** property in the **Advanced Editor** dialog box of the ADO NET source.</span></span> <span data-ttu-id="be903-112">有关详细信息，请参阅 [Common Properties](../common-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="be903-112">For more information, see [Common Properties](../common-properties.md).</span></span>  
  
 <span data-ttu-id="be903-113">通过在 ADO NET 源之后使用数据转换，还可以将 DT_NTEXT 数据类型转换为 DT_BYTES 或 DT_STR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="be903-113">The DT_NTEXT data type can also be converted to the DT_BYTES or DT_STR data type by using a Data Conversion transformation after the ADO NET source.</span></span> <span data-ttu-id="be903-114">有关详细信息，请参阅 [Data Conversion Transformation](transformations/data-conversion-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="be903-114">For more information, see [Data Conversion Transformation](transformations/data-conversion-transformation.md).</span></span>  
  
 <span data-ttu-id="be903-115">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中，日期数据类型 DT_DBDATE、DT_DBTIME2、DT_DBTIMESTAMP2 和 DT_DBTIMESTAMPOFFSET 映射到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的某些日期数据类型。</span><span class="sxs-lookup"><span data-stu-id="be903-115">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the date data types, DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET, map to certain date data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="be903-116">您可以配置 ADO NET 源，从而将日期数据类型从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的数据类型转换为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 使用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="be903-116">You can configure the ADO NET source to convert the date data types from those that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to those that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses.</span></span> <span data-ttu-id="be903-117">若要配置 ADO NET 源以便转换这些日期数据类型，请将 **连接管理器的** Type System Version [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 属性设置为 **Latest**。</span><span class="sxs-lookup"><span data-stu-id="be903-117">To configure the ADO NET source to convert these date data types, set the **Type System Version** property of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to **Latest**.</span></span> <span data-ttu-id="be903-118">（**Type System Version** 属性位于“连接管理器”  对话框的“全部”  页。</span><span class="sxs-lookup"><span data-stu-id="be903-118">(The **Type System Version** property is on the **All** page of the **Connection Manager** dialog box.</span></span> <span data-ttu-id="be903-119">若要打开“连接管理器”  对话框，请右键单击 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器，然后单击“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="be903-119">To open the **Connection Manager** dialog box, right-click the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager, and then click **Edit**.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be903-120">如果将 **连接管理器的** Type System Version [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 属性设置为 **SQL Server 2005**，则系统会将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期数据类型转换为 DT_WSTR。</span><span class="sxs-lookup"><span data-stu-id="be903-120">If the **Type System Version** property for the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager is set to **SQL Server 2005**, the system converts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types to DT_WSTR.</span></span>  
  
 <span data-ttu-id="be903-121">当 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 连接管理器将提供程序指定为 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 时，系统会将用户定义的数据类型 (UDT) 转换为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 二进制大型对象 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="be903-121">The system converts user-defined data types (UDTs) to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] binary large objects (BLOB) when the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager specifies the provider as the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient).</span></span> <span data-ttu-id="be903-122">当系统转换 UDT 数据类型时会应用下列规则：</span><span class="sxs-lookup"><span data-stu-id="be903-122">The system applies the following rules when it converts the UDT data type:</span></span>  
  
-   <span data-ttu-id="be903-123">如果数据是非大型 UDT，系统会将该数据转换为 DT_BYTES。</span><span class="sxs-lookup"><span data-stu-id="be903-123">If the data is a non-large UDT, the system converts the data to DT_BYTES.</span></span>  
  
-   <span data-ttu-id="be903-124">如果数据是非大型 UDT，并且数据库中列的 **Length** 属性设置为 -1 或大于 8,000 个字节的值，则系统会将该数据转换为 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="be903-124">If the data is a non-large UDT, and the **Length** property of the column on the database is set to -1 or a value greater than 8,000 bytes, the system converts the data to DT_IMAGE.</span></span>  
  
-   <span data-ttu-id="be903-125">如果数据是大型 UDT，系统会将该数据转换为 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="be903-125">If the data is a large UDT, the system converts the data to DT_IMAGE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be903-126">如果 ADO NET 源未配置为使用错误输出，则系统会以 8,000 个字节为单位成块地使数据流向 DT_IMAGE 列。</span><span class="sxs-lookup"><span data-stu-id="be903-126">If the ADO NET source is not configured to use error output, the system streams the data to the DT_IMAGE column in chunks of 8,000 bytes.</span></span> <span data-ttu-id="be903-127">如果 ADO NET 源配置为使用错误输出，则系统会将整个字节数组传递到 DT_IMAGE 列。</span><span class="sxs-lookup"><span data-stu-id="be903-127">If the ADO NET source is configured to use error output, the system passes the whole array of bytes to the DT_IMAGE column.</span></span> <span data-ttu-id="be903-128">有关如何将组件配置为使用错误输出的详细信息，请参阅 [数据中的错误处理](error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="be903-128">For more information about how to configure components to use error output, see [Error Handling in Data](error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="be903-129">有关 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型、支持的数据类型转换以及某些数据库（包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]）之间的数据类型映射的详细信息，请参阅 [Integration Services 数据类型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="be903-129">For more information about the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, supported data type conversions, and data type mapping across certain databases including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="be903-130">有关将 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型映射为托管数据类型的详细信息，请参阅 [在数据流中使用数据类型](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="be903-130">For information about mapping [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types to managed data types, see [Working with Data Types in the Data Flow](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md).</span></span>  
  
## <a name="ado-net-source-troubleshooting"></a><span data-ttu-id="be903-131">ADO NET 源故障排除</span><span class="sxs-lookup"><span data-stu-id="be903-131">ADO NET Source Troubleshooting</span></span>  
 <span data-ttu-id="be903-132">可以记录 ADO NET 源对外部数据访问接口所做的调用。</span><span class="sxs-lookup"><span data-stu-id="be903-132">You can log the calls that the ADO NET source makes to external data providers.</span></span> <span data-ttu-id="be903-133">利用此日志记录功能，可以对 ADO NET 源执行的从外部数据源加载数据的操作进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="be903-133">You can use this logging capability to troubleshoot the loading of data from external data sources that the ADO NET source performs.</span></span> <span data-ttu-id="be903-134">若要记录 ADO NET 源对外部数据访问接口所做的调用，请在包级别启用包日志记录并选择 **“诊断”** 事件。</span><span class="sxs-lookup"><span data-stu-id="be903-134">To log the calls that the ADO NET source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="be903-135">有关详细信息，请参阅 [包执行的疑难解答工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="be903-135">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="ado-net-source-configuration"></a><span data-ttu-id="be903-136">ADO NET 源配置</span><span class="sxs-lookup"><span data-stu-id="be903-136">ADO NET Source Configuration</span></span>  
 <span data-ttu-id="be903-137">通过提供定义结果集的 SQL 语句可以配置 ADO NET 源。</span><span class="sxs-lookup"><span data-stu-id="be903-137">You configure the ADO NET source by providing the SQL statement that defines the result set.</span></span> <span data-ttu-id="be903-138">例如，连接到 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 数据库并使用 SQL 语句 `SELECT * FROM Production.Product` 的 ADO NET 源可从 **Production.Product** 表提取所有行，并将数据集提供给下游组件。</span><span class="sxs-lookup"><span data-stu-id="be903-138">For example, an ADO NET source that connects to the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database and uses the SQL statement `SELECT * FROM Production.Product` extracts all the rows from the **Production.Product** table and provides the dataset to a downstream component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be903-139">在您使用 SQL 语句调用从临时表返回结果的某一存储过程时，使用 WITH RESULT SETS 选项可为结果集定义元数据。</span><span class="sxs-lookup"><span data-stu-id="be903-139">When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be903-140">如果使用 SQL 语句来执行存储过程且包因为以下错误失败，您可以通过在 exec 语句前添加 `SET FMTONLY OFF` 语句来更正错误。</span><span class="sxs-lookup"><span data-stu-id="be903-140">If you use an SQL statement to execute a stored procedure and the package fails with the following error, you may be able to resolve the error by adding the `SET FMTONLY OFF` statement before the exec statement.</span></span>  
>   
>  <span data-ttu-id="be903-141">**在数据源中找不到列 <列名>。**</span><span class="sxs-lookup"><span data-stu-id="be903-141">**Column <column_name> cannot be found at the datasource.**</span></span>  
  
 <span data-ttu-id="be903-142">ADO NET 源使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器连接到数据源，该连接管理器指定 .NET 提供程序。</span><span class="sxs-lookup"><span data-stu-id="be903-142">The ADO NET source uses an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to a data source, and the connection manager specifies the .NET provider.</span></span> <span data-ttu-id="be903-143">有关详细信息，请参阅 [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="be903-143">For more information, see [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).</span></span>  
  
 <span data-ttu-id="be903-144">ADO NET 源有一个常规输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="be903-144">The ADO NET source has one regular output and one error output.</span></span>  
  
 <span data-ttu-id="be903-145">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="be903-145">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="be903-146">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="be903-146">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="be903-147">Common Properties</span><span class="sxs-lookup"><span data-stu-id="be903-147">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="be903-148">ADO NET 自定义属性</span><span class="sxs-lookup"><span data-stu-id="be903-148">ADO NET Custom Properties</span></span>](ado-net-custom-properties.md)  
  
 <span data-ttu-id="be903-149">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="be903-149">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be903-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be903-150">See Also</span></span>  
 <span data-ttu-id="be903-151">[DataReader 目标](datareader-destination.md) </span><span class="sxs-lookup"><span data-stu-id="be903-151">[DataReader Destination](datareader-destination.md) </span></span>  
 <span data-ttu-id="be903-152">[ADO NET 目标](ado-net-destination.md) </span><span class="sxs-lookup"><span data-stu-id="be903-152">[ADO NET Destination](ado-net-destination.md) </span></span>  
 [<span data-ttu-id="be903-153">数据流</span><span class="sxs-lookup"><span data-stu-id="be903-153">Data Flow</span></span>](data-flow.md)  
  
  
