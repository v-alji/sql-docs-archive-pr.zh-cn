---
title: 强密码 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5e878e0de5ee1f496dcc981182d42f5898838c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688707"
---
# <a name="strong-passwords"></a><span data-ttu-id="22da7-102">强密码</span><span class="sxs-lookup"><span data-stu-id="22da7-102">Strong Passwords</span></span>
  <span data-ttu-id="22da7-103">在服务器安全部署中，密码可能是最薄弱的一个环节。</span><span class="sxs-lookup"><span data-stu-id="22da7-103">Passwords can be the weakest link in a server security deployment.</span></span> <span data-ttu-id="22da7-104">请务必在选择密码时保持高度谨慎。</span><span class="sxs-lookup"><span data-stu-id="22da7-104">You should always take great care when you select a password.</span></span> <span data-ttu-id="22da7-105">强密码有以下特征：</span><span class="sxs-lookup"><span data-stu-id="22da7-105">A strong password has the following characteristics:</span></span>  
  
-   <span data-ttu-id="22da7-106">长度至少有 8 个字符。</span><span class="sxs-lookup"><span data-stu-id="22da7-106">Is at least 8 characters long.</span></span>  
  
-   <span data-ttu-id="22da7-107">密码中组合使用字母、数字和符号字符。</span><span class="sxs-lookup"><span data-stu-id="22da7-107">Combines letters, numbers, and symbol characters within the password.</span></span>  
  
-   <span data-ttu-id="22da7-108">字典中查不到。</span><span class="sxs-lookup"><span data-stu-id="22da7-108">Is not found in a dictionary.</span></span>  
  
-   <span data-ttu-id="22da7-109">不是命令名。</span><span class="sxs-lookup"><span data-stu-id="22da7-109">Is not the name of a command.</span></span>  
  
-   <span data-ttu-id="22da7-110">不是人名。</span><span class="sxs-lookup"><span data-stu-id="22da7-110">Is not the name of a person.</span></span>  
  
-   <span data-ttu-id="22da7-111">不是用户名。</span><span class="sxs-lookup"><span data-stu-id="22da7-111">Is not the name of a user.</span></span>  
  
-   <span data-ttu-id="22da7-112">不是计算机名。</span><span class="sxs-lookup"><span data-stu-id="22da7-112">Is not the name of a computer.</span></span>  
  
-   <span data-ttu-id="22da7-113">定期更改。</span><span class="sxs-lookup"><span data-stu-id="22da7-113">Is changed regularly.</span></span>  
  
-   <span data-ttu-id="22da7-114">与以前的密码明显不同。</span><span class="sxs-lookup"><span data-stu-id="22da7-114">Is significantly different from previous passwords.</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="22da7-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 密码最多可包含 128 个字符，其中包括字母、符号和数字。</span><span class="sxs-lookup"><span data-stu-id="22da7-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] passwords can contain up to 128 characters, including letters, symbols, and digits.</span></span> <span data-ttu-id="22da7-116">由于在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中经常使用登录名、用户名、角色和密码，所以必须用英文双引号 (") 或方括号 ([ ]) 括起某些符号。</span><span class="sxs-lookup"><span data-stu-id="22da7-116">Because logins, user names, roles, and passwords are frequently used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, certain symbols must be enclosed by double quotation marks (") or square brackets ([ ]).</span></span> <span data-ttu-id="22da7-117">如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 登录名、用户、角色或密码具有以下特征，请在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 语句中使用以下分隔符：</span><span class="sxs-lookup"><span data-stu-id="22da7-117">Use these delimiters in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login, user, role, or password has the following characteristics:</span></span>  
  
-   <span data-ttu-id="22da7-118">含有空格或以空格开头。</span><span class="sxs-lookup"><span data-stu-id="22da7-118">Contains or starts with a space character.</span></span>  
  
-   <span data-ttu-id="22da7-119">以 $ 或 \@ 字符开头。</span><span class="sxs-lookup"><span data-stu-id="22da7-119">Starts with the $ or \@ character.</span></span>  
  
 <span data-ttu-id="22da7-120">如果用于 OLE DB 或 ODBC 连接字符串，则登录名或密码不能包含以下字符：[] {}() , ; ?</span><span class="sxs-lookup"><span data-stu-id="22da7-120">If used in an OLE DB or ODBC connection string, a login or password must not contain the following characters: [] {}() , ; ?</span></span> <span data-ttu-id="22da7-121">\* !</span><span class="sxs-lookup"><span data-stu-id="22da7-121">\* !</span></span> <span data-ttu-id="22da7-122">\@.</span><span class="sxs-lookup"><span data-stu-id="22da7-122">\@.</span></span> <span data-ttu-id="22da7-123">这些字符用于初始化连接或分隔连接值。</span><span class="sxs-lookup"><span data-stu-id="22da7-123">These characters are used to either initialize a connection or separate connection values.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="22da7-124">相关内容</span><span class="sxs-lookup"><span data-stu-id="22da7-124">Related Content</span></span>  
 [<span data-ttu-id="22da7-125">密码策略</span><span class="sxs-lookup"><span data-stu-id="22da7-125">Password Policy</span></span>](password-policy.md)  
  
  
