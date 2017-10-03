---
title: "Commande AddResource : Stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5effcbe-bf53-4741-8d5e-227620d4d84d
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9037e2277823027f1d379b8a65552b4d32ac05a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-policy"></a>Commande AddResource : stratégie
Pour ajouter une stratégie à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : Rules** pour le paramètre de Type. L'exécution de cette commande ajoute la stratégie à la base de données de gestion BizTalk. La stratégie s'affiche également dans la console Administration de BizTalk Server, dans le dossier Stratégies de l'application à laquelle vous l'avez ajoutée. En outre, la stratégie apparaît lorsque vous utilisez la [commande ListApp](../core/listapp-command.md).  
  
 Pour que cette commande fonctionne, la stratégie doit exister dans la base de données du moteur des règles. Pour obtenir des instructions sur l’importation d’une stratégie dans la base de données du moteur de règles, consultez [comment importer une stratégie](../core/how-to-import-a-policy.md). Lorsque vous ajoutez une stratégie en utilisant la commande AddResource, tous les vocabulaires utilisés par la stratégie sont automatiquement ajoutés.  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:Rules** [**/overwrite**] **/Nom :***valeur***/version :***valeur* [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk à laquelle ajouter la stratégie. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe.|  
|**/ Type** (ou **/T**, consultez la section Notes)|Oui|**System.BizTalk : Rules** (cette valeur ne respecte pas la casse).|  
|**/ Remplacer** (ou **/O**, consultez la section Notes)|Non|Option permettant de mettre à jour une stratégie. Si cette option n'est pas spécifiée et qu'une stratégie, dont le nom est le même que celui de la stratégie à ajouter, existe déjà dans l'application, l'opération AddResource échoue.|  
|**/ Nom** (ou **/N**, consultez la section Notes)|Oui|Nom de la stratégie.|  
|**Version** (ou **/V**, consultez la section Notes)|Oui|Numéro de version de la stratégie au format nombre.nombre.<br /><br /> Exemple : 1.0|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/D**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si n’est fourni, la base de données de gestion BizTalk en cours d’exécution dans l’instance locale de SQL Server est utilisé.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource, /ApplicationName:MyApplication/type : System.BizTalk : Rules /overwrite /Name:MyPolicy /Version:1.0 /Server:MyDatabaseServer Server**  
  
## <a name="remarks"></a>Notes  
 Si MyPolicy a été déployé, la commande ci-dessus retourne ce qui suit :  
  
 Erreur : Impossible d’ajouter des ressources.  
  
 Échec de validation de 1 ressource(s).  
  
 Impossible de remplacer la version 1.0 de la stratégie de règles "MyPolicy" puisqu'elle est déjà en production.  
  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter une stratégie à une Application](../core/how-to-add-a-policy-to-an-application.md)