---
title: 将 PAGE_VERIFY 数据库选项设置为 CHECKSUM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13296a976722390668b8ca6d901cf0dd080e5cc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693256"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a><span data-ttu-id="236c6-102">将 PAGE_VERIFY 数据库选项设置为 CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="236c6-102">Set the PAGE_VERIFY Database Option to CHECKSUM</span></span>
  <span data-ttu-id="236c6-103">此规则检查 PAGE_VERIFY 数据库选项是否已设置为 CHECKSUM。</span><span class="sxs-lookup"><span data-stu-id="236c6-103">This rule checks whether PAGE_VERIFY database option is set to CHECKSUM.</span></span> <span data-ttu-id="236c6-104">为 PAGE_VERIFY 数据库选项启用 CHECKSUM 后， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 会在向磁盘中写入页面时计算整个页面内容的校验并将该值存储在页头中。</span><span class="sxs-lookup"><span data-stu-id="236c6-104">When CHECKSUM is enabled for the PAGE_VERIFY database option, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calculates a checksum over the contents of the whole page, and stores the value in the page header when a page is written to disk.</span></span> <span data-ttu-id="236c6-105">从磁盘中读取页时，将重新计算校验和，并与存储在页头中的校验和值进行比较。</span><span class="sxs-lookup"><span data-stu-id="236c6-105">When the page is read from disk, the checksum is recomputed and compared to the checksum value that is stored in the page header.</span></span> <span data-ttu-id="236c6-106">这有助于提供高级别的数据文件完整性。</span><span class="sxs-lookup"><span data-stu-id="236c6-106">This helps provide a high level of data-file integrity.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="236c6-107">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="236c6-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="236c6-108">将 PAGE_VERIFY 数据库选项设置为 CHECKSUM。</span><span class="sxs-lookup"><span data-stu-id="236c6-108">Set the PAGE_VERIFY database option to CHECKSUM.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="236c6-109">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="236c6-109">For More Information</span></span>  
 [<span data-ttu-id="236c6-110">ALTER DATABASE SET 选项 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="236c6-110">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
