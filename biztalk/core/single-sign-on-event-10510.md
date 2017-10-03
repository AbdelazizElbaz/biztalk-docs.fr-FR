---
title: "Single Sign-On : Événement 10510 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4553ad4c-9553-4b8b-b3a3-72aed2a61202
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 053f75541597e3b2e721c53714aaaf8517c3c49f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10510"></a>Single Sign-On : Événement 10510
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10510|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_INFO_DLL_LOAD_FAILED|  
|Texte du message|Échec du chargement de %1. Vérifiez que ce fichier est disponible.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'informations indique que le service d'authentification unique n'a pas pu charger le fichier DLL.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet événement, effectuez une ou plusieurs des opérations suivantes :  
  
-   Vérifiez le fichier DLL situé dans le répertoire d'installation de l'authentification unique (généralement, C:\Program Files\Common Files\Enterprise Single Sign-On). Il se peut que votre répertoire d'installation de l'authentification unique soit différent.  
  
-   Si le fichier DLL est manquant ou endommagé, remplacez-le, puis redémarrez le service.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)