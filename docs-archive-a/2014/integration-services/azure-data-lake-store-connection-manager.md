---
title: Azure Data Lake Store 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSCM.F1
- SQL11.DTS.DESIGNER.AFPADLSCM.F1
ms.assetid: 7f1323f9-9dc3-4378-9c70-bbc65bfeabfd
author: yualan
ms.author: chugu
ms.openlocfilehash: 1ab6e90aad6472cc10bbb12cf4ca17def501bf00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693025"
---
# <a name="azure-data-lake-store-connection-manager"></a><span data-ttu-id="18c3d-102">Azure Data Lake Store 连接管理器</span><span class="sxs-lookup"><span data-stu-id="18c3d-102">Azure Data Lake Store Connection Manager</span></span>
  <span data-ttu-id="18c3d-103">**Azure Data Lake Store 连接管理器** 启用了 SSIS 包，该包通过以下两种身份验证类型连接到 Azure Data Lake Store 服务：Azure AD 用户标识和 Azure AD 服务标识。</span><span class="sxs-lookup"><span data-stu-id="18c3d-103">The **Azure Data Lake Store connection manager** enables an SSIS package to connect to an Azure Data Lake Store service through two authentication types: Azure AD User Identity and Azure AD Service Identity.</span></span>  

## <a name="configure-the-azure-data-lake-store-connection-manager"></a><span data-ttu-id="18c3d-104">配置 Azure Data Lake Store 连接管理器</span><span class="sxs-lookup"><span data-stu-id="18c3d-104">Configure the Azure Data Lake Store Connection Manager</span></span> 
  
1.  <span data-ttu-id="18c3d-105">在“添加 SSIS 连接管理器” \*\*\*\* 对话框中，选择“AzureDataLake” \*\*\*\*，然后单击“添加” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="18c3d-105">In the **Add SSIS Connection Manager** dialog box, select **AzureDataLake**, and click **Add**.</span></span>   
  
2.  <span data-ttu-id="18c3d-106">在“Azure Data Lake Store 连接管理器编辑器”对话框的“ADLS 主机” \*\*\*\* 字段中，键入 Azure Data Lake Store 主机 URL。</span><span class="sxs-lookup"><span data-stu-id="18c3d-106">In the Azure Data Lake Store Connection Manager Editor dialog box, type in the Azure Data Lake Store host URL in **ADLS Host** field.</span></span> <span data-ttu-id="18c3d-107">例如： https： \/ /test.azuredatalakestore.net 或 test.azuredatalakestore.net。</span><span class="sxs-lookup"><span data-stu-id="18c3d-107">For example: https:\//test.azuredatalakestore.net or test.azuredatalakestore.net.</span></span>
  
3.  <span data-ttu-id="18c3d-108">选择相应的身份验证类型来访问 Azure Data Lake Store 数据。</span><span class="sxs-lookup"><span data-stu-id="18c3d-108">Choose corresponding authentication type to access Azure Data Lake Store data.</span></span>

    1.  <span data-ttu-id="18c3d-109">如果选择“Azure AD 用户标识” \*\*\*\* 身份验证选项，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="18c3d-109">If you selected **Azure AD User Identity** authentication option, do the following:</span></span>

        1. <span data-ttu-id="18c3d-110">为“用户名” \*\*\*\* 和“密码” \*\*\*\* 字段指定值。</span><span class="sxs-lookup"><span data-stu-id="18c3d-110">Specify values for the **User Name** and **Password** field.</span></span> 
    
        2. <span data-ttu-id="18c3d-111">单击“测试连接” \*\*\*\* 以测试连接。</span><span class="sxs-lookup"><span data-stu-id="18c3d-111">Click **Test Connection** button to test the connection.</span></span> <span data-ttu-id="18c3d-112">如果你和你的租户管理员先前不同意 SSIS 访问 Azure Data Lake Store 数据，则需在弹出对话框中单击“接受” \*\*\*\* 按钮，允许 SSIS 访问 Azure Data Lake Store 数据。</span><span class="sxs-lookup"><span data-stu-id="18c3d-112">If you and your tenant administrator didn't consent SSIS to access your Azure Data Lake Store data before, you need click **Accept** button to consent SSIS to access your Azure Data Lake Store data in the pop out dialog.</span></span> <span data-ttu-id="18c3d-113">若要深入了解此同意体验，请参阅 [Integrating applications with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-an-application-integration#integrating-applications-with-azure-ad)（将应用程序与 Azure Active Directory 集成）。</span><span class="sxs-lookup"><span data-stu-id="18c3d-113">For more information about this consent experience, see [Integrating applications with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-an-application-integration#integrating-applications-with-azure-ad).</span></span>
    
        > [!NOTE] 
        > <span data-ttu-id="18c3d-114">“Azure AD 用户标识”身份验证选项不支持多重身份验证和 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="18c3d-114">For Azure AD User Identity authentication option, multi-factor authentication and Microsoft account is NOT supported.</span></span>
    
    2.  <span data-ttu-id="18c3d-115">如果选择“Azure AD 服务标识” \*\*\*\* 身份验证选项，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="18c3d-115">If you selected **Azure AD Service Identity** authentication option, do the following:</span></span>
        1. <span data-ttu-id="18c3d-116">创建 AAD 应用程序和服务主体，使其可访问 Azure Data Lake 资源。</span><span class="sxs-lookup"><span data-stu-id="18c3d-116">Create an AAD application and service principal that can access Azure Data Lake resources.</span></span>
    
        2. <span data-ttu-id="18c3d-117">为此 AAD 应用程序分配相应权限，以便访问 Azure Data Lake 资源。</span><span class="sxs-lookup"><span data-stu-id="18c3d-117">Assign this AAD application corresponding permissions to access your Azure Data Lake resources.</span></span> <span data-ttu-id="18c3d-118">若要深入此身份验证选项，请参阅 [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)（使用门户创建可访问资源的 Active Directory 应用程序和服务主体）。</span><span class="sxs-lookup"><span data-stu-id="18c3d-118">For more information about this authentication option, see [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).</span></span>
    
        3. <span data-ttu-id="18c3d-119">为“客户端 ID” \*\*\*\*、“密钥” \*\*\*\* 和“租户名” \*\*\*\* 字段指定值。</span><span class="sxs-lookup"><span data-stu-id="18c3d-119">Specify values for **Client Id**, **Secret Key** and **Tenant Name** field.</span></span>
    
        4. <span data-ttu-id="18c3d-120">单击“测试连接” \*\*\*\* 以测试连接。</span><span class="sxs-lookup"><span data-stu-id="18c3d-120">Click **Test Connection** button to test the connection.</span></span>  
  
4.  <span data-ttu-id="18c3d-121">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="18c3d-121">Click **OK** to close the dialog box.</span></span>  
  
    <span data-ttu-id="18c3d-122">你可以看到你在“属性” \*\*\*\* 窗口中创建的连接管理器的属性。</span><span class="sxs-lookup"><span data-stu-id="18c3d-122">You can see the properties of the connection manager you created in the **Properties** window.</span></span>  
  
  
