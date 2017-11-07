---
title: "Type de données, mappage de gestionnaires d’envoi dans TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1a9233-8781-45a8-9c55-a18ecaa0f456
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bda336d149d373477b26efeb2e4b05de4aac7554
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="data-type-mapping-for-send-handlers-in-tibco-rendezvous"></a>Mappage de types de données pour les gestionnaires d'envoi dans TIBCO Rendezvous
Le mappage des types de schémas XML aux types TIBCO Rendezvous est possible seulement si TIBCO Rendezvous fournit les informations relatives aux types (xsi:type=). Les types non pris en charge sont mappés à des chaînes dans la mesure du possible. Si le mappage est impossible ou si l'option est désactivée dans la configuration du port, une erreur est générée.  
  
## <a name="xml-schema-to-tibco-rendezvous-data-type-mapping"></a>Mappage des types de schémas XML aux types de données TIBCO Rendezvous  
 Le tableau suivant présente le mappage possible entre les types de schémas XML et les types TIBCO Rendezvous.  
  
|Type XML|Type TIBCO RV|  
|--------------|-------------------|  
||TIBRVMSG_MSG|  
||TIBRVMSG_XML|  
|xsd:dateTime|TIBRVMSG_DATETIME|  
|xsd:boolean|TIBRVMSG_BOOL|  
|xsd:byte|TIBRVMSG_I8|  
|xsd:short|TIBRVMSG_I16|  
|xsd:int|TIBRVMSG_I32|  
|xsd:long|TIBRVMSG_I64|  
|xsd:unsignedByte|TIBRVMSG_U8|  
|xsd:unsignedShort|TIBRVMSG_U16|  
|xsd:unsignedInt|TIBRVMSG_U32|  
|xsd:unsignedLong|TIBRVMSG_U64|  
|xsd:float|TIBRVMSG_F32|  
|xsd:double|TIBRVMSG_F64|  
|tibrv:IPaddress|TIBRVMSG_IPADDR32|  
|tibrv:IPport|TIBRVMSG_IPPORT16|  
|tibrv:arrayOfByte|TIBRVMSG_I8ARRAY|  
|tibrv:arrayOfShort|TIBRVMSG_I16ARRAY|  
|tibrv:arrayOfInt|TIBRVMSG_I32ARRAY|  
|tibrv:arrayOfLong|TIBRVMSG_I64ARRAY|  
|tibrv:arrayOfUnsignedByte|TIBRVMSG_U8ARRAY|  
|tibrv:arrayOfUnsignedShort|TIBRVMSG_U16ARRAY|  
|tibrv:arrayOfUnsignedInt|TIBRVMSG_U32ARRAY|  
|tibrv:arrayOfUnsignedLong|TIBRVMSG_U64ARRAY|  
|tibrv:arrayOfFloat|TIBRVMSG_F32ARRAY|  
|tibrv:arrayOfDouble|TIBRVMSG_F64ARRAY|  
|Autre type, avec un message de débogage|TIBRVMSG_STRING le journal.|  
  
 Comme l'adaptateur BizTalk pour TIBCO Rendezvous n'a pas accès à un schéma, lorsque vous effectuez des transferts entre BizTalk Server et TIBCO Rendezvous, vous devez fournir l'attribut `xsi:type` XML pour les champs de type non chaîne. L'adaptateur utilise ces informations pour générer le type de champ de message approprié dans le message TIBCO Rendezvous.  
  
## <a name="message-mapping-example"></a>Exemple de mappage d'un message  
 L'exemple suivant illustre le mappage d'un message entre BizTalk Server et TIBCO Rendezvous Pour plus d'informations sur le mappage des types, consultez le tableau de mappage des types de données.  
  
```  
<ns:QuoteUpdate xmlns:xsi http://www.w3.org/2001/XMLSchema-instance"  
xmlns:xsd http://www.w3.org/2001/XMLSchema"  
xmlns:tibrv="http://schemas.microsoft.com/TibcoRendezvous/Types"  
xmlns:ns="some namespace for this message [value not important, unless the schema is also used for receive ports]">  
  
<ns:SymbolName id=1 xsi:type="xsd:string">MSFT</ns:SymbolName>  
  
<ns:LastTrade id=2 xsi:type="xsd:double">28.40</ns:LastTrade>   
<ns:DayLow id=3 xsi:type="xsd:double">28.25</ns:DayLow>  
  
```  
  
|||  
|-|-|  
|`<ns:DayHigh`|`id=4 xsi:type="xsd:double">28.40</ns:DayHigh>`|  
|`<ns:MarketCap`|`id=10>262575234981</ns:MarketCap>`|  
|`<ns:Bids`|`id=100 xsi:type="tibrv:message">`|  
  
```  
<ns:TopBids id=1 xsi:type="tibrv:arrayOfDouble">  
<item>28.40</item>  
<item>28.39</item>  
<item>28.39</item>  
<item>28.39</item>  
<item>28.38</item>  
  
</ns:TopBids>  
  
<ns:BidsSize id=2 xsi:type="tibrv:arrayOfLong">  
<item>500</item>  
<item>1000</item>  
<item>100</item>  
<item>100</item>  
<item>2000</item>  
  
</ns:BidsSize>  
</ns:Bids>  
</ns:QuoteUpdate>  
  
```  
  
 Une fois le message précédent généré sous la forme d'un message TIBCO Rendezvous structuré, il devient une instance TibcoMsg de niveau supérieur avec six champs. Les derniers champs sont un sous-message, constitué de deux champs de types de tableaux (les éléments « item » ne sont pas mappés aux champs Message TIBCO Rendezvous mais aux éléments d'un champ Message de type `array`). Le champ MarketCap, dont le type n'est pas spécifié, est envoyé en tant que champ de message de type chaîne.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires d’envoi TIBCO Rendezvous](../core/creating-tibco-rendezvous-send-handlers.md)