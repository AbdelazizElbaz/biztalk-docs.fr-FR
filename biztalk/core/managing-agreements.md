---
title: Gestion des contrats | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.resultsobject.agreement
ms.assetid: e9c6cdd1-8c17-4b1e-a556-2b287593bb9d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 012a4a5032bd9f9e9a66b855d41a83b5dc5736d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-agreements"></a>Gestion des accords
Un accord de partenariat commercial est défini comme un accord définitif et ferme entre deux partenaires commerciaux pour le traitement des messages via un protocole interentreprises spécifique. Consultez [accord de partenariat commercial](../core/trading-partner-agreement.md). 

Cette rubrique vous montre comment créer, afficher, modifier, activer, désactiver ou supprimer un accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="create-an-agreement"></a>Créer un accord  
  
1.  Ouvrez **Administration de BizTalk Server**, développez le groupe BizTalk, puis sélectionnez **Parties**. 
2. Dans le **tiers et profils d’entreprise** page, cliquez sur un profil d’entreprise qui fait partie de l’accord que vous créez, sélectionnez **nouveau**, puis sélectionnez **accord**.  
  
3.  Dans le **propriétés générales**: 
  
    1.  Dans le **paramètres de l’accord** section, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Entrez un nom pour l’accord|  
        |**ID**|Répertorie l'identification unique de l'accord. Cette zone de texte est en lecture seule et afficher l’ID de l’accord après avoir sélectionné **appliquer** pour la première fois et les paramètres sont acceptés.|  
        |**État**|Spécifie l'état de l'accord. Par défaut, un accord est créé dans un **Active** état. Si vous souhaitez que l’accord doit être désactivée lorsqu’il est créé, sélectionnez **désactivé** dans la liste déroulante.|  
        |**Protocole**|Spécifie le protocole pour l'accord.<br /><br /> -Pour une X12 protocole de codage, sélectionnez **X12** dans la liste déroulante. Consultez [configuration X12 des propriétés d’accord](../core/configuring-x12-specific-agreement-properties.md)<br />-Pour un protocole de codage EDIFACT, sélectionnez **EDIFACT** dans la liste déroulante.  Consultez [configuration des propriétés de l’accord EDIFACT spécifique](../core/configuring-edifact-specific-agreement-properties.md).<br />-Pour un protocole de codage AS2, sélectionnez **AS2** dans la liste déroulante. Consultez [configuration des propriétés d’accord AS2](../core/configuring-as2-agreement-properties.md). <br/><br/>**Remarque**<br/>  Les onglets de l'accord unidirectionnel contiennent les propriétés de l'accord. Les onglets de l'accord unidirectionnel apparaissent une fois que vous avez sélectionné le deuxième profil avec lequel l'accord sera créé. Vous sélectionnez le second partenaire aux étapes suivantes.|  
  
    2.  Dans le **premier partenaire** section, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Affiche le nom du partenaire qui a le profil d'entreprise pour lequel vous créez l'accord. Cette zone de texte est en lecture seule.|  
        |**Profil**|Affiche le nom du profil pour lequel vous créez l'accord. Cette zone de texte est en lecture seule.|  
        |**Ensemble de protocoles**|Si vous avez créé un ensemble de protocoles X12 dans le cadre du profil d'entreprise, vous pouvez le sélectionner dans la liste déroulante. Si vous n'avez pas créé un ensemble de protocoles X12 dans le cadre du profil d'entreprise, vous pouvez laisser ce champ vide.|  
  
    3.  Dans le **deuxième partenaire** section, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Dans la liste déroulante, sélectionnez un tiers qui a le profil d'entreprise avec lequel vous voulez créer un accord.|  
        |**Profil**|Dans la liste déroulante, sélectionnez un profil avec lequel vous voulez créer un accord.|  
        |**Ensemble de protocoles**|Si vous avez créé un ensemble de protocoles X12 dans le cadre du profil d'entreprise, vous pouvez le sélectionner dans la liste déroulante. Si vous n'avez pas créé un ensemble de protocoles X12 dans le cadre du profil d'entreprise, vous pouvez laisser ce champ vide.|  
  
        > [!TIP]
        >  Appuyez sur `CTRL`, sélectionnez les profils d’entreprise qui seront inclus dans le contrat, avec le bouton droit à un profil d’entreprise, sélectionnez **nouveau**, puis sélectionnez **accord**. Les valeurs de nom du partenaire et profils d’entreprise pour les deux partenaires sont automatiquement renseignées dans la **propriétés de l’accord** boîte de dialogue.  
  
        > [!NOTE]
        >  Dès que vous sélectionnez l’autre profil, deux onglets sont ajoutés à côté du **général** onglet. Chaque onglet représente un accord unidirectionnel entre les deux tiers. Les onglets vous permet d’entrer des propriétés de l’accord.  
  
    4.  Sélectionnez le **activer l’accord** case à cocher pour activer l’accord, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**From**|Sélectionnez la date et l’heure à partir de laquelle l’accord est valide.|  
        |**Aucune Date de fin**|Sélectionnez cette option si vous ne voulez pas définir de date de fin lorsque l'accord est désactivé.|  
        |**Pour terminer**|Sélectionnez cette option pour entrer la date et l’heure jusqu'à ce que l’accord est valide.|  
  
    5.  Dans le **paramètres d’hôte communs** section, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Enregistrer les erreurs dans le journal des événements**|Sélectionnez cette option si vous désirez consigner les erreurs générées par le moteur EDI (pipelines EDI, orchestration du traitement par lot, orchestration de routage, etc.), avec des informations contextuelles, dans l'Observateur d'événements Windows.<br/><br/>**Remarque**: ne s’applique pas aux accords AS2.|  
        |**Consigner les avertissements dans le journal des événements**|Sélectionnez cette option si vous désirez consigner les avertissements générés par le moteur EDI (pipelines EDI, orchestration du traitement par lot, orchestration de routage, etc.), avec des informations contextuelles, dans l'Observateur d'événements Windows. <br/><br/>**Remarque**: ne s’applique pas aux accords AS2.|  
        |**Activer les rapports d'**|Sélectionnez cette option pour afficher les entrées d’état pour tous les messages EDI (entrants et sortants) sur le **échange EDI et état ACK corrélé** onglet de la **vue d’ensemble du groupe** page dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’administration. Si elle est désactivée, aucune entrée d’état n’est affichées.|  
        |**Stocker la charge de message de création de rapports**|Si vous avez sélectionné **activer le rapport d’état**, sélectionnez cette option pour stocker les transactions se définit dans les tables EDI de la base de données des suivis (BizTalk BizTalkDTADb). <br/><br/>**Remarque**: ne s’applique pas aux accords AS2.|  
  
4.  Dans le **général** sous l’onglet dans le **les informations de Contact** page, procédez comme suit :  
  
    1.  Dans le **Contact1** , entrez les informations de contact pour le profil du tiers avec lequel vous créez un accord. Ces données sont à titre d’information uniquement. Il n’est pas utilisé par le Runtime de BizTalk.  
  
    2.  Pour ajouter un autre onglet de contact, sélectionnez le **nouveau Contact** onglet.  
  
    3.  Pour supprimer un onglet de contact, sélectionnez **supprimer** à partir de l’angle supérieur droit de la page d’onglets.  
  
        > [!NOTE]
        >  Vous ne pouvez pas supprimer le **Contact1** onglet. Vous pouvez supprimer uniquement les nouveaux onglets que vous ajoutez.  
  
5.  Dans le **général** sous l’onglet dans le **des propriétés supplémentaires** page, procédez comme suit :  
  
    > [!NOTE]
    >  Les informations que vous entrez sur cette page ne sont pas utilisées par BizTalk Server pour tout traitement ; ces données sont à titre d’information uniquement.  
  
    1.  Dans le **des propriétés supplémentaires** grille, entrez les paires nom-valeur pour les informations que vous souhaitez ajouter relatives à la partie ou l’accord.  Entrez une paire nom-valeur pour mémoriser toute information sur le tiers. Vous pouvez ajouter autant de paires nom-valeur que vous voulez.  
  
         Pour supprimer une paire nom-valeur, sélectionnez la ligne, puis **supprimer** à partir de l’angle supérieur droit.  
  
    2.  Dans le **texte 1**, **texte 2**, et **accord** zones de texte, entrez les informations sur l’accord avec un tiers.  
  
    3.  Sélectionnez **appliquer** pour accepter les propriétés, ou sélectionnez **OK** pour terminer la configuration. Des actions valide les paramètres.  

## <a name="view-or-change-an-agreement"></a>Afficher ou modifier un accord  
  
1.  Dans **Administration de BizTalk Server**, sélectionnez **Parties**. 

2. Dans le **tiers et profils d’entreprise** , sélectionnez un des profils d’entreprise qui ont le contrat que vous souhaitez afficher ou modifier.  
  
3.  Dans le **accords** section, avec le bouton droit de l’accord, puis sélectionnez **propriétés**.  
  
4.  Dans le **propriétés de l’accord**, afficher ou modifier l’accord. Pour les valeurs qui peuvent être entrés sur les différents onglets et les pages dans le **propriétés de l’accord** boîte de dialogue zone, consultez les rubriques suivantes :  
  
    |Pour cela|Consultez le|  
    |--------------|--------------|  
    |Pour un accord X12|[Configuration des propriétés d’accord spécifique X12](../core/configuring-x12-specific-agreement-properties.md)|  
    |Pour un accord EDIFACT|[Configuration des propriétés de l’accord EDIFACT spécifique](../core/configuring-edifact-specific-agreement-properties.md)|  
    |Pour un accord AS2|[Configuration des propriétés d’accord AS2](../core/configuring-as2-agreement-properties.md)|  
  
5.  Sélectionnez **appliquer** pour accepter les propriétés, ou sélectionnez **OK** pour terminer la configuration. Des actions valide les paramètres. 

## <a name="enable-or-disable-an-agreement"></a>Activer ou désactiver un accord  
  
1.  Dans **Administration de BizTalk Server**, sélectionnez **Parties**. 

2. Dans le **tiers et profils d’entreprise** , sélectionnez un des profils d’entreprise qui ont le contrat que vous souhaitez modifier.  
  
3.  Dans le **accords** section, avec le bouton droit de l’accord, puis sélectionnez **activer** ou **désactiver**. 
  
    > [!NOTE]
    >  Lors de sa création, un accord est par défaut dans un état Actif. Le **activer** option est disponible uniquement lorsque l’accord est désactivé. Le **désactiver** option est disponible uniquement lorsque l’accord est activé.  

## <a name="delete-an-agreement"></a>Suppression d’un accord  
1.  Dans **Administration de BizTalk Server**, sélectionnez **Parties**. 
  
2.  Dans le **tiers et profils d’entreprise** , sélectionnez un des profils d’entreprise qui ont le contrat que vous souhaitez supprimer.  
  
3.  Dans le **accords** section, avec le bouton droit de l’accord que vous souhaitez supprimer, puis sélectionnez **supprimer**.  
  
4.  Dans le **confirmer la suppression du contrat** boîte de dialogue, sélectionnez **Oui** pour supprimer l’accord.  

      
## <a name="see-also"></a>Voir aussi  
 [La gestion des Solutions EDI et AS2](../core/managing-edi-and-as2-solutions.md)