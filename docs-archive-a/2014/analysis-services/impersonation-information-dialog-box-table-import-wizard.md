---
title: "\"模拟信息\" 对话框 (表导入向导) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5300f8b6106a7f29f51018b4e039c2a8c28aa729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687328"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>“模拟信息”对话框（表导入向导）
  使用 **“模拟信息”** 页可以指定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将用于连接到数据源的凭据。 有关凭据模拟的详细信息，请参阅[模拟 &#40;SSAS 表格&#41;](tabular-models/impersonation-ssas-tabular.md)。  
  
## <a name="options"></a>选项  
 **特定的 Windows 用户名和密码**  
 选择此选项将使表格模型使用指定的 Windows 用户帐户的安全凭据。  
  
 **用户名**  
 键入要使用的用户帐户的域和名称。 使用以下格式：  
  
 *\<Domain name>* **\\** *\<User account name>*  
  
 只有选定了 **“使用特定名称和密码”** ，才启用此选项。  
  
 **密码**  
 键入表格模型将使用的用户帐户的密码。  
  
 只有选定了 **“使用特定名称和密码”** ，才启用此选项。  
  
 **服务帐户**  
 选择此选项将使用与管理该模型的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务相关联的安全凭据。  
  
## <a name="see-also"></a>另请参阅  
 [模拟（SSAS 表格）](tabular-models/impersonation-ssas-tabular.md)  
  
  
