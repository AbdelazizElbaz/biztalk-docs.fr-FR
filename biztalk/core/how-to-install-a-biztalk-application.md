---
title: Comment installer une Application BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, requirements
- installing, applications
- installing, warnings
- applications, installing
ms.assetid: 99ee0b1a-d46a-4fb6-802b-6827dc740418
caps.latest.revision: "56"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a73bd610f94e5b56dc5af5d27f90ec8bb4eb1d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-a-biztalk-application"></a>Installation d'une application BizTalk
Cette rubrique décrit la procédure d'installation d'une application sur l'ordinateur local par double-clic sur le fichier Windows Installer (.msi) de l'application dans l'interface Windows ou par l'exécution du programme msiexec à partir de la ligne de commande. Vous pouvez également démarrer l’Assistant Installation de la dernière étape de l’Assistant Importation, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
> [!CAUTION]
>  Si l'application a déjà été installée sur l'ordinateur, vous aurez la possibilité de la réparer. La réparation est possible uniquement lorsqu'un seul fichier .msi a été installé pour l'application. Si vous avez installé plusieurs fichiers .msi sur l'ordinateur pour l'application, vous ne pourrez pas sélectionner cette option, car la réparation annule toutes les modifications apportées par les fichiers .msi installés après le fichier .msi, ce qui peut entraîner un mauvais fonctionnement de l'application.  
  
 Avant de pouvoir exécuter une application, vous devez l'installer sur les ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui l'exécuteront. L'installation d'une application place ses ressources sur le système de fichiers local. Selon l'application, son contenu et sa configuration, l'installation peut aussi effectuer les opérations suivantes :  
  
-   ajout d'assemblys au GAC ;  
  
-   installation des certificats et des répertoires virtuels ;  
  
-   ajout de composants au Registre Windows ;  
  
-   exécution de scripts de prétraitement et de post-traitement s'ils se trouvent dans le fichier .msi.  
  
 Pour plus d’informations, consultez [que se passe-t-il pour les artefacts lors de l’Installation et la désinstallation](../core/what-happens-to-artifacts-during-installation-and-uninstallation.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter les procédures décrites dans cette rubrique, vous devez être connecté avec un compte disposant d'autorisations en écriture sur le système de fichiers local. Selon les éléments contenus dans l'application, vous pouvez avoir également besoin d'autorisations en écriture sur le Registre Windows, le GAC, le magasin de certificats et les services IIS. Le compte des administrateurs de l'ordinateur local dispose de ces autorisations. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="considerations-for-installing-an-application"></a>Considérations relatives à l'installation d'une application  
 Lors de l'installation d'une application, tenez compte des éléments suivants :  
  
-   **Vous devez également installer des applications sur lequel cette application a une dépendance.** Lorsque vous installez une application dépendant d'un artefact, comme un assembly BizTalk, contenu dans une autre application, vous devez également installer l'application qui contient cet artefact. Vous devez effectuer cette opération avant d'exécuter l'application. Par exemple, si l’Application A dépend d’un assembly dans l’Application B, vous devez également installer Application B. Vous pouvez ensuite installer l’Application a Pour plus d’informations, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).  
  
-   **Vous devez arrêter l’application que vous mettez à jour.** Si vous effectuez l'installation afin de mettre à jour un artefact de l'application, il n'est pas utile d'arrêter cette dernière sauf si la mise à jour inclut des assemblys dont la version est identique aux assemblys existants. Dans ce cas, vous devez arrêter l'application avant de procéder à la mise à jour. Nous vous recommandons d'arrêter l'application dans tous les cas, sauf si vous êtes sûr que la mise à jour n'interfèrera pas avec l'exécution de l'application. Pour plus d’informations, consultez [mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md).  
  
-   **Lorsque vous installez plusieurs fichiers .msi pour la même application, il existe une seule entrée créée dans Ajout / Suppression de programmes.** Vous pouvez procéder ainsi pour mettre à jour une application existante par exemple. Vous pouvez ensuite utiliser Ajout / Suppression de programmes (dans le panneau de configuration) pour désinstaller l’application complète, y compris tous les éléments mis à jour. La désinstallation d'une application par double-clic sur le fichier .msi ou par l'exécution du programme msiexec n'est pas prise en charge. Pour plus d’informations, consultez [comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md).  
  
-   **Certificats doivent être présents sur tous les ordinateurs qui hébergent des ports d’envoi avant d’exécuter l’application.** Le magasin de certificats d'autres personnes contient le certificat utilisé par les ports d'envoi.  
  
-   **Vous pouvez factoriser les artefacts de l’application dans différents fichiers .msi pour l’installation.** Vous n'avez pas besoin d'installer tous les artefacts de l'application sur chaque ordinateur qui devra exécuter l'application. Il est plutôt préférable d'exporter des sous-ensembles d'artefacts de l'application dans différents fichiers .msi à installer sur les différents ordinateurs. Pour obtenir des instructions, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
-   **Si le fichier .msi d’application inclut un répertoire virtuel, Internet Information Services (IIS) doivent être en cours d’exécution sur l’ordinateur local.** Dans le cas contraire, l'installation échouera.  
  
-   **Si l’application inclut un répertoire virtuel portant le même nom que celle qui existe déjà sur l’ordinateur local, les ressources de l’application sont ajoutés à ce dernier.** Dans le cas contraire, le répertoire virtuel est créé. Tout fichier existant portant le même nom que les fichiers ajoutés sera remplacé. En outre, les paramètres de sécurité d'un répertoire virtuel ne sont pas modifiés, vous devez donc vérifier qu'ils sont suffisamment sécurisés.  
  
-   **Créer des pools d’applications pour les répertoires virtuels avant d’installer une application.** Si l'application contient un répertoire virtuel et que le pool d'applications n'existe pas encore dans IIS, vous devez le créer manuellement avant de procéder à l'installation. Ainsi, le répertoire virtuel sera associé au pool d'applications au cours de l'installation. Si vous ne créez pas l'application, le répertoire virtuel sera associé au pool d'applications par défaut au cours de l'installation.  
  
-   **Vérifiez que BTSHttpReceive.dll est enregistré comme un mappage de gestionnaire avec Internet Information Services (IIS) 7.0.** Vous devez le faire si votre application inclut un répertoire virtuel dans l’ordre pour le protocole HTTP emplacement de réception à utiliser.  
  
-   **Vous pouvez rencontrer des problèmes lors de l’installation d’une application qui comprend des artefacts 64 bits sur un ordinateur 32 bits.** Pour plus d’informations, consultez [comment ajouter un artefact 64 bits à une Application](../core/how-to-add-a-64-bit-artifact-to-an-application.md).  
  
-   **Vous pouvez rencontrer des problèmes si le répertoire cible dépasse 260 caractères.** Si le nombre de caractères du répertoire cible spécifié au cours de l'installation d'un package MSI dépasse les 260 caractères, l'installation échoue. Pour résoudre ce problème, assurez-vous que le nombre de caractères indiqué pour le répertoire cible ne dépasse pas 260.  
  
-   **Vous ne devez pas déplacer un dossier d’installation.** Une fois l'application installée, vous ne devez en aucun cas déplacer le dossier d'installation ni les fichiers qu'il contient. Dans le cas contraire, toute tentative ultérieure de désinstallation de l'application échouera, notamment si le dossier d'installation de l'application contient des fichiers générés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et nécessaires à la suppression. Par conséquent, vous ne devez pas renommer ces fichiers, ni les déplacer, ni les supprimer. Ces fichiers sont les suivants :  
  
    -   ApplicationDefinition.adf  
  
    -   Microsoft.BizTalk.CustomInstaller.dll  
  
    -   Microsoft.BizTalk.CustomInstaller.InstallState  
  
> [!NOTE]
>  Si vous annulez l'installation avant qu'elle soit terminée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] l'annule, sauf si des scripts de pré-traitement ou de post-traitement ont commencé des actions avant l'annulation de l'opération.  
  
> [!IMPORTANT]
>  Avant d’installer n’importe quelle application, veillez à ce que vous avez reçu le fichier .msi à partir d’une source approuvée. Un utilisateur malveillant peut inclure du code dans un fichier .msi qui peut avoir un effet indésirable sur votre système ou votre réseau.  Pour plus d’informations, consultez [sécurité et Windows Installer](../core/security-and-windows-installer.md).  
>   
>  Si l'application inclut un site Web ou une orchestration qui utilise un site Web, sachez que les paramètres de sécurité du répertoire virtuel utilisés sont ceux qui sont activés lorsque le fichier .msi est généré au cours de l'exportation de l'application, sauf s'il existe déjà un répertoire virtuel, auquel cas, les paramètres existants sont employés. Une fois l'application installée, vous devez vérifier que ces paramètres répondent à vos exigences en matière de sécurité.  
>   
>  Listes de contrôle d’accès Alldiscretionary (DACL) sont supprimés des fichiers et dossiers lors de l’exportation d’une application. Une fois l'application installée sur une instance de l'hôte, vous devez reconfigurer tous les paramètres de sécurité dans les fichiers et les dossiers, y compris dans les répertoires virtuels.  
  
-   **Vous devrez peut-être modifier le chemin d’accès Local : emplacement de réception désignation d’un répertoire virtuel qui est référencé par une requête HTTP après sa création sur l’ordinateur cible.**  
  
     Une fois le répertoire virtuel créé sur l'ordinateur cible, il pointe vers un des répertoires physiques suivants :  
  
     \<*lecteur d’installation*> \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\HttpReceive  
  
     \-**ou** :  
  
     \<*lecteur d’installation*> \Program Files (x86) \Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\HttpReceive  
  
     Si le fichier BTSHTTPReceive.dll d'extension ISAPI de l'emplacement de réception HTTP BizTalk ne se trouve pas dans le répertoire spécifié ou si l'ordinateur cible exécute un système d'exploitation 64 bits, vous devez modifier la désignation du chemin d'accès local : du répertoire virtuel de sorte qu'il pointe vers le répertoire physique contenant le fichier d'extension ISAPI de l'emplacement de réception HTTP BizTalk. Par exemple, si l’ordinateur cible exécute la version 64 bits de Windows Vista, puis le chemin d’accès Local : du répertoire virtuel doit être modifiée en \<lecteur d’installation > \Program Files (x86) \Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\HttpReceive64 .  
  
## <a name="to-install-a-biztalk-application"></a>Pour installer une application BizTalk  
  
#### <a name="using-the-windows-interface"></a>Utilisation de l'interface Windows  
  
1.  Copiez le fichier .msi file de l'application sur l'ordinateur local.  
  
2.  Si vous réinstallez ou mettez à niveau une application BizTalk existante et la nouvelle installation inclut un assembly qui possède la même version qu’un qui existe déjà dans l’application, ou interagit avec un artefact que vous mettez à jour, assurez-vous que le application est arrêtée en double-cliquant sur le dossier de l’application, puis sur **arrêter**.  
  
3.  Dans l'Explorateur Windows, double-cliquez sur le fichier .msi pour démarrer l'Assistant Installation.  
  
4.  Sur le **sélectionner le dossier** page **dossier**, tapez le chemin d’accès de terminer l’installation de l’application BizTalk. Exemple : C:\Program Files\Generated by BizTalk\MyApplication.  
  
5.  Cliquez sur **suivant** quatre fois, puis, dans le **Installation complète** , cliquez sur **fermer**.  
  
6.  Si plusieurs ordinateurs doivent exécuter l'application, répétez ces étapes pour chacun d'eux.  
  
     Une fois que l’application est installée sur tous les ordinateurs qui l’exécuteront et l’application a été importée dans le groupe BizTalk, vous pouvez démarrer l’application à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration en cliquant sur le dossier de l’application en cliquant sur **Démarrer**. Pour plus d’informations, consultez [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Copiez le fichier .msi file de l'application sur l'ordinateur local.  
  
2.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
3.  Accédez à l'emplacement où se trouve le fichier .msi.  
  
4.  Entrez la commande suivante pour installer l'application, en saisissant les paramètres et valeurs adéquats, comme indiqué dans le tableau suivant :  
  
    > [!IMPORTANT]
    >  Seuls les paramètres de msiexec affichés dans le tableau suivant sont pris en charge.  
  
     **msiexec** [**/i**] *Package* [**/qn**] **TARGETDIR = «***valeur* **"**]  
  
     Exemple : **msiexec /i MyApplication.msi**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/i**|Installe l'application.|  
    |*Package*|Nom du fichier Windows Installer (.msi).|  
    |**/qn**|Effectue l'installation sans afficher d'interface utilisateur.|  
    |**TARGETDIR = «** *valeur* **»**|Spécifie l'emplacement du dossier d'installation de l'application. Cette valeur est également définie dans la variable d'environnement %BTAD_InstallDir%.<br /><br /> Exemple : TARGETDIR="C:\Programs\BizTalk Applications\My Application"|  
  
5.  Si plusieurs ordinateurs doivent exécuter l'application, répétez ces étapes pour chacun d'eux.  
  
     Une fois que l’application est installée sur tous les ordinateurs qui vont l’exécuter, vous pouvez démarrer l’application à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration en cliquant sur le dossier de l’application en cliquant sur **Démarrer**. Pour plus d’informations, consultez [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’Applications BizTalk](../core/deploying-biztalk-applications.md)   
 [Comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md)