---
title: 删除以保留日期和时间数据类型命名的 UDT&#39;Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 827f060b309a7a620fd448554b074f45d78d3cb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588843"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a><span data-ttu-id="e6601-102">删除以保留日期和时间数据类型命名的 UDT&#39;</span><span class="sxs-lookup"><span data-stu-id="e6601-102">Remove UDT&#39;s named after the reserved DATE and TIME data types</span></span>
  <span data-ttu-id="e6601-103">升级顾问检测到根据为 `date` 或 `time` 数据类型保留的术语命名的用户定义类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="e6601-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for either the `date` or the `time` data types.</span></span>  
  
## <a name="component"></a><span data-ttu-id="e6601-104">组件</span><span class="sxs-lookup"><span data-stu-id="e6601-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="e6601-105">说明</span><span class="sxs-lookup"><span data-stu-id="e6601-105">Description</span></span>  
 <span data-ttu-id="e6601-106">用于数据类型的术语不应用作公共语言运行时 (CLR) 或别名 UDT 的名称。</span><span class="sxs-lookup"><span data-stu-id="e6601-106">The terms used for data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="e6601-107">纠正措施</span><span class="sxs-lookup"><span data-stu-id="e6601-107">Corrective Action</span></span>  
 <span data-ttu-id="e6601-108">删除根据数据类型命名的 UDT，并使用非保留名称重新创建 UDT。</span><span class="sxs-lookup"><span data-stu-id="e6601-108">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
  
