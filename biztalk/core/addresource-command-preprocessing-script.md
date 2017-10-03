---
title: "Commande AddResource : Script de prétraitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b4f66e5-1f40-4bc3-82a8-c27a0e435797
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5255bfa0bfe73941b69d8e6b95f2230a9dfbd85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-preprocessing-script"></a>Commande AddResource : Script de prétraitement
Pour ajouter un script de pré-traitement à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : preprocessingscript** pour le paramètre de Type. L'exécution de cette commande permet d'ajouter le fichier du script à la base de données de gestion BizTalk. Ce fichier s'affiche également dans la console Administration de BizTalk Server, dans le dossier Ressources de l'application pour laquelle vous l'avez ajouté. En outre, le fichier apparaît lorsque vous utilisez la [commande ListApp](../core/listapp-command.md).  
  
 Un script de pré-traitement s'exécute à partir du fichier .msi avant l'importation ou l'installation d'une application ou après sa désinstallation. Vous pouvez également utiliser l’outil BTSTask pour ajouter un script de post-traitement qui s’exécute après l’importation ou l’installation, ou avant la désinstallation, comme décrit dans [commande AddResource : scripts de post-traitement](../core/addresource-command-postprocessing-script.md). Pour plus d’informations sur le prétraitement et de scripts de post-traitement, voir [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:PreProcessingScript**[**/Overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Server :**  *valeur*] [**/Database :***valeur*] [**/Property:Args = «***liste d’arguments***»** ]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk à laquelle ajouter le script. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe.|  
|**/ Type** (ou **/T**, consultez la section Notes)|Oui|**System.BizTalk : preprocessingscript** (cette valeur ne respecte pas la casse).|  
|**/ Remplacer** (ou **/O**, consultez la section Notes)|Non|Option permettant de mettre à jour un script existant. Si non spécifié et un fichier de script existe déjà dans l’application qui a le même nom que le fichier de script est ajouté, l’opération d’ajout échoue.|  
|**/ Source** (ou **/So**, consultez la section Notes)|Oui|Chemin d'accès complet du fichier de script, nom du fichier inclus. Si le chemin d’accès contient des espaces, vous devez le placer entre guillemets doubles («).|  
|**/ Destination** (ou **/De**, consultez la section Notes)|Non|Chemin d'accès complet de l'emplacement où le fichier de script doit être copié lorsque l'application est installée à partir du fichier .msi. Si ce paramètre n'est pas défini, le fichier n'est pas copié dans le système de fichiers local lors de l'installation. Si ce script doit être exécuté pendant la désinstallation d'une application, vous devez définir le paramètre Destination. À défaut, le script ne sera pas copié dans le système de fichiers local et ne pourra pas être exécuté pendant une désinstallation. Si le chemin d’accès contient des espaces, vous devez le placer entre guillemets doubles («).|  
|**/ Serveur** (ou **/Se**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si n’est fourni, la base de données de gestion BizTalk en cours d’exécution dans l’instance locale de SQL Server est utilisé.|  
|**/ Propriété** (ou **/P**, consultez la section Notes)|Non|Propriété(s) de ressource transmise(s) au script en tant qu'arguments lorsque le script est appelé.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource, /ApplicationName:MyApplication/type : System.BizTalk : preprocessingscript /overwrite/source : facultatif de /Destination « Scripts\MyScript.vbs C:\Source » : « C:\New Scripts\MyScript.vbs » /Server:MyDatabaseServer Server /Property:args = « argument1 argument2 »**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
 Les extensions suivantes sont prises en charge pour les fichiers de script : .com, .exe, .bat, .cmd, .vbs, .vbe, .js, .jse, .wsf, .wsh.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter un Script de pré-traitement ou de post-traitement à une Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)