---
title: "Comment créer des définitions de vocabulaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, vocabularies
- vocabularies, creating
- vocabularies, definitions
ms.assetid: 6f8fc4c2-2c46-4a7d-a02f-89de0396e3e2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff9fdfc7cd444a97d1a24353c13d93460c00d4ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-vocabulary-definitions"></a>Comment créer des définitions de vocabulaire
Vous pouvez utiliser l'Assistant Définition de vocabulaire pour créer des définitions de vocabulaire. Vous pouvez définir une définition de vocabulaire en tant que valeur constante, plage de valeurs, ensemble de valeurs ou éléments d'un assembly .NET, d'un document XML ou d'une table de base de données. Si vous sélectionnez une variable publique, il y aura **obtenir** et **définir** options de la même façon que dans l’Assistant Définition de base de données et XML.  
  
 Vous pouvez également créer une définition de vocabulaire en sélectionnant un fait à partir d’un des trois onglets : par exemple, une colonne de base de données, un nœud XML ou un membre d’une classe .NET, en faisant glisser le fait sur pour le **vocabulaires** onglet, et sa suppression à une version non publiée d’un vocabulaire.  
  
> [!NOTE]
>  Vous ne pouvez pas ajouter une définition de vocabulaire à une version de vocabulaire qui a été publiée.  
  
### <a name="to-define-a-vocabulary-definition-as-a-constant-value"></a>Pour définir une définition de vocabulaire en tant que valeur constante  
  
1.  Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.  
  
    > [!NOTE]
    >  Vous pouvez également faire glisser des éléments à partir d’autres onglets de l’Explorateur de faits : schémas XML, des bases de données et des Classes .NET  
  
2.  Dans l’Assistant Définition de vocabulaire, sélectionnez **valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **suivant**.  
  
3.  Modifiez le nom et la description de la définition.  
  
    > [!NOTE]
    >  La longueur maximale d'un nom complet de définition est de 512 caractères.  
  
4.  Sélectionnez **valeur constante**, puis cliquez sur **suivant**.  
  
5.  Dans la liste déroulante des types de systèmes disponibles, sélectionnez un type de définition.  
  
6.  Modifiez le nom d’affichage et la valeur, puis cliquez sur **Terminer**.  
  
### <a name="to-define-a-vocabulary-definition-as-a-range-of-values"></a>Pour définir une définition de vocabulaire en tant que plage de valeurs  
  
1.  Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.  
  
2.  Dans l’Assistant Définition de vocabulaire, sélectionnez **valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **suivant**.  
  
3.  Modifiez le nom et la description de la définition.  
  
4.  Sélectionnez **plage de valeurs**, puis cliquez sur **suivant**.  
  
5.  Sélectionnez un type de définition dans la liste déroulante.  
  
6.  Cliquez sur **plage inférieure**, puis cliquez sur **modifier** pour spécifier les valeurs de la plage inférieure. La boîte de dialogue de définition de paramètre s'ouvre alors.  
  
7.  Sélectionnez **utiliser une valeur constante** et entrer une valeur constante, ou sélectionnez **utiliser une définition d’un vocabulaire publié** et accédez à une définition de vocabulaire, puis cliquez sur **OK**.  
  
8.  Répétez les étapes 6 et 7 pour **plage supérieure**.  
  
    > [!NOTE]
    >  Le **plage supérieure** valeur doit dépasser la **plage inférieure** valeur.  
  
9. Tapez la chaîne de format d’affichage ou cliquez sur **par défaut** pour revenir à la chaîne de format d’affichage par défaut, puis cliquez sur **Terminer**.  
  
    > [!NOTE]
    >  Votre format de chaîne doit inclure des index de paramètre dans des accolades, par exemple, « {0} » et « {1}"—to servent d’espaces réservés pour les paramètres de la plage haute et basse.  
  
     ![Définitions de vocabulaire](../core/media/3db84492-d6b8-4059-9d2c-a720ccc207b6.gif "3db84492-d6b8-4059-9d2c-a720ccc207b6")  
Plage de valeurs avec format de chaîne  
  
### <a name="to-define-a-vocabulary-definition-as-a-set-of-values"></a>Pour définir une définition de vocabulaire en tant qu'ensemble de valeurs  
  
1.  Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.  
  
2.  Dans l’Assistant Définition de vocabulaire, sélectionnez **valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **suivant**.  
  
3.  Modifiez le nom et la description de la définition.  
  
4.  Sélectionnez **ensemble de valeurs**, puis cliquez sur **suivant**.  
  
5.  Entrez le type de la définition et son nom complet.  
  
6.  Pour ajouter un membre à l’ensemble, sélectionnez **utiliser une valeur constante** et entrer une valeur constante, ou sélectionnez **utiliser une définition d’un vocabulaire publié** et accédez à une définition de vocabulaire, puis cliquez sur **Ajouter**.  
  
7.  Recommencez l'étape 6 avec n'importe quelle combinaison de constantes ou de définitions de vocabulaire, pour tous les éléments que vous souhaitez inclure dans votre ensemble.  
  
8.  Pour déplacer un membre dans l’ordre relatif de l’ensemble, sélectionnez-le, puis **des** ou **vers le bas**.  
  
9. Pour supprimer un membre de l’ensemble, sélectionnez-le, puis **supprimer**.  
  
10. Lorsque vous avez terminé votre jeu, cliquez sur **Terminer**.  
  
     ![Définitions de vocabulaire](../core/media/461d0d70-52ed-4f43-927d-3efb1fbfb934.gif "461d0d70-52ed-4f43-927d-3efb1fbfb934")  
Ensemble de valeurs  
  
### <a name="to-define-a-vocabulary-definition-as-a-net-class-or-class-member"></a>Pour définir une définition de vocabulaire en tant que classe .Net ou que membre de classe  
  
1.  Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.  
  
2.  Dans l’Assistant Définition de vocabulaire, sélectionnez **classe .NET ou membre de classe**, puis cliquez sur **suivant**.  
  
3.  Modifier la **nom de la définition** et **Description** champs.  
  
4.  Cliquez sur **Parcourir**.  
  
5.  Dans le **assemblys .NET** boîte de dialogue, sélectionnez un assembly, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Les assemblys doivent se trouver dans le Global Assembly Cache (GAC). L’éditeur des règles d’entreprise charge un assembly .NET lorsque vous recherchez l’assembly .NET dans le **l’Explorateur de faits** fenêtre ou dans le **classe .NET ou définition de membre de classe** page de la **vocabulaire Définition** fenêtre.  Si vous mettez à jour l'assembly dans le GAC, fermez l'Éditeur des règles d'entreprise et redémarrez-le afin de charger l'assembly .NET mis à jour. L'actualisation n'est en effet pas automatique.  
  
6.  Développez le nœud de l'assembly.  
  
7.  Sélectionnez une classe ou développez une classe et sélectionnez un membre de classe, puis cliquez sur **OK**.  
  
8.  Cliquez sur **suivant**et spécifiez le nom complet.  
  
     Pour plus d'informations, voir la section « Pour spécifier le format d'affichage d'une définition de vocabulaire à l'aide de paramètres » plus loin dans cette rubrique.  
  
9. Cliquez sur **Terminer**.  
  
     ![Définitions de vocabulaire](../core/media/4259101f-26dd-488f-81c0-f8d225e4016e.gif "4259101f-26dd-488f-81c0-f8d225e4016e")  
Définition de vocabulaire d'objets .NET  
  
### <a name="to-define-a-vocabulary-definition-as-an-xml-document-element-or-attribute"></a>Pour définir une définition de vocabulaire en tant qu'élément ou attribut de document XML  
  
1.  Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.  
  
2.  Dans l’Assistant Définition de vocabulaire, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.  
  
3.  Tapez un nom de définition et une description de la définition.  
  
4.  Cliquez sur **Parcourir** pour localiser un fichier de schéma et de spécifier un attribut ou élément de document.  
  
5.  Dans la liste déroulante, sélectionnez un type compatible avec celui de l'élément ou de l'attribut du schéma.  
  
    > [!NOTE]
    >  Si aucun cast valide ne peut être effectué vers ou à partir du type spécifié dans le type de l'élément ou de l'attribut du document, un message d'erreur s'affichera lors de l'exécution.  
  
6.  Sélectionnez un type d'opération selon que vous souhaitez obtenir la valeur de l'élément ou de l'attribut, ou définir sa valeur.  
  
7.  Si vous avez choisi de définir la valeur, cliquez sur **suivant**, puis spécifiez le format d’affichage.  
  
8.  Cliquez sur **Terminer**.  
  
     ![Définitions de vocabulaire](../core/media/fd81b534-ec41-4147-b716-1e10ffc01d6f.gif "fd81b534-ec41-4147-b716-1e10ffc01d6f")  
Définition de vocabulaire XML  
  
> [!NOTE]
>  L'existence de l'élément défini et du type de document n'est jamais validée. Si le document déclaré ne comporte pas l'élément, une erreur d'exécution se produira. Si vous déclarez un document d'un type inconnu, il sera tout simplement ignoré.  
  
#### <a name="to-define-a-vocabulary-definition-as-a-database-table-or-database-table-column"></a>Pour définir une définition de vocabulaire en tant que table de base de données ou que colonne de table de base de données  
  
1.  Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.  
  
2.  Dans l’Assistant Définition de vocabulaire, sélectionnez **Table de base de données ou la définition de colonne de Table de base de données**, puis cliquez sur **suivant**.  
  
3.  Tapez un nom et une description de définition.  
  
4.  Cliquez sur **Parcourir**.  
  
5.  Sélectionnez un ordinateur SQL Server avec lequel établir une connexion. Si l’ordinateur SQL Server n’est pas démarré, sélectionnez le **démarrer SQL Server s’il est arrêté** case à cocher.  
  
6.  Sélectionnez un type d'authentification. Si vous sélectionnez l’authentification SQL Server, tapez votre nom de connexion et un mot de passe, puis cliquez sur **OK**.  
  
7.  Sélectionnez la table ou la colonne de table que vous souhaitez lier, puis cliquez sur **OK**.  
  
8.  Si vous avez sélectionné une colonne de table, vous devez choisir entre obtenir sa valeur et définir sa valeur. Si vous choisissez de définir sa valeur, tapez le nom complet. Si vous choisissez de définir sa valeur, cliquez sur **suivant** pour spécifier le format d’affichage.  
  
     Pour plus d'informations, voir la section « Pour spécifier le format d'affichage d'une définition de vocabulaire à l'aide de paramètres » plus loin dans cette rubrique.  
  
9. Si vous avez sélectionné une table, tapez un nom complet.  
  
10. Cliquez sur **Terminer**.  
  
    > [!NOTE]
    >  Par défaut, **DataConnection** liaison est utilisée.  
  
     ![Définitions de vocabulaire](../core/media/f8121306-cd73-4997-adc4-71a055dfd824.gif "f8121306-cd73-4997-adc4-71a055dfd824")  
Définition de vocabulaire de base de données  
  
#### <a name="to-specify-the-display-format-of-a-vocabulary-definition-by-using-parameters"></a>Pour spécifier le format d'affichage d'une définition de vocabulaire à l'aide de paramètres  
  
1.  Sélectionnez un paramètre dans la liste des **paramètres** dans l’Assistant Définition de vocabulaire, puis cliquez sur **modifier**.  
  
2.  Sélectionnez **utiliser une valeur constante** et entrer une valeur constante, ou sélectionnez **utiliser une définition d’un vocabulaire publié** et accédez à une définition de vocabulaire, puis cliquez sur **OK**.  
  
3.  Tapez la chaîne de format d’affichage ou cliquez sur **par défaut** pour revenir à la chaîne de format d’affichage par défaut, puis cliquez sur **Terminer**.  
  
    > [!NOTE]
    >  Votre format de chaîne doit inclure des index de paramètre dans des accolades, par exemple, « {0} » et « {1}"—to servent d’espaces réservés pour les paramètres.  
  
     ![Définitions de vocabulaire](../core/media/822f78f4-278a-4211-83ad-44032fa81f13.gif "822f78f4-278a-4211-83ad-44032fa81f13")  
Définition de paramètres à l'aide de paramètres