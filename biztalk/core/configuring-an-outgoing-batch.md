---
title: "Configuration d’un lot sortant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75e6f41a-0e24-47bf-9234-125791c62044
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de6b7ef0a8683374322d4b6f720bc1ebd1ed4b06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-an-outgoing-batch"></a>Configuration d'un lot sortant
Pour définir la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] regroupe les documents informatisés en un échange EDI, vous devez créer une ou plusieurs configurations de lot pour un accord. Tous les échanges que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] associe à cet accord et qui répondent aux critères de filtre d'un lot sont traités par lot et déclenchés selon les critères de déclenchement de cette configuration de lot.  
  
 La configuration de lot est constituée des éléments suivants : nom du lot, ID du lot, définition du filtre, définition du groupe, critères de déclenchement du lot et critères d'activation du lot. Toutes les propriétés et les options relatives aux lots sont disponibles sur le **Configuration de lot** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue. Pour créer une configuration de lot pour un accord, consultez [configurer le traitement par lot (X12)](../core/configuring-batching-x12.md).  
  
> [!NOTE]
>  La norme de document du lot est déterminée par les propriétés d'accord. Par exemple, si l'accord concerne des messages X12, la norme de document des lots est x12.  
  
## <a name="batch-categories"></a>Catégories de lots  
 Utilisez la liste déroulante dans le coin supérieur droit de la **Configuration de lot** page pour déterminer les configurations de lot sont affichées.  
  
-   **Tous les**: affiche toutes les configurations de lot.  
  
-   **Active**: affiche uniquement les configurations de lot actives.  
  
-   **Inactif**: affiche uniquement les configurations de lot inactives.  
  
## <a name="batch-identification"></a>Identification du lot  
 L'identification du lot inclut le nom du lot, la description, l'ID du lot et l'ID d'instance de l'orchestration de traitement par lot.  
  
### <a name="batch-name"></a>Nom du lot  
 Une configuration de lot est créée en fonction du nom de lot spécifié dans **Configuration de lot** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue. Bien que plusieurs lots puissent partager les mêmes paramètres de configuration, ils doivent posséder un nom unique.  
  
### <a name="batch-description"></a>Description du lot  
 La zone de texte Description du lot fournit une description de la configuration de lot.  
  
### <a name="batch-id"></a>ID de lot  
 L’ID de lot est généré automatiquement par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lorsqu’une nouvelle configuration de lot est créée dans le **Configuration de lot** page. Cette valeur est utilisée par le composant de pipeline BatchMarker pour baliser les échanges entrants correspondant au filtre par lot d'une configuration de lot spécifique. Elle sert également de filtre d'abonnement de l'orchestration de traitement par lot associée à une configuration de lot spécifique.  
  
### <a name="orchestration-instance-id"></a>ID d’Instance d’orchestration  
 ID d'instance de l'orchestration de traitement par lot activée pour cette configuration de lot.  
  
## <a name="batch-filter"></a>Filtre par lot  
 Un lot est créé en fonction de la définition de filtre de lot appliquée dans le **Configuration de lot** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue. Dans ce filtre, vous déterminez les documents informatisés ou messages traités par lot. Vous pouvez modifier la valeur de ce filtre alors qu'une instance de l'orchestration de traitement par lot est activée. La modification du filtre n'affecte pas les critères de déclenchement du lot.  
  
> [!NOTE]
>  Si vous modifiez le filtre par lot d'un lot actif, 15 minutes seront nécessaires pour que les nouveaux critères de filtre deviennent actifs car ces informations sont mises en cache par BizTalk Server. Cet intervalle d’actualisation ne peut pas être modifié.  
>   
>  Pour que le filtre devienne actif immédiatement, redémarrez le processus hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Les lots sortants peuvent inclure plusieurs groupes mais seul un groupe est autorisé par type de transaction. Un groupe peut contenir plusieurs documents informatisés, mais ceux-ci doivent correspondre au même type de transaction.  
  
 Plusieurs configurations de lot peuvent partager le même filtre par lot. Si un document correspond à plusieurs filtres par lot, il est acheminé vers tous les lots correspondants.  
  
## <a name="group-definition"></a>Définition du groupe  
 Vous pouvez déterminer la composition des groupes dans la sortie du lot en définissant les en-têtes de groupe fonctionnel (GS pour X12 et UNG pour EDIFACT) dans les propriétés de l'accord. Les groupes sont définis en fonction de leur identificateur de document informatisé (ST1) pour X12 ou du type de message (UNH2.1) pour EDIFACT, de leur version et de leur espace de noms cible. Par exemple, un échange peut contenir un premier groupe composé d'un type de message spécifique et un deuxième groupe constitué d'un autre type de message. Pour plus d’informations sur la configuration des groupes, consultez [configuration des propriétés EDI](../core/configuring-edi-properties.md).  
  
> [!NOTE]
>  L'ordre des groupes au sein d'un échange n'est pas défini.  
  
## <a name="batch-release-criteria"></a>Critères de déclenchement du lot  
 Lots sont déclenchés en fonction de critères définis le **Configuration de lot** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue. Ils peuvent être déclenchés de l'une des manières suivantes :  
  
-   en fonction d'une planification, sur une base horaire, quotidienne ou hebdomadaire ;  
  
-   lorsqu'un nombre spécifique de documents informatisés est disponible dans un groupe ;  
  
-   lorsqu'un nombre spécifique de documents informatisés est disponible pour un échange ;  
  
-   lorsqu'un nombre spécifique de caractères est disponible pour un traitement par lot ;  
  
-   lorsqu'un déclencheur externe est exécuté par une application externe à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Si vous sélectionnez le **alerte signalant un lot vide envoi** propriété sur le **planification par lot** boîte de dialogue, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie un message de lot vide lorsque le lot est planifié pour être envoyé même si aucun message n’ont pas été reçu par l’orchestration de traitement par lot.  
  
## <a name="batch-activation-criteria"></a>Critères d'activation du lot  
 Les lots sont déclenchés en fonction des critères de déclenchement du lot uniquement lorsque le critère d'activation du lot a été satisfait. Pour activer une instance d’orchestration, vous devez appuyer sur la **Démarrer** situé dans le **Configuration de lot** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord**boîte de dialogue. Cette action crée une instance de l'orchestration pour la configuration de lot. Si le **Démarrer** bouton est disponible, une instance de l’orchestration pour la configuration de lot n’est pas activée actuellement.  
  
 Après avoir appuyé sur le **Démarrer** bouton, les messages seront collectés pour un lot uniquement si les conditions suivantes sont remplies :  
  
-   Les messages satisfont les critères du filtre par lot.  
  
-   Date et heure sont postérieures à celles entrées dans le **Démarrer** champ.  
  
-   La date et l’heure sont antérieures à celles entrées dans le **se terminer par** champ ou le nombre de lots traités est inférieur ou égal au nombre d’occurrences dans le **fin après (occurrences)** d’un champ ou la  **Aucune date de fin** option est sélectionnée. Les trois options sont disponibles sous les **arrêt** section.  
  
 Les critères d’activation sont définies le **Configuration de lot** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.  
  
 Une fois que vous avez appuyé sur le **Démarrer** bouton pour activer une instance de l’orchestration de traitement par lot, les messages ne seront pas collectées pour un lot jusqu'à ce que l’heure mentionnée pour le **Démarrer** propriété est dépassée.  Dans le **Configuration de lot** page, si **démarrer immédiatement** n’est pas sélectionnée et les **Démarrer** datetime est définie sur une valeur antérieure à l’heure à laquelle vous appuyez sur la **Démarrer** bouton, le traitement par lot commencera dès que l’orchestration est activée. Si les date et heure d'activation sont situées dans le futur, le traitement par lot commencera à cette heure.  
  
 Vous pouvez définir le **Démarrer** datetime pour être une valeur datetime dans le futur. Toutefois, si vous cliquez sur le **Démarrer** bouton lorsque le **Démarrer** datetime est dans le futur, l’instance d’orchestration sera activée, mais aucun message ne sera collecté jusqu'à ce que la valeur datetime de début se produit. Le composant de pipeline BatchMarker n'assurera pas la promotion des propriétés appropriées nécessaires à l'orchestration de routage ou de traitement par lot tant que les date et heure définies pour l'option Démarrer ne seront pas atteintes. Par conséquent, les messages ne seront pas traités par lot. Toutefois, ils seront récupérés par un port d'envoi ou une orchestration abonnée en tant que messages individuels. Pour plus d’informations sur ce que fait le composant de pipeline BatchMarker, consultez [assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md).  
  
## <a name="batch-termination-criteria"></a>Critères d'arrêt du lot  
 Messages cessera d’être collectées pour un lot après le **se terminer par** datetime ou après le nombre d’occurrences dans le **fin après (occurrences)** propriété. Si vous ne souhaitez pas que l’orchestration de traitement par lot doit être désactivé, sélectionnez le **aucune date de fin** option.  
  
> [!NOTE]
>  Si le **fin après (occurrences)** propriété a été sélectionnée, lot vide signale le nombre d’occurrences requises à la fin de la plage de l’activation du lot sont comptabilisées. Le nombre d'occurrences est également incrémenté si les conditions qui génèrent habituellement une alerte signalant un lot vide se produisent (aucun message reçu par l'orchestration de traitement par lot lorsque l'envoi du lot est planifié), mais aucune alerte signalant un lot vide n'est envoyée car le signal n'est pas configuré.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement par lot des Messages EDI sortants](../core/batching-outgoing-edi-messages.md)