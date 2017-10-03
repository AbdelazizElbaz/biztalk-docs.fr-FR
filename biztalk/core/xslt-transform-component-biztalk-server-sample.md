---
title: XSLT transformer le composant (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- examples, pipeline components [custom]
- XSLT, examples
- examples, XSLT
ms.assetid: 9152e897-4db9-4924-b37e-fd9e908dbef1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8374e2069660998a46265986125b6b0159ea1961
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xslt-transform-component-biztalk-server-sample"></a>Composant Transformation XSLT (exemple BizTalk Server)
L'exemple de composant Transformation XSLT décrit l'écriture d'un composant de pipeline personnalisé permettant de transformer un message XML à l'aide de XSLT.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple effectue la transformation selon la procédure suivante :  
  
1.  Un document XML est extrait d'un dossier.  
  
2.  Le pipeline transforme le document XML en un corps de message électronique HTML à l'aide de Transform.xsl.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès >*\Pipelines\XslTransformComponent\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|Fichier d'assembly C#.|  
|Cleanup.bat|Exemple de fichier de nettoyage.|  
|Confirmation.xsd|Exemple de fichier de schéma.|  
|DocInstance.xml|Exemple de fichier .xml à transformer.|  
|SendHtmlMessage.btproj|Projet BizTalk.|  
|Setup.bat|Fichier de commandes de configuration.|  
|Xml2HtmlSendPipeline.btp|Fichier de pipeline BizTalk Server.|  
|XslTransform.csproj|Projet C#.|  
|XslTransformComponent.sln|Exemple de fichier de solution.|  
|XslTransformComponentBinding.XML|Fichier de liaison XML.|  
|XslTransformer.cs|Code source C#.|  
|Transform.xsl|Fichier XSLT permettant de transformer DocInstance.xml.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 La procédure suivante permet de créer et d'initialiser l'exemple de composant Transformation XSLT.  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, accédez au répertoire (**cd)** dans le dossier suivant :  
  
     *\<Exemples de chemin d’accès >*\Pipelines\XslTransformComponent  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (\In) et de sortie (\Out) utilisés dans l'exemple ;  
  
    -   Création d'un nouveau fichier clé ;  
  
    -   Création et déploiement du pipeline de composant Transformation XSLT ;  
  
    -   Copie le composant de pipeline créé à le \<chemin d’Installation > dossier \Pipeline Components.  
  
    -   crée les ports d'envoi et de réception ;  
  
    > [!NOTE]
    >  Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.  
  
    > [!NOTE]
    >  Pour annuler les modifications apportées par Setup.bat, arrêtez puis redémarrez l'instance de l'hôte à partir de la console MMC Administration de BizTalk Server. Ensuite, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 La procédure suivante permet d'exécuter l'exemple de composant Transformation XSLT.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Copiez le fichier DocInstance.xml dans le dossier \In.  
  
2.  Examinez les résultats dans le dossier \Out (le nom du fichier de sortie est guid.htm).  
  
## <a name="configuring-this-sample-using-smtp"></a>Configuration de l'exemple à l'aide de SMTP  
 La procédure suivante permet de configurer l'exemple de composant Transformation XSLT à des fins de compatibilité avec un serveur SMTP.  
  
#### <a name="to-configure-this-sample-using-smtp"></a>Pour configurer l'exemple à l'aide de SMTP  
  
1.  Reconfigurez le port d'envoi du composant Transformation XSLT de manière à ce qu'il utilise un type de transport SMTP.  
  
2.  Configurez le paramètre SMTP en modifiant les paramètres d'adresse (URI) de manière à ce qu'ils correspondent à votre configuration SMTP.  
  
## <a name="running-this-sample-with-output-to-an-smtp-port"></a>Exécution de l'exemple avec une sortie vers un port SMTP  
 La procédure suivante permet d'exécuter l'exemple de composant Transformation XSLT avec une sortie vers un port SMTP.  
  
#### <a name="to-run-this-sample-with-output-to-an-smtp-port"></a>Pour exécuter l'exemple avec une sortie vers un port SMTP  
  
1.  Copiez le fichier DocInstance.xml dans le dossier \In.  
  
2.  Examinez les résultats dans le client de messagerie associé au destinataire configuré pour le port SMTP.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines (dossier d’exemples BizTalk Server)](../core/pipelines-biztalk-server-samples-folder.md)