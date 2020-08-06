---
title: 使用 Updategram 修改 SQLXML 4.0 中的数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- data insertions [SQLXML]
- data deletions [SQLXML]
- updating data [SQLXML]
- modifying data [SQLXML]
- OPENXML function
- updategrams [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- modifying databases
- data modifications [SQLXML]
- deleting data
- inserting data
ms.assetid: b8b3b892-cb73-41d0-b945-bce148d81d9b
author: rothja
ms.author: jroth
ms.openlocfilehash: a4a2397668ed08df91377cc35dea22fd52788580
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588430"
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a><span data-ttu-id="10464-102">使用 Updategram 修改 SQLXML 4.0 中的数据</span><span class="sxs-lookup"><span data-stu-id="10464-102">Using Updategrams to Modify Data in SQLXML 4.0</span></span>
  <span data-ttu-id="10464-103">您可以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 通过使用 UPDATEGRAM 或 OPENXML 函数，从现有的 XML 文档中修改) 中的数据库 (插入、更新或删除 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="10464-103">You can modify (insert, update, or delete) a database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from an existing XML document by using an updategram or the OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="10464-104">本节提供有关 updategram 的信息及其使用示例。</span><span class="sxs-lookup"><span data-stu-id="10464-104">This section provides information about updategrams and examples of their usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10464-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="10464-105">In This Section</span></span>  
 [<span data-ttu-id="10464-106">SQLXML 4.0 &#40;Updategram 简介&#41;</span><span class="sxs-lookup"><span data-stu-id="10464-106">Introduction to Updategrams &#40;SQLXML 4.0&#41;</span></span>](introduction-to-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="10464-107">提供 updategram 的基本信息和示例。</span><span class="sxs-lookup"><span data-stu-id="10464-107">Provides basic information and examples of updategrams.</span></span>  
  
 [<span data-ttu-id="10464-108">在 Updategram 中指定带批注的映射架构 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="10464-108">Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;</span></span>](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 <span data-ttu-id="10464-109">说明 updategram 中带批注的映射架构并提供有关示例。</span><span class="sxs-lookup"><span data-stu-id="10464-109">Explains and provides examples of annotated mapping schemas in updategrams.</span></span>  
  
 [<span data-ttu-id="10464-110">SQLXML 4.0 &#40;的 NULL 处理&#41;</span><span class="sxs-lookup"><span data-stu-id="10464-110">NULL Handling &#40;SQLXML 4.0&#41;</span></span>](null-handling-sqlxml-4-0.md)  
 <span data-ttu-id="10464-111">说明如何为元素和属性值指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="10464-111">Describes how to specify NULL for element and attribute values.</span></span>  
  
 [<span data-ttu-id="10464-112">使用 XML Updategram 插入数据 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="10464-112">Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="10464-113">说明如何使用 updategram 插入数据并提供有关示例。</span><span class="sxs-lookup"><span data-stu-id="10464-113">Describes and provides examples of using updategrams to insert data.</span></span>  
  
 [<span data-ttu-id="10464-114">使用 XML Updategram 删除数据 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="10464-114">Deleting Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="10464-115">说明如何使用 updategram 删除数据并提供有关示例。</span><span class="sxs-lookup"><span data-stu-id="10464-115">Describes and provides examples of using updategrams to delete data.</span></span>  
  
 [<span data-ttu-id="10464-116">使用 XML Updategram 更新数据 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="10464-116">Updating Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="10464-117">说明如何使用 updategram 修改现有数据并提供有关示例。</span><span class="sxs-lookup"><span data-stu-id="10464-117">Describes and provides examples of using updategrams to modify existing data.</span></span>  
  
 [<span data-ttu-id="10464-118">将参数传递给 Updategram &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="10464-118">Passing Parameters to Updategrams &#40;SQLXML 4.0&#41;</span></span>](passing-parameters-to-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="10464-119">说明如何将参数传递到 updategram 并提供有关示例。</span><span class="sxs-lookup"><span data-stu-id="10464-119">Describes and provides examples of passing parameters to updategrams.</span></span>  
  
 [<span data-ttu-id="10464-120">处理 Updategram 中的数据库并发问题 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="10464-120">Handling Database Concurrency Issues in Updategrams &#40;SQLXML 4.0&#41;</span></span>](handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="10464-121">说明为处理 updategram 中的并发问题可能采取的不同层级的保护并且提供有关示例。</span><span class="sxs-lookup"><span data-stu-id="10464-121">Describes the various levels of protection possible for handling concurrency issues in updategrams, and provides examples.</span></span>  
  
 [<span data-ttu-id="10464-122">SQLXML 4.0 &#40;Updategram 示例应用程序&#41;</span><span class="sxs-lookup"><span data-stu-id="10464-122">Updategram Sample Applications &#40;SQLXML 4.0&#41;</span></span>](../../../database-engine/dev-guide/updategram-sample-applications-sqlxml-4-0.md)  
 <span data-ttu-id="10464-123">提供使用 updategram 的示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="10464-123">Provides sample applications that use updategrams.</span></span>  
  
 [<span data-ttu-id="10464-124">XML Updategram &#40;SQLXML 4.0&#41;的准则和限制</span><span class="sxs-lookup"><span data-stu-id="10464-124">Guidelines and Limitations of XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="10464-125">列出使用 updategram 时应注意的一些事项。</span><span class="sxs-lookup"><span data-stu-id="10464-125">Lists some things to remember when working with updategrams.</span></span>  
  
  
