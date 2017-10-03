---
title: "Single Sign-On : Événement 10512 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edf0512-112d-40b8-9e29-7dd67f999b6d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a586af2b280e9d968b87a7cb3e7680a17457ca0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10512"></a>Single Sign-On : Événement 10512
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10512|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_LOADLIBRARY|  
|Texte du message|Impossible de charger %1%r<br /><br /> Code d’erreur : %2.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que le fichier DLL (Dynamic Link Library) n'a pas pu être chargé dans le processus de serveur SSO. L'absence du fichier DLL dans le répertoire d'installation de l'authentification unique (généralement, C:\Program Files\Common Files\Enterprise Single Sign-On) peut indiquer que le programme d'installation n'a pas été correctement exécuté ou que le fichier DLL a été supprimé après l'exécution du programme d'installation. Si le fichier DLL est présent, il se peut qu'il y ait un problème dans le cadre de la résolution du chemin d'accès correct au fichier DLL par le service d'authentification unique. Il se peut également que le fichier DLL soit lui-même endommagé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Si une défaillance du programme d'installation est suspectée, il peut être nécessaire de désinstaller, puis de réinstaller le produit.  
  
-   Si le fichier DLL est manquant ou endommagé, remplacez-le, puis redémarrez le service.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)