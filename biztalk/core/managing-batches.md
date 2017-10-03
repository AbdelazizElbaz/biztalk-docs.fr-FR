---
title: Gestion des traitements | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82755840-4e00-4fed-80e0-1a22b248c0bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4903cf2722f1938ceb1df92c2a3ac2a88fe6d61e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-batches"></a>Gestion des traitements
Comment contrôler manuellement la version de traités par lot des échanges, à l’aide de contrôles en haut de la **Configuration de lot** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue (dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’administration) pour X12 et le codage EDIFACT. Cette opération implique les commandes suivantes :  
  
-   **Démarrage d’un lot**. Active une instance de l’orchestration de traitement par lot. Après avoir sélectionné le **Démarrer** bouton, les éléments de traitement par lot sont collectés lorsque l’instance est dans la plage d’activation.  
  
-   **Remplacement d’un lot**. Crée un lot à l’aide des éléments existants qu’il envoie immédiatement. Une fois le lot envoyé, l'orchestration du traitement par lot reprend le traitement par lot conformément aux paramètres définis.  
  
-   **Arrêt d’un lot**. Désactive une instance activée de l’orchestration de traitement par lot. Après avoir sélectionné le **arrêter** bouton, l’orchestration crée un lot à partir d’éléments de lot existants, transfert l’échange au pipeline d’envoi EDI et s’arrête.  
  
 Les commandes agissent sur une configuration du lot.  
  
 Les actions effectuées par BizTalk lorsque vous appuyez sur la **Démarrer** bouton dépendent les **filtre** critères, **version** critères, et **Activation**paramètres de plage sur le **Configuration de lot** page. Les critères de filtre déterminent les messages qui seront traités par lot. Les critères de déclenchement déterminent les moments d'exécution des lots. Les propriétés des plages d'activation déterminent si une instance activée de l'orchestration de traitement par lot recueillera des éléments pour le traitement par lot. Pour plus d’informations sur ces paramètres, consultez [configuration d’un lot sortant](../core/configuring-an-outgoing-batch.md).  

Cette rubrique vous montre comment démarrer, arrêter, remplacer et supprimer des lots.  

> [!NOTE]
>  Pour obtenir des instructions sur la configuration des lots, consultez [configuration X12 le traitement par lot](../core/configuring-batching-x12.md) ou [le traitement par lot EDIFACT configuration](../core/configuring-batching-edifact.md). 
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Un membre du groupe d'opérateurs B2B [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut démarrer, arrêter ou remplacer un lot, mais ne peut pas modifier de paramètre de configuration associé au traitement par lot. Vous devez être connecté en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour modifier la configuration du lot.  
  
## <a name="start-stop-and-override-batches"></a>Démarrer, arrêter et substituer des lots  
  
1.  Ouvrez  **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, développez le groupe BizTalk, puis sélectionnez **Parties**.  
  
2.  Dans le **tiers et profils d’entreprise** sous le **accords** section, avec le bouton droit de l’accord avec la configuration du lot que vous souhaitez démarrer, arrêter ou remplacer.  
  
3.  Dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord**, sélectionnez le **Configuration de lot** page.  
  
4.  Sur le **Configuration de lot** , sélectionnez l’onglet correspondant au lot que vous souhaitez démarrer, arrêter ou remplacer.  
  
5.  Vérifiez que les critères de filtre, les critères de déclenchement et les propriétés de plages d'activation sont tels qu'ils devraient être.  
  
    > [!NOTE]
    >  Si vous êtes un membre de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe d’opérateurs, mais pas les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs, vous pouvez démarrer, arrêter ou remplacer des lots. Toutefois, vous ne pouvez pas modifier les paramètres de configuration de lot. Les paramètres sont visibles par vous, mais si vous modifiez un paramètre et sélectionnez **OK**, vous obtenez une erreur d’autorisation.  
  
6.  Si une instance de l’orchestration de traitement par lot n’a pas été activée, sélectionnez **Démarrer** pour activer une instance.  
  
    > [!NOTE]
    >  - Vous pouvez indiquer qu’une instance de l’orchestration de traitement par lot n’a pas été activée si le **Démarrer** bouton est activé, et **le traitement par lot n’est pas activé** s’affiche juste en dessous du **Démarrer** contrôle.  
    >  - Si vous avez cliqué sur le **Démarrer** bouton et une instance de l’orchestration de traitement par lot a été activée, mais Aucuns éléments ne sont collectés pour le lot, puis vérifiez que la valeur datetime dans le **Activation** zone de texte a été dépassé. Si ce n’est pas le cas, le **Activation** date doit être définie à la date actuelle ou une version antérieure.  
  
7.  Pour envoyer un échange par lot lorsque les critères de déclenchement n’ont pas été remplies, sélectionnez **remplacer**.  
  
    > [!NOTE]
    >  En sélectionnant **remplacer** aboutit à un échange par lot envoyé, mais n’affecte pas l’état d’activation de l’instance d’orchestration de traitement par lot, les critères d’activation ou les critères de déclenchement.  
  
8.  Pour désactiver l’instance de l’orchestration de traitement par lot, sélectionnez **arrêter**.  
  
    > [!NOTE]
    >  En sélectionnant **arrêter** provoque un échange par lot envoyé et l’instance d’orchestration par lot en cours d’arrêt.  
  
9. Sélectionnez **OK** ou **Annuler** pour fermer la **propriétés de l’accord**.  

## <a name="delete-batches"></a>Supprimer des lots  
  
1.  Dans  **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, sélectionnez **Parties**.  
  
2.  Dans le **tiers et profils d’entreprise** sous le **accords** section, avec le bouton droit de l’accord avec la configuration du lot que vous souhaitez supprimer.  
  
3.  Dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue, sélectionnez le **Configuration de lot** page.  
  
4.  Sur le **Configuration de lot** , sélectionnez l’onglet correspondant au lot que vous souhaitez supprimer.  
  
5.  Dans le coin droit de la page d’onglet, sélectionnez **supprimer**.  
  
6.  Sélectionnez **OK** pour fermer la **propriétés de l’accord**.  

  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’un lot sortant](../core/configuring-an-outgoing-batch.md)  
 [La gestion des Solutions EDI et AS2](../core/managing-edi-and-as2-solutions.md)