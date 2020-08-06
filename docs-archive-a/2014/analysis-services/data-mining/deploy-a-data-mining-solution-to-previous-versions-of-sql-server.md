---
title: 将数据挖掘解决方案部署到以前版本的 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [Analysis Services]
- holdout [data mining]
- deploy [Analysis Services]
- time series [Analysis Services]
- deploying [Analysis Services - data mining]
- synchronization [Analysis Services]
- deployment [Analysis Services]
ms.assetid: 2715c245-f206-43af-8bf5-e6bd2585477a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f09a37c078cf58f24db9a08e3ddcb68cb2638717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589965"
---
# <a name="deploy-a-data-mining-solution-to-previous-versions-of-sql-server"></a><span data-ttu-id="e57a6-102">将数据挖掘解决方案部署到以前版本的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="e57a6-102">Deploy a Data Mining Solution to Previous Versions of SQL Server</span></span>
  <span data-ttu-id="e57a6-103">尝试将在 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 实例中创建的数据挖掘模型或数据挖掘结构部署到使用 SQL Server 2005 Analysis Services 的数据库，或者将在 SQL Server 2005 中创建的模型部署到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]实例中时，有可能会遇到兼容性问题。本节将讲述这些已知的兼容性问题。</span><span class="sxs-lookup"><span data-stu-id="e57a6-103">This section describes known compatibility issues that may arise when you attempt to deploy a data mining model or data mining structure that was created in an instance of [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to a database that uses SQL Server 2005 Analysis Services, or when you deploy models created in SQL Server 2005 to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="e57a6-104">不支持部署到 SQL Server 2000 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="e57a6-104">Deployment to an instance of SQL Server 2000 Analysis Services is not supported.</span></span>  
  
 [<span data-ttu-id="e57a6-105">部署时序模型</span><span class="sxs-lookup"><span data-stu-id="e57a6-105">Deploying Time Series Models</span></span>](#bkmk_TimeSeries)  
  
 [<span data-ttu-id="e57a6-106">部署具有维持的模型</span><span class="sxs-lookup"><span data-stu-id="e57a6-106">Deploying Models with Holdout</span></span>](#bkmk_Holdout)  
  
 [<span data-ttu-id="e57a6-107">部署具有筛选器的模型</span><span class="sxs-lookup"><span data-stu-id="e57a6-107">Deploying Models with Filters</span></span>](#bkmk_Filter)  
  
 [<span data-ttu-id="e57a6-108">从数据库备份还原</span><span class="sxs-lookup"><span data-stu-id="e57a6-108">Restoring from Database Backups</span></span>](#bkmk_Backup)  
  
 [<span data-ttu-id="e57a6-109">使用数据库同步</span><span class="sxs-lookup"><span data-stu-id="e57a6-109">Using Database Synchronization</span></span>](#bkmk_Synch)  
  
##  <a name="deploying-times-series-models"></a><a name="bkmk_TimeSeries"></a><span data-ttu-id="e57a6-110">部署时序模型</span><span class="sxs-lookup"><span data-stu-id="e57a6-110">Deploying Times Series Models</span></span>  
 <span data-ttu-id="e57a6-111">SQL Server 2008 中新增了一个辅助补充算法 ARIMA，从而增强了原有的 Microsoft 时序算法。</span><span class="sxs-lookup"><span data-stu-id="e57a6-111">The Microsoft Time Series algorithm was enhanced in SQL Server 2008 by the addition of a second, complementary algorithm, ARIMA.</span></span> <span data-ttu-id="e57a6-112">有关时序算法方面的更改的详细信息，请参阅 [Microsoft 时序算法](microsoft-time-series-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="e57a6-112">For more information about the changes in the time series algorithm, see [Microsoft Time Series Algorithm](microsoft-time-series-algorithm.md).</span></span>  
  
 <span data-ttu-id="e57a6-113">因此，使用新 ARIMA 算法的时序挖掘模型部署到 SQL Server 2005 Analysis Services 实例时的行为可能与以往不同。</span><span class="sxs-lookup"><span data-stu-id="e57a6-113">Therefore, time series mining models that use the new ARIMA algorithm may behave differently when deployed to an instance of SQL Server 2005 Analysis Services.</span></span>  
  
 <span data-ttu-id="e57a6-114">如果在预测过程中已显式设置 PREDICTION_SMOOTHING 参数来控制 ARTXP 和 ARIMA 模型的混合，则在将该模型部署到 SQL Server 2005 实例时，Analysis Services 将引发错误，指出此参数无效。</span><span class="sxs-lookup"><span data-stu-id="e57a6-114">If you have explicitly set the parameter PREDICTION_SMOOTHING to control the mixture of ARTXP and ARIMA models in prediction, when you deploy this model to an instance of SQL Server 2005, Analysis Services will raise an error stating that the parameter is not valid.</span></span> <span data-ttu-id="e57a6-115">若要避免产生此错误，必须删除 PREDICTION_SMOOTHING 参数并将以上两个模型转换为纯 ARTXP 模型。</span><span class="sxs-lookup"><span data-stu-id="e57a6-115">To prevent this error, you must delete the PREDICTION_SMOOTHING parameter and convert the models to a pure ARTXP model.</span></span>  
  
 <span data-ttu-id="e57a6-116">反之，如果将使用 SQL Server 2005 Analysis Services 创建的时序模型部署到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]实例中，则使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]打开该挖掘模型时，定义文件将首先转换为新格式，并且默认情况下有两个新参数添加到所有时序模型中。</span><span class="sxs-lookup"><span data-stu-id="e57a6-116">Conversely, if you deploy a time series model that was created using SQL Server 2005 Analysis Services to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], when you open the mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the definition files are first converted to the new format, and two new parameters are added by default to all time series models.</span></span> <span data-ttu-id="e57a6-117">参数 FORECAST_METHOD 是使用默认值 MIXED 添加的，而参数 PREDICTION_SMOOTHING 是使用默认值 0.5 添加的。</span><span class="sxs-lookup"><span data-stu-id="e57a6-117">The parameter FORECAST_METHOD is added with the default value of MIXED, and the parameter PREDICTION_SMOOTHING is added with the default value of 0.5.</span></span> <span data-ttu-id="e57a6-118">不过，如果不重新处理该模型，该模型仍将只使用 ARTXP 算法进行预测。</span><span class="sxs-lookup"><span data-stu-id="e57a6-118">However, the model will continue to use only ARTXP for forecasting until you reprocess the model.</span></span> <span data-ttu-id="e57a6-119">一旦重新处理该模型，预测就改为同时使用 ARIMA 和 ARTXP。</span><span class="sxs-lookup"><span data-stu-id="e57a6-119">As soon as you reprocess the model, prediction changes to use both ARIMA and ARTXP.</span></span>  
  
 <span data-ttu-id="e57a6-120">因此，如果您不希望更改此模型，则应当只浏览该模型，绝对不可处理该模型。</span><span class="sxs-lookup"><span data-stu-id="e57a6-120">Therefore, if you wish to avoid changing the model, you should only browse the model and never process it.</span></span> <span data-ttu-id="e57a6-121">或者，您可以显式设置 FORECAST_METHOD 或 PREDICTION_SMOOTHING 参数。</span><span class="sxs-lookup"><span data-stu-id="e57a6-121">Alternatively, you could explicitly set the FORECAST_METHOD or PREDICTION_SMOOTHING parameters.</span></span>  
  
 <span data-ttu-id="e57a6-122">有关配置已混合模型的详细信息，请参阅 [Microsoft 时序算法技术参考](microsoft-time-series-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="e57a6-122">For detailed information about configuring mixed models, see [Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="e57a6-123">如果用于该模型数据源的访问接口是 SQL Client Data Provider 10，则还必须修改数据源定义以指定 SQL Server Native Client 的以前版本。</span><span class="sxs-lookup"><span data-stu-id="e57a6-123">If the provider that is used for the model's data source is SQL Client Data Provider 10, you must also modify the data source definition to specify the previous version of the SQL Server Native Client.</span></span> <span data-ttu-id="e57a6-124">否则， [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 将生成一个错误，指出提供程序未注册。</span><span class="sxs-lookup"><span data-stu-id="e57a6-124">Otherwise, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] generates an error stating that the provider is not registered.</span></span>  
  
##  <a name="deploying-models-with-holdout"></a><a name="bkmk_Holdout"></a><span data-ttu-id="e57a6-125">部署具有维持的模型</span><span class="sxs-lookup"><span data-stu-id="e57a6-125">Deploying Models with Holdout</span></span>  
 <span data-ttu-id="e57a6-126">如果使用 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 创建了包含一个维持部分（用于测试数据挖掘模型）的挖掘结构，则该挖掘结构可以部署到 SQL Server 2005 实例，但此维持部分的信息将丢失。</span><span class="sxs-lookup"><span data-stu-id="e57a6-126">If you use [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to create a mining structure that contains a holdout partition used for testing data mining models, the mining structure can be deployed to an instance of SQL Server 2005, but the partition information will be lost.</span></span>  
  
 <span data-ttu-id="e57a6-127">使用 SQL Server 2005 Analysis Services 打开该挖掘结构时， [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 将引发错误，然后重新生成该结构以删除维持部分。</span><span class="sxs-lookup"><span data-stu-id="e57a6-127">When you open the mining structure in SQL Server 2005 Analysis Services, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] raises an error, and then regenerates the structure to remove the holdout partition.</span></span>  
  
 <span data-ttu-id="e57a6-128">重新生成结构后，维持分区的大小在属性窗口中将不再可用;但是， \<ddl100_100:HoldoutMaxPercent> \</ddl100_100:HoldoutMaxPercent> ASSL 脚本文件中仍可能存在值 30) 。</span><span class="sxs-lookup"><span data-stu-id="e57a6-128">After the structure has been rebuilt, the size of the holdout partition is no longer available in the Properties window; however, the value \<ddl100_100:HoldoutMaxPercent>30\</ddl100_100:HoldoutMaxPercent>) may still be present in the ASSL script file.</span></span>  
  
##  <a name="deploying-models-with-filters"></a><a name="bkmk_Filter"></a><span data-ttu-id="e57a6-129">部署具有筛选器的模型</span><span class="sxs-lookup"><span data-stu-id="e57a6-129">Deploying Models with Filters</span></span>  
 <span data-ttu-id="e57a6-130">如果使用 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 将某个筛选器应用于挖掘模型，则该模型可以部署到 SQL Server 2005 实例，但不会应用该筛选器。</span><span class="sxs-lookup"><span data-stu-id="e57a6-130">If you use [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to apply a filter to a mining model, the model can be deployed to an instance of SQL Server 2005, but the filter will not be applied.</span></span>  
  
 <span data-ttu-id="e57a6-131">打开该挖掘模型时， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 将引发错误，然后重新生成该模型以删除该筛选器。</span><span class="sxs-lookup"><span data-stu-id="e57a6-131">When you open the mining model, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] raises an error, and then regenerates the model to remove the filter.</span></span>  
  
##  <a name="restoring-from-database-backups"></a><a name="bkmk_Backup"></a><span data-ttu-id="e57a6-132">从数据库备份还原</span><span class="sxs-lookup"><span data-stu-id="e57a6-132">Restoring from Database Backups</span></span>  
 <span data-ttu-id="e57a6-133">不能将使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 创建的数据库备份还原到 SQL Server 2005 实例。</span><span class="sxs-lookup"><span data-stu-id="e57a6-133">You cannot restore a database backup that was created in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to an instance of SQL Server 2005.</span></span> <span data-ttu-id="e57a6-134">否则，SQL Server Management Studio 将生成错误。</span><span class="sxs-lookup"><span data-stu-id="e57a6-134">If you do so, SQL Server Management Studio generates an error.</span></span>  
  
 <span data-ttu-id="e57a6-135">如果创建 SQL Server 2005 Analysis Services 数据库的备份并在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]实例中还原此备份，则所有时序模型都会进行上一节所述的修改。</span><span class="sxs-lookup"><span data-stu-id="e57a6-135">If you create a backup of a SQL Server 2005 Analysis Services database and restore this backup on an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], all time series models are modified as described in the previous section.</span></span>  
  
##  <a name="using-database-synchronization"></a><a name="bkmk_Synch"></a><span data-ttu-id="e57a6-136">使用数据库同步</span><span class="sxs-lookup"><span data-stu-id="e57a6-136">Using Database Synchronization</span></span>  
 <span data-ttu-id="e57a6-137">不支持从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 到 SQL Server 2005 的数据库同步。</span><span class="sxs-lookup"><span data-stu-id="e57a6-137">Database synchronization is not supported from [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to SQL Server 2005.</span></span>  
  
 <span data-ttu-id="e57a6-138">如果尝试同步 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 数据库，则服务器将返回错误，且数据库同步失败。</span><span class="sxs-lookup"><span data-stu-id="e57a6-138">If you attempt to synchronize a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] database, the server returns an error and database synchronization fails.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57a6-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e57a6-139">See Also</span></span>  
 [<span data-ttu-id="e57a6-140">Analysis Services 向后兼容性</span><span class="sxs-lookup"><span data-stu-id="e57a6-140">Analysis Services Backward Compatibility</span></span>](../analysis-services-backward-compatibility.md)  
  
  
