---
title: "Schéma Windows Communication Foundation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e95e0e8d-82cf-4608-b54f-188cb8cdaaee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5094e2d7544a88ebfd759fcb3c39fedd1dd411d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-communication-foundation-schema"></a><span data-ttu-id="c0f93-102">Schéma Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c0f93-102">Windows Communication Foundation Schema</span></span>
<span data-ttu-id="c0f93-103">Cette section contient le schéma de l'intercepteur Windows Communication Framework.</span><span class="sxs-lookup"><span data-stu-id="c0f93-103">This section contains the schema for the Windows Communication Framework interceptor.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema targetNamespace="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/WcfInterceptorConfiguration"   
           xmlns="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/WcfInterceptorConfiguration"   
           xmlns:xs="http://www.w3.org/2001/XMLSchema"  
           elementFormDefault="qualified" >  
  
  <xs:element name="Operation">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Argument" type="xs:string" minOccurs="0" maxOccurs="unbounded" />  
      </xs:sequence>  
      <xs:attribute name="Name" type="WcfOperationType" use="required" />  
    </xs:complexType>  
  </xs:element>  
  
  <xs:simpleType name="WcfOperationType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="GetContextProperty" />  
      <xs:enumeration value="GetEndpointName" />  
      <xs:enumeration value="GetOperationName" />  
      <xs:enumeration value="GetServiceContractCallPoint" />  
      <xs:enumeration value="XPath" />  
      <xs:enumeration value="AutoGenerateCorrelationToken" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:element name="NamespaceMappings">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Namespace" type="WcfNamespaceMapping" minOccurs="1" maxOccurs="unbounded" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  
  <xs:complexType name="WcfNamespaceMapping">  
    <xs:sequence>  
    </xs:sequence>  
    <xs:attribute name="Prefix" type="xs:string" use="required" />  
    <xs:attribute name="Uri" type="xs:string" use="required" />  
  </xs:complexType>  
  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0f93-104">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0f93-104">See Also</span></span>  
 <span data-ttu-id="c0f93-105">[Schéma Windows Workflow Foundation](../core/windows-workflow-foundation-schema.md) </span><span class="sxs-lookup"><span data-stu-id="c0f93-105">[Windows Workflow Foundation Schema](../core/windows-workflow-foundation-schema.md) </span></span>  
 [<span data-ttu-id="c0f93-106">Schéma de Configuration de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="c0f93-106">Interceptor Configuration Schema</span></span>](../core/interceptor-configuration-schema.md)