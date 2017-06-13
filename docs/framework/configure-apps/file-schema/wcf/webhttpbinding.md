---
title: "&lt;webHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84179d77-825d-44b9-895a-ab08e7aa044d
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;webHttpBinding&gt;
定义一个绑定元素，该元素用于为响应 HTTP 请求（而不是 SOAP 消息）的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web 服务配置终结点。  
  
## 语法  
  
```  
  
<webHttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxBufferSize="integer"  
        maxReceivedMessageSize="Integer"  
        name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
                transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        useDefaultWebProxy="Boolean">  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        <security mode="None/Transport/TransportCredentialOnly">  
            <transport clientCredentialType =   
                 "Basic/Certificate/Digest/None/Ntlm/Windows"  
                  proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                  realm="string" />  
        </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"           
            maxStringContentLength="Integer" />  
    </binding>  
</webHttpBinding>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|allowCookies|一个布尔值，指示客户端是否接受 Cookie 并在今后的请求中传播这些 Cookie。  默认值为 false。<br /><br /> 在与使用 Cookie 的 ASMX Web 服务进行交互时，可以使用此属性。  通过这种方式，可以确保从服务器返回的 Cookie 自动复制到客户端今后对该服务的所有请求。|  
|bypassProxyOnLocal|一个布尔值，指示是否对本地地址不使用代理服务器。  默认值为 `false`。|  
|closeTimeout|一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。  此值应大于或等于 <xref:System.TimeSpan.Zero>。  默认值为 00:01:00。|  
|hostnameComparisonMode|指定用于分析 URI 的 HTTP 主机名比较模式。  此属性的类型为 <xref:System.ServiceModel.HostnameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。  默认值为 <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。|  
|maxBufferPoolSize|一个整数，指定此绑定的最大缓冲池大小。  默认值为 524,288 字节 \(512 \* 1024\)。  Windows Communication Foundation \(WCF\) 的许多部件使用缓冲区。  每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。  利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。  这样就避免了创建和销毁缓冲区的系统开销。|  
|maxBufferSize|一个整数，指定为从通道接收消息的消息缓冲区管理器分配并供其使用的最大内存量。  默认值为 524,288 \(0x80000\) 字节。|  
|maxReceivedMessageSize|一个正整数，指定采用此绑定配置的通道上可以接收的最大消息大小（字节），包括消息头。  如果消息超出此限制，则发送方将收到错误。  接收方将删除该消息，并在跟踪日志中创建事件项。  默认值为 65536。 **Note:**  在 ASP.NET 兼容模式下，单独增加此值是不够的。  还应增加 `httpRuntime` 的值（请参见 [httpRuntime 元素（ASP.NET 设置架构）](http://msdn.microsoft.com/zh-cn/e9b81350-8aaf-47cc-9843-5f7d0c59f369)）。|  
|name|一个包含绑定的配置名称的字符串。  因为此值用作绑定的标识，所以它应该是唯一的。  从 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 开始，不要求绑定和行为具有名称。  有关默认配置以及无名称绑定和行为的更多信息，请参见[简化配置](../../../../../docs/framework/wcf/simplified-configuration.md)和 [WCF 服务的简化配置](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|openTimeout|一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。  此值应大于或等于 <xref:System.TimeSpan.Zero>。  默认值为 00:01:00。|  
|proxyAddress|一个指定 HTTP 代理的地址的 URI。  如果 `useSystemWebProxy` 为 `true`，则此设置必须为 `null`。  默认值为 `null`。|  
|receiveTimeout|一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。  此值应大于或等于 <xref:System.TimeSpan.Zero>。  默认值为 00:01:00。|  
|sendTimeout|一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。  此值应大于或等于 <xref:System.TimeSpan.Zero>。  默认值为 00:01:00。|  
|transferMode。|一个 <xref:System.ServiceModel.TransferMode> 值，指示采用此绑定配置的服务是使用消息传输的流处理模式还是缓冲模式（还是使用这两种模式）。  默认值为 `Buffered`。|  
|useDefaultWebProxy|一个布尔值，指定是否使用系统的自动配置 HTTP 代理。  默认值为 `true`。|  
|writeEncoding|指定用于消息文本的字符编码。  包括以下有效值：<br /><br /> UnicodeFffeTextEncoding：Unicode BigEndian 编码。<br /><br /> Utf16TextEncoding：16 位编码。<br /><br /> Utf8TextEncoding：8 位编码。<br /><br /> 默认值为 Utf8TextEncoding。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|定义可由采用此绑定配置的终结点进行处理的 POX 消息的复杂性约束。  此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|定义绑定的安全设置。  此元素的类型为 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement>。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[\<绑定\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|此元素包含标准绑定和自定义绑定的集合。|  
  
## 备注  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Web 编程模型允许开发人员通过 HTTP 请求（这些请求使用“纯旧式 XML”\(POX\) 样式消息，而不是使用基于 SOAP 的消息）来公开 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Web 服务。  为了让客户端使用 HTTP 请求与服务进行通信，必须使用附加了 \<WebHttpBehavior\> 的 [\<wsHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 对服务的终结点进行配置。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 中的联合支持和 ASP.AJAX 集成都建立在 Web 编程模型的基础之上。  有关模型的更多信息，请参见 [WCF Web HTTP 编程模型](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)。  
  
## 请参阅  
 <xref:System.ServiceModel.WebHttpBinding>   
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>   
 [WCF Web HTTP 编程模型](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)   
 [绑定](../../../../../docs/framework/wcf/bindings.md)   
 [配置系统提供的绑定](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-cn/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<绑定\>](../../../../../docs/framework/misc/binding.md)