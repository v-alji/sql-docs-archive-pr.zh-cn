---
title: 服务器配置-排序规则 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- collation configuration, SQL Server
- collation configuration, Setup
- collation configuration
ms.assetid: e3986870-5be4-458b-b671-5ff12a27b022
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d06735590d23da6e91151202dd421639ea433b97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588828"
---
# <a name="server-configuration---collation"></a><span data-ttu-id="ce425-102">服务器配置 - 排序规则</span><span class="sxs-lookup"><span data-stu-id="ce425-102">Server Configuration - Collation</span></span>
  <span data-ttu-id="ce425-103">可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导的“服务器配置 – 排序规则”页上修改 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 排序时所用的排序规则设置。</span><span class="sxs-lookup"><span data-stu-id="ce425-103">On the Server Configuration - Collation page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard, you can modify collation settings that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] use for sorting purposes.</span></span> <span data-ttu-id="ce425-104">选择相应选项以匹配其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安装或者其他计算机的排序规则设置。</span><span class="sxs-lookup"><span data-stu-id="ce425-104">Select the option to match collation settings of different installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or of another computer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ce425-105">选项</span><span class="sxs-lookup"><span data-stu-id="ce425-105">Options</span></span>  
 <span data-ttu-id="ce425-106">为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 进行自定义</span><span class="sxs-lookup"><span data-stu-id="ce425-106">Customize for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ce425-107">提供了两组排序规则：Windows 排序规则和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 排序规则。</span><span class="sxs-lookup"><span data-stu-id="ce425-107">provides two groups of collations: Windows collations and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span> <span data-ttu-id="ce425-108">您可以为 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]指定不同的排序规则设置，也可以为它们指定相同的排序规则。</span><span class="sxs-lookup"><span data-stu-id="ce425-108">You can specify separate collation settings for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], or you can specify the same collation for both.</span></span>  
  
 <span data-ttu-id="ce425-109">默认情况下，对于美国英语系统区域设置，选择的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 排序规则。</span><span class="sxs-lookup"><span data-stu-id="ce425-109">By default, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collation is selected for US-English system locales.</span></span> <span data-ttu-id="ce425-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本地化版本的默认排序规则由您的计算机的 Windows 系统区域设置决定。</span><span class="sxs-lookup"><span data-stu-id="ce425-110">The default collation for localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is determined by the Windows system locale setting for your computer.</span></span>  
  
 <span data-ttu-id="ce425-111">仅当此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的排序规则设置必须与另一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例所用的排序规则设置相匹配，或者必须与另一台计算机的 Windows 系统区域设置相匹配时，才应更改默认设置。</span><span class="sxs-lookup"><span data-stu-id="ce425-111">The default settings should be changed only if the collation setting for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must match the collation settings used by another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or if it must match the Windows system locale of another computer.</span></span>  
  
 <span data-ttu-id="ce425-112">**注意** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 仅使用 Windows 排序规则。</span><span class="sxs-lookup"><span data-stu-id="ce425-112">**Note** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses Windows collations only.</span></span> <span data-ttu-id="ce425-113">如果计划安装 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，请在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装期间，选择 Windows 排序规则，以确保 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]之间结果的一致性。</span><span class="sxs-lookup"><span data-stu-id="ce425-113">If you plan to install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], select a Windows collation during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to ensure consistent results between the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ce425-114">有关详细信息，请参阅 [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977)（安装程序中的排序规则设置）。</span><span class="sxs-lookup"><span data-stu-id="ce425-114">For more information, see [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="ce425-115">最佳方案</span><span class="sxs-lookup"><span data-stu-id="ce425-115">Best Practices</span></span>  
 <span data-ttu-id="ce425-116">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序使用的 Windows 系统区域设置以及相应的默认排序规则的表的详细信息，请参阅 [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977)（安装程序中的排序规则设置）。</span><span class="sxs-lookup"><span data-stu-id="ce425-116">For more information about a table of Windows System locales and the corresponding default collations used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, see [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977).</span></span>  
  
 <span data-ttu-id="ce425-117">如果可能，请为您的组织使用一个排序规则。</span><span class="sxs-lookup"><span data-stu-id="ce425-117">If it is possible, use a single collation for your organization.</span></span> <span data-ttu-id="ce425-118">这样就不必为每个数据库、列、表达式或标识符显式指定排序规则。</span><span class="sxs-lookup"><span data-stu-id="ce425-118">This way, you do not have to explicitly specify the collation for every database, column, expression, or identifier.</span></span> <span data-ttu-id="ce425-119">如果必须使用多个排序规则和代码页设置，请对查询进行编码，以考虑排序规则优先顺序规则。</span><span class="sxs-lookup"><span data-stu-id="ce425-119">If you must work with multiple collations and code page settings, code your queries to consider the rules of collation precedence.</span></span> <span data-ttu-id="ce425-120">有关详细信息，请参阅联机丛书主题中的[排序规则优先级 (Transact-SQL)](/sql/t-sql/statements/collation-precedence-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ce425-120">For more information, see the Books Online topic for [Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql).</span></span>  
  
 <span data-ttu-id="ce425-121">为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 选择排序规则时，请考虑下列建议：</span><span class="sxs-lookup"><span data-stu-id="ce425-121">When you select a collation for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consider the following recommendations:</span></span>  
  
-   <span data-ttu-id="ce425-122">如果基于二进制码位的排序顺序可接受，请选择 BINARY2 排序规则。</span><span class="sxs-lookup"><span data-stu-id="ce425-122">Select a BINARY2 collation if binary code point based ordering is acceptable.</span></span>  
  
-   <span data-ttu-id="ce425-123">选择 Windows 排序规则以便在各数据类型之间进行一致的比较。</span><span class="sxs-lookup"><span data-stu-id="ce425-123">Select a Windows collation for consistent comparison across data types.</span></span>  
  
-   <span data-ttu-id="ce425-124">使用新的 100 级排序规则以便获得更好的语言排序支持。</span><span class="sxs-lookup"><span data-stu-id="ce425-124">Use a new 100-level collation for better linguistic sorting support.</span></span> <span data-ttu-id="ce425-125">有关详细信息，请参阅 [排序规则和 Unicode 支持](../../relational-databases/collations/collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="ce425-125">For more information, see [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="ce425-126">如果您计划将数据库迁移到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的升级实例，则选择与您的数据库的现有排序规则匹配的排序规则。</span><span class="sxs-lookup"><span data-stu-id="ce425-126">If you plan to migrate a database to the upgraded instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select the collation that matches your existing collation of the database.</span></span>  
  
  
