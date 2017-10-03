---
title: La commande ListPackage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be09b76b-429b-4639-89f0-1eadb0c851ce
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88fca4820dba7c04908e2b756fda0d1d25794a10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="listpackage-command"></a>Commande ListPackage
Cette commande permet d'afficher sous forme de liste les artefacts contenus dans un fichier .msi généré par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="usage"></a>Utilisation  
 **BTSTask ListPackage** [**/Package :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis| Description|  
|---------------|--------------|-----------------|  
|**/ Package** ou **/P**|Oui|Nom et chemin d'accès du fichier .msi. Exemple : C:\MSI\MyApplication.msi. Si le chemin d’accès comprend des espaces, il doit être encadré par des guillemets doubles («).|  
  
## <a name="sample"></a>Exemple  
 **ListPackage /Package : « Files\MyApplication.msi MSI C:\My »**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)