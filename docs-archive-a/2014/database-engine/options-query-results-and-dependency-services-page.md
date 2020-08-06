---
title: "\"查询结果\" 和 \"依赖关系服务\" 页)  (选项 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 356714ee933fb40eda7038f4088309b6187f3ed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589875"
---
# <a name="options-query-results-and-dependency-services-page"></a><span data-ttu-id="e8a13-102">选项（“查询结果”和“依赖关系服务”页）</span><span class="sxs-lookup"><span data-stu-id="e8a13-102">Options (Query Results and Dependency Services Page)</span></span>
  <span data-ttu-id="e8a13-103">使用此页可为依赖关系服务指定要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="e8a13-103">Use this page to specify the server to connect for Dependency Services.</span></span> <span data-ttu-id="e8a13-104">通过依赖关系服务，您可以提取与在不同服务器上存储的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象之间的依赖关系有关的信息。</span><span class="sxs-lookup"><span data-stu-id="e8a13-104">Dependency Services enables you to extract information about dependencies between [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects stored on different servers.</span></span> <span data-ttu-id="e8a13-105">您可以使用中的 "**对象依赖关系**" 对话框查看对象依赖关系 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e8a13-105">You view object dependencies by using the **Object Dependencies** dialog box in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="e8a13-106">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="e8a13-106">**What do you want to do?**</span></span>  
  
1.  [<span data-ttu-id="e8a13-107">打开“选项”（“查询结果”/“依赖关系服务”页）对话框</span><span class="sxs-lookup"><span data-stu-id="e8a13-107">Open the Options (Query Results/Dependency Services Page) Dialog Box</span></span>](#open_dialog)  
  
2.  [<span data-ttu-id="e8a13-108">配置选项</span><span class="sxs-lookup"><span data-stu-id="e8a13-108">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a><span data-ttu-id="e8a13-109">打开 "查询结果/依赖关系服务页)  (选项" 对话框</span><span class="sxs-lookup"><span data-stu-id="e8a13-109">Open the Options (Query Results/Dependency Services Page) Dialog Box</span></span>  
  
1.  <span data-ttu-id="e8a13-110">在中 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ，单击 "**工具**" 菜单上的 "**选项**"。</span><span class="sxs-lookup"><span data-stu-id="e8a13-110">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="e8a13-111">展开\*\*\*\*“查询结果”，然后单击\*\*\*\*“依赖关系服务”。</span><span class="sxs-lookup"><span data-stu-id="e8a13-111">Expand **Query Results**, and then click **Dependency Services**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="e8a13-112">配置选项</span><span class="sxs-lookup"><span data-stu-id="e8a13-112">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="e8a13-113">选项</span><span class="sxs-lookup"><span data-stu-id="e8a13-113">Options</span></span>  
 <span data-ttu-id="e8a13-114">**依赖关系服务服务器**</span><span class="sxs-lookup"><span data-stu-id="e8a13-114">**Dependency Services server**</span></span>  
 <span data-ttu-id="e8a13-115">指定安装依赖关系服务的服务器。</span><span class="sxs-lookup"><span data-stu-id="e8a13-115">Specify the server that Dependency Services is installed on.</span></span>  
  
 <span data-ttu-id="e8a13-116">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="e8a13-116">**Authentication**</span></span>  
 <span data-ttu-id="e8a13-117">选择 Windows 身份验证以便使用 Microsoft Windows 用户帐户登录，或者选择 SQL Server 身份验证。</span><span class="sxs-lookup"><span data-stu-id="e8a13-117">Select Windows Authentication to log on using a Microsoft Windows user account, or select SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="e8a13-118">当用户使用指定的登录名和密码从不可信连接进行连接时，SQL Server 将通过检查是否已设置 SQL Server 登录帐户以及指定的密码是否与以前记录的密码匹配，自行进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="e8a13-118">When a user connects with a specified login name and password from a non-trusted connection, SQL Server performs the authentication by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="e8a13-119">如果 SQL Server 找不到登录帐户，则身份验证会失败，用户将收到错误消息。</span><span class="sxs-lookup"><span data-stu-id="e8a13-119">If SQL Server cannot find the login account, authentication fails, and the user receives an error message.</span></span>  
  
 <span data-ttu-id="e8a13-120">**用户名**</span><span class="sxs-lookup"><span data-stu-id="e8a13-120">**User name**</span></span>  
 <span data-ttu-id="e8a13-121">如果使用 SQL Server 身份验证，请提供用户名。</span><span class="sxs-lookup"><span data-stu-id="e8a13-121">If using SQL Server Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="e8a13-122">**密码**</span><span class="sxs-lookup"><span data-stu-id="e8a13-122">**Password**</span></span>  
 <span data-ttu-id="e8a13-123">如果使用 SQL Server 身份验证，请提供密码。</span><span class="sxs-lookup"><span data-stu-id="e8a13-123">If using SQL Server Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="e8a13-124">**Test**</span><span class="sxs-lookup"><span data-stu-id="e8a13-124">**Test**</span></span>  
 <span data-ttu-id="e8a13-125">单击此选项可对连接进行测试。</span><span class="sxs-lookup"><span data-stu-id="e8a13-125">Click to test the connection.</span></span>