---
title: 推断维度成员（渐变维度向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dda4345b91c69b134516baab2e5ba9b9990bd6af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589797"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a><span data-ttu-id="367b0-102">推断维度成员（渐变维度向导）</span><span class="sxs-lookup"><span data-stu-id="367b0-102">Inferred Dimension Members (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="367b0-103">可以使用 **“推断维度成员”** 对话框指定使用推断成员的选项。</span><span class="sxs-lookup"><span data-stu-id="367b0-103">Use the **Inferred Dimension Members** dialog box to specify options for using inferred members.</span></span> <span data-ttu-id="367b0-104">当事实数据表引用尚未加载的维度成员时，存在推断成员。</span><span class="sxs-lookup"><span data-stu-id="367b0-104">Inferred members exist when a fact table references dimension members that are not yet loaded.</span></span> <span data-ttu-id="367b0-105">当加载推断成员的数据后，可以更新现有记录，而不必创建一个新记录。</span><span class="sxs-lookup"><span data-stu-id="367b0-105">When data for the inferred member is loaded, you can update the existing record rather than create a new one.</span></span>  
  
 <span data-ttu-id="367b0-106">若要了解有关此向导的详细信息，请参阅 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="367b0-106">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="367b0-107">选项</span><span class="sxs-lookup"><span data-stu-id="367b0-107">Options</span></span>  
 <span data-ttu-id="367b0-108">**启用推断成员支持**</span><span class="sxs-lookup"><span data-stu-id="367b0-108">**Enable inferred member support**</span></span>  
 <span data-ttu-id="367b0-109">如果选择启用推断成员，必须选择以下两个选项之一。</span><span class="sxs-lookup"><span data-stu-id="367b0-109">If you choose to enable inferred members, you must select one of the two options that follow.</span></span>  
  
 <span data-ttu-id="367b0-110">**带更改类型的列均为空**</span><span class="sxs-lookup"><span data-stu-id="367b0-110">**All columns with a change type are null**</span></span>  
 <span data-ttu-id="367b0-111">指定是否对新推断成员记录中所有带更改类型的列输入空值。</span><span class="sxs-lookup"><span data-stu-id="367b0-111">Specify whether to enter null values in all columns with a change type in the new inferred member record.</span></span>  
  
 <span data-ttu-id="367b0-112">**使用布尔值列指示当前记录是否为推断成员**</span><span class="sxs-lookup"><span data-stu-id="367b0-112">**Use a Boolean column to indicate whether the current record is an inferred member**</span></span>  
 <span data-ttu-id="367b0-113">指定是否使用一个现有的布尔值列来指示当前记录是不是推断成员。</span><span class="sxs-lookup"><span data-stu-id="367b0-113">Specify whether to use an existing Boolean column to indicate whether the current record is an inferred member.</span></span>  
  
 <span data-ttu-id="367b0-114">**推断成员指示器**</span><span class="sxs-lookup"><span data-stu-id="367b0-114">**Inferred member indicator**</span></span>  
 <span data-ttu-id="367b0-115">如果如上所述选择了使用布尔值列来指示推断成员，请从该列表中选择此列。</span><span class="sxs-lookup"><span data-stu-id="367b0-115">If you have chosen to use a Boolean column to indicate inferred members as described above, select the column from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367b0-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="367b0-116">See Also</span></span>  
 [<span data-ttu-id="367b0-117">使用渐变维度向导配置输出</span><span class="sxs-lookup"><span data-stu-id="367b0-117">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
