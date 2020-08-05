---
title: 第4课：以编程方式更新报表定义 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1f0a1d46-6d6d-4f67-b51e-06dbbbffacf9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c090fc023e3ac47927b99ab61a45fd8ca2c79321
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581061"
---
# <a name="lesson-4-update-the-report-definition-programmatically"></a><span data-ttu-id="3576f-102">第 4 课：以编程方式更新报表定义</span><span class="sxs-lookup"><span data-stu-id="3576f-102">Lesson 4: Update the Report Definition Programmatically</span></span>
  <span data-ttu-id="3576f-103">从报表服务器加载了报表定义并且通过报表字段拥有了对该报表定义的引用之后，需要更新报表定义。</span><span class="sxs-lookup"><span data-stu-id="3576f-103">Now that the report definition has been loaded from the report server and you have a reference to it using the report field, you need to update the report definition.</span></span> <span data-ttu-id="3576f-104">对本例来说，您将更新报表的 `Description` 属性。</span><span class="sxs-lookup"><span data-stu-id="3576f-104">For this example, you will update the `Description` property for the report.</span></span>  
  
### <a name="to-update-the-report-definition"></a><span data-ttu-id="3576f-105">更新报表定义</span><span class="sxs-lookup"><span data-stu-id="3576f-105">To update the report definition</span></span>  
  
1.  <span data-ttu-id="3576f-106">将 Program.cs 文件中的 UpdateReportDefinition ( # A1 方法替换为以下代码) 的 (文件中的代码 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="3576f-106">Replace the code for the UpdateReportDefinition() method in the Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void UpdateReportDefinition()  
    {  
        System.Console.WriteLine("Updating Report Definition");  
  
        // Create a list of the Items Choices for the Report. The   
        // ItemsChoiceType118 enum represents all the properties  
        // available in the report and the ItemsElementName   
        // represents the properties that exist in the current   
        // instance of the report.  
        List<ItemsChoiceType118> _reportItems =   
            new List<ItemsChoiceType118>(_report.ItemsElementName);  
  
        // Locate the index for the Description property  
        int index = _reportItems.IndexOf(  
            ItemsChoiceType118.Description);  
  
        // The Description item is of type StringLocIDType, so   
        // cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
  
        // Update the Description for the Report  
        ((StringLocIDType)_report.Items[index]).Value =   
            "New Report Description";  
  
        System.Console.WriteLine("- New Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
    }  
    ```  
  
    ```vb  
    Private Sub UpdateReportDefinition()  
  
        System.Console.WriteLine("Updating Report Definition")  
  
        'Create a list of the Items Choices for the Report. The   
        'ItemsChoiceType118 enum represents all the properties  
        'available in the report and the ItemsElementName   
        'represents the properties that exist in the current   
        'instance of the report.  
        Dim reportItems As List(Of ItemsChoiceType118) = _  
            New List(Of ItemsChoiceType118)(m_report.ItemsElementName)  
  
        'Locate the index for the Description property  
        Dim index As Integer = _  
            reportItems.IndexOf(ItemsChoiceType118.Description)  
  
        'The Description item is of type StringLocIDType, so   
        'cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
        'Update the Description for the Report  
        DirectCast(m_report.Items(index), StringLocIDType).Value = _  
            "New Report Description"  
  
        System.Console.WriteLine("- New Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="3576f-107">下一课</span><span class="sxs-lookup"><span data-stu-id="3576f-107">Next Lesson</span></span>  
 <span data-ttu-id="3576f-108">在下一课中，您将学习如何将更新的报表定义保存回报表服务器。</span><span class="sxs-lookup"><span data-stu-id="3576f-108">In the next lesson, you will save the updated report definition back to the report server.</span></span> <span data-ttu-id="3576f-109">请参阅[第5课：将报表定义发布到报表服务器](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3576f-109">See [Lesson 5: Publish the Report Definition to the Report Server](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3576f-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3576f-110">See Also</span></span>  
 [<span data-ttu-id="3576f-111">使用从 RDL 架构生成的类更新报表 &#40;SSRS 教程&#41;</span><span class="sxs-lookup"><span data-stu-id="3576f-111">Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)  
  
  
