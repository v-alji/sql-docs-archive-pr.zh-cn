---
title: 步骤 3：修改平面文件连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b897f9412a8f2978ebe4137e3e79bf1d28c97844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578308"
---
# <a name="step-3-modifying-the-flat-file-connection-manager"></a><span data-ttu-id="7c6bc-102">步骤 3：修改平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="7c6bc-102">Step 3: Modifying the Flat File Connection Manager</span></span>
  <span data-ttu-id="7c6bc-103">在本任务中，您将修改在第 1 课中创建和配置的平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-103">In this task, you will modify the Flat File connection manager that you created and configured in Lesson 1.</span></span> <span data-ttu-id="7c6bc-104">平面文件连接管理器在最初创建时配置为静态加载单个文件。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-104">When originally created, the Flat File connection manager was configured to statically load a single file.</span></span> <span data-ttu-id="7c6bc-105">若要启用平面文件连接管理器以重复加载文件，必须修改连接管理器的 ConnectionString 属性以接受用户定义的变量 `User:varFileName`，该变量包含要在运行时加载的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-105">To enable the Flat File connection manager to iteratively load files, you must modify the ConnectionString property of the connection manager to accept the user-defined variable `User:varFileName`, which contains the path of the file to be loaded at run time.</span></span>  
  
 <span data-ttu-id="7c6bc-106">通过将连接管理器修改为使用用户定义的变量 `User::varFileName`的值并填充连接管理器的 ConnectionString 属性，连接管理器将能够连接到不同的平面文件。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-106">By modifying the connection manager to use the value of the user-defined variable, `User::varFileName`, to populate the ConnectionString property of the connection manager, the connection manager will be able to connect to different flat files.</span></span> <span data-ttu-id="7c6bc-107">在运行时，Foreach 循环容器的每次迭代都将动态更新 `User::varFileName` 变量。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-107">At run time, each iteration of the Foreach Loop container will dynamically update the `User::varFileName` variable.</span></span> <span data-ttu-id="7c6bc-108">更新变量时，还会使连接管理器连接到不同的平面文件，并使数据流任务处理其他数据集。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-108">Updating the variable, in turn, causes the connection manager to connect to a different flat file, and the data flow task to process a different set of data.</span></span>  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a><span data-ttu-id="7c6bc-109">配置平面文件连接管理器以使用连接字符串的变量</span><span class="sxs-lookup"><span data-stu-id="7c6bc-109">To configure the Flat File connection manager to use a variable for the connection string</span></span>  
  
1.  <span data-ttu-id="7c6bc-110">在 **“连接管理器”** 窗格中，右键单击 **Sample Flat File Source Data**，再选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-110">In the **Connection Managers** pane, right-click **Sample Flat File Source Data**, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="7c6bc-111">在属性窗口中，对于 "**表达式**"，单击空单元格，然后单击省略号按钮 " \*\* ( ... ) \*\*"。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-111">In the Properties window, for **Expressions**, click in the empty cell, and then click the ellipsis button **(...)**.</span></span>  
  
3.  <span data-ttu-id="7c6bc-112">在 "**属性表达式编辑器**" 对话框的 "**属性**" 列中，键入或选择 `ConnectionString` 。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-112">In the **Property Expressions Editor** dialog box, in the **Property** column, type or select `ConnectionString`.</span></span>  
  
4.  <span data-ttu-id="7c6bc-113">在 "**表达式**" 列中，单击省略号按钮 " \*\* ( ..." ) **以打开 "**表达式生成器\*\*" 对话框。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-113">In the **Expression** column, click the ellipsis button **(...)** to open the **Expression Builder** dialog box.</span></span>  
  
5.  <span data-ttu-id="7c6bc-114">在 **“表达式生成器”** 对话框中，展开 **“变量”** 节点。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-114">In the **Expression Builder** dialog box, expand the **Variables** node.</span></span>  
  
6.  <span data-ttu-id="7c6bc-115">将变量 " **User：： varFileName**" 拖到 "**表达式**" 框中。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-115">Drag the variable, **User::varFileName**, into the **Expression** box.</span></span>  
  
7.  <span data-ttu-id="7c6bc-116">单击 **“确定”** 关闭 **“表达式生成器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-116">Click **OK** to close the **Expression Builder** dialog box.</span></span>  
  
8.  <span data-ttu-id="7c6bc-117">再次单击 **“确定”** 关闭 **“属性表达式编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="7c6bc-117">Click **OK** again to close the **Property Expressions Editor** dialog box.</span></span>  
  
## <a name="next-lesson-task"></a><span data-ttu-id="7c6bc-118">下一课程任务</span><span class="sxs-lookup"><span data-stu-id="7c6bc-118">Next Lesson Task</span></span>  
 [<span data-ttu-id="7c6bc-119">步骤 4：测试第 2 课教程包</span><span class="sxs-lookup"><span data-stu-id="7c6bc-119">Step 4: Testing the Lesson 2 Tutorial Package</span></span>](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
