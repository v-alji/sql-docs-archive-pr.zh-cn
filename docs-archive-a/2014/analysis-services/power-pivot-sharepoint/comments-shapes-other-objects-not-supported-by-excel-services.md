---
title: Excel Services 不支持以下功能，可能不会显示或仅部分显示：注释、形状或其他对象 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
author: minewiskan
ms.author: owend
ms.openlocfilehash: 67c2989ab89f242fdce2ca64f3c2f361e17d49ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689616"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a><span data-ttu-id="1e853-102">Excel Services 不支持以下功能并且可能无法显示或者只能部分显示以下功能：注释、形状或其他对象</span><span class="sxs-lookup"><span data-stu-id="1e853-102">The following features are not supported by Excel Services and may not display or may display only partially: Comments, Shapes, or other objects</span></span>
  <span data-ttu-id="1e853-103">在您将切片器从 PowerPivot 字段列表添加到 PowerPivot 工作簿时会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="1e853-103">This error occurs when you add Slicers to a PowerPivot workbook from a PowerPivot Field List.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e853-104">详细信息</span><span class="sxs-lookup"><span data-stu-id="1e853-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e853-105">适用于</span><span class="sxs-lookup"><span data-stu-id="1e853-105">Applies to</span></span>|<span data-ttu-id="1e853-106">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="1e853-106">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="1e853-107">产品版本</span><span class="sxs-lookup"><span data-stu-id="1e853-107">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="1e853-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e853-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="1e853-109">原因</span><span class="sxs-lookup"><span data-stu-id="1e853-109">Cause</span></span>|<span data-ttu-id="1e853-110">Excel Web Access 无法呈现用于控制从 PowerPivot 字段列表添加到某一工作簿的切片器的位置和格式的形状对象。</span><span class="sxs-lookup"><span data-stu-id="1e853-110">Excel Web Access cannot render the Shape object used to control positioning and formatting of Slicers added to a workbook from the PowerPivot Field List.</span></span>|  
|<span data-ttu-id="1e853-111">消息正文</span><span class="sxs-lookup"><span data-stu-id="1e853-111">Message Text</span></span>|<span data-ttu-id="1e853-112">Excel Services 不支持以下功能并且可能无法显示或者只能部分显示以下功能：</span><span class="sxs-lookup"><span data-stu-id="1e853-112">The following features are not supported by Excel Services and may not display or may display only partially:</span></span><br /><br /> <span data-ttu-id="1e853-113">注释、形状或其他对象</span><span class="sxs-lookup"><span data-stu-id="1e853-113">Comments, Shapes, or other objects</span></span><br /><br /> <span data-ttu-id="1e853-114">某些功能（例如外部数据查询）显示只能在 Microsoft Excel 中刷新的缓存数据。</span><span class="sxs-lookup"><span data-stu-id="1e853-114">Some features, such as external data queries, display cached data which can only be refreshed in Microsoft Excel.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1e853-115">说明</span><span class="sxs-lookup"><span data-stu-id="1e853-115">Explanation</span></span>  
 <span data-ttu-id="1e853-116">当您在浏览器中打开 PowerPivot 工作簿并单击消息的 "**详细信息**" 按钮、**不支持的功能、此工作簿可能无法按预期方式显示**时，Excel Web 访问将显示此错误。</span><span class="sxs-lookup"><span data-stu-id="1e853-116">Excel Web Access shows this error when you open a PowerPivot workbook in a browser and you click the **Details** button for the message, **Unsupported Features This workbook may not display as intended**.</span></span>  
  
 <span data-ttu-id="1e853-117">出现此错误的原因是因为 PowerPivot 工作簿包含其布局由 Excel 中隐藏的形状对象控制的切片器。</span><span class="sxs-lookup"><span data-stu-id="1e853-117">This error occurs because the PowerPivot workbook contains Slicers whose layout is controlled by a hidden Shape object in Excel.</span></span> <span data-ttu-id="1e853-118">该形状对象在水平和垂直位置上控制切片器的格式和位置。</span><span class="sxs-lookup"><span data-stu-id="1e853-118">The Shape object controls the formatting and positioning of the Slicers in horizontal and vertical placements.</span></span>  
  
 <span data-ttu-id="1e853-119">Excel Services 无法呈现形状对象，但因为该对象是隐藏的，所以尽管无法呈现，但这并不是问题。</span><span class="sxs-lookup"><span data-stu-id="1e853-119">Excel Services cannot render a Shape object, but because the object is hidden, the fact that it does not render is not an issue.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1e853-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="1e853-120">User Action</span></span>  
 <span data-ttu-id="1e853-121">可以忽略此错误。</span><span class="sxs-lookup"><span data-stu-id="1e853-121">This error can be ignored.</span></span> <span data-ttu-id="1e853-122">单击 **“确定”** 以便关闭该错误消息并且可以放心地继续使用工作簿和切片器。</span><span class="sxs-lookup"><span data-stu-id="1e853-122">Click **OK** to close the error message and proceed to use the workbook and Slicers with no problem.</span></span>  
  
  
