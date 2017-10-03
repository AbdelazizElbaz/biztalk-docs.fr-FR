---
title: "Configuration des accusés de réception de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, configuring
- messages, acknowledgements
- configuring, acknowledgements
ms.assetid: 6ebcfc32-0a0b-4388-938f-6569a2014b91
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b0e9be1934374d1aa8def379560f675493c590d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-message-acknowledgments"></a>Configuration des accusés de réception de Message
Vous utilisez la [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Configuration Explorer **accusé de réception** onglet pour spécifier les propriétés de l’accusé de réception pour les accusés de réception entrants et générés.  
  
 L’illustration suivante montre le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **accusé de réception** onglet.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-ack.gif "hl7_ops_ack")  
  
 Utilisez les procédures suivantes pour ouvrir [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration et configurer des accusés de réception de message.  
  
### <a name="to-open-btahl7-configuration-explorer"></a>Pour ouvrir l’Explorateur de Configuration de BTAHL7  
  
-   Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.  
  
### <a name="to-configure-message-acknowledgments"></a>Pour configurer des accusés de réception de message  
  
1.  Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** , sélectionnez la partie que vous souhaitez configurer, puis, dans le **accusés de réception** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Type d’accusé de réception**|Sélectionnez l'une des options suivantes :<br /><br /> -   **None**. Sélectionnez cette option si vous ne souhaitez pas configurer les accusés de réception.<br />-   **OriginalMode**. Sélectionnez cette option pour configurer **MSH1-séparateur de champs**, **où MSH2 a été – l’encodage de caractères**, et **MSH8 – sécurité** options uniquement.<br />-   **EnhancedMode**. Sélectionnez cette option pour configurer toutes les options disponibles d’accusé de réception.<br />-   **DeferredMode**. Sélectionnez cette option pour configurer **MSH1-séparateur de champs**, **où MSH2 a été – l’encodage de caractères**, et **MSH8 – sécurité** options uniquement.<br />-   **StaticMode**. Sélectionnez cette option pour configurer le **en cas de réussite** et **en cas d’échec** options d’accusé de réception.|  
    |**MSH 15 accepter le Type d’accusé de réception**|Sélectionnez l'une des options suivantes :<br /><br /> -   **AL**. Sélectionnez cette option si vous souhaitez toujours envoyer accepter les accusés de réception.<br />-   **NOU**. Sélectionnez cette option si vous ne souhaitez pas envoyer accepter les accusés de réception.<br />-   **SU**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception uniquement en cas d’erreur.|  
    |**Type d’accusé de réception MSH Application 16**|Sélectionnez l'une des options suivantes :<br /><br /> -   **AL**. Sélectionnez cette option si vous souhaitez toujours envoyer les accusés de réception application.<br />-   **NOU**. Sélectionnez cette option si vous ne souhaitez pas envoyer les accusés de réception application.<br />-   **SU**. Sélectionnez cette option si vous souhaitez envoyer des accusés de réception application après la transmission réussie d’un message.<br /><br /> **ER**. Sélectionnez cette option si vous souhaitez envoyer des accusés de réception application uniquement en cas d’erreur.|  
    |**MSH1 – séparateur de champs**|Entrez un caractère unique comme un séparateur de champs. La valeur par défaut est une barre verticale (**&#124;**), et le nombre maximal de caractères autorisé est un caractère. Notez que si vous devez modifier MSH1, vous devez utiliser une orchestration qui écrit la valeur appropriée de MSH1 à votre contexte de message HL7. Le sérialiseur BTAHL7 lit la valeur à partir du contexte et l’utilise dans le message sérialisé.|  
    |**Où MSH2 a été – codage de caractères**|Type de caractères uniques comme les codage des caractères conformément à la norme HL7. La valeur par défaut de codage de caractères est ^, ~, \\, et &. Le minimum de caractères requis sont deux caractères, et la valeur maximale autorisée sont les quatre caractères. Notez que si MSH2_3 ou MSH2_4 (le d’échappement et le sous-composant dynamique délimiteurs) ne sont pas spécifiés dans votre message d’origine, le message d’accusé de réception remplit automatiquement les champs. Par exemple, si le segment de message MSH d’origine est `MSH&#124;^~&#124;`, sachant seulement les séparateurs de composant et de répétition sont spécifiés, le message d’accusé de réception renseigne automatiquement ce champ pour inclure le troisième et quatrième composant en tant que `MSH&#124;^~\&` si ces valeurs n’étaient pas configurés dans les sections de l’accusé de réception dans l’Explorateur de Configuration BTAHL7.|  
    |**MSH 3**|Tapez les valeurs de champ pour les accusés de réception générés pour l’application émettrice. La longueur maximale autorisée de 180 caractères collectivement.<br /><br /> Lorsque ne pas configurée, les accusés de réception générés contiennent entrant **MSH5** valeur du message. **Remarque :** cette option s’applique uniquement aux messages 2.X. **Remarque :** pour remplacer la valeur existante pour la valeur null, tapez  **\\** .|  
    |**MSH 5**|Tapez les valeurs de champ pour les accusés de réception générés pour l’application de destination. La longueur maximale autorisée de 180 caractères collectivement.<br /><br /> Lorsque ne pas configurée, les accusés de réception générés contiennent entrant **MSH3** valeur du message. **Remarque :** cette option s’applique uniquement aux messages 2.X. **Remarque :** pour remplacer la valeur existante pour la valeur null, tapez  **\\** .|  
    |**MSH8 – sécurité**|Tapez un caractère de sécurité facultatif.|  
    |**MSH 9**|Tapez les valeurs de champ pour le type de message généré accusés de réception.<br /><br /> Lorsque ne pas configurée, les accusés de réception générés contiennent entrant **MSH9** valeur du message. **Remarque :** cette option s’applique uniquement aux messages 2.X. **Remarque :** pour remplacer la valeur existante pour la valeur null, tapez  **\\** .|  
    |**MSH15 : acceptez le Type d’accusé de réception**|Sélectionnez parmi les options suivantes pour le type d’accusé de réception accepte :<br /><br /> -   **AL**. Sélectionnez cette option si vous souhaitez toujours envoyer accepter les accusés de réception.<br />-   **NOU**. Sélectionnez cette option si vous ne souhaitez pas envoyer accepter les accusés de réception.<br />-   **SU**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception uniquement en cas d’erreur.|  
    |**En cas de réussite**|Tapez le texte pour un accusé de réception statique pour une remise des messages de réussite.|  
    |**En cas d’échec**|Tapez le texte pour un accusé de réception statique pour une remise des messages ayant échoué.|  
    |**Port d’envoi de router les ACK vers le pipeline d’envoi de requête-réponse**|Sélectionnez cette option pour envoyer un message d’accusé de réception synchrone pour l’application métier source. Cette option est uniquement disponible sur un port d’envoi de sollicitation-réponse.<br /><br /> Si cette option n’est pas sélectionnée, le pipeline de réception génère le message d’accusé de réception en fonction de vos paramètres d’accusé de réception.|  
  
2.  Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de Configuration de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/ack-configuration-settings.md)   
 [Paramètres de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md)   
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)