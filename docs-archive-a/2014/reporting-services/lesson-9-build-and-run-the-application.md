---
title: 第 9 课：生成并运行应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 068deb075f0f60dde634ac29f6f8f934448dc6a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578699"
---
# <a name="lesson-9-build-and-run-the-application"></a><span data-ttu-id="191d9-102">Lesson 9: Build and Run the Application</span><span class="sxs-lookup"><span data-stu-id="191d9-102">Lesson 9: Build and Run the Application</span></span>
  <span data-ttu-id="191d9-103">创建用于数据表的数据筛选器后，接下来要生成并运行网站应用程序。</span><span class="sxs-lookup"><span data-stu-id="191d9-103">After you create a data filter for the data table, your next step is to build and run the website application.</span></span>

### <a name="to-build-and-run-the-application"></a><span data-ttu-id="191d9-104">生成并运行应用程序</span><span class="sxs-lookup"><span data-stu-id="191d9-104">To build and run the application</span></span>

1.  <span data-ttu-id="191d9-105"> 按 CTRL+F5 以运行 Default.aspx 页但不调试，或按 F5 以运行该页并进行调试。</span><span class="sxs-lookup"><span data-stu-id="191d9-105">Press **CTRL+F5** to run the Default.aspx page without debugging, or press F5 to run the page with debugging.</span></span>

     <span data-ttu-id="191d9-106"> 在生成过程中，将编译报表，并将所发现的任何错误（如报表所使表达式中的语法错误）添加到位于 Visual Studio 窗口底部的“任务列表”。</span><span class="sxs-lookup"><span data-stu-id="191d9-106">As part of the build process, the report is compiled and any errors found (such as a syntax error in an expression used in the report) are added to the **Task List** that is located at the bottom of the Visual Studio window.</span></span>

     <span data-ttu-id="191d9-107">在浏览器中显示该网页。</span><span class="sxs-lookup"><span data-stu-id="191d9-107">The webpage appears in the browser.</span></span> <span data-ttu-id="191d9-108">ReportViewer 控件显示报表。</span><span class="sxs-lookup"><span data-stu-id="191d9-108">The ReportViewer control displays the report.</span></span> <span data-ttu-id="191d9-109">可使用工具栏在报表中浏览、进行缩放以及将报表导出到 Excel。</span><span class="sxs-lookup"><span data-stu-id="191d9-109">You can use the toolbar to browse through the report, zoom, and export the report to Excel.</span></span>

2.  <span data-ttu-id="191d9-110"> 将鼠标悬停在“名称”列下的任意行上方。</span><span class="sxs-lookup"><span data-stu-id="191d9-110">Hover the mouse over any of the rows under **Name** column.</span></span> <span data-ttu-id="191d9-111">鼠标光标将显示一个手形符号。</span><span class="sxs-lookup"><span data-stu-id="191d9-111">The mouse cursor will display a Hand symbol.</span></span>

3.  <span data-ttu-id="191d9-112">\*\*\*\* 单击“名称”列中的某个值。</span><span class="sxs-lookup"><span data-stu-id="191d9-112">Click a value in the **Name** column.</span></span> <span data-ttu-id="191d9-113">随后将显示子报表以及经过筛选的相应数据。</span><span class="sxs-lookup"><span data-stu-id="191d9-113">The child report is shown with the corresponding filtered data.</span></span>

4.  <span data-ttu-id="191d9-114">\*\*\*\* 单击“返回父报表” \*\*\*\* 图标，在 **ReportViewer** 工具栏中导航回父报表。</span><span class="sxs-lookup"><span data-stu-id="191d9-114">Click the icon, **Go back to parent report**, in the **ReportViewer** tool bar to navigate back to the **Parent** report.</span></span>

     <span data-ttu-id="191d9-115">![ssrs 使用 ReportViewer 钻取](../../2014/tutorials/media/ssrs-drillthrough-report.png "ssrs 使用 ReportViewer 钻取")</span><span class="sxs-lookup"><span data-stu-id="191d9-115">![ssrs drill through using ReportViewer](../../2014/tutorials/media/ssrs-drillthrough-report.png "ssrs drill through using ReportViewer")</span></span>

5.  <span data-ttu-id="191d9-116">关闭浏览器以退出。</span><span class="sxs-lookup"><span data-stu-id="191d9-116">Close the browser to exit.</span></span>


