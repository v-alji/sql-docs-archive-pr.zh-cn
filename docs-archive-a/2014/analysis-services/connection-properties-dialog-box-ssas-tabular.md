---
title: "\"连接属性\" 对话框 (SSAS-表格) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.ConnectionProperties.F1
ms.assetid: 17bae8ae-2ba0-4978-be70-61c687f59d54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e4b0360d59f43bc932f68a846f239c4873a5aa9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579190"
---
# <a name="connection-properties-dialog-box-ssas---tabular"></a><span data-ttu-id="a2d30-102">“连接属性”对话框（SSAS - 表格）</span><span class="sxs-lookup"><span data-stu-id="a2d30-102">Connection Properties Dialog Box (SSAS - Tabular)</span></span>
  <span data-ttu-id="a2d30-103">使用此页可在 SQL Server Management Studio 中查看或修改表格模型数据库使用的数据源的连接属性。</span><span class="sxs-lookup"><span data-stu-id="a2d30-103">Use this page to view or modify in SQL Server Management Studio the connection properties of a data source used by a tabular model database.</span></span>  
  
 <span data-ttu-id="a2d30-104">此对话框提供了时间戳和其他说明性信息，以及确定连接特性的可自定义属性。</span><span class="sxs-lookup"><span data-stu-id="a2d30-104">This dialog box provides timestamps and other descriptive information, plus customizable properties that determine characteristics of the connection.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a2d30-105">选项</span><span class="sxs-lookup"><span data-stu-id="a2d30-105">Options</span></span>  
  
|<span data-ttu-id="a2d30-106">术语</span><span class="sxs-lookup"><span data-stu-id="a2d30-106">Term</span></span>|<span data-ttu-id="a2d30-107">定义</span><span class="sxs-lookup"><span data-stu-id="a2d30-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="a2d30-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="a2d30-108">**Name**</span></span>|<span data-ttu-id="a2d30-109">指定数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="a2d30-109">Specifies the name of the data source.</span></span>|  
|<span data-ttu-id="a2d30-110">**ID**</span><span class="sxs-lookup"><span data-stu-id="a2d30-110">**ID**</span></span>|<span data-ttu-id="a2d30-111">显示数据源对象的标识符。</span><span class="sxs-lookup"><span data-stu-id="a2d30-111">Displays the identifier of the data source object.</span></span>|  
|<span data-ttu-id="a2d30-112">**说明**</span><span class="sxs-lookup"><span data-stu-id="a2d30-112">**Description**</span></span>|<span data-ttu-id="a2d30-113">显示数据源对象的说明。</span><span class="sxs-lookup"><span data-stu-id="a2d30-113">Displays the description of the data source object.</span></span>|  
|<span data-ttu-id="a2d30-114">**创建时间戳**</span><span class="sxs-lookup"><span data-stu-id="a2d30-114">**Create Timestamp**</span></span>|<span data-ttu-id="a2d30-115">显示数据库的创建日期和时间。</span><span class="sxs-lookup"><span data-stu-id="a2d30-115">Displays the date and time the database was created.</span></span>|  
|<span data-ttu-id="a2d30-116">**上次架构更新时间**</span><span class="sxs-lookup"><span data-stu-id="a2d30-116">**Last Schema Update**</span></span>|<span data-ttu-id="a2d30-117">显示上次更新数据库元数据的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="a2d30-117">Displays the date and time the metadata for the database was last updated.</span></span>|  
|<span data-ttu-id="a2d30-118">**连接字符串**</span><span class="sxs-lookup"><span data-stu-id="a2d30-118">**Connection String**</span></span>|<span data-ttu-id="a2d30-119">显示用于连接到向模型提供数据的数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="a2d30-119">Displays the connection string used to connect to the data source that provides data to the model.</span></span>|  
|<span data-ttu-id="a2d30-120">**最大连接数**</span><span class="sxs-lookup"><span data-stu-id="a2d30-120">**Maximum Number of Connections**</span></span>|<span data-ttu-id="a2d30-121">指定与此数据库之间的最大客户端连接数。</span><span class="sxs-lookup"><span data-stu-id="a2d30-121">Specifies the maximum number of client connections to this database.</span></span>|  
|<span data-ttu-id="a2d30-122">**隔离**</span><span class="sxs-lookup"><span data-stu-id="a2d30-122">**Isolation**</span></span>|<span data-ttu-id="a2d30-123">有效值为 ReadCommitted 或 Snapshot。</span><span class="sxs-lookup"><span data-stu-id="a2d30-123">Valid values are ReadCommitted or Snapshot.</span></span> <span data-ttu-id="a2d30-124">有关详细信息，请参阅 [Isolation 元素 (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/isolation-element-assl)。</span><span class="sxs-lookup"><span data-stu-id="a2d30-124">For more information, see [Isolation Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/isolation-element-assl).</span></span>|  
|<span data-ttu-id="a2d30-125">**查询超时**</span><span class="sxs-lookup"><span data-stu-id="a2d30-125">**Query Timeout**</span></span>|<span data-ttu-id="a2d30-126">指定一段时间（以秒为单位），在这段时间过后试图检索数据时发生超时。</span><span class="sxs-lookup"><span data-stu-id="a2d30-126">Specifies the time, in seconds, after which an attempt to retrieve data is timed out.</span></span>|  
|<span data-ttu-id="a2d30-127">**托管提供程序**</span><span class="sxs-lookup"><span data-stu-id="a2d30-127">**Managed Provider**</span></span>|<span data-ttu-id="a2d30-128">指定托管访问接口的名称。</span><span class="sxs-lookup"><span data-stu-id="a2d30-128">Specifies the name of the managed provider.</span></span> <span data-ttu-id="a2d30-129">如果数据源连接使用本机 OLE DB 访问接口，则此值为空。</span><span class="sxs-lookup"><span data-stu-id="a2d30-129">If the data source connection uses a native OLE DB provider, this value is empty.</span></span>|  
|<span data-ttu-id="a2d30-130">**模拟信息**</span><span class="sxs-lookup"><span data-stu-id="a2d30-130">**Impersonation Info**</span></span>|<span data-ttu-id="a2d30-131">指定在处理或刷新数据时用于数据库连接的模拟帐户、针对关系数据存储区（通过 DirectQuery）运行的查询、外部绑定、远程分区以及从目标到源的数据库同步。</span><span class="sxs-lookup"><span data-stu-id="a2d30-131">Specifies the impersonation account used for database connections when processing or refreshing data, queries that run against a relational data store (via DirectQuery), out-of-line bindings, remote partitions, and database synchronization from target to source.</span></span><br /><br /> <span data-ttu-id="a2d30-132">有效值包括 Analysis Services 服务帐户或一组特定的 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="a2d30-132">Valid values include the Analysis Services service account or a specific set of Windows credentials.</span></span> <span data-ttu-id="a2d30-133">不要指定 **“使用当前用户的凭据”** 或 **“继承”**。</span><span class="sxs-lookup"><span data-stu-id="a2d30-133">Do not specify **Use the credentials of the current user** or **Inherit**.</span></span> <span data-ttu-id="a2d30-134">表格模型数据库不支持这些凭据选项。</span><span class="sxs-lookup"><span data-stu-id="a2d30-134">Those credential options are not supported for a tabular model database.</span></span>|  
  
  
