---
title: 表格)  (的计算列表示形式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 190bfa92-2445-404d-86df-7cc94d283add
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1f7a56c01a1c4af7a2e618c6b6a6cb586424e639
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692568"
---
# <a name="calculated-column-representation-tabular"></a><span data-ttu-id="08197-102">计算列表示形式（表格）</span><span class="sxs-lookup"><span data-stu-id="08197-102">Calculated Column Representation (Tabular)</span></span>
  <span data-ttu-id="08197-103">计算列是在表中创建新列并且获取的值存储于该表中的 DAX 表达式。</span><span class="sxs-lookup"><span data-stu-id="08197-103">A calculated column is DAX expression that creates a new column in a table and the obtained values are stored in the table.</span></span> <span data-ttu-id="08197-104">每次处理表时，都会对计算列表达式进行计算。</span><span class="sxs-lookup"><span data-stu-id="08197-104">The calculated column expression is evaluated every time the table is processed.</span></span>  
  
## <a name="calculated-column-representation"></a><span data-ttu-id="08197-105">计算列表示形式</span><span class="sxs-lookup"><span data-stu-id="08197-105">Calculated Column Representation</span></span>  
  
### <a name="calculated-columns-in-amo"></a><span data-ttu-id="08197-106">AMO 中的计算列</span><span class="sxs-lookup"><span data-stu-id="08197-106">Calculated Columns in AMO</span></span>  
 <span data-ttu-id="08197-107">在使用 AMO 管理表格模型表时，对于 AMO 中的计算列没有一对一的对象匹配。</span><span class="sxs-lookup"><span data-stu-id="08197-107">When using AMO to manage a tabular model table, there is no one-to-one object match for a calculated column in AMO.</span></span> <span data-ttu-id="08197-108">计算列由 <xref:Microsoft.AnalysisServices.Dimension> 中的属性以及 <xref:Microsoft.AnalysisServices.MeasureGroup> 中的属性表示。</span><span class="sxs-lookup"><span data-stu-id="08197-108">A calculated column is represented by an attribute in <xref:Microsoft.AnalysisServices.Dimension> and an attribute in <xref:Microsoft.AnalysisServices.MeasureGroup>.</span></span>  
  
 <span data-ttu-id="08197-109">下面的代码段演示如何向现有表格模型添加计算列。</span><span class="sxs-lookup"><span data-stu-id="08197-109">The following code snippet shows how to add a calculated column to an existing tabular model.</span></span> <span data-ttu-id="08197-110">代码中假定您具有 AMO 数据库对象 newDatabase 和 AMO 多维数据集对象 modelCube。</span><span class="sxs-lookup"><span data-stu-id="08197-110">The code assumes you have an AMO database object, newDatabase, and an AMO cube object, modelCube.</span></span>  
  
```  
  
private void addCalculatedColumn(  
                   AMO.Database newDatabase  
                 , AMO.Cube modelCube  
                 , String ccTableName  
                 , String ccName  
                 , String newCalculatedColumnExpression  
             )  
{  
    if (string.IsNullOrEmpty(ccName) || string.IsNullOrWhiteSpace(ccName))  
    {  
        MessageBox.Show(String.Format("Calculated Column name is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
    if (string.IsNullOrEmpty(newCalculatedColumnExpression) || string.IsNullOrWhiteSpace(newCalculatedColumnExpression))  
    {  
        MessageBox.Show(String.Format("Calculated Column expression is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    if (newDatabase.Dimensions[ccTableName].Attributes.Contains(ccName))  
    {  
        MessageBox.Show(String.Format("Calculated Column name already defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
    //Add CC attribute to the Dimension  
    AMO.Dimension dim = newDatabase.Dimensions[ccTableName];  
    AMO.DimensionAttribute currentAttribute = dim.Attributes.Add(ccName, ccName);  
    currentAttribute.Usage = AMO.AttributeUsage.Regular;  
    currentAttribute.KeyUniquenessGuarantee = false;  
  
    currentAttribute.KeyColumns.Add(new AMO.DataItem(ccTableName, ccName, OleDbType.Empty));  
    currentAttribute.KeyColumns[0].Source = new AMO.ExpressionBinding(newCalculatedColumnExpression);  
    currentAttribute.KeyColumns[0].NullProcessing = AMO.NullProcessing.Preserve;  
    currentAttribute.NameColumn = new AMO.DataItem(ccTableName, ccName, System.Data.OleDb.OleDbType.WChar);  
    currentAttribute.NameColumn.Source = new AMO.ExpressionBinding(newCalculatedColumnExpression);  
    currentAttribute.NameColumn.NullProcessing = AMO.NullProcessing.ZeroOrBlank;  
  
    currentAttribute.OrderBy = AMO.OrderBy.Key;  
    AMO.AttributeRelationship currentAttributeRelationship = dim.Attributes["RowNumber"].AttributeRelationships.Add(currentAttribute.ID);  
    currentAttributeRelationship.Cardinality = AMO.Cardinality.Many;  
    currentAttributeRelationship.OverrideBehavior = AMO.OverrideBehavior.None;  
  
    //Add CC as attribute to the MG  
    AMO.MeasureGroup mg = modelCube.MeasureGroups[ccTableName];  
    AMO.DegenerateMeasureGroupDimension currentMGDim = (AMO.DegenerateMeasureGroupDimension)mg.Dimensions[ccTableName];  
    AMO.MeasureGroupAttribute mga = new AMO.MeasureGroupAttribute(ccName);  
  
    mga.KeyColumns.Add(new AMO.DataItem(ccTableName, ccName, OleDbType.Empty));  
    mga.KeyColumns[0].Source = new AMO.ExpressionBinding(newCalculatedColumnExpression);  
  
    currentMGDim.Attributes.Add(mga);  
  
    try  
    {  
        //Update Dimension, CubeDimension and MG in server  
        newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    }  
    catch (AMO.OperationException amoOpXp)  
    {  
        MessageBox.Show(String.Format("Calculated Column expression contains syntax errors, or references undefined or missspelled elements.\nError message: {0}", amoOpXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
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
  
  
