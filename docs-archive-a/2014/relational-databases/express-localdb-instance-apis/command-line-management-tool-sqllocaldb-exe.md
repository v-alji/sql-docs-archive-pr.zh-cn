---
title: 命令行管理工具： SqlLocalDB.exe |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d21a6a8879e981e52bd2e7d3bd05a37e65d8cf4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578221"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a><span data-ttu-id="fe815-102">命令行管理工具：SqlLocalDB.exe</span><span class="sxs-lookup"><span data-stu-id="fe815-102">Command-Line Management Tool: SqlLocalDB.exe</span></span>
  <span data-ttu-id="fe815-103">SqlLocalDB.exe 是一个简单的工具，它使用户能够从命令行轻松管理 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="fe815-103">SqlLocalDB.exe is a simple tool that enables the user to easily manage LocalDB instances from the command line.</span></span> <span data-ttu-id="fe815-104">它作为 LocalDB 实例 API 的简单包装实现。</span><span class="sxs-lookup"><span data-stu-id="fe815-104">It is implemented as a simple wrapper around the LocalDB instance API.</span></span> <span data-ttu-id="fe815-105">与在很多类似的 SQL Server 工具（例如 SQLCMD）中一样，参数作为命令行参数传递给 SqlLocalDB，并且将输出发送到控制台。</span><span class="sxs-lookup"><span data-stu-id="fe815-105">As in many similar SQL Server tools (for example, SQLCMD), parameters are passed to SqlLocalDB as command-line arguments and output is sent to the console.</span></span>  
  
 <span data-ttu-id="fe815-106">借助于 SqlLocalDB，开发人员不必编写代码或依赖于其他工具来调用 API，即可使用 LocalDB。</span><span class="sxs-lookup"><span data-stu-id="fe815-106">SqlLocalDB enables developers to use LocalDB without having to write code to call the API or depend on other tools to do it for them.</span></span>  
  
## <a name="sqllocaldb-options"></a><span data-ttu-id="fe815-107">SqlLocalDB 选项</span><span class="sxs-lookup"><span data-stu-id="fe815-107">SqlLocalDB Options</span></span>  
 <span data-ttu-id="fe815-108">SqlLocalDB 支持以下选项。</span><span class="sxs-lookup"><span data-stu-id="fe815-108">SqlLocalDB supports the following options.</span></span>  
  
|<span data-ttu-id="fe815-109">选项</span><span class="sxs-lookup"><span data-stu-id="fe815-109">Option</span></span>|<span data-ttu-id="fe815-110">作用</span><span class="sxs-lookup"><span data-stu-id="fe815-110">What it does</span></span>|  
|------------|------------------|  
|`-?`|<span data-ttu-id="fe815-111">打印帮助文本。</span><span class="sxs-lookup"><span data-stu-id="fe815-111">Prints help text.</span></span>|  
|`create&#124;c "instance name" [version-number] [-s]`|<span data-ttu-id="fe815-112">创建具有指定名称和版本的新 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="fe815-112">Creates a new LocalDB instance with a specified name and version.</span></span><br /><br /> <span data-ttu-id="fe815-113">如果省略 [version-number] 参数，则它默认为 SqlLocalDB 内部版本。</span><span class="sxs-lookup"><span data-stu-id="fe815-113">If the [version-number] parameter is omitted, it defaults to the SqlLocalDB build version.</span></span><br /><br /> <span data-ttu-id="fe815-114">-s 在创建新的 LocalDB 实例后启动它。</span><span class="sxs-lookup"><span data-stu-id="fe815-114">-s starts the new LocalDB instance after it is created.</span></span>|  
|`delete&#124;d "instance name"`|<span data-ttu-id="fe815-115">删除具有指定名称的 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="fe815-115">Deletes the LocalDB instance with the specified name.</span></span>|  
|`start&#124;s "instance name"`|<span data-ttu-id="fe815-116">启动具有指定名称的 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="fe815-116">Starts the LocalDB instance with the specified name.</span></span>|  
|`stop&#124;p "instance name" [-i&#124;-k]`|<span data-ttu-id="fe815-117">当前查询完成运行后，停止具有指定名称的 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="fe815-117">Stops the LocalDB instance with the specified name, after current queries finish running.</span></span><br /><br /> <span data-ttu-id="fe815-118">-i 请求使用 NOWAIT 选项关闭 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="fe815-118">-i requests the LocalDB instance shutdown with the NOWAIT option.</span></span><br /><br /> <span data-ttu-id="fe815-119">-k 终止 LocalDB 实例进程而不联系它。</span><span class="sxs-lookup"><span data-stu-id="fe815-119">-k kills the LocalDB instance process without contacting it.</span></span>|  
|`share&#124;h ["owner SID or account"] "private name" "shared name"`|<span data-ttu-id="fe815-120">使用指定的共享名称共享指定的私有实例。</span><span class="sxs-lookup"><span data-stu-id="fe815-120">Shares the specified private instance using the specified shared name.</span></span> <span data-ttu-id="fe815-121">如果省略该用户 SID 或帐户名称，则默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="fe815-121">If the user SID or account name is omitted, it defaults to the current user.</span></span>|  
|`unshare&#124;u "shared name"`|<span data-ttu-id="fe815-122">不共享指定的共享 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="fe815-122">Unshares the specified shared LocalDB instance.</span></span>|  
|`info&#124;i`|<span data-ttu-id="fe815-123">列出当前用户拥有的所有现有 LocalDB 实例和所有共享的 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="fe815-123">Lists all existing LocalDB instances that are owned by the current user and all shared LocalDB instances.</span></span>|  
|`info&#124;i "instance name"`|<span data-ttu-id="fe815-124">打印有关指定的 LocalDB 实例的信息。</span><span class="sxs-lookup"><span data-stu-id="fe815-124">Prints the information about the specified LocalDB instance.</span></span>|  
|`versions&#124;v`|<span data-ttu-id="fe815-125">列出计算机上安装的所有 LocalDB 版本。</span><span class="sxs-lookup"><span data-stu-id="fe815-125">Lists all LocalDB versions installed on the computer.</span></span>|  
|||  
|`trace&#124;t on&#124;off`|<span data-ttu-id="fe815-126">打开和关闭跟踪。</span><span class="sxs-lookup"><span data-stu-id="fe815-126">Turns tracing on and off.</span></span>|  
  
 <span data-ttu-id="fe815-127">SqlLocalDB 将空格作为分隔符；必须将包含空格和特殊字符的实例名称用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="fe815-127">SqlLocalDB treats spaces as delimiters; you must surround the instance names that contain spaces and special characters with quotes.</span></span> <span data-ttu-id="fe815-128">例如：</span><span class="sxs-lookup"><span data-stu-id="fe815-128">For example:</span></span>  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
