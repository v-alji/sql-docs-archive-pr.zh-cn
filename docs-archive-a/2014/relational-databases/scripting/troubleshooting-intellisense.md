---
title: IntelliSense 故障排除
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- unavailable options [IntelliSense]
- IntelliSense [SQL Server], troubleshooting
- IntelliSense [SQL Server], unavailable options
- troubleshooting [IntelliSense]
ms.assetid: 4b72ffc6-aea2-4e11-ab36-fa2de4d7bcc5
author: rothja
ms.author: jroth
ms.openlocfilehash: 087baf616fc215c480ae78621623cbe1ed512b57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690479"
---
# <a name="troubleshooting-intellisense-sql-server-management-studio"></a><span data-ttu-id="5c160-102">IntelliSense 故障排除 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5c160-102">Troubleshooting IntelliSense (SQL Server Management Studio)</span></span>
  <span data-ttu-id="5c160-103">在某些情况下，IntelliSense 选项可能无法按预期要求工作。</span><span class="sxs-lookup"><span data-stu-id="5c160-103">There are certain cases when the IntelliSense options might not work as you expect.</span></span>  
  
## <a name="conditions-that-affect-intellisense"></a><span data-ttu-id="5c160-104">影响 IntelliSense 的状况</span><span class="sxs-lookup"><span data-stu-id="5c160-104">Conditions That Affect IntelliSense</span></span>  
 <span data-ttu-id="5c160-105">以下状况可能会影响 IntelliSense 的行为：</span><span class="sxs-lookup"><span data-stu-id="5c160-105">The following conditions might affect the behavior of IntelliSense:</span></span>  
  
-   <span data-ttu-id="5c160-106">游标上方出现一个代码错误。</span><span class="sxs-lookup"><span data-stu-id="5c160-106">There is a code error above the cursor.</span></span>  
  
     <span data-ttu-id="5c160-107">如果在插入点上方有不完整的语句或其他代码错误，IntelliSense 可能无法分析代码元素，因此不会起作用。</span><span class="sxs-lookup"><span data-stu-id="5c160-107">If there is an incomplete statement or other coding error above the location of the insertion point, IntelliSense may be unable to parse the code elements, and therefore will not work.</span></span> <span data-ttu-id="5c160-108">您可以注释掉相应的代码，以再次启用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="5c160-108">You can comment out the applicable code to enable IntelliSense again.</span></span>  
  
-   <span data-ttu-id="5c160-109">插入点在代码注释内。</span><span class="sxs-lookup"><span data-stu-id="5c160-109">The insertion point is inside a code comment.</span></span>  
  
     <span data-ttu-id="5c160-110">如果插入点在源文件中的注释内，则 IntelliSense 选项不可用。</span><span class="sxs-lookup"><span data-stu-id="5c160-110">IntelliSense options are not available when the insertion point is within a comment in your source file.</span></span>  
  
-   <span data-ttu-id="5c160-111">插入点在字符串文字内。</span><span class="sxs-lookup"><span data-stu-id="5c160-111">The insertion point is inside a string literal.</span></span>  
  
     <span data-ttu-id="5c160-112">如果插入点在字符串文字周围的引号内，则 IntelliSense 选项不可用，例如：</span><span class="sxs-lookup"><span data-stu-id="5c160-112">IntelliSense options are not available when the insertion point is inside the quotation marks around a string literal, for example:</span></span>  
  
     `WHERE FirstName LIKE 'Patri%|'`  
  
-   <span data-ttu-id="5c160-113">自动选项被禁用。</span><span class="sxs-lookup"><span data-stu-id="5c160-113">The automatic options are turned off.</span></span>  
  
     <span data-ttu-id="5c160-114">默认情况下，许多 IntelliSense 功能都会自动工作，但您可以禁用任何功能。</span><span class="sxs-lookup"><span data-stu-id="5c160-114">Many IntelliSense features work automatically by default, but you can disable any feature.</span></span>  
  
     <span data-ttu-id="5c160-115">即使禁用了自动结束语句功能，仍可以使用 IntelliSense 功能。</span><span class="sxs-lookup"><span data-stu-id="5c160-115">Even when automatic statement completion is disabled, you can use an IntelliSense feature.</span></span> <span data-ttu-id="5c160-116">有关详细信息，请参阅[配置 IntelliSense (SQL Server Management Studio)](configure-intellisense-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="5c160-116">For more information, see [Configure IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).</span></span>  
  
## <a name="database-engine-query-intellisense"></a><span data-ttu-id="5c160-117">数据库引擎查询 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="5c160-117">Database Engine Query IntelliSense</span></span>  
 <span data-ttu-id="5c160-118">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 查询编辑器会出现以下问题：</span><span class="sxs-lookup"><span data-stu-id="5c160-118">The following issues apply to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Query Editor:</span></span>  
  
-   <span data-ttu-id="5c160-119">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器的 IntelliSense 功能不支持所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法元素。</span><span class="sxs-lookup"><span data-stu-id="5c160-119">The IntelliSense functionality of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor does not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax elements.</span></span> <span data-ttu-id="5c160-120">参数帮助不支持某些对象（例如扩展存储过程）中的参数。</span><span class="sxs-lookup"><span data-stu-id="5c160-120">Parameter help does not support the parameters in some objects, such as extended stored procedures.</span></span> <span data-ttu-id="5c160-121">有关详细信息，请参阅 [IntelliSense 支持的 Transact-SQL 语法](transact-sql-syntax-supported-by-intellisense.md)。</span><span class="sxs-lookup"><span data-stu-id="5c160-121">For more information, see [Transact-SQL Syntax Supported by IntelliSense](transact-sql-syntax-supported-by-intellisense.md).</span></span>  
  
-   <span data-ttu-id="5c160-122">仅当 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器从 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 或更高版本连接到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 实例时，才可以使用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="5c160-122">IntelliSense is only available when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span> <span data-ttu-id="5c160-123">如果查询编辑器连接到以前版本的 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，将无法使用 Intellisense。</span><span class="sxs-lookup"><span data-stu-id="5c160-123">IntelliSense is not available when the Query Editor is connected to earlier versions of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="5c160-124">将 SQLCMD 模式设置为开启时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中的 IntelliSense 将关闭。</span><span class="sxs-lookup"><span data-stu-id="5c160-124">IntelliSense is turned off in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor when the SQLCMD mode is set on.</span></span>  
  
-   <span data-ttu-id="5c160-125">IntelliSense 功能不适用于在您的编辑器窗口连接到数据库后由其他连接创建的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="5c160-125">IntelliSense functionality does not cover database objects created by another connection after your editor window connected to the database.</span></span> <span data-ttu-id="5c160-126">如果对象缺少完成列表之类的 IntelliSense 功能，您可以选择以下三种机制之一以便为您的编辑器窗口刷新对象缓存：</span><span class="sxs-lookup"><span data-stu-id="5c160-126">If objects are missing from IntelliSense features such as completion lists, you can choose one of these three mechanisms to refresh the cache of objects for your editor window:</span></span>  
  
    -   <span data-ttu-id="5c160-127">依次选择 **“编辑”** 菜单、 **“IntelliSense”** 和 **“刷新本地缓存”**。</span><span class="sxs-lookup"><span data-stu-id="5c160-127">Select the **Edit** menu, select **IntelliSense**, then select **Refresh Local Cache**.</span></span>  
  
    -   <span data-ttu-id="5c160-128">使用键盘快捷键 Ctrl+Shift+R。</span><span class="sxs-lookup"><span data-stu-id="5c160-128">Use the CTRL+Shift+R keyboard shortcut.</span></span>  
  
    -   <span data-ttu-id="5c160-129">从 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例中断开您的编辑器窗口，然后重新连接。</span><span class="sxs-lookup"><span data-stu-id="5c160-129">Disconnect your editor window from the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and reconnect.</span></span>  
  
-   <span data-ttu-id="5c160-130">完成列表不包含您对其没有权限的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="5c160-130">Completion lists do not include database objects for which you do not have permissions.</span></span> <span data-ttu-id="5c160-131">IntelliSense 标志会引用您确实拥有其权限的对象。</span><span class="sxs-lookup"><span data-stu-id="5c160-131">IntelliSense flags references to objects for which you do have permissions.</span></span> <span data-ttu-id="5c160-132">例如，如果您打开了由他人编写的脚本，则对该人拥有权限而您没有权限的对象的任何引用都会被标记为不正确。</span><span class="sxs-lookup"><span data-stu-id="5c160-132">For example, if you open a script that is written by someone else, any references to objects for which that person has permissions and you do not are flagged as incorrect.</span></span>  
  
-   <span data-ttu-id="5c160-133">如果失去了与 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的连接，完成列表可能会停止工作。</span><span class="sxs-lookup"><span data-stu-id="5c160-133">Completion lists might stop working if you lose the connection to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="5c160-134">请重新连接到该实例。</span><span class="sxs-lookup"><span data-stu-id="5c160-134">Reconnect to the instance.</span></span>  
  
  
