---
title: 教程：使用基于策略的管理来管理服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Policy-Based Management]
- Policy-Based Management, tutorials
ms.assetid: 7de96e7b-9fb8-4cc8-8d85-61345d68a1e8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9b707a5ecd362c6b3b54e853f89d79e25a9e1428
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580188"
---
# <a name="tutorial-administering-servers-by-using-policy-based-management"></a><span data-ttu-id="0b510-102">教程：使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="0b510-102">Tutorial: Administering Servers by Using Policy-Based Management</span></span>
  <span data-ttu-id="0b510-103">欢迎使用“使用基于策略的管理策略来管理服务器”教程。</span><span class="sxs-lookup"><span data-stu-id="0b510-103">Welcome to the Administering Servers by Using Policy-Based Management Policies tutorial.</span></span> <span data-ttu-id="0b510-104">本教程适用于熟悉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 但不熟悉基于策略的管理的用户。</span><span class="sxs-lookup"><span data-stu-id="0b510-104">This tutorial is intended for users who are familiar with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but new to the Policy-Based Management.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="0b510-105">学习内容</span><span class="sxs-lookup"><span data-stu-id="0b510-105">What You Will Learn</span></span>  
 <span data-ttu-id="0b510-106">本教程创建一个用于管理服务器的策略以及一个应用于单个数据库的策略。</span><span class="sxs-lookup"><span data-stu-id="0b510-106">This tutorial creates a policy to administer your server and a policy that applies to a single database.</span></span> <span data-ttu-id="0b510-107">根据需要，运行一个策略以测试是否符合要求。</span><span class="sxs-lookup"><span data-stu-id="0b510-107">One policy is run on demand to test for compliance.</span></span> <span data-ttu-id="0b510-108">另一个策略强制要求以后符合策略。</span><span class="sxs-lookup"><span data-stu-id="0b510-108">The other policy enforces future compliance.</span></span>  
  
 <span data-ttu-id="0b510-109">本教程分为两课：</span><span class="sxs-lookup"><span data-stu-id="0b510-109">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="0b510-110">第 1 课：创建并应用 Off By Default 策略</span><span class="sxs-lookup"><span data-stu-id="0b510-110">Lesson 1: Create and Apply an Off By Default Policy</span></span>](lesson-1-create-and-apply-an-off-by-default-policy.md)  
 <span data-ttu-id="0b510-111">本课创建一个策略，用于指定在服务器上不启用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="0b510-111">This lesson creates a policy that specifies that Database Mail is not enabled on the server.</span></span> <span data-ttu-id="0b510-112">然后，它检查服务器是否符合该策略，并配置服务器以禁用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="0b510-112">Then, it checks to see whether your server complies with the policy, and configures the server by disabling Database Mail.</span></span>  
  
 [<span data-ttu-id="0b510-113">第 2 课：创建并应用命名标准策略</span><span class="sxs-lookup"><span data-stu-id="0b510-113">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
 <span data-ttu-id="0b510-114">该课程创建一个策略，用于定义并强制执行表命名标准。</span><span class="sxs-lookup"><span data-stu-id="0b510-114">This lesson creates a policy that defines and enforces a naming standard for tables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b510-115">要求</span><span class="sxs-lookup"><span data-stu-id="0b510-115">Requirements</span></span>  
 <span data-ttu-id="0b510-116">本课程要求您了解数据库和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的基础知识。</span><span class="sxs-lookup"><span data-stu-id="0b510-116">This lesson requires basic database knowledge and a basic understanding of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="0b510-117">若要使用本教程，您的系统必须安装了 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0b510-117">To use this tutorial, your system must have [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] installed.</span></span>  
  
## <a name="start-the-tutorial"></a><span data-ttu-id="0b510-118">开始教程</span><span class="sxs-lookup"><span data-stu-id="0b510-118">Start the Tutorial</span></span>  
 [<span data-ttu-id="0b510-119">第 1 课：创建并应用 Off By Default 策略</span><span class="sxs-lookup"><span data-stu-id="0b510-119">Lesson 1: Create and Apply an Off By Default Policy</span></span>](lesson-1-create-and-apply-an-off-by-default-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="0b510-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b510-120">See Also</span></span>  
 [<span data-ttu-id="0b510-121">使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="0b510-121">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
