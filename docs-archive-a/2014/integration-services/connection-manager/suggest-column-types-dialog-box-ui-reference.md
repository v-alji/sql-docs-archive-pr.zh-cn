---
title: “提供列类型建议”对话框 UI 参考 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.suggestdatatypes.f1
ms.assetid: 8d5652e0-cf57-483f-828b-10f00c08418b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cbca2a3186a58b1148eb9627825fdfddf334339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693428"
---
# <a name="suggest-column-types-dialog-box-ui-reference"></a><span data-ttu-id="d562f-102">“提供列类型建议”对话框 UI 参考</span><span class="sxs-lookup"><span data-stu-id="d562f-102">Suggest Column Types Dialog Box UI Reference</span></span>
  <span data-ttu-id="d562f-103">可以使用 **“提供列类型建议”** 对话框，根据文件内容抽样指定平面文件连接管理器中的列的数据类型和长度。</span><span class="sxs-lookup"><span data-stu-id="d562f-103">Use the **Suggest Column Types** dialog box to identify the data type and length of columns in a Flat File Connection Manager based on a sampling of the file content.</span></span>  
  
 <span data-ttu-id="d562f-104">若要了解有关 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]使用的数据类型的详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d562f-104">To learn more about the data types used by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d562f-105">选项</span><span class="sxs-lookup"><span data-stu-id="d562f-105">Options</span></span>  
 <span data-ttu-id="d562f-106">**行数**</span><span class="sxs-lookup"><span data-stu-id="d562f-106">**Number of rows**</span></span>  
 <span data-ttu-id="d562f-107">键入或选择算法使用的示例中的行数。</span><span class="sxs-lookup"><span data-stu-id="d562f-107">Type or select the number of rows in the sample that the algorithm uses.</span></span>  
  
 <span data-ttu-id="d562f-108">**建议使用最小整数数据类型**</span><span class="sxs-lookup"><span data-stu-id="d562f-108">**Suggest the smallest integer data type**</span></span>  
 <span data-ttu-id="d562f-109">清除此复选框可以略过评估。</span><span class="sxs-lookup"><span data-stu-id="d562f-109">Clear this check box to skip the assessment.</span></span> <span data-ttu-id="d562f-110">选中此复选框之后，将为包含整型数字数据的列确定可能的最小整型数据类型。</span><span class="sxs-lookup"><span data-stu-id="d562f-110">If selected, determines the smallest possible integer data type for columns that contain integral numeric data.</span></span>  
  
 <span data-ttu-id="d562f-111">**建议使用最小的实型数据类型**</span><span class="sxs-lookup"><span data-stu-id="d562f-111">**Suggest the smallest real data type**</span></span>  
 <span data-ttu-id="d562f-112">清除此复选框可以略过评估。</span><span class="sxs-lookup"><span data-stu-id="d562f-112">Clear this check box to skip the assessment.</span></span> <span data-ttu-id="d562f-113">选中此复选框之后，将确定包含实型数字数据的列是否可以使用较小的实型数据类型 DT_R4。</span><span class="sxs-lookup"><span data-stu-id="d562f-113">If selected, determines whether columns that contain real numeric data can use the smaller real data type, DT_R4.</span></span>  
  
 <span data-ttu-id="d562f-114">**使用下列值标识布尔值列**</span><span class="sxs-lookup"><span data-stu-id="d562f-114">**Identify Boolean columns using the following values**</span></span>  
 <span data-ttu-id="d562f-115">键入要用作布尔值 True 和 False 的两个值。</span><span class="sxs-lookup"><span data-stu-id="d562f-115">Type the two values that you want to use as the Boolean values true and false.</span></span> <span data-ttu-id="d562f-116">两个值必须用逗号分隔，并且第一个值代表 True。</span><span class="sxs-lookup"><span data-stu-id="d562f-116">The values must be separated by a comma, and the first value represents True.</span></span>  
  
 <span data-ttu-id="d562f-117">**填充字符串列**</span><span class="sxs-lookup"><span data-stu-id="d562f-117">**Pad string columns**</span></span>  
 <span data-ttu-id="d562f-118">选中此复选框，可以启用字符串填充。</span><span class="sxs-lookup"><span data-stu-id="d562f-118">Select this check box to enable string padding.</span></span>  
  
 <span data-ttu-id="d562f-119">**填充百分比**</span><span class="sxs-lookup"><span data-stu-id="d562f-119">**Percent padding**</span></span>  
 <span data-ttu-id="d562f-120">对于字符数据类型的列，键入或选择列长度增加的百分比。</span><span class="sxs-lookup"><span data-stu-id="d562f-120">Type or select the percentage of the column lengths by which to increase the length of columns for character data types.</span></span> <span data-ttu-id="d562f-121">百分比必须为整数。</span><span class="sxs-lookup"><span data-stu-id="d562f-121">The percentage must be an integer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d562f-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d562f-122">See Also</span></span>  
 <span data-ttu-id="d562f-123">[Integration Services 错误和消息引用](../integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d562f-123">[Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="d562f-124">平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="d562f-124">Flat File Connection Manager</span></span>](file-connection-manager.md)  
  
  
