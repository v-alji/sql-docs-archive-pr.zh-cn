---
title: 结论 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b1e6fde6-c3a7-4b91-b176-fa465325dd21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 906f9f10c541e7662d5573fd242a84f37483166e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691399"
---
# <a name="conclusion"></a><span data-ttu-id="e8255-102">结论</span><span class="sxs-lookup"><span data-stu-id="e8255-102">Conclusion</span></span>
  <span data-ttu-id="e8255-103">在本教程中，您已学习了如何一起使用 SQL Server Integration Services (SSIS)、Master Data Services (MDS) 和 Data Quality Services (DQS) 来实现一个示例企业信息管理 (EIM) 解决方案。</span><span class="sxs-lookup"><span data-stu-id="e8255-103">In this tutorial, you have learned how to use SQL Server Integration Services (SSIS), Master Data Services (MDS), and Data Quality Services (DQS) together to implement a sample Enterprise Information Management (EIM) solution.</span></span> <span data-ttu-id="e8255-104">首先，您使用数据质量客户端工具创建了一个包含与供应商有关知识的 DQS 知识库，对照该知识库清理了一个 excel 文件中的输入供应商数据，然后通过使用该知识库中的匹配策略对供应商数据进行了匹配，以便标识并删除数据中的重复项。</span><span class="sxs-lookup"><span data-stu-id="e8255-104">First, you used the Data Quality Client tool to create a DQS knowledge base with the knowledge about suppliers, cleansed the input supplier data in an excel file against the knowledge base, and then matched the supplier data by using a matching policy in the knowledge base to identify and remove duplicates in the data.</span></span> <span data-ttu-id="e8255-105">接下来，通过使用用于 Excel 的 MDS 外接程序，您将已清理和已匹配的供应商列表存储到 MDS 中。</span><span class="sxs-lookup"><span data-stu-id="e8255-105">Next, by using the MDS Add-in for Excel, you stored the cleansed and matched supplier list in MDS.</span></span> <span data-ttu-id="e8255-106">最后，您通过创建一个 SSIS 解决方案，将接收输入数据、清理和匹配数据以及将主数据存储于 MDS 中的整个过程自动化。</span><span class="sxs-lookup"><span data-stu-id="e8255-106">Finally, you automated the whole process of receiving input data, cleansing and matching the data, and storing the master data in MDS by creating an SSIS solution.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="e8255-107">更多相关信息：</span><span class="sxs-lookup"><span data-stu-id="e8255-107">For more information:</span></span>  
  
 [<span data-ttu-id="e8255-108">企业信息管理 (EIM)：将 SSIS、DQS 和 MDS 融汇在一起（视频）</span><span class="sxs-lookup"><span data-stu-id="e8255-108">Enterprise Information Management (EIM): Bringing together SSIS, DQS, and MDS (Video)</span></span>](https://go.microsoft.com/fwlink/?LinkId=258672)  
  
  
