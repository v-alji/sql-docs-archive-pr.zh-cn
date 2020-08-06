---
title: “验证”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackagevalidate.f1
- sql12.ssis.ssms.isprojectvalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69e29d106dc9f4f100bf191911c5c34e0250be8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578367"
---
# <a name="validate-dialog-box"></a>“验证”对话框
  使用 **“验证”** 对话框检查 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目或包中的常见问题。  
  
 如果有问题，将在该对话框的顶部显示一条消息。 否则，在顶部显示“就绪”一词。  
  
 **您希望做什么？**  
  
-   [打开“验证”对话框](#open_dialog)  
  
-   [设置“常规”页上的选项](#general)  
  
##  <a name="open-the-validate-dialog-box"></a><a name="open_dialog"></a> 打开“验证”对话框  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。  
  
     正在连接到承载 SSISDB 数据库的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例。  
  
2.  在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。  
  
3.  展开 **“SSISDB”** 节点。  
  
4.  展开包含您要验证的项目或包的文件夹。  
  
5.  右键单击该包，然后单击“验证”  。  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> 设置“常规”页上的选项  
 **环境**  
 选择要用于验证项目或包的环境。  
  
 **32 位运行时**  
 选择使用 32 位运行时来执行包。  
  
 **“参数”** 选项卡列出了用于验证项目或包的参数值。 以下是“参数”选项卡上的选项。  
  
 **容器**  
 列出包含参数的对象。  
  
 **Parameter**  
 列出参数的名称  
  
 **值**  
 列出参数值。  
  
 **“连接管理器”** 选项卡列出了用于验证项目或包的连接管理器属性值。  
  
 以下是 **“连接管理器”** 选项卡中的选项。  
  
 **容器**  
 列出包含连接管理器的对象。  
  
 **名称**  
 列出连接管理器名称。  
  
 **属性名称**  
 列出连接管理器属性的名称。  
  
 **值**  
 列出分配给连接管理器属性的值。  
  
  
