---
title: Comment configurer des certificats avec un adaptateur MSMQ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 922a171d-705f-4465-acda-212aa3797c57
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f36e3d13920982f79fe693a306a8123f089c76e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-with-an-msmq-adapter"></a>Comment configurer des certificats avec un adaptateur MSMQ
L’adaptateur d’envoi MSMQ peut aider à sécuriser une connexion avec les serveurs qui acceptent ou demandent des certificats clients. Si un certificat client est spécifié, l’adaptateur d’envoi MSMQ utilise le certificat lors de la connexion avec les serveurs qui demandent ou acceptent des certificats clients. Si le certificat client n’est pas spécifié et le serveur de destination requiert des certificats clients, l’expéditeur n’est pas authentifié et d’envoi MSMQ adaptateur ne parvient pas à envoyer le message et suit la logique de nouvelle tentative standard.  
  
 MSMQ adaptateur d’envoi utilise le certificat client dans le magasin personnel du compte sous lequel le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est en cours. Le certificat est spécifié par son empreinte. Si l’adaptateur d’envoi MSMQ ne parvient pas à charger le certificat pour une raison quelconque, le message envoyé est interrompu.  
  
 Lorsque vous utilisez un adaptateur MSMQ pour envoyer un message signé ou chiffré, configurez la propriété de transport MSMQ d’empreinte numérique du certificat pour le port d’envoi. Dans cette propriété, spécifiez l’empreinte numérique du certificat à utiliser pour l’authentification des messages. Utilisez cette propriété en combinaison avec la propriété Utiliser l'authentification pour vérifier les messages. Accédez aux files d'attente à l'aide des propriétés Nom d'utilisateur et Mot de passe.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
### <a name="to-configure-biztalk-server-to-send-messages-over-an-msmq-connection"></a>Pour configurer BizTalk Server pour envoyer des messages via une connexion MSMQ  
  
1.  Dans la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, créez un port d’envoi MSMQ ou ouvrez les propriétés de port d’envoi un MSMQ existant.  
  
2.  Cliquez sur **configurer** dans les **Transport** section de la **propriétés de Port d’envoi** boîte de dialogue.  
  
3.  Dans le **propriétés du Transport MSMQ** boîte de dialogue, pour **authentification**, sélectionnez **True**.  
  
4.  Pour **empreinte numérique du certificat**, entrez l’empreinte numérique approprié.  
  
5.  Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.