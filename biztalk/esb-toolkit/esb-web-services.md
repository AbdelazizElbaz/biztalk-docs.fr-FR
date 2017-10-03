---
title: Les Services Web ESB | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c122ecdd-344a-4f76-9c73-bf692d479c09
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e6f59770e14e14ed9599d0c26bae187f340e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="esb-web-services"></a>Services Web ESB
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contient les services Web suivants :  
  
-   **Démarrage d’itinéraire services Web.** Ces services accepte les messages externes et envoyer des messages pour le traitement. Le contenu d’un itinéraire contient des instructions de traitement et les métadonnées qui décrivent les services à exécuter. Services de routage définissent les points de terminaison auquel le message doit être routé, alors que les services de transformation de spécifient la façon dont les messages doivent être transformés. Ces services de support unidirectionnels et bidirectionnels (requête-réponse) de traitement ; les implémentations ASMX et Windows Communication Foundation (WCF) sont fournies. Les services Web de rampe d’entrée d’itinéraire ne sont pas propres au type, de message afin qu’ils acceptent n’importe quel type de message.  
  
-   **Service Web de programme de résolution.** Ce service permet aux applications externes à appeler l’infrastructure de programme de résolution ESB Microsoft pour rechercher des points de terminaison ESB basées sur des mécanismes de résolution pris en charge par l’infrastructure de programme de résolution. Le service offre également des implémentations ASMX et WCF.  
  
-   **Service Web de transformation.** Ce service permet l’exécution de Microsoft BizTalk Server mappe sans subir la surcharge de la persistance de la boîte de Message, étendant les capacités de BizTalk Server l’exécution de la carte pour les applications qui ne sont pas basées sur le serveur BizTalk. Le service offre des implémentations ASMX et WCF.  
  
-   **Service Web de gestion des exceptions.** Ce service accepte des messages d’exception à partir de sources externes et des itinéraires à l’aide du pipeline du processeur de pannes normaliser, suivre et publier le message d’exception pour le portail de gestion ESB. Le service offre des implémentations ASMX et WCF.  
  
-   **Service Web UDDI.** Ce service permet aux applications et les utilisateurs rechercher des points de terminaison selon le nom du service, fournisseur de l’entreprise ou catégorie d’entreprise ; il permet également d’applications et les utilisateurs à manipuler les fournisseurs d’entreprise, services, et catégories stockées dans un Référentiel UDDI. Il s’agit d’un service de l’infrastructure à clé utilisé par le portail de gestion ESB et les fournisseurs tiers.  
  
-   **Service Web d’opérations BizTalk.** Basés sur ASMX ce service expose des informations sur les hôtes BizTalk Server, orchestration, applications et état de l’activation des utilisateurs et des tiers à facilement une requête pour l’état de l’application et l’hôte, quelle que soit l’emplacement des ordinateurs au sein de le groupe BizTalk Server. Les requêtes peuvent inclure état du message et flux de changement d’état, des instances de service en cours et détails du message. Le service peut également mettre à jour les emplacements de réception. Il s’agit d’un service de l’infrastructure à clé utilisé par le portail de gestion ESB et les fournisseurs tiers.  
  
 Pour plus d’informations sur les services Web fourni dans le cadre de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], consultez [à l’aide des Services Web BizTalk ESB Toolkit](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md).