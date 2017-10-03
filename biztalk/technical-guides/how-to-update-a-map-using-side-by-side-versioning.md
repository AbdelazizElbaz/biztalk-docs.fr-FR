---
title: "Comment mettre à jour un mappage à l’aide de la gestion des versions côte à côte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b0e377f-92ab-483e-9f3c-222c7b5ac0b1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d463823a7038e1ead7e2de323da97eda372db76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-a-map-using-side-by-side-versioning"></a>Comment mettre à jour un mappage à l’aide de la gestion des versions côte à côte
Certains artefacts BizTalk, tels que des cartes, sont choisis par nom fort qualifié complet (FQSN), dans ce cas les liaisons incluent la version utilisée. Cela permet à deux ou plusieurs mappages de coexister côte à côte dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Par conséquent, vous pouvez sélectionner un des mappages pour le mappage dans les propriétés d’emplacement de réception entrant ou sortant dans les propriétés de port d’envoi.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server.  
  
### <a name="to-add-a-second-map-side-by-side-to-an-existing-map"></a>Pour ajouter une deuxième carte côte à côte pour un mappage existant  
  
1.  Ouvrez Visual Studio et ouvrez le projet contenant le mappage.  
  
2.  Ouvrez le mappage dans l’assembly et modifier un code à la carte.  
  
    > [!NOTE]  
    >  Si vous appelez un mappage à partir d’une orchestration, et la référence de mappage est codé en dur, vous devrez apporter des modifications de code à l’orchestration lui-même.  
  
3.  Modifier le numéro de version de l’assembly :  
  
    1.  Dans l’Explorateur de solutions, cliquez sur le projet BizTalk, puis cliquez sur **propriétés**.  
  
    2.  Dans le **Concepteur de projets**, cliquez sur le **Application** onglet.  
  
    3.  Dans le volet droit, cliquez sur **informations de l’Assembly**.  
  
    4.  Dans le **informations d’Assembly** boîte de dialogue, spécifiez les valeurs pour le **Version de l’Assembly** champ pour modifier le numéro de version d’assembly. Vous devez modifier uniquement le numéro de version majeure ou mineure. Le numéro de version majeure est le premier chiffre de la séquence (***n***.0.0.0).) ; le numéro de version mineure est le deuxième chiffre de la séquence (0.*** n ***. 0.0).  
  
    5.  Cliquez sur **OK** pour fermer la **informations d’Assembly** boîte de dialogue.  
  
4.  Compilez l’assembly.  
  
5.  Déployer l’assembly dans le groupe (et tous les ordinateurs).  
  
## <a name="modifying-a-map-to-reflect-updated-version-numbers"></a>Modification d’un mappage afin de refléter mis à jour les numéros de Version  
 Assemblys .NET peuvent être appelés à partir d’un mappage à l’aide du fonctoid script. Cela apporte une grande flexibilité et permet au développeur de résoudre de nombreux problèmes relatifs au mappage personnalisé. En outre, une seule contrainte est imposée pour le mappage : il doit, de manière interne, faire référence au nom du type d'assembly ainsi qu'au numéro de version complet de l'assembly invoqué. Cela signifie que, si le numéro de version de l'assembly appelé par le mappage change, tous les liens qui font référence à cet assembly sont rompus.  
  
 Pour éviter ce problème, nous recommandons que si les assemblys sont requis pour être appelée à partir d’une carte, un assembly particulier est créé pour contenir uniquement des fonctionnalités de carte et que le numéro de version de cet assembly est fixe. Ainsi, la version d'assembly des autres fonctions d'assistance peut être mise à jour sans supprimer les mappages.  
  
 Si un assembly référencé dans un mappage est modifié après le développement des mappages, pensez à mettre à jour le fichier de mappage hors de l'Éditeur de mappage pour répercuter les numéros de version mis à jour.  
  
#### <a name="to-modify-a-map-file-to-reflect-updated-version-numbers"></a>Pour modifier un fichier de mappage pour refléter les numéros de version de mise à jour  
  
1.  À l’aide de la **Démarrer** menu, ouvrir **bloc-notes**.  
  
2.  Dans **bloc-notes**, dans le **fichier** menu, cliquez sur **ouvrir**. Dans le **ouvrir** boîte de dialogue, sélectionnez le fichier de mappage que vous souhaitez modifier, puis cliquez sur **ouvrir**.  
  
3.  Dans le menu **Edition** , cliquez sur **Rechercher**. Dans le **trouver** boîte de dialogue, entrez **Assembly =**, puis cliquez sur **suivant**.  
  
4.  S'il existe une référence de script à un assembly externe, le Bloc-notes doit rechercher un élément XML tel que :  
  
    ```  
    <Script Language="ExternalAssembly" Assembly="Contoso.Scripts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=  
    <token>  
    " Class="Contoso.Scripts" Function="CalculateValue" AssemblyPath="Contoso.Scripts.dll"/>  
    ```  
  
5.  Mettez à jour le numéro de version. S’il existe plusieurs instances, utilisez **remplacer** sur la **modifier** menu.  
  
6.  Enregistrez le fichier.  
  
    > [!NOTE]  
    >  Vous pouvez maintenant ouvrir le mappage à l'aide de l'Éditeur de mappage.