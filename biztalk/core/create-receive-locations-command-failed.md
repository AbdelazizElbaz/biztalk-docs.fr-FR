---
title: "Créer échouée de la commande emplacements de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f73ff211-af7f-40be-ad7e-7bde7bf75a2d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a6ad1c7992bb696eb05223e9830a7114d8a0fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-receive-locations-command-failed"></a>Échec de la commande de création d'emplacements de réception
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Créer échouée de la commande emplacements de réception : nom de fichier = {0} Arguments = \ {1\\} ExitCode = \ {2\}|  
  
## <a name="explanation"></a>Explication  
 L'Assistant Publication n'a pas pu créer un emplacement de réception.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit : dans la console Administration de BizTalk, assurez-vous que l’emplacement de réception spécifié par l’attribut receiveLocationName dans le fichier Web.config que l’Assistant de publication WCF BizTalk a généré existe et qu’il est démarré.  
  
 Pour plus d'informations sur la création des emplacements de réception, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Publication des Services WCF avec WCF isolé des adaptateurs de réception](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [Pour configurer les emplacement de réception WCF-BasicHttp](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [Pour configurer les emplacement de réception WCF-WSHttp](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [Pour configurer les emplacement de réception WCF-CustomIsolated](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)