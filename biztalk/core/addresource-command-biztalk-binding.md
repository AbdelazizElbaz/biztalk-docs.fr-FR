---
title: "Commande AddResource : BizTalk liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69c732d3-82c8-4615-b68f-ed29b54ebbf3
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00f9a5eac7d2c6f2be72ba78ee4c538ca505151e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="addresource-command-biztalk-binding"></a>Commande AddResource : Liaison de BizTalk
Pour ajouter un fichier de liaison à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : biztalkbinding** pour le **Type** paramètre. Lorsque vous ajoutez un fichier de liaison, vous pouvez indiquer un environnement de déploiement en particulier. Lorsque vous importerez ensuite l'application, vous pourrez sélectionner cet environnement de déploiement pour y appliquer les liaisons. Vous pouvez ajouter à une application BizTalk autant de fichiers de liaison que vous le souhaitez et définir un environnement de déploiement différent pour chacun. Pour ajouter plusieurs fichiers de liaison, exécutez la commande AddResource sur chaque fichier à ajouter.  
  
 Vous pouvez ajouter un fichier de liaison que vous avez exporté pour un assembly, une application ou un groupe, comme décrit dans [commande ExportBindings](../core/exportbindings-command.md), puis utilisez la commande AddResource pour ajouter le fichier de liaison à une application.  
  
 L'exécution de cette commande entraîne l'ajout du fichier de liaison à la base de données de gestion BizTalk ainsi que l'affichage du fichier dans le dossier Ressources de l'application. En outre, le fichier apparaît lorsque vous utilisez la [commande ListApp](../core/listapp-command.md). Contrairement à l'importation d'un fichier de liaison, l'ajout d'un tel fichier ne modifie pas immédiatement les liaisons existantes. Les liaisons ne sont pas appliquées tant que l'application n'a pas été importée dans un autre groupe BizTalk.  
  
 Lorsque vous ajoutez un fichier de liaison, vous pouvez spécifier son environnement de déploiement à l'aide du paramètre facultatif de la propriété « TargetEnvironment ». La valeur de ce paramètre peut être une chaîne qui représente l'environnement de déploiement dans lequel vous voulez appliquer les liaisons du fichier : « test » ou « production » par exemple. Si vous ne spécifiez pas une valeur pour le paramètre de cette propriété, la valeur  **\<par défaut\>**  est automatiquement spécifiée, et ce fichier de liaison est appliqué à chaque fois que l’application est importée.  
  
 Lorsque vous importez une application qui comprend un ou plusieurs fichiers de liaison ainsi ajoutés de manière explicite, vous pouvez sélectionner le ou les fichiers de liaison à appliquer en spécifiant la valeur du paramètre de propriété. Les liaisons sont appliquées lors de l'importation de l'application.  
  
 À mesure que des liaisons sont appliquées au cours du processus d'importation, les liaisons déjà appliquées sont remplacées par de nouvelles liaisons qui portent le même nom. Autrement dit, la liaison d'un nom donné la plus récente est celle qui est effectivement appliquée. Ayez cela à l'esprit lorsque vous utilisez plusieurs fichiers de liaison. Si les fichiers de liaison contiennent des entrées en double, la liaison prise en compte est celle qui a été appliquée en dernier. Lorsque vous importez une application, les liaisons sont appliquées dans l'ordre suivant :  
  
1.  Liaisons d'application générées par BizTalk Server, n'ayant pas été explicitement ajoutées à l'application au moyen d'un fichier de liaison, mais ayant été sélectionnées par l'utilisateur pour leur exportation dans le fichier .msi de l'application.  
  
2.  Fichiers de liaison ajoutés de manière explicite mais pour lesquels aucun environnement de déploiement cible n'a été défini. À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.  
  
3.  Liaisons ajoutées de manière explicite auxquelles est associé un environnement de déploiement cible correspondant à l'environnement de déploiement sélectionné pour l'importation de l'application. À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.  
  
 Pour plus d’informations, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Pour des informations générales sur l’utilisation de fichiers de liaison, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [**« ApplicationName » : «***valeur***»**] **/Type:System.BizTalk:BizTalkBinding/Property : TargetEnvironment = «***valeur***»** [**/overwrite**] **/Source :***valeur* [**/Server :***valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk à laquelle ajouter le fichier de liaison. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut.|  
|**/ Type** (ou **/T**, consultez la section Notes)|Oui|**System.BizTalk : biztalkbinding** (cette valeur ne respecte pas la casse).|  
|**/ Source** (ou **/So**, consultez la section Notes)|Oui|Chemin d'accès complet du fichier de liaison, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
|**/Property:TargetEnvironment =** (ou **/P:TargetEnvironment =**, consultez la section Notes)|Non|Chaîne indiquant l'environnement de déploiement cible. Vous pouvez la chaîne de votre choix (ex. : Production). Exemple : **/Property:TargetEnvironment = « Production »**<br /><br /> Si non spécifié, la valeur  **\<par défaut\>**  est appliqué automatiquement. La valeur respecte la casse. Si elle comprend des espaces, vous devez la placer entre guillemets doubles ("). La longueur maximale de cette valeur ne doit pas dépasser 128 caractères.|  
|**/ Remplacer** (ou **/Ov**, consultez la section Notes)|Non|Option permettant de mettre à jour un fichier de liaison existant. Si cette option n'est pas spécifiée et qu'un fichier de liaison, dont le nom est le même que celui du fichier à ajouter, existe déjà dans l'application, l'opération AddResource échoue.|  
|**/ Serveur** (ou **/Se**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si n’est fourni, la base de données de gestion BizTalk en cours d’exécution dans l’instance locale de SQL Server est utilisé.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:BizTalkBinding /Property:TargetEnvironment = / de Test source : « C:\Binding Files\MyBinding.xml » /Server:MyDatabaseServer Server**  
  
## <a name="remarks"></a>Notes  
 Les noms de propriété respectent la casse. Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter un fichier de liaison à une application](../core/how-to-add-a-binding-file-to-an-application2.md)