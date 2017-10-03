---
title: "Comment les Variables d’environnement indiquent état du déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: scripts, variables
ms.assetid: 022b782b-008d-41a7-9880-d1c4e5e4015e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 041e77eadb7c1b62e3441ee3b3c138203299f3a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-environment-variables-indicate-deployment-state"></a>Indication de l'état du déploiement par les variables d'environnement
Une fois appelé, un script de pré-traitement ou de post-traitement détermine l'état du déploiement dans lequel il est exécuté (installation, importation, suppression, désinstallation, annulation de l'importation ou de l'installation) en vérifiant les variables d'environnement BTAD_ChangeRequestAction, BTAD_InstallMode et BTAD_HostClass.  
  
 Le tableau suivant décrit les combinaisons des trois variables qui indiquent des états de déploiement différents.  
  
|État du déploiement|Valeurs attendues|  
|----------------------|---------------------|  
||BTAD_ChangeRequestAction|BTAD_InstallMode|BTAD_HostClass|  
|Importation sans indicateur de remplacement|Créer|Importer|ConfigurationDb|  
|Importation avec indicateur de remplacement|Update|Importer|ConfigurationDb|  
|Install|Update|Install|BizTalkHostInstance|  
|Désinstaller|DELETE|Désinstaller|BizTalkHostInstance|  
|Annulation d'importation|DELETE|Importer|ConfigurationDb|  
|Annulation d'installation|DELETE|Install|BizTalkHostInstance|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement d’Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)   
 [BTAD_ChangeRequestAction](../core/btad-changerequestaction.md)   
 [BTAD_InstallMode](../core/btad-installmode.md)   
 [BTAD_HostClass](../core/btad-hostclass.md)