---
title: 连接到 Microsoft SQL Server Analysis Services (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserveras.f1
ms.assetid: 7f3244ee-b690-471c-893d-68e361c2d416
author: minewiskan
ms.author: owend
ms.openlocfilehash: 984979480e3ea54c86c986fa6dd9771aaf879cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579192"
---
# <a name="connect-to-microsoft-sql-server-analysis-services-ssas"></a><span data-ttu-id="2425d-102">连接到 Microsoft SQL Server Analysis Services (SSAS)</span><span class="sxs-lookup"><span data-stu-id="2425d-102">Connect to Microsoft SQL Server Analysis Services (SSAS)</span></span>
  <span data-ttu-id="2425d-103">"**表导入向导**" 的这一页可用于指定设置以从 Microsoft SQL Server Analysis Services 多维数据集或在 SharePoint 上承载的 PowerPivot 工作簿导入数据。</span><span class="sxs-lookup"><span data-stu-id="2425d-103">This page of the **Table Import Wizard** enables you to specify settings to import data from a Microsoft SQL Server Analysis Services cube or a PowerPivot workbook that is hosted on SharePoint.</span></span> <span data-ttu-id="2425d-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="2425d-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="2425d-105">若要连接到数据源，必须在计算机上安装适当的访问接口。</span><span class="sxs-lookup"><span data-stu-id="2425d-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2425d-106">在此页中选择数据库时，将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="2425d-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="2425d-107">但是，如果在“模拟信息”页中指定的用户没有足够的权限从所选数据库中读取，则导入将不会成功。</span><span class="sxs-lookup"><span data-stu-id="2425d-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="2425d-108">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="2425d-108">UI element list</span></span>  
 <span data-ttu-id="2425d-109">**友好的连接名称**</span><span class="sxs-lookup"><span data-stu-id="2425d-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="2425d-110">键入此数据源连接的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="2425d-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="2425d-111">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="2425d-111">This is a required field.</span></span>  
  
 <span data-ttu-id="2425d-112">**服务器名或文件名**</span><span class="sxs-lookup"><span data-stu-id="2425d-112">**Server or File Name**</span></span>  
 <span data-ttu-id="2425d-113">输入下列项之一：</span><span class="sxs-lookup"><span data-stu-id="2425d-113">Enter one of the following:</span></span>  
  
-   <span data-ttu-id="2425d-114">键入要连接到的 SQL Server Analysis Services 服务器的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="2425d-114">Type the name or IP address of the SQL Server Analysis Services server to connect to.</span></span>  
  
     <span data-ttu-id="2425d-115">可以使用句点 (.)、(local) 或 localhost 来指示本地服务器。</span><span class="sxs-lookup"><span data-stu-id="2425d-115">You can use a period (.), (local), or localhost to indicate the local server.</span></span>  
  
-   <span data-ttu-id="2425d-116">键入发布到 SharePoint 的 PowerPivot 工作簿的 URL。</span><span class="sxs-lookup"><span data-stu-id="2425d-116">Type the URL of a PowerPivot workbook that is published to SharePoint.</span></span>  
  
 <span data-ttu-id="2425d-117">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="2425d-117">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="2425d-118">指定是否使用 Windows 身份验证来连接到 SQL Server Analysis Services server。</span><span class="sxs-lookup"><span data-stu-id="2425d-118">Specify whether Windows Authentication is used to connect to a SQL Server Analysis Services server.</span></span>  
  
 <span data-ttu-id="2425d-119">Windows 身份验证模式允许用户通过 Windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="2425d-119">Windows Authentication mode enables a user to connect through a Windows user account.</span></span> <span data-ttu-id="2425d-120">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="2425d-120">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="2425d-121">在使用 Windows 身份验证时，在“表格属性”窗口和“导入向导”中预览和筛选数据时，也使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="2425d-121">When Windows Authentication is used, the credentials of the current user are used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="2425d-122">这些凭据不用于导入或刷新数据；而是使用在“模拟信息”页中指定的 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="2425d-122">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="2425d-123">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="2425d-123">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="2425d-124">指定是否使用 SQL Server 身份验证来连接到 SQL Server Analysis Services server。</span><span class="sxs-lookup"><span data-stu-id="2425d-124">Specify whether SQL Server Authentication is used to connect to a SQL Server Analysis Services server.</span></span>  
  
 <span data-ttu-id="2425d-125">若使用 SQL Server 身份验证，SQL Server 将通过检查是否已设置 SQL Server 登录帐户以及指定的密码是否与以前记录的密码匹配，自行进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2425d-125">With SQL Server Authentication, SQL Server performs the authentication itself by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span>  
  
 <span data-ttu-id="2425d-126">使用 SQL Server 身份验证构造数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="2425d-126">SQL Server Authentication is used to construct the connection string for the data source.</span></span> <span data-ttu-id="2425d-127">在“表格属性”窗口和“导入向导”中预览和筛选数据时，也使用这些凭据。</span><span class="sxs-lookup"><span data-stu-id="2425d-127">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="2425d-128">这些凭据不用于导入或刷新数据；而是使用在“模拟信息”页中指定的 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="2425d-128">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="2425d-129">**用户名**</span><span class="sxs-lookup"><span data-stu-id="2425d-129">**User name**</span></span>  
 <span data-ttu-id="2425d-130">为数据库连接指定用户名。</span><span class="sxs-lookup"><span data-stu-id="2425d-130">Specify a user name for the database connection.</span></span> <span data-ttu-id="2425d-131">只有在已选择使用 Windows 身份验证进行连接的情况下，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="2425d-131">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="2425d-132">**密码**</span><span class="sxs-lookup"><span data-stu-id="2425d-132">**Password**</span></span>  
 <span data-ttu-id="2425d-133">为数据库连接指定密码。</span><span class="sxs-lookup"><span data-stu-id="2425d-133">Specify a password for the database connection.</span></span> <span data-ttu-id="2425d-134">只有在已选择使用 SQL Server 身份验证进行连接的情况下，此选项才是可编辑的。</span><span class="sxs-lookup"><span data-stu-id="2425d-134">This option is only editable if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="2425d-135">**保存密码**</span><span class="sxs-lookup"><span data-stu-id="2425d-135">**Save my password**</span></span>  
 <span data-ttu-id="2425d-136">指定是否存储已在“密码”\*\*\*\* 框中输入的密码。</span><span class="sxs-lookup"><span data-stu-id="2425d-136">Specify whether the password you have entered in the **Password** box is stored.</span></span> <span data-ttu-id="2425d-137">只有在已选择使用 SQL Server 身份验证进行连接的情况下，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="2425d-137">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="2425d-138">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="2425d-138">**Database name**</span></span>  
 <span data-ttu-id="2425d-139">从数据库列表中选择数据库。</span><span class="sxs-lookup"><span data-stu-id="2425d-139">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="2425d-140">**高级**</span><span class="sxs-lookup"><span data-stu-id="2425d-140">**Advanced**</span></span>  
 <span data-ttu-id="2425d-141">使用 "**设置高级属性**" 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="2425d-141">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="2425d-142">有关详细信息，请参阅[设置高级属性 (SSAS)](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="2425d-142">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="2425d-143">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="2425d-143">**Test Connection**</span></span>  
 <span data-ttu-id="2425d-144">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="2425d-144">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="2425d-145">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="2425d-145">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
