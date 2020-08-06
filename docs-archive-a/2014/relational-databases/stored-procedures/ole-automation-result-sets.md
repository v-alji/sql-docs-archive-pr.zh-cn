---
title: OLE 自动化结果集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- data types [SQL Server], OLE Automation
- two-dimensional arrays
- one-dimensional arrays
- result sets [SQL Server], OLE Automation
- OLE Automation [SQL Server], result sets
- arrays [SQL Server]
ms.assetid: b2f99e33-2303-427c-94b9-9d55f8e2a6ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7c9bdc4d51d989db2d4d676b29e0824c0e5b59a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591863"
---
# <a name="ole-automation-result-sets"></a><span data-ttu-id="8bc9a-102">OLE 自动化结果集</span><span class="sxs-lookup"><span data-stu-id="8bc9a-102">OLE Automation Result Sets</span></span>
  <span data-ttu-id="8bc9a-103">如果 OLE 自动化属性或方法返回的数据是一维或二维数组，则该数组将作为结果集返回到客户端：</span><span class="sxs-lookup"><span data-stu-id="8bc9a-103">If an OLE Automation property or method returns data in an array with one or two dimensions, the array is returned to the client as a result set:</span></span>  
  
-   <span data-ttu-id="8bc9a-104">一维数组作为单行结果集返回给客户端，其中的列数与数组中的元素数相等。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-104">A one-dimensional array is returned to the client as a single-row result set with as many columns as there are elements in the array.</span></span> <span data-ttu-id="8bc9a-105">例如，array(10) 作为 10 列单行返回。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-105">For example, an array(10) is returned as a single row of 10 columns.</span></span>  
  
-   <span data-ttu-id="8bc9a-106">二维数组作为结果集返回给客户端，其中的列数与数组第一维中的元素数相同，行数与数组第二维中的元素数相同。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-106">A two-dimensional array is returned to the client as a result set with as many columns as there are elements in the first dimension of the array and with as many rows as there are elements in the second dimension of the array.</span></span> <span data-ttu-id="8bc9a-107">例如，array(2,3) 作为 2 列 3 行返回。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-107">For example, an array(2,3) is returned as 2 columns in 3 rows.</span></span>  
  
 <span data-ttu-id="8bc9a-108">当属性返回值或方法返回值是数组时，sp_OAGetProperty 或 sp_OAMethod 将向客户端返回结果集。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-108">When a property return value or method return value is an array, sp_OAGetProperty or sp_OAMethod returns a result set to the client.</span></span> <span data-ttu-id="8bc9a-109">（方法输出参数不能是数组。这些过程可扫描数组中的所有数据值，以确定用于结果集中各列的相应 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型和数据长度。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-109">(Method output parameters cannot be arrays.) These procedures scan all the data values in the array to determine the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and data lengths to use for each column in the result set.</span></span> <span data-ttu-id="8bc9a-110">对于某个特定的列，这些过程将使用显示该列中的所有数据值所需要的数据类型和长度。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-110">For a particular column, these procedures use the data type and length required to represent all data values in that column.</span></span>  
  
 <span data-ttu-id="8bc9a-111">如果一列中的所有数据值具有相同的数据类型，此数据类型将用于整个列。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-111">When all data values in a column share the same data type, that data type is used for the whole column.</span></span> <span data-ttu-id="8bc9a-112">当一个列中的数据值的数据类型不同时，将根据下表选择整个列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-112">When data values in a column are different data types, the data type of the whole column is chosen based on the following table.</span></span> <span data-ttu-id="8bc9a-113">若要使用下表，请沿着左侧行轴找到一种数据类型，再沿着最上面的列轴找到第二种数据类型。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-113">To use the following table, find one data type along the left row axis and a second data type along the top column axis.</span></span> <span data-ttu-id="8bc9a-114">行和列的交点会说明结果集这一列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="8bc9a-114">The intersection of the row and column describes the data type of the result set column.</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
||`int`|`float`|`money`|`datetime`|`varchar`|`nvarchar`|  
|`int`|`int`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`float`|`float`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`money`|`money`|`money`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`datetime`|`varchar`|`varchar`|`varchar`|`datetime`|`varchar`|`nvarchar`|  
|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`nvarchar`|  
|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|  
  
## <a name="related-content"></a><span data-ttu-id="8bc9a-115">相关内容</span><span class="sxs-lookup"><span data-stu-id="8bc9a-115">Related Content</span></span>  
 [<span data-ttu-id="8bc9a-116">OLE 自动存储过程 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8bc9a-116">OLE Automation Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql)  
  
 [<span data-ttu-id="8bc9a-117">Ole Automation Procedures 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="8bc9a-117">Ole Automation Procedures Server Configuration Option</span></span>](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  
