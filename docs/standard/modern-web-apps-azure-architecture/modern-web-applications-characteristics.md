---
title: 现代 Web 应用程序的特征
description: 使用 ASP.NET Core 和 Azure 构建新式 Web 应用程序 | 新式 Web 应用程序的特征
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: cc4493bf8e45c41a94e8e6f719318b14ad5b05f1
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105802"
---
# <a name="characteristics-of-modern-web-applications"></a>新式 Web 应用程序的特征

> "… 恰当合理的设计，会使功能的价格变便宜。 这种方式有难度，但是却总有成效。”  
> \- Dennis Ritchie

## <a name="summary"></a>总结

新式 Web 应用程序比以往承载着更高的用户期望和要求。 当今的 Web 应用需要能在全球任何地方任意时刻可用，需要可在任何设备或屏幕尺寸上使用。 Web 应用程序必须具有安全性、灵活性和可缩放性，以便满足高峰需求。 如今复杂方案日益需要由丰富的用户体验来处理，这建立在使用 JavaScript 并通过 Web API 进行有效通信的客户端的基础之上。

ASP.NET Core 针对新式 Web 应用程序和基于云的托管方案进行了优化。 其模块化设计使应用程序仅依赖于其实际使用的功能，从而提升应用程序安全性和性能，降低托管资源要求。

## <a name="reference-application-eshoponweb"></a>参考应用程序：eShopOnWeb

本指南包含一个参考应用程序 eShopOnWeb，该应用程序演示了一些原则和建议。 该应用程序是一个简单在线商店，支持浏览衬衫、咖啡杯和其他市场产品名录。 特意选择该简单的参考应用，方便理解。

**图 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>参考应用程序
> - **eShopOnWeb**  
> <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>云托管和可缩放

由于低内存、高吞吐量的特点，ASP.NET Core 针对云（公共云、私有云以及任何云）进行了优化。 ASP.NET Core 应用程序占用空间更小，因此在相同硬件上可托管更多此类应用。并且，使用即用即付云托管服务时仅需为极少数资源付费。 更高的高吞吐量意味着，通过相同硬件上的一个应用，你可服务更多客户，进而降低服务器和托管基础设施所需的投入。

## <a name="cross-platform"></a>跨平台

ASP.NET Core 具有跨平台性，可在 Linux、MacOS 以及 Windows 上运行。 这为开发和部署通过 ASP.NET Core 构建的应用程序带来了新的选择。 Docker 容器如今通常运行 Linux，可托管 ASP.NET Core 应用程序，从而使应用程序可利用[容器和微服务](../microservices-architecture/index.md)的优势。

## <a name="modular-and-loosely-coupled"></a>模块化和松散耦合

NuGet 包在 .NET Core 中处于第一等级，而 ASP.NET Core 应用经 NuGet 由众多库构成。 此功能的粒度有助于确保应用仅依赖和部署其实际所需的功能，从而降低占用空间和安全漏洞外围应用。

ASP.NET Core 还完全支持内部和应用程序级别的依赖项注入。 接口可具有多个能按需换出的实现。 依赖项注入可使应用松散耦合到此类接口，从而使其扩展、维护和测试更加容易。

## <a name="easily-tested-with-automated-tests"></a>通过自动测试轻松实现测试

ASP.NET Core 应用程序支持单元测试，并且通过其松散耦合和依赖项注入支持，可轻松出于测试目的轻松将基础设施顾虑转换为虚假实现。 ASP.NET Core 还附带可用于托管内存中应用的 TestServer。 功能测试然后可向此内存中服务器发出请求，从而能在真实服务器上托管应用和通过网络层作出请求所需时间的短暂时间内，执行完整的应用程序堆栈（包括中间件、路由、模型绑定、筛选器等）和接收响应。 对于在新式 Web 应用程序中愈发重要的 API 而言，这些测试非常易于编写，具有很大作用。

## <a name="traditional-and-spa-behaviors-supported"></a>支持传统和 SPA 行为

传统 Web 应用程序涉及极少的客户端行为，而是依赖服务器执行该应用可能需要执行的所有导航、查询和更新。 用户执行的每个新操作会被转换为新的 Web 请求，其结果是最终用户浏览器中的完整页面重载。 经典模型视图控制器 (MVC) 框架通常采用此方式，其中每个新请求对应一个不同的控制器操作，这些操作会反过来作用于模型并返回一个视图。 特定页面上的一些单独操作可使用 AJAX（异步 JavaScript 和 XML）功能改进，但该应用的总体体系结构使用了多个不同的 MVC 视图和 URL 终结点。

与之相反，单页应用程序 (SPAs) 涉及极少动态生成的服务器端页面负载（如有）。 许多 SPA 在一个静态 HTML 文件中进行初始化，此文件加载该应用启动和运行所需的 JavaScript 库。 这些应用大量使用 Web API 处理数据需求，并提供更为丰富的用户体验。

许多 Web 应用程序同时涉及传统 Web 应用程序行为（尤其是对于内容）和 SPA（对于交互）。 ASP.NET Core 通过使用相同工具集和基础框架库，在同一应用程序中同时支持 MVC 和 Web API。

## <a name="simple-development-and-deployment"></a>简单的开发和部署

可使用简单的文本编辑器、命令行接口或者全功能开发环境（例如 Visual Studio）编写 ASP.NET Core 应用程序。 整体应用程序通常部署到单个终结点。 可轻松将部署自动化，作为持续集成 (CI) 和持续交付 (CD) 管道的一部分。 除传统的 CI/CD 工具外，Microsoft Azure 还集成了 git 存储库支持，并可在对特定 git 分支或标记作出更新时自动部署更新。

## <a name="traditional-aspnet-and-web-forms"></a>传统的 ASP.NET 和 Web 窗体

除 ASP.NET Core 外，传统的 ASP.NET 4.x 依然是一个用于构建 Web 应用程序的可靠强大的平台。 ASP.NET 支持 MVC 和 Web API 开发模型以及 Web 窗体。Web 窗体非常适合用于基于页面的丰富应用程序开发，具有丰富的第三方组件系统。 Microsoft Azure 长期以来支持 ASP.NET 4.x 应用程序，而且许多开发人员非常熟悉该平台。

> ### <a name="references--modern-web-applications"></a>参考 - 新式 Web 应用程序
> - **ASP.NET Core 简介**  
> <https://docs.microsoft.com/aspnet/core/>
> - **ASP.NET Core 六大关键优势使其更加独特和优秀**  
> <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **在 ASP.NET Core 进行测试**  
> <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[上一页](index.md)
[下一页](choose-between-traditional-web-and-single-page-apps.md)
