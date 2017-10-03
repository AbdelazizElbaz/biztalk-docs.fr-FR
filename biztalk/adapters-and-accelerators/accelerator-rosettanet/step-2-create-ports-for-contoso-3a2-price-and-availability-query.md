---
title: "Étape 2 : Création de Ports pour le prix de 3A2 de Contoso et le scénario de requête-réponse de disponibilité à l’aide de l’Explorateur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating ports
ms.assetid: e0b12a96-e799-47ac-8293-7de10662bdf0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64101a31b1d1ea9c7af00471c5d764a1d8cfe598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-creating-ports-for-the-contoso-3a2-price-and-availability-queryresponse-scenario"></a>Étape 2 : Création de Ports pour le prix 3A2 de Contoso et le scénario de requête/réponse de disponibilité
Dans cette étape, vous créez des ports d’envoi à l’aide de l’adaptateur SQL fourni par BizTalk Server. Vous utilisez le port SQL pour envoyer et recevoir la réponse 3A2 en matière de prix et de disponibilité, à destination et en provenance du système ERP de Contoso.  
  
### <a name="to-configure-a-send-port-using-the-sql-adapter"></a>Pour configurer un port d'envoi à l'aide de l'adaptateur SQL  
  
1.  Dans Visual Studio, sur le **vue** menu, cliquez sur **l’Explorateur BizTalk**.  
  
2.  Dans l'Explorateur BizTalk, cliquez avec le bouton droit sur **Ports d'envoi**, puis cliquez sur **Ajouter un port d'envoi**.  
  
3.  Dans la boîte de dialogue Créer un groupe de ports d'envoi, sélectionnez **Port statique avec sollicitation-réponse** dans la liste déroulante, puis cliquez sur **OK**.  
  
4.  Dans la zone **Nom** de la boîte de dialogue Propriétés du port d'envoi statique avec sollicitation-réponse, tapez **3A2SQLReqResponseSendPort**.  
  
5.  Dans la fenêtre Propriétés, sous le titre **Général** , sélectionnez **SQL** en tant que **Type de transport**.  
  
6.  Dans la zone **Adresse (URI)** , cliquez sur le bouton de sélection (**…**).  
  
7.  Dans la boîte de dialogue Propriétés du transport SQL, cliquez sur le bouton de sélection (**...**) en regard de la zone **Chaîne de connexion** .  
  
8.  Dans la boîte de dialogue Propriétés des liaisons de données, dans la zone **Sélectionnez un serveur ou entrez un nom de serveur** , tapez **localhost**.  
  
9. Sélectionnez **Utiliser la sécurité intégrée de Windows NT**.  
  
10. Dans la zone **Sélectionnez la base de données sur le serveur** , sélectionnez **Contoso**, puis cliquez sur **OK**.  
  
11. Dans la boîte de dialogue Propriétés du transport SQL, dans la zone **Espace de noms cible du document** , tapez **http://Contoso.com/Price**.  
  
12. Dans la zone **Nom de l'élément racine du document de réponse** , tapez **rootPriceResponse**, puis cliquez sur **OK**.  
  
13. Dans le volet gauche de la boîte de dialogue Propriétés du port d'envoi statique avec sollicitation-réponse, cliquez sur **Envoyer**.  
  
14. Dans la boîte de dialogue Propriétés du port d'envoi statique avec sollicitation-réponse-Configurations-Envoi-Général, dans la zone **Pipeline d'envoi** , sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
15. Dans la zone **Pipeline de réception** , sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, puis cliquez sur **OK**.  
  
16. Dans l'Explorateur BizTalk, cliquez avec le bouton droit sur **3A2SQLReqResponseSendPort**, puis cliquez sur **Inscrire**. Cliquez avec le bouton droit une fois de plus, puis cliquez sur **Démarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification du processus privé pour Contoso](creating-and-modifying-the-private-process-for-contoso.md)