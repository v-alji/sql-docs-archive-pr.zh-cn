---
title: 创建事务数据的 InfoSource | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab5f23e2-cd4e-4507-83d9-ac5ef721c171
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e3a60bb93da17e79087982473e92c35fa0856d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682988"
---
# <a name="create-infosource-for-transaction-data"></a><span data-ttu-id="e062f-102">创建事务数据的 InfoSource</span><span class="sxs-lookup"><span data-stu-id="e062f-102">Create InfoSource for Transaction Data</span></span>
  <span data-ttu-id="e062f-103">使用 **“创建事务数据的 InfoSource”** 对话框为 SAP Netweaver BW 系统中的事务数据创建一个新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="e062f-103">Use the **Create InfoSource for Transaction Data** dialog box to create a new InfoSource for transaction data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="e062f-104">从 **“SAP BW 目标编辑器”** 的 **“连接管理器”** 页可以打开 **“创建事务数据的 InfoSource”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e062f-104">You can open the **Create InfoSource for Transaction Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="e062f-105">若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="e062f-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e062f-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="e062f-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="e062f-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="e062f-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="e062f-108">**打开“创建事务数据的 InfoSource”对话框**</span><span class="sxs-lookup"><span data-stu-id="e062f-108">**To open the Create InfoSource for Transaction Data dialog box**</span></span>  
  
1.  <span data-ttu-id="e062f-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="e062f-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="e062f-110">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="e062f-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="e062f-111">在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="e062f-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="e062f-112">在 **“连接管理器”** 页的 **“创建 SAP BW 对象”** 组框中，选择 **“InfoSource”** ，然后单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="e062f-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
5.  <span data-ttu-id="e062f-113">在 **“创建 InfoSource”** 对话框中，选择 **“事务数据”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="e062f-113">In the **Create InfoSource** dialog box, select **Transaction data**, and then click **OK**.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="e062f-114">常规选项</span><span class="sxs-lookup"><span data-stu-id="e062f-114">General Options</span></span>  
 <span data-ttu-id="e062f-115">**InfoSource 名称**</span><span class="sxs-lookup"><span data-stu-id="e062f-115">**InfoSource name**</span></span>  
 <span data-ttu-id="e062f-116">输入新 InfoSource 的名称。</span><span class="sxs-lookup"><span data-stu-id="e062f-116">Enter a name for the new InfoSource.</span></span>  
  
 <span data-ttu-id="e062f-117">**简短说明**</span><span class="sxs-lookup"><span data-stu-id="e062f-117">**Short description**</span></span>  
 <span data-ttu-id="e062f-118">输入新 InfoSource 的简短说明。</span><span class="sxs-lookup"><span data-stu-id="e062f-118">Enter a short description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="e062f-119">**详细说明**</span><span class="sxs-lookup"><span data-stu-id="e062f-119">**Long description**</span></span>  
 <span data-ttu-id="e062f-120">输入新 InfoSource 的详细说明。</span><span class="sxs-lookup"><span data-stu-id="e062f-120">Enter a long description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="e062f-121">**源系统**</span><span class="sxs-lookup"><span data-stu-id="e062f-121">**Source system**</span></span>  
 <span data-ttu-id="e062f-122">选择与 InfoSource 相关联的源系统。</span><span class="sxs-lookup"><span data-stu-id="e062f-122">Select the source system associated with the InfoSource.</span></span>  
  
 <span data-ttu-id="e062f-123">**保存并激活**</span><span class="sxs-lookup"><span data-stu-id="e062f-123">**Save & Activate**</span></span>  
 <span data-ttu-id="e062f-124">保存并激活该新 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="e062f-124">Save and activate the new InfoSource.</span></span>  
  
## <a name="infosource-transfer-structure-options"></a><span data-ttu-id="e062f-125">InfoSource 传输结构选项</span><span class="sxs-lookup"><span data-stu-id="e062f-125">InfoSource Transfer Structure Options</span></span>  
 <span data-ttu-id="e062f-126">InfoSource 传输结构可供您将数据流列与 InfoSource 关联。</span><span class="sxs-lookup"><span data-stu-id="e062f-126">The InfoSource transfer structure lets you associate data flow columns to InfoSources.</span></span>  
  
 <span data-ttu-id="e062f-127">**PipelineElement**</span><span class="sxs-lookup"><span data-stu-id="e062f-127">**PipelineElement**</span></span>  
 <span data-ttu-id="e062f-128">显示数据流输出中与 SAP BW 目标连接的列。</span><span class="sxs-lookup"><span data-stu-id="e062f-128">Displays the column in the output of the data flow that is connected to the SAP BW destination.</span></span>  
  
 <span data-ttu-id="e062f-129">**PipelineDataType**</span><span class="sxs-lookup"><span data-stu-id="e062f-129">**PipelineDataType**</span></span>  
 <span data-ttu-id="e062f-130">显示数据流列的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e062f-130">Displays the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type of the data flow column.</span></span>  
  
 <span data-ttu-id="e062f-131">**Iobject - 搜索**</span><span class="sxs-lookup"><span data-stu-id="e062f-131">**Iobject - Search**</span></span>  
 <span data-ttu-id="e062f-132">将现有的 InfoObject 与当前行中的数据流列关联。</span><span class="sxs-lookup"><span data-stu-id="e062f-132">Associate an existing InfoObject to the data flow column in the current row.</span></span> <span data-ttu-id="e062f-133">要进行此关联，请单击 **“搜索”** ，然后使用 **“查找 InfoObject”** 对话框选择现有的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="e062f-133">To make this association, click **Search**, and then use the **Look Up InfoObject** dialog box to select the existing InfoObject.</span></span> <span data-ttu-id="e062f-134">有关此对话框的详细信息，请参阅 [Look Up InfoObject](look-up-infoobject.md)。</span><span class="sxs-lookup"><span data-stu-id="e062f-134">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="e062f-135">选择现有的 InfoObject 后，组件会将选定的值填充在 **“InfoObject”** 和 **“类型”** 列中。</span><span class="sxs-lookup"><span data-stu-id="e062f-135">After you select an existing InfoObject, the component populates the **InfoObject** and **Type** columns with the selected values.</span></span>  
  
 <span data-ttu-id="e062f-136">**Iobject - 新建**</span><span class="sxs-lookup"><span data-stu-id="e062f-136">**Iobject - New**</span></span>  
 <span data-ttu-id="e062f-137">创建一个新的 InfoObject 并将该新 InfoObject 与当前行中的数据流列关联。</span><span class="sxs-lookup"><span data-stu-id="e062f-137">Create a new InfoObject and associate this new InfoObect to the data flow column in the current row.</span></span> <span data-ttu-id="e062f-138">要创建新的 InfoObject，请单击 **“新建”** ，然后使用 **“新建 InfoObject”** 对话框创建 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="e062f-138">To create the new InfoObject, click **New**, and then use the **Create New InfoObject** dialog box to create the InfoObject.</span></span> <span data-ttu-id="e062f-139">有关此对话框的详细信息，请参阅 [Create New InfoObject](create-new-infoobject.md)。</span><span class="sxs-lookup"><span data-stu-id="e062f-139">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="e062f-140">创建新 InfoObject 后，组件会将新值填充在 **“InfoObject”** 和 **“类型”** 列中。</span><span class="sxs-lookup"><span data-stu-id="e062f-140">After you create a new InfoObject, the component populates the **InfoObject** and **Type** columns with the new values.</span></span>  
  
 <span data-ttu-id="e062f-141">**Iobject - 删除**</span><span class="sxs-lookup"><span data-stu-id="e062f-141">**Iobject - Remove**</span></span>  
 <span data-ttu-id="e062f-142">删除 InfoObject 与当前行的数据流列之间的关联。</span><span class="sxs-lookup"><span data-stu-id="e062f-142">Remove the association between the InfoObject and the data flow column for the current row.</span></span> <span data-ttu-id="e062f-143">若要删除此关联，请单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="e062f-143">To remove this association, click **Remove**.</span></span>  
  
 <span data-ttu-id="e062f-144">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="e062f-144">**InfoObject**</span></span>  
 <span data-ttu-id="e062f-145">显示与数据流列相关联的 InfoObject 的名称。</span><span class="sxs-lookup"><span data-stu-id="e062f-145">Displays the name of the InfoObject that is associated with the data flow column.</span></span>  
  
 <span data-ttu-id="e062f-146">类型 </span><span class="sxs-lookup"><span data-stu-id="e062f-146">**Type**</span></span>  
 <span data-ttu-id="e062f-147">显示与数据流列相关联的 InfoObject 的类型。</span><span class="sxs-lookup"><span data-stu-id="e062f-147">Displays the type of the InfoObject that is associated with the data flow column.</span></span> <span data-ttu-id="e062f-148">下表列出了该类型的可能值。</span><span class="sxs-lookup"><span data-stu-id="e062f-148">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="e062f-149">值</span><span class="sxs-lookup"><span data-stu-id="e062f-149">Value</span></span>|<span data-ttu-id="e062f-150">说明</span><span class="sxs-lookup"><span data-stu-id="e062f-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e062f-151">CHA</span><span class="sxs-lookup"><span data-stu-id="e062f-151">CHA</span></span>|<span data-ttu-id="e062f-152">特征</span><span class="sxs-lookup"><span data-stu-id="e062f-152">Characteristics</span></span>|  
|<span data-ttu-id="e062f-153">UNI</span><span class="sxs-lookup"><span data-stu-id="e062f-153">UNI</span></span>|<span data-ttu-id="e062f-154">单位</span><span class="sxs-lookup"><span data-stu-id="e062f-154">Units</span></span>|  
|<span data-ttu-id="e062f-155">KYF</span><span class="sxs-lookup"><span data-stu-id="e062f-155">KYF</span></span>|<span data-ttu-id="e062f-156">关键数字</span><span class="sxs-lookup"><span data-stu-id="e062f-156">Key figures</span></span>|  
|<span data-ttu-id="e062f-157">TIM</span><span class="sxs-lookup"><span data-stu-id="e062f-157">TIM</span></span>|<span data-ttu-id="e062f-158">时间特征</span><span class="sxs-lookup"><span data-stu-id="e062f-158">Time characteristics</span></span>|  
  
 <span data-ttu-id="e062f-159">**单位字段**</span><span class="sxs-lookup"><span data-stu-id="e062f-159">**Unit Field**</span></span>  
 <span data-ttu-id="e062f-160">指定 InfoObject 将使用的单位。</span><span class="sxs-lookup"><span data-stu-id="e062f-160">Specify the units that the InfoObject will use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e062f-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e062f-161">See Also</span></span>  
 <span data-ttu-id="e062f-162">[“创建 InfoSource”](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="e062f-162">[Create InfoSource](create-infosource.md) </span></span>  
 [<span data-ttu-id="e062f-163">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="e062f-163">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
