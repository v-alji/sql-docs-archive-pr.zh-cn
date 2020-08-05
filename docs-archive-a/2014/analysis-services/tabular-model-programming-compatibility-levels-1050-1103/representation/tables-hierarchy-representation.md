---
title: 表格)  (层次结构表示形式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 1d53dda1-f2c8-4a9b-8ec7-78f43ca1d7db
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83d91be5152c4e7f1345cee8756abbe57c0016f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579080"
---
# <a name="hierarchy-representation-tabular"></a><span data-ttu-id="c3032-102">层次结构表示形式（表格）</span><span class="sxs-lookup"><span data-stu-id="c3032-102">Hierarchy Representation (Tabular)</span></span>
  <span data-ttu-id="c3032-103">在表格模型中，层次结构是根据用户选定的值从一个属性导航到另一个属性的路径。</span><span class="sxs-lookup"><span data-stu-id="c3032-103">In tabular models a hierarchy is navigation path from one attribute to another based on values selected by the user.</span></span>  
  
## <a name="hierarchy-representation"></a><span data-ttu-id="c3032-104">层次结构表示形式</span><span class="sxs-lookup"><span data-stu-id="c3032-104">Hierarchy Representation</span></span>  
  
### <a name="hierarchy-in-amo"></a><span data-ttu-id="c3032-105">AMO 中的层次结构</span><span class="sxs-lookup"><span data-stu-id="c3032-105">Hierarchy in AMO</span></span>  
 <span data-ttu-id="c3032-106">在使用 AMO 管理表格模型表时，对于 AMO 中的层次结构存在一对一的对象匹配。</span><span class="sxs-lookup"><span data-stu-id="c3032-106">When using AMO to manage a tabular model table, there is a one-to-one object match for a hierarchy in AMO.</span></span> <span data-ttu-id="c3032-107">层次结构由 <xref:Microsoft.AnalysisServices.Hierarchy> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="c3032-107">A hierarchy is represented by the <xref:Microsoft.AnalysisServices.Hierarchy> object.</span></span>  
  
 <span data-ttu-id="c3032-108">下面的代码段演示如何向现有表格模型添加层次结构。</span><span class="sxs-lookup"><span data-stu-id="c3032-108">The following code snippet shows how to add a hierarchy to an existing tabular model.</span></span> <span data-ttu-id="c3032-109">代码中假定您具有 AMO 数据库对象 newDatabase 和 AMO 多维数据集对象 modelCube。</span><span class="sxs-lookup"><span data-stu-id="c3032-109">The code assumes you have an AMO database object, newDatabase, and an AMO cube object, modelCube.</span></span>  
  
```  
  
private void addHierarchy(  
                    AMO.Database newDatabase  
                 ,  AMO.Cube modelCube  
                 ,  string tableName  
                 ,  string hierarchyName  
                 ,  string levelsText  
             )  
{  
    //Validate input  
    if (string.IsNullOrEmpty(hierarchyName) || string.IsNullOrEmpty(levelsText))  
    {  
        MessageBox.Show(String.Format("Hierarchy Name or Layout must be provided."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
  
    if (!overwriteHierarchy.Checked && newDatabase.Dimensions[tableName].Hierarchies.Contains(hierarchyName))  
    {  
        MessageBox.Show(String.Format("Hierarchy already exists.\nGive a new name or enable overwriting"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
  
    try  
    {  
        if (newDatabase.Dimensions[tableName].Hierarchies.Contains(hierarchyName))  
        {  
            //Hierarchy exists... deleting it to write it later  
            newDatabase.Dimensions[tableName].Hierarchies.Remove(hierarchyName, true);  
            newDatabase.Dimensions[tableName].Update(AMO.UpdateOptions.AlterDependents);  
        }  
        AMO.Hierarchy currentHierarchy = newDatabase.Dimensions[tableName].Hierarchies.Add(hierarchyName, hierarchyName);  
        currentHierarchy.AllMemberName = string.Format("(All of {0})", hierarchyName);  
        //Parse hierarchyLayout  
        using (StringReader levels = new StringReader(levelsText))  
        {  
            //Each line:  
            //  must come with: The columnId of the attribute in the dimension --> this represents the SourceAttributeID  
            //  optional: A display name for the Level (if this argument doesn't come the default is the SourceAttributeID)  
            string line;  
            while ((line = levels.ReadLine()) != null)  
            {  
                if (string.IsNullOrEmpty(line) || string.IsNullOrWhiteSpace(line)) continue;  
                line = line.Trim();  
                string[] hierarchyData = line.Split(',');  
                if (string.IsNullOrEmpty(hierarchyData[0])) continue; //first argument cannot be empty or blank,   
                                                                      //assume is a blank line and ignore it  
                string levelSourceAttributeID = hierarchyData[0].Trim();  
                string levelID = (hierarchyData.Length > 1 && !string.IsNullOrEmpty(hierarchyData[1])) ? hierarchyData[1].Trim() : levelSourceAttributeID;  
                currentHierarchy.Levels.Add(levelID).SourceAttributeID = levelSourceAttributeID;  
            }  
        }  
        newDatabase.Dimensions[tableName].Update(AMO.UpdateOptions.AlterDependents);  
  
    }  
    catch (Exception ex)  
    {  
        MessageBox.Show(String.Format("Error creating hierarchy [{0}].\nError message: {1}", newHierarchyName.Text, ex.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        if (newDatabase.Dimensions[tableName].Hierarchies.Contains(hierarchyName))  
        {  
            //Hierarchy was created but exception prevented complete hierarchy to be written... deleting incomplete hierarchy  
            newDatabase.Dimensions[tableName].Hierarchies.Remove(hierarchyName, true);  
            newDatabase.Dimensions[tableName].Update(AMO.UpdateOptions.AlterDependents);  
        }  
  
    }  
    newDatabase.Dimensions[tableName].Process(AMO.ProcessType.ProcessFull);  
    modelCube.MeasureGroups[tableName].Process(AMO.ProcessType.ProcessFull);  
}  
  
```  
  
  
