---
title: 创建 InfoSource | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7db233b-5464-43de-9d26-6dd24c7ac1b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9620d3170310322c79679e8298ffe465067ae7d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682986"
---
# <a name="create-infosource"></a><span data-ttu-id="a6a44-102">“创建 InfoSource”</span><span class="sxs-lookup"><span data-stu-id="a6a44-102">Create InfoSource</span></span>
  <span data-ttu-id="a6a44-103">使用 **“创建 InfoSource”** 对话框创建一个新 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="a6a44-103">Use the **Create InfoSource** dialog box to create a new InfoSource.</span></span> <span data-ttu-id="a6a44-104">要创建新 InfoSource，请使用 **“创建事务数据的 InfoSource”** 或 **“创建主数据的 InfoSource”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a6a44-104">To create the new InfoSource, you use either the **Create InfoSource for Transaction Data** or the **Create InfoSource for Master Data** dialog box.</span></span>  
  
 <span data-ttu-id="a6a44-105">从 **“SAP BW 目标编辑器”** 的 **“连接管理器”** 页可以打开 **“创建 InfoSource”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a6a44-105">You can open the **Create InfoSource** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="a6a44-106">若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a44-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a6a44-107">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="a6a44-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="a6a44-108">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="a6a44-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="a6a44-109">**打开“创建 InfoSource”对话框**</span><span class="sxs-lookup"><span data-stu-id="a6a44-109">**To open the Create InfoSource dialog box**</span></span>  
  
1.  <span data-ttu-id="a6a44-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="a6a44-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="a6a44-111">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="a6a44-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="a6a44-112">在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="a6a44-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="a6a44-113">在 **“连接管理器”** 页的 **“创建 SAP BW 对象”** 组框中，选择 **“InfoSource”** ，然后单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="a6a44-113">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a6a44-114">选项</span><span class="sxs-lookup"><span data-stu-id="a6a44-114">Options</span></span>  
 <span data-ttu-id="a6a44-115">**事务数据**</span><span class="sxs-lookup"><span data-stu-id="a6a44-115">**Transaction data**</span></span>  
 <span data-ttu-id="a6a44-116">创建事务数据的新 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="a6a44-116">Create a new InfoSource for transaction data.</span></span>  
  
 <span data-ttu-id="a6a44-117">如果您选择此选项，将打开 **“创建事务数据的 InfoSource”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a6a44-117">If you select this option, the **Create InfoSource for Transaction Data** dialog box opens.</span></span> <span data-ttu-id="a6a44-118">您可使用 **“创建事务数据的 InfoSource”** 对话框来创建新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="a6a44-118">You use the **Create InfoSource for Transaction Data** dialog box to create the new InfoSource.</span></span> <span data-ttu-id="a6a44-119">有关此对话框的详细信息，请参阅 [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a44-119">For more information about this dialog box, see [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md).</span></span>  
  
 <span data-ttu-id="a6a44-120">**主数据**</span><span class="sxs-lookup"><span data-stu-id="a6a44-120">**Master data**</span></span>  
 <span data-ttu-id="a6a44-121">创建主数据的新 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="a6a44-121">Create a new InfoSource for master data.</span></span>  
  
 <span data-ttu-id="a6a44-122">如果您选择此选项，将打开 **“创建主数据的 InfoSource”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a6a44-122">If you select this option, the **Create InfoSource for Master Data** dialog box opens.</span></span> <span data-ttu-id="a6a44-123">您可使用 **“创建主数据的 InfoSource”** 对话框来创建新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="a6a44-123">You use the **Create InfoSource for Master Data** dialog box to create the new InfoSource.</span></span> <span data-ttu-id="a6a44-124">有关此对话框的详细信息，请参阅 [Create InfoSource for Master Data](create-infosource-for-master-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a44-124">For more information about this dialog box, see [Create InfoSource for Master Data](create-infosource-for-master-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a44-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6a44-125">See Also</span></span>  
 [<span data-ttu-id="a6a44-126">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="a6a44-126">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
