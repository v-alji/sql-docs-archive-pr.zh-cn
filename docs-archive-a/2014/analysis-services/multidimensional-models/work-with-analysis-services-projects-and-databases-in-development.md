---
title: 在开发阶段使用 Analysis Services 项目和数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762ea6f33a94f65e7dd6895cd038d4a52d40d43e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587048"
---
# <a name="working-with-analysis-services-projects-and-databases-during-the-development-phase"></a><span data-ttu-id="8cdae-102">在开发阶段使用 Analysis Services 项目和数据库</span><span class="sxs-lookup"><span data-stu-id="8cdae-102">Working with Analysis Services Projects and Databases During the Development Phase</span></span>
  <span data-ttu-id="8cdae-103">可以在项目模式或联机模式下使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 开发 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="8cdae-103">You can develop an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in either project mode or online mode.</span></span>  
  
## <a name="single-developer"></a><span data-ttu-id="8cdae-104">一个开发人员</span><span class="sxs-lookup"><span data-stu-id="8cdae-104">Single Developer</span></span>  
 <span data-ttu-id="8cdae-105">如果只有一个开发人员开发整个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库及其所有构成对象，则在商业智能解决方案生命周期中，开发人员可以随时在项目模式或联机模式下使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8cdae-105">When only a single developer is developing the entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and all of its constituent objects, the developer can use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in either project mode or online mode at any time during the lifecycle of the business intelligence solution.</span></span> <span data-ttu-id="8cdae-106">在一个开发人员进行开发的情况下，模式的选择不是特别重要。</span><span class="sxs-lookup"><span data-stu-id="8cdae-106">In the case of a single developer, the choice of modes is not particularly critical.</span></span> <span data-ttu-id="8cdae-107">维护与源代码管理系统集成的离线项目文件有许多优点，例如存档和回滚。</span><span class="sxs-lookup"><span data-stu-id="8cdae-107">The maintenance of an offline project file integrated with a source control system has many benefits, such as archiving and rollback.</span></span> <span data-ttu-id="8cdae-108">但是，对于一个开发人员，就不存在与其他开发人员交流更改的问题。</span><span class="sxs-lookup"><span data-stu-id="8cdae-108">However, with a single developer you will not have the problem of communicating changes with another developer.</span></span>  
  
## <a name="multiple-developers"></a><span data-ttu-id="8cdae-109">多个开发人员</span><span class="sxs-lookup"><span data-stu-id="8cdae-109">Multiple Developers</span></span>  
 <span data-ttu-id="8cdae-110">多个开发人员使用商业智能解决方案时，在多数情况下（如果不是全部情况的话），要是开发人员不在项目模式下使用源代码管理进行工作，则将出现问题。</span><span class="sxs-lookup"><span data-stu-id="8cdae-110">When multiple developers are working on a business intelligence solution, problems will arise if the developers do not work in project mode with source control under most, if not all circumstances.</span></span> <span data-ttu-id="8cdae-111">源代码管理可确保两个开发人员不会同时对同一对象进行更改。</span><span class="sxs-lookup"><span data-stu-id="8cdae-111">Source control ensures that two developers are not making changes to the same object at the same time.</span></span>  
  
 <span data-ttu-id="8cdae-112">例如，假设一个开发人员在项目模式下工作，并且对所选对象进行更改。</span><span class="sxs-lookup"><span data-stu-id="8cdae-112">For example, suppose a developer is working in project mode and making changes to selected objects.</span></span> <span data-ttu-id="8cdae-113">在该开发人员进行这些更改时，假设另一个开发人员在联机模式下对已部署的数据库进行更改。</span><span class="sxs-lookup"><span data-stu-id="8cdae-113">While the developer is making these changes, suppose that another developer makes a change to the deployed database in online mode.</span></span> <span data-ttu-id="8cdae-114">当第一个开发人员尝试部署他或她的已修改 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目时，将出现问题。</span><span class="sxs-lookup"><span data-stu-id="8cdae-114">A problem will arise when the first developer attempts to deploy his or her modified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="8cdae-115">也就是说， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 将检测到，在已部署的数据库中这些对象已被更改，并提示此开发人员覆盖整个数据库，从而覆盖第二个开发人员所做的更改。</span><span class="sxs-lookup"><span data-stu-id="8cdae-115">Namely, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] will detect that objects have changed within the deployed database and prompt the developer to overwrite the entire database, overwriting the changes of the second developer.</span></span> <span data-ttu-id="8cdae-116">因为 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 无法解决 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目对象之间即将覆盖的更改，所以，第一个开发人员唯一的实际选择就是必须放弃他或她的所有更改，并基于当前版本的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库重新开始新的项目。</span><span class="sxs-lookup"><span data-stu-id="8cdae-116">Since [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] has no means of resolving the changes between the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database instance and the objects in the project about to be overwritten, the only real choice the first developer has is to discard all of his or her changes and starting anew from a new project based on the current version of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
  
