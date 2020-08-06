---
title: " (SSAS) 连接到 Microsoft SQL Server 数据库 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserverdb.f1
ms.assetid: 6ebfe029-dbba-4f0d-a556-328e79ef629f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 64267cd65836cf8e6c8d8b26a177de595894b601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579215"
---
# <a name="connect-to-a-microsoft-sql-server-database-ssas"></a><span data-ttu-id="95ccf-102">连接到 Microsoft SQL Server 数据库 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="95ccf-102">Connect to a Microsoft SQL Server Database (SSAS)</span></span>
  <span data-ttu-id="95ccf-103">**“表导入向导”** 的这一页可用于指定用于连接到 Microsoft SQL Server 数据库的设置。</span><span class="sxs-lookup"><span data-stu-id="95ccf-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft SQL Server database.</span></span> <span data-ttu-id="95ccf-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="95ccf-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="95ccf-105">若要连接到数据源，必须在计算机上安装适当的访问接口。</span><span class="sxs-lookup"><span data-stu-id="95ccf-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95ccf-106">在此页中选择数据库时，将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="95ccf-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="95ccf-107">但是，如果在“模拟信息”页中指定的用户没有足够的权限从所选数据库中读取，则导入将不会成功。</span><span class="sxs-lookup"><span data-stu-id="95ccf-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="95ccf-108">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="95ccf-108">UI element list</span></span>  
 <span data-ttu-id="95ccf-109">**友好的连接名称**</span><span class="sxs-lookup"><span data-stu-id="95ccf-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="95ccf-110">键入此数据源连接的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="95ccf-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="95ccf-111">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="95ccf-111">This is a required field.</span></span>  
  
 <span data-ttu-id="95ccf-112">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="95ccf-112">**Server name**</span></span>  
 <span data-ttu-id="95ccf-113">选择要连接到的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的名称或者键入其名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="95ccf-113">Select the name, or type the name or IP address, of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to connect to.</span></span>  
  
 <span data-ttu-id="95ccf-114">可以使用句点 (.)、(local) 或 localhost 来指示本地服务器。</span><span class="sxs-lookup"><span data-stu-id="95ccf-114">You can use a period (.), (local), or localhost to indicate the local server.</span></span>  
  
 <span data-ttu-id="95ccf-115">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="95ccf-115">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="95ccf-116">指定是否使用 Windows 身份验证来连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="95ccf-116">Specify whether Windows Authentication is used to connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="95ccf-117">Windows 身份验证模式允许用户通过使用 Windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="95ccf-117">Windows Authentication mode enables a user to connect by using a Windows user account.</span></span> <span data-ttu-id="95ccf-118">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="95ccf-118">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="95ccf-119">在使用 Windows 身份验证时，在“表格属性”窗口和“导入向导”中预览和筛选数据时，也使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="95ccf-119">When Windows Authentication is used, the credentials of the current user are used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="95ccf-120">这些凭据不用于导入或刷新数据；而是使用在“模拟信息”页中指定的 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="95ccf-120">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation information page are used instead.</span></span>  
  
 <span data-ttu-id="95ccf-121">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="95ccf-121">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="95ccf-122">指定是否使用 SQL Server 身份验证来连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="95ccf-122">Specify whether SQL Server Authentication is used to connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="95ccf-123">若使用 SQL Server 身份验证，SQL Server 将通过检查是否已设置 SQL Server 登录帐户以及指定的密码是否与以前记录的密码匹配，自行进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="95ccf-123">With SQL Server Authentication, SQL Server performs the authentication itself by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span>  
  
 <span data-ttu-id="95ccf-124">使用 SQL Server 身份验证构造数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="95ccf-124">SQL Server Authentication is used to construct the connection string for the data source.</span></span> <span data-ttu-id="95ccf-125">在“表格属性”窗口和“导入向导”中预览和筛选数据时，也使用这些凭据。</span><span class="sxs-lookup"><span data-stu-id="95ccf-125">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="95ccf-126">这些凭据不用于导入或刷新数据；而是使用在“模拟信息”页中指定的 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="95ccf-126">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="95ccf-127">**用户名**</span><span class="sxs-lookup"><span data-stu-id="95ccf-127">**User name**</span></span>  
 <span data-ttu-id="95ccf-128">为数据库连接指定用户名。</span><span class="sxs-lookup"><span data-stu-id="95ccf-128">Specify a user name for the database connection.</span></span> <span data-ttu-id="95ccf-129">只有在已选择使用 SQL Server 身份验证进行连接的情况下，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="95ccf-129">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="95ccf-130">**密码**</span><span class="sxs-lookup"><span data-stu-id="95ccf-130">**Password**</span></span>  
 <span data-ttu-id="95ccf-131">为数据库连接指定密码。</span><span class="sxs-lookup"><span data-stu-id="95ccf-131">Specify a password for the database connection.</span></span> <span data-ttu-id="95ccf-132">只有在已选择使用 SQL Server 身份验证进行连接的情况下，此选项才是可编辑的。</span><span class="sxs-lookup"><span data-stu-id="95ccf-132">This option is only editable if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="95ccf-133">**保存密码**</span><span class="sxs-lookup"><span data-stu-id="95ccf-133">**Save my password**</span></span>  
 <span data-ttu-id="95ccf-134">指定是否存储已在“密码”\*\*\*\* 框中输入的密码。</span><span class="sxs-lookup"><span data-stu-id="95ccf-134">Specify whether the password you have entered in the **Password** box is stored.</span></span> <span data-ttu-id="95ccf-135">只有在已选择使用 SQL Server 身份验证进行连接的情况下，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="95ccf-135">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="95ccf-136">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="95ccf-136">**Database name**</span></span>  
 <span data-ttu-id="95ccf-137">从数据库列表中选择数据库。</span><span class="sxs-lookup"><span data-stu-id="95ccf-137">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="95ccf-138">**高级**</span><span class="sxs-lookup"><span data-stu-id="95ccf-138">**Advanced**</span></span>  
 <span data-ttu-id="95ccf-139">使用 "**设置高级属性**" 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="95ccf-139">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="95ccf-140">有关详细信息，请参阅[设置高级属性 (SSAS)](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="95ccf-140">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="95ccf-141">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="95ccf-141">**Test Connection**</span></span>  
 <span data-ttu-id="95ccf-142">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="95ccf-142">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="95ccf-143">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="95ccf-143">A message is displayed indicating whether the connection was successful.</span></span>  
  
  
