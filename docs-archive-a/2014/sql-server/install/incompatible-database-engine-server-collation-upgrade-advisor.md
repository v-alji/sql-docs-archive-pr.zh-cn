---
title: 升级顾问) 数据库引擎服务器排序规则不兼容 (|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b6ce0555bdf5a878e56d87a8bd55b5ce6c4b2649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590528"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a><span data-ttu-id="c42c3-102">不兼容的数据库引擎服务器排序规则（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="c42c3-102">Incompatible Database Engine Server Collation (Upgrade Advisor)</span></span>
  <span data-ttu-id="c42c3-103">升级顾问检测到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 配置为使用不兼容的服务器排序规则。</span><span class="sxs-lookup"><span data-stu-id="c42c3-103">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is using an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that is configured to use an incompatible server collation.</span></span>  
  
||  
|-|  
|<span data-ttu-id="c42c3-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="c42c3-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="c42c3-105">组件</span><span class="sxs-lookup"><span data-stu-id="c42c3-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c42c3-106">说明</span><span class="sxs-lookup"><span data-stu-id="c42c3-106">Description</span></span>  
 <span data-ttu-id="c42c3-107">升级顾问检测到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 配置为使用不兼容的服务器排序规则。</span><span class="sxs-lookup"><span data-stu-id="c42c3-107">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is using an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that is configured to use an incompatible server collation.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="c42c3-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sharepoint 模式利用 sharepoint 共享服务体系结构。</span><span class="sxs-lookup"><span data-stu-id="c42c3-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode utilizes the SharePoint shared services architecture.</span></span> <span data-ttu-id="c42c3-109">SharePoint 不支持为区分大小写的服务器排序规则或二进制排序规则配置的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c42c3-109">SharePoint does not support [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] configured for case sensitive or server collations or binary server collations.</span></span> <span data-ttu-id="c42c3-110">不兼容的排序规则包括默认区分大小写或为二进制的排序规则，以及默认兼容但使用任何以下排序规则指示符配置的基本排序规则：</span><span class="sxs-lookup"><span data-stu-id="c42c3-110">Incompatible collations include collations that are by default case sensitive or binary and a base collation that by default is compatible but has been configured with any of the following collation designators:</span></span>  
  
-   <span data-ttu-id="c42c3-111">**二进制**</span><span class="sxs-lookup"><span data-stu-id="c42c3-111">**Binary**</span></span>  
  
-   <span data-ttu-id="c42c3-112">**区分大小写**</span><span class="sxs-lookup"><span data-stu-id="c42c3-112">**Case-sensitive**</span></span>  
  
-   <span data-ttu-id="c42c3-113">**二进制-码位**</span><span class="sxs-lookup"><span data-stu-id="c42c3-113">**Binary-codepoint**</span></span>  
  
 <span data-ttu-id="c42c3-114">因为当前 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服务器排序规则不兼容，所以升级被阻止。</span><span class="sxs-lookup"><span data-stu-id="c42c3-114">Because the current [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] server collation is incompatible, upgrade is blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c42c3-115">纠正措施</span><span class="sxs-lookup"><span data-stu-id="c42c3-115">Corrective Action</span></span>  
 <span data-ttu-id="c42c3-116">不能更改 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服务器排序规则属性。</span><span class="sxs-lookup"><span data-stu-id="c42c3-116">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] server collation property cannot be changed.</span></span> <span data-ttu-id="c42c3-117">您将不能完成 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的升级。</span><span class="sxs-lookup"><span data-stu-id="c42c3-117">You will not be able to complete an upgrade of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="c42c3-118">您将需要将您的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装迁移到正在使用兼容的服务器排序规则的新服务器。</span><span class="sxs-lookup"><span data-stu-id="c42c3-118">You will need to migrate your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a new server which is using a compatible server collation.</span></span> <span data-ttu-id="c42c3-119">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="c42c3-119">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="c42c3-120">升级和迁移 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="c42c3-120">Upgrade and Migrate Reporting Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [<span data-ttu-id="c42c3-121">选择 SQL Server 排序规则</span><span class="sxs-lookup"><span data-stu-id="c42c3-121">Selecting a SQL Server Collation</span></span>](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
