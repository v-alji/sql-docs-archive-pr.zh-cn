---
title: 使用向导创建模型部署包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], creating
- models [Master Data Services], creating a deployment package
- creating packages [Master Data Services]
ms.assetid: b24ec4c2-1378-4c72-ac69-4ec2647030f0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: abb30f9d8e08d8eec8e04960b61575da3a1dbcc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590888"
---
# <a name="create-a-model-deployment-package-by-using-the-wizard"></a><span data-ttu-id="411de-102">使用向导创建模型部署包</span><span class="sxs-lookup"><span data-stu-id="411de-102">Create a Model Deployment Package by Using the Wizard</span></span>
  <span data-ttu-id="411de-103">使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 模型部署向导可创建只包含模型对象的包。</span><span class="sxs-lookup"><span data-stu-id="411de-103">Use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] model deployment wizard to create a package of the model objects only.</span></span> <span data-ttu-id="411de-104">如果需要在包中包含数据，请参阅 [使用 MDSModelDeploy 创建模型部署包](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)。</span><span class="sxs-lookup"><span data-stu-id="411de-104">If you need to include data in the package, see [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="411de-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="411de-105">Prerequisites</span></span>  
 <span data-ttu-id="411de-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="411de-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="411de-107">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中，您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="411de-107">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="411de-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="411de-108">You must be a model administrator.</span></span> <span data-ttu-id="411de-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="411de-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="411de-110">模型对于您要创建的包必须存在。</span><span class="sxs-lookup"><span data-stu-id="411de-110">A model must exist for you to create a package of.</span></span> <span data-ttu-id="411de-111">有关详细信息，请参阅[创建模型 (Master Data Services)](../../2014/master-data-services/create-a-model-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="411de-111">For more information, see [Create a Model &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-deployment-package"></a><span data-ttu-id="411de-112">创建模型部署包</span><span class="sxs-lookup"><span data-stu-id="411de-112">To create a model deployment package</span></span>  
  
1.  <span data-ttu-id="411de-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="411de-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="411de-114">在 **“模型视图”** 页上，从菜单栏中，指向 **“系统”** ，然后单击 **“部署”**。</span><span class="sxs-lookup"><span data-stu-id="411de-114">On the **Model View** page, from the menu bar, point to **System** and click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="411de-115">在 **“模型部署向导”** 上，单击 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="411de-115">On the **Model Deployment Wizard**, click **Create**.</span></span>  
  
4.  <span data-ttu-id="411de-116">在 **“创建包”** 页上，从 **“模型”** 列表中选择一个模型。</span><span class="sxs-lookup"><span data-stu-id="411de-116">On the **Create Package** page, select a model from the **Model** list.</span></span>  
  
5.  <span data-ttu-id="411de-117">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="411de-117">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="411de-118">单击“下载”。</span><span class="sxs-lookup"><span data-stu-id="411de-118">Click **Download**.</span></span>  
  
7.  <span data-ttu-id="411de-119">保存文件。</span><span class="sxs-lookup"><span data-stu-id="411de-119">Save the file.</span></span>  
  
8.  <span data-ttu-id="411de-120">单击“**关闭**”以关闭向导。</span><span class="sxs-lookup"><span data-stu-id="411de-120">Click **Close** to close the wizard.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="411de-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="411de-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="411de-122">使用向导部署模型部署包</span><span class="sxs-lookup"><span data-stu-id="411de-122">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="411de-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="411de-123">See Also</span></span>  
 [<span data-ttu-id="411de-124">部署模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="411de-124">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
