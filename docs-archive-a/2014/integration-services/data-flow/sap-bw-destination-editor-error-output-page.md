---
title: SAP BW 目标编辑器（“错误输出”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a543d811-0bd2-4890-a0d3-f5fdcd4524b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ffd58580865a71626252aa2d177530e41156537
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682981"
---
# <a name="sap-bw-destination-editor-error-output-page"></a><span data-ttu-id="64f96-102">SAP BW 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="64f96-102">SAP BW Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="64f96-103">可以使用 **“SAP BW 目标编辑器”** 的 **“错误输出”** 页指定错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="64f96-103">Use the **Error Output** page of the **SAP BW Destination Editor** to specify error handling options.</span></span>  
  
 <span data-ttu-id="64f96-104">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目标的详细信息，请参阅 [SAP BW 目标](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="64f96-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="64f96-105">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="64f96-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="64f96-106">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="64f96-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="64f96-107">**打开“错误输出”页**</span><span class="sxs-lookup"><span data-stu-id="64f96-107">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="64f96-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="64f96-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="64f96-109">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="64f96-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="64f96-110">在 **“SAP BW 目标编辑器”** 中单击 **“错误输出”** ，以打开编辑器的 **“错误输出”** 页。</span><span class="sxs-lookup"><span data-stu-id="64f96-110">In the **SAP BW Destination Editor**, click **Error Output** to open the **Error Output** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="64f96-111">选项</span><span class="sxs-lookup"><span data-stu-id="64f96-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64f96-112">如果您不知道配置目标所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="64f96-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="64f96-113">**输入或输出**</span><span class="sxs-lookup"><span data-stu-id="64f96-113">**Input or Output**</span></span>  
 <span data-ttu-id="64f96-114">查看输入的名称。</span><span class="sxs-lookup"><span data-stu-id="64f96-114">View the name of the input.</span></span>  
  
 <span data-ttu-id="64f96-115">**列**</span><span class="sxs-lookup"><span data-stu-id="64f96-115">**Column**</span></span>  
 <span data-ttu-id="64f96-116">未使用此选项。</span><span class="sxs-lookup"><span data-stu-id="64f96-116">This option is not used.</span></span>  
  
 <span data-ttu-id="64f96-117">**错误**</span><span class="sxs-lookup"><span data-stu-id="64f96-117">**Error**</span></span>  
 <span data-ttu-id="64f96-118">指定发生错误时目标应执行的操作：忽略错误、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="64f96-118">Specify what the destination should do when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="64f96-119">**截断**</span><span class="sxs-lookup"><span data-stu-id="64f96-119">**Truncation**</span></span>  
 <span data-ttu-id="64f96-120">未使用此选项。</span><span class="sxs-lookup"><span data-stu-id="64f96-120">This option is not used.</span></span>  
  
 <span data-ttu-id="64f96-121">**说明**</span><span class="sxs-lookup"><span data-stu-id="64f96-121">**Description**</span></span>  
 <span data-ttu-id="64f96-122">查看操作的说明。</span><span class="sxs-lookup"><span data-stu-id="64f96-122">View the description of the operation.</span></span>  
  
 <span data-ttu-id="64f96-123">**将此值设置到选定的单元格**</span><span class="sxs-lookup"><span data-stu-id="64f96-123">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="64f96-124">指定发生错误或截断时目标应对所有选定单元格执行的操作：忽略错误、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="64f96-124">Specify what the destination should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="64f96-125">**应用**</span><span class="sxs-lookup"><span data-stu-id="64f96-125">**Apply**</span></span>  
 <span data-ttu-id="64f96-126">将错误处理选项应用到选定的单元格。</span><span class="sxs-lookup"><span data-stu-id="64f96-126">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f96-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64f96-127">See Also</span></span>  
 <span data-ttu-id="64f96-128">[SAP BW 目标编辑器（“连接管理器”页）](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="64f96-128">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="64f96-129">[SAP BW 目标编辑器（“映射”页）](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="64f96-129">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="64f96-130">[SAP BW 目标编辑器（“高级”页）](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="64f96-130">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="64f96-131">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="64f96-131">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
