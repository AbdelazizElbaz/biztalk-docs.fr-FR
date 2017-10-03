---
title: Comment configurer des certificats avec un adaptateur HTTP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2f454f-22b5-4113-9a23-e00a816d5e48
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f74b0a88983ede90899dac908a5407f8406ec1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-with-an-http-adapter"></a>Comment configurer des certificats avec un adaptateur HTTP
L’adaptateur d’envoi HTTP peut aider à sécuriser une connexion avec les serveurs qui acceptent ou demandent des certificats clients. Si un certificat client est spécifié, l'adaptateur d'envoi HTTP utilise le certificat lors de la connexion aux serveurs qui demandent ou acceptent des certificats clients. Si le certificat client n’est pas spécifié et que le serveur de destination requiert des certificats clients, l’expéditeur n’est pas authentifié et le protocole HTTP d’envoi échoue d’adaptateur pour envoyer le message et suit la logique de nouvelle tentative standard.  
  
 L'adaptateur d'envoi HTTP utilise le certificat client du magasin Personnel du compte sous lequel le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté. Le certificat est spécifié par son empreinte. Si l'adaptateur d'envoi HTTP ne peut pas charger le certificat pour une raison quelconque, le message envoyé est interrompu.  
  
 Lorsque vous utilisez un adaptateur HTTP pour envoyer un message signé ou chiffré, configurez l’empreinte de certificat SSL propriété de transport HTTP pour le port d’envoi. Dans cette propriété, spécifiez l’empreinte numérique du certificat à utiliser pour l’authentification des messages.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
### <a name="to-configure-biztalk-server-to-send-messages-over-an-http-connection"></a>Pour configurer BizTalk Server pour envoyer des messages via une connexion HTTP  
  
1.  Dans la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, créez un port d’envoi HTTP ou ouvrez les propriétés de port d’envoi HTTP existant.  
  
2.  Cliquez sur **configurer** dans la section de Transport de la **propriétés de Port d’envoi** boîte de dialogue.  
  
3.  Cliquez sur **authentification** dans les **propriétés du Transport HTTP** boîte de dialogue.  
  
4.  Dans **type d’authentification**, sélectionnez **anonyme**, **base**, **Digest**, ou **Kerberos**.  
  
5.  Si le type d’authentification est **base** ou **Digest**, sélectionnez **n’utilisez pas l’authentification unique sur** (auquel cas vous devez spécifier le nom d’utilisateur et un mot de passe) ou sélectionnez  **Utiliser l’authentification unique sur** (auquel cas vous devez sélectionner l’Application associée).  
  
6.  Dans **l’empreinte numérique du certificat SSL client**, entrez l’empreinte numérique approprié.  
  
7.  Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.