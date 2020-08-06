---
title: "\"数据库属性\" 对话框 (SSAS-多维) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.databaseproperties.f1
ms.assetid: 70f000b7-917f-4699-b142-7a0d13ff767c
author: minewiskan
ms.author: owend
ms.openlocfilehash: a465c333557f19e9572cd9c2b1f7c80aaf4ab5bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682436"
---
# <a name="database-properties-dialog-box-ssas---multidimensional"></a><span data-ttu-id="2c1a5-102">“数据库属性”对话框（SSAS - 多维）</span><span class="sxs-lookup"><span data-stu-id="2c1a5-102">Database Properties Dialog Box (SSAS - Multidimensional)</span></span>
  <span data-ttu-id="2c1a5-103">可以使用 **中的** “数据库属性” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 对话框设置 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库的属性。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-103">Use the **Database Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of a database in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="2c1a5-104">在对象资源管理器中右键单击某个数据库，并选择“属性”，可以显示“数据库属性”对话框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-104">You can display the **Database Properties** dialog box by right-clicking a database in Object Explorer and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2c1a5-105">选项</span><span class="sxs-lookup"><span data-stu-id="2c1a5-105">Options</span></span>  
  
|<span data-ttu-id="2c1a5-106">术语</span><span class="sxs-lookup"><span data-stu-id="2c1a5-106">Term</span></span>|<span data-ttu-id="2c1a5-107">定义</span><span class="sxs-lookup"><span data-stu-id="2c1a5-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="2c1a5-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-108">**Name**</span></span>|<span data-ttu-id="2c1a5-109">键入内容即可更改数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-109">Type to change the name of the database.</span></span>|  
|<span data-ttu-id="2c1a5-110">**ID**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-110">**ID**</span></span>|<span data-ttu-id="2c1a5-111">显示数据库的标识符。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-111">Displays the identifier of the database.</span></span>|  
|<span data-ttu-id="2c1a5-112">**说明**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-112">**Description**</span></span>|<span data-ttu-id="2c1a5-113">键入内容即可更改数据库的说明。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-113">Type to change the description of the database.</span></span>|  
|<span data-ttu-id="2c1a5-114">**创建时间戳**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-114">**Create Timestamp**</span></span>|<span data-ttu-id="2c1a5-115">显示数据库的创建日期和时间。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-115">Displays the date and time the database was created.</span></span>|  
|<span data-ttu-id="2c1a5-116">**上次架构更新时间**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-116">**Last Schema Update**</span></span>|<span data-ttu-id="2c1a5-117">显示上次更新数据库元数据的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-117">Displays the date and time the metadata for the database was last updated.</span></span>|  
|<span data-ttu-id="2c1a5-118">**上次更新时间**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-118">**Last Update**</span></span>|<span data-ttu-id="2c1a5-119">显示上次更新数据库的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-119">Displays the date and time the data for the database was last updated.</span></span>|  
|<span data-ttu-id="2c1a5-120">**数据源模拟信息**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-120">**Data Source Impersonation Info**</span></span>|<span data-ttu-id="2c1a5-121">选择在连接到数据库中包含的数据源以及与该数据源进行交互时数据库所使用的模拟信息。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-121">Select the impersonation information used by the database when connecting to and interacting with data sources contained by the database.</span></span> <span data-ttu-id="2c1a5-122">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="2c1a5-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2c1a5-123">**ImpersonateAccount** （使用特定的 Windows 用户名和密码）。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-123">**ImpersonateAccount** (use a specific Windows user name and password).</span></span><br /><br /> <span data-ttu-id="2c1a5-124">**ImpersonateService** （使用服务帐户）。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-124">**ImpersonateService** (use the service account).</span></span><br /><br /> <span data-ttu-id="2c1a5-125">**ImpersonateCurrentUser** （使用当前用户的凭据）。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-125">**ImpersonateCurrentUser** (use the credentials of the current user).</span></span><br /><br /> <span data-ttu-id="2c1a5-126">**默认值** （使用服务帐户执行 MOLAP 操作，使用当前用户执行数据挖掘）。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-126">**Default** (use the service account for MOLAP operations and current user for data mining).</span></span><br /><br /> <span data-ttu-id="2c1a5-127">尽管您可以在数据库级别设置数据源模拟设置，但这样做只影响为其模拟设置指定 **“继承”** 的那些数据源。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-127">Although you can set data source impersonation settings at the database level, doing so will only affect those data sources that specify **Inherit** for their impersonation settings.</span></span> <span data-ttu-id="2c1a5-128">直接在数据源上指定的模拟设置始终覆盖在数据库级别指定的任何设置。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-128">Impersonation settings specified directly on the data source will always override any settings that are specified at the database level.</span></span><br /><br /> <span data-ttu-id="2c1a5-129">当选择模拟选项时，请考虑需要支持的操作类型。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-129">When choosing an impersonation option, consider the types of operations that will need to be supported.</span></span> <span data-ttu-id="2c1a5-130">无法执行某些操作（如处理）</span><span class="sxs-lookup"><span data-stu-id="2c1a5-130">Some operations, such as processing, cannot be performed by</span></span>|  
|<span data-ttu-id="2c1a5-131">**上次处理时间**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-131">**Last Processed**</span></span>|<span data-ttu-id="2c1a5-132">显示上次处理数据库的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-132">Displays the date and time the database was last processed.</span></span>|  
|<span data-ttu-id="2c1a5-133">**估计大小**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-133">**Estimated Size**</span></span>|<span data-ttu-id="2c1a5-134">显示数据库的估计大小。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-134">Displays the estimated size of the database.</span></span>|  
|<span data-ttu-id="2c1a5-135">**存储位置**</span><span class="sxs-lookup"><span data-stu-id="2c1a5-135">**Storage Location**</span></span>|<span data-ttu-id="2c1a5-136">指定数据库的位置。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-136">Specifies the location of the database.</span></span> <span data-ttu-id="2c1a5-137">如果数据库位于默认数据目录中，则此值将为空。</span><span class="sxs-lookup"><span data-stu-id="2c1a5-137">If the database is located in the default Data directory, this value will be empty.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c1a5-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c1a5-138">See Also</span></span>  
 <span data-ttu-id="2c1a5-139">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="2c1a5-139">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="2c1a5-140">多维模型数据库 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="2c1a5-140">Multidimensional Model Databases &#40;SSAS&#41;</span></span>](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
