---
uid: web-forms/overview/ajax-control-toolkit/getting-started/creating-a-custom-ajax-control-toolkit-control-extender-cs
title: "创建自定义 AJAX 控件工具包控件扩展程序 (C#) |Microsoft 文档"
author: microsoft
description: "自定义扩展程序，可以自定义和扩展 ASP.NET 控件的功能而无需创建新类。"
ms.author: aspnetcontent
manager: wpickett
ms.date: 05/12/2009
ms.topic: article
ms.assetid: 96b56eca-a892-45a4-96b4-67e61178650a
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/getting-started/creating-a-custom-ajax-control-toolkit-control-extender-cs
msc.type: authoredcontent
ms.openlocfilehash: 2ae03484dd1161c65b77f4718bb8cedb5abfdd82
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2017
---
<a name="creating-a-custom-ajax-control-toolkit-control-extender-c"></a><span data-ttu-id="d256c-103">创建自定义 AJAX 控件工具包控件扩展程序 (C#)</span><span class="sxs-lookup"><span data-stu-id="d256c-103">Creating a Custom AJAX Control Toolkit Control Extender (C#)</span></span>
====================
<span data-ttu-id="d256c-104">通过[Microsoft](https://github.com/microsoft)</span><span class="sxs-lookup"><span data-stu-id="d256c-104">by [Microsoft](https://github.com/microsoft)</span></span>

> <span data-ttu-id="d256c-105">自定义扩展程序，可以自定义和扩展 ASP.NET 控件的功能而无需创建新类。</span><span class="sxs-lookup"><span data-stu-id="d256c-105">Custom Extenders enable you to customize and extend the capabilities of ASP.NET controls without having to create new classes.</span></span>


<span data-ttu-id="d256c-106">在本教程中，您将学习如何创建自定义的 AJAX 控件工具包控件扩展程序。</span><span class="sxs-lookup"><span data-stu-id="d256c-106">In this tutorial, you learn how to create a custom AJAX Control Toolkit control extender.</span></span> <span data-ttu-id="d256c-107">我们将创建一个简单、 但有用，新的扩展程序从禁用启用时文本框中键入文本更改按钮的状态。</span><span class="sxs-lookup"><span data-stu-id="d256c-107">We create a simple, but useful, new extender that changes the state of a Button from disabled to enabled when you type text into a TextBox.</span></span> <span data-ttu-id="d256c-108">阅读完本教程之后, 你将能够扩展 ASP.NET AJAX 工具包使用你自己的控件扩展器。</span><span class="sxs-lookup"><span data-stu-id="d256c-108">After reading this tutorial, you will be able to extend the ASP.NET AJAX Toolkit with your own control extenders.</span></span>

<span data-ttu-id="d256c-109">你可以创建自定义控件扩展程序使用 Visual Studio 或 Visual Web Developer （请确保你有 Visual Web Developer 的最新版本）。</span><span class="sxs-lookup"><span data-stu-id="d256c-109">You can create custom control extenders using either Visual Studio or Visual Web Developer (make sure that you have the latest version of Visual Web Developer).</span></span>

## <a name="overview-of-the-disabledbutton-extender"></a><span data-ttu-id="d256c-110">DisabledButton 扩展程序的概述</span><span class="sxs-lookup"><span data-stu-id="d256c-110">Overview of the DisabledButton Extender</span></span>

<span data-ttu-id="d256c-111">我们新控件扩展程序被命名为 DisabledButton 扩展程序。</span><span class="sxs-lookup"><span data-stu-id="d256c-111">Our new control extender is named the DisabledButton extender.</span></span> <span data-ttu-id="d256c-112">此扩展将具有三个属性：</span><span class="sxs-lookup"><span data-stu-id="d256c-112">This extender will have three properties:</span></span>

- <span data-ttu-id="d256c-113">TargetControlID-控件扩展文本框。</span><span class="sxs-lookup"><span data-stu-id="d256c-113">TargetControlID - The TextBox that the control extends.</span></span>
- <span data-ttu-id="d256c-114">TargetButtonIID-已禁用或启用的按钮。</span><span class="sxs-lookup"><span data-stu-id="d256c-114">TargetButtonIID - The Button that is disabled or enabled.</span></span>
- <span data-ttu-id="d256c-115">DisabledText-最初显示的按钮中的文本。</span><span class="sxs-lookup"><span data-stu-id="d256c-115">DisabledText - The text that is initially displayed in the Button.</span></span> <span data-ttu-id="d256c-116">当你开始键入时，按钮将显示按钮文本属性的值。</span><span class="sxs-lookup"><span data-stu-id="d256c-116">When you start typing, the Button displays the value of the Button Text property.</span></span>

<span data-ttu-id="d256c-117">可以将挂接 DisabledButton 扩展程序添加到文本框和按钮控件。</span><span class="sxs-lookup"><span data-stu-id="d256c-117">You hook the DisabledButton extender to a TextBox and Button control.</span></span> <span data-ttu-id="d256c-118">您输入的任何文本之前，将禁用的按钮和文本框和按钮如下所示：</span><span class="sxs-lookup"><span data-stu-id="d256c-118">Before you type any text, the Button is disabled and the TextBox and Button look like this:</span></span>


[![](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image2.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image1.png)

<span data-ttu-id="d256c-119">([单击以查看实际尺寸的图像](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="d256c-119">([Click to view full-size image](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image3.png))</span></span>


<span data-ttu-id="d256c-120">开始键入文本后，会启用该按钮和文本框和按钮如下所示：</span><span class="sxs-lookup"><span data-stu-id="d256c-120">After you start typing text, the Button is enabled and the TextBox and Button look like this:</span></span>


[![](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image5.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image4.png)

<span data-ttu-id="d256c-121">([单击以查看实际尺寸的图像](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image6.png))</span><span class="sxs-lookup"><span data-stu-id="d256c-121">([Click to view full-size image](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image6.png))</span></span>


<span data-ttu-id="d256c-122">若要创建我们控件扩展程序，我们需要创建以下三个文件：</span><span class="sxs-lookup"><span data-stu-id="d256c-122">To create our control extender, we need to create the following three files:</span></span>

- <span data-ttu-id="d256c-123">DisabledButtonExtender.cs-此文件是服务器端控件类，以便管理创建您的扩展器，允许你在设计时设置的属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-123">DisabledButtonExtender.cs - This file is the server-side control class that will manage creating your extender and allow you to set the properties at design-time.</span></span> <span data-ttu-id="d256c-124">它还定义了可以在您的扩展器设置的属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-124">It also defines the properties that can be set on your extender.</span></span> <span data-ttu-id="d256c-125">这些属性可通过代码和在设计时访问和匹配 DisableButtonBehavior.js 文件中定义的属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-125">These properties are accessible via code and at design time and match properties defined in the DisableButtonBehavior.js file.</span></span>
- <span data-ttu-id="d256c-126">DisabledButtonBehavior.js-此文件是你将添加所有你的客户端脚本逻辑。</span><span class="sxs-lookup"><span data-stu-id="d256c-126">DisabledButtonBehavior.js -- This file is where you will add all of your client script logic.</span></span>
- <span data-ttu-id="d256c-127">DisabledButtonDesigner.cs-此类使设计时功能。</span><span class="sxs-lookup"><span data-stu-id="d256c-127">DisabledButtonDesigner.cs - This class enables design-time functionality.</span></span> <span data-ttu-id="d256c-128">如果你想要正常使用 Visual Studio/Visual Web Developer 设计器的控件扩展程序，你需要此类。</span><span class="sxs-lookup"><span data-stu-id="d256c-128">You need this class if you want the control extender to work correctly with the Visual Studio/Visual Web Developer Designer.</span></span>

<span data-ttu-id="d256c-129">因此控件扩展程序包含服务器端控件、 一个客户端行为和服务器端设计器类。</span><span class="sxs-lookup"><span data-stu-id="d256c-129">So a control extender consists of a server-side control, a client-side behavior, and a server-side designer class.</span></span> <span data-ttu-id="d256c-130">了解如何在以下各节中创建这些文件的所有三个。</span><span class="sxs-lookup"><span data-stu-id="d256c-130">You learn how to create all three of these files in the following sections.</span></span>

## <a name="creating-the-custom-extender-website-and-project"></a><span data-ttu-id="d256c-131">创建自定义扩展程序网站和项目</span><span class="sxs-lookup"><span data-stu-id="d256c-131">Creating the Custom Extender Website and Project</span></span>

<span data-ttu-id="d256c-132">第一步是在 Visual Studio/Visual Web Developer 中创建类库项目和网站。</span><span class="sxs-lookup"><span data-stu-id="d256c-132">The first step is to create a class library project and website in Visual Studio/Visual Web Developer.</span></span> <span data-ttu-id="d256c-133">我们 ll 在类库项目中创建的自定义的扩展程序和网站中测试自定义的扩展程序。</span><span class="sxs-lookup"><span data-stu-id="d256c-133">We�ll create the custom extender in the class library project and test the custom extender in the website.</span></span>

<span data-ttu-id="d256c-134">让我们来启动与网站。</span><span class="sxs-lookup"><span data-stu-id="d256c-134">Let�s start with the website.</span></span> <span data-ttu-id="d256c-135">请按照下列步骤以创建网站：</span><span class="sxs-lookup"><span data-stu-id="d256c-135">Follow these steps to create the website:</span></span>

1. <span data-ttu-id="d256c-136">选择菜单选项**文件、 新的 Web 站点**。</span><span class="sxs-lookup"><span data-stu-id="d256c-136">Select the menu option **File, New Web Site**.</span></span>
2. <span data-ttu-id="d256c-137">选择**ASP.NET 网站**模板。</span><span class="sxs-lookup"><span data-stu-id="d256c-137">Select the **ASP.NET Web Site** template.</span></span>
3. <span data-ttu-id="d256c-138">将新的网站命名*Website1*。</span><span class="sxs-lookup"><span data-stu-id="d256c-138">Name the new website *Website1*.</span></span>
4. <span data-ttu-id="d256c-139">单击**确定**按钮。</span><span class="sxs-lookup"><span data-stu-id="d256c-139">Click the **OK** button.</span></span>

<span data-ttu-id="d256c-140">接下来，我们需要创建类库项目将包含该控件扩展程序的代码：</span><span class="sxs-lookup"><span data-stu-id="d256c-140">Next, we need to create the class library project that will contain the code for the control extender:</span></span>

1. <span data-ttu-id="d256c-141">选择菜单选项**文件，添加和新项目**。</span><span class="sxs-lookup"><span data-stu-id="d256c-141">Select the menu option **File, Add, New Project**.</span></span>
2. <span data-ttu-id="d256c-142">选择**类库**模板。</span><span class="sxs-lookup"><span data-stu-id="d256c-142">Select the **Class Library** template.</span></span>
3. <span data-ttu-id="d256c-143">名称命名的新类库**CustomExtenders**。</span><span class="sxs-lookup"><span data-stu-id="d256c-143">Name the new class library with the name **CustomExtenders**.</span></span>
4. <span data-ttu-id="d256c-144">单击**确定**按钮。</span><span class="sxs-lookup"><span data-stu-id="d256c-144">Click the **OK** button.</span></span>

<span data-ttu-id="d256c-145">完成这些步骤后，你的解决方案资源管理器窗口应如下所示图 1。</span><span class="sxs-lookup"><span data-stu-id="d256c-145">After you complete these steps, your Solution Explorer window should look like Figure 1.</span></span>


<span data-ttu-id="d256c-146">[![与网站和类库项目的解决方案](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image8.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image7.png)</span><span class="sxs-lookup"><span data-stu-id="d256c-146">[![Solution with website and class library project](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image8.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image7.png)</span></span>

<span data-ttu-id="d256c-147">**图 01**： 与网站和类库项目的解决方案 ([单击以查看实际尺寸的图像](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image9.png))</span><span class="sxs-lookup"><span data-stu-id="d256c-147">**Figure 01**: Solution with website and class library project([Click to view full-size image](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image9.png))</span></span>


<span data-ttu-id="d256c-148">接下来，你需要添加所有对该类库项目的必要的程序集引用：</span><span class="sxs-lookup"><span data-stu-id="d256c-148">Next, you need to add all of the necessary assembly references to the class library project:</span></span>

1. <span data-ttu-id="d256c-149">右键单击 CustomExtenders 项目并选择菜单选项**添加引用**。</span><span class="sxs-lookup"><span data-stu-id="d256c-149">Right-click the CustomExtenders project and select the menu option **Add Reference**.</span></span>
2. <span data-ttu-id="d256c-150">选择.NET 选项卡。</span><span class="sxs-lookup"><span data-stu-id="d256c-150">Select the .NET tab.</span></span>
3. <span data-ttu-id="d256c-151">添加对下列程序集的引用：</span><span class="sxs-lookup"><span data-stu-id="d256c-151">Add references to the following assemblies:</span></span>

    1. <span data-ttu-id="d256c-152">System.Web.dll</span><span class="sxs-lookup"><span data-stu-id="d256c-152">System.Web.dll</span></span>
    2. <span data-ttu-id="d256c-153">System.Web.Extensions.dll</span><span class="sxs-lookup"><span data-stu-id="d256c-153">System.Web.Extensions.dll</span></span>
    3. <span data-ttu-id="d256c-154">System.Design.dll</span><span class="sxs-lookup"><span data-stu-id="d256c-154">System.Design.dll</span></span>
    4. <span data-ttu-id="d256c-155">System.Web.Extensions.Design.dll</span><span class="sxs-lookup"><span data-stu-id="d256c-155">System.Web.Extensions.Design.dll</span></span>
4. <span data-ttu-id="d256c-156">选择浏览选项卡。</span><span class="sxs-lookup"><span data-stu-id="d256c-156">Select the Browse tab.</span></span>
5. <span data-ttu-id="d256c-157">添加对 AjaxControlToolkit.dll 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="d256c-157">Add a reference to the AjaxControlToolkit.dll assembly.</span></span> <span data-ttu-id="d256c-158">此程序集位于下载 AJAX 控件工具包的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d256c-158">This assembly is located in the folder where you downloaded the AJAX Control Toolkit.</span></span>

<span data-ttu-id="d256c-159">完成这些步骤后，你类库项目 References 文件夹应该如图 2 所示。</span><span class="sxs-lookup"><span data-stu-id="d256c-159">After you complete these steps, your class library project References folder should look like Figure 2.</span></span>


<span data-ttu-id="d256c-160">[![与所需的引用的引用文件夹](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image11.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image10.png)</span><span class="sxs-lookup"><span data-stu-id="d256c-160">[![References folder with required references](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image11.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image10.png)</span></span>

<span data-ttu-id="d256c-161">**图 02**： 所需的引用的引用文件夹 ([单击以查看实际尺寸的图像](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image12.png))</span><span class="sxs-lookup"><span data-stu-id="d256c-161">**Figure 02**: References folder with required references([Click to view full-size image](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image12.png))</span></span>


## <a name="creating-the-custom-control-extender"></a><span data-ttu-id="d256c-162">创建自定义控件扩展</span><span class="sxs-lookup"><span data-stu-id="d256c-162">Creating the Custom Control Extender</span></span>

<span data-ttu-id="d256c-163">现在，我们已我们类的库，我们可以开始生成我们扩展程序控件。</span><span class="sxs-lookup"><span data-stu-id="d256c-163">Now that we have our class library, we can start building our extender control.</span></span> <span data-ttu-id="d256c-164">允许 s 开头准系统的自定义的扩展程序控件类 （请参阅列表 1）。</span><span class="sxs-lookup"><span data-stu-id="d256c-164">Let�s start with the bare bones of a custom extender control class (see Listing 1).</span></span>

<span data-ttu-id="d256c-165">**列表 1-MyCustomExtender.cs**</span><span class="sxs-lookup"><span data-stu-id="d256c-165">**Listing 1 - MyCustomExtender.cs**</span></span>

[!code-csharp[Main](creating-a-custom-ajax-control-toolkit-control-extender-cs/samples/sample1.cs)]

<span data-ttu-id="d256c-166">有几种您注意到了列表 1 中的控件扩展程序类的方法。</span><span class="sxs-lookup"><span data-stu-id="d256c-166">There are several things that you notice about the control extender class in Listing 1.</span></span> <span data-ttu-id="d256c-167">首先，请注意此类从 ExtenderControlBase 基类继承。</span><span class="sxs-lookup"><span data-stu-id="d256c-167">First, notice that the class inherits from the base ExtenderControlBase class.</span></span> <span data-ttu-id="d256c-168">所有 AJAX 控件工具包扩展程序控件都派生自这个基类。</span><span class="sxs-lookup"><span data-stu-id="d256c-168">All AJAX Control Toolkit extender controls derive from this base class.</span></span> <span data-ttu-id="d256c-169">例如，基类包括为每个控件扩展程序的必需的属性的 TargetID 属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-169">For example, the base class includes the TargetID property that is a required property of every control extender.</span></span>

<span data-ttu-id="d256c-170">接下来，请注意，此类包含与客户端脚本相关的以下两个属性：</span><span class="sxs-lookup"><span data-stu-id="d256c-170">Next, notice that the class includes the following two attributes related to client script:</span></span>

- <span data-ttu-id="d256c-171">Web 资源的会导致要作为嵌入资源的程序集中包含的文件。</span><span class="sxs-lookup"><span data-stu-id="d256c-171">WebResource - Causes a file to be included as an embedded resource in an assembly.</span></span>
- <span data-ttu-id="d256c-172">ClientScriptResource-会导致脚本资源要从程序集检索。</span><span class="sxs-lookup"><span data-stu-id="d256c-172">ClientScriptResource - Causes a script resource to be retrieved from an assembly.</span></span>

<span data-ttu-id="d256c-173">Web 资源属性用于编译自定义的扩展程序时，将 MyControlBehavior.js JavaScript 文件嵌入到程序集。</span><span class="sxs-lookup"><span data-stu-id="d256c-173">The WebResource attribute is used to embed the MyControlBehavior.js JavaScript file into the assembly when the custom extender is compiled.</span></span> <span data-ttu-id="d256c-174">ClientScriptResource 属性用于在网页中使用的自定义的扩展程序时的程序集中检索 MyControlBehavior.js 脚本。</span><span class="sxs-lookup"><span data-stu-id="d256c-174">The ClientScriptResource attribute is used to retrieve the MyControlBehavior.js script from the assembly when the custom extender is used in a web page.</span></span>


<span data-ttu-id="d256c-175">在要工作的 web 资源和 ClientScriptResource 属性的顺序，您必须作为嵌入资源将编译 JavaScript 文件。</span><span class="sxs-lookup"><span data-stu-id="d256c-175">In order for the WebResource and ClientScriptResource attributes to work, you must compile the JavaScript file as an embedded resource.</span></span> <span data-ttu-id="d256c-176">选择解决方案资源管理器窗口中的文件，打开属性表中，并将值分配*嵌入的资源*到**生成操作**属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-176">Select the file in the Solution Explorer window, open the property sheet, and assign the value *Embedded Resource* to the **Build Action** property.</span></span>


<span data-ttu-id="d256c-177">请注意，该控件扩展程序还包含 TargetControlType 属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-177">Notice that the control extender also includes a TargetControlType attribute.</span></span> <span data-ttu-id="d256c-178">此属性用于指定由该控件扩展程序扩展的控件的类型。</span><span class="sxs-lookup"><span data-stu-id="d256c-178">This attribute is used to specify the type of control that is extended by the control extender.</span></span> <span data-ttu-id="d256c-179">列出 1，在该控件扩展程序用于扩展文本框。</span><span class="sxs-lookup"><span data-stu-id="d256c-179">In the case of Listing 1, the control extender is used to extend a TextBox.</span></span>

<span data-ttu-id="d256c-180">最后，请注意，自定义扩展包含名为 MyProperty 的属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-180">Finally, notice that the custom extender includes a property named MyProperty.</span></span> <span data-ttu-id="d256c-181">属性用 ExtenderControlProperty 特性标记。</span><span class="sxs-lookup"><span data-stu-id="d256c-181">The property is marked with the ExtenderControlProperty attribute.</span></span> <span data-ttu-id="d256c-182">GetPropertyValue() 和 SetPropertyValue() 方法用于将从服务器端控件扩展程序的属性值传递到客户端行为。</span><span class="sxs-lookup"><span data-stu-id="d256c-182">The GetPropertyValue() and SetPropertyValue() methods are used to pass the property value from the server-side control extender to the client-side behavior.</span></span>

<span data-ttu-id="d256c-183">让我们来继续操作并实现我们 DisabledButton 扩展程序的代码。</span><span class="sxs-lookup"><span data-stu-id="d256c-183">Let�s go ahead and implement the code for our DisabledButton extender.</span></span> <span data-ttu-id="d256c-184">列出 2 中找不到此扩展程序的代码。</span><span class="sxs-lookup"><span data-stu-id="d256c-184">The code for this extender can be found in Listing 2.</span></span>

<span data-ttu-id="d256c-185">**列出 2-DisabledButtonExtender.cs**</span><span class="sxs-lookup"><span data-stu-id="d256c-185">**Listing 2 - DisabledButtonExtender.cs**</span></span>

[!code-csharp[Main](creating-a-custom-ajax-control-toolkit-control-extender-cs/samples/sample2.cs)]

<span data-ttu-id="d256c-186">列出 2 中的 DisabledButton 扩展程序具有名为 TargetButtonID 和 DisabledText 的两个属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-186">The DisabledButton extender in Listing 2 has two properties named TargetButtonID and DisabledText.</span></span> <span data-ttu-id="d256c-187">应用于 TargetButtonID 属性 IDReferenceProperty 防止将按钮控件的 ID 以外的任何分配给此属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-187">The IDReferenceProperty applied to the TargetButtonID property prevents you from assigning anything other than the ID of a Button control to this property.</span></span>

<span data-ttu-id="d256c-188">Web 资源和 ClientScriptResource 属性将位于此扩展程序的名为 DisabledButtonBehavior.js 文件中的客户端行为相关联。</span><span class="sxs-lookup"><span data-stu-id="d256c-188">The WebResource and ClientScriptResource attributes associate a client-side behavior located in a file named DisabledButtonBehavior.js with this extender.</span></span> <span data-ttu-id="d256c-189">此 JavaScript 文件在下一部分中的，我们讨论。</span><span class="sxs-lookup"><span data-stu-id="d256c-189">We discuss this JavaScript file in the next section.</span></span>

## <a name="creating-the-custom-extender-behavior"></a><span data-ttu-id="d256c-190">创建自定义的扩展程序行为</span><span class="sxs-lookup"><span data-stu-id="d256c-190">Creating the Custom Extender Behavior</span></span>

<span data-ttu-id="d256c-191">控件扩展程序的客户端组件调用行为。</span><span class="sxs-lookup"><span data-stu-id="d256c-191">The client-side component of a control extender is called a behavior.</span></span> <span data-ttu-id="d256c-192">禁用和启用该按钮的实际逻辑包含在 DisabledButton 行为。</span><span class="sxs-lookup"><span data-stu-id="d256c-192">The actual logic for disabling and enabling the Button is contained in the DisabledButton behavior.</span></span> <span data-ttu-id="d256c-193">行为的 JavaScript 代码包含在列出 3 中。</span><span class="sxs-lookup"><span data-stu-id="d256c-193">The JavaScript code for the behavior is included in Listing 3.</span></span>

<span data-ttu-id="d256c-194">**列出 3-DisabledButton.js**</span><span class="sxs-lookup"><span data-stu-id="d256c-194">**Listing 3 - DisabledButton.js**</span></span>

[!code-javascript[Main](creating-a-custom-ajax-control-toolkit-control-extender-cs/samples/sample3.js)]

<span data-ttu-id="d256c-195">列出 3 中的 JavaScript 文件包含一个名为 DisabledButtonBehavior 的客户端类。</span><span class="sxs-lookup"><span data-stu-id="d256c-195">The JavaScript file in Listing 3 contains a client-side class named DisabledButtonBehavior.</span></span> <span data-ttu-id="d256c-196">此类，如其服务器端双向，包括两个属性名为 TargetButtonID 并使用户能够使用 DisabledText 获取\_TargetButtonID/set\_TargetButtonID 并获取\_DisabledText/set\_DisabledText。</span><span class="sxs-lookup"><span data-stu-id="d256c-196">This class, like its server-side twin, includes two properties named TargetButtonID and DisabledText which you can access using get\_TargetButtonID/set\_TargetButtonID and get\_DisabledText/set\_DisabledText.</span></span>

<span data-ttu-id="d256c-197">Initialize （） 方法将与行为的目标元素关联的 keyup 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="d256c-197">The initialize() method associates a keyup event handler with the target element for the behavior.</span></span> <span data-ttu-id="d256c-198">与此行为关联的文本框中键入字母每次 keyup 处理程序执行。</span><span class="sxs-lookup"><span data-stu-id="d256c-198">Each time you type a letter into the TextBox associated with this behavior, the keyup handler executes.</span></span> <span data-ttu-id="d256c-199">Keyup 处理程序启用，或禁用的按钮，具体取决于是否包含任何文本与行为关联的文本框。</span><span class="sxs-lookup"><span data-stu-id="d256c-199">The keyup handler either enables or disables the Button depending on whether the TextBox associated with the behavior contains any text.</span></span>

<span data-ttu-id="d256c-200">请记住，必须编译作为嵌入资源清单 3 中的 JavaScript 文件。</span><span class="sxs-lookup"><span data-stu-id="d256c-200">Remember that you must compile the JavaScript file in Listing 3 as an embedded resource.</span></span> <span data-ttu-id="d256c-201">选择解决方案资源管理器窗口中的文件，打开属性表中，并将值分配*嵌入的资源*到**生成操作**属性 （请参见图 3）。</span><span class="sxs-lookup"><span data-stu-id="d256c-201">Select the file in the Solution Explorer window, open the property sheet, and assign the value *Embedded Resource* to the **Build Action** property (see Figure 3).</span></span> <span data-ttu-id="d256c-202">此选项是在 Visual Studio 和 Visual Web Developer 中可用。</span><span class="sxs-lookup"><span data-stu-id="d256c-202">This option is available in both Visual Studio and Visual Web Developer.</span></span>


<span data-ttu-id="d256c-203">[![添加一个 JavaScript 文件作为嵌入资源](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image14.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image13.png)</span><span class="sxs-lookup"><span data-stu-id="d256c-203">[![Adding a JavaScript file as an embedded resource](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image14.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image13.png)</span></span>

<span data-ttu-id="d256c-204">**图 03**： 添加一个 JavaScript 文件作为嵌入资源 ([单击以查看实际尺寸的图像](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image15.png))</span><span class="sxs-lookup"><span data-stu-id="d256c-204">**Figure 03**: Adding a JavaScript file as an embedded resource([Click to view full-size image](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image15.png))</span></span>


## <a name="creating-the-custom-extender-designer"></a><span data-ttu-id="d256c-205">创建自定义的扩展程序设计器</span><span class="sxs-lookup"><span data-stu-id="d256c-205">Creating the Custom Extender Designer</span></span>

<span data-ttu-id="d256c-206">没有一个我们需要进行创建，以完成我们扩展程序的最后一个类。</span><span class="sxs-lookup"><span data-stu-id="d256c-206">There is one last class that we need to create to complete our extender.</span></span> <span data-ttu-id="d256c-207">我们需要在列出 4 中创建设计器类。</span><span class="sxs-lookup"><span data-stu-id="d256c-207">We need to create the designer class in Listing 4.</span></span> <span data-ttu-id="d256c-208">此类才能与 Visual Studio/Visual Web Developer 设计器的正确行为的扩展程序。</span><span class="sxs-lookup"><span data-stu-id="d256c-208">This class is required to make the extender behave correctly with the Visual Studio/Visual Web Developer Designer.</span></span>

<span data-ttu-id="d256c-209">**列出 4-DisabledButtonDesigner.cs**</span><span class="sxs-lookup"><span data-stu-id="d256c-209">**Listing 4 - DisabledButtonDesigner.cs**</span></span>

[!code-csharp[Main](creating-a-custom-ajax-control-toolkit-control-extender-cs/samples/sample4.cs)]

<span data-ttu-id="d256c-210">你将使用设计器特性的 DisabledButton 扩展程序与关联的设计器中列出的 4。你需要将该设计器属性应用到 DisabledButtonExtender 类如下：</span><span class="sxs-lookup"><span data-stu-id="d256c-210">You associate the designer in Listing 4 with the DisabledButton extender with the Designer attribute.You need to apply the Designer attribute to the DisabledButtonExtender class like this:</span></span>

[!code-csharp[Main](creating-a-custom-ajax-control-toolkit-control-extender-cs/samples/sample5.cs)]

## <a name="using-the-custom-extender"></a><span data-ttu-id="d256c-211">使用自定义的扩展程序</span><span class="sxs-lookup"><span data-stu-id="d256c-211">Using the Custom Extender</span></span>

<span data-ttu-id="d256c-212">现在，我们已完成创建 DisabledButton 控件扩展程序，就可以在我们的 ASP.NET 网站中使用它。</span><span class="sxs-lookup"><span data-stu-id="d256c-212">Now that we have finished creating the DisabledButton control extender, it is time to use it in our ASP.NET website.</span></span> <span data-ttu-id="d256c-213">首先，我们需要向工具箱添加自定义的扩展程序。</span><span class="sxs-lookup"><span data-stu-id="d256c-213">First, we need to add the custom extender to the toolbox.</span></span> <span data-ttu-id="d256c-214">请执行这些步骤：</span><span class="sxs-lookup"><span data-stu-id="d256c-214">Follow these steps:</span></span>

1. <span data-ttu-id="d256c-215">通过双击解决方案资源管理器窗口中的网页中打开 ASP.NET 页。</span><span class="sxs-lookup"><span data-stu-id="d256c-215">Open an ASP.NET page by double-clicking the page in the Solution Explorer window.</span></span>
2. <span data-ttu-id="d256c-216">右击工具箱并选择菜单选项**选择项**。</span><span class="sxs-lookup"><span data-stu-id="d256c-216">Right-click the toolbox and select the menu option **Choose Items**.</span></span>
3. <span data-ttu-id="d256c-217">在选择工具箱项对话框中，浏览到 CustomExtenders.dll 程序集。</span><span class="sxs-lookup"><span data-stu-id="d256c-217">In the Choose Toolbox Items dialog, browse to the CustomExtenders.dll assembly.</span></span>
4. <span data-ttu-id="d256c-218">单击**确定**按钮以关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="d256c-218">Click the **OK** button to close the dialog.</span></span>

<span data-ttu-id="d256c-219">完成这些步骤后，DisabledButton 控件扩展程序应出现在工具箱 （请参见图 4）。</span><span class="sxs-lookup"><span data-stu-id="d256c-219">After you complete these steps, the DisabledButton control extender should appear in the toolbox (see Figure 4).</span></span>


<span data-ttu-id="d256c-220">[![在工具箱 DisabledButton](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image17.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image16.png)</span><span class="sxs-lookup"><span data-stu-id="d256c-220">[![DisabledButton in the toolbox](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image17.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image16.png)</span></span>

<span data-ttu-id="d256c-221">**图 04**: 工具箱中的 DisabledButton ([单击以查看实际尺寸的图像](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image18.png))</span><span class="sxs-lookup"><span data-stu-id="d256c-221">**Figure 04**: DisabledButton in the toolbox([Click to view full-size image](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image18.png))</span></span>


<span data-ttu-id="d256c-222">接下来，我们需要创建一个新的 ASP.NET 页。</span><span class="sxs-lookup"><span data-stu-id="d256c-222">Next, we need to create a new ASP.NET page.</span></span> <span data-ttu-id="d256c-223">请执行这些步骤：</span><span class="sxs-lookup"><span data-stu-id="d256c-223">Follow these steps:</span></span>

1. <span data-ttu-id="d256c-224">创建一个名为 ShowDisabledButton.aspx 的新 ASP.NET 页。</span><span class="sxs-lookup"><span data-stu-id="d256c-224">Create a new ASP.NET page named ShowDisabledButton.aspx.</span></span>
2. <span data-ttu-id="d256c-225">ScriptManager 拖到页。</span><span class="sxs-lookup"><span data-stu-id="d256c-225">Drag a ScriptManager onto the page.</span></span>
3. <span data-ttu-id="d256c-226">将 TextBox 控件拖到该页面。</span><span class="sxs-lookup"><span data-stu-id="d256c-226">Drag a TextBox control onto the page.</span></span>
4. <span data-ttu-id="d256c-227">将按钮控件拖到该页面。</span><span class="sxs-lookup"><span data-stu-id="d256c-227">Drag a Button control onto the page.</span></span>
5. <span data-ttu-id="d256c-228">在属性窗口中，将更改按钮 ID 属性的值*btnSave*和值的文本属性*保存\**。</span><span class="sxs-lookup"><span data-stu-id="d256c-228">In the Properties window, change the Button ID property to the value *btnSave* and the Text property to the value *Save\**.</span></span>
  

<span data-ttu-id="d256c-229">我们创建了一个页面，标准 ASP.NET 文本框和按钮控件。</span><span class="sxs-lookup"><span data-stu-id="d256c-229">We created a page with a standard ASP.NET TextBox and Button control.</span></span>

<span data-ttu-id="d256c-230">接下来，我们需要扩展带 DisabledButton 扩展程序的 TextBox 控件：</span><span class="sxs-lookup"><span data-stu-id="d256c-230">Next, we need to extend the TextBox control with the DisabledButton extender:</span></span>

1. <span data-ttu-id="d256c-231">选择**添加扩展程序**任务选项来打开扩展程序向导对话框 （请参见图 5）。</span><span class="sxs-lookup"><span data-stu-id="d256c-231">Select the **Add Extender** task option to open the Extender Wizard dialog (see Figure 5).</span></span> <span data-ttu-id="d256c-232">请注意对话框包括我们自定义的 DisabledButton 扩展程序。</span><span class="sxs-lookup"><span data-stu-id="d256c-232">Notice that the dialog includes our custom DisabledButton extender.</span></span>
2. <span data-ttu-id="d256c-233">选择 DisabledButton 扩展程序，然后单击**确定**按钮。</span><span class="sxs-lookup"><span data-stu-id="d256c-233">Select the DisabledButton extender and click the **OK** button.</span></span>


<span data-ttu-id="d256c-234">[![扩展程序向导对话框](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image20.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image19.png)</span><span class="sxs-lookup"><span data-stu-id="d256c-234">[![The Extender Wizard dialog](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image20.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image19.png)</span></span>

<span data-ttu-id="d256c-235">**图 05**: 扩展程序向导对话框 ([单击以查看实际尺寸的图像](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image21.png))</span><span class="sxs-lookup"><span data-stu-id="d256c-235">**Figure 05**: The Extender Wizard dialog([Click to view full-size image](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image21.png))</span></span>


<span data-ttu-id="d256c-236">最后，我们可以设置 DisabledButton 扩展程序的属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-236">Finally, we can set the properties of the DisabledButton extender.</span></span> <span data-ttu-id="d256c-237">你可以通过修改文本框控件的属性来修改 DisabledButton 扩展程序的属性：</span><span class="sxs-lookup"><span data-stu-id="d256c-237">You can modify the properties of the DisabledButton extender by modifying the properties of the TextBox control:</span></span>

1. <span data-ttu-id="d256c-238">在设计器中选择文本框。</span><span class="sxs-lookup"><span data-stu-id="d256c-238">Select the TextBox in the Designer.</span></span>
2. <span data-ttu-id="d256c-239">在属性窗口中，展开扩展节点 （请参阅图 6）。</span><span class="sxs-lookup"><span data-stu-id="d256c-239">In the Properties window, expand the Extenders node (see Figure 6).</span></span>
3. <span data-ttu-id="d256c-240">将值分配*保存*DisabledText 属性和的值*btnSave*到 TargetButtonID 属性。</span><span class="sxs-lookup"><span data-stu-id="d256c-240">Assign the value *Save* to the DisabledText property and the value *btnSave* to the TargetButtonID property.</span></span>


<span data-ttu-id="d256c-241">[![设置扩展程序属性](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image23.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image22.png)</span><span class="sxs-lookup"><span data-stu-id="d256c-241">[![Setting extender properties](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image23.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image22.png)</span></span>

<span data-ttu-id="d256c-242">**图 06**： 设置扩展程序属性 ([单击以查看实际尺寸的图像](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image24.png))</span><span class="sxs-lookup"><span data-stu-id="d256c-242">**Figure 06**: Setting extender properties([Click to view full-size image](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image24.png))</span></span>


<span data-ttu-id="d256c-243">（通过点击 F5） 运行页面时，该按钮控件最初处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="d256c-243">When you run the page (by hitting F5), the Button control is initially disabled.</span></span> <span data-ttu-id="d256c-244">只要你开始在文本框中输入文本，按钮控件被启用 （请参阅图 7）。</span><span class="sxs-lookup"><span data-stu-id="d256c-244">As soon as you start entering text into the TextBox, the Button control is enabled (see Figure 7).</span></span>


<span data-ttu-id="d256c-245">[![操作 DisabledButton 扩展器](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image26.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image25.png)</span><span class="sxs-lookup"><span data-stu-id="d256c-245">[![The DisabledButton extender in action](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image26.png)](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image25.png)</span></span>

<span data-ttu-id="d256c-246">**图 07**: DisabledButton 扩展程序中操作 ([单击以查看实际尺寸的图像](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image27.png))</span><span class="sxs-lookup"><span data-stu-id="d256c-246">**Figure 07**: The DisabledButton extender in action([Click to view full-size image](creating-a-custom-ajax-control-toolkit-control-extender-cs/_static/image27.png))</span></span>


## <a name="summary"></a><span data-ttu-id="d256c-247">摘要</span><span class="sxs-lookup"><span data-stu-id="d256c-247">Summary</span></span>

<span data-ttu-id="d256c-248">本教程的目的是说明如何将扩展 AJAX 控件工具包带有自定义的扩展程序控件。</span><span class="sxs-lookup"><span data-stu-id="d256c-248">The goal of this tutorial was to explain how you can extend the AJAX Control Toolkit with custom extender controls.</span></span> <span data-ttu-id="d256c-249">在本教程中，我们创建了一个简单 DisabledButton 控件扩展程序添加。</span><span class="sxs-lookup"><span data-stu-id="d256c-249">In this tutorial, we created a simple DisabledButton control extender.</span></span> <span data-ttu-id="d256c-250">我们通过创建 DisabledButtonExtender 类、 DisabledButtonBehavior JavaScript 行为和 DisabledButtonDesigner 类实现了此扩展程序。</span><span class="sxs-lookup"><span data-stu-id="d256c-250">We implemented this extender by creating a DisabledButtonExtender class, a DisabledButtonBehavior JavaScript behavior, and a DisabledButtonDesigner class.</span></span> <span data-ttu-id="d256c-251">每当创建自定义控件扩展程序遵循一组类似的步骤。</span><span class="sxs-lookup"><span data-stu-id="d256c-251">You follow a similar set of steps whenever you create a custom control extender.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="d256c-252">[上一页](using-ajax-control-toolkit-controls-and-control-extenders-cs.md)
[下一页](get-started-with-the-ajax-control-toolkit-vb.md)</span><span class="sxs-lookup"><span data-stu-id="d256c-252">[Previous](using-ajax-control-toolkit-controls-and-control-extenders-cs.md)
[Next](get-started-with-the-ajax-control-toolkit-vb.md)</span></span>