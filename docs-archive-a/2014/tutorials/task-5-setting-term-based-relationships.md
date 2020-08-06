---
title: 任务5：设置基于字词的关系 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1589ec5843053baa6c42a0b9b0dec019c887da9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691363"
---
# <a name="task-5-setting-term-based-relationships"></a><span data-ttu-id="1209e-102">任务 5：设置基于字词的关系</span><span class="sxs-lookup"><span data-stu-id="1209e-102">Task 5: Setting Term Based Relationships</span></span>
  <span data-ttu-id="1209e-103">在此任务中，将为**供应商名称**域的值定义一些基于字词的关系。</span><span class="sxs-lookup"><span data-stu-id="1209e-103">In this task, you define a few term-based relations for values for the **Supplier Name** domain.</span></span> <span data-ttu-id="1209e-104">通过基于字词的关系，您可以对属于域中某个值的字词进行更正。</span><span class="sxs-lookup"><span data-stu-id="1209e-104">A term-based relation enables you to make a correction to a term that is part of a value in a domain.</span></span> <span data-ttu-id="1209e-105">基于字词的关系使完全相同的多个值（只有其公共部分的拼写除外）可被视为相同的同义词。</span><span class="sxs-lookup"><span data-stu-id="1209e-105">It enables multiple values that are identical except for the spelling of a common part of them to be considered identical synonyms.</span></span> <span data-ttu-id="1209e-106">例如， **inc.** 可以更正为 "**合并**"。</span><span class="sxs-lookup"><span data-stu-id="1209e-106">For example, **Inc.** can be corrected to **Incorporated**.</span></span> <span data-ttu-id="1209e-107">DQS 在知识发现、清理或匹配过程中使用这些关系。</span><span class="sxs-lookup"><span data-stu-id="1209e-107">DQS uses these relations in the knowledge discovery, cleansing, or matching processes.</span></span> <span data-ttu-id="1209e-108">有关更多详细信息，请参阅[创建基于字词的关系](https://msdn.microsoft.com/library/hh510404.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1209e-108">See [Create Term-based Relations](https://msdn.microsoft.com/library/hh510404.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="1209e-109">选择 "**域列表**" 中的 "**供应商名称**"。</span><span class="sxs-lookup"><span data-stu-id="1209e-109">Select **Supplier Name** in the **Domain list**.</span></span>  
  
2.  <span data-ttu-id="1209e-110">切换到右窗格中的 "**基于字词的关系**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1209e-110">Switch to the **Term-Based Relationships** tab in the right pane.</span></span>  
  
3.  <span data-ttu-id="1209e-111">单击工具栏上的 "**添加新关系**" 按钮，以向表中添加关系。</span><span class="sxs-lookup"><span data-stu-id="1209e-111">Click **Add new relation** button on the toolbar to add a relation to the table.</span></span>  
  
4.  <span data-ttu-id="1209e-112">键入 **"Co** " 作为 "**正确**的" 字段的 "**值**" 字段和 "**公司**"。</span><span class="sxs-lookup"><span data-stu-id="1209e-112">Type **Co.** for the **Value** field and **Company** for the **Correct To** field.</span></span>  
  
5.  <span data-ttu-id="1209e-113">对以下值重复前两个步骤：</span><span class="sxs-lookup"><span data-stu-id="1209e-113">Repeat the previous two steps for the following values:</span></span>  
  
    |<span data-ttu-id="1209e-114">值</span><span class="sxs-lookup"><span data-stu-id="1209e-114">Value</span></span>|<span data-ttu-id="1209e-115">更正为</span><span class="sxs-lookup"><span data-stu-id="1209e-115">Correct To</span></span>|  
    |-----------|----------------|  
    |<span data-ttu-id="1209e-116">Corp.</span><span class="sxs-lookup"><span data-stu-id="1209e-116">Corp.</span></span>|<span data-ttu-id="1209e-117">Corporation</span><span class="sxs-lookup"><span data-stu-id="1209e-117">Corporation</span></span>|  
    |<span data-ttu-id="1209e-118">Inc.</span><span class="sxs-lookup"><span data-stu-id="1209e-118">Inc.</span></span>|<span data-ttu-id="1209e-119">Incorporated</span><span class="sxs-lookup"><span data-stu-id="1209e-119">Incorporated</span></span>|  
  
     <span data-ttu-id="1209e-120">![基于字词的关系](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "基于字词的关系")</span><span class="sxs-lookup"><span data-stu-id="1209e-120">![Term Based Relations](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Term Based Relations")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="1209e-121">下一步</span><span class="sxs-lookup"><span data-stu-id="1209e-121">Next Step</span></span>  
 [<span data-ttu-id="1209e-122">任务 6：设置同义词</span><span class="sxs-lookup"><span data-stu-id="1209e-122">Task 6: Setting Synonyms</span></span>](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
