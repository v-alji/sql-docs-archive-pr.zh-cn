---
title: 外部工具的参数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71a7fb99eee3286d21a405e9564d046847406a1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590506"
---
# <a name="arguments-for-external-tools"></a><span data-ttu-id="f51f9-102">外部工具的参数</span><span class="sxs-lookup"><span data-stu-id="f51f9-102">Arguments for External Tools</span></span>
  <span data-ttu-id="f51f9-103">参数是在从“工具”  菜单中启动外部工具时，由 Studio 环境提供值的变量。</span><span class="sxs-lookup"><span data-stu-id="f51f9-103">Arguments are variables that the Studio environment supplies values for when an external tool is launched from the **Tools** menu.</span></span> <span data-ttu-id="f51f9-104">可以使用“外部工具”对话框将外部工具（如记事本）添加到“工具”菜单。</span><span class="sxs-lookup"><span data-stu-id="f51f9-104">External tools such as Notepad can be added to the **Tools** menu using the **External Tools** dialog box.</span></span>  
  
 <span data-ttu-id="f51f9-105">下表列出了外部工具的参数。</span><span class="sxs-lookup"><span data-stu-id="f51f9-105">The following table lists arguments for external tools.</span></span>  
  
|<span data-ttu-id="f51f9-106">名称</span><span class="sxs-lookup"><span data-stu-id="f51f9-106">Name</span></span>|<span data-ttu-id="f51f9-107">参数</span><span class="sxs-lookup"><span data-stu-id="f51f9-107">Argument</span></span>|<span data-ttu-id="f51f9-108">说明</span><span class="sxs-lookup"><span data-stu-id="f51f9-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="f51f9-109">**项路径**</span><span class="sxs-lookup"><span data-stu-id="f51f9-109">**Item Path**</span></span>|<span data-ttu-id="f51f9-110">$(ItemPath)</span><span class="sxs-lookup"><span data-stu-id="f51f9-110">$(ItemPath)</span></span>|<span data-ttu-id="f51f9-111">当前源代码的完整文件名（以驱动器 + 路径 + 文件名形式定义）；如果一个非源代码窗口处于活动状态，则该参数将是空白的。</span><span class="sxs-lookup"><span data-stu-id="f51f9-111">The complete file name of the current source (defined as drive + path + file name); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="f51f9-112">**项目录**</span><span class="sxs-lookup"><span data-stu-id="f51f9-112">**Item Directory**</span></span>|<span data-ttu-id="f51f9-113">$(ItemDir)</span><span class="sxs-lookup"><span data-stu-id="f51f9-113">$(ItemDir)</span></span>|<span data-ttu-id="f51f9-114">当前源代码的目录（以驱动器 + 路径形式定义）；如果一个非源代码窗口处于活动状态，则该参数将是空白的。</span><span class="sxs-lookup"><span data-stu-id="f51f9-114">The directory of the current source (defined as drive + path); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="f51f9-115">**项文件名**</span><span class="sxs-lookup"><span data-stu-id="f51f9-115">**Item File Name**</span></span>|<span data-ttu-id="f51f9-116">$(ItemFilename)</span><span class="sxs-lookup"><span data-stu-id="f51f9-116">$(ItemFilename)</span></span>|<span data-ttu-id="f51f9-117">当前源代码的文件名（定义为文件名）；如果一个非源代码窗口处于活动状态，则该参数将是空白的。</span><span class="sxs-lookup"><span data-stu-id="f51f9-117">The file name of the current source (defined as file name); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="f51f9-118">**项扩展名**</span><span class="sxs-lookup"><span data-stu-id="f51f9-118">**Item extension**</span></span>|<span data-ttu-id="f51f9-119">$(ItemExt)</span><span class="sxs-lookup"><span data-stu-id="f51f9-119">$(ItemExt)</span></span>|<span data-ttu-id="f51f9-120">当前源代码的文件扩展名</span><span class="sxs-lookup"><span data-stu-id="f51f9-120">The file name extension of the current source.</span></span>|  
|<span data-ttu-id="f51f9-121">**当前行** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f51f9-121">**Current Line** <sup>1</sup></span></span>|<span data-ttu-id="f51f9-122">$(CurLine)</span><span class="sxs-lookup"><span data-stu-id="f51f9-122">$(CurLine)</span></span>|<span data-ttu-id="f51f9-123">游标在编辑器中的当前行位置。</span><span class="sxs-lookup"><span data-stu-id="f51f9-123">The current line position of the cursor in the editor.</span></span>|  
|<span data-ttu-id="f51f9-124">**当前列**1</span><span class="sxs-lookup"><span data-stu-id="f51f9-124">**Current Column**1</span></span>|<span data-ttu-id="f51f9-125">$(CurCol)</span><span class="sxs-lookup"><span data-stu-id="f51f9-125">$(CurCol)</span></span>|<span data-ttu-id="f51f9-126">游标在编辑器中的当前列位置。</span><span class="sxs-lookup"><span data-stu-id="f51f9-126">The current column position of the cursor in the editor.</span></span>|  
|<span data-ttu-id="f51f9-127">**当前文本**1</span><span class="sxs-lookup"><span data-stu-id="f51f9-127">**Current Text**1</span></span>|<span data-ttu-id="f51f9-128">$(CurText)</span><span class="sxs-lookup"><span data-stu-id="f51f9-128">$(CurText)</span></span>|<span data-ttu-id="f51f9-129">当前文本（当前游标位置下的字，或单行选择（如果存在））。</span><span class="sxs-lookup"><span data-stu-id="f51f9-129">The current text (the word under the current cursor position, or a single-line selection, if there is one).</span></span>|  
|<span data-ttu-id="f51f9-130">**目标路径**</span><span class="sxs-lookup"><span data-stu-id="f51f9-130">**Target Path**</span></span>|<span data-ttu-id="f51f9-131">$(TargetPath)</span><span class="sxs-lookup"><span data-stu-id="f51f9-131">$(TargetPath)</span></span>|<span data-ttu-id="f51f9-132">目标的完整文件名（以驱动器 + 路径 + 文件名形式定义）。</span><span class="sxs-lookup"><span data-stu-id="f51f9-132">The complete file name of the target (defined as drive + path + file name).</span></span>|  
|<span data-ttu-id="f51f9-133">**目标目录**</span><span class="sxs-lookup"><span data-stu-id="f51f9-133">**Target Directory**</span></span>|<span data-ttu-id="f51f9-134">$(TargetDir)</span><span class="sxs-lookup"><span data-stu-id="f51f9-134">$(TargetDir)</span></span>|<span data-ttu-id="f51f9-135">目标的目录。</span><span class="sxs-lookup"><span data-stu-id="f51f9-135">The directory of the target.</span></span>|  
|<span data-ttu-id="f51f9-136">**目标名称**</span><span class="sxs-lookup"><span data-stu-id="f51f9-136">**Target Name**</span></span>|<span data-ttu-id="f51f9-137">$(TargetName)</span><span class="sxs-lookup"><span data-stu-id="f51f9-137">$(TargetName)</span></span>|<span data-ttu-id="f51f9-138">目标的文件名。</span><span class="sxs-lookup"><span data-stu-id="f51f9-138">The file name of the target.</span></span>|  
|<span data-ttu-id="f51f9-139">**目标扩展名**</span><span class="sxs-lookup"><span data-stu-id="f51f9-139">**Target Extension**</span></span>|<span data-ttu-id="f51f9-140">$(TargetExt)</span><span class="sxs-lookup"><span data-stu-id="f51f9-140">$(TargetExt)</span></span>|<span data-ttu-id="f51f9-141">目标的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="f51f9-141">The file name extension of the target.</span></span>|  
|<span data-ttu-id="f51f9-142">**项目目录**</span><span class="sxs-lookup"><span data-stu-id="f51f9-142">**Project Directory**</span></span>|<span data-ttu-id="f51f9-143">$(ProjDir)</span><span class="sxs-lookup"><span data-stu-id="f51f9-143">$(ProjDir)</span></span>|<span data-ttu-id="f51f9-144">当前项目的目录（以驱动器 + 路径的形式定义）。</span><span class="sxs-lookup"><span data-stu-id="f51f9-144">The directory of the current project (defined as drive + path).</span></span>|  
|<span data-ttu-id="f51f9-145">**项目文件名**</span><span class="sxs-lookup"><span data-stu-id="f51f9-145">**Project File Name**</span></span>|<span data-ttu-id="f51f9-146">$(ProjFileName)</span><span class="sxs-lookup"><span data-stu-id="f51f9-146">$(ProjFileName)</span></span>|<span data-ttu-id="f51f9-147">当前项目的文件名（以驱动器 + 路径 + 文件名形式定义）。</span><span class="sxs-lookup"><span data-stu-id="f51f9-147">The file name of the current project (defined as drive + path + file name).</span></span>|  
|<span data-ttu-id="f51f9-148">**解决方案目录**</span><span class="sxs-lookup"><span data-stu-id="f51f9-148">**Solution Directory**</span></span>|<span data-ttu-id="f51f9-149">$(SolutionDir)</span><span class="sxs-lookup"><span data-stu-id="f51f9-149">$(SolutionDir)</span></span>|<span data-ttu-id="f51f9-150">当前解决方案的目录（以驱动器 + 路径的形式定义）。</span><span class="sxs-lookup"><span data-stu-id="f51f9-150">The directory of the current solution (defined as drive + path).</span></span>|  
|<span data-ttu-id="f51f9-151">**解决方案文件名**</span><span class="sxs-lookup"><span data-stu-id="f51f9-151">**Solution File Name**</span></span>|<span data-ttu-id="f51f9-152">$(SolutionFileName)</span><span class="sxs-lookup"><span data-stu-id="f51f9-152">$(SolutionFileName)</span></span>|<span data-ttu-id="f51f9-153">当前解决方案的文件名（以驱动器 + 路径 + 文件名形式定义）。</span><span class="sxs-lookup"><span data-stu-id="f51f9-153">The file name of the current solution (defined as drive + path + file name).</span></span>|  
  
 <span data-ttu-id="f51f9-154"><sup>1</sup>当前行、当前列或当前文本基于游标在文本编辑器中的位置（如状态栏中所示）。</span><span class="sxs-lookup"><span data-stu-id="f51f9-154"><sup>1</sup> The current line, current column, or current text is based on the position of the cursor in the text editor as shown in the status bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f51f9-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f51f9-155">See Also</span></span>  
 <span data-ttu-id="f51f9-156">["外部工具" 对话框](external-tools-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="f51f9-156">[External Tools Dialog Box](external-tools-dialog-box.md) </span></span>  
 [<span data-ttu-id="f51f9-157">常规用户界面元素</span><span class="sxs-lookup"><span data-stu-id="f51f9-157">General User Interface Elements</span></span>](general-user-interface-elements.md)  
  
  
