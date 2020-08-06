---
title: 配置检查点以重新启动失败的包 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a85354377453e0b24692ab8c2b567cc8998b6b05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691833"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a><span data-ttu-id="e82ca-102">配置检查点以重新启动失败的包</span><span class="sxs-lookup"><span data-stu-id="e82ca-102">Configure Checkpoints for Restarting a Failed Package</span></span>
  <span data-ttu-id="e82ca-103">通过设置应用于检查点的属性，可以将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包配置为从失败点重新启动，而不是重新运行整个包。</span><span class="sxs-lookup"><span data-stu-id="e82ca-103">You configure [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to restart from a point of failure, instead of rerunning the entire package, by setting the properties that apply to checkpoints.</span></span>  
  
### <a name="to-configure-a-package-to-restart"></a><span data-ttu-id="e82ca-104">将包配置为重新启动</span><span class="sxs-lookup"><span data-stu-id="e82ca-104">To configure a package to restart</span></span>  
  
1.  <span data-ttu-id="e82ca-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要配置的包所在的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="e82ca-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure.</span></span>  
  
2.  <span data-ttu-id="e82ca-106">在“解决方案资源管理器”中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="e82ca-106">In **Solution Explorer**, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e82ca-107">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e82ca-107">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="e82ca-108">右键单击控制流设计图面背景中的任意位置，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e82ca-108">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e82ca-109">将 SaveCheckpoints 属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="e82ca-109">Set the SaveCheckpoints property to `True`.</span></span>  
  
6.  <span data-ttu-id="e82ca-110">在 CheckpointFileName 属性中键入检查点文件的名称。</span><span class="sxs-lookup"><span data-stu-id="e82ca-110">Type the name of the checkpoint file in the CheckpointFileName property.</span></span>  
  
7.  <span data-ttu-id="e82ca-111">将 CheckpointUsage 属性设置为以下两个值之一：</span><span class="sxs-lookup"><span data-stu-id="e82ca-111">Set the CheckpointUsage property to one of two values:</span></span>  
  
    -   <span data-ttu-id="e82ca-112">选择 `Always`，始终从检查点重新启动包。</span><span class="sxs-lookup"><span data-stu-id="e82ca-112">Select `Always` to always restart the package from the checkpoint.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="e82ca-113">如果检查点文件不可用，将出现错误。</span><span class="sxs-lookup"><span data-stu-id="e82ca-113">An error occurs if the checkpoint file is not available.</span></span>  
  
    -   <span data-ttu-id="e82ca-114">选择 `IfExists`，仅当检查文件可用时才重新启动包。</span><span class="sxs-lookup"><span data-stu-id="e82ca-114">Select `IfExists` to restart the package only if the checkpoint file is available.</span></span>  
  
8.  <span data-ttu-id="e82ca-115">配置包可以从中重新启动的任务和容器。</span><span class="sxs-lookup"><span data-stu-id="e82ca-115">Configure the tasks and containers from which the package can restart.</span></span>  
  
    -   <span data-ttu-id="e82ca-116">右键单击任务或容器，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e82ca-116">Right-click a task or container and click **Properties**.</span></span>  
  
    -   <span data-ttu-id="e82ca-117">将 `True` 每个所选任务和容器的 FailPackageOnFailure 属性设置为。</span><span class="sxs-lookup"><span data-stu-id="e82ca-117">Set the FailPackageOnFailure property to `True` for each selected task and container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e82ca-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e82ca-118">See Also</span></span>  
 [<span data-ttu-id="e82ca-119">通过使用检查点重新启动包</span><span class="sxs-lookup"><span data-stu-id="e82ca-119">Restart Packages by Using Checkpoints</span></span>](packages/restart-packages-by-using-checkpoints.md)  
  
  
