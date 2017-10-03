---
title: "Gérer les Scripts de pré-traitement et post-traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 107ada12-fef2-4b56-8ff8-228c13761104
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18926a0c51e5ab5f65b32373d20b2931ccaa627d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-pre--and-post-processing-scripts"></a>Gérer les Scripts de pré-traitement et post-traitement

## <a name="overview"></a>Vue d'ensemble
Cette section fournit des instructions sur l'utilisation de la console Administration de BizTalk ou de l'outil de ligne de commande BTSTask pour la gestion les scripts de prétraitement et de post-traitement. Vous pouvez créer un script à exécuter lors de l'importation, l'installation ou la désinstallation (suppression) d'une application BizTalk, puis ajouter le script à l'application. Lorsque vous ajoutez un script, vous pouvez spécifier s'il s'agit d'un script de prétraitement qui s'exécute avant l'importation, l'installation ou la désinstallation d'une application, ou un script de post-traitement qui s'exécute après l'importation, l'installation ou la désinstallation d'une application.  
  
 Si vous sélectionnez le script lors de l'exportation de l'application, le script est inclus dans le fichier .msi de l'application. Lorsque vous installez, désinstallez ou importez l'application, le script s'exécute automatiquement, en fonction de la manière dont vous l'avez écrit. Pour plus d’informations sur la création et à l’aide de scripts, consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Ajouter un Script de pré-traitement ou de post-traitement à une Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [Modifier l’emplacement de Destination d’un Script de pré-traitement ou post-traitement](../core/how-to-change-the-destination-location-of-a-pre-or-post-processing-script.md)  
  
-   [Supprimer un Script de pré-traitement ou de post-traitement d’une Application](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md)