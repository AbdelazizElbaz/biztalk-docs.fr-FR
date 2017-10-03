---
title: Commande ExportApp | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6217d0f1-cf39-4520-87c8-8d25b21865af
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 966e53a7c74ce687724a77ea57888a4c61bb2773
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exportapp-command"></a>Commande ExportApp
Cette commande permet d'exporter une application BizTalk dans un fichier .msi. Si un fichier .msi dont le nom et le chemin d'accès sont identiques existe déjà, il est remplacé.  
  
 Vous pouvez utiliser le paramètre ResourceSpec pour exporter de manière sélective les artefacts d'une application dans un fichier .msi. Vous spécifiez les artefacts à exporter en modifiant le fichier XML créé lorsque vous exécutez le **ListApp** commande avec le paramètre ResourceSpec, comme décrit dans [commande ListApp](../core/listapp-command.md). Vous utilisez ensuite l’emplacement de ce fichier XML en tant que la valeur du paramètre ResourceSpec lors de l’exécution le **ExportApp** commande. Ainsi, seuls les artefacts mentionnés dans le fichier XML spécifié sont exportés dans le fichier .msi.  
  
> [!NOTE]
>  Pour des raisons de sécurité, pendant l'exportation d'une application, les mots de passe sont supprimés des liaisons d'application. Ils ne sont pas supprimés des fichiers de liaison qui ont été ajoutés à l’application. Après avoir installé l'application à partir du fichier .msi, vous devez reconfigurer les mots de passe afin que l'application fonctionne correctement.  
>   
>  De plus, des clés privées sont supprimées des fichiers de certificat.  
  
## <a name="usage"></a>Utilisation  
 **BTSTask ExportApp** [**« ApplicationName » :***valeur*] **/Package :***valeur* [**/ Spécification de ressource :***valeur*] [**/GlobalParties**] [**/Server :***valeur*] [**/ Base de données :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk à exporter. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe.|  
|**/ Package** (ou **/P**, consultez la section Notes)|Oui|Chemin d'accès complet du fichier .msi. Si le chemin d’accès comprend des espaces, vous devez le placer entre guillemets («). Exemple : Package : « Files\My.msi MSI C:\My »|  
|**/ Spécification de ressource** (ou **/R**, consultez la section Notes)|Non|Chemin d'accès complet du fichier de spécification des ressources. Si le chemin d’accès comprend des espaces, vous devez le placer entre guillemets («). Exemple : Spécification de ressource : « C:\My Files\MyResourceSpec.xml »|  
|**/ GlobalParties** (ou **/G**, consultez la section Notes)|Non|Si ce paramètre est défini, les informations du tiers global pour le groupe sont exportées dans le fichier .msi.|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/D**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="sample"></a>Exemple  
 **ExportApp /ApplicationName:MyApplication /Package:C:\MSI\MyApplication.msi**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
 [Comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md)