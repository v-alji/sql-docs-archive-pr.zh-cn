---
title: 作业属性和新作业 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7a5d2ab84ed211a03a3c217bd5f4cd54453a4dc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689239"
---
# <a name="job-properties-and-new-job-general-page"></a><span data-ttu-id="cc91e-102">作业属性和新建作业（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="cc91e-102">Job Properties and New Job (General Page)</span></span>
  <span data-ttu-id="cc91e-103">使用此页可以查看和修改代理作业的常规属性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cc91e-103">Use this page to view and modify the general properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cc91e-104">选项</span><span class="sxs-lookup"><span data-stu-id="cc91e-104">Options</span></span>  
 <span data-ttu-id="cc91e-105">**名称**</span><span class="sxs-lookup"><span data-stu-id="cc91e-105">**Name**</span></span>  
 <span data-ttu-id="cc91e-106">更改作业的名称。</span><span class="sxs-lookup"><span data-stu-id="cc91e-106">Change the name of the job.</span></span>  
  
 <span data-ttu-id="cc91e-107">**所有者**</span><span class="sxs-lookup"><span data-stu-id="cc91e-107">**Owner**</span></span>  
 <span data-ttu-id="cc91e-108">选择作业的所有者。</span><span class="sxs-lookup"><span data-stu-id="cc91e-108">Select the owner for the job.</span></span>  
  
 <span data-ttu-id="cc91e-109">**类别**</span><span class="sxs-lookup"><span data-stu-id="cc91e-109">**Category**</span></span>  
 <span data-ttu-id="cc91e-110">为作业选择作业类别。</span><span class="sxs-lookup"><span data-stu-id="cc91e-110">Select the job category for the job.</span></span>  
  
 <span data-ttu-id="cc91e-111">**...**</span><span class="sxs-lookup"><span data-stu-id="cc91e-111">**...**</span></span>  
 <span data-ttu-id="cc91e-112">查看所选类别的作业。</span><span class="sxs-lookup"><span data-stu-id="cc91e-112">View the jobs in the selected category.</span></span>  
  
 <span data-ttu-id="cc91e-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="cc91e-113">**Description**</span></span>  
 <span data-ttu-id="cc91e-114">更改作业的说明。</span><span class="sxs-lookup"><span data-stu-id="cc91e-114">Change the description of the job.</span></span>  
  
 <span data-ttu-id="cc91e-115">**已启用**</span><span class="sxs-lookup"><span data-stu-id="cc91e-115">**Enabled**</span></span>  
 <span data-ttu-id="cc91e-116">启用作业。</span><span class="sxs-lookup"><span data-stu-id="cc91e-116">Enable the job.</span></span> <span data-ttu-id="cc91e-117">虽然可以使用 **sp_start_job** 存储过程启动作业，但是如果不启用作业，作业将不会响应计划或警报。</span><span class="sxs-lookup"><span data-stu-id="cc91e-117">When the job is not enabled, the job does not run in response to a schedule or an alert, although you can still start the job using the **sp_start_job** stored procedure.</span></span>  
  
 <span data-ttu-id="cc91e-118">**数据源**</span><span class="sxs-lookup"><span data-stu-id="cc91e-118">**Source**</span></span>  
 <span data-ttu-id="cc91e-119">显示作业的主服务器。</span><span class="sxs-lookup"><span data-stu-id="cc91e-119">Displays the master server for the job.</span></span> <span data-ttu-id="cc91e-120">仅在“作业属性”-“常规”\*\*\*\* 页上可用。</span><span class="sxs-lookup"><span data-stu-id="cc91e-120">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="cc91e-121">**创建时间**</span><span class="sxs-lookup"><span data-stu-id="cc91e-121">**Created**</span></span>  
 <span data-ttu-id="cc91e-122">显示作业的创建日期和时间。</span><span class="sxs-lookup"><span data-stu-id="cc91e-122">Displays the date and time that the job was created.</span></span> <span data-ttu-id="cc91e-123">仅在“作业属性”-“常规”\*\*\*\* 页上可用。</span><span class="sxs-lookup"><span data-stu-id="cc91e-123">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="cc91e-124">**上次修改时间**</span><span class="sxs-lookup"><span data-stu-id="cc91e-124">**Last modified**</span></span>  
 <span data-ttu-id="cc91e-125">显示上次修改作业的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="cc91e-125">Displays the date and time that the job was last modified.</span></span> <span data-ttu-id="cc91e-126">仅在“作业属性”-“常规”\*\*\*\* 页上可用。</span><span class="sxs-lookup"><span data-stu-id="cc91e-126">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="cc91e-127">**上次执行时间**</span><span class="sxs-lookup"><span data-stu-id="cc91e-127">**Last executed**</span></span>  
 <span data-ttu-id="cc91e-128">显示上次执行作业的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="cc91e-128">Displays the date and time that the job last started running.</span></span> <span data-ttu-id="cc91e-129">仅在“作业属性”-“常规”\*\*\*\* 页上可用。</span><span class="sxs-lookup"><span data-stu-id="cc91e-129">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="cc91e-130">**查看作业历史记录**</span><span class="sxs-lookup"><span data-stu-id="cc91e-130">**View Job History**</span></span>  
 <span data-ttu-id="cc91e-131">查看作业的历史记录。</span><span class="sxs-lookup"><span data-stu-id="cc91e-131">View the job history for the job.</span></span> <span data-ttu-id="cc91e-132">仅在“作业属性”-“常规”\*\*\*\* 页上可用。</span><span class="sxs-lookup"><span data-stu-id="cc91e-132">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc91e-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc91e-133">See Also</span></span>  
 <span data-ttu-id="cc91e-134">[执行作业](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="cc91e-134">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="cc91e-135">作业类别：管理作业类别</span><span class="sxs-lookup"><span data-stu-id="cc91e-135">Job Categories: Manage Job Categories</span></span>](job-categories-manage-job-categories.md)  
  
  
