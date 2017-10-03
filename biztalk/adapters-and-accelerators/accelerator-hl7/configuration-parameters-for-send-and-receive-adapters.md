---
title: "Les paramètres de configuration pour l’envoi et les adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters
- send adapters
- configuration parameters [adapters]
- receive adapters
ms.assetid: f24ca8ae-feaf-4e5f-b434-76bc3c1c8ccf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c33e49e82f9ebbf8856dd447989d7557558c0e4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-parameters-for-send-and-receive-adapters"></a>Les paramètres de configuration pour l’envoi et les adaptateurs de réception
Cette section fournit des paramètres de configuration pour envoyer et recevoir des cartes de protocole de couche inférieure minimale (MLLP). Ces paramètres se répartissent en deux types : bloquer les caractères et les paramètres de connexion réseau.  
  
 Définissez le bloc de paramètres de caractères dans les propriétés de Transport MLLP pour un port d’envoi à l’aide du type de transport MLLP.  
  
 Vous pouvez définir les paramètres de connexion réseau dans les propriétés de Transport MLLP pour soit un port d’envoi ou emplacement à l’aide du type de transport MLLP de réception. Pour ce faire, ouvrez la Console Administration de BizTalk Server, accédez au dossier des Ports d’envoi ou emplacements de réception, le cas échéant, cliquez sur le port d’envoi ou emplacement de réception, cliquez sur **propriétés**, puis cliquez sur  **Configurer**.  
  
## <a name="block-characters"></a>Caractères de bloc  
 Ces paramètres sont des caractères spéciaux qui doivent placer HL7 messages reçus ou envoyés par les cartes MLLP. Ces caractères forment un bloc au format suivant : \<SB >*DDD*\<EB >\<CR >, où *DDD* les données du message, l’acronyme \<SB > est le caractère de début de bloc, \<EB > est le caractère de fin de bloc, et \<CR > est le transport retour.  
  
|Paramètre|Utiliser|  
|---------------|---------|  
|**\<CR > retour chariot**|Valeur d’octet (au format hexadécimal) que vous utilisez pour le retour chariot (le deuxième wrapper octets après l’octet de fin). Ce paramètre est facultatif.|  
|**\<EB > caractère du bloc de fin**|Valeur d’octet que vous utilisez pour l’octet de fin (wrapper du code de fin de message). ASCII \<FS >, par exemple, \<1C >.|  
|**\<SB > caractère de début de bloc**|Valeur d’octet que vous utilisez pour l’octet de début (wrapper d’en-tête de message). ASCII \<VT >, par exemple, \<0 b >.|  
  
## <a name="deliverymode"></a>DeliveryMode  
 Vous utilisez le paramètre de mode de livraison pour contrôler si les fichiers de l’instance sont remis en séquence, ou hors séquence (dans l’ordre, en désordre). Chaque emplacement de réception a son propre remise pour l’instance de séquence de fichiers.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|livraison chronologique des messages (éventuellement en anglais)|**Réception de MLLP**:<br /><br /> Définir le **livraison chronologique des messages** propriété **TRUE**, pour spécifier que les messages doivent être traités dans un ordre spécifié. Cette option est importante dans les cas où les messages doivent être traités les uns à la suite des autres, comme indiqué par le processus d'entreprise partenaire.<br /><br /> Si vous définissez la **livraison chronologique des messages** propriété **FALSE** (la valeur par défaut), le port n’applique pas la livraison chronologique des messages.|  
  
## <a name="network-connection-parameters"></a>Paramètres de connexion réseau  
 Vous utilisez ces paramètres pour établir une connexion sur le réseau, y compris les commentaires, nom de la connexion, nom d’hôte, ID de port, délai de réception et un délai d’envoi.  
  
|Paramètre|Utiliser|  
|---------------|---------|  
|**Commentaires**|Description de la connexion. Ce paramètre est facultatif.|  
|**Nom de la connexion**|Nom de connexion analysée. Il est recommandé que le nom unique. Le nom est inclus dans le nom des instances de compteur de performance pour cette connexion.|  
|**Hôte**|**Réception de MLLP**:<br /><br /> Ce paramètre est facultatif. Spécifiez une interface locale sur lequel écouter les connexions entrantes. Par défaut est à l’écoute sur toutes les interfaces locales.<br /><br /> **Envoi MLLP**:<br /><br /> Spécifiez le nom NetBIOS ou l’adresse IP de l’ordinateur de métier (LOB) à laquelle vous souhaitez vous connecter.|  
|**Connexion permanente**|**Réception de MLLP**:<br /><br /> Définir le **connexion permanente** propriété **FALSE** (la valeur par défaut), pour fermer la connexion une fois que la connexion est inactive pendant la période d’expiration. Définir le **connexion permanente** propriété **True**, pour maintenir ouverte la connexion.<br /><br /> Le tableau suivant montre les résultats pour les valeurs possibles de la **connexion permanente** et **délai d’attente de réception** valeurs.<br /><br /> **FALSE**<br /><br /> - >0<br /><br /> -La connexion se ferme après un message est reçu ou que le délai d’expiration est écoulé.<br /><br /> **FALSE**<br /><br /> - 0<br /><br /> -Provoque une condition d’erreur : « valeur de délai d’attente de réception ne doit pas être zéro en cas de connexion persistante FALSE ».<br /><br /> **TRUE**<br /><br /> - 0<br /><br /> -Jamais la connexion s’arrête.<br /><br /> **TRUE**<br /><br /> - <>0<br /><br /> -Provoque une condition d’erreur : « valeur de délai d’attente de réception doit être zéro en cas de connexion persistante TRUE. »<br /><br /> **Envoi MLLP**:<br /><br /> Définir le **connexion permanente** propriété **FALSE**pour fermer la connexion si une réponse est reçue dans le délai imparti ou si le délai d’expiration est écoulé. Définir le **connexion permanente** propriété **True** (la valeur par défaut), pour maintenir ouverte la connexion.<br /><br /> Le tableau suivant montre les résultats pour les valeurs possibles de la **connexion permanente** et **délai d’attente de réception** valeurs.<br /><br /> **FALSE**<br /><br /> -O ou > 0<br /><br /> -La connexion se ferme après une réponse est reçue ou le délai d’expiration est écoulé.<br /><br /> **TRUE**<br /><br /> -0 ou différente de 0<br /><br /> -Jamais la connexion s’arrête. Le **envoyer un délai d’attente** valeur n’affecte pas l’état de la connexion.<br /><br /> Le tableau suivant indique les types de l’état de connexion pour le port d’envoi différent lorsque les paramètres de connexion persistante et avec sollicitation-réponse sont modifiés.<br /><br /> Unidirectionnel statique<br /><br /> -TRUE<br /><br /> -Non<br /><br /> -Reste ouvert<br /><br /> Unidirectionnel statique<br /><br /> -TRUE<br /><br /> -Oui<br /><br /> -Reste ouvert<br /><br /> Unidirectionnel statique<br /><br /> -FALSE<br /><br /> -Non<br /><br /> -Fermé<br /><br /> Unidirectionnel statique<br /><br /> -FALSE<br /><br /> -Oui<br /><br /> -Fermé<br /><br /> Statique avec sollicitation-réponse<br /><br /> -TRUE<br /><br /> -Non<br /><br /> -Reste ouvert<br /><br /> Statique avec sollicitation-réponse<br /><br /> -TRUE<br /><br /> -Oui<br /><br /> -Reste ouvert<br /><br /> Statique avec sollicitation-réponse<br /><br /> -FALSE<br /><br /> -Non<br /><br /> -Fermé<br /><br /> Statique avec sollicitation-réponse<br /><br /> -FALSE<br /><br /> -Oui<br /><br /> -Fermé|  
|**Port**|**Réception de MLLP**:<br /><br /> ID de port local à écouter.<br /><br /> **Envoi MLLP**:<br /><br /> ID de port distant auquel vous souhaitez vous connecter.|  
|**Un délai d’envoi**|**Envoi MLLP**:<br /><br /> La durée maximale que l’adaptateur d’envoi doit patienter lors de l’envoi d’un message, après laquelle le socket émetteur expire. Lors de l’expiration, BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) va réessayer le message.<br /><br /> En outre, en cas d’opération synchrone du port d’envoi, la durée maximale pour la réception de l’accusé de réception (ACK) à partir de l’objet LOB.|  
|**Délai de réception**|**Réception de MLLP**:<br /><br /> La durée maximale pendant laquelle l’adaptateur de réception doit patienter lors de la réception d’un message, après laquelle le socket de réception expire. Lors de l’expiration, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ferme la connexion.<br /><br /> En outre, en cas de fonctionnement synchrone de l’emplacement de réception, la durée maximale pour l’envoi de l’accusé de réception à l’objet LOB.|  
|**Sollicitation-réponse activé**|**Envoi MLLP**:<br /><br /> Oui/non. Permet de recevoir des accusés de réception sur la même connexion TCP.|  
|**Soumettre emplacement de réception URI pour l’accusé de réception**|**Envoi MLLP**:<br /><br /> URI de l’emplacement de réception sous lequel les accusés de réception reçus sur la même connexion TCP sera remis à la base de données MessageBox.|  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages encodés en MLLP](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [Traitement de l’adaptateur de réception de MLLP](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [Traitement d’adaptateur MLLP envoi](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [Configuration d’un Port d’envoi pour recevoir des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)