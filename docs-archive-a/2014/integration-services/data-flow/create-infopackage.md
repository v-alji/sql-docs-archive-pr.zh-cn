---
title: 创建 InfoPackage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9cd4a848-409f-4681-a390-1c49a2aadbd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95f6ddce4e97c0c21d9f77c432231d414770dbce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682994"
---
# <a name="create-infopackage"></a><span data-ttu-id="e533d-102">创建 InfoPackage</span><span class="sxs-lookup"><span data-stu-id="e533d-102">Create InfoPackage</span></span>
  <span data-ttu-id="e533d-103">使用 **“创建 InfoPackage”** 对话框在 SAP Netweaver BW 系统中创建新的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="e533d-103">Use the **Create InfoPackage** dialog box to create a new InfoPackage in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="e533d-104">从 **“SAP BW 目标编辑器”** 的 **“连接管理器”** 页可以打开 **“创建 InfoPackage”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e533d-104">You can open the **Create InfoPackage** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="e533d-105">若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="e533d-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e533d-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="e533d-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="e533d-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="e533d-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="e533d-108">**打开“创建 InfoPackage”对话框**</span><span class="sxs-lookup"><span data-stu-id="e533d-108">**To open the Create InfoPackage dialog box**</span></span>  
  
1.  <span data-ttu-id="e533d-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="e533d-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="e533d-110">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="e533d-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="e533d-111">在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="e533d-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="e533d-112">在 **“连接管理器”** 页中，找到 **“创建 SAP BW 对象”** 组框，选择 **“InfoPackage”** ，然后单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="e533d-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoPackage**, and then click **Create**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e533d-113">选项</span><span class="sxs-lookup"><span data-stu-id="e533d-113">Options</span></span>  
 <span data-ttu-id="e533d-114">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="e533d-114">**InfoSource**</span></span>  
 <span data-ttu-id="e533d-115">输入新 InfoPackage 应基于的 InfoSource 的名称。</span><span class="sxs-lookup"><span data-stu-id="e533d-115">Enter the name of the InfoSource on which the new InfoPackage should be based.</span></span>  
  
 <span data-ttu-id="e533d-116">**简短说明**</span><span class="sxs-lookup"><span data-stu-id="e533d-116">**Short description**</span></span>  
 <span data-ttu-id="e533d-117">输入新 InfoPackage 的说明。</span><span class="sxs-lookup"><span data-stu-id="e533d-117">Enter a description for the new InfoPackage.</span></span>  
  
 <span data-ttu-id="e533d-118">**源系统**</span><span class="sxs-lookup"><span data-stu-id="e533d-118">**Source system**</span></span>  
 <span data-ttu-id="e533d-119">选择将与新 InfoPackage 相关联的源系统。</span><span class="sxs-lookup"><span data-stu-id="e533d-119">Select the source system with which the new InfoPackage should be associated.</span></span>  
  
 <span data-ttu-id="e533d-120">**属性**</span><span class="sxs-lookup"><span data-stu-id="e533d-120">**Attributes**</span></span>  
 <span data-ttu-id="e533d-121">指示 InfoPackage 将加载属性数据。</span><span class="sxs-lookup"><span data-stu-id="e533d-121">Indicates that the InfoPackage will load attribute data.</span></span>  
  
 <span data-ttu-id="e533d-122">**文本**</span><span class="sxs-lookup"><span data-stu-id="e533d-122">**Texts**</span></span>  
 <span data-ttu-id="e533d-123">指示 InfoPackage 将加载文本数据。</span><span class="sxs-lookup"><span data-stu-id="e533d-123">Indicates that the InfoPackage will load text data.</span></span>  
  
 <span data-ttu-id="e533d-124">**事务**</span><span class="sxs-lookup"><span data-stu-id="e533d-124">**Transaction**</span></span>  
 <span data-ttu-id="e533d-125">指示 InfoPackage 将加载事务数据。</span><span class="sxs-lookup"><span data-stu-id="e533d-125">Indicates that the InfoPackage will load transaction data.</span></span>  
  
 <span data-ttu-id="e533d-126">**保存并激活**</span><span class="sxs-lookup"><span data-stu-id="e533d-126">**Save & Activate**</span></span>  
 <span data-ttu-id="e533d-127">保存并激活该新 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="e533d-127">Save and activate the new InfoPackage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e533d-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e533d-128">See Also</span></span>  
 [<span data-ttu-id="e533d-129">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="e533d-129">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
