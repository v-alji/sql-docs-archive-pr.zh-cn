---
title: 任务2：将 Excel 列映射到 DQS 域 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 293b035ff52845959e2c8b70c63df643ae6e3e55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589986"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a><span data-ttu-id="0ba9f-102">任务 2：将 Excel 列映射到 DQS 域</span><span class="sxs-lookup"><span data-stu-id="0ba9f-102">Task 2: Mapping Excel Columns to DQS Domains</span></span>
    
1.  <span data-ttu-id="0ba9f-103">在“映射” \*\*\*\* 页中，为“数据源” \*\*\*\* 选择“Excel 文件” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-103">In the **Map** page, select **Excel File** for **Data Source**.</span></span>  
  
2.  <span data-ttu-id="0ba9f-104">单击 "**浏览**"，选择**Suppliers.xlsx**，并单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-104">Click **Browse**, select **Suppliers.xlsx**, and click **Open**.</span></span>  
  
3.  <span data-ttu-id="0ba9f-105">选择**工作表**的**IncomingSuppliers $** 。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-105">Select **IncomingSuppliers$** for the **Worksheet**.</span></span>  
  
4.  <span data-ttu-id="0ba9f-106">映射列，如下面的表格和屏幕快照中所示。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-106">Map columns as shown in the following table and screenshot.</span></span> <span data-ttu-id="0ba9f-107">创建**状态**域的映射时，单击位于列表上方的工具栏上的 "**添加列映射**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-107">When creating mappings for the **State** domain, click **Add a column mapping** button on the toolbar located just above the list.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="0ba9f-108">你未使用**供应商 ID**列/域进行清理。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-108">You are not using **Supplier ID** column/domain for cleansing.</span></span> <span data-ttu-id="0ba9f-109">稍后将在匹配活动中使用**供应商 ID**域。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-109">You will use the **Supplier ID** domain later in the matching activity.</span></span>  
  
    |<span data-ttu-id="0ba9f-110">Excel 列</span><span class="sxs-lookup"><span data-stu-id="0ba9f-110">Excel column</span></span>|<span data-ttu-id="0ba9f-111">DQS 域</span><span class="sxs-lookup"><span data-stu-id="0ba9f-111">DQS Domain</span></span>|  
    |------------------|----------------|  
    |<span data-ttu-id="0ba9f-112">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="0ba9f-112">Supplier Name</span></span>|<span data-ttu-id="0ba9f-113">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="0ba9f-113">Supplier Name</span></span>|  
    |<span data-ttu-id="0ba9f-114">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="0ba9f-114">ContactEmailAddress</span></span>|<span data-ttu-id="0ba9f-115">联系人电子邮件</span><span class="sxs-lookup"><span data-stu-id="0ba9f-115">Contact Email</span></span>|  
    |<span data-ttu-id="0ba9f-116">Address Line</span><span class="sxs-lookup"><span data-stu-id="0ba9f-116">Address Line</span></span>|<span data-ttu-id="0ba9f-117">Address Line</span><span class="sxs-lookup"><span data-stu-id="0ba9f-117">Address Line</span></span>|  
    |<span data-ttu-id="0ba9f-118">城市</span><span class="sxs-lookup"><span data-stu-id="0ba9f-118">City</span></span>|<span data-ttu-id="0ba9f-119">城市</span><span class="sxs-lookup"><span data-stu-id="0ba9f-119">City</span></span>|  
    |<span data-ttu-id="0ba9f-120">州省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="0ba9f-120">State</span></span>|<span data-ttu-id="0ba9f-121">州省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="0ba9f-121">State</span></span>|  
    |<span data-ttu-id="0ba9f-122">国家 (单击 " \*\*+ (添加列映射) \*\*工具栏添加行) </span><span class="sxs-lookup"><span data-stu-id="0ba9f-122">Country (Click **+(Add a column mapping)** toolbar to add a row)</span></span>|<span data-ttu-id="0ba9f-123">国家/地区</span><span class="sxs-lookup"><span data-stu-id="0ba9f-123">Country</span></span>|  
    |<span data-ttu-id="0ba9f-124">Zip Code</span><span class="sxs-lookup"><span data-stu-id="0ba9f-124">Zip Code</span></span>|<span data-ttu-id="0ba9f-125">Zip</span><span class="sxs-lookup"><span data-stu-id="0ba9f-125">Zip</span></span>|  
  
     <span data-ttu-id="0ba9f-126">![Excel 列到域的映射](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Excel 列到域的映射")</span><span class="sxs-lookup"><span data-stu-id="0ba9f-126">![Mappings of Excel Columns to Domains](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Mappings of Excel Columns to Domains")</span></span>  
  
5.  <span data-ttu-id="0ba9f-127">在 "**地址验证**" 复合域中映射了所有各个域后，复合域会自动参与清理过程。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-127">As you have mapped all the individual domains within the **Address Validation** composite domain, the composite domain automatically participates in the cleansing process.</span></span> <span data-ttu-id="0ba9f-128">单击 "**查看/选择复合域**" 按钮，查看是否自动选择了 "**地址验证**" 复合域，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-128">Click **View/Select Composite Domains** button to see that the **Address Validation** composite domain is automatically selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0ba9f-129">![“查看/选择复合域”对话框](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "“查看/选择复合域”对话框")</span><span class="sxs-lookup"><span data-stu-id="0ba9f-129">![View/Select Composite Domains Dialog Box](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "View/Select Composite Domains Dialog Box")</span></span>  
  
6.  <span data-ttu-id="0ba9f-130">单击 "**下一步**" 切换到 "**清理**" 页。</span><span class="sxs-lookup"><span data-stu-id="0ba9f-130">Click **Next** to switch to the **Cleanse** page.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="0ba9f-131">下一步</span><span class="sxs-lookup"><span data-stu-id="0ba9f-131">Next Step</span></span>  
 [<span data-ttu-id="0ba9f-132">任务 3：对照 Suppliers 知识库清理数据</span><span class="sxs-lookup"><span data-stu-id="0ba9f-132">Task 3: Cleansing Data against the Suppliers Knowledge Base</span></span>](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
