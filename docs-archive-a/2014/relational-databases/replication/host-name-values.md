---
title: HOST_NAME 值 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 67d01df05c8d56fd435eb0ee1b42ba2da6a312ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578078"
---
# <a name="host_name-values"></a><span data-ttu-id="50ccc-102">HOST_NAME 值</span><span class="sxs-lookup"><span data-stu-id="50ccc-102">HOST_NAME Values</span></span>
  <span data-ttu-id="50ccc-103">具有参数化筛选器的合并发布使用 SUSER_SNAME() 和/或 HOST_NAME() 函数筛选数据。</span><span class="sxs-lookup"><span data-stu-id="50ccc-103">Merge publications with parameterized filters use the SUSER_SNAME() function and/or the HOST_NAME() function to filter data.</span></span> <span data-ttu-id="50ccc-104">函数在新建发布向导或 **“发布属性”** 对话框中指定。</span><span class="sxs-lookup"><span data-stu-id="50ccc-104">The function is specified in the New Publication Wizard or the **Publication Properties** dialog box.</span></span>  
  
 <span data-ttu-id="50ccc-105">默认情况下，HOST_NAME() 函数返回连接到发布服务器的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="50ccc-105">By default, the HOST_NAME() function returns the name of the computer connecting to the Publisher.</span></span> <span data-ttu-id="50ccc-106">在使用参数化筛选器时，通常在向导的此页上提供值来覆盖此值。</span><span class="sxs-lookup"><span data-stu-id="50ccc-106">When using parameterized filters, it is common to override this value by supplying a value on this page of the wizard.</span></span> <span data-ttu-id="50ccc-107">这样，HOST_NAME() 函数将返回指定的值而非计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="50ccc-107">The HOST_NAME() function then returns the value you specify rather than the name of the computer.</span></span> <span data-ttu-id="50ccc-108">有关详细信息，请参阅[参数化行筛选器](merge/parameterized-filters-parameterized-row-filters.md)的“覆盖 HOST_NAME() 值”部分。</span><span class="sxs-lookup"><span data-stu-id="50ccc-108">For more information, see the "Overriding the HOST_NAME() Value" section of [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50ccc-109">如果覆盖 HOST_NAME()，则对 HOST_NAME() 函数的所有调用将全部返回指定的值。</span><span class="sxs-lookup"><span data-stu-id="50ccc-109">If you override HOST_NAME(), all calls to the HOST_NAME() function will return the value you specify.</span></span> <span data-ttu-id="50ccc-110">请确保其他应用程序未依赖于返回计算机名称的 HOST_NAME()。</span><span class="sxs-lookup"><span data-stu-id="50ccc-110">Ensure that other applications are not depending on HOST_NAME() returning the computer name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="50ccc-111">选项</span><span class="sxs-lookup"><span data-stu-id="50ccc-111">Options</span></span>  
 <span data-ttu-id="50ccc-112">**订阅属性**</span><span class="sxs-lookup"><span data-stu-id="50ccc-112">**Subscription properties**</span></span>  
 <span data-ttu-id="50ccc-113">在 **“HOST_NAME 值”** 列中为每个订阅服务器输入一个值或者接受默认值，默认值为订阅服务器计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="50ccc-113">Enter a value for each Subscriber in the **HOST_NAME Value** column or accept the default, which is the name of the Subscriber computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ccc-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50ccc-114">See Also</span></span>  
 <span data-ttu-id="50ccc-115">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="50ccc-115">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="50ccc-116">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="50ccc-116">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="50ccc-117">[查看和修改请求订阅属性](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="50ccc-117">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="50ccc-118">[查看和修改推送订阅属性](view-and-modify-push-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="50ccc-118">[View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) </span></span>  
 <span data-ttu-id="50ccc-119">[HOST_NAME (Transact-SQL)](/sql/t-sql/functions/host-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="50ccc-119">[HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) </span></span>  
 [<span data-ttu-id="50ccc-120">订阅发布</span><span class="sxs-lookup"><span data-stu-id="50ccc-120">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
