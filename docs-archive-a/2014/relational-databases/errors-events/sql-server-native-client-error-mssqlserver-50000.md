---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3cc805042bff7259a311ca3f2acf4c26db59381b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689916"
---
# <a name="mssqlserver_50000"></a><span data-ttu-id="04971-102">MSSQLSERVER_50000</span><span class="sxs-lookup"><span data-stu-id="04971-102">MSSQLSERVER_50000</span></span>
    
## <a name="details"></a><span data-ttu-id="04971-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="04971-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04971-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="04971-104">Product Name</span></span>|<span data-ttu-id="04971-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="04971-105">SQL Server</span></span>|  
|<span data-ttu-id="04971-106">产品版本</span><span class="sxs-lookup"><span data-stu-id="04971-106">Product Version</span></span>|<span data-ttu-id="04971-107">11.0</span><span class="sxs-lookup"><span data-stu-id="04971-107">11.0</span></span>|  
|<span data-ttu-id="04971-108">事件 ID</span><span class="sxs-lookup"><span data-stu-id="04971-108">Event ID</span></span>|<span data-ttu-id="04971-109">50000</span><span class="sxs-lookup"><span data-stu-id="04971-109">50000</span></span>|  
|<span data-ttu-id="04971-110">事件源</span><span class="sxs-lookup"><span data-stu-id="04971-110">Event Source</span></span>|<span data-ttu-id="04971-111">SETUP</span><span class="sxs-lookup"><span data-stu-id="04971-111">SETUP</span></span>|  
|<span data-ttu-id="04971-112">组件</span><span class="sxs-lookup"><span data-stu-id="04971-112">Component</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="04971-113">Native Client</span><span class="sxs-lookup"><span data-stu-id="04971-113">Native Client</span></span>|  
|<span data-ttu-id="04971-114">符号名称</span><span class="sxs-lookup"><span data-stu-id="04971-114">Symbolic Name</span></span>||  
|<span data-ttu-id="04971-115">消息正文</span><span class="sxs-lookup"><span data-stu-id="04971-115">Message Text</span></span>|<span data-ttu-id="04971-116">尝试从文件“%.\*ls”中读取内容时出现网络错误。</span><span class="sxs-lookup"><span data-stu-id="04971-116">A network error occurred while attempting to read from the file '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="04971-117">说明</span><span class="sxs-lookup"><span data-stu-id="04971-117">Explanation</span></span>  
 <span data-ttu-id="04971-118">尝试在满足以下条件的计算机上安装（或更新） [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client：已安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client，并且现有安装是来自从 sqlncli.msi 重命名的 MSI 文件。</span><span class="sxs-lookup"><span data-stu-id="04971-118">An attempt was made to install (or update) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client on a computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is already installed, and where the existing installation was from an MSI file that was renamed from sqlncli.msi.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="04971-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="04971-119">User Action</span></span>  
 <span data-ttu-id="04971-120">若要解决此错误，请卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 的现有版本。</span><span class="sxs-lookup"><span data-stu-id="04971-120">To resolve this error, uninstall the existing version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="04971-121">若要防止此错误，请不要从未命名为 sqlncli.msi 的 MSI 文件安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="04971-121">To prevent this error, do not install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client from an MSI file that is not named sqlncli.msi.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="04971-122">仅内部</span><span class="sxs-lookup"><span data-stu-id="04971-122">Internal-Only</span></span>  
  
