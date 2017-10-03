---
title: Commande ImportBindings | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b8dd1ee-1719-4cd1-b503-b004f312daeb
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 576f9055e7b70ab43cc150f208f8c55789f28da8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importbindings-command"></a>Commande ImportBindings
Cette commande permet d'importer des liaisons d'un fichier de liaison XML dans une application ou un groupe BizTalk. Les liaisons peuvent avoir été exportées à partir d’un assembly, une application ou un groupe, comme décrit dans [exportation des liaisons](../core/exporting-bindings6.md). Les paramètres ApplicationName et GroupLevel n'ont pas les mêmes effets selon l'emplacement à partir duquel les liaisons ont été exportées. Pour plus d'informations, consultez la section « Remarques » plus loin dans cette rubrique.  
  
> [!NOTE]
>  Aucune application n'est spécifiée pour les fichiers de liaison générés dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ceux-ci sont donc importés dans l'application par défaut.  
  
## <a name="usage"></a>Utilisation  
 **BTSTask ImportBindings-Source**:*valeur* [**- GroupLevel** &#124; **- ApplicationName**:*valeur*] [**-Server**:*valeur*] [**-base de données**: *valeur*] [**- ImportTrackingSettings**:*valeur*] [**- ExcludeParties**]
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**-Source** (ou **-donc**, consultez la section Notes)|Requis|Chemin d'accès complet du fichier de liaison à importer, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets (").|  
|**-GroupLevel** (ou **- G**, consultez la section Notes)|Ce paramètre est facultatif|Option permettant d'importer le fichier de liaison dans le groupe actuel. Si vous définissez cette option, ne définissez pas le paramètre « ApplicationName ».|  
|**ApplicationName -** (ou **-**, consultez la section Notes)|Ce paramètre est facultatif|Nom de l'application BizTalk où les liaisons doivent être importées. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). L'application doit exister, faute de quoi, l'opération d'importation échoue. L'application BizTalk par défaut est utilisée si ce paramètre n'est pas spécifié. Si vous définissez ce paramètre, ne définissez pas le paramètre « GroupLevel ».|  
|**-Server** (ou **-Se**, consultez la section Notes)|Ce paramètre est facultatif|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**-De base de données** (ou **-D**, consultez la section Notes)|Ce paramètre est facultatif|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
| **-ImportTrackingSettings** | Ce paramètre est facultatif | Nouveau commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. <br /><br />Cette option d’importation des paramètres de suivi global est ignoré. Une valeur « true » permet l’importation des paramètres de suivi. False n’autorise pas l’importation des paramètres de suivi. |
| **-ExcludeParties** | Ce paramètre est facultatif | Nouveau commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. <br /><br />Si spécifié, il exclut les informations de tiers à partir du fichier de liaison. |
  
## <a name="sample"></a>Exemple  
 La commande suivante permet d'importer des liaisons dans l'application appelée MyApplication du groupe BizTalk par défaut.  
  
`BTSTask ImportBindings -ApplicationName:MyApplication -Source:C:\Bindings\Binding1.xml`
  
 La commande suivante permet d'importer des liaisons dans le groupe défini dans la base de données de gestion BizTalk qui s'exécute sur une instance de SQL Server appelée MY_Server.  
  
 `BTSTask ImportBindings -GroupLevel -Server:MY_Server -Database:BiztalkMgmtDb -Source:C:\Bindings\Binding1.xml`
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
 Ces liaisons peuvent avoir été exportées depuis un assembly, une application ou un groupe. Les paramètres ApplicationName et GroupLevel n'ont pas les mêmes effets selon l'emplacement à partir duquel les liaisons ont été exportées. Le tableau suivant récapitule ces différents effets.  
  
|Origine des liaisons|Effet avec le paramètre ApplicationName|Effet avec le paramètre GroupLevel|  
|----------------------------|-----------------------------------------------|------------------------------------------|  
|Liaisons exportées à partir d'un assembly|L'application spécifiée pour le paramètre ApplicationName doit contenir un assembly portant le même nom que l'assembly à partir duquel le fichier de liaison a été exporté, faute de quoi, l'opération d'importation échoue.|Le groupe actuel doit contenir un assembly et une application portant le même nom que l'assembly et l'application à partir desquels le fichier de liaison a été exporté, faute de quoi, l'importation échoue.|  
|Liaisons exportées à partir d'une application|L'application à partir de laquelle le fichier de liaison a été exporté doit porter le même nom que l'application indiquée par le paramètre ApplicationName, faute de quoi, l'opération d'importation échoue.|L'application à partir de laquelle le fichier de liaison a été exporté doit porter le même nom qu'une application du groupe dans lequel les liaisons sont importées, faute de quoi, l'opération d'importation échoue.|  
|Liaisons exportées à partir d'un groupe|Le groupe à partir duquel le fichier de liaison a été exporté doit inclure une application portant le même nom que l'application indiquée par le paramètre ApplicationName, faute de quoi, l'opération d'importation échoue.|L'importation de liaisons se fait en fonction de correspondances. Autrement dit, les liaisons d'une application faisant partie du groupe à partir duquel les liaisons ont été exportées sont importées dans une application portant le même nom que le groupe actuel.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
 [Comment importer des liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md)   
 [Comment importer des liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md)