---
title: "Comment utiliser l’Assistant schéma de fichier plat BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cb8b18-266d-422e-bdb8-1efefb6b4c8e
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff7d87959bd39b9040a495022c2b7bf352954848
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-biztalk-flat-file-schema-wizard"></a>Utilisation de l'Assistant Schéma de fichier plat BizTalk
Dans les versions précédentes de BizTalk Server, vous deviez ajouter manuellement les annotations aux schémas XSD (XML Schema Definition language) dans l'Éditeur de schéma BizTalk pour rendre ces schémas compréhensibles par les composants de pipeline de fichier plat, tels que Désassembleur de fichier plat et Assembleur de fichier plat. Vous pouvez toujours procéder de cette manière à l'aide de l'Éditeur de schéma [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour réduire le nombre d'étapes manuelles et accélérer la création de solutions, utilisez l'Assistant Schéma de fichier plat BizTalk, qui offre les fonctionnalités suivantes :  
  
-   utilisation d'instances de fichier plat réelles comme entrées ;  
  
-   surface de conception visuelle pour le traitement des schémas de fichier plat délimité et positionnel ;  
  
-   processus réentrant basé sur un Assistant permettant d'ajouter des éléments au schéma et de définir des annotations associées au fichier plat de manière interactive ;  
  
-   prise en charge des identificateurs de balise et des délimiteurs sous forme de caractère et de valeur hexadécimale ;  
  
-   détermination automatique des décalages d'identificateur de balise et de l'ordre de délimitation des enfants ;  
  
-   fonctions de prévisualisation pour le format de fichier ;  
  
-   possibilité de sélectionner les sous-données privilégiées dans l'instance d'échange à utiliser pour définir les schémas de fichier plat.  
  
## <a name="how-to-start-the-biztalk-flat-file-schema-wizard"></a>Démarrage de l'Assistant Schéma de fichier plat BizTalk  
 Vous pouvez démarrer l'Assistant à partir de l'Explorateur de solutions Microsoft Visual Studio ou de l'Éditeur de schéma BizTalk.  
  
#### <a name="to-start-the-wizard-from-solution-explorer"></a>Pour démarrer l'Assistant à partir de l'Explorateur de solutions  
  
1.  Dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le **l’Explorateur de solutions**.  
  
2.  Pour ajouter le nouveau schéma de fichier plat, cliquez sur le projet BizTalk, puis sélectionnez **ajouter**.  
  
3.  Cliquez sur **un nouvel élément.**  
  
     ![Menu de l’Explorateur de solutions](../core/media/flatfileschemawizard-01.gif "FlatFileSchemaWizard_01")  
  
4.  Dans le **ajouter un nouvel élément** fenêtre, procédez comme suit :  
  
    1.  Dans le **catégories** section, sélectionnez **les fichiers de schéma**.  
  
    2.  Dans le **modèles** section, sélectionnez **Assistant schéma de fichier plat**.  
  
    3.  Dans le **nom** zone de texte, tapez un nom pour le nouveau schéma.  
  
    4.  Cliquez sur **Ajouter**.  
  
         L'Assistant Schéma de fichier plat BizTalk s'ouvre.  
  
#### <a name="to-start-the-wizard-from-the-schema-editor"></a>Pour démarrer l'Assistant à partir de l'Éditeur de schéma  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le **l’Explorateur de solutions**.  
  
2.  Pour ajouter le nouveau schéma de fichier plat, cliquez sur le projet BizTalk, puis sélectionnez **ajouter**. Sélectionnez **un nouvel élément** et cliquez sur **un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** fenêtre, procédez comme suit :  
  
    1.  Dans le **catégories** section, sélectionnez **les fichiers de schéma**.  
  
    2.  Dans le **modèles** section, sélectionnez **schéma de fichier plat**.  
  
    3.  Dans le **nom** zone de texte, tapez un nom pour le nouveau schéma.  
  
    4.  Cliquez sur **Ajouter**.  
  
    5.  Avec le bouton droit **racine** et sélectionnez **définir l’enregistrement à partir de l’Instance de fichier plat**.  
  
         L'Assistant Schéma de fichier plat BizTalk démarre.  
  
> [!NOTE]
>  Si vous avez un schéma de travail est ouvert dans l’éditeur de schéma, vous devez simplement est droit sur le nœud sélectionné, puis sélectionnez **définir l’enregistrement à partir de l’Instance de fichier plat**.  
  
> [!NOTE]
>  Le **définir l’enregistrement à partir de l’Instance de fichier plat** option est activée si le nœud sélectionné est un enregistrement sans éléments enfants. Si le nœud sélectionné comporte des éléments enfants, l'Assistant supprime tous les éléments enfants actuels et en crée de nouveaux. L'Assistant vous invite à confirmer la suppression des éléments enfants existants.  
  
## <a name="considerations-for-using-the-flat-file-schema-wizard"></a>Éléments à prendre en compte lors de l'utilisation de l'Assistant Schéma de fichier plat  
 Cette section décrit les problèmes à prendre en compte lors de l'utilisation de l'Assistant Schéma de fichier plat BizTalk.  
  
### <a name="working-with-multibyte-character-set-mbcs"></a>Utilisation du jeu de caractères multi-octets (MBCS)  
 Par défaut, le **compter les positions par octet** case à cocher est désactivée sur l’écran d’informations de schéma de fichier plat. L'Assistant compte les positions par caractère, ce qui signifie que si votre instance de fichier plat positionnel comporte des caractères MBCS, les positions ne sont pas comptées correctement. En sélectionnant le **compter les positions par octet** case à cocher, l’Assistant affiche les caractères MBCS avec une indication supplémentaire de leur longueur positionnelle. Le caractère occupe une position sur l'affichage et la longueur restante est remplie par des points « • ». Le nombre de symboles point remplis sera défini en fonction des fichiers enregistrés dans le format du jeu de caractères codés sur deux octets (DBCS), Unicode ou UTF-8.  
  
### <a name="code-pages-supported-in-the-flat-file-schema-wizard"></a>Pages de codes prises en charge dans l'Assistant Schéma de fichier plat  
 Les pages de codes prises en charge par l'Assistant sont listées ci-dessous :  
  
-   Arabe (1256)  
  
-   ASCII (20127)  
  
-   Baltique (1257)  
  
-   Big-Endian-UTF16 (1201)  
  
-   Europe centrale (1250)  
  
-   Cyrillique (1251)  
  
-   Grec (1253)  
  
-   Hébreu (1255)  
  
-   Japonais-Shift-JIS (932)  
  
-   Coréen (949)  
  
-   Little-Endian-UTF16 (1200)  
  
-   Chinois simplifié GBK (936)  
  
-   Chinois simplifié GB18030 (54936)  
  
-   Thaï (874)  
  
-   Chinois traditionnel BIG5 (950)  
  
-   Turc (1254)  
  
-   UTF-7 (65000)  
  
-   UTF-8 (65001)  
  
-   Vietnamien (1258)  
  
-   Europe occidentale (1252)  
  
### <a name="record-types-in-the-flat-file-schema-wizard"></a>Types d'enregistrement dans l'Assistant Schéma de fichier plat  
 Les fichiers plats ne peuvent pas contenir d'enregistrements délimités à l'intérieur d'enregistrements positionnels. L’Assistant étant réentrant basé, les cases d’option qui définissent le type de la **par symbole délimiteur** et **par positions relatives** sont activées ou désactivées selon le format des enregistrements parents pour l’enfant que vous définissez dans l’Assistant. Par exemple :  
  
-   Si l'Assistant est exécuté pour un enfant d'un enregistrement délimité, les deux cases d'option sont sélectionnées.  
  
-   Si l’Assistant est exécuté pour un enfant d’un enregistrement positionnel, la **par symbole délimiteur** case d’option est désactivée.  
  
### <a name="delimiter-symbols-in-the-flat-file-schema-wizard"></a>Symboles délimiteurs dans l'Assistant Fichier de schéma plat  
 La liste déroulante des propriétés de délimiteur enfant contient les délimiteurs communs suivants :  
  
-   {CR}{LF}  
  
-   {CR}  
  
-   {LF}  
  
-   {TAB}  
  
-   {ESPACE}  
  
-   {0x1A}  
  
-   &#124;  
  
-   ,  
  
-   ;  
  
 La valeur par défaut pour cette propriété est {CR}{LF}. La propriété est également une zone de texte modifiable, qui vous permet de spécifier le délimiteur enfant en tant que séquence de caractères ou comme valeurs hexadécimales des caractères. « une » ou « rue » sont des exemples d'utilisation de caractères pour le délimiteur enfant. Les délimiteurs hexadécimaux sont spécifiés selon le format suivant :  
  
-   {0xnnnn} : par exemple, {0x0D}{0x0A}, {0x09} ou {0x20}.  
  
 Voici un exemple d'utilisation de séquence de valeurs hexadécimales : {0x0D}{0x0A}, {0x09}{0x20}.  
  
 Si vous utilisez les symboles \\, {, ou} comme délimiteur, vous devez placer un symbole de barre oblique inverse supplémentaire devant le symbole de délimiteur, sinon vous recevrez un message d’erreur. Par exemple :  
  
-   \\\\, \\{, ou \\}.  
  
### <a name="relative-positions-in-the-flat-file-schema-wizard"></a>Positions relatives dans l'Assistant Schéma de fichier plat  
  
#### <a name="setting-position-markers"></a>Définition des marqueurs de position  
 Cliquez sur un marqueur de position dans la zone de sélection de la position pour déterminer la nouvelle ligne de marqueur de position. Le marqueur de position est représenté sous la forme d'un trait plein. Par défaut, une ligne de marqueur de position figure au début de l'enregistrement à la position zéro. Pour supprimer une ligne de marqueur de position existante, cliquez dessus.  
  
### <a name="escape-characters-in-the-flat-file-schema-wizard"></a>Caractères d'échappement dans l'Assistant Schéma de fichier plat  
 Un caractère d'échappement est un caractère unique qui supprime toute signification du caractère qui le suit. Pour plus d’informations, consultez [caractères d’échappement](../core/escape-characters.md) rubrique sous [comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md). Vous utilisez la propriété de caractère d'échappement dans l'Assistant pour indiquer le caractère d'échappement à utiliser lors de l'analyse de l'instance de fichier plat. La valeur par défaut est Null, ce qui signifie que le caractère d'échappement par défaut défini au niveau du schéma est utilisé.  
  
 Le caractère d'échappement peut être spécifié sous forme de caractère ou de valeur hexadécimale. La valeur hexadécimale est indiquée selon le format suivant :  
  
-   {0xnnnn} : par exemple, {0x0D}{0x0A}, {0x09} ou {0x20}  
  
 Si vous utilisez les symboles \\, {, ou} comme caractère d’échappement, vous devez placer un symbole de barre oblique inverse supplémentaire devant le symbole de délimiteur, sinon vous recevrez un message d’erreur, par exemple,  
  
-   \\\\, \\{, \\}.  
  
### <a name="child-elements-in-the-flat-file-schema-wizard"></a>Éléments enfants dans l'Assistant Schéma de fichier plat  
 Chaque élément enfant contient **nom de l’élément**, **le Type d’élément**, **Type de données** et **contenu**. Vous utilisez la **nom de l’élément** zone de texte, tapez un nom explicite pour le nœud. Le **le Type d’élément** est une liste déroulante avec les valeurs suivantes :  
  
-   **Élément de champ**: Spécifie que ce nœud sera créé dans le schéma en tant qu’élément.  
  
-   **Attribut de champ**: Spécifie que ce nœud sera créé dans le schéma en tant qu’attribut.  
  
-   **Enregistrement**: Spécifie qu’un enregistrement sans enfants sera créé dans le schéma.  
  
-   **Enregistrement répété**: Spécifie qu’un enregistrement sans enfants sera créé dans le schéma et son occurrence maximale est définie sur **Unbounded**.  
  
-   **Ignorer**: rien ne sera créé dans le schéma de ce nœud.  
  
 Par défaut, tous les éléments sont de type **fieldelement** et leur type de données est **chaîne**.  
  
> [!NOTE]
>  Un élément enfant peut être déclaré comme un **attribut de champ** uniquement s’il n’existe pas d’enfants avant qu’il qui sont déclarés comme **champ éléments**, **enregistrement** ou  **Enregistrement répété**.  
  
> [!NOTE]
>  Vous verrez un point d’exclamation devant le **nœuds enfants** dans les cas suivants :  
  
-   Le **attribut de champ** est défini après **fieldelement**, **enregistrement,** ou **enregistrement répété**.  
  
-   L'élément enfant n'a pas de nom.  
  
-   L'élément enfant a un nom en double.  
  
-   Le type de données sélectionné pour l'élément enfant n'est pas adapté au contenu.  
  
## <a name="see-also"></a>Voir aussi  
 [Description de l’Assistant schéma fichier plat BizTalk](../core/biztalk-flat-file-schema-wizard-walkthrough.md)