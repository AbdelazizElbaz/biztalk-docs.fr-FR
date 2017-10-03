---
title: "Commande AddResource : L’Assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c18607b5-d929-48c9-9fa3-f728a7a80d04
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94cf353abb1e601a14c9e2f081fa2946f1e3ed24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-biztalk-assembly"></a>Commande AddResource : L’Assembly BizTalk
Pour ajouter un assembly BizTalk à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : BiztalkAssembly** pour le paramètre de Type. L'exécution de cette commande ajoute l'assembly à la base de données de gestion BizTalk. Cet assembly s'affiche également dans la console Administration de BizTalk Server, dans le dossier Ressources de l'application à laquelle vous l'avez ajouté. Les artefacts intégrés à l'assembly sont également affichés dans les dossiers appropriés. En outre, les artefacts sont répertoriés lorsque vous utilisez la [commande ListApp](../core/listapp-command.md).  
  
 Lors de l'utilisation de cette commande, gardez à l'esprit les points suivants :  
  
-   Si un assembly porte le même nom complet qu'un assembly existant dans l'application, vous devez spécifier le paramètre Overwrite. À défaut, l'opération correspondant à la commande AddResource échoue. Le nom complet de l'assembly se compose de son nom, d'un jeton de clé publique, de sa culture et de sa version. Si une autre application dépend de cet assembly, l'opération AddResource échoue, que vous spécifiiez ou non le paramètre Overwrite.  
  
-   Si un autre assembly portant le même nom complet existe dans le groupe, la commande AddResource échoue, que vous spécifiiez ou non le paramètre Overwrite.  
  
-   Si vous remplacez un assembly qui contient des orchestrations, les orchestrations doivent être arrêtées et désinscrites avant l'exécution de la commande. De même, les ports d'envoi auxquels les orchestrations sont liées doivent être arrêtés et désinscrits, et les emplacements de réception désactivés.  
  
-   L'opération AddResource échoue également si l'assembly que vous ajoutez dépend d'un artefact qui n'est pas inclus dans l'application.  
  
 Pour plus d’informations sur les dépendances, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:BizTalkAssembly** [**/Overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Options:GacOnAdd** *&#124;* **GacOnInstall***&#124;* **GacOnImport**] [**/Server :***valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk à laquelle ajouter l'assembly. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut.|  
|**/ Type** (ou **/T**, consultez la section Notes)|Oui|**System.BizTalk : BiztalkAssembly** (cette valeur ne respecte pas la casse).|  
|**/ Remplacer** (ou **/Ov**, consultez la section Notes)|Non|Option permettant de mettre à jour un assembly existant. Si cette option n'est pas spécifiée et qu'un assembly, dont le nom complet est le même que celui de l'assembly à ajouter, existe déjà dans l'application, l'opération AddResource échoue. Ce nom complet correspond à l'identificateur unique local (LUID) de l'assembly. Vous pouvez afficher la liste des LUID pour les artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md). Si une autre application dépend de l'assembly qui doit être remplacé, l'opération AddResource échoue, même lorsque ce paramètre est spécifié.|  
|**/ Source** (ou **/So**, consultez la section Notes)|Oui|Chemin d'accès complet du fichier de l'assembly, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
|**/ Destination** (ou **/De**, consultez la section Notes)|Non|Chemin d'accès complet de l'emplacement où le fichier de l'assembly doit être copié lorsque l'application est installée à partir du fichier .msi. Si n’est fourni, le fichier d’assembly n’est pas copié dans le système de fichiers local lors de l’installation. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles ("). **Remarque :** environnement variable % BTAD_InstallDir %, qui est définie lors de l’installation de BizTalk Server, vous permet de spécifier le dossier d’installation de l’application. Cela permet de créer, pour les fichiers des applications, un emplacement qui est similaire sur les différents ordinateurs de destination. Exemple : « % BTAD_InstallDir%\MyFiles\Orchestrations.dll »|  
|**/ Options** (ou **/Op**, consultez la section Notes)|Non|-   **GacOnAdd**: spécifier pour installer l’assembly dans le global assembly cache (GAC) sur l’ordinateur local pendant l’opération AddResource.<br />-   **GacOnInstall**: spécifiez d’installer l’assembly dans le GAC lors de l’application est installée à partir du fichier .msi.<br />-   **GacOnImport**: spécifiez d’installer l’assembly dans le GAC lors de l’importation du fichier .msi de l’application.<br /><br /> Si vous spécifiez plusieurs options, séparez-les par des virgules.|  
|**/ Serveur** (ou **/Se**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:BizTalkAssembly de remplacement**  
  
 **/Options:GacOnInstall /source:"%BTAD_InstallDir%\Source Assemblies\Orchestrations.dll » /Destination:"%BTAD_InstallDir%\New Assemblies\Orchestrations.dll », GacOnImport /Server:MyDatabaseServer Server**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter un Assembly BizTalk à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md)