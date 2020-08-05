---
title: 第2课：按计划评估最佳实践策略 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 37ffad63-d6db-4609-8deb-786200659554
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a454e38ec2f07bf9867183a3894ac4ea001a942e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579917"
---
# <a name="lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis"></a><span data-ttu-id="3dcf6-102">第 2 课：定期评估最佳做法策略</span><span class="sxs-lookup"><span data-stu-id="3dcf6-102">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>
  <span data-ttu-id="3dcf6-103">您可以对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一个或多个实例配置最佳实践策略的定期评估。</span><span class="sxs-lookup"><span data-stu-id="3dcf6-103">You can configure scheduled evaluations of best practices policies on one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3dcf6-104">若要配置定义运行的最佳实践策略，您必须将这些策略导入到目标实例中。</span><span class="sxs-lookup"><span data-stu-id="3dcf6-104">To configure best practices policies to run on a scheduled basis, you must import the policies into the target instance.</span></span>  
  
 <span data-ttu-id="3dcf6-105">若要将计划的策略部署到多个服务器中，您可以将这些策略导入到一个实例，为每个策略配置计划，将计划的策略导出到某一文件夹，然后通过已注册的服务器将计划的策略部署到目标实例。</span><span class="sxs-lookup"><span data-stu-id="3dcf6-105">To deploy scheduled policies to multiple servers, you can import the policies to one instance, configure the schedules for each policy, export the scheduled policies to a folder, and then deploy the scheduled policies to target instances through Registered Servers.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3dcf6-106">目标实例必须运行 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 或者更高版本。</span><span class="sxs-lookup"><span data-stu-id="3dcf6-106">The target instances must be running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span> <span data-ttu-id="3dcf6-107">自动过程要求在实例上本地存储策略，但早于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 版本不支持此功能。</span><span class="sxs-lookup"><span data-stu-id="3dcf6-107">Automation requires the policies to be stored locally on the instance, which is not supported by versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="3dcf6-108">在本课程中，您将执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3dcf6-108">In this lesson, you will do the following:</span></span>  
  
-   <span data-ttu-id="3dcf6-109">将最佳实践策略导入到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的实例中。</span><span class="sxs-lookup"><span data-stu-id="3dcf6-109">Import the best practices policies into an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="3dcf6-110">配置要定期运行的策略。</span><span class="sxs-lookup"><span data-stu-id="3dcf6-110">Configure the policies to run on a schedule.</span></span>  
  
-   <span data-ttu-id="3dcf6-111">通过已注册的服务器将计划的最佳实践策略部署到多个实例。</span><span class="sxs-lookup"><span data-stu-id="3dcf6-111">Deploy the scheduled best practices policies to multiple instances through Registered Servers.</span></span>  
  
 <span data-ttu-id="3dcf6-112">本课程包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="3dcf6-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="3dcf6-113">将策略导入到单个实例</span><span class="sxs-lookup"><span data-stu-id="3dcf6-113">Import the Policies to a Single Instance</span></span>](../../2014/tutorials/import-the-policies-to-a-single-instance.md)  
  
-   [<span data-ttu-id="3dcf6-114">计划策略</span><span class="sxs-lookup"><span data-stu-id="3dcf6-114">Schedule the Policies</span></span>](../../2014/tutorials/schedule-the-policies.md)  
  
-   [<span data-ttu-id="3dcf6-115">将计划的策略部署到多个实例</span><span class="sxs-lookup"><span data-stu-id="3dcf6-115">Deploy Scheduled Policies to Multiple Instances</span></span>](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
## <a name="see-also"></a><span data-ttu-id="3dcf6-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3dcf6-116">See Also</span></span>  
 [<span data-ttu-id="3dcf6-117">使用中央管理服务器管理多台服务器</span><span class="sxs-lookup"><span data-stu-id="3dcf6-117">Administer Multiple Servers Using Central Management Servers</span></span>](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
