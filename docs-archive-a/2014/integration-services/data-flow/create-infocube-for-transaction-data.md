---
title: 创建事务数据的 InfoCube | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 673cea01-a260-4fce-a1a0-f73839289805
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a20fe051cfdd3e6afe285279996fcf696a83c21b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682996"
---
# <a name="create-infocube-for-transaction-data"></a><span data-ttu-id="07f96-102">“创建事务数据的 InfoCube”</span><span class="sxs-lookup"><span data-stu-id="07f96-102">Create InfoCube for Transaction Data</span></span>
  <span data-ttu-id="07f96-103">使用 **“创建事务数据的 InfoCube”** 对话框为 SAP Netweaver BW 系统中的事务数据创建一个新的 InfoCube。</span><span class="sxs-lookup"><span data-stu-id="07f96-103">Use the **Create InfoCube for Transaction Data** dialog box to create a new InfoCube for transaction data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="07f96-104">从 **“SAP BW 目标编辑器”** 的 **“连接管理器”** 页可以打开 **“创建事务数据的 InfoCube”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="07f96-104">You can open the **Create InfoCube for Transaction Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="07f96-105">若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="07f96-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="07f96-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="07f96-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="07f96-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="07f96-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="07f96-108">**打开“创建事务数据的 InfoCube”对话框**</span><span class="sxs-lookup"><span data-stu-id="07f96-108">**To open the Create InfoCube for Transaction Data dialog box**</span></span>  
  
1.  <span data-ttu-id="07f96-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="07f96-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="07f96-110">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="07f96-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="07f96-111">在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="07f96-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="07f96-112">在 **“连接管理器”** 页中，找到 **“创建 SAP BW 对象”** 分组框，选择 **“InfoCube”** ，然后单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="07f96-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoCube**, and then click **Create**.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="07f96-113">常规选项</span><span class="sxs-lookup"><span data-stu-id="07f96-113">General Options</span></span>  
 <span data-ttu-id="07f96-114">**InfoCube 名称**</span><span class="sxs-lookup"><span data-stu-id="07f96-114">**InfoCube name**</span></span>  
 <span data-ttu-id="07f96-115">输入新 InfoCube 的名称。</span><span class="sxs-lookup"><span data-stu-id="07f96-115">Enter a name for the new InfoCube.</span></span>  
  
 <span data-ttu-id="07f96-116">**详细说明**</span><span class="sxs-lookup"><span data-stu-id="07f96-116">**Long description**</span></span>  
 <span data-ttu-id="07f96-117">输入新 InfoCube 的说明。</span><span class="sxs-lookup"><span data-stu-id="07f96-117">Enter a description for the new InfoCube.</span></span>  
  
 <span data-ttu-id="07f96-118">**保存并激活**</span><span class="sxs-lookup"><span data-stu-id="07f96-118">**Save & Activate**</span></span>  
 <span data-ttu-id="07f96-119">保存并激活新的 InfoCube。</span><span class="sxs-lookup"><span data-stu-id="07f96-119">Save and activate the new InfoCube.</span></span>  
  
## <a name="infocube-transfer-structure-options"></a><span data-ttu-id="07f96-120">InfoCube 传输结构选项</span><span class="sxs-lookup"><span data-stu-id="07f96-120">InfoCube Transfer Structure Options</span></span>  
 <span data-ttu-id="07f96-121">InfoCube 传输结构部分可供您将数据流列与 InfoObject 关联。</span><span class="sxs-lookup"><span data-stu-id="07f96-121">The InfoCube transfer structure section lets you associate data flow columns to InfoObjects.</span></span>  
  
 <span data-ttu-id="07f96-122">**PipelineElement**</span><span class="sxs-lookup"><span data-stu-id="07f96-122">**PipelineElement**</span></span>  
 <span data-ttu-id="07f96-123">显示数据流输出中与 SAP BW 目标连接的列。</span><span class="sxs-lookup"><span data-stu-id="07f96-123">Displays the column in the output of the data flow that is connected to the SAP BW destination.</span></span>  
  
 <span data-ttu-id="07f96-124">**PipelineDataType**</span><span class="sxs-lookup"><span data-stu-id="07f96-124">**PipelineDataType**</span></span>  
 <span data-ttu-id="07f96-125">显示数据流列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="07f96-125">Displays the data type of the data flow column.</span></span>  
  
 <span data-ttu-id="07f96-126">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="07f96-126">**InfoObject**</span></span>  
 <span data-ttu-id="07f96-127">显示与数据流列相关联的 InfoObject 的名称。</span><span class="sxs-lookup"><span data-stu-id="07f96-127">Displays the name of the InfoObject that is associated with the data flow column.</span></span>  
  
 <span data-ttu-id="07f96-128">类型 </span><span class="sxs-lookup"><span data-stu-id="07f96-128">**Type**</span></span>  
 <span data-ttu-id="07f96-129">显示与数据流列相关联的 InfoObject 的类型。</span><span class="sxs-lookup"><span data-stu-id="07f96-129">Displays the type of the InfoObject that is associated with the data flow column.</span></span> <span data-ttu-id="07f96-130">下表列出了该类型的可能值。</span><span class="sxs-lookup"><span data-stu-id="07f96-130">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="07f96-131">值</span><span class="sxs-lookup"><span data-stu-id="07f96-131">Value</span></span>|<span data-ttu-id="07f96-132">说明</span><span class="sxs-lookup"><span data-stu-id="07f96-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07f96-133">CHA</span><span class="sxs-lookup"><span data-stu-id="07f96-133">CHA</span></span>|<span data-ttu-id="07f96-134">特征</span><span class="sxs-lookup"><span data-stu-id="07f96-134">Characteristics</span></span>|  
|<span data-ttu-id="07f96-135">UNI</span><span class="sxs-lookup"><span data-stu-id="07f96-135">UNI</span></span>|<span data-ttu-id="07f96-136">单位</span><span class="sxs-lookup"><span data-stu-id="07f96-136">Units</span></span>|  
|<span data-ttu-id="07f96-137">KYF</span><span class="sxs-lookup"><span data-stu-id="07f96-137">KYF</span></span>|<span data-ttu-id="07f96-138">关键数字</span><span class="sxs-lookup"><span data-stu-id="07f96-138">Key figures</span></span>|  
|<span data-ttu-id="07f96-139">TIM</span><span class="sxs-lookup"><span data-stu-id="07f96-139">TIM</span></span>|<span data-ttu-id="07f96-140">时间特征</span><span class="sxs-lookup"><span data-stu-id="07f96-140">Time characteristics</span></span>|  
  
 <span data-ttu-id="07f96-141">**Iobject - 搜索**</span><span class="sxs-lookup"><span data-stu-id="07f96-141">**Iobject - Search**</span></span>  
 <span data-ttu-id="07f96-142">将现有的 InfoObject 与当前行的数据流列关联。</span><span class="sxs-lookup"><span data-stu-id="07f96-142">Associate an existing InfoObject to the data flow column for the current row.</span></span> <span data-ttu-id="07f96-143">要进行此关联，请单击 **“搜索”** ，然后使用 **“查找 InfoObject”** 对话框选择现有的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="07f96-143">To make this association, click **Search**, and then use the **Look Up InfoObject** dialog box to select the existing InfoObject.</span></span> <span data-ttu-id="07f96-144">有关此对话框的详细信息，请参阅 [Look Up InfoObject](look-up-infoobject.md)。</span><span class="sxs-lookup"><span data-stu-id="07f96-144">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="07f96-145">选择现有的 InfoObject 后，组件会将选定的值填充在 **“InfoObject”** 和 **“类型”** 列中。</span><span class="sxs-lookup"><span data-stu-id="07f96-145">After you select an existing InfoObject, the component populates the **InfoObject** and **Type** columns with the selected values.</span></span>  
  
 <span data-ttu-id="07f96-146">**Iobject - 新建**</span><span class="sxs-lookup"><span data-stu-id="07f96-146">**Iobject - New**</span></span>  
 <span data-ttu-id="07f96-147">创建一个新的 InfoObject 并将该新的 InfoObject 与当前行中的数据流列关联。</span><span class="sxs-lookup"><span data-stu-id="07f96-147">Create a new InfoObject and associate this new InfoObject to the data flow column in the current row.</span></span> <span data-ttu-id="07f96-148">要创建新的 InfoObject，请单击 **“新建”** ，然后使用 **“新建 InfoObject”** 对话框创建 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="07f96-148">To create the new InfoObject, click **New**, and then use the **Create New InfoObject** dialog box to create the InfoObject.</span></span> <span data-ttu-id="07f96-149">有关此对话框的详细信息，请参阅 [Create New InfoObject](create-new-infoobject.md)。</span><span class="sxs-lookup"><span data-stu-id="07f96-149">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="07f96-150">创建新 InfoObject 后，组件会将新值填充在 **“InfoObject”** 和 **“类型”** 列中。</span><span class="sxs-lookup"><span data-stu-id="07f96-150">After you create a new InfoObject, the component populates the **InfoObject** and **Type** columns with the new values.</span></span>  
  
 <span data-ttu-id="07f96-151">**Iobject - 删除**</span><span class="sxs-lookup"><span data-stu-id="07f96-151">**Iobject - Remove**</span></span>  
 <span data-ttu-id="07f96-152">删除 InfoObject 与当前行的数据流列之间的关联。</span><span class="sxs-lookup"><span data-stu-id="07f96-152">Remove the association between the InfoObject and the data flow column for the current row.</span></span> <span data-ttu-id="07f96-153">若要删除此关联，请单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="07f96-153">To remove this association, click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f96-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07f96-154">See Also</span></span>  
 [<span data-ttu-id="07f96-155">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="07f96-155">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
