---
title: "Échec de l’enregistrement du récepteur isolé pour l’adresse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 313b436a-d7c5-4b46-bfe3-bbad0d8efe42
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edd55360a1638128ed687cf83f2e05bf52ad9dfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="failed-to-register-isolated-receiver-for-address"></a>Échec de l'enregistrement du récepteur isolé pour l'adresse
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Échec de l'enregistrement du récepteur isolé pour l'adresse « {0} » ; l'emplacement de réception n'existe pas ou est désactivé.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique qu'un emplacement de réception WCF isolé et publié n'a pas pu trouver l'emplacement de réception correspondant.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit : dans la console Administration de BizTalk, assurez-vous que l’emplacement de réception spécifié par l’attribut receiveLocationName dans le fichier Web.config que l’Assistant Publication Services WCF BizTalk a généré existe et qu’il est a démarré.  
  
 Pour plus d'informations sur la création des emplacements de réception, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Publication des Services WCF avec WCF isolé des adaptateurs de réception](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [Pour configurer les emplacement de réception WCF-BasicHttp](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [Pour configurer les emplacement de réception WCF-WSHttp](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [Pour configurer les emplacement de réception WCF-CustomIsolated](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)