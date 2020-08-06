---
title: 解析列引用编辑器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.resolvereferences.mapper.F1
- sql12.dts.designer.resolvereferences.preview.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 600b6f4d5ec12290d654f0854cc548a5bbcf4335
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587516"
---
# <a name="resolve-column-reference-editor"></a><span data-ttu-id="1e82b-102">解析列引用编辑器</span><span class="sxs-lookup"><span data-stu-id="1e82b-102">Resolve Column Reference Editor</span></span>
  <span data-ttu-id="1e82b-103">在某一输入路径断开连接或者在该路径中存在任何未映射的列时，在相应的数据路径旁将显示一个错误图标。</span><span class="sxs-lookup"><span data-stu-id="1e82b-103">When an input path is disconnected or if there are any unmapped columns in the path, an error icon is displayed beside the corresponding data path.</span></span> <span data-ttu-id="1e82b-104">为了简化列引用错误的解决方法，对于执行树中的所有路径，可以使用新的“解决引用”编辑器将未映射的输出列与未映射的输入列相链接。</span><span class="sxs-lookup"><span data-stu-id="1e82b-104">To simplify the resolution of column reference errors, the new Resolve References editor allows you to link unmapped output columns with unmapped input columns for all paths in the execution tree.</span></span> <span data-ttu-id="1e82b-105">“解决引用”编辑器还将突出显示路径以便指示正在解决的路径。</span><span class="sxs-lookup"><span data-stu-id="1e82b-105">The Resolve References editor will also highlight the paths to indicate which paths are being resolved.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e82b-106">现在，即使在某一组件的输入路径断开连接时，也可以编辑该组件</span><span class="sxs-lookup"><span data-stu-id="1e82b-106">It is now possible to edit a component even when its input path is disconnected</span></span>  
  
 <span data-ttu-id="1e82b-107">在所有列引用都已解决后，如果没有任何其他数据路径错误，则在数据路径旁将不会显示错误图标。</span><span class="sxs-lookup"><span data-stu-id="1e82b-107">After all column references have been resolved, if there are no other data path errors, no error icons will be displayed beside the data paths.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1e82b-108">选项</span><span class="sxs-lookup"><span data-stu-id="1e82b-108">Options</span></span>  
 <span data-ttu-id="1e82b-109">未映射的输出列（源）：</span><span class="sxs-lookup"><span data-stu-id="1e82b-109">Unmapped Output Columns (Source):</span></span>  
 <span data-ttu-id="1e82b-110">来自当前未映射的上游路径的列</span><span class="sxs-lookup"><span data-stu-id="1e82b-110">Columns from the upstream path that are not currently mapped</span></span>  
  
 <span data-ttu-id="1e82b-111">映射的列（源）：</span><span class="sxs-lookup"><span data-stu-id="1e82b-111">Mapped Columns (Source):</span></span>  
 <span data-ttu-id="1e82b-112">来自映射到下游路径中的列的上游路径的列</span><span class="sxs-lookup"><span data-stu-id="1e82b-112">Columns from the upstream path that are mapped to columns from the downstream path</span></span>  
  
 <span data-ttu-id="1e82b-113">映射的列（目标）：</span><span class="sxs-lookup"><span data-stu-id="1e82b-113">Mapped Columns (Destination):</span></span>  
 <span data-ttu-id="1e82b-114">来自映射到下游路径中的列的上游路径的列</span><span class="sxs-lookup"><span data-stu-id="1e82b-114">Columns from the upstream path that are mapped to columns from the downstream path</span></span>  
  
 <span data-ttu-id="1e82b-115">未映射的输入列（目标）：</span><span class="sxs-lookup"><span data-stu-id="1e82b-115">Unmapped Input Columns (Destination):</span></span>  
 <span data-ttu-id="1e82b-116">来自当前未映射的下游路径的列</span><span class="sxs-lookup"><span data-stu-id="1e82b-116">Columns from the downstream path that are not currently mapped</span></span>  
  
 <span data-ttu-id="1e82b-117">删除未映射的输入列</span><span class="sxs-lookup"><span data-stu-id="1e82b-117">Delete Unmapped Input Columns</span></span>  
 <span data-ttu-id="1e82b-118">选中“删除未映射的输入列”可以忽略数据路径目标处的未映射的列。</span><span class="sxs-lookup"><span data-stu-id="1e82b-118">Check Delete Unmapped Input Columns to ignore unmapped columns at the destination of the data path.</span></span> <span data-ttu-id="1e82b-119">“预览更改”按钮显示在您按下“确定”按钮时将发生的更改的列表。</span><span class="sxs-lookup"><span data-stu-id="1e82b-119">The Preview Changes button displays a list of the changes that will occur when you press the OK button.</span></span>  
  
  
