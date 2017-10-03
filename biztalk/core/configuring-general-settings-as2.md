---
title: "Configuration des paramètres généraux (AS2) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8592c52e-5156-418c-9c49-7478f73c372e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23ff62f90f14238f7834312ab909a137d49bcbab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-general-settings-as2"></a>Configuration des paramètres généraux (AS2)
Dans le cadre des paramètres généraux, vous spécifiez le nom de l'accord, le protocole utilisé (AS2), les tiers et profils impliqués et l'activation ou non de la création de rapports pour tous les messages traités par l'accord. Vous pouvez également spécifier les informations de contact des tiers dans le cadre de l'accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-general-agreement-settings"></a>Pour configurer les paramètres généraux de l'accord  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **Parties** dans l’arborescence de la console, puis, dans le **tiers et profils d’entreprise** page, cliquez sur un profil d’entreprise qui doit faire partie de l’accord qui vous créez, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
2.  Les tableaux suivants répertorient les différentes propriétés et les valeurs pour les propriétés de la **propriétés générales** page.  
  
    1.  Dans le **paramètres de l’accord** section, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Spécifiez un nom pour l'accord.|  
        |**ID**|Répertorie l'identification unique de l'accord. Cette zone de texte n’est pas modifiable et affiche l’ID de l’accord après avoir cliqué sur **appliquer** pour la première fois et paramètres sont acceptés.|  
        |**État**|Spécifie l'état de l'accord. Par défaut, un accord est créé dans un **Active** état. Si vous souhaitez que l’accord doit être désactivée lorsqu’il est créé, sélectionnez **désactivé** dans la liste déroulante.|  
        |**Protocole**|Spécifie le protocole pour l'accord. Pour un protocole de transport AS2, sélectionnez **AS2** dans la liste déroulante.|  
  
    2.  Dans le **premier partenaire** section, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Affiche le nom du partenaire qui a le profil d'entreprise pour lequel vous créez l'accord. Cette zone de texte n'est pas modifiable.|  
        |**Profil**|Affiche le nom du profil pour lequel vous créez l'accord. Cette zone de texte n'est pas modifiable.|  
        |**Ensemble de protocoles**|Si vous avez créé un ensemble de protocoles AS2 dans le cadre du profil d'entreprise, vous pouvez le sélectionner dans la liste déroulante. Si vous n'avez pas créé un ensemble de protocoles AS2 dans le cadre du profil d'entreprise, vous pouvez laisser ce champ vide.|  
  
    3.  Dans le **deuxième partenaire** section, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Dans la liste déroulante, sélectionnez un tiers qui a le profil d'entreprise avec lequel vous voulez créer un accord.|  
        |**Profil**|Dans la liste déroulante, sélectionnez un profil avec lequel vous voulez créer un accord.|  
        |**Ensemble de protocoles**|Si vous avez créé un ensemble de protocoles AS2 dans le cadre du profil d'entreprise, vous pouvez le sélectionner dans la liste déroulante. Si vous n'avez pas créé un ensemble de protocoles AS2 dans le cadre du profil d'entreprise, vous pouvez laisser ce champ vide.|  
  
        > [!TIP]
        >  Appuyez sur `CTRL`, sélectionnez les profils d’entreprise qui seront inclus dans le contrat, avec le bouton droit à un profil d’entreprise, pointez sur **nouveau**, puis cliquez sur **accord**. Les valeurs de nom du partenaire et profils d’entreprise pour les deux partenaires seront automatiquement remplis dans le **propriétés de l’accord** boîte de dialogue.  
  
        > [!NOTE]
        >  Dès que vous sélectionnez l’autre profil, deux onglets sont ajoutés à côté du **général** onglet. Chaque onglet représente un accord AS2 unidirectionnel entre les deux tiers. Vous utilisez les onglets pour spécifier les paramètres liés à l'échange et au document informatisé dans les onglets.  
  
    4.  Sélectionnez le **activer l’accord** case à cocher pour activer l’accord et procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**From**|Sélectionnez la date et l'heure à partir desquelles l'accord est valide.|  
        |**Aucune Date de fin**|Sélectionnez cette option si vous ne voulez pas définir de date de fin lorsque l'accord est désactivé.|  
        |**Pour terminer**|Sélectionnez cette option et spécifiez la date et l'heure jusqu'auxquelles l'accord est valide.|  
  
    5.  Dans le **paramètres d’hôte communs** section, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Activer les rapports d'**|Pour afficher les entrées d’état pour tous les messages AS2 (entrants et sortants) dans le **Message AS2 et état MDN corrélé** onglet de la **vue d’ensemble du groupe** volet dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration. Si cette option n'est pas activée, aucune entrée d'état ne s'affiche.|  
  
3.  Dans le **général** sous l’onglet dans le **les informations de Contact** page, procédez comme suit :  
  
    1.  Dans le **Contact1** , entrez les informations de contact pour le profil du tiers avec lequel vous créez un accord. Ces données n'ont qu'une valeur informative ; elles ne seront pas utilisées par le composant d'exécution BizTalk.  
  
    2.  Pour ajouter un autre onglet de contact, cliquez sur le **nouveau Contact** onglet.  
  
    3.  Pour supprimer un onglet de contact, cliquez sur **supprimer** à partir de l’angle supérieur droit de la page d’onglets.  
  
        > [!NOTE]
        >  Vous ne pouvez pas supprimer le **Contact1** onglet. Vous pouvez supprimer uniquement les nouveaux onglets que vous ajoutez.  
  
4.  Dans le **général** sous l’onglet dans le **des propriétés supplémentaires** page, procédez comme suit :  
  
    > [!NOTE]
    >  Les informations que vous spécifiez dans cette page ne sont pas utilisées par BizTalk Server pour tout traitement, ces données sont fournies à des fins d'information uniquement.  
  
    1.  Dans le **des propriétés supplémentaires** grille, entrez les paires nom-valeur pour les informations que vous souhaitez ajouter relatives à la partie ou l’accord.  Entrez une paire nom-valeur pour mémoriser toute information sur le tiers. Vous pouvez ajouter autant de paires nom-valeur que vous voulez.  
  
         Pour supprimer une paire nom-valeur, sélectionnez la ligne et cliquez sur **supprimer** à partir de l’angle supérieur droit.  
  
    2.  Dans le **texte 1**, **texte 2**, et **accord** zones de texte, entrez les informations sur l’accord avec un tiers.  
  
        > [!IMPORTANT]
        >  Si vous cliquez sur **OK** ou **appliquer** après fournir toutes les valeurs répertoriées dans cette page, vous obtiendrez une erreur. Cela est dû au fait que les valeurs obligatoires pour créer un accord ne sont pas encore fournies. Il s’agit d’AS2-à partir à AS2-des valeurs sur le **identificateurs** page de chaque onglet d’accord unidirectionnel.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous devez à présent configurer les paramètres de l'identificateur pour l'accord. Pour obtenir des instructions, consultez [configuration des identificateurs (AS2)](../core/configuring-identifiers-as2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés d’accord AS2](../core/configuring-as2-agreement-properties.md)