---
title: '第6课：运行 RDL 架构应用程序 (VB-C # ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2cd2386-2df8-4b69-ab81-9ad1a31f6d27
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5a0fc2cd9c12b4b1602f517dc215ca44e686c663
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682455"
---
# <a name="lesson-6-run-the-rdl-schema-application-vb-c"></a><span data-ttu-id="d2124-102">第6课：运行 RDL 架构应用程序 (VB-C # ) </span><span class="sxs-lookup"><span data-stu-id="d2124-102">Lesson 6: Run the RDL Schema Application (VB-C#)</span></span>
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <span data-ttu-id="d2124-103">提供了两种从集成开发环境 (IDE) 生成和运行控制台应用程序的方法：</span><span class="sxs-lookup"><span data-stu-id="d2124-103">offers two methods to build and run a console application from the integrated development environment (IDE):</span></span>  
  
-   <span data-ttu-id="d2124-104">开始执行（调试）</span><span class="sxs-lookup"><span data-stu-id="d2124-104">Start (with Debugging)</span></span>  
  
-   <span data-ttu-id="d2124-105">开始执行（不调试）</span><span class="sxs-lookup"><span data-stu-id="d2124-105">Start without Debugging</span></span>  
  
### <a name="to-build-and-run-the-samplerdlschema-application"></a><span data-ttu-id="d2124-106">生成并运行 SampleRDLSchema 应用程序</span><span class="sxs-lookup"><span data-stu-id="d2124-106">To build and run the SampleRDLSchema application</span></span>  
  
1.  <span data-ttu-id="d2124-107">在**调试**菜单上，单击**开始执行(不调试)**。</span><span class="sxs-lookup"><span data-stu-id="d2124-107">From the **Debug** menu, click **Start Without Debugging**.</span></span> <span data-ttu-id="d2124-108">该操作可确保控制台窗口在程序执行完毕后保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="d2124-108">This ensures that the console window remains open after the program has finished executing.</span></span>  
  
     <span data-ttu-id="d2124-109">应用程序将以下输出内容打印到控制台：</span><span class="sxs-lookup"><span data-stu-id="d2124-109">The application prints the following output to the console:</span></span>  
  
    ```  
    Loading Report Definition  
    Updating Report Definition  
    - Old Description: <Old Report Description>  
    - New Description: <New Report Description>  
    Publishing Report Definition  
    ```  
  
2.  <span data-ttu-id="d2124-110">按任意键关闭控制台。</span><span class="sxs-lookup"><span data-stu-id="d2124-110">Press any key to close the console.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d2124-111">发生的所有错误都将写入控制台。</span><span class="sxs-lookup"><span data-stu-id="d2124-111">Any errors that occur are written to the console.</span></span>  
  
3.  <span data-ttu-id="d2124-112">示例应用程序完成运行时，经过更新的该报表副本将保存至报表服务器。</span><span class="sxs-lookup"><span data-stu-id="d2124-112">When the sample application is finished running an updated copy of the report will be saved to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2124-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2124-113">See Also</span></span>  
 <span data-ttu-id="d2124-114">[使用从 RDL 架构生成的类更新报表 &#40;SSRS 教程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="d2124-114">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="d2124-115">报表定义语言 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="d2124-115">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
