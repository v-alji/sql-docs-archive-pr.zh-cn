---
title: MSSQLSERVER_9524 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6c46ee0ef0bd1be299614e2cb04a3d6cd99d92e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581231"
---
# <a name="mssqlserver_9524"></a><span data-ttu-id="0384a-102">MSSQLSERVER_9524</span><span class="sxs-lookup"><span data-stu-id="0384a-102">MSSQLSERVER_9524</span></span>
    
## <a name="details"></a><span data-ttu-id="0384a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="0384a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0384a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="0384a-104">Product Name</span></span>|<span data-ttu-id="0384a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0384a-105">SQL Server</span></span>|  
|<span data-ttu-id="0384a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0384a-106">Event ID</span></span>|<span data-ttu-id="0384a-107">9254</span><span class="sxs-lookup"><span data-stu-id="0384a-107">9254</span></span>|  
|<span data-ttu-id="0384a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="0384a-108">Event Source</span></span>|<span data-ttu-id="0384a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0384a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0384a-110">组件</span><span class="sxs-lookup"><span data-stu-id="0384a-110">Component</span></span>|<span data-ttu-id="0384a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0384a-111">SQLEngine</span></span>|  
|<span data-ttu-id="0384a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="0384a-112">Symbolic Name</span></span>|<span data-ttu-id="0384a-113">XMLERR_INVALID_COLUMNSET_XML</span><span class="sxs-lookup"><span data-stu-id="0384a-113">XMLERR_INVALID_COLUMNSET_XML</span></span>|  
|<span data-ttu-id="0384a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="0384a-114">Message Text</span></span>|<span data-ttu-id="0384a-115">提供的 XML 内容不符合稀疏列集所需的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="0384a-115">The XML content provided does not conform to the required XML format for sparse column sets.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0384a-116">说明</span><span class="sxs-lookup"><span data-stu-id="0384a-116">Explanation</span></span>  
 <span data-ttu-id="0384a-117">已尝试修改列集。</span><span class="sxs-lookup"><span data-stu-id="0384a-117">An attempt was made to modify a column set.</span></span> <span data-ttu-id="0384a-118">列集的 XML 内容必须满足列集的格式限制要求。</span><span class="sxs-lookup"><span data-stu-id="0384a-118">The XML content of a column set must meet the format restrictions of a column set.</span></span> <span data-ttu-id="0384a-119">列集的常用格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="0384a-119">The general format of a column set is as follows:</span></span>  
  
 `<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
 <span data-ttu-id="0384a-120">有关列集的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“使用列集”主题。</span><span class="sxs-lookup"><span data-stu-id="0384a-120">For more information about column sets, see the topic "Using Column Sets" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0384a-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="0384a-121">User Action</span></span>  
 <span data-ttu-id="0384a-122">在语句中更正此列集的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="0384a-122">Correct the format of the XML for the column set in the statement.</span></span>  
  
  
