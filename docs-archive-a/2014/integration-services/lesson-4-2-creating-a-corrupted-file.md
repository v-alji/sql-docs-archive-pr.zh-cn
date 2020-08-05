---
title: 步骤 2：创建损坏的文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd5fbe942774192881489e9ea430672f9da5083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581369"
---
# <a name="step-2-creating-a-corrupted-file"></a><span data-ttu-id="ab4e9-102">步骤 2：创建损坏的文件</span><span class="sxs-lookup"><span data-stu-id="ab4e9-102">Step 2: Creating a Corrupted File</span></span>
  <span data-ttu-id="ab4e9-103">为阐释如何配置和处理转换错误，必须创建一个在处理时导致组件失败的示例平面文件。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-103">In order to demonstrate the configuration and handling of transformation errors, you will have to create a sample flat file that when processed causes a component to fail.</span></span>  
  
 <span data-ttu-id="ab4e9-104">在本任务中，将创建现有示例平面文件的一个副本。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-104">In this task, you will create a copy of an existing sample flat file.</span></span> <span data-ttu-id="ab4e9-105">然后，用记事本打开该文件，编辑 **CurrencyID** 列，以确保该列在转换查找期间无法生成匹配项。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-105">You will then open the file in Notepad and edit the **CurrencyID** column to ensure that it will fail to produce a match during the transformations lookup.</span></span> <span data-ttu-id="ab4e9-106">处理新文件时，查找失败将导致 Currency Key 查找转换失败，因此，包的剩余部分将失败。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-106">When the new file is processed, the lookup failure will cause the Currency Key Lookup transformation to fail and therefore fail the rest of the package.</span></span> <span data-ttu-id="ab4e9-107">创建了损坏的示例文件后，将运行包以查看包失败的情况。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-107">After you have created the corrupted sample file, you will run the package to view the package failure.</span></span>  
  
### <a name="to-create-a-corrupted-sample-flat-file"></a><span data-ttu-id="ab4e9-108">创建损坏的示例平面文件</span><span class="sxs-lookup"><span data-stu-id="ab4e9-108">To create a corrupted sample flat file</span></span>  
  
1.  <span data-ttu-id="ab4e9-109">在记事本或任何其他文本编辑器中，打开 Currency_VEB.txt 文件。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-109">In Notepad or any other text editor, open the Currency_VEB.txt file.</span></span>  
  
     <span data-ttu-id="ab4e9-110">示例数据与 SSIS 课程包一起提供。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-110">The sample data is included with the SSIS Lesson packages.</span></span> <span data-ttu-id="ab4e9-111">要下载示例数据和课程包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ab4e9-111">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="ab4e9-112">导航到[Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkID=267527)。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-112">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=267527).</span></span>  
  
    2.  <span data-ttu-id="ab4e9-113">单击 "**下载**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-113">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="ab4e9-114">单击 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-114">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
2.  <span data-ttu-id="ab4e9-115">使用文本编辑器的查找和替换功能可查找的所有实例 `VEB` ，并将其替换为 `BAD` 。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-115">Use the text editor's find and replace feature to find all instances of `VEB` and replace them with `BAD`.</span></span>  
  
3.  <span data-ttu-id="ab4e9-116">在与其他示例数据文件相同的文件夹中，将修改后的文件另存为 `Currency_BAD.txt` 。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-116">In the same folder as the other sample data files, save the modified file as `Currency_BAD.txt`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ab4e9-117">请确保与 `Currency_BAD.txt` 其他示例数据文件保存在同一文件夹中。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-117">Make sure that `Currency_BAD.txt` is saved the same folder as the other sample data files.</span></span>  
  
4.  <span data-ttu-id="ab4e9-118">关闭文本编辑器。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-118">Close your text editor.</span></span>  
  
### <a name="to-verify-that-an-error-will-occur-during-run-time"></a><span data-ttu-id="ab4e9-119">验证是否将在运行时发生错误</span><span class="sxs-lookup"><span data-stu-id="ab4e9-119">To verify that an error will occur during run time</span></span>  
  
1.  <span data-ttu-id="ab4e9-120">在“调试”菜单上，单击“开始调试”。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-120">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="ab4e9-121">在数据流第三次迭代时，Lookup Currency Key 转换将尝试处理 Currency_BAD.txt 文件，并且该转换将失败。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-121">On the third iteration of the data flow, the Lookup Currency Key transformation tries to process the Currency_BAD.txt file, and the transformation will fail.</span></span> <span data-ttu-id="ab4e9-122">转换失败将导致整个包失败。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-122">The failure of the transformation will cause the whole package to fail.</span></span>  
  
2.  <span data-ttu-id="ab4e9-123">在“调试”菜单上，单击“停止调试”。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-123">On the **Debug** menu, click **Stop Debugging**.</span></span>  
  
3.  <span data-ttu-id="ab4e9-124">在设计图面上，单击“执行结果”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-124">On the design surface, click the **Execution Results** tab.</span></span>  
  
4.  <span data-ttu-id="ab4e9-125">浏览日志，确认是否发生了以下未处理的错误：</span><span class="sxs-lookup"><span data-stu-id="ab4e9-125">Browse through the log and verify that the following unhandled error occurred:</span></span>  
  
     `[Lookup Currency Key[27]] Error: Row yielded no match during lookup.`  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab4e9-126">数字 27 为组件的 ID。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-126">The number 27 is the ID of the component.</span></span> <span data-ttu-id="ab4e9-127">该值在生成数据流时进行分配，可能与包中的值不同。</span><span class="sxs-lookup"><span data-stu-id="ab4e9-127">This value is assigned when you build the data flow, and the value in your package may be different.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ab4e9-128">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ab4e9-128">Next Steps</span></span>  
 [<span data-ttu-id="ab4e9-129">步骤 3：添加错误流重定向</span><span class="sxs-lookup"><span data-stu-id="ab4e9-129">Step 3: Adding Error Flow Redirection</span></span>](lesson-4-3-adding-error-flow-redirection.md)  
  
  
