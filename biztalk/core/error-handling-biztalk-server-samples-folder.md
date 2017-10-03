---
title: "(Dossier d’exemples BizTalk Server) de la gestion des erreurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, errors
- errors, examples
- examples, messages
- messages, examples
- messages, errors
ms.assetid: b39791ed-277b-4625-b9a9-72480a1b6ff6
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bfd309f332726efe2a13231ee1a337b428e3cff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-handling-biztalk-server-samples-folder"></a>Gestion des erreurs (dossier d'exemples BizTalk Server)
La fonction de cet exemple est de générer une fonctionnalité de gestion des erreurs pour l'application de routage basé sur le contenu (CBR).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter l’exemple, il est recommandé que vous disposez de Microsoft Office InfoPath 2010 ou version ultérieure. Vous pouvez exécuter l'exemple sans utiliser InfoPath, mais dans ce cas vous ne pouvez pas visualiser les bilans d'exploitation ni l'envoi des bilans d'exploitation via l'adaptateur HTTP.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L'exemple implémente une partie d'un système de traitement de bilan d'exploitation. Plus précisément, cet exemple effectue les opérations suivantes :  
  
1.  Définit un schéma de bilan d'exploitation contenant des informations sur un bilan d'exploitation et le soumissionnaire individuel, dont le nom du département.  
  
2.  Fournit l'envoi du bilan d'exploitation via un répertoire ou via un service Web utilisant InfoPath.  
  
3.  Promeut la **service** et **correlationID** propriétés dans le message document afin qu’il peut être utilisé dans un filtre de port pour contrôler le routage.  
  
4.  Achemine les bilans d'exploitation du département Marketing vers un fichier d'un répertoire, simulant la remise au système principal du département.  
  
5.  Génère un message ayant échoué pour les bilans d'exploitation appartenant aux départements autres que Marketing. Le message ayant échoué inclut des informations sur l'erreur, dont le code d'erreur et la description de l'erreur.  
  
6.  Achemine les messages ayant échoué vers un destinataire humain (utilisateur des activités ou opérateur d'application) en vue de la correction et du renvoi.  
  
7.  Achemine les bilans d'exploitation renvoyés sur la base du département, comme décrit plus haut.  
  
 Une grande partie de ces opérations est effectuée par le biais d'une planification d'orchestration BizTalk.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 La conception repose sur les pipelines XML d'envoi et de réception par défaut, la promotion des propriétés, les filtres d'abonnement, et les planifications d'orchestration dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour acheminer les messages. Ces critères de conception et leur justification sont récapitulés dans le tableau suivant.  
  
|Élément de conception|Raison(s) sélectionnée(s)|  
|--------------------|--------------------------|  
|Pipeline XML de réception par défaut|-Le pipeline XMLReceive prend en charge la promotion de propriétés ; le pipeline PassThruReceive ne fait pas.<br />-Le message entrant est déjà au format XML et ne nécessite pas de traitement dépasse le désassemblage de base et la résolution du tiers.|  
|Routage pour les messages ayant échoué|-Réception ports suspendre les messages ayant échouées et générer un accusé de réception négatif par défaut. Si le routage est activé, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lance une tentative d'acheminement des messages dont le traitement a échoué vers une application abonnée (un autre port de réception ou une planification d'orchestration).|  
|Promotion des propriétés|-BizTalk Server dépend des champs de propriété pour effectuer le routage. Des champs distinctifs sont utilisés par les orchestrations et ne peuvent pas être utilisés à des fins de routage.|  
|Filtre d'abonnement|-Le filtre d’abonnement réalise l’acheminement en capturant les messages qui répondent aux critères d’un ou plusieurs en fonction des champs de propriété.|  
|Planification d'orchestration BizTalk|-Fournit la possibilité d’ajouter des informations aux messages ayant échoué.<br />-Permet le routage des messages ayant échoué vers un emplacement spécifique d’une intervention humaine.<br />-Processus bilans d’exploitation.|  
|XMLTransmit|-Effectue l’assemblage de base des messages XML sortants. Le pipeline PassThruTransmit ne fournit aucune prise en charge supplémentaire.|  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Cet exemple se trouve dans <`Samples Path>`\Messaging\ErrorHandling\\.  
  
 Le tableau suivant contient une liste de fichiers de cet exemple.  
  
|Fichier| Description|  
|----------|-----------------|  
|Cleanup.bat|Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache.<br /><br /> Supprime les ports d'envoi et de réception.<br /><br /> Supprime les répertoires virtuels de Services Internet (IIS) si nécessaire.|  
|ErrorHandling.sln|Fichier de solution Visual Studio pour l'exemple.|  
|ErrorHandlingBinding.xml|Fichier de liaison pour l'exemple.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
|Bilan d'exploitation – John Doe.xml|Exemple de document InfoPath de bilan d'exploitation.|  
|Bilan d'exploitation non valide – John Doe.xml|Exemple de document InfoPath de bilan d'exploitation contenant des données non valides.|  
|Dans le dossier ErrorHandler :<br /><br /> ErrorHandler.btproj|Projet BizTalk pour l'orchestration.|  
|Dans le dossier ErrorHandler :<br /><br /> ResubmitLogic.odx|Orchestration qui s'abonne à des messages ayant échoué, les envoie au destinataire humain en vue de la correction, puis renvoie les messages corrigés au serveur en vue du routage.|  
|Dans le dossier ErrorHandler :<br /><br /> SuspendMessage.odx|Orchestration permettant d'interrompre les messages qui ne peuvent pas être traités au sein de l'orchestration de gestion des erreurs.|  
|Dans le dossier InfoPathForms :<br /><br /> Expense Report.xsn<br /><br /> Bilan d'exploitation - Resubmit.xsn|Formulaire InfoPath de bilan d'exploitation et formulaire utilisé pour visualiser et renvoyer les messages ayant échoué.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> ExpenseReportSchema.xsd|Schéma XML pour le document de bilan d'exploitation.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> PipelinesAndSchemas.btproj|Projet BizTalk pour l'exemple.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> PropertySchema.xsd|Schéma de propriété pour l'exemple.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Cet exemple fournit un point de départ pour créer votre propre procédure de gestion des erreurs.  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-compose-sample"></a>Pour créer et initialiser l'exemple Compose  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     <`Samples Path`>**\Messaging\ErrorHandling**  
  
2.  Exécutez **Setup.bat**, qui effectue les actions suivantes :  
  
    -   Crée trois dossiers : **ExpenseReportIn**, **ExpenseReportOut**, et **ResubmittedReportIn** sous le chemin d’accès suivant :  
  
         <`Samples Path`>**\Messaging\ErrorHandling**  
  
    -   Copie et publie les formulaires InfoPath **Expense Report.xsn** et **Expense Report – Resubmit.xsn** dans le dossier **C:\Temp\InfoPathForms**.  
  
    -   Compilation des projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de cet exemple.  
  
    -   Crée un répertoire virtuel appelé **ExpenseReports**.  
  
    -   Crée une application BizTalk appelée **exemple de gestion des erreurs** et déploie les assemblys de l’exemple dans celui-ci.  
  
    -   Création et liaison des emplacements de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que des ports d'envoi et de réception.  
  
    -   Inscription et démarrage des orchestrations, activation des emplacements de réception et démarrage des ports d'envoi.  
  
         Si vous décidez d'ouvrir et de créer les projets de cet exemple sans exécuter Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe). Celle-ci permet de signer les assemblys de l'exemple.  
  
3.  Avant de tenter d'exécuter cet exemple, vous devez vérifier que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur durant le processus de création ou d'initialisation.  
  
    > [!NOTE]
    >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
4.  Si vous utilisez Internet Information Services (IIS) 7.0, vous devez en outre modifier le paramètre de répertoire virtuel correspondant à l'emplacement de réception HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisé par l'exemple. Configurez IIS en procédant comme suit :  
  
    1.  À l'aide du gestionnaire IIS 7.0 Manager, créez un nouveau pool d'applications pour le groupe d'utilisateurs d'hôtes BizTalk isolés.  
  
    2.  Configurez le pool d'applications pour l'exécuter sous l'identité de l'utilisateur d'hôte isolé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. (Vous pouvez passer cette étape si vous disposez déjà d'un pool d'applications configuré pour d'autres emplacements de réception HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)  
  
    3.  Configurez le répertoire virtuel **ExpenseReport** pour utiliser le protocole HTTP réception pool d’applications créé à l’étape précédente.  
  
     Si vous ne disposez pas encore d'extension de serveur Web pour l'extension BTSHTTPReceive.dll ISAPI, créez-en une et activez-la en réglant son statut sur « Autorisé ». Cela à l’aide de la console de gestion IIS dans IIS 7.0 (soit directement sous **outils d’administration** ou via la console de gestion de l’ordinateur) comme suit :  
  
    1.  Développez le **Gestionnaire des Services Internet** arborescence.  
  
    2.  Cliquez sur le **Extensions du Service Web** dossier.  
  
    3.  Dans le volet droit de la console de gestion, cliquez sur **ajouter une nouvelle extension de Service Web**.  
  
    4.  Dans le **nouvelle Extension de Service Web** boîte de dialogue, cliquez sur **ajouter**.  
  
    5.  Dans le **ajouter le fichier** boîte de dialogue, cliquez sur **Parcourir** pour sélectionner le fichier <`BizTalkInstallPath>`**\HttpReceive\BTSHTTPReceive.dll**, puis cliquez sur **OK**.  
  
    6.  Configurez le répertoire virtuel **ExpenseReport** à utiliser le chemin d’accès local [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HTTPReceive  
  
     Pour plus d’informations, consultez [comment configurer les services IIS pour un emplacement de réception HTTP](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  
 Avant d'exécuter l'exemple avec le bilan d'exploitation correct, recourez à la procédure suivante pour s'assurer que l'exemple de cas « absence d'erreur » fonctionne correctement.  
  
#### <a name="to-verify-that-the-no-errors-case-sample-works-correctly"></a>Pour vérifier le bon fonctionnement de l'exemple de cas « absence d'erreur »  
  
1.  Ouvrez le formulaire InfoPath **Expense Report - John Doe.xml**. Examinez le **service** champ dans le formulaire. Ce champ doit être réglé sur « Marketing ».  
  
2.  Dans le coin supérieur gauche de la fenêtre InfoPath, cliquez sur **Submit** ou cliquez sur **renvoyer le bilan**. Attendez confirmation que le bilan d'exploitation a bien été envoyé.  
  
     -OU-  
  
     Copiez et collez ce fichier dans le **ExpenseReportIn** dossier.  
  
3.  Vous devez voir un nouveau fichier déposé dans le **ExpenseReportOut** dossier. Ce fichier est le même formulaire de bilan d'exploitation envoyé à l'étape précédente.  
  
 Après avoir confirmé le cas « absence d'erreur », suivez la procédure suivante pour exécuter l'exemple avec un bilan d'exploitation incorrect afin de déclencher la fonctionnalité de gestion des erreurs.  
  
#### <a name="to-trigger-error-handling"></a>Pour déclencher la gestion des erreurs  
  
1.  Ouvrez le formulaire InfoPath **Invalid Expense Report - John Doe.xml**. Examinez le **service** champ dans le formulaire. Ce champ est réglé sur une valeur non valide.  
  
2.  Dans le coin supérieur gauche de la fenêtre InfoPath, cliquez sur **Submit**. Attendez confirmation que le bilan d'exploitation a bien été envoyé.  
  
     -OU-  
  
     Copiez et collez ce fichier dans le **ExpenseReportIn** dossier.  
  
3.  Vous devez voir un nouveau fichier appelé **ErrorReport_\<***date*_*temps***> .xml** déposé dans le  **ExpenseReportOut** dossier.  
  
     Ouvrez ce fichier et vérifiez qu'il s'agit du bilan d'exploitation envoyé à l'étape précédente mais avec les informations d'erreur ajoutées au début.  
  
4.  Remplacez la valeur de département erronée par « Marketing », puis cliquez sur **Submit** dans le coin supérieur gauche de la fenêtre InfoPath.  
  
     -OU-  
  
     Copiez et collez ce fichier dans le **ResubmittedReportIn** dossier.  
  
5.  Vous devez voir un nouveau fichier créé dans le **ExpenseReportOut** dossier. Ce fichier est le bilan d'exploitation corrigé qui a été renvoyé au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de routage des messages ayant échoué](../core/using-failed-message-routing.md)   
 [Messagerie (dossier d’exemples BizTalk Server)](../core/messaging-biztalk-server-samples-folder.md)