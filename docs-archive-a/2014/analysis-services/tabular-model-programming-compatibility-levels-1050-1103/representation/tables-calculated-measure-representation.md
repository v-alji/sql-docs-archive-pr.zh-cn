---
title: 表格) 的计算度量值表示形式 (|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 4cb9fea5-1616-467b-a539-d051e5833aea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6b630fa075ae07b84e4886ad8bc115611da8e2d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589230"
---
# <a name="calculated-measure-representation-tabular"></a><span data-ttu-id="ba09f-102">计算度量值表示形式（表格）</span><span class="sxs-lookup"><span data-stu-id="ba09f-102">Calculated Measure Representation (Tabular)</span></span>
  <span data-ttu-id="ba09f-103">计算度量值是每次在使用时计算其值的已命名 DAX 表达式。</span><span class="sxs-lookup"><span data-stu-id="ba09f-103">A calculated measure is a named DAX expression evaluated every time it is used.</span></span>  
  
## <a name="calculated-measure-representation"></a><span data-ttu-id="ba09f-104">计算度量值表示形式</span><span class="sxs-lookup"><span data-stu-id="ba09f-104">Calculated Measure Representation</span></span>  
  
### <a name="calculated-measure-in-amo"></a><span data-ttu-id="ba09f-105">AMO 中的计算度量值</span><span class="sxs-lookup"><span data-stu-id="ba09f-105">Calculated Measure in AMO</span></span>  
 <span data-ttu-id="ba09f-106">使用 AMO 管理表格模型计算度量值时，在逻辑计算度量值对象和 <xref:Microsoft.AnalysisServices.Command> 对象的 <xref:Microsoft.AnalysisServices.MdxScript> 对象中定义的度量值之间存在一对一匹配关系。</span><span class="sxs-lookup"><span data-stu-id="ba09f-106">When using AMO to manage a tabular model calculated measure, there is a one-to-one match between the logical Calculated Measure object and a measure defined in a <xref:Microsoft.AnalysisServices.Command> object of the <xref:Microsoft.AnalysisServices.MdxScript> object.</span></span> <span data-ttu-id="ba09f-107">每个**计算度量值**都定义为 `CREATE MEASURE` 对象内的表达式 <xref:Microsoft.AnalysisServices.Command> ，并用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="ba09f-107">Each **Calculated Measure** is defined as a `CREATE MEASURE` expression inside a <xref:Microsoft.AnalysisServices.Command> object and separated by a semicolon.</span></span> <span data-ttu-id="ba09f-108">表格模型中的所有计算度量值对应于 <xref:Microsoft.AnalysisServices.MdxScript> 对象中的一个命令对象中的集合 `CREATE MEASURE` 字符串。</span><span class="sxs-lookup"><span data-stu-id="ba09f-108">All calculated measures in a tabular model correspond to the collection `CREATE MEASURE` string in one command object in a <xref:Microsoft.AnalysisServices.MdxScript> object.</span></span> <span data-ttu-id="ba09f-109">对于每个计算度量值，存在与 <xref:Microsoft.AnalysisServices.CalculationProperty> 的一对一映射关系。</span><span class="sxs-lookup"><span data-stu-id="ba09f-109">For each calculated measure, there is one-to-one mapping with a <xref:Microsoft.AnalysisServices.CalculationProperty>.</span></span>  
  
 <span data-ttu-id="ba09f-110">下面的代码段演示如何创建计算度量值。</span><span class="sxs-lookup"><span data-stu-id="ba09f-110">The following code snippet shows how to create a calculated measure.</span></span>  
  
```  
  
private void addCalculatedMeasure(  
                   AMO.Cube modelCube  
                 , string cmTableName  
                 , string cmName  
                 , string newCalculatedMeasureExpression  
             )  
{  
    //Verify input requirements  
    if (string.IsNullOrEmpty(cmName) || string.IsNullOrWhiteSpace(cmName))  
    {  
        MessageBox.Show(String.Format("Calculated Measure name is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
    if (string.IsNullOrEmpty(newCalculatedMeasureExpression) || string.IsNullOrWhiteSpace(newCalculatedMeasureExpression))  
    {  
        MessageBox.Show(String.Format("Calculated Measure expression is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    StringBuilder measuresCommand = new StringBuilder();  
  
    AMO.MdxScript mdxScript = modelCube.MdxScripts["MdxScript"];  
  
    //ToDo: Verify if measure already exits and ask user what wants to do next  
  
    if (mdxScript.Commands.Count == 1)  
    {  
        measuresCommand.AppendLine("-------------------------------------------------------------");  
        measuresCommand.AppendLine("-- Tabular Model measures command (do not modify manually) --");  
        measuresCommand.AppendLine("-------------------------------------------------------------");  
        measuresCommand.AppendLine();  
        measuresCommand.AppendLine();  
        mdxScript.Commands.Add(new AMO.Command(measuresCommand.ToString()));  
  
    }  
    else  
    {  
        measuresCommand.Append(mdxScript.Commands[1].Text);  
    }  
    measuresCommand.AppendLine(string.Format("CREATE MEASURE '{0}'[{1}]={2};", cmTableName, cmName, newCalculatedMeasureExpression));  
  
    mdxScript.Commands[1].Text = measuresCommand.ToString();  
  
    if (!mdxScript.CalculationProperties.Contains(cmName))  
    {  
        AMO.CalculationProperty cp = new AMO.CalculationProperty(cmName, AMO.CalculationType.Member);  
        cp.FormatString = ""; // ToDo: Get formatting attributes for the member  
        cp.Visible = true;  
        mdxScript.CalculationProperties.Add(cp);  
    }  
  
    try  
    {  
        modelCube.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
        MessageBox.Show(String.Format("Calculated Measure successfully defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
    }  
    catch (AMO.OperationException amoOpXp)  
    {  
        MessageBox.Show(String.Format("Calculated Measure expression contains syntax errors, or references undefined or missspelled elements.\nError message: {0}", amoOpXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (AMO.AmoException amoXp)  
    {  
        MessageBox.Show(String.Format("AMO exception accessing the server.\nError message: {0}", amoXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (Exception)  
    {  
        throw;  
    }  
}  
  
```  
  
  
