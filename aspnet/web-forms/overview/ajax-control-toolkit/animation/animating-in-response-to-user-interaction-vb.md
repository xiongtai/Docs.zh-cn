---
uid: web-forms/overview/ajax-control-toolkit/animation/animating-in-response-to-user-interaction-vb
title: 对进行动画处理以响应用户交互 (VB) |Microsoft 文档
author: wenz
description: ASP.NET AJAX 控件工具包中的动画控件不只是一个控件，但一个整个框架，以向控件添加动画。 动画可以星...
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: c8204c05-ec27-40fe-933d-88e4e727a482
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/animation/animating-in-response-to-user-interaction-vb
msc.type: authoredcontent
ms.openlocfilehash: e12467bfeb88c2ab9d1cfb866506e9e8e7f9ae25
ms.sourcegitcommit: f8852267f463b62d7f975e56bea9aa3f68fbbdeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/06/2018
---
<a name="animating-in-response-to-user-interaction-vb"></a>对进行动画处理以响应用户交互 (VB)
====================
通过[Christian Wenz](https://github.com/wenz)

[下载代码](http://download.microsoft.com/download/f/9/a/f9a26acd-8df4-4484-8a18-199e4598f411/Animation6.vb.zip)或[下载 PDF](http://download.microsoft.com/download/6/7/1/6718d452-ff89-4d3f-a90e-c74ec2d636a3/animation6VB.pdf)

> ASP.NET AJAX 控件工具包中的动画控件不只是一个控件，但一个整个框架，以向控件添加动画。 动画会自动启动，或可能会触发由用户交互，例如通过使用鼠标单击。


## <a name="overview"></a>概述

ASP.NET AJAX 控件工具包中的动画控件不只是一个控件，但一个整个框架，以向控件添加动画。 动画会自动启动，或可能会触发由用户交互，例如通过使用鼠标单击。

## <a name="steps"></a>步骤

首先，包括`ScriptManager`在页中; 然后，ASP.NET AJAX 库加载后，使其可以使用该控件工具包：

[!code-aspx[Main](animating-in-response-to-user-interaction-vb/samples/sample1.aspx)]

动画将应用于如下所示的文本的一个面板中：

[!code-aspx[Main](animating-in-response-to-user-interaction-vb/samples/sample2.aspx)]

在关联 CSS 类中的面板，定义一种很好的背景色，并且还设置面板的宽度固定:

[!code-css[Main](animating-in-response-to-user-interaction-vb/samples/sample3.css)]

然后，将添加`AnimationExtender`到页中，提供`ID`、`TargetControlID`属性和强制性`runat="server"`:

[!code-aspx[Main](animating-in-response-to-user-interaction-vb/samples/sample4.aspx)]

在`<Animations>`节点，有五种方法可以启动动画通过用户交互 (缺少的元素是`<OnLoad>`整个页面完全加载后将执行它):

- `<OnClick>` （在控件上的鼠标单击）
- `<OnHoverOut>` （鼠标离开控件）
- `<OnHoverOver>` (鼠标悬停在一个控件，停止`<OnHoverOut>`动画)
- `<OnMouseOut>` （鼠标离开控件）
- `<OnMouseOver>` (鼠标悬停在一个控件，不停止`<OnMouseOut>`动画)

在此方案中，`<OnClick>`使用。 当用户单击面板上时，它调整大小，并在同一时间淡出。

[!code-aspx[Main](animating-in-response-to-user-interaction-vb/samples/sample5.aspx)]


[![鼠标单击启动动画](animating-in-response-to-user-interaction-vb/_static/image2.png)](animating-in-response-to-user-interaction-vb/_static/image1.png)

鼠标单击启动动画 ([单击以查看实际尺寸的图像](animating-in-response-to-user-interaction-vb/_static/image3.png))

> [!div class="step-by-step"]
> [上一页](picking-one-animation-out-of-a-list-vb.md)
> [下一页](disabling-actions-during-animation-vb.md)
