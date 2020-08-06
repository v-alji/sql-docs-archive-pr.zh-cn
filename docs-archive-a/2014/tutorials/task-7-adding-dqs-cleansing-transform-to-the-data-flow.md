---
title: 任务7：将 DQS 清理转换添加到数据流 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 887bc361a51b61e9137404e054bd52e2b630ca5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578571"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a><span data-ttu-id="8ca02-102">任务 7：将 DQS 清理转换添加到数据流</span><span class="sxs-lookup"><span data-stu-id="8ca02-102">Task 7: Adding DQS Cleansing Transform to the Data Flow</span></span>
  <span data-ttu-id="8ca02-103">在本任务中，您将向数据流添加 DQS 清理转换以使用 DQS 清理输入的供应商数据。</span><span class="sxs-lookup"><span data-stu-id="8ca02-103">In this task, you add DQS Cleansing Transform to the data flow to cleanse the input supplier data by using DQS.</span></span> <span data-ttu-id="8ca02-104">有关转换的详细信息，请参阅**[DQS 清理转换](https://msdn.microsoft.com/library/ee677619.aspx)**。</span><span class="sxs-lookup"><span data-stu-id="8ca02-104">See **[DQS Cleansing Transform](https://msdn.microsoft.com/library/ee677619.aspx)** for more details about the transform.</span></span>  
  
1.  <span data-ttu-id="8ca02-105">右键**单击 "数据流**" 选项卡中的 " **DQS 清理**"，然后单击 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="8ca02-105">Right-click **DQS Cleansing** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="8ca02-106">键入 "**清理供应商数据**"，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="8ca02-106">Type **Cleanse Supplier Data**, and press **ENTER**.</span></span>  
  
2.  <span data-ttu-id="8ca02-107">选择 "**从 Excel 文件读取供应商数据**"。拖动蓝色连接器以**清理供应商数据**。</span><span class="sxs-lookup"><span data-stu-id="8ca02-107">Select **Read Supplier Data from Excel File**; drag the blue connector to **Cleanse Supplier Data**.</span></span> <span data-ttu-id="8ca02-108">组件现在已连接。</span><span class="sxs-lookup"><span data-stu-id="8ca02-108">The components are now connected.</span></span>  
  
     <span data-ttu-id="8ca02-109">![读取供应商数据-> 清理供应商数据](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "读取供应商数据 -> 清理供应商数据")</span><span class="sxs-lookup"><span data-stu-id="8ca02-109">![Read Supplier Data -> Cleanse Supplier Data](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "Read Supplier Data -> Cleanse Supplier Data")</span></span>  
  
3.  <span data-ttu-id="8ca02-110">双击 "**清理供应商数据**"。</span><span class="sxs-lookup"><span data-stu-id="8ca02-110">Double-click **Cleanse Supplier Data**.</span></span>  
  
4.  <span data-ttu-id="8ca02-111">在 " **DQS 清理转换编辑器**" 中，单击 "**数据质量连接管理器" 下拉列表**旁边的 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="8ca02-111">In the **DQS Cleansing Transformation Editor**, click **New** next to the **Data Quality Connection Manager drop-down list**.</span></span>  
  
5.  <span data-ttu-id="8ca02-112">在 " **DQS 清除连接管理器**" 对话框中，键入 " \*\* (本地) \*\* " 或 "**句点** (" ) 以连接到本地服务器。</span><span class="sxs-lookup"><span data-stu-id="8ca02-112">In the **DQS Cleansing Connection Manager** dialog box, type **(local)** or **period** (.) to connect to the local server.</span></span> <span data-ttu-id="8ca02-113">本课假定您在本地服务器上安装了 DQS。</span><span class="sxs-lookup"><span data-stu-id="8ca02-113">This lesson assumes that you have DQS installed on a local server.</span></span>  
  
6.  <span data-ttu-id="8ca02-114">单击 "**测试连接**" 以测试与 DQS 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="8ca02-114">Click **Test Connection** to test the connection to DQS server.</span></span>  
  
7.  <span data-ttu-id="8ca02-115">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="8ca02-115">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="8ca02-116">选择**数据质量知识库**的 "**供应商**"。</span><span class="sxs-lookup"><span data-stu-id="8ca02-116">Select **Suppliers** for the **Data Quality Knowledge Base**.</span></span>  
  
     <span data-ttu-id="8ca02-117">![DQS 清理转换编辑器 - 供应商知识库](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS 清理转换编辑器 - 供应商知识库")</span><span class="sxs-lookup"><span data-stu-id="8ca02-117">![DQS Cleansing Transformation Editor - Suppliers KB](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS Cleansing Transformation Editor - Suppliers KB")</span></span>  
  
9. <span data-ttu-id="8ca02-118">切换到顶部的 "**映射**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8ca02-118">Switch to the **Mapping** tab at the top.</span></span>  
  
10. <span data-ttu-id="8ca02-119">在 "**可用输入列**" 中，通过选中相应的复选框来选择**供应商名称**、 **ContactEmailAddress**、**地址行**、**城市**、**省**/市/自治区、**国家/地区**和**邮政编码**。</span><span class="sxs-lookup"><span data-stu-id="8ca02-119">From **Available Input Columns**, select **Supplier Name**, **ContactEmailAddress**, **Address Line**, **City**, **State**, **Country**, and **Zip Code** by selecting the check boxes.</span></span>  
  
     <span data-ttu-id="8ca02-120">![DQS 清理转换编辑器 - 映射](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS 清理转换编辑器 - 映射")</span><span class="sxs-lookup"><span data-stu-id="8ca02-120">![DQS Cleansing Transformation Editor - Mappings](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS Cleansing Transformation Editor - Mappings")</span></span>  
  
11. <span data-ttu-id="8ca02-121">在底部窗格中，使用 "**域**" 列中的下拉列表映射这些列：</span><span class="sxs-lookup"><span data-stu-id="8ca02-121">In the bottom pane, map these columns by using drop-down lists in the **Domain** column:</span></span>  
  
    |<span data-ttu-id="8ca02-122">列</span><span class="sxs-lookup"><span data-stu-id="8ca02-122">Column</span></span>|<span data-ttu-id="8ca02-123">域</span><span class="sxs-lookup"><span data-stu-id="8ca02-123">Domain</span></span>|  
    |------------|------------|  
    |<span data-ttu-id="8ca02-124">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="8ca02-124">Supplier Name</span></span>|<span data-ttu-id="8ca02-125">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="8ca02-125">Supplier Name</span></span>|  
    |<span data-ttu-id="8ca02-126">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="8ca02-126">ContactEmailAddress</span></span>|<span data-ttu-id="8ca02-127">联系人电子邮件</span><span class="sxs-lookup"><span data-stu-id="8ca02-127">Contact Email</span></span>|  
    |<span data-ttu-id="8ca02-128">Address Line</span><span class="sxs-lookup"><span data-stu-id="8ca02-128">Address Line</span></span>|<span data-ttu-id="8ca02-129">Address Line</span><span class="sxs-lookup"><span data-stu-id="8ca02-129">Address Line</span></span>|  
    |<span data-ttu-id="8ca02-130">城市</span><span class="sxs-lookup"><span data-stu-id="8ca02-130">City</span></span>|<span data-ttu-id="8ca02-131">城市</span><span class="sxs-lookup"><span data-stu-id="8ca02-131">City</span></span>|  
    |<span data-ttu-id="8ca02-132">州省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="8ca02-132">State</span></span>|<span data-ttu-id="8ca02-133">州省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="8ca02-133">State</span></span>|  
    |<span data-ttu-id="8ca02-134">国家/地区</span><span class="sxs-lookup"><span data-stu-id="8ca02-134">Country</span></span>|<span data-ttu-id="8ca02-135">国家/地区</span><span class="sxs-lookup"><span data-stu-id="8ca02-135">Country</span></span>|  
    |<span data-ttu-id="8ca02-136">Zip Code</span><span class="sxs-lookup"><span data-stu-id="8ca02-136">Zip Code</span></span>|<span data-ttu-id="8ca02-137">Zip</span><span class="sxs-lookup"><span data-stu-id="8ca02-137">Zip</span></span>|  
  
12. <span data-ttu-id="8ca02-138">单击 **"确定"** 关闭 " **DQS 清理转换编辑器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8ca02-138">Click **OK** to close the **DQS Cleansing Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="8ca02-139">下一步</span><span class="sxs-lookup"><span data-stu-id="8ca02-139">Next Step</span></span>  
 [<span data-ttu-id="8ca02-140">任务 8：添加有条件拆分转换以拆分清理输出</span><span class="sxs-lookup"><span data-stu-id="8ca02-140">Task 8: Adding Conditional Split Transform to Split Cleansing Output</span></span>](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
