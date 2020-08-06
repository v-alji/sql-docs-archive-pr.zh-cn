---
title: 配置清理和匹配活动的阈值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0faf64e96468a3a9aac0de12d3ec3acbb1e1ed85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683071"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a><span data-ttu-id="025e4-102">配置清理和匹配活动的阈值</span><span class="sxs-lookup"><span data-stu-id="025e4-102">Configure Threshold Values for Cleansing and Matching</span></span>
  <span data-ttu-id="025e4-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中配置在计算机辅助清理和匹配活动中使用的阈值。</span><span class="sxs-lookup"><span data-stu-id="025e4-103">This topic describes how to configure threshold values that will be used during the computer-assisted cleansing and matching activities in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="025e4-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="025e4-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="025e4-105">Security</span><span class="sxs-lookup"><span data-stu-id="025e4-105">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="025e4-106">权限</span><span class="sxs-lookup"><span data-stu-id="025e4-106">Permissions</span></span>  
 <span data-ttu-id="025e4-107">您必须对 DQS_MAIN 数据库具有 dqs_administrator 角色才能配置这些阈值。</span><span class="sxs-lookup"><span data-stu-id="025e4-107">You must have the dqs_administrator role on the DQS_MAIN database to configure these threshold values.</span></span>  
  
##  <a name="configuring-the-threshold-values"></a><a name="Configure"></a> <span data-ttu-id="025e4-108">配置阈值</span><span class="sxs-lookup"><span data-stu-id="025e4-108">Configuring the Threshold Values</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="025e4-109">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="025e4-109">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="025e4-110">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“配置”**。</span><span class="sxs-lookup"><span data-stu-id="025e4-110">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="025e4-111">接下来，单击 "**常规设置**" 选项卡。此选项卡允许您指定清理和匹配活动的阈值。</span><span class="sxs-lookup"><span data-stu-id="025e4-111">Next, click the **General Settings** tab. This tab enables you to specify threshold values for cleansing as well as matching activities.</span></span>  
  
4.  <span data-ttu-id="025e4-112">若要为清理活动指定阈值，请在 **“交互式清理”** 区域下的以下各框中指定适当的值：</span><span class="sxs-lookup"><span data-stu-id="025e4-112">To specify threshold values for the cleansing activity, specify appropriate values in the following boxes under the **Interactive Cleansing** area:</span></span>  
  
    -   <span data-ttu-id="025e4-113">**用于建议的最低分数**：在计算机辅助清除过程中 DQS 用于建议替换值的最低分数或置信度。</span><span class="sxs-lookup"><span data-stu-id="025e4-113">**Min score for suggestions**: The minimum score or the confidence level that will be used by DQS for suggesting replacements for a value during the computer-assisted cleansing process.</span></span> <span data-ttu-id="025e4-114">以相应百分比值的小数表示形式输入一个值。</span><span class="sxs-lookup"><span data-stu-id="025e4-114">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="025e4-115">例如，对于 75% 键入 0.75。</span><span class="sxs-lookup"><span data-stu-id="025e4-115">For example, type 0.75 for 75%.</span></span> <span data-ttu-id="025e4-116">该值应小于或等于在 **“用于自动更正的最低分数”** 框中指定的值。</span><span class="sxs-lookup"><span data-stu-id="025e4-116">This value should be less than or equal to the value specified in the **Min score for auto corrections** box.</span></span> <span data-ttu-id="025e4-117">默认值为 0.7。</span><span class="sxs-lookup"><span data-stu-id="025e4-117">The default value is 0.7.</span></span>  
  
    -   <span data-ttu-id="025e4-118">**用于自动更正的最低分数**：在计算机辅助清理过程中 DQS 用于自动更正值的最低分数或置信度。</span><span class="sxs-lookup"><span data-stu-id="025e4-118">**Min score for auto corrections**: The minimum score or the confidence level that will be used by DQS for automatically correcting a value during the computer-assisted cleansing process.</span></span> <span data-ttu-id="025e4-119">以相应百分比值的小数表示形式输入一个值。</span><span class="sxs-lookup"><span data-stu-id="025e4-119">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="025e4-120">例如，对于 90% 输入 0.9。</span><span class="sxs-lookup"><span data-stu-id="025e4-120">For example, enter 0.9 for 90%.</span></span> <span data-ttu-id="025e4-121">默认值为 0.8。</span><span class="sxs-lookup"><span data-stu-id="025e4-121">The default value is 0.8.</span></span>  
  
5.  <span data-ttu-id="025e4-122">若要为匹配活动指定阈值，请在 **“匹配”** 区域下的 **“最低记录分数”** 框中指定一个值。</span><span class="sxs-lookup"><span data-stu-id="025e4-122">To specify threshold value for the matching activity, specify a value in the **Min record score** box under the **Matching** area.</span></span> <span data-ttu-id="025e4-123">此值表示一条记录要被视为另一条记录的匹配项的最低分数。</span><span class="sxs-lookup"><span data-stu-id="025e4-123">This value signifies the minimum score for a record to be considered as a match for another record.</span></span> <span data-ttu-id="025e4-124">默认值为 80%。</span><span class="sxs-lookup"><span data-stu-id="025e4-124">The default value is 80%.</span></span>  
  
6.  <span data-ttu-id="025e4-125">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="025e4-125">Click **Close**.</span></span>  
  
  
