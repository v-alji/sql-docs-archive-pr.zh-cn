---
title: SQLXML 托管类 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: rothja
ms.author: jroth
ms.openlocfilehash: bb8d2d4f2d2fc512901e4ad37f0e46cf696b9475
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576601"
---
# <a name="sqlxml-managed-classes"></a><span data-ttu-id="81d39-102">SQLXML 托管类</span><span class="sxs-lookup"><span data-stu-id="81d39-102">SQLXML Managed Classes</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="81d39-103">SQLXML 托管类在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 中公开 SQLXML 4.0 的功能。</span><span class="sxs-lookup"><span data-stu-id="81d39-103">SQLXML Managed Classes exposes the functionality of SQLXML 4.0 inside the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="81d39-104">利用 SQLXML 托管类，您可以编写 C# 应用程序，以便访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例中的 XML 数据，将该数据载入 .NET Framework 环境并进行处理，然后将更新作为 DiffGram 发回 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以应用此更新。</span><span class="sxs-lookup"><span data-stu-id="81d39-104">With SQLXML Managed Classes, you can write a C# application to access XML data from an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], bring the data into the .NET Framework environment, process the data, and send the updates back to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as a DiffGram to apply the updates.</span></span> <span data-ttu-id="81d39-105">使用 SQLXML 托管类向 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库应用更新时必须使用映射架构。</span><span class="sxs-lookup"><span data-stu-id="81d39-105">You must use a mapping schema when applying updates to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database using SQLXML Managed Classes.</span></span> <span data-ttu-id="81d39-106">有关工作示例，请参阅[在 .Net 环境中访问 SQLXML 功能](accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="81d39-106">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="81d39-107">若要配合使用 SQLXML 托管类和 SQLXML 4.0，必须安装 Microsoft Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="81d39-107">To use the SQLXML Managed Classes with SQLXML 4.0, you must install Microsoft Visual Studio.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81d39-108">.NET Framework 包括 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET 数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="81d39-108">The .NET Framework includes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET Data Provider.</span></span> <span data-ttu-id="81d39-109">该访问接口可用于从 .NET 环境访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]；但是，它只能处理传统 SQL 查询（即除 FOR XML 查询以外的关系数据库查询）。</span><span class="sxs-lookup"><span data-stu-id="81d39-109">This provider can be used to access [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from the .NET environment; however, it can handle only traditional SQL queries (that is, relational database queries with the exception of FOR XML queries).</span></span> <span data-ttu-id="81d39-110">您不能在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中执行 XML 模板或服务器端 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="81d39-110">You cannot execute XML templates or the server-side XPath queries in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81d39-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="81d39-111">In This Section</span></span>  
 [<span data-ttu-id="81d39-112">SQLXML 托管类对象模型</span><span class="sxs-lookup"><span data-stu-id="81d39-112">SQLXML Managed Classes Object Model</span></span>](../../../database-engine/dev-guide/sqlxml-managed-classes-object-model.md)  
 <span data-ttu-id="81d39-113">记录 SQLXML 托管类及其属性和方法。</span><span class="sxs-lookup"><span data-stu-id="81d39-113">Documents SQLXML Managed Classes and their properties and methods.</span></span>  
  
 [<span data-ttu-id="81d39-114">使用 SQLXML 托管类</span><span class="sxs-lookup"><span data-stu-id="81d39-114">Using the SQLXML Managed Classes</span></span>](sqlxml-4-0-net-framework-support-managed-classes.md)  
 <span data-ttu-id="81d39-115">提供使用 SQLXML 托管类的示例。</span><span class="sxs-lookup"><span data-stu-id="81d39-115">Provides examples of using SQLXML Managed Classes.</span></span>  
  
  
