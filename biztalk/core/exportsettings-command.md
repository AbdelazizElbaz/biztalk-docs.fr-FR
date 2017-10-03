---
title: Commande ExportSettings | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa34dab1-c854-473e-a693-43ba45624e16
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab8c39ef6903affbd2a1446bbde18a56e1a7778c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exportsettings-command"></a>Commande ExportSettings
La commande ExportSettings permet d'exporter les paramètres de BizTalk Server d'une base de données de configuration BizTalk Server vers un fichier XML. Vous pouvez ensuite importer ces paramètres dans un autre environnement comme décrit dans [comment importer à l’aide de paramètres du Panneau de configuration BizTalk](../core/how-to-import-biztalk-settings-using-settings-dashboard.md) ou [comment importer des paramètres de BizTalk à l’aide de BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
## <a name="usage"></a>Utilisation  
 `ExportSettings –Destination:value[-Server:value] [-Database:value]`  
  
## <a name="parameters"></a>Paramètres  
  
|**Paramètre**|Requis|Valeur|  
|-------------------|--------------|-----------|  
|**-Destination**|Oui|Nom et chemin d'accès au fichier XML à écrire.|  
|**-Serveur**|Ce paramètre est facultatif|Nom du serveur SQL Server hébergeant la base de données de configuration BizTalk.|  
|**-Base de données**|Ce paramètre est facultatif|Nom de la base de données de configuration BizTalk.|  
  
## <a name="sample"></a>Exemple  
 `BTSTask ExportSettings /Destination:MyFile.xml /Server:MyServer /Database:MyMgmtDb`  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)