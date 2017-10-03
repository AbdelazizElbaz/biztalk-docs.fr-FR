---
title: Commande ImportSettings | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 587f7e1f-9cf7-4e7b-90cd-11a266f474dc
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c609634422f8c8b5f2c1a96691fe4eda708e5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importsettings-command"></a>Commande ImportSettings
Importe les paramètres de groupe, de l'hôte ou de l'instance d'hôte BizTalk dans la base de données de configuration à partir d'un fichier XML source. Les paramètres sont mappés tels qu'ils le sont dans le fichier XML. Ces paramètres ont été exportés comme décrit dans [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) ou [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette opération, vous devez être connecté en tant que membre du groupe Administrateurs de BizTalk Server.  
  
## <a name="usage"></a>Utilisation  
 `ImportSettings –Source:value –Map: value [-Server:value] [-Database:value]`  
  
## <a name="parameters"></a>Paramètres  
  
|**Paramètre**|Requis|Valeur|  
|-------------------|--------------|-----------|  
|**-Source**|Oui|Nom et chemin d'accès au fichier XML contenant les paramètres exportés.|  
|**-Map**|Oui|Nom et chemin d'accès au fichier XML de mappage.|  
|**-Serveur**|Ce paramètre est facultatif|Nom de l'ordinateur SQL Server hébergeant la base de données de configuration BizTalk.|  
|**-Base de données**|Ce paramètre est facultatif|Nom de la base de données de configuration BizTalk.|  
  
## <a name="sample"></a>Exemple  
 `BTSTask ImportSettings /Source:”C:\My Folder>\ExportedSettings.xml” /Map:Mappings.xml /Server:MyServer /Database:MyMgmtDb`  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)