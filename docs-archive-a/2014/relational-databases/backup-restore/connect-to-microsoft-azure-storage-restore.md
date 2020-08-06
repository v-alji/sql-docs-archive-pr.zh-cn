---
title: " (Restore) 连接到 Azure 存储 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dff9730d6592381b1c8e8a1cf7ee45ad7532a440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591412"
---
# <a name="connect-to-azure-storage-restore"></a><span data-ttu-id="ff1a4-102">连接到 Azure 存储（还原）</span><span class="sxs-lookup"><span data-stu-id="ff1a4-102">Connect to Azure Storage (Restore)</span></span>
  <span data-ttu-id="ff1a4-103">可使用该对话框来指定与 Azure 存储帐户信息的连接，以便检索 Azure 存储帐户中的文件存储。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-103">The dialog box allows you to specify the connection to Azure storage account information in order to retrieve the files storage in the Azure storage account.</span></span> <span data-ttu-id="ff1a4-104">在指定所需信息后，请单击“连接”  以与 Azure 存储建立连接。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-104">After specifying the required information, click **Connect** to establish the connection to Azure storage.</span></span>  
  
## <a name="azure-storage-account"></a><span data-ttu-id="ff1a4-105">Azure 存储帐户</span><span class="sxs-lookup"><span data-stu-id="ff1a4-105">Azure Storage Account</span></span>  
 <span data-ttu-id="ff1a4-106">**存储帐户**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-106">**Storage account**</span></span>  
 <span data-ttu-id="ff1a4-107">选择、键入或粘贴要使用的 Azure 存储帐户名称。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-107">Select, type or paste the name of the Azure storage account you want to use.</span></span> <span data-ttu-id="ff1a4-108">下拉框会列出以前使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-108">The drop down box lists the accounts previously used.</span></span>  
  
 <span data-ttu-id="ff1a4-109">**帐户密钥**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-109">**Account key**</span></span>  
 <span data-ttu-id="ff1a4-110">指定 Azure 存储帐户访问密钥。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-110">Specify the Azure storage account access key.</span></span>  
  
 <span data-ttu-id="ff1a4-111">**使用安全端点 (HTTPS)** 复选框</span><span class="sxs-lookup"><span data-stu-id="ff1a4-111">**Use secure endpoints (HTTPS)** check box</span></span>  
 <span data-ttu-id="ff1a4-112">选择此选项可与 Azure 存储建立安全连接（建议使用）。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-112">Select this option to make a secure connection to Azure storage - recommended.</span></span>  
  
 <span data-ttu-id="ff1a4-113">**保存帐户密钥** 复选框</span><span class="sxs-lookup"><span data-stu-id="ff1a4-113">**Save account key** check box</span></span>  
 <span data-ttu-id="ff1a4-114">如果希望 SQL Server 记住此存储帐户的访问密钥，请选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-114">Select this check box if you want SQL Server to remember the access key for this storage account.</span></span>  
  
### <a name="sql-credential"></a><span data-ttu-id="ff1a4-115">SQL 凭据</span><span class="sxs-lookup"><span data-stu-id="ff1a4-115">SQL Credential</span></span>  
 <span data-ttu-id="ff1a4-116">**选择现有凭据**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-116">**Select an existing credential**</span></span>  
 <span data-ttu-id="ff1a4-117">选择与存储帐户和帐户密钥信息匹配的现有 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-117">Select an existing SQL Credential that matches the storage account and account key information.</span></span>  
  
 <span data-ttu-id="ff1a4-118">**创建新凭据**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-118">**Create a new Credential**</span></span>  
 <span data-ttu-id="ff1a4-119">选择此选项可使用存储帐户和帐户密钥信息创建新的凭据。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-119">Select this option to create a new credential using the storage account and account key information.</span></span> <span data-ttu-id="ff1a4-120">在 **“凭据名称”** 字段中指定新凭据的名称。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-120">Specify the name of the new credential in the **Credential Name** field.</span></span>  
  
  
