---
title: 修复 Distributed Replay 安装 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 57f5b2bde308e48dbf14b52a8b159b30f6a98bc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588842"
---
# <a name="repair-a-distributed-replay-installation"></a>修复 Distributed Replay 安装
  修复 Distributed Replay 组件（控制器或客户端）时将执行以下操作：  
  
1.  在磁盘上再次安装所有关联的文件，并替换所有现有文件。  
  
2.  重新创建 Windows 服务帐户（如果相应的服务帐户已删除）。  
  
 您无法使用修复操作添加或删除组件。 若要添加或删除组件，请在安装程序的 "**功能选择**" 页上的功能树中选中或取消选中相应的组件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a>修复失败的 Distributed Replay 安装  
  
1.  从 "**开始**" 菜单中，单击 "**控制面板**"，然后双击 "**添加或删除程序**"。  
  
2.  在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] "**卸载或更改程序**" 窗口中选择，然后在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 对话框中单击 "**修复**"。  
  
3.  按照向导中的步骤操作 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，然后在 "**选择功能**" 页上，选择要修复的 Distributed Replay 组件，然后单击 "**下一步"。**  
  
4.  完成 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导以修复选定的 Distributed Replay 功能。  
  
  
