---
title: 预览 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a795338122c1e7a37a23fdb6af6153f74b927e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579661"
---
# <a name="preview"></a><span data-ttu-id="68be9-102">预览</span><span class="sxs-lookup"><span data-stu-id="68be9-102">Preview</span></span>
  <span data-ttu-id="68be9-103">使用 **“预览”** 对话框可以预览 SAP BW 源所要提取的数据。</span><span class="sxs-lookup"><span data-stu-id="68be9-103">Use the **Preview** dialog box to preview the data that the SAP BW source will extract.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="68be9-104">**“预览”** 选项位于 **“SAP BW 源编辑器”** 的 **“连接管理器”** 页，实际用来提取数据。</span><span class="sxs-lookup"><span data-stu-id="68be9-104">The **Preview** option, that is available on the **Connection Manager** page of the **SAP BW Source Editor**, actually extracts data.</span></span> <span data-ttu-id="68be9-105">如果您已配置 SAP Netweaver BW 只提取自从上次提取后发生更改的数据，则选择 **“预览”** 将从下次数据提取中排除已经预览过的数据。</span><span class="sxs-lookup"><span data-stu-id="68be9-105">If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.</span></span>  
  
 <span data-ttu-id="68be9-106">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 源组件的详细信息，请参阅 [SAP BW 源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="68be9-106">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="68be9-107">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="68be9-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="68be9-108">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="68be9-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="68be9-109">从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。</span><span class="sxs-lookup"><span data-stu-id="68be9-109">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="68be9-110">请向 SAP 核实以便确认这些要求。</span><span class="sxs-lookup"><span data-stu-id="68be9-110">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="68be9-111">**打开“预览”对话框**</span><span class="sxs-lookup"><span data-stu-id="68be9-111">**To open the Preview dialog box**</span></span>  
  
1.  <span data-ttu-id="68be9-112">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="68be9-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="68be9-113">在“数据流”选项卡上，双击“SAP BW 源”。</span><span class="sxs-lookup"><span data-stu-id="68be9-113">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="68be9-114">在 **“SAP BW 源编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="68be9-114">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="68be9-115">配置 SAP BW 源。</span><span class="sxs-lookup"><span data-stu-id="68be9-115">Configure the SAP BW source.</span></span>  
  
5.  <span data-ttu-id="68be9-116">配置 SAP BW 源后，在 **“连接管理器”** 页中单击 **“预览”** ，在 **“预览”** 对话框中预览数据。</span><span class="sxs-lookup"><span data-stu-id="68be9-116">After you configure the SAP BW source, on the **Connection Manager** page, click **Preview** to preview the data in the **Preview** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="68be9-117">单击 **“预览”** 还将打开 **“请求日志”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="68be9-117">Clicking **Preview** also opens the **Request Log** dialog box.</span></span> <span data-ttu-id="68be9-118">有关此对话框的详细信息，请参阅 [Request Log](request-log.md)。</span><span class="sxs-lookup"><span data-stu-id="68be9-118">For more information about this dialog box, see [Request Log](request-log.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="68be9-119">选项</span><span class="sxs-lookup"><span data-stu-id="68be9-119">Options</span></span>  
 <span data-ttu-id="68be9-120">**“预览”** 对话框显示从 SAP Netweaver BW 系统中请求的行。</span><span class="sxs-lookup"><span data-stu-id="68be9-120">The **Preview** dialog box displays the rows that are requested from the SAP Netweaver BW system.</span></span> <span data-ttu-id="68be9-121">显示的列为源数据中定义的列。</span><span class="sxs-lookup"><span data-stu-id="68be9-121">The columns that are displayed are the columns that are defined in the source data.</span></span>  
  
 <span data-ttu-id="68be9-122">此对话框中没有其他选项。</span><span class="sxs-lookup"><span data-stu-id="68be9-122">There are no other options in this dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68be9-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68be9-123">See Also</span></span>  
 <span data-ttu-id="68be9-124">[SAP BW 源编辑器（“连接管理器”页）](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="68be9-124">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="68be9-125">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="68be9-125">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
