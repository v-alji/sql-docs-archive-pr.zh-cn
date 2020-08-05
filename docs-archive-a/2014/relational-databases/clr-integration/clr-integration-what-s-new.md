---
title: CLR 集成中的新增&#39;Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: b51eb5d8bee5ff8e514f294d5e9facca93a30bfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581314"
---
# <a name="what39s-new-in-clr-integration"></a><span data-ttu-id="b0f96-102">CLR 集成中的新增功能&#39;</span><span class="sxs-lookup"><span data-stu-id="b0f96-102">What&#39;s New in CLR Integration</span></span>
  <span data-ttu-id="b0f96-103">以下是 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中 CLR 集成的新功能：</span><span class="sxs-lookup"><span data-stu-id="b0f96-103">The following are new features in CLR integration in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:</span></span>  
  
-   <span data-ttu-id="b0f96-104">在 CLR 版本 4 中，CLR 数据库对象不再捕获损坏的状态异常。</span><span class="sxs-lookup"><span data-stu-id="b0f96-104">In version 4 of the CLR, CLR database objects no longer catch corrupted state exceptions.</span></span> <span data-ttu-id="b0f96-105">这些异常现在在 CLR 集成承载层中捕获。</span><span class="sxs-lookup"><span data-stu-id="b0f96-105">These exceptions are now caught in the CLR integration hosting layer.</span></span> <span data-ttu-id="b0f96-106">CLR 数据库组件仍可以通过将代码特性设置 ([ \<legacyCorruptedStateExceptionsPolicy> 元素](https://go.microsoft.com/fwlink/?LinkId=204954)) 来捕获这些异常。</span><span class="sxs-lookup"><span data-stu-id="b0f96-106">These exceptions can still be caught by the CLR database components by setting a code attribute ([\<legacyCorruptedStateExceptionsPolicy> Element](https://go.microsoft.com/fwlink/?LinkId=204954)).</span></span> <span data-ttu-id="b0f96-107">但是，我们建议不要这样做，因为损坏的状态异常发生时结果不可靠。</span><span class="sxs-lookup"><span data-stu-id="b0f96-107">However, this is not recommended because results are not reliable when a corrupted state exception occurs.</span></span>  
  
-   <span data-ttu-id="b0f96-108">由于 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 的严格安全要求，CLR 数据库组件将继续使用 CLR 版本 2.0 中定义的代码访问安全性模型。</span><span class="sxs-lookup"><span data-stu-id="b0f96-108">Due to the strict security requirements of [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], CLR database components will continue to use the Code Access Security model defined in CLR version 2.0.</span></span>  
  
-   <span data-ttu-id="b0f96-109">在 CLR 版本 4 中，`System.TimeSpan` 值中的格式错误将生成 `System.FormatExceptions`。</span><span class="sxs-lookup"><span data-stu-id="b0f96-109">In CLR version 4, a format error in a `System.TimeSpan` value will generate a `System.FormatExceptions`.</span></span> <span data-ttu-id="b0f96-110">在 CLR 版本 4 之前，忽略 `System.TimeSpan` 值中的格式错误。</span><span class="sxs-lookup"><span data-stu-id="b0f96-110">Prior to version 4 of the CLR, a format error in a `System.TimeSpan` value was ignored.</span></span> <span data-ttu-id="b0f96-111">依赖于 CLR 版本 4 之前的行为的数据库应用程序应使用数据库兼容级别 (`ALTER DATABASE Compatibility Level`) 100 或更低来运行。</span><span class="sxs-lookup"><span data-stu-id="b0f96-111">Database applications that rely on the behavior prior to version 4 of the CLR should run with a database compatibility level (`ALTER DATABASE Compatibility Level`) of 100 or lower.</span></span> <span data-ttu-id="b0f96-112">有关详细信息，请参阅[<TimeSpan_LegacyFormatMode> 元素](https://go.microsoft.com/fwlink/?LinkId=205109)。</span><span class="sxs-lookup"><span data-stu-id="b0f96-112">For more information, see [<TimeSpan_LegacyFormatMode> Element](https://go.microsoft.com/fwlink/?LinkId=205109).</span></span>  
  
-   <span data-ttu-id="b0f96-113">版本 4 的 CLR 支持 Unicode 5.1。</span><span class="sxs-lookup"><span data-stu-id="b0f96-113">Version 4 of the CLR supports Unicode 5.1.</span></span> <span data-ttu-id="b0f96-114">将会改善涉及一些重音记号和符号的排序操作。</span><span class="sxs-lookup"><span data-stu-id="b0f96-114">Sort operations involving some accent marks and symbols will be improved.</span></span> <span data-ttu-id="b0f96-115">如果您的应用程序依赖于旧的排序行为，可能会出现兼容性问题。</span><span class="sxs-lookup"><span data-stu-id="b0f96-115">Compatibility problems may occur if your application relies on legacy sorting behavior.</span></span> <span data-ttu-id="b0f96-116">若要启用旧的排序，必须将数据库兼容级别 (`ALTER DATABASE Compatibility Level`) 设置为 100 或更低。</span><span class="sxs-lookup"><span data-stu-id="b0f96-116">To enable legacy sorting, the database compatibility level (`ALTER DATABASE Compatibility Level`) must be set to 100 or lower.</span></span> <span data-ttu-id="b0f96-117">为此，[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 将在 .NET Framework 4 目录 (C:\Windows\Microsoft.NET\Framework\v4.0.30319) 中安装 sort00001000.dll。</span><span class="sxs-lookup"><span data-stu-id="b0f96-117">To support this, [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] will install sort00001000.dll in the .NET Framework 4 directory (C:\Windows\Microsoft.NET\Framework\v4.0.30319).</span></span> <span data-ttu-id="b0f96-118">有关详细信息，请参阅 [\<CompatSortNLSVersion> 元素](https://go.microsoft.com/fwlink/?LinkId=205110)。</span><span class="sxs-lookup"><span data-stu-id="b0f96-118">For more information, see [\<CompatSortNLSVersion> Element](https://go.microsoft.com/fwlink/?LinkId=205110).</span></span>  
  
-   <span data-ttu-id="b0f96-119">以下列已添加到[sys.databases dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql)： `total_processor_time_ms` 、 `total_allocated_memory_kb` 和 `survived_memory_kb` 。</span><span class="sxs-lookup"><span data-stu-id="b0f96-119">The following columns have been added to [sys.dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql): `total_processor_time_ms`, `total_allocated_memory_kb`, and `survived_memory_kb`.</span></span>  
  
  
