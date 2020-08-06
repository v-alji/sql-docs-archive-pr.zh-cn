---
title: 生成脚本向导支持的对象
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: rothja
ms.author: jroth
ms.openlocfilehash: 5ddc1da0d2f87fc12dfbe034a683802f54b7d34f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590160"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a><span data-ttu-id="127c0-102">生成脚本向导支持的对象</span><span class="sxs-lookup"><span data-stu-id="127c0-102">Objects Supported by the Generate Scripts Wizard</span></span>
  <span data-ttu-id="127c0-103">“生成和发布脚本向导”支持 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]所支持的对象的一个子集。</span><span class="sxs-lookup"><span data-stu-id="127c0-103">The Generate and Publish Scripts wizard supports a subset of the objects supported by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="supported-objects"></a><span data-ttu-id="127c0-104">支持的对象</span><span class="sxs-lookup"><span data-stu-id="127c0-104">Supported Objects</span></span>  
 <span data-ttu-id="127c0-105">下表列出“生成和发布脚本向导”支持的可发布对象。</span><span class="sxs-lookup"><span data-stu-id="127c0-105">The following table lists the objects that can be published supported by the Generate and Publish Scripts Wizard.</span></span>  
  
||||||  
|-|-|-|-|-|  
|<span data-ttu-id="127c0-106">应用程序角色</span><span class="sxs-lookup"><span data-stu-id="127c0-106">Application role</span></span>|<span data-ttu-id="127c0-107">数据库角色</span><span class="sxs-lookup"><span data-stu-id="127c0-107">Database role</span></span>|<span data-ttu-id="127c0-108">架构</span><span class="sxs-lookup"><span data-stu-id="127c0-108">Schema</span></span>|<span data-ttu-id="127c0-109">用户定义聚合</span><span class="sxs-lookup"><span data-stu-id="127c0-109">User-defined aggregate</span></span>|<span data-ttu-id="127c0-110">查看<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="127c0-110">View<sup>1</sup></span></span>|  
|<span data-ttu-id="127c0-111">Assembly</span><span class="sxs-lookup"><span data-stu-id="127c0-111">Assembly</span></span>|<span data-ttu-id="127c0-112">DEFAULT 约束</span><span class="sxs-lookup"><span data-stu-id="127c0-112">DEFAULT constraint</span></span>|<span data-ttu-id="127c0-113">存储过程<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="127c0-113">Stored procedure<sup>1</sup></span></span>|<span data-ttu-id="127c0-114">用户定义数据类型</span><span class="sxs-lookup"><span data-stu-id="127c0-114">User-defined data type</span></span>|<span data-ttu-id="127c0-115">XML 架构集合</span><span class="sxs-lookup"><span data-stu-id="127c0-115">XML schema collection</span></span>|  
|<span data-ttu-id="127c0-116">CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="127c0-116">CHECK constraint</span></span>|<span data-ttu-id="127c0-117">全文目录</span><span class="sxs-lookup"><span data-stu-id="127c0-117">Full-text catalog</span></span>|<span data-ttu-id="127c0-118">同义词</span><span class="sxs-lookup"><span data-stu-id="127c0-118">Synonym</span></span>|<span data-ttu-id="127c0-119">用户定义函数</span><span class="sxs-lookup"><span data-stu-id="127c0-119">User-defined function</span></span>||  
|<span data-ttu-id="127c0-120">CLR (公共语言运行时) 存储过程<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="127c0-120">CLR (common language runtime) stored procedure<sup>1</sup></span></span>|<span data-ttu-id="127c0-121">索引</span><span class="sxs-lookup"><span data-stu-id="127c0-121">Index</span></span>|<span data-ttu-id="127c0-122">表</span><span class="sxs-lookup"><span data-stu-id="127c0-122">Table</span></span>|<span data-ttu-id="127c0-123">用户定义表</span><span class="sxs-lookup"><span data-stu-id="127c0-123">User-defined table</span></span>||  
|<span data-ttu-id="127c0-124">CLR 用户定义函数</span><span class="sxs-lookup"><span data-stu-id="127c0-124">CLR user-defined function</span></span>|<span data-ttu-id="127c0-125">规则</span><span class="sxs-lookup"><span data-stu-id="127c0-125">Rule</span></span>|<span data-ttu-id="127c0-126">用户<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="127c0-126">User<sup>2</sup></span></span>|<span data-ttu-id="127c0-127">用户定义类型</span><span class="sxs-lookup"><span data-stu-id="127c0-127">User-defined type</span></span>||  
  
 <span data-ttu-id="127c0-128"><sup>1</sup>发布但未加密。</span><span class="sxs-lookup"><span data-stu-id="127c0-128"><sup>1</sup> Published without encryption.</span></span>  
  
 <span data-ttu-id="127c0-129"><sup>2</sup>数据库中存在的任何非系统用户将作为角色发布。</span><span class="sxs-lookup"><span data-stu-id="127c0-129"><sup>2</sup> Any non-system users that exist in the database are published as Roles.</span></span>  
  
  
