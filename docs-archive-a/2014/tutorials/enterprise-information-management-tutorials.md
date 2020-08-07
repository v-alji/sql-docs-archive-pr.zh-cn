---
title: 企业信息管理教程 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8745dc80-193d-4de0-9f17-ba648ab1e81c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b8cde162479645ab13a6ae000cc46e42e3c10e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588781"
---
# <a name="enterprise-information-management-tutorials"></a><span data-ttu-id="bc51d-102">企业信息管理教程</span><span class="sxs-lookup"><span data-stu-id="bc51d-102">Enterprise Information Management Tutorials</span></span>
  <span data-ttu-id="bc51d-103">本节包含通过使用在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中随附的企业信息管理 (EIM) 技术在企业中管理信息的教程。</span><span class="sxs-lookup"><span data-stu-id="bc51d-103">This section contains tutorials for managing information in an enterprise by using Enterprise Information Management (EIM) technologies that are included in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="bc51d-104">企业信息管理 (EIM) 提供一组解决方案，使组织能够信任其数据的可信性和一致性，以便组织可以作出关键业务决策。</span><span class="sxs-lookup"><span data-stu-id="bc51d-104">Enterprise Integration Management (EIM) provides a portfolio of solutions that enable organizations to trust the credibility and consistency of their data so they can make critical business decisions.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="bc51d-105">具有以下技术，帮助您在企业中实现 EIM 解决方案。</span><span class="sxs-lookup"><span data-stu-id="bc51d-105">has the following technologies that help you implement EIM solutions in your enterprise.</span></span>  
  
-   <span data-ttu-id="bc51d-106">SQL Server Integration Services (SSIS)。</span><span class="sxs-lookup"><span data-stu-id="bc51d-106">SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="bc51d-107">SSIS 提供强大的可扩展平台，用于在支持业务工作流、数据仓库或主数据管理的全面的提取、转换和加载 (ETL) 解决方案中集成来自不同源的数据。</span><span class="sxs-lookup"><span data-stu-id="bc51d-107">SSIS provides a powerful, extensible platform for integrating data from various sources in a comprehensive extract, transform, and load (ETL) solution that supports business workflows, a data warehouse, or master data management.</span></span>  
  
-   <span data-ttu-id="bc51d-108">SQL Server Data Quality Services (DQS)。</span><span class="sxs-lookup"><span data-stu-id="bc51d-108">SQL Server Data Quality Services (DQS).</span></span> <span data-ttu-id="bc51d-109">通过 DQS，您可以清理、匹配、标准化和丰富数据，以便您可以提供可信的信息来用于商业智能、数据仓库和事务处理工作负荷。</span><span class="sxs-lookup"><span data-stu-id="bc51d-109">DQS enables you to cleanse, match, standardize, and enrich data, so you can deliver trusted information for business intelligence, a data warehouse, and transaction processing workloads.</span></span>  
  
-   <span data-ttu-id="bc51d-110">SQL Server Master Data Services (MDS)。</span><span class="sxs-lookup"><span data-stu-id="bc51d-110">SQL Server Master Data Services (MDS).</span></span> <span data-ttu-id="bc51d-111">MDS 提供一个集中的数据中心，确保信息的完整性和数据的一致性在不同应用程序中是不变的。</span><span class="sxs-lookup"><span data-stu-id="bc51d-111">MDS provides a central data hub that ensures that the integrity of information and consistency of data is constant across different applications.</span></span>  
  
 [<span data-ttu-id="bc51d-112">使用 SSIS、MDS 和 DQS 将企业信息管理结合在一起 &#91;教程&#93;</span><span class="sxs-lookup"><span data-stu-id="bc51d-112">Enterprise Information Management using SSIS, MDS, and DQS Together &#91;Tutorial&#93;</span></span>](../../2014/tutorials/enterprise-information-management-using-ssis-mds-and-dqs-together-[tutorial].md)  
 <span data-ttu-id="bc51d-113">在本教程中，您将学习如何一起使用 SSIS、MDS 和 DQS 来实现一个示例企业信息管理 (EIM) 解决方案。</span><span class="sxs-lookup"><span data-stu-id="bc51d-113">In this tutorial, you learn how to use SSIS, MDS, and DQS together to implement a sample Enterprise Information Management (EIM) solution.</span></span> <span data-ttu-id="bc51d-114">首先，您将使用 DQS 创建一个包含与供应商数据（元数据）有关的知识的知识库，根据该知识库清理一个 Excel 文件中的数据，并且对数据进行匹配以便标识并删除数据中的重复项。</span><span class="sxs-lookup"><span data-stu-id="bc51d-114">First, you use DQS to create a knowledgebase with the knowledge about the supplier data (metadata), cleanse the data in an Excel file against the knowledge base, and match the data to identify and remove duplicates in the data.</span></span> <span data-ttu-id="bc51d-115">接下来，您将使用用于 Excel 的 MDS 外接程序将已清理和匹配的数据上载到 MDS。</span><span class="sxs-lookup"><span data-stu-id="bc51d-115">Next, you use the MDS Add-in for Excel to upload the cleansed and matched data to MDS.</span></span> <span data-ttu-id="bc51d-116">然后，您通过使用一个 SSIS 解决方案自动化整个过程。</span><span class="sxs-lookup"><span data-stu-id="bc51d-116">Then, you automate the whole process by using an SSIS solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc51d-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc51d-117">See Also</span></span>  
 [<span data-ttu-id="bc51d-118">企业信息管理-Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="bc51d-118">Enterprise Information Management - Microsoft SQL Server</span></span>](https://go.microsoft.com/fwlink/?LinkId=270871)  
  
  
