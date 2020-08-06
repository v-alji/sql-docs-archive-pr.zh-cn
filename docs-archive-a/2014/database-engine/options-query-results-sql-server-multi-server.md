---
title: 选项 (查询结果-SQL Server 多服务器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
author: rothja
ms.author: jroth
ms.openlocfilehash: 8273ad5edc65dd7351533209e9fa670c49f75f7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691861"
---
# <a name="options-query-results-sql-server-multi-server"></a><span data-ttu-id="6b440-102">选项（“查询结果”-“SQL Server”-“多服务器”）</span><span class="sxs-lookup"><span data-stu-id="6b440-102">Options (Query Results-SQL Server-Multi-Server)</span></span>
  <span data-ttu-id="6b440-103">在同时查询多个服务器时，可使用此页指定显示结果集的选项。</span><span class="sxs-lookup"><span data-stu-id="6b440-103">When you are querying multiple servers at the same time, use this page to specify the options for displaying result sets.</span></span> <span data-ttu-id="6b440-104">“合并结果”可将所有服务器中的结果集合并为单个结果集。</span><span class="sxs-lookup"><span data-stu-id="6b440-104">Merge results combines the result sets from all servers into a single result set.</span></span> <span data-ttu-id="6b440-105">合并结果时，响应的第一个服务器将设置结果集的架构。</span><span class="sxs-lookup"><span data-stu-id="6b440-105">When merging results, the first server to respond sets the schema for the result set.</span></span> <span data-ttu-id="6b440-106">若要合并结果集，查询必须从每个服务器中返回具有相同列名的相同列数。</span><span class="sxs-lookup"><span data-stu-id="6b440-106">To merge the result sets, the query must return the same number of columns with the same column names from each server.</span></span> <span data-ttu-id="6b440-107">在合并结果时，如果某个服务器与第一个服务器在返回结果时返回的架构（列计数和列名称）不匹配，则会为该服务器显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="6b440-107">When merging results, a message is displayed for each server that does not match the schema (column count and column names) that is returned by the first server to return results.</span></span>  
  
 <span data-ttu-id="6b440-108">如果不合并结果，每个服务器中的结果集将显示在其自己的网格中，并使用其自己的架构。</span><span class="sxs-lookup"><span data-stu-id="6b440-108">When you do not merge results, the result set from each server will be displayed in its own grid with its own schema.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="6b440-109">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="6b440-109">UI element list</span></span>  
 <span data-ttu-id="6b440-110">**合并结果**</span><span class="sxs-lookup"><span data-stu-id="6b440-110">**Merge results**</span></span>  
 <span data-ttu-id="6b440-111">选中此复选框可将几个服务器组中的结果集合并到相同的网格中。</span><span class="sxs-lookup"><span data-stu-id="6b440-111">Select this check box to combine the result sets from several servers into the same grid.</span></span>  
  
 <span data-ttu-id="6b440-112">**将服务器名称添加到结果**</span><span class="sxs-lookup"><span data-stu-id="6b440-112">**Add server name to the results**</span></span>  
 <span data-ttu-id="6b440-113">选中此复选框可包含一个额外的列，其中提供生成每一行的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="6b440-113">Select this check box to include an additional column that provides the name of the server that produced each row.</span></span>  
  
 <span data-ttu-id="6b440-114">**将登录名添加到结果**</span><span class="sxs-lookup"><span data-stu-id="6b440-114">**Add login name to the results**</span></span>  
 <span data-ttu-id="6b440-115">选中此复选框可包含一个额外的列，其中提供用于连接到提供每一行的服务器的登录名。</span><span class="sxs-lookup"><span data-stu-id="6b440-115">Select this check box to include an additional column that provides the login that was used to connect to the server that provided each row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b440-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b440-116">See Also</span></span>  
 <span data-ttu-id="6b440-117">[创建中央管理服务器和服务器组 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md) </span><span class="sxs-lookup"><span data-stu-id="6b440-117">[Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md) </span></span>  
 [<span data-ttu-id="6b440-118">同时对多个服务器执行语句 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6b440-118">Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  
