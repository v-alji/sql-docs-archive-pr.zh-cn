---
title: 查找 InfoPackage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1e45477e8faeed07faa114850e10a3bc4bbcf170
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689536"
---
# <a name="look-up-infopackage"></a><span data-ttu-id="c5211-102">查找 InfoPackage</span><span class="sxs-lookup"><span data-stu-id="c5211-102">Look Up InfoPackage</span></span>
  <span data-ttu-id="c5211-103">使用 **“查找 InfoPackage”** 对话框查找在 SAP Netweaver BW 系统中定义的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="c5211-103">Use the **Look Up InfoPackage** dialog box to look up an InfoPackage that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="c5211-104">当 InfoPackage 列表显示时，选择您需要的 InfoPackage，然后目标将使用需要的值填充关联的选项。</span><span class="sxs-lookup"><span data-stu-id="c5211-104">When the list of InfoPackages appears, select the InfoPackage that you want, and the destination will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="c5211-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目标使用 **“查找进程链”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c5211-105">The SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="c5211-106">若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="c5211-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c5211-107">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="c5211-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="c5211-108">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="c5211-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="c5211-109">**打开“查找 InfoPackage”对话框**</span><span class="sxs-lookup"><span data-stu-id="c5211-109">**To open the Look Up InfoPackage dialog box**</span></span>  
  
1.  <span data-ttu-id="c5211-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="c5211-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="c5211-111">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="c5211-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="c5211-112">在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="c5211-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="c5211-113">在“连接管理器”页面上的“InfoPackage/InfoSource”组框中，单击“查找”显示“查找 InfoPackage”对话框     。</span><span class="sxs-lookup"><span data-stu-id="c5211-113">On the **Connection Manager** page, in the **InfoPackage/InfoSource** group box, click **Look up** to display the **Look Up InfoPackage** dialog box.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="c5211-114">查找选项</span><span class="sxs-lookup"><span data-stu-id="c5211-114">Lookup Options</span></span>  
 <span data-ttu-id="c5211-115">在查找字段中，您可以使用星号通配符 (\*) 或使用部分字符串结合星号通配符来筛选结果。</span><span class="sxs-lookup"><span data-stu-id="c5211-115">In the lookup fields, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="c5211-116">但是，如果您将查找字段保留为空，则查找操作仅与该字段中的空字符串匹配。</span><span class="sxs-lookup"><span data-stu-id="c5211-116">However, if you leave a lookup field empty, the lookup operation will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="c5211-117">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="c5211-117">**InfoPackage**</span></span>  
 <span data-ttu-id="c5211-118">输入您要查找的 InfoPackage 的名称，或输入部分名称加上星号通配符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c5211-118">Enter the name of the InfoPackage that you want to look up, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="c5211-119">或者，仅使用星号通配符，以包括所有 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="c5211-119">Or, use the asterisk wildcard character alone to include all InfoPackages.</span></span>  
  
 <span data-ttu-id="c5211-120">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="c5211-120">**InfoSource**</span></span>  
 <span data-ttu-id="c5211-121">输入 InfoSource 的名称，或输入部分名称加上星号通配符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c5211-121">Enter the name of the InfoSource, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="c5211-122">或者，仅使用星号通配符以包括所有 InfoPackage（而无论 InfoSource 是什么）。</span><span class="sxs-lookup"><span data-stu-id="c5211-122">Or, use the asterisk wildcard character alone to include all InfoPackages regardless of InfoSource.</span></span>  
  
 <span data-ttu-id="c5211-123">**源系统**</span><span class="sxs-lookup"><span data-stu-id="c5211-123">**Source system**</span></span>  
 <span data-ttu-id="c5211-124">输入源系统的名称，或输入部分名称加上星号通配符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c5211-124">Enter the name of the source system, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="c5211-125">或者，仅使用星号通配符以包括所有 InfoPackage（而无论源系统是什么）。</span><span class="sxs-lookup"><span data-stu-id="c5211-125">Or, use the asterisk wildcard character alone to include all InfoPackages regardless of source systems.</span></span>  
  
 <span data-ttu-id="c5211-126">**查找**</span><span class="sxs-lookup"><span data-stu-id="c5211-126">**Look up**</span></span>  
 <span data-ttu-id="c5211-127">查找在 SAP Netweaver BW 系统中定义的匹配 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="c5211-127">Look up matching InfoPackages that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="c5211-128">查找结果</span><span class="sxs-lookup"><span data-stu-id="c5211-128">Lookup Results</span></span>  
 <span data-ttu-id="c5211-129">单击“查找”按钮后，将在一个包含以下列标题的表中显示 SAP Netweaver BW 系统中 InfoPackage 的列表。</span><span class="sxs-lookup"><span data-stu-id="c5211-129">After you click the Look up button, a list of the InfoPackages in the SAP Netweaver BW system appears in a table with the following column headings.</span></span>  
  
 <span data-ttu-id="c5211-130">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="c5211-130">**InfoPackage**</span></span>  
 <span data-ttu-id="c5211-131">显示在 SAP Netweaver BW 系统中定义的 InfoPackage 的名称。</span><span class="sxs-lookup"><span data-stu-id="c5211-131">Displays the name of the InfoPackage that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="c5211-132">类型 </span><span class="sxs-lookup"><span data-stu-id="c5211-132">**Type**</span></span>  
 <span data-ttu-id="c5211-133">显示 InfoPackage 的类型。</span><span class="sxs-lookup"><span data-stu-id="c5211-133">Displays the type of the InfoPackage.</span></span> <span data-ttu-id="c5211-134">下表列出了该类型的可能值。</span><span class="sxs-lookup"><span data-stu-id="c5211-134">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="c5211-135">值</span><span class="sxs-lookup"><span data-stu-id="c5211-135">Value</span></span>|<span data-ttu-id="c5211-136">说明</span><span class="sxs-lookup"><span data-stu-id="c5211-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5211-137">Trans.</span><span class="sxs-lookup"><span data-stu-id="c5211-137">Trans.</span></span>|<span data-ttu-id="c5211-138">事务数据。</span><span class="sxs-lookup"><span data-stu-id="c5211-138">Transaction data.</span></span>|  
|<span data-ttu-id="c5211-139">Attr.</span><span class="sxs-lookup"><span data-stu-id="c5211-139">Attr.</span></span>|<span data-ttu-id="c5211-140">属性数据。</span><span class="sxs-lookup"><span data-stu-id="c5211-140">Attribute data.</span></span>|  
|<span data-ttu-id="c5211-141">文本</span><span class="sxs-lookup"><span data-stu-id="c5211-141">Texts</span></span>|<span data-ttu-id="c5211-142">文本。</span><span class="sxs-lookup"><span data-stu-id="c5211-142">Texts.</span></span>|  
  
 <span data-ttu-id="c5211-143">**说明**</span><span class="sxs-lookup"><span data-stu-id="c5211-143">**Description**</span></span>  
 <span data-ttu-id="c5211-144">显示 InfoPackage 的说明。</span><span class="sxs-lookup"><span data-stu-id="c5211-144">Displays the description of the InfoPackage.</span></span>  
  
 <span data-ttu-id="c5211-145">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="c5211-145">**InfoSource**</span></span>  
 <span data-ttu-id="c5211-146">显示与 InfoPackage 相关联的 InfoSource（如果有）的名称。</span><span class="sxs-lookup"><span data-stu-id="c5211-146">Displays the name of the InfoSource, if any, that is associated with the InfoPackage.</span></span>  
  
 <span data-ttu-id="c5211-147">**Source System**</span><span class="sxs-lookup"><span data-stu-id="c5211-147">**Source System**</span></span>  
 <span data-ttu-id="c5211-148">显示源系统的名称。</span><span class="sxs-lookup"><span data-stu-id="c5211-148">Displays the name of the source system.</span></span>  
  
 <span data-ttu-id="c5211-149">当 InfoPackage 列表显示时，选择您需要的 InfoPackage，然后目标将使用需要的值填充关联的选项。</span><span class="sxs-lookup"><span data-stu-id="c5211-149">When the list of InfoPackages appears, select the InfoPackage that you want, and the destination will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5211-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5211-150">See Also</span></span>  
 <span data-ttu-id="c5211-151">[SAP BW 目标编辑器（“连接管理器”页）](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="c5211-151">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="c5211-152">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="c5211-152">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
