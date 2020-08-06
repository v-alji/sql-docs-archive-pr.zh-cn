---
title: 如何管理 CDC 实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e387b9e1a75b7279a68d1c9c9b637f5473071013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683013"
---
# <a name="how-to-manage-a-cdc-instance"></a><span data-ttu-id="63cd6-102">How to Manage a CDC Instance</span><span class="sxs-lookup"><span data-stu-id="63cd6-102">How to Manage a CDC Instance</span></span>
  <span data-ttu-id="63cd6-103">本过程介绍如何使用 CDC 设计器控制台在运行时管理 CDC 实例操作。</span><span class="sxs-lookup"><span data-stu-id="63cd6-103">This procedure describes how to use the CDC Designer Console to manage CDC instance operations at runtime.</span></span>  
  
### <a name="to-manage-cdc-instance-operations"></a><span data-ttu-id="63cd6-104">管理 CDC 实例操作</span><span class="sxs-lookup"><span data-stu-id="63cd6-104">To manage CDC instance operations</span></span>  
  
1.  <span data-ttu-id="63cd6-105">从 **“开始”** 菜单上，选择 **“CDC 设计器控制台”** 。</span><span class="sxs-lookup"><span data-stu-id="63cd6-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="63cd6-106">在左侧的窗格中，展开 **“变更数据捕获”** ，然后展开包含您要查看的实例的服务。</span><span class="sxs-lookup"><span data-stu-id="63cd6-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance you want to view.</span></span>  
  
3.  <span data-ttu-id="63cd6-107">选择要使用的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="63cd6-107">Select the name of an instance you want to work with.</span></span>  
  
4.  <span data-ttu-id="63cd6-108">从 CDC 设计器控制台右侧的 **“操作”** 窗格中，单击要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="63cd6-108">From the **Actions** pane on the right side of the CDC Designer Console, click on the operation you want to carry out.</span></span>  
  
     <span data-ttu-id="63cd6-109">您还可以在左侧窗格中右键单击实例的名称，然后选择要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="63cd6-109">You can also right-click the name of the instance in the left pane and select the operation you want to carry out.</span></span>  
  
     <span data-ttu-id="63cd6-110">您可以执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="63cd6-110">You can carry out the following tasks:</span></span>  
  
    -   <span data-ttu-id="63cd6-111">**开始**：开始捕获更改。</span><span class="sxs-lookup"><span data-stu-id="63cd6-111">**Start**: To start capturing changes.</span></span>  
  
    -   <span data-ttu-id="63cd6-112">**停止**：停止捕获更改。</span><span class="sxs-lookup"><span data-stu-id="63cd6-112">**Stop**: To stop capturing changes</span></span>  
  
    -   <span data-ttu-id="63cd6-113">**重置**：单击“重置”  可将 CDC 实例重置为其初始（空）状态。</span><span class="sxs-lookup"><span data-stu-id="63cd6-113">**Reset**: Click **Reset** to reset the CDC instance to its initial (empty) state.</span></span> <span data-ttu-id="63cd6-114">此选项在 CDC 实例停止后可用。</span><span class="sxs-lookup"><span data-stu-id="63cd6-114">This option is available when the CDC instance is stopped.</span></span> <span data-ttu-id="63cd6-115">更改表中的所有更改以及 CDC 实例内部状态将被删除。</span><span class="sxs-lookup"><span data-stu-id="63cd6-115">All changes in the change tables and the CDC instance internal state are deleted.</span></span> <span data-ttu-id="63cd6-116">当 CDC 实例在以后启动时，变更捕获将从该时间点开始，并且仅包含在 CDC 实例启动后开始的事务。</span><span class="sxs-lookup"><span data-stu-id="63cd6-116">When the CDC instance is started later on, change capture will start from that point in time and only includes transactions that started after the CDC instance started.</span></span>  
  
    -   <span data-ttu-id="63cd6-117">**删除**：删除 CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="63cd6-117">**Delete**: To delete the CDC instance.</span></span>  
  
    -   <span data-ttu-id="63cd6-118">**Oracle 日志记录脚本**：单击“Oracle 日志记录脚本”  将显示具有 Oracle 补充日志记录脚本的“Oracle 日志记录脚本”对话框。</span><span class="sxs-lookup"><span data-stu-id="63cd6-118">**Oracle Logging Script**: Click **Oracle Logging Script** to display the Oracle Logging script dialog box with the Oracle supplemental-logging script.</span></span> <span data-ttu-id="63cd6-119">有关可以在此对话框中执行的操作的信息，请参阅 [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md)。</span><span class="sxs-lookup"><span data-stu-id="63cd6-119">For information on what you can do in this dialog box, see [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).</span></span>  
  
         <span data-ttu-id="63cd6-120">**注意**：在您运行补充日志记录脚本时，“用于运行脚本的 Oracle 凭据”对话框将打开，您可以在其中提供有效的 Oracle 用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="63cd6-120">**Note**: When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="63cd6-121">有关如何提供适当的 Oracle 凭据的信息，请参阅 [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)。</span><span class="sxs-lookup"><span data-stu-id="63cd6-121">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
    -   <span data-ttu-id="63cd6-122">**CDC 实例部署**：为 CDC 实例生成部署脚本。</span><span class="sxs-lookup"><span data-stu-id="63cd6-122">**CDC Instance Deployment**: To generate a deployment script for the CDC Instance.</span></span> <span data-ttu-id="63cd6-123">有关此对话框的信息，请参阅 [CDC Instance Deployment Script](cdc-instance-deployment-script.md)。</span><span class="sxs-lookup"><span data-stu-id="63cd6-123">For information about this dialog box, see [CDC Instance Deployment Script](cdc-instance-deployment-script.md).</span></span>  
  
     <span data-ttu-id="63cd6-124">有关这些任务的详细信息，请参阅 [Manage a CDC Instance](manage-a-cdc-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="63cd6-124">For more information about these tasks, see [Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
 <span data-ttu-id="63cd6-125">您还可以选择 **“属性”** 来编辑 CDC 实例的配置属性。</span><span class="sxs-lookup"><span data-stu-id="63cd6-125">You can also select **Properties** to edit the CDC instance configuration properties.</span></span> <span data-ttu-id="63cd6-126">有关编辑 CDC 实例属性的详细信息，请参阅 [Edit Instance Properties](edit-instance-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="63cd6-126">For more information about editing the CDC instance properties, see [Edit Instance Properties](edit-instance-properties.md).</span></span>  
  
  
