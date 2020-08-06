---
title: 教程：使用基于策略的管理来评估最佳实践 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- best practices analyzer
- Policy-Based Management, best practices policies
- Best Practices [Database Engine]
- Policy-Based Management, evaluating policies
- BPA
- tutorials [Policy-Based Management]
- Policy-Based Management, tutorials
ms.assetid: c7867f9b-7acc-4fae-bde1-63808c403ebc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 42e6b505c71abecce7b56b5cb2544b4e9f4e8f71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690243"
---
# <a name="tutorial-evaluating-best-practices-by-using-policy-based-management"></a><span data-ttu-id="feca5-102">教程：使用基于策略的管理来评估最佳做法</span><span class="sxs-lookup"><span data-stu-id="feca5-102">Tutorial: Evaluating Best Practices by Using Policy-Based Management</span></span>
  <span data-ttu-id="feca5-103">欢迎使用“使用基于策略的管理来评估最佳实践”教程。</span><span class="sxs-lookup"><span data-stu-id="feca5-103">Welcome to the Evaluating Best Practices by Using Policy-Based Management tutorial.</span></span> <span data-ttu-id="feca5-104">本教程适用于熟悉 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 但不熟悉基于策略的管理的用户。</span><span class="sxs-lookup"><span data-stu-id="feca5-104">This tutorial is intended for users who are familiar with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but new to Policy-Based Management.</span></span> <span data-ttu-id="feca5-105">基于策略的管理是一个系统，用于定义可用于强制执行网站管理标准的策略。</span><span class="sxs-lookup"><span data-stu-id="feca5-105">Policy-Based Management is a system for defining policies that can be used enforce site administration standards.</span></span> <span data-ttu-id="feca5-106">基于策略的管理包括一组最佳实践策略，这些策略可用于分析某一 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，以便确定该实例是否满足最佳实践指导原则和建议。</span><span class="sxs-lookup"><span data-stu-id="feca5-106">Policy-Based Management includes a set of best practices policies that you can use to analyze an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to determine whether the instance meets best practices guidelines and recommendations.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="feca5-107">学习内容</span><span class="sxs-lookup"><span data-stu-id="feca5-107">What You Will Learn</span></span>  
 <span data-ttu-id="feca5-108">在本教程中，您将学习如何按需（或者“即席”）或者定期为 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 评估最佳实践策略。</span><span class="sxs-lookup"><span data-stu-id="feca5-108">In this tutorial, you will learn how to evaluate best practices policies for the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on an on-demand (or "ad hoc") basis, or on a scheduled basis.</span></span>  
  
 <span data-ttu-id="feca5-109">本教程分为两课：</span><span class="sxs-lookup"><span data-stu-id="feca5-109">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="feca5-110">第 1 课：按需评估最佳做法策略</span><span class="sxs-lookup"><span data-stu-id="feca5-110">Lesson 1: Evaluate Best Practices on an On-Demand Basis</span></span>](../../2014/tutorials/lesson-1-evaluate-best-practices-on-an-on-demand-basis.md)  
 <span data-ttu-id="feca5-111">在本课程中，您可以对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一个或多个实例执行策略的按需评估。</span><span class="sxs-lookup"><span data-stu-id="feca5-111">In this lesson, you perform an on-demand evaluation of the policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="feca5-112">第 2 课：定期评估最佳做法策略</span><span class="sxs-lookup"><span data-stu-id="feca5-112">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
 <span data-ttu-id="feca5-113">在本课程中，您配置要定期运行的最佳实践策略。</span><span class="sxs-lookup"><span data-stu-id="feca5-113">In this lesson, you configure best practices policies to run on a scheduled basis.</span></span> <span data-ttu-id="feca5-114">本课程演示如何对单个实例配置定期策略，以及如何将定期策略从中央位置部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的多个实例。</span><span class="sxs-lookup"><span data-stu-id="feca5-114">The lesson shows how to configure scheduled policies on a single instance, and how to deploy scheduled policies from a central location to multiple instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feca5-115">要求</span><span class="sxs-lookup"><span data-stu-id="feca5-115">Requirements</span></span>  
 <span data-ttu-id="feca5-116">本课程要求您了解数据库和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的基础知识。</span><span class="sxs-lookup"><span data-stu-id="feca5-116">This lesson requires basic database knowledge and a basic understanding of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="feca5-117">若要使用本教程，服务器中必须已安装 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="feca5-117">To use this tutorial, the server must have [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] installed.</span></span>  
  
## <a name="start-the-tutorial"></a><span data-ttu-id="feca5-118">开始教程</span><span class="sxs-lookup"><span data-stu-id="feca5-118">Start the Tutorial</span></span>  
 [<span data-ttu-id="feca5-119">第 1 课：按需评估最佳做法策略</span><span class="sxs-lookup"><span data-stu-id="feca5-119">Lesson 1: Evaluate Best Practices on an On-Demand Basis</span></span>](../../2014/tutorials/lesson-1-evaluate-best-practices-on-an-on-demand-basis.md)  
  
## <a name="see-also"></a><span data-ttu-id="feca5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="feca5-120">See Also</span></span>  
 [<span data-ttu-id="feca5-121">使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="feca5-121">Administer Servers by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
