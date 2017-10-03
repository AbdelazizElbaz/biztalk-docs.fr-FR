---
title: "Comment ajouter un artefact BAM à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, definition files [BAM]
- BAM, applications
- managing [applications], definition files [BAM]
- definition files [BAM], managing
ms.assetid: 86f19030-e510-4527-ba74-10498c361c00
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b4a55141b2e5cfbc527dd386c9f1cbdd464dc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-bam-artifact-to-an-application"></a>Ajout d'un artefact BAM à une application
Cette rubrique explique comment ajouter un artefact BAM à une application BizTalk à l'aide de la console Administration de BizTalk Server ou de la ligne de commande. L'ajout d'un fichier de définition BAM n'entraîne pas le déploiement de la définition BAM. Celle-ci est déployée lors de l'importation du fichier .msi de l'application.  
  
 Pour remplacer un artefact BAM qui existe déjà dans l'application, précisez l'option de remplacement. L’option de remplacement est requise uniquement lorsque l’artefact BAM existant porte le même nom de fichier que celui que vous souhaitez ajouter. Si non spécifié et artefact BAM existe déjà dans l’application avec le même nom que celui en cours d’ajout, l’opération d’ajout échoue.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-add-a-bam-artifact-to-an-application"></a>Pour ajouter un artefact BAM à une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **Al Programs**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk, Applications, puis l'application dans laquelle vous souhaitez ajouter un fichier d'artefact BAM.  
  
3.  Cliquez sur le **ressources** dossier, pointez sur **ajouter**, puis cliquez sur **ressources**.  
  
4.  Cliquez sur **ajouter**, sélectionnez le fichier de l’artefact BAM, puis cliquez sur **ouvrir**.  
  
5.  Dans le **type de fichier** la liste déroulante, sélectionnez **System.BizTalk : BAM**.  
  
6.  Dans **Destination**, tapez le chemin d’accès complet de l’emplacement où le fichier d’artefact doit être copié lorsque l’application est installée à partir du fichier .msi, y compris le nom de fichier. Si ce chemin n'est pas défini, le fichier ne sera pas copié dans le système de fichiers local lors de l'installation, mais il sera déployé lors de l'importation du fichier .msi.  
  
     Exemple : **C:\My Applications\MyBAMfile.xml**  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:Bam** [**/overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Bam /overwrite/source : « C:\Source BAMfiles\MyBAMfile.xml » /Destination:"%BTADInstallDir%\ BAMfiles\MyBAMfile.xml » /Server:MyDatabaseServer Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à laquelle ajouter l'artefact BAM. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : BAM** (cette valeur ne respecte pas la casse).|  
    |**/ Remplacer**|Option permettant de remplacer un artefact BAM. Si cette option n'est pas spécifiée et qu'un artefact BAM, dont le nom de fichier est le même que celui de l'artefact BAM à ajouter, existe déjà dans l'application, l'opération AddResource échoue.|  
    |**/ Source**|Chemin d'accès complet de l'artefact BAM, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
    |**Et de destination**|Chemin d'accès complet de l'emplacement où le fichier de l'artefact BAM doit être copié lorsque l'application est installée à partir du fichier .msi. Si ce paramètre n'est pas défini, le fichier n'est pas copié dans le système de fichiers local lors de l'installation. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles ("). Vous pouvez utiliser la variable d'environnement %BTADInstallDir% dans le chemin d'accès pour spécifier le dossier d'installation de l'application.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [Commande AddResource : Artefact BAM](../core/addresource-command-bam-artifact.md)   
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)   
 [Comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md)