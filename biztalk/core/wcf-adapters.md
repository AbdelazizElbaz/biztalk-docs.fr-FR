---
title: Adaptateurs WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e64cd189-8805-4209-bd06-971363f38585
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb77124dbad631cd521a285ff4f036e0545ca819
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapters"></a>Adaptateurs WCF

## <a name="overview"></a>Vue d'ensemble
Les adaptateurs BizTalk pour Windows Communication Foundation (WCF) permettent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de communiquer avec les applications WCF. Les adaptateurs WCF BizTalk incluent cinq adaptateurs physiques qui représentent les liaisons prédéfinies WCF :**BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**,  **NetNamedPipeBinding**, et **NetMsmqBinding**. Les adaptateurs WCF pour les liaisons prédéfinies simplifient la définition des informations nécessaires pour la plupart des configurations d'application.  
  
 Les adaptateurs WCF BizTalk incluent également deux adaptateurs qui vous permettent de configurer librement les informations de liaison et de comportement WCF de l'emplacement de réception et du port d'envoi.  

## <a name="available-wcf-adapters"></a>Adaptateurs WCF disponibles
    
-   **Adaptateur WCF-WSHttp**. assure la prise en charge des normes WS-* sur le transport HTTP. L'adaptateur WCF-WSHttp met en œuvre les spécifications suivantes : WS-Transaction pour les interactions transactionnelles entre des applications externes et la base de données MessageBox, et WS-Security pour la sécurité et l'authentification des messages. Le transport est de type HTTP ou HTTPS, et le codage des messages est de type texte ou MTOM (Message Transmission Optimization Mechanism).  
  
-   **Adaptateur WCF-BasicHttp**. communique avec des clients et services Web basés sur des fichiers ASMX, ainsi que d'autres services conformes à la norme WS-I Basic Profile 1.1. Le transport est de type HTTP ou HTTPS, et le codage des messages de type texte.  
  
-   **Adaptateur WCF-NetTcp**. assure la prise en charge des normes WS-* via le transport TCP. Cet adaptateur permet une communication efficace dans un environnement WCF à WCF. L’adaptateur implémente les spécifications suivantes : WS-Transaction pour les interactions transactionnelles entre des applications externes et la base de données MessageBox et WS-Security pour l’authentification et de sécurité de message. Le transport est de type TCP et le codage des messages est binaire.  
  
-   **Adaptateur WCF-NetMsmq**. assure la prise en charge de la mise en file d'attente en utilisant [!INCLUDE[btsCoName](../includes/btsconame-md.md)] Message Queuing (MSMQ) pour le transport, et permet la prise en charge d'applications faiblement couplées, de l'isolement des pannes, de l'égalisation de la charge et des opérations déconnectées.  
  
-   **Adaptateur WCF-NetNamedPipe**. assure une optimisation sécurisée pour la communication entre processus sur un ordinateur. L'adaptateur WCF-NetNamedPipe utilise la sécurité de transport pour le transfert, des canaux nommés pour la remise des messages, ainsi qu'un codage de message binaire.  
  
-   **Adaptateur WCF-Custom**. permet d'utiliser des fonctionnalités d'extensibilité WCF. L'adaptateur vous permet de sélectionner et de configurer les informations de liaison et de comportement WCF pour l'emplacement de réception et le port d'envoi.  
  
-   **Adaptateur WCF-CustomIsolated**. permet d'utiliser des fonctionnalités d'extensibilité WCF sur le transport HTTP. L'adaptateur vous permet de sélectionner et configurer une liaison WCF et les informations de comportement pour l'emplacement de réception exécuté dans un hôte isolé.  
  
 En outre, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut l'Assistant Publication de services WCF BizTalk et l'Assistant Consommation de service WCF BizTalk. Le premier permet de créer et publier des orchestrations BizTalk, et de publier des schémas sous la forme de services WCF. Le second permet de générer les artefacts [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (par exemple, orchestrations et types) pour utiliser un service WCF basé sur le document de métadonnées du service WCF.  
  
 Les ressources dans cette section vous aident à configurer et déployer les adaptateurs WCF.  
  
## <a name="next"></a>Suivant 
  
-   [Quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md)  
  
-   [Configuration des adaptateurs WCF](../core/configuring-the-wcf-adapters.md)  
  
-   [Adaptateur WCF-BasicHttp](../core/wcf-basichttp-adapter.md)  
  
-   [Adaptateur WCF-WSHttp](../core/wcf-wshttp-adapter.md)  
  
-   [Adaptateur WCF-NetTcp](../core/wcf-nettcp-adapter.md)  
  
-   [Adaptateur WCF-NetMsmq](../core/wcf-netmsmq-adapter.md)  
  
-   [Adaptateur WCF-NetNamedPipe](../core/wcf-netnamedpipe-adapter.md)  
  
-   [Adaptateur WCF-Custom](../core/wcf-custom-adapter.md)  
  
-   [Adaptateur WCF-CustomIsolated](../core/wcf-customisolated-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des Services WCF](../core/using-wcf-services.md)   