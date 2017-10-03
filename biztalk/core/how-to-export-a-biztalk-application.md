---
title: Comment exporter une Application BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, exporting
- exporting, warnings
- exporting, applications
- applications, exporting
- applications, security
- applications, warnings
- exporting, security
ms.assetid: a1d6ffca-3d29-44c7-a811-6cf8b42e23f6
caps.latest.revision: "50"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f1b2becead061ec1bad089bd5ceddbbc076d83f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-a-biztalk-application"></a>Comment exporter une Application BizTalk
Cette rubrique décrit comment exporter une application à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou de la ligne de commande. L'exportation d'une application BizTalk génère un fichier Windows Installer (.msi) qui contient l'application, ainsi que les artefacts qu'elle contient et que vous sélectionnez pour l'exportation. L'option par défaut sélectionne tous les artefacts de l'application, mais vous pouvez en sélectionner certains seulement. Vous pouvez ensuite importer le fichier .msi file dans un autre groupe BizTalk afin d'ajouter les artefacts à une application existant dans le nouveau groupe, mettre à jour les artefacts dans une application existante ou créer une application dans le groupe contenant les artefacts importés. Pour plus d’informations, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Vous utilisez également le fichier .msi pour installer l’application sur les ordinateurs qui exécuteront, comme décrit dans [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md). Si l’application inclut des artefacts basés sur le fichier, vous devez également l’installer pour qu’elle puisse fonctionner.  
  
 Lorsque vous exportez une application, gardez les points importants suivants à l'esprit :  
  
-   **Les liaisons existantes sont automatiquement remplacées par les liaisons importées.** Pour éviter que les liaisons de l'application exportée ne remplacent les liaisons de l'application dans laquelle vous importez un fichier .msi, ne sélectionnez pas le fichier de liaison en tant que ressource à exporter. Lorsque vous importez un fichier .msi file contenant un fichier de liaison dans une application existante, les liaisons existantes sont remplacées par celles en cours d'importation, même si vous n'avez pas choisi de remplacer les artefacts existants.  
  
-   **Un utilisateur peut être apporter des modifications à un artefact pendant que vous exportez l’application.** Si un utilisateur modifie un artefact basé sur une base de données, tel qu'un répertoire virtuel, un certificat ou une stratégie, pendant l'exportation, ces modifications n'apparaissent pas dans le fichier .msi exporté. Nous vous recommandons par conséquent de planifier les exportations à des heures où les utilisateurs ne sont pas susceptibles de modifier ces artefacts.  
  
-   **Erreur incorrecte peut s’afficher lors de l’installation d’un fichier .msi sur Windows Vista**. Lorsque vous installez un package .msi exporté à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez recevoir l’erreur incorrecte suivante, « le programme d’installation a rencontré une erreur inattendue, l’installation de ce package. Il s'agit peut-être d'un problème lié au package. Le code d'erreur est 2869. ». Pour remédier à cette erreur, importez d'abord le package .msi à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis ré-exportez-le et installez-le.  
  
-   **L’application peut avoir des dépendances sur une autre application.** Ceci peut affecter le mode de déploiement de l'application. Pour plus d’informations, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).  
  
-   **Vous pouvez modifier le répertoire de destination des ressources dans votre application avant l’exportation.** Si vous souhaitez modifier l’emplacement de destination, développez le nœud de ressources de votre application, avec le bouton droit de la ressource que vous souhaitez modifier, puis choisissez **modifier**. Dans la boîte de dialogue Modifier les ressources, entrez un nouvel emplacement pour **l’emplacement de Destination**.  
  
-   **Exportation échoue si l’application contient une stratégie qui a été supprimée de la base de données du moteur de règles.** Lorsque vous supprimez une stratégie de la base de données du moteur de règles à l'aide de l'Assistant Déploiement du moteur de règles, il affiche la console d'administration en l'état « Non publié », et vous ne pouvez pas exporter l'application. Pour plus d’informations sur l’Assistant Déploiement du moteur de règles, consultez [comment déployer et annuler le déploiement de stratégies et vocabulaires](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
> [!IMPORTANT]
>  Le fichier .msi peut contenir des données sensibles. Vérifiez que le fichier est sécurisé. Pour plus d’informations, consultez [sécurité et Windows Installer](../core/security-and-windows-installer.md).  
>   
>  Pendant l'exportation d'une application, les mots de passe sont supprimés des liaisons de l'application. Après avoir installé l’application à partir du fichier .msi, vous devez reconfigurer les mots de passe afin que l’application de fonctionner. Les mots de passe ne sont cependant pas supprimés des fichiers de liaison ajoutés à l'application.  
>   
>  Si l'application inclut un site Web ou une orchestration qui utilise un site Web, sachez que les paramètres de sécurité du répertoire virtuel utilisés sont ceux qui sont activés lorsque le fichier .msi est généré au cours de l'exportation de l'application. Si vous déployez une application dans l'environnement de production, avant de l'exporter, vérifiez que les paramètres répondent à vos exigences en matière de sécurité. Si le répertoire virtuel existe déjà sur l'ordinateur hôte, ses paramètres de sécurité ne sont pas remplacés, mais les fichiers de l'application sont ajoutés au répertoire. Une fois l'application importée, vous devez vérifier les paramètres de sécurité.  
>   
>  Toutes les listes de contrôle d'accès discrétionnaires (DACL) sont supprimées des fichiers et dossiers lors de l'exportation d'une application. Une fois l'application installée, vous devez reconfigurer tous les paramètres de sécurité dans les fichiers et les dossiers, y compris dans les répertoires virtuels.  
  
> [!NOTE]
>  Si l'exportation échoue, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supprime tous les fichiers temporaires avec le fichier .msi éventuellement créé.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter les procédures décrites dans cette rubrique, vous devez ouvrir une session à l'aide d'un compte membre du groupe Administrateurs de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md). De plus, le Moteur des règles d'entreprise doit être installé. Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
## <a name="to-export-an-application"></a>Pour exporter une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, puis développez **Applications**.  
  
3.  Cliquez sur l’application que vous souhaitez exporter, pointez sur **exporter**, puis cliquez sur **fichier MSI**.  
  
4.  Dans la page d’accueil de l’Assistant Exportation de fichier MSI, cliquez sur **suivant**.  
  
5.  Dans la page Sélectionner les ressources, sélectionnez les artefacts à exporter dans le fichier .msi, puis cliquez sur **suivant**.  
  
6.  Si vous y êtes invité, dans la page spécifier les hôtes IIS, tapez le nom de l’ordinateur qui héberge le répertoire virtuel que vous souhaitez inclure, puis cliquez sur **suivant**. Vous êtes invité à indiquer le serveur uniquement si le répertoire virtuel n'a pas encore été ajouté à la base de données de gestion BizTalk, comme lorsqu'il a été ajouté à l'application ou importé dans une application.  
  
7.  Sur la page dépendances, vérifiez les dépendances de l’application, puis cliquez sur **suivant**.  
  
8.  Dans la page de Destination, dans **nom de l’application Destination**, tapez le nom de l’application.  
  
9. Dans **fichier MSI à générer**, tapez le chemin d’accès complet pour le fichier .msi, puis cliquez sur **exporter**. Exemple : C:\MSI\Errorhandling.msi  
  
    > [!NOTE]
    >  Nous vous recommandons d'enregistrer les fichiers .msi dans un dossier sécurisé.  
  
10. Dans la page Résumé, prenez note de l’emplacement du fichier journal pour cette opération, puis cliquez sur **Terminer**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask ExportApp** [**« ApplicationName » :***valeur*] **/Package :***valeur* [**ResourceSpec :***valeur* [**/Server :***valeur*] [**/Database :***valeur*]  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
     Exemple :  
  
     **BTSTask ExportApp /ApplicationName:MyApplication /Package:C:/MSI/MyApplication.msi /resourcespec. : « C:\My Files\ResourceSpec.xml » /Server:MySQLServer Server**  
  
     Les artefacts mentionnés sont exportés dans le fichier .msi à l'emplacement spécifié.  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à exporter. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut. Si le nom comprend des espaces, il doit être placé entre guillemets doubles («).|  
    |**/ Package**|Chemin du fichier .msi à créer, y compris son nom.|  
    |**/ Spécification de ressource**|Chemin d'accès du fichier XML de spécification de ressource, nom du fichier inclus. Vous pouvez spécifier les artefacts à exporter en modifiant le fichier XML de la spécification de la ressource, qui est créé lorsque vous exécutez le ListApp de commande avec le paramètre ResourceSpec, comme décrit dans [commande ListApp](../core/listapp-command.md). Vous devez ajouter manuellement à ce fichier le nom du serveur hôte des services IIS du répertoire virtuel à exporter si le serveur Web se trouve sur un ordinateur distant|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation de stratégies, les liaisons et les Applications BizTalk](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [Commande ExportApp](../core/exportapp-command.md)