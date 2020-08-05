---
title: 第3课：从报表服务器加载报表定义 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ad8b31c-43b0-4481-a31b-090cbed4a438
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: dc6ed26703599792b9c739f8d185ae4f190fc8be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581074"
---
# <a name="lesson-3-load-a-report-definition-from-the-report-server"></a><span data-ttu-id="856c4-102">第 3 课：从报表服务器加载报表定义</span><span class="sxs-lookup"><span data-stu-id="856c4-102">Lesson 3: Load a Report Definition from the Report Server</span></span>
  <span data-ttu-id="856c4-103">创建项目并从 RDL 架构生成类之后，您就可以从报表服务器加载报表定义了。</span><span class="sxs-lookup"><span data-stu-id="856c4-103">After you have created your project and generated the classes from the RDL schema, you are ready to load a report definition from the report server.</span></span>  
  
### <a name="to-load-a-report-definition"></a><span data-ttu-id="856c4-104">加载报表定义</span><span class="sxs-lookup"><span data-stu-id="856c4-104">To load a report definition</span></span>  
  
1.  <span data-ttu-id="856c4-105">`ReportUpdater`如果对类使用) ，请在类的顶部添加私有字段 (模块 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Report` 。</span><span class="sxs-lookup"><span data-stu-id="856c4-105">Add a private field at the top of the `ReportUpdater` class (module if you are using [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) for the `Report` class.</span></span> <span data-ttu-id="856c4-106">此字段将用于在应用程序的生存期内维护对从报表服务器加载的报表的引用。</span><span class="sxs-lookup"><span data-stu-id="856c4-106">This field will be used to maintain a reference to report that is loaded from the report server for the life of the application.</span></span>  
  
    ```csharp  
    private Report _report;  
    ```  
  
    ```vb  
    Private m_report As Report  
    ```  
  
2.  <span data-ttu-id="856c4-107">用以下代码替换 Program.cs 文件（对于 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]，为 Module1.vb）中 `LoadReportDefinition()` 方法的代码：</span><span class="sxs-lookup"><span data-stu-id="856c4-107">Replace the code for the `LoadReportDefinition()` method in the Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void LoadReportDefinition()  
    {  
        System.Console.WriteLine("Loading Report Definition");  
  
        string reportPath =   
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        // Retrieve the report definition   
        // from the report server  
        byte[] bytes =   
            _reportService.GetItemDefinition(reportPath);  
  
        if (bytes != null)  
        {  
            XmlSerializer serializer =   
                new XmlSerializer(typeof(Report));  
  
            // Load the report bytes into a memory stream  
            using (MemoryStream stream = new MemoryStream(bytes))  
            {  
                // Deserialize the report stream to an   
                // instance of the Report class  
                _report = (Report)serializer.Deserialize(stream);  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub LoadReportDefinition()  
  
        System.Console.WriteLine("Loading Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
  
        'Retrieve the report definition   
        'from the report server  
        Dim bytes As Byte() = _  
            m_reportService.GetItemDefinition(reportPath)  
  
        If Not (bytes Is Nothing) Then  
  
            Dim serializer As XmlSerializer = _  
                New XmlSerializer(GetType(Report))  
  
            'Load the report bytes into a memory stream  
            Using stream As MemoryStream = New MemoryStream(bytes)  
  
                'Deserialize the report stream to an   
                'instance of the Report class  
                m_report = CType(serializer.Deserialize(stream), _  
                                 Report)  
  
            End Using  
  
        End If  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="856c4-108">下一课</span><span class="sxs-lookup"><span data-stu-id="856c4-108">Next Lesson</span></span>  
 <span data-ttu-id="856c4-109">在下一课中，您将学习如何编写用于更新从报表服务器加载的报表定义的代码。</span><span class="sxs-lookup"><span data-stu-id="856c4-109">In the next lesson, you will write code to update the report definition that was loaded from the report server.</span></span> <span data-ttu-id="856c4-110">请参阅[第4课：以编程方式更新报表定义](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="856c4-110">See [Lesson 4: Update the Report Definition Programmatically](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856c4-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="856c4-111">See Also</span></span>  
 <span data-ttu-id="856c4-112">[使用从 RDL 架构生成的类更新报表 &#40;SSRS 教程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="856c4-112">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="856c4-113">报表定义语言 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="856c4-113">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
