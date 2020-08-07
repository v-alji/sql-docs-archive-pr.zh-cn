---
title: MDX)  (处理错误 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 357194b9f789fdeacfb65ce3c894d4747867eafb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589316"
---
# <a name="error-handling-mdx"></a><span data-ttu-id="91839-102">错误处理 (MDX)</span><span class="sxs-lookup"><span data-stu-id="91839-102">Error Handling (MDX)</span></span>
  <span data-ttu-id="91839-103">每个多维数据集都可以控制多维表达式 (MDX) 脚本中处理错误的方法。</span><span class="sxs-lookup"><span data-stu-id="91839-103">Each cube can control how errors within a Multidimensional Expressions (MDX) script are handled.</span></span> <span data-ttu-id="91839-104">通过 `ScriptErrorHandlingMode` 枚举器完成错误处理。</span><span class="sxs-lookup"><span data-stu-id="91839-104">Error handling is done through the `ScriptErrorHandlingMode` enumerator.</span></span> <span data-ttu-id="91839-105">此枚举器的可能值包括：</span><span class="sxs-lookup"><span data-stu-id="91839-105">The possible values for this enumerator are:</span></span>  
  
 `IgnoreNone`  
 <span data-ttu-id="91839-106">导致服务器在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] MDX 脚本中发现任何错误时引发错误。</span><span class="sxs-lookup"><span data-stu-id="91839-106">Causes the server to raise an error when [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] finds any error in the MDX script.</span></span>  
  
 `IgnoreAll`  
 <span data-ttu-id="91839-107">导致服务器忽略 MDX 脚本中包含错误（包括语法错误、名称解析错误等）的所有命令。</span><span class="sxs-lookup"><span data-stu-id="91839-107">Causes the server to ignore all commands in the MDX script that contain an error, including syntax errors, name resolution errors, and more.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91839-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91839-108">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
