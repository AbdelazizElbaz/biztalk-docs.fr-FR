---
title: "Configuration des paramètres de l’hôte Local (EDIFACT-informatisés paramètres) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f7c9cb9-7b4b-41de-a3f3-c0519b18673c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 912af3a047f77f077bf9de58a25802f3c658e6b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-local-host-settings-edifact-transaction-set-settings"></a>Configuration des paramètres de l'hôte local (EDIFACT - Paramètres de documents informatisés)
Pour traiter un échange entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit déterminer le schéma dont il a besoin pour le traitement et la validation de l'échange. Pour ce faire, il doit déterminer l'espace de noms cible associé au schéma, ainsi que le schéma à utiliser. Dans cette page de l'accord de tiers, vous entrez les propriétés à utiliser pour déterminer l'espace de noms cible. Comment BizTalk Server détermine le schéma est décrite dans [résolution de l’accord, détection de schéma et l’autorisation pour les Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher pour le tiers A. Toutefois, toutes les propriétés sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="determining-the-target-namespace"></a>Détermination de l'espace de noms cible  
 Dans le **personnaliser le Namespace cible** grille, vous pouvez définir l’espace de noms cible à un des espaces de noms pour les schémas standard fournis avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans la grille, vous associez la valeur de la **cible Namespace** élément avec des valeurs de la **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, **UNG2.1**, et **UNG2.2** éléments. Lorsque BizTalk reçoit un message dont **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, **UNG2.1**, et **UNG2.2** éléments correspondent à ceux d’une ligne de la grille, il utilise l’espace de noms correspondant pour déterminer le schéma qu’il utilisera pour traiter le message. La valeur des éléments doit être unique.  
  
 Si un message n’a pas de correspondance avec la **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, **UNG2.1**, et **UNG2.2** éléments dans n’importe quelle ligne de la grille, BizTalk Server traite le message à l’aide de l’espace de noms dans la ligne pour laquelle le **par défaut** colonne est cochée. Cet espace de noms cible est ensuite utilisé par défaut. Si aucun espace de noms n'est identifié, BizTalk utilise l'espace de noms par défaut de `http://schemas.microsoft.com/BizTalk/Edi/Edifact/2006`.  
  
> [!NOTE]
>  Si vous entrez une valeur pour n'importe quel champ de la grille, puis que vous la supprimez, vous devrez supprimer l'ensemble de la ligne, sinon la validation de la page échouera.  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a>Pour configurer les paramètres de l'hôte local des documents informatisés  
  
1.  Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **paramètres d’hôte Local**.  
  
3.  Comme la partie de la transaction définie les paramètres de validation, si vous définissez **stratégie de séparateur de fin** à **facultatif** ou **obligatoire**, vous pouvez sélectionner **créer vide Les balises XML pour les séparateurs de fin** pour que l’expéditeur des échanges inclue des balises XML vides pour les séparateurs de fin.  
  
4.  Sélectionnez **utiliser le point (.) comme séparateur décimal** pour activer BizTalk Server incluent un point (.) dans le message XML créé à partir d’un échange contenant un nombre décimal.  
  
5.  Dans le **personnaliser le Namespace cible** section, procédez comme suit :  
  
    1.  Sélectionnez le **par défaut** case à cocher de la ligne qui contient l’espace de noms par défaut cible que vous souhaitez définir.  
  
    2.  Dans le **UNH2.1** colonne, spécifiez le type de message. (6 caractères maximum).  
  
    3.  Dans le **UNH2.2** colonne, spécifiez le numéro de version de message. (au minimum, un caractère ; 3 caractères).  
  
    4.  Dans le **UNH2.3** colonne, spécifiez le numéro de version de message. (au minimum, un caractère ; 3 caractères).  
  
    5.  Dans le **UNH2.5** colonne, spécifiez le code affecté. (6 caractères maximum, au format alphanumérique).  
  
    6.  Dans le **UNG2.1** colonne, entrez une valeur alphanumérique pour l’identification de l’expéditeur application avec un minimum d’un caractère et au maximum 35 caractères. Ce champ est obligatoire.  
  
    7.  Dans le **UNG2.2** colonne, entrez une valeur alphanumérique pour le qualificateur de code application expéditeur avec un caractère au minimum et un maximum de quatre caractères. Ce champ est facultatif.  
  
    8.  Dans le **cible Namespace** colonne, sélectionnez dans la liste déroulante ou entrez l’espace de noms cible à utiliser pour un échange lorsqu’aucune correspondance n’est trouvée entre les éléments de données dans n’importe quelle ligne de la grille et les champs dans l’échange.  
  
        > [!NOTE]
        >  BizTalk Server compare ensuite ces valeurs à celles associées à l'échange qu'il reçoit.  
  
    9. Répétez ces étapes pour les autres espaces de noms cibles à utiliser.  
  
    10. Pour supprimer un espace de noms cible dans la liste, sélectionnez la ligne, puis cliquez sur **supprimer**.  
  
6.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des documents informatisés (EDIFACT) de paramètres](../core/configuring-transaction-set-settings-edifact.md)