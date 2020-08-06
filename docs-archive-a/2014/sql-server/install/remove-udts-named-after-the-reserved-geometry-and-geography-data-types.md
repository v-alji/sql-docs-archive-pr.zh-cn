---
title: 删除以保留的 GEOMETRY 和 GEOGRAPHY 数据类型命名的 Udt |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4977d45d53e1114edc8e04ad504963bae0b9eb9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694238"
---
# <a name="remove-udts-named-after-the-reserved-geometry-and-geography-data-types"></a><span data-ttu-id="40154-102">删除根据保留的 GEOMETRY 和 GEOGRAPHY 数据类型命名的 UDT</span><span class="sxs-lookup"><span data-stu-id="40154-102">Remove UDTs named after the reserved GEOMETRY and GEOGRAPHY data types</span></span>
  <span data-ttu-id="40154-103">升级顾问检测到根据为 `geometry` 或 `geography` 数据类型保留的术语命名的用户定义类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="40154-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for either the `geometry` or the `geography` data types.</span></span> <span data-ttu-id="40154-104">`geometry` 和 `geography` 数据类型是空间数据功能的一部分。</span><span class="sxs-lookup"><span data-stu-id="40154-104">The `geometry` and `geography` data types are part of the spatial data feature.</span></span>  
  
## <a name="component"></a><span data-ttu-id="40154-105">组件</span><span class="sxs-lookup"><span data-stu-id="40154-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="40154-106">说明</span><span class="sxs-lookup"><span data-stu-id="40154-106">Description</span></span>  
 <span data-ttu-id="40154-107">用于空间数据类型的术语不应用作公共语言运行时 (CLR) 或别名 UDT 的名称。</span><span class="sxs-lookup"><span data-stu-id="40154-107">The terms used for spatial data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="40154-108">纠正措施</span><span class="sxs-lookup"><span data-stu-id="40154-108">Corrective Action</span></span>  
 <span data-ttu-id="40154-109">删除根据数据类型命名的 UDT，并使用非保留名称重新创建 UDT。</span><span class="sxs-lookup"><span data-stu-id="40154-109">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="40154-110">外部资源</span><span class="sxs-lookup"><span data-stu-id="40154-110">External Resources</span></span>  
 [<span data-ttu-id="40154-111">创建用户定义类型</span><span class="sxs-lookup"><span data-stu-id="40154-111">Creating a User-Defined Type</span></span>](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [<span data-ttu-id="40154-112">空间数据类型概述</span><span class="sxs-lookup"><span data-stu-id="40154-112">Spatial Data Types Overview</span></span>](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
