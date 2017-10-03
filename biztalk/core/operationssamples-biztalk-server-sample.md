---
title: OperationsSamples (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c9e3f3e-a570-4edd-aa2e-3f8e2e37c8a0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3e190d06c084a6b1b3c9965856897e0df94daab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operationssamples-biztalk-server-sample"></a>OperationsSamples (exemple BizTalk Server)
L'exemple OperationsSamples montre comment réaliser des activités opérationnelles à l'aide du modèle objet Opérations.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple illustre les fonctions suivantes :  
  
-   Utilisation d'un modèle de suivi pour commenter une orchestration contenant des activités.  
  
-   Recherche d'un ID d'activité dans la base de données des suivis BAM pour ensuite rechercher à l'aide de cet ID une instance d'orchestration liée.  
  
-   Comment rechercher et utiliser des flux de messages à l’aide de la **MessageFlow** classe et d’autres API et classes du modèle objet opérations.  
  
-   Comment accéder aux ports, messages et d’autres instances à l’aide des classes dérivées de la **Instance** classe.  
  
 Cet exemple contient de nombreuses classes et méthodes d'assistance pour assurer la prise en charge des opérations précitées. Elles sont présentées dans la section suivante, avec d'autres éléments de code.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Conception et finalité de l'exemple  
 Cet exemple est conçu de façon à présenter plusieurs des principales classes et méthodes du modèle objet Opérations et pour expliquer comment exécuter une requête dans la base de données publique des suivis BAM.  
  
 Le modèle objet Opérations contient des classes qui permettent de manipuler des messages ainsi que d'autres instances dans BizTalk Server.  
  
### <a name="using-a-bam-activity-id"></a>Utilisation d'un ID d'activité BAM  
 Cet exemple montre comment interagir avec la base de données des suivis BAM en utilisant les vues publiques pour rechercher un message actif dans le MessageBox à l'aide des données de l'entreprise. Pour ce faire, l'exemple procède à l'extraction d'un ID d'orchestration correspondant à un numéro de bon de commande. Pour que cette tâche aboutisse, la procédure suivante doit être respectée :  
  
1.  Utiliser des données d’entreprise (un numéro de commande) pour rechercher un ID d’activité. Cette étape mappe les données d’entreprise à un ID interne qui peut être utilisé pour rechercher des informations supplémentaires.  
  
2.  Extraction des références BAM associées à l'ID de l'activité.  
  
3.  Recherche d'une référence dont le type correspond à « BizTalkService » et se rapporte à une orchestration. Si une référence est trouvée, l'ID correspondant à l'instance doit être renvoyée.  
  
 Cette fonctionnalité est fournie par le **BAMWebService.GetOrchestrationID** méthode statique et les méthodes d’assistance associées, y compris les classes et méthodes dans le fichier source BamManagementService.cs.  
  
### <a name="suspending-terminating-and-resuming-an-instance"></a>Interruption, arrêt et reprise d'une instance  
 L’exemple de programme inclut un **Samples.OperateOnInstance** méthode qui accepte un ID d’opération et l’instance et effectue l’opération spécifiée sur l’instance. Les opérations valides sont définies par le **InstanceOperation** énumération et inclure l’interrompre, terminer et reprendre. Ces opérations sont directement mappent aux méthodes de la classe BizTalkOperations :**SuspendInstance**, **TerminateInstance**, et **ResumeInstance**.  
  
 Notez que cette méthode gère à la fois les exceptions ArgumentException et les exceptions SqlException. Vous devez veiller à anticiper les exceptions (y compris l’exception SqlException) lorsque vous travaillez avec les classes et méthodes du modèle objet Opérations.  
  
> [!NOTE]
>  De nombreuses méthodes Opérations nécessitent un accès à la base de données. Vous devez anticiper les exceptions générées par ces méthodes et les gérer de façon appropriée.  
  
### <a name="retrieving-all-live-messages"></a>Récupération de tous les messages actifs  
 Avec le modèle objet Opérations, il s'avère très simple d'effectuer des itérations sur tous les messages actifs disponibles, comme l'illustre le fragment de code suivant :  
  
```  
BizTalkOperations _operations = new BizTalkOperations()  
IEnumerable messages = _operations.GetMessages();  
foreach (BizTalkMessage msg in messages)  
…  
```  
  
 Le programme OperationsSamples va encore plus loin puisqu'il permet d'accéder aux informations relatives à chaque message, notamment l'ID et le type du message, ainsi que le nombre de parties dont est constitué le message, et leur type. Vous pouvez modifier ce code et l'utiliser dans le cadre de scénarios dans lesquels vous devez effectuer des itérations sur tous les messages actifs ou sur un grand nombre d'entre eux dans BizTalk Server.  
  
> [!NOTE]
>  Il peut y avoir des centaines, voire des milliers de messages disponibles. Une analyse complète de la liste risque de nuire aux performances.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*> \Admin\OperationsOM\OperationsSamples\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|BamManagementService.cs|Classe proxy Web du service Web BAM.|  
|Cleanup.bat|Supprime l'exemple d'orchestration et rétablit l'exemple HelloWorld à son état d'origine.|  
|HelloOrchestration.btt|Modèle de suivi permettant de mapper des sources d'événements BizTalk à des activités cible BAM.|  
|HelloOrchestration.xls|Feuille de style de définition BAM.|  
|OperationsSamples.cs|Fichier source C# contenant le code qui illustre les différents aspects du modèle objet Opérations.|  
|OperationsSamples.csproj, OperationsSamples.sln, AssemblyInfo.cs|Fichiers de projet, de solution et d'informations de l'assembly pour cet exemple.|  
|Setup.bat|Permet de créer et d'initialiser cet exemple en modifiant l'exemple d'orchestration HelloWorld. Il installe un exemple d'orchestration, déploie des fichiers de définition d'activités BAM et d'éditeur de modèle de suivi, configure des ports et dépose un fichier exemple dans l'emplacement de réception.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Cet exemple permet d'explorer les fonctionnalités disponibles dans le modèle objet Opérations. Vous pouvez modifier les routines existantes pour rechercher et utiliser des messages de façon différente, ou ajouter du code répliquant des portions du Hub du groupe dans BizTalk Server Management Console.  
  
 Vous pouvez également réaliser les tâches suivantes :  
  
-   Écrire une application qui assure la réplication du sous-ensemble le plus utilisé dans le Hub du groupe sous la forme d'une application personnalisée.  
  
-   Écrire une application d'approvisionnement personnalisée qui assure la création de ports et l'envoi d'un message destiné aux nouveaux partenaires commerciaux.  
  
-   Modifier l'exemple de programme en utilitaire de ligne de commande qui indique à l'écran, dans un fichier XML ou un rapport de type texte, des informations sur un seul ou plusieurs bons de commande.  
  
## <a name="installing-sample-support-files"></a>Installation de fichiers d'exemple de support  
 Cette section présente les procédures requises pour installer et exécuter l'exemple.  
  
> [!NOTE]
>  Avant de procéder à l'installation et à l'exécution de cet exemple, vous devez vérifier que l'analyse BAM est bien installée et en état de fonctionnement. Dans le cas contraire, cet exemple ne pourra pas s'exécuter.  
  
#### <a name="to-compile-and-install-the-support-files-for-this-sample"></a>Pour compiler et installer les fichiers de support de cet exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création de répertoires d'envoi et de réception  
  
    -   Création et démarrage de ports d'envoi et de réception  
  
    -   Compilation et déploiement de l'orchestration HelloWorld dans le dossier `<Samples Path>`\Orchestrations\HelloWorld.  
  
    -   Modification du jeton de clé publique pour l'orchestration HelloWorld  
  
    -   Déploiement des fichiers de définition d'activité BAM et d'éditeur de modèle de suivi  
  
    -   Attribution d'un nouveau nom au répertoire de sortie  
  
    > [!NOTE]
    >  Pour abandonner l'installation, appuyez sur CTRL+C lorsque la première invite s'affiche, vous demandant d'appuyer sur une touche pour continuer. Le script est ainsi arrêté et l'exemple HelloWorld reste à son état d'origine. Si vous appuyez sur CTRL+C à la deuxième et dernière invite, le processus d'installation ne s'arrête pas. Dans ce cas, vous devez exécuter le fichier Cleanup.bat pour désinstaller l'exemple OperationsOM et rétablir l'exemple HelloWorld à son état d'origine.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 La procédure suivante permet d'exécuter l'exemple OperationsOM.  
  
#### <a name="to-compile-and-run-the-sample"></a>Pour compiler et exécuter l'exemple  
  
1.  Cliquez sur **Démarrer**, sélectionnez **tous les programmes**, sélectionnez **Microsoft BizTalk Server**, puis sélectionnez **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Instances de l’hôte**.  
  
3.  Avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **redémarrer**.  
  
    > [!NOTE]
    >  Il peut s'avérer nécessaire de redémarrer l'instance de l'hôte BizTalkServerApplication pour définir la base de données effective pour l'analyse BAM, si vous n'avez pas redémarré l'instance de l'hôte depuis la configuration du produit.  
  
4.  Dans l'Explorateur Windows, accédez au dossier suivant :  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
5.  Double-cliquez sur le **OperationsOM.sln** fichier projet pour le charger dans [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
6.  Appuyez sur la touche F5 pour exécuter l'exemple.  
  
     --OU--  
  
     Sur le **générer** menu, cliquez sur **régénérer la Solution**. Lorsque la build est terminée, utilisez l’Explorateur Windows pour accéder à `<Samples Path>\Admin\OperationsOM\OperationSamples\bin\Debug,` , puis double-cliquez sur **OperationsSamples.exe**.  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans l'exemple  
 [Microsoft.BizTalk.Operations.BizTalkOperations](http://msdn.microsoft.com/library/microsoft.biztalk.operations.biztalkoperations.aspx)&#124; [Microsoft.BizTalk.Operations.MessageFlow](http://msdn.microsoft.com/library/microsoft.biztalk.operations.messageflow.aspx)&#124; [Microsoft.BizTalk.Operations.SendPortInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.sendportinstance.aspx)&#124; [Microsoft.BizTalk.Operations.RoutingFailureInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.routingfailureinstance.aspx)&#124; [Microsoft.BizTalk.Operations.OrchestrationInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.orchestrationinstance.aspx)&#124; [Microsoft.BizTalk.Operations.MSMQtInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.msmqtinstance.aspx)&#124; [Microsoft.BizTalk.Operations.TrackedServiceInstance](http://msdn.microsoft.com/library/Microsoft.BizTalk.Operations.TrackedServiceInstance.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-OperationsOM (dossier d’exemples BizTalk Server)](../core/admin-operationsom-biztalk-server-samples-folder.md)