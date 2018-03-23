---
title: 'Commande AddResource : Assembly .NET | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef6ec298-35fe-4845-9549-685993d2c659
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67f20e259611d312429c3bd909a85a3162f1dd64
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="addresource-command-net-assembly"></a>Commande AddResource : Assembly .NET
Pour ajouter un assembly .NET (qui inclut des composants COM ou COM + gérés) à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : assembly** pour le paramètre de Type. L'exécution de cette commande ajoute l'assembly à la base de données de gestion BizTalk. L'assembly s'affiche également dans la console Administration de BizTalk Server, dans le dossier Ressources de l'application à laquelle vous l'avez ajouté. En outre, l’assembly est répertorié, lorsque vous utilisez la [commande ListApp](../core/listapp-command.md).  
  
 Si un assembly porte le même nom complet qu'un assembly existant dans l'application, vous pouvez spécifier le paramètre Overwrite. Le nom complet de l'assembly se compose de son nom, d'un jeton de clé publique, de sa culture et de sa version. Dans ce cas, l'assembly existant est remplacé. Pour plus d’informations sur les dépendances, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [**/ApplicationName:***value*] **/Type:System.BizTalk:Assembly**[**/Overwrite**] **/Source:***value* [**/Destination:***value*] [**/Options:GacOnAdd***&#124;***GacOnInstall***&#124;***GacOnImport**&#124;**RegasmOnInstall**&#124;**RegsvcsOnInstall**] [**/Server:***value*] [**/Database:***value*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|non|Nom de l'application BizTalk à laquelle ajouter l'assembly. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe.|  
|**/ Type** (ou **/T**, consultez la section Notes)|Oui|**System.BizTalk : assembly** (cette valeur ne respecte pas la casse).|  
|**/ Remplacer** (ou **/Ov**, consultez la section Notes)|non|Option permettant de mettre à jour un assembly existant. Si cette option n'est pas spécifiée et qu'un assembly, dont le nom complet est le même que celui de l'assembly à ajouter, existe déjà dans l'application, l'opération AddResource échoue. Le nom complet comprend le nom de l’assembly, la version, culture et jeton de clé publique. Cette information s'affiche dans le champ Nom du dossier Ressources de l'application dans la console Administration de BizTalk Server.|  
|**/ Source** (ou **/So**, consultez la section Notes)|Oui|Chemin d'accès complet du fichier de l'assembly, nom du fichier inclus. Si le chemin d’accès comprend des espaces, vous devez le placer entre guillemets doubles («).|  
|**/ Destination** (ou **/De**, consultez la section Notes)|non|Chemin d'accès complet de l'emplacement où le fichier de l'assembly doit être copié lorsque l'application est installée à partir du fichier .msi. Si n’est fourni, le fichier d’assembly n’est pas copié dans le système de fichiers local lors de l’installation. Si le chemin d’accès comprend des espaces, vous devez le placer entre guillemets doubles («). Si vous spécifiez l'option RegasmOnInstall ou RegsvcsOnInstall, vous devez également spécifier Destination. **Remarque :** vous pouvez utiliser la variable d’environnement % BTAD_InstallDir % pour spécifier le dossier d’installation de l’application. Cette opération crée un emplacement cohérent pour les fichiers de l’application sur différents ordinateurs de destination. Example: "%BTAD_InstallDir%\MyAssemblies\Orchestrations.dll"|  
|**/ Options** (ou **/Op**, consultez la section Notes)|non|-   **GacOnAdd**: installer l’assembly dans le global assembly cache (GAC) sur l’ordinateur local pendant l’opération AddResource.<br />-   **GacOnInstall**: installer l’assembly dans le GAC lors de l’application est installée à partir du fichier .msi.<br />-   **GacOnImport**: installer l’assembly dans le GAC lors de l’importation du fichier .msi de l’application.<br />-   **RegasmOnInstall**: ajouter un assembly COM géré au Registre Windows lorsque l’application est installée à partir du fichier .msi. Si vous définissez cette option, vous devez également définir le paramètre Destination.<br />-   **RegsvcsOnInstall**: ajouter un assembly COM + géré au Registre Windows lorsque l’application est installée à partir du fichier .msi. Si vous définissez cette option, vous devez également définir le paramètre Destination.<br /><br /> Si vous spécifiez plusieurs options, séparez-les par des virgules. Aucun espace n'est autorisé entre les virgules et les valeurs.|  
|**/ Serveur** (ou **/Se**, consultez la section Notes)|non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|non|Nom de la base de données de gestion BizTalk. Si n’est fourni, la base de données de gestion BizTalk en cours d’exécution dans l’instance locale de SQL Server est utilisé.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource, /ApplicationName:MyApplication/type : System.BizTalk : assembly /overwrite /Source:"%BTAD_InstallDir%\Source Assemblies\MyAssembly.dll « /Destination:"%BTAD_InstallDir%\New Assemblies\MyAssembly.dll » /Options:GacOnAdd, RegasmOnInstall /Server:MyDatabaseServer Server**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter un Assembly .NET à une Application](../core/how-to-add-a-net-assembly-to-an-application.md)