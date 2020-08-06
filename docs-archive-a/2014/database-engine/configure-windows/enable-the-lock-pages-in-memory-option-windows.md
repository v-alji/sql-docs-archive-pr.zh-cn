---
title: 启用“锁定内存页”选项 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13290940c3a94a7ba79582d892a5e28670f24b29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586972"
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a><span data-ttu-id="1ed0c-102">启用“锁定内存页”选项 (Windows)</span><span class="sxs-lookup"><span data-stu-id="1ed0c-102">Enable the Lock Pages in Memory Option (Windows)</span></span>
  <span data-ttu-id="1ed0c-103">此 Windows 策略将确定哪些帐户可以使用进程将数据保留在物理内存中，从而阻止系统将数据分页到磁盘的虚拟内存中。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-103">This Windows policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ed0c-104">当预计会将内存分页到磁盘时，锁定内存中的页可以大大提高性能。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-104">Locking pages in memory may boost performance when paging memory to disk is expected.</span></span>  
  
 <span data-ttu-id="1ed0c-105">使用 Windows 组策略工具 (gpedit.msc)，可以为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用的帐户启用此策略。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-105">Use the Windows Group Policy tool (gpedit.msc) to enable this policy for the account used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ed0c-106">必须是系统管理员才能更改此策略。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-106">You must be a system administrator to change this policy.</span></span>  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a><span data-ttu-id="1ed0c-107">启用“锁定内存页”选项</span><span class="sxs-lookup"><span data-stu-id="1ed0c-107">To enable the lock pages in memory option</span></span>  
  
1.  <span data-ttu-id="1ed0c-108">在 **“开始”** 菜单上，单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-108">On the **Start** menu, click **Run**.</span></span> <span data-ttu-id="1ed0c-109">在 "**打开**" 框中，键入 `gpedit.msc` 。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-109">In the **Open** box, type `gpedit.msc`.</span></span>  
  
2.  <span data-ttu-id="1ed0c-110">在 **“本地组策略编辑器”** 控制台上，展开 **“计算机配置”** ，再展开 **“Windows 设置”** 。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-110">On the **Local Group Policy Editor** console, expand **Computer Configuration**, and then expand **Windows Settings**.</span></span>  
  
3.  <span data-ttu-id="1ed0c-111">展开 **“安全设置”** ，再展开 **“本地策略”** 。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-111">Expand **Security Settings**, and then expand **Local Policies**.</span></span>  
  
4.  <span data-ttu-id="1ed0c-112">选择 **“用户权利指派”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-112">Select the **User Rights Assignment** folder.</span></span>  
  
     <span data-ttu-id="1ed0c-113">细节窗格中随即显示出策略。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-113">The policies will be displayed in the details pane.</span></span>  
  
5.  <span data-ttu-id="1ed0c-114">在该窗格中，双击“锁定内存页”。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-114">In the pane, double-click **Lock pages in memory**.</span></span>  
  
6.  <span data-ttu-id="1ed0c-115">在“本地安全设置 - 锁定内存中的页”对话框中，单击“添加用户或组” 。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-115">In the **Local Security Setting - Lock pages in memory** dialog box, click **Add User or Group**.</span></span>  
  
7.  <span data-ttu-id="1ed0c-116">在 **“选择用户、服务帐户或组”** 对话框中，添加有权运行 sqlservr.exe 的帐户。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-116">In the **Select Users, Service Accounts, or Groups** dialog box, add an account with privileges to run sqlservr.exe.</span></span>  
  
8.  <span data-ttu-id="1ed0c-117">注销后重新登录，此更改才生效。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-117">Log out and then log back in for this change to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed0c-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ed0c-118">See Also</span></span>  
 [<span data-ttu-id="1ed0c-119">“服务器内存”服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="1ed0c-119">Server Memory Server Configuration Options</span></span>](server-memory-server-configuration-options.md)  
  
  
