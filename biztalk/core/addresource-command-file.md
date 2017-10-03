---
title: "Commande AddResource : Fichier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9635e43-af26-48d3-af0e-df245a8955e7
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92ed0b99c942adbb63fd7ca3bd2e29cc1ba040c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-file"></a>Commande AddResource : fichier
Pour ajouter un fichier à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : file** pour le paramètre de Type. L'exécution de cette commande ajoute le fichier à la base de données de gestion BizTalk. Ce fichier s'affiche également dans la console Administration de BizTalk Server, dans le dossier Ressources de l'application à laquelle vous l'avez ajouté. En outre, le fichier apparaît lorsque vous utilisez la [commande ListApp](../core/listapp-command.md).  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:File** [**/overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk à laquelle ajouter le fichier. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles ("). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut.|  
|**/ Type** (ou **/T**, consultez la section Notes)|Oui|**System.BizTalk : file** (cette valeur ne respecte pas la casse).|  
|**/ Remplacer** (ou **/O**, consultez la section Notes)|Non|Option permettant de mettre à jour un fichier existant. Si cette option n'est pas spécifiée et qu'un fichier, dont le nom est le même que celui du fichier à ajouter, existe déjà dans l'application, l'opération AddResource échoue.|  
|**/ Source** (ou **/So**, consultez la section Notes)|Oui|Chemin d'accès complet du fichier, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
|**/ Destination** (ou **De**, consultez la section Notes)|Non|Chemin d'accès complet de l'emplacement où le fichier doit être copié lorsque l'application est installée à partir du fichier .msi. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles ("). Si ce paramètre n'est pas défini, le fichier n'est pas copié dans le système de fichiers local lors de l'installation.|  
|**/ Serveur** (ou **/Se**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si n’est fourni, la base de données de gestion BizTalk en cours d’exécution dans l’instance locale de SQL Server est utilisé.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource, /ApplicationName:MyApplication/type : System.BizTalk : file /overwrite/source : facultatif de /Destination « Files\File.txt C:\Source » : « C:\New Files\File.txt » /Server:MyDatabaseServer Server**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter un Assembly .NET à une Application](../core/how-to-add-a-net-assembly-to-an-application.md)