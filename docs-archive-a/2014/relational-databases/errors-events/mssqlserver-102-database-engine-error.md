---
title: MSSQLSERVER_102 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 18c330b8d6a534ca11e2ad2c03f89793f8c832e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577737"
---
# <a name="mssqlserver_102"></a><span data-ttu-id="5b9f3-102">MSSQLSERVER_102</span><span class="sxs-lookup"><span data-stu-id="5b9f3-102">MSSQLSERVER_102</span></span>
    
## <a name="details"></a><span data-ttu-id="5b9f3-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5b9f3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b9f3-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5b9f3-104">Product Name</span></span>|<span data-ttu-id="5b9f3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5b9f3-105">SQL Server</span></span>|  
|<span data-ttu-id="5b9f3-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5b9f3-106">Event ID</span></span>|<span data-ttu-id="5b9f3-107">102</span><span class="sxs-lookup"><span data-stu-id="5b9f3-107">102</span></span>|  
|<span data-ttu-id="5b9f3-108">事件源</span><span class="sxs-lookup"><span data-stu-id="5b9f3-108">Event Source</span></span>|<span data-ttu-id="5b9f3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5b9f3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5b9f3-110">组件</span><span class="sxs-lookup"><span data-stu-id="5b9f3-110">Component</span></span>|<span data-ttu-id="5b9f3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5b9f3-111">SQLEngine</span></span>|  
|<span data-ttu-id="5b9f3-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="5b9f3-112">Symbolic Name</span></span>|<span data-ttu-id="5b9f3-113">P_SYNTAXERR2</span><span class="sxs-lookup"><span data-stu-id="5b9f3-113">P_SYNTAXERR2</span></span>|  
|<span data-ttu-id="5b9f3-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="5b9f3-114">Message Text</span></span>|<span data-ttu-id="5b9f3-115">“%.\*ls”附近有语法错误。</span><span class="sxs-lookup"><span data-stu-id="5b9f3-115">Incorrect syntax near '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5b9f3-116">说明</span><span class="sxs-lookup"><span data-stu-id="5b9f3-116">Explanation</span></span>  
 <span data-ttu-id="5b9f3-117">指示语法错误。</span><span class="sxs-lookup"><span data-stu-id="5b9f3-117">Indicates a syntax error.</span></span> <span data-ttu-id="5b9f3-118">无法提供其他信息，因为该错误阻止[!INCLUDE[ssDE](../../includes/ssde-md.md)]处理语句。</span><span class="sxs-lookup"><span data-stu-id="5b9f3-118">Additional information is not available because the error prevents the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from processing the statement.</span></span>  
  
 <span data-ttu-id="5b9f3-119">当不处于 90 或 100 兼容模式下时，如果尝试使用不推荐使用的 RC4 或 RC4_128 加密创建对称密钥，可能导致此错误。</span><span class="sxs-lookup"><span data-stu-id="5b9f3-119">Can be caused by attempting to create a symmetric key using the deprecated RC4 or RC4_128 encryption, when not in 90 or 100 compatibility mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5b9f3-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="5b9f3-120">User Action</span></span>  
 <span data-ttu-id="5b9f3-121">搜索 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，查找语法错误。</span><span class="sxs-lookup"><span data-stu-id="5b9f3-121">Search the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement for syntax errors.</span></span>  
  
 <span data-ttu-id="5b9f3-122">如果使用 RC4 或 RC4_128 创建对称密钥，请选择较新的加密（如某个 AES 算法）。</span><span class="sxs-lookup"><span data-stu-id="5b9f3-122">If creating a symmetric key using the RC4 or RC4_128, select a newer encryption such as one of the AES algorithms.</span></span> <span data-ttu-id="5b9f3-123">（建议。）如果必须使用 RC4，请使用 ALTER DATABASE SET COMPATIBILITY_LEVEL 将数据库兼容级别设置为 90 或 100。</span><span class="sxs-lookup"><span data-stu-id="5b9f3-123">(Recommended.) If you must use RC4, use ALTER DATABASE SET COMPATIBILITY_LEVEL to set the database to compatibility level 90 or 100.</span></span> <span data-ttu-id="5b9f3-124">（建议不要使用。）</span><span class="sxs-lookup"><span data-stu-id="5b9f3-124">(Not recommended.)</span></span>  
  
  
