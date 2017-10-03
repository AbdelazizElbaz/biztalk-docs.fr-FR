---
title: "Dépannage des erreurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, troubleshooting
- troubleshooting, errors
ms.assetid: 08cc95a3-4be9-450f-a015-e031011158f7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae7ad99b699da29d4d8680375f88e4d4a74ff66a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-errors"></a>Résolution des erreurs
Cette section traite des problèmes liés à [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] a généré des erreurs.  
  
## <a name="the-mllp-adapter-can-run-only-on-a-single-host-instance"></a>L’adaptateur MLLP être exécuté uniquement sur une seule instance d’hôte  
  
### <a name="symptom"></a>Symptôme  
 Vous ne pouvez pas activer un emplacement de réception avec un type de transport de MLLP et un gestionnaire de réception différent à un autre emplacement de réception existant. En outre, vous ne peut pas inscrire et démarrer un port d’envoi avec un gestionnaire d’envoi différent que le port d’envoi existant un autre.  
  
**Cause possible** : vous ne pouvez utiliser un MLLP réception (ou envoi) Gestionnaire sur un seul serveur. En outre, l’URI est désigné pour l’emplacement de réception (ou le port d’envoi) (le nom d’hôte dans les propriétés de Transport MLLP) doit être « localhost » ou le nom du serveur sur lequel l’ordinateur hôte de l’instance pour le Gestionnaire d’adaptateur de réception (ou d’envoi) est en cours d’exécution.  
  
**Résolution** : désigne le même gestionnaire de réception (ou envoi) pour MLLP tous les emplacements de réception (ou ports d’envoi) sur un serveur unique.  
  
## <a name="msh-and-ack-schemas-must-be-added-to-only-one-project"></a>Schémas MSH et l’accusé de réception doivent être ajoutés à un seul projet  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous essayez de générer un projet, vous obtenez une des erreurs suivantes :  
  
`Error: Cannot locate document specification as multiple schemas match the message type "http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF"`
  
`Schema http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF not found`
  
**Cause possible** : schémas MSH l’et l’accusé de réception (MSH_25_GLO_DEF.xsd et ACK_24_GLO_DEF.xsd) ont été déployés dans plusieurs projets.  
  
**Résolution** : Vérifiez que MSH_25_GLO_DEF.xsd et ACK_24_GLO_DEF.xsd ont été ajoutées à un seul projet.  
  
## <a name="exception-of-type-systemoutofmemoryexception-has-thrown-an-error-in-the-event-log"></a>Exception de type System.OutOfMemoryException a levé une erreur dans le journal des événements  
  
### <a name="symptom"></a>Symptôme  
 Vous obtenez l’erreur suivante ou similaire dans le journal des événements :  
  
`Exception of type System.OutOfMemoryException has thrown an error.`
  
**Cause possible** : lors du traitement d’un grand nombre de messages, certaines [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] composants de moteur peuvent présenter des fuites de mémoire.  
  
**Résolution** : redémarrer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="header-serialization-generates-an-error-in-the-event-viewer"></a>Sérialisation de l’en-tête génère une erreur dans l’Observateur d’événements  
  
### <a name="symptom"></a>Symptôme  
 Vous obtenez l’erreur suivante ou similaire dans le journal des événements, même si le message dans l’outil de contrôle d’intégrité et l’activité de suivi du fonctionnement (HAT) indique la réussite :  
  
`An error happened in the header during serialization.`
  
**Cause possible** : la valeur de transformation d’en-tête de message n’est pas définie correctement [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.  
  
**Résolution** : mappage de MSH de vérifier les valeurs dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.  
  
## <a name="duplicate-event-id-4133-serializer-errors-are-logged"></a>Les erreurs de sérialiseur événement ID 4133 en double sont enregistrées  
  
### <a name="symptom"></a>Symptôme  
 ID d’événement 4133 : « Erreur s’est produite dans l’en-tête pendant la sérialisation » se produit deux fois pour chaque instance d’un message avec une valeur MSH11 qui n’est pas valide.  
  
**Cause possible** : une erreur s’est produite lors du traitement de deux accusés de réception (validation et les accusés de réception Application) sans erreurs en double dans le journal des événements. Au lieu de cela, vous recevez un 4133 d’ID d’événement pour chacun des deux accusés de réception. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Crée une entrée de journal pour chaque accusé de réception qu’il génère.  
  
**Résolution** : Assurez-vous que vos messages ont un champ MSH11 correctement mis en forme et rempli.  
  
## <a name="send-pipeline-generates-an-error-when-using-the-2-way-mllp-adapter"></a>Envoyer le pipeline génère une erreur lors de l’utilisation de l’adaptateur MLLP à 2 facteurs  
  
### <a name="symptom"></a>Symptôme  
 Vous obtenez l’erreur suivante ou similaire dans le journal des événements :  
  
`There was a failure executing the send pipeline: "[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XPipelines.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XSendPipeline" Source: "[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fAsm" Send Port: "<*host name: port number*>" Reason: Message does not contain a part with name MSHSegment.`
  
**Cause possible** : l’application réceptrice ne répond pas avec un accusé de réception et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] attend une réponse de l’application de réception.  
  
**Résolution** : il s’agit par conception, et vous pouvez ignorer le message d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus et dépannage dans HL7](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)