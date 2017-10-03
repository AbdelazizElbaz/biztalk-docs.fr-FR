---
title: "Gestion des profils d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.resultsobject.businessprofile
ms.assetid: cf98c5a4-71bb-440b-8172-717ed0eb8373
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 434979376e679f1098557dc5b55f50e599ed21cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-business-profiles"></a>Gestion des profils d'entreprise
Un profil d'entreprise représente les départements au sein d'une organisation. Tout comme une organisation peut avoir plusieurs départements, un tiers peut avoir différents [profils d’entreprise](http://msdn.microsoft.com/library/f8286130-57fe-40ed-9fd8-81da2c8baaaf). 
  
Un profil d'entreprise représente un département dans une organisation. Tout comme une organisation peut inclure plusieurs départements (comptabilité, achat, expédition, etc.), un tiers peut inclure plusieurs profils d'entreprise représentant chacun un département d'une organisation. Les propriétés d'un profil d'entreprise contiennent les informations suivantes :  
  
-   informations générales telles que le nom du profil d'entreprise ;  
  
-   identités uniques qui peuvent être associées à un profil d'entreprise ;  
  
-   Paramètres d’encodage (pour les messages X12 et EDIFACT) et [paramètres de protocole](../core/protocol-settings.md) (AS2) qui définit comment le profil d’entreprise peut envoyer ou recevoir des messages à partir d’une autre partie.  
  
Cette rubrique vous montre comment créer, afficher, modifier ou supprimer un profil d’entreprise.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="create-a-business-profile"></a>Créer un profil d’entreprise  
  
1.  Dans **Administration de BizTalk Server**, développez le groupe BizTalk, puis sélectionnez **Parties**. 
2. Dans le **tiers et profils d’entreprise** , avec le bouton droit un tiers, sélectionnez **nouveau**, puis sélectionnez **profil d’entreprise**.  
  
3.  Dans le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Entrez un nom de profil d'entreprise.|  
    |**Description**|Entrez la description du profil d'entreprise.|  
    |**Propriétés supplémentaires – nom / valeur**|Entrez une paire nom-valeur pour mémoriser toute information sur le tiers. Vous pouvez ajouter autant de paires nom-valeur que vous voulez. **Remarque :** les paires nom-valeur ne sont pas utilisés par BizTalk Server pour tout traitement, ces données sont à titre d’information uniquement.|  
    |**Delete**|Sélectionnez cette option pour supprimer la paire nom-valeur sélectionnée.|  
  
4.  Le cas échéant, ajoutez des identités d'entreprise pour les profils d'entreprise. Dans le **identités** onglet, procédez comme suit :  
  
    > [!NOTE]
    >  L'ajout d'identités d'entreprise à ce stade n'est pas obligatoire. Vous pouvez ajouter les identités d’entreprise ultérieurement, dans le cadre d’un accord pour le profil d’entreprise. Si vous avez choisi d’ajouter que les identités d’entreprise maintenant, elles sont disponibles lors de la création d’un accord pour ce profil d’entreprise.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Sélectionnez la cellule vide et dans la grille de la liste déroulante, sélectionnez un corps d’authentification qui fournit des identités d’entreprise uniques aux organisations. Par exemple, **D-U-N-S (DUN and Bradstreet)**. Deux partenaires commerciaux peuvent opter pour une identité d'entreprise dont ils conviennent mutuellement. Dans ce cas, sélectionnez **défini mutuellement** (pour EDIFACT) ou **défini mutuellement (X12)** (pour X12).|  
    |**Qualificateur**|Affiche une valeur prédéfinie basée sur la valeur que vous avez sélectionné pour **nom**.|  
    |**Valeur**|Entrez une valeur pour l'identité d'entreprise. Vous devez prendre en compte les points suivants lorsque vous définissez une valeur pour les identités d'entreprise :<br /><br /> -Pour un tiers donné, vous pouvez avoir plusieurs profils d’entreprise à l’aide de la même combinaison de nom de l’identité et la valeur d’identité. Par exemple, vous pouvez avoir deux profils d’entreprise pour un tiers avec **nom** en tant que **défini mutuellement (X12)** et **valeur** en tant que **THEM**.<br />-Entre plusieurs tiers, vous ne pouvez avoir deux profils d’entreprise à l’aide de la même combinaison de nom de l’identité et la valeur d’identité.|  
    |**Supprimer**|Sélectionnez cette option pour supprimer l’identité sélectionnée.|  
  
5.  Si nécessaire, ajoutez les paramètres de protocole pour les messages encodés X12, encodé en EDIFACT des messages ou les paramètres de protocole pour le transport AS2. Consultez [configuration des propriétés de profil d’entreprise](../core/configuring-business-profile-properties.md).  
  
6.  Sélectionnez **appliquer** pour accepter les propriétés, ou sélectionnez **OK** pour terminer la configuration. Des actions valide les paramètres.  
  
## <a name="view-or-change-a-business-profile"></a>Afficher ou modifier un profil d’entreprise  
  
1.  Dans **Administration de BizTalk Server**, sélectionnez **Parties**. 

2. Dans le **tiers et profils d’entreprise** volet, développez un nœud tiers pour afficher les profils d’entreprise. Cliquez sur un profil d’entreprise que vous souhaitez modifier, puis sélectionnez **propriétés**.  
  
3.  Dans le **propriétés de profil** boîte de dialogue, afficher ou modifier le profil. Pour plus d’informations sur les valeurs qui peuvent être spécifiés sur les différentes pages de le **propriétés de profil** boîte de dialogue, consultez [configuration des propriétés de profil d’entreprise](../core/configuring-business-profile-properties.md).  
  
4.  Sélectionnez **appliquer** pour accepter les propriétés, ou sélectionnez **OK** pour terminer la configuration. Des actions valide les paramètres.  

## <a name="delete-a-business-profile"></a>Supprimer un profil d’entreprise  
  
1.  Dans **Administration de BizTalk Server**, sélectionnez **Parties**.  
  
3.  Dans le **tiers et profils d’entreprise** volet, développez un nœud tiers pour afficher les profils d’entreprise.  
  
4.  Cliquez sur le profil d’entreprise que vous souhaitez supprimer, puis sélectionnez **supprimer**. 
  
5.  Dans le **confirmer la suppression du profil d’entreprise** boîte de dialogue, sélectionnez **Oui** pour supprimer le profil d’entreprise.  


## <a name="see-also"></a>Voir aussi  
 [La gestion des Solutions EDI et AS2](../core/managing-edi-and-as2-solutions.md)