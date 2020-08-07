---
title: “验证警告”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65556
- vdt.dlgbox.validationwarnings
ms.assetid: fc76e234-ec9c-4a19-a65b-cb558ec8268e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4f94c3ae91e077af853db949847bc8448f6a4753
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587662"
---
# <a name="validation-warnings-dialog-box-visual-database-tools"></a><span data-ttu-id="b29b2-102">“验证警告”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b29b2-102">Validation Warnings Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="b29b2-103">如果尝试保存的修改具有潜在的破坏性副作用，或者数据库提交操作很可能会失败，则会显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="b29b2-103">This dialog box appears if you attempt to save modifications with potentially damaging side effects, or if the database commit operation is likely to fail.</span></span> <span data-ttu-id="b29b2-104">此对话框可指示这些副作用可能会是什么或提交操作可能失败的原因。</span><span class="sxs-lookup"><span data-stu-id="b29b2-104">This dialog box indicates what those side effects might be or why the commit operation might fail.</span></span> <span data-ttu-id="b29b2-105">使用此对话框可以选择继续修改还是取消操作。</span><span class="sxs-lookup"><span data-stu-id="b29b2-105">It gives you the chance to continue with the modification or cancel the operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b29b2-106">在尝试将修改传输到数据库或保存更改脚本时，将显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="b29b2-106">This dialog box appears when you attempt to transmit your modifications to the database or when you save a change script.</span></span>  
  
 <span data-ttu-id="b29b2-107">以下任一原因都可能导致显示该对话框：</span><span class="sxs-lookup"><span data-stu-id="b29b2-107">The dialog box can appear for any of these reasons:</span></span>  
  
-   <span data-ttu-id="b29b2-108">您可能没有提交所有修改的数据库权限。</span><span class="sxs-lookup"><span data-stu-id="b29b2-108">You might not have database permissions to commit all the modifications.</span></span>  
  
-   <span data-ttu-id="b29b2-109">您的修改将导致生成格式不正确的派生列、默认约束或 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="b29b2-109">Your modifications would result in improperly formed derived columns, default constraints, or check constraints.</span></span>  
  
-   <span data-ttu-id="b29b2-110">对列数据类型的修改可能导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="b29b2-110">A modification to a column's data type might cause data loss.</span></span>  
  
-   <span data-ttu-id="b29b2-111">修改可能导致索引大于 900 字节。</span><span class="sxs-lookup"><span data-stu-id="b29b2-111">A modification would result in an index greater than 900 bytes.</span></span>  
  
-   <span data-ttu-id="b29b2-112">修改将更改分配给绑定到架构的视图或用户定义函数的表或列。</span><span class="sxs-lookup"><span data-stu-id="b29b2-112">A modification would change a table or column contributing to a schema-bound view or user-defined function.</span></span>  
  
-   <span data-ttu-id="b29b2-113">修改将导致重新创建具有一个或多个加密触发器的表；这些触发器将被删除。</span><span class="sxs-lookup"><span data-stu-id="b29b2-113">A modification would result in the re-creation of a table that has one or more encrypted triggers; the triggers will be dropped.</span></span>  
  
-   <span data-ttu-id="b29b2-114">所做的修改将导致对一个表中的列的 ANSI_NULLS 或 ANSI_PADDING 选项进行重要设置，或同时对这两个选项进行设置。</span><span class="sxs-lookup"><span data-stu-id="b29b2-114">Your modifications will yield noteworthy settings of ANSI_NULLS or ANSI_PADDING or both for the columns within one table.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b29b2-115">选项</span><span class="sxs-lookup"><span data-stu-id="b29b2-115">Options</span></span>  
 <span data-ttu-id="b29b2-116">**是**</span><span class="sxs-lookup"><span data-stu-id="b29b2-116">**Yes**</span></span>  
 <span data-ttu-id="b29b2-117">继续操作以生成更改脚本或将修改传输到数据库。</span><span class="sxs-lookup"><span data-stu-id="b29b2-117">Proceed with the operation and generate the change script or transmit the modifications to the database.</span></span> <span data-ttu-id="b29b2-118">提交操作在以下情况仍然会失败：您没有修改数据库的权限；所做的修改会导致索引大于 900 字节；或者修改会导致生成格式不正确的计算列、默认约束或 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="b29b2-118">The commit operation can still fail if you do not have privileges to modify the database, if your modifications will result in an index greater than 900 bytes, or if your modifications will result in an improperly formed computed column, default constraint, or check constraint.</span></span>  
  
 <span data-ttu-id="b29b2-119">**是**</span><span class="sxs-lookup"><span data-stu-id="b29b2-119">**No**</span></span>  
 <span data-ttu-id="b29b2-120">取消保存操作。</span><span class="sxs-lookup"><span data-stu-id="b29b2-120">Cancel the save action.</span></span>  
  
 <span data-ttu-id="b29b2-121">**保存文本文件**</span><span class="sxs-lookup"><span data-stu-id="b29b2-121">**Save Text File**</span></span>  
 <span data-ttu-id="b29b2-122">显示“另存为”  对话框，可以在其中为包含警告列表的文本文件指定位置。</span><span class="sxs-lookup"><span data-stu-id="b29b2-122">Display the **Save As** dialog box, where you can specify a location for a text file containing a list of the warnings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29b2-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b29b2-123">See Also</span></span>  
 <span data-ttu-id="b29b2-124">[&#40;Visual Database Tools 设计表&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b29b2-124">[Design Tables &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b29b2-125">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b29b2-125">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
