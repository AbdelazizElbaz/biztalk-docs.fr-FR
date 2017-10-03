---
title: Envoyer les erreurs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cf61c82-ad48-4555-af53-fb841fd0f503
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67741af0520d990be9a552685c8319aa6a5ae881
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-errors"></a>Erreurs en relation avec l'envoi
Informations sur le diagnostic et résolution des erreurs d’envoi WCF.  
  
## <a name="failed-to-generate-odx-file"></a>Impossible de générer le fichier ODX

||Détails de l’erreur|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible de générer le fichier ODX|  
  
### <a name="explanation"></a>Explication  
 Cette erreur indique qu'une erreur s'est produite lors de l'utilisation du service.  
  
### <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que le service WCF possède une méthode Web valide et que des métadonnées sont hébergées (si vous en êtes le propriétaire). Sinon, contactez le fournisseur de services.  
  
 Pour plus d’informations sur l’utilisation des services WCF, consultez [Considérations lors de la consommation de Services WCF avec les adaptateurs d’envoi WCF](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md).
 
## <a name="response-message-body-was-not-read"></a>Impossible de lire le corps du message de réponse
  
||Détails de l’erreur|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible de lire le corps du message de réponse. (Ceci peut indiquer que la connexion a été fermée.)|  
  
### <a name="explanation"></a>Explication  
 Le client a peut-être été déconnecté avant l'envoi du message de réponse.  
  
### <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez la connectivité client. La procédure à suivre et les suites de l'action dépendent du type de port.   
Pour plus d’informations, consultez [outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md).