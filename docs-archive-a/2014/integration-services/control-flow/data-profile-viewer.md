---
title: 数据配置文件查看器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], output viewer
ms.assetid: b9043428-ce26-45bb-910c-588d07579565
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e82aae19525625d966bdd01334eca07a1c4c68f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587550"
---
# <a name="data-profile-viewer"></a><span data-ttu-id="7cec8-102">数据配置文件查看器 (Data Profile Viewer)</span><span class="sxs-lookup"><span data-stu-id="7cec8-102">Data Profile Viewer</span></span>
  <span data-ttu-id="7cec8-103">数据事件探查过程的下一步是查看和分析数据配置文件。</span><span class="sxs-lookup"><span data-stu-id="7cec8-103">Viewing and analyzing the data profiles is the next step in the data profiling process.</span></span> <span data-ttu-id="7cec8-104">可以在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包内运行数据事件探查任务并计算数据配置文件之后，查看这些配置文件。</span><span class="sxs-lookup"><span data-stu-id="7cec8-104">You can view these profiles after you have run the Data Profiling task inside an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package and computed the data profiles.</span></span> <span data-ttu-id="7cec8-105">有关如何设置和运行数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="7cec8-105">For more information about how to set up and run the Data Profiling tasks, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7cec8-106">输出文件可能包含有关数据库的敏感数据和数据库所包含的数据。</span><span class="sxs-lookup"><span data-stu-id="7cec8-106">The output file might contain sensitive data about your database and the data that database contains.</span></span> <span data-ttu-id="7cec8-107">有关如何使此文件更加安全的建议，请参阅 [访问包使用的文件](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="7cec8-107">For suggestions on how to make this file more secure, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
## <a name="data-profiles"></a><span data-ttu-id="7cec8-108">数据配置文件</span><span class="sxs-lookup"><span data-stu-id="7cec8-108">Data Profiles</span></span>  
 <span data-ttu-id="7cec8-109">若要查看数据配置文件，请将数据事件探查任务配置为将其输出发送到文件，然后使用独立的数据配置文件查看器。</span><span class="sxs-lookup"><span data-stu-id="7cec8-109">To view the data profiles, you configure the Data Profiling task to send its output to a file, and then you use the stand-alone Data Profile Viewer.</span></span> <span data-ttu-id="7cec8-110">若要打开数据配置文件查看器，请执行以下操作之一。</span><span class="sxs-lookup"><span data-stu-id="7cec8-110">To open the Data Profile Viewer, do one of the following.</span></span>  
  
-   <span data-ttu-id="7cec8-111">在“[!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器”中右键单击“数据事件探查”任务，然后单击“编辑”。</span><span class="sxs-lookup"><span data-stu-id="7cec8-111">Right-click the **Data Profiling** task in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, and then click **Edit**.</span></span> <span data-ttu-id="7cec8-112">在 **“数据事件探查任务编辑器”** 的 **“常规”** 页上，单击 **“打开配置文件查看器”** 。</span><span class="sxs-lookup"><span data-stu-id="7cec8-112">Click **Open Profile Viewer** on the **General** page of the **Data Profiling Task Editor**.</span></span>  
  
-   <span data-ttu-id="7cec8-113">在文件夹 \<drive>:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn 中运行 DataProfileViewer.exe。</span><span class="sxs-lookup"><span data-stu-id="7cec8-113">In the folder, *\<drive>*:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn, run DataProfileViewer.exe.</span></span>  
  
 <span data-ttu-id="7cec8-114">该查看器使用多个窗格来显示请求的配置文件和计算所得的结果，包含可选详细信息和明细功能：</span><span class="sxs-lookup"><span data-stu-id="7cec8-114">The viewer uses multiple panes to display the profiles that you requested and the computed results, with optional details and drilldown capability:</span></span>  
  
 <span data-ttu-id="7cec8-115">**“配置文件”** 窗格</span><span class="sxs-lookup"><span data-stu-id="7cec8-115">**Profiles** pane</span></span>  
 <span data-ttu-id="7cec8-116">“配置文件”  窗格显示数据配置文件任务中所请求的配置文件。</span><span class="sxs-lookup"><span data-stu-id="7cec8-116">The **Profiles** pane displays the profiles that were requested in the Data Profile task.</span></span> <span data-ttu-id="7cec8-117">若要查看配置文件的计算结果，请在 **“配置文件”** 窗格中选择配置文件，结果将显示在查看器的其他窗格中。</span><span class="sxs-lookup"><span data-stu-id="7cec8-117">To view the computed results for the profile, select the profile in the **Profiles** pane and the results will appear in the other panes of the viewer.</span></span>  
  
 <span data-ttu-id="7cec8-118">**“结果”** 窗格</span><span class="sxs-lookup"><span data-stu-id="7cec8-118">**Results** pane</span></span>  
 <span data-ttu-id="7cec8-119">“结果”  窗格使用单行来汇总配置文件的计算结果。</span><span class="sxs-lookup"><span data-stu-id="7cec8-119">The **Results** pane uses a single row to summarize the computed results of the profile.</span></span> <span data-ttu-id="7cec8-120">例如，如果请求 **“列长度分布配置文件”** ，此行将包括最小和最大长度以及行数。</span><span class="sxs-lookup"><span data-stu-id="7cec8-120">For example, if you request a **Column Length Distribution Profile**, this row includes the minimum and maximum length, and the row count.</span></span> <span data-ttu-id="7cec8-121">对于大多数配置文件，可以在 **“结果”** 窗格中选择此行，以便在可选的 **“详细信息”** 窗格中查看其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="7cec8-121">For most profiles, you can select this row in the **Results** pane to see additional detail in the optional **Details** pane.</span></span>  
  
 <span data-ttu-id="7cec8-122">**“详细信息”** 窗格</span><span class="sxs-lookup"><span data-stu-id="7cec8-122">**Details** pane</span></span>  
 <span data-ttu-id="7cec8-123">对于大多数配置文件类型，“详细信息”  窗格显示有关在“结果”  窗格中选择的配置文件结果的其他信息。</span><span class="sxs-lookup"><span data-stu-id="7cec8-123">For most profile types, the **Details** pane displays additional information about the profile results selected in the **Results** pane.</span></span> <span data-ttu-id="7cec8-124">例如，如果请求 **“列长度分布配置文件”** ， **“详细信息”** 窗格将显示找到的每列长度。</span><span class="sxs-lookup"><span data-stu-id="7cec8-124">For example, if you request a **Column Length Distribution Profile**, the **Details** pane displays each column length that was found.</span></span> <span data-ttu-id="7cec8-125">该窗格还显示列值为该列长度的行数和行数百分比。</span><span class="sxs-lookup"><span data-stu-id="7cec8-125">The pane also displays the number and percentage of rows in which the column value has that column length.</span></span>  
  
 <span data-ttu-id="7cec8-126">对于对多列进行计算的三种配置文件类型（候选键、函数依赖关系和值包含），“详细信息”  窗格显示违反期望关系的信息。</span><span class="sxs-lookup"><span data-stu-id="7cec8-126">For the three profile types that are computed against more than one column (Candidate Key, Functional Dependency, and Value Inclusion), the **Details** pane displays violations of the expected relationship.</span></span> <span data-ttu-id="7cec8-127">例如，如果请求候选键配置文件，“详细信息”窗格将显示违反候选键唯一性约束的重复值。</span><span class="sxs-lookup"><span data-stu-id="7cec8-127">For example, if you request a Candidate Key Profile, the Details pane displays duplicate values that violate the uniqueness of the candidate key.</span></span>  
  
 <span data-ttu-id="7cec8-128">如果有用于计算配置文件的数据源，则可以双击“详细信息”  窗格中的行，在“明细”  窗格中查看匹配的数据行。</span><span class="sxs-lookup"><span data-stu-id="7cec8-128">If the data source that is used to compute the profile is available, you can double-click a row in the **Details** pane to see the matching rows of data in the **Drilldown** pane.</span></span>  
  
 <span data-ttu-id="7cec8-129">“明细”  窗格</span><span class="sxs-lookup"><span data-stu-id="7cec8-129">**Drilldown** pane</span></span>  
 <span data-ttu-id="7cec8-130">在满足以下条件的情况下，可以双击“详细信息”  窗格中的行，在“明细”  窗格中查看匹配的数据行：</span><span class="sxs-lookup"><span data-stu-id="7cec8-130">You can double-click a row in the **Details** pane to see the matching rows of data in the **Drilldown** pane when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="7cec8-131">有用于计算配置文件的数据源。</span><span class="sxs-lookup"><span data-stu-id="7cec8-131">The data source that is used to compute the profile is available.</span></span>  
  
-   <span data-ttu-id="7cec8-132">您有权查看数据。</span><span class="sxs-lookup"><span data-stu-id="7cec8-132">You have permission to view the data.</span></span>  
  
 <span data-ttu-id="7cec8-133">为了连接到明细请求的源数据库，数据配置文件查看器使用 Windows 身份验证和当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="7cec8-133">To connect to the source database for a drilldown request, the Data Profile Viewer uses Windows Authentication and the credentials of the current user.</span></span> <span data-ttu-id="7cec8-134">数据配置文件查看器不会使用运行数据事件探查任务的包中存储的连接信息。</span><span class="sxs-lookup"><span data-stu-id="7cec8-134">The Data Profile Viewer does not use the connection information that is stored in the package that ran the Data Profiling task.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7cec8-135">数据配置文件查看器中提供的明细功能会将实时查询发送到原始数据源。</span><span class="sxs-lookup"><span data-stu-id="7cec8-135">The drilldown capability that is available in the Data Profile Viewer sends live queries to the original data source.</span></span> <span data-ttu-id="7cec8-136">这些查询可能会对服务器的性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="7cec8-136">These queries may have a negative impact on the performance of the server.</span></span>  
>   
>  <span data-ttu-id="7cec8-137">如果从并非最近创建的输出文件中深化，则明细查询所返回的行集可能会与计算原始输出时所使用的行集不同。</span><span class="sxs-lookup"><span data-stu-id="7cec8-137">If you drill down from an output file that was not created recently, the drilldown queries might return a different set of rows than those on which the original output was calculated.</span></span>  
  
 <span data-ttu-id="7cec8-138">有关数据配置文件查看器的用户界面的详细信息，请参阅 [Data Profile Viewer F1 Help](../data-profile-viewer-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="7cec8-138">For more information about the user interface of the Data Profile Viewer, see [Data Profile Viewer F1 Help](../data-profile-viewer-f1-help.md).</span></span>  
  
  
