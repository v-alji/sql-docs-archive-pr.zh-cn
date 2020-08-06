---
title: 将数据质量规则应用于数据源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d59e6fb5ffb752b3346d40740e0b841bf574344e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682968"
---
# <a name="apply-data-quality-rules-to-data-source"></a><span data-ttu-id="10532-102">将数据质量规则应用于数据源</span><span class="sxs-lookup"><span data-stu-id="10532-102">Apply Data Quality Rules to Data Source</span></span>
  <span data-ttu-id="10532-103">您可以使用 Data Quality Services (DQS) 来更正包数据流中的数据，方法是将 DQS 情理转换连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="10532-103">You can use Data Quality Services (DQS) to correct data in the package data flow by connecting the DQS Cleansing transformation to the data source.</span></span> <span data-ttu-id="10532-104">有关 DQS 的详细信息，请参阅 [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="10532-104">For more information about DQS, see [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).</span></span> <span data-ttu-id="10532-105">有关该转换的详细信息，请参阅 [DQS Cleansing Transformation](dqs-cleansing-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="10532-105">For more information about the transformation, see [DQS Cleansing Transformation](dqs-cleansing-transformation.md).</span></span>  
  
 <span data-ttu-id="10532-106">使用 DQS 清理转换处理数据时，将在数据质量服务器上创建一个数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="10532-106">When you process data with the DQS Cleansing transformation, a data quality project is created on the Data Quality Server.</span></span> <span data-ttu-id="10532-107">使用数据质量客户端管理项目。</span><span class="sxs-lookup"><span data-stu-id="10532-107">You use the Data Quality Client to manage the project.</span></span> <span data-ttu-id="10532-108">有关详细信息，请参阅[管理（打开、解锁、重命名和删除）数据质量项目](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)。</span><span class="sxs-lookup"><span data-stu-id="10532-108">For more information, see [Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md).</span></span>  
  
### <a name="to-correct-data-in-the-data-flow"></a><span data-ttu-id="10532-109">更正数据流中的数据</span><span class="sxs-lookup"><span data-stu-id="10532-109">To correct data in the data flow</span></span>  
  
1.  <span data-ttu-id="10532-110">创建一个包。</span><span class="sxs-lookup"><span data-stu-id="10532-110">Create a package.</span></span>  
  
2.  <span data-ttu-id="10532-111">添加并配置 DQS 清除转换。</span><span class="sxs-lookup"><span data-stu-id="10532-111">Add and configure the DQS Cleansing transformation.</span></span> <span data-ttu-id="10532-112">有关详细信息，请参阅 [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="10532-112">For more information, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="10532-113">将 DQS 清除转换连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="10532-113">Connect the DQS Cleansing transformation to a data source.</span></span>  
  
  
