---
title: "Comment ajouter un Script de pré-traitement ou de post-traitement à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], adding scripts
- managing [scripts], applications
- applications, scripts
- managing [scripts], adding
- scripts, adding to applications
- scripts
ms.assetid: 729cb236-b9cf-468a-8b98-a24d86e60d3c
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d0646bc9e896e7b4e4d9264efba7c9bb5f0eb66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-pre--or-post-processing-script-to-an-application"></a>Ajout d'un script de prétraitement ou de post-traitement à une application
Cette rubrique décrit comment ajouter un script de pré-traitement ou de post-traitement à une application à l'aide de la console Administration de BizTalk Server ou de la ligne de commande. Lorsque vous ajoutez un script à une application, le script est inclus dans le fichier .msi de l'application et s'exécute quand l'application est importée, installée ou désinstallée.  
  
 Lorsque vous ajoutez un script, vous devez préciser s'il s'agit d'un script de pré-traitement qui s'exécute avant l'importation ou l'installation d'une application, ou d'un script de post-traitement qui s'exécute après l'importation ou l'installation. Scripts de pré-traitement et de post-traitement s’exécutent aussi pendant la désinstallation, dans l’ordre inverse de leur exécution lors de l’installation : scripts de pré-traitement s’exécutent après la désinstallation et exécutent des scripts de post-traitement avant la désinstallation.  
  
 Vous pouvez également supprimer un script d'une application. Pour obtenir des instructions, consultez [suppression antérieur ou un Script de post-traitement à partir d’une Application](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-add-a-script-to-an-application"></a>Pour ajouter un script à une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Développez le groupe BizTalk, puis Applications, et cliquez avec le bouton droit sur le dossier de l'application à laquelle vous souhaitez ajouter un script.  
  
3.  Pointez sur **ajouter**, effectuez l’une des opérations suivantes :  
  
    -   Cliquez sur **Scripts de pré-traitement** si vous souhaitez que le script à exécuter avant l’importation de l’application ou l’installation ou après la désinstallation.  
  
    -   Cliquez sur **Scripts de post-traitement** si vous souhaitez que le script s’exécute après l’importation ou l’installation, ou avant la désinstallation.  
  
4.  Cliquez sur **ajouter** et recherchez le fichier de script à ajouter.  
  
5.  Sélectionnez le fichier de script, cliquez sur **ouvrir**.  
  
6.  Si vous souhaitez remplacer un fichier de script qui existe déjà dans l’application, sélectionnez le **remplacer tous les** case à cocher. Le fichier de script doit porter le même nom que celui qui doit être remplacé. Sinon, le nouveau script est ajouté et le script existant demeure inchangé dans l'application.  
  
7.  Cliquez sur le **type de fichier** liste déroulante, puis cliquez sur le type de fichier, soit **System.BizTalk : preprocessingscript** ou **System.BizTalk : postprocessingscript**.  
  
8.  Si nécessaire, dans **l’emplacement de Destination** tapez le chemin d’accès où vous souhaitez que le script de fichier pour être copié lorsque l’application est installée, puis cliquez sur **OK**. Le chemin d'accès par défaut installe le script dans le dossier d'installation de l'application (%BTAD_InstallDir%).  
  
> [!NOTE]
>  Si vous n'indiquez pas de chemin d'accès, le script ne sera pas copié dans le système de fichiers local lors de l'installation. Si ce script doit être exécuté pendant la désinstallation d'une application, vous devez indiquer le chemin d'accès, sinon le script ne sera pas copié dans le système de fichiers local et ne pourra pas être exécuté pendant une désinstallation.  
  
 Le script est ajouté à l'application et s'affiche dans le dossier Ressources de l'application.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:PreProcessingScript**&#124; **System.BizTalk : postprocessingscript** [**/overwrite**] **/Source :***valeur* [**facultatif /Destination :**  *valeur*] [**/Server :***valeur*] [**/Database :***valeur*] [**/Property:Args = »**  *liste d’arguments***»**]  
  
     Exemple :  
  
     **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:PreProcessingScript /overwrite/source : facultatif de /Destination « Scripts\MyScript.vbs C:\Source » : « C:\New Scripts\MyScript.vbs » /Server:MyDatabaseServer Server /Property:args = « argument1 argument2 »**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à laquelle ajouter le script. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : preprocessingscript** ou **System.BizTalk : postprocessingscript**, selon le type de script à ajouter. Utilisez **System.BizTalk : preprocessingscript** si vous souhaitez que le script à exécuter avant l’importation ou l’installation ou après la désinstallation. Utilisez **System.BizTalk : postprocessingscript** si vous souhaitez que le script s’exécute après l’importation ou l’installation, ou avant la désinstallation.|  
    |**/ Remplacer**|Met à jour un script existant. Si cette option n'est pas spécifiée et qu'un script, dont le nom est le même que celui du fichier de script à ajouter, existe déjà dans l'application, l'opération d'ajout échoue.|  
    |**/ Source**|Chemin d'accès complet du fichier de script, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
    |**Et de destination**|Chemin d'accès complet de l'emplacement où le fichier de script doit être copié lorsque l'application est installée à partir du fichier .MSI. Si ce paramètre n'est pas défini, le fichier n'est pas copié dans le système de fichiers local lors de l'installation. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
    |**/Property:args =**|Zéro ou plusieurs arguments. Les arguments fournis ici sont transmis au script lorsque ce dernier est appelé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Scripts de pré-traitement et post-traitement](../core/managing-pre-and-post-processing-scripts.md)   
 [Commande AddResource : Script de prétraitement](../core/addresource-command-preprocessing-script.md)   
 [Commande AddResource : Script de post-traitement](../core/addresource-command-postprocessing-script.md)