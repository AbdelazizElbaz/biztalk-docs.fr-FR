---
title: Page Rapports du portail | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51d793cc-dcea-4c29-883b-a5045d39d4f6
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14e9f6491c403f5386f47587c5420c3748e18a24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="portal-reports-page"></a>Page Rapports du portail
La page de rapports du portail, illustrée dans la Figure 1, affiche les graphiques suivants :  
  
-   **Nombre de pannes par Application**. Cette option affiche une vue agrégée de toutes les erreurs générées pour un ensemble spécifié d’applications sur une période spécifiée.  
  
-   **Nombre de pannes par Type d’erreur**. Cette option affiche une vue agrégée de toutes les erreurs par type d’erreur spécifié généré pour un ensemble spécifié d’applications sur une période spécifiée.  
  
-   **Nombre de défauts par heure**. Cette option affiche le nombre d’erreurs sur une période donnée pour un ensemble d’applications spécifié. Vous pouvez sélectionner une application pour afficher un graphique de tendance indiquant le nombre d’erreurs au fil du temps pour des services spécifiques au sein de l’application.  
  
-   **Nombre d’alertes par Application**. Cette option affiche une vue agrégée de toutes les alertes générées pour un ensemble spécifié d’applications sur une période spécifiée.  
  
-   **Nouvelles soumissions au fil du temps**. Cette option affiche le nombre de nouvelles soumissions de message ayant échoué sur une période donnée pour un ensemble d’applications spécifié.  
  
-   **Au fil du temps, les abonnements d’alerte**. Cette option affiche le nombre d’abonnements aux alertes sur une période donnée pour un ensemble d’applications spécifié.  
  
 ![Page Rapports du portail](../esb-toolkit/media/portalreportspage.gif "PortalReportsPage")  
  
 **Figure 1**  
  
 **La page Rapports de portail de gestion ESB**  
  
 La liste suivante explique comment vous pouvez utiliser les fonctionnalités de la page de gestion ESB portail nouvelle entrée de Registre :  
  
-   Cliquez sur le **SelectApplications** ci-dessus le premier graphique, puis activez ou désactivez les cases à cocher dans la liste des applications installées de Microsoft BizTalk Server qui s’affiche. Vous pouvez également utiliser les liens qui s’affichent pour sélectionner la totalité ou aucun des applications. Cliquez sur **enregistrer** pour afficher les informations pour les applications sélectionnées, ou cliquez sur **Annuler** pour abandonner vos modifications.  
  
-   Utilisez la liste déroulante ci-dessus le premier graphique pour sélectionner l’intervalle sur laquelle vous souhaitez que les graphiques pour afficher les données. Vous pouvez choisir d’inclure des données pour les précédents **heure, jour, semaine, mois, trimestre, année,** ou **tous les**.  
  
-   Cliquez sur un des graphiques dans la page pour afficher une répartition des données par le service dans l’application. Selon le graphique que vous sélectionnez, cela indique une ligne de nombre ou de tendance pour l’erreurs individuelles, les alertes, les types d’erreurs, les nouvelles soumissions ou les abonnements aux alertes pour chaque service.  
  
-   Cliquez sur le nom d’un service dans ce graphique pour afficher une table répertoriant toutes les erreurs, alertes, les types d’erreurs, nouvelles soumissions ou des abonnements aux alertes pour le service sélectionné.  
  
-   Cliquez sur **exporter vers Excel** pour télécharger la liste des abonnements dans un format que vous pouvez afficher dans Microsoft Excel.