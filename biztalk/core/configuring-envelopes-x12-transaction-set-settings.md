---
title: "Configuration d’enveloppes (paramètres X12-Transaction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9313a7b9-72fa-4071-8c65-007371643179
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 519062fa4647cdc2c7c39dda19373ff888eaf601
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-envelopes-x12-transaction-set-settings"></a>Configuration des enveloppes (X12 - Paramètres de documents informatisés)
Dans le **enveloppes** page de la **paramètres des documents informatisés** section, vous définissez la façon dont BizTalk Server génère les segments GS et ST pour un échange codé X12 qu’elle envoie au tiers. Un segment GS identifie et spécifie un groupe fonctionnel pour un échange X12. Un segment ST est l'en-tête de message d'un échange X12.  
  
 Dans cette page, vous associez les valeurs de la **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, et **GS8** des éléments de données avec des valeurs de la **Type de Transaction**, **Version/publication**, et **cible espace de noms** des éléments de données. Lorsque BizTalk détermine qu’un message XML BizTalk les valeurs définies pour le **Type de Transaction**, **Version/publication**, et **espace de noms cible** éléments d’une ligne de la grille, Il renseigne le **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, et **GS8** des éléments de données dans l’enveloppe de la sortie de l’échange avec les valeurs de la même ligne de la grille. Les valeurs de la **Type de Transaction**, **Version/publication**, et **espace de noms cible** éléments doivent être uniques.  
  
> [!NOTE]
>  Si vous entrez une valeur pour n'importe quel champ de la grille, puis que vous la supprimez, vous devrez supprimer l'ensemble de la ligne, sinon la validation de la page échouera.  
  
> [!NOTE]
>  Cette rubrique s'applique également aux paramètres liés à HIPAA.  
  
> [!IMPORTANT]
>  Toutes les propriétés sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** vérifier boîte pour tiers A. Toutefois, toutes les propriétés sont activées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-define-the-gs-and-st-segments"></a>Pour définir les segments GS et ST  
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **enveloppes**.  
  
3.  Dans une ligne de la grille, entrez les valeurs suivantes :  
  
    -   Pour le **Type de Transaction** , sélectionnez une valeur pour le code d’identificateur de document informatisé dans la liste déroulante.  
  
    -   Pour **Version/publication**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de 12 caractères.  
  
    -   Pour **espace de noms cible** éléments, sélectionnez une valeur dans la liste déroulante ou entrez un espace de noms.  
  
        > [!NOTE]
        >  BizTalk Server compare ces valeurs à celles associées à l'échange qu'il crée.  
  
4.  Dans la même ligne de la grille, entrez les valeurs suivantes :  
  
    -   Pour **GS1**, sélectionnez une valeur pour le code fonctionnel dans la liste déroulante. Il s’agit d’un champ facultatif.  
  
    -   Pour **GS2**, entrez une valeur alphanumérique pour l’application émettrice comportant deux caractères au minimum et un maximum de 15 caractères. Ce champ est obligatoire.  
  
    -   Pour **GS3**, entrez une valeur alphanumérique pour l’application réceptrice avec un minimum de deux caractères et un maximum de 15 caractères. Ce champ est obligatoire.  
  
    -   Pour **GS4**, sélectionnez **SSAAMMJJ** ou **aammjj**. Il s’agit d’un champ facultatif  
  
    -   Pour **GS5**, sélectionnez **HHMM**, **HHMMSS**, ou **HHMMSSdd**. Il s’agit d’un champ facultatif  
  
    -   Pour **GS7**, sélectionnez une valeur pour l’entité responsable dans la liste déroulante. Il s’agit d’un champ facultatif.  
  
    -   Pour **GS8**, entrez une valeur alphanumérique pour le document identifié avec un caractère au minimum et un maximum de 12 caractères. Il s’agit d’un champ facultatif.  
  
        > [!NOTE]
        >  Ils vous seront les valeurs que BizTalk Server entre dans les champs GS de l’échange qu’il crée si les **Type de Transaction**, **Version/publication**, et **d’espacedenomscible**dans la même ligne, les éléments sont correspondent à ceux associés à l’échange.  
  
5.  Répétez les étapes 3 et 4 pour entrer des lignes supplémentaires dans la grille.  
  
6.  Pour une ligne dans la grille, cliquez sur **par défaut** pour désigner la ligne par défaut.  
  
    > [!NOTE]
    >  Si un message n’a pas de correspondance avec la **Type de Transaction**, **Version/publication**, et **espace de noms cible** éléments dans n’importe quelle ligne, BizTalk Server attribue au message avec les valeurs pour le **GS1**, **GS2**, **GS3**, **GS5**, **GS7**et **GS8** éléments de la ligne par défaut. Ces valeurs sont utilisées même si le message n’a pas de correspondance avec la **Type de Transaction**, **Version/publication**, et **espace de noms cible** les éléments de la ligne par défaut.  
  
    > [!NOTE]
    >  Si aucune valeur par défaut n’est sélectionnées, les documents entrants ne correspondant pas à la **Type de Transaction**, **Version/publication**, et **espace de noms cible** éléments des lignes seront suspendus. .  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres (X12) documents informatisés](../core/configuring-transaction-set-settings-x12.md)