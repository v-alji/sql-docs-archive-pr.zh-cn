---
title: 创建主数据的 InfoSource | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b52a9a89-8380-4a02-8a83-dcfb46ae860e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bb90bc5cf27f37dc89df236b765db98088a5804a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682992"
---
# <a name="create-infosource-for-master-data"></a><span data-ttu-id="84dcb-102">“创建主数据的 InfoSource”</span><span class="sxs-lookup"><span data-stu-id="84dcb-102">Create InfoSource for Master Data</span></span>
  <span data-ttu-id="84dcb-103">使用 **“创建主数据的 InfoSource”** 对话框为 SAP Netweaver BW 系统中的主数据创建一个新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="84dcb-103">Use the **Create InfoSource for Master Data** dialog box to create a new InfoSource for master data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="84dcb-104">从 **“SAP BW 目标编辑器”** 的 **“连接管理器”** 页可以打开 **“创建主数据的 InfoSource”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="84dcb-104">You can open the **Create InfoSource for Master Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="84dcb-105">若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="84dcb-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="84dcb-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="84dcb-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="84dcb-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="84dcb-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="84dcb-108">**打开“创建主数据的 InfoSource”对话框**</span><span class="sxs-lookup"><span data-stu-id="84dcb-108">**To open the Create InfoSource for Master Data dialog box**</span></span>  
  
1.  <span data-ttu-id="84dcb-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="84dcb-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="84dcb-110">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="84dcb-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="84dcb-111">在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="84dcb-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="84dcb-112">在 **“连接管理器”** 页的 **“创建 SAP BW 对象”** 组框中，选择 **“InfoSource”** ，然后单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="84dcb-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
5.  <span data-ttu-id="84dcb-113">在 **“创建 InfoSource”** 对话框中，选择 **“主数据”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="84dcb-113">In the **Create InfoSource** dialog box, select **Master data**, and then click **OK**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="84dcb-114">选项</span><span class="sxs-lookup"><span data-stu-id="84dcb-114">Options</span></span>  
 <span data-ttu-id="84dcb-115">**InfoObject 名称**</span><span class="sxs-lookup"><span data-stu-id="84dcb-115">**InfoObject name**</span></span>  
 <span data-ttu-id="84dcb-116">输入新 InfoSource 应基于的 InfoObject 的名称。</span><span class="sxs-lookup"><span data-stu-id="84dcb-116">Enter the name of the InfoObject on which the new InfoSource should be based.</span></span>  
  
 <span data-ttu-id="84dcb-117">**查找**</span><span class="sxs-lookup"><span data-stu-id="84dcb-117">**Look up**</span></span>  
 <span data-ttu-id="84dcb-118">查找 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="84dcb-118">Look up the InfoObject.</span></span> <span data-ttu-id="84dcb-119">此选项可打开 **“查找 InfoObject”** 对话框，您可从该对话框中选择 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="84dcb-119">This option opens the **Look Up InfoObject** dialog box in which you can select the InfoObject.</span></span> <span data-ttu-id="84dcb-120">有关此对话框的详细信息，请参阅 [Look Up InfoObject](look-up-infoobject.md)。</span><span class="sxs-lookup"><span data-stu-id="84dcb-120">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="84dcb-121">在您选择 InfoObject 后，组件会将选定 InfoObject 的名称填充在 **“InfoObject 名称”** 文本框中。</span><span class="sxs-lookup"><span data-stu-id="84dcb-121">After you select an InfoObject, the component populates the **InfoObject name** text box with the name of the selected InfoObject.</span></span>  
  
 <span data-ttu-id="84dcb-122">**新建**</span><span class="sxs-lookup"><span data-stu-id="84dcb-122">**New**</span></span>  
 <span data-ttu-id="84dcb-123">新建 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="84dcb-123">Create a new InfoObject.</span></span> <span data-ttu-id="84dcb-124">此选项可打开“新建 InfoObject”对话框，您可在其中创建新的 InfoObject  。</span><span class="sxs-lookup"><span data-stu-id="84dcb-124">This option opens the **Create New InfoObject** dialog box in which you can create the new InfoObject.</span></span> <span data-ttu-id="84dcb-125">有关此对话框的详细信息，请参阅 [Create New InfoObject](create-new-infoobject.md)。</span><span class="sxs-lookup"><span data-stu-id="84dcb-125">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="84dcb-126">创建 InfoObject 后，组件会将新 InfoObject 的名称填充在 **“InfoObject 名称”** 文本框中。</span><span class="sxs-lookup"><span data-stu-id="84dcb-126">After you create an InfoObject, the component populates the **InfoObject name** text box with the name of the new InfoObject.</span></span>  
  
 <span data-ttu-id="84dcb-127">**简短说明**</span><span class="sxs-lookup"><span data-stu-id="84dcb-127">**Short description**</span></span>  
 <span data-ttu-id="84dcb-128">输入新 InfoSource 的简短说明。</span><span class="sxs-lookup"><span data-stu-id="84dcb-128">Enter a short description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="84dcb-129">**详细说明**</span><span class="sxs-lookup"><span data-stu-id="84dcb-129">**Long description**</span></span>  
 <span data-ttu-id="84dcb-130">输入新 InfoSource 的详细说明。</span><span class="sxs-lookup"><span data-stu-id="84dcb-130">Enter a long description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="84dcb-131">**源系统**</span><span class="sxs-lookup"><span data-stu-id="84dcb-131">**Source system**</span></span>  
 <span data-ttu-id="84dcb-132">选择要与新 InfoSource 相关联的源系统。</span><span class="sxs-lookup"><span data-stu-id="84dcb-132">Select the source system to be associated with the new InfoSource.</span></span>  
  
 <span data-ttu-id="84dcb-133">**应用程序**</span><span class="sxs-lookup"><span data-stu-id="84dcb-133">**Application**</span></span>  
 <span data-ttu-id="84dcb-134">输入要与新 InfoSource 关联的应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="84dcb-134">Enter the name of the application to be associated with the new InfoSource.</span></span>  
  
 <span data-ttu-id="84dcb-135">**属性**</span><span class="sxs-lookup"><span data-stu-id="84dcb-135">**Attributes**</span></span>  
 <span data-ttu-id="84dcb-136">指示主数据由属性组成。</span><span class="sxs-lookup"><span data-stu-id="84dcb-136">Indicates that the master data consists of attributes.</span></span>  
  
 <span data-ttu-id="84dcb-137">**文本**</span><span class="sxs-lookup"><span data-stu-id="84dcb-137">**Texts**</span></span>  
 <span data-ttu-id="84dcb-138">指示主数据由属性组成。</span><span class="sxs-lookup"><span data-stu-id="84dcb-138">Indicates that the master data consists of attributes.</span></span>  
  
 <span data-ttu-id="84dcb-139">**保存并激活**</span><span class="sxs-lookup"><span data-stu-id="84dcb-139">**Save & Activate**</span></span>  
 <span data-ttu-id="84dcb-140">保存并激活该新 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="84dcb-140">Save and activate the new InfoSource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84dcb-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84dcb-141">See Also</span></span>  
 <span data-ttu-id="84dcb-142">[“创建 InfoSource”](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="84dcb-142">[Create InfoSource](create-infosource.md) </span></span>  
 [<span data-ttu-id="84dcb-143">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="84dcb-143">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
