---
title: 删除以保留 ORDPATH 数据类型命名的 UDT&#39;Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0528d19de17781d863e3a42fdef7db558fe5d190
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694239"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a><span data-ttu-id="77335-102">删除以保留 ORDPATH 数据类型命名的 UDT&#39;</span><span class="sxs-lookup"><span data-stu-id="77335-102">Remove UDT&#39;s named after the reserved ORDPATH data type</span></span>
  <span data-ttu-id="77335-103">升级顾问检测到根据为 `ORDPATH` 数据类型保留的术语命名的用户定义类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="77335-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for the `ORDPATH` data type.</span></span>  
  
## <a name="component"></a><span data-ttu-id="77335-104">组件</span><span class="sxs-lookup"><span data-stu-id="77335-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="77335-105">说明</span><span class="sxs-lookup"><span data-stu-id="77335-105">Description</span></span>  
 <span data-ttu-id="77335-106">用于内置数据类型的术语不应用作公共语言运行时 (CLR) 或别名 UDT 的名称。</span><span class="sxs-lookup"><span data-stu-id="77335-106">The terms used for built-in data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="77335-107">纠正措施</span><span class="sxs-lookup"><span data-stu-id="77335-107">Corrective Action</span></span>  
 <span data-ttu-id="77335-108">删除根据数据类型命名的 UDT，并使用非保留名称重新创建 UDT。</span><span class="sxs-lookup"><span data-stu-id="77335-108">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="77335-109">外部资源</span><span class="sxs-lookup"><span data-stu-id="77335-109">External Resources</span></span>  
 [<span data-ttu-id="77335-110">创建用户定义类型</span><span class="sxs-lookup"><span data-stu-id="77335-110">Creating a User-Defined Type</span></span>](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
