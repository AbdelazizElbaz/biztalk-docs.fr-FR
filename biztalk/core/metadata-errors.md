---
title: "Erreurs dans les métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccb60c91-5905-4852-813b-586b82de4825
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dce5fc9eb944eccbeed57073c2546f81825ec6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-errors"></a>Erreurs en relation avec les métadonnées
Informations sur le diagnostic et résolution des erreurs dans les métadonnées de WCF.  
  
## <a name="error-consuming-wcf-service-metadata"></a>Erreur de consommation des métadonnées de service WCF

||Détails de l’erreur|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Erreur de consommation des métadonnées de service WCF|  
  
### <a name="explanation"></a>Explication  
 Cette erreur indique que les métadonnées du service ne sont pas disponibles ou sont non valides.  
  
### <a name="user-action"></a>Action de l'utilisateur  
 Corrigez les métadonnées du service WCF et tentez de l'utiliser (si vous en êtes le propriétaire). Accédez à l’éditeur de Configuration de Service (**svcConfigEditor.exe**) et apporter des modifications au fichier de configuration.  Sinon, contactez le fournisseur de services

## <a name="failed-to-get-metadata"></a>Échec de l'obtention des métadonnées

||Détails de l’erreur|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Échec de l'obtention des métadonnées à partir de « {0} »|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que les métadonnées ne sont pas disponibles pour ce service.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Activez les métadonnées pour le service, puis réexécutez l'Assistant Consommation (si vous êtes propriétaire du service WCF que vous tentez d'utiliser). Sinon, contactez le fournisseur de services.