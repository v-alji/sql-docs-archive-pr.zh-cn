---
title: 编辑模型部署包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b8bfd7083e2ba763d15a405266260b5a096c8378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591913"
---
# <a name="edit-a-model-deployment-package"></a><span data-ttu-id="6491c-102">编辑模型部署包</span><span class="sxs-lookup"><span data-stu-id="6491c-102">Edit a Model Deployment Package</span></span>
  <span data-ttu-id="6491c-103">本主题介绍如何在 MDS 中部署模型的所选部分，而不是部署整个模型。</span><span class="sxs-lookup"><span data-stu-id="6491c-103">This topic describes how to deploy selected parts of a model in MDS, rather than an entire model.</span></span> <span data-ttu-id="6491c-104">为此，您需使用模型包编辑器来编辑 MDS 模型包。</span><span class="sxs-lookup"><span data-stu-id="6491c-104">To do so, you edit an MDS model package using the Model Package Editor.</span></span>  
  
 <span data-ttu-id="6491c-105">利用模型包编辑器向导，您可以在要包含在 MDS 包中的模型中选择特定实体、派生层次结构、订阅视图和业务规则，并在稍后进行部署。</span><span class="sxs-lookup"><span data-stu-id="6491c-105">The Model Package Editor wizard enables you to select the specific entities, derived hierarchies, subscription views, and business rules in a model that you want to include in an MDS package, and then later deploy.</span></span> <span data-ttu-id="6491c-106">您可以忽略不想部署的那部分模型。</span><span class="sxs-lookup"><span data-stu-id="6491c-106">You can leave out those parts of the model that you do not want to deploy.</span></span> <span data-ttu-id="6491c-107">当您选择一个实体时，还会自动选择该实体中的所有依赖对象。</span><span class="sxs-lookup"><span data-stu-id="6491c-107">When you select an entity, all of the dependent objects in that entity are also automatically selected.</span></span>  
  
 <span data-ttu-id="6491c-108">可使用模型包编辑器选择通过 MDSModelDeploy 工具（用于创建包含对象和数据的包文件）或模型部署向导（用于创建仅包含模型结构的文件）创建的包文件中的模型的一部分。</span><span class="sxs-lookup"><span data-stu-id="6491c-108">You use the Model Package Editor to select parts of a model in a package file that was created by either the MDSModelDeploy tool (which creates a package file that includes objects and data) or the Model Deployment wizard (which creates a file that includes only the model structure).</span></span> <span data-ttu-id="6491c-109">在编辑包中的模型之后，可使用 MDSModelDeploy 工具部署对象和数据，或使用模型部署向导仅部署模型结构。</span><span class="sxs-lookup"><span data-stu-id="6491c-109">After editing the model in the package, you use the MDSModelDeploy tool to deploy objects and data, or the Model Deployment wizard to deploy just the model structure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6491c-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="6491c-110">Prerequisites</span></span>  
 <span data-ttu-id="6491c-111">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="6491c-111">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="6491c-112">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="6491c-112">You must be a model administrator.</span></span> <span data-ttu-id="6491c-113">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6491c-113">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="6491c-114">您要编辑的模型包必须存在。</span><span class="sxs-lookup"><span data-stu-id="6491c-114">A model package must exist for you to edit.</span></span> <span data-ttu-id="6491c-115">有关详细信息，请参阅[部署模型 (Master Data Services)](../../2014/master-data-services/deploying-models-master-data-services.md)和[使用向导创建模型部署包](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)或[使用 MDSModelDeploy 创建模型部署包](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)。</span><span class="sxs-lookup"><span data-stu-id="6491c-115">For more information, see [Deploying Models &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md) and [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md) or [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
### <a name="to-edit-a-model-deployment-package"></a><span data-ttu-id="6491c-116">编辑模型部署包</span><span class="sxs-lookup"><span data-stu-id="6491c-116">To edit a model deployment package</span></span>  
  
1.  <span data-ttu-id="6491c-117">在 MDS 服务器上的 Windows 资源管理器中，转到*drive*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\configuration。</span><span class="sxs-lookup"><span data-stu-id="6491c-117">In Windows Explorer on the MDS server, move to *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
2.  <span data-ttu-id="6491c-118">执行 ModelPackageEditor.exe。</span><span class="sxs-lookup"><span data-stu-id="6491c-118">Execute ModelPackageEditor.exe.</span></span>  
  
3.  <span data-ttu-id="6491c-119">在模型编辑器向导中，单击 **“浏览”**，移至包含您的包的文件夹，选择一个包，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="6491c-119">In the Model Package Editor wizard, click **Browse**, move to the folder containing your packages, select a package, and then click **Open**.</span></span> <span data-ttu-id="6491c-120">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6491c-120">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="6491c-121">选择要部署的实体、派生层次结构、订阅视图或业务规则。</span><span class="sxs-lookup"><span data-stu-id="6491c-121">Select those entities, derived hierarchies, subscriptions views, or business rules that you want to deploy.</span></span> <span data-ttu-id="6491c-122">取消选择不想部署的这类项。</span><span class="sxs-lookup"><span data-stu-id="6491c-122">Deselect those that you do not want to deploy.</span></span> <span data-ttu-id="6491c-123">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6491c-123">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="6491c-124">验证要部署的所选内容的列表。</span><span class="sxs-lookup"><span data-stu-id="6491c-124">Verify the list of selections to deploy.</span></span> <span data-ttu-id="6491c-125">若要更改，请单击 **“返回”** 并重复步骤 4。</span><span class="sxs-lookup"><span data-stu-id="6491c-125">To change, click **Back** and repeat step 4.</span></span>  
  
6.  <span data-ttu-id="6491c-126">单击“浏览”\*\*\*\*，移至要保存部分包的文件夹，然后输入部分包的文件名（使用 .pkg 扩展名）。</span><span class="sxs-lookup"><span data-stu-id="6491c-126">Click **Browse**, move to the folder that you want to save the partial package in, and then enter the file name of the partial package (with a .pkg extension).</span></span> <span data-ttu-id="6491c-127">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="6491c-127">Click **Save**.</span></span>  
  
7.  <span data-ttu-id="6491c-128">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="6491c-128">Click **Finish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6491c-129">后续步骤</span><span class="sxs-lookup"><span data-stu-id="6491c-129">Next Steps</span></span>  
  
-   [<span data-ttu-id="6491c-130">使用向导部署模型部署包</span><span class="sxs-lookup"><span data-stu-id="6491c-130">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [<span data-ttu-id="6491c-131">使用 MDSModelDeploy 部署模型部署包</span><span class="sxs-lookup"><span data-stu-id="6491c-131">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
