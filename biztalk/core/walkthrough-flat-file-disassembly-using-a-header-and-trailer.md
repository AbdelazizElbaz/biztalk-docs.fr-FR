---
title: "Procédure pas à pas : Désassemblage de fichier plat à l’aide d’un en-tête et un code de fin | Documents Microsoft"
description: "Utilisez l’Assistant schéma de fichier plat pour créer un schéma d’en-tête, le schéma de code de fin et le schéma de corps, puis désassembler un fichier plat dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 715af9cc-d718-483d-b593-64462aa5a58b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e49014ac4c15f1fd303b2646c74f11b5242aed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-flat-file-disassembly-using-a-header-and-trailer"></a>Procédure pas à pas : Désassemblage de fichier plat à l’aide d’un en-tête et un code de fin

## <a name="overview"></a>Vue d'ensemble
Cette procédure pas à pas illustre l'utilisation de schémas créés par l'Assistant Schéma de fichier plat pour effectuer le désassemblage de fichier plat d'un fichier contenant un en-tête, un code de fin et un corps de message répété. Lors de cette procédure pas à pas, vous développez en partie un système de suivi des erreurs fictif répondant aux conditions suivantes :  
  
-   les messages d'erreur sont consignés dans divers sites physiques de l'entreprise, puis envoyés vers un emplacement central pour être traités par différents systèmes principaux ;  
  
-   les messages d'erreur sont écrits dans un format de fichier plat qui comprend un en-tête indiquant l'emplacement, un corps contenant un ou plusieurs messages d'erreur et un code de fin indiquant le numéro du lot ;  
  
-   les messages sont considérés comme non valides s'ils ne comportent ni en-tête, ni corps, ni code de fin.  
  
 Au terme de la procédure pas à pas, vous disposez d'une application BizTalk Server qui traite les fichiers plats et les convertit au format XML en vue de leur traitement par un système principal.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Cet exemple nécessite que vous soyez familiarisé avec la création de projets BizTalk, la signature d'un assembly et l'utilisation de la console Administration de BizTalk Server pour afficher les applications et les ports. Vous devez également être familiarisé avec les concepts présentés dans [procédure pas à pas : déploiement d’une Application BizTalk base](../core/walkthrough-deploying-a-basic-biztalk-application.md). Les notions de base de l'Assistant Schéma de fichier plat sont également utiles mais pas nécessaires.  
  
## <a name="what-this-example-does"></a>Ce que fait cet exemple  
 Cet exemple traite des messages de fichier plat entrants à l'aide d'un pipeline personnalisé et du composant Désassembleur de fichier plat. Les messages sont analysés à l'aide de schémas d'en-tête, de code de fin et de corps, puis écrits dans un emplacement d'envoi en vue du traitement principal.  
  
## <a name="example"></a>Exemple  
 Pour créer l'exemple, suivez les étapes présentées dans les sections ci-après.  
  
### <a name="create-a-new-biztalk-project"></a>Créez un projet BizTalk  
 Avant de concevoir une solution, vous devez créer un projet BizTalk, vous assurer qu'il porte un nom fort, puis lui attribuer un nom d'application. Attribuer un nom d'application empêche BizTalk Server de déployer la solution dans l'application BizTalk par défaut.  
  
1.  Créez un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Appelez le projet **FFDisassemblerWalkthrough**.  
  
2.  Générez un fichier de clé et attribuez-le au projet. Pour plus d’informations, consultez [Page signature, Concepteur de projets](http://go.microsoft.com/fwlink/?LinkId=125876).  
  
3.  Dans les propriétés de déploiement pour le projet, définissez **nom de l’Application** à « FlatFileExample » et affectez **redémarrer les Instances d’hôte** à `True`. La définition de cet indicateur indique à l'hôte d'effacer toutes les instances mises en cache de l'assembly.  
  
### <a name="create-the-sample-data-file"></a>Création du fichier de données exemple  
Avant de générer des schémas, vous devez créer un fichier de test.   
  
1.  Lancez le Bloc-notes ou un autre éditeur de texte.  
  
2.  Créer un exemple de fichier de test. Ce fichier est composé d'un en-tête indiquant l'emplacement qui signale les erreurs, d'un code de fin accompagné de l'ID de ce lot et d'un corps consistant en un ou plusieurs enregistrements Error. Le format du fichier est le suivant :  
  
    ```  
    Location  
    ERRORid|type|priority|description|errorDateTime  
    …additional error records   
    BatchID  
    ```  
  
    L’enregistrement ERROR est marqué avec le texte « Erreur » et délimité avec le « &#124; « caractère (et non pas positionnel). Les données qu'il contient sont décrites dans le tableau suivant.  
  
    |Élément|Type de données| Description|  
    |---|---|---|  
    |ID|entier|ID de l'erreur|  
    |Type|entier|Type d'erreur|  
    |Priorité|chaîne|Indicateur de priorité : haute, moyenne ou faible.|  
    | Description|chaîne|Description de l’erreur.|  
    |ErrorDateTime|DateTime|Date et heure auxquelles l'erreur s'est produite.|  
  
    Le fichier peut comporter un ou plusieurs enregistrements ERROR.  
  
     **--OU--**
  
     Copiez les données suivantes dans le nouveau fichier. La dernière ligne contient un saut de ligne de fin :
  
    ```  
    East Coast Facility  
    ERROR102|0|High|Sprocket query fails.|1999-05-31T13:20:00.000-05:00  
    ERROR16502|2|Low|Time threshold exceeded.|1999-05-31T13:20:00.000-05:00  
    8675309  
  
    ```  
  
3.  Enregistrez le nouveau fichier exemple dans le répertoire du projet. Nommez-le par exemple « ErrorFile.txt. ».  
  
### <a name="create-and-test-the-header-trailer-and-body-schemas"></a>Création et test des schémas d'en-tête, de code de fin et de corps  
 Une fois le fichier de données exemple créé, l'étape suivante consiste à créer les schémas d'en-tête, de code de fin et de corps. Ces schémas sont utilisés avec le composant de pipeline Désassembleur de fichier plat pour traiter les messages reçus.  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-header-schema"></a>Utilisez l’Assistant schéma de fichier plat pour créer le schéma d’en-tête  
  
1.  Ajoutez un nouveau schéma au projet. Dans l’Explorateur de solutions, cliquez sur **FFDisassemblerWalkthrough**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **les fichiers de schéma** et sélectionnez **Assistant schéma de fichier plat**. Nommez le nouveau schéma « Header.xsd », puis **ajouter**.  
  
3.  Sur le **Bienvenue dans l’Assistant schéma de fichier plat BizTalk** , cliquez sur **suivant**.  
  
4.  Sur le **informations de schéma de fichier plat** , cliquez sur **Parcourir** et recherchez le fichier de données exemple créé précédemment. Modifier la **nom de l’enregistrement** à « En-tête », vérifiez que la page de codes, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Si vous avez enregistré l'exemple de fichier au format Unicode, le format de la page de code est Little-Endian-UTF16 (1200). Ceci n'affecte pas l'exemple.  
  
5.  Sélectionnez ensuite les données du document. Sur le **sélectionner des données du Document** page, mettez en surbrillance la première ligne de données, notamment les caractères de nouvelle ligne {CR} et {LF} comme suit :  
  
     ![Données sélectionnées pour le schéma d’en-tête](../core/media/ffwiz-header-select-document-data.gif "ffwiz_header_select_document_data")  
  
     Cliquez sur **Suivant**.  
  
6.  Sur le **sélectionner le Format d’enregistrement** , cliquez sur **suivant** pour accepter la valeur par défaut. Vous pouvez accepter l'option « par symbole délimiteur » par défaut, car le fichier de données n'utilise pas de position relative.  
  
7.  Sur le **enregistrement délimité** , cliquez sur **suivant**.  
  
8.  À présent, spécifiez les éléments enfants. L'en-tête contient un élément nommé « Location » :  
  
     ![Nœud d’emplacement défini pour l’en-tête](../core/media/ffwiz-header-child-elements.gif "ffwiz_header_child_elements")  
  
     Cliquez sur **Suivant** pour continuer.  
  
9. Sur le **vue schéma** , vérifiez le schéma.  
  
     ![Schéma d’en-tête de vue de schéma illustrant terminée](../core/media/ffwiz-header-schema-view.gif "ffwiz_header_schema_view")  
  
     Lorsque vous êtes satisfait, cliquez sur **Terminer** pour terminer l’Assistant.  
  
10. Cliquez sur le  **\<schéma >** nœud dans le volet Schéma d’en-tête. Dans le volet Propriétés, modifiez **Element FormDefault** à **Qualified**. Vous indiquez ainsi que les éléments déclarés localement doivent être qualifiés par l'espace de noms cible dans un document d'instance.  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-trailer-schema"></a>Utilisez l’Assistant schéma de fichier plat pour créer le schéma de code de fin  
  
1.  Ajoutez un nouveau schéma au projet. Dans l’Explorateur de solutions, cliquez sur **FFDisassemblerWalkthrough**, pointez sur **ajouter** , puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **les fichiers de schéma** et sélectionnez **Assistant schéma de fichier plat**. Nommez le nouveau schéma « Trailer.xsd », puis **ajouter**.  
  
3.  Sur le **Bienvenue dans l’Assistant schéma de fichier plat BizTalk** , cliquez sur **suivant**.  
  
4.  Sur le **informations de schéma de fichier plat** , cliquez sur **Parcourir** et recherchez le fichier de données exemple créé précédemment. Modifier la **nom de l’enregistrement** par « Trailer », vérifiez que la page de codes, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Si vous avez enregistré l'exemple de fichier au format Unicode, le format de la page de code est Little-Endian-UTF16 (1200). Ceci n'affecte pas l'exemple.  
  
5.  Sélectionnez ensuite les données du document. Sur le **sélectionner des données du Document** page, sélectionnez la dernière ligne de données, notamment les caractères de nouvelle ligne {CR} et {LF} comme suit :  
  
     ![Les données sélectionnées pour le schéma de code de fin](../core/media/ffwiz-trailer-select-document-data.gif "ffwiz_trailer_select_document_data")  
  
     Cliquez sur **Suivant**.  
  
6.  Sur le **sélectionner le Format d’enregistrement** , cliquez sur **suivant** pour accepter la valeur par défaut. Vous pouvez accepter l'option « par symbole délimiteur » par défaut, car le fichier de données n'utilise pas de position relative.  
  
7.  Sur le **enregistrement délimité** , cliquez sur **suivant**.  
  
8.  À présent, spécifiez les éléments enfants. L'en-tête contient un élément nommé « BatchID » :  
  
     ![Nœud d’emplacement défini pour le code de fin](../core/media/ffwiz-trailer-child-elements.gif "ffwiz_trailer_child_elements")  
  
     Cliquez sur **Suivant** pour continuer.  
  
9. Sur le **vue schéma** , vérifiez le schéma.  
  
     ![Schéma de code de fin terminée affichant](../core/media/ffwiz-trailer-schema-view.gif "ffwiz_trailer_schema_view")  
  
     Lorsque vous êtes satisfait, cliquez sur **Terminer** pour terminer l’Assistant.  
  
10. Cliquez sur le  **\<schéma >** nœud dans le volet Schéma de code de fin. Dans le volet Propriétés, modifiez **elementFormDefault** à **Qualified**. Vous indiquez ainsi que les éléments déclarés localement doivent être qualifiés par l'espace de noms cible dans un document d'instance.  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-body-schema"></a>Utilisez l’Assistant schéma de fichier plat pour créer le schéma de corps  
  
1.  Ajoutez un nouveau schéma au projet. Dans l’Explorateur de solutions, cliquez sur **FFDisassemblerWalkthrough**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **les fichiers de schéma** et sélectionnez **Assistant schéma de fichier plat**. Nommez le nouveau schéma « Body.xsd », puis **ajouter**.  
  
3.  Sur le **Bienvenue dans l’Assistant schéma de fichier plat BizTalk** , cliquez sur **suivant**.  
  
4.  Sur le **informations de schéma de fichier plat** , cliquez sur **Parcourir** et recherchez le fichier de données exemple créé précédemment. Modifier la **nom de l’enregistrement** sur « Corps », vérifiez que la page de codes, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Si vous avez enregistré l'exemple de fichier au format Unicode, le format de la page de code est Little-Endian-UTF16 (1200). Ceci n'affecte pas l'exemple.  
  
5.  Sélectionnez ensuite les données du document. Sur le **sélectionner des données du Document** page, sélectionnez les lignes deux et trois des données, notamment les caractères de nouvelle ligne {CR} et {LF} comme suit :  
  
     ![Les données sélectionnées pour le schéma de corps](../core/media/ffwiz-body-select-document-data.gif "ffwiz_body_select_document_data")  
  
     Cliquez sur **Suivant**.  
  
6.  Sur le **sélectionner le Format d’enregistrement** , cliquez sur **suivant** pour accepter la valeur par défaut. Vous pouvez accepter l'option « par symbole délimiteur » par défaut, car le fichier de données n'utilise pas de position relative.  
  
7.  Sur le **enregistrement délimité** page, sélectionnez **suivant**.  
  
8.  Définissez ensuite les éléments enfants. Modification **Body_Child1** à **erreur**et définissez son type d’élément **enregistrement répété**. Définir le **Body_Child2** type d’enregistrement à élément **ignorer**.  
  
9. Sur le **vue schéma** , cliquez sur **suivant** pour définir les éléments enfants de l’enregistrement d’erreur.  
  
10. Sur le **sélectionner des données du Document** , cliquez sur **suivant**. L'Assistant choisit les données de définition d'enregistrement correctement.  
  
11. Sur le **sélectionner le Format d’enregistrement** , cliquez sur **suivant**. Les données sont formatées par symbole délimiteur.  
  
12. Sur le **enregistrement délimité** page, sélectionnez **&#124;** pour le **délimiteur enfant**. Ensuite, sélectionnez le **enregistrement comporte un identificateur de balise** et tapez **erreur** pour la valeur de balise.  
  
     ![Configuration délimitées enregistrement avec l’identificateur de balise](../core/media/ffwiz-bodyerror-delimited-record.gif "ffwiz_bodyerror_delimited_record")  
  
     Cliquez sur **Suivant**.  
  
13. Définissez à présent les éléments enfants de l'enregistrement Error.  
  
     ![Enregistrement d’erreur défini avec cinq éléments](../core/media/ffwiz-bodyerror-child-elements.gif "ffwiz_bodyerror_child_elements")  
  
     Cliquez sur **Suivant**.  
  
14. Sur le **vue schéma** , vérifiez le schéma.  
  
     ![Schéma de corps terminée affichant](../core/media/ffwiz-bodyerror-schema-view.gif "ffwiz_bodyerror_schema_view")  
  
     Si vous avez apporté des erreurs, cliquez sur **nouveau** et apporter les corrections nécessaires. Lorsque vous êtes satisfait, cliquez sur **Terminer** pour terminer l’Assistant.  
  
15. Cliquez sur le  **\<schéma >** nœud dans le volet Schéma de corps. Dans le volet Propriétés, modifiez **Element FormDefault** à **Qualified**. Vous indiquez ainsi que les éléments déclarés localement doivent être qualifiés par l'espace de noms cible dans un document d'instance.  
  
16. Cliquez sur le  **\<erreur >** nœud dans le volet Schéma de corps. Dans le volet Propriétés, modifiez **Max Occurs** à **1**. Le désassembleur de fichier plat fractionne alors chaque erreur dans son propre message.  
  
##### <a name="test-the-schemas-using-ffdasm"></a>Tester les schémas à l’aide de FFDasm  
  
1.  Ouvrez une invite de commandes et remplacez le répertoire par celui de votre projet.  
  
2.  À l'invite de commandes, exécutez FFDasm.exe comme suit.  
  
    ```  
    <Samples Path>\SDK\Utilities\PipelineTools\FFDasm ErrorFile.txt  -hs header.xsd -bs body.xsd -ts Trailer.xsd  
    ```  
  
     Pour plus d’informations sur l’emplacement de ce document et d’autres outils de pipeline, consultez [outils de Pipeline](../core/pipeline-tools.md).  
  
3.  FFDasm.exe génère normalement deux fichiers de sortie nommés {GUID}.xml, un pour chaque enregistrement ERROR du fichier de test. L'enregistrement Error prioritaire se présente comme suit :  
  
    ```  
    <Body xmlns="http://FFDisassemblerWalkthrough.Body">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails.</Description>  
        <DateTime>1999-05-31T13:20:00.000-05:00</DateTime>  
      </Error>  
    </Body>  
    ```  
  
### <a name="create-a-custom-receive-pipeline"></a>Création d'un pipeline de réception personnalisé  
 À présent que les schémas de fichier plat sont définis, vous devez créer un pipeline de réception personnalisé qui utilise le composant Désassembleur de fichier plat. Le composant Désassembleur de fichier plat peut ensuite être configuré pour utiliser les schémas d'en-tête, de corps et de code de fin afin de scinder les messages.    
 
1.  Ajoutez un nouveau pipeline de réception au projet. Dans l’Explorateur de solutions, cliquez sur le **FFDisassemblerWalkthrough** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, pointez sur **fichiers de Pipeline** puis cliquez sur **Pipeline de réception**. Nommez le nouveau pipeline « FFReceivePipeline », puis **ajouter**.  
  
3.  Configurez le nouveau pipeline en faisant glisser le composant Désassembleur de fichier plat du volet Boîte à outils vers l'étape Désassembler.  
  
4.  Dans le volet Propriétés, définissez la **schéma de Document** à **FFDisassemblerWalkthrough.Body**, le **schéma d’en-tête** à  **FFDisassemblerWalkthrough.Header** et **schéma de code de fin** à **FFDisassemblerWalkthrough.Trailer**.  
  
### <a name="deploy-the-application-and-configure-the-send-and-receive-ports"></a>Déploiement de l'application et configuration des ports d'envoi et de réception  
 Une fois les schémas et le pipeline de réception personnalisé créés, vous devez compiler et déployer le projet. Lorsque le projet est déployé, vous pouvez utiliser la console Administration de BizTalk Server pour configurer les ports d'envoi et de réception.  

##### <a name="deploy"></a>Déployer  
1.  Depuis [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], déployez la solution en cliquant sur le projet, puis cliquez sur **déployer**.  
  
2.  À l’aide de la console Administration de BizTalk Server, développez le **Applications** groupe pour vérifier que **FlatFileExample** est présent sous la forme d’une application personnalisée.  
  
##### <a name="configure-the-receive-port"></a>Configurer le port de réception  
  
1.  Utilisez l’Explorateur Windows pour créer un répertoire nommé « Receive » sous le **FFDisassemblerWalkthrough** répertoire du projet.  
  
2.  Dans la console Administration de BizTalk Server, développez le **FlatFileExample** application, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Unidirectionnel Port de réception**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, définissez le nom du port sur « ReceiveError ».  
  
4.  Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau** pour ajouter un emplacement de réception. Nommez le nouvel emplacement « ReceiveErrorLocation ». Définir le **Pipeline de réception** à **FFReceivePipeline**. Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**. Sélectionnez le répertoire de réception que vous avez créé et puis définissez la **masque de fichier** *.txt.  
  
5.  Cliquez sur **OK**. Votre port de réception devrait à présent être configuré. Cliquez sur **OK** à fermer.  
  
##### <a name="configure-the-send-port"></a>Configurer le port d’envoi  
  
1.  Utilisez l’Explorateur Windows pour créer un répertoire nommé « Send » sous le **FFDisassemblerWalkthrough** répertoire du projet.  
  
2.  Dans la console Administration de BizTalk Server, développez le **FlatFileExample** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur  **Port d’envoi unidirectionnel statique...** .  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, définissez le nom du port sur « Send ».  
  
4.  Pour le type de transport, sélectionnez **fichier**, puis cliquez sur **configurer**. Définissez le dossier de destination sur le répertoire d'envoi que vous avez créé auparavant.  
  
5.  Configurez à présent le filtre. Cliquez sur **filtres** et ajouter une expression :  
  
    -   BIZTALK SERVER. MessageType == **http://FFDisassemblerWalkthrough.Body#Body**  
  
6.  Cliquez sur **OK** pour terminer la configuration de port d’envoi. Votre port d'envoi devrait à présent être configuré.  
  
### <a name="run-the-example"></a>Exécution de l'exemple  
 Il est maintenant temps d'exécuter l'exemple. Après avoir utilisé la console Administration de BizTalk Server pour démarrer l’application, copiez les fichiers de test à l’emplacement de réception et observez le résultat produit dans l’emplacement d’envoi.  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur le **FlatFileExample** application, puis sur **Démarrer**. Il inscrit et démarre l’envoi et ports de réception.  
  
2.  Faites glisser la copie de l'exemple de fichier Errorfile.txt dans le répertoire de réception. Deux fichiers de sortie sont normalement écrits dans le répertoire d'envoi.  
  
