---
title: Extension du Mappeur (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Mapper, examples
- XML tools
- BizTalk Mapper, extending
- examples, BizTalk Mapper
- examples, XML tools
ms.assetid: 6010a13f-b715-4766-ad91-5aa9b98589e3
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b2b4538d8bff60330de24f00b6565ed43a9c079
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="extending-mapper-biztalk-server-sample"></a>Extension du Mappeur (exemple BizTalk Server)
L'exemple Extending Mapper présente l'utilisation et l'extension du Mappeur BizTalk. L'exemple inclut plusieurs fichiers de mappage (.btm) [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], chacun illustrant des aspects différents du Mappeur BizTalk.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L'exemple Extending Mapper s'appuie sur le routage basé sur le contenu et n'utilise pas d'orchestration. En spécifiant un filtre sur l'exemple de port d'envoi, il est connecté directement à l'exemple de port de réception. Un mappage est spécifié sur le port d'envoi à appliquer au document traité.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\XmlTools\ExtendingMapper  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|MapperClassLibrary\AssemblyInfo.cs, MapperClassLibrary\MapperClassLibrary.csproj, MapperClassLibrary\MapperHelper.cs, MapperClassLibrary\MapperClassLibrary.sln|Fichier de projet Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]® et fichiers sources Visual C#®.|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC).|  
|Destination.xsd|Fichier de schéma.|  
|ExtendingMapper.btproj, ExtendingMapper.sln|Fichiers de projet et de solution BizTalk pour cet exemple.|  
|ExtendingMapper.xml|Fichier XML source.|  
|ExtendingMapperBinding.xml|Fichier XML de liaison.|  
|ExternalAssembly.xml|Fichier XML d'assembly externe.|  
|OverridingMapXslt.btm|Fichier de mappage.|  
|OverridingMapXslt.xml|Fichier XML de mappage de remplacement.|  
|OverridingMapXslt.xslt|Feuille de style de mappage de remplacement.|  
|Scriptor_CallExternalAssembly.btm|Exemple de fichier de mappage.|  
|Scriptor_GlobalVariableInInlineScript.btm|Exemple de fichier de mappage.|  
|Scriptor_InlineScripts.btm|Exemple de fichier de mappage.|  
|Scriptor_InlineXslt.btm|Exemple de fichier de mappage.|  
|Scriptor_InlineXsltCallingExternalAssembly.btm|Exemple de fichier de mappage.|  
|Scriptor_XsltCalltemplate.btm|Exemple de fichier de mappage.|  
|Setup.bat|Utilisé pour créer et initialiser l'exemple.|  
|Source.xsd|Fichier de schéma.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 La procédure suivante permet de créer et d'initialiser l'exemple Extending Mapper.  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, accédez au répertoire (**cd**) dans le dossier suivant :  
  
     *\<Exemples de chemin d’accès\>*\XmlTools\ExtendingMapper  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (\In) et de sortie (\Out) pour cet exemple  
  
    -   Compilation et déploiement du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
     Si vous voulez utiliser le mappage Scriptor_CallExternalAssembly.btm ou Scriptor_InlineXsltCallingExternalAssembly.btm, ouvrez ExtendingMapper.sln dans Visual Studio et apportez les modifications suivantes (sinon, passez à l'étape 3) :  
  
    1.  Dans l'Explorateur de solutions, ouvrez Scriptor_CallExternalAssembly.btm.  
  
    2.  Dans la grille du Mappeur, sélectionnez le fonctoid Script.  
  
    3.  Dans la grille des propriétés, sélectionnez le **Script** propriété, puis cliquez sur le bouton de sélection (...) pour configurer le script du fonctoid.  
  
    4.  Dans le **configurer le fonctoid script** boîte de dialogue, sélectionnez le **Configuration du fonctoid Script**, spécifiez les éléments suivants :  
  
        |Définition de|Sur|  
        |--------------|-------------|  
        |**Type de script**|Assembly externe|  
        |**Assembly du script**|Microsoft.Samples.BizTalk.ExtendingMapper.MapperClassLibrary|  
        |**Classe du script**|Microsoft.Samples.BizTalk.ExtendingMapper.MapperHelper|  
        |**Méthode de script**|MyConcat|  
  
    5.  À partir de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] **fichier** menu, choisissez **enregistrer** pour enregistrer les modifications dans le fichier de mappage, puis fermez la solution.  
  
3.  Appuyez sur n'importe quelle touche pour continuer avec Setup.bat.  
  
    > [!IMPORTANT]
    >  Si vous voulez utiliser Scriptor_InlineXsltCallingExternalAssembly.btm, vous devez modifier le fichier ExternalAssembly.xml. ExternalAssembly.xml est utilisé par BizTalk pour mapper un espace de noms enregistré comme objet d'extension de mappeur à un assembly .NET. Comme l'assembly dépendant est référencé avec son nom complet (y compris son jeton de clé publique automatiquement généré), vous devez mettre à jour cette valeur. Si vous ne voulez pas utiliser Scriptor_InlineXsltCallingExternalAssembly.btm, vous ne devez pas effectuer les étapes a à e.  
  
4.  Dans l’Explorateur Windows, accédez à \<dossier Windows\>\assembly\\.  
  
    1.  Avec le bouton droit **Microsoft.Samples.BizTalk.ExtendingMapper.MapperClassLibrary** et sélectionnez **propriétés**.  
  
    2.  Copiez la valeur du jeton de clé publique.  
  
    3.  Dans un éditeur de texte, ouvrez  *\<exemples de chemin\>*\XML Tools\ExtendingMapper\ExternalAssembly.xml.  
  
    4.  Sélectionnez le **Microsoft.Samples.BizTalk.extendingmapper.mapperclasslibrary, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 68496d20c737d84b »**d’attribut, puis remplacez le  **PublicKeyToken** valeur avec le jeton de clé publique valeur que vous avez copiée à l’étape c.  
  
    5.  Enregistrez et fermez ExternalAssembly.xml.  
  
    > [!NOTE]
    >  Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.  
  
#### <a name="to-configure-enlist-and-start-the-send-port"></a>Pour configurer, inscrire et démarrer le port d'envoi  
  
1.  Cliquez sur **Démarrer**, sélectionnez **tous les programmes**, sélectionnez **Microsoft BizTalk Server**, puis sélectionnez **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, cliquez pour développer **Administration de BizTalk Server**, cliquez pour développer **groupe BizTalk [\<nom_serveur\>:\<base de données de gestion \>]**et développez **Applications**.  
  
3.  Cliquez pour développer **ExtendingMapperApplication**, puis cliquez sur **Ports d’envoi**.  
  
4.  Dans le volet droit, cliquez sur **Ports d’envoi**, puis cliquez sur **propriétés**.  
  
5.  Dans le **ExtendingMapperSP – propriétés de Port d’envoi** boîte de dialogue, cliquez sur le **mappages sortants** page.  
  
     Dans le **carte** colonne, sélectionnez le mappage requis dans la liste déroulante, puis cliquez sur **OK**. Ces mappages sont décrits dans le tableau suivant.  
  
    |Propriété Mappage à appliquer| Description|  
    |---------------------------|-----------------|  
    |Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_CallExternalAssembly|Montre comment appeler une fonction dans un assembly .NET externe depuis un **script** fonctoid dans un mappage, en fonction des paramètres d’entrée pour ce fonctoid. Cela permet de séparer clairement toute logique de traitement du fichier de mappage. Ce fichier de mappage utilise l'assembly MapperClassLibrary.dll qui est livré avec cet exemple.|  
    |Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_InlineScripts|Montre comment écrire de simples scripts inline **script** fonctoids dans un fichier de mappage à l’aide des langages .NET tels que c#, Visual Basic.NET et JScript.NET.|  
    |Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_GlobalVariableInInlineScript|Montre comment utiliser des variables globales dans les scripts inline de **script** fonctoids. Les variables globales sont généralement utilisées pour mettre à jour les informations d’état dans un fichier de mappage entre les différentes **script** fonctoids.|  
    |Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_InlineXslt|Montre comment construire la structure du document de destination à l’aide d’un inline XSLT brut à l’intérieur d’un **script** fonctoid dans le mappage. Vous pouvez construire certaines parties du document de destination avec **script** fonctoids avec inline XSLT, lorsqu’il n’est pas possible de le faire dans le Mappeur BizTalk à l’aide d’autres fonctoids.|  
    |Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_XsltCalltemplate|Montre comment créer la structure du document de destination à l’aide d’un modèle d’appel XSLT à l’intérieur d’un **script** fonctoid dans le mappage. L’avantage d’un modèle d’appel XSLT inline XSLT est que le modèle d’appel peut accepter des paramètres, vous pouvez donc créer la structure en fonction des paramètres d’entrée pour le **script** fonctoid. Vous pouvez construire certaines parties du document de destination avec **script** fonctoids avec inline XSLT, lorsqu’il n’est pas possible de le faire dans le Mappeur BizTalk à l’aide d’autres fonctoids.|  
    |Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_InlineXsltCallingExternalAssembly|Montre comment appeler un assembly .NET externe depuis l’Inline XSLT d’un **script** fonctoid dans un mappage. Explique comment vous pouvez substituer le **XML avec extensions personnalisées** propriété de la grille du Mappeur BizTalk avec le fichier d’extension personnalisé ExternalAssembly_extxml.xml qui contient les détails de l’assembly .NET externe à appeler. Vous pouvez construire certaines parties du document de destination avec **script** fonctoids avec inline XSLT, lorsqu’il n’est pas possible de le faire dans l’interface utilisateur du Mappeur à l’aide d’autres fonctoids.|  
    |Microsoft.Samples.BizTalk.ExtendingMapper. OverridingMapXslt|Illustre le remplacement complet du XSLT compilé du fichier du Mappeur BizTalk par un fichier XSLT personnalisé. Vous faire cela en substituant le **chemin du XSL personnalisé**propriété et éventuellement le **XML avec extensions personnalisées** propriété de la grille du Mappeur BizTalk. Le fichier XSLT personnalisé que vous fournissez est inclus dans l'assembly [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] compilé du projet à utiliser au moment de l'exécution. Dans ce cas, le contenu du fichier de mappage (.btm) est ignoré. Ce fichier de mappage utilise OverridingMapXslt.xslt et OverridingMapXslt.xml pour le **chemin du XSL personnalisé** et **XML avec extensions personnalisées** propriétés, respectivement.<br /><br /> Vous pouvez valider un fichier de mappage dans l'Explorateur de solutions. Vous pouvez ensuite l’utiliser en tant que fichier de modèle que vous pouvez modifier et utiliser pour la **chemin du XSL personnalisé** propriété de la grille du Mappeur BizTalk. Vous pouvez recourir à cette option lorsqu'il n'est pas possible de produire ce XSLT à l'aide du Mappeur BizTalk.|  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 La procédure suivante permet d'exécuter l'exemple Extending Mapper.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Copie l’entrée de fichier ExtendingMapper.xml dans le dossier d’entrée à  *\<exemples de chemin\>*\XmlTools\ExtendingMapper\In.  
  
2.  Remarquez que le fichier est transformé et acheminé vers le  *\<exemples de chemin\>*dossier \XmlTools\ExtendingMapper\Out. La transformation qui se produit est basée sur le mappage que vous avez appliqué.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils XML (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md)