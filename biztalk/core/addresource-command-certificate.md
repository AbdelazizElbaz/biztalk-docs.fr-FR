---
title: "Commande AddResource : Certificat de | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e915043-6634-4644-8d69-376d762c7cec
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fc2f1ca82dcd7a91f3572a4db96e9fc75f62839
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-certificate"></a>Commande AddResource : certificat
Pour ajouter un certificat de sécurité à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : Certificate** pour le paramètre de Type. Pour que cette commande puisse fonctionner, le certificat doit être présent dans le magasin de certificats Autres personnes de l'ordinateur local.  
  
 Cette commande permet d'ajouter le certificat à la base de données de gestion BizTalk. Ce certificat s'affiche également dans la console Administration de BizTalk Server, dans le dossier Ressources de l'application pour laquelle vous l'avez ajouté. En outre, le certificat est répertorié, lorsque vous utilisez la [commande ListApp](../core/listapp-command.md).  
  
 Lorsque vous installez l'application, le certificat est importé dans le magasin de certificats Autres personnes de l'ordinateur local.  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [**« ApplicationName » :***valeur*] **ApplicationName** [**/Overwrite**] **/Overwrite/Thumbprint : «***valeur***»** [**/Server :***valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk pour laquelle ajouter le certificat. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe.|  
|**/ Type** (ou **/Ty**, consultez la section Notes)|Oui|**System.BizTalk : Certificate** (cette valeur ne respecte pas la casse).|  
|**/ Remplacer** (ou **/O**, consultez la section Notes)|Non|Option permettant de mettre à jour un certificat existant. Si cette option n'est pas spécifiée et qu'un certificat, dont l'empreinte est la même que celle du certificat à ajouter, existe déjà dans l'application, l'opération d'ajout échoue. Vous pouvez afficher la propriété Empreinte en double-cliquant sur le certificat dans le composant logiciel enfichable Certificats et en cliquant sur l'onglet Détails. Pour plus d'informations, consultez la rubrique relative à l'affichage des informations sur les certificats dans la documentation du composant logiciel enfichable Certificats.|  
|**/ Empreinte numérique** (ou **/Th**, consultez la section Notes)|Oui|Propriété de l’empreinte numérique du certificat (une *l’empreinte numérique* est un résumé des données). Cette valeur doit être entourée de guillemets doubles (").|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/D**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si n’est fourni, la base de données de gestion BizTalk en cours d’exécution dans l’instance locale de SQL Server est utilisé.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource /ApplicationName:MyApplication/type : System.BizTalk : Certificate /overwrite/Thumbprint remplacer : "04 a2 8e 32 24 f9 36 b9 42 81 12 71 3 a d2 ef db c7 9c 83 dc « /Server:MyDatabaseServer Server**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter un certificat à une Application](../core/how-to-add-a-certificate-to-an-application.md)