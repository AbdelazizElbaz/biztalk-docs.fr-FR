---
title: "Le schéma d’itinéraire ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 168e7b98-6282-494e-bde8-3171e0be7d59
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66bcbe6780105a97e58df393d0e060688048a02b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-itinerary-schema"></a><span data-ttu-id="086b2-102">Le schéma d’itinéraire ESB</span><span class="sxs-lookup"><span data-stu-id="086b2-102">The ESB Itinerary Schema</span></span>
<span data-ttu-id="086b2-103">Le schéma d’ESB itinéraire nommé Itinerary.xsd définit un itinéraire en tant qu’ensemble de l’instruction de traitement, généralement appelée services d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="086b2-103">The ESB Itinerary schema named Itinerary.xsd defines an itinerary as a set of processing instructions, generally referred to as itinerary services.</span></span> <span data-ttu-id="086b2-104">Un service d’itinéraire peut contenir un ou plusieurs services d’itinéraire et les chaînes de connexion de programme de résolution correspondant, comme indiqué dans la définition de schéma suivante.</span><span class="sxs-lookup"><span data-stu-id="086b2-104">An itinerary service may contain one or more itinerary services and the corresponding resolver connection strings, as shown in the following schema definition.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary" targetNamespace="http://schemas.microsoft.biztalk.practices.esb.com/itinerary" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <xs:annotation>  
    <xs:appinfo>  
      <b:schemaInfo root_reference="Itinerary" xmlns:b="http://schemas.microsoft.con/BizTalk/2003" />  
    </xs:appinfo>  
  </xs:annotation>  
  <xs:element name="Itinerary">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="BizTalkSegment">  
          <xs:complexType>  
            <xs:attribute name="interchangeId" type="xs:string" />  
            <xs:attribute name="epmRRCorrelationToken" type="xs:string" />  
            <xs:attribute name="receiveInstanceId" type="xs:string" />  
            <xs:attribute name="messageId" type="xs:string" />  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="ServiceInstance">  
          <xs:complexType>  
            <xs:attribute name="uuid" type="xs:string" />  
            <xs:attribute name="name" type="xs:string" />  
            <xs:attribute name="type" type="xs:string" />  
            <xs:attribute name="state" type="xs:string" />  
            <xs:attribute name="position" type="xs:int" />  
            <xs:attribute name="isRequestResponse" type="xs:boolean" />  
            <xs:attribute name="stage" type="Stages" />  
          </xs:complexType>  
        </xs:element>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="Services">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Services">  
                <xs:complexType>  
                  <xs:sequence>  
                    <xs:element minOccurs="0" maxOccurs="1" name="PropertyBag" nillable="true">  
                      <xs:complexType>  
                        <xs:sequence minOccurs="0" maxOccurs="1">  
                          <xs:element minOccurs="0" maxOccurs="unbounded" name="Property">  
                            <xs:complexType>  
                              <xs:attribute name="name" type="xs:string" use="required" />  
                              <xs:attribute name="value" type="xs:string" use="required" />  
                            </xs:complexType>  
                          </xs:element>  
                        </xs:sequence>  
                      </xs:complexType>  
                    </xs:element>  
                  </xs:sequence>  
                  <xs:attribute name="uuid" type="xs:string" />  
                  <xs:attribute name="beginTime" type="xs:string" />  
                  <xs:attribute name="completeTime" type="xs:string" />  
                  <xs:attribute name="name" type="xs:string" />  
                  <xs:attribute name="type" type="xs:string" />  
                  <xs:attribute name="state" type="xs:string" />  
                  <xs:attribute name="resolve" type="xs:boolean" />  
                  <xs:attribute name="isRequestResponse" type="xs:boolean" />  
                  <xs:attribute name="position" type="xs:int" />  
                  <xs:attribute name="serviceInstanceId" type="xs:string" />  
                  <xs:attribute name="isTrackingEnabled">  
                    <xs:simpleType>  
                      <xs:restriction base="xs:boolean" />  
                    </xs:simpleType>  
                  </xs:attribute>  
                  <xs:attribute name="stage" type="Stages" />  
                </xs:complexType>  
              </xs:element>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="ResolverGroups">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element maxOccurs="unbounded" name="Resolvers">  
                <xs:complexType>  
                  <xs:simpleContent>  
                    <xs:extension base="xs:string">  
                      <xs:attribute name="serviceId" type="xs:string" />  
                    </xs:extension>  
                  </xs:simpleContent>  
                </xs:complexType>  
              </xs:element>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
      <xs:attribute name="uuid" type="xs:string" />  
      <xs:attribute name="beginTime" type="xs:string" />  
      <xs:attribute name="completeTime" type="xs:string" />  
      <xs:attribute name="state" type="xs:string" />  
      <xs:attribute name="isRequestResponse" type="xs:boolean" />  
      <xs:attribute name="servicecount" type="xs:int" use="required" />  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="Stages">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="notSpecified" />  
      <xs:enumeration value="receiveInbound" />  
      <xs:enumeration value="receiveTransmit" />  
      <xs:enumeration value="sendTransmit" />  
      <xs:enumeration value="sendInbound" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
 <span data-ttu-id="086b2-105">Le **ServiceInstance** élément correspond au service en cours d’itinéraire et contient des propriétés telles que **nom**, **type**, **état**, et **position** que le service promeut dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="086b2-105">The **ServiceInstance** element corresponds to the current itinerary service and contains properties such as **name**, **type**, **state**, and **position** that the service promotes into the message context.</span></span> <span data-ttu-id="086b2-106">Le schéma nommé système-.xsd dans le **Microsoft.Practices.ESB.ItinerarySchemas** assembly définit ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="086b2-106">The schema named System-Properties.xsd in the **Microsoft.Practices.ESB.ItinerarySchemas** assembly defines these properties.</span></span>  
  
 <span data-ttu-id="086b2-107">Le **Services** élément représente un ensemble de services d’itinéraire, avec chaque service défini par l’état, faites commencer le temps, la durée d’exécution, type (**Orchestration** ou **messagerie**) et, éventuellement, étape (**receiveInbound**, **receiveTransmit**, **sendTransmit**, **sendInbound**).</span><span class="sxs-lookup"><span data-stu-id="086b2-107">The **Services** element represents a set of itinerary services, with each service defined by its state, begin time, completion time, type (**Orchestration** or **Messaging**), and, optionally, stage (**receiveInbound**, **receiveTransmit**, **sendTransmit**, **sendInbound**).</span></span>  
  
 <span data-ttu-id="086b2-108">Le **ResolverGroups** élément contient plusieurs **résolveurs** éléments, chacun d’eux définit une ou plusieurs chaînes de connexion de programme de résolution qui fait référence à un itinéraire via le **serviceid**  attribut.</span><span class="sxs-lookup"><span data-stu-id="086b2-108">The **ResolverGroups** element contains multiple **Resolvers** elements, each of which defines one or more resolver connection strings that an itinerary references through the **serviceid** attribute.</span></span>  
  
 <span data-ttu-id="086b2-109">Voici un exemple d’un en-tête SOAP de feuille de route soumis avant son traitement par le composant de Pipeline d’itinéraire ESB.</span><span class="sxs-lookup"><span data-stu-id="086b2-109">The following shows a sample of a submitted itinerary SOAP header before it is processed by the ESB Itinerary Pipeline component.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Itinerary xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" uuid="" beginTime="" completeTime="" state="Pending" isRequestResponse="false" xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary">  
  
  <ServiceInstance uuid="" name="Microsoft.Practices.ESB.Services.Transform" type="Messaging" state="Pending" position="0" isRequestResponse="false" xmlns="" />  
  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="Microsoft.Practices.ESB.Services.Transform" type="Messaging" state="Pending" isRequestResponse="false" position="0" serviceInstanceId="" />  
  </Services>  
  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="DynamicResolutionSolicitResp" type="Messaging" state="Pending" isRequestResponse="true" position="1" serviceInstanceId="" />  
  </Services>  
  
  <ResolverGroups xmlns="">  
    <Resolvers serviceId="DynamicResolutionSolicitResp1"><![CDATA[BRE:\\policy=GetCanadaEndPoint;version=;useMsg=;]]></Resolvers>  
  
    <Resolvers serviceId="Microsoft.Practices.ESB.Services.Transform0"><![CDATA[BRE:\\policy=CanadaSubmitOrderMaps;version=;useMsg=;]]></Resolvers>  
  </ResolverGroups>  
  
</Itinerary>  
```