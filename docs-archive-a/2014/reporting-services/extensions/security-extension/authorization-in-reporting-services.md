---
title: Reporting Services 中的授权 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- authorization [Reporting Services]
ms.assetid: 15fc1c7b-560c-4737-b126-e0d428a1b530
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7420b45175ca0b0a5fc66da4a7939b07b79c75b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587215"
---
# <a name="authorization-in-reporting-services"></a><span data-ttu-id="fd521-102">Reporting Services 中的授权</span><span class="sxs-lookup"><span data-stu-id="fd521-102">Authorization in Reporting Services</span></span>
  <span data-ttu-id="fd521-103">授权是指确定是否应为某个身份授予其请求的、针对报表服务器数据库的给定资源的访问权限的过程。</span><span class="sxs-lookup"><span data-stu-id="fd521-103">Authorization is the process of determining whether an identity should be granted the requested type of access to a given resource in the report server database.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fd521-104">使用基于角色的授权体系结构，根据用户的应用程序角色分配为用户授予针对给定资源的访问权限。</span><span class="sxs-lookup"><span data-stu-id="fd521-104">uses a role-based authorization architecture that grants a user access to a given resource based on the user's role assignment for the application.</span></span> <span data-ttu-id="fd521-105">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的安全扩展插件包含对一个授权组件的实现，该组件用于在报表服务器上对用户进行身份验证后授予用户访问权限。</span><span class="sxs-lookup"><span data-stu-id="fd521-105">Security extensions for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] contain an implementation of an authorization component that is used to grant access to users once they are authenticated on the report server.</span></span> <span data-ttu-id="fd521-106">在某一用户尝试通过 SOAP API 和通过 URL 访问对系统或报表服务器项执行操作时，调用授权。</span><span class="sxs-lookup"><span data-stu-id="fd521-106">Authorization is invoked when a user attempts to perform an operation on the system or a report server item through the SOAP API and via URL access.</span></span> <span data-ttu-id="fd521-107">这可以通过安全扩展接口**IAuthorizationExtension**来实现。</span><span class="sxs-lookup"><span data-stu-id="fd521-107">This is made possible through the security extension interface **IAuthorizationExtension**.</span></span> <span data-ttu-id="fd521-108">如前所述，所有扩展插件均继承自 IExtension，这是部署的所有扩展插件的基接口  。</span><span class="sxs-lookup"><span data-stu-id="fd521-108">As stated previously, all extensions inherit from **IExtension** the base interface for any extension that you deploy.</span></span> <span data-ttu-id="fd521-109">**IExtension**和**IAuthorizationExtension**是**microsoft.reportingservices.interfaces.dll**命名空间的成员。</span><span class="sxs-lookup"><span data-stu-id="fd521-109">**IExtension** and **IAuthorizationExtension** are members of the **Microsoft.ReportingServices.Interfaces** namespace.</span></span>

## <a name="checking-access"></a><span data-ttu-id="fd521-110">检查访问</span><span class="sxs-lookup"><span data-stu-id="fd521-110">Checking Access</span></span>
 <span data-ttu-id="fd521-111">在授权中，任何自定义安全实现的关键环节都是访问权限检查，访问权限检查是在 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 方法中实现的。</span><span class="sxs-lookup"><span data-stu-id="fd521-111">In authorization, the key to any custom security implementation is the access check, which is implemented in the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method.</span></span> <span data-ttu-id="fd521-112">每当用户尝试对报表服务器执行操作时，就会调用 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>。</span><span class="sxs-lookup"><span data-stu-id="fd521-112"><xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> is called each time a user attempts an operation on the report server.</span></span> <span data-ttu-id="fd521-113">为每个操作类型都将重载 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="fd521-113">The <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method is overloaded for each operation type.</span></span> <span data-ttu-id="fd521-114">对于文件夹操作，访问检查的示例可能如下：</span><span class="sxs-lookup"><span data-stu-id="fd521-114">For folder operations, an example of an access check might look like the following:</span></span>

```
// Overload for Folder operations
public bool CheckAccess(
   string userName, 
   IntPtr userToken, 
   byte[] secDesc, 
   FolderOperation requiredOperation)
{
   // If the user is the administrator, allow unrestricted access.
   if (userName == m_adminUserName) 
      return true;

   AceCollection acl = DeserializeAcl(secDesc);
   foreach(AceStruct ace in acl)
   {
         if (userName == ace.PrincipalName)
         {
            foreach(FolderOperation aclOperation in 
               ace.FolderOperations)
            {
               if (aclOperation == requiredOperation)
                     return true;
            }
         }
   }
   return false;
}
```

 <span data-ttu-id="fd521-115">通过传入登录用户的名称、用户标记、项的安全描述符和请求的操作，报表服务器调用 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="fd521-115">The report server calls the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method by passing in the name of the logged-on user, a user token, the security descriptor for the item, and the requested operation.</span></span> <span data-ttu-id="fd521-116">在此处，您将检查用户名的安全描述符和相应权限以完成该请求，然后返回 `true` 以指示授予访问，或者返回 `false` 以指示拒绝访问。</span><span class="sxs-lookup"><span data-stu-id="fd521-116">Here you would check the security descriptor for the user name and the appropriate permission to complete the request, then return `true` to signify that access is granted or `false` to signify access is denied.</span></span>

## <a name="security-descriptors"></a><span data-ttu-id="fd521-117">安全描述符</span><span class="sxs-lookup"><span data-stu-id="fd521-117">Security Descriptors</span></span>
 <span data-ttu-id="fd521-118">在设置针对报表服务器数据库中的项的授权策略时，客户端应用程序（例如报表管理器）会将用户信息提交到安全扩展插件，同时提交用于该项的安全策略。</span><span class="sxs-lookup"><span data-stu-id="fd521-118">When setting authorization policies on items in the report server database, a client application (such as Report Manager) submits the user information to the security extension along with a security policy for the item.</span></span> <span data-ttu-id="fd521-119">此安全策略和用户信息统称为安全描述符。</span><span class="sxs-lookup"><span data-stu-id="fd521-119">This security policy and user information are known collectively as a security descriptor.</span></span> <span data-ttu-id="fd521-120">安全描述符包含报表服务器数据库中某一项的以下信息：</span><span class="sxs-lookup"><span data-stu-id="fd521-120">A security descriptor contains the following information for an item in the report server database:</span></span>

-   <span data-ttu-id="fd521-121">具有对项执行操作所需的某一类型权限的组或用户。</span><span class="sxs-lookup"><span data-stu-id="fd521-121">The group or user that has some type of permission to perform operations on the item.</span></span>

-   <span data-ttu-id="fd521-122">项的类型。</span><span class="sxs-lookup"><span data-stu-id="fd521-122">The item's type.</span></span>

-   <span data-ttu-id="fd521-123">控制对项的访问的任意访问控制列表。</span><span class="sxs-lookup"><span data-stu-id="fd521-123">A discretionary access control list controlling access to the item.</span></span>

 <span data-ttu-id="fd521-124">安全描述符是使用 Web 服务 <xref:ReportService2010.ReportingService2010.SetPolicies%2A> 和 <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> 方法创建的。</span><span class="sxs-lookup"><span data-stu-id="fd521-124">Security descriptors are created using the Web service <xref:ReportService2010.ReportingService2010.SetPolicies%2A> and <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> methods.</span></span>

### <a name="authorization-flow"></a><span data-ttu-id="fd521-125">授权流程</span><span class="sxs-lookup"><span data-stu-id="fd521-125">Authorization Flow</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fd521-126">授权由当前配置为在服务器上运行的安全扩展插件控制。</span><span class="sxs-lookup"><span data-stu-id="fd521-126">authorization is controlled by the security extension currently configured to run on the server.</span></span> <span data-ttu-id="fd521-127">授权是基于角色的，并且限制为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 安全体系结构提供的权限和操作。</span><span class="sxs-lookup"><span data-stu-id="fd521-127">Authorization is role-based and limited to the permissions and operations supplied by the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security architecture.</span></span> <span data-ttu-id="fd521-128">下图描述授权用户对报表服务器数据库中的项执行操作的流程：</span><span class="sxs-lookup"><span data-stu-id="fd521-128">The following diagram depicts the process of authorizing users to operate on items in the report server database:</span></span>

 <span data-ttu-id="fd521-129">![Reporting Services 安全授权流程](../../media/rosettasecurityextensionauthorizationflow.gif "Reporting Services 安全授权流程")</span><span class="sxs-lookup"><span data-stu-id="fd521-129">![Reporting Services security authorization flow](../../media/rosettasecurityextensionauthorizationflow.gif "Reporting Services security authorization flow")</span></span>

 <span data-ttu-id="fd521-130">如此图中所示，授权采用以下顺序：</span><span class="sxs-lookup"><span data-stu-id="fd521-130">As shown in this diagram, authorization follows this sequence:</span></span>

1.  <span data-ttu-id="fd521-131">一旦进行身份验证后，客户端应用程序通过 Reporting Services Web 服务方法对报表服务器进行请求。</span><span class="sxs-lookup"><span data-stu-id="fd521-131">Once authenticated, client applications make requests to the report server through the Reporting Services Web service methods.</span></span> <span data-ttu-id="fd521-132">身份验证票证将在每个 Web 请求的 HTTP 标头中以 cookie 的形式传递到报表服务器中。</span><span class="sxs-lookup"><span data-stu-id="fd521-132">An authentication ticket is passed to the report server in the form of a cookie in the HTTP header of each Web request.</span></span>

2.  <span data-ttu-id="fd521-133">将在任何访问检查前验证该 cookie。</span><span class="sxs-lookup"><span data-stu-id="fd521-133">The cookie is validated prior to any access check.</span></span>

3.  <span data-ttu-id="fd521-134">一旦对 cookie 进行验证后，报表服务器将调用 <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> 并且向用户授予某一身份。</span><span class="sxs-lookup"><span data-stu-id="fd521-134">Once the cookie is validated, the report server calls <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> and the user is given an identity.</span></span>

4.  <span data-ttu-id="fd521-135">用户尝试通过 Reporting Services Web 服务执行某一操作。</span><span class="sxs-lookup"><span data-stu-id="fd521-135">The user attempts an operation through the Reporting Services Web service.</span></span>

5.  <span data-ttu-id="fd521-136">报表服务器调用 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="fd521-136">The report server calls the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method.</span></span>

6.  <span data-ttu-id="fd521-137">安全描述符被检索并传递到 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 的自定义安全扩展插件实现中。</span><span class="sxs-lookup"><span data-stu-id="fd521-137">The security descriptor is retrieved and passed to a custom security extension implementation of <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>.</span></span> <span data-ttu-id="fd521-138">此时，用户、组或计算机将与要访问的项的安全描述符进行比较，然后授权它们执行请求的操作。</span><span class="sxs-lookup"><span data-stu-id="fd521-138">At this point, the user, group, or computer is compared to the security descriptor of the item being accessed and is authorized to perform the requested operation.</span></span>

7.  <span data-ttu-id="fd521-139">如果已对用户授权，则 Web 服务将执行请求的操作并向调用应用程序返回响应。</span><span class="sxs-lookup"><span data-stu-id="fd521-139">If the user is authorized, the Web service performs the operation and returns a response to the calling application.</span></span>


