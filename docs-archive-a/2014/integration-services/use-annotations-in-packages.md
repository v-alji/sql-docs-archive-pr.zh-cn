---
title: 在包中使用批注 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 27c7df6afd894ea9730027da1d54786ed8397fad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591945"
---
# <a name="use-annotations-in-packages"></a><span data-ttu-id="e053d-102">在包中使用批注</span><span class="sxs-lookup"><span data-stu-id="e053d-102">Use Annotations in Packages</span></span>
  <span data-ttu-id="e053d-103">[!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器提供批注，利用它们可使包自文档化，且更易理解和维护。</span><span class="sxs-lookup"><span data-stu-id="e053d-103">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides annotations, which you can use to make packages self-documenting and easier to understand and maintain.</span></span> <span data-ttu-id="e053d-104">可以将批注添加到 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器的控制流、数据流和事件处理程序设计图面。</span><span class="sxs-lookup"><span data-stu-id="e053d-104">You can add annotations to the control flow, data flow, and event handler design surfaces of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="e053d-105">批注可以包含任何类型的文本，对将标签、注释和其他说明性信息添加到包十分有用。</span><span class="sxs-lookup"><span data-stu-id="e053d-105">The annotations can contain any type of text, and they are useful for adding labels, comments, and other descriptive information to a package.</span></span> <span data-ttu-id="e053d-106">批注仅为设计时功能。</span><span class="sxs-lookup"><span data-stu-id="e053d-106">Annotations are a design-time feature only.</span></span> <span data-ttu-id="e053d-107">例如，批注不会写入日志。</span><span class="sxs-lookup"><span data-stu-id="e053d-107">For example, they are not written to logs.</span></span>  
  
 <span data-ttu-id="e053d-108">按 Enter 时，文本会换行到下一行。</span><span class="sxs-lookup"><span data-stu-id="e053d-108">When you press ENTER, the text wraps to the next line.</span></span> <span data-ttu-id="e053d-109">在添加其他文本行时，批注框的大小会自动增加。</span><span class="sxs-lookup"><span data-stu-id="e053d-109">The annotation box automatically increases in size as you add additional lines of text.</span></span> <span data-ttu-id="e053d-110">包批注会以明文形式持久保持在包文件的 CDATA 部分。</span><span class="sxs-lookup"><span data-stu-id="e053d-110">Package annotations are persisted as clear text in the CDATA section of the package file.</span></span>  
  
 <span data-ttu-id="e053d-111">有关更改包文件格式的详细信息，请参阅 [SSIS 包格式](../../2014/integration-services/ssis-package-format.md)。</span><span class="sxs-lookup"><span data-stu-id="e053d-111">For more information about changes to the format of the package file, see [SSIS Package Format](../../2014/integration-services/ssis-package-format.md).</span></span>  
  
 <span data-ttu-id="e053d-112">保存包时， [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器将批注保存在包中。</span><span class="sxs-lookup"><span data-stu-id="e053d-112">When you save the package, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer saves the annotations in the package.</span></span>  
  
### <a name="to-add-an-annotation-to-a-package"></a><span data-ttu-id="e053d-113">将批注添加到包</span><span class="sxs-lookup"><span data-stu-id="e053d-113">To add an annotation to a package</span></span>  
  
-   [<span data-ttu-id="e053d-114">将批注添加到包</span><span class="sxs-lookup"><span data-stu-id="e053d-114">Add an Annotation to a Package</span></span>](../../2014/integration-services/add-an-annotation-to-a-package.md)  
  
  
