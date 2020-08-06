---
title: " (AlwaysOn 可用性组向导) 的验证页 |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.validation.f1
- sql12.swb.addreplicawizard.validation.f1
- sql12.swb.adddatabasewizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f2010074a357932f8af7358a05ee6ed16f5c0881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577856"
---
# <a name="validation-page-alwayson-availability-group-wizards"></a><span data-ttu-id="93409-102">“验证”页（AlwaysOn 可用性组向导）</span><span class="sxs-lookup"><span data-stu-id="93409-102">Validation Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="93409-103">本帮助主题介绍 **“验证”** 页中的选项。</span><span class="sxs-lookup"><span data-stu-id="93409-103">This help topic describes the options of the **Validation** page.</span></span> <span data-ttu-id="93409-104">本主题适用于 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]的 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]、 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 和 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="93409-104">This topic applies to the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="93409-105">使用此页可以验证您的环境是否支持您在向导前面的页面中做出的所有配置选择。</span><span class="sxs-lookup"><span data-stu-id="93409-105">Use this page to validate that your environment supports all the configuration choices you made on previous pages of the wizard.</span></span>  
  
##  <a name="validation-page-options"></a><a name="PageOptions"></a><span data-ttu-id="93409-106">验证页选项</span><span class="sxs-lookup"><span data-stu-id="93409-106">Validation Page Options</span></span>  
 <span data-ttu-id="93409-107">**可用性组验证的结果。**</span><span class="sxs-lookup"><span data-stu-id="93409-107">**Results of availability group validation.**</span></span>  
 <span data-ttu-id="93409-108">此网格显示每个已完成的验证步骤的结果。</span><span class="sxs-lookup"><span data-stu-id="93409-108">This grid displays the results of each completed validation step.</span></span> <span data-ttu-id="93409-109">网格列如下所示：</span><span class="sxs-lookup"><span data-stu-id="93409-109">The grid columns are as follows:</span></span>  
  
 <span data-ttu-id="93409-110">**名称**</span><span class="sxs-lookup"><span data-stu-id="93409-110">**Name**</span></span>  
 <span data-ttu-id="93409-111">显示描述特定步骤的短语。</span><span class="sxs-lookup"><span data-stu-id="93409-111">Displays a phrase that describes a specific step.</span></span>  
  
 <span data-ttu-id="93409-112">**结果**</span><span class="sxs-lookup"><span data-stu-id="93409-112">**Result**</span></span>  
 <span data-ttu-id="93409-113">显示以下超链接文本之一。</span><span class="sxs-lookup"><span data-stu-id="93409-113">Displays one of the following hyperlink texts.</span></span> <span data-ttu-id="93409-114">有关给定验证步骤的结果的详细信息，请单击该超链接。</span><span class="sxs-lookup"><span data-stu-id="93409-114">For more information about the result of given validation step, click the hyperlink.</span></span>  
  
|<span data-ttu-id="93409-115">结果</span><span class="sxs-lookup"><span data-stu-id="93409-115">Result</span></span>|<span data-ttu-id="93409-116">说明</span><span class="sxs-lookup"><span data-stu-id="93409-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="93409-117">**错误**</span><span class="sxs-lookup"><span data-stu-id="93409-117">**Error**</span></span>|<span data-ttu-id="93409-118">指示验证步骤失败。</span><span class="sxs-lookup"><span data-stu-id="93409-118">Indicates that the validation step failed.</span></span> <span data-ttu-id="93409-119">单击该链接可以查看错误消息。</span><span class="sxs-lookup"><span data-stu-id="93409-119">Click the link to view the error message.</span></span>|  
|<span data-ttu-id="93409-120">已跳过</span><span class="sxs-lookup"><span data-stu-id="93409-120">**Skipped**</span></span>|<span data-ttu-id="93409-121">指示已通过该验证步骤，因为您所做的选择不需要验证。</span><span class="sxs-lookup"><span data-stu-id="93409-121">Indicates that the validation step was skipped because it is not required by your selections.</span></span> <span data-ttu-id="93409-122">单击该链接可以查看跳过某步骤的原因。</span><span class="sxs-lookup"><span data-stu-id="93409-122">Click the link to view the reason that a step was skipped.</span></span>|  
|<span data-ttu-id="93409-123">**Success**</span><span class="sxs-lookup"><span data-stu-id="93409-123">**Success**</span></span>|<span data-ttu-id="93409-124">指示此验证步骤已成功完成。</span><span class="sxs-lookup"><span data-stu-id="93409-124">Indicates that the validation step completed successfully</span></span>|  
|<span data-ttu-id="93409-125">**警告**</span><span class="sxs-lookup"><span data-stu-id="93409-125">**Warning**</span></span>|<span data-ttu-id="93409-126">指示可用性组配置可能存在问题。</span><span class="sxs-lookup"><span data-stu-id="93409-126">Indicates a potential issue with the availability group configuration.</span></span>  <span data-ttu-id="93409-127">单击该链接可以查看警告消息。</span><span class="sxs-lookup"><span data-stu-id="93409-127">Click the link to view the warning message.</span></span>|  
  
 <span data-ttu-id="93409-128">**重新运行验证**</span><span class="sxs-lookup"><span data-stu-id="93409-128">**Re-run Validation**</span></span>  
 <span data-ttu-id="93409-129">如果您在该向导之外针对验证错误做出了更改，则单击此选项可以重复执行验证步骤。</span><span class="sxs-lookup"><span data-stu-id="93409-129">Click to repeat the validation steps if you make a change outside of the wizard in response to a validation error.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="93409-130">相关任务</span><span class="sxs-lookup"><span data-stu-id="93409-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="93409-131">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="93409-131">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="93409-132">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="93409-132">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="93409-133">使用“将数据库添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="93409-133">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="93409-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93409-134">See Also</span></span>  
 [<span data-ttu-id="93409-135">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="93409-135">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
