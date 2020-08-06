---
title: 全文目录名称的长度限制为120个字符 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fa9b06fa6fe4acd79782c19a8814357721e59c24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591730"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a><span data-ttu-id="3efda-102">全文目录名称的长度不能超过 120 个字符</span><span class="sxs-lookup"><span data-stu-id="3efda-102">Length of full-text catalog names restricted to 120 characters</span></span>
  <span data-ttu-id="3efda-103">全文目录名称的最大长度均不能超过 120 个字符，与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以前版本中的 128 个字符限制相比有所减少。</span><span class="sxs-lookup"><span data-stu-id="3efda-103">The length of full-text catalog names is restricted to 120 characters, reduced from the 128 character restriction in previous releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="description"></a><span data-ttu-id="3efda-104">说明</span><span class="sxs-lookup"><span data-stu-id="3efda-104">Description</span></span>  
 <span data-ttu-id="3efda-105">此更改不会影响现有的目录名称，但是如果脚本创建的全文目录的名称长度超过 120 个字符，则会导致错误。</span><span class="sxs-lookup"><span data-stu-id="3efda-105">This change does not affect existing catalog names; however, scripts that create full-text catalogs with names longer than 120 characters result in an error.</span></span> <span data-ttu-id="3efda-106">目录名称用于生成与目录对应的逻辑文件名。</span><span class="sxs-lookup"><span data-stu-id="3efda-106">The catalog names are used to generate logical file names that correspond to catalogs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="3efda-107">纠正措施</span><span class="sxs-lookup"><span data-stu-id="3efda-107">Corrective Action</span></span>  
 <span data-ttu-id="3efda-108">修改所有创建全文目录的脚本，以确保目录名称的长度不超过 120 个字符。</span><span class="sxs-lookup"><span data-stu-id="3efda-108">Modify all scripts that create full-text catalogs to ensure that they restrict catalog names to 120 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3efda-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3efda-109">See Also</span></span>  
 [<span data-ttu-id="3efda-110">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="3efda-110">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
