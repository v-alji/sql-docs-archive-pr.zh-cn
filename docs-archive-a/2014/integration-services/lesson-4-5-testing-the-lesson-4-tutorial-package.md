---
title: 步骤 5：测试第 4 课教程包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a897f99bf68805e4e66c3b6bbe818b312077fb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691306"
---
# <a name="step-5-testing-the-lesson-4-tutorial-package"></a><span data-ttu-id="e59e3-102">步骤 5：测试第 4 课教程包</span><span class="sxs-lookup"><span data-stu-id="e59e3-102">Step 5: Testing the Lesson 4 Tutorial Package</span></span>
  <span data-ttu-id="e59e3-103">在运行时，损坏的文件 Currency_BAD.txt 将无法在 Currency Key 查找转换中生成匹配。</span><span class="sxs-lookup"><span data-stu-id="e59e3-103">At run time, the corrupted file, Currency_BAD.txt, will fail to generate a match within the Currency Key Lookup transformation.</span></span> <span data-ttu-id="e59e3-104">由于 Currency Key 查找的错误输出现在已配置为将失败的行重定向到新的失败的行目标，因此该组件不会失败，并且包会成功地运行。</span><span class="sxs-lookup"><span data-stu-id="e59e3-104">Because the error output of Currency Key Lookup has now been configured to redirect failed rows to the new Failed Rows destination, the component does not fail, and the package runs successfully.</span></span> <span data-ttu-id="e59e3-105">所有失败的错误行都将写入 ErrorOutput.txt。</span><span class="sxs-lookup"><span data-stu-id="e59e3-105">All failed error rows are written to ErrorOutput.txt.</span></span>  
  
 <span data-ttu-id="e59e3-106">在此任务中，您将通过运行该包对已修改的错误输出配置进行测试。</span><span class="sxs-lookup"><span data-stu-id="e59e3-106">In this task, you will test the revised error output configuration by running the package.</span></span> <span data-ttu-id="e59e3-107">包成功执行后，您将查看 ErrorOutput.txt 文件的内容。</span><span class="sxs-lookup"><span data-stu-id="e59e3-107">Upon successful package execution, you will then view the contents of the ErrorOutput.txt file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e59e3-108">如果不需要在 ErrorOutput.txt 文件中积累错误行，则应在包的运行间隔手动删除文件内容。</span><span class="sxs-lookup"><span data-stu-id="e59e3-108">If you do not want to accumulate error rows in the ErrorOutput.txt file, you should manually delete the file content between package runs.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="e59e3-109">检查包布局</span><span class="sxs-lookup"><span data-stu-id="e59e3-109">Checking the Package layout</span></span>  
 <span data-ttu-id="e59e3-110">测试包之前，应当确保第 4 课包中的控制流和数据流包含下列关系图中显示的对象。</span><span class="sxs-lookup"><span data-stu-id="e59e3-110">Before you test the package you should verify that the control flow and the data flow in the Lesson 4 package contain the objects shown in the following diagrams.</span></span> <span data-ttu-id="e59e3-111">控制流应与第 2 到第 4 课中的控制流相同。</span><span class="sxs-lookup"><span data-stu-id="e59e3-111">The control flow should be identical to the control flow in lessons 2 - 4.</span></span>  
  
 <span data-ttu-id="e59e3-112">**控制流**</span><span class="sxs-lookup"><span data-stu-id="e59e3-112">**Control Flow**</span></span>  
  
 <span data-ttu-id="e59e3-113">![包中的控制流](../../2014/tutorials/media/task4lesson2control.gif "包中的控制流")</span><span class="sxs-lookup"><span data-stu-id="e59e3-113">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="e59e3-114">**数据流**</span><span class="sxs-lookup"><span data-stu-id="e59e3-114">**Data Flow**</span></span>  
  
 <span data-ttu-id="e59e3-115">![包中的数据流](../../2014/tutorials/media/task5lesson5data.gif "包中的数据流")</span><span class="sxs-lookup"><span data-stu-id="e59e3-115">![Data flow in package](../../2014/tutorials/media/task5lesson5data.gif "Data flow in package")</span></span>  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a><span data-ttu-id="e59e3-116">运行第 4 课教程包</span><span class="sxs-lookup"><span data-stu-id="e59e3-116">To run the Lesson 4 tutorial package</span></span>  
  
1.  <span data-ttu-id="e59e3-117">在“调试”菜单上，单击“开始调试”。</span><span class="sxs-lookup"><span data-stu-id="e59e3-117">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
2.  <span data-ttu-id="e59e3-118">当包运行完毕后，在 **“调试”** 菜单中，单击 **“停止调试”**。</span><span class="sxs-lookup"><span data-stu-id="e59e3-118">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a><span data-ttu-id="e59e3-119">验证 ErrorOutput.txt 文件的内容</span><span class="sxs-lookup"><span data-stu-id="e59e3-119">To verify the contents of the ErrorOutput.txt file</span></span>  
  
-   <span data-ttu-id="e59e3-120">在记事本或任何其他文本编辑器中，打开 ErrorOutput.txt 文件。</span><span class="sxs-lookup"><span data-stu-id="e59e3-120">In Notepad or any other text editor, open the ErrorOutput.txt file.</span></span> <span data-ttu-id="e59e3-121">默认的列顺序为：AverageRate、CurrencyID、CurrencyDate、EndOfDateRate、ErrorCode、ErrorColumn、ErrorDescription。</span><span class="sxs-lookup"><span data-stu-id="e59e3-121">The default column order is: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.</span></span>  
  
     <span data-ttu-id="e59e3-122">请注意，文件中的所有行都包含不匹配的 CurrencyID 值 BAD、ErrorCode 值 -1071607778、ErrorColumn 值 0 以及 ErrorDescription 值“在查找期间行没有生成任何匹配项”。</span><span class="sxs-lookup"><span data-stu-id="e59e3-122">Notice that all the rows in the file contain the unmatched CurrencyID value of BAD, the ErrorCode value of -1071607778, the ErrorColumn value of 0, and the ErrorDescription value "Row yielded no match during lookup".</span></span> <span data-ttu-id="e59e3-123">由于此错误并不是列所特有的，所以 ErrorColumn 的值设置为 0。</span><span class="sxs-lookup"><span data-stu-id="e59e3-123">The value of the ErrorColumn is set to 0 because the error is not column specific.</span></span> <span data-ttu-id="e59e3-124">它是已失败的查找操作。</span><span class="sxs-lookup"><span data-stu-id="e59e3-124">It is the lookup operation that failed.</span></span> <span data-ttu-id="e59e3-125">.</span><span class="sxs-lookup"><span data-stu-id="e59e3-125">.</span></span>  
  
  
