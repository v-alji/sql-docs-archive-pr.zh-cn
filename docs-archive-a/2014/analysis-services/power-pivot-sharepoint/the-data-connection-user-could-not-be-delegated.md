---
title: 数据连接使用 Windows 身份验证并且无法对用户凭据进行委托。 以下连接无法刷新： PowerPivot 数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
author: minewiskan
ms.author: owend
ms.openlocfilehash: be4c61ad4514f3aa4f6f1eda1fe44ad97c4c064f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580442"
---
# <a name="the-data-connection-uses-windows-authentication-and-user-credentials-could-not-be-delegated-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="79923-103">数据连接使用 Windows 身份验证并且无法对用户凭据进行委托。</span><span class="sxs-lookup"><span data-stu-id="79923-103">The data connection uses Windows Authentication and user credentials could not be delegated.</span></span> <span data-ttu-id="79923-104">以下连接无法刷新：PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="79923-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="79923-105">对于包含 PowerPivot 数据的 Excel 工作簿，如果 Excel Services 无法连接到 SharePoint 中的 PowerPivot 服务器实例，则会返回此错误。</span><span class="sxs-lookup"><span data-stu-id="79923-105">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it cannot connect to a PowerPivot server instance in SharePoint.</span></span>  
  
## <a name="details"></a><span data-ttu-id="79923-106">详细信息</span><span class="sxs-lookup"><span data-stu-id="79923-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79923-107">适用于</span><span class="sxs-lookup"><span data-stu-id="79923-107">Applies to</span></span>|<span data-ttu-id="79923-108">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="79923-108">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="79923-109">产品版本</span><span class="sxs-lookup"><span data-stu-id="79923-109">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="79923-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79923-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="79923-111">原因</span><span class="sxs-lookup"><span data-stu-id="79923-111">Cause</span></span>|<span data-ttu-id="79923-112">在尝试使用 PowerPivot 数据访问接口时出现连接错误。</span><span class="sxs-lookup"><span data-stu-id="79923-112">Connection failed when attempting to use a PowerPivot data provider.</span></span>|  
|<span data-ttu-id="79923-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="79923-113">Message Text</span></span>|<span data-ttu-id="79923-114">数据连接使用 Windows 身份验证并且无法对用户凭据进行委托。</span><span class="sxs-lookup"><span data-stu-id="79923-114">The data connection uses Windows Authentication and user credentials could not be delegated.</span></span> <span data-ttu-id="79923-115">以下连接无法刷新：PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="79923-115">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="79923-116">说明</span><span class="sxs-lookup"><span data-stu-id="79923-116">Explanation</span></span>  
 <span data-ttu-id="79923-117">有多个原因会导致出现此错误消息。</span><span class="sxs-lookup"><span data-stu-id="79923-117">There are multiple causes for this error message.</span></span> <span data-ttu-id="79923-118">但所有这些原因都具有一个共性，就是 Excel Services 无法从 SharePoint 的声明令牌中获取有效的 Windows 用户标识。</span><span class="sxs-lookup"><span data-stu-id="79923-118">The common factor behind all of them is that Excel Services cannot get a valid Windows user identity from a claims token in SharePoint.</span></span> <span data-ttu-id="79923-119">在 Excel 工作簿包含 PowerPivot 数据时，如果以下任何条件成立，都会出现此错误：</span><span class="sxs-lookup"><span data-stu-id="79923-119">In the case of Excel workbooks that contain PowerPivot data, this error occurs when any of the following conditions exist:</span></span>  
  
-   <span data-ttu-id="79923-120">Claims to Windows Token Service 未运行。</span><span class="sxs-lookup"><span data-stu-id="79923-120">The Claims to Windows Token Service is not running.</span></span> <span data-ttu-id="79923-121">您可以通过查看 SharePoint 日志文件确认导致此错误的原因。</span><span class="sxs-lookup"><span data-stu-id="79923-121">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="79923-122">如果 SharePoint 日志包括消息“The pipe endpoint 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' could not be found on your local machine”，则 Claims to Windows Token Service 未运行。</span><span class="sxs-lookup"><span data-stu-id="79923-122">If the SharePoint logs include the message "The pipe endpoint 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' could not be found on your local machine", the Claims to Windows Token Service is not running.</span></span> <span data-ttu-id="79923-123">若要启动该服务，请使用管理中心，然后在“服务”控制台应用程序中确认该服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="79923-123">To start it, use Central Administration and then verify the service is running in the Services console application.</span></span>  
  
-   <span data-ttu-id="79923-124">域控制器不可用于确认用户标识。</span><span class="sxs-lookup"><span data-stu-id="79923-124">A domain controller is not available to validate the user identity.</span></span> <span data-ttu-id="79923-125">Claims to Windows Token Service 不使用缓存凭据。</span><span class="sxs-lookup"><span data-stu-id="79923-125">The Claims to Windows Token Service does not use cached credentials.</span></span> <span data-ttu-id="79923-126">它会验证每个连接的用户标识。</span><span class="sxs-lookup"><span data-stu-id="79923-126">It validates the user identity for each connection.</span></span> <span data-ttu-id="79923-127">您可以通过查看 SharePoint 日志文件确认导致此错误的原因。</span><span class="sxs-lookup"><span data-stu-id="79923-127">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="79923-128">如果 SharePoint 日志包括消息“Failed to get WindowsIdentity from IClaimsIdentity”，则无法对该用户标识进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="79923-128">If the SharePoint logs include the message "Failed to get WindowsIdentity from IClaimsIdentity", the user identity could not be authenticated.</span></span>  
  
-   <span data-ttu-id="79923-129">计算机必须是同一域中的成员，或者必须处于具有双向信任关系的域中。</span><span class="sxs-lookup"><span data-stu-id="79923-129">The computers must be members of the same domain or in domains that have a two-way trust relationship.</span></span>  
  
-   <span data-ttu-id="79923-130">您必须使用 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="79923-130">You must use Windows domain user accounts.</span></span> <span data-ttu-id="79923-131">这些帐户必须具有通用主体名称 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="79923-131">The accounts must have a Universal Principal Name (UPN).</span></span>  
  
-   <span data-ttu-id="79923-132">Excel Services 服务帐户必须具有 Active Directory 权限以便查询对象。</span><span class="sxs-lookup"><span data-stu-id="79923-132">The Excel Services service account must have Active Directory permissions to query the object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="79923-133">用户操作</span><span class="sxs-lookup"><span data-stu-id="79923-133">User Action</span></span>  
 <span data-ttu-id="79923-134">使用以下说明可以查看 Claims to Windows Token Service 的状态。</span><span class="sxs-lookup"><span data-stu-id="79923-134">Use the following instructions to check the status of the Claims to Windows Token Service.</span></span>  
  
 <span data-ttu-id="79923-135">对于所有其他情况，请与您的网络管理员联系。</span><span class="sxs-lookup"><span data-stu-id="79923-135">For all other scenarios, check with your network administrator.</span></span>  
  
#### <a name="enable-claims-to-windows-token-service"></a><span data-ttu-id="79923-136">启用 Claims to Windows Token Service</span><span class="sxs-lookup"><span data-stu-id="79923-136">Enable Claims to Windows Token Service</span></span>  
  
1.  <span data-ttu-id="79923-137">在管理中心的 "系统设置" 中，单击 "**管理服务器上的服务**"。</span><span class="sxs-lookup"><span data-stu-id="79923-137">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="79923-138">选择 **“Claims to Windows Token Service”**，然后单击 **“开始”**。</span><span class="sxs-lookup"><span data-stu-id="79923-138">Select **Claims to Windows Token Service**, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="79923-139">验证服务是否也在“服务”控制台上运行：</span><span class="sxs-lookup"><span data-stu-id="79923-139">Verify the service is also running in the Services console:</span></span>  
  
    1.  <span data-ttu-id="79923-140">在“管理工具”中，单击“服务”。</span><span class="sxs-lookup"><span data-stu-id="79923-140">In Administrative Tools, click Services.</span></span>  
  
    2.  <span data-ttu-id="79923-141">如果 Claims to Windows Token Service 未运行，则启动它。</span><span class="sxs-lookup"><span data-stu-id="79923-141">Start the Claims to Windows Token Service if it is not running.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79923-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79923-142">See Also</span></span>  
 [<span data-ttu-id="79923-143">配置 PowerPivot 服务帐户</span><span class="sxs-lookup"><span data-stu-id="79923-143">Configure PowerPivot Service Accounts</span></span>](configure-power-pivot-service-accounts.md)  
  
  
