---
title: "Gérer les alertes (affichage d’Administration) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f8bf7d-15b7-448d-8c13-e4969b90d021
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc5472e96414fe5141de27630ebe3c810d2df28c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-alerts-administration-view"></a>Gérer les alertes (affichage d’Administration)
Figure 1 montre la page des alertes dans la vue administration, dont les administrateurs peuvent utiliser pour afficher une liste de toutes les alertes et un résumé de leur activité. Une table affiche une ligne pour chaque alerte. Chaque ligne affiche le nom de l’alerte, le nom du créateur, les statistiques générales de l’alerte (par exemple, le nombre d’activations alerte au sein de la dernière heure, jour ou mois), un nombre d’abonnés pour les alertes avec un lien pour afficher une liste et une colonne d’Actions contenant un ensemble de l’interface cli icônes ckable pour effectuer des actions sur l’alerte.  
  
 ![Page Gérer les alertes](../esb-toolkit/media/ch8-managealertspage.jpg "Ch8-ManageAlertsPage")  
  
 **Figure 1**  
  
 **La page des alertes gérer ESB Management Portal (affichage d’Administration)**  
  
 La liste suivante explique comment vous pouvez utiliser les fonctionnalités de la page du portail de gestion ESB gérer les alertes :  
  
-   Cliquez sur le **créer une alerte** lien en haut de la page pour créer une nouvelle alerte.  
  
-   Cliquez sur le **exporter vers Excel** lien pour exporter la liste des alertes en tant qu’une feuille de calcul Microsoft Excel.  
  
-   Cliquez sur le + **vue abonnés** lien dans une ligne pour afficher une liste d’abonnés à l’alerte. La liste se développe dans la ligne, et une icône de suppression s’affiche dans la colonne Actions pour chacun d’eux qui permet aux administrateurs de supprimer un abonné à partir de l’alerte. En même temps, le lien devient - **masquer les abonnés**, ce qui vous permet de réduire la liste des abonnés.  
  
-   Cliquez sur une icône dans la colonne d’Actions à effectuer une tâche pour les alertes de cette ligne. Les icônes (dans l’ordre de qu'apparition) et les tâches sont les suivantes :  
  
    -   **Afficher les détails de l’alerte.** Cette icône affiche les détails de l’alerte sélectionnée.  
  
    -   **Afficher l’historique**. Cette icône affiche un tableau qui contient toutes les activations de l’alerte sélectionnée.  
  
    -   **Ajouter un abonné**. Cette icône permet aux administrateurs d’ajouter un abonné à l’alerte sélectionnée.  
  
    -   **Modifier l’alerte**. Ce lien permet aux administrateurs de modifier les détails de l’alerte.  
  
    -   **Suppression d’alerte**. Ce lien supprime une alertes et les abonnements.