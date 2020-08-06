---
title: Reporting Services SharePoint 模式身份验证 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3b1316a1a49726ab0754f39160125425fec116d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692124"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a><span data-ttu-id="e2d3a-102">Reporting Services SharePoint 模式身份验证</span><span class="sxs-lookup"><span data-stu-id="e2d3a-102">Reporting Services SharePoint Mode Authentication</span></span>
  <span data-ttu-id="e2d3a-103">使用 \*\*\*\*[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 页可以指定在当前 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装中使用的服务帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-103">Use the **Reporting Services SharePoint Mode Authentication** page of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify the credentials of the service account that is used in the current [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span> <span data-ttu-id="e2d3a-104">这些凭据将用来创建新的 SharePoint 应用程序池。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-104">The credentials will be used to create a new SharePoint application pool.</span></span> <span data-ttu-id="e2d3a-105">此外，还将创建一个新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-105">Also, one new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service application will be created.</span></span> <span data-ttu-id="e2d3a-106">客户端应用程序名称将包含前一个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-106">The service application name will contain the name of the previous [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2d3a-107">选项</span><span class="sxs-lookup"><span data-stu-id="e2d3a-107">Options</span></span>  
  
-   <span data-ttu-id="e2d3a-108">**“SSRS 应用程序池帐户名称:”** 选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-108">The **SSRS Application Pool Account Name:** option is read only.</span></span> <span data-ttu-id="e2d3a-109">系统将自动使用来自您正在升级的现有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装中的当前值填充此值。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-109">The value is automatically populated with the current value from the existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation that you are upgrading.</span></span>  
  
-   <span data-ttu-id="e2d3a-110">如果应用程序池帐户不需要密码，则将禁用 **“SSRS 应用程序池帐户密码:”** 选项。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-110">The **SSRS Application Pool Account Password:** option will be disabled if the application pool account does not require a password.</span></span> <span data-ttu-id="e2d3a-111">例如，"NT Authority\NetworkService"。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-111">For example, "NT Authority\NetworkService".</span></span> <span data-ttu-id="e2d3a-112">如果应用程序池帐户的确需要密码，仅当您键入正确的密码，才能继续进行升级。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-112">If the application pool account does require a password, you cannot continue with upgrade until you type the correct password.</span></span>  
  
 <span data-ttu-id="e2d3a-113">有关详细信息，请参阅[升级和迁移 Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) (https://go.microsoft.com/fwlink/?LinkID=245628) 。</span><span class="sxs-lookup"><span data-stu-id="e2d3a-113">For more information, see [Upgrade and Migrate Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) (https://go.microsoft.com/fwlink/?LinkID=245628).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d3a-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2d3a-114">See Also</span></span>  
 [<span data-ttu-id="e2d3a-115">升级和迁移 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="e2d3a-115">Upgrade and Migrate Reporting Services</span></span>](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
