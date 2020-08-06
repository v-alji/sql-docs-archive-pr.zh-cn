---
title: 案例研究：使用 Microsoft Dynamics ERP 生成企业生态系统和 SQL Server 2014 复制以实现可伸缩性和性能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 2b0b5ab7-4e08-431a-bd59-360177c4565c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: dfde59b5e3e12746aa6dbaf975b079cfe32a3718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577109"
---
# <a name="case-study-building-an-enterprise-ecosystem-with-microsoft-dynamics-erp-and-sql-server-2014-replication-for-scalability-and-performance"></a><span data-ttu-id="6af9c-102">案例研究：使用 Microsoft Dynamics ERP 和 SQL Server 2014 复制构建一个企业生态系统以实现可伸缩性并提高性能</span><span class="sxs-lookup"><span data-stu-id="6af9c-102">Case Study: Building an Enterprise Ecosystem with Microsoft Dynamics ERP and SQL Server 2014 Replication for Scalability and Performance</span></span>

  <span data-ttu-id="6af9c-103">**摘要：** 本文介绍了以下方案：</span><span class="sxs-lookup"><span data-stu-id="6af9c-103">**Summary:** This paper covers the following scenarios:</span></span>  
<span data-ttu-id="6af9c-104">如何使用 SQL Server 2014 中的事务复制跨多个节点分布 Dynamics AX 客户端的事务。</span><span class="sxs-lookup"><span data-stu-id="6af9c-104">How to use transactional replication in SQL Server 2014 to distribute the transactions from Dynamics AX clients across multiple nodes.</span></span> <span data-ttu-id="6af9c-105">因为数据以实时的方式在节点上进行维护，因此事务复制提供了数据冗余，可用于提高数据的可用性，其中包括适用于更加高效的性能分析的数据。</span><span class="sxs-lookup"><span data-stu-id="6af9c-105">Because data is maintained across the nodes in real-time, transactional replication provides data redundancy, which increases the availability of data, includes data available for more efficient performance analysis.</span></span>  
<span data-ttu-id="6af9c-106">如何在利用事务复制时了解涉及的具体内容，以在 Microsoft Dynamics ERP 中构建高度可伸缩的企业生态系统。</span><span class="sxs-lookup"><span data-stu-id="6af9c-106">How to understand the specifics involved while leveraging transactional replication to build highly scalable Enterprise ecosystems in Microsoft Dynamics ERP.</span></span> <span data-ttu-id="6af9c-107">提供高性能和可伸缩性，无需自定义 AX 自带功能。</span><span class="sxs-lookup"><span data-stu-id="6af9c-107">Deliver high performance and scalability without customizing the AX out-of-box features.</span></span>  
  
 <span data-ttu-id="6af9c-108">事务复制通常用于需要高吞吐量的服务器到服务器工作流中。</span><span class="sxs-lookup"><span data-stu-id="6af9c-108">Transactional replication is typically used in server-to-server workflows that require high throughput.</span></span> <span data-ttu-id="6af9c-109">其中包括如下方案：提高可伸缩性和可用性、数据仓库和报告、集成多个站点的数据、集成异类数据以及减轻批处理的负荷。</span><span class="sxs-lookup"><span data-stu-id="6af9c-109">These include scenarios, such as improving scalability and availability, data warehousing and reporting, integrating data from multiple sites, integrating heterogeneous data, and offloading batch processing.</span></span> <span data-ttu-id="6af9c-110">本白皮书介绍了在 Microsoft Dynamics ERP 中利用事务复制的不同方案和关联模式。</span><span class="sxs-lookup"><span data-stu-id="6af9c-110">This white paper describes a distinct scenario and associated patterns where transactional replication is leveraged in Microsoft Dynamics ERP.</span></span> <span data-ttu-id="6af9c-111">它还介绍了在考虑使用事务复制构建特定于企业资源规划 (ERP) 的企业解决方案时所面临的挑战和最佳做法，以及不同阶段的性能分析。</span><span class="sxs-lookup"><span data-stu-id="6af9c-111">It also covers the challenges and best practices when considering transactional replication to build enterprise solutions specific to Enterprise Resource Planning (ERP), as well as the performance analysis at different stages.</span></span>  
  
 <span data-ttu-id="6af9c-112">此内容是适用于开发人员、架构师和数据库管理员。</span><span class="sxs-lookup"><span data-stu-id="6af9c-112">This content is suitable for developers, architects, and database administrators.</span></span> <span data-ttu-id="6af9c-113">假定本白皮书的读者具有 SQL Server 2008、2012 或 2014 的基本知识以及 SQL Server 的管理经验。</span><span class="sxs-lookup"><span data-stu-id="6af9c-113">It is assumed that readers of this white paper have basic knowledge of SQL Server 2008, 2012, or 2014 as well as SQL Server administration experience.</span></span>  
  
 <span data-ttu-id="6af9c-114">**编写器：** Prabhakaran Sethuraman (PRAB) ，Microsoft</span><span class="sxs-lookup"><span data-stu-id="6af9c-114">**Writer:** Prabhakaran Sethuraman (PRAB), Microsoft</span></span>  
  
 <span data-ttu-id="6af9c-115">**技术审阅者：** Prabhakaran Sethuraman (PRAB) ，Microsoft;Santosh Padhy，Microsoft;Pavel Majstrov，Microsoft;Karthik Sankaranarayanan，Microsoft;吴建 Acone、Microsoft;David Stahlkopf、Microsoft;Kent Oldenburger，Microsoft;Mandi Ohlinger，Microsoft;Jason Roth，Microsoft</span><span class="sxs-lookup"><span data-stu-id="6af9c-115">**Technical Reviewers:** Prabhakaran Sethuraman (PRAB), Microsoft; Santosh Padhy, Microsoft; Pavel Majstrov, Microsoft; Karthik Sankaranarayanan, Microsoft; Jon Acone, Microsoft; David Stahlkopf, Microsoft;Kent Oldenburger, Microsoft; Mandi Ohlinger, Microsoft; Jason Roth, Microsoft</span></span>  
  
 <span data-ttu-id="6af9c-116">**已发布：** 2015年10月</span><span class="sxs-lookup"><span data-stu-id="6af9c-116">**Published:** October 2015</span></span>  
  
 <span data-ttu-id="6af9c-117">**适用于：** SQL Server 2008、SQL Server 2012 和 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="6af9c-117">**Applies to:** SQL Server 2008, SQL Server 2012, and SQL Server 2014</span></span>  
  
 <span data-ttu-id="6af9c-118">若要查看文档，请下载</span><span class="sxs-lookup"><span data-stu-id="6af9c-118">To review the document, please download the</span></span>  
        <span data-ttu-id="6af9c-119">[案例研究：使用 Microsoft DYNAMICS ERP 生成企业生态系统和 SQL Server 2014 复制，以实现可伸缩性和性能](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx)Word 文档。</span><span class="sxs-lookup"><span data-stu-id="6af9c-119">[Case Study: Building an Enterprise Ecosystem with Microsoft Dynamics ERP and SQL Server 2014 Replication for Scalability and Performance](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx) Word document.</span></span>  
  
  
