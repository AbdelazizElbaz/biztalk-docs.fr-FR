---
title: Affichage des flux de messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing, messages
- messages, processing
- HAT, Message Flow view
- messages, HAT
ms.assetid: 08d2c052-98d0-43ca-99e5-48d0754411df
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d15ba3e6fa45b95ab49e1d24d5388a767d6bd8ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="viewing-message-flow"></a>Affichage du flux de message
Un flux de message est un ensemble d'étapes de traitement consécutives auquel est soumis un message. Vous pouvez accéder à la vue Flux de messages via le menu contextuel qui apparaît lorsque vous cliquez avec le bouton droit sur une instance de service ou de message dans la page Présentation du groupe dans la console Administration de BizTalk Server. Une fois la vue Flux message affichée, vous pouvez basculer entre la vue Flux message et le débogueur de l'orchestration.  
  
 La vue Flux message affiche les messages envoyés et reçus par une instance de service (pipeline/port ou orchestration), et des détails comme l'URL, le port et le tiers utilisés. Elle affiche également les instances de service qui ont traité les messages avant qu'ils n'arrivent dans l'instance de service que vous êtes en train de consulter. Vous avez la possibilité de revenir sur ces instances et de voir les messages qu'elles reçoivent et envoient. Vous pouvez aussi afficher les instances de service qui ont reçu les messages traités par l'instance de service que vous consultez actuellement et les examiner plus en détail. En d'autres termes, vous pouvez suivre l'intégralité du chemin d'un message d'activation dans votre processus d'entreprise.  
  
 Vous pouvez également naviguer d'une instance de service non terminée (c'est-à-dire en train de traiter un message) dans la vue Flux message, aux détails de cette instance dans la console Administration de BizTalk Server pour voir son état actuel (en cours, suspendu, etc.).  
  
 La partie supérieure de la fenêtre Flux message comporte des informations sur l'instance de service, telles que l'heure de début et de fin, les codes d'erreur ou la version. La partie inférieure de la fenêtre présente l'activité des messages pour l'instance de service, détaillant les messages reçus ou envoyés. Pour afficher plus de détails sur chacune des instances de message, cliquez sur les boutons Développer ou Réduire. Les instances de message affichent tous les détails par défaut.  
  
 En regard de la colonne Entrée/Sortie, l'espace de noms cible et l'élément racine identifient le schéma. Ensuite, apparaissent les informations détaillées sur le message. Sous les informations relatives au schéma figure un lien avec un nom d'élément, par exemple PipelineRéceptionPrêtParticipatif. Cliquez sur le lien pour obtenir des informations sur cet élément et pouvoir suivre, ainsi, l'acheminement du message via cet élément.  
  
 Pour revenir au service par lequel vous avez commencé, cliquez sur l'élément source ou de destination correspondant, dans l'autre élément.  
  
 Le tableau ci-dessous présente les informations affichées pour chacun des services.  
  
|Nom|Sommaire|  
|----------|--------------|  
|ID de l'instance|GUID (Globally Unique Identifier) associé à l'instance.|  
|Hôte|Nom de l'hôte exécutant l'orchestration ou le pipeline.|  
|État|État actuel de l'instance. L'instance peut être en cours d'exécution, réussie, manuellement suspendue, en état d'erreur, terminée, en mode de débogage ou en arrêt.|  
|Start Time|Heure à laquelle l'orchestration/le pipeline a commencé.|  
|Heure de fin|Heure à laquelle l'orchestration/le pipeline s'est terminé.|  
|Duration|Durée d'exécution, en millisecondes, de l'élément.|  
|Code de sortie|Code de sortie technique.|  
|Informations sur l’erreur|Message texte sur l'erreur.|  
|Nom|Nom de l'orchestration ou du pipeline.|  
|Type|Type d'élément : orchestration ou pipeline.|  
|ID de version|Version unique de l'élément.|  
|Heure du déploiement|Heure à laquelle l'orchestration/le pipeline a été déployé.|  
  
 En dessous, le tableau des détails de l'élément présente l'activité des messages envoyés ou reçus par l'orchestration ou le pipeline pour les instances de service. Chaque ligne du tableau représente un message. Vous pouvez développer une instance de message afin d'en afficher les détails, tels que l'ID, la taille et le nom du port.  
  
 Le tableau suivant récapitule les informations affichées pour chaque instance de message.  
  
|Nom|Sommaire|  
|----------|--------------|  
|Entrée/Sortie|L'icône Message reçu ou Message envoyé indique l'état des messages.|  
|Instance de message|Espace de noms cible et élément de niveau supérieur ; échange non analysé si inconnu.|  
|État du message|Les états possibles : OK, en cours de Transmission, Échec de la Transmission, Échec de la Transmission (essai à renouveler) et Échec de la Transmission (essai à renouveler lors du transport secondaire).|  
|Horodateur|Heure à laquelle un message spécifique a été impliqué dans l'action en cours (envoi/réception).|  
  
 Lorsque vous avez développé l'instance de message, les informations suivantes s'affichent.  
  
|Nom|Sommaire|  
|----------|--------------|  
|ID d'instance de message|GUID du message.|  
|Taille|Taille du message. Aucune valeur ne s'affiche si le message ne comporte pas de taille.|  
|Éléments|Nombre de parties du message hors raccourci.|  
|Adaptateur|Adaptateur utilisé pour transmettre le message, par exemple FILE, HTTP, SOAP, Message Queuing BizTalk, SOAP ou un adaptateur WCF.|  
|URL|URL source ou de destination.|  
|Port|Nom du port d'envoi ou de réception du message.|  
|Nom du tiers|Nom du tiers envoyant ou recevant le message. Ce champ apparaît uniquement si l'information est connue.|  
|Certificat de déchiffrement|Empreinte du certificat utilisé pour déchiffrer le message. Ce champ apparaît uniquement si un message comporte un certificat de déchiffrement.|  
|Signature|Signature dans le message. Ce champ apparaît uniquement si le message est signé.|  
|Icône d'état|Indique l'état actuel du message, notamment s'il a été reçu, envoyé ou s'il se trouve dans la file de travail.|  
|URL de l'élément source/cible|Élément (orchestration ou pipeline) identifié comme source/destination du message. Lorsque vous cliquez sur l'URL, le système redirige l'utilisateur vers une vue de cette instance de l'élément.|  
  
 Lorsque vous affichez une instance d’orchestration, vous pouvez basculer vers la vue débogueur Orchestration en cliquant sur **basculer vers débogueur de l’Orchestration**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la vue débogueur Orchestration](../core/working-with-the-orchestration-debugger-view.md)   
 [Affichage des messages suivis et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)