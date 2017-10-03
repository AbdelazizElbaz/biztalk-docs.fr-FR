---
title: Commande ExportBindings | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6573142e-7ca7-4990-98e3-b7a54840da13
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f12e28b68698aeb42aefa387c94bd76470ecaf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exportbindings-command"></a>Commande ExportBindings
Cette commande permet d'exporter des liaisons pour un assembly, une application ou un groupe BizTalk. Vous pouvez également exporter les liaisons du tiers global en même temps que les liaisons d'assembly, d'application ou de groupe. Remarque : un tiers correspond à toutes les entités (les partenaires de votre organisation, par exemple) qui interagissent avec une orchestration.  
  
## <a name="usage"></a>Utilisation  
 **Facultatif /Destination de BTSTask ExportBindings :** *valeur* [**paramètre « GroupLevel »**] [**« ApplicationName » :***valeur*] [**/AssemblyName :***valeur* ] &#124; [**/GlobalParties**] [**/Server :***valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ Destination** (ou **/De**, consultez la section Notes)|Oui|Chemin d'accès complet du fichier de liaison à créer, nom du fichier inclus. Si un fichier de liaison doté du même chemin d'accès existe déjà, il est remplacé. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
|**/ GroupLevel** (ou **/GR**, consultez la section Notes)|Non|Lorsque ce paramètre est défini, toutes les liaisons du groupe en cours d'utilisation sont exportées. Vous pouvez spécifier un seul de ces trois paramètres : GroupLevel, ApplicationName ou AssemblyName.|  
|**/ ApplicationName** (ou **/Ap**, consultez la section Notes)|Non|Nom de l'application à partir de laquelle exporter les liaisons. L'application doit exister. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Pour vérifier le nom de l’application, vous pouvez utiliser la **ListApps** de commande, comme décrit dans [commande ListApps](../core/listapps-command.md). L'application BizTalk par défaut est utilisée si ce paramètre n'est pas spécifié. Vous pouvez spécifier un seul de ces trois paramètres : GroupLevel, ApplicationName ou AssemblyName.|  
|**/ AssemblyName** (ou **/As**, consultez la section Notes)|Non|Identificateur unique local (LUID) de l'assembly à partir duquel les liaisons sont exportées. Vous pouvez afficher la liste des LUID pour les artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md). Vous pouvez spécifier un seul de ces trois paramètres : GroupLevel, ApplicationName ou AssemblyName.|  
|**/ GlobalParties** (ou **/Gl**, consultez la section Notes)|Non|Une fois défini, ce paramètre permet d'exporter les informations de tiers global pour le groupe.|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="sample"></a>Exemple  
 **Facultatif /Destination de BTSTask ExportBindings : « C:\Binding Files\MyBindings.xml » GroupLevel /Server:MyDatabaseServer Server**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
 [L’exportation des liaisons](../core/exporting-bindings6.md)