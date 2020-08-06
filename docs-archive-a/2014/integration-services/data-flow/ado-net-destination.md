---
title: ADO NET 目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.f1
helpviewer_keywords:
- destinations [Integration Services], ADO.NET
- ADO.NET destination
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8289a8c91c7b78749a341cc95055562d01164866
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690011"
---
# <a name="ado-net-destination"></a><span data-ttu-id="64f7a-102">ADO NET 目标</span><span class="sxs-lookup"><span data-stu-id="64f7a-102">ADO NET Destination</span></span>
  <span data-ttu-id="64f7a-103">ADO NET 目标可将数据加载到各种使用数据库表或视图的兼容 [!INCLUDE[vstecado](../../includes/vstecado-md.md)]的数据库中。</span><span class="sxs-lookup"><span data-stu-id="64f7a-103">The ADO NET destination loads data into a variety of [!INCLUDE[vstecado](../../includes/vstecado-md.md)]-compliant databases that use a database table or view.</span></span> <span data-ttu-id="64f7a-104">你可以选择将这些数据加载到现有表或视图中，或者先创建一个新表，然后将这些数据加载到新表中。</span><span class="sxs-lookup"><span data-stu-id="64f7a-104">You have the option of loading this data into an existing table or view, or you can create a new table and load the data into the new table.</span></span>  
  
 <span data-ttu-id="64f7a-105">可使用 ADO NET 目标连接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="64f7a-105">You can use the ADO NET destination to connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="64f7a-106">不支持使用 OLE DB 连接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="64f7a-106">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span> <span data-ttu-id="64f7a-107">有关 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 的详细信息，请参阅[通用指导原则和限制（Azure SQL 数据库）](https://go.microsoft.com/fwlink/?LinkId=248228)。</span><span class="sxs-lookup"><span data-stu-id="64f7a-107">For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see [General Guidelines and Limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span></span>  
  
## <a name="troubleshooting-the-ado-net-destination"></a><span data-ttu-id="64f7a-108">ADO NET 目标故障排除</span><span class="sxs-lookup"><span data-stu-id="64f7a-108">Troubleshooting the ADO NET Destination</span></span>  
 <span data-ttu-id="64f7a-109">可以记录 ADO NET 目标对外部数据访问接口所做的调用。</span><span class="sxs-lookup"><span data-stu-id="64f7a-109">You can log the calls that the ADO NET destination makes to external data providers.</span></span> <span data-ttu-id="64f7a-110">利用此日志记录功能，可以排除 ADO NET 目标执行将数据保存到外部数据源的操作过程中发生的故障。</span><span class="sxs-lookup"><span data-stu-id="64f7a-110">You can use this logging capability to troubleshoot the saving of data to external data sources that the ADO NET destination performs.</span></span> <span data-ttu-id="64f7a-111">若要记录 ADO NET 目标对外部数据访问接口所做的调用，请在包级别启用包日志记录并选择 **“诊断”** 事件。</span><span class="sxs-lookup"><span data-stu-id="64f7a-111">To log the calls that the ADO NET destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="64f7a-112">有关详细信息，请参阅 [包执行的疑难解答工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="64f7a-112">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ado-net-destination"></a><span data-ttu-id="64f7a-113">配置 ADO NET 目标</span><span class="sxs-lookup"><span data-stu-id="64f7a-113">Configuring the ADO NET Destination</span></span>  
 <span data-ttu-id="64f7a-114">此目标使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器连接到数据源，并且此连接管理器可指定要使用的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 访问接口。</span><span class="sxs-lookup"><span data-stu-id="64f7a-114">This destination uses an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to a data source and the connection manager specifies the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider to use.</span></span> <span data-ttu-id="64f7a-115">有关详细信息，请参阅 [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="64f7a-115">For more information, see [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).</span></span>  
  
 <span data-ttu-id="64f7a-116">ADO NET 目标包括输入列和目标数据源中的列之间的映射。</span><span class="sxs-lookup"><span data-stu-id="64f7a-116">An ADO NET destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="64f7a-117">不必将输入列映射到所有目标列。</span><span class="sxs-lookup"><span data-stu-id="64f7a-117">You do not have to map input columns to all destination columns.</span></span> <span data-ttu-id="64f7a-118">但是，某些目标列的属性可能需要输入列的映射。</span><span class="sxs-lookup"><span data-stu-id="64f7a-118">However, the properties of some destination columns can require the mapping of input columns.</span></span> <span data-ttu-id="64f7a-119">否则，可能会发生错误。</span><span class="sxs-lookup"><span data-stu-id="64f7a-119">Otherwise, errors might occur.</span></span> <span data-ttu-id="64f7a-120">例如，如果目标列不允许出现空值，则必须将输入列映射到该目标列。</span><span class="sxs-lookup"><span data-stu-id="64f7a-120">For example, if a destination column does not allow for null values, you must map an input column to that destination column.</span></span> <span data-ttu-id="64f7a-121">另外，映射的列的数据类型必须是兼容的。</span><span class="sxs-lookup"><span data-stu-id="64f7a-121">In addition, the data types of mapped columns must be compatible.</span></span> <span data-ttu-id="64f7a-122">例如，如果 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 访问接口不支持将数据类型为字符串的输入列映射到数据类型为数值的目标列，则不能进行此映射。</span><span class="sxs-lookup"><span data-stu-id="64f7a-122">For example, you cannot map an input column with a string data type to a destination column with a numeric data type if the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider does not support this mapping.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="64f7a-123">不支持将文本插入到数据类型设置为图像的列中。</span><span class="sxs-lookup"><span data-stu-id="64f7a-123">does not support inserting text into columns whose data type is set to image.</span></span> <span data-ttu-id="64f7a-124">有关值数据类型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的详细信息，请参阅 [数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="64f7a-124">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64f7a-125">ADO NET 目标不支持将数据类型设置为 DT_DBTIME 的输入列映射到数据类型设置为 datetime 的数据库列。</span><span class="sxs-lookup"><span data-stu-id="64f7a-125">The ADO NET destination does not support mapping an input column whose type is set to DT_DBTIME to a database column whose type is set to datetime.</span></span> <span data-ttu-id="64f7a-126">有关 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型的详细信息，请参阅 [Integration Services 数据类型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="64f7a-126">For more information about [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="64f7a-127">ADO NET 目标具有一个常规输入和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="64f7a-127">The ADO NET destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="64f7a-128">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="64f7a-128">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="64f7a-129">有关可在 **“ADO NET 目标编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="64f7a-129">For more information about the properties that you can set in the **ADO NET Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="64f7a-130">ADO NET 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="64f7a-130">ADO NET Destination Editor &#40;Connection Manager Page&#41;</span></span>](../ado-net-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="64f7a-131">ADO NET 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="64f7a-131">ADO NET Destination Editor &#40;Mappings Page&#41;</span></span>](../ado-net-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="64f7a-132">ADO NET 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="64f7a-132">ADO NET Destination Editor &#40;Error Output Page&#41;</span></span>](../ado-net-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="64f7a-133">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="64f7a-133">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="64f7a-134">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="64f7a-134">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="64f7a-135">Common Properties</span><span class="sxs-lookup"><span data-stu-id="64f7a-135">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="64f7a-136">ADO NET 自定义属性</span><span class="sxs-lookup"><span data-stu-id="64f7a-136">ADO NET Custom Properties</span></span>](ado-net-custom-properties.md)  
  
 <span data-ttu-id="64f7a-137">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="64f7a-137">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
