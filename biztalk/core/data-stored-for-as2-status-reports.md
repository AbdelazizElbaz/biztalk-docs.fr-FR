---
title: "Données stockées pour les rapports d’état AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6aa4077-3768-436b-99b9-d203a86a7e69
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2341004abe65864b2fceb90985871ecad0cf1e5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-stored-for-as2-status-reports"></a>Données stockées pour les rapports d'état AS2
Deux niveaux de création de rapports sont disponibles dans le rapport d’état AS2 : le premier si les **activer la création de rapports** propriété est sélectionnée pour un accord (à partir de la **propriétés générales** page de la **général**  onglet dans le **propriétés de l’accord** boîte de dialogue) et le second si une propriété de stockage de base de données de non-répudiation est sélectionnée pour un accord.  
  
## <a name="data-stored-if-as2-reporting-is-activated"></a>Les données sont stockées si la création de rapports AS2 a été activée  
 Si le **activer la création de rapports** propriété est sélectionnée pour un accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve un enregistrement de tous les envoyé ou reçu les messages AS2 et MDN.  
  
 Dans le cas d'un message AS2, BizTalk Server conserve les informations suivantes :  
  
-   Un enregistrement du message AS2.  
  
 Dans le cas d'un MDN reçu ou envoyé (synchrone ou asynchrone), BizTalk Server conserve les informations suivantes :  
  
-   Un enregistrement du MDN.  
  
 L'interface utilisateur de rapport d'état permet la corrélation de l'enregistrement du message AS2 avec l'enregistrement MDN approprié.  
  
## <a name="data-stored-if-resend-as2-message-if-mdn-not-received-is-enabled"></a>Les données sont stockées si Renvoyer le message AS2 si un MDN n'est pas reçu est activé  
 Si le **renvoyer le message AS2 si MDN non reçu** propriété est sélectionnée pour un accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enregistrera les informations suivantes :  
  
-   Heure de chaque nouvelle tentative d'envoi  
  
-   État de chaque nouvelle tentative d'envoi  
  
-   Index de chaque nouvelle tentative d'envoi  
  
## <a name="data-stored-if-non-repudiation-database-storage-is-enabled"></a>Les données sont stockées si le stockage dans la base de données de non-répudiation est activé  
 Le stockage dans la base de données de non-répudiation est activé si les propriétés d'accord suivantes sont sélectionnées :  
  
-   NRR activé pour les messages AS2 codés en sortie  
  
-   NRR activé pour les messages AS2 décodés en sortie  
  
-   NRR activé pour le MDN en entrée  
  
-   NRR activé pour les messages AS2 codés en entrée  
  
-   NRR activé pour les messages AS2 décodés en entrée  
  
-   NRR activé pour le MDN en sortie  
  
 Si au moins une propriété est sélectionnée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enregistrera les informations suivantes :  
  
-   Le contenu de tout message AS2 et le contenu de n'importe quel MDN (avec ou sans en-têtes AS2).  
  
## <a name="data-stored-for-edi-over-as2"></a>Données stockées pour EDI via AS2  
 Si le **activer la création de rapports** propriété est sélectionnée pour un accord EDI ainsi que d’un accord AS2, puis vous pouvez associer l’enregistrement de message AS2 (contenant la charge EDI) avec un enregistrement de message EDI.  
  
 Si le stockage des documents informatisés est activé, vous pouvez afficher les documents informatisés et le message AS2 dans l'interface utilisateur du rapport d'état.  
  
> [!NOTE]
>  Vous devez utiliser le pipeline AS2EdiReceive ou AS2EdiSend pour accéder à ces rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Données stockées pour les rapports d’état AS2 et EDI](../core/data-stored-for-edi-and-as2-status-reports.md)   
 [Données stockées pour les rapports d’état EDI](../core/data-stored-for-edi-status-reports.md)   
 [Données stockées pour les rapports d’état de traitement par lot](../core/data-stored-for-batching-status-reports.md)