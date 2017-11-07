---
title: "Mappage de Type de données à recevoir de TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36908a94-3c0d-466e-aa49-f674ba4a26af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcb17ceac0c323bba7a6f25cff0d07473b6d7fa3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="data-type-mapping-for-receive-handlers-in-tibco-rendezvous"></a>Mappage de types de données pour les gestionnaires de réception dans TIBCO Rendezvous
L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous mappe les types TIBCO RV aux types de schéma XML, comme indiqué dans le tableau suivant.  
  
## <a name="tibco-rv-to-xml-data-type-mapping"></a>Mappage des types TIBCO RV aux types de données XML  
  
|Type TIBCO RV|Type de schéma XML|Commentaires|  
|-------------------|---------------------|--------------|  
|TIBRVMSG_MSG|tibrv:message|Document XML complet construit à partir du message entier.|  
|TIBRVMSG_XML|tibrv:rawxml|Document XML construit à partir du tableau d'octets (non interprété par l'adaptateur).|  
|TIBRVMSG_DATETIME|xsd:dateTime|L'adaptateur utilise la classe System.Xml.XmlConvert pour effectuer la conversion entre les instances `dateTime` et `System.DateTime` du schéma XML.|  
|TIBRVMSG_OPAQUE|xsd:base64Binary||  
|TIBRVMSG_STRING|xsd:string||  
|TIBRVMSG_BOOL|xsd:boolean||  
|TIBRVMSG_I8|xsd:byte||  
|TIBRVMSG_I16|xsd:short||  
|TIBRVMSG_I32|xsd:int||  
|TIBRVMSG_I64|xsd:long||  
|TIBRVMSG_U8|xsd:unsignedByte||  
|TIBRVMSG_U16|xsd:unsignedShort||  
|TIBRVMSG_U32|xsd:unsignedInt||  
|TIBRVMSG_U64|xsd:unsignedLong||  
|TIBRVMSG_F32|xsd:float||  
|TIBRVMSG_F64|xsd:double||  
|TIBRVMSG_IPADDR32|tibrv:IPaddress|`System.Net.IPAddress.ToString( )` est utilisé pour générer la sortie. Le contenu apparaît dans l'ordre de tri du réseau grâce à ToString().|  
|TIBRVMSG_IPPORT16|tibrv:IPport|Le contenu est dans l’ordre d’octet du réseau|  
|TIBRVMSG_I8ARRAY|tibrv:arrayOfByte|L'espace de noms de schéma « tibrv » est fourni avec l'adaptateur.|  
|TIBRVMSG_I16ARRAY|tibrv:arrayOfShort||  
|TIBRVMSG_I32ARRAY|tibrv:arrayOfInt||  
|TIBRVMSG_I64ARRAY|tibrv:arrayOfLong||  
|TIBRVMSG_U8ARRAY|tibrv:arrayOfUnsignedByte||  
|TIBRVMSG_U16ARRAY|tibrv:arrayOfUnsignedShort||  
|TIBRVMSG_U32ARRAY|tibrv:arrayOfUnsignedInt||  
|TIBRVMSG_U64ARRAY|tibrv:arrayOfUnsignedLong||  
|TIBRVMSG_F32ARRAY|tibrv:arrayOfFloat||  
|TIBRVMSG_F64ARRAY|tibrv:arrayOfDouble||  
  
 Les tableaux TIBCO Rendezvous diffèrent d'une séquence de champs dotés d'un même nom. Par exemple, un message TIBCO Rendezvous peut inclure un tableau de 70 000 éléments, mais pas 70 000 champs.  
  
 Le schéma des types de tableaux dans le tableau précédent ressemble à ce qui suit :  
  
```  
…  
<xsd:complexType name='arrayOfShort'>  
<xsd:sequence>  
<xsd:element name="item" type="xsd:short"/>  
</xsd:sequence>  
</xsd:complexType>  
  
```  
  
 Un élément de tableau dans un message ressemble à ce qui suit :  
  
```  
<someElement xsi:type='tibrv:arrayOfShort'>  
<item>100</item>  
<item>200</item>  
<item>300</item>  
<item>400</item>  
<item>500</item>  
</someElement>  
  
```  
  
 Le schéma de l'adresse IP ressemble à ce qui suit :  
  
```  
<xsd:simpleType name='IPaddress'>  
  
 <xsd:restriction base="xs:string">  
   <xsd:minLength value="7" />  
   <xsd:maxLength value="15" />  
  
 </xsd:restriction>  
       </xsd:simpleType>   
</xsd:simpleType>  
  
```  
  
 Le schéma du port IP ressemble à ce qui suit :  
  
```  
<xsd:simpleType name='IPport'>  
  
<xsd:restriction base='xsd:ushort'>  
</xsd:simpleType>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des messages dans TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md)   
 [Création de gestionnaires de réception TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)