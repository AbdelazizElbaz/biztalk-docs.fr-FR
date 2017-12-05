---
title: La gestion des tiers | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.resultsobject.party
helpviewer_keywords:
- Administration Console [BizTalk Server], parties
- managing [parties]
- managing [parties], about managing parties
- parties, managing
ms.assetid: 96d2bcb3-1e38-4dad-a0d6-e5913ba531e7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f639ad516ec4f4a61406b9690d2d52f2ea98599f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="managing-parties"></a>Gestion des tiers
À l’aide de la **Parties** nœud, vous pouvez configurer des partenaires commerciaux (tiers) ou les services internes (profils d’entreprise) avec lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions interagissent. Pour plus d’informations, consultez [partenaires commerciaux](../core/trading-partners-and-business-profiles.md).  

Vous pouvez créer et configurer un tiers à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Après avoir créé un tiers dans BizTalk Server, vous voudrez probablement interagir avec lui à l'aide d'une orchestration. Les tiers interagissent avec les orchestrations grâce à des rôles. Votre orchestration peut compter, par exemple, un rôle de livraison. Dans ce cas, au moins un tiers sera associé à l'expéditeur. Lorsque l'orchestration doit déterminer quelle est la société de transport la moins onéreuse pour l'expédition d'un article, elle peut comparer les prix des tiers dans le rôle Expéditeur.  
  
 Vous devez inscrire un tiers pour pouvoir le lier à un rôle spécifique. Le fait d'inscrire un tiers permet à une orchestration d'interagir avec ce dernier. Consultez [comment inscrire ou désinscrire un tiers pour un rôle](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md).
 
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="create-or-edit-a-party"></a>Créer ou modifier un tiers
  
1.  Ouvrez **Administration de BizTalk Server.**  Développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **Parties**, sélectionnez **nouveau**, puis sélectionnez **tiers**.  
  
2.  Sur le **général** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Entrer un nom de tiers.|  
    |**BizTalk local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers**|Cochez cette case pour spécifier que le tiers représente le même partenaire commercial qui héberge également [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. **Important :** pour un module de plateforme sécurisée deux tiers solution qui utilise des pipelines de l’emploi fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez sélectionner cette case à cocher pour au moins un tiers. **Remarque :** si vous désactivez cette case à cocher, certaines propriétés seront désactivées lors de la création d’un accord pour ce tiers.|  
    |**Propriétés supplémentaires – nom / valeur**|Entrez une paire nom-valeur pour mémoriser toute information sur le tiers. Vous pouvez ajouter autant de paires nom-valeur que vous voulez. **Remarque**: les paires nom-valeur ne sont pas utilisés par BizTalk Server pour tout traitement, ces données sont à titre d’information uniquement.|  
    |**Delete**|Sélectionnez cette option pour supprimer la paire nom-valeur sélectionnée.|  
  
3.  Sur le **Ports d’envoi** page, procédez comme suit.  
  
    > [!NOTE]
    >  Dans BizTalk Server, l’association de ports d’envoi est effectuée au niveau de l’accord. Le **Ports d’envoi** page est disponible dans le cadre des propriétés du tiers uniquement pour la compatibilité descendante. Chaque fois que vous associez un port d'envoi à un accord, le paramètre de port d'envoi est propagé au paramètre du tiers et l'association de ports d'envoi est visible dans cette page. L'inverse n'est toutefois pas vrai. Vous ne pouvez pas associer un port d'envoi à un tiers, puis rendre ce port d'envoi automatiquement disponible dans le cadre des paramètres de l'accord.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Ports d’envoi - nom**|Dans la liste déroulante, sélectionner un port d'envoi à lier à ce tiers.|  
    |**Ports d’envoi - URI**|Afficher l'adresse du port d'envoi.|  
    |**Supprimer**|Sélectionnez cette option pour supprimer le port d’envoi du tiers.|  
    |**Propriétés**|Sélectionnez cette option pour afficher le **propriétés de Port d’envoi** boîte de dialogue pour le port d’envoi sélectionné.|  
  
4.  Sur le **certificat** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Parcourir**|Sélectionnez cette option pour afficher le **sélectionner un certificat** boîte de dialogue, où vous sélectionnez le certificat de signature dans le magasin de certificats ordinateur Local ou d’autres personnes à appliquer aux messages transmis au tiers.|  
    |**Nom commun**|Afficher une description du certificat sélectionné.|  
    |**Empreinte numérique**|Afficher l'empreinte du certificat de clé privée utilisée pour la résolution du tiers et la vérification de signature. Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).|  
    |**Supprimer le certificat**|Sélectionnez cette option pour supprimer le certificat affiché.|  
  
5.  Sélectionnez **appliquer** pour accepter les propriétés, ou sélectionnez **OK** pour terminer la configuration. Les deux actions valident les paramètres.  

### <a name="update-an-existing-party"></a>Mise à jour d’un tiers existant
Après avoir inscrit un tiers dans un rôle et lié les ports, vous pouvez effectuer les opérations suivantes :  
  
-   Modifier le nom et la description de la partie  
-   Modifier le certificat du tiers  
-   Spécifiez si le tiers est pour l’hébergement de l’organisation[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]

1. Dans **Administration de BizTalk Server**, puis sélectionnez **Parties**.

2. Dans le **tiers et profils d’entreprise** volet, avec le bouton droit le tiers que vous souhaitez afficher ou modifier, puis sélectionnez **propriétés**.  

3. Afficher ou modifier les propriétés. 

4. Sélectionnez **appliquer** pour accepter les propriétés, ou sélectionnez **OK** pour terminer la configuration. Des actions valider les paramètres.  

## <a name="delete-a-party"></a>Supprimer un tiers
Supprimer le tiers à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.  
  
> [!IMPORTANT]
>  Vous ne pouvez supprimer un tiers que s'il n'est pas inscrit dans un rôle. Avant de pouvoir supprimer un tiers, vous devez le désinscrire du ou des rôles où il est inscrit. Consultez [comment inscrire ou désinscrire un tiers pour un rôle](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md). 

1. Dans **Administration de BizTalk Server**, sélectionnez **Parties**, avec le bouton droit de la partie que vous souhaitez supprimer, puis sélectionnez **supprimer**.  
  
2.  Dans le **confirmer la suppression du tiers** boîte de dialogue, sélectionnez **Oui** pour supprimer le tiers.  

## <a name="search-for-a-party"></a>Recherche d’un tiers
Si vous avez un grand nombre de parties créé, vous pouvez utiliser la **recherche** option pour afficher les parties que vous souhaitez voir.  

1. Dans **Administration de BizTalk Server**, sélectionnez **Parties**.

3.  Dans le **tiers et profils d’entreprise** volet, vers l’angle supérieur droit, entrez une chaîne de recherche dans les **recherche tiers** zone de texte, puis sélectionnez l’icône de recherche. Vous pouvez également appuyer sur ENTRÉE pour lancer la recherche.  
  
     Lors d'une recherche, vous devez prendre en compte les points suivants :  
  
    -   La chaîne de recherche ne respecte pas la casse
  
    -   Vous pouvez rechercher du texte dans le nom (recherche de sous-chaînes). Par exemple, si vous recherchez ‘ar’, la console Administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affiche les tiers qui commencent par la chaîne de recherche (par exemple Artist) ou les tiers dont le nom contient la chaîne de recherche (par exemple Party1).  
  
    -   L’opération de recherche est limitée aux noms de tiers.  
  
4.  Pour effacer les résultats de recherche, sélectionnez le « x » rouge en regard de la zone de texte de recherche.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des liens de rôle](../core/managing-role-links.md)   
 [Comment configurer le composant de Pipeline résolution du tiers](../core/how-to-configure-the-party-resolution-pipeline-component.md)  
 [La gestion des Solutions EDI et AS2](../core/managing-edi-and-as2-solutions.md)