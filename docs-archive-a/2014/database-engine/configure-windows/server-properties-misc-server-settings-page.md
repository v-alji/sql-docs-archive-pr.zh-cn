---
title: 服务器属性（“杂项服务器设置”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.miscserversettings.f1
ms.assetid: b170c066-30cd-42dd-8d34-aa129ea09551
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9a82a787140141c3bfa7b18776328a813be9f41f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587594"
---
# <a name="server-properties-misc-server-settings-page"></a><span data-ttu-id="75963-102">服务器属性（“杂项服务器设置”页）</span><span class="sxs-lookup"><span data-stu-id="75963-102">Server Properties (Misc Server Settings Page)</span></span>
  <span data-ttu-id="75963-103">使用此页可以查看或修改服务器设置。</span><span class="sxs-lookup"><span data-stu-id="75963-103">Use this page to view or modify your server settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="75963-104">选项</span><span class="sxs-lookup"><span data-stu-id="75963-104">Options</span></span>  
 <span data-ttu-id="75963-105">**用户的默认语言**</span><span class="sxs-lookup"><span data-stu-id="75963-105">**Default language for users**</span></span>  
 <span data-ttu-id="75963-106">指定所有新建登录名的默认语言。</span><span class="sxs-lookup"><span data-stu-id="75963-106">Specifies the default language for all newly created logins.</span></span>  
  
 <span data-ttu-id="75963-107">**允许触发器激发其他触发器**</span><span class="sxs-lookup"><span data-stu-id="75963-107">**Allow triggers to fire other triggers**</span></span>  
 <span data-ttu-id="75963-108">控制触发器是否可以执行启动另一个触发器的操作。</span><span class="sxs-lookup"><span data-stu-id="75963-108">Controls whether a trigger can perform an action that initiates another trigger.</span></span> <span data-ttu-id="75963-109">清除此选项后，触发器不能由另外一个触发器来激发。</span><span class="sxs-lookup"><span data-stu-id="75963-109">When cleared, triggers cannot be fired by another trigger.</span></span> <span data-ttu-id="75963-110">选中此选项时，触发器可以由其他触发器来激发，级联等级最高为 32 级。</span><span class="sxs-lookup"><span data-stu-id="75963-110">When selected, triggers can be fired by other triggers to as many as 32 levels.</span></span>  
  
 <span data-ttu-id="75963-111">**使用查询调控器防止查询长时间运行**</span><span class="sxs-lookup"><span data-stu-id="75963-111">**Use query governor to prevent long-running queries**</span></span>  
 <span data-ttu-id="75963-112">指定查询运行时间的上限。</span><span class="sxs-lookup"><span data-stu-id="75963-112">Specifies an upper limit on the time within which a query can run.</span></span> <span data-ttu-id="75963-113">查询开销是指在特定硬件配置中执行查询所需的估计占用时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="75963-113">Query cost refers to the estimated elapsed time, in seconds, required to execute a query on a specific hardware configuration.</span></span> <span data-ttu-id="75963-114">查询调控器默认为关闭，允许运行所有查询。</span><span class="sxs-lookup"><span data-stu-id="75963-114">By default, the query governor is turned off and all queries are allowed to run.</span></span> <span data-ttu-id="75963-115">如果选中此选项，则必须在下面的文本框中输入时间限制。</span><span class="sxs-lookup"><span data-stu-id="75963-115">If this option is selected, you must enter a time limit in the text box below.</span></span> <span data-ttu-id="75963-116">如果为该选项指定一个非零、非负的数值，则查询调控器将不允许执行估计开销超过该值的查询。</span><span class="sxs-lookup"><span data-stu-id="75963-116">If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost exceeding that value.</span></span>  
  
 <span data-ttu-id="75963-117">**将两位数的年份解释为介于**</span><span class="sxs-lookup"><span data-stu-id="75963-117">**Interpret a two-digit year as falling between**</span></span>  
 <span data-ttu-id="75963-118">指定 100 年的日期范围，用于解释针两位数年份值。</span><span class="sxs-lookup"><span data-stu-id="75963-118">Specifies the 100-year date range for interpreting two-digit year values.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="75963-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会将两位数日期值解释为指定范围内以这两位数值结尾的年份。</span><span class="sxs-lookup"><span data-stu-id="75963-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will interpret two-digit date values to refer to the year ending in those digits that falls within the specified range.</span></span>  
  
 <span data-ttu-id="75963-120">在右侧的框中设置结束年份。</span><span class="sxs-lookup"><span data-stu-id="75963-120">Set the right box with the ending year.</span></span> <span data-ttu-id="75963-121">保存结束年份时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会自动在左侧的框中填充起始年份。</span><span class="sxs-lookup"><span data-stu-id="75963-121">When the ending year is saved, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will automatically populate the left box with the beginning year.</span></span>  
  
 <span data-ttu-id="75963-122">**配置值**</span><span class="sxs-lookup"><span data-stu-id="75963-122">**Configured Values**</span></span>  
 <span data-ttu-id="75963-123">显示此窗格上选项的配置值。</span><span class="sxs-lookup"><span data-stu-id="75963-123">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="75963-124">如果更改了这些值，请单击 **“运行值”** 以查看更改是否已生效。</span><span class="sxs-lookup"><span data-stu-id="75963-124">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="75963-125">如果更改未生效，则必须首先重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="75963-125">If the changes have not taken effect, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restated first.</span></span>  
  
 <span data-ttu-id="75963-126">**“运行值”**</span><span class="sxs-lookup"><span data-stu-id="75963-126">**Running Values**</span></span>  
 <span data-ttu-id="75963-127">查看此窗格上选项的当前运行值。</span><span class="sxs-lookup"><span data-stu-id="75963-127">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="75963-128">这些值是只读的。</span><span class="sxs-lookup"><span data-stu-id="75963-128">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75963-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75963-129">See Also</span></span>  
 [<span data-ttu-id="75963-130">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="75963-130">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
