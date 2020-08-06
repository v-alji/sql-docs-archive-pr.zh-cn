---
title: 使用 Diffgram 修改 SQLXML 4.0 中的数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- data deletions [SQLXML]
- updating data [SQLXML]
- DiffGrams [SQLXML]
- modifying data [SQLXML]
- .NET Framework [SQLXML], DiffGrams
- XML [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- data modifications [SQLXML]
- record insertion [SQLXML]
- SQLXML, DiffGrams
- deleting data
- record updates [SQLXML]
- record deletions [SQLXML]
ms.assetid: 48b8a8f9-f3af-404f-8c84-f4c3703364d9
author: rothja
ms.author: jroth
ms.openlocfilehash: cc2e24304679a7648f18148eb45f33b9bf719a9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587286"
---
# <a name="using-diffgrams-to-modify-data-in-sqlxml-40"></a><span data-ttu-id="a6162-102">使用 DiffGram 修改 SQLXML 4.0 中的数据</span><span class="sxs-lookup"><span data-stu-id="a6162-102">Using DiffGrams to Modify Data in SQLXML 4.0</span></span>
  <span data-ttu-id="a6162-103">DiffGram 格式是在 .NET Framework 的**数据集**组件中引入的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a6162-103">The DiffGram format is introduced in the **DataSet** component of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="a6162-104">在 .NET Framework 中，您可以创建 DiffGram，并使用它来修改 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中的表的数据。</span><span class="sxs-lookup"><span data-stu-id="a6162-104">Within the .NET Framework, you can create DiffGrams and use them to modify data in tables in a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6162-105">本部分简单介绍了 DiffGram，并提供了如何使用 DiffGram 的示例。</span><span class="sxs-lookup"><span data-stu-id="a6162-105">This section provides a brief introduction to DiffGrams and examples of how to use them.</span></span> <span data-ttu-id="a6162-106">本部分假定您熟悉 .NET Framework 中的 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="a6162-106">It is assumed that you are familiar with DiffGrams in the .NET Framework.</span></span> <span data-ttu-id="a6162-107">本文档重点关注特定于 SQLXML 的 DiffGram 问题。</span><span class="sxs-lookup"><span data-stu-id="a6162-107">In this documentation, the primary focus is on DiffGram issues that are specific to SQLXML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6162-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="a6162-108">In This Section</span></span>  
 [<span data-ttu-id="a6162-109">SQLXML 4.0 中的 DiffGrams 简介</span><span class="sxs-lookup"><span data-stu-id="a6162-109">Introduction to DiffGrams in SQLXML 4.0</span></span>](introduction-to-diffgrams-in-sqlxml-4-0.md)  
 <span data-ttu-id="a6162-110">提供有关 Diffgram 的基本信息。</span><span class="sxs-lookup"><span data-stu-id="a6162-110">Provides basic information about Diffgrams.</span></span>  
  
 [<span data-ttu-id="a6162-111">&#40;SQLXML 4.0&#41;的 DiffGram 示例</span><span class="sxs-lookup"><span data-stu-id="a6162-111">DiffGram Examples &#40;SQLXML 4.0&#41;</span></span>](diffgram-examples-sqlxml-4-0.md)  
 <span data-ttu-id="a6162-112">提供使用 Diffgram 的示例。</span><span class="sxs-lookup"><span data-stu-id="a6162-112">Provides examples of using Diffgrams.</span></span>  
  
 [<span data-ttu-id="a6162-113">使用 ADO 执行 DiffGram &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a6162-113">Executing a DiffGram by Using ADO &#40;SQLXML 4.0&#41;</span></span>](executing-a-diffgram-by-using-ado-sqlxml-4-0.md)  
 <span data-ttu-id="a6162-114">提供使用 ActiveX 数据对象 (ADO) 执行 Diffgram 的示例。</span><span class="sxs-lookup"><span data-stu-id="a6162-114">Provides an example of executing a Diffgram with ActiveX Data Objects (ADO).</span></span>  
  
 [<span data-ttu-id="a6162-115">使用 SQLXML 托管类执行 DiffGram</span><span class="sxs-lookup"><span data-stu-id="a6162-115">Executing a DiffGram by Using SQLXML Managed Classes</span></span>](../net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)  
 <span data-ttu-id="a6162-116">提供使用 SQLXML 托管类执行 Diffgram 的示例。</span><span class="sxs-lookup"><span data-stu-id="a6162-116">Provides an example of executing a Diffgram with SQLXML Managed Classes.</span></span>  
  
  
