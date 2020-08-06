---
title: 创建 Off By Default 策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 98fde3c5-297c-4d95-981e-95700bbf5ccd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16d0893c155627a41149263b5ce7b21a4a217b74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578162"
---
# <a name="create-the-off-by-default-policy"></a><span data-ttu-id="2b3e8-102">创建 Off By Default 策略</span><span class="sxs-lookup"><span data-stu-id="2b3e8-102">Create the Off By Default Policy</span></span>
  <span data-ttu-id="2b3e8-103">此任务创建一个基于外围应用配置器方面的名为 Mail Off 的条件。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-103">This task creates a condition named Mail Off that is based on the Surface Area Configuration facet.</span></span> <span data-ttu-id="2b3e8-104">然后，创建一个名为 Off By Default 的条件。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-104">Then, it creates a policy named Off By Default.</span></span>  
  
### <a name="to-create-the-mail-off-condition"></a><span data-ttu-id="2b3e8-105">创建 Mail Off 条件</span><span class="sxs-lookup"><span data-stu-id="2b3e8-105">To create the Mail Off condition</span></span>  
  
1.  <span data-ttu-id="2b3e8-106">在对象资源管理器中，依次展开“管理”\*\*\*\*、“策略管理”\*\*\*\* 和“方面”\*\*\*\*，右键单击“外围应用配置器”\*\*\*\*，然后单击“新建条件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-106">In Object Explorer, expand **Management**, expand **Policy Management**, expand **Facets**, right-click **Surface Area Configuration**, and then click **New Condition**.</span></span>  
  
2.  <span data-ttu-id="2b3e8-107">在“创建新条件”\*\*\*\* 对话框的“名称”\*\*\*\* 框中，输入 **Mail Off**。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-107">In the **Create New Condition** dialog box, in the **Name** box, type **Mail Off**.</span></span>  
  
3.  <span data-ttu-id="2b3e8-108">在“方面”\*\*\*\* 框中，确认选择了“外围应用配置器”\*\*\*\* 方面。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-108">In the **Facet** box, confirm that **Surface Area Configuration** facet is selected.</span></span>  
  
4.  <span data-ttu-id="2b3e8-109">在“表达式”\*\*\*\* 区域中，在“字段”\*\*\*\* 框中选择“\@DatabaseMailEnabled”\*\*\*\*，在“运算符”\*\*\*\* 框中选择“=”\*\*\*\*，然后在“值”\*\*\*\* 框中选择“False”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-109">In the **Expression** area, in the **Field** box, select **\@DatabaseMailEnabled**, in the **Operator** box select **=**, and in the **Value** select **False**.</span></span>  
  
5.  <span data-ttu-id="2b3e8-110">在“说明”\*\*\*\* 页上输入条件说明，然后单击“确定”\*\*\*\* 以创建条件。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-110">On the **Description** page, type a description of the condition, and then click **OK** to create the condition.</span></span>  
  
### <a name="to-create-the-off-by-default-policy"></a><span data-ttu-id="2b3e8-111">创建 Off By Default 策略</span><span class="sxs-lookup"><span data-stu-id="2b3e8-111">To create the Off By Default policy</span></span>  
  
1.  <span data-ttu-id="2b3e8-112">在对象资源管理器中，右键单击“外围应用配置器”\*\*\*\*，然后单击“新建策略”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-112">In Object Explorer, right-click **Surface Area Configuration**, and then click **New Policy**.</span></span>  
  
2.  <span data-ttu-id="2b3e8-113">在“创建新策略”\*\*\*\* 对话框的“名称”\*\*\*\* 框中，输入 **Off By Default**。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-113">In the **Create New Policy** dialog box, in the **Name** box, type **Off By Default**.</span></span>  
  
3.  <span data-ttu-id="2b3e8-114">取消选中“已启用”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-114">Leave the **Enabled** checkbox unchecked.</span></span> <span data-ttu-id="2b3e8-115">“已启用”\*\*\*\* 复选框适用于自动策略，而此策略是按需执行的。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-115">The **Enabled** checkbox applies to automated policies, and this policy will be executed on demand.</span></span>  
  
4.  <span data-ttu-id="2b3e8-116">在“检查条件”\*\*\*\* 复选框中，向下滚动到“外围应用配置器”\*\*\*\* 区域，然后选择“Mail Off”\*\*\*\* 作为要检查的条件。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-116">In the **Check condition** checkbox, scroll down to the **Surface Area Configuration** area, and then select **Mail Off** as the condition to check.</span></span>  
  
5.  <span data-ttu-id="2b3e8-117">“针对目标”\*\*\*\* 框为空，因为这是一个服务器范围内的策略。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-117">The **Against targets** box will be blank because this is a server-scoped policy.</span></span>  
  
6.  <span data-ttu-id="2b3e8-118">在“评估模式”\*\*\*\* 复选框中，选择“按需”\*\*\*\* 作为评估模式。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-118">In the **Evaluation Mode** checkbox, select **On demand** as the evaluation mode.</span></span>  
  
7.  <span data-ttu-id="2b3e8-119">在“服务器限制”\*\*\*\* 复选框中，选择“无”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-119">In the **Server restriction** checkbox, select **None**.</span></span>  
  
8.  <span data-ttu-id="2b3e8-120">在“说明”\*\*\*\* 页上，输入策略的说明。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-120">On the **Description** page, type a description of the policy.</span></span>  
  
9. <span data-ttu-id="2b3e8-121">可以在“更多帮助超链接”\*\*\*\* 区域中提供策略网页的超链接。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-121">You can provide a hyperlink to a Web page for your policies in the **Additional help hyperlink** area.</span></span> <span data-ttu-id="2b3e8-122">请在“要显示的文本”\*\*\*\* 框中，输入为超链接显示的文本。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-122">In the **Text to display** box, type the text that will appear for the hyperlink.</span></span>  
  
10. <span data-ttu-id="2b3e8-123">在“地址”\*\*\*\* 框中输入“帮助”页的超链接，例如，公司 IT 部门的主页。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-123">In the **Address** box, type a hyperlink to a Help page, such as the home page for the IT department of your company.</span></span>  
  
11. <span data-ttu-id="2b3e8-124">若要通过打开网页来确认地址是否正确，请单击“测试链接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b3e8-124">To confirm the address by opening the Web page, click **Test Link**.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2b3e8-125">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="2b3e8-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2b3e8-126">将服务器配置为运行 Off By Default 策略</span><span class="sxs-lookup"><span data-stu-id="2b3e8-126">Configure a Server to Run the Off By Default Policy</span></span>](lesson-1-2-configure-a-server-to-run-the-off-by-default-policy.md)  
  
  
