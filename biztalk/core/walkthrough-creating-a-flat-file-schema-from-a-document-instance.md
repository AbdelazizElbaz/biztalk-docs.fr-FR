---
title: "Procédure pas à pas : Création d’un schéma de fichier plat à partir d’une Instance de Document | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5e1453f-0380-4505-97a9-9d3526db0923
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9077e8c8b878b3e24319ef112eb391a3eaf4e0ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-flat-file-schema-from-a-document-instance"></a>Procédure pas à pas : Création d’un schéma de fichier plat à partir d’une Instance de Document
Cette procédure vous indique comment créer un schéma de fichier plat à partir d'instances de document à l'aide de l'Assistant Schéma de fichier plat BizTalk, sur la base de l'exemple de bon de commande suivant. Pour une présentation de l’Assistant schéma de fichier plat BizTalk, consultez [l’Assistant schéma de fichier plat utilisez BizTalk](../core/how-to-use-biztalk-flat-file-schema-wizard.md).  
  
 ![Exemple de bon de commande](../core/media/flatfileschema-samplepurchaseorder.gif "FlatFileSchema_SamplePurchaseOrder")  
  
 Chaque ligne du bon de commande se termine par un caractère de retour chariot avec changement de ligne (CRLF) marqué en vert. Le bon de commande commence par une balise PO marquée en rouge et suivie d'une date. Deux champs positionnel fixes répétés apparaissant en violet contiennent des informations sur le client. Après le champ de commentaire, il existe un champ répété commençant par une balise ITEMS qui contient plusieurs enregistrements, séparés par des virgules (,) et les valeurs de données séparées par des canaux (&#124;), qui sont indiqué en bleu.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de vous entraîner à effectuer cette procédure, assurez-vous que les logiciels suivants sont installés et configurés sur votre serveur :  
  
-   Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec la **outils de développement** installé
  
 Pour préparer l’instance de document pour la procédure pas à pas, copiez le texte suivant dans un éditeur de texte et enregistrez-le dans un fichier texte. Veillez à copier la ligne tous les flux et les retours chariot.  
  
```
PO1999-10-20
US        Alice Smith         123 Maple Street    Mill Valley    CA 90952
US        Robert Smith        8 Oak Avenue        Old Town       PA 95819
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric

```

  
## <a name="start-the-wizard"></a>Démarrer l’Assistant  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le **l’Explorateur de solutions**.  
  
2.  Pour ajouter le nouveau schéma de fichier plat, cliquez sur le projet, puis sélectionnez **ajouter**. Cliquez sur **un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** fenêtre, procédez comme suit :  
  
    1.  Dans le **catégories** section, sélectionnez **les fichiers de schéma**.  
  
    2.  Dans le **modèles** section, sélectionnez **Assistant schéma de fichier plat**.  
  
    3.  Dans le **nom** , entrez **PurchaseOrder.xsd** pour le nouveau schéma.  
  
    4.  Cliquez sur **Ajouter**.  
  
4.  Lorsque l'Assistant Schéma de fichier plat BizTalk s'ouvre, la page Bienvenue apparaît.   
    Pour ignorer cet écran lors de l’exécution de l’Assistant à l’avenir, activez la **ne plus afficher cette page d’introduction** boîte. Cliquez sur **Suivant** pour continuer.  
  
## <a name="selecting-purchase-order-instance"></a>Sélection d’instance de bon de commande  
  
-   Sur le **informations de schéma de fichier plat** écran, sélectionnez votre instance et entrez les informations suivantes. Lorsque vous avez terminé, cliquez sur **suivant** pour continuer.  
  
    -   **Fichier de l’instance :** cliquez sur le **Parcourir** pour rechercher le fichier plat à partir de laquelle le schéma sera généré. Accédez au dossier contenant le fichier texte que vous avez créé dans la section conditions préalables de la procédure pas à pas : création d’un schéma dans un Document Instance de fichier plat.  
  
    -   **Nom de l’enregistrement :** Type **PO** car elle sera le nom racine du schéma.  
  
    -   **Espace de noms cible :** Type **http://Flat_File_Project.PurchaseOrder** pour l’espace de noms de schéma cible.  
  
    -   **Page de codes :** sélectionnez **UTF-8 (65001)** à partir de la liste déroulante.  
  
    -   **Compter les positions par octet :** cette case à cocher si vous souhaitez compter les champs de données positionnels par octets. Par défaut, les champs de données positionnel sont comptés en caractères. Dans cette procédure pas à pas, laissez le **compter les positions par octet** case à cocher est désactivée.  
  
## <a name="select-purchase-order-data"></a>Sélectionnez les données des bons de commande  
  
-   Sur le **sélectionner des données du Document** écran, le contenu du fichier plat sont affichés. Sélectionnez les données nécessaires pour la création du schéma, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Si vous souhaitez utiliser l’instance de la totalité du document, vous pouvez appuyer sur **Ctrl-A** pour sélectionner tous.  
  
    > [!NOTE]
    >  Vérifiez **retour longues lignes automatique** si vous souhaitez afficher le contenu de l’instance tout document encapsulé dans la zone d’édition dans l’ensemble de l’Assistant.  
  
    > [!NOTE]
    >  Si vous créez le schéma à partir d'une instance d'échange, sélectionnez seulement la partie qui représente la structure de document individuel.  
  
## <a name="delimit-purchase-order-record"></a>Délimiter l’enregistrement de bon de commande  
  
-   Comme chaque ligne du bon de commande se termine par un retour chariot de saut de ligne (CRLF), sélectionnez **par symbole délimiteur**, puis cliquez sur **suivant** sur **sélectionner le Format d’enregistrement** écran.  
  
## <a name="specify-purchase-order-record-property"></a>Spécifiez la propriété de l’enregistrement bon ordre  
  
-   Sur le **enregistrement délimité** écran, entrez la commande suivante pour définir le premier niveau du schéma et lorsque vous avez terminé, cliquez sur **suivant**.  
  
    -   **Délimiteur enfant :** sélectionnez **{CR} {LF}**.  
  
        > [!NOTE]
        >  **Délimiteur enfant** propriété est une zone modifiable avec liste déroulante contient un ensemble de valeurs par défaut. Le **délimiteur enfant** peut être spécifié comme un caractère ou d’une valeur hexadécimale. Par exemple,  **\\{** ou **{0x0D0A}**.  
  
    -   **Caractère d’échappement :** un caractère d’échappement est un caractère unique qui supprime toute signification particulière du caractère qui le suit. Consultez [caractères d’échappement](../core/escape-characters.md) pour plus d’informations. Ne spécifiez pas de caractère d'échappement pour la procédure pas à pas.  
  
        > [!NOTE]
        >  Lorsque vous utilisez  **\\** , **{,** et **}** pour **délimiteur enfant** ou **caractère d’échappement**, un barre oblique inverse doit être utilisée. Par exemple,  **\\ \\,** et  **\\{**.  
  
    -   Vérifiez **enregistrement comporte un identificateur de balise** et tapez **PO** dans **balise**. Dans un fichier à enregistrements multiples, **PO** doit servir à identifier chaque enregistrement individuel. Cliquez sur **Suivant** pour continuer.  
  
     ![Écran enregistrement délimité](../core/media/flatfileschemawizard-delimitedrecord1.gif "FlatFileSchemaWizard_DelimitedRecord1")  
  
## <a name="define-the-element-in-the-purchase-order-record"></a>Définir l’élément dans l’enregistrement de bon de commande  
  
1.  L'Assistant a identifié quatre éléments dans l'enregistrement de bon de commande ; vous devez maintenant définir la propriété des éléments. Dans la première ligne, effectuez les opérations suivantes :  
  
    1.  Type **date** pour le **nom de l’élément**.  
  
    2.  Sélectionnez **fieldelement** pour **le Type d’élément**.  
  
    3.  Sélectionnez **date** dans la liste de sélection déroulante pour **Type de données**.  
  
2.  Répétez les étapes a à c pour les éléments suivants. Lorsque vous avez terminé, cliquez sur **suivant**.  
  
    |Nom de l’élément|Type d’élément|Type de données|  
    |------------------|------------------|---------------|  
    |**client**|**Enregistrement répété**||  
    ||**Ignorer**||  
    |**éléments**|**Enregistrement**||  
  
     ![Écran d’éléments enfants](../core/media/flatfileschemawizard-childelements.gif "FlatFileSchemaWizard_ChildElements")  
  
    > [!NOTE]
    >  Vous pouvez sélectionner plusieurs lignes et modifiez leurs **le Type d’élément** à un seul type à l’aide de la souris et la touche MAJ ou CTRL.  
  
    > [!NOTE]
    >  Après avoir cliqué sur **suivant** sur la **des éléments enfants** écran, vous ne pourrez cliquer sur **retour** pour redéfinir ou apporter des modifications aux éléments enfants. Vous devrez alors probablement fermer l'Assistant et le relancer pour définir le schéma de fichier plat.  
  
3.  À la fin de cette procédure, le premier niveau du schéma est généré comme indiqué dans les captures d'écran suivantes. Trois éléments uniques sont définis et vous poursuivrez la définition des enregistrements enfants pour les éléments de l'enregistrement de bon de commande. Cliquez sur **Suivant**.  
  
     ![Écran : exemple de schéma](../core/media/flatfileschemawizard-schema1.gif "FlatFileSchemaWizard_Schema1")  
  
## <a name="define-the-customer-record"></a>Définir l’enregistrement de client  
  
1.  Étant donné que nous avons défini le **client** élément en tant que le **enregistrement répété** type et la **éléments** élément en tant que le **enregistrement** BizTalk, tapez Assistant schéma de fichier plat continue à définir ces deux éléments. Sur le **vue schéma** écran, sélectionnez **client**, puis cliquez sur **suivant** pour continuer.  
  
2.  Pour utiliser l'enregistrement customer, vous devez sélectionner les données représentant cet élément. Cet enregistrement étant un enregistrement répété, l'une ou l'autre des lignes peut être utilisée pour définir l'enregistrement. Sélectionnez la première ligne des données client, cliquez sur **suivant** pour continuer.  
  
3.  Sur le **sélectionner le Format d’enregistrement** , sélectionnez **par positions relatives**, puis cliquez sur **suivant**.  
  
4.  L'Assistant fournit un outil visuel permettant d'afficher ou de calculer la distance entre les champs. Sur le **enregistrement positionnel** page, utilisez le bouton gauche de la souris pour cliquer sur le marqueur de position 10 pour représenter où le champ de nom commence. Cliquez sur les marqueurs de position suivants pour représenter le reste des champs de données :  
  
    |Nom du champ|Marqueur de position|  
    |----------------|---------------------|  
    |street|30|  
    |city|50|  
    |state|65|  
    |postalcode|68|  
  
     Cliquez sur **Suivant** pour continuer.  
  
     ![Écran enregistrement positionnel](../core/media/flatfileschemawizard-positionalrecord.gif "FlatFileSchemaWizard_PositionalRecord")  
  
5.  Sur le **des éléments enfants** page, vous spécifiez les propriétés des éléments enfants. Sélectionnez la première ligne et tapez **pays** comme le **nom de l’élément**. Conservez les valeurs par défaut dans les autres colonnes. Tapez les valeurs suivantes pour les autres propriétés pour le **nom de l’élément**:  
  
    |Nom de l’élément|Valeur|  
    |------------------|-----------|  
    |**customer_Child2**|**nom complet**|  
    |**customer_Child3**|**rue**|  
    |**customer_Child4**|**Ville**|  
    |**customer_Child5**|**état**|  
    |**customer_Child6**|**code postal**|  
  
     Cliquez sur **Suivant** pour continuer.  
  
     ![Écran d’éléments enfants](../core/media/flatfileschemawizard-childelements2.gif "FlatFileSchemaWizard_ChildElements2")  
  
6.  Les éléments enfants de l'enregistrement customer sont créés comme indiqué dans la capture d'écran suivante. Cliquez sur **suivant** pour définir les éléments enfants pour l’enregistrement items.  
  
     ![Écran : exemple de schéma](../core/media/flatfileschemawizard-schema2.gif "FlatFileSchemaWizard_Schema2")  
  
#### <a name="define-the-items-record"></a>Définir l’enregistrement items  
  
1.  Sur le **vue schéma** page, sélectionnez **éléments**, puis cliquez sur **suivant**.  
  
2.  Sur le **sélectionner des données du Document** page, sélectionnez la ligne entière commençant par ITEMS, puis cliquez sur **suivant** pour définir ses éléments enfants.  
  
3.  Sur le **sélectionner le Format d’enregistrement** , sélectionnez **par symbole délimiteur**, puis cliquez sur **suivant**.  
  
4.  Dans l'enregistrement Items, les virgules sont utilisées pour délimiter les éléments. Par conséquent, sur le **enregistrement délimité** , entrez la commande suivante pour définir l’enregistrement items. Lorsque vous avez terminé, cliquez sur **suivant**.  
  
    -   Sélectionnez **,** de **délimiteur enfant** liste de sélection de liste déroulante.  
  
    -   Laissez le **caractère d’échappement** zone de texte vide.  
  
    -   Sélectionnez **enregistrement comporte un identificateur de balise** et type **éléments** dans **balise**.  
  
         Dans un enregistrement items multiple, **éléments** est utilisé pour identifier chaque enregistrement individuel.  
  
5.  En utilisant les valeurs à partir de la **enregistrement délimité** page, l’Assistant identifie deux éléments enfants. Un d’eux étant un enregistrement répété, sélectionnez le premier élément et entrez **élément** pour le nom de l’élément, puis sélectionnez **enregistrement répété** dans la liste déroulante la liste de sélection pour **le Type d’élément** . Conservez les autres valeurs par défaut dans les colonnes. Sélectionnez la deuxième ligne et sélectionnez le **ignorer** de **le Type d’élément** liste. Lorsque vous cliquez sur **suivant**, le niveau suivant pour l’enregistrement items est créé dans le schéma. Vous continuez à définir la partie finale du schéma de bon de commande.  
  
6.  Sélectionnez **élément** puis cliquez sur **suivant** pour continuer sur le **vue schéma** page.  
  
7.  Sur le **sélectionner des données du Document** , sélectionnez **ITEM872-AA &#124; TONDEUSE &#124; 1 &#124; 148.95 &#124; Confirmer qu’il se**. Cliquez sur **Suivant** pour continuer.  
  
8.  Sur le **sélectionner le Format d’enregistrement** , sélectionnez le **par symbole délimiteur** option car l’élément individuel est délimité par une barre verticale (&#124;).  
  
9. Sur le **enregistrement délimité** , entrez la commande suivante pour définir l’enregistrement de l’élément. Lorsque vous avez terminé, cliquez sur **suivant**.  
  
    -   Sélectionnez **&#124;** à partir de la **délimiteur enfant** liste déroulante.  
  
    -   Laissez le **caractère d’échappement** zone de texte vide.  
  
10. Sur le **des éléments enfants** page, l’Assistant a identifié cinq éléments enfants. Sélectionnez la première ligne, puis entrez **productCode** pour **nom de l’élément**. Laissez les valeurs par défaut dans le reste des colonnes. Pour le reste de la **propriétés de nom de l’élément**, tapez la commande suivante :  
  
    |Nom de l’élément|Valeur|  
    |------------------|-----------|  
    |**item_Child2**|**Description**|  
    |**item_Child3**|**quantité**|  
    |**item_Child4**|**prix unitaire**|  
    |**item_Child5**|**Notes**|  
  
     Cliquez sur **Suivant** pour continuer.  
  
11. Vous avez défini tous les nœuds pour le schéma de bon de commande. Sur le **vue schéma** , cliquez sur **Terminer**.  
  
12. Vous pouvez maintenant afficher le schéma de bon de commande final. Vous pouvez également affiner le schéma à l'aide de l'Éditeur de schéma BizTalk. Consultez la table de noms de propriété de fichier plat et les tables de propriétés dans **propriétés de nœud de schéma**. Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="summary"></a>Résumé  
 Dans cette procédure pas à pas, vous avez appris à utiliser l'Assistant Schéma de fichier plat BizTalk pour créer un schéma de fichier plat à partir d'une instance de document.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
### <a name="validate-po-instance"></a>Valider l’Instance de bon de commande  
 Pour vous assurer que le schéma PurchaseOrder.xsd peut analyser correctement l'instance de bon de commande, procédez comme indiqué ci-dessous :  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **PurchaseOrder.xsd** , puis sélectionnez **propriétés**.  
  
2.  Dans le **Pages de propriétés**, assurez-vous que le **nom de fichier d’entrée Instance** champ pointe vers l’emplacement de l’instance de bon de commande que vous avez créé dans la section conditions préalables de la procédure pas à pas : création d’un fichier plat Schéma à partir d’une Instance de Document. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
3.  Dans l’Explorateur de solutions, cliquez sur **PurchaseOrder.xsd**, puis sélectionnez **valider l’Instance**. Le composant de validation s'ouvre.  
  
4.  Une fois la validation terminée, un lien vous est fourni pour afficher la sortie XML en fonction du résultat de l'analyse sur l'instance de bon de commande à l'aide du schéma PurchaseOrder.xsd. Pour afficher la sortie XML, appuyez sur Ctrl, puis cliquez sur le lien.  
  
### <a name="create-pipelines-for-the-schema"></a>Créer des Pipelines pour le schéma  
 Vous pouvez maintenant créer un pipeline de réception ou d'envoi en fonction du schéma PurchaseOrder.xsd à utiliser avec votre application BizTalk.  
  
 Pour créer un pipeline, consultez [comment créer un Pipeline](../core/how-to-create-a-new-pipeline.md). Pour configurer les composants de Pipeline de fichier plat, voir [comment configurer le composant de Pipeline assembleur de fichier plat](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md) et [comment configurer le composant de Pipeline désassembleur de fichier plat](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser l’Assistant schéma de fichier plat BizTalk](../core/how-to-use-biztalk-flat-file-schema-wizard.md)   
 [Création de schémas à l’aide d’Assistant schéma de fichier plat BizTalk](../core/creating-schemas-using-biztalk-flat-file-schema-wizard.md)