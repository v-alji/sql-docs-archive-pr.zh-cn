---
title: 步骤 4：添加平面文件目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eff65f4a94a412d55af8055e302195f87ae4cdb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691309"
---
# <a name="step-4-adding-a-flat-file-destination"></a><span data-ttu-id="e94c3-102">步骤 4：添加平面文件目标</span><span class="sxs-lookup"><span data-stu-id="e94c3-102">Step 4: Adding a Flat File Destination</span></span>
  <span data-ttu-id="e94c3-103">Lookup Currency Key 转换的错误输出将无法执行查找操作的所有数据行重定向到脚本转换。</span><span class="sxs-lookup"><span data-stu-id="e94c3-103">The error output of the Lookup Currency Key transformation redirects to the Script transformation any data rows that failed the lookup operation.</span></span> <span data-ttu-id="e94c3-104">为了突显相关错误的信息，脚本转换将运行可获取错误说明的脚本。</span><span class="sxs-lookup"><span data-stu-id="e94c3-104">To enhance information about the errors that occurred, the Script transformation runs a script that gets the description of errors.</span></span>  
  
 <span data-ttu-id="e94c3-105">在本任务中，请将有关失败行的所有这些信息保存到分隔的文件中，以便进行后续处理。</span><span class="sxs-lookup"><span data-stu-id="e94c3-105">In this task, you will save all this information about the failed rows to a delimited file for later processing.</span></span> <span data-ttu-id="e94c3-106">若要保存失败的行，必须为将包含错误数据和平面文件目标的文本文件添加并配置平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e94c3-106">To save the failed rows, you must add and configure a Flat File connection manager for the text file that will contain the error data and a Flat File destination.</span></span> <span data-ttu-id="e94c3-107">通过设置平面文件目标所用平面文件连接管理器的属性，可以指定平面文件目标如何格式化和写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="e94c3-107">By setting properties on the Flat File connection manager that the Flat File destination uses, you can specify how the Flat File destination formats and writes the text file.</span></span> <span data-ttu-id="e94c3-108">有关详细信息，请参阅[平面文件连接管理器](connection-manager/file-connection-manager.md)和[平面文件目标](data-flow/flat-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="e94c3-108">For more information, see [Flat File Connection Manager](connection-manager/file-connection-manager.md) and [Flat File Destination](data-flow/flat-file-destination.md).</span></span>  
  
### <a name="to-add-and-configure-a-flat-file-destination"></a><span data-ttu-id="e94c3-109">添加并配置平面文件目标</span><span class="sxs-lookup"><span data-stu-id="e94c3-109">To add and configure a Flat File destination</span></span>  
  
1.  <span data-ttu-id="e94c3-110">单击 **“数据流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e94c3-110">Click the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="e94c3-111">在“SSIS 工具箱”\*\*\*\* 中，展开“其他”\*\*\*\*，然后将“平面文件目标”\*\*\*\* 拖动到数据流设计图面上。</span><span class="sxs-lookup"><span data-stu-id="e94c3-111">In the **SSIS Toolbox**, expand **Other**, and drag **Flat File Destination** onto the data flow design surface.</span></span> <span data-ttu-id="e94c3-112">将“平面文件目标”  直接放在“获取错误说明”  转换的下面。</span><span class="sxs-lookup"><span data-stu-id="e94c3-112">Put the **Flat File Destination** directly underneath the **Get Error Description** transformation.</span></span>  
  
3.  <span data-ttu-id="e94c3-113">单击“获取错误说明”\*\*\*\* 转换，然后将绿色箭头拖动到新的“平面文件目标”\*\*\*\* 上。</span><span class="sxs-lookup"><span data-stu-id="e94c3-113">Click the **Get Error Description** transformation, and then drag the green arrow onto the new **Flat File Destination**.</span></span>  
  
4.  <span data-ttu-id="e94c3-114">在“数据流”\*\*\*\* 设计图面上，在新添加的“平面文件目标”\*\*\*\* 转换中单击“平面文件目标”\*\*\*\*，然后将该名称更改为 **Failed Rows**。</span><span class="sxs-lookup"><span data-stu-id="e94c3-114">On the **Data Flow** design surface, click **Flat File Destination** in the newly added **Flat File Destination** transformation, and change the name to **Failed Rows**.</span></span>  
  
5.  <span data-ttu-id="e94c3-115">右键单击 **Failed Rows** 转换，再单击“编辑”\*\*\*\*，然后在”平面文件目标编辑器”\*\*\*\* 中单击“新建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e94c3-115">Right-click the **Failed Rows** transformation, click **Edit**, and then in the **Flat File Destination Editor**, click **New**.</span></span>  
  
6.  <span data-ttu-id="e94c3-116">在“平面文件格式”\*\*\*\* 对话框中，确认已选中“带分隔符”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e94c3-116">In the **Flat File Format** dialog box, verify that **Delimited** is selected, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="e94c3-117">在 "**平面文件连接管理器编辑器**" 的 "**连接管理器名称**" 框中，键入 `Error Data` 。</span><span class="sxs-lookup"><span data-stu-id="e94c3-117">In the **Flat File Connection Manager Editor**, in the **Connection Manager Name** box type `Error Data`.</span></span>  
  
8.  <span data-ttu-id="e94c3-118">在“平面文件连接管理器编辑器”\*\*\*\* 对话框中，单击“浏览”\*\*\*\*，然后找到存储文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="e94c3-118">In the **Flat File Connection Manager Editor** dialog box, click **Browse**, and locate the folder in which to store the file.</span></span>  
  
9. <span data-ttu-id="e94c3-119">在 "**打开**" 对话框中，**为 "文件名"** 键入 `ErrorOutput.txt` ，然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="e94c3-119">In the **Open** dialog box, for **File name**, type `ErrorOutput.txt`, and then click **Open**.</span></span>  
  
10. <span data-ttu-id="e94c3-120">在“平面文件连接管理器编辑器”\*\*\*\* 对话框中，验证“区域设置”\*\*\*\* 框是否包含“英语(美国)”，“代码页”\*\*\*\* 是否包含 1252 (ANSI -Latin I)。</span><span class="sxs-lookup"><span data-stu-id="e94c3-120">In the **Flat File Connection Manager Editor** dialog box, verify that the **Locale** box contains English (United States) and **Code page** contains 1252 (ANSI -Latin I).</span></span>  
  
11. <span data-ttu-id="e94c3-121">在“选项”窗格中，单击“列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e94c3-121">In the options pane, click **Columns**.</span></span>  
  
     <span data-ttu-id="e94c3-122">注意，除了源数据文件中的列以外，还存在三个新列：ErrorCode、ErrorColumn 和 ErrorDescription。</span><span class="sxs-lookup"><span data-stu-id="e94c3-122">Notice that, in addition to the columns from the source data file, three new columns are present: ErrorCode, ErrorColumn, and ErrorDescription.</span></span> <span data-ttu-id="e94c3-123">这三列由 Lookup Currency Key 转换的错误输出和获取错误说明转换中的脚本生成，可用于排查失败行的原因。</span><span class="sxs-lookup"><span data-stu-id="e94c3-123">These columns are generated by the error output of the Lookup Currency Key transformation and by the script in the Get Error Description transformation, and can be used to troubleshoot the cause of the failed row.</span></span>  
  
12. <span data-ttu-id="e94c3-124">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="e94c3-124">Click **OK**.</span></span>  
  
13. <span data-ttu-id="e94c3-125">在“平面文件目标编辑器”\*\*\*\* 中，清除“覆盖文件中的数据”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="e94c3-125">In the **Flat File Destination Editor**, clear the **Overwrite data in the file** check box.</span></span>  
  
     <span data-ttu-id="e94c3-126">清除该复选框可使错误在执行多个包的过程中持续存在。</span><span class="sxs-lookup"><span data-stu-id="e94c3-126">Clearing this check box persists the errors over multiple package executions.</span></span>  
  
14. <span data-ttu-id="e94c3-127">在“平面文件目标编辑器”\*\*\*\* 中，单击“映射”\*\*\*\* 来验证所有列是否正确。</span><span class="sxs-lookup"><span data-stu-id="e94c3-127">In the **Flat File Destination Editor**, click **Mappings** to verify that all the columns are correct.</span></span> <span data-ttu-id="e94c3-128">您也可以选择重命名目标中的列。</span><span class="sxs-lookup"><span data-stu-id="e94c3-128">Optionally, you can rename the columns in the destination.</span></span>  
  
15. <span data-ttu-id="e94c3-129">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="e94c3-129">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e94c3-130">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e94c3-130">Next Steps</span></span>  
 [<span data-ttu-id="e94c3-131">步骤 5：测试第 4 课教程包</span><span class="sxs-lookup"><span data-stu-id="e94c3-131">Step 5: Testing the Lesson 4 Tutorial Package</span></span>](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  
