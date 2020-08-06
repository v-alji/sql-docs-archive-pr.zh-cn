---
title: SQLXML 中 Diffgram 的准则和限制 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f2901f02f8b4a8fc7b77dcb6c1cb166cb6af6ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587300"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a><span data-ttu-id="265b4-102">SQLXML 中 DiffGram 的准则和限制</span><span class="sxs-lookup"><span data-stu-id="265b4-102">Guidelines and Limitations of DiffGrams in SQLXML</span></span>
  <span data-ttu-id="265b4-103">通过 SQLXML 4.0 使用 DiffGram 时请记住以下事项：</span><span class="sxs-lookup"><span data-stu-id="265b4-103">Remember the following when using DiffGrams with SQLXML 4.0:</span></span>  
  
-   <span data-ttu-id="265b4-104">在使用 DiffGram 时，不应在 `text/ntext` 块中使用诸如 `<diffgr:before>` 和 image 的二进制大型对象 (BLOB) 类型，因为这将使它们用在并发控制中。</span><span class="sxs-lookup"><span data-stu-id="265b4-104">Binary large object (BLOB) types like `text/ntext` and images should not be used in the `<diffgr:before>` block in when working with DiffGrams, because this will include them for use in concurrency control.</span></span> <span data-ttu-id="265b4-105">由于 BLOB 类型的比较限制，这可能导致 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 出现问题。</span><span class="sxs-lookup"><span data-stu-id="265b4-105">This can cause problems with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="265b4-106">例如，在 WHERE 子句中使用 LIKE 关键字比较 `text` 数据类型的列；不过，对于数据大小大于 8K 的 BLOB 类型，比较将失败。</span><span class="sxs-lookup"><span data-stu-id="265b4-106">For example, the LIKE keyword is used in the WHERE clause for comparing between columns of the `text` data type; however, comparisons will fail in the case of BLOB types where the size of the data is greater than 8K.</span></span>  
  
-   <span data-ttu-id="265b4-107">由于 BLOB 类型的比较限制，`ntext` 数据中的特殊字符可能导致 SQLXML 4.0 出现问题。</span><span class="sxs-lookup"><span data-stu-id="265b4-107">Special characters in `ntext` data can cause problems with SQLXML 4.0 because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="265b4-108">例如，在对 `<diffgr:before>` 类型的列进行并发检查时，如果在 DiffGram 的 `ntext` 块中使用“[Serializable]”，检查将失败，并显示以下 SQLOLEDB 错误说明：</span><span class="sxs-lookup"><span data-stu-id="265b4-108">For example, the use of "[Serializable]" in the `<diffgr:before>` block of a DiffGram when used in concurrency checking of a column of `ntext` type will fail with the following SQLOLEDB error description:</span></span>  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
