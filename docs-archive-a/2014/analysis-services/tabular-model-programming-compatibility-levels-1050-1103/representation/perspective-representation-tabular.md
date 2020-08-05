---
title: 表格)  (透视表示形式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 6d2636c4-dae4-448f-a1d4-dbee739e177c
author: minewiskan
ms.author: owend
ms.openlocfilehash: ca8a66d3134748fd524dc0c6b524d944213533e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580420"
---
# <a name="perspective-representation-tabular"></a><span data-ttu-id="362cd-102">透视表示形式（表格）</span><span class="sxs-lookup"><span data-stu-id="362cd-102">Perspective Representation (Tabular)</span></span>
  <span data-ttu-id="362cd-103">透视是一种机制，用于针对客户端应用程序简化模型或将模型的侧重点置于其某个较小部分。</span><span class="sxs-lookup"><span data-stu-id="362cd-103">A perspective is a mechanism to simplify or focus the model into a smaller portion of it for the client application.</span></span>  
  
 <span data-ttu-id="362cd-104">有关如何创建和操作透视表示形式的详细说明，请参阅[透视表示形式 (表格) ](perspective-representation-tabular.md) 。</span><span class="sxs-lookup"><span data-stu-id="362cd-104">See [Perspective Representation (Tabular)](perspective-representation-tabular.md) for a detailed explanation on how to create and manipulate the perspective representation.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="362cd-105">透视并不是一种安全机制；用户仍可通过其他接口访问透视外部的对象。</span><span class="sxs-lookup"><span data-stu-id="362cd-105">Perspectives are not a security mechanism; objects outside the perspective can still be accessed by the user through other interfaces.</span></span>  
  
## <a name="perspective-representation"></a><span data-ttu-id="362cd-106">透视表示形式</span><span class="sxs-lookup"><span data-stu-id="362cd-106">Perspective Representation</span></span>  
 <span data-ttu-id="362cd-107">就 AMO 对象而言，透视表示形式与 <xref:Microsoft.AnalysisServices.Perspective> 之间存在一对一映射关系，并且不需要任何其他主要 AMO 对象。</span><span class="sxs-lookup"><span data-stu-id="362cd-107">In terms of AMO objects a perspective representation has a one to one mapping relationship with <xref:Microsoft.AnalysisServices.Perspective> and no other main AMO objects are required.</span></span>  
  
### <a name="perspective-in-amo"></a><span data-ttu-id="362cd-108">AMO 中的透视</span><span class="sxs-lookup"><span data-stu-id="362cd-108">Perspective in AMO</span></span>  
 <span data-ttu-id="362cd-109">下面的代码段演示如何在表格模型中创建透视。</span><span class="sxs-lookup"><span data-stu-id="362cd-109">The following code snippet shows how to create a perspective in a Tabular model.</span></span> <span data-ttu-id="362cd-110">此代码段中的关键元素是 perspectiveElements；此对象是表格模型中向用户公开的所有对象的图形化表示形式。</span><span class="sxs-lookup"><span data-stu-id="362cd-110">The key element in this piece of code is the perspectiveElements; this object is a graphical representation of all the objects in the tabular model that are exposed to the user.</span></span> <span data-ttu-id="362cd-111">*perspectiveElements*包含4列，在此方案中，只有列1、2和3是相关的。</span><span class="sxs-lookup"><span data-stu-id="362cd-111">*perspectiveElements* contains 4 columns and for this scenario only columns 1, 2 and 3 are relevant.</span></span> <span data-ttu-id="362cd-112">第 1 列包含显示的元素的类型 - elementTypeValue；第 2 列包含元素的完整名称 --（可能需要进行分析以在透视中输入该元素）；第 3 列包含一个复选框项 - checkedElement，该项说明元素是否为透视的一部分。</span><span class="sxs-lookup"><span data-stu-id="362cd-112">Column 1 contains the type of element displayed -elementTypeValue-; column 2 contains the complete name of the element --, that probably will need to parsed to enter the element in the perspective; column 3 contains a checkbox item -checkedElement- that tells if the element is part of the perspective or not.</span></span>  
  
```  
  
private void updatePerspective_Click(  
                     AMO.Cube modelCube  
                  ,  DataGridView perspectiveElements  
                  ,  string updatedPerspectiveID  
             )  
{  
    //Update is done by delete first, create new and insert after  
    //if perspective doesn't exist then create first and insert after  
    updatedPerspectiveID = updatedPerspectiveID.Trim();  
    if (modelCube.Perspectives.Contains(updatedPerspectiveID))  
    {  
        modelCube.Perspectives.Remove(updatedPerspectiveID, true);  
        newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    }  
    AMO.Perspective currentPerspective = modelCube.Perspectives.Add(updatedPerspectiveID, updatedPerspectiveID);  
  
    foreach (DataGridViewRow currentDGVRow in perspectiveElements.Rows)  
    {  
        bool checkedElement = (bool)currentDGVRow.Cells[3].Value;  
        if (checkedElement)  
        {  
            string elementTypeValue = currentDGVRow.Cells[1].Value.ToString();  
            string elementNameValue = currentDGVRow.Cells[2].Value.ToString();  
            switch (elementTypeValue)  
            {  
                case "Column: Attribute":  
                case "Column: Calculated Column":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionAttributeName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Attributes.Contains(perspectiveDimensionAttributeName))  
                        {  
                            currentPerspectiveDimension.Attributes.Add(perspectiveDimensionAttributeName);  
                        }  
                    }  
                    break;  
                case "Hierarchy":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionHierarchyName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Hierarchies.Contains(perspectiveDimensionHierarchyName))  
                        {  
                            currentPerspectiveDimension.Hierarchies.Add(perspectiveDimensionHierarchyName);  
                        }  
                    }  
                    break;  
                case "Measure":  
                    {  
                        string perspectiveMeasureGroupName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string measureName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        string perspectiveMeasureName = string.Format("[Measures].[{0}]", measureName);  
                        AMO.PerspectiveCalculation currentPerspectiveCalculation = new AMO.PerspectiveCalculation(perspectiveMeasureName, AMO.PerspectiveCalculationType.Member);  
                        if (!currentPerspective.Calculations.Contains(perspectiveMeasureName))  
                        {  
                            currentPerspective.Calculations.Add(currentPerspectiveCalculation);  
                        }  
                        if (modelCube.MdxScripts["MdxScript"].CalculationProperties.Contains(string.Format("KPIs.[{0}]", measureName)))  
                        {//Current Measure is also a KPI ==> will be added to the KPIs collection of the perspective  
                            AMO.PerspectiveKpi currentPerspectiveKpi = new AMO.PerspectiveKpi(perspectiveMeasureName);  
                            if (!currentPerspective.Kpis.Contains(perspectiveMeasureName))  
                            {  
                                currentPerspective.Kpis.Add(currentPerspectiveKpi);  
                            }  
                        }  
                    }  
                    break;  
                default:  
                    break;  
            }  
        }  
    }  
  
    newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.CreateOrReplace);  
    MessageBox.Show(String.Format("Perpective successfully updated."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
}  
  
```  
  
## <a name="amo2tabular-sample"></a><span data-ttu-id="362cd-113">AMO2Tabular 示例</span><span class="sxs-lookup"><span data-stu-id="362cd-113">AMO2Tabular sample</span></span>  
 <span data-ttu-id="362cd-114">不过，若要了解如何使用 AMO 创建和操作透视表示形式，请参阅“AMO 到表格”示例中的源代码。</span><span class="sxs-lookup"><span data-stu-id="362cd-114">However, to have an understanding on how to use AMO to create and manipulate perspective representations see the source code of the AMO to Tabular sample.</span></span> <span data-ttu-id="362cd-115">该示例位于 Codeplex。</span><span class="sxs-lookup"><span data-stu-id="362cd-115">The sample is available at Codeplex.</span></span> <span data-ttu-id="362cd-116">有关该代码的重要说明：提供该代码只是为了支持本文介绍的逻辑概念，不应用于生产环境中；也不应用于除教学之外的其他用途。</span><span class="sxs-lookup"><span data-stu-id="362cd-116">An important note about the code: the code is provided only as a support to the logical concepts explained here and should not be used in a production environment; nor should it be used for other purpose other than the pedagogical one.</span></span>  
  
  
