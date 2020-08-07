---
title: " (SQLXML 4.0) 的 Updategram 安全注意事项 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
author: rothja
ms.author: jroth
ms.openlocfilehash: eb0319285e6e8cf6e8b3e70f3eb6b9923de06f55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589472"
---
# <a name="updategram-security-considerations-sqlxml-40"></a><span data-ttu-id="b26bd-102">updategram 的安全注意事项 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="b26bd-102">Updategram Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="b26bd-103">以下是使用 updategram 的安全准则：</span><span class="sxs-lookup"><span data-stu-id="b26bd-103">The following are security guidelines for using updategrams:</span></span>  
  
-   <span data-ttu-id="b26bd-104">使用 updategram 更新数据时，不要使用默认映射。</span><span class="sxs-lookup"><span data-stu-id="b26bd-104">Avoid using default mapping when you use updategrams to update data.</span></span> <span data-ttu-id="b26bd-105">如果使用默认映射，则 updategram 中的元素名称会映射到表名称，属性名称会映射到列。</span><span class="sxs-lookup"><span data-stu-id="b26bd-105">When you use default mapping, an element name in an updategram maps to a table name, and an attribute name maps to a column.</span></span> <span data-ttu-id="b26bd-106">这会公开数据库中的数据库表和列信息，从而可能成为潜在的安全隐患。</span><span class="sxs-lookup"><span data-stu-id="b26bd-106">This exposes the database table and column information in the database, which can be a potential security risk.</span></span> <span data-ttu-id="b26bd-107">相反，如果指定单独的映射架构将 updategram 中的元素和属性映射到数据库表和列，则 updategram 元素和属性名称可以为任意名称，且架构只在必要时才将这些名称映射到数据库表和列。</span><span class="sxs-lookup"><span data-stu-id="b26bd-107">Instead, if you specify a separate mapping schema that maps the elements and attributes in an updategram to the database tables and columns, your updategram element and attribute names can be arbitrary, and the schema does necessary mapping of these names to the database tables and columns.</span></span> <span data-ttu-id="b26bd-108">因此，数据库信息不会在 updategram 中公开。</span><span class="sxs-lookup"><span data-stu-id="b26bd-108">Thus, the database information is not exposed in an updategram.</span></span>  
  
-   <span data-ttu-id="b26bd-109">切勿允许用户创建和执行自己的 updategram。</span><span class="sxs-lookup"><span data-stu-id="b26bd-109">Do not allow users to create and execute their updategrams.</span></span> <span data-ttu-id="b26bd-110">建议将 updategram 作为模板驻留在服务器上，而不是在 ASP 类型应用程序中动态创建 updategram，因为这样可能会给数据库中的数据带来风险。</span><span class="sxs-lookup"><span data-stu-id="b26bd-110">It is recommended having updategrams reside as templates on a server rather than creating them dynamically in ASP-type applications, which could put the data in the database at risk.</span></span> <span data-ttu-id="b26bd-111">如果只允许用户通过作为模板提供的 updategram 访问数据，则可避免这种风险。</span><span class="sxs-lookup"><span data-stu-id="b26bd-111">Allowing users to access the data only through the updategrams provided as templates, can eliminate this risk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b26bd-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b26bd-112">See Also</span></span>  
 [<span data-ttu-id="b26bd-113">使用 Updategram 修改 SQLXML 4.0 中的数据</span><span class="sxs-lookup"><span data-stu-id="b26bd-113">Using Updategrams to Modify Data in SQLXML 4.0</span></span>](../updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  
