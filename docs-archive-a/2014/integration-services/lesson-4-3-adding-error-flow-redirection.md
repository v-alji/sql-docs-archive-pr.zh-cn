---
title: 步骤 3：添加错误流重定向 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5683a45d-9e73-4cd5-83ca-fae8b26b488c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ceaea310cba05a940f310c01b52d5f912a53bea8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581370"
---
# <a name="step-3-adding-error-flow-redirection"></a><span data-ttu-id="750e2-102">步骤 3：添加错误流重定向</span><span class="sxs-lookup"><span data-stu-id="750e2-102">Step 3: Adding Error Flow Redirection</span></span>
  <span data-ttu-id="750e2-103">如上一个任务中所示，当 Lookup Currency Key 转换尝试对产生错误的已损坏示例平面文件进行处理时，该转换无法生成匹配。</span><span class="sxs-lookup"><span data-stu-id="750e2-103">As demonstrated in the previous task, the Lookup Currency Key transformation cannot generate a match when the transformation tries to process the corrupted sample flat file, which produced an error.</span></span> <span data-ttu-id="750e2-104">由于转换针对错误输出使用了默认设置，因此，任何错误都将导致该转换失败。</span><span class="sxs-lookup"><span data-stu-id="750e2-104">Because the transformation uses the default settings for error output, any error causes the transformation to fail.</span></span> <span data-ttu-id="750e2-105">当转换失败时，该包的其余部分也将失败。</span><span class="sxs-lookup"><span data-stu-id="750e2-105">When the transformation fails, the rest of the package also fails.</span></span>  
  
 <span data-ttu-id="750e2-106">可以使用错误输出将组件配置为将失败的行重定向到其他处理路径，而不是允许转换失败。</span><span class="sxs-lookup"><span data-stu-id="750e2-106">Instead of permitting the transformation to fail, you can configure the component to redirect the failed row to another processing path by using the error output.</span></span> <span data-ttu-id="750e2-107">使用单独的错误处理路径，您可以执行多项任务。</span><span class="sxs-lookup"><span data-stu-id="750e2-107">Use of a separate error processing path lets you do a number of things.</span></span> <span data-ttu-id="750e2-108">例如，您可能要尝试清除该数据，然后重新处理失败的行。</span><span class="sxs-lookup"><span data-stu-id="750e2-108">For instance, you might try to clean the data and then reprocess the failed row.</span></span> <span data-ttu-id="750e2-109">或者，您可能要将失败的行与其他错误信息保存在一起，以便以后进行验证和重新处理。</span><span class="sxs-lookup"><span data-stu-id="750e2-109">Or, you might save the failed row along with additional error information for later verification and reprocessing.</span></span>  
  
 <span data-ttu-id="750e2-110">在本任务中，您将 Lookup Currency Key 转换配置为将所有失败的行重定向到错误输出。</span><span class="sxs-lookup"><span data-stu-id="750e2-110">In this task, you will configure the Lookup Currency Key transformation to redirect any rows that fail to the error output.</span></span> <span data-ttu-id="750e2-111">在数据流的错误分支中，这些行将被写入文件中。</span><span class="sxs-lookup"><span data-stu-id="750e2-111">In the error branch of the data flow, these rows will be written to a file.</span></span>  
  
 <span data-ttu-id="750e2-112">默认情况下，错误输出中的另外两列 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] **ErrorCode**和**ErrorColumn**只包含表示错误号的数值代码以及出现错误的列的 ID。</span><span class="sxs-lookup"><span data-stu-id="750e2-112">By default the two extra columns in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] error output, **ErrorCode** and **ErrorColumn**, contain only numeric codes that represent an error number, and the ID of the column in which the error occurred.</span></span> <span data-ttu-id="750e2-113">如果没有相应的错误说明，这些数值没有多大用处。</span><span class="sxs-lookup"><span data-stu-id="750e2-113">These numeric values may be of limited use without the corresponding error description.</span></span>  
  
 <span data-ttu-id="750e2-114">若要更有效地使用错误输出，请在包将失败的行写入文件之前，使用脚本组件来访问 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] API，然后获取错误说明。</span><span class="sxs-lookup"><span data-stu-id="750e2-114">To enhance the usefulness of the error output, before the package writes the failed rows to the file, you will use a Script component to access the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] API and get a description of the error.</span></span>  
  
### <a name="to-configure-an-error-output"></a><span data-ttu-id="750e2-115">配置错误输出</span><span class="sxs-lookup"><span data-stu-id="750e2-115">To configure an error output</span></span>  
  
1.  <span data-ttu-id="750e2-116">在 " **SSIS 工具箱**" 中，展开 "**常规**"，然后将 "**脚本组件**" 拖到 "数据流" 选项卡的设计图**面上。** 将**脚本**放置在**Lookup Currency Key**转换的右侧。</span><span class="sxs-lookup"><span data-stu-id="750e2-116">In the **SSIS Toolbox**, expand **Common**, and then drag **Script Component** onto the design surface of the **Data Flow** tab. Place **Script** to the right of the **Lookup Currency Key** transformation.</span></span>  
  
2.  <span data-ttu-id="750e2-117">在“选择脚本组件类型”\*\*\*\* 对话框中，单击“转换”\*\*\*\*，再单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="750e2-117">In the **Select Script Component Type** dialog box, click **Transformation**, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="750e2-118">单击“Lookup Currency Key”\*\*\*\* 转换，并将红色箭头拖动到新添加的“脚本”\*\*\*\* 转换中，以连接这两个组件。</span><span class="sxs-lookup"><span data-stu-id="750e2-118">Click the **Lookup Currency Key** transformation and then drag the red arrow onto the newly added **Script** transformation to connect the two components.</span></span>  
  
     <span data-ttu-id="750e2-119">红色箭头表示“Lookup Currency Key”\*\*\*\* 转换的错误输出。</span><span class="sxs-lookup"><span data-stu-id="750e2-119">The red arrow represents the error output of the **Lookup Currency Key** transformation.</span></span> <span data-ttu-id="750e2-120">通过使用红色箭头将转换连接到脚本组件，您可以将所有处理错误重定向到脚本组件，然后，该组件会处理这些错误并将它们发送到目标。</span><span class="sxs-lookup"><span data-stu-id="750e2-120">By using the red arrow to connect the transformation to the Script component, you can redirect any processing errors to the Script component, which then processes the errors and sends them to the destination.</span></span>  
  
4.  <span data-ttu-id="750e2-121">在“配置错误输出”\*\*\*\* 对话框的“错误”\*\*\*\* 列中，选择“重定向行”\*\*\*\*，再单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="750e2-121">In the **Configure Error Output** dialog box, in the **Error** column, select **Redirect row**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="750e2-122">在“数据流”\*\*\*\* 设计图面上，在新添加的“ScriptComponent”\*\*\*\* 中单击“ScriptComponent”\*\*\*\*，然后将该名称更改为Get Error Description”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="750e2-122">On the **Data Flow** design surface, click **Script Component** in the newly added **ScriptComponent**, and change the name to **Get Error Description**.</span></span>  
  
6.  <span data-ttu-id="750e2-123">双击“Get Error Description”\*\*\*\* 转换。</span><span class="sxs-lookup"><span data-stu-id="750e2-123">Double-click the **Get Error Description** transformation.</span></span>  
  
7.  <span data-ttu-id="750e2-124">在“脚本转换编辑器”\*\*\*\* 对话框中的“输入列”\*\*\*\* 页中，选择“ErrorCode”\*\*\*\* 列。</span><span class="sxs-lookup"><span data-stu-id="750e2-124">In the **Script Transformation Editor** dialog box, on the **Input Columns** page, select the **ErrorCode** column.</span></span>  
  
8.  <span data-ttu-id="750e2-125">在“输入和输出”\*\*\*\* 页中，展开“输出 0”\*\*\*\*，单击“输出列”\*\*\*\*，再单击“添加列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="750e2-125">On the **Inputs and Outputs** page, expand **Output 0**, click **Output Columns**, and then click **Add Column**.</span></span>  
  
9. <span data-ttu-id="750e2-126">在 `Name` 属性中，键入**ErrorDescription**并将 `DataType` 属性设置为**Unicode string [DT_WSTR]**。</span><span class="sxs-lookup"><span data-stu-id="750e2-126">In the `Name` property, type **ErrorDescription** and set the `DataType` property to **Unicode string [DT_WSTR]**.</span></span>  
  
10. <span data-ttu-id="750e2-127">在 "**脚本**" 页上，验证 `LocaleID` 属性是否设置为 "**英语 (美国。**</span><span class="sxs-lookup"><span data-stu-id="750e2-127">On the **Script** page, verify that the `LocaleID` property is set to **English (United States.**</span></span>  
  
11. <span data-ttu-id="750e2-128">单击“编辑脚本”打开 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="750e2-128">Click **Edit Script** to open [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="750e2-129">在 `Input0_ProcessInputRow` 方法中，键入或粘贴以下代码。</span><span class="sxs-lookup"><span data-stu-id="750e2-129">In the `Input0_ProcessInputRow` method, type or paste the following code.</span></span>  
  
     <span data-ttu-id="750e2-130">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="750e2-130">[Visual Basic]</span></span>  
  
    ```  
    Row.ErrorDescription =   
      Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
    ```  
  
     <span data-ttu-id="750e2-131">[Visual C#]</span><span class="sxs-lookup"><span data-stu-id="750e2-131">[Visual C#]</span></span>  
  
    ```  
    Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
    ```  
  
     <span data-ttu-id="750e2-132">已完成的子例程如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="750e2-132">The completed subroutine will look like the following code.</span></span>  
  
     <span data-ttu-id="750e2-133">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="750e2-133">[Visual Basic]</span></span>  
  
    ```  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription =   
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
    ```  
  
     <span data-ttu-id="750e2-134">[Visual C#]</span><span class="sxs-lookup"><span data-stu-id="750e2-134">[Visual C#]</span></span>  
  
    ```  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
        {  
  
            Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
        }  
    ```  
  
12. <span data-ttu-id="750e2-135">在“生成”\*\*\*\* 菜单上，单击“生成解决方案”\*\*\*\* 生成脚本并保存更改，然后关闭 VSTA。</span><span class="sxs-lookup"><span data-stu-id="750e2-135">On the **Build** menu, click **Build Solution** to build the script and save your changes, and then close VSTA.</span></span>  
  
13. <span data-ttu-id="750e2-136">单击“确定”\*\*\*\* 关闭“脚本转换编辑器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="750e2-136">Click **OK** to close the **Script Transformation Editor** dialog box.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="750e2-137">后续步骤</span><span class="sxs-lookup"><span data-stu-id="750e2-137">Next Steps</span></span>  
 <span data-ttu-id="750e2-138">[步骤4：添加平面文件目标] (lesson-4-4-adding-a-flat-file-destination.md</span><span class="sxs-lookup"><span data-stu-id="750e2-138">[Step 4: Adding a Flat File Destination](lesson-4-4-adding-a-flat-file-destination.md</span></span>  
  
  
