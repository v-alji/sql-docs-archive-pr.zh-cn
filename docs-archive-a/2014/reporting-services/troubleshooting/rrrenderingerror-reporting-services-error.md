---
title: rrRenderingError - Reporting Services 错误 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rrRenderingError
ms.assetid: 0751efc3-b81b-44ee-8aac-8560f86ca322
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b44b042c5f3c0cfdb9ffb99d3f45ed073beb972a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689724"
---
# <a name="rrrenderingerror---reporting-services-error"></a><span data-ttu-id="c5eb0-102">rrRenderingError - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="c5eb0-102">rrRenderingError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="c5eb0-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="c5eb0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c5eb0-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="c5eb0-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="c5eb0-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="c5eb0-105">Event ID</span></span>|<span data-ttu-id="c5eb0-106">rrRenderingError</span><span class="sxs-lookup"><span data-stu-id="c5eb0-106">rrRenderingError</span></span>|  
|<span data-ttu-id="c5eb0-107">事件源</span><span class="sxs-lookup"><span data-stu-id="c5eb0-107">Event Source</span></span>|<span data-ttu-id="c5eb0-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings</span><span class="sxs-lookup"><span data-stu-id="c5eb0-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings</span></span>|  
|<span data-ttu-id="c5eb0-109">组件</span><span class="sxs-lookup"><span data-stu-id="c5eb0-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="c5eb0-110">消息正文</span><span class="sxs-lookup"><span data-stu-id="c5eb0-110">Message Text</span></span>|<span data-ttu-id="c5eb0-111">呈现报表时出错。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-111">An error occurred during rendering of the report.</span></span> <span data-ttu-id="c5eb0-112">(rrRenderingError) %1</span><span class="sxs-lookup"><span data-stu-id="c5eb0-112">(rrRenderingError) %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c5eb0-113">说明</span><span class="sxs-lookup"><span data-stu-id="c5eb0-113">Explanation</span></span>  
 <span data-ttu-id="c5eb0-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 无法呈现或导出报表时返回此消息。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-114">This message is returned when [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] cannot render or export the report.</span></span>  
  
 <span data-ttu-id="c5eb0-115">当指定的 RDL 页大小无效时，通常会出现此消息，指明不支持该大小。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-115">A message that indicates that the size is not supported is typically caused when the specified RDL page size is not valid.</span></span> <span data-ttu-id="c5eb0-116">请指定有效的 RDL 页大小，然后重试。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-116">Specify a valid RDL page size and then try again.</span></span>  
  
 <span data-ttu-id="c5eb0-117">当指定了不支持的单位类型时，通常会出现此消息，指明不支持 RDL 大小度量值。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-117">A message that indicates that an RDL size measurement is not supported is typically caused when an unsupported unit type is specified.</span></span> <span data-ttu-id="c5eb0-118">有效的单位类型包括 cm、in、mm、pc 和 pt。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-118">Valid unit types are cm, in, mm, pc, and pt.</span></span> <span data-ttu-id="c5eb0-119">请指定有效的单位类型，然后重试。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-119">Specify a valid unit type and then try again.</span></span>  
  
 <span data-ttu-id="c5eb0-120">为页大小指定了负值（例如 -5 cm）时，通常会出现此消息，指明不支持负的大小度量值。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-120">A message that indicates that a negative size is not supported is typically caused when a negative measurement for the page size, for example -5 cm, is specified.</span></span> <span data-ttu-id="c5eb0-121">请为页大小指定一个正数，然后重试。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-121">Specify a positive number for the page size and then try again.</span></span>  
  
 <span data-ttu-id="c5eb0-122">当页大小度量值超出有效的页边距大小范围时，通常会出现此消息，指明指定的 RDL 大小超出范围。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-122">A message that indicates that an RDL size is specified out of range is typically caused when a measurement for the page size is outside of the valid page margin size.</span></span> <span data-ttu-id="c5eb0-123">请为页大小指定位于有效页边距大小范围内的度量值。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-123">Specify a measurement for the page size that is within the valid page margin sizes.</span></span>  
  
 <span data-ttu-id="c5eb0-124">当 RDL 中指定的颜色无效时，通常会出现此消息，指明不支持指定的颜色。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-124">A message that indicates that a color specified is not supported is typically caused when a color specified in the RDL is not valid.</span></span> <span data-ttu-id="c5eb0-125">请选择一种 RDL 支持的颜色，然后重试。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-125">Choose a color supported by RDL and then try again.</span></span>  
  
 <span data-ttu-id="c5eb0-126">当指定的操作标签无效时，通常会出现此消息，指明只有使用单个操作时操作标签才是可选的，添加多个操作要求每个操作都有对应标签。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-126">A message that indicates that the action label is only optional when using a single action and that adding multiple actions requires labels for each action is typically caused when an action label is specified and it is not valid.</span></span> <span data-ttu-id="c5eb0-127">请为每个操作指定有效的操作标签。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-127">Specify a valid action label for each action.</span></span>  
  
 <span data-ttu-id="c5eb0-128">当为数据类型指定了不正确的样式值时，通常会出现此消息，指明样式参数必须为特定类型。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-128">A message that indicates the style argument has to be of a specific type is typically caused when an incorrect style value for the data type is specified.</span></span> <span data-ttu-id="c5eb0-129">RDL 规范中标识了可用作不同 RDL 元素的样式值的有效类型。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-129">The RDL specification identifies the valid types that you can use in the style values of different RDL elements.</span></span> <span data-ttu-id="c5eb0-130">例如，不正确的背景颜色样式值为“2pt”，不正确的高度值为“true”。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-130">For example, an incorrect style value for background color is "2pt" and incorrect value for height is "true".</span></span> <span data-ttu-id="c5eb0-131">请指定正确的值，然后重试。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-131">Specify a correct value and then try again.</span></span>  
  
 <span data-ttu-id="c5eb0-132">当指定的边框样式无效时，通常会出现此消息，指明不支持该边框样式。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-132">A message that indicates that the border style is not supported is typically caused when the border style specified is not valid.</span></span> <span data-ttu-id="c5eb0-133">请指定受支持的边框样式，然后重试。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-133">Specify a supported border style and then try again.</span></span>  
  
 <span data-ttu-id="c5eb0-134">为图像报表项指定的 MIME 类型无效时，通常会出现此消息，指明不支持该图像 MIME 类型。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-134">A message that indicates that the image mimetype is not supported is typically caused when the specified mimetype for an image report item is not valid.</span></span> <span data-ttu-id="c5eb0-135">请为报表项指定受支持的 MIME 类型，然后重试。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-135">Specify a supported mimetype for the report item and then try again.</span></span>  
  
 <span data-ttu-id="c5eb0-136">当 Excel 工作表中的行数超出限制时，通常会出现此消息，指明行数超出了每页允许的最大行数。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-136">A message that indicates that the number of rows exceeds the maximum possible rows per sheet is typically caused when the number of rows in an Excel worksheet is exceeded.</span></span> <span data-ttu-id="c5eb0-137">Excel 最多支持 65,000 行。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-137">Excel supports up to 65,000 rows.</span></span>  
  
 <span data-ttu-id="c5eb0-138">当 Excel 工作表中的列数超出限制时，通常会出现此消息，指明列数超出了每页允许的最大列数。</span><span class="sxs-lookup"><span data-stu-id="c5eb0-138">A message that indicates that the number of columns exceeds the maximum possible columns per sheet is typically caused when the number of columns in an Excel worksheet is exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c5eb0-139">用户操作</span><span class="sxs-lookup"><span data-stu-id="c5eb0-139">User Action</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="c5eb0-140">仅内部</span><span class="sxs-lookup"><span data-stu-id="c5eb0-140">Internal-Only</span></span>  
  
