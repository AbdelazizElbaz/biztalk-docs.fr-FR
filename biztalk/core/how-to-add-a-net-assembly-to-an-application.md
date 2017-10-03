---
title: "Comment ajouter un Assembly .NET à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [.NET assemblies], adding to applications
- managing [applications], .NET assemblies
- managing [.NET assemblies], applications
- applications, .NET assemblies
- .NET assemblies, adding to applications
ms.assetid: 75dc3303-a622-40df-881e-3109cbc81c91
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b455dfb8f84580e3a8a4f5b6e2322c4f4e1d1b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-net-assembly-to-an-application"></a>Ajout d'un assembly .NET à une application
Cette rubrique décrit comment ajouter un assembly .NET qui n'est pas un assembly BizTalk à une application BizTalk à l'aide de la console Administration de BizTalk Server ou de la ligne de commande. Lorsque vous ajoutez un assembly .NET à une application, gardez les points importants suivants à l'esprit :  
  
-   Si vous souhaitez remplacer un assembly existant déjà dans l'application, précisez l'option de remplacement. L'option de remplacement est nécessaire uniquement si les deux assemblys ont le même LUID. Si cette option n'est pas spécifiée, et qu'un assembly ayant le même LUID que celui en cours d'ajout existe déjà dans l'application, l'opération d'ajout échoue. Vous pouvez afficher la liste des LUID pour les artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md).  
  
-   Lorsque vous ajoutez un assembly .NET, vous pouvez préciser une ou plusieurs des options suivantes pour installer l'assembly dans le GAC (global assembly cache) :  
  
    -   **Ajouter au global assembly cache sur Ajouter une ressource (gacutil).** Si vous sélectionnez cette option, l'assembly est installé dans le GAC sur l'ordinateur local lorsque l'assembly est ajouté à une application, suite à l'utilisation des procédures de cette rubrique.  
  
    -   **Ajouter au global assembly cache lors de l’importation du fichier MSI (gacutil).** Lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que le fichier .msi est importé dans un groupe BizTalk, l'assembly est installé dans le GAC sur l'ordinateur local au cours de la procédure d'importation. Sélectionnez cette option si votre application comprend une stratégie et un assembly dont dépend la stratégie. Vous devez procéder ainsi car lorsque vous importez une application contenant une stratégie, tous les assemblys dont dépend la stratégie doivent être présents dans le GAC.  
  
    -   **Ajoutez dans le global assembly cache lors de l’installation du fichier MSI (gacutil).** Lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, l'assembly est installé dans le GAC sur l'ordinateur local au cours de la procédure d'installation.  
  
    -   **Rendre visible pour les composants COM (regasm).** lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, un assembly COM géré est ajouté au Registre Windows sur l'ordinateur local au cours de la procédure d'installation. Si vous spécifiez cette option, vous devez également préciser un emplacement pour le fichier dans Destination.  
  
    -   **Inscrire les composants traités (regsvcs).** lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, un assembly COM+ géré est ajouté au Registre Windows sur l'ordinateur local au cours de la procédure d'installation. Si vous spécifiez cette option, vous devez également préciser un emplacement pour le fichier dans Destination.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-add-a-net-assembly-to-an-application"></a>Pour ajouter un assembly .NET à une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, **Applications**, puis développez l’application à laquelle vous souhaitez ajouter l’assembly .NET.  
  
3.  Cliquez sur le **ressources** dossier, pointez sur **ajouter**, puis cliquez sur **ressources**.  
  
4.  Cliquez sur **ajouter**et cliquez sur l’assembly, puis cliquez sur **ouvrir**.  
  
5.  Dans le **type de fichier** la liste déroulante, sélectionnez **System.BizTalk : assembly**.  
  
6.  Dans **Options**, sélectionnez les options de déploiement pour cet assembly.  
  
7.  Dans **Destination**, tapez le chemin d’accès complet de l’emplacement où le fichier doit être copié lorsque l’application est installée à partir du fichier .msi, y compris le nom de fichier. Si ce chemin d'accès n'est pas fourni, le fichier n'est pas copié dans le système de fichiers local lors de l'installation. Pour copier le fichier dans le dossier d'installation de l'application, vous pouvez inclure dans le chemin d'accès la variable d'environnement %BTAD_InstallDir%, qui extrait la valeur du dossier d'installation de l'application au moment où l'application est installée. Ainsi, vous n'avez pas besoin de connaître le chemin d'accès au dossier d'installation de l'application lorsque vous indiquez l'emplacement de destination.  
  
     Exemple : **%BTADInstall_Dir%\Assemblies\Orchestrations.dll**  
  
8.  Cliquez sur le **dépendances** onglet et afficher les artefacts dont dépend cet assembly.  
  
9. Si un artefact dont dépend cet assembly n’est pas présent dans cette application, et que vous souhaitez ajouter, cliquez sur **ajouter à l’Application**, naviguez jusqu'à l’artefact, puis cliquez sur **ouvrir**.  
  
10. Lorsque vous avez terminé, cliquez sur **OK**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante, en remplaçant par les valeurs appropriées, comme décrit dans le tableau suivant.  
  
     **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:Assembly** [**/overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Options:GacOnAdd** *&#124;*  **GacOnInstall***&#124;* **GacOnImport**&#124; **RegasmOnInstall**&#124; **RegsvcsOnInstall**] [**/Server :***valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Assembly /overwrite/source : « C:\Source Assemblies\MyAssembly.dll » /Destination:"%BTAD_InstallDir%\New Assemblies\MyAssembly.dll » /Options:GacOnAdd, RegasmOnInstall /Server:MyDatabaseServer Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à laquelle ajouter l'assembly. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : assembly** (cette valeur ne respecte pas la casse).|  
    |**/ Remplacer**|Option permettant de mettre à jour un assembly existant. Si cette option n'est pas spécifiée et qu'un assembly, dont le nom complet est le même que celui de l'assembly à ajouter, existe déjà dans l'application, l'opération AddResource échoue. Le nom complet de l'assembly se compose de son nom de fichier, d'un jeton de clé publique, de sa culture et de sa version. Vous pouvez afficher la liste des LUID pour les artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md).|  
    |**/ Source**|Chemin d'accès complet du fichier de l'assembly, nom du fichier inclus. Si le chemin d’accès comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Et de destination**|Chemin d'accès complet de l'emplacement où le fichier de l'assembly doit être copié lorsque l'application est installée à partir du fichier .msi. Si n’est fourni, le fichier d’assembly n’est pas copié dans le système de fichiers local lors de l’installation. Si le chemin comprend des espaces, vous devez le placer entre guillemets doubles ("). Si vous spécifiez l'option RegasmOnInstall ou RegsvcsOnInstall, vous devez également spécifier Destination. **Remarque :** vous pouvez utiliser la variable d’environnement % BTAD_InstallDir % dans le chemin d’accès. Elle extrait la valeur du dossier d'installation de l'application au moment où l'application est installée. Ainsi, vous n'avez pas besoin de connaître le chemin d'accès au dossier d'installation de l'application lorsque vous indiquez l'emplacement de destination. Exemple : %BTAD_InstallDir%\Assemblies\Orchestrations.dll|  
    |**/ Options**|-   **GacOnAdd**: installer l’assembly dans le global assembly cache (GAC) sur l’ordinateur local pendant l’opération AddResource.<br />-   **GacOnInstall**: installer l’assembly dans le GAC lors de l’application est installée à partir du fichier .msi.<br />-   **GacOnImport**: installer l’assembly dans le GAC lors de l’importation du fichier .msi de l’application.<br />-   **RegasmOnInstall**: ajouter un assembly COM géré au Registre Windows lorsque l’application est installée à partir du fichier .msi. Si vous définissez cette option, vous devez également définir le paramètre Destination.<br />-   **RegsvcsOnInstall**: ajouter un assembly COM + géré au Registre Windows lorsque l’application est installée à partir du fichier .msi. Si vous définissez cette option, vous devez également définir le paramètre Destination.<br /><br /> Si vous spécifiez plusieurs options, séparez-les par des virgules.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [Commande AddResource : Assembly .NET](../core/addresource-command-net-assembly.md)   
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)