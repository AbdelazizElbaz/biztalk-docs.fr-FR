---
title: "Configurer le traitement par lot des accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, acknowledgements
- acknowledgements, batching
ms.assetid: f3529638-e036-4270-ae6d-1bdc3ef98727
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60e6c9b3a6fadfcc0407c1b4fa206d0f966fa7dd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-batching-acknowledgments"></a>Configuration des accusés de réception de traitement par lot
Vous utilisez [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Explorer de Configuration pour spécifier les propriétés de l’accusé de réception pour les accusés de réception entrants et générés.  
  
### <a name="to-run-btahl7-configuration-explorer"></a>Pour exécuter l’Explorateur de Configuration de BTAHL7  
  
-   Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis cliquez sur  **BTAHL7 L’Explorateur de Configuration**.  
  
### <a name="to-configure-message-batching-acknowledgments"></a>Pour configurer le traitement par lot des accusés de réception de message  
  
-   Dans l’Explorateur de Configuration de BTAHL7, dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **Parties** , sélectionnez la partie que vous souhaitez configurer, puis, dans le **d’accusésderéception** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Type d’accusé de réception**|Sélectionnez l'une des options suivantes :<br /><br /> -   **None**. Sélectionnez si vous ne souhaitez pas configurer les accusés de réception.<br />-   **OriginalMode**. Sélectionnez cette option pour configurer le **MSH1-séparateur de champs**, **où MSH2 a été – l’encodage de caractères**, et **MSH8 – sécurité** options uniquement.<br />-   **EnhancedMode**. Sélectionnez cette option pour configurer toutes les options disponibles d’accusé de réception.<br />-   **DeferredMode**. Sélectionnez cette option pour configurer le **MSH1-séparateur de champs**, **où MSH2 a été – l’encodage de caractères**, et **MSH8 – sécurité** options uniquement.<br />-   **StaticMode**. Sélectionnez cette option pour configurer le **en cas de réussite** et **en cas d’échec** options d’accusé de réception.|  
    |**MSH 15 accepter le Type d’accusé de réception**|Sélectionnez l'une des options suivantes :<br /><br /> -   **AL**. Sélectionnez cette option pour toujours envoyer accepte des accusés de réception.<br />-   **NOU**. Sélectionnez cette option pour ne jamais envoyer accepte des accusés de réception.<br />-   **SU**. Sélectionnez cette option pour envoyer accepte les accusés de réception après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option pour envoyer accepte les accusés de réception uniquement en cas d’erreur.|  
    |**Type d’accusé de réception MSH Application 15**|Sélectionnez l'une des options suivantes :<br /><br /> -   **AL**. Sélectionnez cette option pour toujours envoyer les accusés de réception application.<br />-   **NOU**. Sélectionnez cette option pour ne jamais envoyer les accusés de réception application.<br />-   **SU**. Sélectionnez cette option pour envoyer des accusés de réception application après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option pour envoyer des accusés de réception application uniquement en cas d’erreur.|  
    |**MSH1 – séparateur de champs**|Entrez un caractère unique comme un séparateur de champs. La valeur par défaut est une barre verticale (**&#124;**), et le nombre maximal de caractères autorisé est un caractère. Notez que si vous devez modifier MSH1, vous devez utiliser une orchestration qui écrit la valeur appropriée de MSH1 à votre contexte de message HL7. Le sérialiseur BTAHL7 lit la valeur à partir du contexte et l’utilise dans le message sérialisé.|  
    |**Où MSH2 a été – codage de caractères**|Type de caractères uniques comme les codage des caractères conformément à la norme HL7. La valeur par défaut de codage de caractères est ^, ~, \\, et &. Le minimum de caractères requis sont deux caractères, et la valeur maximale autorisée sont les quatre caractères. Notez que si MSH2_3 ou MSH2_4 (le d’échappement et le sous-composant dynamique délimiteurs) ne sont pas spécifiés dans votre message d’origine, le message d’accusé de réception (ACK) renseigne automatiquement ces champs. Par exemple, si le segment de message MSH d’origine est `MSH&#124;^~&#124;`, sachant seulement les séparateurs de composant et de répétition sont spécifiés, le message d’accusé de réception renseigne automatiquement ce champ pour inclure le troisième et quatrième composant en tant que `MSH&#124;^~\&`, en fournissant que les valeurs de champ n'avaient pas déjà été configurés dans la section de l’accusé de réception dans l’Explorateur de Configuration BTAHL7.|  
    |**MSH3**|Tapez les valeurs de champ pour les accusés de réception générés pour l’application émettrice. La longueur maximale autorisée est de 180 caractères collectivement.<br /><br /> Lorsque ne pas configurée, les accusés de réception générés contiennent entrant **MSH5** une valeur de message. **Remarque :** cette option s’applique uniquement aux messages 2.X. **Remarque :** pour remplacer la valeur existante pour la valeur null, tapez  **\\** .|  
    |**MSH5**|Tapez les valeurs de champ pour les accusés de réception générés pour l’application de destination. La longueur maximale autorisée est de 180 caractères collectivement.<br /><br /> Lorsque ne pas configurée, les accusés de réception générés contiennent entrant **MSH3** une valeur de message. **Remarque :** cette option s’applique uniquement aux messages 2.X. **Remarque :** pour remplacer la valeur existante pour la valeur null, tapez  **\\** .|  
    |**MSH8 – sécurité**|Tapez un caractère de sécurité facultatif.|  
    |**MSH15 : acceptez le Type d’accusé de réception**|Sélectionnez parmi les options suivantes pour le type d’accusé de réception accepte :<br /><br /> -   **AL**. Sélectionnez si vous souhaitez toujours envoyer accepter des accusés de réception.<br />-   **NOU**. Sélectionnez si vous ne souhaitez pas envoyer accepter des accusés de réception.<br />-   **SU**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception uniquement en cas d’erreur.|  
    |**En cas de réussite**|Tapez le texte d’accusé de réception statique pour une remise des messages de réussite.|  
    |**En cas d’échec**|Tapez le texte de l’accusé de réception statique pour une remise des messages ayant échoué.|  
    |**Port d’envoi de router les ACK vers le pipeline d’envoi de requête-réponse**|Sélectionnez cette option pour envoyer un message d’accusé de réception synchrone pour l’application métier source. Cette option est uniquement disponible sur un port d’envoi de sollicitation-réponse.<br /><br /> Si cette option n’est pas sélectionnée, le pipeline de réception génère le message d’accusé de réception en fonction de vos paramètres d’accusé de réception.|  
  
    > [!NOTE]
    >  Accusés de réception générés pour un lot de messages avec la fragmentation mises hors tension contiendra MSH12.1 avec la valeur 2.4. Vous pouvez modifier manuellement le numéro de version en appliquant un mappage dans le pipeline d’envoi. Pour plus d’informations, consultez [création et traiter les accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du traitement par lot](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)