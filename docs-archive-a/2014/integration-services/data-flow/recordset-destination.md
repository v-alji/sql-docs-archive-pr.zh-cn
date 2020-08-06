---
title: 记录集目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1acc29c904e9020721e8ac62dff09a8ec29a392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579650"
---
# <a name="recordset-destination"></a><span data-ttu-id="7e0a3-102">记录集目标</span><span class="sxs-lookup"><span data-stu-id="7e0a3-102">Recordset Destination</span></span>
  <span data-ttu-id="7e0a3-103">记录集目标创建和填充内存中的 ADO 记录集。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-103">The Recordset destination creates and populates an in-memory ADO recordset.</span></span> <span data-ttu-id="7e0a3-104">记录集的形式是在设计时由记录集目标的输入定义的。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-104">The shape of the recordset is defined by the input to the Recordset destination at design time.</span></span>  
  
## <a name="configuration-of-the-recordset-destination"></a><span data-ttu-id="7e0a3-105">记录集目标的配置</span><span class="sxs-lookup"><span data-stu-id="7e0a3-105">Configuration of the Recordset Destination</span></span>  
 <span data-ttu-id="7e0a3-106">您可以通过指定用于存储 ADO 记录集的变量，来配置记录集目标。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-106">You configure the Recordset destination by specifying the variable that stores the ADO recordset.</span></span>  
  
 <span data-ttu-id="7e0a3-107">运行时，ADO 记录集写入由记录集目标的 VariableName 属性所指定的类型变量 Object。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-107">At run time, an ADO recordset is written to the variable of type, Object, that is specified in the VariableName property of the Recordset destination.</span></span> <span data-ttu-id="7e0a3-108">然后，该变量使该记录集在数据流外部可用，这样脚本和其他包元素便可使用它。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-108">The variable then makes the Recordset available outside the data flow, where it can be used by scripts and other package elements.</span></span>  
  
 <span data-ttu-id="7e0a3-109">此源具有一个输入。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-109">This source has one input.</span></span> <span data-ttu-id="7e0a3-110">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-110">It does not support an error output.</span></span>  
  
 <span data-ttu-id="7e0a3-111">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-111">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="7e0a3-112">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-112">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="7e0a3-113">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="7e0a3-113">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="7e0a3-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="7e0a3-114">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="7e0a3-115">记录集目标自定义属性</span><span class="sxs-lookup"><span data-stu-id="7e0a3-115">Recordset Destination Custom Properties</span></span>](recordset-destination-custom-properties.md)  
  
 <span data-ttu-id="7e0a3-116">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="7e0a3-116">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="7e0a3-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="7e0a3-117">Related Tasks</span></span>  
 [<span data-ttu-id="7e0a3-118">使用记录集目标</span><span class="sxs-lookup"><span data-stu-id="7e0a3-118">Use a Recordset Destination</span></span>](recordset-destination.md)  
  
  
