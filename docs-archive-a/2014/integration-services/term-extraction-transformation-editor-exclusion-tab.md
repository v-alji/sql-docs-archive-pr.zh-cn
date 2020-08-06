---
title: 字词提取转换编辑器 (排除选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.inclusionexclusion.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 90110d95-fd97-4542-9cda-832c86606130
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bc4b0401a1dd27111d0498e9e0d848c80da1742
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590912"
---
# <a name="term-extraction-transformation-editor-exclusion-tab"></a><span data-ttu-id="60433-102">字词提取转换编辑器（“排除”选项卡）</span><span class="sxs-lookup"><span data-stu-id="60433-102">Term Extraction Transformation Editor (Exclusion Tab)</span></span>
  <span data-ttu-id="60433-103">可以使用 **“字词提取转换编辑器”** 对话框的 **“排除”** 选项卡，建立与排除表的连接并指定包含排除字词的列。</span><span class="sxs-lookup"><span data-stu-id="60433-103">Use the **Exclusion** tab of the **Term Extraction Transformation Editor** dialog box to set up a connection to an exclusion table and specify the columns that contain exclusion terms.</span></span>  
  
 <span data-ttu-id="60433-104">若要了解有关字词提取转换的详细信息，请参阅 [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="60433-104">To learn more about the Term Extraction transformation, see [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="60433-105">选项</span><span class="sxs-lookup"><span data-stu-id="60433-105">Options</span></span>  
 <span data-ttu-id="60433-106">**使用排除字词**</span><span class="sxs-lookup"><span data-stu-id="60433-106">**Use exclusion terms**</span></span>  
 <span data-ttu-id="60433-107">指示在字词提取过程中是否通过指定包含排除字词的列来排除特定的字词。</span><span class="sxs-lookup"><span data-stu-id="60433-107">Indicate whether to exclude specific terms during term extraction by specifying a column that contains exclusion terms.</span></span> <span data-ttu-id="60433-108">如果选择要排除字词，则必须指定以下源属性：</span><span class="sxs-lookup"><span data-stu-id="60433-108">You must specify the following source properties if you choose to exclude terms.</span></span>  
  
 <span data-ttu-id="60433-109">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="60433-109">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="60433-110">选择现有的 OLE DB 连接管理器，或通过单击“新建”创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="60433-110">Select an existing OLE DB connection manager, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="60433-111">**新建**</span><span class="sxs-lookup"><span data-stu-id="60433-111">**New**</span></span>  
 <span data-ttu-id="60433-112">通过使用“配置 OLE DB 连接管理器”  对话框创建与数据库的新连接。</span><span class="sxs-lookup"><span data-stu-id="60433-112">Create a new connection to a database by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="60433-113">**表或视图**</span><span class="sxs-lookup"><span data-stu-id="60433-113">**Table or view**</span></span>  
 <span data-ttu-id="60433-114">选择包含排除字词的表或视图。</span><span class="sxs-lookup"><span data-stu-id="60433-114">Select the table or view that contains the exclusion terms.</span></span>  
  
 <span data-ttu-id="60433-115">**列**</span><span class="sxs-lookup"><span data-stu-id="60433-115">**Column**</span></span>  
 <span data-ttu-id="60433-116">在表或视图中选择包含排除字词的列。</span><span class="sxs-lookup"><span data-stu-id="60433-116">Select the column in the table or view that contains the exclusion terms.</span></span>  
  
 <span data-ttu-id="60433-117">**配置错误输出**</span><span class="sxs-lookup"><span data-stu-id="60433-117">**Configure Error Output**</span></span>  
 <span data-ttu-id="60433-118">使用[“配置错误输出” ](../../2014/integration-services/configure-error-output.md) 对话框可以为导致错误的行指定错误处理方式。</span><span class="sxs-lookup"><span data-stu-id="60433-118">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60433-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60433-119">See Also</span></span>  
 <span data-ttu-id="60433-120">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="60433-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="60433-121">[字词提取转换编辑器 &#40;字词提取选项卡&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span><span class="sxs-lookup"><span data-stu-id="60433-121">[Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span></span>  
 <span data-ttu-id="60433-122">[字词提取转换编辑器 &#40;高级 "选项卡&#41;](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="60433-122">[Term Extraction Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="60433-123">字词查找转换</span><span class="sxs-lookup"><span data-stu-id="60433-123">Term Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
