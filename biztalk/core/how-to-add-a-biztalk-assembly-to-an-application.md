---
title: "Comment ajouter un Assembly BizTalk à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], adding assemblies
- assemblies, applications
- managing [assemblies], adding to applications
- applications, assemblies
- managing [assemblies], applications
ms.assetid: 1525a0f6-cb0f-43bf-a851-40c06ab2135e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9165415ec736c7cf9f4716e8fb183395602a687d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-add-a-biztalk-assembly-to-an-application"></a>Ajout d'un assembly BizTalk à une application
Cette rubrique décrit comment ajouter un assembly BizTalk à une application à l'aide de la console Administration de BizTalk Server ou de la ligne de commande.  
  
 Lorsque vous ajoutez un assembly BizTalk à une application, gardez les points importants suivants à l'esprit :  
  
-   Si vous voulez ajouter un assembly et replacer un assembly ayant le même LUID que celui qui existe déjà dans l'application, sélectionnez l'option Remplacer. Si non spécifié et si un assembly qui a le même LUID que l’assembly à ajouter déjà existant dans l’application que l’opération échoue. Le LUID de l'assembly se compose du nom de fichier de l'assembly, d'un jeton de clé publique, de sa culture et de sa version. Vous pouvez afficher la liste des LUID pour les artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md).  
  
-   L'opération d'ajout échoue également si l'assembly que vous ajoutez dépend d'un artefact qui n'est pas inclus dans l'application.  
  
-   Lorsque vous ajoutez un assembly BizTalk, vous pouvez préciser une ou plusieurs des options suivantes pour installer l'assembly dans le GAC (global assembly cache) :  
  
    -   **Ajouter au global assembly cache sur Ajouter une ressource (gacutil).** Si vous sélectionnez cette option, l'assembly est installé dans le GAC sur l'ordinateur local lorsque l'assembly est ajouté à une application, suite à l'utilisation des procédures de cette rubrique.  
  
    -   **Ajouter au global assembly cache lors de l’importation du fichier MSI (gacutil).** Lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que le fichier .msi est importé dans un groupe BizTalk, l'assembly est installé dans le GAC sur l'ordinateur local au cours de la procédure d'importation.  
  
    -   **Ajoutez dans le global assembly cache lors de l’installation du fichier MSI (gacutil).** Lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, l'assembly est installé dans le GAC sur l'ordinateur local au cours de la procédure d'installation.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-add-a-biztalk-assembly-to-an-application"></a>Pour ajouter un assembly BizTalk à une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez Administration de BizTalk Server et le groupe BizTalk contenant l’application à laquelle vous souhaitez ajouter l’assembly BizTalk.  
  
3.  Développez Applications, ainsi que l'application à laquelle vous souhaitez ajouter l'assembly BizTalk.  
  
4.  Avec le bouton droit **ressources**, pointez sur **ajouter** puis cliquez sur **assemblys BizTalk**.  
  
5.  Cliquez sur **ajouter**, sélectionnez le fichier d’assembly BizTalk, puis cliquez sur **ouvrir**.  
  
6.  Dans **Destination**, tapez le chemin d’accès complet de l’emplacement où le fichier d’assembly doit être copié lorsque l’application est installée à partir du fichier .msi, y compris le nom de fichier. Si n’est fourni, le fichier d’assembly n’est pas copié dans le système de fichiers local lors de l’installation.  
  
7.  Dans **Options**, spécifiez les options d’installation de l’assembly BizTalk dans le GAC, puis cliquez sur **OK**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:BizTalkAssembly** [**/Overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Options:GacOnAdd**&#124; **GacOnInstall**&#124; **GacOnImport**] [**/Server :***valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:BizTalkAssembly /overwrite/source : facultatif /Destination de « C:\BizTalk Assemblies\MyOrchestration.dll » : « MyOrchestration.dll de BizTalk Assemblies\ C:\New » /Server : MonServeurBaseDeDonnées Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à laquelle ajouter l'assembly BizTalk. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : BiztalkAssembly**|  
    |**/ Remplacer**|Option permettant de mettre à jour un assembly existant. Si cette option n'est pas spécifiée et qu'un assembly, dont le LUID est le même que celui de l'assembly à ajouter, existe déjà dans l'application, l'opération AddResource échoue. Vous pouvez afficher la liste des LUID pour les artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md). Si une autre application dépend de l'assembly qui doit être remplacé, l'opération AddResource échoue, même lorsque ce paramètre est spécifié.|  
    |**/ Source**|Chemin d'accès complet du fichier de l'assembly, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
    |**Et de destination**|Chemin d'accès complet de l'emplacement où le fichier de l'assembly doit être copié lorsque l'application est installée à partir du fichier .msi. Si n’est fourni, le fichier d’assembly n’est pas copié dans le système de fichiers local lors de l’installation. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
    |**/ Options**|-   **GacOnAdd**: spécifier pour installer l’assembly dans le global assembly cache (GAC) sur l’ordinateur local pendant l’opération AddResource.<br />-   **GacOnInstall**: spécifiez d’installer l’assembly dans le GAC lors de l’application est installée à partir du fichier .msi.<br />-   **GacOnImport**: spécifiez d’installer l’assembly dans le GAC lors de l’importation du fichier .msi de l’application.<br /><br /> Si vous spécifiez plusieurs options, séparez-les par des virgules.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys BizTalk](../core/managing-biztalk-assemblies.md)   
 [Commande AddResource : assembly BizTalk](../core/addresource-command-biztalk-assembly.md)