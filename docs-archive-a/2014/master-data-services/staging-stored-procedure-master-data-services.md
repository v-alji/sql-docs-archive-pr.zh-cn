---
title: 临时存储过程 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9259352350a099db5d9b18411ad4da06dfb19819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591444"
---
# <a name="staging-stored-procedure-master-data-services"></a><span data-ttu-id="0860b-102">临时存储过程 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0860b-102">Staging Stored Procedure (Master Data Services)</span></span>
  <span data-ttu-id="0860b-103">从 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]启动临时过程时，您使用三个存储过程之一。</span><span class="sxs-lookup"><span data-stu-id="0860b-103">When initiating the staging process from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you use one of three stored procedures.</span></span>  
  
-   <span data-ttu-id="0860b-104">stg.udp_name_Leaf</span><span class="sxs-lookup"><span data-stu-id="0860b-104">stg.udp_name_Leaf</span></span>  
  
-   <span data-ttu-id="0860b-105">stg.udp_name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="0860b-105">stg.udp_name_Consolidated</span></span>  
  
-   <span data-ttu-id="0860b-106">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="0860b-106">stg.udp_name_Relationship</span></span>  
  
 <span data-ttu-id="0860b-107">其中 name 是创建实体时指定的临时表的名称。</span><span class="sxs-lookup"><span data-stu-id="0860b-107">Where name is the name of the staging table that was specified when the entity was created.</span></span>  
  
## <a name="staging-process-stored-procedure-parameters"></a><span data-ttu-id="0860b-108">临时过程存储过程参数</span><span class="sxs-lookup"><span data-stu-id="0860b-108">Staging Process Stored Procedure Parameters</span></span>  
 <span data-ttu-id="0860b-109">下表列出了这些存储过程的参数。</span><span class="sxs-lookup"><span data-stu-id="0860b-109">The following table lists the parameters of these stored procedures.</span></span>  
  
|<span data-ttu-id="0860b-110">参数</span><span class="sxs-lookup"><span data-stu-id="0860b-110">Parameter</span></span>|<span data-ttu-id="0860b-111">说明</span><span class="sxs-lookup"><span data-stu-id="0860b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0860b-112">**VersionName**</span><span class="sxs-lookup"><span data-stu-id="0860b-112">**VersionName**</span></span><br /><br /> <span data-ttu-id="0860b-113">必需</span><span class="sxs-lookup"><span data-stu-id="0860b-113">Required</span></span>|<span data-ttu-id="0860b-114">版本的名称。</span><span class="sxs-lookup"><span data-stu-id="0860b-114">The name of the version.</span></span> <span data-ttu-id="0860b-115">这可能区分大小写，也可能不区分，具体取决于您的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 排序规则设置。</span><span class="sxs-lookup"><span data-stu-id="0860b-115">This may or may not be case-sensitive, depending on your [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] collation setting.</span></span>|  
|<span data-ttu-id="0860b-116">**LogFlag**</span><span class="sxs-lookup"><span data-stu-id="0860b-116">**LogFlag**</span></span><br /><br /> <span data-ttu-id="0860b-117">必需</span><span class="sxs-lookup"><span data-stu-id="0860b-117">Required</span></span>|<span data-ttu-id="0860b-118">确定在临时过程中是否记录事务。</span><span class="sxs-lookup"><span data-stu-id="0860b-118">Determines whether transactions are logged during the staging process.</span></span> <span data-ttu-id="0860b-119">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="0860b-119">Possible values are:</span></span><br /><br /> <span data-ttu-id="0860b-120">**0**：不记录事务。</span><span class="sxs-lookup"><span data-stu-id="0860b-120">**0**: Do not log transactions.</span></span><br /><span data-ttu-id="0860b-121">**1**：记录事务。</span><span class="sxs-lookup"><span data-stu-id="0860b-121">**1**: Log transactions.</span></span><br /><br /> <br /><br /> <span data-ttu-id="0860b-122">有关事务的详细信息，请参阅[事务 (Master Data Services)](transactions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0860b-122">For more information about transactions, see [Transactions &#40;Master Data Services&#41;](transactions-master-data-services.md).</span></span>|  
|<span data-ttu-id="0860b-123">**BatchTag**</span><span class="sxs-lookup"><span data-stu-id="0860b-123">**BatchTag**</span></span><br /><br /> <span data-ttu-id="0860b-124">必需，但是 Web 服务除外</span><span class="sxs-lookup"><span data-stu-id="0860b-124">Required, except by web service</span></span>|<span data-ttu-id="0860b-125">在临时表中指定 **BatchTag** 值。</span><span class="sxs-lookup"><span data-stu-id="0860b-125">The **BatchTag** value as specified in the staging table.</span></span>|  
|<span data-ttu-id="0860b-126">**Batch_ID**</span><span class="sxs-lookup"><span data-stu-id="0860b-126">**Batch_ID**</span></span><br /><br /> <span data-ttu-id="0860b-127">仅对 Web 服务为必需的</span><span class="sxs-lookup"><span data-stu-id="0860b-127">Required by web service only</span></span>|<span data-ttu-id="0860b-128">在临时表中指定的 **Batch_ID** 值。</span><span class="sxs-lookup"><span data-stu-id="0860b-128">The **Batch_ID** value as specified in the staging table.</span></span>|  
  
### <a name="staging-process-stored-procedure-example"></a><span data-ttu-id="0860b-129">临时过程存储过程示例</span><span class="sxs-lookup"><span data-stu-id="0860b-129">Staging Process Stored Procedure Example</span></span>  
 <span data-ttu-id="0860b-130">下面的示例说明了如何使用临时存储过程启动临时过程。</span><span class="sxs-lookup"><span data-stu-id="0860b-130">The following example shows how to start the staging process by using the staging stored procedure.</span></span>  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="0860b-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0860b-131">See Also</span></span>  
 <span data-ttu-id="0860b-132">[验证存储过程 &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0860b-132">[Validation Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md) </span></span>  
 <span data-ttu-id="0860b-133">[通过使用临时过程在 Master Data Services 中加载或更新成员](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0860b-133">[Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) </span></span>  
 [<span data-ttu-id="0860b-134">查看临时过程中发生的错误 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0860b-134">View Errors that Occur During the Staging Process &#40;Master Data Services&#41;</span></span>](view-errors-that-occur-during-staging-master-data-services.md)  
  
  
