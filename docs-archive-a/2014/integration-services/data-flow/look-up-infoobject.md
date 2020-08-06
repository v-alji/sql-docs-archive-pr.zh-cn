---
title: 查找 InfoObject | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7f4c132-a5ec-49d8-a964-45775432731f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1616b4fcb368afc9e3f1157a3fc2511d4a7e8cce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689537"
---
# <a name="look-up-infoobject"></a><span data-ttu-id="6c032-102">查找 InfoObject</span><span class="sxs-lookup"><span data-stu-id="6c032-102">Look Up InfoObject</span></span>
  <span data-ttu-id="6c032-103">使用 **“查找 InfoObject”** 对话框查找在 SAP Netweaver BW 系统中定义的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="6c032-103">Use the **Look Up InfoObject** dialog box to look up an InfoObject that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="6c032-104">当可用 InfoObject 列表显示时，选择您需要的 InfoObject，然后 SAP BW 目标将使用需要的值填充关联的选项。</span><span class="sxs-lookup"><span data-stu-id="6c032-104">When the list of available InfoObjects appears, select the InfoObject that you want, and the SAP BW destination will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="6c032-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目标使用 **“查找 InfoObject”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="6c032-105">The SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up InfoObject** dialog box.</span></span> <span data-ttu-id="6c032-106">若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="6c032-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6c032-107">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="6c032-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="6c032-108">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="6c032-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="6c032-109">**打开“查找 InfoObject”对话框**</span><span class="sxs-lookup"><span data-stu-id="6c032-109">**To open the Look Up InfoObject dialog box**</span></span>  
  
1.  <span data-ttu-id="6c032-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="6c032-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="6c032-111">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="6c032-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="6c032-112">在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="6c032-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="6c032-113">在 **“连接管理器”** 页的 **“创建 SAP BW 对象”** 组框中，选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="6c032-113">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select one of the following options:</span></span>  
  
    1.  <span data-ttu-id="6c032-114">选择 **“InfoCube”** 。</span><span class="sxs-lookup"><span data-stu-id="6c032-114">Select **InfoCube**.</span></span> <span data-ttu-id="6c032-115">然后单击“创建”  。</span><span class="sxs-lookup"><span data-stu-id="6c032-115">Then, click **Create**.</span></span> <span data-ttu-id="6c032-116">在 **“创建事务数据的 InfoCube”** 对话框中单击列表中某一行的 **“IObject”** 列中的 **“搜索”** 。</span><span class="sxs-lookup"><span data-stu-id="6c032-116">In the **Create InfoCube for Transaction Data** dialog box, click **Search** in the **IObject** column for one of the rows in the list.</span></span> <span data-ttu-id="6c032-117">每一行表示包数据流中的一列。</span><span class="sxs-lookup"><span data-stu-id="6c032-117">Each row represents a column in the data flow of the package.</span></span>  
  
    2.  <span data-ttu-id="6c032-118">选择 **“InfoSource”** 。</span><span class="sxs-lookup"><span data-stu-id="6c032-118">Select **InfoSource**.</span></span> <span data-ttu-id="6c032-119">然后单击“创建”  。</span><span class="sxs-lookup"><span data-stu-id="6c032-119">Then click **Create**.</span></span> <span data-ttu-id="6c032-120">在 **“创建 InfoSource”** 对话框中，选择 **“事务数据”** 。</span><span class="sxs-lookup"><span data-stu-id="6c032-120">In the **Create InfoSource** dialog box, select **Transaction data**.</span></span> <span data-ttu-id="6c032-121">在 **“创建事务数据的 InfoSource”** 对话框中单击列表中某一行的 **“IObject”** 列中的 **“搜索”** 。</span><span class="sxs-lookup"><span data-stu-id="6c032-121">In the **Create InfoSource for Transaction Data** dialog box, click **Search** in the **IObject** column for one of the rows in the list.</span></span> <span data-ttu-id="6c032-122">每一行表示包数据流中的一列。</span><span class="sxs-lookup"><span data-stu-id="6c032-122">Each row represents a column in the data flow of the package.</span></span>  
  
    3.  <span data-ttu-id="6c032-123">选择 **“InfoSource”** 。</span><span class="sxs-lookup"><span data-stu-id="6c032-123">Select **InfoSource**.</span></span> <span data-ttu-id="6c032-124">然后单击“创建”  。</span><span class="sxs-lookup"><span data-stu-id="6c032-124">Then click **Create**.</span></span> <span data-ttu-id="6c032-125">在 **“创建 InfoSource”** 对话框中，选择 **“主数据”** 。</span><span class="sxs-lookup"><span data-stu-id="6c032-125">In the **Create InfoSource** dialog box, select **Master data**.</span></span> <span data-ttu-id="6c032-126">在 **“创建主数据的 InfoSource”** 对话框中单击 **“查找”** 。</span><span class="sxs-lookup"><span data-stu-id="6c032-126">In the **Create InfoSource for Master Data** dialog box, click **Look up**.</span></span>  
  
 <span data-ttu-id="6c032-127">您还可以单击 **“新建 InfoObject”** 对话框中 **“属性”** 部分中的 **“添加”** 来打开 **“查找 InfoObject”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="6c032-127">You can also open the **Look Up InfoObject** dialog box by clicking **Add** in the **Attributes** section of the **Create New InfoObject** dialog box.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="6c032-128">查找选项</span><span class="sxs-lookup"><span data-stu-id="6c032-128">Lookup Options</span></span>  
 <span data-ttu-id="6c032-129">在查找字段文本框中，您可以使用星号通配符 (\*) 或使用部分字符串结合星号通配符来筛选结果。</span><span class="sxs-lookup"><span data-stu-id="6c032-129">In the lookup field text boxes, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="6c032-130">但是，如果您将查找字段保留为空，则查找过程仅与该字段中的空字符串匹配。</span><span class="sxs-lookup"><span data-stu-id="6c032-130">However, if you leave a lookup field empty, the lookup process will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="6c032-131">**特征**</span><span class="sxs-lookup"><span data-stu-id="6c032-131">**Characteristics**</span></span>  
 <span data-ttu-id="6c032-132">查找代表特征的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="6c032-132">Look up InfoObjects that represent characteristics.</span></span>  
  
 <span data-ttu-id="6c032-133">**单位**</span><span class="sxs-lookup"><span data-stu-id="6c032-133">**Units**</span></span>  
 <span data-ttu-id="6c032-134">查找代表单位的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="6c032-134">Look up InfoObjects that represent units.</span></span>  
  
 <span data-ttu-id="6c032-135">**关键数字**</span><span class="sxs-lookup"><span data-stu-id="6c032-135">**Key figures**</span></span>  
 <span data-ttu-id="6c032-136">查找代表关键数字的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="6c032-136">Look up InfoObjects that represent key figures.</span></span>  
  
 <span data-ttu-id="6c032-137">**时间特征**</span><span class="sxs-lookup"><span data-stu-id="6c032-137">**Time characteristics**</span></span>  
 <span data-ttu-id="6c032-138">查找代表时间特征的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="6c032-138">Look up InfoObjects that represent time characteristics.</span></span>  
  
 <span data-ttu-id="6c032-139">**名称**</span><span class="sxs-lookup"><span data-stu-id="6c032-139">**Name**</span></span>  
 <span data-ttu-id="6c032-140">输入您要查找的 InfoObject 的名称，或输入部分名称加上星号通配符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="6c032-140">Enter the name of the InfoObject that you want to look up, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="6c032-141">或者，仅使用星号通配符以包括所有 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="6c032-141">Or, use the asterisk wildcard character alone to include all InfoObjects.</span></span>  
  
 <span data-ttu-id="6c032-142">**说明**</span><span class="sxs-lookup"><span data-stu-id="6c032-142">**Description**</span></span>  
 <span data-ttu-id="6c032-143">输入说明，或输入部分说明加上星号通配符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="6c032-143">Enter the description, or a partial description with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="6c032-144">或者，仅使用星号通配符以包括所有 InfoObject（而无论说明是什么）。</span><span class="sxs-lookup"><span data-stu-id="6c032-144">Or, use the asterisk wildcard character alone to include all InfoObjects regardless of description.</span></span>  
  
 <span data-ttu-id="6c032-145">**查找**</span><span class="sxs-lookup"><span data-stu-id="6c032-145">**Look up**</span></span>  
 <span data-ttu-id="6c032-146">查找在 SAP Netweaver BW 系统中定义的匹配 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="6c032-146">Look up matching InfoObjects that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="6c032-147">查找结果</span><span class="sxs-lookup"><span data-stu-id="6c032-147">Lookup Results</span></span>  
 <span data-ttu-id="6c032-148">单击“查找”按钮后，将在一个包含以下列标题的表中显示 SAP Netweaver BW 系统中 InfoObject 的列表。</span><span class="sxs-lookup"><span data-stu-id="6c032-148">After you click the Look up button, a list of the InfoObjects in the SAP Netweaver BW system appears in a table with the following column headings.</span></span>  
  
 <span data-ttu-id="6c032-149">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="6c032-149">**InfoObject**</span></span>  
 <span data-ttu-id="6c032-150">显示在 SAP Netweaver BW 系统中定义的 InfoObject 的名称。</span><span class="sxs-lookup"><span data-stu-id="6c032-150">Displays the name of the InfoObject that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="6c032-151">**文本(短)**</span><span class="sxs-lookup"><span data-stu-id="6c032-151">**Text (short)**</span></span>  
 <span data-ttu-id="6c032-152">显示与 InfoObject 相关联的简短文本。</span><span class="sxs-lookup"><span data-stu-id="6c032-152">Displays the short text that is associated with the InfoObject.</span></span>  
  
 <span data-ttu-id="6c032-153">当可用 InfoObject 列表显示时，选择您需要的 InfoObject，然后目标将使用需要的值填充关联的选项。</span><span class="sxs-lookup"><span data-stu-id="6c032-153">When the list of available InfoObjects appears, select the InfoObject that you want, and the destination will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c032-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c032-154">See Also</span></span>  
 <span data-ttu-id="6c032-155">[“创建事务数据的 InfoCube”](create-infocube-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="6c032-155">[Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md) </span></span>  
 <span data-ttu-id="6c032-156">[“创建 InfoSource”](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="6c032-156">[Create InfoSource](create-infosource.md) </span></span>  
 <span data-ttu-id="6c032-157">[创建事务数据的 InfoSource](create-infosource-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="6c032-157">[Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) </span></span>  
 <span data-ttu-id="6c032-158">[创建主数据的 InfoSource](create-infosource-for-master-data.md) </span><span class="sxs-lookup"><span data-stu-id="6c032-158">[Create InfoSource for Master Data](create-infosource-for-master-data.md) </span></span>  
 <span data-ttu-id="6c032-159">[新建 InfoObject](create-new-infoobject.md) </span><span class="sxs-lookup"><span data-stu-id="6c032-159">[Create New InfoObject](create-new-infoobject.md) </span></span>  
 <span data-ttu-id="6c032-160">[SAP BW 目标编辑器（“连接管理器”页）](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="6c032-160">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="6c032-161">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="6c032-161">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
