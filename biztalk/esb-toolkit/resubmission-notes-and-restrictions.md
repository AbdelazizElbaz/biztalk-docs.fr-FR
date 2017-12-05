---
title: Les Restrictions et les Notes de la nouvelle soumission | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 391064a9-1d61-4b10-97ab-d93b37d1ae23
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d03c969dc056e251d8109ce5bc0a29c16f8ffeda
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="resubmission-notes-and-restrictions"></a>Nouvelle soumission Remarques et Restrictions
Les notes et les restrictions suivantes s’appliquent au processus renvoyés :  
  
-   Vous pouvez renvoyer des messages XML à l’ESB WCF rampe d’entrée, SOAP (ASMX) rampe d’entrée, ou emplacement de réception n’importe quel HTTP.  
  
-   L’URL par défaut de WCF rampe est http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc.  
  
-   Le fichier Web.config du portail définit les détails de point de terminaison pour le WCF rampe d’entrée dans le  **\<Client\>**  nœud de la  **\<System.ServiceModel\>**  section. Voici la valeur par défaut.  
  
    ```  
    <endpoint  
      address="http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc"  
      binding="wsHttpBinding"  
      bindingConfiguration="WSHttpBinding_ITwoWayAsyncVoid"  
      contract="ProcessRequest"   
      name="WSHttpBinding_ITwoWayAsyncVoid">                  
    </endpoint>  
    ```  
  
-   Si WCF rampe réside sur un serveur distant, vous devez mettre à jour l’adresse pour pointer vers le serveur approprié.  
  
-   L’URL par défaut pour le SOAP (ASMX) rampe d’entrée est http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx.  
  
-   Le fichier Web.config du portail définit la configuration pour le SOAP (ASMX) rampe d’entrée dans le  **\<applicationSettings\>**  section. Voici la valeur par défaut.  
  
    ```  
    <setting   
      name="Microsoft_Practices_ESB_Portal_ProcessItinerary_Process"  
      serializeAs="String">  
      <value>  
        http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx  
      </value>  
    </setting>  
    ```  
  
-   Si ASMX rampe réside sur un serveur distant, vous devez mettre à jour l’URL avec l’adresse de serveur correct.  
  
-   Vous pouvez soumettre à nouveau fichier plat emplacement de réception des messages mis en forme uniquement à HTTP. Vous ne pouvez pas les envoyer à un WCF ou SOAP rampe d’entrée. Vous devez vous assurer que le protocole HTTP emplacement de réception a le pipeline approprié qui peut consommer et/ou analyser le fichier plat.  
  
-   Le message soumise à nouveau ne contient pas toutes les propriétés de contexte du message d’origine.  
  
-   Nouvelle soumission s’applique à uniquement le corps du message ; Il ne s’applique pas à la totalité du message.  
  
-   Le processus de nouvelle soumission prend en charge uniquement les messages en une seule partie. Vous ne pouvez pas utiliser le processus de nouvelle soumission avec des messages à parties multiples.  
  
-   Vous ne peut pas renvoyer des messages au format binaire.