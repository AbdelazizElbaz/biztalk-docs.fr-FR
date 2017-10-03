---
title: "Configuration des paramètres de l’hôte Local (paramètres X12-Transaction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31b41c3-49fc-46ef-ab69-889e30dfc58e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fcc099535e6a7b96c5c4bbdd29112da46af3522
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-local-host-settings-x12-transaction-set-settings"></a>Configuration des paramètres de l'hôte local (X12 - Paramètres de documents informatisés)
Pour traiter un échange entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit déterminer le schéma dont il a besoin pour le traitement et la validation de l'échange. Pour ce faire, il doit déterminer l'espace de noms cible associé au schéma, ainsi que le schéma à utiliser. Dans cette page de l'accord de tiers, vous entrez les propriétés à utiliser pour déterminer l'espace de noms cible. Comment [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine le schéma est décrit dans [résolution de l’accord, détection de schéma et l’autorisation pour les Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).  
  
> [!NOTE]
>  Cette rubrique s'applique également aux paramètres liés à HIPAA.  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher pour le tiers A. Toutefois, toutes les propriétés sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="determining-the-target-namespace"></a>Détermination de l'espace de noms cible  
 Dans le **espace de noms cible de personnaliser** grille, vous pouvez définir les espaces de noms cible à un des espaces de noms pour les schémas standard fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans la grille, vous associez la valeur de la **cible Namespace** élément avec des valeurs de l’application émettrice (**GS2**) et le code identificateur du document informatisé (**ST1**). Lorsque BizTalk reçoit un message dont **GS2** et **ST1** des éléments de données correspondent à ceux d’une ligne de la grille, il utilise l’espace de noms correspondant pour traiter le message. La valeur des éléments doit être unique.  
  
 Si un message n’a pas de correspondance avec la **GS2** et **ST1** des éléments de données dans n’importe quelle ligne de la grille, BizTalk Server traite le message à l’aide de l’espace de noms dans la ligne pour laquelle le **par défaut** colonne est cochée. Cet espace de noms cible est ensuite utilisé par défaut. Si aucun espace de noms n'est identifié, BizTalk Server utilise l'espace de noms par défaut de `http://schemas.microsoft.com/BizTalk/Edi/EDIFACT/2006`.  
  
> [!NOTE]
>  Si vous entrez une valeur pour n'importe quel champ de la grille, puis que vous la supprimez, vous devrez supprimer l'ensemble de la ligne, sinon la validation de la page échouera.  
  
> [!NOTE]
>  Pour accéder à une illustration de l'utilisation de cette grille, parcourez le didacticiel EDI Interface Developer et définissez un tiers expéditeur d'un échange. Pour plus d’informations, consultez [étape 4 : configurer un tiers et un profil d’entreprise pour votre partenaire commercial](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md).  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a>Pour configurer les paramètres de l'hôte local des documents informatisés  
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **paramètres d’hôte Local**.  
  
3.  Sélectionnez **conversion implicite de base 10 de valeur numérique de format décimal** pour convertir un nombre EDI spécifié au format Nn en une valeur numérique de base 10 dans le fichier XML intermédiaire dans BizTalk Server.  
  
    > [!NOTE]
    >  Une fois la conversion effectuée, la validation de la longueur du fichier XML intermédiaire peut échouer. Cela peut se produire car la valeur numérique en base 10 contient une virgule, ce qui la rend plus longue que le format Nn. Vous pouvez résoudre ce problème en ajoutant une valeur de **1** à la valeur de longueur minimale/maximale.  
  
4.  Comme la partie de la transaction définie les paramètres de validation, si vous définissez **stratégie de séparateur de fin** à **facultatif** ou **obligatoire**, vous pouvez sélectionner **créer vide Les balises XML pour les séparateurs de fin** pour que l’expéditeur des échanges inclue des balises XML vides pour les séparateurs de fin.  
  
5.  Dans le **personnaliser le Namespace cible** section, procédez comme suit :  
  
    1.  Sélectionnez le **par défaut** case à cocher de la ligne qui contient l’espace de noms par défaut cible que vous souhaitez définir.  
  
    2.  Dans le **pour ST1** code identificateur de jeu de colonnes, sélectionnez une valeur pour la Transaction dans la liste déroulante.  
  
    3.  Dans le **GS2** colonne, entrez une valeur alphanumérique pour l’Application émettrice comportant deux caractères au minimum et un maximum de 15 caractères. Ce champ est obligatoire.  
  
    4.  Dans le **cible Namespace** colonne, sélectionnez dans la liste déroulante ou entrez l’espace de noms cible à utiliser pour un échange lorsqu’aucune correspondance n’est trouvée entre les éléments de données dans n’importe quelle ligne de la grille et les champs dans l’échange.  
  
        > [!NOTE]
        >  BizTalk Server compare ensuite ces valeurs à celles associées à l'échange qu'il reçoit.  
  
    5.  Répétez ces étapes pour les autres espaces de noms cibles à utiliser.  
  
    6.  Pour supprimer un espace de noms cible dans la liste, sélectionnez la ligne, puis cliquez sur **supprimer**.  
  
6.  Cliquez sur **appliquer** pour accepter les modifications, ou cliquez sur **OK** pour entrer et valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres (X12) documents informatisés](../core/configuring-transaction-set-settings-x12.md)