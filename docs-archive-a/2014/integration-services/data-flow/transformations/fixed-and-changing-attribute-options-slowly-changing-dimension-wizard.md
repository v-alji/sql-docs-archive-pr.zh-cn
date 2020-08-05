---
title: 固定和变化的属性选项（渐变维度向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df654cd97b343179828ebd94dea40eacc90e003d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578970"
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a><span data-ttu-id="b6e6c-102">固定的属性选项和变化的属性选项（渐变维度向导）</span><span class="sxs-lookup"><span data-stu-id="b6e6c-102">Fixed and Changing Attribute Options (Slowly Changing Dimension Wizard</span></span>
  <span data-ttu-id="b6e6c-103">可以使用 **“固定的属性选项和变化的属性选项”** 对话框，指定如何对固定的属性和变化的属性中的更改进行响应。</span><span class="sxs-lookup"><span data-stu-id="b6e6c-103">Use the **Fixed and Changing Attribute Options** dialog box to specify how to respond to changes in fixed and changing attributes.</span></span>  
  
 <span data-ttu-id="b6e6c-104">若要了解有关此向导的详细信息，请参阅 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e6c-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b6e6c-105">选项</span><span class="sxs-lookup"><span data-stu-id="b6e6c-105">Options</span></span>  
 <span data-ttu-id="b6e6c-106">**固定的属性**</span><span class="sxs-lookup"><span data-stu-id="b6e6c-106">**Fixed attributes**</span></span>  
 <span data-ttu-id="b6e6c-107">对于固定的属性，指示在固定的属性中检测到更改时，任务是否失败。</span><span class="sxs-lookup"><span data-stu-id="b6e6c-107">For fixed attributes, indicate whether the task should fail if a change is detected in a fixed attribute.</span></span>  
  
 <span data-ttu-id="b6e6c-108">**变化的属性**</span><span class="sxs-lookup"><span data-stu-id="b6e6c-108">**Changing attributes**</span></span>  
 <span data-ttu-id="b6e6c-109">对于变化的属性，指示在变化的属性中检测到更改时，任务是否应更改除当前记录之外的过时记录或过期记录。</span><span class="sxs-lookup"><span data-stu-id="b6e6c-109">For changing attributes, indicate whether the task should change outdated or expired records, in addition to current records, when a change is detected in a changing attribute.</span></span> <span data-ttu-id="b6e6c-110">过期记录指被历史特性中的更改（类型 2 更改）替换为较新记录的记录。</span><span class="sxs-lookup"><span data-stu-id="b6e6c-110">An expired record is a record that has been replaced with a newer record by a change in a historical attribute (a Type 2 change).</span></span> <span data-ttu-id="b6e6c-111">选中此选项可能会对在关系数据仓库上构造的多维对象施加其他处理要求。</span><span class="sxs-lookup"><span data-stu-id="b6e6c-111">Selecting this option may impose additional processing requirements on a multidimensional object constructed on the relational data warehouse.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e6c-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6e6c-112">See Also</span></span>  
 [<span data-ttu-id="b6e6c-113">使用渐变维度向导配置输出</span><span class="sxs-lookup"><span data-stu-id="b6e6c-113">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
