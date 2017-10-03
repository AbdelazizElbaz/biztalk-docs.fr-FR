---
title: "Ajouter l’abonnement aux alertes et modifier des Pages d’abonnement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad5e99f1-714e-458b-b5f0-85ac69be5335
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49bed9959b51439f21d625795a69804fd41d77ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-alert-subscription-and-edit-subscription-pages"></a>Ajouter l’abonnement aux alertes et modifier des Pages d’abonnement
Les pages de l’abonnement aux alertes ajouter et modifier l’abonnement sont similaires. Ils diffèrent la page Modifier l’abonnement affiche l’ID de l’abonné (le compte Microsoft Windows de l’utilisateur du portail actuel) et possède un ensemble différent de boutons. Figure 1 montre les pages d’abonnement aux alertes ajouter et modifier un abonnement.  
  
 ![Ajouter un abonnement de modification d’alerte](../esb-toolkit/media/ch8-addalerteditsubscription.gif "Ch8-AddAlertEditSubscription")  
  
 **Figure 1**  
  
 **Les pages ESB Management Portal ajouter abonnement aux alertes et modifier un abonnement**  
  
 Les pages d’abonnement aux alertes ajouter et modifier un abonnement vous autorise à spécifier et modifier les éléments suivants :  
  
-   Une adresse de courrier électronique personnalisé à utiliser pour l’abonnement (au lieu de votre adresse de messagerie du compte Microsoft Windows)  
  
-   La période de temps lorsque vous acceptez des notifications d’alerte  
  
-   Un « noir » délai pour des événements tels que les vacances  
  
-   L’intervalle sur lequel le portail n’envoie pas d’alertes en double  
  
 Vous pouvez effectuer les opérations suivantes sur les pages d’abonnement aux alertes ajouter et modifier un abonnement :  
  
-   Sélectionnez la case à cocher à côté du **par courrier électronique personnalisé** texte si vous souhaitez utiliser une adresse de messagerie pour l’abonnement qui est différent de votre adresse de messagerie du compte Windows standard, puis tapez l’adresse de messagerie par défaut dans la zone de texte.  
  
-   Activez la case à cocher en haut de la **planification** section si vous souhaitez spécifier une période pendant laquelle le portail doit envoyer des alertes pour vous et puis spécifiez les heures de début et de fin pour la période de la **l’heure de début** et **Heure de fin** listes déroulantes. Les alertes qui se produisent en dehors de cette période sont en file d’attente et remis pendant la période spécifiée.  
  
-   Tapez la date de début et date de fin pour un **temps mort** s’il existe une période lorsque vous ne pouvez pas recevoir et d’agir sur les alertes. Utilisez le format mm/jj/aaaa pour les deux dates.  
  
-   Sélectionnez un **intervalle** dans **Minutes** pendant qui le portail de comparer les alertes déclenchées et qu’un seul envoi lorsque plusieurs instances de la même alerte se produisent. Cela empêche une erreur qui se produisent rapidement à partir de la création d’un grand nombre de messages d’alerte identiques.  
  
-   Cliquez sur le **enregistrer** bouton pour créer ou mettre à jour l’abonnement.  
  
-   Cliquez sur le **supprimer** bouton (disponible uniquement dans la page Modifier l’abonnement) pour supprimer l’abonnement sélectionné.  
  
-   Cliquez sur le **Annuler** bouton pour revenir à la [Page visionneuse alerte](../esb-toolkit/alert-viewer-page.md) sans la création ou la modification de l’abonnement.