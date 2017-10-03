---
title: "Le processus d’approbation et inscription automatique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfd3e72e-e28b-4ee3-bc4a-89ef3f64e6d5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 333e1403ffd45f80a98d3eb17f5d3aa2b63c7798
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-auto-enlist-and-approval-process"></a>Le processus d’approbation et inscription automatique
Vous pouvez configurer le portail de gestion ESB pour publier des points de terminaison de Microsoft BizTalk Server de deux manières :  
  
-   Il peut être configuré via le processus d’approbation, où un administrateur doit vérifier et approuver la demande d’inscription.  
  
-   Il peut être configuré à l’aide de publication automatique, où le portail publie automatiquement la demande dans le Registre Universal Description, Discovery and Integration (UDDI) sans nécessiter d’intervention de l’administrateur.  
  
 Vous pouvez également spécifier d’autres paramètres de fonctionnalités d’intégration d’UDDI du portail, comme décrit dans les deux procédures suivantes.  
  
### <a name="to-configure-auto-approval-and-publishing-in-the-esb-management-portal"></a>Pour configurer l’approbation automatique et la publication dans le portail de gestion ESB  
  
1.  Assurez-vous que vous vous connectez au portail à l’aide d’un compte qui est membre du groupe Administrateurs de BizTalk Server.  
  
2.  Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **paramètres du Registre** pour ouvrir le portail [Page Paramètres du Registre](../esb-toolkit/registry-settings-page.md).  
  
3.  Pour activer l’approbation automatique et la publication, tapez l’URL de votre serveur UDDI dans la zone de texte en haut de la **UDDI détails** section de la page, puis sélectionnez le **qu’elle publie automatiquement** case à cocher.  
  
4.  Pour désactiver l’approbation automatique et la publication, désactivez le **publication automatique** case à cocher.  
  
### <a name="to-configure-e-mail-and-registry-settings-for-the-uddi-integration-features"></a>Pour configurer les paramètres de messagerie et du Registre pour les fonctionnalités d’intégration d’UDDI  
  
1.  Assurez-vous que vous vous connectez au portail à l’aide d’un compte qui est membre d’un groupe Administrateurs de BizTalk Server.  
  
2.  Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **paramètres du Registre** pour ouvrir le portail [Page Paramètres du Registre](../esb-toolkit/registry-settings-page.md).  
  
3.  Modifiez l’URL de votre serveur UDDI dans la zone de texte en haut de la **UDDI détails** section de la page. Le service UDDI par défaut est le service de Microsoft UDDI local.  
  
4.  Sélectionnez le **anonyme** case à cocher si vous souhaitez que le portail pour l’authentification anonyme lorsque l’accès au serveur UDDI.  
  
5.  Si vous souhaitez que le portail pour vous informer par courrier électronique lorsqu’une publication UDDI la demande est en attente d’approbation, sélectionnez le **Notification activée** case à cocher dans la **Notification par courrier électronique** section de la page. Puis entrez les détails de votre serveur de messagerie, l’adresse de livraison des messages électroniques, une adresse de messagerie « from » approprié, l’objet du message et le corps du message.  
  
6.  Entrez le nom du contact administrateur et l’adresse de messagerie pour la réception de UDDI demander des messages électroniques dans les **les paramètres par défaut** section de la page.  
  
### <a name="to-approve-or-decline-a-registration-request-as-an-administrator"></a>Pour approuver ou refuser une demande d’enregistrement en tant qu’administrateur  
  
1.  Assurez-vous que vous vous connectez au portail à l’aide d’un compte qui est membre du groupe Administrateurs de BizTalk Server.  
  
2.  Pointez sur le **Registre** onglet dans le menu principal de portail, puis cliquez sur **gérer les demandes en attente** pour ouvrir le portail [Page Gestion des demandes en attente](../esb-toolkit/manage-pending-requests-page.md).  
  
3.  Pour approuver une demande en attente, cliquez sur le **approuver** icône (coche) en regard de cette demande dans la liste.  
  
4.  Pour refuser une demande en attente, cliquez sur le **rejeter** icône (croix) en regard de cette demande dans la liste.  
  
5.  Pour afficher les détails d’une demande en attente, cliquez sur le **afficher les détails** icône (la Loupe) pour ouvrir la [Page Détails du Registre](../esb-toolkit/registry-details-page.md). Vous pouvez publier, supprimer ou mettre à jour de la demande dans cette page.  
  
6.  Pour consulter l’état des demandes et affiche une liste de demandes précédentes, cliquez sur le **afficher l’historique de demande** lien.