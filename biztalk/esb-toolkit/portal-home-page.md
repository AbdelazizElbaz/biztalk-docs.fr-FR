---
title: "Page d’accueil du portail | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60072c30-d57b-4bd8-a7ee-b4d0fa50de58
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c2c525fdc8e5786143e8b4f942f0f2379226d3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="portal-home-page"></a>Page d'accueil du portail
La figure 1 montre la page d’accueil, qui contient quatre sections :  
  
-   Le **graphiques** section contient une répartition des erreurs par application, par type et une analyse au fil du temps, qui indique l’intégrité globale de l’entreprise à partir d’une perspective d’application.  
  
-   Le **Registre** section contient une liste de demandes récentes pour la publication de point de terminaison service envoyées au service Universal Description, Discovery and Integration (UDDI).  
  
-   Le **l’historique des alertes** section affiche la liste des alertes reçues par le service d’alertes.  
  
-   Le **erreurs** section affiche une liste abrégée des erreurs plus récent généré par le mécanisme d’ESB Échec de l’Orchestration Exception routage et le mécanisme de routage des messages a échoué BizTalk. La liste affiche les erreurs regroupés par application et affiche le niveau de gravité, nom du service, type d’erreur et les date et heure pour chaque erreur dans la liste.  
  
 ![Page d’accueil du portail](../esb-toolkit/media/portalhomepage.gif "PortalHomePage")  
  
 **Figure 1**  
  
 **La page d’accueil du portail de gestion ESB**  
  
 La liste suivante explique comment vous pouvez utiliser les fonctionnalités de la page d’accueil du portail de gestion ESB.  
  
-   Lorsque vous chargez tout d’abord la page d’accueil, vous ne pouvez pas voir toutes les applications dans le premier graphique. Pour sélectionner les applications pour lesquelles vous souhaitez afficher plus d’informations, cliquez sur le **sélectionner des Applications** ci-dessus le premier graphique, puis activez ou désactivez les cases à cocher dans la liste des applications BizTalk installées qui s’affiche. Vous pouvez également utiliser les liens qui s’affichent pour sélectionner la totalité ou aucun des applications. Cliquez sur **enregistrer** pour afficher les informations pour les applications sélectionnées, ou cliquez sur **Annuler** pour abandonner vos modifications. Vous pouvez modifier la liste par défaut des applications sur le [Page Paramètres de portail](../esb-toolkit/portal-my-settings-page.md).  
  
-   Pour modifier la période pour laquelle le portail affiche des informations, modifiez le paramètre dans la liste déroulante au-dessus du premier graphique. Vous pouvez choisir d’afficher des informations pour les précédents **heure, jour, semaine,** ou **mois**. Vous pouvez modifier la période par défaut sur le [Page Paramètres de portail](../esb-toolkit/portal-my-settings-page.md).  
  
-   Pour activer ou désactiver la publication automatique des entrées d’UDDI, cliquez sur le **modification** lien en haut de la **Registre** section de la page. Cette opération ouvre le [Page Paramètres du Registre](../esb-toolkit/registry-settings-page.md), où vous spécifiez les éléments suivants :  
  
    -   Détails du serveur UDDI le portail utilisera, y compris l’URI du serveur, indique si la publication automatique est activée et si l’accès anonyme est activé.  
  
    -   Notification par courrier électronique des publications de UDDI sont activé ou non et les paramètres à utiliser pour le serveur de messagerie, adresses de messagerie, objet du message et le corps du message.  
  
    -   Votre contact nom et adresse électronique pour les entrées publiées.  
  
-   Pour afficher une liste de demandes de Registre UDDI en attente, cliquez sur le lien en haut de la **Registre** section de la page qui affiche le nombre de demandes en attente. Cette opération ouvre le [Page Gestion des demandes en attente](../esb-toolkit/manage-pending-requests-page.md), qui contient les éléments suivants :  
  
    -   **Une liste de demandes d’inscription en attente**. Pour chacune d’elles, vous pouvez cliquer sur les icônes à droite de la demande pour afficher les détails, approuver la demande ou refuser la demande. Lors de l’affichage de la demande, vous consultez les détails du Registre, les détails du service de Registre (que vous pouvez le modifier) et détails du contact.  
  
    -   **Un lien pour afficher un historique des demandes sous forme de liste**. Cette liste affiche une plage de valeurs à partir de chaque demande d’inscription.  
  
-   Pour modifier l’ordre de tri des erreurs répertoriées dans le **erreurs** section de la page, cliquez sur le **Date** ou **gravité** case d’option située au-dessus de la liste d’erreurs.  
  
-   Le portail affiche les erreurs dans le **erreurs** section de la page groupées par application BizTalk. Pour afficher les erreurs pour une application spécifique, cliquez sur le lien qui est le nom de l’application au-dessus du groupe applique des erreurs.  
  
-   Pour afficher les détails d’une erreur spécifique, cliquez n’importe où dans la ligne contenant cette erreur dans le **erreurs** section de la page. Cette opération ouvre le [Afficheur des messages d’erreur portail](../esb-toolkit/portal-fault-message-viewer.md) pour l’erreur sélectionnée.