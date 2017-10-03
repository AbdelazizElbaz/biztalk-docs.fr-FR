---
title: "Comment ajouter un fichier à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], adding files
- files, adding to applications
- managing [resources], adding files
ms.assetid: 6665b946-113a-4026-a0a3-6b67ede4b689
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4493eafe2bba4e1203a230180024e0e5a8a2ce08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-file-to-an-application"></a>Ajout d'un fichier à une application
Cette rubrique explique comment ajouter un fichier à une application BizTalk à l'aide de la console Administration de BizTalk Server ou de la ligne de commande. Les fichiers que vous ajoutez à votre application sont copiés dans le dossier d'installation de l'application. Les fichiers peuvent également être exportés dans le fichier .msi de l'application, puis déplacés vers d'autres environnements de déploiement avec l'application.  
  
> [!NOTE]
>  Pour obtenir des instructions sur l’ajout d’un fichier Lisez-moi, consultez [comment créer un lien vers un fichier Lisez-moi](../core/how-to-link-to-a-readme-file.md).  
  
 Si vous souhaitez remplacer un fichier existant déjà dans l'application, précisez l'option de remplacement. L'option de remplacement ne fonctionne que si les deux fichiers ont le même nom. Si cette option n'est pas spécifiée, et qu'un fichier portant le même nom de fichier que celui en cours d'ajout existe déjà dans l'application, l'opération d'ajout échoue.  
  
> [!NOTE]
>  Contrairement à ce qui se passe avec d'autres types d'artefacts, vous pouvez avoir plusieurs fichiers portant le même nom dans un groupe BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-add-a-file-to-an-application"></a>Pour ajouter un fichier à une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez la [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] et le groupe BizTalk contenant l'application à laquelle vous souhaitez ajouter le fichier.  
  
3.  Développez Applications, ainsi que l'application à laquelle vous souhaitez ajouter un fichier.  
  
4.  Cliquez sur le **ressources** dossier, pointez sur **ajouter**, puis cliquez sur **ressources**.  
  
5.  Cliquez sur **ajouter**, sélectionnez le fichier, puis cliquez sur **ouvrir**.  
  
6.  Dans le **type de fichier** la liste déroulante, sélectionnez **System.BizTalk : file**.  
  
7.  Dans **Destination**, tapez le chemin d’accès complet de l’emplacement où le fichier doit être copié lorsque l’application est installée à partir du fichier .msi, y compris le nom de fichier. Le chemin d'accès par défaut est %BTAD_InstallDir%, qui correspond au dossier d'installation de l'application. Si ce chemin d'accès n'est pas fourni, le fichier n'est pas copié dans le système de fichiers local lors de l'installation.  
  
8.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:File** [**/overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:File /overwrite/source : facultatif de /Destination « Files\File.txt C:\Source » : « C:\New Files\File.txt » /Server:MyDatabaseServer Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à laquelle ajouter le fichier. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : file** (cette valeur ne respecte pas la casse).|  
    |**/ Remplacer**|Option permettant de mettre à jour un fichier existant. Si cette option n'est pas spécifiée et qu'un fichier, dont le nom est le même que celui du fichier à ajouter, existe déjà dans l'application, l'opération AddResource échoue.|  
    |**/ Source**|Chemin d'accès complet du fichier, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
    |**Et de destination**|Chemin d'accès complet de l'emplacement où le fichier doit être copié lorsque l'application est installée à partir du fichier .msi. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles ("). Si ce paramètre n'est pas défini, le fichier n'est pas copié dans le système de fichiers local lors de l'installation.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [Commande AddResource : fichier](../core/addresource-command-file.md)   
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)