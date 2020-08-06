---
title: SAP BW 源编辑器（“列”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c2ec8bb7-be9b-4783-ad88-32512de784b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba605360d01abc520cedfbc457dd89319ed83c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692463"
---
# <a name="sap-bw-source-editor-columns-page"></a><span data-ttu-id="18b22-102">SAP BW 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="18b22-102">SAP BW Source Editor (Columns Page)</span></span>
  <span data-ttu-id="18b22-103">使用“SAP BW 源编辑器”的“列”页将输出列映射到每个外部（源）列。</span><span class="sxs-lookup"><span data-stu-id="18b22-103">Use the **Columns** page of the **SAP BW Source Editor** to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="18b22-104">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 源组件的详细信息，请参阅 [SAP BW 源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="18b22-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="18b22-105">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="18b22-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="18b22-106">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="18b22-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="18b22-107">从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。</span><span class="sxs-lookup"><span data-stu-id="18b22-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="18b22-108">请向 SAP 核实以便确认这些要求。</span><span class="sxs-lookup"><span data-stu-id="18b22-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="18b22-109">**打开“列”页**</span><span class="sxs-lookup"><span data-stu-id="18b22-109">**To open the Columns page**</span></span>  
  
1.  <span data-ttu-id="18b22-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="18b22-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="18b22-111">在“数据流”  选项卡上，双击“SAP BW 源”。</span><span class="sxs-lookup"><span data-stu-id="18b22-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="18b22-112">在 **“SAP BW 源编辑器”** 中单击 **“列”** ，以打开编辑器的 **“列”** 页。</span><span class="sxs-lookup"><span data-stu-id="18b22-112">In the **SAP BW Source Editor**, click **Columns** to open the **Columns** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="18b22-113">选项</span><span class="sxs-lookup"><span data-stu-id="18b22-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18b22-114">如果您不知道配置源所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="18b22-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="18b22-115">**可用外部列**</span><span class="sxs-lookup"><span data-stu-id="18b22-115">**Available External Columns**</span></span>  
 <span data-ttu-id="18b22-116">查看数据源中可用外部列的列表，然后选择要包括在数据流中的列。</span><span class="sxs-lookup"><span data-stu-id="18b22-116">View the list of available external columns in the data source, and then select the columns to be included in the data flow.</span></span>  
  
 <span data-ttu-id="18b22-117">若要在数据流中包括某列，请选中该列对应的复选框。</span><span class="sxs-lookup"><span data-stu-id="18b22-117">To include a column in the data flow, select the check box that corresponds to that column.</span></span> <span data-ttu-id="18b22-118">您选择这些复选框的顺序决定了列的输出顺序。</span><span class="sxs-lookup"><span data-stu-id="18b22-118">The order in which you select the check boxes determines the order in which columns will be output.</span></span> <span data-ttu-id="18b22-119">也就是说，您选择的第一个复选框将是第一个输出列，而选择的第二个复选框则将是第二个输出列，以此类推。</span><span class="sxs-lookup"><span data-stu-id="18b22-119">That is, the first check box that you select will be the first output column, the second check box will be the second output columns, and so on.</span></span>  
  
 <span data-ttu-id="18b22-120">**“外部列”**</span><span class="sxs-lookup"><span data-stu-id="18b22-120">**External Column**</span></span>  
 <span data-ttu-id="18b22-121">查看选定外部（源）列。</span><span class="sxs-lookup"><span data-stu-id="18b22-121">View the selected external (source) columns.</span></span> <span data-ttu-id="18b22-122">选定列将按照您在配置要使用来自此源的数据的下游组件时将看到的对应输出列的顺序显示。</span><span class="sxs-lookup"><span data-stu-id="18b22-122">The selected columns appear in the order in which you will see their corresponding output columns when you configure downstream components that consume data from this source.</span></span>  
  
 <span data-ttu-id="18b22-123">要更改这些列的顺序，请在 **“可用外部列”** 列表中清除所有列的复选框。</span><span class="sxs-lookup"><span data-stu-id="18b22-123">To change the order of the columns, in the **Available External Columns** list, clear the check boxes for all columns.</span></span> <span data-ttu-id="18b22-124">然后按照您希望列显示的顺序选择列。</span><span class="sxs-lookup"><span data-stu-id="18b22-124">Then, select the columns in the order that you want them to appear.</span></span>  
  
 <span data-ttu-id="18b22-125">**输出列**</span><span class="sxs-lookup"><span data-stu-id="18b22-125">**Output Column**</span></span>  
 <span data-ttu-id="18b22-126">为每个输出列提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="18b22-126">Provide a unique name for each output column.</span></span> <span data-ttu-id="18b22-127">默认值是所选外部（源）列的名称。</span><span class="sxs-lookup"><span data-stu-id="18b22-127">The default is the name of the selected external (source) column.</span></span> <span data-ttu-id="18b22-128">但是，您可以输入任何唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="18b22-128">However, you can enter any unique, descriptive name.</span></span> [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="18b22-129">设计器将显示列的 **输出列** 名称。</span><span class="sxs-lookup"><span data-stu-id="18b22-129">Designer will display the **Output Column** names for the columns when you configure downstream components that consume data from this source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b22-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18b22-130">See Also</span></span>  
 <span data-ttu-id="18b22-131">[SAP BW 源编辑器（“连接管理器”页）](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="18b22-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="18b22-132">[SAP BW 源编辑器（“错误输出”页）](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="18b22-132">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="18b22-133">[SAP BW 源编辑器（“高级”页）](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="18b22-133">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="18b22-134">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="18b22-134">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
