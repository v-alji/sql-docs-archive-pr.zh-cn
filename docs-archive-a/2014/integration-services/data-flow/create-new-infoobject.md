---
title: 新建 InfoObject | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3587a633-1c0b-4d63-a22a-6b2b93923c3a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 022f2d1e3fe10ae037ea379a02a18845b3a36107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590312"
---
# <a name="create-new-infoobject"></a><span data-ttu-id="54efe-102">新建 InfoObject</span><span class="sxs-lookup"><span data-stu-id="54efe-102">Create New InfoObject</span></span>
  <span data-ttu-id="54efe-103">使用 **“新建 InfoObject”** 对话框在 SAP Netweaver BW 系统中创建新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="54efe-103">Use the **Create New InfoObject** dialog box to create a new InfoObject in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="54efe-104">从 **“SAP BW 目标编辑器”** 的 **“连接管理器”** 页可以打开 **“创建 InfoObject”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="54efe-104">You can open the **Create InfoObject** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="54efe-105">若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="54efe-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="54efe-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="54efe-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="54efe-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="54efe-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="54efe-108">**打开“新建 InfoObject”对话框**</span><span class="sxs-lookup"><span data-stu-id="54efe-108">**To open the Create New InfoObject dialog box**</span></span>  
  
1.  <span data-ttu-id="54efe-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="54efe-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="54efe-110">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="54efe-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="54efe-111">在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="54efe-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="54efe-112">在 **“连接管理器”** 页中，找到 **“创建 SAP BW 对象”** 分组框，执行以下步骤之一来创建 InfoObject：</span><span class="sxs-lookup"><span data-stu-id="54efe-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, do one of the following steps to create an InfoObject:</span></span>  
  
    1.  <span data-ttu-id="54efe-113">要直接创建 InfoObject，请选择 **“InfoObject”** ，然后单击 **“创建”** 打开 **“新建 InfoObject”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="54efe-113">To create an InfoObject directly, select **InfoObject**, and then click **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
    2.  <span data-ttu-id="54efe-114">要在创建 InfoCube 的同时创建 InfoObject，请选择 **“InfoCube”** ，然后单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="54efe-114">To create an InfoObject while creating an InfoCube, select **InfoCube**, and then click **Create**.</span></span> <span data-ttu-id="54efe-115">在 **“创建事务数据的 InfoCube”** 对话框中找到列表中某一行的 **“IObject”** 列，选择 **“创建”** 打开 **“新建 InfoObject”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="54efe-115">In the **Create InfoCube for Transaction Data** dialog box, in the **IObject** column for one of the rows in the list, select **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="54efe-116">表中每一行表示包数据流中的一列。</span><span class="sxs-lookup"><span data-stu-id="54efe-116">Each row in the table represents a column in the data flow of the package.</span></span>  
  
    3.  <span data-ttu-id="54efe-117">要在创建事务数据的 InfoSouce 的同时创建 InfoObject，请选择 **“InfoSource”** ，然后单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="54efe-117">To create an InfoObject while creating an InfoSouce for transactional data, select **InfoSource**, and then click **Create**.</span></span> <span data-ttu-id="54efe-118">在 **“创建 InfoSource”** 对话框中，选择 **“事务数据”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="54efe-118">In the **Create InfoSource** dialog box, select **Transaction Data**, and then click **OK**.</span></span> <span data-ttu-id="54efe-119">在 **“创建事务数据的 InfoSource”** 对话框中找到列表中某一行的 **“IObject”** 列，选择 **“创建”** 打开 **“新建 InfoObject”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="54efe-119">In the **Create InfoSource for Transaction Data** dialog box, in the **IObject** column for one of the rows in the list, select **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="54efe-120">表中每一行表示包数据流中的一列。</span><span class="sxs-lookup"><span data-stu-id="54efe-120">Each row in the table represents a column in the data flow of the package.</span></span>  
  
    4.  <span data-ttu-id="54efe-121">要在创建主数据的 InfoSource 的同时创建 InfoObject，请选择 **“InfoSource”** ，然后单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="54efe-121">To create an InfoObject while creating an InfoSource for master data, select **InfoSource**, and then click **Create**.</span></span> <span data-ttu-id="54efe-122">在 **“创建 InfoSource”** 对话框中，选择 **“主数据”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="54efe-122">In the **Create InfoSource** dialog box, select **Master Data**, and then click **OK**.</span></span> <span data-ttu-id="54efe-123">在 **“创建主数据的 InfoSource”** 对话框中，单击 **“新建”** 打开 **“新建 InfoObject”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="54efe-123">In the **Create InfoSource for Master Data** dialog box, click **New** to open the **Create New InfoObject** dialog box.</span></span>  
  
 <span data-ttu-id="54efe-124">您也可在 **“新建 InfoObject”** 对话框的 **“属性”** 部分中单击 **“新建”** 来打开 **“新建 InfoObject”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="54efe-124">You can also open the **Create New InfoObject** dialog box by clicking **New** in the **Attributes** section of the **Create New InfoObject** dialog box.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="54efe-125">常规选项</span><span class="sxs-lookup"><span data-stu-id="54efe-125">General Options</span></span>  
 <span data-ttu-id="54efe-126">**特征**</span><span class="sxs-lookup"><span data-stu-id="54efe-126">**Characteristic**</span></span>  
 <span data-ttu-id="54efe-127">创建一个表示维度数据的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="54efe-127">Create an InfoObject that represents dimension data.</span></span>  
  
 <span data-ttu-id="54efe-128">**关键数字**</span><span class="sxs-lookup"><span data-stu-id="54efe-128">**Key figure**</span></span>  
 <span data-ttu-id="54efe-129">创建一个表示事实数据的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="54efe-129">Create an InfoObject that represents fact data.</span></span>  
  
 <span data-ttu-id="54efe-130">**InfoObject 名称**</span><span class="sxs-lookup"><span data-stu-id="54efe-130">**InfoObject name**</span></span>  
 <span data-ttu-id="54efe-131">输入 InfoObject 的名称。</span><span class="sxs-lookup"><span data-stu-id="54efe-131">Enter a name for the InfoObject.</span></span>  
  
 <span data-ttu-id="54efe-132">**简短说明**</span><span class="sxs-lookup"><span data-stu-id="54efe-132">**Short description**</span></span>  
 <span data-ttu-id="54efe-133">输入 InfoObject 的简短说明。</span><span class="sxs-lookup"><span data-stu-id="54efe-133">Enter a short description for the InfoObject.</span></span>  
  
 <span data-ttu-id="54efe-134">**详细说明**</span><span class="sxs-lookup"><span data-stu-id="54efe-134">**Long description**</span></span>  
 <span data-ttu-id="54efe-135">输入 InfoObject 的详细说明。</span><span class="sxs-lookup"><span data-stu-id="54efe-135">Enter a long description for the InfoObject.</span></span>  
  
 <span data-ttu-id="54efe-136">**包含主数据**</span><span class="sxs-lookup"><span data-stu-id="54efe-136">**Has master data**</span></span>  
 <span data-ttu-id="54efe-137">指示 InfoObject 中包含属性、文本或层次结构形式的主数据。</span><span class="sxs-lookup"><span data-stu-id="54efe-137">Indicate that the InfoObject contains master data in the form of attributes, texts, or hierarchies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54efe-138">如果 InfoObject 表示维度数据且你已选择了“特征”  选项，则应选择此选项。</span><span class="sxs-lookup"><span data-stu-id="54efe-138">Select this option if the InfoObject represents dimensional data and you have selected the **Characteristic** option.</span></span>  
  
 <span data-ttu-id="54efe-139">**允许小写字符**</span><span class="sxs-lookup"><span data-stu-id="54efe-139">**Allow lower-case characters**</span></span>  
 <span data-ttu-id="54efe-140">允许 InfoObject 数据中使用小写字符。</span><span class="sxs-lookup"><span data-stu-id="54efe-140">Allow lower-case characters in the InfoObject data.</span></span>  
  
 <span data-ttu-id="54efe-141">**保存并激活**</span><span class="sxs-lookup"><span data-stu-id="54efe-141">**Save & Activate**</span></span>  
 <span data-ttu-id="54efe-142">保存并激活新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="54efe-142">Save and active the new InfoObject.</span></span>  
  
## <a name="data-type-options"></a><span data-ttu-id="54efe-143">数据类型选项</span><span class="sxs-lookup"><span data-stu-id="54efe-143">Data Type Options</span></span>  
 <span data-ttu-id="54efe-144">**CHAR - 字符串**</span><span class="sxs-lookup"><span data-stu-id="54efe-144">**CHAR - Character String**</span></span>  
 <span data-ttu-id="54efe-145">指示 InfoObject 包含字符数据。</span><span class="sxs-lookup"><span data-stu-id="54efe-145">Indicates that the InfoObject contains character data.</span></span>  
  
 <span data-ttu-id="54efe-146">**NUMC - 数值字符串**</span><span class="sxs-lookup"><span data-stu-id="54efe-146">**NUMC - Numeric String**</span></span>  
 <span data-ttu-id="54efe-147">指示 InfoObject 包含数值数据。</span><span class="sxs-lookup"><span data-stu-id="54efe-147">Indicates that the InfoObject contains numeric data.</span></span>  
  
 <span data-ttu-id="54efe-148">**DATS - 日期(YYYYMMDD)**</span><span class="sxs-lookup"><span data-stu-id="54efe-148">**DATS - Date (YYYYMMDD)**</span></span>  
 <span data-ttu-id="54efe-149">指示 InfoObject 包含日期数据。</span><span class="sxs-lookup"><span data-stu-id="54efe-149">Indicates that the InfoObject contains date data.</span></span>  
  
 <span data-ttu-id="54efe-150">**TIMS - 时间(HHMMSS)**</span><span class="sxs-lookup"><span data-stu-id="54efe-150">**TIMS - Time (HHMMSS)**</span></span>  
 <span data-ttu-id="54efe-151">指示 InfoObject 包含时间数据。</span><span class="sxs-lookup"><span data-stu-id="54efe-151">Indicates that the InfoObject contains time data.</span></span>  
  
 <span data-ttu-id="54efe-152">**长度**</span><span class="sxs-lookup"><span data-stu-id="54efe-152">**Length**</span></span>  
 <span data-ttu-id="54efe-153">输入数据的长度。</span><span class="sxs-lookup"><span data-stu-id="54efe-153">Enter the length of the data.</span></span>  
  
## <a name="text-options"></a><span data-ttu-id="54efe-154">文本选项</span><span class="sxs-lookup"><span data-stu-id="54efe-154">Text Options</span></span>  
 <span data-ttu-id="54efe-155">**包含文本**</span><span class="sxs-lookup"><span data-stu-id="54efe-155">**With Texts**</span></span>  
 <span data-ttu-id="54efe-156">指示 InfoObject 包含文本。</span><span class="sxs-lookup"><span data-stu-id="54efe-156">Indicate that the InfoObject contains texts.</span></span>  
  
 <span data-ttu-id="54efe-157">**短文本**</span><span class="sxs-lookup"><span data-stu-id="54efe-157">**Short Text**</span></span>  
 <span data-ttu-id="54efe-158">指示 InfoObject 包含短文本。</span><span class="sxs-lookup"><span data-stu-id="54efe-158">Indicates that the InfoObject contains short texts.</span></span>  
  
 <span data-ttu-id="54efe-159">**中等长度文本**</span><span class="sxs-lookup"><span data-stu-id="54efe-159">**Medium Text**</span></span>  
 <span data-ttu-id="54efe-160">指示 InfoObject 包含中等长度文本。</span><span class="sxs-lookup"><span data-stu-id="54efe-160">Indicates that the InfoObject contains medium texts.</span></span>  
  
 <span data-ttu-id="54efe-161">**长文本**</span><span class="sxs-lookup"><span data-stu-id="54efe-161">**Long Text**</span></span>  
 <span data-ttu-id="54efe-162">指示 InfoObject 包含长文本。</span><span class="sxs-lookup"><span data-stu-id="54efe-162">Indicates that the InfoObject contains long texts.</span></span>  
  
 <span data-ttu-id="54efe-163">**文本语言依赖**</span><span class="sxs-lookup"><span data-stu-id="54efe-163">**Text Language-Dependent**</span></span>  
 <span data-ttu-id="54efe-164">指示文本依赖于语言。</span><span class="sxs-lookup"><span data-stu-id="54efe-164">Indicates that the texts are language-dependent.</span></span>  
  
 <span data-ttu-id="54efe-165">**文本时间依赖**</span><span class="sxs-lookup"><span data-stu-id="54efe-165">**Text Time-Dependent**</span></span>  
 <span data-ttu-id="54efe-166">指示文本依赖于时间。</span><span class="sxs-lookup"><span data-stu-id="54efe-166">Indicates that the texts are time-dependent.</span></span>  
  
## <a name="attributes-section"></a><span data-ttu-id="54efe-167">属性部分</span><span class="sxs-lookup"><span data-stu-id="54efe-167">Attributes Section</span></span>  
 <span data-ttu-id="54efe-168">**“属性”** 部分包含 InfoObject 的属性列表和用于在列表中添加和删除属性的选项。</span><span class="sxs-lookup"><span data-stu-id="54efe-168">The **Attributes** section consists of a list of attributes for the InfoObject, and the options that let you add and remove attributes from the list.</span></span>  
  
### <a name="attributes-list"></a><span data-ttu-id="54efe-169">“属性”列表</span><span class="sxs-lookup"><span data-stu-id="54efe-169">Attributes List</span></span>  
 <span data-ttu-id="54efe-170">**“属性”** 列表显示所创建的 InfoObject 的属性。</span><span class="sxs-lookup"><span data-stu-id="54efe-170">The **Attributes** list displays the attributes of the InfoObject that you are creating.</span></span> <span data-ttu-id="54efe-171">**“属性”** 列表包含以下列标题：</span><span class="sxs-lookup"><span data-stu-id="54efe-171">The **Attributes** list has the following column headings:</span></span>  
  
 <span data-ttu-id="54efe-172">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="54efe-172">**InfoObject**</span></span>  
 <span data-ttu-id="54efe-173">查看 InfoObject 的名称</span><span class="sxs-lookup"><span data-stu-id="54efe-173">View the name of the InfoObject.</span></span>  
  
 <span data-ttu-id="54efe-174">**说明**</span><span class="sxs-lookup"><span data-stu-id="54efe-174">**Description**</span></span>  
 <span data-ttu-id="54efe-175">查看 InfoObject 的说明。</span><span class="sxs-lookup"><span data-stu-id="54efe-175">View the description of the InfoObject.</span></span>  
  
 <span data-ttu-id="54efe-176">**InfoObject 类型**</span><span class="sxs-lookup"><span data-stu-id="54efe-176">**InfoObject Type**</span></span>  
 <span data-ttu-id="54efe-177">查看 InfoObject 的类型。</span><span class="sxs-lookup"><span data-stu-id="54efe-177">View the type of the InfoObject.</span></span> <span data-ttu-id="54efe-178">下表列出了该类型的可能值。</span><span class="sxs-lookup"><span data-stu-id="54efe-178">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="54efe-179">值</span><span class="sxs-lookup"><span data-stu-id="54efe-179">Value</span></span>|<span data-ttu-id="54efe-180">说明</span><span class="sxs-lookup"><span data-stu-id="54efe-180">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54efe-181">CHA</span><span class="sxs-lookup"><span data-stu-id="54efe-181">CHA</span></span>|<span data-ttu-id="54efe-182">特征</span><span class="sxs-lookup"><span data-stu-id="54efe-182">Characteristics</span></span>|  
|<span data-ttu-id="54efe-183">KYF</span><span class="sxs-lookup"><span data-stu-id="54efe-183">KYF</span></span>|<span data-ttu-id="54efe-184">关键数字</span><span class="sxs-lookup"><span data-stu-id="54efe-184">Key figures</span></span>|  
|<span data-ttu-id="54efe-185">UNI</span><span class="sxs-lookup"><span data-stu-id="54efe-185">UNI</span></span>|<span data-ttu-id="54efe-186">单位</span><span class="sxs-lookup"><span data-stu-id="54efe-186">Units</span></span>|  
|<span data-ttu-id="54efe-187">TIM</span><span class="sxs-lookup"><span data-stu-id="54efe-187">TIM</span></span>|<span data-ttu-id="54efe-188">时间特征</span><span class="sxs-lookup"><span data-stu-id="54efe-188">Time characteristics</span></span>|  
  
### <a name="attributes-options"></a><span data-ttu-id="54efe-189">属性选项</span><span class="sxs-lookup"><span data-stu-id="54efe-189">Attributes Options</span></span>  
 <span data-ttu-id="54efe-190">使用以下选项添加和删除所创建的 InfoObject 的属性：</span><span class="sxs-lookup"><span data-stu-id="54efe-190">Use the following options to add and remove attributes for the InfoObject that you are creating:</span></span>  
  
 <span data-ttu-id="54efe-191">**添加**</span><span class="sxs-lookup"><span data-stu-id="54efe-191">**Add**</span></span>  
 <span data-ttu-id="54efe-192">添加现有的 InfoObject 作为属性。</span><span class="sxs-lookup"><span data-stu-id="54efe-192">Add an existing InfoObject as an attribute.</span></span>  
  
 <span data-ttu-id="54efe-193">要添加现有 InfoObject，请单击“添加”，然后使用 **“查找 InfoObject”** 对话框查找 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="54efe-193">To add an existing InfoObject, click Add, and then use the **Look Up InfoObject** dialog box to find the InfoObject.</span></span> <span data-ttu-id="54efe-194">有关此对话框的详细信息，请参阅 [Look Up InfoObject](look-up-infoobject.md)。</span><span class="sxs-lookup"><span data-stu-id="54efe-194">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="54efe-195">**新建**</span><span class="sxs-lookup"><span data-stu-id="54efe-195">**New**</span></span>  
 <span data-ttu-id="54efe-196">添加新的 InfoObject 作为属性。</span><span class="sxs-lookup"><span data-stu-id="54efe-196">Add a new InfoObject as an attribute.</span></span>  
  
 <span data-ttu-id="54efe-197">要创建和添加新的 InfoObject，请单击“新建”，然后使用 **“新建 InfoObject”** 对话框的一个新实例来创建新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="54efe-197">To create and add a new InfoObject, click New, and then use a new instance of the **Create New InfoObject** dialog box to create the new InfoObject.</span></span>  
  
 <span data-ttu-id="54efe-198">**删除**</span><span class="sxs-lookup"><span data-stu-id="54efe-198">**Remove**</span></span>  
 <span data-ttu-id="54efe-199">从“属性”  列表删除选择的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="54efe-199">Remove the selected InfoObject from the **Attributes** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54efe-200">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54efe-200">See Also</span></span>  
 <span data-ttu-id="54efe-201">[“创建事务数据的 InfoCube”](create-infocube-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="54efe-201">[Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md) </span></span>  
 <span data-ttu-id="54efe-202">[“创建 InfoSource”](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="54efe-202">[Create InfoSource](create-infosource.md) </span></span>  
 <span data-ttu-id="54efe-203">[创建事务数据的 InfoSource](create-infosource-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="54efe-203">[Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) </span></span>  
 <span data-ttu-id="54efe-204">[创建主数据的 InfoSource](create-infosource-for-master-data.md) </span><span class="sxs-lookup"><span data-stu-id="54efe-204">[Create InfoSource for Master Data](create-infosource-for-master-data.md) </span></span>  
 [<span data-ttu-id="54efe-205">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="54efe-205">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
