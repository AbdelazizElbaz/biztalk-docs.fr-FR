---
title: Configuration de traitement par lot (X12) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f4f9e7b-262d-488e-9a04-088aad289d70
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7912aad3610b7c05ddc0db37f6c7989be3bc04a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-batching-x12"></a>Configuration du traitement par lot (X12)
Les lots définissent la méthode utilisée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]pour générer et envoyer des lots EDI au tiers.  
  
> [!NOTE]
>  Les paramètres décrits dans cette rubrique s'appliquent également aux échanges HIPAA.  
  
> [!IMPORTANT]
>  Toutes les propriétés sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord. Le **nouveau lot** bouton est désactivé sur cette page.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, le **nouveau lot** bouton est désactivé sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-batching-settings"></a>Pour configurer les paramètres de traitement par lot  
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **le traitement par lot de Configuration**.  
  
3.  À partir de la **Configuration de lot** page, cliquez sur **nouveau lot** pour créer une nouvelle configuration de lot. A **LOT1** onglet est ajouté.  
  
4.  Dans le **Identification** section de l’onglet procédez comme suit :  
  
    1.  Entrez le **lot** nom. Cette valeur est utilisée comme identificateur d'onglet pour cette configuration de lot.  
  
    2.  Entrez une description de cette configuration de lot dans **description du lot**.  
  
    3.  **ID de lot** est une zone de texte en lecture seule qui affiche l’ID de lot unique après avoir appliqué les paramètres pour le lot.  
  
    4.  **ID d’instance d’orchestration** est une zone de texte en lecture seule qui affiche l’ID d’instance d’orchestration traitement par lot auquel le lot est associé. Un ID d'instance de l'orchestration s'affiche après le démarrage d'un lot.  
  
5.  Dans le **filtre** section de l’onglet procédez comme suit :  
  
    1.  Cliquez sur **filtre**.  
  
    2.  Dans le **filtre par lot** boîte de dialogue, entrez la propriété, opérateur et valeurs pour créer le filtre d’abonnement pour l’orchestration de traitement par lot. Ces clauses de filtre déterminent les documents informatisés que l'orchestration de routage va router vers la MessageBox pour le traitement par lot.  
  
        > [!NOTE]
        >  Pour spécifier que tous les messages vers un groupe seront mis par lot, définissez la propriété de tiers dans le filtre du lot sur le nom du tiers.  
  
        > [!NOTE]
        >  Pour plus d’informations sur le processus de traitement par lot, consultez [assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md).  
  
    3.  Pour supprimer une ligne, sélectionnez la ligne, puis cliquez sur **supprimer**.  
  
    4.  Pour déplacer une ligne vers le haut ou vers le bas, cliquez sur le **monter** ou **Descendre** boutons.  
  
6.  Dans le **version** section de l’onglet procédez comme suit :  
  
    1.  Sélectionnez **planification** pour créer et envoyer un lot selon une planification prédéterminée. Pour définir la planification, cliquez sur **planificateur** et puis procédez comme suit :  
  
        > [!NOTE]
        >  La planification par lot peut être affectée par des événements spéciaux. Exemple : le passage à l'heure d'été. Si un lot est censé être traité toutes les heures moins d'une heure après le passage à l'heure d'été, ce lot n'est pas créé ni envoyé après l'avancement des horloges. Vous pouvez compenser ce décalage des événements spéciaux qui entraînent un traitement du lot en cliquant sur le **Démarrer** bouton sur le **lots** page pour démarrer l’orchestration de traitement par lot manuellement. Il est parfois nécessaire d'arrêter le traitement d'un lot dupliqué.  
  
        -   Pour envoyer un lot toutes les heures, sélectionnez **toutes les heures**. Dans la liste déroulante pour **premier déclenchement**, sélectionnez la date de la première version du lot, puis entrez l’heure. Pour **déclenchements chaque**, sélectionnez dans la liste déroulante si la période est définie en **heures** ou **Minutes**, puis entrez le nombre d’heures ou minutes seront Séparez chaque lot.  
  
        -   Pour envoyer un lot sur une base quotidienne, sélectionnez **quotidienne**. Dans la liste déroulante pour **premier déclenchement**, sélectionnez la date de la première version du lot, puis entrez l’heure. Pour **déclenchements chaque**, entrez le nombre de jours entre chaque lot.  
  
        -   Pour envoyer un lot sur une base hebdomadaire, sélectionnez **hebdomadaire**. Dans la liste déroulante pour **premier déclenchement**, sélectionnez la date de la première version du lot, puis entrez l’heure. Pour **déclenchements chaque**, entrez le nombre de semaines entre la semaine du premier déclenchement et de la semaine du déclenchement suivant. Sélectionnez ensuite les jours de la semaine auxquels le lot sera déclenché.  
  
            > [!NOTE]
            >  Le premier déclenchement sera effectué à la date et définir dans le **premier déclenchement** champ, même si ce jour de la semaine n’a pas été sélectionné dans la boîte de dialogue.  
  
            > [!NOTE]
            >  Si vous avez sélectionné un ou plusieurs jours de la semaine dans la boîte de dialogue, une mise en production sera effectué le jour de la semaine qui vient après la première version. Par exemple, si lundi et vendredi ont été sélectionnés et que le premier déclenchement a eu lieu un mercredi, un autre déclenchement sera effectué le vendredi de la première semaine. Les versions ultérieures se produira  *n*  semaines après la première semaine, avec  *n*  déterminée par la valeur dans la **déclenchements chaque** champ. Un déclenchement aura lieu chaque jour de la semaine sélectionné dans la boîte de dialogue.  
  
        -   Sélectionnez **alerte signalant un lot vide envoi** pour envoyer une alerte signalant un lot vide si aucun message n’a été reçu par l’orchestration de traitement par lot lorsque le lot est planifié pour être envoyé.  
  
    2.  Sélectionnez **nombre maximal de transaction définit** pour créer et envoyer un lot chaque fois qu’un certain nombre de documents informatisés ou messages ait été routé vers la MessageBox pour le traitement par lot. Sélectionnez la partie du message concernée (soit **groupe** ou **échange**), puis entrez le nombre maximal de documents informatisés à inclure dans le groupe traité par lot ou l’échange.  
  
         Par exemple, si vous souhaitez traiter par lot deux échanges par lot sélectionnez **échange** à partir de la liste déroulante et entrez `2` dans la zone de texte.  
  
    3.  Sélectionnez **nombre maximal de caractères dans un échange** pour créer et envoyer un lot lorsqu’un nombre spécifique de caractères est disponible pour le traitement par lots. Entrez le nombre maximal de caractères dans le groupe ou l'échange traité par lot.  
  
         L'orchestration de traitement par lot cumule les éléments de lot jusqu'à ce que le nombre de caractères dans ces éléments (moins le nombre dans l'enveloppe) dépasse le nombre maximal. Il traite ensuite tous les éléments par lot, à l'exception du dernier élément (qui a provoqué le dépassement du nombre maximal).  
  
        > [!NOTE]
        >  Pour le nombre maximal de caractères, entrez un nombre suffisamment grand pour générer des lots significatifs. Ce nombre doit être au moins supérieur au nombre total de caractères dans les en-têtes et au nombre maximal de caractères dans un message. Un nombre trop petit pourrait donner lieu à des lots vides.  
  
    4.  Sélectionnez **déclencheur externe** à créer, puis envoyer un lot lorsqu’un déclencheur externe est exécuté par une application externe à BizTalk Server. Pour plus d’informations sur la façon de configurer ce mécanisme, consultez [implémenter un mécanisme de déclenchement de lot externe](../core/implementing-an-external-batch-release-mechanism.md).  
  
        > [!NOTE]
        >  Le **remplacer** bouton et **plage d’Activation** contrôles restent valides si la **déclenchement externe** propriété déclencheur a été sélectionnée.  
  
7.  Dans le **Activation** section de l’onglet procédez comme suit :  
  
    1.  Sélectionnez **démarrer immédiatement** pour que le traitement par lot, orchestration commence le traitement par lot des messages immédiatement.  
  
         Pour démarrer l’orchestration de traitement par lot sur une date spécifique, désactivez la **démarrer immédiatement** zone et sélectionnez une date et heure pour activer l’orchestration de traitement par lot.  
  
8.  Dans le **arrêt** section de l’onglet procédez comme suit :  
  
    1.  Conserver **aucune date de fin** sélectionné si vous ne souhaitez pas spécifier une date de fin de l’orchestration de traitement par lot doit être désactivé.  
  
    2.  Sélectionnez **fin après (occurrences)** pour spécifier que l’orchestration de traitement par lot sera désactivée après un certain nombre de lots ont été généré. Entrez le nombre désiré dans la zone de texte.  
  
    3.  Sélectionnez **se terminer par** pour spécifier une date de fin, l’orchestration de traitement par lot sera désactivée. Les messages ne seront pas collectés pour le traitement par lot après l'heure définie. Sélectionnez une date de fin dans le calendrier ou modifiez la date ou l'heure directement dans la zone de texte.  
  
9. Cliquez sur **appliquer** pour appliquer les paramètres de lot que vous avez fournies dans les étapes précédentes. Après avoir cliqué sur **appliquer**, un code de lot est créé et s’affiche dans le **ID de lot** champ de texte dans le **Identification** section.  
  
    > [!NOTE]
    >  Un message **le traitement par lot n’est pas activé** s’affiche sous le **Démarrer** bouton.  
  
10. Cliquez sur **Démarrer** pour activer une orchestration de traitement par lot manuellement.  
  
    > [!NOTE]
    >  Pour vous assurer que l’orchestration de traitement par lot sera rapidement activée lorsque vous cliquez sur le **Démarrer** et mettre à jour l’intervalle d’interrogation pour l’emplacement de réception de l’adaptateur SQL dans le BatchControlMessageReccvLoc. Pour plus d’informations, consultez [procédure pas à pas (X12) : envoi d’échanges traités par lot EDI](../core/walkthrough-x12-sending-batched-edi-interchanges.md).  
  
    > [!NOTE]
    >  Après avoir cliqué sur **Démarrer**, cliquez sur **Actualiser**. L'association du lot à l'instance d'orchestration peut prendre un certain temps. Si vous cliquez sur **Actualiser** avant que le lot est associé à l’orchestration, vous voyez le message **le traitement par lots est activé, l’orchestration ne pas encore instanciée**. Cliquez sur **Actualiser** pour pouvoir voir les ID d’instance de l’orchestration associée dans le **ID d’instance d’Orchestration** zone de texte. Le message **le traitement par lots est activé** est affiché sous la **Démarrer** bouton.  
  
11. Cliquez sur **remplacer** à force l’orchestration de traitement par lot pour envoyer un lot, ou non les critères de déclenchement ont été remplies. L'utilisation de cette option remplace les critères de lot existants, un lot étant créé à l'aide des éléments existants, puis immédiatement envoyé. Une fois cette opération terminée, l'orchestration reprend le traitement par lot conformément aux paramètres définis.  
  
12. Cliquez sur **arrêter** pour mettre fin à une orchestration de traitement par lot active sans envoyer un lot et désactiver l’orchestration de traitement par lot manuellement.  
  
13. Cliquez sur **Actualiser** pour actualiser l’état de l’orchestration de traitement par lot.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la liste déroulante en haut de **la Configuration de lot** page pour filtrer les onglets de configuration de lot affichés en sélectionnant **tous les** (pour afficher des onglets pour tous les lots), **Active** (pour afficher les onglets des lots actifs), ou **inactif** (pour afficher les onglets des lots inactifs).  
  
    > [!NOTE]
    >  Si vous modifiez les paramètres de configuration pendant que l'orchestration traite un lot, les nouveaux paramètres ne seront pas appliqués à ce lot. Cela peut donner lieu à des erreurs de validation dans le pipeline d'envoi.  
  
    > [!NOTE]
    >  Pour accélérer l'activation du tiers d'orchestration de traitement par lot sur un serveur de développement, vous pouvez réduire l'intervalle d'interrogation pour l'emplacement de réception de l'adaptateur SQL de traitement par lot (BatchControlMessageRecvLoc) sur ce serveur. Nous vous recommandons de que définir l’intervalle d’interrogation pour un serveur de développement à 30 secondes.  
  
14. Cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (X12)](../core/configuring-interchange-settings-x12.md)   
 [Configuration d’un lot sortant](../core/configuring-an-outgoing-batch.md)   
 [Assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md)   
 [Implémentation d’un mécanisme de déclenchement externe du lot](../core/implementing-an-external-batch-release-mechanism.md)