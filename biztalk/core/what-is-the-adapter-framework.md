---
title: "Présentation de l'infrastructure d'adaptateurs | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd1e2fd7-4e77-49c4-839d-c2bf16b10ba2
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 648c22a52e543b24458daa73146836e1e3a5463e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-adapter-framework"></a>Présentation de l'infrastructure d'adaptateurs
L'infrastructure d'adaptateurs BizTalk offre un mécanisme ouvert et stable permettant à tous les adaptateurs d'implémenter des données ou d'y accéder à partir du moteur de messagerie [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les interfaces décrites dans le **Microsoft.BizTalk.adaptateur.Framework** espace de noms permettent aux adaptateurs fournissent un moyen de modifier des pages de propriétés de configuration. Elles sont également un moyen d'importer des services et des schémas dans le projet BizTalk.  
  
 La figure suivante montre comment un adaptateur et l'infrastructure d'adaptateurs s'associent pour connecter votre application à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 ![L’infrastructure d’adaptateurs](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")  
  
 Les étapes suivantes décrivent la séquence d'étapes montrées dans cette figure :  
  
1.  Les données sont reçues d'un emplacement de réception qui écoute les messages ayant un protocole donné à une adresse spécifiée. Cet emplacement de réception est associé à un adaptateur et à un pipeline de réception. Vous pouvez configurer à la fois l'adaptateur et les composants de pipeline pour appliquer une logique spécifique aux messages d'un protocole prédéterminé.  
  
2.  Une fois que le message a été reçu à l'emplacement de réception, il est transmis à l'adaptateur, qui, à sont tour, crée un message BizTalk. L'adaptateur joint ensuite le flux de données au message (généralement dans le corps du message), ajoute les métadonnées appartenant au point de terminaison depuis lequel les données ont été reçues, puis soumet le message au moteur de messagerie BizTalk.  
  
3.  Le moteur de messagerie envoie le message au pipeline de réception au sein duquel plusieurs opérations ont lieu : conversion des données au format XML, authentification de l'expéditeur du message, décryptage du message et validation des données XML.  
  
4.  Le moteur de messagerie publie le message sur la base de données MessageBox. Cette base de données est une table Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui contient les messages à traiter. Les orchestrations et les ports d'envoi peuvent s'y abonner.  
  
5.  Le moteur de messagerie envoie le message soit à une orchestration, soit à un port d'envoi abonné en fonction des propriétés de contexte du message correspondant aux spécifications définies dans le filtre de l'abonné.  
  
6.  Si une orchestration est l'abonné, elle traite le message et l'envoie via un port d'envoi. Si l'abonné est un port d'envoi, le message passe par le pipeline d'envoi, puis par un adaptateur d'envoi avant d'être transmis.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [L’utilisation des outils de Framework adaptateur](../core/using-the-adapter-framework-tools.md)  
  
-   [Modèles d’échange de Message de l’adaptateur](../core/adapter-message-exchange-patterns.md)  
  
-   [Composants d’adaptateur Framework](../core/adapter-framework-components.md)  
  
-   [Modèle d’hébergement de carte](../core/adapter-hosting-model.md)  
  
-   [Composants de l’adaptateur](../core/adapter-components.md)