---
title: Utiliser des fichiers de liaison pour importer ou exporter | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9a2a82a-f8d4-4ec2-b8c1-be6cda3f993a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3707726eb9e8e77e0536f36700fe098d83ad414
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-binding-files-to-import-or-export"></a>Utiliser des fichiers de liaison pour importer ou exporter

En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], vous pouvez exporter et importer des fichiers de liaison à la **Parties** et **accord** niveaux. Pour les versions précédentes de BizTalk, vous exportez au niveau de l’application, comme décrit dans : 

* [Comment exporter des liaisons pour une Solution EDI AS2](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [Comment importer des liaisons pour une Solution EDI-AS2](../core/how-to-import-bindings-for-an-edi-as2-solution.md)

Cette rubrique vous montre comment importer et exporte les parties, leurs profils, accords, les paramètres de secours et à l’aide de plusieurs [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] et BTSTask. 

## <a name="overview"></a>Vue d'ensemble

Voici quelques-unes des fonctionnalités d’importation et d’exportation :

* Importer des tiers, des profils d’entreprise et des accords à partir d’un fichier de liaison XML
* Exporter les tiers, profils d’entreprise, des contrats et les paramètres de secours EDI dans un fichier de liaison XML
* Lorsque vous importez un fichier de liaison, vous pouvez choisir n’importe ne pas les parties ou les paramètres de secours
* Lors de l’importation au niveau du tiers, uniquement les parties et les accords dans le fichier de liaison sont importées.
* Exporter des tiers spécifiques dans le même fichier de liaison, puis choisissez d’exporter également tous les accords associés à ces parties
* L’Assistant Liaison importer l’application vous permet de choisir d’importer les paramètres de suivi ou exclure les parties.
* BTSTask inclut la `ImportParties` et `ExportParties` commandes 

## <a name="prerequisites"></a>Conditions préalables

* Vous devez être connecté avec un compte qui est membre de la ** groupe Administrateurs de BizTalk Server **. Consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  

* Vous devez avoir ajouté une référence à la **Application EDI BizTalk** à partir d’une application BizTalk qui sera utilisée comme une application EDI. Consultez [post-configuration étapes](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).

## <a name="import-or-export-all-the-trading-partners"></a>Importer ou exporter tous les partenaires commerciaux
1. Ouvrez  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]** , développez le groupe BizTalk.
2. Avec le bouton droit **Parties**, puis sélectionnez **exporter**. 

    Lorsque vous exportez à la **parties**-niveau, vous exportez tous les partenaires commerciaux. Cette opération exporte également tous les éléments utilisés par les partenaires commerciaux, y compris les profils d’entreprise et des accords dans un fichier XML. 

3. Avec le bouton droit **Parties**, sélectionnez **importation**, puis sélectionnez le fichier XML de liaison. 

      Choisissez de **exclure les Parties**, ou **exclure des paramètres de secours EDI** afin qu’ils ne sont pas importés. Dans le cas contraire, tous les éléments dans le fichier de liaison sont importé, y compris les partenaires, profils d’entreprise et des accords commerciaux.     

### <a name="btstask-example"></a>Exemple de BTSTask

`BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

Consultez [ImportParties commande](../core/importparties-command.md).

    
## <a name="export-individual-partners"></a>Exporter des partenaires
1. Dans  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]** , sélectionnez **Parties**.
2. Dans le **tiers et profils d’entreprise** volet, avec le bouton droit à un tiers, puis sélectionnez **exporter**.

    Lorsque vous exportez un tiers spécifique, vous êtes proposé pour exporter toutes les parties et tous les contrats utilisés par ce tiers. Vous pouvez désactiver **exporter tiers sélectionnés et tous les contrats dans les parties sélectionnées** pour exporter uniquement la partie que vous sélectionnez.

3. Sélectionnez **OK**. 

> [!TIP]
> Dans le **tiers et profils d’entreprise** volet, vous pouvez également utiliser le **CTRL** et **MAJ** enfoncée pour sélectionner plusieurs parties dans la liste. Tous les tiers que vous sélectionnez Exporter dans le même fichier de liaison.

### <a name="btstask-example"></a>Exemple de BTSTask

`BTSTask ExportParties -Destination:"C:\Temp\MyParties.Xml"`

Consultez [ExportParties commande](../core/exportparties-command.md).


## <a name="import-application-binding-file"></a>Fichier de liaison d’application importation

Au niveau de l’application, vous pouvez importer un fichier de liaison avec des tiers EDI et AS2. 

1. Dans  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]** , développez **Applications**
2. Avec le bouton droit de votre application, puis sélectionnez **importation**.
3. **Importer des paramètres de suivi** et **exclure les Parties** options sont disponibles. À l’aide de ces options, vous pouvez choisir Importer les paramètres de suivi existants ou exclure des parties EDI/AS2 dans le fichier de liaison.

    | Paramètre | Détails |
    |---|---|
    |**Importer les paramètres de suivi** | Importe les paramètres de suivi activés sur les différents artefacts dans l’application, telles que le corps de message de suivi et suivre les événements. <br/><br/>Activé par défaut pour garantir la compatibilité descendante. |
    | **Exclure les Parties**|Effectue pas les parties d’importation, les profils et accords existants dans le fichier. <br/><br/>Cette option est désactivée par défaut pour garantir la compatibilité descendante.|

     > [!IMPORTANT] 
     > Les paramètres de suivi global remplacent **importer les paramètres de suivi**. Par conséquent, si vous avez désactivé le suivi au niveau global de niveau, tout le suivi de paramètres ne sont pas importés, même si **importer les paramètres de suivi** est activée.
     > 
     > **Panneau de configuration de BizTalk, Page groupe** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] explique le **autoriser l’importation des paramètres de suivi** paramètre global.

### <a name="btstask-example"></a>Exemple de BTSTask

`BTSTask ImportBindings -ApplicationName:MyApplication -Source:C:\Bindings\Binding1.xml -ImportTrackingSettings:true`

Consultez [commande ImportBindings](../core/importbindings-command.md).

## <a name="in-this-section"></a>Contenu de cette section
Pour importer ou exporter des fichiers de liaison EDI et AS2 sur les versions précédentes de BizTalk, consultez : 

* [Comment exporter des liaisons pour une Solution EDI AS2](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [Comment importer des liaisons pour une Solution EDI-AS2](../core/how-to-import-bindings-for-an-edi-as2-solution.md)
