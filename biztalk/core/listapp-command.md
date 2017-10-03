---
title: Commande ListApp | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5329dd55-4ce7-46d2-8983-90ac33725055
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 868e1606ae994a39fb8b558cdf2f282be12e5ad4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="listapp-command"></a>Commande ListApp
Cette commande permet d'imprimer sur la console une liste de tous les artefacts de ressource possibles pour une application BizTalk, ainsi que leurs identificateurs uniques locaux (LUID) et leur type. Un artefact est une ressource que vous pouvez ajouter à une application BizTalk à l’aide de la [commande AddResource](../core/addresource-command.md), comme un assembly, un script, un fichier, une stratégie, un composant COM, un répertoire virtuel, un artefact BAM ou un certificat. Ces artefacts de ressource s'affichent également sous le nœud Ressources de la console Administration de BizTalk Server.  
  
 Lorsque vous définissez le paramètre ResourceSpec de la commande ListApp, l'information entrée est écrite dans un fichier .xml. Vous pouvez utiliser ce fichier .xml avec le **ExportApp** commande pour exporter un sous-ensemble d’artefacts dans une application vers un fichier .msi, comme décrit dans [commande ExportApp](../core/exportapp-command.md).  
  
 Pour les répertoires virtuels, cette commande remplace le nom d’hôte de serveur Web avec « localhost ». Si vous utilisez le fichier généré par le paramètre ResourceSpec avec la commande ExportApp, vous modifiez manuellement le fichier pour remplacer « localhost » par le nom d’hôte et le numéro de port si le serveur Web se trouve sur un ordinateur distant. Si vous n'utilisez pas ce fichier, le répertoire virtuel et son contenu ne seront pas ajoutés au fichier .msi de l'application.  
  
 Exemple : http://MyWebServer:80/MyVirtualDirectory.  
  
## <a name="usage"></a>Utilisation  
 **BTSTask ListApp** [**« ApplicationName » :***valeur*] [**/resourcespec. :***valeur*] [  **/Server :***valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk pour laquelle afficher les artefacts. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).  L'application par défaut est utilisée si ce paramètre n'est pas spécifié.|  
|**/ Spécification de ressource** (ou **/R**, consultez la section Notes)|Non|Chemin d'accès complet du fichier .xml à générer à l'aide de cette commande. Ce fichier permet de dresser une liste des artefacts d'une application affichant également l'identificateur LUID et le type des artefacts. Exemple : C:\Artifacts\MyArtifacts.xml. Si le chemin d’accès comprend des espaces, il doit être placé entre guillemets doubles («). Si un fichier dont le nom et le chemin d'accès sont identiques existe déjà, il est remplacé.|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/D**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask ListApp /ApplicationName:MyApplication /ResourceSpec:C:\Artifacts\MyArtifacts.xml**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)