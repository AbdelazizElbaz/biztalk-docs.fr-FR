---
title: "Configuration d’enveloppes (EDIFACT-informatisés paramètres) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec140def-6155-4b8a-8489-6e0a530bd697
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1d910f52d9ea90ae0c486356a7ecb3b01bf07a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-envelopes-edifact-transaction-set-settings"></a>Configuration des enveloppes (EDIFACT - Paramètres de documents informatisés)
Dans le **enveloppes** page de la **paramètres des documents informatisés** section, vous définissez la façon dont BizTalk Server génère les segments UNG et UNH pour un échange EDIFACT envoyé au tiers.  
  
 Le segment UNG est l'en-tête qui identifie et indique un groupe fonctionnel d'un échange EDIFACT. Il contient la date et l'heure de préparation du groupe fonctionnel, ainsi que le type et la version du document inclus dans le groupe.  
  
 Le segment UNH est l'en-tête de message d'un échange EDIFACT. Il fournit des informations sur le type du message et sur l'entité responsable de la gestion de la publication de ce type de message. Ce segment permet d'indiquer le début d'un document d'un échange, ainsi que le type de document qui suit.  
  
 Dans le **en-tête de groupe fonctionnel (UNG)** section, vous associez **UNG** les valeurs de **UNH** et un espace de noms. Lorsque BizTalk Server détermine qu’un message XML BizTalk les valeurs définies pour le **UNH** éléments et **espace de noms cible** dans une ligne de la grille, BizTalk Server remplira la **UNG** des éléments de données avec les valeurs de la même ligne de la grille. Les valeurs de la **UNH** éléments et **espace de noms cible** doit être unique.  
  
 Si un message n’a pas de correspondance avec la **UNH** éléments et **espace de noms cible** dans n’importe quelle ligne, BizTalk Server attribue au message avec les valeurs de la **UNG** éléments dans la ligne par défaut. Ces valeurs sont utilisées même si le message n’a pas de correspondance avec la **UNH** éléments et **espace de noms cible** de la ligne par défaut.  
  
 Lorsque le moteur BizTalk détermine qu’un message XML BizTalk possède des valeurs définies pour les éléments UNH et l’espace de noms cible, il renseigne les éléments UNG du message avec les valeurs de la grille, fournie le **créer un regroupement Segments** case à cocher est activée.  
  
> [!NOTE]
>  Dans le **en-tête de groupe fonctionnel (UNG)** section, si vous entrez une valeur pour l’un des champs de la grille, puis que vous la supprimez, vous devez supprimer la ligne entière ou validation échouera dans la page.  
  
> [!IMPORTANT]
>  Toutes les propriétés sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** vérifier boîte pour tiers A. Toutefois, toutes les propriétés sont activées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-define-the-ung-and-unh-segments"></a>Définition des segments UNG et UNH.  
  
1.  Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **enveloppes**.  
  
3.  Dans une ligne de la grille, entrez les valeurs suivantes :  
  
    -   Dans le **pour le message de type UNH2.1** colonne, entrez un type de transaction. (6 caractères maximum).  
  
    -   Dans le **UNH2.2** colonne, entrez le numéro de version de message. (constitué de 1 à 3 caractères).  
  
    -   Dans le **UNH2.3** colonne, entrez le numéro de version de message. (constitué de 1 à 3 caractères).  
  
    -   Dans le **UNH2.5** colonne, entrez le code affecté. (6 caractères maximum). au format alphanumérique).  
  
    -   Dans le **espace de noms cible** colonne, sélectionnez l’espace de noms cible du schéma. Ce champ est obligatoire.  
  
        > [!NOTE]
        >  BizTalk Server compare ces valeurs à celles associées à l'échange qu'il crée.  
  
4.  Sur la même ligne de la grille, entrez les valeurs suivantes :  
  
    -   Pour le **UNG1** (ID de groupe fonctionnel), entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de six caractères. Ce champ est obligatoire.  
  
    -   Pour **UNG2.1** (ID de l’expéditeur de l’Application), entrez une valeur alphanumérique comportant un caractère au minimum et 35 caractères au maximum. Ce champ est obligatoire.  
  
    -   Pour **UNG2.2** (qualificateur de code l’expéditeur Application), entrez une valeur alphanumérique, avec un maximum de quatre caractères. Il s’agit d’un champ facultatif.  
  
    -   Pour **UNG3.1** (destinataire identification de l’Application), entrez une valeur alphanumérique comportant un caractère au minimum et 35 caractères au maximum. Ce champ est obligatoire.  
  
    -   Pour **UNG3.2** (qualificateur de code du destinataire de l’Application), entrez une valeur alphanumérique, avec un maximum de quatre caractères. Il s’agit d’un champ facultatif.  
  
    -   Pour **UNG6** (agence de contrôle), entrez une valeur alphanumérique contenant au moins un et un maximum de deux. Ce champ est obligatoire.  
  
    -   Pour **UNG7.1** (numéro version de type de Message), entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de trois caractères. Ce champ est obligatoire.  
  
    -   Pour **UNG7.2** (numéro version de type de Message), entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de trois caractères. Ce champ est obligatoire.  
  
    -   Pour **UNG7.3** (code d’Association assigné), entrez une valeur alphanumérique contenant au minimum 1 caractère et un maximum de 6 caractères. Ce champ est obligatoire.  
  
    -   Pour **UNG8** (Application un mot de passe), entrez une valeur alphanumérique comportant un caractère au minimum et maximum 14 caractères. Ce champ est obligatoire.  
  
        > [!NOTE]
        >  Ils vous seront les valeurs que BizTalk Server entre dans les champs UNG de l’échange qu’il crée si les **pour le message de type UNH2.1**, **UNH2.2**, **UNH2.3**,  **UNH2.5**, et **espace de noms cible** dans la même ligne, les éléments sont correspondent à ceux associés à l’échange.  
  
5.  Répétez les étapes 4 et 5 pour entrer des lignes supplémentaires dans la grille.  
  
6.  Pour une ligne dans la grille, cliquez sur **par défaut** pour désigner la ligne par défaut.  
  
    > [!NOTE]
    >  Si un message n’a pas de correspondance avec la **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, et **d’espacedenomscible** éléments dans n’importe quelle ligne, BizTalk Server attribue au message avec les valeurs pour le **UNG1**, **UNG2.1**, **UNG2.2**,  **UNG3.1**, **UNG3.2**, **UNG6**, **UNG7.1**, **UNG7.2**, **UNG7.3**, et **UNG8** éléments de la ligne par défaut. Ces valeurs sont utilisées même si le message n’a pas de correspondance avec la **pour le message de type UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, et **espace de noms cible** les éléments de la ligne par défaut.  
  
    > [!NOTE]
    >  Si aucune ligne par défaut n’est sélectionnée, et le message n’a pas de correspondance pour le **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**et **Espace de noms cible** éléments dans n’importe quelle ligne, BizTalk interrompra le message.  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des documents informatisés (EDIFACT) de paramètres](../core/configuring-transaction-set-settings-edifact.md)