---
title: "Single Sign-On : Événement 10727 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ff7ac94-6f1e-4e56-853e-efc50b1fa1b6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ceadb1bc742a11e05e54757b44618020c93b0d04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10727"></a>Single Sign-On : Événement 10727
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10727|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_REPLAY_RECORD_FAILED|  
|Texte du message|Échec de la relecture de la modification du mot de passe externe stocké.%r<br /><br /> Carte : %1 %r<br /><br /> Nom du fichier : %2 %r<br /><br /> Code d’erreur : %3|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique que l'authentification unique n'a pas pu relire une modification de mot de passe enregistrée dans le fichier de relecture.  
  
 Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO. Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Consultez les événements associés dans les journaux des événements système et de l'application.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)