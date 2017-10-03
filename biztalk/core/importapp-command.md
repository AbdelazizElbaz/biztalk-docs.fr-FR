---
title: Commande ImportApp | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8ee5a78-1e8f-4290-b70a-36f2f888a1d6
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4200b5559ddfc12597c95d0e924a0159665f5f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importapp-command"></a>Commande ImportApp
Cette commande permet d'importer dans une application BizTalk les artefacts contenus dans un fichier .msi. Si l'application n'existe pas déjà, elle est créée.  
  
 Lorsque vous importez une application, vous pouvez utiliser le paramètre /Environment pour spécifier l'environnement cible de déploiement pour l'application si vous lui avez ajouté des fichiers de liaison personnalisés pour un environnement de déploiement particulier. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md). Pour obtenir des instructions sur l’ajout de fichiers de liaison, consultez [commande AddResource : liaison BizTalk](../core/addresource-command-biztalk-binding.md).  
  
> [!NOTE]
>  Une opération d'importation expire si elle dépasse 3 600 secondes. Si vous essayez d'importer un fichier .msi et que l'opération arrive à expiration, vous devez diviser le contenu de l'application en plusieurs fichiers .msi en réexportant l'application et en sélectionnant un sous-ensemble d'artefacts à exporter. Pour plus d’informations, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
 Si l'importation échoue, BTSTask retourne le nombre d'erreurs. La plupart des actions entreprises pendant l'opération sont annulées, hormis les actions suivantes :  
  
-   Les actions effectuées par des scripts personnalisés ne sont pas annulées. Vous pouvez écrire vos scripts de manière qu'ils soient annulés à l'aide de la variable d'environnement Delete.  
  
-   Si des assemblys étaient installés dans le Global Assembly Cache (GAC), ils ne sont pas supprimés.  
  
-   Les entrées effectuées dans le registre Windows ne sont pas supprimées.  
  
 Si l'importation réussit, BTSTask retourne « 0 ».  
  
## <a name="usage"></a>Utilisation  
 **ImportApp /Package de BTSTask :** *valeur* [**/Environment :***valeur*] [**« ApplicationName » :**  *valeur*] [**/overwrite**] [**/Server :***valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ Package** (ou **/P**, consultez la section Notes)|Oui|Chemin d'accès complet du fichier .msi. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles ("). Exemple : « C:\My MSI Files\MyApplication.msi »|  
|**/ Environnement** (ou **/E**, consultez la section Notes)|Non|L'environnement cible de déploiement du fichier de liaison à appliquer, tel que Test. Il s'agit de la valeur spécifiée pour l'environnement cible de déploiement lors de l'ajout du fichier de liaison à l'application. Lorsque cette valeur n'est pas indiquée, toutes les liaisons non affectées à un environnement sont appliquées.|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk dans laquelle les artefacts du fichier .msi sont importés. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si cette valeur n'est pas définie, l'application par défaut est utilisée. Si l'application spécifiée n'existe pas déjà, elle est créée.|  
|**/ Remplacer** (ou **/O**, consultez la section Notes)|Non|Option permettant d'écraser les artefacts de l'application avec ceux du fichier .msi dotés du même identificateur local unique (LUID). Vous pouvez afficher la liste des LUID des artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md). Si cette option n'est pas spécifiée et qu'un ou plusieurs artefacts dans l'application possèdent le même LUID que des artefacts du fichier .msi, l'importation échoue.|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/D**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="sample"></a>Exemple  
 **ImportApp de BTSTask /Package:C:\MSI\MyApplication.msi /Environment:Test /ApplicationName:MyApplication de remplacement**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
 [Comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md)