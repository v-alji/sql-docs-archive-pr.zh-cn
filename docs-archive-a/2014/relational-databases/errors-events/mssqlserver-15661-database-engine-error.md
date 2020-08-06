---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 966e23e8d970c36eba81253228cc18ed4af3ff77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576798"
---
# <a name="mssqlserver_15661"></a><span data-ttu-id="ddb7d-102">MSSQLSERVER_15661</span><span class="sxs-lookup"><span data-stu-id="ddb7d-102">MSSQLSERVER_15661</span></span>
    
## <a name="details"></a><span data-ttu-id="ddb7d-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="ddb7d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ddb7d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ddb7d-104">Product Name</span></span>|<span data-ttu-id="ddb7d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ddb7d-105">SQL Server</span></span>|  
|<span data-ttu-id="ddb7d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ddb7d-106">Event ID</span></span>|<span data-ttu-id="ddb7d-107">15661</span><span class="sxs-lookup"><span data-stu-id="ddb7d-107">15661</span></span>|  
|<span data-ttu-id="ddb7d-108">事件源</span><span class="sxs-lookup"><span data-stu-id="ddb7d-108">Event Source</span></span>|<span data-ttu-id="ddb7d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ddb7d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ddb7d-110">组件</span><span class="sxs-lookup"><span data-stu-id="ddb7d-110">Component</span></span>|<span data-ttu-id="ddb7d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ddb7d-111">SQLEngine</span></span>|  
|<span data-ttu-id="ddb7d-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="ddb7d-112">Symbolic Name</span></span>|<span data-ttu-id="ddb7d-113">SQLErrorNum15661</span><span class="sxs-lookup"><span data-stu-id="ddb7d-113">SQLErrorNum15661</span></span>|  
|<span data-ttu-id="ddb7d-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="ddb7d-114">Message Text</span></span>|<span data-ttu-id="ddb7d-115">sp_estimate_data_compression_savings 存储过程不能用于临时表。</span><span class="sxs-lookup"><span data-stu-id="ddb7d-115">The sp_estimate_data_compression_savings stored procedure cannot be used for temporary tables.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ddb7d-116">说明</span><span class="sxs-lookup"><span data-stu-id="ddb7d-116">Explanation</span></span>  
 <span data-ttu-id="ddb7d-117">临时表已用作 sp_estimate_data_compression_savings 存储过程的参数。</span><span class="sxs-lookup"><span data-stu-id="ddb7d-117">A temporary table was used as an argument for the sp_estimate_data_compression_savings stored procedure.</span></span> <span data-ttu-id="ddb7d-118">尽管支持压缩临时表，但 sp_estimate_data_compression_savings 不能用于估计压缩的存储内容。</span><span class="sxs-lookup"><span data-stu-id="ddb7d-118">Although the compression of temporary tables is supported, you cannot use sp_estimate_data_compression_savings to estimate the compression savings.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ddb7d-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="ddb7d-119">User Action</span></span>  
 <span data-ttu-id="ddb7d-120">删除用作 sp_estimate_data_compression_savings 参数的临时表。</span><span class="sxs-lookup"><span data-stu-id="ddb7d-120">Remove the temporary table as an argument for sp_estimate_data_compression_savings.</span></span>  
  
  
