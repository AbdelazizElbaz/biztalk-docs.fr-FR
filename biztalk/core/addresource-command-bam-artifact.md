---
title: "Commande AddResource : Artefact | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9de7a82-9b06-4d50-9678-73140e80d0af
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2753be55fa8cf71b04bbf34d2fdfd8d1190e65e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-bam-artifact"></a>Commande AddResource : Artefact BAM
Pour ajouter un artefact BAM à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : BAM** pour le paramètre de Type. L'exécution de cette commande permet d'ajouter le fichier de l'artefact BAM à la base de données de gestion BizTalk. Cet artefact s'affiche également dans la console Administration de BizTalk Server, dans le dossier Ressources de l'application pour laquelle vous l'avez ajouté. En outre, le fichier apparaît lorsque vous utilisez la [commande ListApp](../core/listapp-command.md).  
  
 L'ajout d'une définition BAM à l'aide de la commande AddResource n'entraîne pas son déploiement. Néanmoins, lorsqu'un fichier .msi qui comprend une définition BAM est importé dans une application à l'aide de l'Assistant Importation, la définition BAM est déployée sur l'ordinateur local.  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:Bam**[**/overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk à laquelle ajouter l'artefact BAM. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe.|  
|**/ Type** (ou **/T**, consultez la section Notes)|Oui|**System.BizTalk : BAM** (cette valeur ne respecte pas la casse).|  
|**/ Remplacer** (ou **/O**, consultez la section Notes)|Non|Option permettant de mettre à jour un artefact BAM. Si cette option n'est pas spécifiée et qu'un artefact, dont le nom est le même que celui de l'artefact BAM à ajouter, existe déjà dans l'application, l'opération AddResource échoue.|  
|**/ Source** (ou **/So**, consultez la section Notes)|Oui|Chemin d'accès complet de l'artefact BAM, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
|**/ Destination** (ou **De**, consultez la section Notes)|Non|Chemin d'accès complet de l'emplacement où le fichier de l'artefact BAM doit être copié lorsque l'application est installée à partir du fichier .msi. Si ce paramètre n'est pas défini, le fichier n'est pas copié dans le système de fichiers local lors de l'installation. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
|**/ Serveur** (ou **/Se**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si n’est fourni, la base de données de gestion BizTalk en cours d’exécution dans l’instance locale de SQL Server est utilisé.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource, /ApplicationName:MyApplication/type : System.BizTalk : BAM /overwrite/source : facultatif de /Destination « BAMfiles\MyBAMfile.xml C:\Source » : « C:\New BAMfiles\MyBAMfile.xml » /Server:MyDatabaseServer Server**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter un artefact BAM à une Application](../core/how-to-add-a-bam-artifact-to-an-application.md)