---
title: "\"DQS 清理转换编辑器\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssdqs.designer.cleansing.f1
- SQL12.SSDQS.DESIGNER.DQCONNECTION.F1
ms.assetid: 07e79641-71ee-45d0-a9ba-ed6f9f68f333
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e97cd138bb17ce3cfe476496e5bc576875728224
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577758"
---
# <a name="dqs-cleansing-transformation-editor-dialog-box"></a><span data-ttu-id="8c107-102">“DQS 清除转换编辑器”对话框</span><span class="sxs-lookup"><span data-stu-id="8c107-102">DQS Cleansing Transformation Editor Dialog Box</span></span>
  <span data-ttu-id="8c107-103">可使用 Data Quality Services (DQS) 通过“DQS 清除转换编辑器”\*\*\*\* 对话框来更正数据。</span><span class="sxs-lookup"><span data-stu-id="8c107-103">Use the **DQS Cleansing Transformation Editor** dialog box to correct data using Data Quality Services (DQS).</span></span> <span data-ttu-id="8c107-104">有关详细信息，请参阅 [Data Quality Services Concepts](../../2014/data-quality-services/data-quality-services-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-104">For more information, see [Data Quality Services Concepts](../../2014/data-quality-services/data-quality-services-concepts.md).</span></span>  
  
 <span data-ttu-id="8c107-105">若要了解有关转换的详细信息，请参阅 [DQS Cleansing Transformation](data-flow/transformations/dqs-cleansing-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-105">To learn more about the transformation, see [DQS Cleansing Transformation](data-flow/transformations/dqs-cleansing-transformation.md).</span></span>  
  
 <span data-ttu-id="8c107-106">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="8c107-106">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="8c107-107">打开 DQS 清除转换编辑器</span><span class="sxs-lookup"><span data-stu-id="8c107-107">Open the DQS Cleansing Transformation Editor</span></span>](#open)  
  
-   [<span data-ttu-id="8c107-108">设置 "连接管理器" 选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="8c107-108">Set options on the Connection Manager tab</span></span>](#connection)  
  
-   [<span data-ttu-id="8c107-109">设置“映射”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="8c107-109">Set options on the Mapping tab</span></span>](#mapping)  
  
-   [<span data-ttu-id="8c107-110">设置“高级”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="8c107-110">Set options on the Advanced tab</span></span>](#advanced)  
  
-   [<span data-ttu-id="8c107-111">设置 "DQS 清除连接管理器" 对话框中的选项</span><span class="sxs-lookup"><span data-stu-id="8c107-111">Set the options in the DQS Cleansing Connection Manager dialog box</span></span>](#manager)  
  
##  <a name="open-the-dqs-cleansing-transformation-editor"></a><a name="open"></a><span data-ttu-id="8c107-112">打开 DQS 清除转换编辑器</span><span class="sxs-lookup"><span data-stu-id="8c107-112">Open the DQS Cleansing Transformation Editor</span></span>  
  
1.  <span data-ttu-id="8c107-113">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中，将“DQS 清除转换”添加到 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]包。</span><span class="sxs-lookup"><span data-stu-id="8c107-113">Add the DQS Cleansing Transformation to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="8c107-114">右键单击该组件，然后单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="8c107-114">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="8c107-115">设置“连接管理器”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="8c107-115">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="8c107-116">**数据质量连接管理器**</span><span class="sxs-lookup"><span data-stu-id="8c107-116">**Data quality connection manager**</span></span>  
 <span data-ttu-id="8c107-117">从列表中选择现有 DQS 连接管理器，或单击“新建”\*\*\*\* 创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="8c107-117">Select an existing DQS connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="8c107-118">**新建**</span><span class="sxs-lookup"><span data-stu-id="8c107-118">**New**</span></span>  
 <span data-ttu-id="8c107-119">使用“DQS 清除连接管理器”\*\*\*\* 对话框创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="8c107-119">Create a new connection manager by using the **DQS Cleansing Connection Manager** dialog box.</span></span> <span data-ttu-id="8c107-120">请参阅 [设置“DQS 清除连接管理器”对话框中的选项](#manager)</span><span class="sxs-lookup"><span data-stu-id="8c107-120">See [Set the options in the DQS Cleansing Connection Manager dialog box](#manager)</span></span>  
  
 <span data-ttu-id="8c107-121">**数据质量知识库**</span><span class="sxs-lookup"><span data-stu-id="8c107-121">**Data Quality Knowledge Base**</span></span>  
 <span data-ttu-id="8c107-122">为所连接的数据源选择现有的 DQS 知识库。</span><span class="sxs-lookup"><span data-stu-id="8c107-122">Select an existing DQS knowledge base for the connected data source.</span></span> <span data-ttu-id="8c107-123">有关 DQS 知识库的详细信息，请参阅 [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-123">For more information about the DQS knowledge base, see [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
 <span data-ttu-id="8c107-124">**加密连接**</span><span class="sxs-lookup"><span data-stu-id="8c107-124">**Encrypt connection**</span></span>  
 <span data-ttu-id="8c107-125">指定是否加密连接，以加密 DQS 服务器和之间的数据传输 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8c107-125">specify whether to encrypt the connection, in order to encrypt the data transfer between the DQS Server and [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8c107-126">**可用域**</span><span class="sxs-lookup"><span data-stu-id="8c107-126">**Available domains**</span></span>  
 <span data-ttu-id="8c107-127">列出可用于选定知识库的域。</span><span class="sxs-lookup"><span data-stu-id="8c107-127">Lists the available domains for the selected knowledge base.</span></span> <span data-ttu-id="8c107-128">存在两种类型的域：单一域和包含两个或两个以上的单一域的复合域。</span><span class="sxs-lookup"><span data-stu-id="8c107-128">There are two types of domains: single domains, and composite domains that contain two or more single domains.</span></span>  
  
 <span data-ttu-id="8c107-129">有关如何将列映射到复合域的信息，请参阅 [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-129">For information on how to map columns to composite domains, see [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).</span></span>  
  
 <span data-ttu-id="8c107-130">有关域的详细信息，请参阅 [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-130">For more information about domains, see [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
 <span data-ttu-id="8c107-131">**配置错误输出**</span><span class="sxs-lookup"><span data-stu-id="8c107-131">**Configure Error Output**</span></span>  
 <span data-ttu-id="8c107-132">指定如何处理行级错误。</span><span class="sxs-lookup"><span data-stu-id="8c107-132">Specify how to handle row-level errors.</span></span> <span data-ttu-id="8c107-133">在转换更正来自已连接数据源的数据时可能会由于意外的数据值或验证约束而出错。</span><span class="sxs-lookup"><span data-stu-id="8c107-133">Errors can occur when the transformation corrects data from the connected data source, due to unexpected data values or validation constraints.</span></span>  
  
 <span data-ttu-id="8c107-134">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="8c107-134">The following are the valid values:</span></span>  
  
-   <span data-ttu-id="8c107-135">**“组件失败”**，指示转换失败并且输入数据未插入 Data Quality Services 数据库中。</span><span class="sxs-lookup"><span data-stu-id="8c107-135">**Fail Component**, which indicates that the transformation fails and the input data is not inserted into the Data Quality Services database.</span></span> <span data-ttu-id="8c107-136">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="8c107-136">This is the default value.</span></span>  
  
-   <span data-ttu-id="8c107-137">**“重定向行”**，指示输入数据未插入 Data Quality Services 数据库中并且重定向到错误输出。</span><span class="sxs-lookup"><span data-stu-id="8c107-137">**Redirect Row**, which indicates that the input data is not inserted into the Data Quality Services database and is redirected to the error output.</span></span>  
  
##  <a name="set-options-on-the-mapping-tab"></a><a name="mapping"></a><span data-ttu-id="8c107-138">设置 "映射" 选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="8c107-138">Set options on the Mapping tab</span></span>  
 <span data-ttu-id="8c107-139">有关如何将列映射到复合域的信息，请参阅 [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-139">For information on how to map columns to composite domains, see [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).</span></span>  
  
 <span data-ttu-id="8c107-140">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="8c107-140">**Available Input Columns**</span></span>  
 <span data-ttu-id="8c107-141">列出所连接数据源中的列。</span><span class="sxs-lookup"><span data-stu-id="8c107-141">Lists the columns from the connected data source.</span></span> <span data-ttu-id="8c107-142">选择包含要更正的数据的一个或多个列。</span><span class="sxs-lookup"><span data-stu-id="8c107-142">Select one or more columns that contain data that you want to correct.</span></span>  
  
 <span data-ttu-id="8c107-143">**输入列**</span><span class="sxs-lookup"><span data-stu-id="8c107-143">**Input Column**</span></span>  
 <span data-ttu-id="8c107-144">列出你在“可用输入列”\*\*\*\* 区域中选定的输入列。</span><span class="sxs-lookup"><span data-stu-id="8c107-144">Lists an input column that you selected in the **Available Input Columns** area.</span></span>  
  
 <span data-ttu-id="8c107-145">**Domain**</span><span class="sxs-lookup"><span data-stu-id="8c107-145">**Domain**</span></span>  
 <span data-ttu-id="8c107-146">选择要映射到输入列的域。</span><span class="sxs-lookup"><span data-stu-id="8c107-146">Select a domain to map to the input column.</span></span>  
  
 <span data-ttu-id="8c107-147">**源别名**</span><span class="sxs-lookup"><span data-stu-id="8c107-147">**Source Alias**</span></span>  
 <span data-ttu-id="8c107-148">列出包含原始列值的源列。</span><span class="sxs-lookup"><span data-stu-id="8c107-148">Lists the source column that contains the original column value.</span></span>  
  
 <span data-ttu-id="8c107-149">在该字段中单击可修改列名。</span><span class="sxs-lookup"><span data-stu-id="8c107-149">Click in the field to modify the column name.</span></span>  
  
 <span data-ttu-id="8c107-150">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="8c107-150">**Output Alias**</span></span>  
 <span data-ttu-id="8c107-151">列出“DQS 清除转换”\*\*\*\* 输出的列。</span><span class="sxs-lookup"><span data-stu-id="8c107-151">Lists the column that is outputted by the **DQS Cleansing Transformation**.</span></span> <span data-ttu-id="8c107-152">该列包含原始列值或更正的值。</span><span class="sxs-lookup"><span data-stu-id="8c107-152">The column contains the original column value or the corrected value.</span></span>  
  
 <span data-ttu-id="8c107-153">在该字段中单击可修改列名。</span><span class="sxs-lookup"><span data-stu-id="8c107-153">Click in the field to modify the column name.</span></span>  
  
 <span data-ttu-id="8c107-154">**状态别名**</span><span class="sxs-lookup"><span data-stu-id="8c107-154">**Status Alias**</span></span>  
 <span data-ttu-id="8c107-155">列出包含已更正数据的状态信息的列。</span><span class="sxs-lookup"><span data-stu-id="8c107-155">Lists the column that contains status information for the corrected data.</span></span> <span data-ttu-id="8c107-156">在该字段中单击可修改列名。</span><span class="sxs-lookup"><span data-stu-id="8c107-156">Click in the field to modify the column name.</span></span>  
  
##  <a name="set-options-on-the-advanced-tab"></a><a name="advanced"></a><span data-ttu-id="8c107-157">设置 "高级" 选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="8c107-157">Set options on the Advanced tab</span></span>  
 <span data-ttu-id="8c107-158">**标准化输出**</span><span class="sxs-lookup"><span data-stu-id="8c107-158">**Standardize output**</span></span>  
 <span data-ttu-id="8c107-159">指示是否根据为域定义的输出格式以标准化格式输出数据。</span><span class="sxs-lookup"><span data-stu-id="8c107-159">Indicate whether to output the data in the standardized format based on the output format defined for domains.</span></span> <span data-ttu-id="8c107-160">有关标准化格式的详细信息，请参阅 [数据清理](../../2014/data-quality-services/data-cleansing.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-160">For more information about standardized format, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="8c107-161">**—**</span><span class="sxs-lookup"><span data-stu-id="8c107-161">**Confidence**</span></span>  
 <span data-ttu-id="8c107-162">指示是否包括已更正数据的置信度。</span><span class="sxs-lookup"><span data-stu-id="8c107-162">Indicate whether to include the confidence level for corrected data.</span></span> <span data-ttu-id="8c107-163">置信度指示 DQS 对更正或建议的确信程度。</span><span class="sxs-lookup"><span data-stu-id="8c107-163">The confidence level indicates the extend of certainty of DQS for the correction or suggestion.</span></span> <span data-ttu-id="8c107-164">有关置信度的详细信息，请参阅 [数据清理](../../2014/data-quality-services/data-cleansing.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-164">For more information about confidence levels, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="8c107-165">**Reason**</span><span class="sxs-lookup"><span data-stu-id="8c107-165">**Reason**</span></span>  
 <span data-ttu-id="8c107-166">指示是否包括数据更正的原因。</span><span class="sxs-lookup"><span data-stu-id="8c107-166">Indicate whether to include the reason for the data correction.</span></span>  
  
 <span data-ttu-id="8c107-167">**追加的数据**</span><span class="sxs-lookup"><span data-stu-id="8c107-167">**Appended Data**</span></span>  
 <span data-ttu-id="8c107-168">指示是否输出从现有的引用数据访问接口接收的附加数据。</span><span class="sxs-lookup"><span data-stu-id="8c107-168">Indicate whether to output additional data that is received from an existing reference data provider.</span></span> <span data-ttu-id="8c107-169">有关详细信息，请参阅 [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-169">For more information, see [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md).</span></span>  
  
 <span data-ttu-id="8c107-170">**追加的数据架构**</span><span class="sxs-lookup"><span data-stu-id="8c107-170">**Appended Data Schema**</span></span>  
 <span data-ttu-id="8c107-171">指示是否输出数据架构。</span><span class="sxs-lookup"><span data-stu-id="8c107-171">Indicate whether to output the data schema.</span></span> <span data-ttu-id="8c107-172">有关详细信息，请参阅[将域或复合域附加到引用数据](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-172">For more information, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>  
  
##  <a name="set-the-options-in-the-dqs-cleansing-connection-manager-dialog-box"></a><a name="manager"></a><span data-ttu-id="8c107-173">设置 "DQS 清除连接管理器" 对话框中的选项</span><span class="sxs-lookup"><span data-stu-id="8c107-173">Set the options in the DQS Cleansing Connection Manager dialog box</span></span>  
 <span data-ttu-id="8c107-174">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="8c107-174">**Server name**</span></span>  
 <span data-ttu-id="8c107-175">选择或键入要连接的 DQS 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="8c107-175">Select or type the name of the DQS server that you want to connect to.</span></span> <span data-ttu-id="8c107-176">有关该服务器的详细信息，请参阅 [DQS Administration](../../2014/data-quality-services/dqs-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="8c107-176">For more information about the server, see [DQS Administration](../../2014/data-quality-services/dqs-administration.md).</span></span>  
  
 <span data-ttu-id="8c107-177">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="8c107-177">**Test Connection**</span></span>  
 <span data-ttu-id="8c107-178">单击该选项可以确认您指定的连接是否有效。</span><span class="sxs-lookup"><span data-stu-id="8c107-178">Click to confirm that the connection that you specified is viable.</span></span>  
  
 <span data-ttu-id="8c107-179">您还可以通过执行以下操作从连接区域打开 **“DQS 清除连接管理器”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="8c107-179">You can also open the **DQS Cleansing Connection Manager** dialog box from the connections area, by doing the following:</span></span>  
  
1.  <span data-ttu-id="8c107-180">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开现有的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目或者创建一个新项目。</span><span class="sxs-lookup"><span data-stu-id="8c107-180">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or create a new one.</span></span>  
  
2.  <span data-ttu-id="8c107-181">在连接区域中单击右键，依次单击“新建连接”\*\*\*\* 和“DQS”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c107-181">Right-click in the connections area, click **New Connection**, and then click **DQS**.</span></span>  
  
3.  <span data-ttu-id="8c107-182">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="8c107-182">Click **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c107-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c107-183">See Also</span></span>  
 [<span data-ttu-id="8c107-184">将数据质量规则应用于数据源</span><span class="sxs-lookup"><span data-stu-id="8c107-184">Apply Data Quality Rules to Data Source</span></span>](data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
  
