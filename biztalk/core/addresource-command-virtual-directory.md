---
title: "Commande AddResource : Répertoire virtuel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 446be3b3-31da-4f03-81b5-3a75c8da6558
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f28605a4bac678cefaafcb853d3dcdc55994831
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-virtual-directory"></a>Commande AddResource : Répertoire virtuel
Pour ajouter un répertoire virtuel pour un site Web ou des services Web à une application BizTalk, vous utilisez la **AddResource** de commandes et spécifiez **System.BizTalk : WebDirectory** pour le paramètre de Type. L'exécution de cette commande permet d'ajouter le répertoire virtuel à la base de données de gestion BizTalk. Ce répertoire virtuel s'affiche également dans la console Administration de BizTalk Server, dans le dossier Ressources de l'application à laquelle vous l'avez ajouté. En outre, le répertoire virtuel est répertorié, lorsque vous utilisez la [commande ListApp](../core/listapp-command.md).  
  
> [!IMPORTANT]
>  Lorsque vous ajoutez un répertoire virtuel dont l'URL contient « https », préférez l'utilisation de « http » à celle de « https » dans l'URL que vous spécifiez. Si vous utilisez « https », l'opération consistant à ajouter un répertoire virtuel échoue. Bien que vous ajoutiez le répertoire en utilisant « http » dans l'URL, le paramètre « https » correspondant à l'URL dans la métabase des services Internet est activé, de sorte que le répertoire virtuel fonctionne correctement.  
  
> [!NOTE]
>  Si vous ajoutez un répertoire virtuel depuis une version 64 bits du service Web et essayez d'installer l'application comprenant ce répertoire sur un ordinateur 32 bits, le répertoire virtuel ne sera pas installé. Il est installé uniquement sur un ordinateur 64 bits.  
  
## <a name="usage"></a>Utilisation  
 **BTSTask AddResource** [/**ApplicationName :***valeur*] **/Type:System.BizTalk:WebDirectory**[**/Overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Non|Nom de l'application BizTalk à laquelle ajouter le répertoire virtuel. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe.|  
|**/ Type** (ou **/T**, consultez la section Notes)|Oui|**System.BizTalk : WebDirectory** (cette valeur ne respecte pas la casse).|  
|**/ Remplacer** (ou **/O**, consultez la section Notes)|Non|Option permettant de mettre à jour un répertoire virtuel existant. Si cette option n'est pas spécifiée et qu'un répertoire virtuel, dont le nom est le même que celui du répertoire virtuel à ajouter, existe déjà dans l'application, l'opération AddResource échoue.|  
|**/ Source** (ou **/S**, consultez la section Notes)|Oui|URI complet du répertoire virtuel source.<br /><br /> Exemples :<br /><br /> http://MyHost:80/MyPath/MyVirtualDirectory|  
|**/ Destination** (ou **/De**, consultez la section Notes)|Non|URI à affecter au répertoire virtuel lorsque l'application est installée à partir du fichier .msi. Si ce paramètre n'est pas spécifié, la valeur utilisée est celle du paramètre Source, où l'hôte est défini sur « localhost ».|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/Da**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si n’est fourni, la base de données de gestion BizTalk en cours d’exécution dans l’instance locale de SQL Server est utilisé.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask AddResource, /ApplicationName:MyApplication/type : System.BizTalk : WebDirectory /overwrite /Source:http://Host1:90 / MyVirtualDirectory /Destination:http://Host2:90 / / Database de MyVirtualDirectory /Server:MyDatabaseServer : BizTalkMgmtDb**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Commande AddResource](../core/addresource-command.md)   
 [Comment ajouter un Assembly .NET à une Application](../core/how-to-add-a-net-assembly-to-an-application.md)