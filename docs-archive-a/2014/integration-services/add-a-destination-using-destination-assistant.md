---
title: 使用目标助手添加目标 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 747a0de0-3c2f-4d31-a692-7111fc0911d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd36828a7bab7fb33b86765f9f064b6406a17a9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579013"
---
# <a name="add-a-destination-using-destination-assistant"></a><span data-ttu-id="58870-102">使用目标助手添加目标</span><span class="sxs-lookup"><span data-stu-id="58870-102">Add a Destination using Destination Assistant</span></span>
  <span data-ttu-id="58870-103">本主题介绍了使用目标助手添加新目标的步骤，并列出了在  “添加新目标”对话框中提供的选项，将目标助手下拉到 SSIS 设计器时可看到此对话框。</span><span class="sxs-lookup"><span data-stu-id="58870-103">This topic provides steps to add a new destination using the Destination Assistant and also lists the options that are available on the **Add New Destination** dialog, which you will see when you drag-drop the Destination Assistant to the SSIS Designer.</span></span>  
  
### <a name="to-use-destination-assistant-to-add-a-destination"></a><span data-ttu-id="58870-104">使用目标助手添加目标</span><span class="sxs-lookup"><span data-stu-id="58870-104">To use Destination Assistant to add a destination</span></span>  
  
1.  <span data-ttu-id="58870-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要将目标组件添加到的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="58870-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you want to add a destination component to.</span></span>  
  
2.  <span data-ttu-id="58870-106">将 **“目标助手”** 组件从 SSIS 工具箱拖到 **“数据流”** 选项卡。您应该会看到 **“添加新目标”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="58870-106">Drag the **Destination Assistant** component from the SSIS Toolbox to the **Data Flow** tab. You should see the **Add New Destination** dialog box.</span></span> <span data-ttu-id="58870-107">下一节提供了有关该对话框中的可用选项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="58870-107">The next section provides you details about the options available in the dialog box.</span></span>  
  
3.  <span data-ttu-id="58870-108">在 **“类型”** 列表中，选择目标的类型。</span><span class="sxs-lookup"><span data-stu-id="58870-108">Select the type of the destination in the **Types** list.</span></span>  
  
4.  <span data-ttu-id="58870-109">在“连接管理器”列表中选择现有连接管理器，或选择“\<New>”以创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="58870-109">Select an existing connection manager in the **Connection Managers** list or select **\<New>** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="58870-110">如果您选择现有连接管理器，则单击 **“确定”** 以便关闭 **“添加新目标”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="58870-110">If you select an existing connection manager, click **OK** to close the **Add New Destination** dialog box.</span></span> <span data-ttu-id="58870-111">您应该会看到添加到数据流的目标管理器和连接管理器。</span><span class="sxs-lookup"><span data-stu-id="58870-111">You should see the destination and connection managers added to the data flow.</span></span>  
  
6.  <span data-ttu-id="58870-112">如果单击“\<New>”创建新的连接管理器，则应该会看到“连接管理器”对话框，你看从中指定连接的参数 。</span><span class="sxs-lookup"><span data-stu-id="58870-112">If you click **\<New>** to create a new connection manager, you should see a **Connection Manager** dialog box, which lets you specify parameters for the connection.</span></span> <span data-ttu-id="58870-113">在您创建完新的连接管理器后，将在 SSIS 设计器中看到目标和连接管理器。</span><span class="sxs-lookup"><span data-stu-id="58870-113">After you are done with creating the new connection manager, you will see the destination and the connection manager in SSIS Designer.</span></span>  
  
  
