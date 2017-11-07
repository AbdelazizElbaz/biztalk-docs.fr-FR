---
title: "Recevoir des schémas et traiter les événements avec l’adaptateur TIBCO Rendezvous | Documents Microsoft"
description: "Utiliser les schémas de TIBCO Rendezvous sur le côté réception et le traitement des événements à l’aide de l’adaptateur BizTalk pour TIBCO Rendezvous dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26cb20f9-4d26-48f6-a5e9-a51348a56538
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbbae69dc1b7df1f5675442dde544a444cec02fb
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="using-tibco-rendezvous-receive-ports-from-biztalk-server"></a>Utilisation des ports de réception TIBCO Rendezvous à partir de BizTalk Server

## <a name="overview"></a>Vue d'ensemble
Pour utiliser un port de réception, vous pouvez fournir un schéma à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour les messages entrants. Un port de réception est configuré pour écouter un ensemble de noms d'objet particulier. Il fait appel à un nom d'objet possédant des caractères génériques facultatifs de façon à correspondre à plusieurs noms d'objet. Dans l'orchestration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez définir des opérations de port distinctes pour chaque objet possible qui correspond à une chaîne donnée.  
  
> [!NOTE]
>  L’adaptateur prend en charge à la fois d’orchestration et de scénarios de messagerie.  
  
## <a name="define-schemas"></a>Définir des schémas  
 Par exemple, si le port est configuré pour écouter le nom du sujet, **STOCK. MARCHÉ. INDICES. >** («**>**' est un caractère générique signifiant que rien d’autre à droite), il serait valide de définir des opérations pour les noms d’objet comme **STOCK. MARCHÉ. INDEX. WALL STREET. SP500**, **STOCK. MARCHÉ. INDEX. TSX.TSX60**, et ainsi de suite. L’adaptateur génère des messages à l’aide de la stratégie décrite dans [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)et génère le nom de l’élément racine et les espaces de noms en fonction de l’écoute de l’objet nom et message reçu noms de sujet respectivement.  
  
 Dans l’exemple précédent, l’adaptateur génère un message qui ressemble à celui-ci pour l’événement SP500 :  
  
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

## <a name="event-processing"></a>Traitement des événements
L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous distribue des événements à partir d'une file d'attente sur plusieurs threads. Emplacement de réception BizTalk Server est associé à une file d’attente des événements TIBCO Rendezvous et son pool de threads du répartiteur.  
  
### <a name="memory-use-and-errors"></a>Utilisation de la mémoire et erreurs  
 L'adaptateur surveille les ressources utilisées lors du traitement d'événements. Si l'utilisation de la mémoire dépasse la limite supérieure, l'adaptateur arrête la distribution des événements jusqu'à ce que la consommation de mémoire atteigne la limite inférieure. Notez que des messages TIBCO Rendezvous non certifiés peuvent ainsi être manqués (un utilisateur de TIBCO RV dispose de 60 secondes pour supprimer des messages dans une file d'attente). Cette perte de données est signalée en tant qu'erreur. Si l'adaptateur reçoit un message d'avertissement NO_MEMORY en provenance du système TIBCO Rendezvous, cela signifie que des messages ont déjà été perdus.  
  
 L'adaptateur BizTalk pour TIBCO Rendezvous conserve un état et exécute des tâches de différentes façons en fonction de cet état. Si le moteur de messagerie BizTalk renvoie une erreur et si l'adaptateur est configuré en tant qu'écouteur certifié, le moteur la signale à TIBCO Rendezvous afin qu'il puisse renvoyer le message.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md)   
 [Mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)   
 [Création de gestionnaires de réception TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)