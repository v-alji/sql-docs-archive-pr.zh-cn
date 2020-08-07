---
title: " (SSRS 本机模式) 的备份加密密钥 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.backupencryptionkey.F1
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d82a9b594e4a7ef7ceeb6737932e7e42a7f6fb74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586226"
---
# <a name="backup-encryption-key-ssrs-native-mode"></a><span data-ttu-id="d4b6d-102">备份加密密钥（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="d4b6d-102">Backup Encryption Key (SSRS Native Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d4b6d-103">使用加密密钥来保护存储在报表服务器数据库中的敏感数据。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-103">uses an encryption key to secure sensitive data that is stored in the report server database.</span></span> <span data-ttu-id="d4b6d-104">备份该密钥对于确保可继续访问连接字符串和凭据至关重要。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-104">Having a backup of this key is essential for ensuring continued access to encrypted connection strings and credentials.</span></span> <span data-ttu-id="d4b6d-105">如果将报表服务器数据库移动到其他计算机，或者更改报表服务器服务帐户的用户名或密码，则必须备份该密钥。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-105">You must have a backup copy of this key if you move the report server database to another computer or if you change the user name or password of the Report Server service account.</span></span> <span data-ttu-id="d4b6d-106">这两个操作均要求您从先前创建的备份副本还原密钥。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-106">Both operations require that you restore the key from a backup copy that you previously created.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="d4b6d-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="d4b6d-108">若要打开“备份加密密钥”对话框，请单击 **配置管理器导航窗格中的** “加密密钥” [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，然后单击 **“备份”**。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-108">To open the Backup Encryption Key dialog box, click **Encryption Keys** in the navigation pane of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, and then click **Backup**.</span></span> <span data-ttu-id="d4b6d-109">当使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器中的“服务帐户”页更新服务帐户时，也会显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-109">This dialog box also appears when you update the service account using the Service Account page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="d4b6d-110">有关 Configuration Manager 的详细信息 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，请参阅[Reporting Services 配置管理器 &#40;本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-110">For more information on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d4b6d-111">选项</span><span class="sxs-lookup"><span data-stu-id="d4b6d-111">Options</span></span>  
 <span data-ttu-id="d4b6d-112">**文件位置**</span><span class="sxs-lookup"><span data-stu-id="d4b6d-112">**File Location**</span></span>  
 <span data-ttu-id="d4b6d-113">为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 指定对称密钥的文件名和位置。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-113">Specify a file name and location for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to the symmetric key.</span></span> <span data-ttu-id="d4b6d-114">对称密钥决不能以纯文本形式存储。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-114">The symmetric key is never stored in plain text.</span></span> <span data-ttu-id="d4b6d-115">您必须键入密码来保护该文件。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-115">You must type a password to protect the file.</span></span>  
  
 <span data-ttu-id="d4b6d-116">**密码**</span><span class="sxs-lookup"><span data-stu-id="d4b6d-116">**Password**</span></span>  
 <span data-ttu-id="d4b6d-117">键入密码以防止对该文件进行未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-117">Type a password that protects the file against unauthorized access.</span></span> <span data-ttu-id="d4b6d-118">只有知道密码的用户才能还原封存在该文件中的密钥。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-118">Only users who know the password will be able to restore the key that is locked inside the file.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d4b6d-119">强制实施强密码策略。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-119">enforces a strong password policy.</span></span> <span data-ttu-id="d4b6d-120">密码必须至少包含 8 个字符，并且应由大小写字母数字字符和至少一个符号字符组合而成。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-120">The password must be at least 8 characters and include a combination of uppercase and lowercase alphanumeric characters and at least one symbol character.</span></span>  
  
 <span data-ttu-id="d4b6d-121">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="d4b6d-121">**Confirm Password**</span></span>  
 <span data-ttu-id="d4b6d-122">重新键入刚才输入的密码。</span><span class="sxs-lookup"><span data-stu-id="d4b6d-122">Re-type the password you entered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b6d-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4b6d-123">See Also</span></span>  
 <span data-ttu-id="d4b6d-124">[Reporting Services 配置管理器的 F1 帮助主题 &#40;SSRS 本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d4b6d-124">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="d4b6d-125">[备份和还原 Reporting Services 加密密钥](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="d4b6d-125">[Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="d4b6d-126">[删除和重新创建加密密钥（SSRS 配置管理器）](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="d4b6d-126">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="d4b6d-127">[初始化 Report Server（SSRS 配置管理器）](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="d4b6d-127">[Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span></span>  
 <span data-ttu-id="d4b6d-128">[存储加密的 Report Server 数据（SSRS 配置管理器）](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="d4b6d-128">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 [<span data-ttu-id="d4b6d-129">SSRS 本机模式 &#40;的加密密钥&#41;</span><span class="sxs-lookup"><span data-stu-id="d4b6d-129">Encryption Keys &#40;SSRS Native Mode&#41;</span></span>](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
