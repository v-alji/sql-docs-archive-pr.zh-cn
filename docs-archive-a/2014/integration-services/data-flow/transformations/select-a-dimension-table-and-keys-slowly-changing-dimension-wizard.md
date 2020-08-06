---
title: 选择维度表和键（渐变维度向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 671c66a8a5d5f1f4f5201fd8c9ecc144540d8b68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694538"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a><span data-ttu-id="46b22-102">选择维度表和键（渐变维度向导）</span><span class="sxs-lookup"><span data-stu-id="46b22-102">Select a Dimension Table and Keys (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="46b22-103">使用 **“选择维度表和键”** 页可以选择要加载的维度表。</span><span class="sxs-lookup"><span data-stu-id="46b22-103">Use the **Select a Dimension Table and Keys** page to select a dimension table to load.</span></span> <span data-ttu-id="46b22-104">将数据流中的列映射到要加载的列。</span><span class="sxs-lookup"><span data-stu-id="46b22-104">Map columns from the data flow to the columns that will be loaded.</span></span>  
  
 <span data-ttu-id="46b22-105">若要了解有关此向导的详细信息，请参阅 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="46b22-105">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="46b22-106">选项</span><span class="sxs-lookup"><span data-stu-id="46b22-106">Options</span></span>  
 <span data-ttu-id="46b22-107">**“ODBC 目标编辑器”**</span><span class="sxs-lookup"><span data-stu-id="46b22-107">**Connection manager**</span></span>  
 <span data-ttu-id="46b22-108">从列表中选择现有 OLE DB 连接管理器，或者单击“新建”  创建 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="46b22-108">Select an existing OLE DB connection manager from the list, or click **New** to create an OLE DB connection manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46b22-109">渐变维度向导仅支持 OLE DB 连接管理器，并且仅支持与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的连接。</span><span class="sxs-lookup"><span data-stu-id="46b22-109">The Slowly Changing Dimension Wizard only supports OLE DB connection managers, and only supports connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="46b22-110">**新建**</span><span class="sxs-lookup"><span data-stu-id="46b22-110">**New**</span></span>  
 <span data-ttu-id="46b22-111">使用“配置 OLE DB 连接管理器”  对话框可以选择现有的连接管理器，或者单击“新建”  创建新的 OLE DB 连接。</span><span class="sxs-lookup"><span data-stu-id="46b22-111">Use the **Configure OLE DB Connection Manager** dialog box to select an existing connection manager, or click **New** to create a new OLE DB connection.</span></span>  
  
 <span data-ttu-id="46b22-112">**“表或视图”**</span><span class="sxs-lookup"><span data-stu-id="46b22-112">**Table or View**</span></span>  
 <span data-ttu-id="46b22-113">从该列表中选择表或视图。</span><span class="sxs-lookup"><span data-stu-id="46b22-113">Select a table or view from the list.</span></span>  
  
 <span data-ttu-id="46b22-114">**输入列**</span><span class="sxs-lookup"><span data-stu-id="46b22-114">**Input Columns**</span></span>  
 <span data-ttu-id="46b22-115">可以从输入列列表中选择要为其指定映射的输入列。</span><span class="sxs-lookup"><span data-stu-id="46b22-115">Select from the list of input columns for which you may specify mapping.</span></span>  
  
 <span data-ttu-id="46b22-116">**维度列**</span><span class="sxs-lookup"><span data-stu-id="46b22-116">**Dimension Columns**</span></span>  
 <span data-ttu-id="46b22-117">查看所有可用的维度列。</span><span class="sxs-lookup"><span data-stu-id="46b22-117">View all available dimension columns.</span></span>  
  
 <span data-ttu-id="46b22-118">**键类型**</span><span class="sxs-lookup"><span data-stu-id="46b22-118">**Key Type**</span></span>  
 <span data-ttu-id="46b22-119">选择一个维度列作为业务键。</span><span class="sxs-lookup"><span data-stu-id="46b22-119">Select one of the dimension columns to be the business key.</span></span> <span data-ttu-id="46b22-120">您必须具有一个业务键。</span><span class="sxs-lookup"><span data-stu-id="46b22-120">You must have one business key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b22-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46b22-121">See Also</span></span>  
 [<span data-ttu-id="46b22-122">使用渐变维度向导配置输出</span><span class="sxs-lookup"><span data-stu-id="46b22-122">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
