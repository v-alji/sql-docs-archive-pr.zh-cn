---
title: MSSQLSERVER 属性的协议（“证书”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.computermgr.cert.general.f1
helpviewer_keywords:
- MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
author: stevestein
ms.author: sstein
ms.openlocfilehash: 020d33eba7621f877f8622ca89dbd26a071f16a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692045"
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a><span data-ttu-id="4243e-102">MSSQLSERVER 属性的协议（“证书”选项卡）</span><span class="sxs-lookup"><span data-stu-id="4243e-102">Protocols for MSSQLSERVER Properties (Certificate Tab)</span></span>
  <span data-ttu-id="4243e-103">使用“MSSQLSERVER 协议的属性”  对话框中的“证书”  选项卡可以选择 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 证书，也可以查看证书的属性。</span><span class="sxs-lookup"><span data-stu-id="4243e-103">Use the **Certificate** tab on the **Protocols for MSSQLSERVER Properties** dialog box to select a certificate for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or to view the properties of a certificate.</span></span> <span data-ttu-id="4243e-104">在选择证书之前，所有字段均为空。</span><span class="sxs-lookup"><span data-stu-id="4243e-104">All fields are blank until a certificate is selected.</span></span>  
  
 <span data-ttu-id="4243e-105">用户的证书存储在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="4243e-105">Certificates are stored locally for the users on the computer.</span></span> <span data-ttu-id="4243e-106">若要加载供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用的证书，您必须在与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务所用的同一用户帐户下运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="4243e-106">To load a certificate for use by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager under the same user account as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
## <a name="page-header"></a><span data-ttu-id="4243e-107">页眉</span><span class="sxs-lookup"><span data-stu-id="4243e-107">Page Header</span></span>  
 <span data-ttu-id="4243e-108">**视图**</span><span class="sxs-lookup"><span data-stu-id="4243e-108">**View**</span></span>  
 <span data-ttu-id="4243e-109">通过它可以访问有关证书的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="4243e-109">Provides access to additional details on the certificate.</span></span> <span data-ttu-id="4243e-110">只有在 **“证书”** 框中选择某个证书后，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="4243e-110">Not available until a certificate is selected in the **Certificate** box.</span></span> <span data-ttu-id="4243e-111">有关证书详细信息的其他信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="4243e-111">For additional information on certificate details, see your [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
 <span data-ttu-id="4243e-112">**Clear**</span><span class="sxs-lookup"><span data-stu-id="4243e-112">**Clear**</span></span>  
 <span data-ttu-id="4243e-113">从“证书”框中删除所选证书。 </span><span class="sxs-lookup"><span data-stu-id="4243e-113">Removes the selection from the **Certificate** box.</span></span>  
  
 <span data-ttu-id="4243e-114">**证书**</span><span class="sxs-lookup"><span data-stu-id="4243e-114">**Certificate**</span></span>  
 <span data-ttu-id="4243e-115">由安全提供程序确定的证书名称。</span><span class="sxs-lookup"><span data-stu-id="4243e-115">Name of certificate as determined by security provider.</span></span> <span data-ttu-id="4243e-116">选择某个证书可以在属性网格中查看详细信息。</span><span class="sxs-lookup"><span data-stu-id="4243e-116">Select a certificate to see the details in the properties grid.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4243e-117">选项</span><span class="sxs-lookup"><span data-stu-id="4243e-117">Options</span></span>  
 <span data-ttu-id="4243e-118">过期日期</span><span class="sxs-lookup"><span data-stu-id="4243e-118">Expiration Date</span></span>  
 <span data-ttu-id="4243e-119">证书有效期最后一天的日期。</span><span class="sxs-lookup"><span data-stu-id="4243e-119">The final date for the period in which the certificate is valid.</span></span>  
  
 <span data-ttu-id="4243e-120">友好名称</span><span class="sxs-lookup"><span data-stu-id="4243e-120">Friendly Name</span></span>  
 <span data-ttu-id="4243e-121">获得证书的个人或证书颁发机构的友好名称或公用名称。</span><span class="sxs-lookup"><span data-stu-id="4243e-121">A friendly or common name for the individual or certification authority to whom the certificate is issued.</span></span>  
  
 <span data-ttu-id="4243e-122">颁发者</span><span class="sxs-lookup"><span data-stu-id="4243e-122">Issued By</span></span>  
 <span data-ttu-id="4243e-123">有关颁发证书的证书颁发机构的信息。</span><span class="sxs-lookup"><span data-stu-id="4243e-123">Information regarding the certification authority that issued the certificate.</span></span>  
  
 <span data-ttu-id="4243e-124">颁发给</span><span class="sxs-lookup"><span data-stu-id="4243e-124">Issued To</span></span>  
 <span data-ttu-id="4243e-125">有关证书接收者的信息。</span><span class="sxs-lookup"><span data-stu-id="4243e-125">Information regarding the recipient of the certificate.</span></span>  
  
  
