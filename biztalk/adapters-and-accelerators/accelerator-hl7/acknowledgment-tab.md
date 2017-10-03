---
title: "Onglet d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: btahl7.configurationexplorer.tab.acknowledgement
helpviewer_keywords:
- acknowledgements, configuring
- Acknowledgement tab [Configuration Explorer]
- configuring, acknowledgements
ms.assetid: f00d698c-1a33-4885-853f-c6b58d49d937
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28dcf3d0faee6ebf37a827f3773f33b955ce5447
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgment-tab"></a>Onglet d’accusé de réception
Vous utilisez la **accusé de réception** onglet pour spécifier les propriétés de l’accusé de réception pour les accusés de réception entrants et générés.  
  
 Dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **accusés de réception** onglet, procédez comme suit :  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Type d’accusé de réception**|Sélectionnez l'une des options suivantes :<br /><br /> -   **None**. Sélectionnez cette option si vous ne souhaitez pas configurer les accusés de réception.<br />-   **OriginalMode**. Sélectionnez cette option pour configurer **MSH1-séparateur de champs**, **où MSH2 a été – l’encodage de caractères**et le **MSH8 – sécurité** options uniquement.<br />-   **EnhancedMode**. Sélectionnez cette option pour configurer toutes les options disponibles d’accusé de réception.<br />-   **DeferredMode**. Sélectionnez cette option pour configurer **MSH1-séparateur de champs**, **où MSH2 a été – l’encodage de caractères**et le **MSH8 – sécurité** options uniquement.<br />-   **StaticMode**. Sélectionnez cette option pour configurer le **en cas de réussite** et **en cas d’échec** options d’accusé de réception.|  
|**MSH 15 accepter le Type d’accusé de réception**|Sélectionnez l'une des options suivantes :<br /><br /> -   **AL**. Sélectionnez cette option si vous souhaitez toujours envoyer accepter les accusés de réception.<br />-   **NOU**. Sélectionnez cette option si vous ne souhaitez pas envoyer accepter les accusés de réception.<br />-   **SU**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception uniquement en cas d’erreur.|  
|**Type d’accusé de réception MSH Application 16**|Sélectionnez l'une des options suivantes :<br /><br /> -   **AL**. Sélectionnez cette option si vous souhaitez toujours envoyer les accusés de réception application.<br />-   **NOU**. Sélectionnez cette option si vous ne souhaitez pas envoyer les accusés de réception application.<br />-   **SU**. Sélectionnez cette option si vous souhaitez envoyer des accusés de réception application après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option si vous souhaitez envoyer des accusés de réception application uniquement en cas d’erreur.|  
|**MSH1 – séparateur de champs**|Entrez un caractère unique comme un séparateur de champs. La valeur par défaut est **&#124;**, et le nombre maximal de caractères autorisé est un caractère. Notez que si vous devez modifier MSH1, vous devez utiliser une orchestration qui écrit la valeur appropriée de MSH1 à votre contexte de message HL7. Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur lit la valeur à partir du contexte et l’utilise dans le message sérialisé.|  
|**Où MSH2 a été – codage de caractères**|Tapez les caractères uniques pour les caractères de codage conformément aux spécifications HL7. La valeur par défaut de codage de caractères est ^, ~, \\, et &. Le minimum de caractères requis sont deux caractères, et la valeur maximale autorisée sont les quatre caractères. Notez que si MSH2_3 ou MSH2_4 (le d’échappement et le sous-composant dynamique délimiteurs) ne sont pas spécifiés dans votre message d’origine, le message d’accusé de réception remplit automatiquement les champs. Par exemple, si le segment de message MSH d’origine est `MSH&#124;^~&#124;`, sachant seulement les séparateurs de composant et de répétition sont spécifiés, le message d’accusé de réception renseigne automatiquement ce champ pour inclure le troisième et quatrième composant en tant que `MSH&#124;^~\&` si ces valeurs non configurés dans les sections de l’accusé de réception de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.|  
|**MSH 3**|Tapez les valeurs de champ pour les accusés de réception générés pour l’application émettrice. La longueur maximale autorisée est de 180 caractères collectivement.<br /><br /> Lorsque ne pas configurée, les accusés de réception générés contiennent entrant **MSH5** une valeur de message. **Remarque :** cette option s’applique uniquement aux messages 2.X. **Remarque :** pour remplacer la valeur existante pour la valeur null, tapez  **\\** .|  
|**MSH 5**|Tapez les valeurs de champ pour les accusés de réception générés pour l’application de destination. La longueur maximale autorisée est de 180 caractères collectivement.<br /><br /> Lorsque ne pas configurée, les accusés de réception générés contiennent entrant **MSH3** une valeur de message. **Remarque :** cette option s’applique uniquement aux messages 2.X. **Remarque :** pour remplacer la valeur existante pour la valeur null, tapez  **\\** .|  
|**MSH8 – sécurité**|Tapez un caractère de sécurité facultatif.|  
|**MSH 9**|Tapez les valeurs de champ pour le type de message généré accusés de réception.<br /><br /> Lorsque ne pas configurée, les accusés de réception générés contiennent entrant **MSH9** une valeur de message. **Remarque :** cette option s’applique uniquement aux messages 2.X. **Remarque :** pour remplacer la valeur existante pour la valeur null, tapez  **\\** .|  
|**MSH15 : acceptez le Type d’accusé de réception**|Sélectionnez parmi les options suivantes pour le type d’accusé de réception accepte :<br /><br /> -   **AL**. Sélectionnez cette option si vous souhaitez toujours envoyer accepter les accusés de réception.<br />-   **NOU**. Sélectionnez cette option si vous ne souhaitez pas envoyer accepter les accusés de réception.<br />-   **SU**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception uniquement en cas d’erreur.|  
|**En cas de réussite**|Tapez le texte pour un accusé de réception statique pour une remise des messages de réussite.|  
|**En cas d’échec**|Tapez le texte pour un accusé de réception statique pour une remise des messages ayant échoué.|  
|**Port d’envoi de router les ACK vers le pipeline d’envoi de requête-réponse**|Sélectionnez cette option pour envoyer un message d’accusé de réception synchrone pour l’application métier source. Cette option est uniquement disponible sur un port d’envoi de sollicitation-réponse.<br /><br /> Si cette option n’est pas sélectionnée, le pipeline de réception génère le message d’accusé de réception en fonction de vos paramètres d’accusé de réception.|