---
title: "Comment ajouter un composant COM à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], COM components
- managing [resources], COM components
- applications, COM components
- COM components, applications
ms.assetid: fdda1a9d-96af-41fe-9d94-ee1fbd80a7c9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3e32e05fbc7ba9f08a7bbbd5fd546033806c3ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-com-component-to-an-application"></a>Ajout d'un composant COM à une application
Cette rubrique décrit comment ajouter un composant COM à une application BizTalk à l'aide de la console Administration de BizTalk Server ou de l'invite de commandes :  
  
 Lorsque vous ajoutez un composant COM à une application, gardez les points importants suivants à l'esprit :  
  
-   Si vous souhaitez remplacer un composant COM existant déjà dans l'application, précisez l'option de remplacement. L’option permettant d'écraser n’est nécessaire que lorsque les deux artefacts sont dotés du même identificateur local unique (LUID). Si cette option n'est pas spécifiée, et qu'un composant COM ayant le même LUID que celui en cours d'ajout existe déjà dans l'application, l'opération d'ajout échoue. Vous pouvez afficher la liste des LUID pour les artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md).  
  
-   BizTalk Server ne vérifie pas la présence des dépendances des composants COM, c’est pourquoi vous devez vérifiez que tous les artefacts dont dépend le composant sont présents.  
  
-   Si vous ajoutez un composant COM ou COM+ non managé pour ordinateur 64 bits et essayez d'installer l'application comprenant ledit composant sur un ordinateur 32 bits, vous n'y parviendrez pas. Un tel composant ne peut être installé que sur un ordinateur 64 bits.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-add-a-com-component-to-an-application"></a>Pour ajouter un composant COM à une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration, le groupe BizTalk, Applications, puis l'application dans laquelle vous souhaitez ajouter le composant COM.  
  
3.  Cliquez sur le **ressources** dossier, pointez sur **ajouter**, puis cliquez sur **ressources**.  
  
4.  Cliquez sur **ajouter**, sélectionnez le composant COM, puis cliquez sur **ouvrir**.  
  
5.  Dans le **type de fichier** la liste déroulante, cliquez sur **System.BizTalk : com**.  
  
6.  Dans **Options**, activez ou désactivez le **enregistrer le fichier de destination (regsvr32)** selon si vous souhaitez que le composant à ajouter au Registre Windows lorsque l’application est installé.  
  
7.  Dans **Destination**, tapez le chemin d’accès complet de l’emplacement où le composant COM doit être copié lorsque l’application est installée à partir du fichier .msi, y compris le nom de fichier. Si ce chemin d'accès n'est pas fourni, le fichier n'est pas copié dans le système de fichiers local lors de l'installation. Ce chemin d’accès est requis si vous avez sélectionné le **enregistrer le fichier de destination (regsvr32)** case à cocher à l’étape précédente.  
  
     Exemple : **%BTAD_InstallDir%\MyComponent.dll**  
  
8.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:Com** [**/overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Options:Regsvr32OnInstall** ] [**/Server :***valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Com /overwrite/source : facultatif de « C:\Source Components\COM.dll » /Destination : /Server:MyDatabaseServer/Database /Options:Regsvr32OnInstall de « C:\New Components\COM.dll » : BizTalkMgmtDb**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à laquelle ajouter le composant COM. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : com** (cette valeur ne respecte pas la casse).|  
    |**/ Remplacer**|Option permettant de mettre à jour un composant COM existant. Si cette option n'est pas spécifiée et qu'un composant COM, dont l’identificateur unique local LUID est le même que celui du composant COM à ajouter, existe déjà dans l'application, l'opération AddResource échoue. Vous pouvez afficher la liste des LUID pour les artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md).|  
    |**/ Source**|Chemin d'accès complet du fichier de composant COM, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
    |**Et de destination**|Chemin d'accès complet de l'emplacement où le fichier .dll du composant COM doit être copié lorsque l'application est installée à partir du fichier .msi. Si ce paramètre n'est pas défini, le fichier n'est pas copié dans le système de fichiers local lors de l'installation. Par conséquent, le composant ne peut pas être ajouté au Registre Windows au cours de cette installation. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles ("). Si vous définissez le paramètre Regsvr32OnInstallOption, vous devez également définir le paramètre Destination.|  
    |**/ Options**|**Regsvr32OnInstall.** Permet d'ajouter le composant COM au Registre Windows lorsque l'application est installée à partir du fichier .msi. Si vous définissez cette option, vous devez également définir le paramètre Destination.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [Commande AddResource : Un composant COM](../core/addresource-command-com-component.md)   
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)