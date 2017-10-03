---
title: "À l’aide de TIBCO Rendezvous les Ports de réception de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive ports, using from BizTalk Server
ms.assetid: 26cb20f9-4d26-48f6-a5e9-a51348a56538
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b8e0999362844570bb56cfbc488e5fd5775e286
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-tibco-rendezvous-receive-ports-from-biztalk-server"></a>Utilisation des ports de réception TIBCO Rendezvous à partir de BizTalk Server
Pour utiliser un port de réception, vous pouvez fournir un schéma à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour les messages entrants. Un port de réception est configuré pour écouter un ensemble de noms d'objet particulier. Il fait appel à un nom d'objet possédant des caractères génériques facultatifs de façon à correspondre à plusieurs noms d'objet. Dans l'orchestration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez définir des opérations de port distinctes pour chaque objet possible qui correspond à une chaîne donnée.  
  
> [!NOTE]
>  L'adaptateur prend en charge les scénarios d'orchestration et de messagerie.  
  
## <a name="defining-schemas"></a>Définition de schémas  
 Par exemple, si le port est configuré pour écouter le nom du sujet, **STOCK. MARCHÉ. INDICES. >** («**>**' est un caractère générique signifiant que rien d’autre à droite), il serait valide de définir des opérations pour les noms d’objet comme **STOCK. MARCHÉ. INDEX. WALL STREET. SP500**, **STOCK. MARCHÉ. INDEX. TSX.TSX60**, et ainsi de suite. L’adaptateur génère des messages à l’aide de la stratégie décrite dans [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)et génère le nom de l’élément racine et les espaces de noms en fonction de l’écoute de l’objet nom et message reçu noms de sujet respectivement.  
  
 Dans l'exemple précédent, l'adaptateur a généré un message pour l'événement SP500 qui ressemble à ce qui suit :  
  
```  
<ns:STOCK.MARKET.INDICES.NYSE.SP500 xmlns:ns='   
http://schemas.microsoft.com/TibcoRendezvous/Types/  
STOCK.MARKET.INDICES.NYSE.GTWILDCARD'  
xmlns:tibrv=' http://schemas.microsoft.com/TibcoRendezvous/Types' … >  
<message body>  
</ns: STOCK.MARKET.INDICES.NYSE.SP500>  
  
```  
  
 Vous devez définir un schéma qui fait appel aux mêmes conventions. Exemple :  
  
```  
<xsd:schema  
targetNamespace='   
  
http://schemas.microsoft.com/TibcoRendezvous/Types/STOCK.MARKET.INDICES.N  
YSE.GTWILDCARD'  
xmlns:xsd=' http://www.w3.org/2001/XMLSchema'  
xmlns:tibrv=' http://schemas.microsoft.com/TibcoRendezvous/Types'>  
xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
<xsd:element name='STOCK.MARKET.INDICES.NYSE.SP500'>  
  
 <xs:annotation>  
   <xs:appinfo>  
     <b:recordInfo rootTypeName="STOCK_MARKET_INDICES_NYSE_SP500" />  
   </xs:appinfo>  
  
 </xs:annotation>  
<xsd:complexType>  
<SP500 message definitions goes here>  
</xsd:complexType>  
<xsd:element name='STOCK.MARKET.INDICES.TSX.TSX60'>  
  
 <xs:annotation>  
   <xs:appinfo>  
     <b:recordInfo rootTypeName="STOCK_MARKET_INDICES_TSX_TSX60" />  
   </xs:appinfo>  
  
 </xs:annotation>  
<xsd:complexType>  
<TSX60 message definitions goes here>  
</xsd:complexType>  
  
```  
  
 Notez l’utilisation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **recordInfo/rootTypeName** annotation. Elle permet d'indiquer à l'intégration [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk qu'il est nécessaire d'utiliser ce nom pour les types .NET Framework générés au lieu du nom contenant des points. Vous pouvez spécifier n'importe quelle valeur. Dans les exemples, les points sont remplacés par des traits de soulignement.  
  
> [!NOTE]
>  Les points entraînent la création de noms qui ne sont pas valides à l'aide des outils de développement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)   
 [Gestionnaires de réception création TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)