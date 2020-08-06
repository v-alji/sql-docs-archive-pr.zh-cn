---
title: 步骤 5：添加并配置平面文件源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 504cfb4bc722627eb8ee70ec1f2c562cef8f1f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586827"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a><span data-ttu-id="fa624-102">步骤 5：添加并配置平面文件源</span><span class="sxs-lookup"><span data-stu-id="fa624-102">Step 5: Adding and Configuring the Flat File Source</span></span>
  <span data-ttu-id="fa624-103">在此任务中，将向包中添加一个平面文件源并对其进行配置。</span><span class="sxs-lookup"><span data-stu-id="fa624-103">In this task, you will add and configure a Flat File source to your package.</span></span> <span data-ttu-id="fa624-104">平面文件源是一个数据流组件，它使用平面文件连接管理器定义的元数据来指定转换过程要从此平面文件中提取的数据的格式和结构。</span><span class="sxs-lookup"><span data-stu-id="fa624-104">A Flat File source is a data flow component that uses metadata defined by a Flat File connection manager to specify the format and structure of the data to be extracted from the flat file by a transform process.</span></span> <span data-ttu-id="fa624-105">可以通过使用平面文件连接管理器提供的文件格式定义将平面文件源配置为从单个平面文件提取数据。</span><span class="sxs-lookup"><span data-stu-id="fa624-105">The Flat File source can be configured to extract data from a single flat file by using the file format definition provided by the Flat File connection manager.</span></span>  
  
 <span data-ttu-id="fa624-106">在本教程中，您将把平面文件源配置为使用 `Sample Flat File Source Data` 您之前创建的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="fa624-106">For this tutorial, you will configure the Flat File source to use the `Sample Flat File Source Data` connection manager that you previously created.</span></span>  
  
### <a name="to-add-a-flat-file-source-component"></a><span data-ttu-id="fa624-107">添加平面文件源组件</span><span class="sxs-lookup"><span data-stu-id="fa624-107">To add a Flat File Source component</span></span>  
  
1.  <span data-ttu-id="fa624-108">通过双击**Data Flow**数据流 `Extract Sample Currency Data` 任务或单击 "数据流"**选项卡**，打开 "数据流设计器"。</span><span class="sxs-lookup"><span data-stu-id="fa624-108">Open the **Data Flow** designer, either by double-clicking the `Extract Sample Currency Data` data flow task or by clicking the **Data Flow tab**.</span></span>  
  
2.  <span data-ttu-id="fa624-109">在“SSIS 工具箱”\*\*\*\* 中，展开 **OtherSources**，然后将“平面文件源”\*\*\*\* 拖动到“数据流”\*\*\*\* 选项卡的设计图面上。</span><span class="sxs-lookup"><span data-stu-id="fa624-109">In the **SSIS Toolbox**, expand **OtherSources**, and then drag a **Flat File Source** onto the design surface of the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="fa624-110">在 "**数据流" 设计图面**上，右键单击新添加的 "**平面文件源**"，单击 "**重命名**"，然后将名称更改为 `Extract Sample Currency Data` 。</span><span class="sxs-lookup"><span data-stu-id="fa624-110">On the **Data Flow** design surface, right-click the newly added **Flat File Source**, click **Rename**, and change the name to `Extract Sample Currency Data`.</span></span>  
  
4.  <span data-ttu-id="fa624-111">双击此平面文件源，打开“平面文件源编辑器”对话框。</span><span class="sxs-lookup"><span data-stu-id="fa624-111">Double-click the Flat File source to open the Flat File Source Editor dialog box.</span></span>  
  
5.  <span data-ttu-id="fa624-112">在 "**平面文件连接管理器**" 框中，选择 `Sample Flat File Source Data` 。</span><span class="sxs-lookup"><span data-stu-id="fa624-112">In the **Flat file connection manager** box, select `Sample Flat File Source Data`.</span></span>  
  
6.  <span data-ttu-id="fa624-113">单击“列”\*\*\*\* 并验证列名是否正确。</span><span class="sxs-lookup"><span data-stu-id="fa624-113">Click **Columns** and verify that the names of the columns are correct.</span></span>  
  
7.  <span data-ttu-id="fa624-114">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="fa624-114">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="fa624-115">右键单击“平面文件源”并单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa624-115">Right-click the Flat File source and click **Properties**.</span></span>  
  
9. <span data-ttu-id="fa624-116">在属性窗口中，验证 `LocaleID` 属性是否设置为\*\*英语 (美国) \*\*。</span><span class="sxs-lookup"><span data-stu-id="fa624-116">In the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fa624-117">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="fa624-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fa624-118">步骤 6：添加并配置查找转换</span><span class="sxs-lookup"><span data-stu-id="fa624-118">Step 6: Adding and Configuring the Lookup Transformations</span></span>](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="fa624-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa624-119">See Also</span></span>  
 <span data-ttu-id="fa624-120">[平面文件源](data-flow/flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="fa624-120">[Flat File Source](data-flow/flat-file-source.md) </span></span>  
 [<span data-ttu-id="fa624-121">平面文件连接管理器编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="fa624-121">Flat File Connection Manager Editor &#40;General Page&#41;</span></span>](general-page-of-integration-services-designers-options.md)  
  
  
