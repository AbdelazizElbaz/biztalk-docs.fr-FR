---
title: Les Packages DTS BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DTS packages, BAM
- BAM, DTS packages
ms.assetid: bba70d81-6ddf-4f1f-a1f7-d5a5bf453bae
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 105d1b42848b73505d9a82df07693111708ce802
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-dts-packages"></a>Lots DTS BAM
Un administrateur peut mettre à jour les paramètres des lots DTS BAM suivants :  
  
-   Le **CubeUpdate** package de Services DTS (Data Transformation) se trouve toujours sur le même serveur que la base de données de schémas en étoile.  
  
-   Le **DataMaintenance** de package DTS est toujours situé sur le même serveur que la base de données d’importation principale.  
  
 Les lots DTS utilisent les paramètres suivants dans le fichier BAMConfiguration.xml.  
  
|Paramètre| Description|  
|---------------|-----------------|  
|ConnectionTimeOut|La valeur du délai avant expiration (en secondes) de la connexion DTS est un entier. Si ce paramètre est omis, le fichier de configuration se base sur 60 secondes, qui est la valeur par défaut.|  
|Chiffrement|Par défaut, les lots DTS ne chiffrent pas les données pendant qu'ils les transforment (la valeur d'Encryption est 0). Définissez Encryption sur 1 pour chiffrer les données pendant la transformation.|  
|OwnerPassword|Le mot de passe du propriétaire de lot DTS. Les propriétaires de lots DTS peuvent les ouvrir et les modifier. Pour plus d'informations sur les propriétaires de lots DTS, consultez documentation en ligne de SQL Server.|  
|UserPassword|Le mot de passe de l'utilisateur DTS. Les utilisateurs de lots DTS peuvent exécuter des lots DTS. Pour plus d'informations sur les utilisateurs de lots DTS, consultez documentation en ligne de SQL Server.|  
  
 Dans le fichier BAMConfiguration.xml, les lots DTS font appel aux conventions d'attribution de noms suivantes :  
  
-   **CubeUpdate** de package DTS  
  
     **bam_AN_\<**   
     ***Nom du cube* >**, où NomCube est le nom du cube. Le classeur BAM génère le nom de cube à partir du nom de la vue. Si vous modifiez le nom du cube dans le document XML de configuration BAM, le nouveau nom en résultant est utilisé dans le nom du lot DTS.  
  
-   **DataMaintenance** de package DTS  
  
     **bam_DM_\<**   
     ***ActivityName* >**, où Nomactivité est le nom de l’activité.  
  
 Pour regrouper l'agrégation planifiée, vous devez exécuter le lot DTS CubeUpdate. Dans la section suivante, vous pouvez spécifier la fenêtre de temps destinée à l'agrégation en temps réel.  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma de Configuration BAM](../core/bam-configuration-schema.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [La gestion BAM](../core/managing-bam.md)