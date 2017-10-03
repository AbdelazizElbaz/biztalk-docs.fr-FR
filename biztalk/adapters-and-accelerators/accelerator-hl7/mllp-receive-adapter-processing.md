---
title: "Traitement de l’adaptateur de réception de MLLP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, receive adapters
- MLLP adapters, send adapters
- receive adapters
ms.assetid: 03c9a5f6-6f23-454f-8bab-e7c7b6057efa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28713e22c37c12ef6f2cb9f8df8d228759d00c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mllp-receive-adapter-processing"></a>Traitement de l’adaptateur de réception de MLLP
Le protocole minimale de couche inférieure (MLLP) de réception adaptateur prend en charge les deux modes de réponse de demande unidirectionnels et bidirectionnels. L’adaptateur écoute et accepte les connexions.  
  
 Lorsque le MLLP réception adaptateur fonctionne en mode bidirectionnel, l’adaptateur recevra pas un nouveau message à partir de la connexion jusqu'à ce que le pipeline a généré l’accusé de réception (ACK) pour le message précédent.  
  
## <a name="configuration-parameters"></a>Paramètres de configuration  
 Les paramètres pour un gestionnaire de réception sont configurées au niveau de l’hôte BizTalk et s’appliquent à tous les emplacements de réception MLLP associés.  
  
|Paramètre|Utiliser|  
|---------------|---------|  
|*Max accepter le nombre maximal de connexions*|Limite le nombre de connexions simultanées ouvertes qui accepte l’adaptateur de réception.|  
  
## <a name="acknowledgments-with-the-two-way-mllp-receive-adapter"></a>Adaptateur de réception des accusés de réception avec le MLLP bidirectionnelle  
 Lors de la réception d’un MLLP bidirectionnelle adaptateur reçoit un message, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) peut générer les types d’accusés de réception suivants :  
  
-   HL7 Amélioré valider l’accusé de réception : dans ce scénario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un accusé de réception de validation sur la même connexion. Il envoie un accusé de réception accepte Application sur un port d’envoi différents.  
  
-   Application accepter l’accusé de réception : Dans ce scénario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un accusé de réception accepte Application sur la même connexion.  
  
-   Statique de l’accusé de réception : dans ce scénario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un accusé de réception sur la même connexion.  
  
-   Le type d’accusé de réception généré varie selon la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] des paramètres de l’Explorateur de Configuration pour le tiers qui a envoyé le message. La valeur des champs MSH 15 16 d’un message individuel peut remplacer ce paramètre. Toutefois, pour les applications attendu des accusés de réception statique, la configuration peut uniquement être définie via [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.  
  
## <a name="error-conditions"></a>Conditions d'erreur  
 Les événements suivants se produisent lorsqu’il existe une condition d’erreur ou d’une inactivité :  
  
-   Si l’emplacement de réception est désactivé ou [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] s’arrête, les éléments suivants se produisent :  
  
    -   L’emplacement de réception n’accepte plus les nouvelles connexions.  
  
    -   Pour les connexions existantes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] complètement reçoit le message en cours, puis ferme la connexion.  
  
-   Lorsque l’inactivité est détectée (aucune donnée de charge utile reçue sur l’emplacement de réception dans le délai spécifié), l’adaptateur ferme la connexion.  
  
-   Si [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] reçoit un message incomplète, la partie reçue est suspendue. Tous les octets reçus en dehors d’un message (avant le premier service bus sur une nouvelle connexion, entre EB/CR et SB du message suivant) sont ignorés.  
  
-   Si le pipeline ne parvient pas à analyser le message, le message est toujours remis à la base de données MessageBox, dont la propriété promue **ParseError = true**.  
  
-   Si un message échoue en raison de l’absence d’un abonnement, ou en raison d’erreurs structurelles dans l’en-tête, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] interrompt le message dans sa forme « format câble » d’origine (avant l’analyse). Une raison fréquente de l’échec de non-abonnement est l’absence de propriétés promues. Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] interrompt le message non analysé, le **BTS. MessageType** sera vide.  
  
 Le tableau suivant répertorie les erreurs que le MLLP réception retourne de la carte.  
  
|Événement|ID|Condition d'erreur|  
|-----------|--------|---------------------|  
|**ErrorListening**|8448|N’a pas pu lier à un socket local (probablement que d’autres applications locales à l’aide de la même combinaison adresse IP/port ID).|  
|**ErrorAcceptingConnection**|8449|N’a pas pu établir une connexion TCP avec le tiers distant. Soit [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] atteint la limite du nombre maximal de connexions, ou les ressources sont insuffisantes.|  
|**ErrorSubmittingMessage**|8452|La base de données MessageBox n’a pas pu accepter le message. Soit [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] n’était pas disponible ou les ressources sont insuffisantes.|  
|**ErrorSendingAck**|8454|[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]n’a pas pu renvoyer l’accusé de réception, car la connexion n’était pas disponible.|  
  
## <a name="performance-counters"></a>Compteurs de performances  
 Le tableau suivant répertorie les compteurs de performances par l’adaptateur MLLP.  
  
|Compteur|Signification|  
|-------------|-------------|  
|Octets|Taille de la charge utile de tous les documents reçus ou envoyés.|  
|Octets par seconde|Débit actuel de la charge utile reçus ou envoyés.|  
|Documents traités|**Réception de MLLP**:<br /><br /> Nombre de documents remis avec succès à la base de données MessageBox.<br /><br /> **Envoi MLLP**:<br /><br /> Nombre de documents prêts à l’application distante.|  
|Documents en échec|**Réception de MLLP**:<br /><br /> Nombre de documents n’a pu être remis à la base de données MessageBox.<br /><br /> **Envoi MLLP**:<br /><br /> Nombre de documents n’a pu être remis à l’application distante.|  
|État de la connexion|L’état de la connexion de la carte, 1 ou 0 (1 = connecté).|  
  
 Les instances de compteur de performances utilisent le modèle de dénomination suivant :  
  
```  
{recv|trans} : connection name : remote IP address : remote port ID  
```  
  
 Où le MLLP réception adaptateur utilise le préfixe « recv », et l’adaptateur d’envoi MLLP « trans ».  
  
> [!NOTE]
>  Accusés de réception envoyés par ports de réception (par exemple, un adaptateur fonctionne en mode bidirectionnel) et envoyer les ports (d’exploitation pour recevoir les accusés de réception sur la même connexion de socket) ne sont pas comptées.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages encodés en MLLP](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [Les paramètres de configuration pour l’envoi et les adaptateurs de réception](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [Traitement d’adaptateur MLLP envoi](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [Configuration d’un Port d’envoi pour recevoir des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)