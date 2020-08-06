---
title: “评估策略”对话框 -“策略选择”页 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.runnow.f1
ms.assetid: 20075fbe-0b48-42c8-b747-690f1aa23dcf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f68a1ccc7873b6a05d2641ddaa87e8d5b0e5c6d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687760"
---
# <a name="evaluate-policies-dialog-box-policy-selection-page"></a><span data-ttu-id="13769-102">“评估策略”对话框，“策略选择”页</span><span class="sxs-lookup"><span data-stu-id="13769-102">Evaluate Policies Dialog Box, Policy Selection Page</span></span>
  <span data-ttu-id="13769-103">此对话框用于评估基于策略的管理策略。</span><span class="sxs-lookup"><span data-stu-id="13769-103">Use this dialog box to evaluate Policy-Based Management policies.</span></span> <span data-ttu-id="13769-104">选择 **“评估结果”** 页后，可以将策略应用于目标集中不符合这些策略的项。</span><span class="sxs-lookup"><span data-stu-id="13769-104">By selecting the **Evaluation Results** page, you can apply policies to the items in a target set that do not comply with the policies.</span></span>  
  
## <a name="options"></a><span data-ttu-id="13769-105">选项</span><span class="sxs-lookup"><span data-stu-id="13769-105">Options</span></span>  
 <span data-ttu-id="13769-106">**数据源**</span><span class="sxs-lookup"><span data-stu-id="13769-106">**Source**</span></span>  
 <span data-ttu-id="13769-107">指定策略的来源。</span><span class="sxs-lookup"><span data-stu-id="13769-107">Specifies the source of the policies.</span></span> <span data-ttu-id="13769-108">若要更改来源，请单击“浏览”按钮 (**...**) 以打开“选择源”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="13769-108">To change the source, click the Browse (**...**) button to open the **Select Source** dialog box.</span></span>  
  
 <span data-ttu-id="13769-109">**文件**</span><span class="sxs-lookup"><span data-stu-id="13769-109">**Files**</span></span>  
 <span data-ttu-id="13769-110">键入包含基于策略的管理策略的文件的路径，或者使用“浏览”按钮 (**...**) 选择文件。</span><span class="sxs-lookup"><span data-stu-id="13769-110">Type the path of a file that contains a Policy-Based Management policy, or use the Browse (**...**) button to select the file.</span></span>  
  
 <span data-ttu-id="13769-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="13769-111">**Server**</span></span>  
 <span data-ttu-id="13769-112">选择此选项可连接到包含所需策略的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="13769-112">Select to connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that contains the policy that you want.</span></span>  
  
 <span data-ttu-id="13769-113">**策略: 策略**</span><span class="sxs-lookup"><span data-stu-id="13769-113">**Policies: Policy**</span></span>  
 <span data-ttu-id="13769-114">单击可打开指定策略的“策略”对话框。</span><span class="sxs-lookup"><span data-stu-id="13769-114">Click to open the policy dialog box for the specified policy.</span></span>  
  
 <span data-ttu-id="13769-115">**策略: 类别**</span><span class="sxs-lookup"><span data-stu-id="13769-115">**Policies: Category**</span></span>  
 <span data-ttu-id="13769-116">策略的类别。</span><span class="sxs-lookup"><span data-stu-id="13769-116">The category of the policy.</span></span> <span data-ttu-id="13769-117">此框是只读的。</span><span class="sxs-lookup"><span data-stu-id="13769-117">This box is read-only.</span></span>  
  
 <span data-ttu-id="13769-118">**策略: 方面**</span><span class="sxs-lookup"><span data-stu-id="13769-118">**Policies: Facet**</span></span>  
 <span data-ttu-id="13769-119">策略所实现的方面。</span><span class="sxs-lookup"><span data-stu-id="13769-119">The facet implemented by the policy.</span></span> <span data-ttu-id="13769-120">此框是只读的。</span><span class="sxs-lookup"><span data-stu-id="13769-120">This box is read-only.</span></span>  
  
 <span data-ttu-id="13769-121">**诂**</span><span class="sxs-lookup"><span data-stu-id="13769-121">**Evaluate**</span></span>  
 <span data-ttu-id="13769-122">在评估模式下运行策略。</span><span class="sxs-lookup"><span data-stu-id="13769-122">Runs the policy in evaluation mode.</span></span> <span data-ttu-id="13769-123">这会为目标集生成符合报告，但不会重新配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或强制要求以后符合策略。</span><span class="sxs-lookup"><span data-stu-id="13769-123">This generates a compliance report for the target set but does not reconfigure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or enforce future compliance.</span></span>  
  
## <a name="possible-errors"></a><span data-ttu-id="13769-124">可能出现的错误</span><span class="sxs-lookup"><span data-stu-id="13769-124">Possible Errors</span></span>  
  
-   <span data-ttu-id="13769-125">**找不到目标**</span><span class="sxs-lookup"><span data-stu-id="13769-125">**No targets found**</span></span>  
  
     <span data-ttu-id="13769-126">由于任何以下原因，目标集可能为空：</span><span class="sxs-lookup"><span data-stu-id="13769-126">The target set could be empty due to any of the following reasons:</span></span>  
  
    -   <span data-ttu-id="13769-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上没有策略所指定类型的目标。</span><span class="sxs-lookup"><span data-stu-id="13769-127">There are no targets on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] of the type specified by the policy.</span></span>  
  
    -   <span data-ttu-id="13769-128">服务器限制可能排除包含目标的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="13769-128">The server restriction might exclude the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains the target.</span></span>  
  
    -   <span data-ttu-id="13769-129">如果策略位于数据库中的对象（如表、视图或用户）上，数据库可能不会订阅策略类别。</span><span class="sxs-lookup"><span data-stu-id="13769-129">If the policy is on an object in a database (for example a table, view, or user) the database might not subscribe to the category of the policy.</span></span>  
  
    -   <span data-ttu-id="13769-130">目标集筛选器可能排除此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上的所有目标。</span><span class="sxs-lookup"><span data-stu-id="13769-130">The target-set filter might exclude all targets on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="13769-131">目标服务器类型不同于在其中评估策略的服务器的类型。</span><span class="sxs-lookup"><span data-stu-id="13769-131">The target server type is different from the server type on which the policy is evaluated.</span></span> <span data-ttu-id="13769-132">例如，在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]中，如果尝试评估一个为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]创建的策略，则会收到一个空的目标集。</span><span class="sxs-lookup"><span data-stu-id="13769-132">For example, in the [!INCLUDE[ssDE](../../includes/ssde-md.md)], if you try to evaluate a policy that has been created for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you will receive an empty target set</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13769-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13769-133">See Also</span></span>  
 <span data-ttu-id="13769-134">[使用基于策略的管理来管理服务器](administer-servers-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="13769-134">[Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md) </span></span>  
 [<span data-ttu-id="13769-135">“评估策略”对话框，“评估结果”页</span><span class="sxs-lookup"><span data-stu-id="13769-135">Evaluate Policies Dialog Box, Evaluation Results Page</span></span>](evaluate-policies-dialog-box-evaluation-results-page.md)  
  
  
