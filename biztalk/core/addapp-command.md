---
title: Commande AddApp | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 445784f1-505b-4259-a3f4-6f0d61578b1c
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a6b91faa406181db3e4195bf57baeb086a0b69e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="addapp-command"></a>Commande AddApp
Cette commande permet de créer une application BizTalk dans la base de données de gestion BizTalk. Vous pouvez afficher l'application concernée dans le nœud Applications de la console Administration de BizTalk Server. Vous pouvez ajouter des artefacts à l’application à l’aide de la commande AddResource, comme décrit dans [commande AddResource](../core/addresource-command.md).  
  
## <a name="usage"></a>Utilisation  
 **« ApplicationName » BTSTask AddApp :** *valeur* [**/Description :***valeur*] [**/par défaut**] [**/ Serveur :***valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Oui|Nom de l’application BizTalk à ajouter. Si le nom de l’application comprend des espaces, il doit être encadré par des guillemets doubles («).|  
|**/ Par défaut** (ou **/Def**, consultez la section Notes)|Non|Lorsque ce paramètre est spécifié, la nouvelle application devient l'application par défaut pour le groupe BizTalk.|  
|**/ Description** (ou **/Des**, consultez la section Notes)|Non|Description de l'application. Elle doit être placée entre guillemets doubles (").|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="sample"></a>Exemple  
 **AddApp MonApplication / Description : « Mon application BizTalk »**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
 [Comment créer une Application](../core/how-to-create-an-application.md)