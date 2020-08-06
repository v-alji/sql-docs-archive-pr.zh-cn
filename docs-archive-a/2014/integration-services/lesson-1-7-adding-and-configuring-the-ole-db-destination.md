---
title: 步骤 7：添加和配置 OLE DB 目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 442c841d-d528-4bf0-8724-7156f909ee50
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da917ccc4ca756c2442e70477976b5a71f7eb56e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586824"
---
# <a name="step-7-adding-and-configuring-the-ole-db-destination"></a><span data-ttu-id="2f20d-102">步骤 7：添加和配置 OLE DB 目标</span><span class="sxs-lookup"><span data-stu-id="2f20d-102">Step 7: Adding and Configuring the OLE DB Destination</span></span>
  <span data-ttu-id="2f20d-103">现在，您的包可以从平面文件源中提取数据，并将数据转换为与目标兼容的格式。</span><span class="sxs-lookup"><span data-stu-id="2f20d-103">Your package now can extract data from the flat file source and transform that data into a format that is compatible with the destination.</span></span> <span data-ttu-id="2f20d-104">下一个任务是将已转换的数据实际加载到目标。</span><span class="sxs-lookup"><span data-stu-id="2f20d-104">The next task is to actually load the transformed data into the destination.</span></span> <span data-ttu-id="2f20d-105">若要加载数据，您必须将 OLE DB 目标添加到数据流。</span><span class="sxs-lookup"><span data-stu-id="2f20d-105">To load the data, you must add an OLE DB destination to the data flow.</span></span> <span data-ttu-id="2f20d-106">OLE DB 目标可以使用数据库表、视图或 SQL 命令将数据加载到各种 OLE DB 兼容的数据库中。</span><span class="sxs-lookup"><span data-stu-id="2f20d-106">The OLE DB destination can use a database table, view, or an SQL command to load data into a variety of OLE DB-compliant databases.</span></span>  
  
 <span data-ttu-id="2f20d-107">在此过程中，您将添加和配置 OLE DB 目标以使用以前创建的 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="2f20d-107">In this procedure, you add and configure an OLE DB destination to use the OLE DB connection manager that you previously created.</span></span>  
  
### <a name="to-add-and-configure-the-sample-ole-db-destination"></a><span data-ttu-id="2f20d-108">添加和配置示例 OLE DB 目标</span><span class="sxs-lookup"><span data-stu-id="2f20d-108">To add and configure the sample OLE DB destination</span></span>  
  
1.  <span data-ttu-id="2f20d-109">在 " **SSIS 工具箱**" 中，**展开 "** **其他目标**"，然后将**OLE DB "目标**" 拖动到 "数据流" 选项卡的设计图面上。将 OLE DB 目标直接放置在**Lookup Date Key**转换的下面。</span><span class="sxs-lookup"><span data-stu-id="2f20d-109">In the **SSIS Toolbox**, expand **Other Destinations**, and drag **OLE DB Destination** onto the design surface of the **Data Flow** tab. Place the OLE DB destination directly below the **Lookup Date Key** transformation.</span></span>  
  
2.  <span data-ttu-id="2f20d-110">单击“查找日期键”\*\*\*\* 转换，并将绿色箭头拖到新添加的“OLE DB 目标”\*\*\*\* 上，以便将两个组件连接在一起。</span><span class="sxs-lookup"><span data-stu-id="2f20d-110">Click the **Lookup Date Key** transformation and drag the green arrow over to the newly added **OLE DB Destination** to connect the two components together.</span></span>  
  
3.  <span data-ttu-id="2f20d-111">在“选择输入输出”\*\*\*\* 对话框中，单击“输出”\*\*\*\* 列表框中的“查找匹配输出”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f20d-111">In the **Input Output Selection** dialog box, in the **Output** list box, click **Lookup Match Output**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="2f20d-112">在“数据流”\*\*\*\* 设计图面上，在新添加的“OLE DB 目标”\*\*\*\* 组件中单击“OLE DB 目标”\*\*\*\*，然后将名称更改为 **Sample OLE DB Destination**。</span><span class="sxs-lookup"><span data-stu-id="2f20d-112">On the **Data Flow** design surface, click **OLE DB Destination** in the newly added **OLE DB Destination** component, and change the name to **Sample OLE DB Destination**.</span></span>  
  
5.  <span data-ttu-id="2f20d-113">双击 **Sample OLE DB Destination**。</span><span class="sxs-lookup"><span data-stu-id="2f20d-113">Double-click **Sample OLE DB Destination**.</span></span>  
  
6.  <span data-ttu-id="2f20d-114">在“OLE DB 目标编辑器”\*\*\*\* 对话框中，确保已在“OLE DB 连接管理器”\*\*\*\* 框中选中 **localhost.AdventureWorksDW2012**。</span><span class="sxs-lookup"><span data-stu-id="2f20d-114">In the **OLE DB Destination Editor** dialog box, ensure that **localhost.AdventureWorksDW2012** is selected in the **OLE DB Connection manager** box.</span></span>  
  
7.  <span data-ttu-id="2f20d-115">在“表或视图的名称”\*\*\*\* 框中，键入或选择 **[dbo].[FactCurrencyRate]**。</span><span class="sxs-lookup"><span data-stu-id="2f20d-115">In the **Name of the table or the view** box, type or select **[dbo].[FactCurrencyRate]**.</span></span>  
  
8.  <span data-ttu-id="2f20d-116">单击“新建”\*\*\*\* 按钮以创建新表。</span><span class="sxs-lookup"><span data-stu-id="2f20d-116">Click the **New** button to create a new table.</span></span>  <span data-ttu-id="2f20d-117">将脚本中表的名称更改为 **NewFactCurrencyRate**。</span><span class="sxs-lookup"><span data-stu-id="2f20d-117">Change the name of the table in the script to read **NewFactCurrencyRate**.</span></span>  <span data-ttu-id="2f20d-118">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="2f20d-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="2f20d-119">单击“确定”\*\*\*\* 后，该对话框将关闭，“表或视图的名称”\*\*\*\* 将自动更改为 **NewFactCurrencyRate**。</span><span class="sxs-lookup"><span data-stu-id="2f20d-119">Upon clicking **OK**, the dialog will close and the **Name of the table or the view** will automatically change to **NewFactCurrencyRate**.</span></span>  
  
10. <span data-ttu-id="2f20d-120">单击“映射”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f20d-120">Click **Mappings**.</span></span>  
  
11. <span data-ttu-id="2f20d-121">验证 **AverageRate**、 **CurrencyKey**、 **EndOfDayRate**以及 **DateKey** 输入列是否已正确映射到目标列。</span><span class="sxs-lookup"><span data-stu-id="2f20d-121">Verify that the **AverageRate**, **CurrencyKey**, **EndOfDayRate**, and **DateKey** input columns are mapped correctly to the destination columns.</span></span> <span data-ttu-id="2f20d-122">如果映射了同名列，则说明映射正确。</span><span class="sxs-lookup"><span data-stu-id="2f20d-122">If same-named columns are mapped, the mapping is correct.</span></span>  
  
12. <span data-ttu-id="2f20d-123">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="2f20d-123">Click **OK**.</span></span>  
  
13. <span data-ttu-id="2f20d-124">右键单击 **Sample OLE DB Destination** 目标，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f20d-124">Right-click the **Sample OLE DB Destination** destination and click **Properties**.</span></span>  
  
14. <span data-ttu-id="2f20d-125">在属性窗口中，验证 `LocaleID` 属性是否设置为**英语 (美国) \*\* ，并将 `DefaultCodePage` 属性设置为**1252\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f20d-125">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the`DefaultCodePage` property is set to **1252**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2f20d-126">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="2f20d-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2f20d-127">步骤 8：使 Lesson 1 包更易理解</span><span class="sxs-lookup"><span data-stu-id="2f20d-127">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
## <a name="see-also"></a><span data-ttu-id="2f20d-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f20d-128">See Also</span></span>  
 [<span data-ttu-id="2f20d-129">OLE DB 目标</span><span class="sxs-lookup"><span data-stu-id="2f20d-129">OLE DB Destination</span></span>](data-flow/ole-db-destination.md)  
  
  
