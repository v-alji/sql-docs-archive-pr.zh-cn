---
title: 创建凭据 - 向 Azure 存储进行身份验证 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: afdbf2647c79e07cf3f190ec6710eeb6b7718f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692970"
---
# <a name="create-credential---authenticate-to-azure-storage"></a><span data-ttu-id="cfb5d-102">创建凭据 - 向 Azure 存储进行身份验证</span><span class="sxs-lookup"><span data-stu-id="cfb5d-102">Create Credential - Authenticate to Azure Storage</span></span>
  <span data-ttu-id="cfb5d-103">使用“备份到 URL - 创建凭据”对话框可创建新的 SQL 凭据  。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-103">Use the **Backup to URL - Create Credential** dialog box to create a new SQL Credential.</span></span>  
  
 <span data-ttu-id="cfb5d-104">使用此对话框创建凭据时，必须提供一个添加到本地证书存储的 Azure 管理证书，或一个已下载到计算机的发布配置文件，以验证订阅和存储帐户信息。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-104">When using this dialog box to create a credential, you must provide an Azure Management Certificate added to the local certificate store or a publishing profile downloaded to your computer to validate the subscription and the storage account information.</span></span>  
  
 <span data-ttu-id="cfb5d-105">**SQL 凭据**</span><span class="sxs-lookup"><span data-stu-id="cfb5d-105">**SQL Credential**</span></span>  
 <span data-ttu-id="cfb5d-106">指定要使用的 SQL 凭据的名称。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-106">Specify the name of the SQL Credential you want to create.</span></span>  
  
## <a name="azure-credentials"></a><span data-ttu-id="cfb5d-107">Azure 凭据</span><span class="sxs-lookup"><span data-stu-id="cfb5d-107">Azure Credentials</span></span>  
 <span data-ttu-id="cfb5d-108">**管理证书**</span><span class="sxs-lookup"><span data-stu-id="cfb5d-108">**Management Certificate**</span></span>  
 <span data-ttu-id="cfb5d-109">可使用此选项从本地证书存储指定与 Azure 管理证书匹配的证书。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-109">Use this option to specify a certificate from the local certificate store that matches the management certificate from Azure.</span></span> <span data-ttu-id="cfb5d-110">有关 Azure 管理证书的详细信息，请参阅[创建并上载 Azure 的管理证书](https://go.microsoft.com/fwlink/?LinkId=320781)。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-110">For more information on Azure management certificate, see [Create and Upload a Management Certificate for Azure](https://go.microsoft.com/fwlink/?LinkId=320781).</span></span>  
  
 <span data-ttu-id="cfb5d-111">**订阅**</span><span class="sxs-lookup"><span data-stu-id="cfb5d-111">**Subscription**</span></span>  
 <span data-ttu-id="cfb5d-112">选择、键入或粘贴与本地证书存储中的管理证书匹配的 Azure 订阅 ID。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-112">Select, type, or paste your Azure subscription ID that matches the management certificate from the local certificate store.</span></span>  
  
 <span data-ttu-id="cfb5d-113">**发布配置文件**</span><span class="sxs-lookup"><span data-stu-id="cfb5d-113">**Publishing Profile**</span></span>  
 <span data-ttu-id="cfb5d-114">如果您有下载到计算机的发布配置文件，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-114">Use this option if you have a publishing profile downloaded to your computer.</span></span> <span data-ttu-id="cfb5d-115">如果您使用此选项，则订阅 ID 和证书将自动填充。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-115">If you use this option, the subscription ID, and the certificate are auto populated.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="cfb5d-116">SQL Server 当前支持发布配置文件版本 2.0。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-116">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="cfb5d-117">要下载支持的发布配置文件版本，请参阅 [下载发布配置文件 2.0](https://go.microsoft.com/fwlink/?LinkId=396421)。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-117">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
  
## <a name="storage-account"></a><span data-ttu-id="cfb5d-118">存储帐户</span><span class="sxs-lookup"><span data-stu-id="cfb5d-118">Storage Account</span></span>  
 <span data-ttu-id="cfb5d-119">选择要用于存储备份文件的存储帐户。</span><span class="sxs-lookup"><span data-stu-id="cfb5d-119">Select the storage account you want to use to store the backup files on.</span></span>  
  
  
