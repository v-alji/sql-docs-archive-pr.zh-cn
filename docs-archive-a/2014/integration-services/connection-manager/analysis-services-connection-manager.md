---
title: Analysis Services 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5da84acd131b75ef9ea174986836265934fb44b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586928"
---
# <a name="analysis-services-connection-manager"></a><span data-ttu-id="54dd6-102">Analysis Services 连接管理器</span><span class="sxs-lookup"><span data-stu-id="54dd6-102">Analysis Services Connection Manager</span></span>
  <span data-ttu-id="54dd6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器使包能够连接到运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库的服务器，或连接到用于访问多维数据集和维度数据的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="54dd6-103">An [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager enables a package to connect to a server that runs an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that provides access to cube and dimension data.</span></span> <span data-ttu-id="54dd6-104">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中开发包时，仅可连接到 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]项目。</span><span class="sxs-lookup"><span data-stu-id="54dd6-104">You can only connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project while developing packages in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="54dd6-105">在运行时，包会连接到您已部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目的服务器和数据库。</span><span class="sxs-lookup"><span data-stu-id="54dd6-105">At run time, packages connect to the server and the database to which you deployed the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
 <span data-ttu-id="54dd6-106">任务（如 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 执行 DDL 任务和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 处理任务）和目标（如数据挖掘模型定型目标）都使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="54dd6-106">Both tasks, such as the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task, and destinations, such as the Data Mining Model Training destination, use an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager.</span></span>  
  
 <span data-ttu-id="54dd6-107">有关 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库的详细信息，请参阅[多维模型数据库 (SSAS)](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-databases-ssas)。</span><span class="sxs-lookup"><span data-stu-id="54dd6-107">For more information about [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, see [Multidimensional Model Databases &#40;SSAS&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-databases-ssas).</span></span>  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a><span data-ttu-id="54dd6-108">Analysis Services 连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="54dd6-108">Configuration of the Analysis Services Connection Manager</span></span>  
 <span data-ttu-id="54dd6-109">将 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器添加到包时，将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 创建一个连接管理器，该管理器 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在运行时作为连接进行解析，设置连接管理器属性，并将该连接管理器添加到 `Connections` 包上的集合。</span><span class="sxs-lookup"><span data-stu-id="54dd6-109">When you add an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="54dd6-110">该连接管理器的 `ConnectionManagerType` 属性设置为 `MSOLAP100`。</span><span class="sxs-lookup"><span data-stu-id="54dd6-110">The `ConnectionManagerType` property of the connection manager is set to `MSOLAP100`.</span></span>  
  
 <span data-ttu-id="54dd6-111">可以通过下列方式配置 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="54dd6-111">You can configure the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="54dd6-112">提供配置为符合 Microsoft OLE Provider for Analysis Services 访问接口要求的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="54dd6-112">Provide a connection string configured to meet the requirements of the Microsoft OLE Provider for Analysis Services provider.</span></span>  
  
-   <span data-ttu-id="54dd6-113">指定要连接到的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的实例或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="54dd6-113">Specify the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to connect to.</span></span>  
  
-   <span data-ttu-id="54dd6-114">如果要连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的实例，则应指定身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="54dd6-114">If you are connecting to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], specify the authentication mode.</span></span>  
  
-   <span data-ttu-id="54dd6-115">指示是否在运行时保留从连接管理器中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="54dd6-115">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="54dd6-116">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="54dd6-116">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="54dd6-117">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="54dd6-117">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="54dd6-118">“添加 Analysis Services 连接管理器”对话框 UI 参考</span><span class="sxs-lookup"><span data-stu-id="54dd6-118">Add Analysis Services Connection Manager Dialog Box UI Reference</span></span>](add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 <span data-ttu-id="54dd6-119">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="54dd6-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
