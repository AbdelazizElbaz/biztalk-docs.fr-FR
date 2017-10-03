---
title: "Commande AddResource : Un composant COM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86a4f2fc-bbbe-4b4a-8008-2c79b3ebb6a1
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 757c6f334d5f3bc694b7db201467be80a3a0bc87
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-com-component"></a>Commande AddResource : Un composant COM
Pour ajouter un composant COM non managé à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : com** pour le paramètre de Type. L'exécution de cette commande permet d'ajouter le composant COM à la base de données de gestion BizTalk. Ce composant s'affiche également dans la console Administration de BizTalk Server, dans le dossier Ressources de l'application pour laquelle vous l'avez ajouté. En outre, le composant est affiché lorsque vous utilisez la [commande ListApp](../core/listapp-command.md).  
  
> [!NOTE]
>  Si vous ajoutez un composant COM ou COM+ non managé pour ordinateur 64 bits et essayez d'installer l'application comprenant ledit composant sur un ordinateur 32 bits, vous n'y parviendrez pas. Un tel composant ne peut être installé que sur un ordinateur 64 bits.  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:Com** [**/overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Options:Regsvr32OnInstall** ] [**/Server :***valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk à laquelle ajouter le composant COM. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe.|  
|**/ Type** (ou **/T**, consultez la section Notes)|Oui|**System.BizTalk : com** (cette valeur ne respecte pas la casse).|  
|**/ Remplacer** (ou **/Ov**, consultez la section Notes)|Non|Option permettant de mettre à jour un composant COM existant. Si cette option n'est pas spécifiée et qu'un composant COM, dont le nom de fichier est le même que celui du composant COM à ajouter, existe déjà dans l'application, l'opération AddResource échoue.|  
|**/ Source** (ou **/So**, consultez la section Notes)|Oui|Chemin d'accès complet du fichier de composant COM, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
|**/ Destination** (ou **/De**, consultez la section Notes)|Non|Chemin d'accès complet de l'emplacement où le fichier .dll du composant COM doit être copié lorsque l'application est installée à partir du fichier .msi. Si ce paramètre n'est pas défini, le fichier n'est pas copié dans le système de fichiers local lors de l'installation. Par conséquent, le composant ne peut pas être ajouté au Registre Windows au cours de cette installation. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles ("). Si vous définissez le paramètre Regsvr32OnInstallOption, vous devez également définir le paramètre Destination.|  
|**/ Options** (ou **/Op**, consultez la section Notes)|Non|**Regsvr32OnInstall.** Permet d'ajouter le composant COM au Registre Windows lorsque l'application est installée à partir du fichier .msi. Si vous définissez cette option, vous devez également définir le paramètre Destination.|  
|**/ Serveur** (ou **/Se**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si n’est fourni, la base de données de gestion BizTalk en cours d’exécution dans l’instance locale de SQL Server est utilisé.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource, /ApplicationName:MyApplication/type : System.BizTalk : com /overwrite/source : facultatif de « C:\Source Components\COM.dll » /Destination : /Server:MyDatabaseServer/Database /Options:Regsvr32OnInstall de « C:\New Components\COM.dll » : BizTalkMgmtDb**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter un Assembly .NET à une Application](../core/how-to-add-a-net-assembly-to-an-application.md)