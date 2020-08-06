---
title: 设置或更改 DirectQuery 的首选连接方法 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
author: minewiskan
ms.author: owend
ms.openlocfilehash: 239c80ace0daa3498c8dafd8fea358ce540931d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691914"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a><span data-ttu-id="d094f-102">设置或更改 DirectQuery 的首选连接方法</span><span class="sxs-lookup"><span data-stu-id="d094f-102">Set or Change the Preferred Connection Method for DirectQuery</span></span>
  <span data-ttu-id="d094f-103">当您创建在 DirectQuery 模式下使用的模型时，必须首先对设计环境进行配置以便支持使用 DirectQuery。</span><span class="sxs-lookup"><span data-stu-id="d094f-103">When you create a model for use in DirectQuery mode, you must first configure the design environment to support use of DirectQuery.</span></span> <span data-ttu-id="d094f-104">若要执行此操作，请参阅[&#40;SSAS 表格&#41;启用 DirectQuery 设计模式](tabular-models/enable-directquery-mode-in-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="d094f-104">To do this, see [Enable DirectQuery Design Mode &#40;SSAS Tabular&#41;](tabular-models/enable-directquery-mode-in-ssdt.md).</span></span>  
  
 <span data-ttu-id="d094f-105">在您做好部署模型的准备后，必须设置其他一些属性以使用户能够使用某一 DirectQuery 模式访问您的模型：</span><span class="sxs-lookup"><span data-stu-id="d094f-105">When you are ready to deploy the model, you must set some additional properties to enable users to access your model using one of the DirectQuery modes:</span></span>  
  
-   <span data-ttu-id="d094f-106">您必须指示针对模型的查询是应该使用缓存数据还是关系数据源。</span><span class="sxs-lookup"><span data-stu-id="d094f-106">You must indicate whether queries against the model should use cached data or the relational data source.</span></span> <span data-ttu-id="d094f-107">您只能使用混合模式或 DirectQuery。</span><span class="sxs-lookup"><span data-stu-id="d094f-107">You can use a hybrid mode or DirectQuery only.</span></span>  
  
-   <span data-ttu-id="d094f-108">如果您正在使用分区，则必须指示哪一分区用作 DirectQuery 数据源。</span><span class="sxs-lookup"><span data-stu-id="d094f-108">If you are using partitions, you must indicate which partition to use as the DirectQuery data source.</span></span>  
  
-   <span data-ttu-id="d094f-109">您必须为将访问 SQL Server 数据源的用户设置模拟选项。</span><span class="sxs-lookup"><span data-stu-id="d094f-109">You must set impersonation options for users who will be accessing the SQL Server data source.</span></span>  
  
 <span data-ttu-id="d094f-110">此过程介绍如何在设计器中为 DirectQuery 模型设置首选连接方法。</span><span class="sxs-lookup"><span data-stu-id="d094f-110">This procedure describes how to set the preferred connection method for a DirectQuery model in the designer.</span></span> <span data-ttu-id="d094f-111">还介绍了在部署了模型后，如何在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中更改此属性。</span><span class="sxs-lookup"><span data-stu-id="d094f-111">It also describes how you can change this property in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] after the model has been deployed.</span></span>  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a><span data-ttu-id="d094f-112">为 DirectQuery 模型设置首选连接方法</span><span class="sxs-lookup"><span data-stu-id="d094f-112">To set the preferred connection method for a DirectQuery model</span></span>  
  
1.  <span data-ttu-id="d094f-113">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开用于 DirectQuery 模型的解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="d094f-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution file for the DirectQuery model.</span></span>  
  
2.  <span data-ttu-id="d094f-114">在 Visual Studio 中，从 **“项目”** 菜单中，选择 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="d094f-114">In Visual Studio, from the **Project** menu, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="d094f-115">在 **“属性”** 窗格中，将属性 **DirectQueryMode**更改为支持 DirectQuery 使用的以下值之一：</span><span class="sxs-lookup"><span data-stu-id="d094f-115">In the **Properties** pane, change the property, **DirectQueryMode**, to one of the values that support DirectQuery usage:</span></span>  
  
    -   <span data-ttu-id="d094f-116">**InMemory 以及 DirectQuery**：如果您使用此选项，则部署模型，但您必须首先处理缓存，然后才能对模型运行查询。</span><span class="sxs-lookup"><span data-stu-id="d094f-116">**InMemory with DirectQuery**: If you use this option, the model is deployed but you must process the cache before you can run queries against the model.</span></span>  
  
    -   <span data-ttu-id="d094f-117">**DirectQuery 以及 InMemory**：如果您使用此选项，则缓存将可供客户端使用（如果已处理缓存）。</span><span class="sxs-lookup"><span data-stu-id="d094f-117">**DirectQuery with InMemory**: If you use this option, the cache will be available for use by clients if it has already been processed.</span></span> <span data-ttu-id="d094f-118">如果您使用此设置部署模型并且未处理缓存，则某些客户端在尝试连接到模型时势必会收到错误消息。</span><span class="sxs-lookup"><span data-stu-id="d094f-118">If you deploy the model with this setting and do not process the cache, some clients must get an error on trying to connect to the model.</span></span>  
  
    -   <span data-ttu-id="d094f-119">**仅限 DirectQuery**：如果您使用此选项，则部署元数据，但模型对其中的数据没有影响。</span><span class="sxs-lookup"><span data-stu-id="d094f-119">**DirectQuery only**: If you use this option, the metadata is deployed but the model has no data in it.</span></span> <span data-ttu-id="d094f-120">尝试使用内存中模式进行连接的客户端将会收到错误消息，指示模型不存在或尚未处理。</span><span class="sxs-lookup"><span data-stu-id="d094f-120">Clients that attempt to connect using In-Memory mode will get an error, indicating that the model does not exist or has not been processed.</span></span>  
  
4.  <span data-ttu-id="d094f-121">如果存在错误，则在 Visual Studio 中，打开 **“错误列表”** ，并且解决将阻止模型部署在 DirectQuery 模式下的任何问题。</span><span class="sxs-lookup"><span data-stu-id="d094f-121">If there are errors, in Visual Studio, open the **Error List** and resolve any problems that would prevent the model from being deployed in DirectQuery mode.</span></span>  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a><span data-ttu-id="d094f-122">为 DirectQuery 模型验证或更改首选连接方法</span><span class="sxs-lookup"><span data-stu-id="d094f-122">To verify or change the preferred connection method for a DirectQuery model</span></span>  
  
1.  <span data-ttu-id="d094f-123">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，连接到部署了 DirectQuery 模型的实例。</span><span class="sxs-lookup"><span data-stu-id="d094f-123">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to the instance where you deployed the DirectQuery model.</span></span>  
  
2.  <span data-ttu-id="d094f-124">右键单击该模型数据库并选择 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="d094f-124">Right-click the model database, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="d094f-125">在 **“属性”** 窗格中，将属性 **DirectQueryMode**更改为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="d094f-125">In the **Properties** pane, change the property, **DirectQueryMode**, to one of these values:</span></span>  
  
    -   <span data-ttu-id="d094f-126">**仅限 DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="d094f-126">**DirectQuery Only**</span></span>  
  
    -   <span data-ttu-id="d094f-127">**InMemory 以及 DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="d094f-127">**InMemory with DirectQuery**</span></span>  
  
    -   <span data-ttu-id="d094f-128">**DirectQuery 以及 InMemory**</span><span class="sxs-lookup"><span data-stu-id="d094f-128">**DirectQuery with InMemory**</span></span>  
  
 <span data-ttu-id="d094f-129">请注意，这些属性与您在 Visual Studio 中部署前对项目设置的属性相同。</span><span class="sxs-lookup"><span data-stu-id="d094f-129">Note that these properties are the same as the properties that you set on the project before deployment in Visual Studio.</span></span> <span data-ttu-id="d094f-130">您可以随时更改针对 DirectQuery 模式的首选连接模式，只要您已将模型配置为支持使用 DirectQuery。</span><span class="sxs-lookup"><span data-stu-id="d094f-130">You can change the preferred connection mode for DirectQuery mode at any time, provided that you have configured the model to support DirectQuery usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d094f-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d094f-131">See Also</span></span>  
 <span data-ttu-id="d094f-132">[DirectQuery 模式 &#40;SSAS 表格&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d094f-132">[DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="d094f-133">&#40;SSAS 表格&#41;启用 DirectQuery 设计模式</span><span class="sxs-lookup"><span data-stu-id="d094f-133">Enable DirectQuery Design Mode &#40;SSAS Tabular&#41;</span></span>](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  
