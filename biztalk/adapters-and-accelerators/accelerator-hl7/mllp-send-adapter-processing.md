---
title: "Traitement de l’adaptateur d’envoi MLLP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, send adapters
- send adapters
- MLLP adapters, send adapters
ms.assetid: b8e47c7f-4a69-4f0c-86b4-26ed9c70613c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1644d699014f23ce90568034c4bd90f6f0c7b099
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mllp-send-adapter-processing"></a>Traitement d’adaptateur MLLP envoi
L’adaptateur d’envoi de protocole de couche inférieure minimale (MLLP) prend en charge les modes de transport unidirectionnels et bidirectionnels dans les configurations suivantes :  
  
-   Adaptateur d’envoi de sollicitation-réponse bidirectionnel  
  
-   Adaptateur d’envoi unidirectionnel configuré pour recevoir des accusés de réception (ACK)  
  
-   Adaptateur d’envoi unidirectionnel configuré pour aucun message de retour  
  
## <a name="two-way-solicit-response-send-mllp-adapter"></a>Adaptateur de sollicitation-réponse bidirectionnel envoi MLLP  
 Utilisez cet adaptateur dans un scénario synchrone de bout en bout à true. Par conséquent, vous pouvez utiliser uniquement cette carte avec des tiers de destination. L’adaptateur d’envoi en continu conserve une connexion ouverte sur le tiers distant (URL) jusqu'à ce qu’il achemine un message de retour à la réponse de demande de port de réception. Consultez le diagramme suivant pour l’architecture de traitement de la réponse demande/réponse de sollicitation.  
  
 Lorsque vous utilisez cet adaptateur, vous pouvez forcer le système pour renvoyer un accusé de réception ou d’un message de réponse à l’application line-of-business. Vous faire avec les accusés de réception d’itinéraire pour le Pipeline d’envoi sur le paramètre de Port de réception de réponse de demande dans le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration. Sélectionnez cette propriété pour renvoyer un accusé de réception, ou désélectionnez-la pour retourner une réunion de réponse.  
  
 Une fois qu’un port d’envoi à l’aide de cet adaptateur a envoyé le message d’origine, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supprime ce message. Le pipeline de réception associé à ce port d’envoi ne génèrent pas d’un accusé de réception. BizTalk transmet la réponse à la requête à l’application source, quelle que soit la valeur du champ MSA2 de cette réponse.  
  
## <a name="one-way-send-mllp-adapter-configured-to-receive-acks"></a>Adaptateur MLLP envoi unidirectionnel configuré pour recevoir des accusés de réception  
 Cet adaptateur reçoit les accusés de réception sur la même connexion de socket qu’il envoie le message d’origine et remet les accusés de réception à l’emplacement de réception. L’adaptateur d’envoi conserve en permanence une connexion ouverte sur le tiers distant (URL), même si aucun message en attente pour [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] les envoyer à celui-ci. Si plusieurs ports pointent vers le même tiers distant, l’adaptateur d’envoi maintient une connexion pour chaque port d’envoi.  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) permet d’installer un par défaut emplacement de réception, TwoWayAckReceiveLocation. Vous pouvez utiliser cet emplacement de réception avec l’adaptateur d’envoi MLLP pour la réception des accusés de réception. Cette configuration du port d’envoi à l’aide de cet adaptateur vous oblige à associer un emplacement de réception avec le port d’envoi.  
  
 Utiliser ce port d’envoi si vous configurez pour recevoir un message de réponse avec un champ de compte de service administré ou pour prendre en charge de plusieurs destinations. L’adaptateur de sollicitation-réponse bidirectionnel ne fonctionne pas avec le champ de compte de service administré ou plusieurs destinations.  
  
### <a name="acknowledgments-received-by-the-one-way-mllp-send-adapter"></a>Adaptateur d’envoi accusés de réception reçus par le MLLP unidirectionnel  
 Lorsqu’un adaptateur d’envoi unidirectionnel MLLP configuré pour les accusés de réception reçoit un, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supprime le message d’origine de la base de données MessageBox, il effectue une nouvelle tentative, suspension ou, selon le type de l’accusé de réception. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]analyse de l’accusé de réception en deux phases :  
  
-   La première phase s’effectue dans l’adaptateur d’envoi où [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] analyse le champ MSA1 pour déterminer le type de l’accusé de réception.  
  
-   Dans la deuxième phase, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] effectue une analyse complète de l’accusé de réception, puis envoie l’accusé de réception à la base de données MessageBox.  
  
 Vous configurez l’accusé de réception qui attend de l’adaptateur d’envoi bidirectionnel dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.  
  
 Le tableau suivant montre les accusés de réception à un adaptateur d’envoi MLLP peut recevoir et l’action résultante sur le message d’origine.  
  
|Accusé de réception reçu|Action sur le message d’origine|  
|------------------|------------------------------------|  
|Accepter de validation, ou Application|Supprimer à partir de la base de données MessageBox|  
|COMMIT/Application, de rejeter l’accusé de réception ou de l’accusé de réception non valide|Suspendre|  
|Erreur de validation / d’Application|Nouvelle tentative/déplacement de transport/Suspend de sauvegarde|  
|Réussite de l’accusé de réception statique|Supprimer à partir de la base de données MessageBox|  
|Échec de l’accusé de réception statique|Suspendre|  
  
 Le tableau suivant répertorie les conditions de l’accusé de réception qui ne sont pas valides.  
  
|Instance|Condition|  
|--------------|---------------|  
|HL7 (Original, des améliorations différés)|1.  Ne contient pas de XML.<br />2.  N’a pas la structure pour le champ MSA1 ne peut pas être récupéré ; ou le champ MSA1 ne contient pas une des valeurs autorisées (autorité de certification, AA, CR, AR, CE, AE).|  
|Statique|Ne pas correspondre à l’une des valeurs autorisées pour la réussite ou échouer l’accusé de réception.|  
|Contient du code XML|Traité comme un accusé de réception d’acceptation (quel que soit le contenu) et de suppression du message d’origine.|  
  
### <a name="error-conditions"></a>Conditions d'erreur  
 Les éléments suivants sont possibles lorsqu’il existe une condition d’erreur ou d’une inactivité :  
  
-   Si le message sortant échoue lors de la sérialisation, l’adaptateur d’envoi n’envoie pas le message, sauf s’il est un lot de messages qui [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sont diffusés en continu. Si tel est le cas, et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] détecte un échec de la sérialisation à mi-chemin via le message, l’adaptateur n’enverra pas EB/CR depuis [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] n’a pas envoyé le message de fin. Le pipeline consigne une erreur et l’adaptateur tente d’envoyer le message du lot à nouveau.  
  
-   Si une opération d’envoi échoue, l’adaptateur tente d’envoyer le message à nouveau, jusqu’au nombre de tentatives spécifié dans les paramètres de configuration du port d’envoi. Après avoir exploré les nouvelles tentatives, le message se déplace vers le transport secondaire, s’il en existe. Si tout le reste échoue, le message est suspendu. Le message suspendu sera sous la forme (XML) d’origine.  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]peut générer des événements pour décrire les conditions d’erreur suivants :  
  
|Événement|ID|Condition d'erreur|  
|-----------|--------|---------------------|  
|ErrorSendingMessage|8450|Impossible d’envoyer un message par le tiers distant. Les raisons les plus courantes sont les défaillances du réseau ou des délais d’attente. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]peut de signaler cette erreur si le pipeline d’envoi échoue lors de la sérialisation d’un message volumineux.|  
|ErrorReceivingAck|8451|N’a pas pu recevoir un accusé de réception, en raison d’une défaillance du réseau ou de délai d’attente.|  
|ErrorConnecting|8453|Pas pu établir de connexion d’un TCP par le tiers distant, le nom d’hôte n’a pas pu être résolu, ou la partie distante n’est pas à l’écoute sur le port ou rejette les connexions.|  
  
> [!NOTE]
>  La configuration du tiers de destination (en MSH5 du message d’origine) détermine si [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] attend un HL7 ou un accusé de réception statique. En cas d’une incompatibilité, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] traite l’accusé de réception comme non valide.  
  
 Une fois la MLLP envoyer traite un accusé de réception, l’accusé de réception est remis à l’emplacement de réception en tant que message sur son propre. Le désassembleur effectue une analyse complète de l’accusé de réception, ce qui peut entraîner l’analyse des erreurs signalées par le pipeline de réception et/ou de l’accusé de réception en cours d’interruption.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages encodés en MLLP](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [Les paramètres de configuration pour l’envoi et les adaptateurs de réception](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [Traitement de l’adaptateur de réception de MLLP](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [Configuration d’un Port d’envoi pour recevoir des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)