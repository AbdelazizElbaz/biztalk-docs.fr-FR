---
title: "Codes de fin système | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: 2fd49be9-afe8-47c6-a613-fa469faa2126
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0a8c5b7be12a90aa2d31e828298cf7b95834036
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="system-trailers"></a>Système de codes de fin
Codes de fin système transmettent des détails supplémentaires ou spéciales sur les messages SWIFT. Si une des camions premier trois système sont présentes, ils se produisent dans l’ordre suivant. Les codes de fin système restantes peuvent se produire dans n’importe quel ordre.  
  
|Code de fin du code|Nom|  
|------------------|----------|  
|**CHK**|Somme de contrôle|  
|**SYS**|Message d’origine de système|  
|**TNG**|Formation|  
|**PDM**|Messages en double possible|  
|**DLM**|Message différé|  
|**MRF**|Référence du message|  
  
-   **Système provient le code de fin de Message (SYS).** Le message système ou service, qui est généré par un système PLT, a un code de fin SYS. Tous les sollicitée de messages système avec l’identificateur Service 01, contiennent le MIR de la demande et peuvent contenir le temps.  
  
     Le code suivant est un exemple du format de code de fin SYS :  
  
    ```  
    {SYS:[<time><mir>]}  
    ```  
  
-   **& (TNG) le code de fin de la formation de test.** Le code de fin TNG est obligatoire pour les messages FIN et amp (avec l’identificateur Service 01) envoyées par ou remis à un Test et de formation logique Terminal (LT). Ce code de fin a une balise uniquement et aucune valeur.  
  
     Le code suivant est un exemple du format de code de fin TNG :  
  
    ```  
    {TNG:}  
    ```  
  
-   **Code de fin possibles d’émission de doublons (PDE).** La destination du message utilise le code de fin PDE. Il s’applique uniquement aux messages d’utilisateur FIN (avec l’identificateur Service 01) et les catégories de message réservés à la banque de messages. Le système peut contenir plusieurs PDE. Le système ne pas vérifier l’ordre ni restreindre le nombre (à l’exception de la longueur maximale de message).  
  
     Le système accepte les codes PDE correctement mis en forme appliquées aux messages de système de l’utilisateur, mais ne pas les traite. Cela signifie que le système ne vérifie pas si le message d’origine existe. Par conséquent, le système peut traiter une demande de récupération envoyée avec un code de fin PDE à deux reprises, si le système a reçu le message d’origine.  
  
     Le code suivant est un exemple du format de code de fin PDE :  
  
    ```  
    {PDE:[<time><mir>]}  
    where <time><mir> refers to the emission of the previous possible issue  
    ```  
  
-   **Code de fin des messages retardés (DLM).** Le code de fin DLM est ajouté à tous les messages de sortie de l’utilisateur FIN qui ont dépassé leur période de l’obsolescence. Si ce code de fin apparaît dans les messages système amp ou de FIN, vous pouvez l’ignorer. Ce code de fin a une balise uniquement et aucune valeur.  
  
     La période de l’obsolescence est comme suit :  
  
    -   U = 15 minutes  
  
    -   N = 100 minutes  
  
     Le code suivant est un exemple du format de code de fin DLM :  
  
    ```  
    {DLM:}  
    ```  
  
-   **Code de fin de Message en double possibles (PDM).** Le code de fin PDM est ajouté par le système pour un message de sortie (amp et FIN avec l’identificateur Service 01) renvoyés, car une remise préalable n’est peut-être pas valide. Si un système PLT reçoit une demande de rapport avec un code de fin PDM, la réponse a un PDM brut (sans la référence de remise facultatif). Autres PDMs peuvent être ajoutés en raison de tentatives de remise ayant échoué à l’utilisateur.  
  
     Le code suivant est un exemple du format de code de fin PDM :  
  
    ```  
    {PDM:[<time><mor>]}  
    where <time> and the Message Output Reference <mor> are that of the previous attempt  
    ```  
  
-   **Référence (MRF) le code de fin.** Le code de fin MRF spécifie la référence du message du message utilisateur d’origine dans la copie de FIN 096 MT pour les Messages d’établissement centrale.  
  
     Le code suivant est un exemple du format de code de fin MRF :  
  
    ```  
    {MRF:<date><full-time><mir>}  
    where <mir> is that of the original user message whose fields are copied in the MT 096 FIN  
    Copy to Central Institution Message  
    ```  
  
    > [!NOTE]
    >  Le code de fin MRF est spécifique à la copie de FIN et est généré automatiquement dans la copie de FIN 096 MT pour Message Institution centrale. Vous pouvez uniquement utiliser ce code de fin de champ 109 de la copie de FIN 096 MT pour Message Institution centrale pour identifier le 096 MT auquel le 097 MT est une réponse. Le format de la structure MRF est susceptible d’être modifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de schémas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)